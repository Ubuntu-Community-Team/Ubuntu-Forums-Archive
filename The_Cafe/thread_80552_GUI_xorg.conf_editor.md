---
title: "GUI xorg.conf editor"
date: 2005-10-14
forum: The Cafe
---

### Post by vvlist on 2005-10-14
On some systems, (including my IBM T40 laptop) hardware rendering is not enabled. It would be very 'handy' if there was a x.org configuration dialog built into ubuntu's GNOME. [GXConf]("http://www.gnomefiles.org/app.php?soft_id=1081") is a step in the right direction. Let me add that this dialog could include resolution switching, color depth, dual monitor support, compositing, etc. I really hope a developer sees this, because this is a feature that would greatly improve Ubuntu's desktop.

---

### Post by luckyaba on 2005-10-14
dpkg-reconfigure xserver-xorg

has most of the feature your looking for

---

### Post by idn on 2005-10-14
[QUOTE=luckyaba]dpkg-reconfigure xserver-xorg

has most of the feature your looking for[/QUOTE]

But in a gtk app would be good, no need to touch the command line.

I think this would be a very good idea.

---

### Post by vvlist on 2005-10-14
[QUOTE=luckyaba]dpkg-reconfigure xserver-xorg

has most of the feature your looking for[/QUOTE]

I am aware of this method. I've used it many a time. But I'm saying would be nice if there was a non-command line equivalent of this method. And little features like it would attract more users to the Ubuntu linux platform.

---

### Post by poofyhairguy on 2005-10-14
I think this is the biggest missing feature.

---

### Post by vvlist on 2005-10-14
How can we notify developers about this missing feature?

---

### Post by poofyhairguy on 2005-10-14
[QUOTE=vvlist]How can we notify developers about this missing feature?[/QUOTE]


I have been thinking about this a lot. I don't thing bugzilla is enough. I almost want to start a petition. At the very least, make a wiki page.

---

### Post by luckyaba on 2005-10-14
[QUOTE=vvlist]I am aware of this method. I've used it many a time. But I'm saying would be nice if there was a non-command line equivalent of this method. And little features like it would attract more users to the Ubuntu linux platform.[/QUOTE]


I getcha... misunderstood sorry.

that is a really good idea when i think about it though...

---

### Post by idn on 2005-10-14
Try to make it onto the goal list for dapper?

---

### Post by GeneralZod on 2005-10-15
[QUOTE=poofyhairguy]I have been thinking about this a lot. I don't thing bugzilla is enough. I almost want to start a petition. At the very least, make a wiki page.[/QUOTE]

I'm almost certain that it was being worked on already as part of the XRoadMap, but can't find an exact map link now :(

The idea would be that a failure to start X would be detected, in which case the X settings would be decreased (e.g. dropping down to vesa) until an X configuration at least worked, at which point a GUI for configuring X would be presented.

Edit:

[This](https://wiki.ubuntu.com/XConfigurationModification?highlight=%28DistroSpec%29) and [this]("https://wiki.ubuntu.com/XorgAutoconfiguration")  are the best I could find.

---

### Post by duffman25 on 2005-10-15
[QUOTE=poofyhairguy]I have been thinking about this a lot. I don't thing bugzilla is enough. I almost want to start a petition. At the very least, make a wiki page.[/QUOTE]

I think the best place for a petition would be here:
[https://wiki.ubuntu.com/UbuntuBelowZero/BOFs](https://wiki.ubuntu.com/UbuntuBelowZero/BOFs)

This is a bit undocumented in the wiki (at least for someone that's new to ubuntu & linux/debian development in general), maybe we should include a wiki page called
"development of the next ubuntu" (or something like that) which talked & explained how the bof's & the conferences (UDU & UBZ) work & how the dev's create the specifications for the next ubuntu version. Then a link to the current bof's page & the next conference. 

Right know you have to understand what is a BOF & what is the next conference to add suggestions for it.

---

### Post by az on 2005-10-15
[QUOTE=vvlist]I am aware of this method. I've used it many a time. But I'm saying would be nice if there was a non-command line equivalent of this method. And little features like it would attract more users to the Ubuntu linux platform.[/QUOTE]

Synaptic - package - configure

Pick the xserver-xorg package and you can config it graphically that way.

The problem is that some hardware does not let you autodetect it while you are running it.  So the best (sure-fire) way to reconfigure x is from a command-line while no X session is running.

---

### Post by sijp on 2005-10-16
a few months ago I played with python and glade, and made something that was supposed to help configure xorg (using debconf). I kinda neglected it :oops:, it was just for fun anyway... :)
I talked about it here: [http://ubuntuforums.org/showthread.php?t=49434](http://ubuntuforums.org/showthread.php?t=49434)

here is a link for those who are interested, it doesn't do much [yet?], except importing some data from debconf. (beware of the configure button, it will open the debconf wizard for configuring xorg and if it is run with sudo might make changes, everything else about the wizard will have no effect).

[http://sijp.no-ip.info/files/XdotConf.xorg.tar.bz2](http://sijp.no-ip.info/files/XdotConf.xorg.tar.bz2)

just unpack and run the xDotConf.py script.

it should be run as root, though if you just want to see the gui, you can run it as a normal user (but most [if not all] data import from debconf will not succeed).

---

### Post by jetpeach on 2005-10-21
I also believe strongly that at least some additional GUI configuration tools need to be available for adjusting resolutions and, in particular, refresh rates.  I always forget how to fix the 60hz resolution after I install Ubuntu and spend 15 minutes before I get it right at 75hz... I hope this makes it into Dapper.
jet

---

### Post by Velvet Elvis on 2005-10-22
I gotta agree with this one.

After suffering for years at 600x800, my antique monitor fried a few days after final 5.10 release.  Getting the higher resolutions to work on my new monitor was a PITA.   Does Xorg have anything like the old xf86config?  I couldn't find it.  As someone who has recently switched over from slackware, I've found debconf quite unintuitive.  I kept looking for some kind, any kind, of Xorg configuration utility that came packaged with X.  It was only after reading the man pages for every single executable in /usr/X11R6/bin that I thought to try debconf.  Had there been an easy to use GUI for this, I'd have used it.  

I think it's a mistake for the Ubuntu devs to assume that Ubuntu won't be winning converts from the non-debian hardcore distros.  Knowing how to use linux and knowing how to use debian are two different things.  A 1k text file in /etc/X11 saying "psst, use debconf" would have saved me hours.

---

### Post by teevee on 2005-10-22
Yeah, we have graphical config tools for all kinds of stuff, but only few are as important as a graphical X.org config would be.

---

### Post by cbudden on 2005-10-22
Does anyone know if this is in the pipeline for Ubuntu?

---

### Post by poofyhairguy on 2005-10-22
[QUOTE=cbudden]Does anyone know if this is in the pipeline for Ubuntu?[/QUOTE]


I don't think it is. Which is a shame, I think its the most needed thing to add.

I have been thinking about it for weeks. I want to find someway to rally forum users around this so we can make sure it get on the agenda. Lets use this thread as a way to brainstorm.

Operation Force the Ubuntu Developers to Make a Xorg Tool.

---

### Post by somuchfortheafter on 2005-10-22
if my programming skills were better it may be possible to do relatively quickly in python using either gtk2 or wxwidgets...

---

### Post by Lovechild on 2005-10-22
One thing to be considered, why do we need that file in the first place.. could one not move X.org over to use HAL to autoconfigure it's settings?

That being said, I'm a proponent of Elektra (a uniform configuration framework), so at least using that a gui editor for any configuration file would be trivially easy to make.

---

### Post by Anthem on 2005-10-22
Why doesn't Ubuntu just use Sax?  Or is it another case of Not Invented Here?

---

### Post by GeneralZod on 2005-10-22
A couple of pertinent links:

[https://wiki.ubuntu.com/XConfigurationModification?highlight=%28DistroSpec%29](https://wiki.ubuntu.com/XConfigurationModification?highlight=%28DistroSpec%29)
[https://wiki.ubuntu.com/XorgAutoconfiguration](https://wiki.ubuntu.com/XorgAutoconfiguration)

---

### Post by ubuntu_demon on 2005-10-22
I merged a similar xorg.conf gui thread into this one

---

### Post by poofyhairguy on 2005-10-22
[QUOTE=Lovechild]One thing to be considered, why do we need that file in the first place.. could one not move X.org over to use HAL to autoconfigure it's settings?[/QUOTE]

Because HAL is not ready, and that plan would take a few releases to be finished. It would be nice to have a way to do this more easily than the command line by Dapper.

Plus, a huge reason for it is multiple monitor support, and I don't think anyone has figured out how to detect that second monitor automatically. Plus it would be nice for the tool to be able to "turn on" the Nvidia and ATI drivers and HAL couldn't do that. We have to use the command line to do that now.

I mean, your plan is a great one for the future but we need something today! We are having to use a Debian command line tool as it is!

---

### Post by poofyhairguy on 2005-10-22
[QUOTE=Anthem]Why doesn't Ubuntu just use Sax?  Or is it another case of Not Invented Here?[/QUOTE]

Because Sax is made with QT and Ubuntu is a Gnome distro. Using Sax would require loading the KDE libs in Ubuntu. That is not the answer.

---

### Post by Lovechild on 2005-10-22
[QUOTE=poofyhairguy]Because Sax is made with QT and Ubuntu is a Gnome distro. Using Sax would require loading the KDE libs in Ubuntu. That is not the answer.[/QUOTE]

That and SAX is complete arse

---

### Post by Innomen on 2007-10-24
This same debate is being had in a different way on other threads. The demand is for a GUI device manager. 

My problem is I want to disable my touchmouse, or edit it, but I keep running into the "you should be born understanding xorg.conf and if you don't like command like you're stupid" wall.

I'm thinking you guys should try to integrate them. GUI everything, is what I say. "linux for people" not "linux for admins/developers/coders" 

The usual "well go learn linux command line NEWB or get windows/mac" doesn't apply here. THIS linux is for us, if YOU want to be Nerdcore, YOU go to some other flavor of linux.

Some experts like GUI too.

---

### Post by azkehmm on 2007-10-24
> **Innomen said:**
> 
 THIS linux is for us, if YOU want to be Nerdcore, YOU go to some other flavor of linux.

Some experts like GUI too.

Let the ones who want to be "nerdcore " (good word, btw :)) be that, and use the command line. Make a GUI tool for the human beings ;)

---

### Post by 23meg on 2007-10-24
Nice bump.

---

### Post by conehead77 on 2007-10-24
I used dpkg-reconfigure xserver-xorg and i have to say i never really knew what i did there.
If there is no GUI tool (where you would be able to search for additional information via firefox) there should be at least a good explanation of each step in the tool itself.

---

