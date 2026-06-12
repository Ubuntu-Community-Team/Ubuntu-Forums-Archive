---
title: "Windows replacing / Alternative OS -&gt; Ubuntu 18.04"
date: 2019-05-12
forum: Ubuntu, Linux and OS Chat
---

### Post by chihwah_li on 2019-05-12
Some years ago I tried Ubuntu as a full Windows replacement. But I went back to Windows 7 after many problems. But now I can finally say Linux (Ubuntu 18.04) and all it's software is mature enough to be used as a replacement to Windows. I dumped windows 7 as of now. Not going to windows 10 ever.

Some programs cannot be replaced yet, but they can be run under wine perfectly:
- FL studio 20 with help of Playonlinux
- Foobar2000

Opensource programs as a replacement of Windows programs:\
- LibreOffice
- Mandarin music player

Benefits Linux:
- lightning fast boot times compared to Windows (about 15 sec, 2 minutes, until I see the SSD stop working)
- Excellent free opensource programs: UFW firewall
- Free updates life long
- out of the box support for many peripherals (windows requires a driver for even a simple 100 Mbit usb 2.0 LAN)
- Much better security, if yo
- Still less virus and Trojan problems compared to Windows.
- Every software component can be replaced by something else you like / want. i.e. XFCE desktop (very light desktop)

u can install extra software to harden linux.

Requires more knowledge to maintain. That is the only downside to Linux

---

### Post by TheFu on 2019-05-12
> **chihwah_li said:**
>  
Requires more knowledge to maintain. That is the only downside to Linux

I would disagree with this statement.  It isn't more knowledge, it is different knowledge. If you have years of learning and knowledge using Windows, expecting a completely different OS to behave exactly the same will only lead to frustration. 

I wonder if anyone might have written an article outlining maintaining a Linux system?
[https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282](https://lifehacker.com/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc-5817282)  In general, that article still applies, but I'd replace apt-get/aptitude with **apt**.

#1 - setup versioned backups - daily, weekly at a minimum. Anything you don't want to loose needs to be included.
#2 - **sudo apt update && sudo apt dist-upgrade**  # do it weekly.

That should cover Ubuntu desktop maintenance for almost every desktop user.  Maintaining a server on a home LAN isn't much more difficult.  Maintaining a server on the internet is a completely different thing, entirely, all together.

---

### Post by crip720 on 2019-05-12
Just wondering what would be the difference between [COLOR=#000000]#2 - [/COLOR]**sudo apt update && sudo apt dist-upgrade # do it weekly  and having software updater setup to run daily or weekly  **

---

### Post by olduse78802 on 2019-05-12
I use kubuntu 18.04 on all but 4 machines 1 has win 7 , 2 winxp pro , 1 laptop with win 10 (old  lat 620 i think) . The win 7 machine will go to kubuntu 18.04 when win 7 dies.  One winxp runs my tv and the other runs my movies/music.  I have no plans to change the winxp machines until i run out of machines to run it.  The laptop with win 10 i dont use at all hardly will put lxbuntu on it one day .

---

### Post by TheFu on 2019-05-12
> **crip720 said:**
> Just wondering what would be the difference between [COLOR=#000000]#2 - [/COLOR]**sudo apt update && sudo apt dist-upgrade # do it weekly  and having software updater setup to run daily or weekly  **

Don't know. I've never used software updater, ever.  There might be an answer in the manpages.  I know **apt** has a useful manpage which explains how things work for the options. 

Perhaps someone else can provide a reference, but with GUI programs, there generally isn't any real documentation for how things actually work.  Just checked my current desktop and it doesn't have Ubuntu Software Center installed. I've never noticed. ;)

---

### Post by crip720 on 2019-05-12
Found this on ask ubuntu, guess the only difference is one you don't have to remember to use.  It is part of longer answer.  [COLOR=#242729][FONT=Arial]Using the Software Updater and using [/FONT][/COLOR]sudo apt-get update ; sudo apt-get dist-upgrade[COLOR=#242729][FONT=Arial] (note the [/FONT][/COLOR]dist-[COLOR=#242729][FONT=Arial]) would be almost equivalent, except that one's obviously a GUI and the other's a console application and also a few [/FONT][/COLOR]*very*[COLOR=#242729][FONT=Arial] minor informational differences.[/FONT][/COLOR]

---

### Post by crip720 on 2019-05-12
Think Windows might need more knowledge for maintenance, you have to search and download and install most of the programs you want.  Most of the programs have to be updated manually one by one plus a reboot for each one, and don't forget about deflag and cleaning the system every so often.

---

### Post by &amp;KyT$0P# on 2019-05-12
> **crip720 said:**
> Just wondering what would be the difference between [COLOR=#000000]#2 - [/COLOR]**sudo apt update && sudo apt dist-upgrade # do it weekly  and having software updater setup to run daily or weekly  **

Software Updater does [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").  Whereas [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] gives you all available updates, including ones you wouldn't yet get with phased updates.

---

### Post by Rubi1200 on 2019-05-12
> **halogen2 said:**
> Software Updater does [phased updates]("https://wiki.ubuntu.com/PhasedUpdates").  Whereas [FONT=Courier New]sudo apt-get dist-upgrade[/FONT] gives you all available updates, including ones you wouldn't yet get with phased updates.

Question is whether the more cautious phased update approach is better for newer or less experienced users than dist-upgrade?

Personally, I would likely not recommend using apt update && and dist-upgrade for new users unless they were confident in being able to track down and resolve issues should any arise.

---

### Post by mastablasta on 2019-05-13
> **crip720 said:**
> Think Windows might need more knowledge for maintenance, you have to search and download and install most of the programs you want.  Most of the programs have to be updated manually one by one plus a reboot for each one, and don't forget about deflag and cleaning the system every so often.

that's probably not what it was meant. though reboot is not necessary in windows after program install. it is needed for drivers install but same situation is in linux.


when things go wrong you need a lot more knowledge especially since you often need to fix it yourself. and even if others ran into same bug that is giving you issues you might need to wait a long time for it to be resolved. but in windows people complain, MS provides patch. upgrades in windows do work. have to work. we have thousands that get them and all work well after the upgrades.

the issue with linux (this is maybe because of low user base and monetary issue) is that when things go wrong (and they often do in desktop edition) there isn't much for the average user to do. the required knowledge to maintain a system should be minimal. instead so many people have issue installing drivers or issues after installing drivers. probably this has something to do they are not really well made.

i am particularly irritated when settings i made in the system get an override. still haven't resolved the issue with primary monitor being switched off in some games and when i switch to console. or the latest one when simply another type of keyboard is being used instead of the one i set. this **never **happened to me in windows. if you set certain parameters they hold. if you set a primary monitor and turn off output on the other - it stays that way.

---

### Post by olduse78802 on 2019-05-13
I almost always do a clean install when i update to the next LTS version.  That always works out for me .  I have a separate partition where i keep my data and files so the os is the only thing on the os partition.

---

