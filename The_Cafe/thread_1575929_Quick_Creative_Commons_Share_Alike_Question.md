---
title: "Quick Creative Commons Share Alike Question"
date: 2010-09-16
forum: The Cafe
---

### Post by JDShu on 2010-09-16
I found some perfect music for a game that I and an artist friend are making. The music is licensed cc-by-nc-sa. I am planning on making the code GPL, but my friend wants to keep the copyright of his artwork. If I used the music, does everything about the game including my friend's artwork need to be cc-by-nc-sa as well? (does it count as a derivative work, I guess?)

---

### Post by kaldor on 2010-09-16
hi jdshu :)

---

### Post by Brunellus on 2010-09-16
That's a proper legal question, and deserves a proper legal answer.  I recommend you call a lawyer, who can give you real advice.  Asking Internet forums for legal advice is a bad idea.

---

### Post by earthpigg on 2010-09-16
> **JDShu said:**
> If I used the music, does everything about the game including my friend's artwork need to be cc-by-nc-sa as well? (does it count as a derivative work, I guess?)

as i understand it, you can include cc-by-nc-sa artwork in GPL'd software, and you can have the rest of the artwork GPL'd.

---

### Post by Bachstelze on 2010-09-16
> **earthpigg said:**
> as i understand it, you can include cc-by-nc-sa artwork in GPL'd software, and you can have the rest of the artwork GPL'd.

CC-BY-NC-SA is **not** GPL-compatible (mainly because of the NC).  Whether or not the artwork is affected by the virality of the GPL is another matter, though, but assuming it is, you can use it in a GPL project.

---

### Post by earthpigg on 2010-09-16
here's an example:

```
---------------------------------------------------------- Tremulous License ---

Tremulous is licensed in two broadly separate sections: the code and the media. 

The code is licensed under the GNU GENERAL PUBLIC LICENSE. This license is
contained in full in the file named GPL. Please be aware of the exceptions to
this license as listed below.

The media is licensed under the CREATIVE COMMONS ATTRIBUTION-SHAREALIKE 2.5
LICENSE. Please read http://creativecommons.org/licenses/by-sa/2.5/ to learn
more about this license. The full license text is contained in the file named
CC. Please be aware of the exceptions to this license as listed below.


---------------------------------------------------- Code License Exceptions ---

The following files contain sections of code that are not licensed under the
GPL, but are nevertheless GPL compatible. The license text for these licenses
is contained within the files as listed.

    src/qcommon/unzip.c                                         zlib license
    src/game/bg_lib.c                                            BSD license
    src/client/snd_adpcm.c            Stichting Mathematisch Centrum license
    src/jpeg-6/*                                                JPEG license


--------------------------------------------------- Media License Exceptions ---

All shaderlab (http://www.shaderlab.com/) textures (by Randy 'ydnar' Reddig)
are subject to the following license:

  Usage and redistribution policy: Textures may be freely downloaded, modified,
  and used in free maps, mods or total conversions provided this copyright
  notice is left intact and a link to Shaderlab is provided in the credits or
  read-me file. Other non-commercial applications are considered on a
  case-by-case basis via e-mail. All other usage requires written permission.
  Bulk redistribution or archival of the textures in any medium, digital or
  otherwise (except mapping packages for mods) is prohibited.
                        
```

---

### Post by JDShu on 2010-09-16
Hmmm seems like Brunellus is right and the ambiguity isn't so easily figured out as I thought. Maybe the best way is to attempt to contact the original music artist and see what he thinks. Lawyers seem a bit beyond my budget at the moment :P

---

### Post by Bachstelze on 2010-09-16
@earthpigg: what you posted is CC-BY-SA,no NC. Also just because a project does it doesn't mean it's correct.

---

### Post by Elfy on 2010-09-16
> **Brunellus said:**
> That's a proper legal question, and deserves a proper legal answer.  I recommend you call a lawyer, who can give you real advice.  Asking Internet forums for legal advice is a bad idea.

> **JDShu said:**
> Hmmm seems like Brunellus is right and the ambiguity isn't so easily figured out as I thought. Maybe the best way is to attempt to contact the original music artist and see what he thinks. Lawyers seem a bit beyond my budget at the moment :P

In the light of these comments I think that this comes too close to handing out legal advice. This really isn't the right place for it. Thread closed

---

