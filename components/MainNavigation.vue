<template>
  <nav class="bg-white shadow-md">
    <div class="max-w-7xl mx-auto px-4">
      <div class="flex justify-between">
        <div class="flex space-x-7">
          <div>
            <NuxtLink to="/" class="flex items-center py-4 px-2">
              <span class="text-gray-500 text-lg hover:text-green-500 font-semibold">Ekobilans</span>
            </NuxtLink>
          </div>
          <div class="hidden md:flex items-center space-x-1">
            <div v-for="(menuItem, index) in menuItems" :key="index" class="relative group">
              <NuxtLink :to="menuItem.link" class="py-4 px-2 text-gray-500 font-semibold hover:text-green-500 transition duration-300">
                {{ menuItem.name }}
              </NuxtLink>
              <div v-if="menuItem.submenu" class="absolute left-0 mt-2 w-48 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 opacity-0 invisible group-hover:opacity-100 group-hover:visible transition duration-300">
                <div class="py-1" role="menu" aria-orientation="vertical" aria-labelledby="options-menu">
                  <template v-for="(subItem, subIndex) in menuItem.submenu" :key="subIndex">
                    <NuxtLink v-if="!subItem.submenu" :to="subItem.link" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-green-500" role="menuitem">
                      {{ subItem.name }}
                    </NuxtLink>
                    <div v-else class="relative group">
                      <NuxtLink :to="subItem.link" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900 flex justify-between items-center" role="menuitem">
                        {{ subItem.name }}
                        <ChevronRight class="h-4 w-4" />
                      </NuxtLink>
                      <div class="absolute left-full top-0 w-48 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 opacity-0 invisible group-hover:opacity-100 group-hover:visible transition duration-300">
                        <div class="py-1" role="menu" aria-orientation="vertical" aria-labelledby="options-menu">
                          <NuxtLink v-for="(grandChild, grandChildIndex) in subItem.submenu" :key="grandChildIndex" :to="grandChild.link" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100 hover:text-gray-900" role="menuitem">
                            {{ grandChild.name }}
                          </NuxtLink>
                        </div>
                      </div>
                    </div>
                  </template>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </nav>
</template>

<script setup>
import { ChevronRight } from 'lucide-vue-next'

const menuItems = [
  {
    name: 'O firmie',
    link: '/o-firmie',
    submenu: [
      { name: 'Historia', link: '/o-firmie/historia' },
      { name: 'Referencje', link: '/o-firmie/referencje' },
      { name: 'Rankingi', link: '/o-firmie/rankingi' },
      { name: 'RODO', link: '/o-firmie/rodo' },
      { name: 'Słownik pojęć', link: '/o-firmie/slownik-pojec' },
    ]
  },
  {
    name: 'Aktualności',
    link: '/aktualnosci',
    submenu: [
      { 
        name: 'Unia Europejska', 
        link: '/aktualnosci/unia-europejska',
        submenu: [
          { name: 'Działanie III.6', link: '/aktualnosci/unia-europejska/dzialanie-iii-6' },
          { name: 'Działanie 8.2', link: '/aktualnosci/unia-europejska/dzialanie-8-2' },
        ]
      },
      { name: 'Aktualności / Wydarzenia', link: '/aktualnosci/wydarzenia' },
      { name: 'Polecane strony www', link: '/aktualnosci/polecane-strony' },
    ]
  },
  {
    name: 'Nasi klienci',
    link: '/nasi-klienci',
    submenu: [
      { name: 'Transport', link: '/nasi-klienci/transport' },
      { name: 'Kultura i sztuka', link: '/nasi-klienci/kultura-i-sztuka' },
      { name: 'Spółdzielnie Mieszkaniowe / TBS', link: '/nasi-klienci/spoldzielnie-mieszkaniowe-tbs' },
      { name: 'Branża medyczna', link: '/nasi-klienci/branza-medyczna' },
      { name: 'Jednostki budżetowe', link: '/nasi-klienci/jednostki-budzetowe' },
      { name: 'Ośrodki badawczo - rozwojowe', link: '/nasi-klienci/osrodki-badawczo-rozwojowe' },
      { name: 'SPOŁEM', link: '/nasi-klienci/spolem' },
      { name: 'Radio', link: '/nasi-klienci/radio' },
      { name: 'Branża komunalna', link: '/nasi-klienci/branza-komunalna' },
      { name: 'Energetyka', link: '/nasi-klienci/energetyka' },
      { name: 'Budownictwo', link: '/nasi-klienci/budownictwo' },
      { name: 'Kluby sportowe', link: '/nasi-klienci/kluby-sportowe' },
      { name: 'Uzdrowiska', link: '/nasi-klienci/uzdrowiska' },
      { name: 'Jednostki notowane na GPW i New Connect', link: '/nasi-klienci/jednostki-notowane-gpw-new-connect' },
      { name: 'Tworzenie biznesplanów', link: '/nasi-klienci/tworzenie-biznesplanow' },
    ]
  },
  {
    name: 'Oferta',
    link: '/oferta',
    submenu: [
      { name: 'Wycena', link: '/oferta/wycena' },
      { 
        name: 'Badanie sprawozdań finansowych', 
        link: '/oferta/badanie-sprawozdan-finansowych',
        submenu: [
          { name: 'Jednostkowe badanie sprawozdania finansowego', link: '/oferta/badanie-sprawozdan-finansowych/jednostkowe' },
          { name: 'Skonsolidowane badanie sprawozdania finansowego', link: '/oferta/badanie-sprawozdan-finansowych/skonsolidowane' },
          { name: 'Łączne badanie sprawozdania finansowego', link: '/oferta/badanie-sprawozdan-finansowych/laczne' },
        ]
      },
      { name: 'Audyt zewnętrzny projektów unijnych', link: '/oferta/audyt-zewnetrzny-projektow-unijnych' },
      { name: 'Wyceny znaków towarowych/udziałów/akcji/ZCP', link: '/oferta/wyceny' },
      { name: 'Podział, połączenia i przekształcenia Spółek', link: '/oferta/podzial-polaczenia-przeksztalcenia-spolek' },
      { name: 'Prowadzenie ksiąg rachunkowych', link: '/oferta/prowadzenie-ksiag-rachunkowych' },
      { name: 'Analiza ekonomiczna', link: '/oferta/analiza-ekonomiczna' },
      { name: 'Doradztwo biznesowe', link: '/oferta/doradztwo-biznesowe' },
      { name: 'Ekspertyzy sądowe i prokuratorskie', link: '/oferta/ekspertyzy-sadowe-i-prokuratorskie' },
      { name: 'Przeprowadzanie postępowań likwidacyjnych i doradztwo w procesie przed upadłościowym', link: '/oferta/postepowania-likwidacyjne-doradztwo-upadlosciowe' },
      { name: 'Biznesplan', link: '/oferta/biznesplan' },
    ]
  },
];
</script>