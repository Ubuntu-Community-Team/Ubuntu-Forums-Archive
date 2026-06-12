---
title: "Can't connect to Eduroam"
date: 2017-09-16
forum: Ubuntu Development Version
---

### Post by rytuklis on 2017-09-16
Hi guys,

So the university I study in (Kaunas Vytautas Magnus University, Lithuania) has eduroam - a wireless network made for students and for learning purposes.
I've just recently decided to give Linux another shot, as I need a stable computer for my studies and Windows.. do not seem that stable.

Anyways, when I was under Windows, all I had to do to connect was simply input my username and password and have it over with. In Ubuntu, however, I had to make a few tweaks, and it still fails to connect.

I followed the guide provided by the university here: [http://eduroam.vdu.lt/lt/2016/10/07/ubuntu-os/](http://eduroam.vdu.lt/lt/2016/10/07/ubuntu-os/)
Everything in the network settings is set as in the guide above, but whenever trying to connect it just keeps prompting me for username and password and upon entering one, it then tries to connect again and prompts me to it again.

Any ideas guys? 
Thanks.
I am using Ubuntu 17.10 (I know it's in beta but this isn't a distro problem, as this persisted in Ubuntu Gnome as well)

---

### Post by Bucky Ball on 2017-09-16
> **rytuklis said:**
> I followed the guide provided by the university here: [http://eduroam.vdu.lt/lt/2016/10/07/ubuntu-os/](http://eduroam.vdu.lt/lt/2016/10/07/ubuntu-os/)

Always the first port of call is your university. Have you tried to sort this out with the uni IT department before coming here? Advise you to do so. The uni know their network and the protocols they are using. We don't. Generally, we can't give a lot of help with these things. Not directly a Ubuntu issue and more to do with something the uni, or Eduroam, has set up.

> **rytuklis said:**
> I am using Ubuntu 17.10 (I know it's in beta but this isn't a distro problem, as this persisted in Ubuntu Gnome as well)

Consequently, this post doesn't belong here and I have asked for it to be moved. 17.10 is not released for another month. As it's not far away, staff may decide to leave this here. 

Good luck. ;)

---

### Post by wildmanne39 on 2017-09-16
*Thread moved to **Ubuntu Development Version**.*

---

### Post by wgarcia on 2017-09-17
Have you entered all the fields provided by your university in the WPA/WPA 2 Enterprise fields? Eduroam is used all over Europe and has the same standards, I'm connecting every day using Ubuntu 17.10 with no problems. In Linux you need to provide all fields, and your university should tell you what they are, for instance in my university I need:

Authentication: Tunneled TLS (you may see TTLS)
Inner Authentication: PAP

but these may be different at your place, apart from this you need anonymous identity, username and password.

---

### Post by Bucky Ball on 2017-09-17
> **wgarcia said:**
> Eduroam is used all over Europe ...

Actually, all over the world I believe. That's why it's called 'Eduroam'. Roam the planet and link up with any uni using Eduroam, which is most of them. ;)

Same requirements for logging on here in Australia. As mentioned, first port of call with this is your uni IT department.

---

