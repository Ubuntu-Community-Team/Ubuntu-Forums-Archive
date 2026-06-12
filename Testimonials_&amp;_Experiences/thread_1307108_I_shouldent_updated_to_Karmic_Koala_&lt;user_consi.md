---
title: "I shouldent updated to Karmic Koala &lt;user considerations&gt;"
date: 2009-10-30
forum: Testimonials &amp; Experiences
---

### Post by 3esmit on 2009-10-30
As any ubuntu lover, I was really exited by the launch of Karmic Koala.
I think I was ones of the first that downloaded the released 9.10 from site. And so I prepared my computer to reformat, backed up everything and lets update!
[B]
First problem:[/B]
First deceptions came in the installer... It didnt supported my hardware video card, like Fedora 11, and also didnt suported in safe graphics mode (or it didnt activated). 
So I used the "nomodeset --xdriver=intel" and the installer could show up in the screen.
Installed, oh... A surprise, the ubuntu didnt showed up! There go I, edit the grub.conf and put the damn nomodeset there, edit xorg.conf and change from vesa to intel.

Now it came up, and working fine... Woow, very fast! Nice look! Nice features, wow!
Ok, started organizing everything to work, installing applications, creating links(shortcuts)... 
Everything ready!
[B]
Second problem:[/B]
Now working on Netbeans, suddenly I saw that the time was always the same.. Whats happening? gnome-panel is not respondig, but the system-monitor applet is, so I clicked on it, and terminated the gnome-panel, automatically it re-opens. OK FINE!

Working.. now everything is getting too slow, and slow... Memory is all loaded... Go to see whats happening, gnome-panel using all computer resources, and oh, its freezed. Killed it.. restarted and freezed again.. restarted and now ok...  And this situation repeted more and more time untillll....  Oh now its already launching freezed.. And I cannot do anything, unless restart... Restarted machine, and everying ok.

**Third problem (and the worst):**
Im a programmer, and I develop applications to a M2M module (Siemens TC65), in J2ME IMP-NG. The IMP-NG profile is just avaliable under windows plataform, but I made it work in ubuntu even better then in its native plataform, using tools like ObexFTP, ttylog and kermit, automated by a shellscript.
My device is plugged on USB (its an USB-Serial interface) and its located in /dev/ttyACM0. This always worked perfect in Ubuntu 9.04, but now in 9.10, sometimes the /dev/ttyACM0 just disappears, and I have to reconnect device (not automated anymore).  And it is not just that, some times the very opposite happens: it starts to appear more ttyACMs, like /dev/ttyACM0, /dev/ttyACM1, /dev/ttyACM2 (...), and my device is always in the last one, the others are ghosts that I cannot remove.. I tryed deleting them with sudo "rm /dev/ttyACM0", it disappears from the list, but when the device is reattached, it appears in the following ttyACM, not in the first one.
This is taking me a lot of time that I could be working, becouse manytimes I have to delete ttyACMs in order to my shellscript identify the device (have to be just one ttyACM*, no matter the id).


I think that ubuntu 9.10 was released imature, and its very unstable. The 9.04 is way better, and its also fast. I really shouldent changed too soon to Karmic Koala.

I was using Ubuntu 9.04 32bits and now I'm on Ubuntu 9.10 64bits. The speed is really notable, but when gnome-panel frezees, all get slow.


Do you have any suggestions on how to report the /dev/ttyACM* bug? I think that this may be kernel, but unsure.  Thank you.

---

### Post by claymater on 2009-10-30
> **3esmit said:**
> 
Do you have any suggestions on how to report the /dev/ttyACM* bug? I think that this may be kernel, but unsure.  Thank you.


Check the blue question mark at the top.



And if you dont like 9.10 use 9.04....

---

### Post by tekkidd on 2009-10-30
This is the same story with most ubuntu releases. Made the mistake when i updated my computer from 8.10 to 9.04 back when it first came out. And oh man i had a whole gang of problems.

I have been running ubuntu 9.10 in virtual box and im not exactly impressed, sure the upsplash looks and the add/remove looks better, but after how the last install went it think ill let 9.10 mature some more before i upgrade. Hey i might just skip it altogether and go to 10.04.

---

### Post by 3esmit on 2009-10-30
Hi tekkidd.
I hope they fix these problems soon, I'm really sad now with my SO, since its not "perfect" anymore, like was in 9.04.
I hope 10.04 kick asses with problems... And also I'm going to try Fedora 12, that looks like amazing!

---

### Post by spuzzdawg on 2009-10-30
I'm beginning to question why 9.10 was released at all. Around 40% of respondents to the install/upgrade poll are saying that either upgrade or full install has hosed their system. I've managed to get round the upgrade hosing my system with a full install only to find weird issues with parts of windows shutting down and the desktop disapearing. Installing proprietary wireless drivers crashed the system and eventually for reasons unkown to me the partition table was corrupted. Hopefully the second install goes better but it appears from the list of topics appearing on the forum that others are having some serious issues.

The major points for this release were ubuntu one and performance increase. Most are complaining that 9.10 is far slower than 9.04 and ubuntu one doesn't work. Was this release tested?

spuzzdawg

---

### Post by 3esmit on 2009-10-31
spuzzdawg, I didnt noticed ubuntu one.. I think it dosent works.
And performance, yes, I got some in the startup. Also the icons are more beautiful...
There are some improvments, but I think its too imature.

Im going to reinstall ubuntu 9.04.

---

### Post by Normie26 on 2009-10-31
Well I took the plunge last night and updated 9.04 to 9.10 Oh boy, I should have done a bit more research.  Most of the hardware installed ok.  But its oh so slow (running a quad core with 3 Gb RAM) can't get Mozilla to access any web page.  Uninstalled and reinstalled it several times without any success. As I'm a newbie to Linux I don't have the skill to trouble shoot the issue, so I'll just do a reinstall I guess and go back to 9.04  or put the Box in the corner and maybe wait for 10.4 to roll around and hopefully fix the glitched.

---

### Post by DeMus on 2009-10-31
I have no sound. I re-installed all kinds of packages but in order to to make them work I have to switch off GDM. This doesn't work anymore like it used to, other methods don't work either.

I have problems with Grub2 which should never have been invented. MS made the same mistake and now Linux is following them.
MS had boot.ini which was simple to edit, now they have some kind of almost uneditable way to boot the computer.
Linux had Grub1 with menu.lst, now it is Grub 2 with ?????

[COLOR="Red"][SIZE="3"]New is certainly not better.[/SIZE][/COLOR]

---

### Post by QIII on 2009-10-31
Basing an assessment of an OS based on a survey conducted a forum where people who come to get help solving problems from those who volunteer to help is making a flawed assumption.

People come to forums when things go wrong, not when things go right.

For all we know, those who post on this forum, either with problems or with solutions, represent a very small fraction of those who use Ubuntu.

How many people post here at all?  10,000?  How many users are there? 1,000,000?

How many don't come here at all because they don't have any problems at all?

What you have here is a small sample size, a poorly designed "survey" and an Argument From Silence: "Of course Karmic is bad for everyon. Nobody can prove it isn't."

There are Windows forums aplenty.  People use them to solve problems.  Does that represent the vast majority of Windows users who happily click away with nary a problem?

Of course there are problems.  But this should be a place to solve them, not gripe about them.  If Karmic doesn't work for you, dual boot with Jaunty and keep banging at Karmic to see what you can do to get it to work.  Report bugs through Launchpad.

There is nothing wrong with sticking with Jaunty if Karmic doesn't work for you.  But unless someone says something to get someone else's attention, the problems won't be fixed.

---

### Post by spuzzdawg on 2009-10-31
> **QIII said:**
> Basing an assessment of an OS based on a survey conducted a forum where people who come to get help solving problems from those who volunteer to help is making a flawed assumption.

You bring up a fair point. The poll isn't a reliable quantitative representation of the entire userbase. I would say though that I don't see a problem with using it as a qualitative indication of the severity of install issues. Viewed that way, I think that it's not inappropriate to say that it appears alot of people are having issues with their entire system being left unuseable. But you are right, nothing can be stated for sure.

---

### Post by bigpond on 2009-10-31
I just installed karmic this morning and im having a great time, i even got sound right out of the box! (which i didnt in jaunty).:D

---

### Post by gsch on 2009-10-31
When I boot up I get "starting up ..." that's it. I have to escape and select an older kernel from the list to boot up. Not even the live CD works. When I boot up with the older kernel, the touchpad does not work. Imagine the mission to write this message. I posted a thread for this, but it seems like everyone is posting in the "show me your bootchart" thread instead of answering my and everyone else who have just buggered up their systems with ubuntu's NOT-READY-FOR-RELEASE operating system.

So tell me, how do I get my system to boot? How do I get my touchpad working? Or will you rather post your bootchart and check who can pee the farthest?

---

### Post by 3esmit on 2009-10-31
> **DeMus said:**
> 
Linux had Grub1 with menu.lst, now it is Grub 2 with ?????
[COLOR=Red][SIZE=3][/SIZE][/COLOR]

Hello DeMus. Grub2 uses a more advanced way to make that list. There is a script that configures the menu listing in /boot/grub/grub.cfg
In some place the entrys look like in grub1's menu.lst.

---

### Post by n_s_simpson on 2009-10-31
> **3esmit said:**
> 
...
**Third problem (and the worst):**
Im a programmer, and I develop applications to a M2M module (Siemens TC65), in J2ME IMP-NG. The IMP-NG profile is just avaliable under windows plataform, but I made it work in ubuntu even better then in its native plataform, using tools like ObexFTP, ttylog and kermit, automated by a shellscript.
My device is plugged on USB (its an USB-Serial interface) and its located in /dev/ttyACM0. This always worked perfect in Ubuntu 9.04, but now in 9.10, sometimes the /dev/ttyACM0 just disappears, and I have to reconnect device (not automated anymore).  And it is not just that, some times the very opposite happens: it starts to appear more ttyACMs, like /dev/ttyACM0, /dev/ttyACM1, /dev/ttyACM2 (...), and my device is always in the last one, the others are ghosts that I cannot remove.. I tryed deleting them with sudo "rm /dev/ttyACM0", it disappears from the list, but when the device is reattached, it appears in the following ttyACM, not in the first one.
This is taking me a lot of time that I could be working, becouse manytimes I have to delete ttyACMs in order to my shellscript identify the device (have to be just one ttyACM*, no matter the id).
...
Do you have any suggestions on how to report the /dev/ttyACM* bug? I think that this may be kernel, but unsure.  Thank you.

To respond to 3esmit's third problem I can agree this is annoying as I have exactly the same problem. The only workaround I have I posted here:

[http://ubuntuforums.org/showthread.php?t=1307753](http://ubuntuforums.org/showthread.php?t=1307753)

Hope this helps.

---

### Post by 3esmit on 2009-10-31
> **n_s_simpson said:**
> To respond to 3esmit's third problem I can agree this is annoying as I have exactly the same problem. The only workaround I have I posted here:

[http://ubuntuforums.org/showthread.php?t=1307753](http://ubuntuforums.org/showthread.php?t=1307753)

Hope this helps.

n_s_simpson, thanks for sharing your problem, i've replied in your topic with launchpad bugs, to help the dev team tracking and fixing this issue. 

If someone is stuck in GNOME-PANEL's bug, I've registred a bug in launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/465853](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/465853)

---

### Post by cmcanulty on 2009-10-31
My firefox has also slowed as soon as I installed Karmic from fast cable now I am slower than dialup, any ideas?

---

### Post by 3esmit on 2009-10-31
> My firefox has also slowed as soon as I installed Karmic from fast cable now I am slower than dialup, any ideas? 	
Try Google Chrome.

---

### Post by NCLI on 2009-10-31
If you're having problems with Karmic, please post seperate threads, and submit bug to Launchpad.net. We cannot fix your bugs, only help you get around them, fixing bugs is done by the developers, and the developers look only at Launchpad.

---

### Post by P4man on 2009-10-31
> **QIII said:**
> 
How many people post here at all?  10,000?  How many users are there? 1,000,000?

How many don't come here at all because they don't have any problems at all?

+1

Entirely true. Although i guess the number of users is considerably higher than 1M. But the other effect is also true, some people may try it out, doesnt work for them and they just go on using whatever OS they had without ever posting here or elesewhere. For all we know 5 million users tried it and decided it didnt work for them. Basically, we got no clue.
 
If I were to guess, Id say ubuntu works without major issues for 9 out of 10 users at the very least. But thats based on nothing other than a gut feeling, own experience on less than 10 machines lol, and by looking at the problems here and relating them to types of machines.

---

### Post by lrcaballero on 2009-10-31
Wise decision!!! If you follow the threads and comments, I thing is our best option to wait before up-grading and/or doing a clean install. I my-self have been having trouble up-grading and even running from a live cd.

Luis

---

### Post by JC Cheloven on 2009-10-31
> **DeMus said:**
> I have no sound. I re-installed all kinds of packages but in order to to make them work I have to switch off GDM. This doesn't work anymore like it used to, other methods don't work either.

I have problems with Grub2 which should never have been invented. MS made the same mistake and now Linux is following them.
MS had boot.ini which was simple to edit, now they have some kind of almost uneditable way to boot the computer.
Linux had Grub1 with menu.lst, now it is Grub 2 with ?????

[COLOR="Red"][SIZE="3"]New is certainly not better.[/SIZE][/COLOR]

+1
Repairing a broken boot was easy. [Now it's rocket science]("http://ubuntuforums.org/showthread.php?p=8206494#post8206494").

---

### Post by G-Com on 2009-10-31
I'm stunned to find so many people having issues with 9.10. :-?

---

### Post by CthulhuFan on 2009-10-31
> **G-Com said:**
> I'm stunned to find so many people having issues with 9.10. :-?

It happens.  After my workstation upgrade, I can tell you that my Wife's laptop will remain on 9.04 for some time yet.

---

### Post by Zoot7 on 2009-10-31
> **JC Cheloven said:**
> +1
Repairing a broken boot was easy. [Now it's rocket science]("http://ubuntuforums.org/showthread.php?p=8206494#post8206494").
I'm not too mad on Grub 2 either, the older one was much more easy to work with. Although the new features it boasts do have potential.
I'm still on the fence about whether I'll revert it back to Grub Legacy or Not.

> **G-Com said:**
> I'm stunned to find so many people having issues with 9.10. :-?
That generally is the way all the time. If you remember when Jaunty came out there were loads of problems too. Best avoid the new releases until 3 weeks or so afterwards.

---

### Post by occams_beard on 2009-10-31
I'm really regretting upgrading as well. I did it this weekend and wish I hadn't, because I work 14 hour days and just do not have the time to mess around with it. 

I unwisely did the distro upgrade from 9.04 in order to keep all my settings, and to save the time of restoring from backups. So now I'm stuck with a partially hosed computer I'll have to use all week.

I am not one to complain, really I'm not... But for $%#$# sake, I can't believe this is supposed to be considered a stable, production ready OS. 

You know, some of us actually USE ubuntu for actual work. We depend on it. This is not some freaking game. If Microsoft released something this bad, we'd NEVER hear the end of it, and rightfully so. However, in Ubuntu land we are told, "Well, you should have done a fresh install", or "Hey, if you don't like it use the previous version" or "Give them a few weeks to work out the bugs before upgrading." To this I can only say, I never saw ANY warning whatsoever from Ubuntu about doing a distro update. There were no warnings that said "Careful, doing this can hose your system" or "Even though this is no longer a beta, this isn't quite ready, give us some more time." There was, however, a nice button that said "upgrade your distro." Secondly, I'd gladly go back if I could but the 'upgrade' only works one way. So now I'll have to waste a day to do a clean install of Jaunty. 

Anyway, sorry for the rant. I know it's really my fault. I should have known better than to upgrade, but did it anyway. But gee wiz, I didn't think it would be this bad.

---

### Post by 3esmit on 2009-10-31
Well, I'm reporting all my bugs, and debbuging them.. You should do that if you want this problems to be solved faster.

---

### Post by JC Cheloven on 2009-11-02
> **occams_beard said:**
> I'm really regretting upgrading as well (...) 
You know, some of us actually USE ubuntu for actual work. We depend on it. This is not some freaking game (...)
Sorry for your problems. I mostly agree with you. The not-written-rule of "released is still beta" is not adviced anywhere, although people is supposed to know it. But many people doesn't (till the first time).  

Anyway, you can take the opportunity to learn something for the future, as I did two years ago: 
1) always do fresh install 
2) keep your main gladly working system, 'just in case' and
3) try new releases in a testing computer, or in a separate partiton

If 3) isn't possible for you, wait a few weeks, have a look on this forums, and install when things appear to be ok. In other words: "don't trust the enthusiasts, keep safe".

---

### Post by win2456 on 2009-11-11
mmhmmm.. Awesome release.  Not too fond of the theme.  Worked out of the box for me.  Very impressive boot-up time.

I upgraded 2 laptops (IBM thinkpad T22 & Dell D830 )and 1 desktop (P4 HT) and had no issues.  Worked flawlessly.

Wait til 10.04 if you want but I didn't see any reason to wait :)

---

### Post by Dullstar on 2009-11-11
> **DeMus said:**
> I have no sound. I re-installed all kinds of packages but in order to to make them work I have to switch off GDM. This doesn't work anymore like it used to, other methods don't work either.

I have problems with Grub2 which should never have been invented. MS made the same mistake and now Linux is following them.
MS had boot.ini which was simple to edit, now they have some kind of almost uneditable way to boot the computer.
Linux had Grub1 with menu.lst, now it is Grub 2 with ?????

[COLOR=Red][SIZE=3]New is certainly not better.[/SIZE][/COLOR]

I hear you, 9.10 turned my system into workable into an epic failure.  It took me about two to three weeks to get it working again, and that was after reinstalling Windows twice to get a dual boot configuration.  I, however, did find directions on how to restore Grub from a LiveCD, so get an ISO of 9.04, install a Grub2 distro, then restore Grub1 from the 9.04 LiveCD.

EDIT:  Might be for Grub2, as I haven't need the directions yet, I'd have to check.  I believe they are for Grub1 though, and it should work for pre 9.04 as well.

---

