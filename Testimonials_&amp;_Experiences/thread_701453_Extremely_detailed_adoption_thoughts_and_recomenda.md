---
title: "Extremely detailed adoption thoughts and recomendations."
date: 2008-02-19
forum: Testimonials &amp; Experiences
---

### Post by pcloadletter on 2008-02-19
**----- Scroll to the bottom for a shorter Cliff's Notes Version of this post -----**

Greetings Ubuntu Community,

I understand that some of the goals of the Ubuntu Linux distribution and its community is to encourage the usage of free and source software, Linux, security, and to develop an operating system that everyone can use and enjoy. As a result, I thought I might write some thoughts on my recent experiences with Ubuntu, as perhaps they could provide useful information on user experience, to further improve development in the future.

I would like to start off by explaining who I am, and in turn my perspective. I am a 21 year old female, an avid computer user, in fact probably bordering on a computer addict, and I have used Linux, Beos/Zeta/Haiku, Solaris, Windows, Mac OS, on and off over the years. I grew up in the Silicon Valley area, and have been using computers for as long as I remember. Computers do not intimidate me. I am NOT a programmer, nor do I have interest in it. The most important thing to me when using a computer is the ease with which I can get tasks done, the feel of the cyber environment (if its a comfortable place to immerse myself in), and the versatility of it. Essentially, I care very little about the technicalities of an OS, so long as it provides the experience I want. I have no religious allegiance to Torvalds, Gates, or Jobs, I am a computing mercenary. Whatever works best for me, I will use.

I enjoy trying new operating systems, as I have been using using Windows XP happily for years, but I am a bit frustrated by the lack of innovation by many operating systems.  As such, I always try new ones out hoping to find one that will provide the experience leap that happened when we went from Windows 3.1 to Windows 95. I recently decided to give Ubuntu another shot.

What lured me to Ubuntu was its philosophy of Linux for human beings. I am perfectly capable of using a command line, but I simply don't want to, and Ubuntu seemed to have that in mind. Next, Ubuntu has a huge support community. As I find Linux to be an operating system where you are reparteed to need support with things like finding drivers that work and such, and since Linux distro's can have varying needs, I was comforted by the fact that there is a large pool of information on forums like this to search on and find solutions to problems. Finally, from the videos I have seen, the user experience of Ubuntu is appealing from the factory in Hardy Heron. Gnome, Compiz Fusion, its a nice cyber space to be in for hours on end.

When I finally decided to commit to an installation, I had two goals. I wanted it to be non destructive, and I wanted it to work with my hardware. Unfortunately, I am in a unique position with my hardware at the moment. At home in the United States, I have many computer systems to draw upon to do things like burn CDs, look up problems online, and use as a backup while a computer is down. Currently however, I am living in Yokohama Japan, with one laptop as my primary system. This computer cannot be out of commission, at all, ever. Second, the optical drive has ceased to function, which is of course, quite lame.

I found the solution that fit my needs again within the Ubntu community, with the software program Wubi. Wubi allowed me to install Ubuntu on my system as a dual boot, without any fear of nuking my Windows Installation, and without use of the optical drive. I tried playing around with USB jump drive installs and such for a while, but Wubi really made it all happen. I honestly feel that this is one of the most important steps forward for Linux's usability and adoptability.

The first time I installed Gutsy Gibbon with Wubi, everything went smoothly, until Ubuntu tried to load the GUI. All I got was a blank screen, and I had to do a some command line work to get into the x-server driver configuration... yada yada yada. Essentially it was not entirely smooth, but I got it working. Getting it to go up to the correct resolution was another hassle, and I gave up on even trying to get it to do 3d acceleration. It was ticking me off, it was not easy, I deleted it. 

While searching around for a Wubi like installer for Mandriva, or PC Linux OS, which I figured might by some stroke of luck have a better experience with my video card, I bumped into the Wubi installer for Hardy Heron, and I tried that out. The Wubi install went smooth again, and I was into Ubuntu in no time with things working as they should. One hickup in the process, is that now when I startup it goes to something about loading the swapfile swap, and pauses there in the command line, but if I hit ctrl-alt-delete... it unsticks itself and works fine. Odd eh? I just kind of discovered that as I tried to reboot into Windows. Most typical users would have been stumped by this issue, and its annoying that I have to do it every time I start Ubuntu. I will look into fixing it later. 

I installed all of the updates, used it for a while, and had very few issues. I found that the proprietary driver for the video card did not work for me, it simply caused a blank unlit screen, and I found that Rythembox would simply stop working and need to be restarted after 20 minutes or so, but hey it wasn't bad. Ubuntu seemed to be slower than my optimized Windows XP installation, but it was not &#8220;slow&#8221;... it just wasn't quite as snappy. You know, its like comparing a Subaru WRX to a WRX sti, both are quick, but one is quicker.

I was however, loving the interface. I loved the design, I love compiz fusion, I love that there is no crapware installed (in fact most of the included programs are top rate), and I love the multiple desktop integration. Like I have banged on about earlier, its a nice place to compute in. I had some issues in programs, but this version is still in beta stage, and I understand that, and will not complain about them until the final release makes it clear if they are addressed or not. I also enjoyed all of the software that was freely available, and was higher quality than much of the free software available for Windows. I spent very little time adjusting to the new software, as in Windows I use Open Office, Pidgin, Thunderbird, etc.

I noticed something strange after having it on my computer for a day. I was using Ubuntu more than I was using Windows XP. I installed some themes, a new backdrop, some programs, and started moving into the cyber space. I was starting to like it.

There is one, major complaint I still have about Ubuntu. I hate the method of installing programs. I hate messing with packages, I never want to see the commands &#8220;sudo&#8221; &#8220;wget&#8221; &#8220;install&#8221; or anything like it again. Synaptics is a nice package manager, and I like having repositories, but for me they are so unbelievably slow. I wish constantly I could simply click on a program, download it, and double click an installer like in Windows. 

Unfortunately, one of the recent updates I did today to my Ubuntu installation, nuked it, and the thing started booting to a command line. Rather than dealing with that (are you noticing a pattern here about command lines?), I went into Windows, uninstalled Wubi, and reinstalled the OS, which since I had only been using it for a day was no loss at all. Now I am back in Ubuntu, and I am hoping whatever happened last time, will not happen again with the update. If if does, I will wait for the official Heron release, or switch to Mandriva, Suse, or PCLOS and try those out.

Here is my checklist for what I believe Ubuntu needs, to truly become a product that I would install on all of my computers, and more importantly for the growth of this OS, on the computers of my family and computer illiterate friends.

1.Wubi needs to become an official installation method.
2.You need to never, ever see a command line unless you want one. Sure they annoy me, but they scare the living bejesus out of most new users. Seriously, take a note from XP and Mac OS. No command lines, ever. In fact, it would be great if we never saw them during boot either.
3.One touch installation is necessary. Installing programs is way too difficult at the moment. I had to Google for how to install Skype, I never could get gnome-go at the time of writing this, repositories are slow for me I'm getting 16.5kps down at this very moment, and they just dont have everything. They are a great resource, but this is simply not enough. Users need to be able to install programs easily, and whatever programs they want. Right now I feel like I am either on training wheels, or I am thrown into a pit to do gladiatorial combat with the command line. 
4.Drivers need to be sorted out. I know people are working on developing drivers for Linux, I accept that, but we really need a better way to manage them. We should not be simply getting everlasting blank screens... we should get a blank screen for 30 seconds and if you don't hit okay... it switches back.

I know that there are some some solutions to these concepts in progress, and I know that there are arguments against them. I must stress, that Ubuntu from my understanding is to supposed to be the Linux for everyone, We need to start easier, and then allow people to work their way up, rather than asking them to commit and learn things at a pace they are uncomfortable or unwilling to adopt.

There are two things I would like, but these are not &#8220;necessary&#8221; like I consider the earlier list.

1.I would like to be able to emulate my Windows XP install from my Wubi installed Ubuntu installation.
2.I would then like to be able to emulate my Wubi installed Ubuntu, from Windows XP.

This would allow me to be in a no loss situation, I simply choose which operating system is best, but I am not without the functionality of the other. Again, there are ways of doing this, and I am working on implementing them for myself, but it should really be a lot easier than it is. The software is out there to do it, it just needs a more streamlined installation and interface.

Thank you for reading my thoughts, I am going to post this up on my blog as well at &#8220;thedigitalkitty.com&#8221; and I will probably post more about my Ubuntu thoughts as the process goes on. I will also let you know whether I decide to keep running both Ubuntu and XP, adopt Ubuntu unilaterally on my non gaming equipment, or if I go back to XP again and wait to see what Windows 7 turns out like. If I had to say where I am at now, I am bothered by Ubuntu but see potential in it, however I would not put money on it just yet.

Best wishes

**----- Cliff's Notes for the lazy or time conscious reader -----**

**Who I am**
     21 year old computer literate female

**Why I chose to try Ubuntu**
     large community to draw knowledge from
      easy of use philosophy
      good design

**How I did it**
      wubi
      Gutsty, then replaced with Hardy

**Results**
     Love gnome with compiz fusion
     Love Wubi
     Like the community
      Display issues &#8211; switch to heron fixes it
      Update nukes install
      Reinstalled, enjoying, hoping for nuke-less future.
      Hate installing programs
      Hate slow repositories
      Hate the command line 
      No faster than Windows XP at this point

**Suggestions**
      No command line ever unless the user wants it
      Easier program installation (one clck perhaps)

**The future**
      Hopeful for Ubuntu
      Eagerly waiting for stable release of Hardy Heron
      Not convinced yet.

---

### Post by lespaul_rentals on 2008-02-19
To be perfectly honest, the only distro I found that never required me to use the command-line interface, ever, was openSUSE.  Linux is an advanced operating system and as such, the user should be prepared to use the command-line interface.  Same with program installation, etc.  Linux is far more advanced than, say, Windows, and users should be comfortable or at least willing to compile software and the like.

Thanks for your review.  Hope you stick around.   :)

---

### Post by pcloadletter on 2008-02-19
> **lespaul_rentals said:**
> To be perfectly honest, the only distro I found that never required me to use the command-line interface, ever, was openSUSE.  Linux is an advanced operating system and as such, the user should be prepared to use the command-line interface.

Thanks for your review.  Hope you stick around.

Thank you for the OpenSUSE mention, I might look into that option. I understand the sentiment of being prepared for what you get yourself into, however I suggest that command line necessity is a barrier to the ultimate goal of Ubuntu's stated "it just works" paradigm.

I do believe the command line is a powerful tool however, that should be available for power users and those knowledgeable of its functions.

---

### Post by SunnyRabbiera on 2008-02-19
well with the installation thing, actually I find installing packages in ubuntu to be easy, heck in many ways installing something in ubuntu can be easier then installing something in XP.
I mean compare Ubuntu's package installation process:
download package and needed dependencies, or use add/remove, or use synaptic... all of them are easy for me compared to:
Next, next, I agree, next, next, enter code on box, next, next, finish, restart...
a good percent of programs work like that on windows.

---

### Post by pcloadletter on 2008-02-19
Don't you agree that one touch would be easier? For example, installing Firefox plugins. 

Also, I don't think hitting next, next, next is such a bad thing. It makes sense, and allows for a linear progression of events that is self explanatory. Though you say it is, I don't think hitting "next" is a difficult thing to do, perhaps monotonous if there are many such buttons in sequence, but its not difficult nor confusing.

I find it annoying that I need directions to install certain programs.

---

### Post by armandh on 2008-02-19
fix the drive

---

### Post by pcloadletter on 2008-02-19
> **armandh said:**
> fix the drive

Not possible at the moment. Anyway, this time it installed and updated without nuking, so theres no problem for now.

---

### Post by lespaul_rentals on 2008-02-19
> **pcloadletter said:**
> Don't you agree that one touch would be easier?

You'll like openSUSE's One-Click Install!

[http://en.opensuse.org/Standards/One_Click_Install](http://en.opensuse.org/Standards/One_Click_Install)

---

### Post by jken146 on 2008-02-19
> **pcloadletter said:**
> Don't you agree that one touch would be easier? For example, installing Firefox plugins. 

Also, I don't think hitting next, next, next is such a bad thing. It makes sense, and allows for a linear progression of events that is self explanatory. Though you say it is, I don't think hitting "next" is a difficult thing to do, perhaps monotonous if there are many such buttons in sequence, but its not difficult nor confusing.

I find it annoying that I need directions to install certain programs.

You only need directions to find out how to install programs because you've never done it before.  Complaining that Ubuntu isn't the same as Windows isn't a very sensible approach IMO.

---

### Post by David Ostrom on 2008-02-19
> I mean compare Ubuntu's package installation process:
download package and needed dependencies, or use add/remove, or use synaptic... all of them are easy for me compared to:
Next, next, I agree, next, next, enter code on box, next, next, finish, restart...
a good percent of programs work like that on windows.

I love it:lolflag:

---

### Post by tvdxer on 2008-02-19
> **SunnyRabbiera said:**
> well with the installation thing, actually I find installing packages in ubuntu to be easy, heck in many ways installing something in ubuntu can be easier then installing something in XP.
I mean compare Ubuntu's package installation process:
download package and needed dependencies, or use add/remove, or use synaptic... all of them are easy for me compared to:
Next, next, I agree, next, next, enter code on box, next, next, finish, restart...
a good percent of programs work like that on windows.

I agree.

If it's in the repositories, it's usually really easy to install.  A complete change from the old days of un-tarring files and compiling them, only to find you're missing 3 dependencies, which themselves have 10 dependencies missing, etc.

---

### Post by pcloadletter on 2008-02-20
It seems that people here are more interested in being reactionary and defensive of the Ubuntu status quo rather than discussing future options for devlopment.

Thank you for the open suse one touch link! I have seen some stuff about it for Ubuntu, and its great to see that its in OpenSuse 10.3.

To claify about my instalation comments, I do not expect nor hope for Ubuntu to install programs in the same way as Windows, I hope for Ubuntu to be as easy as Windows to intall programs that are not in the repositories.

---

### Post by azimuth on 2008-02-20
> **pcloadletter said:**
> 

To claify about my instalation comments, I do not expect nor hope for Ubuntu to install programs in the same way as Windows, I hope for Ubuntu to be as easy as Windows to intall programs that are not in the repositories.

The closest you'll get to the Windows way of installing programs is .deb packaging. It's  one of those search the net, find the package, download the package and click on it to install, procedures. It's really a pain after you get used to aptitude, apt-get, synaptic and the simple add-remove options. It's not my preferred  method of getting programs. To each his or her own. It's nice to have all the different ways to add to programs and never have to read and agree to the fine print to run them.

edit: I just remembered what happened when I went and got the DEB from Skype. I downloaded it and started an install. Up pops a notice that there was a newer version of Skype already in the repositories and something to the effect of "Would you rather install the newer version?" I really appreciated the thoughtfulness of the keepers of the repository and who ever coded for a check on an external install.

---

### Post by AnonCat on 2008-02-20
I don't use the command line frequently in Linux and when I do it's usually for simple operations that are easy to memorize.  Synaptic and .deb files make programs just as easy to install in Ubuntu as in WinXP in my opinion.  People just need to take some time and learn how to use their operating system instead of clamoring for a clone of whatever OS they used last time.

---

### Post by ScottC454 on 2008-02-20
At this point, it's easier to install stuff in Ubuntu than in Windows.  With GDebi, the process couldn't be simpler.  If you have to download source or tar.gz's, it's the fault of the developers who didn't create .deb files. 

Windows installers don't write themselves, so this isn't much different.  I suspect it has more to do with the fact that with open source, you actually have the option of compiling from source code, and this makes things more complex.

---

### Post by 3rdalbum on 2008-02-21
It's got more to do with the fact that Windows basically runs on one architecture: x86.

Linux runs on lots of architectures. A precompiled binary for x86 will not run on any other architecture. The only solution is providing source code - that way you can generate a 64-bit x86 binary, a 32-bit x86 binary, a MIPS binary, a PowerPC binary, an ARM binary, etc, to suit your computer.

Windows does actually run on a second arch - Itanium. But since Windows developers have always been in the frame-of-mind of "Can't give out the source code", there's very little you can do on an Itanium Windows system. In fact, if you're given the source code for a Windows program, it's much much more difficult to compile and install it on Windows than it is for Linux source code on a Linux system.

Having said that, source code can and SHOULD be easier to compile and install than it currently is.

---

