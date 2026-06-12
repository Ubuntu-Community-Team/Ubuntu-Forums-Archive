---
title: "Easy administration for server NIS, DHCP, etc"
date: 2009-01-17
forum: Server Platforms
---

### Post by pb0711 on 2009-01-17
Dear all,

I have relatively recently moved to ubuntu from opensuse. I have started using ubuntu for my personal computer and I love it. However, the only thing that I really miss on opensuse is the the YaST interface to the server apts such as NIS, DHCP, file print servers etc. i would really like to move my servers over to ubuntu and while I can do everything in config files it can be easier for me and my other IT ppl to use a GUI. 
I have done some googling and found that there is a team that is working on this and that it was apparently released for gutsy. When I look in the Package manager I don't find anything under 'easy' or 'server' or 'business'.
[https://wiki.ubuntu.com/UbuntuEasyBusinessServer](https://wiki.ubuntu.com/UbuntuEasyBusinessServer)

Any ideas on how to get this package or is there something else that someone can recommend to me?

Cheers,

Paul

---

### Post by albinootje on 2009-01-17
> **pb0711 said:**
> i would really like to move my servers over to ubuntu and while I can do everything in config files it can be easier for me and my other IT ppl to use a GUI. 


The only thing that comes to mind is webmin.
[http://www.webmin.com/download.html](http://www.webmin.com/download.html)

---

### Post by JeppeM on 2009-01-18
I've seen a lot of good words on the forum about eBox, seems that ubuntu likes eBox better than webmin.

I haven't used either yet though, as i only just got set in charge of our office servers, but if i had to choose, i think that eBox would be it, after reading the recommendations in the posts around here...

Heres a small HowTo from HowToForge about eBox: [http://howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server](http://howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server) - You could start with that...

Otherwise, you can read much more about eBox here: [http://ebox-platform.com/](http://ebox-platform.com/)

Good luck, and keep us posted about how it goes...

---

### Post by albinootje on 2009-01-18
> **JeppeM said:**
> I've seen a lot of good words on the forum about eBox, seems that ubuntu likes eBox better than webmin.


I have used eBox several times, and I do *not* recommend it, it wants to take over your whole machine including network settings, I find it annoying.

If you only want to configure Samba and Apache, or NIS via a GUI remotely, then webmin is very interesting.

Since a few years webmin has disappeared from the Debian repositories, don't remember the reason for that.

---

### Post by redroad55 on 2009-01-18
Hi .. I believe on a simple note you can install desktop .. download and configure appropriate server pkgs. .. then back your way out leaving or shutting down what you no longer need .. best to you

---

### Post by lightningrod66 on 2009-01-18
I have installed and used webmin with ubuntu 8.10, and it seems to work very well for all your config needs.  It does a lot more than I thought it would at first.

---

