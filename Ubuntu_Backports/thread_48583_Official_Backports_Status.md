---
title: "Official Backports Status"
date: 2005-07-13
forum: Ubuntu Backports
---

### Post by Mez on 2005-07-13
Hi all!

I just thought I'd give you a bit of info on the status of the "official" backports.

Basically, all the buildd's are in place, and we've had the go ahead for us to start requesting backported packages :D There's currently no infrastructure in place for us to start backports manually, so either me or John have to email James Troup and ask him to start the build going.

Here's the list of what I've requested to be autobuilt so far.

wesnoth				0.9.3-1
cogito				0.11.3+20050610-1
streamtuner			0.99.99-5ubuntu1
gtk-sharp2-unstable		1.9.5-1ubuntu2
psyco				1.4-1ubuntu1
freeciv 			2.0.2-1
bittornado			0.3.11-4ubuntu1
asciidoc			7.0.0-1
xchat-systray			2.4.5-2
liferea				0.9.1-1
firestarter			1.0.3.1-1
planner				0.13-0.4
drpython			3.10.13-1
gwget2				0.95-2
tla				1.3-1ubuntu1
seahorse			0.7.8-2
clamav				0.85.1-0ubuntu2
gaim-encryption			2.37-1
cli-common			0.1.3ubuntu1
nautilus-open-terminal		0.2-1ubuntu1
gramps				2.0.5-1
ltsp				0.43
nvu				0.99+1.0pre-1build1
openvpn				2.0-3
revelation			0.4.3-2
tor				0.1.0.11-1
java-package			0.24
amule				2.0.0-1
gnome-ppp			0.3.21-1
abiword				2.2.7-3ubuntu4
gimp				2.2.8-2ubuntu1
doxygen				1.4.3-20050530-1.1
gaim				1:1.4.0-1ubuntu1
firefox				1.0.4-1ubuntu3
mozilla				2:1.7.8-1ubuntu2
totem				1.1.2-0ubuntu4
file-roller			2.11.2-0ubuntu1
xchat				2.4.4-0ubuntu1
acroread			7.0.0-9
konversation			0.18-1ubuntu2
zile				2.0.4-2
drivel				2.0.1-1
easytag				1.99.6-2
clearlooks			0.6.2-1
serpentine			0.6.1-0ubuntu3 
smeg				0.7.5-0ubuntu1
mypasswordsafe			0.0.20041004-2build1
electricsheep			2.6.2-1
webmin				1.210a-2
webmin-optional			1.210a-2
graveman			0.3.12-4-2
xmule				1.10.0b-1build1

I'm also going to be checking over and getting all the new KOffice1.4 and KDE3.4.1 stuff put into backports (and KDE 3.4.2 should then hopefully go straight to backports aswell)

If you have a request we add something to the official archives, please post it here and we'll send a list off to James Troup when we get it big enough.

For those interested - the next Community Council will discuss the formation of the "Official" Backports team, so if you want to keep up to date, be there,

At the moment we're waiting for the Test packages to be taken out of the Official Repositories :D so once that's done we'll post details on how to add them

Also, just as an FYI, you can use a country specific archive for backports aswell (for example - gb.archive.ubuntu.com) though it's optional for each mirror if they want to carry backports or not, so you may want to check they do first!

Have fun all

---

### Post by yusufk on 2005-07-18
Whats the URI for the official backports? Will appreciate the apt line (deb http:.....)

Thanks
Yusuf

---

### Post by bored2k on 2005-07-18
[QUOTE=yusufk]Whats the URI for the official backports? Will appreciate the apt line (deb http:.....)

Thanks
Yusuf[/QUOTE]
 [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)
> 
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

---

### Post by fishfork on 2005-07-18
That's the old URL, isn't it? I understood that the backports project was going to move onto the official servers (i.e. something.ubuntu.com) at some point. Am I right?

---

### Post by LaSSarD on 2005-07-19
No, the old repositories were:
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports/](http://backports.ubuntuforums.org/backports/) hoary-extras main universe multiverse restricted

Now MirrorMAX is official.
[http://www.ubuntuforums.org/showthread.php?t=40291](http://www.ubuntuforums.org/showthread.php?t=40291)

---

### Post by Mez on 2005-07-19
No, the ubuntu backports project WILL be moving to xx.archive.ubuntu.com

HOWEVER, at the moment, there are only "test" packages on there, so for now, we are not giving out details regarding those, as it may cause breakages

---

### Post by pelago on 2005-10-04
Hey, could this thread be unstickied now? Seeing as we have the Official Backports Launched thread stickied too

---

