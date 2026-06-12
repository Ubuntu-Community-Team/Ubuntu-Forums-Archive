---
title: "My take on Ubuntu after a few days of using"
date: 2013-06-24
forum: Ubuntu, Linux and OS Chat
---

### Post by argvar on 2013-06-24
There are a lot of desktop usability issues in Ubuntu IMO. I do feel this is the best Linux end-user distro, but is a far cry from e.g. Windows or MacOs.

Here are a few issues, both usability, aesthetics and general linux issues:

1. Unity launchpad placement is awkward on the left. No possibility of moving the launchpad to bottom or customizing it in any manner.
2. Not possible rearrange the order of the icons in the Unity launchpad.
3. All instances of same application are stacked together, so it's not possible to select directly from the unity launchpad the instance you want.
4. Alt-tab disables the mouse.
5. Alt-tab stacks multiple instances of same application, so you need to first stop on the application for it to expand it...and even then the presentation is awkward.
6. Alt-tab does only show icons, but not live window capture.
7. Almost no possibility of customizing the look n' feel of the GUI. There are no alternative themes to select from, nor any way of modifying the theme easily.
8. Showing menu of an active application in the topmost bar makes no sense. I'd rather use that area for launch icons and move application menu to the application window.
9. Ubuntu does not help you install correct video card drivers after install.
10. Difficult to resize a application window, the border is too small. The resize cursor icons ugly.
11. The compact scrollbar is bad.
12. The toggle button is confusing.
13. Filesystem structure is confusing. You have no idea where an application is installed or things are.
14. Defaults fonts are not good enough. I switched to OpenSans. Some text on web pages looks awful, and I see lot of "clipping" and overflowing.
15. Not possible to minimize all windows except current, e.g. window-shaking like in Windows.
16. Inconsistencies in the UI. Try right-clicking in the web browser window, see how the context menu looks like. Then right-click on the desktop, and then right-click on a icon in the launchpad. 3 different look n' feels!
17. I feel like the UI is bulky, and that I have more space to work with in Windows.
18. Ubuntu does not help you discover nice tools to install, you need to know exactly what you want. There's also a lot of garbage in the software center.

Some can be fixed with tweak tools, but if I want to change anything more I feel like I need to spend a lot of time researching it, and do something I feel "hacky".

---

### Post by Toz on 2013-06-24
Since this doesn't appear to be a support request, moving to ***Ubuntu, Linux and OS Chat***.

---

### Post by Copper Bezel on 2013-06-24
Eh. A lot of this is just familiarity with Windows, and I imagine you'd have similar feelings trying OSX for the first time. Ubuntu is its own thing, and you can't expect it to work and think like Windows. Some of the complaints are warranted, and others are things that I personally don't really see as valid but that I've seen complaints about before even from long-time users. 

> **argvar]1. Unity launchpad placement is awkward on the left. No possibility of moving the launchpad to bottom or customizing it in any manner.[/quote]
Eh, you get used to it. Your mouse spends a lot of time over there anyway, so it's actually quicker to get to than the bottom bar. It does have the potential to get in the way, for the same reason. 

> 2. Not possible rearrange the order of the icons in the Unity launchpad.
Drag the icon outward, away from the launcher, then back in where you want it. 

> 3. All instances of same application are stacked together, so it's not possible to select directly from the unity launchpad the instance you want.
The Windows method, with the window previews, is so damned cluttered ... but there's no question that it's faster. I don't honestly use the Launcher for window switching - just Alt Tab and Compiz Scale, which is a plugin that works like Mac's Exposé.

> 4. Alt-tab disables the mouse.
5. Alt-tab stacks multiple instances of same application, so you need to first stop on the application for it to expand it...and even then the presentation is awkward.
6. Alt-tab does only show icons, but not live window capture.
One thing I really like about the 13.04 release is that they finally got the Alt+Tab switcher working properly. There are alternative switchers (more Windows-like) available in the settings, but this one finally at least does what I expect it to. Previously, it would switch applications outright, even if the previous window was another window in the same application, which made it useless to me. Now, just tapping Alt+Tab takes you back to the previous window regardless of whether it's in the same app or another. The grouped windows take a bit of time to get used to, but they certainly make for a cleaner, simpler presentation, and previews wouldn't make sense with grouped applications.

If you want to switch directly between windows in the same application, you can hit the key above Tab instead. 

> 7. Almost no possibility of customizing the look n' feel of the GUI. There are no alternative themes to select from, nor any way of modifying the theme easily.
There's a light theme in Appearance settings. There are also, of course, hundreds of themes available online. Modifying themes is trickier, although I'm just finicky enough to have to "fix" one or two things about any theme I install. I do still think the default theme is a little ugly, which is a very, very old complaint (and the theme is so iconic now that it would probably be a brand identity problem to make any major changes.)

> 8. Showing menu of an active application in the topmost bar makes no sense. I'd rather use that area for launch icons and move application menu to the application window.
17. I feel like the UI is bulky, and that I have more space to work with in Windows.
Which is a subjective effect - you don't - but an important one, I guess. The Launcher takes up as much space as the Windows taskbar if the taskbar is moved to one side, and the menu in the panel means that a maximized window is effectively full-screen, while the content areas of non-maximized windows are still as tall as they would be without a panel at all. Honestly, I think the damned theme has an effect here - that dark panel just seems so *heavy*.

The Launcher can be set to hide itself, again from Appearance settings, and that certainly helps the "boxed in" feeling.

> 16. Inconsistencies in the UI. Try right-clicking in the web browser window, see how the context menu looks like. Then right-click on the desktop, and then right-click on a icon in the launchpad. 3 different look n' feels!
The contrast between the Launcher menus and application menus is intentional and matches the contrast between the Launcher and the menu panel (along with the applications themselves.) It's a visual cue to distinguish between the application and the OS shell. The contrast between the smooth menus in some apps (including the file manager, which is the menu you see when you right-click the desktop) and the flat ugly ones in others is la-la-la technical BS as a result of recent changes to how windows are actually drawn - changes that started rolling in around 2011 and depend on application developers supporting the new standards.

> 9. Ubuntu does not help you install correct video card drivers after install.
18. Ubuntu does not help you discover nice tools to install, you need to know exactly what you want. There's also a lot of garbage in the software center.
It actually *should *prompt you about installing non-free video drivers. I don't have a lot of experience with this, but it worked the one time I had a non-Intel video card. (Intel cards just mostly work.)

> 10. Difficult to resize a application window, the border is too small. The resize cursor icons ugly.
11. The compact scrollbar is bad.
Eh, it led to a lot of arguments when it was introduced, but I think the hidden scrollbar is enough for those cases where you actually need a scrollbar, like jumping to a particular point in a document. It pains me to see Windows users pecking at the little arrow buttons on the scrollbar. I think the idea is that any pointing device made in the last five years has either a scroll wheel, a scroll region, or two-finger scrolling, so it's less important to have a scrollbar (at least until you need it) and more important to have an indication of where you are in the document. Personally, I like the edge-to-edge content.

It's also not remotely as fiddly as those damned resize areas. For about two glorious releases, Ubuntu used Mac OSX Aqua's neat little triangular grab handle superimposed onto the bottom right corner of all windows for resizing and no borders at all. No fat borders, nice, big click target said:**
> 15. Not possible to minimize all windows except current, e.g. window-shaking like in Windows.
A very neat little feature I'd love to have, but like the Mac OSX grab handles, just an odd little thing another OS does. It's not a common enough feature to *expect *it in a random OS. So far as I know, only Windows does this. You *can *do it in two steps with the window switcher - Alt+Tab to the desktop, then tap Alt+Tab once more. A workaround, but if you're going for "focus mode," it's probably worth the extra step.

More to the point, in Linux broadly, it's more common to move to a fresh workspace (desktop) when you want to focus on something. If you haven't tried workspace switching, try it out - it's the weird little button with the "cross" in it on the Launcher. Hit that, drag your window to an empty space, and then click that workspace to follow it. Very nice for getting away from the clutter, and it also means you don't have to dig back through minimized windows later to pick up where you left off.

> 13. Filesystem structure is confusing. You have no idea where an application is installed or things are.
Also true of an iPhone or Android, and for the same reasons. There's no reason to need to know where applications store their files in Ubuntu. They're usually spread out over a bunch of system folders, but you don't interact directly with that stuff anyway. That's what the package manager (Software Center) is for. In Windows, it sometimes makes sense to just download an executable file (the program itself) and run it from wherever you put it, but that's not how Linux works. All applications are handled through the package manager, which means that they won't leave files around when you remove them and always stay updated.

> 14. Defaults fonts are not good enough. I switched to OpenSans. Some text on web pages looks awful, and I see lot of "clipping" and overflowing.
Weird. What browser?

> 12. The toggle button is confusing.
The toggle button widget in some of the settings screens, or something else?

---

### Post by Megaptera on 2013-06-24
Have you tried Xubuntu, Kubuntu or Lubuntu? Their layouts might suit you, or look at changing to perhaps Mate or Cinammon DEs, you might be more comfortable with them.

---

### Post by argvar on 2013-06-25
Thanks for a great reply Copper Bezel!


> Eh, you get used to it. Your mouse spends a lot of time over there  anyway, so it's actually quicker to get to than the bottom bar. It does  have the potential to get in the way, for the same reason.
Perhaps.
I find the answer "you get used to it" really not satisfactory, but seems to be the default here. I can't believe this important issue is perceived as a trivial usability issue that does not really matter... this is the biggest most visible usability feature of the OS, the launchpad, and they don't think users don't want to customize this any differently than they WANT?
It's really frustrating in two ways, first the placement itself and then the ignoring of the issue by ubuntu like it's trivial and doesn't matter. The only trivial thing here is allowing users to place it at bottom! This reminds me of arguing with a unix troll, who does not care about end users needs, like arguing with a rock trying to convince it that people are different and have different perceptions and needs, the unix troll always refuses and says nothing can be changed. This is putting some pre-determined design above the needs of the end user. This simple thing just proves how far Linux still has to go before being considered a proper end-user consumer desktop OS.

Frankly I see more emphasize put on useless visual features, that serve no usability purpose.

> Drag the icon outward, away from the launcher, then back in where you want it.
Great! Thanks :)

> There's a light theme in Appearance settings. There are also, of course,  hundreds of themes available online. Modifying themes is trickier,  although I'm just finicky enough to have to "fix" one or two things  about any theme I install. I do still think the default theme is a  little ugly, which is a very, very old complaint (and the theme is so  iconic now that it would probably be a brand identity problem to make  any major changes.)
I'd like to try out more themes, but I don't know how to get them. Ubuntu doesn't help with that, although it's probably one of the few things new users start to tinker with.

> Which is a subjective effect - you don't - but an important one, I  guess. The Launcher takes up as much space as the Windows taskbar if  the taskbar is moved to one side, and the menu in the panel means that a  maximized window is effectively full-screen, while the content areas of  non-maximized windows are still as tall as they would be without a  panel at all. Honestly, I think the damned theme has an effect here -  that dark panel just seems so *heavy*.

The Launcher can be set to hide itself, again from Appearance settings, and that certainly helps the "boxed in" feeling.
Usually the bar at the top is 90% blank, with a few icons at the right and the title at the left. This is a total waste of space. The windows taskbar almost fits in that area, and has much more options than the unity launcher. The windows taskbar shows you start button, application shortcuts, current application tabs, icons and date. Much more variety, much more compact.
How ubuntu has it cuts both into your vertical screen real estate and horizontal screen real estate, effectively reducing your desktop size. Having two windows side by side is not possible with the unity launchbar. Either the windows are too small or the left window goes under the unity bar.
Anyway, I have a lot of opinion about this. I just feel Ubuntu doesn't give you any choice... when it should!

> Also true of an iPhone or Android, and for the same reasons.  There's no reason to need to know where applications store their files  in Ubuntu. They're usually spread out over a bunch of system folders,  but you don't interact directly with that stuff anyway. That's what the  package manager (Software Center) is for. In Windows, it sometimes makes  sense to just download an executable file (the program itself) and run  it from wherever you put it, but that's not how Linux works. All  applications are handled through the package manager, which means that  they won't leave files around when you remove them and always stay  updated.
I hated how files were managed by Windows, they were scattered everywhere, program files, appdata, roaming, local files, users, registry stuff etc. etc. I want applications to be contained in one place. You never knew where to find your files.
But the linux file structure is just strange. You have so many directories in the root. I have used linux for a long time and I still don't know what the difference is between /var and /opt or /lib and /sbin or whatever. Why don't they just put everything os related into /system and application related into /apps... oh well whatever. This is like fighting with a unix troll :) Change is always bad in their mind.


Anyways, thanks for the feedback.

---

### Post by 3rdalbum on 2013-06-25
You need to use Ubuntu for longer. Most of your points are completely inaccurate, or demonstrate that you haven't explored your operating system yet.

---

### Post by craig10x on 2013-06-25
I suspect you might be using firefox...i use Google Chrome and have the microsoft fonts installed (in the software center if you didn't have them installed with ubuntu restricted extras...
also, as a personal preference, i go into font settings and kick the 3 tabs up to 18 pts (from 16 pts which is the default) looks fabulous to me :D
Could not get Firefox to look as good (when the fonts default is turned off and you set your own)...

While it might be nice if ubuntu had the option of putting the unity dock on the bottom, because of it's large size and the very common wide screens today, it kind of makes sense to have it on the left side and "auto-hidden"...i also reduce the size of icon's pixels to 38 as i like them smaller on my home (laptop) 17" screen...of course, when a small screen is used it's probably better to keep them at the default...

Hey, my friend has an IMAC and he puts his mac's dock on the left side....

---

### Post by sanderj on 2013-06-25
> **3rdalbum said:**
> You need to use Ubuntu for longer. Most of your points are completely inaccurate, or demonstrate that you haven't explored your operating system yet.

Bravo! Well said.

---

### Post by Copper Bezel on 2013-06-25
I certainly don't mean to seem argumentative. There *are *reasons behind some of the things you're complaining about, though. 

> I find the answer "you get used to it" really not satisfactory, but seems to be the default here. I can't believe this important issue is perceived as a trivial usability issue that does not really matter... this is the biggest most visible usability feature of the OS, the launchpad, and they don't think users don't want to customize this any differently than they WANT?
It's not non-controversial - a lot of long-time users have problems with it, too, and there have been many rants and bug reports and feature requests. I kinda thought while I was typing it that "you get used to it" probably wasn't the best way of putting that, as well - I guess I mean that there's a logic to it, once you get the hang of it. 

I honestly think that the decision to make it fixed to the side like that is a brand identity consideration, based on that same "visibility" and centrality you're referring to. 

> Frankly I see more emphasize put on useless visual features, that serve no usability purpose.
Arguably, moving the Launcher is just that. 

For more visual themes, though, see here:

[http://gnome-look.org/index.php?xcontentmode=167](http://gnome-look.org/index.php?xcontentmode=167)

Most of them require a couple of steps to install. After you download the theme archive, you'll create a folder in your home directory called .themes (the dot makes it a hidden folder, which you can see by hitting Control+H) and copy what's inside the archive into that folder. Then, you'll need to install Tweak Tool from the software center to switch between themes. Notice that they come in two parts - normally, the theme will include everything you need, but there are two separate settings in Tweak Tool, "Current Theme" and "GTK+ Theme," that both need to be set.

Icon themes work similarly, in a folder called .icons. Might play around with those, as well.

> Usually the bar at the top is 90% blank, with a few icons at the right and the title at the left. This is a total waste of space. The windows taskbar almost fits in that area, and has much more options than the unity launcher. The windows taskbar shows you start button, application shortcuts, current application tabs, icons and date. Much more variety, much more compact.
Eh ... what version of Windows are you talking about here? The application shortcuts have been folded into the running applications for quite some time now, and the Start menu just left. The last version that worked the way you're describing is Vista. = / Change is not always bad, as you say.

Variety is not really a good thing here. The idea is to keep related things together.
 
The right side of the Unity panel has all the same stuff as the right side of the Windows taskbar. The left side is the application menus instead. If the menu wasn't up there, the application window would have the menubar inside it, which would be the same 20-pixel cost in vertical screen real estate. So, again, when a window isn't maximized, it can display exactly as much vertical content as if the panel wasn't there, and when it *is *maximized, the vertical screen space is the same as if it didn't have a titlebar. In Windows, the taskbar, menu bar, and titlebar are all separate, so in absolute terms, there *is *more space available in Ubuntu, by about sixty pixels. Again, it can subjectively feel "cramped", especially if the Launcher isn't set to hide, but that's separate from the objective description of the actual space used.

> How ubuntu has it cuts both into your vertical screen real estate and horizontal screen real estate, effectively reducing your desktop size. Having two windows side by side is not possible with the unity launchbar. Either the windows are too small or the left window goes under the unity bar.
Anyway, I have a lot of opinion about this. I just feel Ubuntu doesn't give  any choice... when it should!
Well, again, you do have the choice of making the Launcher hide, and then it doesn't take up any screen space at all. I can't stand having the Launcher visible at all times. To be fair, the compact scroll bars help, too. 

> I hated how files were managed by Windows, they were scattered everywhere, program files, appdata, roaming, local files, users, registry stuff etc. etc. I want applications to be contained in one place. You never knew where to find your files.
But the linux file structure is just strange. You have so many directories in the root. I have used linux for a long time and I still don't know what the difference is between /var and /opt or /lib and /sbin or whatever. Why don't they just put everything os related into /system and application related into /apps... oh well whatever. :) This is like fighting with a unix troll  Change is always bad in their mind.
File paths for Windows applications weird me, no question. I'm used to Linux, where there's a system, and it's totally arbitrary, but the apps at least follow it, as opposed to just doing their own damned thing. At least the executables and their configuration data are kept properly separate. 

I'm not claiming that the Linux directory structure out in root makes sense in a human-usable way, certainly from a user's standpoint. There's just no reason to go out there. = ) There have actually been some attempts to propose a better system, but it stays the way it is for compatibility. Should point out that there's not a strict line between apps and system components, though, especially on Linux.

---

### Post by HiImTye on 2013-06-25
if you want to find a programs files you have a few options.
```
whereis <package>
dpkg -L <package>
```
or to search for a specific file
```
locate <regex>
find / -type f -iname <regex>
```
as for what the folder names mean
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

if you don't like the layout of Unity, you should give GnomeShell, LXDE, XFCE, Cinnamon, MATE, Gnome-Fallback, etc a go. there are more than enough DEs with different design philosophies in mind. better still, you could skip a DE and design a 'you' desktop from the ground up starting with just a window manager. with Linux, your possibilities are limited only to your willingness to learn and experiment.[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by sanderj on 2013-06-25
> **argvar said:**
> 
Perhaps.
I find the answer "you get used to it" really not satisfactory, but seems to be the default here. 

IMHO it has to do how you write your questions and opinions: as facts. "xyz doesn't work / abc is confusing". This post and your other posts more look like the start of an argument. 

If you write things like questions ("how does xyz work"), you probably get more help. 

HTH

---

### Post by beautifulcoder on 2013-06-25
The launchpad on the left is Canonical showing that they understand design. Take a look at your machine. Notice it's wider than it is vertically longer? Exactly.

---

### Post by treb0r on 2013-06-25
> **sanderj said:**
> IMHO it has to do how you write your questions and opinions: as facts. "xyz doesn't work / abc is confusing". This post and your other posts more look like the start of an argument. 

If you write things like questions ("how does xyz work"), you probably get more help. 

HTH

I totally agree with this sentiment and find it hard understand why / how people are willing to come across as so arrogant when talking about an operating system that has been provided to them for free.

I myself was an early Ubuntu user who drifted away. After years using a Mac I'm back and I'm very impressed with how things have developed over the last few years.

We can argue about interfaces and unity until the cows come home but the basic advantages of Ubuntu for me are freedom and control. That is true of most GNU/Linux distributions but Ubuntu provides them with the polish and professionalism usually associated with more commercial, binary only operating systems.

Congratulations Mr Shuttleworth on a bold vision well executed. I expect we will be seeing a lot more Ubuntu in the mainstream over the coming years.

---

### Post by sanderj on 2013-06-25
... and in the meantime the OP argvar has continued his rant in his new threads.

[http://ubuntuforums.org/showthread.php?t=2157383](http://ubuntuforums.org/showthread.php?t=2157383)
[http://ubuntuforums.org/search.php?searchid=2149431](http://ubuntuforums.org/search.php?searchid=2149431)

... ignoring this thread he started.

So I'll put him on my ignore list. And I'll ask the forum admins to join threads.

---

### Post by malspa on 2013-06-25
@argvar - With all the "issues" that you mentioned, isn't it curious that so many people (including myself) actually *like* (and even *love*) using Ubuntu (and Linux)? Maybe the "issue" isn't Ubuntu or Linux. Just a thought.

---

### Post by deadflowr on 2013-06-25
The real question should be, what's wrong with microsoft and apple? As they have far far more developers and programmers designing their desktops, and yet their's are, at best, moderately better.
With the resources they have, shouldn't their stuff be utter awesomeness?
Why aren't they?

---

### Post by argvar on 2013-06-25
> **deadflowr said:**
> The real question should be, what's wrong with microsoft and apple? As they have far far more developers and programmers designing their desktops, and yet their's are, at best, moderately better.
With the resources they have, shouldn't their stuff be utter awesomeness?
Why aren't they?

Thank you! This is pretty much my entire point. Here you have two of the world's largest software makers, creators of the world's two most popular human/computer interfaces, have large teams of dedicated user interface experts and the world's top designers, and it's like nobody in the Linux world wants to borrow from them.
There's a reason why so many 3rd party look n' feel themes out there try to mimic them.

>  			 			The launchpad on the left is Canonical showing that they understand  design. Take a look at your machine. Notice it's wider than it is  vertically longer? Exactly. 		 
This is a naive argument. "Understanding design" is just one part of the puzzle, other parts include user convenience, requirements and preference, usability, customization, etc. etc. The fact you cannot even move the launchpad is evidence enough they do not understand.

It surely is a strange argument claiming that the monitor is wider and thus has more space if you'd align a panel vertically! Let's put aside the fact that you know best and have taken away the choice from the end user.
After just 2 days of using Ubuntu this unity launchpad is almost full of icons, on a 1080p display, and I've made the icons the smallest they can be set to. And yet I haven't even started to install all my applications. There are two things here:
- Not able to have application icons elsewhere. So you end up cluttering the launchpad with application icons you rarely use, just because there's no other place for them.
- Vertical space is only 1080 pixels while horizontal space is 1920 pixels, you have 77,8% more space for icons if the panel was at bottom.
- Having the panel at left interferes with application windows and takes away workspace area.




Ubuntu is still by far the best desktop environment solution. I've looked at probably a dozen distros that have been recommended but all give me the feeling that no attention was given to the small aesthetics and overall design of the look n' feel. I notice these things and they bother me, since I'm a graphics designers myself. I don't know why others don't see this, but whenever I use an interface that is clumsy aesthetically I notice, but others seem just fine with it and notice nothing.
It's like whenever someone raises this issue... well that someone always feels like he's come to a community of color blind people while he's trying raise the point of bad color selection. Arguing about it is pointless.

---

### Post by deadflowr on 2013-06-25
You missed my point entirely.

But I'll bite on the issue of why linux developers don't "borrow" from ms and apple.

They don't "borrow", or more commonly known as stealing, from ms or apple because linux is built upon a foundation of ethics.
Something neither microsoft nor apple have.:)

---

### Post by Bashing-om on 2013-06-25
@argvar...
xfce4; fully customize-able in any way that you have the simple skill to edit a config file or download a "theme" someone else wrote and made it available to the general populace....
You do not like something in 'buntu ? ... you have access to the source code... write your own !

[INDENT][INDENT]defending ubuntu, our operating system by choice[/INDENT][/INDENT]

---

### Post by Cheesemill on 2013-06-25
> **argvar said:**
> Not able to have application icons elsewhere. So you end up cluttering the launchpad with application icons you rarely use, just because there's no other place for them.

The launcher is only meant to be used for frequently used applications, you can launch rarely used applications from the dash.

---

### Post by lykwydchykyn on 2013-06-25
Not to pick on you, argvar, but I find it funny that you say Ubuntu is the best Linux distro for new users, but almost every criticism you give is a problem unique to Unity and thus Ubuntu.  Almost none of them are issues if you use KDE, GNOME, Cinnamon, Enlightenment, etc.

As for the filesystem, it's ugly, but it's based on the Unix standard filesystem layout.  It may not be intuitive, but on the plus side important parts of the filesystem aren't moved around willee-nillee every release like they are on some OS's I could mention.

---

### Post by monkeybrain2012 on 2013-06-25
His "new users" don't really mean "new users", but old Windows users who are very set in Windows' way but new to Linux. They tend to judge Linux based on how much it resembles WIndows. The complaint about File system is a case in point. I almost expect him to complain that Linux doesn't have a registry. :)

---

### Post by argvar on 2013-06-26
> **monkeybrain2012 said:**
> His "new users" don't really mean "new users", but old Windows users who are very set in Windows' way but new to Linux. They tend to judge Linux based on how much it resembles WIndows. The complaint about File system is a case in point. I almost expect him to complain that Linux doesn't have a registry. :)

I never liked how Windows did things. I hated the fact files were scattered throughout the file system, you never knew where things ended up, either in a hidden appdata, in some obscure users directory, program files of course. The registry is really retarded IMO. So your accusation here is a total fail.

If I install an application I want its files and everything related to it to be contained, isolated, in the same directory. If I delete an application I don't want to worry about some remnant files, I want to simply be able to delete one directory and everything to it is gone.

Having the config files in /conf/ and binary files in /bin/ and data files in /var/ really is retarded. And you don't have just one /bin/, you have /usr/bin/ etc.

I whole heartily agree with this guy: [http://unix.stackexchange.com/questions/14709/is-the-linux-directory-structure-obsolete-and-obtuse](http://unix.stackexchange.com/questions/14709/is-the-linux-directory-structure-obsolete-and-obtuse)

I know this is legacy stuff, but hey come on, it's 2013, nobody has the balls to change this? The only truly successful open-source distributions of an OS are the ones proprietary companies like Apple and Google have adopted and drastically modified. Google has more apps created for Android every month than desktop Linux has available. Just saying this because I know some people might think that change is always bad, when in fact it enables everyone else to break out of a cage created by code gurus 20 years ago.

You know there are legitimate reasons why a lot of people shy away from Linux. Fussing at those who raise points in that regards will not help Linux.

---

### Post by mastablasta on 2013-06-26
> **argvar said:**
> If I install an application I want its files and everything related to it to be contained, isolated, in the same directory. If I delete an application I don't want to worry about some remnant files, I want to simply be able to delete one directory and everything to it is gone.
.


i think one of BSD versions has something like this. or they jsut have the option to get all packages along. hmmm i forgot that one. as i just read about it once.


anyway i think the structure makes sense. because what if you run a server? you would then do what? block access to directory and in such way block access to server itself?

besides you can always see which files are uninstalled. software center is taking care of cleaning and such for you. there is also apt-get. and if you checked a bit you would notice that programmes share their dependencies. it often happens in windows as well. so in your suggestions each programme would have to come with it's own dependencies. meaning the size of the programmes and disk space take would increase (unnecessarily). heh imagine multiple websites on server each running their own server.... anyway i have Xubutnu on a 8GB virtual drive. still with about 1,5GB left i think. when i checked preinstalled win7 starter it took about 30 GB i believe. and better version of this OS take even more disk space. you might think that hard disk is cheap nowadays, but check the price of server disks. and let's not even mention how that disk space occupied with OS just keeps on growing and growing...

then again if that is what you want the code is open.

i do agree there is a lot of Garbage or 10th rate programmes in software center. there are also some old non-working programmes there. having 30.000 packages means notnign as there is much much less programmes. there are also PPA's and external sources. some external sources have the programmes like you want them. in single folder.

---

### Post by Copper Bezel on 2013-06-26
[QUOTE=argvar][COLOR=#000000]If I install an application I want its files and everything related to it to be contained, isolated, in the same directory. If I delete an application I don't want to worry about some remnant files, I want to simply be able to delete one directory and everything to it is gone.[/COLOR][/QUOTE]
The file manager isn't the package manager; there's no reason to have to delete the files manually. When you remove a package, it's gone; the package manager keeps track of all the files it installed. Some files for some programs also *have* to be in system folders; after all, installing a calculator app, installing a library that's shared across all applications, and installing a kernel module are all tasks that use the same package manager, and again, there's not really a clear dividing line between "system" programs and "applications." 

There's a further problem in that if you *did *have a big folder of all the applications, you'd need to decide who owns it. If it's in the user's data directory, then the user could delete programs, sure, but only that user could run them, and they'd need to be installed individually for each user. If it's a shared folder for the system, then the applications could run under any user account, but an individual user still couldn't delete one without jumping through hoops. 

Further complication: if the applications are shared across all user accounts, you *still *need a folder within the user's personal storage for configuration options, just as there is now. (Of course, there's a reason that applications are kept separate from their configuration files, too - partly, it's just because the application is shared by all users on a system while the configuration files are not, but one particular advantage is that the user can revert the configuration to "factory spec" without uninstalling and reinstalling the program.)

There's a reason why there's a package manager and why everything goes through that.

Edit: Ooh, but if we can mandate that all applications store user-specific config in a folder under ~/.config/whatever, instead of some going there, some going to ~/.whatever, and some going to ~/.local/share/whatever or ~/.local/share/somesillymadeuppath/whatever, that'd be awesome.

---

### Post by Gnawnsense on 2013-06-26
One size doesn't fit all. This guy is obviously looking for something that Windows already provides. Case closed. Don't feed the trolls.

---

### Post by TNFrank on 2013-06-26
I came over to Ubuntu 12.04LTS from Mac OS X 10.3.9 and felt right at home in a day or two. Out of all the op systems I've previewed on Live USB stick Ubuntu 12.04LTS seems to be the one I like best. 
 If you want more of a "Windows" feel you can get a KDE Desktop with Kubuntu and it'll be more like Windows OS. There's so many different version of "Ubuntu" with Lubuntu, Xubuntu, Kubuntu, Linux Mint, PeppermintOS ect that I'm sure you can find something that'll make ya' feel warm and fuzzy. Besides, they're FREE so you can give em' a try without spending a dime which IMHO is totally awesome.

---

### Post by beautifulcoder on 2013-06-26
> **argvar said:**
> "Understanding design" is just one part of the puzzle, other parts include user convenience, requirements and preference, usability, customization, etc. etc. The fact you cannot even move the launchpad is evidence enough they do not understand.

I respectfully disagree. Locking down the design shows Canonical is confident enough in their decision that they feel they can guide you in the right direction. I believe there is a fallacy in customization in that software that attempts to be "everything to everyone" ultimately fails. The reason being is that no software developer can code for the infinite number of ways people will end up using the end product. This means users who end up using edge case features will ultimately end up getting hurt. So, by writing opinionated software you are making a statement on how your software should be used. I believe designers know better about using their own software than end users. Turns out, IMHO, Canonical is 100% right! I love Ubuntu precisely because the UI stays pretty much out of the way of my content. It is like one day I suddenly woke up and realized, hey, I just want to get my stuff while having all the OS chrome crap completely out of the way. Yea, it was a bit jarring and weird at first, but I get it, it is absolutely brilliant the way it is done in Ubuntu. Now, if I'm ever on Windows or Mac OS X I move the bar to the side where it should be.

> **Cheesemill said:**
> The launcher is only meant to be used for frequently used applications, you can launch rarely used applications from the dash.

Exactly! It is called a launchpad for a reason. I usually put no more than five which is a hard limit my humble brain puts on managing clutter. Everything else, I get to it when I get to it, so that is why there is a dash.

---

### Post by buzzingrobot on 2013-06-26
You can put all the files that support one application in a single directory on a very simple OS like DOS. But, once you have an OS of even modest capability, libraries will be written that offer support to any app.  Those  libraries must exist in an indepedent location, where they won't be removed inadvertantly.  Ditto configuration files that must be available to all users on a system. Hence, /etc. (Much naive criticism of the Unix/Linux filesystem stems from unawareness that Unix and Linux are multi-user systems, designed to allow multiple users to log on simultaneously.)

Fedora, etc., have merged most executables in one folder.

---

### Post by craig10x on 2013-06-26
I have 10 myself on the unity launcher (dock) but i also removed some of the apps i don't use, like ubuntu one and amazon...They are favorites and fairly frequently used apps...the rest that i rarely use, i just open dash search and get it there...A launcher/dock is not for putting on 100 app of which you probably only use a handful frequently anyway...even on a windows style slab menu, most people only put a small group of apps on, and use search for the rest...that's a pretty common practice...

---

### Post by Skara Brae on 2013-06-26
> **Copper Bezel said:**
> Eh, you get used to it.
I am being sarcastic now, but I've read someone saying the exact same thing about Windows 8 - one just "has to get used to it".

Is that what OS's have become about: "having to get used to it"?

That is not the way it should be. I should not have to "get used" to an OS. It is the OS that should have to be the way that I want, and not the other way around.

I thought that was _the_ biggest argument for switching to Linux: one can configure it any way one wants. But more and more, this is no longer true. Ubuntu has Unity, and if you don't like that, "get used to it", period. (Or get KDE, or LXDE, or xfce, or whatever.)

After I accidentally deleted my Ubuntu partition last year, I didn't bother reinstalling it (end of support was in April anyway) and I switched to Linux Mint. I don't like Unity and I most certainly don't want to "get used" to it. I tried Fedora 17, but I find Gnome 3 as terrible as Unity, so Fedora was out after 1 day - I didn't give it a change, some/many will now think/say? Again, why do I have to "get used" to an OS/desktop/window manager? I don't buy/acquire things and then "get used" to them for a certain amount of time first. I get them because I like them the way they _are_, period. It has to be the other way around: not the OS is in charge of my computer, but I am.

I am sorry, Canonical, but you have lost a passionate "lover" of Ubuntu. Linux Mint is fine, but Ubuntu (10.04) was the greatest OS I have ever had (Windows 95-7; MacOS X). It was stable, everything worked, and Gnome 2 was extremely user-friendly (talk about (old) KDE 3, on the other hand...). I loved Ubuntu. Ubuntu really used to "rock". It doesn't rock any longer. :(

It is my personal opinion that Canonical has ruined Ubuntu in teh same way that Microsoft has ruined Windows with "Metro" (in Windows 8).

I miss Ubuntu 10.04/Gnome 2.

Just my 2 cents.

> **3rdalbum said:**
> You need to use Ubuntu for longer. Most of your points are completely inaccurate, or demonstrate that you haven't explored your operating system yet.
See? 3rdalbum, you are saying: "Get used to it".

---

### Post by HiImTye on 2013-06-26
> **buzzingrobot said:**
> Fedora, etc., have merged most executables in one folder.

Arch just moved them all to /usr/bin
[https://wiki.archlinux.org/index.php/Arch_filesystem_hierarchy](https://wiki.archlinux.org/index.php/Arch_filesystem_hierarchy)

> **argvar said:**
> If I install an application I want its files and everything related to it to be contained, isolated, in the same directory. If I delete an application I don't want to worry about some remnant files, I want to simply be able to delete one directory and everything to it is gone.
you can manually install any package to any folder, but you lose the ability to have the package manager automagically handle them

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by craig10x on 2013-06-26
Different strokes for different folks, skara brae...you loved the old ubuntu layout and i hated it...in fact, it drove me to linux mint...i returned to ubuntu when unity arrived because i loved the new desktop layout...
having 2 panels taking up a lot of real estate and a spread out apps menu with no search is not what i would call efficient...ubuntu with unity is what i call efficient...

---

### Post by Skara Brae on 2013-06-26
> **treb0r said:**
> I totally agree with this sentiment and find it hard understand why / how people are willing to come across as so arrogant when talking about an operating system that has been provided to them for free.
What, you mean one mustn't whine about it, because one already gets it for free?

> **treb0r said:**
> I myself was an early Ubuntu user who drifted away. After years using a Mac I'm back and I'm very impressed with how things have developed over the last few years.

We can argue about interfaces and unity until the cows come home but the basic advantages of Ubuntu for me are freedom and control.
What freedom and control, if I have to get used to Unity (or get another DM or distro)?

> **treb0r said:**
> That is true of most GNU/Linux distributions but Ubuntu provides them with the polish and professionalism usually associated with more commercial, binary only operating systems.

Congratulations Mr Shuttleworth on a bold vision well executed. I expect we will be seeing a lot more Ubuntu in the mainstream over the coming years.
No comment...

-oo-

I don't want to sound "arrogant" or anything. After having used it since 2007, I am "just" disappointed in where Ubuntu has gone to, that is all.

---

### Post by monkeybrain2012 on 2013-06-26
> **argvar said:**
> 

If I install an application I want its files and everything related to it to be contained, isolated, in the same directory. If I delete an application I don't want to worry about some remnant files, I want to simply be able to delete one directory and everything to it is gone.
.

Yeah as a result your installation will be huge because each application comes with its own duplicated version of libraries. Without even considering Windows, look at some proprietary software (native Linux) that bundles all their libraries. Their size run into a few Gs as a result. Usually they do have all their stuffs in one folder so you can just delete it, but that is because they are not integrated into the system so the package manager cannot see them. Otherwise, WHY would you even want to delete programs manually? (only "pieces" you need to know where they are so you can  delete them  manually are configuration files in you home. Typically in .config but some may have their own "." files. But you don't have to delete them, you can just leave them be.)

I find the way Linux organizes the file system makes a lot of logical (programming) sense, even though it may not make sense to the human user. The OS organizes files in terms of their logical functionalities and how they link to each other, whereas the user thinks of a software as one piece to do some "high level" tasks which seems easy to understand to the humans but too ambiguous for the machine (hence the difficulties of AI)   But since those low level details are taken care of by the package manager it doesn't have to make intuitive sense to you (and also Linux is designed as a multiuser system by default, so in that setting the normal user doesn't even have access to those things)

The only situation where your complaint makes sense is when you use  make install to install a program from source, then the files get scattered in the file system and they are not seen by the package manager, they are not  easy to remove if the program doesn't come with a uninstall script. But this is more of a problem of the people who distribute the program than Linux and there are some workarounds like using checkinstall (or actually build the deb) so that the package manager can detect the installed files.

---

### Post by Skara Brae on 2013-06-26
> **argvar said:**
> I never liked how Windows did things. I hated the fact files were scattered throughout the file system, you never knew where things ended up, either in a hidden appdata, in some obscure users directory, program files of course. The registry is really retarded IMO. So your accusation here is a total fail.
I find the way Windows does thing quite logical (let me not start about _*how*_ it does thing...). System files in /Windows, program files in /program files, user files in your own home folders.

The Windows registry replaced the dozens of .ini files from Windows 3.x (I don't call this better, I am only comparing the Windows registry with the .ini files from the 'old days').

> **argvar said:**
> If I install an application I want its files and everything related to it to be contained, isolated, in the same directory.
They all are in the same directory - Program Files. The Windows files that a program uses - like dll files - are found in the Windows system directory (/windows). I find that quite logical.

> **argvar said:**
> If I delete an application I don't want to worry about some remnant files, I want to simply be able to delete one directory and everything to it is gone.
First part is true... very often remnants stay behind, which is (probably) the result of bad programming.

> **argvar said:**
> Having the config files in /conf/ and binary files in /bin/ and data files in /var/ really is retarded. And you don't have just one /bin/, you have /usr/bin/ etc.
config files in /conf and binaries in /bin is retarded? :p Are you serious?

Seriously. I know little about why the directories in Linux (and UNIX) are the way they are. I assume there are logical reasons for those. UNIX has its origins in the 1960s. The UNIX programmers probably used reasons that they found logical (like binaries in /bin and config files in /conf :p )

> **argvar said:**
> I know this is legacy stuff, but hey come on, it's 2013, nobody has the balls to change this?
"If it ain't broken, don't fix it." Linux and UNIX (and OS X) work, don't they? So, why change them?

> **argvar said:**
> The only truly successful open-source distributions of an OS are the ones proprietary companies like Apple and Google have adopted and drastically modified.
That kind of success has nothing to do with how those OS's are built, but all about marketing (and FUD, in Microsoft's case).

And you haven't you seen the directory structure of Android, have you?

> **argvar said:**
> Google has more apps created for Android every month than desktop Linux has available.
I know nothing about programming, but I do know that you can not compare an Android app with a Linux program. An Android app is much "easier" made than a Linux program (if it weren't, then all Linux devs must be idiots, while all Android app writers are geniuses.)

> **argvar said:**
> You know there are legitimate reasons why a lot of people shy away from Linux. Fussing at those who raise points in that regards will not help Linux.
The fact that people shy away from Linux has nothing to do with the points that you mention.

---

### Post by monkeybrain2012 on 2013-06-26
> **Skara Brae said:**
> I find the way Windows does thing quite logical (let me not start about _*how*_ it does thing...). System files in /Windows, program files in /program files, user files in your own home folders.

.

"Logical" to you is not the same as logical in an architectural and programming sense. Humans are not very logical overall, most would not find advanced mathematics very "logical". Hence the difficulties of AI. :)

---

### Post by Skara Brae on 2013-06-26
> **craig10x said:**
> Different strokes for different folks, skara brae...you loved the old ubuntu layout and i hated it...in fact, it drove me to linux mint...i returned to ubuntu when unity arrived because i loved the new desktop layout...
having 2 panels taking up a lot of real estate and a spread out apps menu with no search is not what i would call efficient...ubuntu with unity is what i call efficient...
People's tastes are hard to understand sometimes: the other week, I read someone saying that he loves Windows 8. They'll proverbially have to pry Win XP (Yes, I've an old computer with XP still on it) out of my proverbial cold dead hands, before I'd ever start using Windows 8. Windows 8 is an abomination - just look at those Youtube clips of people that use Win 8 the first time (I don't really consider myself an idiot, and I wouldn't know how to use Windows 8 either, if I hadn't seen such clips first.)

But you are right that we cannot argue about people's taste. Everyone's taste is valid. I liked Gnome 2, you like Gnome 3. That is how it is and there is nothing wrong with it.

---

### Post by Elfy on 2013-06-26
This whole thread is about the different ways that different people look at things.

Once again we have a thread eating it's tail.

These issues come up regularly - they rarely change,

Thread closed.

---

