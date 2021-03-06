---
title: Java 9
date: 2017-09-24T01:53:22+00:00
slug: java9
categories:
  - Prikaz
  - Razvoj
tag:
  - java
  - java9
  - prikaz
  - razvoj
---

[_Zulu_](http://jdk.java.net/9/) je tu. Mda, neko bi mogao da poradi malo na imenovanju ovih verzija... Kako bilo, deveto izdanje Jave je jedno od najvažnijih izdanja platforme - i sigurno najkontroverznije. Razlog za to je, naravno, JPMS: _Java Platform Modular System;_ okosnica i suština ovog devetog izdanja, oko kojeg su se najviše lomila koplja i koji je bio glavni razlog višestrukih odlaganja datuma izlaska. Sada je sve gotovo; novo poglavlje za Javu može da počne.

<!--more-->

Šta bi bilo najvažnije u Javi 9? Bez obzira šta mislili o tome, JPMS je novina (koja dolazi kasno i) koja se ne može zanemariti. Sigurno, novi modularni sistem će nam u početku doneti manje-više problema, ali na duže staze predstavlja temelj jedne lakše i fleksibilnije JVM platforme. No to ne treba da zaseni i ostale novine: `VarHandle`, na primer, ili _factory_ za kolekcije - siguran sam da će ubrzo naći mesto u svakodnevnom radu. Ako bi dozvolili sebi malo filozofiranja, delim mišljenje koje sam pročitao negde: najvažnija stvar u vezi nove verzije Jave je... Java 10. Čini mi se da devetka postavlja temelj budućih verzija koje bi trebale da donesu snažan napredak platforme.

Ako nastavimo da razmišljamo u tom smeru, druga jedna vest je na mene ostavila veći utisak nego novo izdanje Jave. Reč je o planu Orakla da ubuduće izbacuje nove verzije Java [na svakih šest meseci](http://www.oracle.com/technetwork/java/eol-135779.html)! Imati kraći ciklus verzija je mnogo zdravije za jezik i platformu, a novine će lakše biti usvajane. A sada da se vratimo devetci.

Šta bi bilo najmanje interesantno od novih stvari? `jshell`. Da se razumemo, ne bunim se da postoji, ali ne verujem da ću mu ikada naći primenu.

Šta najviše nedostaje? Nije sasvim fer ukazivati na nedostatke, jer posle svega, Orakl je zaista uložio značajan trud u ovu verziju. No, siguran sam da svima nedostaju unapređenja i usavršavanja samog jezika (sintakse). Drugi [JVM jezici](https://kotlinlang.org) odavno pružaju komforniju sintaksu, koja Javi notorno nedostaje. Imajući ovo u obzir, ne čudi kritika da je Java 9 siromašna novim funkcionalnostima i da više zaslužuje da bude označena kao 8.1. Sigurno, jedan od najpopularnijih programskih jezika ne može tek tako da dozvoli da implementira sve ‘novotarije’: čeka se da se u jezik uključe one koje su se pokazale kao najbolje. Ipak, da li se predugo čeka?

Kada preći na Javu 9? Ako pogledamo unazad, svaka nova verzija Jave je sve brže nalazila put do produkcije. Novi projekti nemaju razloga da ne krenu od poslednje verzije platforme. Postojeći kod će takođe polako pronaći put, na sličan način kako je to bilo sa osmicom. Najveći izazov će biti migracija na JMPS sa postojećih rešenja (OSGI, JBoss).

## Novotarije

Evo nekih novina Jave 9 koje sam izdvojio, a da nisu JPMS; pobrojane bez posebnog reda. Neću se ovde baviti njima; siguran sam da će se mnogo elektronskog mastila potrošiti na detalje, no ništa od toga dok ih sami ne probate u praksi.

  * Kompaktni stringovi - do sada je Java pamtila stringove kao `char[]`. Sada to zavisi od samog sadržaja: ako je u pitanju LATIN1 tekst, slova se čuvaju kao `byte[]`. Troši se manje memorije, a prilično dobija na performansama.
  * `Map.of()`, `List.of()`, `Set.of()` - novi način pravljenja kolekcija. Mogu samo da kažem: "gde ste bili do sada sve ovo vreme?"
  * `java.util.concurrent.Flow` kaže: _Reactive Streams_. O ovome će sigurno još puno toga biti pisano.
  * `CompletableFuture.delayedExecutor()` - za odloženo izvršavanje koda.
  * `VarHandle` je način da se izvrše atomske operacija na polju klase. Slično postoji i `MethodHandle`, za metode. Ono što je ranije sadržano u `Unsafe` klasi, sada je zvaničan deo API-ja. Suština uvođenja ovih klasa su poboljšane performanse.
  * Dokumentacija (_javadoc_) se sada može pretraživati.
  * Stream API je unapređen. Dodate su nove metode: `dropWhile`, `takeWhile`, `ofNullable`. `Optional` može da se pretvori u stream. `iterate()` može da primi 3 argumenta, slično `for`.
  * Interfejsi konačno mogu da imaju privatne metode.
  * Novi HTTP klijent u Javi 9 je `HttpRequest` i podržava HTTP2 i WebSockets. I podseća na [Jodd](https://jodd.org).
  * G1 postaje pretpostavljeni _garbage collector_.
  * Process API je takođe značajno unapređen. Java sada poznaje sistemske PID-ove procesa i sl.
  * Java kompajer donosi kompajliranje pojedinih delova sorsa u _native_ kod pre nego što se kod izvrši na JVM. Ovo smanjuje vreme zagrevanje virtuelne mašine. Još uvek eksperimentalno.
  * Sintaksni konstrukt _Try-With-Resources_ prima `final` varijable.
  * Sistemsko logovanje svih komponenti JVMa.

Promene su vrlo dobrodošle.
