---
title: "Login black screen login after trying to install radeon 2400 HD"
date: 2013-11-03
forum: Ubuntu Studio
---

### Post by pacome.heuze on 2013-11-03
Hi, I tryed to install radeon driver for the 2400 HD graphique card.
I'm on ubuntu studio 13.10. My computer is an imac 7.1. graphique card radeon 2400 HD

So now i've got the login screen i write my password then i've got a black screen and finally back to loggin after 1 second.
so i can't do alt F1.
Is there anyone in the community that can help me ?

i tried some command in root mode but when i type resume it's says no command found.
thanks

---

### Post by jejeman on 2013-11-03
What driver and how you tried to install exactly?

---

### Post by pacome.heuze on 2013-11-04
I tried to install the catalyst beta 3 driver.

But any way i just reinstalled a fresh new ubuntu studio 13.10.

---

### Post by pacome.heuze on 2013-11-04
I used the package from the website

---

### Post by Bashing-om on 2013-11-04
@ pacome.heuze; Hi !

For future reference in this regard:
> 
IF its an HD 2x/3x/4x then you are out of luck as AMD announced <last> summer that it is relegating these chipsets to legacy status and will not be developing new drivers for them. Existing restricted drivers from AMD won't work either, because they require X-server v1.12 and Ubuntu 12.10 uses X-server v1.13.
That's because, starting with Ubuntu 12.04.2, the X-server version was updated to a newer version that is now incompatible with the HD 2x/3x/4x series AMD cards.
(Mark Phelps)

Sad, but ->

[INDENT][INDENT]that is the way it is
[/INDENT][/INDENT]

---

### Post by pacome.heuze on 2013-11-04
ok, you are right it's sad but as long the free drivers work it's fine. Thanks for your reply.
The fresh install works fine.

---

### Post by Bashing-om on 2013-11-04
pacome.heuze; Hey ,

I agree, open source  - what I have for drivers - works fine. The developers (volunteer effort) do well !

Please mark this thread as "solved" as an aid to others seeking solutions and guidance and as well to help keep the forum tidy.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

