---
title: "hydrogen - can not hear no sound"
date: 2016-04-14
forum: Ubuntu Studio
---

### Post by kbogdziewicz on 2016-04-14
Hello, 

I have installed Ubuntu Studio 14.04.4 Trusty Tahr LTS on which is it install Hydrogen.
I'm tying to configure Hydrogen to work with jackd, but, after that, i can not hear any sound.

Messages from jackd:
JackEngine::XRun: client = Hydrogen was not finished, state = Running
JackEngine::XRun: client = hydrogen-midi was not finished, state = Running
JackAudioDriver::ProcessGraphAsyncMaster: Process error

B&#322;&#261;d XSDError w file:///home/cris/.hydrogen/data/drumkits/DeathMetal/drumkit.xml, wiersz 1, kolumna 14: Brak dost&#281;pnej definicji dla elementu drumkit_info.


Messages from Hydrogen:
B&#322;&#261;d XSDError w file:///home/cris/.hydrogen/data/drumkits/DeathMetal/drumkit.xml, wiersz 1, kolumna 14: Brak dost&#281;pnej definicji dla elementu drumkit_info. (No definition is available for the item drumkit info)


(E) XMLDoc::read XML document /usr/share/hydrogen/data/drumkits/UltraAcousticKit/drumkit.xml is not valid (/usr/share/hydrogen/data/xsd/drumkit.xsd), loading may fail
(E) Legacy::load_drumkit loading drumkit with legacy code
(E) XMLDoc::read XML document /usr/share/hydrogen/data/drumkits/VariBreaks/drumkit.xml is not valid (/usr/share/hydrogen/data/xsd/drumkit.xsd), loading may fail
(E) Legacy::load_drumkit loading drumkit with legacy code


I will appreciate for any help.
Chris

---

