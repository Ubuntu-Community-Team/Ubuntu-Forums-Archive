---
title: "Ubuntu wireless test.. ruh roh!"
date: 2012-03-14
forum: Testimonials &amp; Experiences
---

### Post by msmoker85 on 2012-03-14
Hey all, I have been a Linux user since Windows 98. Through trial and error, I learned to set up a Debian system from scratch. I then migrated to OSX where I forgot some of my Linux skills. Flash forward a few years, to the year 2012. I installed Ubuntu and decided to see if the true test of Linux evolution has been met. I tried to use a USB Wirelss-N adapter. 

FAIL. 

It's 2012, and Linux still can't manage to fix this crap for the newbies.

Sigh. They got the storage working, webcams, touch pads, a nice GUI and file browser, an app store, but I STILL HAVE TO WASTE TIME LEARNING HOW TO SET UP WIFI???

We need to get this ubiquitous peripheral WORKING PLUG AND PLAY. Jeesh.

---

### Post by jerome1232 on 2012-03-14
> **msmoker85 said:**
> 
FAIL. 


I plugged mine in, it worked just fine, plug and play.

I plugged it into windows, and had to download a driver from the manufacturers website.

Winning.

Either purchase well supported hardware, contribute to the development of a driver for your card, or us an OS more suited to your preferences.

______________________________________________________________________

In case your not ranting and actually want help with this.


Have you even tried clicking additional drivers to see if a driver is listed in there?

What is the chipset?

```
lsusb
sudo lshw -C network
```

---

### Post by ajgreeny on 2012-03-14
The last time I used windows and installed it myself (XP about 4 years ago on an HP laptop) it took for ever, and absolutely nothing worked when attached to the machine without searching for drivers, and as there were no driver CDs available to use with the machine, it took for ever to get it up and running.  I had to search on another machine to find the drivers for the modem, which was still needed for fax, the wireless card and the graphic card an ATI, I think, but can't remember in detail.  It was a real pain, and not something I would want to do again.

And you think that installing ubuntu and searching for drivers is difficult.  I know which I would rather do.  With linux friendly hardware you could have been lucky and not had to look for anything, exactly as it was with my netbook where all the hardware worked out of the box.

---

### Post by msmoker85 on 2012-03-15
Yes I was just ranting. I have been so curious as to how this crap works, I went back to the drawing board, literally, and breadboarded and PLC'd may way to a basic understanding of registers, processors, assembler code, etc. This lead me years ago to be interested enough in computers to have every OS running on various machines, Linux, OS2, OSX, DOS, and Windows. I liked the Debian system the best, setting everything up after a basic command line install.

I am so impressed that so many people have contributed to the thing that is Linux, and it's a great thing that I love.

However I have been recently working on so many projects, physical projects like computerizing milling equipment, telescope drive, etc. as well as several patents. So when I received a new instrument configured with Ubuntu, I was really hoping that I would not have to re-learn the wifi setup procedures in general, as well as particularities of my usb adapter.
You see, I am doing so much crap that I have reached the point that when I learn something else in order to accomplish something, I must forget at least partially some other crap.
In the last couple years I have forgotten lots of Linux knowledge. I was so good at scripting and compiling that I pretty much knew how to do what I needed.
Until the WIFI issue that I just had.

I do not understand because the Linux community seems to eager to increase its membership, and help others, and all mostly free and open source. Wonderful.

But we still have this problem. The wifi didn't work.

An issue with lack of standards in the manufacturing side? The diversity of equipment requiring unique driver code is astounding. Yet, there are only a few basic elements or tasks done by the computer and this can be divided into obvious groups: networking (ethernet always works, why not wifi? standards lacking?), display, storage, memory, CPU, misc. other I/O like serial and parallel, sound, what am I missing? These are the basics and they should all always be plug and play.

Sometimes I know this, because I feel it myself and admit it, is that I like to have ownership of my knowledge and sometimes my sub conscious therefore tends to obfuscate. What this means can be answered by your example:

lsusb sudo lshw -C network
and that of many others follows the standard form.

Tell the inexperienced user to issue a command that dumps a whole crap load of text onto the screen.

95% of the time, the information you want is on a single line or two, but it is obfuscated by the data dump.

This is not how inexperienced people think.

"
Winning.

Either purchase well supported hardware, contribute to the development  of a driver for your card, or us an OS more suited to your preferences.
"

See? You want me to contribute to development? Are you crazy? THIS IS YOUR SUBCONSCIOUS trying to maintain ownership of your knowledge. If the core Linux community really did not look upon with contempt the outside world, or in fact even truly wanted to make it really easy for the new people, you (Linux core) would change this line of thinking.

Never say anything remotely like "well if you want Linux than you better know what your doing!" and there would be a group doing away with the "enter these commands into the command line and then respew all the lines of code." That right there says it's not working right for new people plug and play, and that an attitude is present still in the Linux core, that this is really for us experts and we'll dish out a little advice here and there, but keep the true knowledge obfuscated. Basic human psychology.

Sorry for my rant I hope it was entertaining. I will get my friend Cyle to fix my wifi before he goes to Black Hat and that way I can continue wiring my mill for God's sake!

Kindest regards.

---

### Post by TBABill on 2012-03-15
So you went from using/knowing Linux since Windows 98 to not understanding command lines? 
 
Linux developers cannot force closed source software owners/creators to simply allow their devices to be plug and play. Licensing issues prevent that and it's up to each company to decide how or if they open their software up to easy distribution. However, a quick search of the help pages ([https://help.ubuntu.com](https://help.ubuntu.com)) shows how they even include some proprietary stuff on the liveCD for users who have Broadcom wireless devices, for example, but you have to read and know it's there and how to use it before it will work. Plug and play just isn't allowed with theirs and others are probably the same.
 
For other wireless, the configuration gets borked and in that regard you are absolutely correct. Someone just needs the experience, time and ability to fix those problems as they are identified. The RT2860 Realtek comes to mind for that as an example and it's been broken for a long time...not sure if it's fixed yet. Unfortunately, I know the workaround but not how to fix the root cause. So, I do agree that supported devices should just work. 
 
Big picture though is that you can't just assume something will work. My son has a DVC-100 Dazzle that "just works" on Windows XP but until recently would not work on Windows 7. I plugged it in and it didn't work....should I blame Microsoft? Pinnacle is the company that didn't make a driver available for Win 7, but following your logic I would have to blame Microsoft because "plug and play should just work".
 
I too wish it all worked magically, but with any computer and OS you have to be willing to fix it by researching, asking questions and applying what you find. Complaining aloud without trying much is just....well, complaining.

---

### Post by jerome1232 on 2012-03-15
> **msmoker85 said:**
> 
"
Winning.

Either purchase well supported hardware, contribute to the development  of a driver for your card, or us an OS more suited to your preferences.
"

See? You want me to contribute to development? Are you crazy? THIS IS YOUR SUBCONSCIOUS trying to maintain ownership of your knowledge. If the core Linux community really did not look upon with contempt the outside world, or in fact even truly wanted to make it really easy for the new people, you (Linux core) would change this line of thinking.

Kindest regards.

I was purposefully answering your rant with a rant. I look on self-entitlement rants with contempt, not the outside world. I'm sorry that the development teams cannot work on backwards engineering new drivers for every wireless chipset out their fast enough to suit your needs. 

I am honestly amazed at how many wireless cards do work out of the box these days, my netbook I just put ubuntu on works flawlessly with zero setup on my end, which is more than I can say if I installed a bare Windows

---

### Post by tbhatia4 on 2012-03-15
> **msmoker85 said:**
> Hey all, I have been a Linux user since Windows 98. Through trial and error, I learned to set up a Debian system from scratch. I then migrated to OSX where I forgot some of my Linux skills. Flash forward a few years, to the year 2012. I installed Ubuntu and decided to see if the true test of Linux evolution has been met. I tried to use a USB Wirelss-N adapter. 

FAIL. 

It's 2012, and Linux still can't manage to fix this crap for the newbies.

Sigh. They got the storage working, webcams, touch pads, a nice GUI and file browser, an app store, but I STILL HAVE TO WASTE TIME LEARNING HOW TO SET UP WIFI???

We need to get this ubiquitous peripheral WORKING PLUG AND PLAY. Jeesh.

specify your issue rather than criticizing linux community is always ther to help

---

### Post by msmoker85 on 2012-03-15
OK I am sorry- I am truly finished venting now. Further posting will be more productive ;) It has just been a couple years since I tried a new distro, and was kinda hoping the dang adapter would just work. But yeah, without some kind of standards enforcement, the variation in hardware is too difficult to overcome. Perhaps one day I could start a database to at least track what works and what does not. Probably already some kind of thing out there like it though.

---

### Post by Lisiano on 2012-03-15
Lists:
[http://linuxwireless.org/en/users/Devices/USB](http://linuxwireless.org/en/users/Devices/USB)
[http://linuxwireless.org/en/users/Devices/PCI](http://linuxwireless.org/en/users/Devices/PCI)
[http://linuxwireless.org/en/users/Devices/PCMCIA](http://linuxwireless.org/en/users/Devices/PCMCIA)

And for nearly everything, there is a generic driver, except WiFi, just as you said, standarts and licensing.

---

### Post by oldos2er on 2012-03-15
Thread moved to Ubuntu Testimonials & Experiences.

---

### Post by gordintoronto on 2012-03-15
TP-Link TL-WN722N: plug it in, boot a recent Linux, "it just works."

Which is a much better experience than under some other OS.

---

### Post by mastablasta on 2012-03-16
regarding command line help:
 
user can actually go to hardware monitor or whatever is called and then find the chip there if it is recognised. however different distributions and desktop environments have this stuff named differently and on different place. however command line will work in all of them. and as an additional conviniency the user can simply copy paste command in and then copy the output and paste it here so others can identify the error or issue.
 
aditionally help provided liek that will be valid even to those with older verisons of the os or if they simply use Ubuntu based OS (for exmaple Linux Mint).
 
and as others said linux compatible hardware should and does work. when i buy hardware i now check if it is compatible with multiple OS or if drivers are provided. no issues so far. everyhting is plug and play or drivers can be installed either via PPA or additional drivers GUI.

---

### Post by stalkingwolf on 2012-03-16
since my first experience with a broadcom wireless adapter , around the time of the release of 7.10 i have kept 2 adapters handy when installing.  a DLink dwl G650 and a netgear wv111 v.2.  both have worked everytime.  Sometimes
window even recognizes the netgear and installs drivers auto magically.

When the painful necessity arises that i have to install windows i download the drivers before i start the install. put them on a thumb drive and off i go.

I might add that since 7.10 the only wifi i have had problems with was on an everex (broadcom) but then there were display issues on that model as well (S3 unichrome pro as i recall.)

---

### Post by 3rdalbum on 2012-03-16
Try plugging it onto a Mac. It wont work either.

Because the manufacturer hasn't made a driver for it.

Or rather, the real problem is that the manufacturers have not designed a way for all Wifi cards to operate with a standard driver like USB keys, mice, speakers etc.

It is surprising how many wifi devices work in Ubuntu easily. Some require a visit to the Additional Drivers program though - have you tried that?

---

### Post by Handssolow on 2012-03-17
A quick glance at the network section and you'll see that many still have problems getting their wifi working. A while back I needed to make up a new desktop PC. The first two pci wifi cards I bought didn't work under Ubuntu. Often you only find out what chipset it has got after you've bought the thing then read it doesn't work so well if at all under Linux.

So I looked on Amazon and found a card recommended to work with Ubuntu by a reviewer, problem solved. Fast forward to last year and this time my wife needs a new PC. Though by now the model of wifi card was obsolete I managed to find one on Amazon, problem sorted again.

---

### Post by coldraven on 2012-03-17
"See? You want me to contribute to development? Are you crazy? THIS IS  YOUR SUBCONSCIOUS trying to maintain ownership of your knowledge. If the  core Linux community really did not look upon with contempt the outside  world, or in fact even truly wanted to make it really easy for the new  people, you (Linux core) would change this line of thinking."

I think you need a long holiday somewhere far away from computers.

---

### Post by Ceedub2 on 2012-03-19
Yea when I installed Ubuntu to my latest laptop I have to plug in an either net cable to get my wifi working. No big deal as there was a install additional drivers button in settings.

---

