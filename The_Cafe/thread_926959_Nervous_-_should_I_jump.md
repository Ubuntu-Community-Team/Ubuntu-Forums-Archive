---
title: "Nervous - should I jump?"
date: 2008-09-22
forum: The Cafe
---

### Post by uberdonkey5 on 2008-09-22
I saw ubuntu just before buying a new lap top in 2007. I bought one with vista (couldn't get ubuntu preinstall). I wiped it, installed ubuntu, and then realised I was a little lost. SO I reinstalled vista, reinstalled ubuntu and for about 6 months I used both. Recently I repeated this, cos I used ubuntu almost exclusively and wanted more HD space for ubuntu. Unfortunately the vista install is buggy (for drivers). I only ever go into Vista now when I have a problem with ubuntu, but I ALWAYS go back into ubuntu when I realise I can't solve the problem with vista either.

I feel like I want to wipe disk and reinstall ubuntu only (boots up faster on its own). But something is holding me back, like there will be software I can only use in windows that will come out, or that I will distance myself from the mainstream microsoft office environment. Basically, once its done its a hassle getting dual boot back.

5 main questions:

1. does repeated reinstallations damage a computer in any way?
2. anyone feel they lost touch with the mainstream (like forgetting how to use windows software) due to exclusive use of ubuntu?
3. Is it not good to have a back up operating system on your computer?
4. what do I need to backup (ok, so websites, home directory , wallpapers and themes.. anything else?)
5. I'm also thinking of changing my file system at the same time. What do you prefer and why?

---

### Post by will1911a1 on 2008-09-22
1. It won't damage your computer.

2. Not at all, although I have to use Windows at work every day.

3. It's not bad... it's really up to you.

4. Make sure you back up any pictures or music that you have saved.

5. I use ext2, but not for any particular reason.

---

### Post by vishzilla on 2008-09-22
1. not sure. i don't shuffle OSes
2. windows is a bit alien to me now. I have a virtual XP, but don't use it much.
3. I dont think so. (though I've a virtual :) )
4. backup whatever you feel is important.
5. ext3. no reason :D

---

### Post by finer recliner on 2008-09-22
> **will1911a1 said:**
> 1. It won't damage your computer.

2. Not at all, although I have to use Windows at work every day.

3. It's not bad... it's really up to you.

4. Make sure you back up any pictures or music that you have saved.

5. I use ext2, but not for any particular reason.


same answers as will, but i use ext3. the only real difference between ext2 and ext3 is the latter has journaling capability.

---

### Post by timcredible on 2008-09-22
1 - no
2 - no, it's point and click, simple enough even managers can use it
3 - i leave windows on my machines as a just-in-case, but have only used windows 2 or 3 times in 8 years
4 - same as other posters said
5 - ext3 because of journaling

---

### Post by mips on 2008-09-22
> **uberdonkey5 said:**
> But something is holding me back, like there will be software I can only use in windows that will come out, or that I will distance myself from the mainstream microsoft office environment. Basically, once its done its a hassle getting dual boot back.


I think I can solve that problem for you if you are not a heavy gamer. Install Vista in a VM like Virtualbox on Ubuntu. This way you can still have access to Vista & related apps if you really need them. And yes, it's fast.

---

### Post by Yannick Le Saint kyncani on 2008-09-22
Hi uberdonkey5, here are my answers :

> 1. does repeated reinstallations damage a computer in any way?

Yeah, if you do millions of installations using the same drive, it will be damaged. Assuming you don't spend day and night installing/reinstalling for thirty years straight, it will be fine.

>  2. anyone feel they lost touch with the mainstream (like forgetting how to use windows software) due to exclusive use of ubuntu?

Yes, I have. But I am also more confortable with debian/ubuntu and I get more time for myself :)

So I can idle in ubuntuforums ;)

>  3. Is it not good to have a back up operating system on your computer?

I have ubuntu hardy (kde) as my main OS and ubuntu hardy (gnome) as a backup. I also use the backup to test the next release and upgrade path, so that I know I can upgrade safely without having any hardware-related trouble.

>  4. what do I need to backup (ok, so websites, home directory , wallpapers and themes.. anything else?)

You need to use tools you are confortable with, nothing more, nothing less.
I like backuppc, rsync, duplicity and a bit of personnal scripts of course :)

> 5. I'm also thinking of changing my file system at the same time. What do you prefer and why?

Ext3, because it's mainstream so I can expect near-zero bugs.


PS: I think I will enjoy reading what others have to answer :guitar:

---

### Post by CorvisRex on 2008-09-22
Good set of questions...  I like you, almost never use windows anymore, Pretty much only use it when I occationally play games (which is not often)  My take...

1. No, I do tons of installs, for testing, checking out new distros, etc.  Never been a problem. Though removing Vista has cuased problems, so look it up first, it is imfamous about fragging HDs when you try to remove it...

2.  No, windows DOES feel alien, and kinda "Wrong" somehow, since I so rarely use it.  But, unless you need to keep you knowledge current, like are an IT admin or something, it realy does not matter.

3.No, having a 2nd os doesn't hurt, but since I found a linux emergency repair and boot cd, It is not needed for anything.  extra OS installs for me are only for testing.  That is one of the joys of LiveCDs, if you have any problems, particularly if you did something "Bad" to your HD,  it is easily fixed.  LiveCDs have saved my tuchas a couple of times. 

4. Backups are always good.  I ALWAYS put my /home on a seperate partition, a nice big fat one, since that is where the majority of the space use is.  Thus keeping my / mount point small. This makes it very easy to backup, painless to restore, and easier if at somepoint you choose to switch distros. Pretty much everything is in there that I need, sure, some things are in /usr/share/...  etc, icons, themes, etc.  pretty much easy to reinstall if need be, so I never really worry about it and just backup /home.

5. Beyond ext3, no real reason to change anything,  I've looked up other types, like Sun's zfs etc.  but for home use, there doesn't really seem to be a need to change to anything else, yet at least, unless you do REALLY HD intensive at home.  Some people really love using LVM as well, particularly when they have a complex partition structure, it has pros and cons. 

hope it helps.  And you can always install windows in a Vbox virtual machine in the future if you ever feel a driving need to remind yourself why you use linux,  or just have to play that new game...

---

### Post by Sealbhach on 2008-09-22
I have one main reason I keep my vista partition (which I never use). If I make a change in Ubuntu and I lose the internets and don't know how to fix it, I can go into windows and get the internets there.

After paying all that money I have to make some use of it.


.

---

### Post by Dragonbite on 2008-09-22
You could also get a 2nd hard drive (ebay? someting small~ish) to install Vista on and then put it in your sock drawer for "just in case".  I've got one hard drive for my Windows XP which hasn't seen the light of day since I got another hard drive for Ubuntu (and one more play on for the computer club).

**1. does repeated reinstallations damage a computer in any way?**
1. Not in the foreseeable future. Eventually the constant hard disk use would wear it out but at this day and age it can last a loooong time.  I still have a hard drive that came with a Pentium I w/MMX laptop if that gives you any idea how old it is.
*Oh, and I'm a distro-ADHD user, so yeah, there have been a number of installs, formats and even encryption :lolflag:*

**2. anyone feel they lost touch with the mainstream (like forgetting how to use windows software) due to exclusive use of ubuntu?**
2. I use Windows at work which is fine, but when I have to use Windows at home I find it is a pain! Constantly needing updates and scanning, if I want to use Windows I have to give it a day for doing all of its updates and scanning before I can actually USE it.

**3. Is it not good to have a back up operating system on your computer?**
3. Having a backup OS on the hard drive isn't bad, but with the abilities of LiveCDs and LiveUSB it isn't as necessary as it once was. Plus if you put your /home directory on a separate partition and back that up then you can re-install your main OS and not have to worry (as much) about loosing everything.

**4. what do I need to backup (ok, so websites, home directory , wallpapers and themes.. anything else?)**
4. To be save, just backup everything in the C:\Documents and Settings\username directory (or at least, that's where it was in Windows XP) and that will get your files and application settings.

**5. I'm also thinking of changing my file system at the same time. What do you prefer and why?**
5. Ext3 seems to be the standard. Ext4 is on the horizon but give it time to get worked out. ReiserFS has an uncertain future now that Hans has been convicted.  If you are looking to dual-boot then it may be worth setting aside a vfat partition as a DMZ for passing back-and-forth between Windows and Linux.

It was mentioned, a virtual machine (VM) is always an option. If it is a later-model laptop then it should be able to run things without too much trouble (just minimize the number of services running and only include the apps you really need).

---

### Post by oldsoundguy on 2008-09-22
> **uberdonkey5 said:**
> 5 main questions:

1. does repeated re installations damage a computer in any way?
2. anyone feel they lost touch with the mainstream (like forgetting how to use windows software) due to exclusive use of Ubuntu?
3. Is it not good to have a back up operating system on your computer?
4. what do I need to backup (OK, so websites, home directory , wallpapers and themes.. anything else?)
5. I'm also thinking of changing my file system at the same time. What do you prefer and why?

1) others have said it .. NO
2) I have 5 computers .. 3 Ubuntu and 2 XP all networked.  The MAIN XP computer is for running media (something that Linux is getting better at, but NOT YET in some instances) and for photography .. IE, ADOBE, which is still better than GIMP (plus the fact I PAID way too much for it in the first place and want to get my bucks and INSTRUCTION costs back via usage!)
3) see answer #2 .. with Linux, the chances of a total un-recoverable crash is VERY slim unless hardware is at fault, and any back up would be un-usable in that instance.
4) your personal folder in Ubuntu needs to be copied.  Save all your image, music, documents .. those can be burned to a disk, too.  Save your browser contents just as you would in Windows.
5) I dance with the one that came with the system.  Never have seen a need to do otherwise.

---

### Post by Bölvaður on 2008-09-22
because I want to be really popular I pick the most popular thread and restate everything everyone else have said about 10 times already but in shorter manner:

1,2,3,4,5) No


Thank you very much :)

---

### Post by uberdonkey5 on 2008-09-23
> **Dragonbite said:**
>  ReiserFS has an uncertain future now that Hans has been convicted.     

wow, any links between excessive linux use and a tendency to murder? Interesting article:
[http://www.theregister.co.uk/2008/04/29/hans_reiser_found_guilty/](http://www.theregister.co.uk/2008/04/29/hans_reiser_found_guilty/)

Thanks for all the replies. Nobody mentioned the XFS file system. I was considering that, but as a bit of a newbie I didn't want to change a file system to something non standard if it didn't seem popular in case I had some weird problems.

I've decided that, when I get the time, I'm going to:
1. make sure I have my original ubuntu disk (misplaced it somewhere!)
2. Keep standard filesystem
3. format hard disk and install ubuntu (alone)
4. buy a hard drive back up and find a copy of windows XP to put on it (with office) [this was a particularly good idea]

In this way I get a stable, fast system with windows if I ever ever need it.


P.S. I know I stuck this in community cafe... it was just cos it was something I was reflecting on, unlike most of my threads in other forums which tend to have a sense of urgency about them :)

---

### Post by Bölvaður on 2008-09-23
you might get into trouble installing xp afterwards because xp isnt what we can call "other os friendly". So you might need master grub disk to restore the option to boot into ubuntu.

---

### Post by qazwsx on 2008-09-23
> **uberdonkey5 said:**
> 
2. anyone feel they lost touch with the mainstream (like forgetting how to use windows software) due to exclusive use of ubuntu?
Yes and no. Thre are bunch of cool CLI apps that works natively on Windows as well (including bash, coreutils, wget, mencoder, mplayer and so on). But using those apps would freak out ordinary Windows people (as well some Linux users)
KDE also has  (partially) Windows port. I guess my Windows desktop would be pretty wierd. Thanks to free software :lolflag: And not so easy to maintain. Windows gives me only crappy OS  and not so many apps.

---

### Post by Vince4Amy on 2008-09-23
> Nobody mentioned the XFS file system. I was considering that, but as a bit of a newbie I didn't want to change a file system to something non standard if it didn't seem popular in case I had some weird problems.

If you're going to use XFS you will need to have a seperate boot partition, perhaps 200MB or so ext2. I always use JFS as it's mature, stable and fast.

---

### Post by lisati on 2008-09-23
Pretty much what the other posters said: and don't be scared of arranging for a backup of your important data on a separate partition (good) or drive (better) just in case something gets messed up.....And getting your installation CDs from reputable sources is a good idea.

---

### Post by Ms_Angel_D on 2008-09-23
Just wanted to point out a couple of helpful tools to the OP for backup purposes

[Foxmarks]("https://addons.mozilla.org/en-US/firefox/addon/2410") (Wonderful for keeping your bookmarks backed up)
[FEBE]("https://addons.mozilla.org/en-US/firefox/addon/2109") (Backs Up Your Firefox Settings and Extensions)

Hope these help ;)

---

### Post by Dragonbite on 2008-09-23
> **qazwsx said:**
> Yes and no. Thre are bunch of cool CLI apps that works natively on Windows as well (including bash, coreutils, wget, mencoder, mplayer and so on). But using those apps would freak out ordinary Windows people (as well some Linux users)
KDE also has  (partially) Windows port. I guess my Windows desktop would be pretty wierd. Thanks to free software :lolflag: And not so easy to maintain. Windows gives me only crappy OS  and not so many apps.

I've been moving my windows to open source apps when I can so as to get my wife used to them and not freak out when she's on Linux instead of windows; Firefox, Thunderbird, Gimp, Inkscape, Pidgin, Dia, OpenOffice.org are great places to start.

But I didn't know about the command line apps, thanks!

---

### Post by lukjad on 2008-09-23
> **uberdonkey5 said:**
> 1. does repeated reinstallations damage a computer in any way?

Not more than shutting down and turning on the PC will.

> 2. anyone feel they lost touch with the mainstream (like forgetting how to use windows software) due to exclusive use of ubuntu?

Not really. If you do, you can always go to a public library to try it out. But honestly, as long as you don't have to start troubleshooting for an IT company or take tests in Windows knowledge, there is not damage.

> ]3. Is it not good to have a back up operating system on your computer?

I don't really know.

> 4. what do I need to backup (ok, so websites, home directory , wallpapers and themes.. anything else?)

Personal files, like .doc, pictures, movies, sound etc.

> 5. I'm also thinking of changing my file system at the same time. What do you prefer and why?

I use ext3. I used to use ReiserFS but I don't think that is supported anymore.

---

### Post by aaaantoine on 2008-09-23
Don't jump!  You have too much to live for!

Wait, is this about converting fully to Ubuntu?  Yeah, go ahead.

Remember, you can always install Windows in VirtualBox (or some other virtual machine) to run those Windows apps that don't run in wine.  Just don't expect to get any 3D games going in a virtual machine.

---

### Post by uberdonkey5 on 2008-09-24
> **aaaantoine said:**
> Don't jump!  You have too much to live for!

Wait, is this about converting fully to Ubuntu?  Yeah, go ahead.

Remember, you can always install Windows in VirtualBox (or some other virtual machine) to run those Windows apps that don't run in wine.  Just don't expect to get any 3D games going in a virtual machine.

well, despite not having too much to live for ;) I don't use games but its things like Excel visual basic I used to use. Heard that some things just don't work well on wine or virtualbox.

---

### Post by mips on 2008-09-24
> **uberdonkey5 said:**
> Heard that some things just don't work well on wine or virtualbox.

Wrt Virtualbox, what exactly does not work? I think what you heard is nonsense. If you install XP in Virtualbox everything behaves just like it behaves in XP.

The only exception to the above is stuff like games that requires hardware 3D support.

I have XP installed in Virtualbox and everything works.

---

### Post by uberdonkey5 on 2008-09-24
that sounds super. Definately another option then. Thanks!

---

### Post by barbedsaber on 2008-09-24
[http://hehe2.net/thedarkside/microsoft/run-windows-apps-100-seamlessly-on-ubuntu/](http://hehe2.net/thedarkside/microsoft/run-windows-apps-100-seamlessly-on-ubuntu/)

one more reason to jump
(DO A FLIP!)

---

### Post by tarps87 on 2008-09-24
Some visual basic bits will run under wine, you can also use Mono for .net programs, but realistically a vm would be best.
I use Virtualbox and there were a few problems when it changed hands to sun Microsystems but they've been fixed and it runs fine now. Virtualbox also has a seamless mode where you can combine the two desktops.
I tend to backup the bits I use regularly and any programs I've downloaded.
Games are the only thing that keeps me duel booting, the rest there are usually alternatives to.
I use xp at work and don't have any problems with using it. I did have problems with office 2007 but that was as they moved the buttons :confused:

Edit: [http://www.osalt.com/](http://www.osalt.com/) has open source alternatives for most windows programs

---

### Post by Linux&amp;Gsus on 2008-09-24
uberdonkey5, I believe pretty much all is said already. Just one tip to save yourself some work...

> **uberdonkey5 said:**
> 3. format hard disk and install ubuntu (alone)
4. buy a hard drive back up and find a copy of windows XP to put on it (with office) [this was a particularly good idea]

In this way I get a stable, fast system with windows if I ever ever need it.

You want to keep a 2nd HDD for a just-in-case/disaster situation? So that you have access to a running system? Well, you have a HDD with 2 working system already. Why wipe it, re-install, get a new drive, install more...
Keep the drive as is, maybe make sure that, as of now, all updates are installed and working. Put it in your drawer or whatever other convenient and  save (!!) place. Get a new drive (size, speed, cache, price tag) of your liking and install Linux on there. Hopefully you have backed up your data from the old drive (Linux and Win), put it back to your new system and be happy.
Time saved, no need to install more than one system. Plus you have 2 backup systems on your current drive. \\:D/

In any case, when you (re-)install Linux make sure to have /home as a separate partition.

Cheers.

PS: I'm one of the many ext3 user. No real reason, except maybe that many people are using it (well tested), it's well supported and I didn't really hear of any major troubles. Actually no troubles at all. Basically it was a "I'm playing safe" decision. ;)

---

### Post by Dragonbite on 2008-09-24
> **uberdonkey5 said:**
> well, despite not having too much to live for ;) I don't use games but its things like Excel visual basic I used to use. Heard that some things just don't work well on wine or virtualbox.

Depending on how involved your VBA is, OpenOffice includes Basic support (though they prefer Java).

I found [[COLOR="Blue"]Go-OO[/COLOR]]("http://go-oo.org/") which is, according to their website:> Go-oo has built in OpenXML  import filters and it will import your Microsoft Works files. Compared with up-stream OO.o, it has better Microsoft binary file support (with eg. fields  support), and it will import WordPerfect  graphics beautifully. **If you are reliant on Excel VBA macros - then Go-oo offers the best macro fidelity too. **If you expect your spreadsheets to calculate compatibly, or you get embedded Visio diagrams in your documents, you'll want Go-oo. 
(emphasis added)

I don't know much about it, but I am interested in what you find out about it and VBA.  Right now I'm working on a project from Excel with VBA and I am finding i have to modify the code to make it work but not majorly.

---

### Post by oldsoundguy on 2008-09-24
There is also another option of purchasing Bordeaux and inserting it in WINE.  Then you can run MS Office, IE, Adobe CS2, any Steam based game and maybe some others .. not sure.  Worth a look for 20 bucks and that means you do NOT have to install the Windows OS and the required protection software (to protect others, not you) and the clean up and maintenance crap you have to install in order to run the Windows OS ANYWHERE if you take it on line! 
NOT sure how well the program works, but really worth it to investigate if you are contemplating PAYING for a Windows OS to put it in a virtual box.

---

### Post by notwen on 2008-09-24
1. No more than normal wear/tear on hardware.  I certainly wouldn't go out of your way to re-install your OS every other day, but here and there won't kill your machine any faster.

2. Going on 3 years now w/o any Windows installations in my household.  I have XP Pro installed in VirtualBox if I ever need it, but it gets used maybe once a month, if that.  And I'm perfectly comfortable forgetting Windows, although I use Windows everyday at work.  =\

3. Good back up OS is as simple as having a LiveCD distro around to access your HDD should your installed OS become un-accessiable.


4.  Backup stuff that you want, I stick w/ daily usage stuff.  The rest I do monthly backups for settings/customizations/etc.

5. EXT3 for Linux, it's the norm.  I'll stick w/ the 'if it isn't broke, don't fix it' motto.  I generally stick w/ FAT32 for EXT drives and flash drives.  For any file exceeding FAT32's 4GB limit, I generally just rar.  

Hope this helps.  =]

---

### Post by Dragonbite on 2008-09-24
> **notwen said:**
> 3. Good back up OS is as simple as having a LiveCD distro around to access your HDD should your installed OS become un-accessiable.

I ran into trouble with that once when I then realized the hard drive was encrypted!

Ok, after a little work I got past that.

Then I found the partition was an LVM format, not Ext3 so I had to go through ANOTHER search-read-and-destroy to get past that little piece.

So make sure if you are going to go with a LiveCD recovery concept, that you have all of the tools you need to access it.

---

### Post by notwen on 2008-09-24
> **Dragonbite said:**
> I ran into trouble with that once when I then realized the hard drive was encrypted!

Ok, after a little work I got past that.

Then I found the partition was an LVM format, not Ext3 so I had to go through ANOTHER search-read-and-destroy to get past that little piece.

So make sure if you are going to go with a LiveCD recovery concept, that you have all of the tools you need to access it.

Agreed, hopefully going w/ an encrypted install would warrant you know what you're getting into.  =p

---

### Post by Dragonbite on 2008-09-24
> **notwen said:**
> Agreed, hopefully going w/ an encrypted install would warrant you know what you're getting into.  =p
Never stopped me before! :lolflag:

---

