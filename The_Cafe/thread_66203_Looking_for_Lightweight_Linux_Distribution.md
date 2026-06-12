---
title: "Looking for Lightweight Linux Distribution"
date: 2005-09-16
forum: The Cafe
---

### Post by Goober on 2005-09-16
Hello,

I am going to be getting a Laptop, however, it is going to be a very old-model Laptop, and, well, I know that Ubuntu will be too "heavy" for it, so I am wondering if anybody experienced with Linux could point me to perhaps a very lightweight version of Linux.  All that I really need is a basic word processor and spreadsheet for it, nothing fancy.

Or, even better, is there such thing as a Ubuntu Lite?  Like, a lightweight Ubuntu version that would work on a very old-model laptop?  I have found some on Wikipedia, but I was wondering if anybody could reccomend something to me?

Thanks in advance,

Goober.

---

### Post by Brunellus on 2005-09-16
[QUOTE=Goober]Hello,

I am going to be getting a Laptop, however, it is going to be a very old-model Laptop, and, well, I know that Ubuntu will be too "heavy" for it, so I am wondering if anybody experienced with Linux could point me to perhaps a very lightweight version of Linux.  All that I really need is a basic word processor and spreadsheet for it, nothing fancy.

Or, even better, is there such thing as a Ubuntu Lite?  Like, a lightweight Ubuntu version that would work on a very old-model laptop?  I have found some on Wikipedia, but I was wondering if anybody could reccomend something to me?

Thanks in advance,

Goober.[/QUOTE]
 in the works.  but if you're looking for a solution now, and don't mind doing a lot of manual installation & configuration, seek out the MiniRAM Howto on the forums.

---

### Post by GeneralZod on 2005-09-16
PuppyLinux, FeatherLinux and VectorLinux are supposed to be very good for this kind of thing; check them out! :)

---

### Post by jdodson on 2005-09-16
damnsmall linux is 50 megs last time I checked.  It SCREAMS on old pentium 50's with low ram(64 megs) because it all fits into ram.

i think there was a lightweight ubuntu someone made some docs for.  basically you just install ubuntu server(option on the install cd), and then apt get xorg and icewm or some other lightweight WM.  seemed to work ok for them.

though, i would go with damnsmall linux personally.

---

### Post by benplaut on 2005-09-16
ditto to jdodson... DSL is the way to go


/intel_jingle "Debian Inside!"

---

### Post by Technoviking on 2005-09-16
I have had luck making Slackware and Gentoo pretty lightweight in the past. I thought there was Light-Ubuntu project in the works?

Mike

---

### Post by TrailerTrash on 2005-09-16
Ive used BeatrIX before..Its kinda like a UbuntuLite distro...It uses a light weight Gnome...Ive used it on OLD hardware and runs great! 

[http://www.watsky.net/](http://www.watsky.net/)

---

### Post by wrtrdood on 2005-09-16
Check out SLAX ([http://slax.linux-live.org)](http://slax.linux-live.org)).  Lightweight enough to fit on the smaller CDs.  Looks like a potential winner.

---

### Post by Brunellus on 2005-09-16
[QUOTE=wrtrdood]Check out SLAX ([http://slax.linux-live.org)](http://slax.linux-live.org)).  Lightweight enough to fit on the smaller CDs.  Looks like a potential winner.[/QUOTE]
 Mad props to slax.  it uses KDE, though.

---

### Post by JEDIDIAH on 2005-09-16
[QUOTE=Goober]Hello,

I am going to be getting a Laptop, however, it is going to be a very old-model Laptop, and, well, I know that Ubuntu will be too "heavy" for it, so I am wondering if anybody experienced with Linux could point me to perhaps a very lightweight version of Linux.  All that I really need is a basic word processor and spreadsheet for it, nothing fancy.

Or, even better, is there such thing as a Ubuntu Lite?  Like, a lightweight Ubuntu version that would work on a very old-model laptop?  I have found some on Wikipedia, but I was wondering if anybody could reccomend something to me?

Thanks in advance,

Goober.[/QUOTE]
 You don't have to flee Ubuntu. You just need to install an alternative window manager. Something like WindowMaker should fit the bill. It will be a bit more DIY in general and moreso on the desktop than KDE or GNOME. But it shouldn't be as problematic as other options suggested here.

There are other lightweight WM's so don't feel limited to WindowMaker. wmaker just happens to be the one I ran before being exposed to Ubuntu.

Just approach Ubuntu as if you were a Debian user.

Check out [http://xwinman.org/](http://xwinman.org/).

For an older laptop, I would be more worried about the video chipset than the dearth of physical memory. Some of those chipsets were notoriously under supported.

---

### Post by karuptdata on 2005-09-16
Just as stated abov you may want t try VectorLinux however no need to ditch Ubuntu just yeah just simply install ICEWM..lighweigh and powerful..I hav used in the past...But im willing to sacrifice a lil speed for all the features o gnome LOL  :smile:

---

### Post by poofyhairguy on 2005-09-16
Damn Small Linux

nuff said.

---

### Post by Goober on 2005-09-16
[QUOTE=poofyhairguy]Damn Small Linux

nuff said.[/QUOTE]
 I am going to try Damn Small Linux, simply because many prople mentioned it, and, well, it seems sufficiently small.  But thanks a bunch for all the suggestions!  Very useful, you lot are!

I probably shouldn't mention that the main reason I am buying this is for the Win98 Official CD, the Laptop I consider a bonus :p  The only reason I want Win98 is for that QEmu Windows Emulator dealie.

---

### Post by xequence on 2005-09-16
I got damn small linux to work on a old computer... Pentium 70mhz, 16 MB RAM. I have no idea how I did but I havnt been able to do it since. DSL installs to the hard drive as debian, so you could apt-get stuff. Or you can do a server install of ubuntu and apt-get some things. Openbox aparently takes up just one MB of ram.

---

### Post by Goober on 2005-09-16
[QUOTE=xequence]I got damn small linux to work on a old computer... Pentium 70mhz, 16 MB RAM. I have no idea how I did but I havnt been able to do it since. DSL installs to the hard drive as debian, so you could apt-get stuff. Or you can do a server install of ubuntu and apt-get some things. Openbox aparently takes up just one MB of ram.[/QUOTE]
 This is very encouraging, because I am installing it on a 75 Mhz, with 12Mb of RAM.  Thankfully, DSL is so small . . .

---

### Post by MetalMusicAddict on 2005-09-16
He asked. Im suprised no one mentioned it. [UbuntuLite](http://ubuntulite.org/)

---

### Post by az on 2005-09-16
[QUOTE=Goober]This is very encouraging, because I am installing it on a 75 Mhz, with 12Mb of RAM.  Thankfully, DSL is so small . . .[/QUOTE]
Debian Woody would install on a box with 8 Megs of ram.  Afterwards, it would only need 4 megs to run.  But that is a basic system with no X windows.

I am not sure that you are going to be able to run X very well with 12 megs of ram....

Try looking into older versions of DSL or other distributions like Slackware or Debian Potato.

---

### Post by Goober on 2005-09-17
What is "x"?

And UbuntuLite requires, according to the Wiki, 1.4Gb of HD Space.  This one will have just over a half-Gig, not nearly enough.

---

### Post by poofyhairguy on 2005-09-17
[QUOTE=Goober]What is "x"?.[/QUOTE]

Long:

[http://en.wikipedia.org/wiki/X_Window_System](http://en.wikipedia.org/wiki/X_Window_System)

Short:

Its the program you need to have any graphic programs (difference between dos and Windows).

---

### Post by Goober on 2005-09-17
Ahh, ok, thanks for enlightening me, poofyhairguy.

For the record, after going through some Websites, only DSL and Puppy Linux look "light" enough for this Laptop.  Feather Linux, SLAX, UbuntuLight, and Vector Linux all look too "heavy" for my purposes, and by that I mean require too much RAM, but I guess only trial and error will give me an answer.

Also, for the record, the Laptop is a Toshiba Satellite 100CS, it seems about 10 years old, according to some Googlage.  

Hrm, I never realized just how many versions of Linux there are . . . I just stumbled upon [BasicLinux](http://distro.ibiblio.org/pub/linux/distributions/baslinux/), which saeems extremely stripped down . . .

---

### Post by stoneguy on 2005-09-20
Definitely, DSL. That's the other place I hang out occasionally. Their community rivals this one for helpfulness.

DSL is targetted to run on low-end gear, but will operate on boxes that don't require 2.6 kernel-specific features (because it's only available with 2.4). A 64MB (plus swap) 133MMX is running it, while my 384MB Cel500 has Ubuntu. (You can see I'm really into bleeding-edge systems :) )

---

### Post by xequence on 2005-09-20
I downloaded DSL and tried it on my 16 MB RAM 75 MHZ Pentium a bit ago. I used a boot floppy... It booted up a little way, but said it couldent find a knoppix filesystem or something, then said it was gonna give me a very limited shell. Not sure what it means, but it might give some info ;)

---

### Post by Goober on 2005-09-20
[QUOTE=xequence]I downloaded DSL and tried it on my 16 MB RAM 75 MHZ Pentium a bit ago. I used a boot floppy... It booted up a little way, but said it couldent find a knoppix filesystem or something, then said it was gonna give me a very limited shell. Not sure what it means, but it might give some info ;)[/QUOTE]
 I assume that you tried this on a Desktop?  And did the Computer you used have either Internet Access or a CDROM drive or a ZIP drive?

The problem with my Laptop is that I don't have a way of getting DSL onto the Laptop.  It comes with a standardf 1.44Mb floppy drive, but, well, no way am I getting DSL, which is 50Mb, onto it with floppies.  I don't have a CDROM Drive, USB, or Ethernet access for it, so getting DSL onto it is a challenge for me, never mind installing it.  I am looking into getting an Ethernet PCMCIA Card, which means I can possibly download DSL, and install it that way.

---

### Post by niobe_logos on 2005-09-20
Puppy Linux is my usual choice, followed by Damn Small Linux.  I carry both the CD and a USB stick of Puppy in my toolkit. Feather Linux, for some reason, punts to kernel panic on half the systems I try it on.

One reason I prefer Puppy is its user-friendly look. Most times, if I'm using Puppy at all, it's to make some really ancient system usable for a non-technical person. The "quasi-windows" look seems to reduce the fear factor a little bit, and  the default desktop makes it pretty easy to start using stuff right away. I've yet to see Puppy have trouble with a system, except for bringing up wireless on a laptop...

---

### Post by Goober on 2005-09-21
But doesn't DSL have a fairly user-friendly GUI as well?  That was my impression at least.  The one reason for me to consider DSL over Puppy is that I am in contact with somebody in Australia trying to install DSL on the exact same machine.

But I might install Puppy and DSL on my Desktop, and test them both out.  I certainly have the room, I guess, and I can always uninstall one or the other.

Thanks for the advice, though.  Just one more thing for me to consider.

---

### Post by benplaut on 2005-09-21
[QUOTE=Goober]But doesn't DSL have a fairly user-friendly GUI as well?  That was my impression at least.  The one reason for me to consider DSL over Puppy is that I am in contact with somebody in Australia trying to install DSL on the exact same machine.

But I might install Puppy and DSL on my Desktop, and test them both out.  I certainly have the room, I guess, and I can always uninstall one or the other.

Thanks for the advice, though.  Just one more thing for me to consider.[/QUOTE]

both are livecds... go ahead and run them as live on your main machine  :) 

Puppy is incredibly fast, even on old machines, and features a taskbar almost identical to Win 9x... DSL is still a old fav, though  :)

---

### Post by rajsarkar on 2005-09-21
I used Puppy, DamnSmall and BeatrIX. For old machines Puppy seems to be the best.

Raj

---

### Post by Eric Plumrose on 2005-09-21
[QUOTE=Goober]

The problem with my Laptop is that I don't have a way of getting DSL onto the Laptop.  It comes with a standard 1.44Mb floppy drive, etc.[/QUOTE]

If you can get hold of a copy of MS-DOS 6 and a lap-link cable Dos has a programme to transfer files via the printer ports or serial ports.

If you are handy with a soldering iron the DOS help files will tell you how the make the cable.

Sorry I can't remember the name of the prog it's ages since I used DOS. :-)

---

### Post by stoneguy on 2005-09-21
I strongly recommend anyone wanting to find out anything about DSL pop over to [the DSL website](http://www.damnsmalllinux.org/index.html). Folks there have come up with solutions to the problems some of you are asking about. Just search the forums there.

---

### Post by xequence on 2005-09-21
[QUOTE=Goober]I assume that you tried this on a Desktop?  And did the Computer you used have either Internet Access or a CDROM drive or a ZIP drive?

The problem with my Laptop is that I don't have a way of getting DSL onto the Laptop.  It comes with a standardf 1.44Mb floppy drive, but, well, no way am I getting DSL, which is 50Mb, onto it with floppies.  I don't have a CDROM Drive, USB, or Ethernet access for it, so getting DSL onto it is a challenge for me, never mind installing it.  I am looking into getting an Ethernet PCMCIA Card, which means I can possibly download DSL, and install it that way.[/QUOTE]

I think it has a network card, but it wasnt connected to the internet. It had a floppy drive and a CD drive.

---

### Post by Goober on 2005-09-22
[QUOTE=xequence]I think it has a network card, but it wasnt connected to the internet. It had a floppy drive and a CD drive.[/QUOTE]
 Ya, see, if mine had a CD Drive, then I coulda installed DSL the day I got the Laptop.  

Anyway, I still need to figure out a reasonable way to get DSL on the Laptop, but thanks for all the advice, folks.  I do appreciate it.  Would you believe this has become my hobby of sorts?

---

### Post by Qrk on 2005-09-22
Debian offers boot floppies the last time I checked, from which you can do a network install. It won't be DSL, but you can apt a window manager of your choice.

---

