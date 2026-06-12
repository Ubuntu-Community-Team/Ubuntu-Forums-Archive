---
title: "Suggest Software to be written"
date: 2006-03-24
forum: The Cafe
---

### Post by clash on 2006-03-24
As title says. 

Suggest a small application you think Linux is missing, not something big like photoshop etc but just a generally useful piece of software that windows has and linux hasn't.

---

### Post by aysiu on 2006-03-24
[QUOTE=clash]As title says. 

Suggest a small application you think Linux is missing, not something big like photoshop etc but just a generally useful piece of software that windows has and linux hasn't.[/QUOTE] Are you offering to write one?

I think what it's mainly missing are graphical user interfaces (GUIs) for a couple common tasks:

- Mounting Windows partitions with the proper permissions (read-only for NTFS, read/write for FAT32). Currently, users have to do some manual editing of the /etc/fstab file

- Changing the timeout and default OS in the Grub menu. Currently, they have to manually edit the /boot/grub/menu.lst file.

---

### Post by Mustard on 2006-03-24
I would like to see a graphical interface that does a variety of screen capture  tasks.  There is a command line screen capture utility 'scrot', amongst others.  I'd like to see it/them GUIfied. :)

---

### Post by Joshuwa on 2006-03-24
[QUOTE=aysiu]
- Changing the timeout and default OS in the Grub menu. Currently, they have to manually edit the /boot/grub/menu.lst file.[/QUOTE]

I second this, big time.

As a new user myself, I'm finding editting the menu manually is not difficult, but it is a little 'scary' lol.

Something like this would be a VERY useful tool, and something I could see being part of the Ubuntu package in the future.

---

### Post by maruchan on 2006-03-24
It's simple, but I'd like to be able to adjust the global volume setting by holding down Ctrl+Shift and moving the mousewheel up or down. 

I found this in [VolumeTouch](http://www.hi.is/~antoni/volumetouch/), a Windows app, and it really works well. 

I've found close equivalents in GNOME and KDE (Ctrl+Shift+Arrow Keys or hovering over the speaker icon and scroll-wheeling), but somehow this one is lots better for me.

Petty, I know! 8)

---

### Post by aysiu on 2006-03-24
[QUOTE=Mustard]I would like to see a graphical interface that does a variety of screen capture  tasks.  There is a command line screen capture utility 'scrot', amongst others.  I'd like to see it/them GUIfied. :)[/QUOTE] Can you name some of these tasks that scrot can do that KSnapshot can't?

---

### Post by briancurtin on 2006-03-24
there are plenty of "GUIfied" screen capture applications already

---

### Post by christhemonkey on 2006-03-24
[QUOTE=aysiu]- Mounting Windows partitions with the proper permissions (read-only for NTFS, read/write for FAT32). Currently, users have to do some manual editing of the /etc/fstab file[/QUOTE]
I can mount RO my NTFS partition from system tools >> admin >> disks in gnome that is.
Though that is only for 1 time use though, (ie it does not stay mounted on reboot)

---

### Post by aysiu on 2006-03-24
[QUOTE=christhemonkey]I can mount RO my NTFS partition from system tools >> admin >> disks in gnome that is.
Though that is only for 1 time use though, (ie it does not stay mounted on reboot)[/QUOTE] The tasks outlined in these two links are very common requests:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

Frankly, I'm surprised that Knoppix can do this but Ubuntu hasn't implemented it.

---

### Post by Mustard on 2006-03-24
[QUOTE=aysiu]Can you name some of these tasks that scrot can do that KSnapshot can't?[/QUOTE]

Something gnome specific I probably should have added.  I'd like to avoid installing kde elements in gnome.

[QUOTE=briancurtin]there are plenty of "GUIfied" screen capture applications already[/QUOTE]

I don't find any dedicated gui screen capture utilites for gnome in my searches. I'd like something with comparable features to say Screen Pilot ([http://www.colorpilot.com/screenshot.html](http://www.colorpilot.com/screenshot.html))

---

### Post by Mustard on 2006-03-24
[QUOTE=aysiu]The tasks outlined in these two links are very common requests:

[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

Frankly, I'm surprised that Knoppix can do this but Ubuntu hasn't implemented it.[/QUOTE]

I find that quite surprising myself too.  I've been playing with Knoppix, Kanotix and even Puppy linux, and the all have very easy methods of mounting different drives.  I can't see why its not a part of ubuntu either.

---

### Post by aysiu on 2006-03-24
[QUOTE=Mustard]Something gnome specific I probably should have added.  I'd like to avoid installing kde elements in gnome.[/QUOTE] In Gnome, I created a launcher for the command ```
gnome-screenshot --delay 5
``` But, you're right, there should be a Gtk utility for that.

---

### Post by red_Marvin on 2006-03-24
[QUOTE=aysiu]- Changing the timeout and default OS in the Grub menu. Currently, they have to manually edit the /boot/grub/menu.lst file.[/QUOTE]

I'm a bored and tired geek, see attachment. Now I'm going to bed...

---

### Post by Mustard on 2006-03-24
[QUOTE=red_Marvin]I'm a bored and tired geek, see attachment. Now I'm going to bed...[/QUOTE]

It looks nice enough. :)  I haven't run it with superuser privileges yet, but I fired it up and saw the interface, and I've been perusing the code.

---

### Post by aysiu on 2006-03-24
[QUOTE=red_Marvin]I'm a bored and tired geek, see attachment. Now I'm going to bed...[/QUOTE] Awesome! It's such a simple interface, but it works! I just tried it on my test partition. Thanks for writing that.

---

### Post by IYY on 2006-03-24
[QUOTE=aysiu]Are you offering to write one?

I think what it's mainly missing are graphical user interfaces (GUIs) for a couple common tasks:

- Mounting Windows partitions with the proper permissions (read-only for NTFS, read/write for FAT32). Currently, users have to do some manual editing of the /etc/fstab file

- Changing the timeout and default OS in the Grub menu. Currently, they have to manually edit the /boot/grub/menu.lst file.[/QUOTE]

I'm going to write a script that'll make mounting NTFS partitions easy. It's not going to be graphical, but will be very simple.

---

### Post by Mustard on 2006-03-24
[QUOTE=IYY]I'm going to write a script that'll make mounting NTFS partitions easy. It's not going to be graphical, but will be very simple.[/QUOTE]

I'd just mention that there is a script for this on the wiki already...

[https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions)

---

### Post by IYY on 2006-03-24
This is not bad. The one I had in mind would allow a bit more control, but I suppose it's good enough.

---

### Post by BluGold on 2006-05-05
[QUOTE=clash]As title says. 

Suggest a small application you think Linux is missing, not something big like photoshop etc but just a generally useful piece of software that windows has and linux hasn't.[/QUOTE]

From a nubee that doesn't know JS (Thats Jacks sh..). Having said that........

Reading these forums I find that many words, acros, abreviatons, terms etc. are speckled thruout. This makes understanding much of it very difficult. ](*,) Currently it's copy and paste to a search engine for the definitions. So a ten minute read takes quite longer and many times still not understanding what is said. :mad:  

What I'm suggesting may be around somewhere (but just don't know where to start looking) is a means to have easy access to the defines of those terms.

Actuallly the concept is available and driven by money, as in advertisments, via words that are highlited and a mouseover pops up a box that includes the ad.

So how about the same thing in these forums only with a quick def and a link to a more difinitive one?

Now you can tell me this is the wrong fourm and go 'here'. :) 

I didn't start this reply with "I know this is the wrong forum but"  because there breeds another suggestion. One that would allow [via a check box?] a scan of the reply for key words. Then offer suggested links to see if it's been suggested afore.  Yea I know, 'just use the search', 'just RTFM', 'Just keep at it', 'just start 'here'. [sigh]. 

Now, if the first suggestions is workable, would the second one be needed?


JAT [Just A Thought] (OK two),          ...BluGold

---

### Post by aysiu on 2006-05-05
[QUOTE=Mustard]I'd just mention that there is a script for this on the wiki already...

[https://wiki.ubuntu.com/AutomaticallyMountPartitions](https://wiki.ubuntu.com/AutomaticallyMountPartitions)[/QUOTE] I don't know if that's sufficient. Look at the assumptions it makes: > Script assumptions

    *

      /media/ is an acceptable location for the partitions to be mounted
    *

      there are no entries in your /etc/fstab for windows drives already
    *

      the windows drives are currently not mounted. I don't think, first of all, that /media/ is an acceptable location. It's worked fine for me in the past, but I've seen at least four instances on these forums of it screwing with permissions on other people's mounted partitions. A static mount point tends to be more reliable.

Breezy defaults to setting up mount points for *every* partition. If you have an NTFS drive at /dev/hda1, it'll automatically add this to your /etc/fstab ```
/dev/hda1 /media/hda1 ntfs defaults 0 0
```

And, if Breezy already adds those by default, it will also have those partitions mounted at boot time.

What we need is a script that will unmount all FAT32 and NTFS drives, create static mount points for them and delete the already-existing /etc/fstab entries for them and put new ones in. Then, remount the drives.

[quote=BluGold]Reading these forums I find that many words, acros, abreviatons, terms etc. are speckled thruout. This makes understanding much of it very difficult. Currently it's copy and paste to a search engine for the definitions. So a ten minute read takes quite longer and many times still not understanding what is said.[/quote] If someone uses an abbreviation you don't understand, just say, "What's _________?" It's a lot faster than looking it up, and it lets the person know she's being cryptic.

---

### Post by unbuntu on 2006-05-05
[QUOTE=aysiu]Are you offering to write one?

I think what it's mainly missing are graphical user interfaces (GUIs) for a couple common tasks:

- Mounting Windows partitions with the proper permissions (read-only for NTFS, read/write for FAT32). Currently, users have to do some manual editing of the /etc/fstab file

- Changing the timeout and default OS in the Grub menu. Currently, they have to manually edit the /boot/grub/menu.lst file.[/QUOTE]

These ones don't sound complicated at all as far as programming is concerned.  However, I myself am not an expert on fstab, although I can mount NTFS and set up permissions, I'm not familiar with the other options that are available to fstab.  It won't take a decent programmer much time to implement what you've proposed, however, I think part of the "Linux fun" is modifying configuration files.

---

### Post by jc87 on 2006-05-05
What about a easy to use GTK GUI for Grub that would allow :

- Auto-add new partitions to the menu.lst cfg file.

- Restore the MBR (would rock at the live-cd).

- Create a Floppy/cd/dvd grub bootable drive (great way to gain acess to Ubuntu if you install Windows for duall-boot after it). 

- Change the image at the grub menu background 

- etc....

---

### Post by aysiu on 2006-05-05
[QUOTE=jc87]What about a easy to use GTK GUI for Grub that would allow :

- Auto-add new partitions to the menu.lst cfg file.

- Restore the MBR (would rock at the live-cd).

- Create a Floppy/cd/dvd grub bootable drive (great way to gain acess to Ubuntu if you install Windows for duall-boot after it). 

- Change the image at the grub menu background 

- etc....[/QUOTE] Mepis has all this already. Is Warren's code open source?

---

### Post by helpme on 2006-05-05
Something that's really missing, at least from Ubuntu, is a nice frontend for pppoeconf and an applet that let's you control pon and poff, so that users are able to start their adsl connection without having to use the command line.

---

### Post by mips on 2006-05-05
[QUOTE=helpme]Something that's really missing, at least from Ubuntu, is a nice frontend for pppoeconf and an applet that let's you control pon and poff, so that users are able to start their adsl connection without having to use the command line.[/QUOTE]

Something like gpppon maybe ?

---

### Post by helpme on 2006-05-05
[QUOTE=mips]Something like gpppon maybe ?[/QUOTE]
Hey, thanks, didn't know about it.
But a real applet written in gtk2 would still be better. ;-D

---

### Post by henriquemaia on 2006-05-21
[quote=jc87]What about a easy to use GTK GUI for Grub that would allow :

- Auto-add new partitions to the menu.lst cfg file.

- Restore the MBR (would rock at the live-cd).

- Create a Floppy/cd/dvd grub bootable drive (great way to gain acess to Ubuntu if you install Windows for duall-boot after it). 

- Change the image at the grub menu background 

- etc....[/quote]

This would be great, specially the restore the mbr, really useful.

---

### Post by thegnark on 2006-05-21
gui application to join ubuntu to an active directory domain. beyond configuration, it should recognize what packages need to be installed (pam, samba, etc.) and be able to install them

---

### Post by hezral on 2006-05-21
how about this one? this guy already developed it half way but stalled it. the source is up for grab tho. its a dashboard widget like apple, even uses the widgets from apple.. 

[http://www.kryogenix.org/days/2006/01/22/jackfield-apples-dashboard-for-the-linux-gnome-desktop](http://www.kryogenix.org/days/2006/01/22/jackfield-apples-dashboard-for-the-linux-gnome-desktop)

---

### Post by flaimo on 2006-05-22
what i miss is a little programm to create custum keyboard layouts like “[Microsoft Keyboard Layout Creator]("http://www.microsoft.com/downloads/details.aspx?FamilyID=fb7b3dcd-d4c1-4943-9c74-d8df57ef19d7&DisplayLang=en")” for windows, so i can easily bind utf-8 characters to certain keys. i know that you can edit the keyboard files directly, but doing it the gui way would be more convenient.

---

### Post by 3rdalbum on 2006-05-22
[QUOTE=maruchan]It's simple, but I'd like to be able to adjust the global volume setting by holding down Ctrl+Shift and moving the mousewheel up or down. 

I found this in [VolumeTouch](http://www.hi.is/~antoni/volumetouch/), a Windows app, and it really works well. 

I've found close equivalents in GNOME and KDE (Ctrl+Shift+Arrow Keys or hovering over the speaker icon and scroll-wheeling), but somehow this one is lots better for me.

Petty, I know! 8)[/QUOTE]

If you have a keyboard with Volume buttons on it, they're likely to work with Gnome without extra configuration. But I agree, that thing sounds really cool.

---

### Post by Cheizzz on 2006-06-05
What I would really like to see is a program like Teach2000, that could work with teach2000's .t2k files.Since it is windows only there is no native linux app that can do this, that I know of, and running teach2000 in Wine isn't practical for me. 

I would need such program because we can grab the complete .t2k files off our school site for easy learning.

I think it wouldn't be too hard to write such program, but I lack the skills to do it myself. Anyone intrested? (the program is free, but closed source)

The main part of the site is in dutch, a small part in english.
Dutch part: [http://www.teach2000.nl]("http://www.teach2000.nl")
english part:[http://www.teach2000.nl/international.php]("http://www.teach2000.nl/international.php")

---

### Post by blackjack6.21.91 on 2006-06-15
I would like to suggest some sort of terminal applet, that could dock in a panel like the deskbar - only when a command is entered, it would let you know what the terminal spits back out.

---

### Post by M7S on 2006-06-15
[QUOTE=blackjack6.21.91]I would like to suggest some sort of terminal applet, that could dock in a panel like the deskbar - only when a command is entered, it would let you what the terminal spits back out.[/QUOTE]
It might not be exactly what you're looking for, but have you tried tilda? You'll find it in universal repositories.

---

### Post by siimo on 2006-06-15
I would like to contribute as well if this project is gonna be open source as im a noob programmer and would like to see if i can help or if im totally clueless :confused:

Update: I have taken the initiative and started working on a more detailed graphical grub configurator than the one posted on this thread - wish me luck :P

---

### Post by blackjack6.21.91 on 2006-06-15
Thanks for the find.  It's pretty nice, but it has no visible scroll button. It would be pretty cool if something like this was added into the deskbar so that when you ran a command you could see the output.  What would be even cooler is if it could hide and reveal the output..  Maybe even with tabs...

Ok i'm drooling..  I should stop.  Jk, but if someone did something like this I would jump on it.

blackjack

---

### Post by foof on 2006-06-15
Please make a better GUI config for the mouse, one where you can set up the functions you want for all buttons.

---

### Post by WorLord on 2006-06-15
- Samba server configuration GUI that actually works.  The built-in Ubuntu GUI works, sort of, under very specific circumstances... but every Samba-serving-on-Ubuntu howto I've read starts with the Ubuntu GUI and ends with detailed modifications to samba.conf.  A functional GUI wouldn't need the .conf file editing.  Maybe something that allows share-based permissions by default.

- As mentioned before: an Active Directory Integration GUI wouldn't be all that bad.

- Grub configuration GUI

- And for the love of $diety, will SOMEONE add SAX or SAX2 to Ubuntu?  I've yet to hear of a good reason why it (a graphical Xorg configurator / resolution setter) isn't there.  The current tool doesn't even begin to cut it.

---

### Post by DoctorMO on 2006-06-15
Something that I notice is that there are a ton of programs already written to do almost any job. problem is we seem to be very bad at searching for them or building theminto ubuntu in a way that makes it easy for new users to know they exist.

don't forget windows users will expect all config pannels to be installed by default and find ommisions to mean that those features don't exist at all.

I would like to see better libs for editing the various config files, it's one thing to write a quick script that adds things to samba.conf quite another to make [http://search.cpan.org/~sscotto/File-Samba-0.03/lib/File/Samba.pm](http://search.cpan.org/~sscotto/File-Samba-0.03/lib/File/Samba.pm) and I think if developers are thinking of making gui apps they should consider searching for and using such libs.

---

### Post by Stone123 on 2006-06-18
Implement sound for every open window so that every window has its own sound volume. Create volume applet where upon opening a new window a new volume bar with window(program) icon is added?

---

### Post by siimo on 2006-06-18
[QUOTE=Stone123]Implement sound for every open window so that every window has its own sound volume. Create volume applet where upon opening a new window a new volume bar with window(program) icon is added?[/QUOTE]

why would you need this?  and where would you draw the line? one for every single process or just ones that show up in gnome taskbar?  what about programs that dont show up in the taskbar?

---

### Post by Stone123 on 2006-06-18
[QUOTE=siimo]why would you need this?  and where would you draw the line? one for every single process or just ones that show up in gnome taskbar?  what about programs that dont show up in the taskbar?[/QUOTE]

As i sad if i have amarok on full volume , i dont wish system sound or gaim sounds or whatever other program under at the same volume. I would draw a line at gtk windows.
And i didnt say process , maby you dont know what process is , anyway i sad window.

---

### Post by Wolki on 2006-06-18
[QUOTE=Stone123]Implement sound for every open window so that every window has its own sound volume. Create volume applet where upon opening a new window a new volume bar with window(program) icon is added?[/QUOTE]

You mean like Polypaudio: [http://0pointer.de/lennart/projects/polypaudio/](http://0pointer.de/lennart/projects/polypaudio/) and the Polypaudio Volume Control: [http://gnomefiles.org/app.php?soft_id=1404](http://gnomefiles.org/app.php?soft_id=1404) ?

Yeah, I'm looking forward to using that, too :)

---

### Post by B0rsuk on 2006-06-18
[QUOTE=B0rsuk]

If you feel like innovating a bit, feel free to grab my idea:
aa-lib based FPS game.
[http://aa-project.sourceforge.net/gallery/alfons.jpg](http://aa-project.sourceforge.net/gallery/alfons.jpg)
[http://aa-project.sourceforge.net/gallery/holecek.jpg](http://aa-project.sourceforge.net/gallery/holecek.jpg)

Why ? Because it would be something fresh. Has it been done befoe ? Yes, there's aaquake and aaquake2. One person runs aalib-based xserver. There's console-based image viewer called aview (that's how ubuntu repositories call it, to run type asciiview imagename). Mplayer output codec is ready to use, too. Software for internet cam (which is said to achieve 25 frames per second with just 50k MODEM !!).
But there's something else. If done properly, the fps game would be immune to cheats by definition.. The problem with cheating online comes from the fact that multiplayer FPS games give clients more information than they will need, because
1) it makes lags harder to notice, and game smoother
2) saves server's CPU extra calculations.
Even aaquake is vulnerable to online cheating, because players are sent data in positions form; I mean stuff like "there's another player at 13, 53, 124, a rocket at X Y Z flying in X Y Z direction" and so on. As I understand, clients render scenes basing on similar data.
But it doesn't have to be this way ! There's already software for using internet cam with connection as poor as 50k modem.It is possible to send players only streaming movie of what they see, and they would send vectors/directions in return. Players are sent only what they can see - no wallhack possible.
I imagine that it would be much, much harder to teach a program to recognize player silhouettes from images rather than from vectors/hacking opengl libraries etc. And silhouettes are even harder for programs to recognize from fractal-based ascii-art !! No aimbot possible.
Another advantage of this solution would be that client applications could have quite small size, and they wouldn't have to download anything to play a modified server. Only server would have to keep data files for mods. Jump in and play !
Aside from that, aalib is plain cool.
[/QUOTE]

That's what I said in another topic.

---

### Post by beowulf62381 on 2006-06-19
I came from mac OS X to ubuntu and the thing I have found most lacking is GUI to video transcoding tools.

the mac users have made guis for mplayer/mencoder and ffmeg and others that make dvd>ipod or xvid or any thing els a breez my favrite of these tools is handbrake which has been ported to linux but the develper has discontenued the linux gui for it. some of the linux user base is alredy working on bringing the gui for linux back it is still in a very early stage.

maybe it is what you looking for maybe not

[http://handbrake.m0k.org/forum/viewtopic.php?t=973&highlight=gui]("http://handbrake.m0k.org/forum/viewtopic.php?t=973&highlight=gui")

---

### Post by vialick on 2006-06-19
Well when I have time and tallent (I have lots of time now, I'm just lacking in tallent) I've got my eye set to create a program that resembles OSX's [Automator](http://www.apple.com/macosx/features/automator/). Hopefully being more than just a graphical way of creating shell scripts (though that in itself would be quite usefull)

Even thought up the mascot...

---

### Post by piratepenguin on 2006-07-05
[QUOTE=vialick]Well when I have time and tallent (I have lots of time now, I'm just lacking in tallent) I've got my eye set to create a program that resembles OSX's [Automator](http://www.apple.com/macosx/features/automator/). Hopefully being more than just a graphical way of creating shell scripts (though that in itself would be quite usefull)

Even thought up the mascot...[/QUOTE]there's one in the works for KDE: [http://vophercel.homelinux.org/~tkadauke/workflow.txt](http://vophercel.homelinux.org/~tkadauke/workflow.txt)
[http://vophercel.homelinux.org/~tkadauke/shot08.png](http://vophercel.homelinux.org/~tkadauke/shot08.png)

An application that I think is badly-needed is something for configuring Xorg - what driver, monitor, extensions to use etc etc. Maybe such an app exists, anyone know of one?

(no time to read the whole thread, so maybe this has already been suggested)

---

### Post by FISHERMAN on 2006-07-05
A GUI for Mencoder would be a great thing.

---

### Post by DoctorMO on 2006-07-05
Sorta something like KMencoder or GMencoder?

---

### Post by FISHERMAN on 2006-07-05
[QUOTE=DoctorMO]Sorta something like KMencoder or GMencoder?[/QUOTE]
Yeah, but those 2 applications are to buggy for end-users, if they will ever be finished.
GMencoder's website latest news is from 2003.

---

### Post by Garyu on 2006-07-29
I don't know if this already exists... but...

1) Daily tips app. I started doing one of these but my time has been totally insufficient. I have both a script using zenity and the beginning of a real app, but nothing completely ready. As a new user it is always nice to be told about things like Automatix, where to find new themes, how to edit fstab, samba for networking and so on.

2) Some app to search for installed software not in menus, and then give the option to include it in the menu or leave it out. A lot of games (i.e. jumpnbump) as well as other software is installed without a menu item. As a new user it might seem difficult to make your own starter for the menu, since you often times not even know where this program you installed is located in the file system. So finding software automatically and then making menu-items automatically would be great (important to have the option to not install in the menu to avoid clutter).

3) A theme designer and chooser. The current theme chooser makes me first choose icons, then window frames, then background image... and so on. I would like to have a program which installs and changes themes for everything at once with one click. (i.e. "Black" theme, click on it once and icons, window-borders, background, colours, and so on changes instantly, then OK to accept changes). Also important to include the possibility to make your own theme and save it to a single file that can easily be shared with other. This way lots of new and nice themes will pop up on the user scene. The more the merrier, and more probable that true artists step up to the challenge.

4) Accounting. Gnucash is only for individuals or really small companies. SQL-ledger is not adapted to swedish circumstances. Lazy8 still has a lot of things unimplemented. A nice accounting software with plugins for different countries and their taxation issues would be a great thing. I haven't even found one to buy.

5) Invoicing. Is there one? The only thing I have found is a suggestion how to use OpenOffice.org for invoicing, which isn't very professional. If possible, tied to the accounting software.

6) Sound card tool. It took a lot of effort to get 5.1 surround sound for me in Breezy. Fortunately it was still working when I upgraded to Dapper. It will be interesting to see what happens when I do a fresh install again. In windows I have an app that tells me what kind of speakers are connected and to which jack they are connected. It also changes settings if I plug in a microphone or change speakers, and remember mixer settings for different speakers. This shouldn't be too hard to implement in linux? That would also give a hint about how much is working and where the error lies.

7) A GUI for lspci, lsusb and maybe dmesg to aid in installation and searching for errors. Something that would make it easier for newbs.

8) As said in this thread before, a GUI for fstab. How difficult can it be, really? To begin with, you don't even have to use anything to tell you what partitions are available, just a GUI for editing hda1, etc3, defaults, and so on in fstab and then saving it.

---

### Post by Johnsie on 2006-07-29
A windows executable that installs Ubuntu from within Windows, doing all the partitioning etc.Making it easy to install Ubuntu without ever having to burn a cd.

When you reboot, hey-presto you have a duel boot system!

---

### Post by OffHand on 2006-07-29
I would like to see a nice app to control my fan speed.

---

### Post by Corbelius on 2006-07-29
An easy application like SoundConverter - [http://soundconverter.berlios.de/](http://soundconverter.berlios.de/) - based on gstreamer 0.10 framework, but that convert video files instead of audio files.

---

### Post by sethmahoney on 2006-07-29
> **thegnark said:**
> gui application to join ubuntu to an active directory domain. beyond configuration, it should recognize what packages need to be installed (pam, samba, etc.) and be able to install them

Agreed, 100%.

---

### Post by sethmahoney on 2006-07-29
> **foof said:**
> Please make a better GUI config for the mouse, one where you can set up the functions you want for all buttons.

Agreed again.  This and network configuration are two of the most annoying parts of setting up a new ubuntu box.

---

### Post by sanderella on 2006-08-06
I like to play Scrabble at the Internet Scrabble Club, [www.isc.ro](www.isc.ro).
They have a Scrabble program download for Linux, but I can't configure it for Ubuntu. Would anyone be interested/able to do this?:)

---

### Post by Boomy on 2006-08-06
An app that will install software from source. Something that will automatically confiure, make, and make install. Something that is smart enough to download and install any dependencies and is smart enough to fix the problem when you get some error like "couldn't find QT3", etc. It would be great for newbies. I've tried quite a few times to install from source and not once could I get it to work without some whack error. Also it could install other types, like .bin automatically without having to open the terminal and type things like "chmod" and all that stuff guys like me are clueless about. Yeah, some utility that will just install anything and just "make it work" would be awesome imo.

---

### Post by pneaveill on 2006-08-06
> **DoctorMO said:**
> Something that I notice is that there are a ton of programs already written to do almost any job. problem is we seem to be very bad at searching for them or building theminto ubuntu in a way that makes it easy for new users to know they exist.

don't forget windows users will expect all config pannels to be installed by default and find ommisions to mean that those features don't exist at all.

I would like to see better libs for editing the various config files, it's one thing to write a quick script that adds things to samba.conf quite another to make [http://search.cpan.org/~sscotto/File-Samba-0.03/lib/File/Samba.pm](http://search.cpan.org/~sscotto/File-Samba-0.03/lib/File/Samba.pm) and I think if developers are thinking of making gui apps they should consider searching for and using such libs.
I agree with the many people saying there are many apps out there in linux-ville. I also agree that for a former windows person switching to Ubuntu, there must be ways of helping the newbie find those programs and help installing/setting them up.

To be honest, if Ubuntu (or any linux for that matter) is going to compete with Redmond, there must be easier ways of installing stuff. As I am not a programmer, I am unsure of what I am asking for, so please be patient with me. THere are many people out there that have limited programming skills (and/or fears of programming) and the thought of compiling a kernel sends them into previous life stage developments. Thus, the apps need to be more professional and install more easily.

Thanks for the opportunity to share.

YAP (Yet another Paul) :)

---

### Post by Terracotta on 2006-08-06
> **Mustard said:**
> I would like to see a graphical interface that does a variety of screen capture  tasks.  There is a command line screen capture utility 'scrot', amongst others.  I'd like to see it/them GUIfied. :)

Ksnapshot will suit your needs :D

---

### Post by aysiu on 2006-08-06
> **pneaveill said:**
> THere are many people out there that have limited programming skills (and/or fears of programming) and the thought of compiling a kernel sends them into previous life stage developments. Thus, the apps need to be more professional and install more easily. I'm not a programmer, and I have never had to compile a kernel... never wanted to either.

Read this:
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by bobbybobington on 2006-08-06
a program that can resolve dependancy problems when you download a program from anywhere other than synaptic, maybe use automatically use synaptic to look them up?

more gui front ends, is always good.

more games

a nice multimedia program like front row or media center. digging around the linux filesystem or organizing media in the first place can be a pain.

---

### Post by TravisNewman on 2006-08-06
Compiling a kernel requires no programming skills, just knowledge about your system. I've noticed some significant speed increases with recompiled kernels for my specific machine, especially in start-up times. I'd like to see a graphical do-it-for-you-after-answering-questions kernel compiler/installer. Do you have intel/amd? Do you have 3com network hardware? etc, etc. The downside is that if you take out too much you'll have to recompile whenever you replace hardware, however, in most cases computers are generally the same for a long time.

---

### Post by red_Marvin on 2006-08-06
> **pneaveill said:**
> (...)To be honest, if Ubuntu (or any linux for that matter) is going to compete with Redmond, there must be easier ways of installing stuff. As I am not a programmer, I am unsure of what I am asking for, so please be patient with me.(...)

Personally I think installing in ubuntu is easier than windows, just
type *sudo apt-get install programname* or use synaptic to install a program, instead of having a wizard asking me **where** I want the program installed. To me the ubuntu way that is just a *different* way to do it which may take some time to adapt to but in the end isn't any harder than Window's way.

If you rather meant the many kinds of formats (deb, rpm, source etc) the programs get delivered in, you've got a point. Still, many programs are available as debs, and for the others you can come here for help. :)

---

### Post by opticyclic on 2006-08-06
I haven't read the whole thread, but since people want certain tasks 'GUI-ified' why not copy and paste the commands into a Kommander script?

[http://ubuntuforums.org/showthread.php?t=168391](http://ubuntuforums.org/showthread.php?t=168391)

Kommander is a really easy to make a GUI (drag and drop) and you can paste BASH commands into it.

---

### Post by patrick295767 on 2006-08-06
> **aysiu said:**
> Are you offering to write one?

I think what it's mainly missing are graphical user interfaces (GUIs) for a couple common tasks:

- Mounting Windows partitions with the proper permissions (read-only for NTFS, read/write for FAT32). Currently, users have to do some manual editing of the /etc/fstab file

- Changing the timeout and default OS in the Grub menu. Currently, they have to manually edit the /boot/grub/menu.lst file.

([B]If we go into GUIs apps wihtout any console possibilities, I would fear that it's being very dangerous for linux itsself. 
  
Admins love to ssh one distant machine and fix it with only the friendly old keyboard.)[/B]
 
Just a remark

Cheers to you aysiu !

---

### Post by Polygon on 2006-08-06
those posted in the first post are just common tasks that many many people have to deal with at least one time or another. just making simple graphical apps to manage these repetitive tasks wouldent be a danger to the console at all. Its still there, you can do it manually if you like.

---

### Post by 3rdalbum on 2006-08-06
GUI frontends, but keep the command-line-and-config-files method for the users who want it.

I'm working on a program myself, actually, for mounting partitions and transferring bookmarks and music libraries from Windows to Ubuntu.

I would like an easy-to-use GUI designer, or an XML language I can use to make a GUI. I'm going to check out that Kommander, and I guess I should also see what Mozilla's XUL is like.

I'd also like a program that can digitise video from my external digitiser box.

---

### Post by pneaveill on 2006-08-07
> **red_Marvin said:**
> Personally I think installing in ubuntu is easier than windows, just
type *sudo apt-get install programname* or use synaptic to install a program, instead of having a wizard asking me **where** I want the program installed. To me the ubuntu way that is just a *different* way to do it which may take some time to adapt to but in the end isn't any harder than Window's way.

If you rather meant the many kinds of formats (deb, rpm, source etc) the programs get delivered in, you've got a point. Still, many programs are available as debs, and for the others you can come here for help. :)
The second listing there was more of what I was thinking. Thanks.

---

### Post by Stealth on 2006-08-07
Personally, I've been thinking of writing (maybe sometime in the future, when I know a lot more about programming :P) Mancala and a Dominoes game. Dominoes especially, as it's such as international game, yet I can't find any good open-source versions, and all the ones in the bargain bins are not multiplayer. Also, I like Mancala too, and would probably program that first as it *seems* easier to write...although I rather find someone else to do it, so that I can work on what I'm better at, on the graphics. ^_^

---

### Post by slimdog360 on 2006-08-07
a good easy to use circuit simulator like electronics workbench.

---

### Post by Michael_aust on 2006-08-07
A nice easy to use video tool, I am talking basically a rip off of windows movie maker.  All the Linux tools I have found are quite complicated.

---

### Post by mustang on 2006-08-07
> **slimdog360 said:**
> a good easy to use circuit simulator like electronics workbench.

Look into [Oregano]("http://arrakis.gforge.lug.fi.uba.ar/"). Last I tried it, it wasn't very functional but the project looked promising itself.

---

### Post by Kaloma on 2006-08-07
For all those looking for a configuration GUI to GRUB, how about [GrubConf]("http://grubconf.sourceforge.net/").  Even if it does not include every feature mentioned in this thread, it seems to be a good start and could easily be extended.

-Matthew-

---

### Post by pneaveill on 2006-08-07
> **mustang said:**
> Look into [Oregano]("http://arrakis.gforge.lug.fi.uba.ar/"). Last I tried it, it wasn't very functional but the project looked promising itself.
Although I have not used it quite yet, oregano is available on one of my repositories for Dapper.

---

### Post by notarikon on 2006-09-29
- Context menu option for all non-free video & audio codec encoded files to convert to OGG :) E.g., right click, click "Convert to Ogg" and the program checks what format it currently is and converts it for you (obviously with a nice progress bar and time remaining option)

- I'm surprised someone hasn't mentioned a DVDShrink and/or DVD Decrypter clone. Don't change anything, just make a Linux version *exactly* the same, and people will looooove you :)

- I second the (home) accounting / banking software, and also suggest landlord/tenancy management software

- An easy way to get a bootable iso onto a flash disk ...

---

### Post by dca on 2006-09-29
> **notarikon said:**
>  and also suggest landlord/tenancy management software

 
Indeed, a decent property management system for resorts instead of what's available on sourceforge.  Throw in point of sales, too WITH working touch-screen options.  
 
...heh heh heh, I know of a resort that is trying to re-open and use mainly open source software running on an old server w/ dual PIII 1GHz processors...  Oldie but a goodie.

---

### Post by NoTiG on 2006-09-29
I would like to see an app(it migh already exist) where you take a bunch of forums across the web and pic your favorites... and then you make a post and it posts to all of them simultaneously.... and tracks them each by email so you know if you get any replies. i think this could help with questions... in regard to linux... but more specifically i was thinking of hardware issues.

Like i had a question earlier today about what if memtest detects that your ram has a single bad address... is it worth keeping or RMA... etc. then post it to my favorite tech sites like pcmech, arstechnica etc....... posting to each manually is too tedious

---

### Post by Garyu on 2006-09-29
> **NoTiG said:**
> I would like to see an app(it migh already exist) where you take a bunch of forums across the web and pic your favorites... and then you make a post and it posts to all of them simultaneously.... 

You mean like spam software? You think it is a good thing to endorse those kind of things? :-k

---

### Post by Nonno Bassotto on 2006-09-29
1. An equalizer. Not one for a single app, like xmms, but a global one. Very useful since most new audio players (rythmbox, listen, ...) don't have one.

2. Something to tag pdf, ps, dvi and djvu files, like you can do for photos using gthumb or f-spot. One should be able to tag a document with useful info (author, language, possibly multiple topics and so on) and do searches based on these tags. Searches should be saved so one would have virtual folders to navigate. Then one should be able to open documents from inside the program. Maybe it should integrate with evince? Alas, as afar as I know, no such software exists even for windows.

---

### Post by notarikon on 2006-09-29
> **Nonno Bassotto said:**
> 2. Something to tag pdf, ps, dvi and djvu files, like you can do for photos using gthumb or f-spot. [snip] Alas, as afar as I know, no such software exists even for windows.

Ah, like the infamous WinFS they left out of Vista ;)

---

### Post by Wolki on 2006-09-29
> **Nonno Bassotto said:**
> 2. Something to tag pdf, ps, dvi and djvu files, like you can do for photos using gthumb or f-spot. One should be able to tag a document with useful info (author, language, possibly multiple topics and so on) and do searches based on these tags. Searches should be saved so one would have virtual folders to navigate. Then one should be able to open documents from inside the program. Maybe it should integrate with evince? Alas, as afar as I know, no such software exists even for windows.

Something like this was one of the Gnome WSOP sponsored projects, unfortunately I haven't heard of it in a long time. :-/ It was called "gJournaler".

---

### Post by Anonii on 2006-09-29
Couldnt find a small script that would find similar or duplicate files in a folder and its subfolders. it should be really easy to make.

---

### Post by NoTiG on 2006-09-29
> **Garyu said:**
> You mean like spam software? You think it is a good thing to endorse those kind of things? :-k

most modern forums have anti spam features these days.... like you can only post so many messages within a certain timeframe. so its not really spam because you couldnt spam more to any one particular forum than you can now.... but i can see how someone would want to use it in that regard.

---

### Post by dominator22 on 2007-06-20
Kuake-like terminal based on Multi Gnome Terminal

---

### Post by Kerin on 2008-03-05
> **dominator22 said:**
> Kuake-like terminal based on Multi Gnome Terminal

You mean Tilda?

(Oh, no.  Sorry about the necromancy, guys.)

---

### Post by DeadSuperHero on 2008-03-05
Make an IDE similar to Adventure Game Studio ([www.bigbluecup.com/](www.bigbluecup.com/)), capable of porting games to other platforms.
There's a few projects, such as SLAGE out there that are under the GPL.
However, I'd like to see one that utilizes the Qt toolkit, and maybe Java.

Benefits/ideas
-SVG support for Vector sprites. Images used wouldn't lose quality when resized.

-It supports complete cross-platform, and the underlying technologies (Plasma, Solid, Decibel, Phonon, Oxygen)

-Easily portable, and can run on top of/integrated with Java code.

-OpenGL acceleration/rendering.

-An extension system that developers could use to write plugins. (Similar to Firefox)

-Plasma technologies use widgets as parts of a window, the desktop,
whatever you want. So, lets say the editor could be rearranged by simply clicking, dragging, and dropping? That way, a user who doesn't like everything about the layout can rearrange it to resemble whatever works for them.

-Phonon is an open-source media framework that allows for a simple, streamlined media runtime. Using only 4 lines of code, one could build a simple music player. So, utilizing this would allow for media tricks in Slage. Ever had a problem playing an MP3 in-game? Ever wanted it to give a certain feedback when that MP3 is played? What about OGG? With Phonon, it is possible to easily resolve these problems.

-Decibel is built on the Telepathy framework, which calls forth technologies allowing the user to simply set up a multiplayer/internet script. Therefore, it would be easier to find ways for developers to write a multiplayer game.

-Solid is a hardware API. It interacts with Decibel and Phonon to tell the
game about the system it's being played on. What graphics card is running? What network card? Sound card? Is it multithreaded?

-Oxygen is not a technology per se. It's a standard for artwork.. Not game artwork, but the editor interface. Using Oxygen artwork, the editor could change from looking just functional to amazingly beautiful. Yes, artwork always takes the longest time, but it makes the environment feel so much more polished. 

It'd make indie Linux game development a whole lot easier, in my opinion.

---

### Post by brokencrystal on 2008-03-06
Native Linux Zune software, a Zune plug-in for Linux media players, or the Microsoft Zune Software running on Wine:

Right now there is no way to sync the Microsoft Zune on Linux.  Even if it had to be made to run on Wine, due to the complexities of the proprietary nature of the Zune.  I really need to be able to sync my Zune and the only way to do it is with the Zune’s proprietary software. Native software would be nice, or integration into a product that we already have available for Linux would be great. (Maybe through a plug-in) Though I fear this would be rather difficult, if not impossible due to the proprietary nature of Microshaft.  (Microsoft)

If you have time to work on this or know someone who works on the Wine project team that can work on this, please do share. The Zune is worthless without the software. Please don’t say “It’s your fault for buying a Zune” because I have already spent the 200+ dollars for it. Besides, the Zune is a really high quality media player! <-No Joke! It just sucks that you have to use Microsoft’s proprietary software to sync it… Any help would be greatly appreciated.

Thanks

---

### Post by phrostbyte on 2008-03-06
> **brokencrystal said:**
> Native Linux Zune software, a Zune plug-in for Linux media players, or the Microsoft Zune Software running on Wine:

Right now there is no way to sync the Microsoft Zune on Linux.  Even if it had to be made to run on Wine, due to the complexities of the proprietary nature of the Zune.  I really need to be able to sync my Zune and the only way to do it is with the Zune’s proprietary software. Native software would be nice, or integration into a product that we already have available for Linux would be great. (Maybe through a plug-in) Though I fear this would be rather difficult, if not impossible due to the proprietary nature of Microshaft.  (Microsoft)

If you have time to work on this or know someone who works on the Wine project team that can work on this, please do share. The Zune is worthless without the software. Please don’t say “It’s your fault for buying a Zune” because I have already spent the 200+ dollars for it. Besides, the Zune is a really high quality media player! <-No Joke! It just sucks that you have to use Microsoft’s proprietary software to sync it… Any help would be greatly appreciated.

Thanks

Zune support is part of libmtp, it's incomplete currently. Hopefully Microsoft will be forced to release specifications for it.

---

### Post by mikeize on 2009-03-16
An answering machine for softphones, like ekiga/gizmo, etc.  Even just a basic script that detects an incoming call on a given phone program, answers it (after a set amount of rings or time), plays a greeting, and records the message with audacity or sound recorder, etc... saves file to wherever as 'message01.wav' or whatever.

I have no idea what it takes to write programs, but shouldn't this be a relatively easy one?  I think a lot of people would find it useful--I definitely have been searching for this functionality for a LONG time.

---

### Post by cmat on 2009-03-16
A full blown configuration applet for wacom that offers all the features of it's equivalent on Windows. I'm currently working on one but it may get pushed back because of work/school.

---

### Post by Mehall on 2009-03-16
LCARS Window Manager

---

### Post by DonaldJ on 2009-03-17
Something that allows the background pix to be set to the left or right of the screen...

Then you can place a pix that is conducive to what it is your are composing...

---

### Post by conradin on 2011-05-15
1. Skype replacement (I know microsoft is going to kill skype linux support)

2. the terminal, history scrolls down screen. multi line command scroll down scree, terminal prompt remains on top. apparently the terminal would have to be rewritten to accomodate that, but it would mean alot to me atleast to not keep looking down screen & still see my past output.

---

### Post by Smilax on 2011-05-15
hello :guitar:

---

### Post by Smilax on 2011-05-15
this thread's been brought back to life 3 times allready, zombie tastic

---

### Post by conradin on 2011-05-15
a tool bar which doesnt dial home and report my logistics to some parent company but manages my bookmarks and synchs them up.

Something which searches for Networked printers, installs them and keeps searching. parts of that code already exist in linux. 

second idea: search engine filter buster. Something that monitors your search preferences akin to what google does, and searches, the antithesis of those ideas. Thus your queries could hope to be less biased. 

a package so I could install a quick temp mail server to my system.

a program that reports malicious traffic to avenues which could be used to stop said traffic. Like an anti zombie program, or that bad-sites thing on google. 

A program / game with the aim of informing people about cyber-security on multiple platforms, either as an RPG, or something else but with realistic examples, and possibly multiple roles.

---

### Post by uRock on 2011-05-15
If you need help, then please start a new thread.

Thread closed for necromancy.

---

