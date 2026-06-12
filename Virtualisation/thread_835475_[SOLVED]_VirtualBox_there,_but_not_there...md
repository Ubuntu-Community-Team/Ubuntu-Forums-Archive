---
title: "[SOLVED] VirtualBox there, but not there..?"
date: 2008-06-20
forum: Virtualisation
---

### Post by Mecharuva on 2008-06-20
I uninstalled VirtualBox-OSE to try and install VirtualBox (the not-open-source version), and the non-OSE version never 'appeared',
I couldn't run it from anywhere.
So I used terminal to remove it,
And reinstalled VirtualBox-OSE.
But now, when I click it in the Applications menu, it won't run!
And I'm still getting to know Linux, so I don't know much about where things are in the folder system, or what file extensions to what.
Any help?

---

### Post by nunki on 2008-06-20
Try running 
```

VirtualBox

```

from a terminal and see if it reports any errors.

---

### Post by Mecharuva on 2008-06-20
Oh yeah.
I tried that.
I get:
```
Could not find VirtualBox installation.  Please reinstall.
```
And I have reinstalled it 5 or six times now.

---

### Post by nunki on 2008-06-20
Download it [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI"). Choose the appropriate ubuntu download from the dropdown list. Then 
```

sudo dpkg -i <whatever the .deb name was>

```

---

### Post by pixel :-) on 2008-06-20
maybe your .VirtualBox directory is broken.Rename it and see what happens.If it works import your old virtuall machines in the new one.

---

### Post by Mecharuva on 2008-06-20
I deleted the .virtualbox directory once already.
I didn't have any machines.
I'll try that download, nunki.

---

### Post by Mecharuva on 2008-06-23
Thanks nunki, it worked.
Now I have a hard drive problem I've gone and brought on myself,
Trying to make more space for Ubuntu :P

---

### Post by barried on 2008-08-29
> **nunki said:**
> Download it [here]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI"). Choose the appropriate ubuntu download from the dropdown list. Then 
```

sudo dpkg -i <whatever the .deb name was>

```


This works well, thanks nunki :guitar:

---

### Post by marlonbr on 2008-11-17
Hello! Just got in the SAME situation and solved it by just doing a COMPLETE REMOVAL on the virtualbox-ose package, on synaptic, and then installed it again,

Hope it helps, =)

---

### Post by theApokalypsis on 2009-01-26
> **marlonbr said:**
> Hello! Just got in the SAME situation and solved it by just doing a COMPLETE REMOVAL on the virtualbox-ose package, on synaptic, and then installed it again,

Hope it helps, =)

I cant believe I didnt do this in the first place. talk about being lazy!

:lolflag:

---

### Post by syn4k on 2009-05-05
> Hello! Just got in the SAME situation and solved it by just doing a COMPLETE REMOVAL on the virtualbox-ose package, on synaptic, and then installed it again,

Hope it helps, =) 

I tried that...and it didn't work. lol.
Downloading the older version for 8.04 (which is the latest version on the website right now) and then following nunki's advice did work though.

Here is the command that I did which did NOT work:
sudo apt-get -y remove virtualbox-ose && sudo apt-get -y autoremove && sudo rm -rf ~/.VirtualBox

---

### Post by bin2hex on 2009-06-25
This is how I resolved it

created an /etc/vbox/vbox.cfg and put this inside
```

# VirtualBox installation directory
INSTALL_DIR="/usr/lib/virtualbox"

```

---

### Post by amr2205 on 2010-09-09
Thanks! It worked for me.

---

