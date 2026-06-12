---
title: "Switching from Windows to Wild Dog (Yikes!)"
date: 2010-07-14
forum: System76 Support
---

### Post by ShowMeGrrl on 2010-07-14
Hello all -- I finally have taken the plunge and just ordered a new Wild Dog to be my main home computer, after years of using Microsoft Windows.

I'm pretty nervous, because, though I use computers a lot, I've never built or repaired one, never installed an operating system, never edited the registry and do not have extensive experience with Linux. 

In addition, I have several legacy Windows programs that I will need to "take with me" to the Linux world and plan to install Virtual Box. I have zero experience with virtualization.

Occasionally, I wake up in the middle of the night and wonder if I've made a huge mistake. But the deed is done and the Wild Dog is on its way.

My question is what is the best way for me to transfer over all of my data from my Windows XP box to the Wild Dog? I believe (though I'm not 100% sure) that my Windows box has a SATA drive.

I apologize in advance, because I'm sure this will not be the last advice I will be asking for!

---

### Post by PabloH on 2010-07-15
I think you are going to be fine. It sounds like you have it figured out pretty well. There will be lots to learn, but you will have plenty of time to learn it.

VirtualBox was a great idea. Installation on it is pretty straightforward and there are plenty of places that can help you get through this if need be.

I would recommend copying over your data to the new computer through a network connection from your old computer. 

I would also scan it for Viruses using free virus scanner (ClamAV) you can download from Ubuntu's software repository. This will keep any old bugs from infecting your new VM.

---

### Post by ShowMeGrrl on 2010-07-15
> I would also scan it for Viruses using free virus scanner (ClamAV) you can download from Ubuntu's software repository. This will keep any old bugs from infecting your new VM.

Thanks, Pablo. The reassurance helps!

Are you saying scan the data while it is on the old machine before transferring it? Or are you saying transfer the data to the new machine and then scan it there? 

If the former (scan it on the old machine), then presumably I would use a Windows-based virus scanner rather than one I would get from the Ubuntu repository?

If the latter, then if I did have old bugs, wouldn't I have already infected the new VM if I waited to scan the data until after I had already loaded it onto the new VM?

I am not very experienced at doing this, so please forgive me if these are not the brightest of questions.

---

### Post by techunit on 2010-07-15
It won't scan as you transfer but scanning is a great way to keep others from getting viruses. You are unlikely to have many problems with a factory computer that comes with Ubuntu. I would recommend that you check out the link in my signature for some tutorials on installing applications and other tasks that you may find useful. 

What are the programs you need to run? Purhaps I can shed some light on the subject and tell you if you really need to install virtualbox or you can just use something called WINE. If you have any questions let me know. If you need me to point out a video or even make a video tutorial I would be pleased (I need ideas despirately) back on subject.

Don't worry. you won't have to use the terminal or anything of that nature right away or even ever if you don't want to.

Note if you don't know much about Ubuntu then do try installing Ubuntu in Virtualbox (I have a video) so you can mess around and test if something you found on the internet for ubuntu isn't going to cause problems...

---

### Post by ShowMeGrrl on 2010-07-15
>  I would recommend that you check out the link in my signature for some tutorials on installing applications and other tasks that you may find useful. 

What are the programs you need to run? Purhaps I can shed some light on the subject and tell you if you really need to install virtualbox or you can just use something called WINE. 

Thanks, techunit. I checked out the link and it looks as if there are some good tutorials there that will be helpful once I get the Wild Dog.

Among the Windows programs I'll want to take with me: Quicken, Homesite 4.1, TopStyle Lite, PaintShop Pro, the scanner software that came with my HP Scanjet 4850, software for my golf gps rangefinder, software for my Sony Ericsson cell phone, the Thayer Birding software, Applian software for capturing streaming media, Adobe Digital Editions, and Microsoft Office 97.

I have years of data on Quicken so I am kind of wedded to it, as mad as I get at it at times. 

I know about Bluefish and Netbeans, but I have never found a programming editor that I like as well as Homesite 4.1, which I adore. You will have to pry it out of my cold dead hands....

I know about the Gimp and will give it a try, but I already know how to use PaintShop Pro and, thus, if the Gimp has too steep a learning curve, I'm sure I'll be tempted to fall back onto PaintShop Pro. 

Adobe Digital Editions is the only way I can download copyright-protected e-books from the public library and from bookstores. I wish Adobe would port the program to Linux. 

I am very comfortable using Open Office and will use that as my primary office software, but occasionally I do need to fall back onto Office 97 for one reason or another. (I've got some macros that I don't want to have to recreate in Open Office, for example.)

I will also want to download mp3s from Amazon and will need to install their wizard or downloader or whatever it's called to do that. I don't think they have a Linux version.

> If you have any questions let me know. If you need me to point out a video or even make a video tutorial I would be pleased (I need ideas despirately) back on subject.

Don't worry. you won't have to use the terminal or anything of that nature right away or even ever if you don't want to.

Thanks for that offer. I'm sure I will be overflowing with questions once I get started on this journey. I get a new desktop computer about every five years and even when I was just moving from one Windows machine to another or having to deal with a reinstalled Windows, it always was a major deal that took me seemingly weeks to accomplish.

I do not fear the terminal. I have used it on a number of occasions, but it is a little laborious, because I don't know most of the commands. I am usually copying commands given to me by others. I have the various cheat sheets with all the BASH commands, but that's really not enough to use the terminal well. You really have to understand your machine to know which commands to use to troubleshoot a problem with, say, your sound or your wi-fi or an external drive, etc.

What gives me cold sweats is talk of partitions and mount points and BIOS and the like.

When I first used Linux, I had a devil of a time copying and pasting files because of permissions issues. I eventually just gave myself permission (via the terminal and with BASH cheat sheet in hand) to copy and paste files into a whole bunch of folders because I got sick of dealing with it on a discrete (file by file) basis. But I was a little worried that I had somehow compromised security by doing so. I didn't understand why I had to make those changes just to have the computer be reasonably convenient to use. 

I like to use my computer a lot but I don't like to spend a lot of time hassling with it to get it so I can do productive work on it fast. I want to work on my work; I don't want to work on my computer!

---

### Post by isantop on 2010-07-15
Hi there.

I don't think you'll be disappointed. Ubuntu is very easy, convenient, and simple. Like they say, Linux for Human Beings!

Once you get your files over, you should be good to go. For at least a few months (and most probably never), you shouldn't have to worry about partitions. You'll never have to learn anything about mount points and the BIOS except that they exist (although, I should point out that it really is hardly new stuff. All computers, even Windows and Mac machines, have a BIOS).

The best way to avoid having permissions issues is to avoid running commands as root or sudo. If you rarely do that, then you should find that all the files you need to access are already set up for you to have permission to access them.

Any other problems are ones we'll take care of here. You won't need to worry about a thing.

---

### Post by techunit on 2010-07-15
Ok well you can run Microsoft Office in an application called WINE. As for quicken you may have to set up a Virtual Machine. Virtual Machines are easy to use all you need to do is install the software and have your Windows Install CD in the tray... (You could watch my video on installing Ubuntu In Virtualbox the same applys for Windows just once you select the Windows CD your on your own. sorry) Um most of those applications are going to have to be run in a Virtual Machine so you may want to get some information about it...

---

### Post by ShowMeGrrl on 2010-07-15
> **techunit said:**
> Ok well you can run Microsoft Office in an application called WINE. As for quicken you may have to set up a Virtual Machine. Virtual Machines are easy to use all you need to do is install the software and have your Windows Install CD in the tray... (You could watch my video on installing Ubuntu In Virtualbox the same applys for Windows just once you select the Windows CD your on your own. sorry) Um most of those applications are going to have to be run in a Virtual Machine so you may want to get some information about it...

One recent thought that concerns me: The System76 Wild Dog has 64-bit Ubuntu on it, and my plan is to install Windows XP using Virtual Box. Will the fact that Windows XP is a 32-bit program be a problem? I sure hope I don't have to buy a copy of Windows 7 -- and probably most of these legacy programs I want to run might have problems running in Windows 7 anyway.

---

### Post by gamerchick02 on 2010-07-15
This shouldn't be a problem.

I virtualized WinXP for a few months using 64-bit Ubuntu on my pangolian.  Just make sure you get the correct VM.  I recommend VirtualBox from Sun: [http://www.virtualbox.org/](http://www.virtualbox.org/)

They have a .deb that's simple to install, plus a lot of documentation to get you started.

I use SimpleScan with my HP 1210 all in one scanner/printer/copier thing; try it out and see if it'll work with your machine.

Enjoy the Wild Dog; I hear it's a great machine.  If I need a desktop, I'd get a S76 one for sure.

Amy

---

### Post by ShowMeGrrl on 2010-07-15
> This shouldn't be a problem.

I virtualized WinXP for a few months using 64-bit Ubuntu on my pangolian.

Whew!

> I use SimpleScan with my HP 1210 all in one scanner/printer/copier thing; try it out and see if it'll work with your machine.

I'll give it a try, Amy. Thanks. My HP scanner software allows me to save scans as searchable .pdfs and non-searchable .pdfs as well as .jpgs and variety of other formats. Does SimpleScan have that functionality?

---

### Post by gamerchick02 on 2010-07-15
I think you can scan to pdf and jpeg, but I'm not sure. I usually use the default...

Amy

---

### Post by isantop on 2010-07-15
> **gamerchick02 said:**
> I virtualized WinXP for a few months using 64-bit Ubuntu on my pangolian.
confirmed. In fact, a 32-bit guest OS should actually perform a little better than a 64-bit guest OS.

They have a .deb that's simple to install, plus a lot of documentation to get you started.[/QUOTE]
There's also an Open Source version available from the Ubuntu repositories. Just open up Software Center and search for "Virtualbox"

We also have a knowledge base article detailing how to get Windows running under Virtualbox. The link is [here](http://knowledge76.com/index.php/Virtualize_Windows).

---

### Post by ShowMeGrrl on 2010-07-15
> There's also an Open Source version available from the Ubuntu repositories. Just open up Software Center and search for "Virtualbox"

I seem to recall earlier posts on this forum that the open source version does not support USB? Has that changed? 


> We also have a knowledge base article detailing how to get Windows running under Virtualbox. The link is here.

Great! I'm sure I will be visiting that page often!

---

### Post by ShowMeGrrl on 2010-07-15
> The best way to avoid having permissions issues is to avoid running commands as root or sudo. If you rarely do that, then you should find that all the files you need to access are already set up for you to have permission to access them.

Good to know. I often use sudo when I'm at the terminal prompt. I guess I didn't realize the consequences of that. I thought I was supposed to use sudo. Clearly, I have a tenuous grasp of the Linux OS.

---

### Post by tech newbie on 2010-07-15
> **ShowMeGrrl said:**
> Good to know. I often use sudo when I'm at the terminal prompt. I guess I didn't realize the consequences of that. I thought I was supposed to use sudo. Clearly, I have a tenuous grasp of the Linux OS.

Depends on the task at hand. For example, any apt-get command will require sudo or it won't work. Sudo justs lets you run a task as root without the risks of logging on as root. ( Well thats my understanding i am also a newbie). Never run a command without knowing what it will do  ESPECIALLY if it is a sudo command. If you are willing to learn linux and how to do things with the os. You should have no problem. Linux isn't hard, just different. Installation is done differently (biggest change). No more downloading .exe files and clicking on them and using the wizard to install. Use the repositories, occasionally you may just need to download a .deb file and double click on that. This is just the system 76 section of the official ubuntu forums. You can go anywhere here for support. There is a great community here to help. Plus there is some nice documentation.

 Also system 76 has their own driver program for some extra stuff. So if you ever have to reinstall the os you will need to download that. (link in their knowledge base website). Also most system 76 computers have 64bit linux. You can run 32 bit programs on 64bit BUT you will need to install 32bit libraries. But you shouldn't need to. One of the first things you should do is install the ubuntu-restricted-extras package. This is provides various codecs and I am pretty sure it also gives java and flash. (You may need to install 32bit libraries since there is no 64bit flash, there was a beta but it has been temporarily withdrawn) You will need a package called libdvdcss2 to play encrypted dvds (such as store bought movies). libdvdcss2 isn't in repositories and its legality is in the grey area but it has never been legally challenged in court. I hear it is in the medibuntu repository. You must get that from medibuntu.org 
And the minimize, maximize, close buttons have been moved to the left side. It's a little annoying but there are guides on how to move it back. Or you could use a different theme. :D

---

### Post by jdb on 2010-07-15
> **ShowMeGrrl said:**
> Whew!



I'll give it a try, Amy. Thanks. My HP scanner software allows me to save scans as searchable .pdfs and non-searchable .pdfs as well as .jpgs and variety of other formats. Does SimpleScan have that functionality?

Over the years, one by one, I've found Linux applications that I like better than the old windows apps.
A good start is using OpenOffice instead of MSOffice.

The only thing I still need windows for is my epson scanner app,
it has just too many bells & whistles that I can't get to in Linux.
I have an old copy of windows 2000 I run in VirtualBox that takes care of that.

jdb

---

### Post by bill516 on 2010-07-16
My experience matches jdb's over the last three years.  Xsane will handle my HP 4070 scanner but the HP software under WinXP does a better job for me.  So when I scan I use the XP+HP combination.

BTW Windows 7 will not support the 4070 so going there would not solve my scanner problem.  And if it did it would introduce a new series of problems!

I am a fairly serious photographer.  I used Adobe Photo Elements under XP and it works well.

I now use Digicam and GIMP which work very well.  For my purposes the handling of file types is particularly good.

Take your time to learn, explore and experiment.  Learning new tools does take a bit of time.  People on the Ubuntu forum are very helpful.  System 76 support is the best I have seen in many years for mass-market consumer PC's.

If you are going to move to Linux you are in the right place.

BTW:  I started out dual-booting between XP and Linux on a laptop.  Dual-booting finally bit the dust because I found I just did not go over to XP very much at all.  An XP Desktop box continues to run in order to handle Flight Simulators and the scanner.

---

### Post by isantop on 2010-07-16
> **ShowMeGrrl said:**
> I seem to recall earlier posts on this forum that the open source version does not support USB? Has that changed? 

The open source version does not support USB yet. But, if you don't need it, the OSE is a great option. The knowledge base article covers both the standard and OSE versions, so it really doen't matter anyway.


Sudo is a tricky fiend. The way I use it is this: if I run a command that I expect to work, and it fails (especially if it says "Permission Denied") then I repeat the command with sudo (just run sudo !! to repeat the last command with sudo).

In general, don't use sudo if you don't know what the command will do (ask). Also, don't use sudo for file management (sudo cp ... or gksudo nautilus) unless you get permission errors. This will help prevent those nasty permissions problems.

---

### Post by ShowMeGrrl on 2010-07-16
> Sudo is a tricky fiend. The way I use it is this: if I run a command that I expect to work, and it fails (especially if it says "Permission Denied") then I repeat the command with sudo (just run sudo !! to repeat the last command with sudo).

In general, don't use sudo if you don't know what the command will do (ask). Also, don't use sudo for file management (sudo cp ... or gksudo nautilus) unless you get permission errors. This will help prevent those nasty permissions problems.

I think that must have been my problem. I was using the sudo nautilus-no-desktop command to get the file browser with root privileges. I thought that would allow me to do whatever I needed to do file-wise anywhere on the computer. Maybe so, but now it seems that it set up later problems for me, in that I later couldn't copy and paste files into some folders in my own home directory. I found it very frustrating. I remember having a permissions issue when I set up my Apache Web server and I was denied access to see Web pages through the browser. Very vexing.

---

### Post by ShowMeGrrl on 2010-07-16
OK, here's a new question about my switch from Windows to Ubuntu (Wild Dog).

I've been on Windows XP for quite a while; my husband is on an iMac. We get our Internet connections via ethernet cable through a Linksys cable router. The model number is BEFSR41 V.2.

I've used this router for several years, but it seems to work OK. We do have to re-boot from time to time and sometimes I wonder if our Internet broadband connection would be faster if we updated our router.

Is it desirable for me to update our router? 

Also, I installed Linksys software on my WindowsXP box that allows me to configure the router. Will I need to look for a router with Linux software to do the configuring? Which routers would those be?

---

### Post by isantop on 2010-07-16
I can't speak for any specific routers, but most routers have a "Web" configuration interface. For example, with mine, if I open a web browser and go to 192.168.0.1, it will take me to the router to configure it. Your number may be different, as mine is also our modem, but usually it is, by default, something like 192.168.X.1 or the like.

I doubt updating your router would make it faster, but it might close up security holes or add new features. It's always good practice to keep all your software up to date, and that is certainly no exception. However, if it is working fine now, and you don't really feel like taking the time to update, then you probably will be fine without the update.

---

### Post by ShowMeGrrl on 2010-07-16
> I can't speak for any specific routers, but most routers have a "Web" configuration interface. For example, with mine, if I open a web browser and go to 192.168.0.1, it will take me to the router to configure it. Your number may be different, as mine is also our modem, but usually it is, by default, something like 192.168.X.1 or the like.

Yes, now that you mention it, that's probably how my router works. It's possible I did not install any software. I just know that I configure it on my PC and assumed -- wrongly probably -- that I had installed some software to do that.

> I doubt updating your router would make it faster, but it might close up security holes or add new features. It's always good practice to keep all your software up to date, and that is certainly no exception. However, if it is working fine now, and you don't really feel like taking the time to update, then you probably will be fine without the update.

Then I'll probably put that off for a while. Enough on my plate for now!

---

### Post by CorruptMonkey on 2010-07-17
> **ShowMeGrrl said:**
> Yes, now that you mention it, that's probably how my router works. It's possible I did not install any software. I just know that I configure it on my PC and assumed -- wrongly probably -- that I had installed some software to do that.



Then I'll probably put that off for a while. Enough on my plate for now!

 I looked up the router specifications. I would agree with the previous commenter that upgrading your router wouldn't increase your speeds. With wireless routers, upgrading can easily lead to faster speeds. With your router, unless you have insanely fast internet connection or transfer gigabit files on the network regularly, a faster router (one that has a gigabit switch) would yield you no tangible speed boost.

---

### Post by jdb on 2010-07-17
> **ShowMeGrrl said:**
> I think that must have been my problem. I was using the sudo nautilus-no-desktop command to get the file browser with root privileges. I thought that would allow me to do whatever I needed to do file-wise anywhere on the computer. Maybe so, but now it seems that it set up later problems for me, in that I later couldn't copy and paste files into some folders in my own home directory. I found it very frustrating. I remember having a permissions issue when I set up my Apache Web server and I was denied access to see Web pages through the browser. Very vexing.

To verify your name and what directory you are in run:
```
12:45:11 ~ whoami
dad
12:45:20 ~ pwd
/home/dad

```
The following command will try to change the owner and group of all files
in the current directory and all subdirectories.
Substitute your name for dad.
```
12:45:45 ~ chown -R dad: .
chown: changing ownership of `./.gvfs': Function not implemented
chown: changing ownership of `./Desktop/.dog': Operation not permitted

```
It won't change the files that belong to root because it doesn't
have permissions but it will print an error message on each one it finds.
If you want to really change them run the following command:
```
12:53:07 ~ sudo chown -R dad: .
chown: cannot access `./.gvfs': Permission denied

```
Don't worry about the ./.gvfs directory, it's a strange animal.

jdb

---

