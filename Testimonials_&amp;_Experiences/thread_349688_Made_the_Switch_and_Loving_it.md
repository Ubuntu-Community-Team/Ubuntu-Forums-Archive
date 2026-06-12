---
title: "Made the Switch and Loving it"
date: 2007-01-30
forum: Testimonials &amp; Experiences
---

### Post by psyne on 2007-01-30
Hello all,

I just wanted to take a few moments say I switched to Ubuntu from Windows last night and I am loving it. As a long time Windows user I was concerned that the switch was going to much more difficult and daunting. In my professional life I develop Windows Applications and support windows based systems and heavily vested in the Microsoft product line carrying several certifications (MCSE, MCT, MCSA etc...) so the choice to switch was not a simple nor quick one. 

In the recent months I have seen the gap in services and support from Microsoft continue to wane. With new applications coming out on a fixed schedule and LTS options for legacy products continuing to drop to the wayside I grew gradually disatisfied with the curren offerings from Microsoft. With the release of Vista I was being told that I would see a wonderful change in the way I work and play but at a huge cost. Through research I found that many of the "features" unique to Vista were readily available in Linux. So I downloaded SLAX, Gentoo, Ubuntu, Knoppix and Whappix and tried to find the flavor that was right for me. As a system admin I wanted to make sure of security and realiablity; across the board this was not a problem, as user and and a newbie to Linux I wanted to make sure of usability and accessibility.

Immediately I was struck by how well fleshed out the live cd versions of these OS choices were. The only comparable system in the Microsoft domain is Windows PE and it fails to compare with the performance and reliabily of the live versions of Linux. After having tested the enviroment for general usability I felt comfortable narrowing the field down further. After much reading and consideration I decided on Ubuntu because of its user community and support. I was immediately able to find the resolutions to issues and concerns through the various support methods.

Finally I made the switch and took the plunge into the Linux world last night. It was completely awesome the way the installer worked (though it did crap out on me while configuring the APT) though that was easily fixed by rebooting and ensuring I had a connection to the internet. Within minutes of installing I was online configuring my system the way I always wanted. From layout choices to programs the variety of tools including the Synaptic Package manager, EasyUbuntu, and Automatix made everything real simple. 

After using the automated installers I tried my hand and using the cli and apt system to grab what I wanted. In minutes I was running VMWARE server, a version of IE using wine (for testing purposes only) and installed VLC player (I know I could of done it through Automatix but I wanted to try it for myself). The CLI was even more simple than the GUI!! Wheras in windows world the CLI is useful like a hammer is useful beating in a nail. The CLI in linux is a thing of beauty within 2 hours of study on linuxcommand and tuxfiles I felt comfortable enough to try my hand at some system customization and setting up a printer.

I could go on and on but let me close by saying that Linux and specifically Ubuntu has reawakened my passion for computers. Wheras with Microsoft I felt like I was using a tool with Ubuntu I feel like I am using exploring and defining my computer's role. The best part is I know that I have barely scratched the surface and I am exited to see where I will be a month from now. Twelve hours later and the only reason I have loaded Windows was to work on some software I am developing for work.

Some other really nice things I was able to do and figure out:

Tried my hand at Gimp and found it much more accessible than Photoshop
Tried my hand at Blender 
Had a lot of fun getting waxed at chess using Eboard
Setup Opera and figured out how to get Java and Flash working for it
Symbolic links are too cool for words
Got evolution working with my exchange server
Wrote my first cli script to report on used and free space on the drive
Scripted uploading and downloading of files from my website

---

### Post by jvc26 on 2007-01-30
Great to hear :) Welcome to the community. I made a similar 100% switch a few months back (having run a dual boot for a few months) and don't look back. Fortunately I had no ties to windows to pull me back in so the freedom comes at no cost :)
Il

---

### Post by muguwmp67 on 2007-01-30
I agree with you when you mention that ubuntu has brought the fun back into computing.  The first PC I worked with was in grade school on an Apple II.  Since that time, I saw DOS on the original IBM PC's, first-generation MAC's, Trash-80's, Commodores, and then...Windows 1.0.

Windows for workgroups came out while I was in college.  The www was just getting started then, and 'the internet' was something that few people outside of college students knew anything about.  Back then, computers were fun.

Then windows 95 came out.  After windows 95, it just wasn't as much fun anymore.  It made the computer easier to use, for the most part.  But maintaining the computer was a nightmare.   I don't think there is any good way to prevent a windows installation from bloating and slowing down after time.  I was reinstalling every 12-18 months.  This wasn't so bad in the days of DOS and windows 3.1 where programs all kept their configuration separate.  After windows 95, a reinstall of the OS required a reinstall of all of your software as well.  But its what I had to do to keep a responsive system.

Linux has brought some of the fun back into it.  Over the years I've gotten lazy, and I admit that a command line isn't as fun as it was, but I'm getting used to it.  Its even easier to get used to it, when I can actually use it to solve problems.  (I do think that we will need to be able to hide the command line from average users in order get more widespread acceptance though)  I'm curious again, and there is a world of software out there to experiment with.

> **psyne said:**
> 
Symbolic links are too cool for words


This statement confuses me though.  I'm still really new at this, so could someone please explain to me what the difference between a symbolic link and a windows shortcut is?  They seem awfully similar to me.

---

### Post by mostwanted on 2007-01-30
I love these posts that display new found enthusiasm for using their computer. Honestly, Linux should be accredited for *bringing the fun back into computing*, as the AmigaOS 4.0 slogan goes.

---

### Post by psyne on 2007-01-30
muguwmp67 When I said that Symbolic Links are too cool for words

I meant that they make life a lot easier. Instead of having to have multiple copies of a binary floating around the harddrive I can create a symbolic link (much like a shortcut in Windows except a shortuct in Windows would not let the program use it) that the program can use. Specifically when I installed Opera 9 on my Ubuntu install I could not get Flash to work. I was able to install flash for Firefox but not for Opera 9. So I looked in the plugin folder of Firefox and FlashNotFree folder and found the flash files. From there I made a symbolic link to my Opera plugins folder restarted and viola I was running flash. In Windows I really doubt such and elegant and simple solution would work. Hence why I said they were too cool for words.

I agree with you about Windows and bloat. When you install a fresh install of windows you are running great but by the time you put office on, antivirus on, installed all the hotfixes and service packs, and maybe a game or two well Windows would bloat up like some overfed wilderbeast. A year or two later and it was always "about that time" that time being to reinstall and start fresh and the cycle would repeat ad naseum.

---

### Post by muguwmp67 on 2007-01-30
Thanks for your explanation, I understand better now.  I think a windows shortcut actually corresponds more to a 'launcher', whereas a symbolic link behaves exactly like a copy of the file would.  Now I've got a new solution in search of  a problem!

---

### Post by indigoshift on 2007-01-30
> **psyne said:**
> Specifically when I installed Opera 9 on my Ubuntu install I could not get Flash to work. I was able to install flash for Firefox but not for Opera 9. So I looked in the plugin folder of Firefox and FlashNotFree folder and found the flash files. From there I made a symbolic link to my Opera plugins folder restarted and viola I was running flash.

I wouldn't mind hearing more information on how this is done (I haven't worked with symbolic links yet).

Oh, and welcome! :)

---

### Post by haligi on 2007-01-31
Just thought I'd join your conversation.  Am waiting for Ubuntu to download and found the topic here somewhat applies to me.  I looked into ubuntu because -- surprise, surprise, I'm in that every 2 year ritual of scrapping everything off my Windows XP computer and reinstalling.  System recovery was going well when, lo and behold, I get an error:  the system recovery CD #2 is scratched!

Well, am now in the process of downloading Ubuntu (93% done) and will see whether I can load it onto my home computer.  I'm assuming it would work without the full system recovery.  Right?  Right?  Or do I need a working, fully functional XP?

Will let you know how it goes.

---

### Post by muguwmp67 on 2007-01-31
Nope you don't need a rescue disk if you have a non-working system to start out with.

---

### Post by psyne on 2007-01-31
> **indigoshift said:**
> I wouldn't mind hearing more information on how this is done (I haven't worked with symbolic links yet).


Indigo this is what I did and it got Flash9 working in Opera 9 on ubuntu. 

When I would try to install it from the cli it would give me a message that flash 9 was not supported in Opera so the install would terminate. I did some reading and I found that two files where responsible for Flash in Firefox flashplayer.xpt and libflashplayer.so. So what I did was find those file and create a symbolic link between them and the opera plugin folder.

first I gave myself root (sorta)

```

sudo su

```

then I linked the files

```

ln -s /usr/lib/flashplugin-nonfree/flashplayer.xpt /usr/lib/opera/plugins/
ln -s /usr/lib/firefox/plugins/libflashplayer.so /usr/lib/opera/plugins

```

Finally I restarted opera and went to youtube to make sure it worked. Oh as a side note I also had to install Java for opera for youtube to work. I don't know if it will be same the for you but my java directory was

```

/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/

```

Basically all I had to do was tell opera to use that directory in order to get Java working, you get to the Java preferences under Tools, preferences, content. Check the box that says use java and then select the directory that the java files are located in. Hopefully this is helpful to someone out there and if I got the commands wrong then please let me know.

---

### Post by bitfoo on 2007-02-01
You do know symbolic links existed under Windows as well right (junctions)? I mean they did teach you that at MCSE school right? ;)

Anyways, glad to see a fellow IT professional coming into the Linux fold.  Now if we could just get a Visio alternative to make our fancy network diagrams in Ubuntu. :D  Hope your newfound experience finds you well. :KS

---

### Post by rocknrolf77 on 2007-02-01
A nice tool to have is either yakuake or tilda. Dropdown terminals. The fastest way to get work done. With yakuake I just push F12 and the terminal is there, ready for your command. :guitar:

---

### Post by muguwmp67 on 2007-02-01
Its not as flashy, but you can also assign a shortcut key to the generic terminal app.  Go to system->Preferences->Keyboard Shortcuts.

I like yakuake for the most part, but find it a little irritating sometimes when it won't let other windows rise in front of it, especially when I do a sudo gedit.  Haven't tried tilde.

---

### Post by indigoshift on 2007-02-01
Thanks for the walkthrough!  I'll give this a try tonight.

---

### Post by quirt3 on 2007-02-01
Welcome!

I know the feeling of switching and it's growing pains. My family has always used Linux, and I used to prefer windows to their disgust. When edgy came out I founs it was more natural to me. I have a few suggestions to make the switch easier:

EasyUbuntu(or Automatix, as they both install the essentials and tweaks)
Listen Music Player (As functional as iTunes and more!)
WINE (for those windows apps you can't live without)
Abiword( easy,simple word editor, MUCH lighter on the CPU and less hard to learn than openoffice)

---

### Post by psyne on 2007-02-01
Bitfoo I was aware that symbolic links existed in Windows but the functionality and usefulness of them are far less useful than the same in Linux. With the registry the accessibility of the links are nare useless, symbolic links, on an NTFS 5.0 filesystem that is. Moreover this functionality isn't very well-documented or accessible, So my excitment was for the fact that this tool is fully featured well document and usable on the linux platform.

The best example of these links in the microsoft world are in the Computer Management MMC snap-in under Disk Management. You can map a volume to a directory within an existing file structure rather than giving it its own volume drive letter this creates a junction from the directory to the root of that volume. This is very usable for extended a drive which is low on space. However the functionality of the link is significantly limited in scope to those on the linux platform. I could not have made the fix I made in opera using symbolic or junction links on a windows platform.

Also, support for junctions in Explorer is sketchy at best if I delete it I can expect some weird errors and maybe BSD or two in linux it is no more trouble than deleting anything else either from NANO or the terminal. But thanks for polling my knowledge I took some good notes at MCSE school :)

---

### Post by psyne on 2007-02-01
Quirt: Thanks for the tips, I tried Easy Ubuntu and Automatix and gave them up for the Terminal and apt-get which I think is awesome!! As for abiword it was no problem to use open office but I will definately try it out in lieu of gedit which I have been using as my notepad replacement. As for wine I tried it out and installed it to run ie (have to for testing purposes and a product we support from a vendor) but gave it up for Crossover Office which seemed to offer more control and flexibility plus the forums are really helpful

---

### Post by penndragonn on 2007-02-20
> **psyne said:**
> muguwmp67 When I said that Symbolic Links are too cool for words

I meant that they make life a lot easier. Instead of having to have multiple copies of a binary floating around the harddrive I can create a symbolic link (much like a shortcut in Windows except a shortuct in Windows would not let the program use it) that the program can use. Specifically when I installed Opera 9 on my Ubuntu install I could not get Flash to work. I was able to install flash for Firefox but not for Opera 9. So I looked in the plugin folder of Firefox and FlashNotFree folder and found the flash files. From there I made a symbolic link to my Opera plugins folder restarted and viola I was running flash. In Windows I really doubt such and elegant and simple solution would work. Hence why I said they were too cool for words.

I agree with you about Windows and bloat. When you install a fresh install of windows you are running great but by the time you put office on, antivirus on, installed all the hotfixes and service packs, and maybe a game or two well Windows would bloat up like some overfed wilderbeast. A year or two later and it was always "about that time" that time being to reinstall and start fresh and the cycle would repeat ad naseum.



PSYNE,

You just switched to Linux, and in one day you seem quite adept at it. I switched also, and am nowhere near where your at? How is this possible...Linux is so Alien from Windows, and your running WINE and other apps? I can't even get it installed correctly...Please tell me how you got so proficient in Linux in one day. I'm quite sure many of us Ultra New Users of Linux would like to know your secret!!!

Ron

---

### Post by anaconda on 2007-02-21
> Linux and specifically Ubuntu has reawakened my passion for computers. Wheras with Microsoft I felt like I was using a tool..

exactly what I feel... ubuntu brought the fun back to computing

---

