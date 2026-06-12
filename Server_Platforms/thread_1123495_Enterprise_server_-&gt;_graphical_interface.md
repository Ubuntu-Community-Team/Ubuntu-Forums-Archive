---
title: "Enterprise server -&gt; graphical interface"
date: 2009-04-12
forum: Server Platforms
---

### Post by Findarato on 2009-04-12
Hello,

I have recently tried to install a complete server environnement for my business using ubuntu desktop. This did not go very well though and much has to be done through a terminal.

I would like to know if there is a distribution (or simple package), giving me graphical interfaces to install and configure a server with the following:

- e-mail client
- web server
 - ftp
- multiple accounts with different rights on the web server
- etc.

The goal is to get my business (web & software development) up and running with the tools it needs, configurable by myself (a linux intermediate) through graphical interfaces.

Thank you very much for your help :)

---

### Post by hyper_ch on 2009-04-12
on a server you don't want a graphical interface

have a look at the perfect server howtos by falko on [http://www.howtoforge.com](http://www.howtoforge.com) (especially also the ispconfig 3 one)

---

### Post by HermanAB on 2009-04-12
Howdy,

If you want wizards, then Ubuntu is the wrong distribution for you.  The more mature distributions like Mandriva and Suse have wizards for *everything*:
[http://forum.mandriva.com](http://forum.mandriva.com)

Using the Mandriva wizards, you can set up everything you need with a few mouse clicks.  However, the advanced Mandriva server wizards are hidden from newbies - you got to install 'drakwizard' and then you'll be in click-heaven.

Unfortunately wizards are anathema to many staunch Ubunto supporters, but despite their best efforts at holding back the tide, the number of wizards in Ubuntu is slowly growing.

---

### Post by cariboo on 2009-04-12
Have a look at this [document]("http://help.ubuntu.com/community/ServerGUI"), for Ubuntu's stand on gui's on a server.

Jim

---

### Post by hyper_ch on 2009-04-12
> **cariboo907 said:**
> Have a look at this [document]("http://help.ubuntu.com/community/ServerGUI"), for Ubuntu's stand on gui's on a server.

Jim

I didn't know that link before :) great finding :) *bookmark*

---

### Post by HermanAB on 2009-04-12
Yes, I do agree with some of the security issues behind running a GUI on a server, yet I use Mandriva for work and Unbuntu for fun, since I just cannot aford to waste time setting up servers the hard way.

However, once the server is running, I change to runlevel 3.  I only pop into runlevel 5 while configuring stuff using the local console - if it has one.  

Ubuntu is slowly crawling in that direction too and the wizards on Ubuntu are improving, but they are many years behind Mandriva and Suse.

BTW, the argument against running X on a server dates back to the time when X was listening by default on port 6000.  That hasn't been the case for the past 10 years or more so the old boogyman is really just a bad excuse for not having proper wizards!

---

### Post by chrisjsmith on 2009-04-12
You can use stuff like webmin though  :)

[http://webmin.com/](http://webmin.com/)

---

### Post by ugm6hr on 2009-04-12
In theory, ebox does all this.

I only dabbled with it briefly, but it is available as v1.0 (Hardy base) now, so hopefully does what it says on the tin!

[http://ebox-platform.com/product/](http://ebox-platform.com/product/)

---

### Post by Iowan on 2009-04-12
Did **ebox** get fixed? The [help]("https://help.ubuntu.com/community/eBox") page suggests:> WARNING: the eBox package released with Ubuntu 8.10 (Intrepid Ibex) is broken and cannot be installed. See bug #255368 for information and unsupported workarounds....but it suggests:> The eBox version released for Ubuntu 8.04 (Hardy Heron) is much more functional.

---

### Post by dguitar on 2009-04-12
GUIs and wizards should never have a place in Enterprise servers. If you want to run a home / project server, great use GUIs, wizards, or whatever automated crap you want to. If you want harden, enterprise level servers, hire someone.

---

### Post by Bite_me_Bill on 2009-04-13
> **dguitar said:**
> GUIs and wizards should never have a place in Enterprise servers. If you want to run a home / project server, great use GUIs, wizards, or whatever automated crap you want to. If you want harden, enterprise level servers, hire someone.

I couldn't agree more.

---

### Post by ugm6hr on 2009-04-13
> **Iowan said:**
> Did **ebox** get fixed? 

I'd suggest just using the 8.04 version on their PPA, or directly using their ebox live-installer.

I did manage to get their 8.10 PPA files to install and work on an 8.10 server, but honestly can't remember what I did.  Pretty sure I just used this repo:     ```
deb http://ppa.launchpad.net/ebox-unstable/ubuntu intrepid main
```

---

