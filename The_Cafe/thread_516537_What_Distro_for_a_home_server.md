---
title: "What Distro for a home server?"
date: 2007-08-03
forum: The Cafe
---

### Post by jgrabham on 2007-08-03
OK, building a sort of server type thing out of old parts - 700MHz P3, 256MB RAM, etc.

Anyway - its main use will to be to store all my data, so I can access it on any computer in my house.

Also eventually want to put a DVD burner in it, for backups etc.

Im not that confidant with a command line, so Ill probably need a GUI.

So what distro??

Also where can I get a very small (10-12 inch) monitor for only a few quid.  An early 90s thing thats lurking in someones loft/garage is what I was thinking.

---

### Post by LaRoza on 2007-08-03
Maybe a server edition of Ubuntu with XFCE?

---

### Post by dca on 2007-08-03
I always recommend 6.06LTS....

---

### Post by jgrabham on 2007-08-03
> **LaRoza said:**
> Maybe a server edition of Ubuntu with XFCE?

Sounds complicated

---

### Post by LaRoza on 2007-08-03
Install Xubuntu as a server, run this command:

```

sudo aptitude install xubuntu-desktop

```

---

### Post by jrusso2 on 2007-08-03
Free NAS

[http://www.freenas.org/](http://www.freenas.org/)

---

### Post by AndyCooll on 2007-08-03
Well, my file server is pretty much those specs and I'm running Feisty on it (Had Dapper on before that). Runs great.

:cool:

---

### Post by qpieus on 2007-08-03
> **dca said:**
> I always recommend 6.06LTS....

I agree. 6.06 is very stable and doesn't have lots of updates anymore, which is fine for a server. You won't need the latest and greatest packages. XFCE (xubuntu) will certainly run fine on that pc, but if you are used to gnome, then go with regular old ubuntu. My server is about the same specs as yours and gnome 6.06 runs just fine.

Feisty will certainly run just fine as well, but then you'll have to consider upgrading when the next release comes out. IMO, for a server you don't need to upgrade every 6 months.

Another option if you want long term stability --->  Debian Etch.

---

### Post by Mathiasdm on 2007-08-03
Debian would do fine on that.

---

### Post by macogw on 2007-08-03
Just do a Dapper server install or use Debian Etch.

---

### Post by igknighted on 2007-08-03
CentOS/Fedora come with much better GUI admin tools for servers than Debian/Ubuntu servers do.  I would check out CentOS (RHEL, but free).  It is supported for several years like Ubuntu LTS as well.

---

### Post by reckless2k2 on 2007-08-03
i would agree that centos would be your best choice but documentation in these forums and other areas on the web are so profound with ubuntu. you will have to go to the command line but the ubuntu community has a lot of good hand holding tutorials. you probably would be good to go with 6.06.

---

### Post by matthinckley on 2007-08-03
why do you need a GUI for a server?

---

### Post by reclusivemonkey on 2007-08-03
> **matthinckley said:**
> why do you need a GUI for a server?

+1

If you need that sort of thing, just install webmin.

[http://www.webmin.com/](http://www.webmin.com/)

You don't really need a monitor either once you've installed.

---

### Post by rbprogrammer on 2007-08-03
> **reclusivemonkey said:**
> +1

If you need that sort of thing, just install webmin.

[http://www.webmin.com/](http://www.webmin.com/)

just out of curiousity, what do people say to not have a GUI installed on a server??

i have a home server, and it works great, especially with a gui (kubuntu).  i found that with the GUI i can administer it much faster when i am physically next to the computer.  although i still use webmin when i'm not around it..

---

### Post by igknighted on 2007-08-03
> **rbprogrammer said:**
> just out of curiousity, what do people say to not have a GUI installed on a server??

i have a home server, and it works great, especially with a gui (kubuntu).  i found that with the GUI i can administer it much faster when i am physically next to the computer.  although i still use webmin when i'm not around it..

If it is a high-traffic server (or if the load is high for any reason - e.g. older hardware) you might notice a speed difference between a server running a GUI and a server not running a GUI.  Otherwise, it is ourely preference.  Most home users will never tax the server heavily, so running a GUI is perfectly fine.  If you want a GUI but it slows the system down, you can install the GUI but not have load at boot.  This can be done be done several ways, the easiest is to just add a grub parameter to have it boot to runlevel three, then bump it to runlevel 5 when you want the full GUI.  Make sure that all your server processes are started at runlevel 3 though.

NOTE: If you use the Ubuntu server, i don't know what the appropriate runlevels are.  Ubuntu doesn't use standard runlevels for some reason.

---

### Post by macogw on 2007-08-03
> **igknighted said:**
> If it is a high-traffic server (or if the load is high for any reason - e.g. older hardware) you might notice a speed difference between a server running a GUI and a server not running a GUI.  Otherwise, it is ourely preference.  Most home users will never tax the server heavily, so running a GUI is perfectly fine.  If you want a GUI but it slows the system down, you can install the GUI but not have load at boot.  This can be done be done several ways, the easiest is to just add a grub parameter to have it boot to runlevel three, then bump it to runlevel 5 when you want the full GUI.  Make sure that all your server processes are started at runlevel 3 though.

NOTE: If you use the Ubuntu server, i don't know what the appropriate runlevels are.  Ubuntu doesn't use standard runlevels for some reason.

I think Ubuntu uses standard runlevels, just not the standard you're used to ;) Red Hat and Debian have different standards for runlevels.

---

### Post by reclusivemonkey on 2007-08-03
> **rbprogrammer said:**
> just out of curiousity, what do people say to not have a GUI installed on a server??

i have a home server, and it works great, especially with a gui (kubuntu).  i found that with the GUI i can administer it much faster when i am physically next to the computer.  although i still use webmin when i'm not around it..

I used to run a CS:Source server. I co do this happily in 128Mb of RAM. Add a GUI on top of that and I would of needed another 128Mb of RAM. Its just a waste of resources to me. You're free to run your server however you want, but to me a GUI and a monitor is a total waste. YMMV.

---

### Post by igknighted on 2007-08-03
> **macogw said:**
> I think Ubuntu uses standard runlevels, just not the standard you're used to ;) Red Hat and Debian have different standards for runlevels.

Actually I was refering to Slack.  However, any third party documentation (NVIDIA & ATI's driver install instructions for example) usually refer to Red Hat's runlevels, as well as all the books I have read.  I haven't used Debian itself much so I really couldn't tell you what runlevels it uses.

I actually started with Slack, which used runlevel 3 as default and it confused the hell out of me and it took me 3 days to get to a GUI.  Right there it was branded in my mind that runlevel 3 was full system, no GUI and 5 was everything (including GUI).  Ubuntu is the only distro I have used that I have noticed this not being the case, but I really haven't used any other debian-based distro long enough to know for sure.

What is the equivelent Debian runlevel for starting all services but not loading the GUI?

EDIT: And why would Debian use different runlevels than Slack, Suse, RedHat, etc... That makes no sense at all.  Anybody know the history behind why?

---

### Post by misfitpierce on 2007-08-03
6.06 Ubuntu for server

---

### Post by perspectoff on 2007-08-03
I disagree with all of the above. Feisty Server is way easier to set up than Dapper.

It has one click meta-package installation for both a LAMP server (which you definitely want) and for a DNS (BIND) server which you likely want.

Furthermore, it has the Drupal package available, which is the best Web site creation/management program available. 

Yes, you can use XFCE, but let me just say Blecch!

XFCE is very barebones and somewhat hard to configure for a new user.

It doesn't matter what desktop you install, anyway, if you are going to use the box as a server only -- you won't be using the desktop very much except for setup!

The overhead from Gnome when you aren't doing things on the desktop is zero -- duh!

But when you need desktop services, it's nice to have the Gnome capabilities. XFCE is tough to configure and customize.

Lastly, become familiar with XDMCP early on -- you can remotely administer your server over your LAN from another Ubuntu box.

Alternatively, you could use TightVNC (or UltraVNC from RealVNC) to view the server's desktop from a Windows box if you don't have 2 Ubuntu boxes.

You will be frustrated with Dapper. Go with Feisty or Gibbon (available October 2007).

---

### Post by Incense on 2007-08-03
Anyone have any good links or how tos for setting up a home server?

---

### Post by Marco Campos on 2007-08-03
Ubuntu 7.04 Server Edition. Installing everything and then use Remote Desktop or VNC to maintain it...

---

### Post by gabng on 2007-08-03
> **Incense said:**
> Anyone have any good links or how tos for setting up a home server?

Here're two that's nice
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)
[http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1](http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1)

---

### Post by Incense on 2007-08-03
> **gabng said:**
> Here're two that's nice
[http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1](http://www.bit-tech.net/bits/2007/06/05/build_your_own_server/1)
[http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1](http://www.bit-tech.net/bits/2007/07/24/build_your_own_better_server/1)

That's just what I was looking for! Thanks! :)

---

### Post by gabng on 2007-08-03
> **Incense said:**
> That's just what I was looking for! Thanks! :)

No problem!  It should help alot with all the screenshots. :)

---

### Post by M$LOL on 2007-08-03
> **reclusivemonkey said:**
> +1

If you need that sort of thing, just install webmin.

[http://www.webmin.com/](http://www.webmin.com/)

You don't really need a monitor either once you've installed.
That's exactly what I'm planning on doing.
> **rbprogrammer said:**
> just out of curiousity, what do people say to not have a GUI installed on a server??

Nah, then you need a monitor. Webmin 4tw.

---

### Post by igknighted on 2007-08-03
> **M$LOL said:**
> That's exactly what I'm planning on doing.

Nah, then you need a monitor. Webmin 4tw.

I typically do all my admin via SSH (usually putty from a windows machine sadly :(), but also keep a GUI on hand in case I want it (like to set up a virtual machine more easily).  I find webmin to be rather annoying, I much prefer to directly interact with what I am trying to change rather than have a middleman like webmin... it just introduces more of a chances for it not to turn out how I want it.

---

### Post by matthinckley on 2007-08-03
gutsy server will come with ebox! i'm excited!

---

### Post by boopyg on 2007-08-03
I would aim towards Ubuntu server edition because you are used to it, and you probably know the ins and outs of it too.

---

### Post by M$LOL on 2007-08-04
> **igknighted said:**
> I typically do all my admin via SSH (usually putty from a windows machine sadly :(), but also keep a GUI on hand in case I want it (like to set up a virtual machine more easily).  I find webmin to be rather annoying, I much prefer to directly interact with what I am trying to change rather than have a middleman like webmin... it just introduces more of a chances for it not to turn out how I want it.

Yeah, I see what you mean, although Webmin is handy if you can't hook up a monitor and you're depending on remote administration, and if Webmin doesn't work, then just go for SSH.

---

