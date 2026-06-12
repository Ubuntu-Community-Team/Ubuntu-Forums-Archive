---
title: "Norwegian LoCo"
date: 2005-02-20
forum: The Cafe
---

### Post by steffen on 2005-02-20
I don't know if there are enough people around to set up a Norwegian LoCo team yet. However, there are a few issues that needs to be addressed, to have Ubuntu looking like a professional alternative on the Norwegian desktop.

**Language mess** 
First of all, the current system of picking .mo and .po files for packages needs to be reworked. Currently, it seems to me (without having any technical knowledge of the matter) that languages for a package is chosen in the following order:

[list=1]
[*] Norwegian, bokmål
[*] If no Norwegian bokmål, then Norwegian nynorsk
[*] If none of the above, Danish
[*] If none of the above, Swedish
[*] If none of the above, English
[/list] 

I'm not sure about removing Norwegian nynorsk from this list (or Norwegian bokmål, if nynorsk is preferred), but Swedish and Danish should definitely go. There are simply too many languages to deal with on the desktop, and it looks unprofessional.

I propose the following preferences:

[list=1]
[*] Norwegian bokmål
[*] If no Norwegian bokmål, then Norwegian nynorsk
[*] If no Norwegian, use English
[/list] 

**Rosetta**
Currently there are a few translators working on Norwegian in Rosetta. In some of these cases there are Norwegian language packs in the repositories of the package, but they have not been reported to Rosetta. Where can we report these language packs, so not to spend unecessary time translating already translated packages?

Another thing that should be done straight away in Rosetta is the mix of Nynorsk and Bokmål. There are currently three "Norwegian"-entries on the list of languages
[list]
[*]Bokmål, Norwegian
[*]Norwegian, Nynorsk
[*]Norwegian
[/list] 

This does not work. First of all, if we are operating with bokmål and nynorsk, Norwegian should not be an entry, since it would have to be split. If someone translates the 'Norwegian' no-one would know, without testing, whether it is bokmål or nynorsk.

Second, few people will find 'bokmål' on the list, since they are usually looking for 'Norwegian, ...'. Some of the projects that are bokmål, are now in the 'Norwegian' list and some in the 'Bokmål, Norwegian list'. This should definitely be changed to:
[list]
[*]Norwegian, bokmål, and
[*]Norwegian, nynorsk
[/list]

Therefore...
[list]
[*] all 'Bokmål, Norwegian' translations should be put into 'Norwegian', 
[*] 'Norwegian' should be renamed 'Norwegian, bokmål' 
[*] and 'Bokmål, Norwegian' should be removed.
[/list]

---

### Post by simira on 2005-02-22
Please see my email on the rosetta mailing list.

I've already reported bugs about these cases in Rosetta. We're also in process of starting a LoCo and a translation team that you (and any other interested)  are very welcome to join and contribute. I hope to get a better opportunity to coordinate and make a priority system for translation through the LoCo work.

---

### Post by steffen on 2005-02-22
Sounds excellent!  \\:D/

---

