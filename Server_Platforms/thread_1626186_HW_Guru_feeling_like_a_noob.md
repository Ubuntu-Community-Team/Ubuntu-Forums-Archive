---
title: "HW Guru feeling like a noob"
date: 2010-11-20
forum: Server Platforms
---

### Post by scorpiooooooh on 2010-11-20
*PREFACE:  While I freely admit I am a noob to Linux & Ubuntu, I am a seasoned HW Tech, MS Admin and Network Tech.  I am also CompTIA A+ and Network+ certified.  Over a four week period, I have spent well over 20 hours looking for the answers to the following questions.  The reason I am writing this preface is because many of the replies to posts originated by others and myself that were found here and/or elsewhere during my research have A) Been rude to the poster because they "didn't do their homework" or B) The answers were, while well intentioned, not very useful because the reader did not read the whole post.  That said, let's not belabor the preface in any replies as it is irrelevant to the task.*

This is the HW that I have on hand to work with:

- MOBO - Tyan Tiger 133A (S1834D)Circa 1999
- VIA APOLLO PRO 133A chipset, VT82C694X and VT82C596B
- Dual P2/P3 Slot 1 with two PIII EB (Coppermine) 733MHz Procs installed.  (may upgrade to dual 1064 MHz procs at a later date)
- 1X,2X,4x AGP2.0

Most of the on board HW like USB 1.0, UART, ECP/EPP etc. probably wont be used and will be disabled in the BIOS.

MEMORY - 1.5 GB 133 MHz SDRAM

SCSI Adapters
Adaptec AHA-2940UW
Antares Microsystems U160 20-052-0076 (LSA0723, SYM53C1010-66)
Compaq 348759-001 SCSI-2 w/LSI53C896
Oodles of SCSI drives from 4.5GB to 18GB

A Multitude of NICs and sound cards to choose from

VIDEO
3DFX Voodoo-3 3000 w/16MB (AGP 4X)
ATI Rage 128 Pro w/8 MB (AGP 4X)
ATI Rage iiC w/8MB (AGP 2X)
Note: What video card is generally regarded as the best for linux? For Windows 2000/2003 servers the ATI Xpert 2000Pro was the cats ***.  Is there a Linux equivalent that's the penguin's ***?

Okay, on to the questions.

1) Where might I find the Linux/Ubuntu equivalent to the VIA 4-in-1 driver for this mobo.  I have looked on VIA's web site and it's a joke.  They have one of the least useful driver search interfaces on the Linux portal I have ever seen.  Now this is where I may go ahead and make myself look stoopid.  Are these things just natively supported in Ubuntu?  I have seen posts by folks using boards with the Apollo Pro 133A chipset, so I know they exist.  But where?  Also, SGI Used dual proc boards with the Apollo Pro 133A chipset.  

2)Is there a linux/ubuntu HCL?  I tried looking on the ubuntu website but it threw me a 401 error when I clicked the link that probably would have taken me to where I need to find all the answers I seek instead of bothering you good people.

3) Which server version would be most appropriate (ie. stable) for the hardware listed above?  PLEASE...  Don't just say server, gimme a #.## version number or the name of an animal, because I already know I want the server edition....I think, which leads to the next question.  But seriously, before we go on to the next Q, I've asked the version question elsewhere and received answers that clearly indicated the person "helping" me only read the Subject line.

4)I want to run server but I hear tell that running a GUI on the server is not in the best interests of the user or the machine.  If I go with whatever version of server, do I put a penguin into another machine along with a GUI to get the pretty interface for remote access and administration?  

This project is, for now, just to get my hands dirty with Linux.  I used to work for AT&T Bell Labs and am (*well, was*) quite familiar with Unix on the user level.  I've also thrown Red Hat on a box a long while ago and was extremely impressed with the ease of installation.  That was just for fun but now I need to update my skill set and aim for a Linux cert in the not too distant future.

BTW... In all the research I've done for this Linux project, the ONLY thing I found that was useful is that one should disable the ACPI function in the BIOS for Linux to operate properly with this chipset.

---

### Post by wojox on 2010-11-20
Look at the HCL in my signature.

I run Debian Lenny for my server.

You can learn a lot from just using the command-line, but try looking at webadmin instead of a GUI for you server. :D

---

### Post by capscrew on 2010-11-20
> **scorpiooooooh said:**
> *PREFACE:  While I freely admit I am a noob to Linux & Ubuntu, I am a seasoned HW Tech, MS Admin and Network Tech.  I am also CompTIA A+ and Network+ certified.  Over a four week period, I have spent well over 20 hours looking for the answers to the following questions.  The reason I am writing this preface is because many of the replies to posts originated by others and myself that were found here and/or elsewhere during my research have A) Been rude to the poster because they "didn't do their homework" or B) The answers were, while well intentioned, not very useful because the reader did not read the whole post.  That said, let's not belabor the preface in any replies as it is irrelevant to the task.*

As long as you realize that this is really a conversation (i.e. back and forth); an interchange of ideas.> 

This is the HW that I have on hand to work with:

- MOBO - Tyan Tiger 133A (S1834D)Circa 1999
- VIA APOLLO PRO 133A chipset, VT82C694X and VT82C596B
- Dual P2/P3 Slot 1 with two PIII EB (Coppermine) 733MHz Procs installed.  (may upgrade to dual 1064 MHz procs at a later date)
- 1X,2X,4x AGP2.0

Most of the on board HW like USB 1.0, UART, ECP/EPP etc. probably wont be used and will be disabled in the BIOS.

MEMORY - 1.5 GB 133 MHz SDRAM

SCSI Adapters
Adaptec AHA-2940UW
Antares Microsystems U160 20-052-0076 (LSA0723, SYM53C1010-66)
Compaq 348759-001 SCSI-2 w/LSI53C896
Oodles of SCSI drives from 4.5GB to 18GB

A Multitude of NICs and sound cards to choose from

VIDEO
3DFX Voodoo-3 3000 w/16MB (AGP 4X)
ATI Rage 128 Pro w/8 MB (AGP 4X)
ATI Rage iiC w/8MB (AGP 2X)
Note: What video card is generally regarded as the best for linux? For Windows 2000/2003 servers the ATI Xpert 2000Pro was the cats ***.  Is there a Linux equivalent that's the penguin's ***?

Okay, on to the questions.

1) Where might I find the Linux/Ubuntu equivalent to the VIA 4-in-1 driver for this mobo. 
By this time this chipset should be supported in the kernel.  There should be no need to you to do anything special.> 
 I have looked on VIA's web site and it's a joke.  They have one of the least useful driver search interfaces on the Linux portal I have ever seen.  Now this is where I may go ahead and make myself look stoopid.  Are these things just natively supported in Ubuntu?  I have seen posts by folks using boards with the Apollo Pro 133A chipset, so I know they exist.  But where?  Also, SGI Used dual proc boards with the Apollo Pro 133A chipset.

2)Is there a linux/ubuntu HCL?  I tried looking on the ubuntu website but it threw me a 401 error when I clicked the link that probably would have taken me to where I need to find all the answers I seek instead of bothering you good people.

A couple of points here.
a) Linux is Linux.  The kernel is the same whether it is Red Hat or SUSE or Debian (Ubuntu).  The different flavors are mostly how the packages are maintained and the location of some of the libs (file structure).  This means you could look for an HCL Linux by kernel number rather than the distro.
 
b) There really is no need for a HCL to be maintained for older hardware.  You can download the Ubuntu version that you want to try out and boot to a fully functioning OS.  You can even install optional applications without permanently modifying the HDD.  So if it works you hardware is supported.  Once installed there are some alternative drivers that can be installed if needed. >  

3) Which server version would be most appropriate (ie. stable) for the hardware listed above?  PLEASE...  Don't just say server, gimme a #.## version number or the name of an animal,
Ubuntu has a simple (once you know) version numbering system. It works like this 8.04 = 2008+April release and 10.10 = 2010+October.  So it boils down to: there are 2 releases per year (April and October (04 and 10).  Every 2 years there are long term releases (LTS).  These are supported for 3 years for the desktop and 5 years for the server. 

From my experience there are a couple of things to bear in mind: 1) LTS versions (either 8.04 or 10.04) are usually more stable after the first year of use.  The other versions or only current for 6 months and folks tend to upgrade to solve problems.  2) 8.04 is now very stable while there are init problems to be worked out on 10.04 and later.  This is due to the use of Upstart rather than SysV init when booting up.  If you want stability you can start with Ubuntu 8.04 LTS or Debian 5 (Lenny).  In a short while Debian 6 Squeeze (stable) will be available.  Debian does not use Upstart yet if I'm not mistaken.     
> 
because I already know I want the server edition....I think,
Glad you left yourself some room to think...

There is really only minimal kernel tuning differences in the kernel build between the server and the desktop versions.  IMHO for testing purposes you won't really notice the difference.  I  have 2 Coppermine CPU based systems.  I run one on the server kernel release and the other on the desktop.  

If I were you I would install the desktop and learn how the terminal works in a friendlier environment.  

> 

which leads to the next question.  But seriously, before we go on to the next Q, I've asked the version question elsewhere and received answers that clearly indicated the person "helping" me only read the Subject line.

4)I want to run server but I hear tell that running a GUI on the server is not in the best interests of the user or the machine.  If I go with whatever version of server, do I put a penguin into another machine along with a GUI to get the pretty interface for remote access and administration?

If you are going to use Ubuntu I would install the desktop version while learning rather than installing the server and then adding the GUI.  But it is up to you.  My server system is my NAS (2TB) for my network and I use SSH via PuTTY to admin from the CLI.>  

This project is, for now, just to get my hands dirty with Linux.  I used to work for AT&T Bell Labs and am (*well, was*) quite familiar with Unix on the user level.  I've also thrown Red Hat on a box a long while ago and was extremely impressed with the ease of installation.  That was just for fun but now I need to update my skill set and aim for a Linux cert in the not too distant future.

BTW... In all the research I've done for this Linux project, the ONLY thing I found that was useful is that one should disable the ACPI function in the BIOS for Linux to operate properly with this chipset.
I have ACPI working on my 2 machines.  If I remember correctly the problem was one of not correctly shutting off and was solved with a BIOS update.

I hope this helps.  If nothing else it will prompt new questions.  :D

---

### Post by BarryDocks on 2010-11-20
I am not a guru and was a noob as little as 18 months ago when I first installed Mint on a spare laptop to play with.  I am a health care professional with no formal IT training.  Since then I have gained good working knowledge of administering an ubuntu server inlcuding networking, samba, printing, zoneminder, etc.  I have found the people on this site extremely helpful and polite despite my woefully basic questions and poor understanding. 

While I can't give you any advice on some of the technical stuff you are asking as far as administration is concerned you may wish to try webmin:
```
:~sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.520_all.deb
:~dpkg -i webmin_1.520_all.deb
```
you might get an error about dependencies but follow the instructions and it will fix itself

You could look at ebox (now called zentyal) [http://www.zentyal.org]("http://www.zentyal.org")  but this has some limitations that can be worked around if you have the basic knowledge of the applications involved.

If you must install a gui on your server this how to will give you a basic gnome desktop: [http://community.spiceworks.com/how_to/show/156]("http://community.spiceworks.com/how_to/show/156")

Alternatively there is always the command line;)

---

### Post by gordintoronto on 2010-11-20
Hi Scorpio,

I'm happy to use the command line when I must, but I prefer a GUI. Lubuntu is pretty lightweight, so it might give acceptable performance on your old machine. Does it have a CD drive? If so, you could try Lubuntu by downloading version 10.10, burning the image to CD and booting the old machine from it.

In my experience, that's faster than trying to figure out what parts of an HCL are still relevant.

What kind of server do you want to run? File? Domain controller? FTP? Web?

I must admit, I've picked more modern computers off the curb than what you have, but none of them had as much memory.

---

### Post by scorpiooooooh on 2010-11-21
@ Wojox - Thanks for the link.  It was the first lead that I looked into and found some very interesting things there.  One of the more interesting things I found was that the 3Dfx (STB)Voodoo 3000 is very well supported.  Who'd a thunk an old gamer card would be the bees knees with Linux (apparantly the cat's a$$ is disallowed here.).

Only one of the SCSI cards I have was listed in the HCL, that kind of surprised me.  The Antares card, A U160 which came out of a Sparc, was not listed, but cards with very similar controllers were on the list. I was subsequently informed that most of the older HW is most likely supported even if it is not on the HCL. I take that as meaning it is more or less taken for granted that older stuff that was pervasive back in the day is generally supported...mostly....pretty much.  

@ capscrew - Re. chipset support, I thought that may be the case, like only 30% sure, but I love the warm fuzzy feeling of confirmation, or affirmation, or somethingmation...  Nearly assured backward compatability is usually the case with WIntel systems too so it makes sense, but Ubuntu is a whole differnet animal,literally.  Choosing the version/distro by kernel is great advice.  

While collecting drivers today, I noticed that kernel ver. seems to be far more relevant than anything else.  It's funny you recomend 8.04 as that was the version I was shooting for.  Mainly 
because of the age of my HW and the LTS tag which in my book equates to stability.

You are correct in your thinking about desktop being a better place to start, but your conventional wisdom may not apply here.  For I am a martyr and I do things the hard way, even if it seems counter intuitive to all rational reasoning.  I am a firm believer in baptisim by fire, jumping in feet first, etc. because the more pressure I am under, the better I perform.  Do the heavy lifting first and the light stuff later because starting with the lighter stuff may wear one down to a point where they may not have the strength to do the heavy lifting later on.  My methodology is probably not good for most folks because most folks have common sense. ;)

I will likely start with server, learn by trial and error, get it right (probably painfully) and then build a workstation later on with a nice sexy GUI and all that jazz.  So, I shall take the advice you and some others gave and go with the CLI on the server.  I still use command prompts in MS systems and a bit on Cisco routers and fully realize the awesome powers of the CLI, they who master the CLI are masters of their domain... okay, that was corney. 

About the ACPI, I should have mentioned that the statement applies, as far as I know, to the VIA Apollo Pro 133A chipset boards because, on Linux systems, they are prone to IRQ Storming, with ACPI enabled.  When I started my "nerdcore lyfe" (the first system I ever assembled was a smoking fast 33MHz i386 with a whopping 2 MB of RAM and a 60 MB HDD)  every add on board had the 
troublesome jumpers for IRQ DMA and just about every other setting now handled by PnP.  As I mentioned before, I do things the hard way.  When I set up HW for my own use or build a special
purpose server with weird or fickle HW, I use a switch in the install routein (on NT Technology based systems) that prevents ACPI from being used at all.  Because I have this "old school" mentality, I sometimes prefer to take complete control over resource allocation lest I be cornered into forcing HW to share and play nice with each other.  As you probably know, not all HW wants to share and many mobos fail miserably at arbitration.

Answers should always lead to new questions.


@ barrydocs - Thanks, I'll look into them.

@ gordintoronto - As you probably read in the above text, I've decided to go the CLI route.  I'm not opposed to using the CLI, in many situations a skilled tech can get things done more efficiently with it, in other situations, it is practically necessary to use it. Systems often get cluttered with icons and bling.  Whenever faced with those situations, I frequently run to 
the command prompt.  I cannot help but laugh, usually under my breath, when users ask..."What's that?  Somethings wrong, I've never seen that before."  Acting as if the little innocent blinking cursor is going to eat up all the words on their hard drive. I just wanted to see what the pretty Ubuntu GUI looks like but it can wait till I build another heap to load desktop on.

To answer your question about server type, the answer is yes, yes and yes.  I'd like to start with a simple file server, then look into DCs, but ultimatly my objective is to build a web/ftp server with a back end SQL server.  I may even (just for fun because I'm sick in the head) build a multihomed DC/NAT router.  I have heard that Linux is fast, secure and competent as a routing platform. Unix based IP routing is what made the Internet possible after all.  I have FiOS and plan on disabling NAT on the router which will allow me to play with my own HW routers on the one dynamic IP I get now.  I may have to upgrade my account to get static IPs, 5 static IPs for $99/mo is the going rate, but I'm pretty sure I can work something out using DDNS that will allow me to play with my stuff on the cheap, just for now. 

I do not consider 1.5 GB of memory an aweful lot now days.  Most of my WIntel systems have 2 GB or more installed.  I am even thinking about throwing a 2K Advanced Server together just because I want to see how the /3GB switch works on a box with 8GB of memory.  <sigh> I need a life.  But that's one of the things I find attractive about Linux, it's not a resource glutton like Winduurz is.  Maybe 1.5 or 2 GB is huge in the Linux world.  I dunno.  The reason I chose the dual proc P3 mobo is that it is rock solid.  It has proven itself as the most stable system I have ever built and owned to date.


Here is a bit of info about some of the other things I'd like to have a whack at.  Besides being a puter nerd, I also do professional graphic arts design and video production.  as a matter of fact, the old mobo I'm using to build the Linux box is a pull from the first graphics/video editing/gaming workstation I built.  At some point, I'd like set up a personal web server to host my family home videos on, something along the lines of youtube just for my family and maybe a few friends.  The video will be flv encoded or maybe even remain in it's native format and be encoded/recoded to flv using VLC Media Player which has streaming server and recoding on the fly built into the app. VLC is freaking awesome and it's open source to boot.  Using VLC I can stream on demand or broadcast without the need for a proprietary player on the user/viewers PC.  Anyone with a web browser and java can watch the videos.  Pretty neat if you ask me.

Now, as far as my family is concerned, I'll just be regarded as the good (albeit nerdy) son, brother, uncle (I have 6  sisters btw), cousin and friend.  But I do have ulterior motives, if I 
can pull this off, I have a whole bidnezz model all ready to go based on this setup.  As is often the case with mad aka insane scientists, I'll be using my friends and family as the unsuspecting lab rats while I hash out a proof of concept design.

VLC is awesome and very worth checking out even if you just need a good video player that can play just about ANY media file type and also recode video from nearly every format to any format you desire.  You can also use it to capture video streams.

Lastly, I'd like to thank all who responded so far for the good advice and prompting some other thoughts about how to use Linux.

---

### Post by HermanAB on 2010-11-21
Howdy,

I think you fret too much!  Just go ahead and install Ubuntu.  Chances are that everything will work just fine, without having to go and hunt down special device drivers.

Relax and enjoy your 'Buntu system.

---

### Post by yettiman2208 on 2010-11-21
Ill add my .02 to this post.

Although I cannot add any useful comments/answers to many of your questions I can say this.

I would recomend against going with a gui server environment. I know some people advise loading up the desktop environment and learning from there. My response is this. I started messing with linux desktop awhile ago and while I did learn my way around the cmd line somewhat I still found myself resortin to GUI enhancements that took the place of cmd line usage. When I went to install my server I decided to go with a headless and GUI-less version. What I learnt from the desktop environment didn't help all that much IMHO. 
So, I would just go ahead with the energy savings and go with a headless environment and you will learn quickly enough any cmd line deficiencies that you may have (I know you have lots of experience with tech, so I doubt you will have much trouble at all).

Also, just run a live CD test of the desktop environment to determine whether your hardware is adequately supported for your needs. Then go back and install server when you find a HW combo that works for you.

---

### Post by scorpiooooooh on 2010-11-30
Whelp, I am writing this post from my Ubuntufied workstation.  I wound up loading 8.04.4 LTS Desktop for now.  I cannot say the install was smooth but things seem to be working pretty good.  There are still a few weird things going with the hardware, but all in all I'd say the install was a success.  A big thank you to all who pitched in.

---

### Post by yettiman2208 on 2010-12-01
congrads and good luck

-a large yetti

---

### Post by James78 on 2010-12-01
> **scorpiooooooh said:**
> Whelp, I am writing this post from my Ubuntufied workstation.  I wound up loading 8.04.4 LTS Desktop for now.  I cannot say the install was smooth but things seem to be working pretty good.  There are still a few weird things going with the hardware, but all in all I'd say the install was a success.  A big thank you to all who pitched in.
If you want to see if the latest 10.10 works with your computer, you could get the ISO and make a bootable USB using the StartUp Disk Creator (really easy to use!), then if it boots and works, like said earlier, it's probably a-ok. I just like the latest versions. :) I feel that LTS releases are really suited for servers (definitely), but really, who wants to have the same old Desktop computer when each release keeps getting more and more wonderful? You'll get a feel to see if any of the newer ones work by using a LiveCD (it's probably worthit to try it out!). Most likely, it'll work, it usually does, and if some things don't they're usually fixable with some persistence! Posted from Kubuntu 10.10. :)

P.S. If you go 10.10, you might want to upgrade the kernel from 2.6.35; I can't stand it, it has memory problems and is slow, where the stable 2.6.36 (from which I'm currently using) is much better.

Enjoy all the testing and awesome satisfaction that comes with learning Linux! The terminal is truly awesome. You can do so many things (you'll see!!). I really feel that Microsoft cut the heart out. Make it user friendly, make it GUI friendly, ok, but don't cut out the usability by cutting out a good terminal and good programs!

---

### Post by scorpiooooooh on 2010-12-01
> **James78 said:**
> If you want to see if the latest 10.10 works with your computer, you could get the ISO and make a bootable USB using the StartUp Disk Creator (really easy to use!), then if it boots and works, like said earlier, it's probably a-ok. I just like the latest versions. :) I feel that LTS releases are really suited for servers (definitely), but really, who wants to have the same old Desktop computer when each release keeps getting more and more wonderful? You'll get a feel to see if any of the newer ones work by using a LiveCD (it's probably worthit to try it out!). Most likely, it'll work, it usually does, and if some things don't they're usually fixable with some persistence! Posted from Kubuntu 10.10. :)

P.S. If you go 10.10, you might want to upgrade the kernel from 2.6.35; I can't stand it, it has memory problems and is slow, where the stable 2.6.36 (from which I'm currently using) is much better.

Enjoy all the testing and awesome satisfaction that comes with learning Linux! The terminal is truly awesome. You can do so many things (you'll see!!). I really feel that Microsoft cut the heart out. Make it user friendly, make it GUI friendly, ok, but don't cut out the usability by cutting out a good terminal and good programs!
Your suggestion to use a USB drive is a good one but the system I am "testing" does not support booting to USB devices.  I can't even get a USB 2.0 PCI card to work. :(

When I move on to the server edition (probably 10.10) I'll be using a board that is much younger and supports booting to USB.  When I get to that stage, USB will be my first choice.  I want to install the newer sever version ASAP but I doubt I will be using the pretty interface.  

For now, I have to work out why my NICs keep going all funky on me when I reboot.

---

