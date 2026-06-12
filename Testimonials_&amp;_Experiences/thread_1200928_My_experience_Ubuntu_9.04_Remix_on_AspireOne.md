---
title: "My experience Ubuntu 9.04 Remix on AspireOne"
date: 2009-06-30
forum: Testimonials &amp; Experiences
---

### Post by markosjal on 2009-06-30
I recently had a friend with a crashed windows Netbook. Because her boss uses the machine in English and her in Spaniosh, I installed Ubuntu 9.04 netBoox remix so they could both understand it on their native language.

I post here my experience so far. Do not flame me for posting here as i refuse to make separate posts in each area, as my timne is tioo inmportant and I want to paint the bigger picture for those who want to know what they are getting into.

When using the launcher some firefox windows have no 'x' to close them. You can see and exaple of this if you go to [www.kvta.com](www.kvta.com) and click on "listen live" 

If the Launcher is turned off no menus appear. Just the wallpaper and documents saved to the desktop the Hotkey for ubuntu menu does not work either (alt f1 I think it is). The only way I got around this was a reinstall

Links to media streams such as [http://67.19.107.122:9000/listen.pls](http://67.19.107.122:9000/listen.pls) appear to be unsupported by any plug in. if you go to [http://67.19.107.122:9000](http://67.19.107.122:9000) and click on "listen" it should open as it does wigth VLC or WinAmp in windows. In  ubunto there seems to be nothiong thst supports this kind of link. I have installed a multitude of plug ins , and codecs , and still the only way I can get there is from Tunapie and the player associated there or by entering the URL in VLC, both of which are too tedious when you have a direct link

AT times the launcher which is necessary to use based on what  indicated earlier, shows icons pon top of icons and there appears to be no way to rearrange them.

The language selection at login asks too many stupid questions about changing folder names and making changes permanent EVERY  time a different language kis selected regardless of user. This preference should be on a per user basis.

Launcher in spanish says "rojo" where it should say "red" meaning "network" go figure that is odd.

deleting a user does not delete the associated group which was probably created when   the user was created. Tjis means if a user has a problem yu can not simply delete and recreate the account from the GUI

SUN Java and Flash are available for installation and in my opinion should optionally install by default, as without them a web browser is incomplete

Third party repositories should appear in synaptic for easy activation.(with whatever warning you see fit)

I have never got the track pad to work necessittating the use of external mouse. None of the solutions I have seen make it work. Including hot key etc

External Panasonic Wide screen 44inch monitor is not recoghnized and resolution defaults to 4x3 aspect ratios. This is a horrible oversight that we went from "plug and pray" which often worked to "plug and look for whatever text file you have to edit"

This system is NOT installable and usab le for the average user. Some may be able typo use it if they have a geek that can get through the issues, but most of what I have indicated here appears to be un-resolvable.
\
All in all it takes the better part of several hours (a days work) to get the the OS and updates installed and the system configiured the way one wants, and too many things are still broken, requiring several hours  more in  forums that you may find others with the same issues, but no answers.


there are still more issues  have ran into along the way, but I do n ot remember all.

this is not a usable OS for the average joe. IT should just work.






mark

---

### Post by pastalavista on 2009-06-30
maybe you should try [Easy Peasy]("http://www.geteasypeasy.com/")... couldn't be much worse

---

### Post by malangaman on 2009-06-30
POTENTIAL USERS CAN CHECK HERE:
[https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)
AND HERE:
[http://ubuntuforums.org/showthread.php?t=1142964](http://ubuntuforums.org/showthread.php?t=1142964)

---

### Post by markbuntu on 2009-06-30
I am using Kuki Linux myself. It is a distro made by a small group of very nice dedicated people especially for the Aspire One and is based on Ubuntu 9.04. It is fast and lightweight and best of all, it works.

[http://www.kuki.me/](http://www.kuki.me/)

If you want to use UNR you should at least use sickboy's kernel. He is the kernel maintainer for Kuki but has made the kernel available for ubuntu. It will make a big difference in your UNR experience.

[http://www.aspireonekernel.com/](http://www.aspireonekernel.com/)

---

### Post by markosjal on 2009-07-01
I  have done about ten ubuntu installations now in the last couple of years, from 6.06 PPC to this 904 remix Those were the first and the last and they were both VERY frustrating, and full of problems. I still have the ubuntu 6.x running. I think maybe it is better to install the regular 9.04 distro than this piece of crap. I think these non mainstream distros like PPC and remix are not as refined as the primary distro (regular old ubuntu 9.04).

I do not care how many threads are out there. I posted MY experience here on a separate thread.

Ubuntu 9.04 remix is SH17Ware, it is all messed up.

Here are more issues. 

No easy way to put a wine entre\y (or any entry not in the menus already) into the favs on the launcher.

From the Launcher the open c:\ or Browse c:\ does not work.

Firefox has no default program for "open containing folder" after a download. 

Mark

---

### Post by guitard00d on 2009-07-07
I'll be tame about criticizing Ubuntu since the last time I chimed in on a thread somebody else started about 7.10 being buggy as hell got me a non-expiring infraction from Vorian. <sarcasm>Oh bummer, how will I continue living?</sarcasm>

But, here's a fact that Vorian will just have to learn to live with, or fix it so people don't have a reason to criticize his flagship and hurting his feelings.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366952](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/366952)

Any kernel in an official release of any distro that reliably locks up systems, gives that distro a huge black eye. Sorry Vorian, blame the others who complained about it first before handing out more infractions.

Anybody have any idea how to get a working RT kernel running on the Nebtbook Remix? Doesn't appear there is a pkg to be found that'll do it. If there is, please tell me what I need to add to my sources.list to get it.

---

### Post by betrunkenaffe on 2009-07-07
Have you copied the devs on these? Should help with prioritizing issues.

---

### Post by moster on 2009-07-07
That thing is small laptop. Why not just put plain good standard Ubuntu 9.4 or newest Mint who is based on Ubuntu but have everything out of box.

Can someone please clarify this mistery for me?

---

### Post by binbash on 2009-07-07
I agree with external monitor part.It just sucks at Ubuntu.

---

### Post by mikjp on 2009-07-07
Well, no system is installable by your average user.

---

### Post by markbuntu on 2009-07-07
> **guitard00d said:**
> ...
Anybody have any idea how to get a working RT kernel running on the Nebtbook Remix? Doesn't appear there is a pkg to be found that'll do it. If there is, please tell me what I need to add to my sources.list to get it.

I do not believe that you can run an rt kernel on a atom processor. I think I saw something about the rt patch and the atom processor being incompatible. I may be wrong....

---

### Post by 3rdalbum on 2009-07-09
> **markosjal said:**
> If the Launcher is turned off no menus appear. Just the wallpaper and documents saved to the desktop the Hotkey for ubuntu menu does not work either (alt f1 I think it is). The only way I got around this was a reinstall

Solution: Don't turn off essential parts of your desktop.

It's a pity you didn't move your hand slightly to the right... Alt-F2 works when the launcher is not running.

> AT times the launcher which is necessary to use based on what  indicated earlier, shows icons pon top of icons and there appears to be no way to rearrange them.

I have not observed this behaviour.

> SUN Java and Flash are available for installation and in my opinion should optionally install by default, as without them a web browser is incomplete

Flash cannot be installed by default unless you have an agreement with Adobe for redistribution. As for Sun Java, I don't have it installed on any of my computers and I haven't needed it since the late 1990s.

> Third party repositories should appear in synaptic for easy activation.(with whatever warning you see fit)

They do. Preferences > Repositories.

> I have never got the track pad to work necessittating the use of external mouse. None of the solutions I have seen make it work. Including hot key etc

That's disturbing - mine works perfectly well. Are you sure you didn't press the key combination to turn off the trackpad?

> This system is NOT installable and usab le for the average user. Some may be able typo use it if they have a geek that can get through the issues, but most of what I have indicated here appears to be un-resolvable.

The system installs quickly, without fuss on Ubuntu 9.04. There are no hardware issues that I've observed on a default installation of Ubuntu 9.04.

> All in all it takes the better part of several hours (a days work) to get the the OS and updates installed and the system configiured the way one wants, and too many things are still broken, requiring several hours  more in  forums that you may find others with the same issues, but no answers.

How on earth did it take you "several hours"? All hardware works out-of-the-box on the Aspire One with 9.04. Installing the "ubuntu-restricted-extras" package takes care of nearly everything else, including Sun Java and Flash. The Medibuntu repository takes care of w32codecs. I installed 8.10 on my Aspire One *without* using ubuntu-restricted-extras (I don't like having Java installed) and I was up and running in about 2 hours.

I'm sorry, I really don't know what's going on with your machine... one or two of your problems are rare glitches that I know about, but most of your problems are alien to me. And I'm an Aspire One owner too.

---

### Post by erikschmitz on 2009-07-09
I have an Aspire One D250 and Ubuntu Netbook Remix 9.04 works great. Within 30 minutes of booting off the usb stick, I was up and running with full hardware functionality. Even HP's distro which is based on Ubuntu 8.04 installed and worked with all of my hardware after a sound driver compile. 

I'm sorry you had such a bad experience markosjal, ubuntu really is a great system especially for netbooks.

---

### Post by llazarte on 2009-07-19
Just my quite recent experience:

I have just (re)installed Windows Home Edition on my wife's AspireOne D250 from the rescue partition, *AND* Ubuntu 9.04 Netbook Remix from an USB stick.

On both cases I did document every step: what I did, where did I get it, how big files were and how long it took to transfer and to install everything.

I configured both systems with mostly the same functionality: Firefox, Flash, Java, Skype, Dropbox, VLC, AVG (in Windows), OpenOffice...

The time to install both systems was similar (10 min Ubuntu, 20 min Windows).

Updating windows was a pain :(: updating, rebooting, clicking on several agreements, updating, rebooting again, etc. Several hours. On Ubuntu it was about 20 min downloading and 20 min installing, both unattended:), no having to wait several hours just to click "Agree", no rebooting, etc.

Summarizing, it was about 3 days for Windows (I did not have several hours at a time just to sit waiting for the next click), and about 3 hours for Ubuntu (including installation, updating, installing new software, configuring [Skype is not easy on the AspireOne], downloading codecs, etc).

Sooo, at most you could say "your milleage may vary", or of course if one is not familiar with an environment it will appear not so friendly. :D

---

