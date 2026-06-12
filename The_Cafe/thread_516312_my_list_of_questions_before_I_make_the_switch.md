---
title: "my list of questions before I make the switch"
date: 2007-08-03
forum: The Cafe
---

### Post by MR.UNOWEN on 2007-08-03
Hello, I'm thinking of making the switch to ubuntu from Win XP and there's just a few questions on my mind.

1. Let's say I do install ubuntu 7.04, have my computer connected to the web, go on the web and Never install anything other than the OS or give approval, is probability getting a virus 0% or is there still a 0.00...01 chance of it?

2. How immune is ubuntu to spyware or anything that may release my personal info such as passwords or any other type of activity whether is accessing a file or surfing the web?

Just to give you an example of how vulnerable I was with XP, a friend of mine was able to breack into my computer and obtain my password using a live linux cd. How safe is Ubuntu with passwords?

3. I'm still planning to keep my windows system, so how hard is it with dual booting? They're going to be on separate hard drives and I may disconnect one every here and there. Can I have dual booting and still be able to remove any of the two hard drives?

4. I'm into visual effects and am currently using a program called samurize ([www.samurize.com](www.samurize.com)) to display all these little things that created to go on my screen, does Linux have anything like this, where the user can create stuff to go on the screen with little to no coding needed?

5. Is there a customize your boot / logon screen tutorial for dummies?
If so please list them in reply.

6. How easy is it to add a new theme for Ubuntu?
6b. How easy is it to create a theme for the desktop.

7. Let's say an OS  file corrupts, does the Ubuntu disc have an automatic recover system?
7b. How reliable is the OS recovery system, I had this problem with Win XP and when tried to recover, I sometimes got the BSOD; can the Ubuntu disc crash in recovery (if it has one)?

8. Does Ubunto have a defrag program?

9. I can change menu bar color or design,  right?

Thanks

---

### Post by Zzl1xndd on 2007-08-03
> **MR.UNOWEN said:**
> 
1. Let's say I do install ubuntu 7.04, have my computer connected to the web, go on the web and Never install anything other than the OS or give approval, is probability getting a virus 0% or is there still a 0.00...01 chance of it?

For the most part your looking at 0 anyway there are no Linux virus' in the wild at this point in time.

> 2. How immune is ubuntu to spyware or anything that may release my personal info such as passwords or any other type of activity whether is accessing a file or surfing the web?

Also no spyware or adware for Linux at this time


> 3. I'm still planning to keep my windows system, so how hard is it with dual booting? They're going to be on separate hard drives and I may disconnect one every here and there. Can I have dual booting and still be able to remove any of the two hard drives?

Dual booting is easy just know that what ever hard drive has your grub info on it will need to be in the machine for it to boot.

> 4. I'm into visual effects and am currently using a program called samurize ([www.samurize.com](www.samurize.com)) to display all these little things that created to go on my screen, does Linux have anything like this, where the user can create stuff to go on the screen with little to no coding needed?

Not into this kinda stuff myself but I everyone I know almost always finds a program that will do what they want and I suspect you will too.

> 5. Is there a customize your boot / logon screen tutorial for dummies?
If so please list them in reply.

Depends on what you mean Grub can be changed to boot what ever OS you want as the primary but its altering a config file much as it is if you wish to do it with the windows boot.ini

> 6. How easy is it to add a new theme for Ubuntu?
6b. How easy is it to create a theme for the desktop.

easy drag and drop, not sure never made one

> 7. Let's say an OS  file corrupts, does the Ubuntu disc have an automatic recover system?
7b. How reliable is the OS recovery system, I had this problem with Win XP and when tried to recover, I sometimes got the BSOD; can the Ubuntu disc crash in recovery (if it has one)?

Linux as an OS is a collection of parts so for the most part if something like that was to happen you could still get in and fix the issue but there is an option to fix form the CD never had to use it myself but the few people I have heard of said it worked well.

> 8. Does Ubunto have a defrag program?
Doesn't need one

> 9. I can change menu bar color or design,  right?



That you can

---

### Post by black_magician on 2007-08-03
I can't answer everything, but I'll answer what I can.

1.  you really can't say there is 0% chance of getting a virus, but I've been using Ubuntu for about a year now without ever running a virus scanner.  I don't worry about viruses one bit.

2.  again, I don't run a spyware scanner because I'm not worried.  I never have anything weird like ads popping up on my desktop or anything like that.

3.  I dual boot Fiesty and Gutsy right now, and that was easy as pie to get working.  don't know about windows and different hard-drives though.

4.  There's all the eye-candy you'll ever need in compiz.  and as for monitoring software like Samurize,  Ubuntu has the same stuff available.

5.  Probably exists, but I don't know where.

6.  it's nothing diffucult.
6b.  no Idea, never done that.

7.  for me, the most common thing that happened if something went wrong was it'll tell you what happened, then bring you to a terminal.  There might some recovery stuff out there though.  I just never use it.  You can always just boot the Live CD if you need it though.

8.  the ext3 file system doesn't need to defrag, so its not built in.  there are defrag programs out there for defragging other filesystems like NTFS if you need it.

9. yes.


I'm sure someone will eventually answer what I couldn't.

---

### Post by popch on 2007-08-03
> **MR.UNOWEN said:**
> Just to give you an example of how vulnerable I was with XP, a friend of mine was able to breack into my computer and obtain my password using a live linux cd. How safe is Ubuntu with passwords?

If someone has physical access to your machine (i.e. can put a CD into your drive), then your machine is vulnerable, regardless of the OS. You would have to encrypt your disks in order to prevent this.

Don't know if it's worth the bother for a private machine, though. Better keep your home locked.

---

### Post by Tux Aubrey on 2007-08-03
While Linux is pretty safe, your vulnerability and security is dependent on using the right tools and good practice.  Malicious attacks are rare, but certainly possible.  Ubuntu does not have any external ports open by default but nor does it have an activated firewall. You can enable the firewall very easily and manage your own security.  

Re the two drives - one of your drives will have the Master Boot Record and removing that one will make your machine unusable (unless, possibly, you have a bootloader on a floppydisk or CD - but I haven't done that)

If you have enough RAM and your machine is reasonably fast, you could run Windows in a Virtual Machine on Ubuntu rather than dual booting.  This has some security advantages but also some disadvantages in terms of performance.

Ubuntu does not have the same recovery options as Windows - but there are ways to set up your machine (with a separate /home partition) that means your work and settings are housed separately to the OS - you could then reinstall Ubuntu (or just about any other Linux distro) and have your important files preserved.  Supplemented with a good backup strategy, this is pretty well 100% reliable.

Eye candy on Linux is a smorgasbord of delights.  It will take a little while to appreciate the vast array of possibilities - and be prepared to feel confused for a while.  Anything can be changed and you will have more choice that you currently believe is possible.  

Its good to ask these questions now - take it slowly and you will be fine.

Here's some useful reading material - [psychocats]("http://www.psychocats.net/ubuntu/index.php")

---

### Post by MR.UNOWEN on 2007-08-03
Regarding the 2x hard drives, is there a way to have two master boot records, one that has options to boot into both and the other with only its own such that if both are in it will go to the one with options and when that one is removed it can boot directly to the remaining hard drive.

If yes, can some try it out and tell me how to go about it?

---

### Post by xzero1 on 2007-08-03
Would you guys get real on security? Read what is being patched and why when the system offers an upgrade. Many if not most are security related. In other words the system is vulnerable without the upgrade and therefore between upgrades. If Ubuntu was targeted as much as windows then we would be in trouble. Moreover, since no one uses virus scanners many systems could be infected before anyone knew about it. If a hacker really wants your system he will have it.

---

### Post by fuscia on 2007-08-03
being a clueless end user, myself, i've had lots of fun taking pre-existing themes, for a number of different desktop environments/window managers, and playing with their config files until they looked the way i want. unlike a program that just gives you mr. potato head like powers, messing with config files is something you can grow in expertise with. in other words, you can start off messing with simple things, get more complicated as you learn more, and pretty soon, you'll be building your own themes. in fact, this is true with other open source aspects, not just look.

---

### Post by frodon on 2007-08-03
> **xzero1 said:**
> Would you guys get real on security? Read what is being patched and why when the system offers an upgrade. Many if not most are security related. In other words the system is vulnerable without the upgrade and therefore between upgrades. If Ubuntu was targeted as much as windows then we would be in trouble. Moreover, since no one uses virus scanners many systems could be infected before anyone knew about it. If a hacker really wants your system he will have it.LOL, fun post, i like posts like that which doesn't contain any technical advanced explanation.

Seriously like any OS you need to keep it updated, just look for example how many major security fixes has been committed for firefox lately. Keeping your system up to date is the only way to prevent someone using a known buffer overflow hole for example.
Virus/spyware are  mainly a windows concept, that don't mean no one can hack your linux computer, that just mean they will use other ways to do so (most known is buffer overflow).

About desktop effects here is a video of what compiz fusion can do :
[http://www.youtube.com/watch?v=E4Fbk52Mk1w](http://www.youtube.com/watch?v=E4Fbk52Mk1w)

---

### Post by Glake on 2007-08-03
This is what I use for security in Ubuntu 7.04. I never believed any operating system is ever 100% perfect in anything, especially security. I do feel Ubuntu (Linux in general,) is the best out there and much better then MS Windows.

Firestarter - Firewall set up for True Stealth
Avast Anti-Virus
rkhunter (tool that scans for rootkits, backdoors and possible local exploits.)
chkrootkit(same)
plus several other programs for security, ex. nmapfe. I have much more control with Ubuntu and security then I do on my XP partition (I also use VMware Server and I have XP on that too, can't use 3D cards with vmware server yet which is why I have an XP partition for the 3D games I can't use with CrossOver.) 

I also go to a website to make sure my ports look good, [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")

I love Beryl as well as Gdesklets though I think more work needs to be done with gdesklets. (Desktop effects, etc.)

I monitor my CPU, RAM/SWAP, etc, with tools that are already a part of Ubuntu/Gnome.

There is so much it is amazing, and fun, lol.

---

### Post by Tux Aubrey on 2007-08-03
> LOL, fun post, i like posts like that which doesn't contain any technical advanced explanation.

Yes, frodon, And please don't overlook Fuscia's slur on Mr Potato Head.

---

### Post by simonalpha on 2007-08-03
In regards to the 2 HDDs, having two separate MBRs can and will work... although, I can't say I've tried it with Ubuntu. 

During the install, tell the installer to put the MBR record for GRUB on the hard drive with Ubuntu on it. As long as BIOS uses that hard drive to load, you'll have the option of Ubuntu or Windows. Remove that drive and booting off the other one will work fine, as the Windows boot records won't have been touched

Hope that helps,
Simon

---

### Post by MR.UNOWEN on 2007-08-03
Thanks simonalpha,

Can anyone give me a list of free ati-spyware/virus programs that I can find on the web?

---

### Post by Adamant1988 on 2007-08-03
> 1. Let's say I do install ubuntu 7.04, have my computer connected to the web, go on the web and Never install anything other than the OS or give approval, is probability getting a virus 0% or is there still a 0.00...01 chance of it?

Currently, there are no viruses for Ubuntu at all.  That doesn't mean that you should just install all sorts of apps from the net, the repos are the safest way to do your app installations. 

> 2. How immune is ubuntu to spyware or anything that may release my personal info such as passwords or any other type of activity whether is accessing a file or surfing the web?
Some security flaws are in FireFox and Ubuntu's developers can only do so much about that.  However, Ubuntu (as it stands) has no known spyware, that doesn't mean that it can't be created very quickly though.  So take that with a grain of salt 

> Just to give you an example of how vulnerable I was with XP, a friend of mine was able to breack into my computer and obtain my password using a live linux cd. How safe is Ubuntu with passwords?

Windows isn't a very secure system at all, but I'm not qualified to answer this, I know nothing about Linux security other than that it's a multi-user system. 

> 3. I'm still planning to keep my windows system, so how hard is it with dual booting? They're going to be on separate hard drives and I may disconnect one every here and there. Can I have dual booting and still be able to remove any of the two hard drives?


Dual booting can be tricky if they're both on the same HD. 


> 4. I'm into visual effects and am currently using a program called samurize ([www.samurize.com](www.samurize.com)) to display all these little things that created to go on my screen, does Linux have anything like this, where the user can create stuff to go on the screen with little to no coding needed?


Those look like widgets/gadgets/screenlets to me.  There are a LOT of Applications for Ubuntu that allow that same kind of effect. 


> 6. How easy is it to add a new theme for Ubuntu?
6b. How easy is it to create a theme for the desktop.
Adding a new theme is as simple as dragging the theme tar.gz to the theme manager.  Creating one is a bit more complex but I have no experience with that. 

> 7. Let's say an OS  file corrupts, does the Ubuntu disc have an automatic recover system?
7b. How reliable is the OS recovery system, I had this problem with Win XP and when tried to recover, I sometimes got the BSOD; can the Ubuntu disc crash in recovery (if it has one)?

In my year of using Ubuntu I never experienced anything other than X breaking.  Which drops you to the CLI where you can easily recover the system. 

> 8. Does Ubunto have a defrag program?

Doesn't need it. 


> 9. I can change menu bar color or design,  right?

Yes. 


Some suggested reading for you, since you're considering the switch. 

[ Getting to know Ubuntu: A short level-headed introduction for new users](http://www.friedcpu.net/?p=47) 

That should cover a lot of the things you might want to know before you switch :) 

Have fun. 

- Adam

---

### Post by fuscia on 2007-08-03
> **Tux Aubrey said:**
> Yes, frodon, And please don't overlook Fuscia's slur on Mr Potato Head.

mr. potato head and ktuberling can kiss my you know what.

---

### Post by forrestcupp on 2007-08-03
About customizing the login screen, all you have to do is click on System->Administration->Login Window in the Gnome menus.  In that settings window, you can choose a theme for your login window.  Pretty easy.  There are tons of GDM (login) themes and Metacity/Compiz/Beryl themes (for everything else) over at gnome-look.org

Many people have already said that you don't need to defragment your drive in Linux.  That is because it uses a superior file system that places files in a more efficient manner.  Unless you manually opt to format your drive using fat32 or something, which would be silly.

---

### Post by MR.UNOWEN on 2007-08-03
By the way is that format readable by windows?

---

### Post by igknighted on 2007-08-03
> **MR.UNOWEN said:**
> Regarding the 2x hard drives, is there a way to have two master boot records, one that has options to boot into both and the other with only its own such that if both are in it will go to the one with options and when that one is removed it can boot directly to the remaining hard drive.

If yes, can some try it out and tell me how to go about it?

Yes.  This is the recommended setup in fact.  You leave your windows drive untouched and install Ubuntu to the other.  Then tell Ubuntu to install the bootloader (GRUB) onto the drive you installed Ubuntu on and it should automatically see the windows bootloader and add an entry for it.

---

### Post by Alterax on 2007-08-03
As far as I know, most Linux filesystem formats are not natively run by Windows.  (as a general rule, Windows only recognizes the Fat-16, Fat32/VFAT, and NTFS filesystems).  Linux recognizes all of these (though you do have to add write support for the NTFS filesystems.  This can be done from the add/remove programs menu)

If you are interested in setting up a place to share data between the two systems, then your best option is to create a partition during installation for the shared programs.  Do not give it a mount point, and format it as VFAT.  (You may have to do this last part outside of the installer; I am not sure).  Use this partition to transfer files between the two systems.

If you opt for using Windows by VMWare instead, then there's no big deal there, set up a SMB share on the Linux box and access it through Windows when you need to.  I will say it's slightly easier than setting up a partition for this, if only because you don't have to reboot and go into a different OS every time you want to move a file over.

I'd seriously rethink dual-booting, though.  Considering the amount of resources this uses in terms of disk space for the operating system, duplicated data files, and time spent on setting it up for dual-boot (and actually having to reboot to switch), it's just really not worth the effort.  If you have an application that you must run in windows, it's better to either run it through VMWare if your system can handle it or (ideally) find a Linux-friendly replacement.

--Alterax

---

### Post by igknighted on 2007-08-03
> **MR.UNOWEN said:**
> By the way is that format readable by windows?

Well, not OOTB.  But there is a driver that you can install.  See this link: [http://www.fs-driver.org/](http://www.fs-driver.org/).

I do not know if there is a Vista driver.

Also, I know that (in theory) the Vista bootloader can act as a dual boot manager, but it is complicated and many cannot get it to work properly.  So if you are running Vista and don't want to use grub as the normal bootloader this might be an option.

---

### Post by igknighted on 2007-08-03
> **Alterax said:**
> As far as I know, most Linux filesystem formats are not natively run by Windows.  (as a general rule, Windows only recognizes the Fat-16, Fat32/VFAT, and NTFS filesystems).  Linux recognizes all of these (though you do have to add write support for the NTFS filesystems.  This can be done from the add/remove programs menu)

If you are interested in setting up a place to share data between the two systems, then your best option is to create a partition during installation for the shared programs.  Do not give it a mount point, and format it as VFAT.  (You may have to do this last part outside of the installer; I am not sure).  Use this partition to transfer files between the two systems.

If you opt for using Windows by VMWare instead, then there's no big deal there, set up a SMB share on the Linux box and access it through Windows when you need to.  I will say it's slightly easier than setting up a partition for this, if only because you don't have to reboot and go into a different OS every time you want to move a file over.

I'd seriously rethink dual-booting, though.  Considering the amount of resources this uses in terms of disk space for the operating system, duplicated data files, and time spent on setting it up for dual-boot (and actually having to reboot to switch), it's just really not worth the effort.  If you have an application that you must run in windows, it's better to either run it through VMWare if your system can handle it or (ideally) find a Linux-friendly replacement.

--Alterax

(1) the FAT32 file format is unstable and corrupts easily, fragments horribly, and has a rachable file size limit (try putting a ripped DVD there...)

(2) Windows can read ext3 with a driver (see my above post), and linux flawlessly handles NTFS.  If you feel the need for a separate partition for data transfer, choose one of these file systems.  I would only recommend doing it in order to protect your ubuntu install.  The file permissions are not supported in windows, so root-owned files are not safe when viewed from windows.  I would use an ext3 shared partition to store data on because its the most efficient file system that both can read, and it won't expose your linux system files.

(3) Running a virtual machine is less capable than a true install.  Plus it makes both systems drag.  If you only need one or two apps in windows and they don't run in wine you can try it, but I don't think this is the case.  Virtualization is no replacement for a true HD install on the desktop.

(4) HD space is meaningless these days.  You can get 100+gb for under $50usd if its that important.

Basically, I would strongly recommend avoiding FAT32 like the plague, and not even considering a virtualization solution at this point.

---

### Post by MR.UNOWEN on 2007-08-03
Well I just started the install process. I have the XP disc off and my other hd on. So currently I'm on the partitioning part. Should I have my  mount point as "boot"? I'm going to do a dual boot so I don't know what to do.

---

### Post by Nekiruhs on 2007-08-03
> **MR.UNOWEN said:**
> Well I just started the install process. I have the XP disc off and my other hd on. So currently I'm on the partitioning part. Should I have my  mount point as "boot"? I'm going to do a dual boot so I don't know what to do.
Make partitions with the mount points / and /home . Thats the most advisable tactic.

---

### Post by MR.UNOWEN on 2007-08-03
Ok, I made it home. So correct me if I'm wrong, I can do the grub thing later, right?

Edit

I just go "no root file system is defined"

What should i do?

---

### Post by Nekiruhs on 2007-08-03
> **MR.UNOWEN said:**
> Ok, I made it home. So correct me if I'm wrong, I can do the grub thing later, right?

Edit

I just go "no root file system is defined"

What should i do?
You need a / mount point too. You want to have 2 partitions. And GRUB needs to be done now.

---

### Post by floke on 2007-08-03
Set the mount point to root '/' - doesn't matter about the boot flag AFAIK - and don't worry, Ubuntu will pick up your XP partition and put it in the grub menu list automagically.

EDIT -- Right click on the partition - and select 'root - /'- from the the menu --

---

### Post by MR.UNOWEN on 2007-08-03
Should I turn on my xp disc?

---

### Post by Nekiruhs on 2007-08-03
> **MR.UNOWEN said:**
> Should I turn on my xp disc?
If you want to be able to boot XP without further configuration (text file editing). Yes.

---

### Post by MR.UNOWEN on 2007-08-03
Still no luck.

I did /root, no effect. I thought this was supposed to be easy?
Also there's no option for root, you have to type it in yourself.

---

### Post by PatrickMay16 on 2007-08-03
I don't get why people like to make a big deal of 'making the switch'. Just install ubuntu or whatever linux distribution and use it. If you like it, you'll use it, if you don't like it, oh well. It's not like it's some life changing fork in the road.

---

### Post by koenn on 2007-08-03
> **MR.UNOWEN said:**
> Still no luck.

I did /root, no effect. I thought this was supposed to be easy?
Also there's no option for root, you have to type it in yourself.
Luck has nothing to do with it. 
Preferably, you have 2 partitions on that disk. for one of them, choose
/ as mount point, 
for the other, choose /home. 

/  is where the operating system will be installed, it's called the 'root' of the filesystem
/home is where you'll keep your personal files. 

If you do not have two partitions, you should make them first. 
If you have only 1 partition, you have no choice as to use / as mount point for it. It will work , but can make recovery of your personal files hard or impossible, if you manage to completly ruin your system.

---

### Post by MR.UNOWEN on 2007-08-03
> **PatrickMay16 said:**
> I don't get why people like to make a big deal of 'making the switch'. Just install ubuntu or whatever linux distribution and use it. If you like it, you'll use it, if you don't like it, oh well. It's not like it's some life changing fork in the road.

OK...  well that was helpful...  You realize I'm new to this all and just want some help. Origonaly I just wanted some info about ubutu, because I've been getting mixed messages about how secure ubuntu is and now I'm having trouble installing. 


Any way, I'm still not having any luck, by the way, I selected the manual option...


EDIT -  I got it working.

---

### Post by forrestcupp on 2007-08-03
> **MR.UNOWEN said:**
> OK...  well that was helpful...  You realize I'm new to this all and just want some help. Origonaly I just wanted some info about ubutu, because I've been getting mixed messages about how secure ubuntu is and now I'm having trouble installing. 


Any way, I'm still not having any luck, by the way, I selected the manual option...


EDIT -  I got it working.

Glad you got it working.  I guess you know now that it isn't /root, but rather just / and that *is* root.

By the way, it is a lot easier and just as capable to do the partitioning automatically instead of manually.

---

### Post by esaym on 2007-08-03
> **MR.UNOWEN said:**
> Hello, I'm thinking of making the switch to ubuntu from Win XP and there's just a few questions on my mind.

1. Let's say I do install ubuntu 7.04, have my computer connected to the web, go on the web and Never install anything other than the OS or give approval, is probability getting a virus 0% or is there still a 0.00...01 chance of it?

[COLOR="Blue"]Yes pretty much.  I don't know of any Linux virus[/COLOR]

2. How immune is ubuntu to spyware or anything that may release my personal info such as passwords or any other type of activity whether is accessing a file or surfing the web?

[COLOR="Blue"]Spyware is only a problem on windows computers because Internet Explorer allows websites to install programs.[/COLOR]

Just to give you an example of how vulnerable I was with XP, a friend of mine was able to breack into my computer and obtain my password using a live linux cd. How safe is Ubuntu with passwords?
[COLOR="Blue"]
If you have physical access to a computer's hard drive, you will always be screwed.  Keep your computer away from people you don't trust! [/COLOR]

3. I'm still planning to keep my windows system, so how hard is it with dual booting? They're going to be on separate hard drives and I may disconnect one every here and there. Can I have dual booting and still be able to remove any of the two hard drives?

[COLOR="Blue"]Dual booting is set up automatically during the ubuntu installation.  GRUB is the OS loader that ubuntu uses (NTLDR is the one windows uses) GRUB defualts to installing on the master hard drive on IDE channel 1.  If you remove the hard drive that grub is installed on you will not have an OS loader!  There is a way to choose what hard drive grub is installed to.  I do not know how off hand though.  [/COLOR]

4. I'm into visual effects and am currently using a program called samurize ([www.samurize.com](www.samurize.com)) to display all these little things that created to go on my screen, does Linux have anything like this, where the user can create stuff to go on the screen with little to no coding needed?

[COLOR="Blue"]I don't use effects sorry.[/COLOR]

5. Is there a customize your boot / logon screen tutorial for dummies?
If so please list them in reply.

[COLOR="Blue"]Yes it is pretty easy[/COLOR]

6. How easy is it to add a new theme for Ubuntu?
6b. How easy is it to create a theme for the desktop.

[COLOR="Blue"]The possibilities are endless[/COLOR]

7. Let's say an OS  file corrupts, does the Ubuntu disc have an automatic recover system?
7b. How reliable is the OS recovery system, I had this problem with Win XP and when tried to recover, I sometimes got the BSOD; can the Ubuntu disc crash in recovery (if it has one)?

[COLOR="Blue"]There really is no "recovery method" for a Linux computer.  It doesn't need it.  Windows corrupts it's self.  That is just the way it works.  If there is ever a corruption problem with a Linux computer it would be due to faulty hardware causing the hard drive to corrupt data.  BUT if for what ever reason a system file comes up missing, it can be easily replaced and there is plenty of help on these forums.[/COLOR]

8. Does Ubunto have a defrag program?

[COLOR="Blue"]Windows uses the FAT32 or NTFS file system.  These files systems are very susceptible to file fragmentation.  Ubuntu defaults to using the [EXT3]("http://en.wikipedia.org/wiki/Ext3") filesystem.  It does not have a file fragmentation problem like the windows counterparts[/COLOR]

9. I can change menu bar color or design,  right?

[COLOR="Blue"]Yea[/COLOR]

Thanks

.

---

### Post by esaym on 2007-08-03
> **xzero1 said:**
> Would you guys get real on security? Read what is being patched and why when the system offers an upgrade. Many if not most are security related. In other words the system is vulnerable without the upgrade and therefore between upgrades. If Ubuntu was targeted as much as windows then we would be in trouble. Moreover, since no one uses virus scanners many systems could be infected before anyone knew about it. If a hacker really wants your system he will have it.

Yes but have you ever read any of the changelogs of the updated packages?  Most of these so called "security patches" are for security problems so small that there is almost no point in even patching them:KS

Moreover, a security update can come out within hours of an exploit being found, with MS they do it once a month regardless.


> **MR.UNOWEN said:**
> Still no luck.

I did /root, no effect. I thought this was supposed to be easy?
Also there's no option for root, you have to type it in yourself.

Your root directory is not /root but /

> **MR.UNOWEN said:**
> OK...  well that was helpful...  You realize I'm new to this all and just want some help. Origonaly I just wanted some info about ubutu, because I've been getting mixed messages about how secure ubuntu is and now I'm having trouble installing. 


Any way, I'm still not having any luck, by the way, I selected the manual option...


EDIT -  I got it working.

Not to discourage you, but you are going to have lots of problems!  You do realize that you are trying to change over to a WHOLE new operating system right?  It is not a windows clone.  You are going to have just as much trouble going from windows to mac or another OS.  

I would suggest that you take your  time on this.  You are not going to be able to install ubuntu and get all your windows data over onto it in one night.  For now I would install ubuntu on a dedicated hard drive and boot into it when ever you fell like playing around/exploring.  

Also hang out on here and read threads everyday.  The biggest issue is READ READ READ.  We get 10 posts just like yours everyday here.  I enjoy helping people but I do not enjoy feeling like I need to wait on you hand and foot.  You will have to learn how to find data yourself someday.  If I tell you how to do something and you don't have the proper knowledge to find info and help yourself, you are just going to come right back to me with more questions! :p

---

### Post by forrestcupp on 2007-08-04
> **esaym said:**
> 
Not to discourage you, but you are going to have lots of problems!  You do realize that you are trying to change over to a WHOLE new operating system right?  It is not a windows clone.  You are going to have just as much trouble going from windows to mac or another OS.  

I would suggest that you take your  time on this.  You are not going to be able to install ubuntu and get all your windows data over onto it in one night.  For now I would install ubuntu on a dedicated hard drive and boot into it when ever you fell like playing around/exploring. 

Pretty pessimistic.

You may not have "lots of problems."  Ubuntu *is* ready for the desktop.  It's getting better and better with each release.  If you keep in mind that it is not a Windows clone, like esaym said, you will not have lots of problems.  You just need to know going into this that things work differently and you can't expect everything to work like Windows.  But I think you know that.

Don't let what esaym said scare you away from asking questions here, though.  There are lots of people here more than happy to help.  You just need to post in the right areas.  The cafe is for off topic discussions.  If you have questions, go to "Absolute Beginners" or one of the specialized help sections and you will find all the help you need.

---

### Post by xzero1 on 2007-08-04
> Yes but have you ever read any of the changelogs of the updated packages? Most of these so called "security patches" are for security problems so small that there is almost no point in even patching them

According to this security website [http://secunia.com/product/14068/?task=statistics]("http://secunia.com/product/14068/?task=statistics")
22% critical, 49% moderate for Ubuntu 7.04. Seems like the patches are needed.

---

### Post by jimrz on 2007-08-04
> **MR.UNOWEN said:**
> Regarding the 2x hard drives, is there a way to have two master boot records, one that has options to boot into both and the other with only its own such that if both are in it will go to the one with options and when that one is removed it can boot directly to the remaining hard drive.

If yes, can some try it out and tell me how to go about it?
my setup on this box is similar to what you describe due to issues involving bios/grub/sata2 on my initial install. what I had to do was remove the XP drive, install feisty to the other drive then replace the XP drive. a bit of a pain but it did leave my XP mbr untouched while loading grub on the other. I set the optical drive as option 1 the feisty drive as option2 and the XP drive as option3 in boot order section of setup. this, absent a bootable disk in one of my optical drives, arrangement will boot into feisty automatically or, if I want to boot XP all I need do is hit f12 during initial splash screen and then select the XP drive to boot. Since I rarely need to boot XP and that this procedure takes no longer than the standard grub dual boot way ( a bit faster to feisty and about the same (but with fewer key strokes involved) for XP, I never have even bothered to add an XP otion to menu.lst on the feisty side. you could likely setup about the same way. the only issue might be that, at least on this box, I must have a hdd (not necessarily the highest boot priority drive) plugged into the 1st sata connection or the machine will not boot. if yours proves to be the same and moving a drive to a different plug confuses your grub or win mbr, I do not know of any work around for this.

---

