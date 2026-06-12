---
title: "Not sure if this is an Issue - what version am I running?"
date: 2013-03-10
forum: Ubuntu Development Version
---

### Post by Quarkrad on 2013-03-10
I did a clean install of 13.04 about a month ago and all is OK - I do the updates when the update windows pops up.  (This is a new machine and for some reason 12.04/12.10 did not like the graphics  (on board intel chipset)). I was under pressure from my wife to 'get her pc back' so tried 13.04 - it went like a dream and although I knew it was not official it has run like a dream. (Mainly used for email/surfing/libreoffice).  Pic1 shows indeed that it is 13.04 - however, today a System Reporting window popped up and indicated that this is a 12.10 machine - see pic 2.  I put this down to 13.04 no yet being official - I take it that this is not an issue.

---

### Post by VinDSL on 2013-03-10
There are many different ways of determining versions.

Here's what I would use (from CLI)...

```
echo && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo
```


As long as it looks similar to this, everything should be okay. ;)

```
vindsl@Zuul:~$ echo && echo -n "Distro Release: " && lsb_release -sd && echo -n "Kernel Release: " || cat /etc/*release && uname -s -r && echo -n "Gnome Release: " && gnome-shell --version && echo -n "Unity Release: " && unity --version && echo && /usr/lib/nux/unity_support_test -p -f && echo

Distro Release: Ubuntu Raring Ringtail (development branch)
Kernel Release: Linux 3.9.0-030900rc1-generic
Gnome Release: GNOME Shell 3.7.91
Unity Release: unity 6.6.0

OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 7600 GT/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 304.84

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

vindsl@Zuul:~$ 

```

---

### Post by grahammechanical on 2013-03-11
You could also try 
```
lsb_release -a
```
You should get something like this. 
> No LSB modules are available.Distributor ID:	Ubuntu
Description:	Ubuntu Raring Ringtail (development branch)
Release:	13.04
Codename:	raring


Remember, at the present time all new releases are built upon the code from the last release. So, the Raring development branch code started out as Quantal (12.10) code. In fact for many weeks every label we saw said "12.10". I am wondering if the USB printer library that caused the crash is still a 12.10 library and that is why Apport is reporting 12.10 as having crashed. I have not seen a crash message for a few days. But I think that Apport is reporting 13.04 on my machine when it does put out a crash message.

Regards.

---

### Post by Quarkrad on 2013-03-11
Interesting.  The first command gave me:

Distro Release: Ubuntu 12.10
Kernel Release: Linux 3.5.0-24-generic
Gnome Release: GNOME Shell 3.6.2
Unity Release: unity 6.12.0


The 2nd command from Graham gives me:

LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.10
Release:	12.10
Codename:	quantal


I just looked at About this Computer and it tells me 13.04

---

### Post by grahammechanical on 2013-03-11
Now that is most weird. And unexplainable. Even a month old ISO image should have had the kernel 3.7 if not 3.8. Updates should have brought all that in. My present Raring install started out as a 12.10 install and it is quiet clearly 13.04.

You could try opening what should be called Software and Updates but might be called Software Sources on your System and check that the repositories are actually Raring and that you have all of them ticked.

Oh, It is not an issue if the OS is working as you want it to work.

---

### Post by mc4man on 2013-03-11
> **Quarkrad said:**
> Interesting.  The first command gave me:

Distro Release: Ubuntu 12.10
Kernel Release: Linux 3.5.0-24-generic
................................
Unity Release: unity 6.12.0



I just looked at About this Computer and it tells me 13.04
That's what you'd expect to see in 12.10, if this was an upgrade vs. fresh install then could be just some info wierdness
(other than the kernel version

this would tell you what unity is installed, should be a daily (currently 6.12.0daily13.03.11-0ubuntu1
```
apt-cache policy unity
```

If this is an upgrade & you upped with & now have raring-proposed enabled you may have not gotten the 3.8.x kernel as it wasn't complete package wise yet. (should be complete now, latest avail. here is 3.8.0.12.26 from -proposed

---

### Post by Quarkrad on 2013-03-11
liz@lizubuntu:~$ apt-cache policy unity
unity:
  Installed: 6.12.0-0ubuntu0.2
  Candidate: 6.12.0-0ubuntu0.2
  Version table:
 *** 6.12.0-0ubuntu0.2 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     6.8.0-0ubuntu2 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages


OK I think I've sorted it following Graham's post.  Everything in the sources lists in the software Centre settings refer to quantal - so although I did a clean install of 13.04 I guess this is a sort of quantal machine.  I am a bit of a newbie - not sure why I have no Raring entries.   As this is my wifes machine and is running OK I do not know what to do.  Try and sort out/change the quantal entries to Raring or leave it.   Post April 2013 what sort of Ubuntu machine will this be (?) 13.04 or stay as it seems at the moment, 13.04 but with quantal repostories?

---

### Post by grahammechanical on 2013-03-11
There is a command that will simply change the repositories from Quantal to Raring. We use it when we want to start testing the next Ubuntu release under development. I used it to create the Raring install that I am using right now.

```
sudo sed -i 's/quantal/raring/g' /etc/apt/sources.list
```
followed by
```
sudo apt-get update && sudo apt-get dist-upgrade
```

That should bring the repositories in line. Otherwise, I suggest that you wait until May 2013 and upgrade to 13.04. If you set Software Sources to notify you of the next version of Ubuntu, then you will get notified when 13.04 is officially released. Regards.

---

### Post by mc4man on 2013-03-11
> **Quarkrad said:**
> 

OK I think I've sorted it following Graham's post.  Everything in the sources lists in the software Centre settings refer to quantal - **so although I did a clean install of 13.04** I guess this is a sort of quantal machine.  I am a bit of a newbie - not sure why I have no Raring entries.   As this is my wifes machine and is running OK I do not know what to do.  Try and sort out/change the quantal entries to Raring or leave it.   Post April 2013 what sort of Ubuntu machine will this be (?) 13.04 or stay as it seems at the moment, 13.04 but with quantal repostories?

While doing a sources.list upgrade now might work out ok I probably wouldn't so do unless prepared to do fresh install of 13.04 in case it goes south  **if** all is working ok for your wife's uses. (& hopefully with better results then last time, however you went about that??

The only package you've posted about to date that appears to be raring is shown via the 'Details' window, otherwise unity, kernel, hplip-data are all quantal. How you got a raring gnome-control-center version & what, if any, other raring packages is quite unknown.

Would be curious about this - 13.04 was added to Details (gnome-info-panel),  in 1:3.6.3-0ubuntu8 (Nov. 26), current is  1:3.6.3-0ubuntu13
```
apt-cache policy gnome-control-center
```

---

### Post by Quarkrad on 2013-03-12
The output of the command is:

liz@lizubuntu:~$ apt-cache policy gnome-control-center
gnome-control-center:
  Installed: 1:3.6.3-0ubuntu11~ubuntu12.10.1
  Candidate: 1:3.6.3-0ubuntu11~ubuntu12.10.1
  Version table:
 *** 1:3.6.3-0ubuntu11~ubuntu12.10.1 0
        500 [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
     1:3.4.2-0ubuntu19.1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal-proposed/main amd64 Packages
     1:3.4.2-0ubuntu19 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages


I don't know how I got these quantal updates with a clean install of 13.04 but as the machine is working OK I will take your advice and leave it until May and do a clean install.  Thank you both for your help.

---

### Post by dino99 on 2013-03-12
watch your: sudo gedit  /etc/apt/sources.list

or maybe there are some old ppa(s) around (use synaptic for ease)

---

### Post by mc4man on 2013-03-12
What you have is actually a **12.10 install with the gnome3 ppa for quantal**. For some reason they built a new gnome-control-center for quantal but included the Ubuntulogo.png for raring.

So everything should be ok & quantal based other than this small mistake on someones part

screen shows a _new 12.10 install with only g-c-c updated from the ppa_, Details says I have 13.04

---

