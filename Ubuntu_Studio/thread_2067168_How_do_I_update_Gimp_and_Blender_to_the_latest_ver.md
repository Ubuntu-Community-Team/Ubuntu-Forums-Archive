---
title: "How do I update Gimp and Blender to the latest version?"
date: 2012-10-06
forum: Ubuntu Studio
---

### Post by Astralogic on 2012-10-06
Hello, I'm a brand new user to Ubuntu Studio. I notice that Gimp and Blender are not up to date, could someone tell me how to update them please?

Thanks
Astralogic

---

### Post by smartboyhw on 2012-10-06
> **Astralogic said:**
> Hello, I'm a brand new user to Ubuntu Studio. I notice that Gimp and Blender are not up to date, could someone tell me how to update them please?

Thanks
Astralogic
Erm.....
```
sudo apt-get remove gimp
sudo apt-get update
sudo apt-get install gimp
```

BTW GIMP 2.8 is out.

---

### Post by jejeman on 2012-10-06
For blender I use version from official website, just unpack in home folder and use.
For GIMP easyiest way is to add PPA.
[http://www.noobslab.com/2012/08/install-latest-gimp-282-in-ubuntu.html](http://www.noobslab.com/2012/08/install-latest-gimp-282-in-ubuntu.html)
Both programs work good.

---

### Post by jerrrys on 2012-10-06
smartboyhw; fix that post  :)

If you use the gimp PPA be sure to completely remove the old gimp first.  Use the purge command

[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

And welcome to the forums  :)

---

### Post by Astralogic on 2012-10-09
To Smartboyhw: Those commands reinstalled the same version of Gimp as was uninstalled (2.6).

To Jejeman: I will do that if I can't successfully update the program I have installed.

To Jerrrys: That worked perfectly, do you know if there is a PPA (whatever that is) for Blender too?

Thanks
Astralogic

---

### Post by GeForce 9500GT on 2012-10-09
Else [take a look here ]("http://www.webupd8.org/2012/05/gimp-28-stable-finally-available-for.html")on how to update to the latest Gimp version.

---

### Post by Elfy on 2012-10-09
Generally, if you have not 

enabled backports
enabled proposed
added PPAs

removing and reinstalling will just get you what you had in the first place.

---

### Post by jerrrys on 2012-10-09
Glad to hear that Astralogic.

I also run gimp2.8 and know it works fine, but I do not run blender so I hope the ppa will work just as good.  A way to find PPA's:

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=blender+ppa&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=blender+ppa&as_qdr=all&sa=Google+Search&lang=en)

Also a good package to have installed when using ppa's is **ppa-purge:**

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ppa+purge&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=ppa+purge&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

I guess that you realize that ppa's are the latest release but not always stable.  The software center will have the approved/stable release of software.

Any questions?

---

