---
title: "Tabuntu"
date: 2007-01-16
forum: The Cafe
---

### Post by Curtisc on 2007-01-16
I've been using Ubuntu for a year or so, and read (and written) the occasional post about tablet PC support.  Today I found [this]("https://launchpad.net/bounties/tabuntu") posted on launchpad - all in all, I've come to the conclusion that I'm not alone in my desire for an alternative to Windows XP Tablet edition.  I'm willing to do what's required to get the project started (although my programming experience is pitiful), but I don't exactly know what to do.  I think what is needed first of all is a listing of desired features and research into possible solutions, but I'm not sure where to start... should I just start up a launchpad project under the name "Tabuntu"?  Is that even an appropriate name?  Maybe a sourceforge project?  I'd appreciate any light anyone can shed on the issue of how to instigate this huge project - that is, a new version of Ubuntu tailored to tablet PC users.

---

### Post by 23meg on 2007-01-16
I'm not sure a separate distro is necessary; maybe a metapackage with tablet-specific tools would be better, but in any case, what's more urgently needed in this area is development of the required tools themselves, namely of handwriting and maybe speech recognition, rather than the putting together of a distro.

---

### Post by maniacmusician on 2007-01-17
I agree with 23meg. We need those tools first, and the tablet PC thing would likely be a metapackage...but if it gets specialised enough, I can definitely see it being another derivative.

In the end, if you really want to do it right, it would probably have a different X server setup, different choices of software, services, and I dont know what else.

---

### Post by 23meg on 2007-01-17
The first priority should be picking up the seemingly dead xstroke and making it into a full featured handwriting recognition app. Anyone looking to put in programming work or bounties should concentrate on this.

---

### Post by Curtisc on 2007-01-17
I think you're both right... there definitely needs to be more work done in those areas.  However, there has already been a lot of tools created - it is currently possible to run Ubuntu on a tablet, albeit with limited tablet functionality, so it would be good to compile and compare a list of these tools.  Since I'm not much of a developer myself, I thought it might encourage other developers if there were some sort of grandiose end goal.  It's probably beyond my capabilities, but I'd still like to try and encourage people to work on some component of the system.

---

### Post by 23meg on 2007-01-17
Except some tablet specific tools, I don't think tablet users need anything too different than laptop users, who in turn don't need anything too different than desktop users; hence the lack of a separate laptop edition of Ubuntu. 

The main strong point we already have is a working Wacom digitizer driver. The xserver-xorg-input-wacom package provides the linuxwacom driver, which is very easy to configure, and its functionality is also utilized by desktop graphics tablet users as well. There are a few notetaking apps, none of which feature handwriting recognition, and all of which leave something to be desired, and that's more or less it, we don't really have anything else already developed.  

Thus I can't think of a justification for a separate distro, but a metapackage, preferably an officially supported one, with working tools and well thought out modifications to upstream GNOME, such as a GDM login and password dialogs usable with an onscreen keyboard, a panel that survives multiple xrandr rotations without losing order, etc. is enough of a grandiose end goal if you ask me. If a separate distro *is* needed beyond that point, it won't be double work to put it together; just about everything needed for it will have been ready.

---

### Post by baslow on 2007-01-17
Emperor Linux claims the following for their [Raven X41 tablet ]("http://emperorlinux.com/mfgr/lenovo/raven/?tab=x41_tablet")(based on a Lenovo ThinkPad X41):

**Dynamic X rotation **- When you hit the rotate button or flip the LCD panel, the screen rotates from landscape to portrait and back. The screen can also be rotated, cycling between four orientations, via the rotate button. (There is no logging out or restarting of X.) 
**Pen/stylus input to screen **- Use it as a mouse pointer and as a pen/stylus. 
Hand-write commands on-screen. (Handwriting is converted to ASCII text in the focus area.) 
**Handwriting recognition **- Includes a software suite to convert handwritten text to ASCII text. (Handwriting features do require some training, but are very nearly as good as the "Windows Journal" at this time.) 
**Pressure sensitive pen **in applications like The GIMP.

Anyone know what particular programs they're using?

---

### Post by 23meg on 2007-01-17
All those features except handwriting recognition are already present in Ubuntu. They don't mention any specific software for handwriting recognition, and I haven't found any information on it with a few web searches. Thus we can in the least assume they haven't developed a brillant GPL'd solution that we or others can benefit from.

---

### Post by Curtisc on 2007-01-17
The only handwriting recognition thing that I could find is [PenReader](http://penreader.com/), and it is not open source, nor free.  Also, if their online demo is anything to go by, it's not very effective.  

Pressure sensitivity works pretty well in most applications that support it thanks to the linuxwacom project.  There are some good looking programs out there such as Xournal that are similar to windows journal.  The best would be handwriting recognition that functions the same way as it does in windows - that is, without having to convert your handwriting to text.  

Other than these, some other things to consider might be the fact that tablets are generally smaller and less powerful than other laptops - maybe use Xubuntu as a base?  Perhaps a minimalist theme to maximize usable desktop space?  I agree, a metapackage would work just fine (to be honest, I don't know what the difference is between a different variant and a metapackage - isn't Kubuntu just Ubuntu + kubuntu-desktop metapackage and without ubuntu-desktop?)

---

### Post by RAV TUX on 2007-01-17
> **Curtisc said:**
> I've been using Ubuntu for a year or so, and read (and written) the occasional post about tablet PC support.  Today I found [this]("https://launchpad.net/bounties/tabuntu") posted on launchpad - all in all, I've come to the conclusion that I'm not alone in my desire for an alternative to Windows XP Tablet edition.  I'm willing to do what's required to get the project started (although my programming experience is pitiful), but I don't exactly know what to do.  I think what is needed first of all is a listing of desired features and research into possible solutions, but I'm not sure where to start... should I just start up a launchpad project under the name "Tabuntu"?  Is that even an appropriate name?  Maybe a sourceforge project?  I'd appreciate any light anyone can shed on the issue of how to instigate this huge project - that is, a new version of Ubuntu tailored to tablet PC users.I actually posted the bounty quite a while back as you can see....

a lot has changed since then....I still use Ubuntu on my old computer....but I have since tested and used over 200 OS's....I currently use Sabayon which is Tablet (Wacom) enabled by default....

This is what Ubuntu should do also....

---

### Post by 23meg on 2007-01-17
[QUOTE=RAV TUX]This is what Ubuntu should do also....[/QUOTE]Doesn't Edgy's xorg.conf come with the required device entries as well, and all you need to do is comment them out in most cases? I'm not sure, but I last remember manually configuring my tablet in Dapper.

Tablet device (auto)configuration is relatively easy, especially given that with Xorg 7.3 we'll probably be able to do away with xorg.conf altogether. The hard part is developing a working handwriting recognition app almost from the ground up, and modifying the desktop environment for tablet specific use in a way that makes sense. 

Just thinking out loud: how about a collective bounty + pledge for developing a handwriting app? We can put up a pledge for the sum, and once the required amount of signers is reached, collect the money and put it into a bounty to be given to the developer(s) who will revive xstroke as a handwriting recognition app, or write one from scratch.

---

### Post by maniacmusician on 2007-01-17
bounties done that way never succeed, unfortunately. People can freely pledge money, but there's a pretty low chance that they'll all live up to it. I think it's better to first ascertain how much money is needed and then quickly collect the money in a small amount of time. Also, a team of coders should be hired and not just a single one. It's a very dreamy prospect, but it takes a lot organization and hard work to even get it off the ground.

i dunno. You guys seem dedicated. Why not write a spec on how you could hire a team to do this? The bounty would probably be of a significant amount, you would just need to find a group of people that are up to it.

---

### Post by RAV TUX on 2007-01-17
the cause is admirable....if the Linux community as a whole took the leading reigns of tablet technology development the future would belong to Linux.

---

### Post by adamsu on 2009-01-07
I know this thread is fairly old, but I have gone through the experience of setting up Ubuntu on my tablet in the past two months, and I think many things are really good. The digitizer works very well, xournal is a great program (a Microsoft Journal replacement), cellwriter is a good handwriting recognition program, etc. 
However, the opensuse people have a better system to setup the tablet. During installation you need only to click the tablet box, and all conceivable programs and settings needed for your tablet are enabled on the install, you need only to run sax2 and select your model to get it all working. (This was on 11.1.) Ubuntu is a better distro, but opensuse has this aspect running much more smoothly than we do.

---

### Post by bcw on 2009-05-03
Hi,

Thanks for those Xstroke packages you provided - I've referenced them in several of my howto posts for tablets.

Please have a look at my project for using Microsoft's handwriting recognition in Linux.  The idea is we can develop the tablet infrastructure and just plug in the Free recognition solution when it arrives:

[http://ubuntuforums.org/showthread.php?p=7203261#post7203261]("http://ubuntuforums.org/showthread.php?p=7203261#post7203261")

Cheers,
Bret

---

