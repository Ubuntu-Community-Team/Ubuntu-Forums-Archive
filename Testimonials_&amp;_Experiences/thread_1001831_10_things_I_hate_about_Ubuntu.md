---
title: "10 things I hate about Ubuntu"
date: 2008-12-04
forum: Testimonials &amp; Experiences
---

### Post by timswait on 2008-12-04
OK, first thing, the title of this post is a little misleading, but "7 things I find mildly irritating about Ubuntu doesn't have quite the same ring"! 
Actually I Think Ubuntu is a wonderful idea, and mostly works brilliantly which is why I use it on my home computer, my work computer and have put it on my girlfriend's laptop. So please take this as constructive criticism rather than a slagging off. Also I'm no expert on computers, so maybe there's simple fixes for some of the problems I've had here (although I have already tried a fair bit with each of them, and I want to spend time using my computer, not trying to make it work.

1. Mounting of hard drives. Why can't it just automatically mount all my hard drives when I boot up? Also I keep getting problems with programs not finding documents easily because the disk number has changed since it was saved (maybe due to leaving a USB memory stick in when I turn it on for instance).

2. Documents folders. I can't find anyway to change where the default Documents, music, pictures folders are. I dual boot with XP (and I think it's safer to keep documents on a different partition to operating systems) so I have one partition for Windows, one for Linux and one for my files. Windows has no problem having the default "My Documents" folder on a different drive to the default "C:", so why can't I do the same with Linux. Similarly there's some folders in my Documents folder that are for no good reason locked, so I can't modify files in them.

3. Permissions. The most annoying thing in trying to follow instructions for how to install some program or other is when I try to copy a file into a folder and get told "You do not have the necessary permission to perform the operation". Why can't it just ask for a password? On the previous version of Ubuntu I had an installed something that gave me an "open as administrator" option for folders, but that's gone since I upgraded.

4. DVDs. I have Ubuntu restricted extras and libdvdcss2 installed and yet still can't always play every DVD (most work OK). I know this isn't the fault of Ubuntu, it's the fault of recording companies who delight in bringing out new and obscure forms of 'protection' (which don't really protect anything, people still seem to pirate them OK, it just annoys ordinary people who buy a DVD and then can't play it), but can the "restricted extras" package be kept a bit more up to date so it'll play everything?

5. Display. I have a built in ATi graphics card on my motherboard and keep getting problems. Mostly fixed now, I've been through the threads, and can't be bothered to fiddle anymore, only to have to do it again when I upgrade to the next release. Again I'm sure it's more ATi's fault than Ubuntu's, but can you hurry up and develop an open source driver for ATi cards, so we don't have to keep on using the proprietary ones?

6. Networking. Connecting and filesharing with Windows machines seems decidedly patchy. ATM I can see my housemate's computers, but not any files. If I want a file I have to go upstairs copy it onto USB stick and bring it down!

7. OK this is open Office and also GIMP, not Ubuntu as such but I thought I'd put it in. Cntrl++ and Cntrl+- don't work to zoom in and out (which are shortcuts I find useful), and clicking the middle button on the mouse doesn't let me drag the page around (which I also find useful).

Rant over, I already use Ubuntu as OS of choice over Windows, but if these things were fixed it would be perfect.

---

### Post by frankleeee on 2008-12-04
This is not a new topic there are many threads with this theme. So let me start anyway; all that free stuff really makes it hard to decide which one I want. I'm so confused.;)

---

### Post by timcredible on 2008-12-04
1 - label your usb drives, then they will mount same place all the time
2 - symlink the Documents directory to wherever you want
3 - linux is not windows.  ever wonder why there's no viruses for linux?  permissions!  they're not a problem, they're the solution.
4 - dvd encryption hasn't changed since the day the first dvd was released.  your problem is something else
5 - ati drivers are ati's responsibility, not ubuntu's
6 - i don't use windows anymore, can't say if linux-windows smb works well or not
7 - you can't be serious - you're complaining about shortcut keys that don't mimic office and photoshop?  that doesn't even deserve an answer.

---

### Post by moster on 2008-12-04
I could not agree more with you. But, I think they want it just like that because they not change some things in years. Take it as fact.

---

### Post by Keyper7 on 2008-12-04
> can the "restricted extras" package be kept a bit more up to date so it'll play everything?

> can you hurry up and develop an open source driver for ATi cards, so we don't have to keep on using the proprietary ones?

These "you developers are my bitches" demands simply make me sad.

---

### Post by cmat on 2008-12-04
Is it hard to accept that Ubuntu isn't Windows? The system was designed the way it is for a reason. It isn't going to change any time soon. Also lots of the developers aren't working on an hourly basis.

---

### Post by g0nzal01 on 2008-12-04
It seems that Windows is your kind of operating system. Not starting problems or anything, but why use Ubuntu if you have all these "problems"? I used and use windows all my life and came to the linux world because I was tired of worrying about virus and having to reimage my computer every time I got one. Not to mention that the software is extremely expensive (legally, that is). timcredible said it best, "linux is not windows. ever wonder why there's no viruses for linux? permissions! they're not a problem, they're the solution.". I'm new to Ubuntu also but just like everything else in life, you have to learn how to crawl to run.

---

### Post by Cracauer on 2008-12-04
Good post.

I'll ignore the points directly caused by messy protocols (Windows networking) and by ATI who now saw the light and give programming documentation, but the drivers we have today aren't benefitting from it yet.

> **timswait said:**
> 1. Mounting of hard drives. Why can't it just automatically mount all my hard drives when I boot up? Also I keep getting problems with programs not finding documents easily because the disk number has changed since it was saved (maybe due to leaving a USB memory stick in when I turn it on for instance).



Well, myself I want to mount some things readonly. Doing a read-write mount by default isn't in my mind.

But lots of bugs and issues, yes. For example, in Ubuntu 8.10 they broke (worked in 8.04) iPod devices in udev. They are now group "disk", not "floppy", so that mortals cannot eject them anymore.

> **timswait said:**
> 

2. Documents folders. I can't find anyway to change where the default Documents, music, pictures folders are. I dual boot with XP (and I think it's safer to keep documents on a different partition to operating systems) so I have one partition for Windows, one for Linux and one for my files. Windows has no problem having the default "My Documents" folder on a different drive to the default "C:", so why can't I do the same with Linux. Similarly there's some folders in my Documents folder that are for no good reason locked, so I can't modify files in them.



That's not the worst, it's a big problem that the big eparate groups in Linux (KDE/GNOME, OpenOffice, Mozilla, everybody else) have different ideas about what to store where.

Then there's things like Wings3D that don't seem to know the concept of a current working directory at all (all file open dialogs start in ~, and they read it from /etc/passwd, not $HOME).

> **timswait said:**
> 

3. Permissions. The most annoying thing in trying to follow instructions for how to install some program or other is when I try to copy a file into a folder and get told "You do not have the necessary permission to perform the operation". Why can't it just ask for a password? On the previous version of Ubuntu I had an installed something that gave me an "open as administrator" option for folders, but that's gone since I upgraded.



Pretty much unsolveable in a clicki-bunti desktop.

> **timswait said:**
> 

4. DVDs. I have Ubuntu restricted extras and libdvdcss2 installed and yet still can't always play every DVD (most work OK). I know this isn't the fault of Ubuntu, it's the fault of recording companies who delight in bringing out new and obscure forms of 'protection' (which don't really protect anything, people still seem to pirate them OK, it just annoys ordinary people who buy a DVD and then can't play it), but can the "restricted extras" package be kept a bit more up to date so it'll play everything?



I can play all my DVDs, and that's a lot, a 5-disk Netflix subscription. I don't use the Ubuntu precompiled packages, though.

> **timswait said:**
> 
7. OK this is open Office and also GIMP, not Ubuntu as such but I thought I'd put it in. Cntrl++ and Cntrl+- don't work to zoom in and out (which are shortcuts I find useful), and clicking the middle button on the mouse doesn't let me drag the page around (which I also find useful).


You can probably bind keys yourself.

---

### Post by tgalati4 on 2008-12-04
The OP brings out some good points.  From a newbie perspective, these are valid concerns.  Yes, there are work-arounds, but you need to know something about Linux to use them.  

For the DVD playback issue, perhaps a more specific description of the problem, such as title.  Perhaps others are having problems with the same movie title.

Perhaps the OP can send an email to ATI for his specific model card and the problems he is having.  Then post the reply from ATI.

There are lots of tutorials on SAMBA sharing.  The tricks needed depend on what types of Windows machines are being shared and how the shared directories are set up.  It's certainly not plug-N-play.

The OP wants specific short-cuts for Gimp and OpenOffice.  Anyone know if these conflict with other shortcuts?

Where the heck are 8, 9, and 10?  I feel cheated.

---

### Post by timswait on 2008-12-04
I'm not trying to be confrontational, and I do really appreciate the work that goes into it, it's breathtaking what's been achieved. But these have caused problems for me, so maybe they cause others problems too. And although I'm happy to spend a bit of time tinkering to make things work, it's nice when things work out the box easily, and I'd rather spend the time actually using the computer rather than setting it up.
Someone mentioned Symlink for my documents, what's that? I put a shortcut icon for the windows "My Documents" folder on my top panel, but it doesn't work when I first turn on the computer, only after I've already visited the folder since turning it on.
Yes I know permissions are important, and it's great that Ubuntu's so secure, but why can't I just enter a password when I want to move a file around, like when you open Synaptic or something, is that such a bad idea?
> It isn't going to change any time soon.
Isn't the whole point of it that it does change all the time? Every new release has improvements. I'm just pointing out things I've had problems with. Yes I can work round them, and I do, and I prefer it to Windows despite the problems, I know they're minor problems but it would be good if they were fixed. I'm not asking that any developers be my bitch, I'm just pointing out things that haven't worked for me.
> ATI who now saw the light and give programming documentation, but the drivers we have today aren't benefitting from it yet.
That's good news, I'm looking forward to the new drivers.:)
I don't think the shortcuts I mentioned are Windows specific. They work in Document viewer and gThumb already, from memory on Macs aswell, and are handy. As far as I'm aware there is no Zoom In/Zoom Out shortcut in Open Office.
> Where the heck are 8, 9, and 10? I feel cheated. 
That's why my subtitle of "7 things I find mildly irritating about Ubuntu" is probably better.

---

### Post by waspbr on 2008-12-04
Symlinks are analagous to shortcuts, when you run nautilus, try right clickin in a folder, you will see a option "make a link", select that, you will see that a folder named "link to the-other-folder" has been created, simply drag (or cut and paste) that to wherever you want to put it, say the desktop, you may even rename it if you wish.

graphics drivers are a hot issue, on one of my computers they work wanderfully, on another they work with a few minor quirks, unfortunately only the manufacturers can help us with that. On the mean time we have to work around it. There are problems even wrt to graphics card even in windows... 

As for the permissions, well, there is something you just need to get used to. Linux is not windows, it keeps sensitive files under permission lock for a reason. 

Though whenever needed these can be easily dropped, for example if you need to move files to a protected directory, the easiest way to do it is to use the command 

```
gksu nautilus
```

this will open a root nautilus, it will allow you to paste/cut/transfer/delete files with full authorization. though bear in mind that what ever you do is done, root permissions should only be used when needed. 

Permissions are something you use a lot in the early stages of your system, when you have all your stuff set, you will barely use it , aside for updates and new software.

remember that linux is not windows, once you started to use windows you had to get used to that too, give it time and patience and you will get used to linux too. 

if you have any problems don't hesitate to ask at the forums.

---

### Post by laceration on 2008-12-04
People are touchy, this guy is only asking for some help in a slightly backhanded sort of way.  Say no evil of Ubuntu, or we shall cut out your tongue ;)!

1.You can mount all your harddrives when you boot.  There is a file called fstab where you make these settings.  Open it like this:
gksudo gedit /etc/fstab
As to the exact settings, its been awhile, sorry, I don't remember--do a search.

2.I thought the same when I first started with Ubuntu, but then I figured it out.  It makes sense to keep your folders in /home/timswait because that's the way it is setup and I have a separate partition for that.  But even if you didn't get it optimally organized use the bookmarks feature in Nautilus.  You will then be able to easily access your locations from the system menu or anywhere a location choosing thing comes up.

3."Why can't it just ask for a password?" Good question.  Sudo is a pain in the a**, but as others have pointed out that's the cost of security.

4.F dvd's use bittorrent!  That could be an inadequate answer for your purposes, but that's the way I look at it.

5.Have you tried Envy to install your ati drivers? 

6.I haven't got the networking dialed in myself--I've got no help for you there.

---

### Post by zaine_ridling on 2008-12-06
1. **Mounting of hard drives.** *Why can't it just automatically mount all my hard drives when I boot up? *
Amen. I run a second drive as a backup in every computer, but this is a hit-or-miss exercise for me every 6-12 months, and a major turnoff for first-time Ubuntu users. Now you can bitch about that if you want and make all the excuses you want, but Canonical needs to sit some newbies in front of Ubuntu and see what they're doing wrong. It would save a lot of forum time and space.

2. **Documents folders.** *I can't find anyway to change where the default Documents, music, pictures folders are. *
For me, it's trying to locate where programs install config files. These get thrown everywhere depending on the program, and sometimes it's difficult to make a simple link on the desktop to an obscure program.

3. **Permissions**. *Why can't it just ask for a password?*
Yes, simple. Why not? You're going to give it eventually anyway. Let me do what I want with my computer.

4. **DVDs**.
Yea, this is just one of those things....

5. **Display**. 
Because I've tried everything to get an ATI card working for the past five weeks with kubuntu, I've reluctantly installed Fedora 10, and holy cow, everything worked, including setting the proper 1900x1200 resolution. (1) If I can't see the screen after installation, I can't use your OS (I've spent days doing everything suggested on this forum), and (2) If I can never buy a newer <1-year old videocard with Linux, then sure, I'll save money, but that also sends me back to distro-hopping when I really want to be using kubuntu.

6. **Networking**. 
I don't use this feature, fortunately. Sorry.

7. **This is [re] open Office and also GIMP**, *Cntrl++ and Cntrl+- don't work to zoom in and out (which are shortcuts I find useful), and clicking the middle button on the mouse doesn't let me drag the page around (which I also find useful)*.
For **OpenOffice**, first, open the default template file (ODT, not ODF), and then customize your keyboard shortcuts in OpenOffice and apply it to all of the suite's apps therein. Then restart. Unfortunately, **Gimp** lacks keyboard customizability and doesn't have shortcuts for several the trivial, repetitive tasks I do every day. I like Gimp, but that's a waste of my time to punch so many keys or grab the mouse and start drilling through the menus.

---

### Post by Tamlynmac on 2008-12-06
The thing I really hate the most about Ubuntu is:

[SIZE=3]**It's FREE.**[/SIZE]

As in free to download, evaluate and use. **It should be illegal**. If it doesn't meet your expectations, it can be un-installed. I struggle with the complaints when considering that no investment (other than time & learning) is needed to try the OS or continuing it's use. Expecting perfection or even a functional, quality OS for free in this commercialized world is inconceivable to me.

We have five home systems and all five run Hardy. The last thing you'll hear from me is a complaint. We used Windows for "years" (since 3.1) and I can say without reservation, that a bad day with Ubuntu is better than any day I've spent troubleshooting Windows.

I'm certain I'll get flamed and that Ubuntu doesn't need me to defend it. But IMHO this incessant need to complain about a free OS because it's not a Windows clone or that it doesn't meet everyones expectations, seems rather petty. I think we should all take a moment to consider the time and effort the developers have already invested to produce this OS. I'm aware that many believe complaining is a form of feedback and I'm fine with that. However, since the developers don't use the forum, then who are the complaints targeting? Other users, new users???

Again, this is simply my opinion. Kinda like bellybuttons.:smile:

---

