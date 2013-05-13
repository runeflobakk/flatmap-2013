flatMap(Oslo), dag 1:
===============================


Keynote: Living in a Post-Functional World
-------------------------------------------

Veldig bra keynote av alltid engasjerte og engasjerende Daniel Spiewak. Han tok for seg funksjonell programmering i stor skala, eller Enterprise om du vil, og at det må bli slutt på denne evinnelige kampen om å bli så forbanna "purely" functional. Ja, funksjonell programmering har virkelig noe for seg, og man gjør best i lære seg dette, men det er ikke slik at objekt-orientering _bare_ er "evil".

I tråd med Martin Odersky sin nylige keynote på Devoxx (http://parleys.com/play/51704efce4b095cc56d8d4b5/chapter1/about) snakker Spiewak om typiske mangler ved funksjonelle språk som gjør at ting ikke skalerer når man får en stor nok kodebase, og hvor man gjerne henter "the good parts" fra OO for å bøte på dette. Det som trekkes frem spesielt er modularisering, "et sted å legge ting", istedet for at alle funksjoner eksisterer i en stor global blob som bare vokser. I Scala brukes traits til å modularisere hvilke funksjoner (og annet) som til enhver tid er tilgjengelig. Det ble vist kodeeksempler på hvordan man kan uttrykke avhengigheter mellom moduler, og hvordan man kan komponere ulike sammensetninger av konkrete moduler for runtime. Modulsystemet ble identifisert som en "enabler" av den famøse cake-pattern av smarte BEKKere etter keynoten.

En annen ting Spiewak snakket om i forbindelse med funksjonell vs. objektorientert programmering var _The expression problem_, et problem identifisert av Philip Wadler, og som man typisk bare løser den ene eller andre delen av hvis man programmerer erketypisk hhv. enten funksjonelt eller objektorientert. En generisk beskrivelse finner på Wikipedia: http://en.wikipedia.org/wiki/Expression_problem

Kort fortalt så går problemet ut på forskjellen ved å uttrykke dispatch av ulike implemenasjoner av en operasjon basert på typer, på en av disse måtene:
(1) eksternt for typene v.h.a. en switch/case eller if-elseif-else (eller typisk pattern matching i funksjonelle språk)
(2) internt i typene (objekter) v.h.a. polymorfisme.

For (1) er det lett å legge til nye operasjoner for typene, man lager en switch/case (eller tilsvarende) som utfører det som er relevant for de ulike typene. Men det er vanskelig å legge til en ny type da dette påvirker alle operasjoner basert på matching av type.

For (2) er det lett å lette til en ny type da de eksisterende ikke trenger å vite om denne typen, og denne kan legges til i isolasjon og implementere abstrakte metoder. Men det er vanskelig å legge til en ny operasjon, da dette påvirker alle subtyper som må implementere sitt case av denne metoden.

(1) er generelt frowned upon i objektorientering, da polymorfisme anses generelt som awesome. Men dette er først og fremst dersom man ønsker å enkelt kunne legge til nye subtyper, og ikke nye operasjoner. Legger man ofte til nye operasjoner på en type, påvirker dette følgelig alle subtyper. En ny operasjon kan legges til uten å måtte rekompilere typene dersom den er ekstern v.h.a. en switch/case.

Wikipedia-artikkelen påstår at problemet kan løses v.h.a. en type class, men Spiewak selv viste ikke frem noen løsning, men viste til at man må være klar over hvilke tradeoff man gjør etter hvilken strategi man velger. Den typiske strategien i FP og OO kommer med hver sine fordeler og ulemper, og selvfølgelig, Scala støtter jo begge deler.

Ulike implementasjoner av en operasjon for ulike typer er forresten også noe man kommer borti i Coursera-kurset om funksjonell programmering i Scala, og hvor det løses både v.h.a. pattern matching (FP) og polymorfisme (OO).



Parsing A La Carte
--------------------

Nok en sesjon av Daniel Spiewak, denne gangen en workshop hvor vi fulgte live-koding i 1,5 time av parser combinators i Scala. Jeg dro opp Mac'en i håp om at jeg kunne code-along, men det viste seg raskt å være håpløst å henge med for mitt vedkommende. Det var dog veldig utbytterikt å bare følge med på hva Spiewak gjorde i forrykende hastighet mens han forklarte og gestikulerte.

http://www.codecommit.com/blog/scala/the-magic-behind-parser-combinators



Shapeless
-----------

https://github.com/milessabin/shapeless

Typesystem-eksperimentene til Miles Sabin er manifestert i et bibliotek som heter Shapeless. Biblioteket forsøker å tilby en måte å utføre operasjoner på enkeltdeler av helt vilkårlige komposittobjekter, på en typesikker måte. F.eks. si at man har et tre med noder av lister av personer. Da skal man med Shapeless f.eks. typesikkert kunne inkrementere alderen på alle personene, selv om denne trestrukturen er helt ukjent for Shapeless. Dette gjør han med å konvertere objekter til og fra en såkalt HList, en Heterogeneous List. En HList er en liste som har samme antall typeparametre som listeelementer, og hver parameter angir den spesifikke typen til hvert element.

Jeg merker jeg er litt "Meh!"... 


Composable Abstractions in Clojure
------------------------------------

Fin introduksjon til Clojure, som likevel var litt mer avansert enn typiske Hello World-eksempler. Lett å følge koden på slidene, og det ble vektlagt Clojures evne til å kunne komponere sammen urelaterte biblioteker, fremfor å velge ett monolittisk rammeverk man støtter seg på.

På slutten fikk Erik Bakstad også sneket inn litt reklame for et verktøy for dokumentasjon og visualisering av systemarkitektur, et verktøy han nå jobber fulltid med. http://www.ardoq.com




Java 8, nytt i Scala 2.10, Practical Lambda Calculus
------------------------------------------------------

Lite nytt man ikke visste fra før, både ang. Java 8 og Scala 2.10. Gjennomgående tema var at det kommer mye niceness med Project Lambda i Java 8, men at Scala et. al. er nicere. 

Practical Lambda Calculus var egentlig bare en show-off i hvordan uttykke heltall i ren lambda calculus, altså man har ingen tall tilgjengelig, bare funksjoner. Ganske lite practical...

