---
title: "A  newbie questions"
date: 2014-11-02
forum: Ubuntu, Linux and OS Chat
---

### Post by david_huang2 on 2014-11-02
Hi, 
I have about 10 years using Windows.
Today is the first day I installed Ubuntu 14.0.4 over a laptop used to run Win 8.1 Pro.

There will be many questions to ask, but I'll start with 2.....
1. How do I make a shortcut to the desktop ?

2. How do I see "my computer" so that I know how much disk space  available ?

Thank you.

---

### Post by mageta2 on 2014-11-02
Welcome to the forums. You can open a terminal ( CTRL + ALT + T ) and type 

df -h

To see information about disk space. I don't use a GUI so I can't tell you how to do it that way unfortunately. I'm sure someone with more experience will be able to show you another way.

---

### Post by Bucky Ball on 2014-11-02
*Thread moved to **(unknown)**.*

> **mageta2 said:**
> Welcome to the forums. You can open a terminal ( CTRL + ALT + T ) and type 

df -h

To see information about disk space. I don't use a GUI so I can't tell you how to do it that way unfortunately. I'm sure someone with more experience will be able to show you another way.

Not great advice for a first time user who has explained they have no Linux experience. They probably don't even know what a terminal is. ;)

Please take note of users' experience level and I have now move this post to reflect it. Thanks.
___

@david_huang2: Welcome. 

1/ I don't use Ubuntu but Xubuntu so making shortcuts I'm not sure about. You could try right clicking on what you want to make a shortcut to and 'Create shortcut' if its there ...

2/ To see used space on all disks and partitions, open Gparted. For me it is in the System menu.

You can find your mounted partitions in /mnt (I change things and it might be different in Ubuntu so might be /media).

Hope that helps.

---

### Post by Bucky Ball on 2014-11-02
There is also this from [HERE]("http://www.codemarvels.com/2012/05/create-shortcut-launcher-on-desktop-on-ubuntu-12-04/"):
> 
If shortcut to an installed application is to be created -

    Go to Home Folder &#8211;> File System &#8211;> usr &#8211;> share &#8211;> applications.
    Right click your favourite icon, choose Copy To &#8211;> Desktop

(from mhdizam&#8217;s comment, verified working)

---

### Post by coldraven on 2014-11-02
1. Most Linux distributions have multiple desktops, sometimes called "workspaces". 
Ubuntu by default has four that are arranged in a square but the number and arrangement can be changed. (See: CompizConfig Settings)
To see all four press Winkey+S (The Windows key is called the "Super" key in Ubuntu)
There you can drag applications to any of the desktops, it is handy for grouping applications. Just click on a desktop to select it.
You can also move between desktops using Ctrl+Alt+Left/Right/Up/Down arrow keys.

2. Ubuntu has a couple of disk information utilities, they are not very good. Bring up the Dash by briefly pressing the Super key and then type Disk. You will see them at the top of the screen. Dash can also be called by clicking the top item in the Launcher. (The bar that pops out when the mouse is moved to the left side of the screen) To exit the dash click it's icon again or press Esc.

Or use  the file manager Nautilus, select it from the launcher (The second icon down, labelled "Home Folder") then right click on some empty space and select "Properties".

---

### Post by grahammechanical on 2014-11-02
The Dash does away with the need for icons on the desktop. Get to know Ubuntu and how it works. Do not try to make Ubuntu work like some other computer operating system. That will lead to disappointment.

Remember, the developers of Linux and all the software projects that make up a Linux distribution are not providing a cheap copy of some other OS. These developers have their own ideas on how a computer operating system should work and what it should look like. And that gives us freedom of choice.

Regards.

---

### Post by buzzingrobot on 2014-11-02
There's no direct equivalent/copy of "My Computer" in Unity.  Clicking the "Details" icon in System Settings will show a broad overview. Note it also shows, and allows you to change, the default applications used for mail, music, etc.

The System Monitor tool displays total disk space and used disk space in its file system tab.  Tap the Super/Windows key and start typing "Monitor".

---

### Post by Bucky Ball on 2014-11-02
> **grahammechanical said:**
> 
Remember, the developers of Linux and all the software projects that make up a Linux distribution are not providing a cheap copy of some other OS. These developers have their own ideas on how a computer operating system should work and what it should look like. And that gives us freedom of choice.


Hear, hear. If Unity, the desktop environment that comes with the standard Ubuntu desktop edition, doesn't toot your horn, there are plenty of other desktop environments (DEs) you can try. lxde and xfce are much more like Win than Unity. You can run Gnome which would seem much more familiar. KDE and Kubuntu are more like Mac so I hear, but don't use either so can't comment.

Unity is not for everyone, but neither's any DE, but some love it. Depends how you want to work and what is most productive.

---

### Post by stalkingwolf on 2014-11-02
AS mentioned there are many DEs , I use and prefer Mate DE.  It has the computer icon you asked about.  and to make a short cut in mate either on the desktop or in the panel (tool bar)  you just right click the item in question and select add to desk top or add to panel.

It is done the same in several of the DEs.

---

### Post by craig10x on 2014-11-02
@ Bucky Ball: Actually, KDE and Kubuntu look more like windows....Unity Desktop is the most "mac-like" i'd say ;)

Since it has a dock (although on the left instead of the bottom of course), a top panel and global menu (which can be turned off in system settings)...
    As was pointed out, the unity launcher is really a shortcuts taskbar (also known as a dock...lol) so that is really where to put them...rather then the desktop itself...You will need to break some of those "windows habits"...

---

### Post by Bucky Ball on 2014-11-02
Ya live and learn. ;)

---

### Post by craig10x on 2014-11-02
Well, as you aussies like to say: no worries, mate :biggrin:

---

### Post by riverguy99 on 2014-11-02
Not sure if it's the same in 14.04 (I think it is), but in 12.04 you just click on your Home Folder (it looks like a file folder), then click on whichever drive you want the info on (disc space used and remaining).  Then right click, go down to "Properties," click, and there's your info.

To put any file/folder/app onto your desktop as a clickable icon, find the file/folder in your Home Folder, right click on it and then click on Make Link. Then right click on your new link and click on Move To, then select Desktop.

The right click option does so many things in Ubuntu!  Try it first for anything like what you are experiencing.  It's handy for copying files from one place to another, too.

BTW, after "upgrading" five computers to 14.04 and then living with many glitches, most of which are addressed on this Forum, I redid them all back to 12.04.  It's rock solid, still supported, needs no fixes, recognizes all our peripherals upon installation from a thumb drive and even configures the wireless card correctly.  It also works out of the box with two displays, another thing 14.04 will not do.

Food for thought if you have any ongoing issues with 14.04.

---

### Post by vasa1 on 2014-11-02
> **craig10x said:**
> .. those "windows habits"...
Not really limited to MS Windows. Several Linux users here who have been of great help to me over the years like icons, shortcuts, etc on their desktop. Live and let live :)

---

### Post by mastablasta on 2014-11-03
though I am getting used to kicker menu (in KDE) icons still tend to clutter my workspace. same like I have stuff on my desk at work. all over the place. yet I immediately know where is what.

---

### Post by Penguin360 on 2014-11-03
I think the OP is probably already overwhelmed by some of the replies.

---

### Post by phidia on 2014-11-03
I think [this]("http://www.howtogeek.com/163154/linux-users-have-a-choice-8-linux-desktop-environments/") could, hopefully be useful.  With so many options you probably can find something that will fit your needs.

---

### Post by JeQhdMD on 2014-11-03
Hello David,

As you can see, there are many ways to do this - - but the answer DEPENDS on what version of Linux desktop you are running.   In one of the versions . . called "KDE" (for K Desktop Environment) . . the short answer is:

1.   After you install a program, you find it listed somewhere in the Start Menu structure (VLC Player would be in the "Media" category for example),
2.  You just right mouse click on the program icon, and you'll get a popup window where one of the 3 or 4 options is to add the icon to the desktop . . 

Other desktops like "Mate" - - - "Cinnnamon" - - - "Gnome" - - - "Unity" - - - "XFCE" - - - "Fluxbox"  . . . . . and about another dozen not listed here all have slightly different ways of handling basic simple things like that.   

NONE of these basic desktop methods or techniques is Rocket Science . . . in other words, if you're clearly smart enough to set up a dual-boot with any version of Linux and any version of Windows 8, then, to find anything else out, just experiment and
goto a "YouTube" where all of these things are shown visually . .  Amazon is also a good source for Ubuntu handbooks (yea, old school but still good). 

By the way, in the default desktop for Ubuntu (Unity), there really isn't a need to populate your entire desktop with icons/shortcuts.   The shortcuts **ARE** **in **the "Launcher" - - the strip of icons on the left side of the screen is like an "accordion" of shortcuts, it's easy to add, remove, rearrange shortcuts by drag & drop operations.   The very top-left icon represents the search utility called the "Dash" . . . this lets you type anything in the search field and you get a flexible listing of icons or program shortcuts that you can apply filters to (see screen upper right quadrant), or goto the bottom of the screen and just click the "A" (applications) button and you'll see a listing of dozens of apps that can be started upon clicking, or can be dragged to the Launcher . . . voila . . . . there are your shortcuts!

Any, Penguin360 may be right, hopefully you're not overwhelmed, but you see in Linux there are MANY choices and methods . . . just take your time, keep a positive attitude, and you'll have a good time learning it!

PS:   here's how to check on your disk space in a manner similar to windows:  (just click on computer in the left pane of Nautilus (Files Manager), then right-click and select "properties" . . .

---

### Post by Penguin360 on 2014-11-03
> **david_huang2 said:**
> Hi, 
I have about 10 years using Windows.
Today is the first day I installed Ubuntu 14.0.4 over a laptop used to run Win 8.1 Pro.

There will be many questions to ask, but I'll start with 2.....
1. How do I make a shortcut to the desktop ?

2. How do I see "my computer" so that I know how much disk space  available ?

Thank you.

Since you are very new to Ubuntu, and just installed Ubuntu, I assume you are using the default desktop environment called Unity. At this moment, you don't need to bother too much about other desktop environment implementation. If you have an Android smartphone, then you know that different phone manufacturer use the same Android core but the UI is different and there are also some difference in functionalities. You can use this example to understand what a desktop environment is: different UI with some different functionalities build on the same core.

This being said, let's get back to your questions:
1. In Unity desktop environment, you are discouraged to add shortcuts  to the desktop. Instead you should add program icons to the launch panel on the left of your screen. First, click the Unity icon at the top left corner screen, then search for the program, once the program is launched, the program icon will appear in the launch panel. Then right-click the icon and choose **Lock to launcher**.

If you really want to add shortcut to the desktop, then you will need to follow the steps mentioned above. Or you can install and use a different desktop environment which enables this feature.

2. In the launch panel, click the File cabinet icon, then under Devices tab, you will see "Computer". Right-click "Computer" icon then choose Properties, it will show you how much space is available.

It is a big challenge to switch from Windows to Ubuntu and it will take a while to get used to the new world, but Ubuntu is very user friendly, so just give it some time and stick around here, you will be fine.

---

### Post by riverguy99 on 2014-11-03
Penguin360, you said, "1. In Unity desktop environment, you are discouraged to add shortcuts  to the desktop."  This is so true, and as a new user I was among the many ex-Windows users who started putting "shortucts" all over my desktop.  Until I learned how to use the Unity Launcher.  Now there are no icons on my desktop and everything is way easier to access through Unity than it ever was on my ultra-cluttered Wondows desktop.  Even my Lovely Bride, who when I switched her from XP to Ubuntu 12.04, was intimidated by the clean desktop and wondered how she was going to "find all her stuff."  Now she's much more comfortable without the clutter, and she loves clutter!

---

### Post by craig10x on 2014-11-03
Right...just think of the unity launcher as "the clutter free desktop solution" ;) :biggrin:
I love using unity...i do shrink the icons on the launcher down to 38 pixels for my desktop/laptop 17" screen...seems like the perfect size for me...

---

### Post by Bucky Ball on 2014-11-03
@JeQhdMD: Please attach large images rather than inserting them in your posts. Spare a thought for those with slow connections and/or vision problems. I have attached the pic [HERE]("http://ubuntuforums.org/showthread.php?t=2251099&page=2&p=13159114&viewfull=1#post13159114"). Thanks. ;)

---

### Post by /ADM on 2014-11-04
> **craig10x said:**
> Right...just think of the unity launcher as "the clutter free desktop solution" ;) :biggrin:
I love using unity...i do shrink the icons on the launcher down to 38 pixels for my desktop/laptop 17" screen...seems like the perfect size for me...

38px is perfect for me also.  Maybe we can get the devs to put it as the default size :)

---

### Post by Bucky Ball on 2014-11-04
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Apologies to david_huang2, if you ever return, but this thread has digressed and is now an off-topic chat (which can happen when the OP doesn't respond ;)) and not that relevant to your origianl support request (but of interest).

So best here. If you have a support request, please post with a descriptive thread title in a support section of the forum and incluce whatever info you think is relevant. Good luck.

---

