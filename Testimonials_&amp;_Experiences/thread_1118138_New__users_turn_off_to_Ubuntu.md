---
title: "New  users turn off to Ubuntu"
date: 2009-04-06
forum: Testimonials &amp; Experiences
---

### Post by V2JTB on 2009-04-06
I am very new to this and have no dought that most of my frustration and failure is down to me.  However  I am sorry to say I have found my experacnce with the forum poor and have found Ubuntu to be very frustraiting.  This is eveident with the amount of quiestions regarding WIFI issues.  Until this is sorted the people will pay for Vista as the current setup is too confusing .  I had great hope when I read how Ubuntu came about as I was having the exact same problem with my WIFI.  I want to learn and use Linux not spend days having to buy diffrent WIFI cards to get Ubunta to work ad still fail.

---

### Post by jpeddicord on 2009-04-06
Moved to Ubuntu Testimonials & Experiences. Sorry things didn't work out for you.

---

### Post by coffeecat on 2009-04-06
**V2JTB**, you have the misfortune to have a wireless NIC with a Marvell chipset. That's not Ubuntu's fault, neither is it this forum's fault, nor is it the fault of the forum members, nor is it your fault. You will probably not care to believe me, but most wireless chipsets work just fine in Ubuntu. I have 6 wireless NICs in my collection: 2 laptop built-in, 2 PCI cards, and 2 USB sticks. All have different chipsets and all work out of the box with Ubuntu, WPA and all. True, there is a minority, usually where the manufacturer can't be bothered to co-operate with the Linux community, that are difficult. You have one of them. 

> **V2JTB said:**
> I have found my experacnce with the forum poor

The reality is that people just don't know how to get your particular wireless NIC working. Or if there are, they didn't notice your thread in what is a very busy forum.

---

### Post by wolfen69 on 2009-04-06
sorry your wifi experience has been less than favorable. 

but considering ubuntu is gaining hundreds if not thousands of new users everyday, it is in no jeopardy of becoming defunct any time soon.

perhaps you should have asked what model #s people were using and buy one of those.

i would just chalk up your experience to bad luck, as most people do not have these issues.

---

### Post by krakk2k on 2009-04-06
ndiswrapper is pretty much the answer to your wifi problems. it allows you to use windows wireless drivers on linux, which is pretty sweet. it would probably be helpful is it was included with an ubuntu install.

---

### Post by GreyGeek on 2009-04-06
I can understand your pain.  Of ALL the distros I have used in the past the Ubuntu/GNOME distros refused to detect or configure my wireless chips on two different laptops: a Gateway m675prr and a Compaq Presario 1500.   They both had a common chip, a broadcom 4306.

Since Ubuntu and its clones did not come with the ndiswrapper on the LiveCD, and it didn't recognize the wireless chip, there was no way I could connect to the Internet and resolve the problem unless I connected a cat5 ethernet cable from the back of the wireless router to my eth0 port.  THEN, I could connect, download ndiswrapper, use the USB port to bring in my *.inf files and get my wireless chip running.

I figured Kubuntu would not recognize the 43xx chip either, so I used the eth0 cable to get a connection and then installed the b43-fwcutter app, which pulled the firmware out of the chip and created a driver for it on the fly.  When I rebooted the wireless chip came up, and I didn't need ndiswrapper.   However, one may have to resort to using the ndiswrapper app.  Here are the steps.

IF you can connect via the eth0 cable then download the Windows drivers for your wireless chip (they will contain *.sys and *.inf files) and install them in a directory under your home account.

Change into the directory and issue
sudo ndiswrapper -e whatever.inf
sudo  ndiswrapper -l  (if you see both "hardware present" AND "driver present" then the install worked.)
sudo modprobe ndiswrapper
If your wireless lamp light comes on then issue
sudo ndiswrapper -m  (to set it up so it can come up on a reboot)

If your lamp doesn't come on, and you are sure the front mechanical switch is on, then the driver is not working.  Use
rmmod ndiswrapper to remove it from the list of active modules.
GG

---

### Post by albinootje on 2009-04-06
> **V2JTB said:**
> This is eveident with the amount of quiestions regarding WIFI issues. 

See here some pages with solutions, for your marvell 88w8335 wifi card :

[http://ubuntuforums.org/showthread.php?t=208088](http://ubuntuforums.org/showthread.php?t=208088)
[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29)

Not easy, but, with some help from the forum here, you have a chance to make it work!

---

### Post by Tamlynmac on 2009-04-07
*Hardware*
When converting from one OS to another, hardware compatibility is critical and expecting hardware to just work is a bad idea.

Prior to changing or trying a new OS, a little investigation may be in order. For example, confirming hardware compatibility and learning a little about the OS may have saved you some frustration.

One should also keep in mind that the forum assistance sections are users helping users (as in no entitlement). If your post didn't get answered, there may be multiple reasons. For example, when anticipating assistance on the forum, one should also realize that it's possible few may have experienced your particular problem.

I understand being new is confusing and yet demeaning the OS because of one piece of hardware incompatibility is foolish. Might I suggest you take a moment and consider you words. You may realize that judging any OS based on one particular brand or model of hardware is unrealistic. When logging on to the forum for assistance, one should keep in mind that it's a user based forum, where no fees or contracts apply. This forum is not customer service based, the users that respond to assistance questions in the help sections do so for free. I believe they do so do be involved and give back to the community - not for profit.

Just my $0.02

---

### Post by Methuselah on 2009-04-07
Ah yes, ndiswrapper. I almost forgot about that.
It allows linux to use manufacturer provided windows wifi drivers.
I used it once to get one of those USB wifi recievers that came with a 2wire router to work with ubuntu.

I think it shows that the community tries every technological avenue to achieve its aims.
While I understand the frustration of the user who just notices something that works in windows and not in Ubuntu, they often don't realize exactly where their angst should be directed.

---

### Post by caravel on 2009-04-07
Seriously, if you want to run Ubuntu and don't want the hassle.  Take the time to find and buy supported hardware.  I bought a generic £10 USB wireless adaptor based on the Realtek 8187 chipset and that worked perfectly.

-Edit: I also have a PEAK 8654ABPK PCI NIC that works ok, I'm not sure what chipset that uses.  That one cost me about £7 - 8

---

### Post by cariboo on 2009-04-07
@GreyGeek

I would suggest you look at the livecd again. ndiswrapper has been a part of the livecd for at least the last 4-5 release. To install ndiswrapper go to System-->Administration-->Software Sources and make sure the cd is enable in the /etc/apt/sources.list. To find it on the CD load the cd into your cd-rom drive, then right-click and select open. Navigate to /pool/main/n. 

Please before spreading fud check your sources.

Jim

---

### Post by 3rdalbum on 2009-04-07
> **caravel said:**
> I bought a generic £10 USB wireless adaptor based on the Realtek 8187 chipset and that worked perfectly.

Er... I don't recommend that chipset, there are bad issues with it at the moment. Says the man who had to compile a new driver for it that doesn't work with WPA, just to get reasonable speed, range and reliability. :-)

Atheros is what I'd buy.

---

### Post by stalkingwolf on 2009-04-07
as of 8.10 none of my wifi adapters work.  All worked with 7.10 and 8.04.  My solution was to return to 8.04.

---

### Post by showman47 on 2009-04-07
I turned to ubuntu because of wifi !

Over a year ago I bought a cheap (really cheap) usb wireless lan stick at a computer fair in London.

I have no choice to use wireless since I share a wireless router in a shared house, so I have no access to cable.

I was trying out linux distros (I tried out over 20 popular ones) and at the time, the only one that worked with my LAN stick was PCLinuxOS.

Then Ubuntu 8.10 came along and it worked perfectly first time in with no intervention from me.

It still works perfectly with absolutely no problems.

I am now a big fan of Ubuntu and use it all the time. I now spend all my computer time having fun and developing websites rather than fixing windows problems and protecting myself from spyware, malware and viruses. 

I don't need or want windows.

the LAN stick I use is a safecom SWMULZ-5400 which uses the Zydas 1211B chipset. I'm sure there are many others that work just as well.

My view is, if your current wireless lan doesn't work, just get a cheap one that does and then realise how much time and money (all that free and legal software !) you are saving.

Can't wait for the new release !

showman47.

---

### Post by solwic on 2009-04-08
> **cariboo907 said:**
> @GreyGeek

I would suggest you look at the livecd again. ndiswrapper has been a part of the livecd for at least the last 4-5 release. To install ndiswrapper go to System-->Administration-->Software Sources and make sure the cd is enable in the /etc/apt/sources.list. To find it on the CD load the cd into your cd-rom drive, then right-click and select open. Navigate to /pool/main/n. 

Please before spreading fud check your sources.

Jim

Maybe we're all using different versions of the livecd, but the last time I had to use ndiswrapper, I had to download it from the repositories.  Was nowhere to be found in the install or the LiveCD.  

Fortunately for me I had the presence of mind to get the wireless card working while I was still hardwired into the router, so not a big deal.  But I can see how it'd be annoying if you didn't have that option....

But if you're right (and I can't see why you'd post this if you weren't), I'd just like to state that navigating to /pool/main/n. isn't very intuitive when you're looking for wireless support.  Perhaps an entry into the menu, organized under networking, perhaps?  

Even Windows figured that out.  :)

Just my .02.

---

### Post by craigeo on 2009-04-08
Why do people expect 100% of all hardware that works on Windows to automatically work on Linux.
But they don't have that same expectation of that hardware to work on MacOS.
I had a wireless nic that didn't work in Linux properly so I researched and got one that did.  Now I have no issues.

Some people just have unreasonable expectations then declare that the whole OS is junk and no one will want to use it.

Sorry, just had to rant.  Good luck getting your hardware to work!

---

### Post by stchman on 2009-04-08
> **V2JTB said:**
> I am very new to this and have no dought that most of my frustration and failure is down to me.  However  I am sorry to say I have found my experacnce with the forum poor and have found Ubuntu to be very frustraiting.  This is eveident with the amount of quiestions regarding WIFI issues.  Until this is sorted the people will pay for Vista as the current setup is too confusing .  I had great hope when I read how Ubuntu came about as I was having the exact same problem with my WIFI.  I want to learn and use Linux not spend days having to buy diffrent WIFI cards to get Ubunta to work ad still fail.

In response to your first thread:

[http://ubuntuforums.org/showthread.php?p=7014396#post7014396](http://ubuntuforums.org/showthread.php?p=7014396#post7014396)

The poster shane8002 told you of a 100% supported WiFi card.  I gather you have chosen to ignore that.

There is an old saying.  You can lead a horse to water but you cannot make him drink.

---

### Post by coffeecat on 2009-04-08
> **stchman said:**
> The poster shane8002 told you of a 100% supported WiFi card.  I gather you have chosen to ignore that.

You gather correctly. :wink: He/she has [has started a new thread]("http://ubuntuforums.org/showthread.php?t=1119013"), and is **still** not listening. :(

---

### Post by jbysmith on 2009-04-08
> **stchman said:**
> There is an old saying. You can lead a user to Linux but you cannot make him think.

Fixed that for ya.

---

### Post by Methuselah on 2009-04-08
I actually think he/she was mistaken about something, thinking that for it to work with the live CD it has to work without any drivers at all.

Coming from a windows background it's not too difficult a conclusion to make. You almost ALWAYS have to install drivers on windows so if something is going to work without you having to install drivers it must be that it doesn't need drivers at all.

Actually, what ubuntu does for properly supported hardware is detect what hardware you have and load the appropriate drivers for you!
So YOU don't have to do anything but drivers are still very much in play.

I think most suggestions said something about drivers which didn't seem too helpful to the OP in light of what he/she thought.

It's a bit like when people complain how difficult software installation is in Ubuntu because they neglect to use the package manager.
On windows you learn to jump around to a million websites to download install packages and run them individually.
Ubuntu fetches the most software packages for you.

It's seems like this OS is almost too good, especially for being free.
The standard ways of doing some things are too magical, so new users don't think of them and try things the hard way they're used to.
Then Ubuntu gives them enough rope to hang themselves with.

Really, a lot of user frustation could probably be solved with education.
Yeah, they might come here and ask, but ask the wrong questions, get answers they deem unhelpful, and leave in frustration when they might very well have enjoyed the system had they understood it.
This might be the difference between a happy Ubuntu user and one that HATES it!

So how do we get people to use Ubuntu like it's meant to be used and not like a windows clone.
It's probably a marketing problem as I've heard others say on occasion.
But how to solve it?

---

### Post by stchman on 2009-04-08
> **jbysmith said:**
> Fixed that for ya.

Excellent, mind if I use that sometime?

---

### Post by jbysmith on 2009-04-08
> **stchman said:**
> Excellent, mind if I use that sometime?

Be my guest, we're all about open source here.

---

### Post by stalkingwolf on 2009-04-12
> Why do people expect 100% of all hardware that works on Windows to automatically work on Linux.

i believe that you have misread or misunderstood several of the posts here.

In My own case i have at least 3 different pieces of hardware that worked OOTB with previous releases. A usb wifi adapter(netgearwg111**), a wifi card (dlink dwl G650) that have worked since 7.04 but dont in 8.10 havent tried 9.04.  Alogitec web cam that works in every application ive tried except Gyachi in 8.04 but only works in Gyachi in 8.10 ( which is the only reason i installed 8.10).

In the last few days i have had several problems with 8.10 after updates. everything from updates no longer working to X flaking out. so far i have been able to repair it all with recovery mode.

I guess what I and many others are saying is " If it aint broke dont fix it."  There are to many things that do need fixing, Build on the working system dont break it.

---

