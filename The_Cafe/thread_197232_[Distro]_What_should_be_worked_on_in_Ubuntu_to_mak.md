---
title: "[Distro] What should be worked on in Ubuntu to make it even better according to you ?"
date: 2006-06-15
forum: The Cafe
---

### Post by patrick295767 on 2006-06-15
Everyone of us experienced at least once this question :
[COLOR="Black"]*** Which distro should I choose ?  ***[/COLOR]
  
Hoping that this great Ubuntu Linux will have even better popularity :-), where should be oriented the efforts according to you? 
  
What is still missing for you in Ubuntu ? 
Hardware, programs, apps, kernel, ... 

Share your thoughts and experiences !

Thanks,   

Sincerely, 

Patrick

---

### Post by jc87 on 2006-06-15
apt-torrent 

Even more packages in the repositories (Universe is ok as long as i can apt-them)

---

### Post by echo $USER on 2006-06-15
The only thing I am missing is support for new vidoe games:-({|= , but I'm starting to grow out of that.

---

### Post by Adamant1988 on 2006-06-15
I'd like to see WINE integrated into the OS or at least as an option (although I'm not sure if it's completely OSS, so it might not be possible). Lots of people are married to a windows program that WINE might run, so it's worth asking for. 
I'd also like to see Ubuntu offer a link to the community 3rd party projects with detailed descriptions of them.  What I mean is that Easy Ubuntu needs to be one of the first things that a 'newbie' finds and installs.

Also, I know it's probably not a possibility, but I'd like to see an installer for those pretty tar.gz. formats and .debs etc. a GUI installer preferably.  I am not scared of the command line, but my fiance will never go near it, I'm sure, and I'd like her to be using linux soon.  She has so many problems with windows.

---

### Post by Sgood1971 on 2006-06-15
keep working on acpi, it's gotten way better but could still improve.

---

### Post by bruce89 on 2006-06-15
Multiarch, [https://launchpad.net/distros/ubuntu/+spec/dependency-removal](https://launchpad.net/distros/ubuntu/+spec/dependency-removal) and my signature.  Actually add Gnash too.

---

### Post by grsing on 2006-06-15
Easier wireless, better ATI support, umm, that's really about it now (well, consistent flash sound would be nice; works great on one install, no go on the other, no apparant reason why).

---

### Post by poofyhairguy on 2006-06-15
[QUOTE=Adamant1988]
Also, I know it's probably not a possibility, but I'd like to see an installer for those pretty tar.gz. formats and .debs etc. a GUI installer preferably.  [/QUOTE]

Installing debs is already done by a GUI in Dapper. I love it! 

What do I want in Ubuntu? Ndisgtk in the main pre-installed if Ubuntu detects a wireless card.

---

### Post by KiwiNZ on 2006-06-15
Don't add new , get the basics right

---

### Post by Wallakoala on 2006-06-15
[QUOTE=poofyhairguy]Installing debs is already done by a GUI in Dapper. I love it! 

What do I want in Ubuntu? Ndisgtk in the main pre-installed if Ubuntu detects a wireless card.[/QUOTE]

Definetly. I don't know if ndisgtk was around when breezy came out, but that is around the time I started to use ubuntu and it took me a loooooooong time to figure out ndiswrapper. I wish I would have been able to use the gui back then...

---

### Post by therunnyman on 2006-06-15
Hard disk support.

---

### Post by Pekkalainen on 2006-06-15
[QUOTE=KiwiNZ]Don't add new , get the basics right[/QUOTE]

Word!

Work on getting all mouse buttons to work out of the box for example

---

### Post by poofyhairguy on 2006-06-15
[QUOTE=therunnyman]Hard disk support.[/QUOTE]


Hmm....I'm a little confused by this one.

I'm pretty sure that Ubuntu supports every hard disk sold on a shelf. 

Do you mean:

A. Better graphical support of hard disk functions (aka better tools to parition/mount and whatnot)?

B. Better access to hard disk file system types (like NTFS write support)?

C. Better support for the controller hardware that controls hard disks (aka drivers for more raid controllers and motherboards)?

I assume that you probably meant C.

---

### Post by poofyhairguy on 2006-06-15
[QUOTE=Pekkalainen]
Work on getting all mouse buttons to work out of the box for example[/QUOTE]

Is a four/five/six/+ button mouse really "basics?" I mean, I have a four button one that I sometimes use and I like having the fourth button do something (yay to guides on forum) but it seems 95% of people I know have the basic two button and a scroll wheel mice.

Not to knock down your point, but it seems like something only the nerdier of us would use. In fact I remember one friend that got me to help him disable the extra buttons on his new mouse in Windows because he kept accendently clicking them, only to get effects he did not want at the time.

---

### Post by therunnyman on 2006-06-15
[QUOTE=poofyhairguy]Hmm....I'm a little confused by this one.

I'm pretty sure that Ubuntu supports every hard disk sold on a shelf. 

Do you mean:

A. Better graphical support of hard disk functions (aka better tools to parition/mount and whatnot)?

B. Better access to hard disk file system types (like NTFS write support)?

C. Better support for the controller hardware that controls hard disks (aka drivers for more raid controllers and motherboards)?

I assume that you probably meant C.[/QUOTE]

No, I mean exactly that: hard disk support.  Lots of folks with multiple hard disks are having trouble with Dapper because it mis-enumerates the drives.  For example, on my machine, the SATA disks plugged into a PCI card are correctly identified as sdc and sdd during installation, then, post installation, are loaded as sda and sdb, causing all kinds of difficulties, especially on the RAID/server front.

Problems with RAID/server stuff on a Linux-based OS, you say, runny?

Yes.  That's a lethally serious problem, I mean, if you ask me.

runny

PS Oh, whoops - yes, C, option C.  Too much fiber in my diet.

---

### Post by poofyhairguy on 2006-06-15
[QUOTE=therunnyman]No, I mean exactly that: hard disk support.  Lots of folks with multiple hard disks are having trouble with Dapper because it mis-enumerates the drives.  For example, on my machine, the SATA disks plugged into a PCI card are correctly identified as sdc and sdd during installation, then, post installation, are loaded as sda and sdb, causing all kinds of difficulties, especially on the RAID/server front.
[/QUOTE]

I have fought that too. Its also really bad when you add drives and that happens. I know of no solutions though....but good point.

---

### Post by xeero on 2006-06-15
[QUOTE=KiwiNZ]Don't add new , get the basics right[/QUOTE]

I agree!  Especially more testing on different hardware.  Make sure the currently included, heavily used apps are solid (don't crash), like Firefox and Nautilus especially.  Other basics like cd/dvd burning are important too.  Fix those bugs in the installer.  

Work on this before adding more apps.

---

### Post by Adamant1988 on 2006-06-15
another one: Keeping more up to date versions of flash, java, etc. in the repos. work on that flash sound thing too... I used to love pandora, now I have to live without =(

---

### Post by poofyhairguy on 2006-06-15
[QUOTE=Adamant1988] Keeping more up to date versions of flash [/QUOTE]

Thats up to Adobe not Ubuntu. They are doing their best to make Linux users mad.

---

### Post by Adamant1988 on 2006-06-15
Sorry for being ignorant on that one. =\.   
I also didn't know that Ubuntu had a GUI installer for .debs *smacks forehead*

Also can someone explain what a .bin is for me? Just in PM don't hijack the thread.

---

### Post by click4851 on 2006-06-15
I'll add my two cents.....put me down for cd/dvd burning as well. I just unloaded gnomebaker/xcdroast and all that entails, turned right around and had synaptic load K3B and all that entails .....so far no coasters, no cdrecord issues that frankly...I know way more than I ever wanted to know. It should just work right, and I wanted Gnomebaker to work, or at least Xcdroast, but there is way too much pissing and moaning going on with cdrecord and atapi/scsi emulation....bwwwahhhhheh......just burn....thats it. Sorry rant mode off....:)...

---

### Post by Christmas on 2006-06-15
What am I missing in Ubuntu... Hard to way the first thing that came into my mind are some apps which could be improved, they don't like they reached maturity. For example, Kaffeine and its subtitle handling (no "synchronize" function, less options than say Media Player Classic in Windows).

Also, Konversation IRC client looks very nice and very friendly, but there is no scripting support. XChat uses TCL, Perl and Python for scripting, and I also tried to make a C plugin and worked very well, but its options are limited (no "Show in active window the /whois information etc) and if you're not a scripter you can't use it at its maximum potential.

The only decent TV-Tunning playing program I could find to work for me is TVtime, but it does not have important functions like recording, and the interface is simple and I feel like missing lots of functions from WinFast PVR software in Windows.

All the text editors and word processors are fine for me though, they seem complete and have more functions like the Windows ones. Simple text editors in Win like Notepad or Wordpad don't have so much functionality (as an example say the syntax highlighting). Maybe for common users doesn't matter but for developers its a must-have.

As audio players, the only one that I could find really lovely is amaroK. For some reason I don't like the GNOME audio players, and XMMS is at Winamp's 2.x level, very rudimentary, and it's not any more under development, isn't it?

Internet browsers are super OK, from Konqueror, Firefox to Epiphany they all are great but the messaging clients (Kopete, Gaim) are rudimentary as well. Of course, they both have interesting functions which cannot be found in their Windows equivalents, but... still work should be done on them.

DC clients... the Linux DC++ port is still at its beginnings and works very slow in KDE. Valknut seems an appreciated DC client, but I never liked it.
Graphics programs seem also pretty complete to me.

I miss a good program who can interact well with mobile phones, still couldn't load into my computer my pics from a Samsung Z500 mobile phone, if anybody does know how this can be done, please PM me.

The KDE helping system should be improved, I think it's over 3 years old? And some important apps miss a helping system (say Akregator, first that came into my mind) or the help is too old.

There would be some other things, but I can't get into my head right now.

---

### Post by Fallom on 2006-06-15
[QUOTE=poofyhairguy]Is a four/five/six/+ button mouse really "basics?" I mean, I have a four button one that I sometimes use and I like having the fourth button do something (yay to guides on forum) but it seems 95% of people I know have the basic two button and a scroll wheel mice.

Not to knock down your point, but it seems like something only the nerdier of us would use. In fact I remember one friend that got me to help him disable the extra buttons on his new mouse in Windows because he kept accendently clicking them, only to get effects he did not want at the time.[/QUOTE]

I think it's very important. I still can't manage to get all 12 buttons working properly on my MX1000. 95% of the people you know may be fine with a two button mouse, but having built-in support for more complicated mice should be an incredibly basic thing for any OS.

---

### Post by Christmas on 2006-06-15
Another thing that came into my mind: in Ubuntu it was a pleasure to use Synaptic, in KDE I don't use Adept. I don't know if others like its functionality, but for me is slow (especially when searching for some package) and harder to use than Synaptic. Despite the fact I like the multitude of options in KDE and dislike GNOME's apps because lack of configuration, this only program I'd like to see more simplified and intuitive.

---

### Post by poofyhairguy on 2006-06-15
[QUOTE=Fallom] having built-in support for more complicated mice should be an incredibly basic thing for any OS.[/QUOTE]

From what I hear (from the person who pretty much runs the Freedesktop.org- Mr. Stone) this is in the works.

---

### Post by 23meg on 2006-06-16
To focus on policies instead of software specifics:

**-** Even more focus on X development and testing in the next couple of releases

**-** Tighter relations with user base to encourage better and more widespread testing

**- **More relaxed attitude on deviating from upstream and forcing modifications, for better streamlining (example: gnome-screensaver)

**-** More sponsored bounties! (in connection with above)

**-** More efficient connections between official and unofficial online existence

---

### Post by bk452 on 2006-06-16
I want the ability to grab that file I forgot on the windows side without having to shut down and boot into windows.  I could do that with SuSE.

---

### Post by Drifter on 2006-06-16
I would like to have the cd and dvd drives and I guess all drives made easier to use.  I also would like an installer for the tar.bz files.  Someone said a gui installer is in dapper.  What is and where is and how do u use it after u download a tar.bz.

---

### Post by deeptingler on 2006-08-26
I agree with Drifter on this one, coming from windows was a nightmare for accessing my drives and could not get the system to allow access to ext3 formated drives without a fight so ended up moving back to fat32 (which I don't trust) - It would be nice for new linux users to have the option to just use these things straight away, even if they were going to be warned each session that it was less secure for example (at least it would be some sort of hand-holding and not put people off Linux straight away when they come from Windows and find they have to fight to gain access to files etc)......  I suppose we can blame Microsoft for everyone not being used to security, so they are shocked at the way Linux works.

---

### Post by Bezmotivnik on 2006-08-26
> **KiwiNZ said:**
> Don't add new , get the basics right
Bingo.

Like wireless, which works about as well as software modems. :rolleyes:

---

### Post by RAV TUX on 2006-08-26
I'm looking forward to when Knoppix adds to it's install list Ubuntu to the 3 alternatives it already has:

1. Debian
2. Beginner
3. Knoppix (like live CD)

Then you will have the superior hardware detection of Knoppix combined with a Ubuntu HD install, plus I do believe Knoppix has the easiest and most intelligent install of any Distro to date.

(it would be nice to include the codecs that Knoppix includes by default also)

---

### Post by Polygon on 2006-08-26
i would like to see a dialogue to configure my keyboard buttons, (mostly the volume buttons), because right now the keyboard volume buttons control "Left" or something, but the volume i actually here is "center". I have not seen any way to configure this.

And there is a bunch of community projects (like USP) that it would be really cool to see in ubuntu by defualt.

---

### Post by ahaslam on 2006-08-26
**Stable** 3D acceleration for my Unichrome K8M800 would be nice.

Tony ;)

---

### Post by red_Marvin on 2006-08-26
Faster loading built in help index (in the works iirc)
More hardware support (or whatever that makes both gentoo and dsl find my laptop's nic but not ubuntu)
An easier way to theme gnome (and I mean change colors, like windows classic)
Burning support for cyberdrw writers...

---

### Post by Dr. C on 2006-08-27
Out of the box dial up modem support for those modems that have open source drivers. A good example is the Intel 536EP modems. 

I installed this modem in Ubuntu by following the instructions in the documentation which were very helpful but required Internet access. Not a problem in my case since I have broadband and only wanted the modem as a backup, but for those that do not have broadband this is another matter. 

[https://help.ubuntu.com/community/DialupModemHowto]("https://help.ubuntu.com/community/DialupModemHowto")

The instructions amount to the following 

1) Downloading the **source** code from the Intel site and yes agreeing to a very liberal open source license from Intel.

2) Installing the required packages.

3) Compiling the driver from source.

4) Installing the driver. 

My suggestion is to focus first on those modems whose manufactures produce open source drivers and support them out of the box. This will do two things. Help many people worldwide who do not have access to broadband and reward those manufactures who produce open source drivers by creating a demand for their products.

---

### Post by Christmas on 2006-08-27
I think it needs drivers and software support from hardware manufacturers, more mature and less buggy applications, and some serious money investments. Ubuntu is on the right way because of Mark's Canonical who sponsors it, but other distributions are completely made and maintained by people who don't get paid at all. This is a weakness for Linux in my opinion.

---

