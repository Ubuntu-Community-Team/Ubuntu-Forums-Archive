---
title: "Installing F-Prot"
date: 2007-01-18
forum: Server Platforms
---

### Post by Man_Beach on 2007-01-18
I dual boot Windows 98 and Ubuntu Edgy. I'd like to install f-prot so that I can do the occasional virus scan (both the windows partition and my home directory). (I used to do this every month or so when I was dual booting Windows & SuSE.)

Should I install via synaptic or download the Debian/GNU package (4.6.7)  from f-prot's website?

---

### Post by jtc on 2007-01-18
> **Man_Beach said:**
> Should I install via synaptic or download the Debian/GNU package (4.6.7)  from f-prot's website?

I assume you refer to the *f-prot-installer* package? Well, I don't think it does much difference, since that package is simply a script which downloads f-prot from their ftp-site and installs it for you.

Basically it comes down to personal preferens. If nothing else, to use Synaptic is probably slightly easier, and you get some magic done. According to the package description you get these scripts setup.

>  This package also comes with a maintenance script to keep your F-Prot(tm) installation up-to-date. Furthermore a cron script for automatic virus definition updates is included.

---

### Post by Josh1 on 2007-01-18
Downloading from the site is usually better I find, since it might have a more updated version then found in apt.

---

### Post by jtc on 2007-01-18
> **Josh1 said:**
> Downloading from the site is usually better I find, since it might have a more updated version then found in apt.
Well, generally true, but in this case the apt-version is simply a script which downloads the latest version from the site.

---

### Post by Man_Beach on 2007-01-19
> **jtc said:**
> I assume you refer to the *f-prot-installer* package? Well, I don't think it does much difference, since that package is simply a script which downloads f-prot from their ftp-site and installs it for you.

Basically it comes down to personal preferens. If nothing else, to use Synaptic is probably slightly easier, and you get some magic done. According to the package description you get these scripts setup.

I didn't realise that the f-prot installer was just a script (still new to the Debian world and the way it works). I just checked the 'All Debian Packages in edgy' list and noticed that there was an f-prot installer package.

I'll try Synaptic and see how it goes. Might be safer while I'm still finding my way around.

Thanks.

---

### Post by jtc on 2007-01-19
> **Man_Beach said:**
> I didn't realise that the f-prot installer was just a script (still new to the Debian world and the way it works).
Dealing with propertarian software, no matter if it at no cost, can involve lots of legal issues. Usually one of the keystones is regarding the rights to distribute. You'll see the same setup when it comes to the nonfree flashplayer, Microsoft fonts, etc.

---

### Post by gg234 on 2007-01-19
Try this [step by step fprot installtion guide]("http://www.ubuntugeek.com/f-prot-antivirus-with-xfprot-web-interface.html")

I hope this helps

---

