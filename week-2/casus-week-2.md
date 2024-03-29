# Casus week 2

De analyses die je vorige week voor de klant hebt uitgevoerd, hebben nieuwsgierigheid gewekt. De klant zou deze inzichten dan ook graag met een breder publiek willen delen. De klant wil graag dat je hier een SSRS-rapport voor vormgeeft, en de ontwerper heeft al een idee gepitcht hoe dit eruit zou kunnen komen te zien. Aan jou de taak om hier zo dicht mogelijk bij te komen!

Het ontwerp waar de ontwerper mee gekomen is, is te vinden in de meegeleverde [PDF](./Report1.pdf). Hierbij de volgende kanttekeningen:

1. De tabel met productverkopen staat normaal gesproken 1 cm onder de grafiek met "top 5 klanten over de jaren". Door de PDF-export is deze echter onbedoeld op de volgende pagina terecht gekomen.
2. De tabel met productverkopen heeft een interactieve drilldown. In de PDF-export is deze als voorbeeld al opengeklapt onder "Bikes" -> "Mountain bikes".

Zoals je ziet is de weergegeven data gebaseerd deels op je queries van vorige week, maar is er regelmatig een kleine extra - zoals het weergeven van de top 5 door de tijd (hint: eerst de top 5 bepalen, daarna de verkopen door de tijd erbij zoeken). De data bepaal je bijna 100% in SQL. Er zijn ook vier extra tabellen, die mag je inlezen op een manier die je zelf prettig vindt. Besteed daar echter niet de meeste tijd aan: je hebt deze maar nodig voor één visual (de tabel onderaan het rapport) dus je kunt deze altijd op een later moment toevoegen.

## Bonus

* Standaard is het rapport statisch. Kun je het rapport parameters geven, zodat de data voor één jaar wordt weergegeven? De trends mogen dan tot aan dat jaar worden weergegeven.
  * Het is dan extra netjes om te kijken 
* Geef de grafiek met VS verkopen per staat een zgn. "Action", waardoor het als een _drillthrough_ gaat functioneren. Een klik op een staat moet het tweede rapport openen, dat dan ook gefilterd wordt op die bewuste staat.
  * Concreet voorbeeld: ik klik op San Francisco. Het tweede rapport opent zich, waarin de top 5 steden, verkopers en klanten worden weergegeven. Deze keer echter alleen voor San Francisco.
* Groepeer je queries in Stored Procedures - zorg ervoor dat er geen SQL meer in de SSRS-datasets zit!
* De klant heeft gevraagd of het rapport op een A3-pagina geprint kan worden, als dat nodig blijkt te zijn. Houd hier rekening mee!

## Hints

* Als BI-team zijn we altijd blij met enthousiaste klanten. Wel vinden we het wat voorbarig om zomaar op de Staging Area "tijdelijke" rapportages neer te zetten. Als die er namelijk éénmaal zijn, is de kans groot dat de klant de noodzaak voor een volledig Data Warehouse minder sterk inziet. Goed om hier op gefocust te blijven, en hier scherpe antwoorden op te bedenken en ontdekken in de komende cursus - het zou zomaar kunnen dat we de klant moeten overtuigen!
* Als je dit rapport voor het eerst ziet, is de kans groot dat je even schrikt: hoe ga je dit voor elkaar boksen? Kaarten in je rapport - hoe werken die eigenlijk? En hoe krijg je de opmaak goed strak? Hoewel je zelf verantwoordelijk bent voor het eindresultaat, zit je deze dag gelukkig precies één dag op kantoor in Huizen tussen de ervaren collega's. Gebruik die aanwezige kennis en ervaring over SSRS!
* SSRS gaat al even mee, dus het zou goed kunnen dat je tijdens je zoekacties op internet oudere versies tegenkomt. Dat is prima, maar steek geen moeite in SSRS-versies lager dan versie 2008R2 ("2008R2" is eigenlijk 2010. Versie 2008 is dus lager) - daar zijn diverse zaken behoorlijk anders ingericht.
* Voor het koppelen van je dataset aan de "map" visual in SSRS heb je de codes nodig van de staten in de V.S. - deze is opgeslagen in `StateProvince`. Kijk hier even goed of je de juiste data van SQL Server terugkrijgt: het zou kunnen dat na de data nog een spatie teveel is opgenomen. Bedenk even goed hoe je hier achter komt - de functie `LEN` gaat je hier in elk geval niet bij helpen (waarom niet?). Mocht je hier tegenaan lopen, kap dan de kolom in je SQL-query af op twee karakters met behulp van de `LEFT`-functie.
* Wanneer je in een grafiek een trend door de tijd wilt weergeven, kan het handig zijn die in SQL vast uit te splitsen op het niveau waarnaar je wilt kijken.
* Staar je niet blind op hoe je de opmaak precies moet afronden. Focus je eerst op de inhoud en globale werking. Wanneer je dan met de opmaak aan de slag gaat:
  * Gebruik niet de ingebouwde chart-titles, maar gebruik eigen textboxes
  * Verander alle Arial-fonts naar Segoe UI Light
  * Maak de achtergrond van het rapport lichtgrijs, zorg ervoor dat alle visuele elementen in witte rectangles daarop worden uitgelijnd.
  * Zoek op [www.msbiblog.com](https://www.msbiblog.com/) naar "SSRS", en kijk wat je daar voor aanwijzingen vindt
