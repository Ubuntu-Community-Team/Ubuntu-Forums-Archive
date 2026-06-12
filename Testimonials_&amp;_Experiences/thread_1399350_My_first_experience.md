---
title: "My first experience"
date: 2010-02-05
forum: Testimonials &amp; Experiences
---

### Post by degarb on 2010-02-05
I dumped windows me on Wife's old laptop computer (p3 600, 512 meg ram and 6 gig hard drive) and installed Ubuntu 9.10 standard.  They recommended xubuntu, but I thought I would give standard a try.  All went okay, except the wireless card didn't work out of box (copy protected belkin drivers.) so, I had to install ndiswrapper gui, which allowed me to put put in the windows cd and install the inf of xp.      

I have tried 5 versions of Linux since 2000, and never liked any.  Vector had a good community, but inferior interface.  Ubuntu has a remarkable huge, helpful community. I have posted comments just short of Linux sucks, and not got flamed or a rude response. Weird.   Firefox loads faster, loads pages faster, and more stable on Linux than Windows.  Using Open office, etc.   One weird thing is you don't have to go on google to find applications, you use something called a snaptic package manager, (you should tell it to use universal servers for more software- one's not officially sanctioned)  and just type in what you want and click install, free so far. 

Quirks:  I haven't yet figured out how automatically mount an xp share folder.  In o office, if you want to use a xp share, you must first browse that folder.  Googling, ubuntu answers often yields command line solutions, even if a gui solution is obvious, because old versions are being googled.  Every time I see a commandline answer to something easily done graphically in windows, it raises my ire. Fortunately, when I have expressed disgust in forum, I haven't got banished, as likely by other nazi forums.  One thing that concerns me is upgrading or repair; I hate installing software since on windows I count about 80 regularly used programs and it takes about 27 hours to reinstall the bulk after each windows wipeout.

Wine: so far this is first intuitive wine I have seen.  I have tried about 8 programs so far and about half of these windows program have worked.  Initially, the first four worked, which got me really excited.   But I have yet to learn any tricks with wine or try any beta versions.

What sets Ubuntu apart is that it works out of the box,  has a huge helpful/friendly community, and wine that seems to work/tons of replacement applications.   What makes it better than xp, is price, community, and works on old hardware  , Though a p1 133 100meg ram is what I consider old hardware, since win 98 would run fine on that old machine.  I do think it remarkable that this little old laptop is running as nicely as if on XP, with same functionality.

I really think alternatives to the directory structure needs to be proposed.  The structure intimidates and 10 years out since first redhat install, I still don't get it and never will, since it lacks logic, missing the obvious organization. Take a room full of 100 average people: age 15 -25 most would learn it without question; age 50-65 none would never learn it, thinking they were dumb; age 25-50 most would realize that the structure doesn't make sense because it was invented in the 80's or 70's when mounting drive was a huge issue (so sub folder) , programs were an after thought, system directories that inventors probably accessed constantly are scattered in root and everywhere.    Obviously, windows has best structure:  drives> system+program files+ docs and settings .   But a compromise could be made.

---

### Post by Methuselah on 2010-02-05
Interesting comments, thanks for posting.

The directory structure is different from windows but I don't personally find it confusing.

All user data is under /home.
So if your account is 'degarb' all your personal files would be stored under /home/degarb making it equivalent to C:\documents and settings\degarb under windows.
Installed programs are generally situated under /usr/bin or in a subfolder thereof while configuration files are under /etc.
/etc is somewhat like the windows registry except that everything is just an ordinary folder with plain 'notepad'-editable text files.
Of course, there are more details but that's the general idea.
The directory organisation is actually a standard used by a number of unix-like OSes and while it may not be incredibly obvious to the uninitiated (of which I was once one) what everything stands for, it *is* organised.

Anyway, glad to hear what worked for you.
Continue to have fun with it!

---

### Post by armandh on 2010-02-05
Love Ubuntu
Hate the way programs are named 

Love VLC
would have never found it looking for a player

and all the Knames drive me nuts


Still Ubuntu is the easiest OS going

---

### Post by kg4cna on 2010-02-05
Seems you're doing pretty good with it despite the "unorganized" filesystem.

The file system makes pretty good sense to me and I've not had a problem finding anything. I like the way it's organized. I don't dislike the windows way...I just prefer the linux way.

A~

---

### Post by woodmaster on 2010-02-06
+1 on the filesystem making pretty good sense.  I've only been using or even seen Linux since last Oct.  Enjoy your Linux experience!!!

---

### Post by Tamlynmac on 2010-02-06
> degarb

Thank you for sharing you testimonial. This section of the forum is the ideal place to post such experiences.

---

### Post by stalkingwolf on 2010-02-06
IMHO your issue with the file structure is that you are used to the windows way.  I find the windows way tedious.  Where is **** system? system32?  programs? i also find that fixing glitches in win is a PITA.  first get it into safe mode then recovery or run apps to fix.  sometimes the easiest(insert sarcasm thick as sorgum) way is to format and reinstall.

With Ubuntu i reboot select recovery then fix broken.

but that is just my opinion.

---

### Post by degarb on 2010-02-06
> **stalkingwolf said:**
> IMHO your issue with the file structure is that you are used to the windows way.  I find the windows way tedious.  Where is **** system? system32?  programs? i also find that fixing glitches in win is a PITA.  first get it into safe mode then recovery or run apps to fix.  sometimes the easiest(insert sarcasm thick as sorgum) way is to format and reinstall.

With Ubuntu i reboot select recovery then fix broken.

but that is just my opinion.

I am yet unfamilar with set recovery.   Is this some error?   

I was wondering if there is some rollback option in Ubuntu.  I am somewhat afraid of messing too much with settings without this.

I like his response for explaining relevant directories. However, I read it yesterday and I am struggling today to remember all of it.   I liked his approach because it concedes only a small part is worth remembering; this is doable for some users, once they aren't hit with poor design that is stated as good design.  But, 1. He proved my point by not mentioning %95 of the directories that are in your face and root that should be under system.  2. He proved my point by stupid naming scheme (etc) which holds limitations of : 1980 directory file naming string limitations; and bad choices for folder names!   ;    still things are not obviously lasso'd into proper master folders--system;programs;settings;docs.;  I never want to use an os where I have to manually mount things, thus drives should never be in a folder, much less buried.

---

### Post by degarb on 2010-02-06
One thing that could be done is a Nautalist plugin that "maps" the current directory structure to a more logical one.    At the least renames 1980s dir naming with longer names. Example: etc could be "ETC/Everday Configuration text files"  and "your drive are hidden here" etc.  A user could toggle between the modern and old views of the directory structures with a click. 

At very least, if you want more people to adopt this old, aging structure, it needs to be taught in a way with 1. mnemonics. 2. focus on the important directories for new users 3. don't pretend this is not a flawed structure; since, this will drive off most people that won't get it.

---

### Post by hashimoto on 2010-02-07
> **degarb said:**
> ... 3. don't pretend this is not a flawed structure; since, this will drive off most people that won't get it.

If you want to drive a car, you need to have a driver's licence (=_learn_ to drive)
If you want to service/fix your car you need to _learn_ mechanics etc.
If 'you want to to make cars/engines you must _learn_ combustion engines, thermodynamics, mecahnics, machining...

 Cars or engines are not made by john doe, but professionals that have studied for years for their degree. Like wise with the operating system/software and programmers. The structure behind the directory system makes perfect sense to programmers. It serves them to make a functioning, clear, structured operating system. If you want to go that deep you must _learn_ and it takes time and effort. Don't expect it to be easy.

---

### Post by lancest on 2010-02-07
Unless you are planning to use the CLI much in Linux all you really need to know is the local directory structure that can been accessed easily in Gnome. 
If you plan to be good at the CLI then no real reason to complain-just learn the Unix way. 
IMHO Windows alphabetic drive structure is a joke. Apple doesn't need it either.

---

### Post by degarb on 2010-02-07
> **lancest said:**
> Unless you are planning to use the CLI much in Linux all you really need to know is the local directory structure that can been accessed easily in Gnome. 
If you plan to be good at the CLI then no real reason to complain-just learn the Unix way. 


Good point,  however, I--and probably a sea of people behind me-- am the system operator and would like something that makes some logical sense.

For example to take the Linux bias out,  if the Unix developers created the first human from a pig and needed a directory structure so people could configure themselves and work on themselves,  the structure of the file system would be:  in the root would be a directory /aed/ which included hands, legs, brain.  While parts of the cerebellum would be in the root.  The person's parents would be in root/mnt  and the person's friends and peer would be in the /home/username/.gsfv  The experience user would argue that this makes sense and of course the feet/hands/legs are in the aed dir, since this is main function of a  person...   Hopefully, one day some one smart would come along and explain that the reason the hands/legs/brain are in the aed is because aed stands for "advanced evolutionary development"  the proudest achievement of the creators;  the persons parents are in the root/mnt (like mounting the family tree) and peers are in a sub directory, is because the very idea of parents and peers was an after thought (gsfv might mean gosip/stuff/files/variables).  The reason many cerebellum parts are in root is because the inventors needed quick access to these via the command line that they need many times per hour....It makes some sense now...And, even better, would be someone saying, "Wait! In the root directory of a person, should only be three directories: /body /head/  and /appendages  the person should be a sub directory of the parent and peers should be at same hierarchy as person    so entire dir structure could be called "my immediate world"  To not rock boat, the old structure could be mapped to simpler, more logical structure, in a "plugin" to default file browser.  Other OS's have reinvented themselves every 5 years.  This would be reform that would be only good, a step forward, for the dominance and acceptance of the Platform, linux/Ubuntu.

You could, at very least, have mouse-over-hover tool tips explaining as much as possible in the Nautist  file browser.

---

### Post by odysseusjak on 2010-02-07
I guess I'm a little confused.  Why does the 'average' person need to be in the file directory anyway?  Most people just click on the icon from the menu(s) and start their application.  Or they open their personal files from their 'home' directory.  People don't really even go to the file directory in Windows (all that much).  They just do the same thing -- click on 'My Documents' or click on an icon in the menu or Quick Launch bar.  It seems like only the 'geeks' or 'geek-leaning' people mess with the file structure.  Most of the people I deal with (I'm a tech for a university) just want their systems to work when they click on an icon.

---

### Post by Roasted on 2010-02-07
> **stalkingwolf said:**
> IMHO your issue with the file structure is that you are used to the windows way.  I find the windows way tedious.  Where is **** system? system32?  programs? i also find that fixing glitches in win is a PITA.  first get it into safe mode then recovery or run apps to fix.  sometimes the easiest(insert sarcasm thick as sorgum) way is to format and reinstall.

With Ubuntu i reboot select recovery then fix broken.

but that is just my opinion.

I agree. As a user of Windows for 10 years, and a user of Ubuntu for 4 years, I can honestly say things click better with the file structure of Linux. I find it extremely lacking in Windows. Just step back and look at the file system tree, where things are stored, etc. You will see many similarities that correspond with one another (My Documents vs Home Folder, etc) but I find what the user I quoted said... system? system 32? Some of it is just kind of stupid, but I can still make my way around the Windows file structure. I just prefer the Linux way.

---

### Post by degarb on 2010-02-08
> **Roasted said:**
> I can honestly say things click better with the file structure of Linux. ... I just prefer the Linux way.

   I think if there are more directories in the root (rather than three root categories), you can get around better with a commandline.  This doesn't make for a more structured structure.


    If Ubuntu really wanted to do better than Windows, each directory could have three fields for index:  a Nickname, a LongName, and a Description.  A nickname wouldn't have to be unique, but if a unique one chosen, a person could just type cd r3nail rather than cd /appendages/right arm/hand/finger/r3nail
The command line would show only nicknames (etc, shares) or longname, depending of which prompt was called.  Nautist or other graphical browser would show nicknames (longname) or either, depending on view choice.  On mouse flyover, the description field would appear, unless turned off.  A good graphical browser usually has a command line at bottom (relative to open directory) and "cd somenick" could be used there.

---

### Post by ElSlunko on 2010-02-08
I understand where the OP is coming from. Even today I get confused by the abbreviations at times and I've been on Ubuntu for almost 3 years now. The thing is, I'm an average user and these things just don't matter in the long run as far as "normal" usage goes. The home directory is powerful enough in containing application specific settings.

Shoot. I just learned that you could replace application specific icons in ~/.icons ! That was pretty sweet :D

---

### Post by Roasted on 2010-02-09
> **degarb said:**
> I think if there are more directories in the root (rather than three root categories), you can get around better with a commandline.  This doesn't make for a more structured structure.


    If Ubuntu really wanted to do better than Windows, each directory could have three fields for index:  a Nickname, a LongName, and a Description.  A nickname wouldn't have to be unique, but if a unique one chosen, a person could just type cd r3nail rather than cd /appendages/right arm/hand/finger/r3nail
The command line would show only nicknames (etc, shares) or longname, depending of which prompt was called.  Nautist or other graphical browser would show nicknames (longname) or either, depending on view choice.  On mouse flyover, the description field would appear, unless turned off.  A good graphical browser usually has a command line at bottom (relative to open directory) and "cd somenick" could be used there.

Even though I understand where you're coming from, I'm failing to see how it's any more complicated than the Windows setup. I work in tech support with a couple hundred XP systems, and I know what a headache it can be to dissect the Windows folder, delete certain files, move this file, etc to get certain issues fixed. While I do not deal with the same amount of Linux systems, I still get into the nitty-gritty of Linux enough to be a little confused over how Windows is in any way shape or form easier, mostly due to my continued frustrations with it day in and day out.

Either way, an average user probably won't need to do anything except in /media and in /home, which in itself is pretty smooth to understand.

Also keep in mind, this may be coming from the stand-point of what's more familiar to me versus you.

---

### Post by jdrodrig on 2010-02-11
I agree with the OP and with several of the suggestions; especially a way to exploit Linux open source property so that third parties could easily build directory simplifiers that map the standard linux way to other simpler structures.

On a related topic; desktop search engines improving as we speak will make the actual directory structure somewhat obsolete given that you would be able to find the desired file right away.

A feature I like of OpenSolaris is the "zfs create directory" command. You can create filesystems (think directories) without caring where in the pool of hard disks it resides. Is there an equivalent current of future feature on ubuntu? or a third party software that could do that?

---

### Post by HappyFeet on 2010-02-11
> **Roasted said:**
> I agree. As a user of Windows for 10 years, and a user of Ubuntu for 4 years, I can honestly say things click better with the file structure of Linux. I find it extremely lacking in Windows. Just step back and look at the file system tree, where things are stored, etc. You will see many similarities that correspond with one another (My Documents vs Home Folder, etc) but I find what the user I quoted said... system? system 32? Some of it is just kind of stupid, but I can still make my way around the Windows file structure. I just prefer the Linux way.

I totally agree. I was a windows user for years. I thought I was the bees knees when it came to computers. I discovered linux in 04, and I discovered a world I never knew existed. Sure, I still try to keep up with windows to a point, (because I fix computers) but I've never felt the satisfaction I feel now as a linux user. I even know how to get around a mac, which affords me the luxury of making *everything* work. 

If linux doesn't work for *you*, that's OK. Windows doesn't work for *me*.

---

