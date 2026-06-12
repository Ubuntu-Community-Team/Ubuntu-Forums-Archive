---
title: "Introducing My Dad to Ubuntu"
date: 2009-07-04
forum: Testimonials &amp; Experiences
---

### Post by sharkbaitbobby2 on 2009-07-04
**Introduction**: My dad is a lawyer who does most of his work inside Microsoft Works on XP on his Dell laptop. Recently though, he's been trying OpenOffice and liking it. His XP install seemed to be degrading significantly (AVG was on the fritz, some weird DSL dialog would popup on startup, the system would lock up and the HD would be in full use for several seconds). He bought a nice HP printer connected to his Compaq desktop a while ago. The printer has an ethernet port, but the router in use is too old and broken to allow for static IP addresses, and Windows on his laptop could not work with it. I decided to introduce him to Ubuntu.

**The laptop** is a few-years-old Dell Inspiron 9400 (17 inch) with Dell/Broadcom WiFi and ATI 256mb GPU. With Ubuntu 9.04, everything except the WiFi worked completely out-of-box, even compositing graphics. After the install, the WiFi worked with Ubuntu's proprietary drivers dialog and a restart. Standby works fine and hibernate worked the first time I tried it, but it probably took about as long as a full reboot. As far as I can tell, all the function keys work, including volume and brightness. Notify-osd pops up for volume, brightness, eject, and battery status.

**The process:** I decided to dual-boot XP and Ubuntu, in case he still needed XP for something or he didn't like Ubuntu. Partitioning was complicated because there were already 4 primary partitions ("DellUtility", XP, Dell MediaDirect, and a seemingly unused backup), and I could not create another. I deleted the backup partition (it was only 3GB and only 1GB was used (the numbers were exact in GiB)) and used it as swap and downsized the XP partition by 9-10GB for Ubuntu. It took 30-45 minutes as it had to move several things around. Then I installed Ubuntu, which took under 30 minutes. Afterwards, I had to do the classic setup routine:
[LIST=1]
[*]Disable the oh-so-annoying and loud system beep
[*]Install the proprietary Broadcom drivers
[*]Choose the best apt mirror
[*]Apt update & upgrade
[*]Don't have update notifier pop up (set /apps/update-notifier/auto_launch to false in gconf-editor)
[*]Install that printer (System->Administration->Printing->New; couldn't be easier)
[*]Copy actual documents from Windows' "My Documents" into ~/Documents
[*]Install Banshee, add "My Music" to library
[*]Install ubuntu-restricted-extras
[*]Create ~/Downloads, add as bookmark, and have Firefox download to it
[*]Install gnome-colors icon themes
[*]Change to Dust Sand gtk with blue (#7395b9) select color, gnome-brave icons, Clearlooks window decoration
[*]Install [Memorizer]("https://launchpad.net/memorizer") just to show it off. ;)
[/LIST]
**Thoughts:**
Many people say Ubuntu will only be "ready for the desktop" when a grandmother can download, install, and use it all by herself. I say that is a horrible metric. The average user would not be able to install even Windows or OS X, and should not be expected to. My thoughts on what I had to do to setup:
[LIST=1]
[*]The system beep should not be enabled. I don't know why it is. It's very loud and annoying.
[*]This could not be easier. Click icon, click Enable, enter password, restart, rinse, repeat.
[*]This is just an advanced optimization. The main server works just fine.
[*]Apt would upgrade eventually, and is easy to do. This was a large update, so I did it then to get it out of the way.
[*]I'm split between "this is a horrible decision" and "it's a matter of personal taste." Either way, I don't like it too much, and there's nothing wrong with the icon in the systray.
[*]Again, couldn't be easier. Definitely a lot easier than in Windows (driver CDs!) (additional crapware!) (not working!).
[*]This isn't necessary for most users. I'm not one of them. However, this process could be difficult for a beginner. The Windows partition is called "103.9 GB Media". Ubuntu should be able to recognize that it's a Windows partition and label it as such. (I think there's a paper cut about that.) Also, there should be an easier way to access "My Documents", maybe in the Places menu or added as a bookmark (if the Windows and Ubuntu user names match closely enough). Or there could be a series of "Bob's Documents", "Tom's Documents", etc, like in Windows' "My Computer" as an administrator.
[*]Same as above about the Windows partition. Rhythmbox is fine for most users, I find Banshee to be easier and better looking.
[*]This is why the average user would not be expected to setup a system he installed; a brand new Ubuntu user would not know about ubuntu-restricted-extras. But when attempting to play an audio or video file, the install-codec popup could not be much easier otherwise.
[*]Should be default, plain and simple. Keeps things organized.
[*]Personal taste. (Very nice and complete icon theme.)
[*]Personal taste. The Human Gtk theme isn't too bad, but the icon theme is ugly, clunky, and not Tango-like at all. Much space could be saved by making the button size smaller and the background color should be just a shade darker.
[*]He likes Memorizer, though he has no use for it.
[/LIST]
**Other Thoughts:**
[LIST]
[*]He's had Ubuntu for a few days now. He said he likes it, but will still use Windows to do work for now until he becomes more accustomed to Ubuntu.
[*]He grasped the concept of an operating system pretty easily. However, he had difficulty understanding the idea of separate partitions for Ubuntu and Windows, what exactly would be updated by Apt, and how Ubuntu can be free. If people have serious difficulty understanding what a browser is, explaining Linux can only be more difficult. Fortunately, he's above that level, as knows he's been using Firefox, not "the Google".
[*]He has not touched the terminal. He does not know what a "terminal" is. I removed it from the menu. As far as I remember, I've only used it to add and sign the Banshee and Memorizer PPAs and install them, which can be done without the terminal.
[*]The only terms he's learned through this process are Ubuntu, Linux, OpenOffice(.org), Banshee, RMS and Linus Torvalds. He has not even heard Apt, GNOME, Gtk, terminal, or command line, nor should he have to. How is an average user supposed to know what a "widget toolkit" is?
[*]He has almost 10GB of music (about 1% of which I like). Banshee uses at most 38mb of what gnome-system-monitor calls "Memory", even while playing. While I type this, the Pandora applet is using over 100mb. Much of the concern over Banshee's memory usage is concerning netbooks. I doubt that many netbook users would have thousands of songs, but I'm not one of them.
[*]I taught him how to export to PDF, and he had no difficulty with flash drives. Though I haven't asked him directly, I suspect he thinks clicking the "eject" icon is much easier than Windows' crappy "Stop device" method.
[*]I haven't yet introduced him to Awn. Because the screen is so wide, Awn will have to be on the left or right, so I'll have to wait until 0.4 is released or at least the rewrite hits trunk. He likes Pandora, so I'll have to add that applet. I'll also add to-do, mail, tomboy/notes, weather, a main menu applet (probably YAMA), and maybe quit/logoff.
[/LIST]
**Overall**, I'd say the process is going very well. Ubuntu really has come a long way, though not quite where most people could install it by themselves. However, OS installation is an inherently difficult and complicated task.
The [Hundred Paper Cuts]("https://launchpad.net/hundredpapercuts") project covers a few problems I pointed out. Especially with Hundred Paper Cuts for Karmic, I think that, with setup from an experienced user, Linux is ready for the desktop.

(Copied from [my blog]("http://sharkbaitbobby.blogspot.com/2009/06/intoducing-my-dad-to-ubuntu.html").)

---

### Post by armandh on 2009-07-04
my wife still asks questions like how do I get the e-mail bigger?
[while reading in the preview pane]

but she hated vista always interrupting her e-mailing or shopping for its house keeping [window cleaning]

I cursed it as well when it insisted on a reboot in 4 minutes after some dumb load while I was looking for a few old e-mail addresses for her. as soon as the AV subscription runs out its a wipe.

my daughter JD/LLM uses ubuntu on her home desktop.

---

### Post by sharkbaitbobby2 on 2009-07-04
> **armandh said:**
> 
but she hated vista always interrupting her e-mailing or shopping for its house keeping [window cleaning]


When my dad bought the laptop, I told him to choose XP instead of Vista.  I don't want to imagine the problems he would have with Vista. :)

---

### Post by betrunkenaffe on 2009-07-05
I like this post because while your set up is a bunch of steps, you qualify that 90% of them are personal preference :P

Find out how it goes, especially if he has any problems with the sending of documents to others.

---

### Post by Tinman131 on 2009-07-05
> **betrunkenaffe said:**
> I like this post because while your set up is a bunch of steps, you qualify that 90% of them are personal preference :P

Ditto, and I'd even say that "...you qualify 90% of them *with* personal experience."  For someone who's also kind of new to Ubuntu and FOSS in general, it's nice to see someone more experienced post up the customizations THEY make and then tell you why they did it.  I plan on applying some of your 'recommendations' to my system as well.

Nice job.

---

### Post by steveneddy on 2009-07-11
Great story.

---

### Post by sharkbaitbobby2 on 2009-07-11
Everyone, I have a tragic story.  Windows no longer works on my dad's laptop.  It had a BSOD and the next time it booted up, it just gave an unhelpful message.  The Windows partition is still working though.  So I had to make Ubuntu the default in GRUB.

In Windows, he used Microsoft Works, which uses the archaic .wps format.  Most people cannot open it, and OpenOffice.org usually has significant difficulty with it.  The text loses its alignment and all the text is strikethrough.  .doc files open fine though.  He's using his desktop at least part of the time until all the .wps files are converted to .doc.  (He emails some files (as .doc) and prints and faxes the others (as .wps/doc).)

I installed Avant Window Navigator and awn-extras.  I built the rewrite from source (not recommended btw, PPA packages ~soon) so I could start a brightness applet. I put Awn on the right side so it somewhat resembles his Google Desktop sidebar he had before and saves space on the widescreen.  From top to bottom, I have YAMA (main menu), taskmanager (tasks only), cairo-clock, file-browser-launcher, to-do, volume-control, pandora, notes, and my WIP brightness applet. [[Screenshot]("http://img89.imageshack.us/img89/766/screenshotsye.png")]

I intoduced him to Awn and the applets, but I don't think he's used them yet.  He relied on a 'Scratch Pad' gadget in Google Desktop, and I think the notes applet will replace it sufficiently.

He uses Yahoo Mail, and I'm not sure if he's sent any files with it yet, but I doubt he'll have much difficulty, provided that he sends .doc files.

Before, I had copied only the files in "My Documents" into ~/Documents.  However, because of OO.org having difficulty with .wps files, he had to use Windows occasionally (before it died).  The files were not synced, but he usually fully writes a document and emails/prints it then doesn't touch it again, so it wasn't a serious problem.  But I decided to copy his Ubuntu-started documents into "My Documents" and link ~/Documents to "My Documents" so it's not a problem.

Over the few years, the laptop's included battery's life degraded from about three hours to zero (literally, 0.0 seconds).  So now the laptop just runs on AC and hope that the cord doesn't come out.  However, the CPU Frequency is set as 'Ondemand' in the gnome-panel applet by default.  The laptop uses at most 90 watts, so I imagine that having the maximum (1.73 GHz in this case) as default under AC wouldn't be an issue. 1.73 GHz is noticeably faster than 'Ondemand'.  (FTR, I don't fully understand/know the purpose of CPU Frequency selecting, but I think I know some of it.)

I showed him how to do Apt updates (without mentioning Apt, of course), including entering his password, which I chose (last name, lowercase).  The notify-osd popup for updates really grabs his attention.

Lastly, GRUB is an important part of the system, especially the default OS.  A graphical editor should be included in Ubuntu by default (System->Administration->Boot Menu), because most people wouldn't know where to look (/boot is easy, but what's "grub"?), and might not be able to figure out what exactly to edit in the file.  And of course, there's the issue with root permission (what's a "sudo"?).  A GRUB editor by default will help significantly novice users who want to modify their boot menu.

---

### Post by Irihapeti on 2009-07-11
If you call that "tragic", then I'm wondering what your "great" story would sound like. We'll all be blown away! :)

---

