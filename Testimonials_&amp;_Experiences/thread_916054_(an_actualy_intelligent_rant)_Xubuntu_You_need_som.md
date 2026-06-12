---
title: "(an actualy intelligent rant) Xubuntu: You need some work."
date: 2008-09-10
forum: Testimonials &amp; Experiences
---

### Post by jaqie on 2008-09-10
Before I get into my post I feel I should make a few things perfectly clear: I am not the type to usually post a rant of any kind. This post will be in a semi rant format, but I am attempting to bring up actual definitive exact shortcomings in the xubuntu build 8.04.1 from the standpoint of it being end user (and light techie) friendly.
A bit about me, I have been a tech for about 16 years, I started playing with linux with RH 5.2 and a while after SUSE 7.1.  I became a FreeBSD fangirl after 6.0 was released, and ran that as my primary operating system for around a year (babysitting make is just plain ugh).  I also happen to have a WRT54GSv2 with DD-WRT which I have customized with AHBL list blocking and other things, so I am not the usual "windows user" coming to complain about things being difficult... anyone who has used FreeBSD to any depth would know it takes a lot of knowledge to get a fully working system up in that.
I have since gone to XP for the most part, however wishing to go back to linux without the babysitting and realized I am very much the type that even knowing how to make and keep an "old style" *nix system up I just don't think it's necessary in this day and age, I want it to "just bleeding work."(tm) Now, with all this in mind I decided to try the latest xubuntu again because I much prefer XFCE's UI to kde or gnome. Here are my experiences and where I see the shortcomings.


Xubuntu: you need some work.
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
I start by downloading and burning a CD to install you on my server, an intel STL2 based system with dual P3 933s and 1GB ram.  The install goes quite well, except the CRT being stuck at 60hz just like every other OS install I do, makes me feel ill, OK, nothing much different there, works quite well, though I do miss the ability to browse the net while you install.
Next, I reboot. I am greeted to a very odd resolution, 1280x1024x60hz... ew. OK, Ill have to change that first. I log in, and go to the proper place, and what's this? only 60hz options despite me having a rather recent (non gamer) ATI radeon 7000 64MB PCI video card (compared to the onboard 2MG ATI rageIIC that is)?  I know, you can't see the DMPS from my NEC accusync 75F because I had to replace the VGA connector myself and couldnt match up the DDC pins to the proper wires, but windows had no problem with that once I installed the drivers.  OK, I do some googling to find the settings for your xorg config file, restart the entire machine properly, and... it ignores the new settings despite those being the ones for ubuntu (no xubuntu specific help anywhere).
OK, back to square one. I do a lot more googling, and after many many dead ends which say they work for xubuntu too but don't because that menu option is not there or such, I finally find one which suggests running displayconfig-gtk.  Wow! A list of all monitors just like windows has, although the program was buried and not mentioned ANYwhere in documentation! I find my exact model and select the resolution and refresh rate I want, and lo and behold I have it, finally.  I restart you to make sure you keep it, and ick the login screen is still 1280 and 60hz, but I guess I can live with that since I will set autologin soon.
Setting autologin... there is no method via any menu to set it, but with *yet more* googling I find another buried program which allows me to set autologin. Yay. So two things fixed now, which would have taken thirty seconds and a few mouse clicks with windows (or ubuntu!) but over an hour and finding and using progams not usable anywhere in the default install without knowing what their name is specifically to run them at a command prompt with you, xubuntu.
Now... Ive got that... I want some nice backgrounds and my music from my other box. Wait, there is no network browser here. I go to do yet more googling and I find out I have to install via command line smbclient and smbfs... ok, I do that, and then I have to use some arcane 80 character command to link a directory to the share. Did that. Ooh, finally.  This is yet another thing that would have taken a few clicks and a few seconds in windows (or in ubuntu!). Copying files.
What's this? the screen goes to DPMS power saving mode? OK... I go to configure the screen saver, and then into power management, and set it to never power off the monitor.  Then I wait and watch. It still powers it off! I then go in to turn on the screensaver set for it's max of two hours, and make doubly sure DPMS power options are both set to "never". It still kicks the monitor off after the same time period of inactivity. UGH! Settings that don't work... what is this? Ill just put up with it since googling yields many many possible causes all of which require editing configurations files for something that should be settable with the setting that says it is for just such a thing!
OK, now I want to set up synergy so I can use one keyboard and mouse for both of my computers. Not too bad, but it requires me to enter a command line command every time I wish to connect, or to start quicksynergy each time and enter the IP there.  I go to autostarted apps and enter the command line there. not too bad, though not as easy as setting it up in windows, and nowhere near as easy if I wanted linux to *serve* the keyboard and mouse, that would take a whole conf file creation. ugh.
I restart the computer after changing a few more things to my liking, and wait... what's this? After several restarts and no complaints, you think that my monitor cannot handle the resolution I have set, xubuntu? safe graphics mode? OK I guess I will just have to set it up again. So I start telling you again, and I only get 640x480@60hz in your included menu for resolutions... but when I click it, I get garbage on my screen... what the heck?  And there is no timer that defaults back to the last resolution either, so now every time I start, it goes to garbage with no way out short of getting deep into the guts, which is why I wanted you instead of BSD in the first place.

(for the record the PC in question has ran without a single problem, crash, lock, error, anything with WinXP for eight months straight, under heavy load, and having an average uptime of almost a month between patches. the system hardware is *VERY* stable and known good)

*sighs and shakes her head*
You really need some work, Xubuntu.
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

For the curious, although I hate how bloated it feels, I am going to wipe it and just go for kubuntu on it for good. I really hoped xubuntu was improved, and it is from previous versions, but not nearly enough to be considered usable without serious tinkering which should not be necessary in this day and age with an OS (xubuntu) that claims to be end user friendly.  kubuntu is, and so is ubuntu, but xubuntu still falls quite short, in my honest opinion.

---

### Post by cardinals_fan on 2008-09-10
> **jaqie said:**
> 
Setting autologin... there is no method via any menu to set it, but with *yet more* googling I find another buried program which allows me to set autologin. Yay. So two things fixed now, which would have taken thirty seconds and a few mouse clicks with windows (or ubuntu!) but over an hour and finding and using progams not usable anywhere in the default install without knowing what their name is specifically to run them at a command prompt with you, xubuntu.

Too bad there's no method via any menu to set it...

Settings -> Login Window -> Security

---

### Post by jaqie on 2008-09-10
Aha. something they fixed as of version 8.x  I had looked all over in 7.x for such a beast, and it wasn't on the default menu system anywhere.

The rest of my arguments still hold, this one was a minor annoyance that I am glad they fixed. I believe they ARE going the right direction, but it needs serious work still.

---

### Post by wolfen69 on 2008-09-10
your post means nothing to me until you line up 25 computers of various hardware configurations and install on each one. then your testimonial will hold some weight. 1 person's experience with 1 computer out of a billion is not an indication of how good or bad an OS is.

going by your logic, (x)ubuntu must be perfect because it runs perfect for me. therefore it doesn't need any work.

why don't you buy a computer with ubuntu preinstalled (just like you did with windows) and then write a review?

---

### Post by zmjjmz on 2008-09-10
I must note that CRT monitors aren't great with Linux.
But why you're still using a CRT monitor is beyond me, they give me headaches.

---

### Post by jaqie on 2008-09-10
> **wolfen69 said:**
> your post means nothing to me until you line up 25 computers of various hardware configurations and install on each one. then your testimonial will hold some weight. 1 person's experience with 1 computer out of a billion is not an indication of how good or bad an OS is.
Assume: this is what you did here. You assumed I have not ran it on any other computer ever. This is just the latest system I have run xubuntu on, most 7.x this one 8.x.  I actually *gasp* have done what you are speaking of, and have had various problems, the most common of which I surmised right here.  I could list each system I have installed and run xubuntu 7 or 8 on, but I thought that people here would not assume after my preface that this is the first one I have ever tried xubuntu on, especially since I basically stated that very fact in the post!
> why don't you buy a computer with ubuntu preinstalled (just like you did with windows) and then write a review?
Wow... Again you assume... and again you didn't even seem to have read my preface at all! I have never "bought a computer" except laptops - I have built my own since the late 1980s, and the laptops I get the first thing I do is DBAN and install my OS of choice on it.  I think you may want to actually READ my post before responding to it next time.

---

### Post by jaqie on 2008-09-10
> **zmjjmz said:**
> I must note that CRT monitors aren't great with Linux.
But why you're still using a CRT monitor is beyond me, they give me headaches.
They give me headaches too if the refresh rate is below 85Hz, which is one of the big things I was wanting to correct here. The reason I am not using an LCD with this system is twofold. One: money. LCDs cost that. this system was built about a year ago (I have always wanted an STL2 but never got one till then) and the total cost for build with parts I had around already was around $40, that's pretty good for a server-class true SMP motherboard with 1GB ECC/registered RAM. Two: related to money, I refuse to buy any of the older LCD models, I require one built in the last year or two, any older of the cheap ones and they are nastier then the decent CRT I have here (NEC accusync 75F, low res but high quality tube).

---

### Post by jrusso2 on 2008-09-10
> **zmjjmz said:**
> I must note that CRT monitors aren't great with Linux.
But why you're still using a CRT monitor is beyond me, they give me headaches.

CRT monitors run fine with Linux.  They still support a ton of them. Just make sure its not running at 60 mhz.  I am still using a Sony Trinitron it has a better display then all but the most expensive LCD

The best thing about LCD is they are light and don't take up as much deskspace but CRT still better for fast motion and color depth.

---

### Post by 3rdalbum on 2008-09-11
> **jaqie said:**
> Aha. something they fixed as of version 8.x  I had looked all over in 7.x for such a beast, and it wasn't on the default menu system anywhere.

I installed UserOS (Australian respin of Xubuntu 7.10) on a friend's computer, and Settings > Login Window was definitely there.

I still haven't figured out how to set auto-login with Windows. Yes, I'm going on 2 years of infrequent Windows use. I've been told that you need the account to have no password, but that sounds utterly stupid.

The monitor problem doesn't sound that bad, as long as you solved it. Are you giving up already?

---

### Post by ukripper on 2008-09-11
> **jaqie said:**
> 
*sighs and shakes her head*
You really need some work, Xubuntu.


You may want to try openGEU based on ubuntu but lighter version with enlightenment instead of XFCE
[http://opengeu.intilinux.com/Home.html](http://opengeu.intilinux.com/Home.html)


taken from their website - 
"*Enlightenment is a light weight Desktop Shell, so your computer will run at a very high speed with incredible 2D effects, such as animations, fading, shadows and much more. E17 doesn't need a 3D card for all of its effects to run properly, since it can use Xcompmgr and the E17 module &#8220;Bling&#8221;. Thanks to the OpenGEU configuration tool, you&#8217;ll be able to easily activate and deactivate these desktop effects with a mouse click! What&#8217;s more exciting about our Desktop Effects is that they run properly on any kind of hardware, even on Virtual Machines! *"

---

### Post by jaqie on 2008-09-11
> **3rdalbum said:**
> I installed UserOS (Australian respin of Xubuntu 7.10) on a friend's computer, and Settings > Login Window was definitely there.
Hm, that's odd. It definitely wasn't on several installs I have done. oh well that particular issue was a small one.
> I still haven't figured out how to set auto-login with Windows. Yes, I'm going on 2 years of infrequent Windows use. I've been told that you need the account to have no password, but that sounds utterly stupid.
it's oh so easy and shown in so many places, and no, a password works fine. google "autologin windows" to find sooo many tutorials on how, but basically, you download tweakUI from microsoft, install it (a whole 400KB or so) and set so many features of windows including autologin with password.
> The monitor problem doesn't sound that bad, as long as you solved it. Are you giving up already?
Solved it? did you read the last parts? it's become useless without going into non-GUI login which i'm not even going to bother with. I can't remember the last time I had to solve a windows issue via a text console.  As I said, I have the skill to solve it, but this was a rant-format end user/light techie look at the shortcomings of xubuntu that I have seen.  Giving up? Not by a long shot. Dropping xubuntu until next version? You bet.

---

### Post by jaqie on 2008-09-11
> **ukripper said:**
> You may want to try openGEU based on ubuntu but lighter version with enlightenment instead of XFCE
See, as I said I very much prefer XFCE as my WM and have for 6ish years now.  That would defeat the purpouse.  However, I am trying out a lot of "just bleeding works" type linucies now, trying to find the flavor I will use on my server, and also as a dual boot on my gaming system. (there are some games I use and some programs I use that simply will not work on wine even with much configuring, while none is needed on windows xp).  I have downloaded about ten flavors of linux since this thread was created, and am trying most of them in VMs, as I have not tried out most of the flavors in a year or so, I want to see if any fit what I want in an OS better now then the last time I tried.

---

### Post by forger on 2008-09-11
jaqie: I don't think that you actually need a monitor for a server, can't you use a vnc server, connect to it through some other computer instead of struggling with graphics card/monitor issues?

---

### Post by jaqie on 2008-09-11
> **forger said:**
> jaqie: I don't think that you actually need a monitor for a server, can't you use a vnc server, connect to it through some other computer instead of struggling with graphics card/monitor issues?
This is a server but not in the sense that you are thinking.
I have had headless servers as well.

I know it is not traditional to call some of the duties I have this system doing server work, but it definitely is a server to me, as it serves or takes offloaded work from my gaming PC so it can perform better when I run some of the newer games out there.
Among many other things, it runs trillian (pidgin, et cetra), video transcoding on demand, looking for cheat sheets or browsing for quest information when I am in a game like WoW or such, serving web, FTP, and files to my other PCs.

Until a week ago it also ran Asheron's Call bots for a friend... AC is an old MMORPG which does not disallow bots, so my two old accounts were both bots. The problem is that most of the plugins for decal are written in a version of .NET that simply will not work in linux yet nomatter what is done to configure it - the MMO itself will run but not the plugin framework known as decal, so I had to have XP on it to do that.  Now that I finally gave up on that old game for good and gave both accounts I owned for 8 years plus to that friend, the system was finally free to run all the things I want it to with linux instead of windows, which I have been looking forward to ever since I built this particular server about a year ago.

Some of the tasks it does are obviously not the ones that most people consider server tasks, but as I explained because it takes offloading tasks from my main PC (serves my main PC) I consider it a server, so it is what most people would consider a hybrid workstation and server hence the need and want for a full GUI and workstation style OS and setup on it.

---

### Post by Elephantman5 on 2008-09-12
> **wolfen69 said:**
> your post means nothing to me until you line up 25 computers of various hardware configurations and install on each one. then your testimonial will hold some weight. 1 person's experience with 1 computer out of a billion is not an indication of how good or bad an OS is.

going by your logic, (x)ubuntu must be perfect because it runs perfect for me. therefore it doesn't need any work.

why don't you buy a computer with ubuntu preinstalled (just like you did with windows) and then write a review?
I think you're right on the money.

---

### Post by wowbuts5 on 2008-09-14
WoW  [wow gold](http://veryge.com/) in our special discounting zone of US servers is the most cheapest [world of warcraft gold](http://veryge.com/) in the world. On our 'buy now' page, you can buy wow gold of this special zone.And you will get gold within 5 minutes after ordered. Please click our "Fast gold order form" on the left hand . [ffxi gil](http://veryge.com/) Fast delivery within 5 minutes,7*24 services.

---

