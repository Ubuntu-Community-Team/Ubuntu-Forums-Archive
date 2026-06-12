---
title: "Ok, now THAT was cool."
date: 2007-01-29
forum: Testimonials &amp; Experiences
---

### Post by muguwmp67 on 2007-01-29
A friend of mine gave me an old dell laptop (C510)  last week.  I decided to install ubuntu on it, but ran into a problem.  The laptop didn't have a cd drive, and my pc doesn't have a floppy.

I'm not a linux wizard and I'm just beginning with this stuff, but I decided to see if I could get the laptop to boot off of my home network and do a network install.  I figured it would take a day or two to get it working right, but I followed a couple of faq's out there, and it worked the first time!

I couldn't believe it.  Now I can take any network bootable laptop, plug it into my network and  replace windows with ubuntu with almost no effort.  Considering that most laptops more than 6 years old can't even think about running XP or Vista, 

I did run into one problem.  I installed the ubuntu destop instead of xubuntu.  Although gnome will run on a 700 mhz PC, it doesn't run very fast.  Xubuntu is downright zippy though.

---

### Post by kairu0 on 2007-01-29
I think use just violated your EULA with unauthorized install media... oh wait, you aren't using Windows ;)

---

### Post by muguwmp67 on 2007-01-30
Oh the EULA.  Isn't it funny how MS hits you with that on one hand, then charges 1000's to train and certify you on how to violate it?

Nevermind that though.  I spent a few hours last night setting up a wireless PCMCIA card on this laptop, and got it working.  I'm now in a local coffee show with free wifi.  

So someone gave me a 10 year old 'garbage' laptop for free, I've installed Xubuntu on that laptop, and can work wirelessly on it.

Considering how many 'garbage' machines are out there, and that the Windows Vista upgrade is going to create more, I'm  thinking that people should be pretty excited.

Everyone, adopt a laptop!  They're healthy and need good homes, are still kinda cute,  and if we don't adopt them, someone's gonna put them to sleep.

PS:  As I was typing this 'Come on, and take a free ride' started playing on the piped music system at the coffee shop.

PPS: I had this same laptop back in the day.  I was lucky if the battery lasted more than 2 hours.  This one lasts 4 on a full charge.  Perhaps the old battery was bad or something, but I'm telling people that its because linux uses less power.  Since there's less disk access due to better memory management, I'm not sure I'm altogether wrong.

---

### Post by happy-and-lost on 2007-01-30
Give [Debian.exe]("http://goodbye-microsoft.com/") or Ubuntu's [install.exe]("https://wiki.ubuntu.com/install.exe") a go whenever you're next faced with a machine with no removable media.

---

### Post by muguwmp67 on 2007-01-30
> **happy-and-lost said:**
> Give [Debian.exe]("http://goodbye-microsoft.com/") or Ubuntu's [install.exe]("https://wiki.ubuntu.com/install.exe") a go whenever you're next faced with a machine with no removable media.

I'll remember those options in the future, but they wouldn't have worked in this case.  The laptop had Windows NT installed with a password lock on it.  I doubt anyone would have known the user/pass information at this point.  Booting from the network allowed me to repartition and install without having to deal with any of this stuff, and it was easier to accomplish than getting the wireless card to work!

---

### Post by glabouni on 2007-01-30
> **happy-and-lost said:**
> Give [Debian.exe]("http://goodbye-microsoft.com/") or Ubuntu's [install.exe]("https://wiki.ubuntu.com/install.exe") a go whenever you're next faced with a machine with no removable media.

nice !

---

### Post by Zuuswa on 2007-01-30
Hm, which faq did you use?  This sounds like a better alternative to burning ubuntu cds for my friends

---

### Post by muguwmp67 on 2007-01-31
> **Zuuswa said:**
> Hm, which faq did you use?  This sounds like a better alternative to burning ubuntu cds for my friends

I started here:
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/install-tftp.html]("https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/install-tftp.html")

I found additional information at these sites:
[http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install]("http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install")
[https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall]("https://help.ubuntu.com/community/Installation/Netboot?action=show&redirect=PXEInstall")
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#DHCP_Server")

Remember to turn DHCP off on your router when you do this.  Note that installing through this means will only install ubuntu server, you will need to connect to the internet and use apt to retrieve (x)(k)ubuntu-desktop after the base install.

---

### Post by Zuuswa on 2007-02-02
Thanks!

---

