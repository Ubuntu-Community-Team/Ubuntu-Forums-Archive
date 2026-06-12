---
title: "Apple Human Interface Guidelines... an example to follow or to avoid?"
date: 2008-03-30
forum: The Cafe
---

### Post by the8thstar on 2008-03-30
Hello all,

I used a friend's Mac for a couple of days and the overall experience was interesting. I now know that buying a Mac is a ridiculous idea, but yet I feel that Aqua is very nice in many aspects.

I checked the Human Interface Guidelines for Aqua ([http://developer.apple.com/documentation/UserExperience/Conceptual/OSXHIGuidelines/XHIGInstallationsUpdates/chapter_10_section_3.html#//apple_ref/doc/uid/TP40002722-CJACABIA]("http://developer.apple.com/documentation/UserExperience/Conceptual/OSXHIGuidelines/XHIGInstallationsUpdates/chapter_10_section_3.html#//apple_ref/doc/uid/TP40002722-CJACABIA"))

I was especially attracted to the "Drag-and-Drop" installation features. I know we use .deb packages, Synaptic or Update Manager on Ubuntu, but it looks like an interesting concept. Other interesting snippets I found:

Designing Icons for Icon Buttons ([http://developer.apple.com/documentation/UserExperience/Conceptual/OSXHIGuidelines/XHIGIcons/chapter_15_section_9.html#//apple_ref/doc/uid/20000967-SW5]("http://developer.apple.com/documentation/UserExperience/Conceptual/OSXHIGuidelines/XHIGIcons/chapter_15_section_9.html#//apple_ref/doc/uid/20000967-SW5"))

System-Provided Images ([http://developer.apple.com/documentation/UserExperience/Conceptual/OSXHIGuidelines/XHIGIcons/chapter_15_section_10.html#//apple_ref/doc/uid/20000967-SW15]("http://developer.apple.com/documentation/UserExperience/Conceptual/OSXHIGuidelines/XHIGIcons/chapter_15_section_10.html#//apple_ref/doc/uid/20000967-SW15"))

These guidelines bring a strong visual unity to the desktop. Do any of the requisites mentioned in Apple's document have their counterpart in Ubuntu? Are they developed by Ubuntu, Gnome, KDE... or else? I don't mean to make a point, just to open the discussion.

**Comments welcome**. :)

---

### Post by mcduck on 2008-03-30
You might be interested in Gnome's own Human Interface Guidelines as well: [http://library.gnome.org/devel/hig-book/stable/]("http://library.gnome.org/devel/hig-book/stable/")

edit: I have a mac as well, and I've actually been quite disappointed in lack of unity in it's interface. Mixing all those Cocoa, Aqua, Carbon and Metal interfaces in applications makes the desktop visually inconsistent. I had to get a 3rd-party application to get the interfaces between different programs to look the same..

Also OS X doesn't really support different themes for applications or icons, so they do not need to worry about different icon sets and application themes and the ways how using them affects the desktop interface. That should make developing consistent interfaces quite easy, but I can't really say that it would show in reality..

---

### Post by the8thstar on 2008-03-30
Thank you **mcduck**. Very interesting and thorough read.

Two ideas:

[B][I][COLOR="Blue"]1. I wonder if there could be a way to enable a drag-and-drop install script by dragging a package (.deb, .rpm, .gz, .gz2) to the Ubuntu icon in the menu bar?
2. If we type a package name in the search bar, it would automatically look for it in Synaptic and offer to install it if available in the repos.[/COLOR][/I][/B]

What do you guys think of that?

---

### Post by mcduck on 2008-03-30
I think the first idea might make sense when the .deb package actually contains application, but as packages could also contain other things (that won't actually go to the Applications-menu) this could me more confusing than useful.

For the second idea, which search bar do you mean? If you mean the deskbar applet, that would actually be a nice idea. But doing that from file manager or web browser's search bar would once again make things more confusing, search in file manager should search for files, and search in web browser should search from the web. Neither one of these should search for programs.

We actually have the apt-protocol for web, which allows installing applications from repositories by clicking a link on a web page. And I think Firefox in Ubuntu comes with Ubuntu's package search included by default, so if the packages.ubuntu.com had apt-links for the packages as well you could actually search for a program in Firefox's search bar, that would take you to packages.ubuntu.com where you could view information about the package and then click a button to install it. But I'm not quite convinced that this would make installing programs any easier for beginners than what the Add/Remove-thing in the Applications-menu is.

---

### Post by the8thstar on 2008-03-30
*> I think the first idea might make sense when the .deb package actually contains application, but as packages could also contain other things (that won't actually go to the Applications-menu) this could me more confusing than useful.*
The other things (I asume you mean dependecies for instance) could be taken care off by the system without bothering the user, except for popping up a dialog box that would saying something like this: "*In order to perform correctly, this program requires that I install dependencies (xxx...) on your system. Do you agree?"* And why not include an invisible compiler to install apps from the source when they are not available anywhere else. 

*> For the second idea, which search bar do you mean? If you mean the deskbar applet, that would actually be a nice idea.*
Yes, this is what I meant. Vista has considerably widened the use of the search bar, and so has OSX, so I'm strongly advocating for a similar move in Linux. To make things a little more sensible, search results could be broken into categories (file systems, audio, .deb packages, etc.). [COLOR="Blue"]**LESS TINKERING, FASTER WORK**[/COLOR].

I think that little steps like this can greatly help potential new users who are afraid to toy with the SYSTEM. More advanced users are of course welcome to bend the system to their will with the command line.

---

### Post by mcduck on 2008-03-30
> **the8thstar said:**
> 
The other things (I asume you mean dependecies for instance) could be taken care off by the system without bothering the user, except for popping up a dialog box that would saying something like this: "*In order to perform correctly, this program requires that I install dependencies (xxx...) on your system. Do you agree?"* And why not include an invisible compiler to install apps from the source when they are not available anywhere else. 

Actually i mean any packages that aren't graphical programs that actually got to the Applications-menu. Like installing lame or w32codecs.

In case of programs that _do_  go to the applications menu it of course makes sense to drag&drop the package there.

I haven't used the Deskbar applet after it's interface changed from a bar in the panel to a button that opens a new window, but I suppose adding the package search/install feature to the applet should not be hard to do. And yes, I agree that the search results should be categorized better, more like the independent Search tools for both Tracker and Beagle do.

I actually belong to that group of people who believe that it's a good thing that Ubuntu doesn't even come with compiler installed by default..

In the end there's also the question of how many different ways of doing the same thing we really need, and how many can we add before the mere amount of different ways of doing the same thing makes the task more confusing and complicated than it really is ;)

---

### Post by the8thstar on 2008-03-30
Good points.

> I actually belong to that group of people who believe that it's a good thing that Ubuntu doesn't even come with compiler installed by default...

In the end there's also the question of how many different ways of doing the same thing we really need, and how many can we add before the mere amount of different ways of doing the same thing makes the task more confusing and complicated than it really is.

Well, the reason I'm advocating for (yet) another way to do things is because I want to make life easier for newbies and for seasoned users who just want to enjoy their computer without having to tinker with the guts of the system for an app, a driver, a configuration file, etc. Apple sell out their "Human Interface" because it's very easy and sensible. And easy doesn't mean lazy in my book when we are talking about end user productivity. Spending hours configuring Grub, iptables, or font rendering in OpenOffice is fun, but it is not productive or user-friendly.

I know this is somehow another wishful thinking. Apple and Microsoft are corporations, with set strategies, whilst Linux is a "software movement" (if that even applies). It is easier for the two former to set and enforce rules about their GUI and homemade WM according to their choices. In the meantime, Linux has several WM alternatives, hundred of distros based on different versions of the kernel, with different packages systems (.deb, .rpm, .tar) and +100,000 swiss-army-knife programs living anywhere between v0.01 and v12.0. This is the very nature of Linux by definition: chaos and flexibility.

The genius of distromaking companies is that they are able to bind and organize this galactic mess into a legible, usable form. I'm just posting to advocate for a little bit more order and ease of use without killing creativity.

---

### Post by geoken on 2008-03-30
I don't see the advantage of dragging a .deb to some specified area. I don't think it's any simpler than  double clicking said file (or single clicking depending on your settings).

IMO, a .deb is recognized as an installer. I think for most people, it's more logical that an installer is initiated (like a regular application) than moved to some arbitrary location. 

If there was some special archive that was used for apps which didn't need any installation (ie. portable style apps) then I think the drag and drop idea might make more sense since that archive would be recognized as a self contained application (like .app files on OS X)

---

### Post by vvlist on 2008-03-30
Its not that you "drag an app to a specified place to install it" thats cool about OSX, its the fact that you can temporarily "mount" programs like a drive thats cool about OSX. Its very handy on public computers that don't have the program you need. It's really the only thing Macs have that Linux does not that I actually desire. I do realize that with a lot of tar.gz packages I can just run the executable inside, but its not really the same.

---

### Post by perce on 2008-03-31
You could drag and drop programs in Linux too, if they are compiled with the libraries statically linked. Don't ask me what it means, I only know that if I download skype with libraries statically linked I can put it in a USB memory stick and run it from there, and I don't have any dependencies problems.

---

### Post by SomeGuyDude on 2008-03-31
What's funny is that I never saw how the "drag and drop installation" thing was even remotely useful.

I've used Macs, Windows, and Linux, and I have to say that by FAR the most efficient and convenient installation method for software is Synaptic. I look up a neat piece of software and read "it's in the repos" and I'm good to go. Don't need to worry about anything. Plus I'm guaranteed updates. And then there's the dependencies business.

I think Apple has a great way of making things look generally "clean" and "polished", but honestly I have NEVER understood why everyone calls the Mac experience so much simpler than anyone else's. Sure if you take a while to get used to it, you'll... get used to it. But for an interface to be able to claim it's simpler or more user-friendly, the learning curve should be nonexistent and OSX definitely has a BIG one (to this day I despise the "MacMenu" global toolbar thing).

---

### Post by Mazza558 on 2008-03-31
Well, with AWN, I found a nice little feature today (I don't know if it's universal)

You can drag images into the GIMP icon to open that file, which is pretty cool.

---

### Post by Lord Illidan on 2008-03-31
Personally, I'll take a package manager over drag-and-drop any time.

You can search for packages, and most importantly, updates are timely and guaranteed to be secure.

As for the .deb file, personally I think double click is less work than drag-and-drop.

And for other programs you need to install by the compiling method, call me a stickler for old habits, but the terminal is the best method, I think. And, come on, it's not hard at all.
./configure; < Check for any dependencies that have been left out> - note, in Ubuntu I end up checking far more than in Arch Linux, as the devel files are included with the libs in the latter.
make, make install.

A thoroughly terrific program would be one that parses the ./configure, automatically install dependencies, and does the make and make install thing for you.

But again, drag and drop? No.

As to the OSX icons, they're nice, but I like the Tango theme more... :D

---

### Post by LaRoza on 2008-03-31
> **perce said:**
> You could drag and drop programs in Linux too, if they are compiled with the libraries statically linked. Don't ask me what it means, I only know that if I download skype with libraries statically linked I can put it in a USB memory stick and run it from there, and I don't have any dependencies problems.

Statically linked means the libraries the app needs are not dynamically linked, in other words, it has everything it needs all in one. This will increase the size. For a dynamically linked program, it wouldn't have the library with it. (If you install a KDE app on Ubuntu, it will also install some KDE and QT libraries, because they are dynamically linked to them)

> **Lord Illidan said:**
> Personally, I'll take a package manager over drag-and-drop any time.

But again, drag and drop? No.


I agree, the drag and drop is an easy thing to do, but considering how bloated and wasteful it can be, a good package manager is better.

---

### Post by Lord Illidan on 2008-03-31
> **LaRoza said:**
> Statically linked means the libraries the app needs are not dynamically linked, in other words, it has everything it needs all in one. This will increase the size.


It has its advantages - 1st of all portability and ease of use, but it also contributes to high RAM requirements as libraries are loaded multiple times.

---

### Post by qazwsx on 2008-03-31
Does OS X have same kind of drag and drop feature as Konsole in KDE? :)

---

### Post by rev7 on 2008-03-31
As a long time Mac user, I just wish Apple would follow their interface guidelines.  Since the departure of Arlo Rose and the release of OS X, Apple has been all over the board.

The Apple terminal app does support drag and drop, but it isn't terribly useful.  The Mac's focus has always been the GUI.

One of my favorite features of Ubuntu is the Synaptic Package Manager.  At first it may seem more complicated than the Mac way of doing things, but the ability to browse thousands of packages, install them and remove them from a single app is a dream come true.  Very easy.  I wish I had this capability on my Mac!

Cheers!

---

### Post by aysiu on 2008-03-31
Drag and drop puts too much strain on the muscles near your wrist, as you have to carefully place your mouse over an icon, hold down the mouse button for the period of dragging while also aiming your pointer to the drag destination, at which point you finally release your mouse button.

Add/Remove is far less of a strain, as you just type in the search box and click once on a checkbox and then click again to confirm you want to apply the changes.

In terms of interface design, I've heard a lot about this supposed Fitt's Law, and I'll concede that using corners can be helpful sometimes, but there are usually more than four places you want to place your mouse, and really the mouse is barely usable from that standpoint. People are constantly shifting their mice back and forth and demonstrating its imprecision for every task. The best interface takes advantage of the keyboard and keyboard shortcuts.

I assure you can I press my terminal-launching keyboard shortcut and type ```
sudo apt-get update && sudo apt-get install *packagename* -y
``` much faster than any Mac user can find, download, double-click, and drag and drop an application into the Applications folder... and with far less strain on my wrist.

---

### Post by SomeGuyDude on 2008-03-31
ALSO, as a note:

Dragging and dropping on a touchpad is about the least convenient thing in the world. It's not AS bad with a mouse, but try and quickly drag and drop something on a pad without using two hands.

---

### Post by the8thstar on 2008-03-31
**Lord Illidan** 
> A thoroughly terrific program would be one that parses the ./configure, automatically install dependencies, and does the make and make install thing for you.

Now THAT sums up with I had in mind. Thanks for putting it into layman's terms, Lord Illidan. That would be a big plus for any users. I thought of drag-and-dropping it, but any double click would do. I'm not a zealot. For those who want total control, there's always the console.

Overall, I'm quite happy to see that my thread has started a little bit of a debate. I don't agree with everything that was said, but just the discussion itself is a good indicator that my thoughts have echoed somewhere. :)

Personally, I tried Mac but I realized that it's not really for me. The Mac interface is yet another learning curve, so I'll pass. And I don't like the bar either, like **SomeGuyDude**. I guess people praising Macs are either ignorant about Linux or maybe I'm ignorant about something groundbreaking with Apple products. :confused:

---

### Post by SomeGuyDude on 2008-03-31
8thstar, sometimes I get the feeling that Apple users get more wrapped up in the "hip factor" of Apple products than in trying to find what works best.

Apple has become the brand of the well-to-do younger adult who's got his thumb on the pulse of the nation and rejects the status quo (the Apple slogan was "think different" at one point, right?). Unfortunatey, none of that has anything to do with it being BETTER, with a few exceptions (iPhone, the original iPod, etc).

---

### Post by SunnyRabbiera on 2008-03-31
well its something to follow I think, at least to attract new users.
If linux is ever to become as popular as windows or OSX it needs more graphical tools and add ons to make people want to use it.
I think there should be a more GUI way of compiling applications that are not in the repo's, I think there should be GUI tools for enabling more repositories and getting people used to the system.
The terminal jockeys might disagree but the less newbies see of the terminal the better, that way we can let them learn at their own rates as opposed to forcing command line down peoples throats.

---

### Post by aysiu on 2008-03-31
People are welcome to disagree with me, but this is my general take on Apple's approach to user interfaces:

1. **Every choice seems deliberate and well thought-out.** I don't *agree* with all the choices made, but I can at least see what they were trying to go for. I can see that they have a vision and layouts, interactions, and looks are not haphazard.

2. **Apple focuses on beauty over substance, and that's what matters to most people. **Yes, I've seen a number of Linux users on forums claiming that they hate the Mac look and think Aqua is ugly, but these are the only instances I've seen this sentiment expressed. Everyone I know in "real life" thinks Macs look awesome, even the die-hard Windows users (who usually justify not switching to Mac as being too expensive, too trendy, or not supportive enough of "real work" with Windows-only applications).

My wife personally hates the Mac interface, but she loves Macs because they look cool. That's it. Seriously. She hates the dock. She hates Spotlight. She doesn't take advantage of all the features I think are cool (Time Machine, universal inbox in Mail, etc.).

3. **Some of Apple's choices aren't good ones for usability**. This is kind of a combination of #1 and #2. Dragging and dropping to the trash to eject a drive may seem cool to those who think it looks cool, but it actually makes no sense from a usability standpoint. Nor does dragging items off the dock to have them vanish in a puff of smoke. Cutting and pasting by drag and drop (or even right-click context menu) appears to be impossible. I think you have to drag and drop while holding some key in order to cut and paste instead of copy and paste. Zooming isn't as useful as maximizing, especially since you have to manually re-zoom every time your view requires itself to be bigger and since most people perform only one task at a time. Cmd-Tab switches by application and not window. It also does not restore minimized windows. You can resize only by the bottom-right corner, even if the Dock is blocking it. I could go on about Apple's bad choices, but I won't, since Mac users seem to not mind these choices... or not mind them enough to get them to stop using Macs.

---

### Post by SomeGuyDude on 2008-03-31
"Gloss over substance, for twice the price" is the Apple business model and always has been. They market to morons with bigger bank accounts than brains.

Why do you think their ads touted "features" like a magnetic power cord or no need for a virus scanner? Their target users are idiots who use their computers irresponsibly and can't be trusted to avoid kicking the plug.


I realize "no viruses" is a Linux perk as well, but it's FAR from the reason I switched. I never got a virus in Windows either.

---

### Post by mcduck on 2008-03-31
> **SunnyRabbiera said:**
> well its something to follow I think, at least to attract new users.
If linux is ever to become as popular as windows or OSX it needs more graphical tools and add ons to make people want to use it.
I think there should be a more GUI way of compiling applications that are not in the repo's, I think there should be GUI tools for enabling more repositories and getting people used to the system.
The terminal jockeys might disagree but the less newbies see of the terminal the better, that way we can let them learn at their own rates as opposed to forcing command line down peoples throats.

There already _is_ a gui tool for adding new repositories, but even that can't change the fact that you still need the actual repository address which is text (New repositories can be added from the same place where you can enable/disable Ubuntu's own repositories), and the key which is also text. So even with a GUI tool adding repositories includes copypasting strings of text.. Of course different repositories could be already included, ready to be enabled like Ubuntu's own repositories are, but that would make Ubuntu responsible for those repositories as well as it's own which is pretty much 
out of the question..

And what comes to new users, I don't think they should be compiling anything at all.. Actually I don't think even I should be compiling anything at all.. :D

BTW, I agree that OS X isn't nearly as easy or intuitive to use as it's reputation would suggest. When I got my mac I needed to open the terminal on the very first day to fix some problems, and also make a script to disable screen dimming and startup sound (as OS X's own tools just fail to work on my iMac.. I'd say that having to write your own scripts just to keep your display from dimming in the middle of movies is quite far from the easiness Apple promises. And the fact that finding information about ho to do these things is insanely harder than with Linux makes it even worse..

I still have some problems with my Mac that I haven't been able to solve because there are no GUI tools for fixing them, and hardly any information about how to do them from terminal.. (For example, Inkscape and all other X11 apps have decided to run using Finnish language even when my system language is English, and I haven't found any way to change this.)

One other good example about the not_so_intuitive_or_logical ways of OS X is the way of unmounting diks and disk images by dragging them into Trash.. r the obscure key combinations used for screenshots.. You really need to know the ways of OS X to figure these things out, new user's definitely won't pick them up intuitively.

And apt-get/Synaptic sure is better way to install and update programs than the images used on Macs. Just the task of keeping my apps up-to-date takes lots of work to do on OS X while in Ubuntu I don't really need to do anything as it all just happens automatically :)

I don't think that blindly copying features from other operating systems would make Linux any better. It's better to figure out the best way to do something than to copy something just because people using other operating systems might be used to do things that way.

---

### Post by aysiu on 2008-03-31
> **SomeGuyDude said:**
> "Gloss over substance, for twice the price" is the Apple business model and always has been. They market to morons with bigger bank accounts than brains. While that may be their target audience, I don't think that would be a fair characterization of all Mac users. I couldn't think of a better operating system for my wife, for example, as she is a professional designer who needs Adobe CS (InDesign, Photoshop, Illustrator) and Flash for work, and she hates Windows. Wine, a workaround anyway, still can't do CS3 properly.

> Why do you think their ads touted "features" like a magnetic power cord or no need for a virus scanner? Their target users are idiots who use their computers irresponsibly and can't be trusted to avoid kicking the plug. Again, excuse me if I take this a little personally... we were very glad to have replaced my wife's Powerbook with a Macbook Pro, and the magnetic power cord was one of many reasons. Those people you call *idiots*? That's me. I tripped over her power cord on the Powerbook and ended up damaging the input part of it. Now that her Macbook Pro's power cord is magnetic, when I trip over it, there's no harm done.

Not everyone is physically coordinated. Some of us are clumsy "idiots."

---

### Post by mcduck on 2008-03-31
> **aysiu said:**
> While that may be their target audience, I don't think that would be a fair characterization of all Mac users. I couldn't think of a better operating system for my wife, for example, as she is a professional designer who needs Adobe CS (InDesign, Photoshop, Illustrator) and Flash for work, and she hates Windows. Wine, a workaround anyway, still can't do CS3 properly.

+1 for this.

Mac is pretty much the industry standard in multimedia and design, and being able to run programs like Photoshop, Illustrator, Flash, Final Cut, Motion and Logic is pretty much a requirement for working in these fields. Even when I actually prefer using Gimp and Inkscape I simply must have these programs available to be able to work with different companies and print houses.

If that makes me a moron with small brains then I suppose I prefer being a small-brained moron.

---

### Post by SomeGuyDude on 2008-03-31
**aysiu**, don't take my generalizations too personally. I'm not gonna apologize for them, but I don't mean them in the kind of "you, you sir are an idiot and should be ashamed of yourself" kind of way. They market to idiots, whether or not that comprises the entirety of their consumer base.

On your first point that's software. Fair enough. It has zip to do with the system itself, only what runs on it. Sort of like saying Windows is a good OS because it has games.

On the second, I realize accidents happen and it can be a convenient little perk, one of those "hey neat" kind of things. However, what does it tell you when that's a centerpiece of an ad campaign? It's not that I think it's a bad idea (although, honestly, I can't say I've EVER done that while sober and I haven't owned a desktop since 2003), but I think making it central to your marketing sends a none-too-subtle message that you don't think your customers are the brightest bulbs on the tree.

Ya dig?

---

### Post by mgmiller on 2008-03-31
Personally I think our own deskbar applet is one of the most under appreciated features of Ubuntu.  Any time I show it to a windows user, they are impressed.  Alt/F3 and type anything.  If it's a name in your address book you can send an email, you can run commands, get definitions in dictionary, look stuff up in wikipedia or google or yahoo, etc.etc.

---

### Post by bobbybobington on 2008-03-31
I think there is no doubt that certain aspects aren't as great as the fanboys/girls may make apple design out to be, you have to admit they do put a lot of time and thought into their design and interface. Ubuntu does have a good interface and it is probably underappreciated, but IMO many linux apps seem to think about the interface after the fact. This is probably a function of their community's priorities, but it can cause problems for users who expect a certain amount of quality in the interface.

We can debate the specifics of the apple interface/design all day, but I think the important lesson to get from apple is the importance of putting time and priority in interface and design. Ubuntu and linux in general is very good on the nuts-and-bolts level, and it has served us well, but we can't ignore the importance of polish and attention to details as well.

Celeste Lyn Paul's [blog]("http://weblog.obso1337.org/") touches this subject on the project level, and is very interesting. Definitely worth the read.

---

### Post by LaRoza on 2008-03-31
> **bobbybobington said:**
> I think there is no doubt that certain aspects aren't as great as the fanboys/girls may make apple design out to be, you have to admit they do put a lot of time and thought into their design and interface. Ubuntu does have a good interface and it is probably underappreciated, but IMO many linux apps seem to think about the interface after the fact. This is probably a function of their community's priorities, but it can cause problems for users who expect a certain amount of quality in the interface.


It should be different people doing interface and function.

I know I skimp on interface, and do it last if at all.

---

### Post by cardinals_fan on 2008-03-31
Avoid, I beg you.  As for drag-and-drop, ROX certainly takes the concept to heart (perhaps a bit too much so).

---

### Post by tawsi on 2008-04-03
> **Lord Illidan said:**
> Personally, I'll take a package manager over drag-and-drop any time.

You can search for packages, and most importantly, updates are timely and guaranteed to be secure.

As for the .deb file, personally I think double click is less work than drag-and-drop.


Why do a package manager and drag-and-drop have to be mutually exclusive? 

 I really like the package management system for the reasons you describe. However, for applications that are not part of the core repository, when newer versions are wanted or a user wants to try something out this won't work. You end up having to either compile your own packages, not exactly straightforward for the vast majority of computer users or use 3rd party repositories, at which point the benefits of package management you mention may go out the window. Plus you need to be in admin to manage packages otherwise you are left compiling stuff into your home dir.

Drag-and-drop is great for individual applications when a user just wants to try something out. On OS X I download a dmg, open it and drag the application somewhere, which I find easy enough on a trackpad one handed,  and can then start it with a double click or using quicksilver. This works great when I want to try out an application. When I want rid of an application I just delete the folder and it goes away, except for the stuff in my home dir but I'd have the same problem with stuff installed with apt. However, it does have issues, theres wasted space since applications have their own copies of non-apple  libraries inside them so you end up with duplication. It also isn't good for development files which typically require an installer or have to explain to a user where to put them.

Both systems have their advantages and disadvantages, it would be nice to see a combination of the two. I guess Klik does this but it isn't directly supported by most applications so user have to wait for klik to build it. Mozilla applications from their site are almost drag and drop since they'll typically run happily from the folder you download them to.

---

### Post by koenn on 2008-04-03
> **LaRoza said:**
> It should be different people doing interface and function.

I know I skimp on interface, and do it last if at all.
That's the traditional unix way : you have a program doing whatever it's supposed to do, and then, if you really have to, you paste a gui on top of it. 

Mac apps are designed 'outside in" (or so I've read) : You design the user interface first, so all interface elements are where the user will want/expect them to be, and behave the way the user expects them to behave, and then you add the code that makes the program do what it should be doing.

Competely opposite styles.

---

### Post by the8thstar on 2008-04-12
> That's the traditional unix way : you have a program doing whatever it's supposed to do, and then, if you really have to, you paste a gui on top of it. 

Mac apps are designed 'outside in" (or so I've read) : You design the user interface first, so all interface elements are where the user will want/expect them to be, and behave the way the user expects them to behave, and then you add the code that makes the program do what it should be doing.

Competely opposite styles.

@ **koenn**:How about the middle way, Linux-like? Programs first and a UNIFIED interface afterwards on top. I thought the Window managements programs we use (Gnome, KDE, XFCE, Enlightenment, etc) were meant for that.

@ **all**: Drag-n-drop is a nice feature that could facilitate things IMO. If compiling a program consists in typing stuff like "sudo, make, install..." and all that jazz, why not replace it? I'm not saying that the CLI should be replaced altogether in any way however.

---

### Post by koenn on 2008-04-12
> **the8thstar said:**
> @ **koenn**:How about the middle way, Linux-like? Programs first and a UNIFIED interface afterwards on top. I thought the Window managements programs we use (Gnome, KDE, XFCE, Enlightenment, etc) were meant for that.

@ **all**: Drag-n-drop is a nice feature that could facilitate things IMO. If compiling a program consists in typing stuff like "sudo, make, install..." and all that jazz, why not replace it? I'm not saying that the CLI should be replaced altogether in any way however.

make and all that jazz is in fact an intelligent, flexible, unified way of compiling source code and installing the resulting program. It's used for source code, not for installing compiled, binary programs. You're comparing apples with orange trees.

Desktop environments such as Gnome indeed offer some integration and attempt to create some sort of unified user experience, but it's not always possible : not all applications are designed to have their user interface customized by window manager / DE themes

---

### Post by the8thstar on 2008-04-13
> make and all that jazz is in fact an intelligent, flexible, unified way of compiling source code and installing the resulting program. 

I agree with you... because that's just the way it works. The drag and drop idea is not meant to eradicate it, but to make it easier on noobs like me. Personally, I think that having to type 3 lines in the CLI instead of 1 operation is _**stupid**_. There could/should be a command that does it in one line only. Why doesn't it exist? Can Alien be a good candidate?

> It's used for source code, not for installing compiled, binary programs. You're comparing apples with orange trees.

By binary, you mean .deb packages? If you mean .bin, I know I can already double-click them if I set the permission to 'Allow executing file as a program' in Nautilus.

---

### Post by koenn on 2008-04-13
> **the8thstar said:**
> I agree with you... because that's just the way it works. The drag and drop idea is not meant to eradicate it, but to make it easier on noobs like me. Personally, I think that having to type 3 lines in the CLI instead of 1 operation is _**stupid**_. There could/should be a command that does it in one line only. Why doesn't it exist? Can Alien be a good candidate?



By binary, you mean .deb packages? If you mean .bin, I know I can already double-click them if I set the permission to 'Allow executing file as a program' in Nautilus.
I suppose you could wrap a script or so around ./configure and make so you'd have to only type one command ... That's not the point. You're looking at the drag-and-drop mechanism that Apple uses to install programs. the Linux equivalent is something like Synaptic (GUI package manager) or apt-get (command line package manager). Alien is a tool to install redhat style rpm packages on a debian style system that expects .deb packages.
 ./configure and make are for source code - Apple doesn't distribute source code so the comparison doesn't make sense.

---

### Post by the8thstar on 2008-04-13
Sorry for the mistake between .rpm packages and source code, I'm still ignorant about a lot of things in regard to Linux. You're right, Alien is indeed used for .rpm, not source.

So... I guess I have to push my point a little further and break it down into two parts:

1. Source code: can a file be installed in a double-click like a .bin or .deb package instead of the CLI method? If yes, how? If not, why?

2. Drag and drop: how about enhanced features such as Apple's ability to drag an image to paste it into an email? Has it been done? I don't use Evolution since I can't import my Yahoo! account info, so if it's already functional, I have no idea!

---

### Post by UK-sHaDoW on 2008-04-13
> **LaRoza said:**
> It should be different people doing interface and function.

I know I skimp on interface, and do it last if at all.
Not really lots of computer sci course do HCI modules.

Which is all about user interface design. 
All the design techniques to makes them useable etc

---

### Post by mgmiller on 2008-04-13
> 2. Drag and drop: how about enhanced features such as Apple's ability to drag an image to paste it into an email? Has it been done? I don't use Evolution since I can't import my Yahoo! account info, so if it's already functional, I have no idea!
__________________

Thanks for the idea.  I never tried it before, but I just discovered it does work just fine in evolution.  I will be using that feature from now on.

---

### Post by saulgoode on 2008-04-13
> **the8thstar said:**
> I agree with you... because that's just the way it works. The drag and drop idea is not meant to eradicate it, but to make it easier on noobs like me. Personally, I think that having to type 3 lines in the CLI instead of 1 operation is _**stupid**_. There could/should be a command that does it in one line only. Why doesn't it exist? 

**./configure && make && sudo make install**

^^ One line :)

The reason configure and make are not combined into a single operation is that a change in configuration demands that the every file in the package be recompiled -- performing a make only recompiles files that have been modified. This is very important to those working on a project since a full recompile might take an hour while a "remake" might only be a minute or so. 

The install is specified separately because the user might not wish to actually install the program. He may wish to test the result before installing it to his system or perhaps wish to build a package (.deb, .rpm, .tgz, etc). 

One could combine the multiple commands into one , and provide switches to specify the various options; but that boils down to a matter of syntax and doesn't really alter what needs to specified (it would actually limit the flexibility of the system). 

The build mechanism of a project's source code is determined by that project. If a distro wishes to provide that source code in a different format, it is their task to do so -- in fact, this is the basic function of "distros", providing binary builds of source code (Debian, Red Hat, Suse, Slackware,...) or a modified build mechanism (Gentoo, Arch, BSD,...). 

Upstream project's are not going to standardize on a single approach (even the GNU build system described is not ubiquitous); and having compilation being "newb-friendly" is not a particularly high priority when compared to other criteria such as debugging, cross-platform functionality, and reducing development times.

---

### Post by Chelidon on 2008-04-13
> BTW, I agree that OS X isn't nearly as easy or intuitive to use as it's reputation would suggest. When I got my mac I needed to open the terminal on the very first day to fix some problems, and also make a script to disable screen dimming and startup sound (as OS X's own tools just fail to work on my iMac.. I'd say that having to write your own scripts just to keep your display from dimming in the middle of movies is quite far from the easiness Apple promises. And the fact that finding information about ho to do these things is insanely harder than with Linux makes it even worse.

I would like to know how to do that!

By the way, I've been using Kubuntu for the past few months and have n't gotten very used to the command line. That's not to say I haven't used it to good effect. I installed some printer drivers and lm-sensors, configured my Wacom tablet and fixed my sound. I have to say that of all of the things I've encountered in this system the package manager is by far the coolest feature. I wish more systems would use something similar! (The closest I guess was Apple's software updater that we had on our big, old Gateway, but we only used that to reformat our iPods when they went on the fritz). 
I've run into OSX's weirder keyboard commands just trying to do something simple like Grab. I was about ready to smash something by the time I figured it out. I think Apple's gone a little nuts with some of the features in Leopard, and while some of them are neat (Time Machine, etc) some of them I thoroughly dislike for their shallowness (gumby, wiggly menus in the dock, 7 more pages in Photobooth). By the way, you can probably tell that I don't really care for Compiz, especially since I trapped myself using it once and had to have my Linux guru kill my GUI.

---

### Post by the8thstar on 2008-04-13
**MgMiller**

> Thanks for the idea. I never tried it before, but I just discovered it does work just fine in evolution. I will be using that feature from now on.

Too bad I can't use my Yahoo! account in Evolution... I'm glad it works for you.


**saulgoode**

> ./configure && make && sudo make install

^^ One line 

Point taken. I understand the need for separation better now, and although its implications are beyond my understanding (I'm not an IT professional, just a computer enthusiast and an obsessive tweaker) I appreciate the fact that you took the time to put it in layman's terms for me.

> One could combine the multiple commands into one , and provide switches to specify the various options; but that boils down to a matter of syntax and doesn't really alter what needs to specified (it would actually limit the flexibility of the system).

Maybe this could be helpful for END-USERS like me, who don't plan to use the program for development, but solely to 'use' it. I do understand that there are more urgent priorities though.

> Upstream project's are not going to standardize on a single approach

All reasons set aside, I think it's a shame somewhat because it certainly doesn't make Linux more appealing to the Windows user. I still wish there was more unification.

---

### Post by mgmiller on 2008-04-13
> Too bad I can't use my Yahoo! account in Evolution

Have you checked out this thread?  It discusses using yahoo with evolution:
[http://ubuntuforums.org/showthread.php?t=662808]("http://ubuntuforums.org/showthread.php?t=662808")

I see from your signature that you may not be in the US.  Perhaps that's why it doesn't let you configure yahoo mail for pop access.

---

### Post by Mr. Picklesworth on 2008-04-13
On the thought of drag & drop, it's a really cool piece of functionality. It is essentially a rapid technique to integrate applications without thinking about it. You tell a widget it is draggable, attach a URI to it when it gets dragged (eg: Path to an image file), and needn't think about anything else. From that point, any app set up to receive dropped URIs can handle it.
My theory is that every application should implement dragging and dropping of everything possible, and then the world will be a happier place :)

---

### Post by 3rdalbum on 2008-04-14
Drag and drop is great, when you're talking about opening documents, cutting and pasting, etc. But drag and drop for application installation is wasteful, as common libraries get duplicated *for each program* rather than installed into system-wide places. As someone who downloaded Quicktime 7 and then iTunes (where the installer contains a full copy of Quicktime anyway), I absolutely LOATHE duplication of libraries!

---

### Post by Mr. Picklesworth on 2008-04-14
> **3rdalbum said:**
> Drag and drop is great, when you're talking about opening documents, cutting and pasting, etc. But drag and drop for application installation is wasteful, as common libraries get duplicated *for each program* rather than installed into system-wide places. As someone who downloaded Quicktime 7 and then iTunes (where the installer contains a full copy of Quicktime anyway), I absolutely LOATHE duplication of libraries!

Definitely! Besides that, how is dragging and dropping an application into Applications, then adding it to the dock for quick access, somehow more effective than simply opening it wherever it is and letting gdebi do its thing?

The latter is more learnable (you open it, just like anything else), automatically puts the application where it should be, does not require a special uninstaller (I have encountered a number of Mac users with issues uninstalling software; the system does not seem to have an effective way of regulating what files applications own), and loses nothing.

*You have one folder with all applications, so you can just go to Applications and open something.*
Unfortunately, they have no organization. It is roughly equivalent to the Windows start menu, but has quite truly everything in it with no categories except for what the user creates himself... completely manually.

*Search indexer sees the applications magically, so you don't really have to hunt them down explicitly*
So does ours, thanks to the .desktop entry standard and /usr/share/applications. I might add that descriptions do really well in that regard. I notice that, with MacOS, I have to know the exact name of a program if I want to find it via Spotlight. Simply "photos" gives me nothing, whereas it should really give me iPhoto. (Not that ours is perfect; does .desktop have a keywords section? It would be helpful in this case to fit all the permutations of a word).

*You can install easily; just click, hold the button, drag the mouse to that Applications folder while still holding the button, make sure the little plus sign is there or you aren't aiming at the right place, and let go...*
You can install easily; just open through any of the ergonomically sound, non-exclusive methods of opening files. For example double click, context menu: open, file: open...

*But you don't open stuff through Applications, you open stuff through the dock after adding it to the thing!*
You don't open stuff through /usr/share/applications, you open stuff through the menu, which is generated automagically... and then drag those launchers elsewhere if need be. Unlike the dock idea, the launchers are already launchers, so missing the dock does not lead us to disaster.


As for drag and drop, the idea does need to be fleshed out. I mentioned that it is not ergonomically sound. However, what I think it does well that is *very important* is it lets us sort of tag displayed content. For example, a program can essentially say "this represents an image located at "file:///home/me/Desktop/myavatar.png".
The power there is interesting. Think synchronization tools and user-friendly desktop scripting GUIs...
My thought is dragging and dropping needs to be phased out as the focus behind the technology, with the push being more at just marking paths for content and processing.

---

### Post by the8thstar on 2008-04-15
**Mr. Picklesworth**

> You have one folder with all applications, so you can just go to Applications and open something.
Unfortunately, they have no organization. It is roughly equivalent to the Windows start menu, but has quite truly everything in it with no categories.

Ubuntu has a serious problem with the organization of its menu system. I don't know if it's because it's dependent on Gnome or what, but could it it be simplified? So many items look redundant or pointless. And of course there's always the program that you installed that's not showing up in Applications... :(

---

### Post by koenn on 2008-04-15
One of the tyhings that struck me when I first installed Ubuntu was how well organized it was, edpacially the clear and concise menus.Every aapplication was where i expected it (without any prior knowledge)
Maybe it's just that may take on "order" is similar to that of the Gnome/ubuntu devs ) I don't know, it just makes sense to me. 

As for the program not showing up in the menu - Gnome provides a mechanism for applications to automatically add theiir menu entry to the menu. If they don't appear, it's most likely the people who build the package forgot (or didn't care) to include the required file for this mechanism to work. So it's really a package-related bug, imo.

---

### Post by the8thstar on 2008-04-19
I'm a fervent Gnome user and I love the interface. However, things could be organized better and faster. Some menus could be put together and grouped in tabs within a GUI instead of being spread out through Preferences and Administration for instance.

> As for the program not showing up in the menu - Gnome provides a mechanism for applications to automatically add theiir menu entry to the menu. If they don't appear, it's most likely the people who build the package forgot (or didn't care) to include the required file for this mechanism to work. So it's really a package-related bug, imo

That's precisely one of my points: it's urgent to enforce some rules when it comes to packages in the repos and .deb packages outside. I understand that control would be time and money-consuming for developers, but it seems to me that this is VERY necessary in order to provide quality applications and an overall stable system to the end user.

Maybe programmers could send their apps and programs to an 'e-committee' of testers and users, prior to having them released into the repos? This way, the program could be tagged as working under Ubuntu.

---

