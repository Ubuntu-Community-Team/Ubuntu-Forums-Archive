---
title: "Please explain to me named.stats file"
date: 2016-01-20
forum: Server Platforms
---

### Post by Grigoriy on 2016-01-20
Hello!

I don't quite understand BIND9's statistics file named.stats. Couple of things:

1.)  +++ Statistics Dump +++ (1453303803)  - what does it mean? Is it when the file was created? And One and half billion - are those seconds counting from 1970? Is there a more human-friendly way to see it?

2.) Below that we've got some statistics. But it's totally unclear to me what's the starting point? Is it from the first installation of BIND9 on my particular system and its first run OR maybe from certain point in the past OR perhaps from the time of last restart?

---

### Post by nerdtron on 2016-01-20
The time stamp is in epoch time. More info on epochtime here: [http://www.epochconverter.com/](http://www.epochconverter.com/)

Yes, it's counting since 1970. And yes you can convert them to human friendly way (not at the config, I think, you have to convert them manually).

---

### Post by Grigoriy on 2016-01-20
I see... Okay thanks! Still if someone could explain me more about this file, I'd appreciate that.

---

