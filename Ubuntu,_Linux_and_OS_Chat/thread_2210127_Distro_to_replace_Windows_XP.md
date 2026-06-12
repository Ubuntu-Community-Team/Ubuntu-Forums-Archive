---
title: "Distro to replace Windows XP"
date: 2014-03-09
forum: Ubuntu, Linux and OS Chat
---

### Post by Jay_Rios on 2014-03-09
As the title says, i am a new Linux user. I have 3 desktops, one has Windows 7 and the other 2 have Windows XP. As you all might now, Windows XP will no longer be supported come April so i need an alternative. Upgrading to Windows 7 or Windows 8 is out of the question as both Windows XP desktops are old and they probably wouldn't be able to handle that bloated OS.

Anyways, if you could please give me some pointers that would be great! Maybe post some links to things that a beginner needs to know. I guess stuff like how to use the firewall and anti virus if there are any. Anything and everything that might be important.

Here are the specs to both Desktops.

[COLOR=#000000]1.[/COLOR]
[COLOR=#000000]Intel Celeron 2.40 Ghz[/COLOR]
[COLOR=#000000]1 GB RAM[/COLOR]
[COLOR=#000000]32 bit[/COLOR]

[COLOR=#000000]2.[/COLOR]
[COLOR=#000000]Pentium 4 CPU 2.40 Ghz[/COLOR]
[COLOR=#000000]480 MB RAM[/COLOR]
[COLOR=#000000]32 bit[/COLOR]

[COLOR=#000000]The second one was actually given to me by someone that no longer used it or wanted it. The weird thing is that it has 512 MB but only reads 480 MB, why i don't know. I will upgrade it to at least 1 or 2 GB though but if i can run Lubuntu on it for now that would be great.[/COLOR]

Thank you for taking the time to read this and help. I really do appreciate it!

---

### Post by Lars Noodén on 2014-03-09
You might look at Xubuntu or Lubuntu.  They, especially Lubuntu, are a bit lighter though Xubuntu is more flexible.  You can try the Live DVD to see what you think of them.  If you use DVD RW or a USB stick to boot then you can reuse the storage medium later.  

As for firewalls, a [firewall is not really needed](https://help.ubuntu.com/community/DoINeedAFirewall) for the desktop.  If you do feel compelled to try one, then the place to start would be [UFW](https://help.ubuntu.com/community/UFW) which is a front-end for the built-in packet filter iptables.  

About [anti-virus](https://help.ubuntu.com/community/Antivirus), GNU/Linux is designed in a way that minimizes the ability for malware to run.  The biggest risk would be trojans (which have to be installed) or maybe things running WINE.  As long as you install only from the repositories you eliminate much of the risk for the former.  If you are really worried about the latter you can try ClamAV to protect from Windows malware.

---

### Post by Impavidus on 2014-03-09
Maybe you can post some details on the hardware of those XP machines. CPU, RAM, graphics.

Chances are that they are not powerful enough to run the full Ubuntu, but Xubuntu (lighter) and Lubuntu (extra light) will most likely run with a good headroom for your applications. As you still have a Win7 desktop for your critical stuff, there is no reason to complicate matters by dual booting (which, BTW, isn't very complicated). You can try them all from a live disk and, if you are happy, install them using the entire disk. Make backups of all files you want to keep on an external drive or on your Win7 machine, as everything on the entire disk (not just on the "C drive" or "D drive", as windows calls them) will be deleted. Try Ubuntu 12.04 or 13.10, Xubuntu 12.04 or 13.10 or Lubuntu 13.10.

By default, Ubuntu is pretty secure already. Your main weapon against malware is being careful, instead of installing antivirus software and forgetting about it (the Windows way, not very secure though). Others can tell you more about security.

---

### Post by Gordonbp531 on 2014-03-09
The only reason you may like to consider using an AV program is if you receive and send files from and to Windows users - to protect them from themselves!

---

### Post by Rob Sayer on 2014-03-09
I use clamtk antivirus but only on demand on dl'ed files.  I still have a windows 7 partition (rarely used), and I might give a file to a windows user.

To put it into perspective:  I only installed ubuntu a few years ago but I know some fairly serious geeks.  Some have been using linux on their personal machines for 20 years ... they didn't install with a live CD, believe me.  Not *one* of them uses an antivirus program like a Windows user would need to.

It's hard to recommend a specific desktop version without knowing the RAM, but lubuntu or xubuntu for an xp machine sounds good.  Lubuntu is *much* faster than xubuntu but configuring it is more difficult for a beginner.  So while I actually prefer lubuntu at this point I'd probably recommend xubuntu more to a novice.

The main thing I'd say with old hardware or things like netbooks is that some desktops require 3D accelerated video just to run *themselves*, eg. unity or cinnamon.  Avoid these like the plague.

One thing I did before installing ubuntu which I'd highly recommend is to go into system information in windows.  Make a note of all your devices, esp. the graphic and wireless adapters.  Then do a search for linux + that particular device.  If there have been problems they'll show up here and askubuntu.

---

### Post by buzzingrobot on 2014-03-09
Welcome to the happy world of Linux.  Some general info:

Ubuntu has fostered several derivative distributions that are, esentially, Ubuntu using a different interface.  Those are Kubuntu, Ubuntu Gnome, Xubuntu, and Lubuntu. Each of these have sites that can be easily found by a search.

Some of those versions, particularly Lubuntu, may work better (faster) on less powerful hardware.

In addition, a large number of independent distributions build their own releases on Ubuntu. The most widely-used is Linux Mint, which is also available in multiple version with different interfaces.  

All of these distributions offer "Live" installations images.  These can be burned to a DVD or USB stick, and booted.  You will be given a choice to install the system or to run it off the DVD/USB.  Doing the latter is, I think, the best way to safely get a taste of a distribution to see if you like it enough to consider installing it. (It's also a good way to check hardware compatibility.)  Here, on this download page at ubuntu.com ([http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)), you will find midway down the page on the right instructions about using a Live image and burning them on DVD's or USB's.   

Looks like you intend to replace Windows with Linux, rather than install Linux in a dual boot scenario.  That will simply things. All the distributions I've mentioned use essentially the same Ubuntu installer.  That installer offers options to install Linux as the only system on the machine, to install it alongside (dual boot) Windows, or to do "Something Else", which means manual partitioning. (You should not attempt manual partitioning unless you understand partitions and have sketched out a partitioning layout for you drive(s).

Here's a link ([http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)) to the Ubuntu page on installing the current (13.10) version. A web search will find dozens of "installing Ubuntu for newbies" hits.

I'll suggest not jumping into the deep end on this. Doing a little background research to familiarize yourself with some of the Linux basics will pay off in reducing frustration. (One example;  While in Windows software is typically downloaded from a source, and includes its own de-installation routines, Linux does it differently.  Software is created in "packages" that usually require the presence of other software -- "dependencies" -- on the system. Distributions, like Ubuntu, keep their software on servers called "repositories". Linux systems include programs that will display the software available in those repositories, and then download and install selected programs, along with the dependencies.)

(Firewalls:  Ubuntu installs a firewall tool called "ufw".  No GUI configuration tool is installed by default, but a very easy one -- "gufw" can be installed from the repositories. Gufw is a firewall configuration tool that you can use to enable or adjust the firewall.)

(Anti-virus:  Yes, if your Linux machines exchange Windows-based mail, etc., with Windows systems.  Otherwise, I think it's overkill on a Linux system used and maintained by someone who  knows enough to avoid clicking on anything that looks interesting.)

Finally, consign your first couple of install efforts to be learning experiences.  If they work, great. If not, post questions here and try again.

---

### Post by p2bc on 2014-03-09
Hello, and good luck. I say good luck only because you are entering a new "world" so to speak, that will seem like and adventure at time full of excitement, and daunting in others. Either way I am sure you will love the experience.

If I can offer a somewhat crude expression, but one that I believes accurately depicts using Linux and all it nuances is; "There are many ways to skin a cat."
At its core, that expression mean there are many ways to get the same result, not all of them are right or easy, but you will get the job done. This is also true for Linux, as you can see with all the varied distros, and just figuring out which one to install. This is why everyone is suggesting trying it out on a LiveCD first. So I will off some guidance to what to do after you install.

First and for most; Read!
There are plenty of sites out there to get your feet wet. Read as many as that interest you and as much time will allow.

[help.ubuntu.com]("http://help.ubuntu.com")
[help.ubuntu.com/community]("http://help.ubuntu.com/community")
[www.linuxjournal.com]("http://www.linuxjournal.com")  .
[www.ubuntugeek.com]("http://www.ubuntugeek.com")
[www.upubuntu.com]("http://www.upubuntu.com")
[www.howtogeek.com]("http://www.howtogeek.com")
[www.liberiangeek.net]("http://www.liberiangeek.net")

One particular site I really appreciated when I started out was;
[ubuntuguide.org]("http://ubuntuguide.org")
It was great to offer different applications, to do the same thing (see expression), but offered explanations on their differences so I could make informed decisions. I tried some, found others, but it was a good starting point.


Second: The first thing I would say to do, before anything else, after you have yourself a fresh install, would be to install "synaptic"
```

sudo apt-get update && sudo apt-get install synaptic

```

The default "Software Centre" from Ubuntu is fine if you decide to use Ubuntu, but it is overwhelming at first. As for the other distros, they don't all have a handy application/software installation program. Synaptic will allow you to install programs and application with all their dependencies easily. It is all well and good to read and find all the cool stuff to install, but it is not so cool when you can't install it properly. In Synaptic you simply start typing the name of the application and it will show you a list relating to that search. You will still have to read to make sure you are installing right thing but you will have an easier time with Synaptic. Once you are feeling a little more confident you can get your geek on with apt-get or aptitude. :)


Third: What videos.
[Youtube.com]("http://Youtube.com") is full of people offering advice on Linux.
[Linuxjournal.com/video]("http://www.linuxjournal.com/video") have plenty of handy stuff.
[CBTNuggets.com]("http://CBTNuggets.com") has some if you are willing to pay.

Regardless of the source of the video, if you don't have a grasp of the lingo, the terms and the operations the videos won't do much good. Reading and familiarizing yourself, see First, will be an asset before watching any video.


Four: You have done it already, visit ubuntuforums.com, or any forums and ask questions. I myself have been using Linux since 2007, and I still need to ask questions. Sometime I have an answer but I am not sure if it is the best answer, see expression, to get the right result. And remember, the only silly question is the ones you don't ask.  :)

---

### Post by pqwoerituytrueiwoq on 2014-03-09
This post contains links are will open the software center on ubuntu, they will not work on your windows installs

14.04 LTS come out in April, about a week after XP kicks the bucket, the pre-release is available, you will feel right at home with xubuntu after you move the top panel to the bottom of the screen
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/trusty-desktop-i386.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/current/trusty-desktop-i386.iso) - 32 bit disk image
[http://cdimage.ubuntu.com/xubuntu/daily-live/current/trusty-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/current/trusty-desktop-amd64.iso) - 64bit disk image (unless you re running something like pentium 4 use this one)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) - create a bootable USB drive
[http://infrarecorder.org/?page_id=5](http://infrarecorder.org/?page_id=5) - Burn Disk Image to dvd
[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule) - release schedule

if your prefer [chrome]("apt:chromium-browser") over firefox, i suggest reading this so you can have the latest flashplayer
[http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html](http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html)

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs) - enable dvd playback

unless you are connected directly to the Internet at your modem and not using a router you don't need a firewall ([gufw]("apt:gufw")), as a router is a firewall
most anti-virus programs in linux are just for server use to protect windows users, or for protecting your network share for windows users

as the last guy said synaptic is good, you can find it in the software center along with other stuff like [libreoffice]("apt:libreoffice") and way too many others to list

there is no need to deal with registry cleaner or defraging, there is a disk cleaner called [bleachbit]("apt:bleachbit")

[http://alternativeto.net/](http://alternativeto.net/) can be used to find alternative to your windows software, if you cant find a suitable one give [wine]("apt:wine") a try

---

### Post by whitesmith on 2014-03-09
Many folks new to Linux can't understand why a firewall or AV protection aren't part of Linux.  The answer is simple: the architecture of this professional OS makes them generally superfluous. A firewall or AV protection might be needed if you run Windows software on Linux (under Wine, say) as the superuser; otherwise they offer nothing but wasted processor cycles. I strongly recommend that you digest the first of the links in my sig line to understand that **Linux is not free Windows.** There is a certain non-monetary price that must be paid to use it -- time and a new way of doing things are part of this indirect cost. Good luck to you!

---

### Post by newb85 on 2014-03-09
A lot of great advice in this thread so far.

If you're going to be sharing files between your Linux and Windows machines, I recommend you install AV...on your Windows machine.  If you're not, I recommend you install AV on your Windows machine.  :)  

I'm not sure I agree with the synaptic advice.  The Software Center seems to me to be more straight-forward for novice users.  My recommendation would be to try out the SC first, and if it seems confusing or you need more in the future, you can always add Synaptic.

---

### Post by rburkartjo on 2014-03-09
check this out

[http://www.itworld.com/open-source/407924/best-linux-distros-replace-windows-xp](http://www.itworld.com/open-source/407924/best-linux-distros-replace-windows-xp)

---

### Post by pqwoerituytrueiwoq on 2014-03-09
> **newb85 said:**
> A lot of great advice in this thread so far.

If you're going to be sharing files between your Linux and Windows machines, I recommend you install AV...on your Windows machine.  If you're not, I recommend you install AV on your Windows machine.  :)  

I'm not sure I agree with the synaptic advice.  The Software Center seems to me to be more straight-forward for novice users.  My recommendation would be to try out the SC first, and if it seems confusing or you need more in the future, you can always add Synaptic.if something gets messed up with the package manager it is easer to fix (if you prefer a GUI to a terminal), obviously it is hard to install synaptic when you are having such a issue

---

### Post by Mark Phelps on 2014-03-09
Some of us like Synaptic simply because it does not hide the activities taking place when we install something.  While it's not necessarily one-click, it also doesn't hide what's going on.  

But then other folks would prefer to click an icon or button and have everything happen behind the scenes.

That's one thing that's great about using Linux -- you have choices on how things get done.

---

### Post by Rex Bouwense on 2014-03-09
There is a great deal of information in the previous posts.  Just remember, this forum is composed of mostly very friendly people with experience in Linux OS that range from zero to uber-geek.  If you have a problem or a question, feel free to ask for help.  There is no such thing as a stupid or too simple question.

---

### Post by pqwoerituytrueiwoq on 2014-03-09
> **Rex Bouwense said:**
> There is a great deal of information in the previous posts.  Just remember, this forum is composed of mostly very friendly people with experience in Linux OS that range from zero to uber-geek.  If you have a problem or a question, feel free to ask for help.  There is no such thing as a stupid or too simple question.
with the only possible exception being "is this a stupid question?"
@Mark Phelps
and it does not have a habit/history of crash or hiding a user input prompt in my experience

---

### Post by PondPuppy on 2014-03-09
I really don't have much to add to the great information others have posted, except to note that Puppy Linux is made to install to a flash drive, and is easy to use. If you don't want to mess with your XP installation until you have a feel for Linux, you could try Puppy. Or Porteus, which is similar and is quite snappy on old hardware. Enjoy Linux -- it's a great world.

---

### Post by Jay_Rios on 2014-03-10
I want to thank everyone that stopped by to offer help. I really appreciate you all taking time to help me with this because other wise i would have been lost lol. Some of you want to know the specs to the PC's so i will post them in the OP as well as here for those of you that might see this message.

1.
Intel Celeron 2.40 Ghz
1 GB RAM
32 bit

2.
Pentium 4 CPU 2.40 Ghz
480 MB RAM
32 bit

The second one was actually given to me by someone that no longer used it or wanted it. The weird thing is that it has 512 MB but only reads 480 MB, why i don't know. I will upgrade it to at least 1 or 2 GB though but if i can run Lubuntu on it for now that would be great.

Once again thank you for the help!

---

### Post by Vladlenin5000 on 2014-03-10
> **Jay_Rios said:**
> The second one was actually given to me by someone that no longer used it or wanted it. The weird thing is that it has 512 MB but only reads 480 MB, why i don't know. I will upgrade it to at least 1 or 2 GB though but if i can run Lubuntu on it for now that would be great.

It has an integrated graphics chipset. 32MB is the video memory assigned and reserved to it. You can probably change that value in BIOS. You may also add a better graphics card - AGP or PCI, not PCie - and by disabling the onboard one you'll then see the full 512MB.

---

### Post by pqwoerituytrueiwoq on 2014-03-10
> **Jay_Rios said:**
> The second one was actually given to me by someone that no longer used it or wanted it. The weird thing is that it has 512 MB but only reads 480 MB, why i don't know. I will upgrade it to at least 1 or 2 GB though but if i can run Lubuntu on it for now that would be great.
Lubuntu/Xubuntu should run on that system, but 1gb of ram would make a world of difference when actually doing work
the missing 32MB of ram is being used my the integrated GPU
on linux that GPU will run 1920x1080 if you tell it to, on windows i could not get over 1366x768 on my old pentium 4 system

---

### Post by C.S.Cameron on 2014-03-10
The Register has done a quick review of some of the 14.04 flavors:

[http://www.theregister.co.uk/2014/03/10/ubuntu_flavours_review/](http://www.theregister.co.uk/2014/03/10/ubuntu_flavours_review/)

---

### Post by spock3 on 2014-03-11
Thanks all who contributed to this thread being very informative.

I suspect many other new to WinXP/7/8 -> Linux Ubuntu converts will find this info valuable as well.

Using a boot from Ubuntu CD or Thumb Drive option, can you view the WinXP files so as to archive them to a previously
defined Ubuntu One cloud account in advance of subsequently conducting a full, on disk installation of Ubuntu?

* Have 2 older WinXP units not currently operable due to XP O/S corruption or missing DLL's.

Please confirm that use case can be achieved?

Thanks

---

### Post by deadflowr on 2014-03-11
> **spock3 said:**
> 
Using a boot from Ubuntu CD or Thumb Drive option, can you view the WinXP files so as to archive them to a previously
defined Ubuntu One cloud account in advance of subsequently conducting a full, on disk installation of Ubuntu?
.
\Please confirm that use case can be achieved?

Thanks

Do you mean can you boot a liveCD and go quickly save your files to UbuntuOne?
Well, you can save your files easy enough.
I've never booted a livecd and connected to Ubuntu One before, but should be easy and possible.

This is, of course a guess as to what you mean.

---

### Post by snazzierella on 2014-03-11
I'm running Lubuntu 13.10 on a Celeron 2.5 GHz which started out on 256 MB of ram, and it ran alright (though I had to use Firefox instead of Chromium until I got more RAM, after upgrading to 1GB Chromium ran alright). I had to use the alternate install iso to get it to go through the install process properly (this was when I had 256 MB of RAM) but it did work.

---

### Post by mastablasta on 2014-03-11
you can go to ubuntu one form live CD. you can also acces ubuntu one via web browser.

---

### Post by Bucky Ball on 2014-03-11
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by newb85 on 2014-03-11
Of course, the practicality of this approach will depend on the size of what you want to back up and your internet connection speed.

---

### Post by mips on 2014-03-11
> **Jay_Rios said:**
> 
1.
Intel Celeron 2.40 Ghz
1 GB RAM
32 bit

2.
Pentium 4 CPU 2.40 Ghz
480 MB RAM
32 bit

Second PC only has 480MB due to integrated gpu using the other ram.

The second pc or both would be worthwhile upgrading the ram, 1-2GB would be cool and makes a big difference. You don't have to buy new, look for second hand or ask friends if they have any old ram lying around.

XFCE would work fine on both machines but my personal preference would be Openbox as it is really slim & trim, you can look at Manjaro Openbox, Crunchbang & Archbang as they would fly on those machines. I use Manjaro Openbox on a old (2005) Celeron 1.4GHz (OC'ed to 1.86GHz) laptop with 1.5GB of ram and it's really fast! I've had much newer laptops on my desk with Win7 on them and they feel less responsive.

---

### Post by spock3 on 2014-03-11
Yep, you understood the question perfectly ;)

Thanks, Microsoft headed out of my life forever, yeah...

---

