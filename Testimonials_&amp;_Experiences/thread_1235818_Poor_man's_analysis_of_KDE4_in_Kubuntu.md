---
title: "Poor man's analysis of KDE4 in Kubuntu"
date: 2009-08-09
forum: Testimonials &amp; Experiences
---

### Post by zugu on 2009-08-09
Having nothing to do this Sunday afternoon, I installed Kubuntu 9.04 in a virtual machine and decided to make a list of what I consider to be bugs, inconsistencies and defects. I am by no means an interface designer, but I did some software QA in my time. Here's what I found, unabridged:

KPackageKit software manager
1. [Blocked updates]("http://i27.tinypic.com/25uksxs.jpg") - What are they? The big red X symbol tells me: "dangerous! do not install!". If the updates are dangerous, why are they listed? Further research on the topic suggests the blocked updates are packages with unmet dependencies. If so, it's obviously dangerous to install them, but then why are dangerous updates listed? Why not list them when their dependencies will be met? [Some googling]("http://www.nabble.com/(jaunty)-What-are-blocked-updates--td23411820.html") suggested I'm seeing blocked updates because the mirror is in the process of syncing with the master repositories. If so, this is a process I, as an end-user, am not interested in. The updates should be listed after the repo sync is complete.

Kate text editor
1. Kate text editor has [word wrap disabled by default]("http://i26.tinypic.com/2po8o06.jpg"). I am not comfortable with this and I believe word wrap should be enabled by default. Enabling "Dynamic word wrap", closing the document and opening it again revealed that the "Dynamic word wrap" setting is no preserved between Kate sessions. Obviously a bug.
2. I created a new text file and I opened it for editing in Kate. On the left side of the screen there's a column listing all the open text documents. [This is a huge waste of space]("http://i26.tinypic.com/2po8o06.jpg"), listing the open documents in tabs would have conserved a lot of screen real-estate.
3. On the far left side of the Kate window there's some [vertical text]("http://i26.tinypic.com/2po8o06.jpg"). UI nightmare.

Kickoff Application Launcher
1. Clicking the blue K in the lower left corner of the screen opens a menu. In this menu, the Favorites tab is selected by default. In the Favorites tab, there's another menu. This menu obviously has more items than it can display, so there's a scrollbar on the left. The problem is that the last menu item, "Audio Player", is not completely visible - [it's truncated]("http://i30.tinypic.com/2e4bsib.jpg"). This makes me feel like the menu has been designed in a hurry, with no concern about presentation. I am running Kubuntu in a VM, but low screen resolution is not a valid excuse - it's obvious the menu has a lot of space to expand in order to display menu items in their entirety.
2. Next, in the Applications tab, there's another menu. [The problem]("http://i30.tinypic.com/9k7cyr.jpg") is this menu has a heading that says: "All applications". I find this redundant. Same for applies for the Favorites tab.
3. In the Computer tab, there's a submenu called "Applications". People annoyed by the redundancy mentioned above will be further annoyed and confused by [another "Applications" label]("http://i28.tinypic.com/2aflefp.jpg"). I suggest everything called "Applications" be kept in the same place, not spread around the K menu. Also, named menus or submenus with just one item are lame (see pic).
4. In the Favorites tab, I can right click an item and select "Remove from favorites", but I cannot find an obvious way to add something. There should probably be an option somewhere obvious that lets me edit the menu to my liking.
5. Some programs listed in the Applications tab have cryptic, unappealing names. Some examples: Krfb, KRDC, K3b, KRandRTray, Kvkbd. Most program names have a K as an initial letter. I can see how this is a pun on the KDE name, but most of the time this is ridiculous. I can accept Kate, Kopete, Kontact, but I find KSnapshot, KTorrent, KMail, KWalletManager to be ridiculous and unimaginative.
6. The item on the right of the K menu is [a folder with a yellow star on it]("http://i26.tinypic.com/2evtabn.jpg"). I don't even know what it does, since it shows no tooltip on mouse over (bug?). Clicking it reveals a menu consisting of locations the developers probably hope I'll make use of, similar to the My Documents folder on Windows, except I never use these special folders. My data - multimedia files, documents, and other stuff are usually kept on another partition. However, on Windows I can point the My Documents folder to where I want; in Kubuntu I could not find a way to do the same. And what possible connection is there between "Desktop, Documents, Music, Pictures" and "screen-configurations.xml"? Actually, WTF is screen-configurations.xml, why should I care about it and why is it present in this menu?
Note: I would have linked some screenshots to this issue, but unfortunately KSnapshot just crapped on me and no longer starts when invoked with Print Screen; I can't take screenshots of Kickoff and other open menus, because KSnapshot requires me to click the "New Snapshot" button in order to capture. Clicking a button anywhere closes any open menu. Lame.


Desktop
1. Widgets do not "snap" to the margins of the screen.
2. There's no obvious way to resize the Desktop Folder widget.
3. Why does the Desktop Folder widget not occupy all the screen? Better said, why is there so much wasted space around the Desktop Widget?
4. I added a Binary Clock widget to the desktop. Then I placed it over the Desktop Folder widget. Now I cannot move or interact with the Binary Clock, since only the Desktop Folder widget controls will appear on mouse over. Very frustrating.
5. What I believe to be the taskbar is cluttered with items. So many items actually, that there's little space left for window buttons. So I thought why not resize the taskbar? It will surely make more room for open windows. Here's [the extremely unfortunate result]("http://i30.tinypic.com/m7qtjo.jpg"), with comments.

Miscellaneous
1. When I mouse over the network item in the system tray / notification area / whatever it's called, a tooltip appears: "Network Management: eth0 connected". WTF is eth0? Why can't it use human language, such as "Wired network connection is connected"? Other variations come to mind: "Ethernet connected", "Local Area Connection / Status: connected" etc. Of course, I'm no interface designer, but anything is better than eth0.
2. Another item in the tray notifies me that "No devices plugged in" (it seems the developers accidentally a word). How about **the item shows up only when devices are actually plugged in**? Clicking the item shows up an empty list titled "Devices recently plugged in:". How about some text instead, like "No devices recently plugged in" and no empty list?
3. We're still in the tray. Some items, such as Volume, Klipper and Software Updates are grouped together, while others, like the removable device manager and the network status are not. I can't find an intuitive rule for this grouping.
4. Subjective observation: the icon for the "Show the Plasma Dashboard" item in the tray is ugly and difficult to understand.
5. During Kubuntu installation, various windows appeared on the screen. These windows communicated important information and allowed me to select important installation parameters. However, some of these windows were so small that the text in their titlebars was not completely visible. I had to manually resize them in order to view the whole text. I recommend shortening the text strings, increasing the default window size so that the whole  text is visible or a combination of both.

Konqueror web browser
1. The default homepage invites me to use Google's "I'm feeling lucky" search. Apart from the fact that displaying a (thumbnailed) list of the most visited sites is much better, why on Earth would I use "I'm feeling lucky" instead of a normal Google search? Having Google directing me to the first result is arguably much better when searching from the address bar, but the search field on the homepage should perform a normal search IMHO.
2. Konqueror should dump KHTML and switch to Webkit. 5 minutes of use and 4 incorrectly rendered sites, including GMail.
3. Logical push-up: let's assume there are 5 tabs open. Tab #4 is currently selected. How does one close tab #1? By clicking on tab #1, then clicking the Close button. This is like the old behavior of Firefox, inherited from Mozilla Suite. It's still present in Seamonkey today. Google Chrome and new releases of Firefox have a close button for each tab, requiring just one click to close a tab, currently selected or not. In Konqueror, one has to move back and forth: select the tab, move the mouse over the close button and click, move back and select another tab, move to the close button again... ad nauseam.

This is what I found in just one hour of using Kubuntu. I am scared about what I might find in a week of use. Such software is, by any definition, bad, beta quality software. Some friends asked me to give another chance to KDE, because it's supposedly mature and not the pile of trash that was KDE 4.0. Things have not improved much - and the KDE obsession with huge clocks and poor interface design is still there.

Don't get me wrong, Qt is a great toolkit, look at Skype on Windows, it rocks and its GUI is proof of this. Yet KDE is and has always been a UI mess.

Thank you for reading my rant. I won't submit bugs, because I'm lazy and I do believe KDE will never be a cool DE, no matter how many bugs are reported. I know most issues can be easily fixed, settings can be changed, but I'm an advocate for sane defaults; I'm not here to look for help, I'm here to share my Kubuntu experience. I used Kubuntu 9.04, vanilla, latest updates applied, in the latest version of VirtualBox.

Later edit
Another inconsistency I forgot to mention: folders in the Desktop Folder widget open up in Dolphin, with a **double-click**. Folders in Dolphin open with a **single click**. Confusing, inconsistent and frustrating behaviour.
Also, the spellchecker in KDE is counter-intuitive. When I right-click a misspelled word I expect the first items in the contextual menu to be spelling suggestions. Except that in Konqueror I have to go one menu deeper to find the suggestions. Did anyone perform any usability test before releasing this software? 99% of the people right-clicking a misspelled word do it to replace it with suggestions, not to "Add it to the dictionary" or whatever. This has to be a "won't fix" issue, it's too friggin' obvious to miss so it has to be by design. KDE devs and their curly brains...

---

### Post by Ms_Angel_D on 2009-08-10
I must that with a good portion of your post I agree about Kubuntu. They Say their are much better implications of KDE on other distro's, however I've not been in the mood to try them out.

It's my humble opinion that KDE works best on Ubuntu when installed along side gnome on a native Gnome install. I'm currently using KDE which I installed along side gnome on Ubuntu. It took me a few days to get everything figured out and set up to my liking, but now it seems to be working just fine.

I too had the system tray problem where I was running out of room, then I discovered that you could right click on it and set it to auto-hide whichever icons you wanted (making it very reminiscent of windows). My question is if this functionality is available why not have it enabled by default, as one could quickly run out of room, with open programs and windows.

I also agree with you about word wrap in Kate. When checking the word wrap option in the menu, this preference should be remembered for the next session.

Kubuntu itself always feels to me like it's only half baked. Like they have spent way too much time fixing the interface and not enough working on the actual functionality of it.

Angel

---

### Post by longtom on 2009-08-10
I used KDE before - and tried again.  Still find it buggy.  Never made the effoert to let somebody know.

You did.  Thank you.

---

### Post by HappyFeet on 2009-08-10
I wish the Kubuntu team would disband and put all their energies into making Ubuntu the best gnome distro on the planet. Kubuntu is the laughing stock of the linux world. It is also the brunt of many jokes and things wrong with linux. Perhaps they could let go of this "project", let KDE4 mature, and revisit it in a couple years. Too many precious man hours are being wasted trying to fight a losing battle. 

There are so many bugs in Kubuntu, it is not even funny. Plasmoids never work for me, is disjointed, and overall seems like an alpha release. It is leaving a lot of people with a bad taste in their mouths, and giving the ubuntu family a bad name.

I know many of you will disagree, but it's just my opinion.

---

### Post by izizzle on 2009-08-10
> **HappyFeet said:**
> I wish the Kubuntu team would disband and put all their energies into making Ubuntu the best gnome distro on the planet. Kubuntu is the laughing stock of the linux world. It is also the brunt of many jokes and things wrong with linux. Perhaps they could let go of this "project", let KDE4 mature, and revisit it in a couple years. Too many precious man hours are being wasted trying to fight a losing battle. 

There are so many bugs in Kubuntu, it is not even funny. Plasmoids never work for me, is disjointed, and overall seems like an alpha release. It is leaving a lot of people with a bad taste in their mouths, and giving the ubuntu family a bad name.

I know many of you will disagree, but it's just my opinion.

Have you tried KDE 4.3 yet?

---

### Post by HappyFeet on 2009-08-10
> **izizzle said:**
> Have you tried KDE 4.3 yet?

Yes.

Why is it that every major distro I have tried with XFCE, Gnome, Fluxbox, etc, works near perfect for me, but KDE4 is riddled with bugs? Can hardware be KDE incompatible? I doubt this is the case, seeing how everything else works fine.

But to be fair, if you like KDE and have no problems with it, by all means, use it, go forth and be happy. 

I will not support it, use it, or install it for anyone. I will check it out when 9.10 comes out, but I won't have much hope for it. We will see the same bad online reviews again and again.

---

### Post by MickS on 2009-08-10
I'm a Kubuntu use who is happy enough with it. I can't comment on Kate because I never use it but the folder with the star if you don't want it remove it I can't see the issue there. The Kickoff launcher is great when you get used to it, I think so anyway, your problem with the half displaying app is simple to fix, just drag the menu out to a larger size. To add things to favourites just find them and right click>add to favourites if you can't find them just start typing in the search bar and kickoff will find them for you.
The Desktop widget can be any size you want just unlock it and resize it, I like mine small, no good reason just do.
The Ksnapshot problem, just set a time delay, click new image then bring up what you want to capture.
Hope that helps a bit.


Mick

---

### Post by ibuclaw on 2009-08-10
> **zugu said:**
> 
KPackageKit software manager
1. [Blocked updates]("http://i27.tinypic.com/25uksxs.jpg") - What are they? The big red X symbol tells me: "dangerous! do not install!". If the updates are dangerous, why are they listed? Further research on the topic suggests the blocked updates are packages with unmet dependencies. If so, it's obviously dangerous to install them, but then why are dangerous updates listed? Why not list them when their dependencies will be met? [Some googling]("http://www.nabble.com/(jaunty)-What-are-blocked-updates--td23411820.html") suggested I'm seeing blocked updates because the mirror is in the process of syncing with the master repositories. If so, this is a process I, as an end-user, am not interested in. The updates should be listed after the repo sync is complete.

You are malinformed. Blocked packages (at least, in the Alpha), are distribution upgrades.
As it stands, kpackagekit cannot install dist upgrades unless a new release is available. Which there won't be because you're running the most recent release of Ubuntu.

This is partly to do with the fact that it was developed by Suse developers, to whom's OS has a completely different concept of package management.

The workaround would be to run the following in the terminal:
```
sudo apt-get dist-upgrade
```

> **zugu said:**
> 
Kate text editor
1. Kate text editor has [word wrap disabled by default]("http://i26.tinypic.com/2po8o06.jpg"). I am not comfortable with this and I believe word wrap should be enabled by default. Enabling "Dynamic word wrap", closing the document and opening it again revealed that the "Dynamic word wrap" setting is no preserved between Kate sessions. Obviously a bug.

Go to: ["**Settings -> Configure Kate -> Appearance**]("http://ubuntuforums.org/attachment.php?attachmentid=124346&stc=1&d=1249935661")".
If you went to: "View -> Dynamic Word Wrap", then that explains why the settings didn't keep.
> **zugu said:**
> 
2. I created a new text file and I opened it for editing in Kate. On the left side of the screen there's a column listing all the open text documents. [This is a huge waste of space]("http://i26.tinypic.com/2po8o06.jpg"), listing the open documents in tabs would have conserved a lot of screen real-estate.
3. On the far left side of the Kate window there's some [vertical text]("http://i26.tinypic.com/2po8o06.jpg"). UI nightmare.

To have a filebrowser to the left is useful for when you are handling projects. This feature is also present in IDEs such as Bluefish and Geany.

But, I do see your point, it is not for everyone, and you can hide it by selecting the middle and dragging to the far left.
> **zugu said:**
> 
Kickoff Application Launcher
1. Clicking the blue K in the lower left corner of the screen opens a menu. In this menu, the Favorites tab is selected by default. In the Favorites tab, there's another menu. This menu obviously has more items than it can display, so there's a scrollbar on the left. The problem is that the last menu item, "Audio Player", is not completely visible - [it's truncated]("http://i30.tinypic.com/2e4bsib.jpg"). This makes me feel like the menu has been designed in a hurry, with no concern about presentation. I am running Kubuntu in a VM, but low screen resolution is not a valid excuse - it's obvious the menu has a lot of space to expand in order to display menu items in their entirety.

That is the downside to using a small screen from a VM. As far as I can tell though, it seems to be fixed in Kubuntu Karmic. I am running from a netbook device and see no truncation.
> **zugu said:**
> 
4. In the Favorites tab, I can right click an item and select "Remove from favorites", but I cannot find an obvious way to add something. There should probably be an option somewhere obvious that lets me edit the menu to my liking.

1) [Right-click KDE Menu -> Menu Editor]("http://ubuntuforums.org/attachment.php?attachmentid=124347&stc=1&d=1249935661")
2) Go to any program listed in the KDE Menu and [Right-click item -> Add to Favourites]("http://ubuntuforums.org/attachment.php?attachmentid=124348&stc=1&d=1249935661")
> **zugu said:**
> 
5. Some programs listed in the Applications tab have cryptic, unappealing names. Some examples: Krfb, KRDC, K3b, KRandRTray, Kvkbd. Most program names have a K as an initial letter. I can see how this is a pun on the KDE name, but most of the time this is ridiculous. I can accept Kate, Kopete, Kontact, but I find KSnapshot, KTorrent, KMail, KWalletManager to be ridiculous and unimaginative.

And what about GEdit, GPilot, GCalctool, GConf-editor and GFloppy from Gnome?
It's their DE, and K is their trademark/label/muse to use + abuse.
> **zugu said:**
> 
6. The item on the right of the K menu is [a folder with a yellow star on it]("http://i26.tinypic.com/2evtabn.jpg"). I don't even know what it does, since it shows no tooltip on mouse over (bug?).

This has been [fixed]("http://ubuntuforums.org/attachment.php?attachmentid=124349&stc=1&d=1249935661") in Kubuntu Karmic
> **zugu said:**
> 
Clicking it reveals a menu consisting of locations the developers probably hope I'll make use of, similar to the My Documents folder on Windows, except I never use these special folders. My data - multimedia files, documents, and other stuff are usually kept on another partition. However, on Windows I can point the My Documents folder to where I want; in Kubuntu I could not find a way to do the same. And what possible connection is there between "Desktop, Documents, Music, Pictures" and "screen-configurations.xml"? Actually, WTF is screen-configurations.xml, why should I care about it and why is it present in this menu?
Note: I would have linked some screenshots to this issue, but unfortunately KSnapshot just crapped on me and no longer starts when invoked with Print Screen; I can't take screenshots of Kickoff and other open menus, because KSnapshot requires me to click the "New Snapshot" button in order to capture. Clicking a button anywhere closes any open menu. Lame.

1) This is not Windows. In UNIX, your home comes under 1 roof, not many. You **can** create symbolic links though, unlike Windows.
```
ln -s  /my/mounted/data  /home/me/Data
```
And you can change the location of your home directory in the /etc/passwd file.

2) Fixed in Kubuntu Karmic. KDE4.3 is alot stabler, and is progressively getting better.
May I also point out that 4.0 == development release, not stable release.
KDE 4.9 would be considered more stable release than KDE 5.0. :)
> **zugu said:**
> 
Desktop
1. Widgets do not "snap" to the margins of the screen.
2. There's no obvious way to resize the Desktop Folder widget.
3. Why does the Desktop Folder widget not occupy all the screen? Better said, why is there so much wasted space around the Desktop Widget?
4. I added a Binary Clock widget to the desktop. Then I placed it over the Desktop Folder widget. Now I cannot move or interact with the Binary Clock, since only the Desktop Folder widget controls will appear on mouse over. Very frustrating.
5. What I believe to be the taskbar is cluttered with items. So many items actually, that there's little space left for window buttons. So I thought why not resize the taskbar? It will surely make more room for open windows. Here's [the extremely unfortunate result]("http://i30.tinypic.com/m7qtjo.jpg"), with comments.

1) It's a feature.
2) [Unlock Widgets, resize is the top button when you hover your mouse over the widget.]("http://ubuntuforums.org/attachment.php?attachmentid=124350&stc=1&d=1249935661")
3) It's a feature, and a heavily liked one. Although you can change this in the KDE settings to have Icons on the Desktop background, if you must.
4) Bink
5) Now you are just being silly :)
> **zugu said:**
> 
Miscellaneous
1. When I mouse over the network item in the system tray / notification area / whatever it's called, a tooltip appears: "Network Management: eth0 connected". WTF is eth0? Why can't it use human language, such as "Wired network connection is connected"? Other variations come to mind: "Ethernet connected", "Local Area Connection / Status: connected" etc. Of course, I'm no interface designer, but anything is better than eth0.
2. Another item in the tray notifies me that "No devices plugged in" (it seems the developers accidentally a word). How about **the item shows up only when devices are actually plugged in**? Clicking the item shows up an empty list titled "Devices recently plugged in:". How about some text instead, like "No devices recently plugged in" and no empty list?
3. We're still in the tray. Some items, such as Volume, Klipper and Software Updates are grouped together, while others, like the removable device manager and the network status are not. I can't find an intuitive rule for this grouping.
4. Subjective observation: the icon for the "Show the Plasma Dashboard" item in the tray is ugly and difficult to understand.
5. During Kubuntu installation, various windows appeared on the screen. These windows communicated important information and allowed me to select important installation parameters. However, some of these windows were so small that the text in their titlebars was not completely visible. I had to manually resize them in order to view the whole text. I recommend shortening the text strings, increasing the default window size so that the whole  text is visible or a combination of both.

1) This is regularly discussed across the board of DE's ... to have Linux device ID jargon, or not to have Linux device ID jargon.
FYI, wlan0, eth0, eth1 and wmaster0 make more sense to me than the alternative.
Although, I use Wicd as my Network Manager, so I don't see what you see when you highlight over the NM Plasma Widget.
2) Feature. It is not an applet, it is a Plasma Widget. The great thing about KDE is that you can freely drag plasma widgets to and from the KDE bar.
3) The items grouped together **are** applets, unlike the previous example.
4) It makes it easy to arrange the plasma widgets without the desktop getting in the way.
5) I think this has to do with you using such a tiny screen. I think it's probably best to note now that GTK and QT windows/applications are "container" orientated, not "pixel" orientated. This is so windows maintain aspect ratio whatever size you put them in.
This is contrary to WinXP applications, but is now true for Vista/Win7 apps.
> **zugu said:**
> 
Konqueror web browser
1. The default homepage invites me to use Google's "I'm feeling lucky" search. Apart from the fact that displaying a (thumbnailed) list of the most visited sites is much better, why on Earth would I use "I'm feeling lucky" instead of a normal Google search? Having Google directing me to the first result is arguably much better when searching from the address bar, but the search field on the homepage should perform a normal search IMHO.
2. Konqueror should dump KHTML and switch to Webkit. 5 minutes of use and 4 incorrectly rendered sites, including GMail.
3. Logical push-up: let's assume there are 5 tabs open. Tab #4 is currently selected. How does one close tab #1? By clicking on tab #1, then clicking the Close button. This is like the old behavior of Firefox, inherited from Mozilla Suite. It's still present in Seamonkey today. Google Chrome and new releases of Firefox have a close button for each tab, requiring just one click to close a tab, currently selected or not. In Konqueror, one has to move back and forth: select the tab, move the mouse over the close button and click, move back and select another tab, move to the close button again... ad nauseam.

1) Konqueror is no longer the default web browser in Karmic.
2) Konqueror is no longer the default web browser in Karmic. :)
3) Konqueror is no longer the default web browser in Karmic. :D \o/
> **zugu said:**
> 
Later edit
Another inconsistency I forgot to mention: folders in the Desktop Folder widget open up in Dolphin, with a **double-click**. Folders in Dolphin open with a **single click**. Confusing, inconsistent and frustrating behaviour.

This appears to be fixed in Karmic. Both the Folder View Plasma and Dolphin should open directories with a single click now.

I have left attached screenshots too.

Regards
Iain

---

### Post by zugu on 2009-08-11
> **tinivole said:**
> You are malinformed. Blocked packages (at least, in the Alpha), are distribution upgrades.
As it stands, kpackagekit cannot install dist upgrades unless a new release is available. Which there won't be because you're running the most recent release of Ubuntu. This is partly to do with the fact that it was developed by Suse developers, to whom's OS has a completely different concept of package management.You described the situation better than me and explained why it occurs. Nevertheless, it's still a bug that should be fixed.

> **tinivole said:**
> Go to: ["**Settings -> Configure Kate -> Appearance**]("http://ubuntuforums.org/attachment.php?attachmentid=124346&stc=1&d=1249935661")".
If you went to: "View -> Dynamic Word Wrap", then that explains why the settings didn't keep.
I don't understand why setting "Dynamic Word Wrap" on from the "View" menu has a temporary effect, while setting it on from the "Settings" menu has a permanent one.

Food for thought: "Settings -> Configure Kate -> Appearance" should be replaced by "Settings -> Appearance". Reason: assume one wants to configure Kate. One starts Kate and goes to the "Settings" menu, _because this is the place to configure Kate from_. In this case "Settings -> **Configure Kate** -> Appearance" is a little bit redundant.

> **tinivole said:**
> To have a filebrowser to the left is useful for when you are handling projects. This feature is also present in IDEs such as Bluefish and Geany.Of course, but IDEs are IDEs, while simple text editors are simple text editors. I just wanted to edit some plain text, not to manage a project or use an IDE. Kate is the most basic GUI text editor installed in Kubuntu by default. Having that huge space on the left wasted is **not cool** and not a good default setting.

> **tinivole said:**
> But, I do see your point, it is not for everyone, and you can hide it by selecting the middle and dragging to the far left.Nice to know it can be changed, but a sane default would be better. Still no explanation for the vertical text. I would need an owl's neck to read it, and I hope KDE is not developed for owls :)

> **tinivole said:**
> That is the downside to using a small screen from a VM. As far as I can tell though, it seems to be fixed in Kubuntu Karmic. I am running from a netbook device and see no truncation.As I mentioned above, while the screen resolution was very low, the menu could have dynamically and automatically expanded towards the top of the screen in order to prevent truncation. There was enough space left, even in a 800x600 resolution. I am pleased to know this issue will be fixed in the next stable version of Kubuntu, but I'm not interested in discussing aplha quality, unreleased software. I'll just assume Karmic doesn't exist until the final version is released.

> **tinivole said:**
> 1) [Right-click KDE Menu -> Menu Editor]("http://ubuntuforums.org/attachment.php?attachmentid=124347&stc=1&d=1249935661")Intriguing, I did not notice the "Menu Editor" menu item. Maybe it's a Karmic addition or maybe I was too tired when I started this thread. I will check my VM installation to confirm.
> **tinivole said:**
> 2) Go to any program listed in the KDE Menu and [Right-click item -> Add to Favourites]("http://ubuntuforums.org/attachment.php?attachmentid=124348&stc=1&d=1249935661")Nice.

> **tinivole said:**
> And what about GEdit, GPilot, GCalctool, GConf-editor and GFloppy from Gnome?What about them? They are irrelevant to this discussion. And they have ugly names, too, but this is not an excuse to KDE and KDE apps to persist in doing the same. The KDE team showed us it's possible to do something smart in this respect when they came up with "Plasma", "Oxygen", "Nepomuk" and so on. I wish this trend will continue.
> **tinivole said:**
> It's their DE, and K is their trademark/label/muse to use + abuse.Of course it's theirs, but this doesn't mean they can't be criticised for the naming choices they make.

> **tinivole said:**
> This has been [fixed]("http://ubuntuforums.org/attachment.php?attachmentid=124349&stc=1&d=1249935661") in Kubuntu KarmicNice. But Karmic is irrelevant right now.

> **tinivole said:**
> 1) This is not Windows. In UNIX, your home comes under 1 roof, not many. You **can** create symbolic links though, unlike Windows.
```
ln -s  /my/mounted/data  /home/me/Data
```
And you can change the location of your home directory in the /etc/passwd file.No, it's not Windows, but the concept is very similar: a user directory with subdirectories structured by type of content: images, music, video files, documents etc. /home or My Documents - same thing actually. I am sure the screen-configurations.xml file has been actually created by some program, but nevertheless it is visible in the "Quick Access Browser". Maybe they should include a dot at the begining of the filename, to hide it. Or maybe they should just put .configuration files in /home/user/cfg and user files in /home/user/files. Windows keeps it clean with "Documents and Settings\user\Application Data" and "Documents and Settings\user\My Documents". Dumping user created files and config files together is not cool.
And why does "Quick Access Browser" have such a pompous name? It's nothing more than a glorified button that opens the home directory.

> **tinivole said:**
> 2) Fixed in Kubuntu Karmic. KDE4.3 is alot stabler, and is progressively getting better.I assume you're referring to KSnapshot. Again, I am not discussing Karmic here.
> **tinivole said:**
> May I also point out that 4.0 == development release, not stable release.Tell that to the distributions who rushed to include it in their "stable" releases.

> **tinivole said:**
> 
1) It's a feature.And what is the advantage of this "feature"? Why would people not prefer to have their widgets snapping to the edges of the screen?
> **tinivole said:**
> 2) [Unlock Widgets, resize is the top button when you hover your mouse over the widget.]("http://ubuntuforums.org/attachment.php?attachmentid=124350&stc=1&d=1249935661")I have to check something in the VM before replying, I'll soon get back to you on this matter.
> **tinivole said:**
> 3) It's a feature, and a heavily liked one. Although you can change this in the KDE settings to have Icons on the Desktop background, if you must.You don't understand, this might be the coolest feature ever, the problem is the developers failed to find an intuitive way to let me know what can be done with that space. Maybe they should have populated it with other widgets or something, but from where I stand all the useful commands (new file, new folder, cut, copy, paste etc.) appear when I right click the "Desktop Folder" widget. It's a different story when clicking the unoccupied space. The context menu in this case is poor and does a poor job explaining me the potential of this newfangled way of looking at a computer desktop.
> **tinivole said:**
> 4) BinkExcuse me?
> **tinivole said:**
> 5) Now you are just being silly :)Are you kidding me? Did you actually look at the image I attached? Taskbar space is **extremely** important and I always thought that KDE offers less taskbar space than Windows. The default is unsatisfactory, so I tried to increase it. [All I got is this UI horror]("http://i30.tinypic.com/m7qtjo.jpg").

> **tinivole said:**
> 1) This is regularly discussed across the board of DE's ... to have Linux device ID jargon, or not to have Linux device ID jargon. FYI, wlan0, eth0, eth1 and wmaster0 make more sense to me than the alternative.Except that they don't make sense for most people, while you just mentioned that the alternative at least makes **some** sense to you. So using the alternative will cover the bigger amount of people. *q.e.d.*
> **tinivole said:**
> 
2) Feature. It is not an applet, it is a Plasma Widget. The great thing about KDE is that you can freely drag plasma widgets to and from the KDE bar.I don't understand what you're replying to here. I was complaining about the presence of a tray item that is there just to tell me that "no devices are plugged in". I would very much appreciate if this item would appear only when something is actually plugged in. Moving the mouse over it, a list of recently plugged in items appears. Since nothing has ever been plugged in, the list is big, white and empty. How about showing the list ***only*** when it contains at least an item?
> **tinivole said:**
> 3) The items grouped together **are** applets, unlike the previous example.I'm sure there's a separation between widgets, applets and whatever. The KDE dudes "reinvented" the desktop. Too bad they did a bad job explaining their revolutionary vision. Are you familiar with the Windows presentation that appears at first run? It always explains what has changed since the last release; nice graphics, nice presentation, well written so that the user can adjust ASAP. And we all know how conservative MS is when it comes to Windows - the biggest change in the Windows GUI since Windows 95 has been the modified taskbar in Windows 7. The KDE dudes were much more radical when transitioning from KDE3 to KDE4. A similar "What's new" introduction screen is mandatory.

> **tinivole said:**
> 4) It makes it easy to arrange the plasma widgets without the desktop getting in the way.I meant that I can't really make anything of the icon itself; I am familiar enough with its function.
> **tinivole said:**
> 5) I think this has to do with you using such a tiny screen. I think it's probably best to note now that GTK and QT windows/applications are "container" orientated, not "pixel" orientated. This is so windows maintain aspect ratio whatever size you put them in.
This is contrary to WinXP applications, but is now true for Vista/Win7 apps.
I never knew this fact, thanks for letting me know. However, I installed Windows 7 RC in a VM and I had no issue with the titlebars, buttons, other widgets. There were no long text strings that didn't fit window widgets while the screen resolution was the same: 800x600. It's called attention to detail.

> **tinivole said:**
> 1) Konqueror is no longer the default web browser in Karmic.Konqueror is the default browser in Kubuntu 9.04, this is all that matters to me. However, I am curious what they replaced it with in Karmic: Arora? Firefox? Other Qt browser?

> **tinivole said:**
> This appears to be fixed in Karmic. Both the Folder View Plasma and Dolphin should open directories with a single click now.See above.

Anyway, I will give Karmic a try when it's released. But I find the current Kubuntu release to be unusable. I'm off to download the latest openSUSE to check out their KDE implementation.

---

### Post by ibuclaw on 2009-08-11
I'll just reply to some of your comments just to keep the post length down.
> **zugu said:**
> 
Of course, but IDEs are IDEs, while simple text editors are simple text editors. I just wanted to edit some plain text, not to manage a project or use an IDE. Kate is the most basic GUI text editor installed in Kubuntu by default. Having that huge space on the left wasted is **not cool** and not a good default setting.

Kate stands for **Kde Advanced Text Editor**, I mean, when you go into the "Configure Kate Settings" there is an option to turn on "**Vi mode**", which made me giggle for all the wrong reasons. :)

But, as you said, Kate is the most basic text editor for KDE as it stands.
> **zugu said:**
> 
I am sure the screen-configurations.xml file has been actually created by some program, but nevertheless it is visible in the "Quick Access Browser". Maybe they should include a dot at the begining of the filename, to hide it. Or maybe they should just put .configuration files in /home/user/cfg and user files in /home/user/files. Windows keeps it clean with "Documents and Settings\user\Application Data" and "Documents and Settings\user\My Documents". Dumping user created files and config files together is not cool.
And why does "Quick Access Browser" have such a pompous name? It's nothing more than a glorified button that opens the home directory.

That file should be located under your **.local** directory in your home. I did not see that file when I tried out the Jaunty version, but I guess you can safely delete it.

Although, one logical feature that KDE could have is Gnome's **[.hidden file concept]("http://library.gnome.org/users/user-guide/stable/nautilus-hidden-files.html.en")** for hiding files that don't have a period infront of their name.
> **zugu said:**
> 
Are you kidding me? Did you actually look at the image I attached? Taskbar space is **extremely** important and I always thought that KDE offers less taskbar space than Windows. The default is unsatisfactory, so I tried to increase it. [All I got is this UI horror]("http://i30.tinypic.com/m7qtjo.jpg").

This kinda relates to what I said about containers and how they keep their aspect ratio.
But I can see you point here, what you expected was probably **[something like this.]("http://ubuntuforums.org/attachment.php?attachmentid=124444&stc=1&d=1249999815")** (Imagine I have 6 windows open).

Apologies for the sketchiness of the image, I'm not that big a kung-foo wizz in GIMP.
> **zugu said:**
> 
I don't understand what you're replying to here. I was complaining about the presence of a tray item that is there just to tell me that "no devices are plugged in". I would very much appreciate if this item would appear only when something is actually plugged in. Moving the mouse over it, a list of recently plugged in items appears. Since nothing has ever been plugged in, the list is big, white and empty. How about showing the list ***only*** when it contains at least an item?

Okie doke, let me rehash my explaination as far as I understand it. (I've been using KDE cold turkey for 1 week) :)

The Device Notifier is a plasma widget (or plasmoid?), it is **[no different to the widget of the Desktop Folder that is on your desktop.]("http://ubuntuforums.org/attachment.php?attachmentid=124443&stc=1&d=1249999815")** And you can **[freely move it to and from the bottom bar.]("http://ubuntuforums.org/attachment.php?attachmentid=124442&stc=1&d=1249999815")**
And it's not just the Device Notifier, it's everything. Everything is a widget. The KDE start icon, the clock, the weather applet, even the application task bar that lists all currently running applications! You can pull that on and off the main bottom bar too. Break apart and put it back together again. :)

I've attached a video for you to see this happening: [http://tinypic.com/r/o9judv/3](http://tinypic.com/r/o9judv/3)
Again, apologies for the sketchy-ness of it. :)

But the point is that It is static, it cannot appear/hide due to the way that plasmoids are designed to be like.
> 
I'm sure there's a separation between widgets, applets and whatever. The KDE dudes "reinvented" the desktop. Too bad they did a bad job explaining their revolutionary vision. Are you familiar with the Windows presentation that appears at first run? It always explains what has changed since the last release; nice graphics, nice presentation, well written so that the user can adjust ASAP. And we all know how conservative MS is when it comes to Windows - the biggest change in the Windows GUI since Windows 95 has been the modified taskbar in Windows 7. The KDE dudes were much more radical when transitioning from KDE3 to KDE4. A similar "What's new" introduction screen is mandatory.

There is plenty of documentation, but most is likely either on their website, or in the Changelog that comes with the source code ... but point taken on user friendly. ;)
> **zugu said:**
> 
Konqueror is the default browser in Kubuntu 9.04, this is all that matters to me. However, I am curious what they replaced it with in Karmic: Arora? Firefox? Other Qt browser?

The new default is Arora, which comes with it's pros/cons too.

The biggest annoyance is that it doesn't save sessions. And flash crashes the application! (Had to write this essay out twice).
In my opinion though, I'd rather a QT4 Firefox browser.

As for OpenSUSE, I have been told that it is more polished as it is the default DE in the OS. Rather than Gnome being Fedora/Ubuntu's default.


Regards
Iain

---

### Post by NormanFLinux on 2009-08-11
The biggest screwup in Kubuntu was adept and the kpackagekit. I had synaptic installed. Its the best GUI apt package front-end period and I don't know why Kubuntu had to remove something proven to work in Ubuntu. Everything else has to be customized but that's the concept behind a modular OS. It should suit the user not the the other way around.

---

### Post by lykwydchykyn on 2009-08-11
> **tinivole said:**
> 
But, as you said, Kate is the most basic text editor for KDE as it stands.

No, actually there's a simpler one: Kwrite.  Very basic text editor.  I don't think it's included by default.  You could argue it should be, but as I see it here are the options:
 - ditch kate and keep kwrite.  In which case you're ditching a much more capable program for a simple one with limited options for no better reason than that you might "scare" the poor simple "average user" who is using a text editor why?
 - Put both on the disc, in which case you're wasting space with a redundant program, and people will gripe that it's just ridiculous and confusing to our "average user" to have two text editors for one DE.
 - Put the obviously more capable and robust text editor on the disc, which will please anyone who makes any kind of regular use of a text editor but might theoretically intimidate the "average user".

What's the right choice? 


As for the OP, I agree about kpackagekit, it's basically worthless for dealing with debian package management at this point.  Lesson to all the folks who are screaming that Ubuntu needs to move to packagekit.

As for the rest, I sincerely hope you've registered your opinion on the official Kubuntu/KDE bugtrackers, since you seem to have put a lot of thought and effort into the post.  It will probably do more good there than it will here.

---

### Post by slakkie on 2009-08-11
Since I'm a KDE user I want to respond to this.

> **zugu said:**
> 
KPackageKit software manager
1. [Blocked updates]("http://i27.tinypic.com/25uksxs.jpg") - What are they? The big red X symbol tells me: "dangerous! do not install!". If the updates are dangerous, why are they listed? Further research on the topic suggests the blocked updates are packages with unmet dependencies. If so, it's obviously dangerous to install them, but then why are dangerous updates listed? Why not list them when their dependencies will be met? [Some googling]("http://www.nabble.com/(jaunty)-What-are-blocked-updates--td23411820.html") suggested I'm seeing blocked updates because the mirror is in the process of syncing with the master repositories. If so, this is a process I, as an end-user, am not interested in. The updates should be listed after the repo sync is complete.


This is something I do not have any problem with. I never install/upgrade my machine via GUI. aptitude is all you need. So I cannot comment on this. I can however say, that upgrading/installing packages via aptitude (or apt-get for that matter) is simple and it is GUI independent. 


> 
Kate text editor
1. Kate text editor has [word wrap disabled by default]("http://i26.tinypic.com/2po8o06.jpg"). I am not comfortable with this and I believe word wrap should be enabled by default. Enabling "Dynamic word wrap", closing the document and opening it again revealed that the "Dynamic word wrap" setting is no preserved between Kate sessions. Obviously a bug.
2. I created a new text file and I opened it for editing in Kate. On the left side of the screen there's a column listing all the open text documents. [This is a huge waste of space]("http://i26.tinypic.com/2po8o06.jpg"), listing the open documents in tabs would have conserved a lot of screen real-estate.
3. On the far left side of the Kate window there's some [vertical text]("http://i26.tinypic.com/2po8o06.jpg"). UI nightmare.


Never used kate, vim rocks.

> 
Kickoff Application Launcher
1. Clicking the blue K in the lower left corner of the screen opens a menu. In this menu, the Favorites tab is selected by default. In the Favorites tab, there's another menu. This menu obviously has more items than it can display, so there's a scrollbar on the left. The problem is that the last menu item, "Audio Player", is not completely visible - [it's truncated]("http://i30.tinypic.com/2e4bsib.jpg").
This makes me feel like the menu has been designed in a hurry, with no concern about presentation. I am running Kubuntu in a VM, but low screen resolution is not a valid excuse - it's obvious the menu has a lot of space to expand in order to display menu items in their entirety.


If you looked closer, as soon as you hover your mouse over the truncated item, the item is displayed correctly. Hovering only "selects" the item. I think it is very friendly to the user.

>  
2. Next, in the Applications tab, there's another menu. [The problem]("http://i30.tinypic.com/9k7cyr.jpg") is this menu has a heading that says: "All applications". I find this redundant. Same for applies for the Favorites tab.


It is just a header. TBH, I find this comment nit-picking. If you don't like the kicker menu, you can easily switch to a KDE3 style kicker. Nothing stopping you.

> 
3. In the Computer tab, there's a submenu called "Applications". People annoyed by the redundancy mentioned above will be further annoyed and confused by [another "Applications" label]("http://i28.tinypic.com/2aflefp.jpg"). I suggest everything called "Applications" be kept in the same place, not spread around the K menu. Also, named menus or submenus with just one item are lame (see pic).


Maybe you've got a point, but what kind of name would you give to that menu, system settings and run a program are displayed (which are applications..). 

> 
4. In the Favorites tab, I can right click an item and select "Remove from favorites", but I cannot find an obvious way to add something. There should probably be an option somewhere obvious that lets me edit the menu to my liking.


I agree there should be a right click option in this section, yet, right clicking on any application/item in the kicker menu will display add to favorites. Took me two seconds to figure out. No real issue IMO.

> 
5. Some programs listed in the Applications tab have cryptic, unappealing names. Some examples: Krfb, KRDC, K3b, KRandRTray, Kvkbd. Most program names have a K as an initial letter. I can see how this is a pun on the KDE name, but most of the time this is ridiculous. I can accept Kate, Kopete, Kontact, but I find KSnapshot, KTorrent, KMail, KWalletManager to be ridiculous and unimaginative.


This was already the case in KDE3 and before. They are moving away from it though. Dolphin is an example of this. And I don't really kare what name the application has, since all applications are listed as what kind of application they are and then the application name eg Audio player - amarok, CD & DVD burning - k3b. Although this can be changed in the settings as well.

> 
6. The item on the right of the K menu is [a folder with a yellow star on it]("http://i26.tinypic.com/2evtabn.jpg"). I don't even know what it does, since it shows no tooltip on mouse over (bug?). Clicking it reveals a menu consisting of locations the developers probably hope I'll make use of, similar to the My Documents folder on Windows, except I never use these special folders. My data - multimedia files, documents, and other stuff are usually kept on another partition. However, on Windows I can point the My Documents folder to where I want; in Kubuntu I could not find a way to do the same. And what possible connection is there between "Desktop, Documents, Music, Pictures" and "screen-configurations.xml"? Actually, WTF is screen-configurations.xml, why should I care about it and why is it present in this menu?


I didn't get this menu either, but I removed it, since I don't use it. Although the menu itself can be useful to others. And the tooltip could have been enabled as a default, I agree.

If you store your files on a seperate partition, why not mount that partition as /home? Doing it the Windows way on a Unix box is pretty.. lame (sorry.. )

It is called quick access (I just enabled it) and you can change in which folder it should look. Apparently you have a file in your home dir called screen-configurations.xml. A simple right click will allow you to change the settings.

> 
Desktop
1. Widgets do not "snap" to the margins of the screen.
2. There's no obvious way to resize the Desktop Folder widget.
3. Why does the Desktop Folder widget not occupy all the screen? Better said, why is there so much wasted space around the Desktop Widget?
4. I added a Binary Clock widget to the desktop. Then I placed it over the Desktop Folder widget. Now I cannot move or interact with the Binary Clock, since only the Desktop Folder widget controls will appear on mouse over. Very frustrating.
5. What I believe to be the taskbar is cluttered with items. So many items actually, that there's little space left for window buttons. So I thought why not resize the taskbar? It will surely make more room for open windows. Here's [the extremely unfortunate result]("http://i30.tinypic.com/m7qtjo.jpg"), with comments.


I have no idea how you managed to do that (screenshot).. But I guess if you want it, KDE allows you to do it.

I run 4.3 atm on Karmic, where the desktop widget has been removed. So I cannot comment on that anymore, but you can change the size of the widget container (if you will) by hovering over it.

I haven't placed widgets on my desktop, since I hate desktop clutter, everything I want to see it placed on two panels (one on top, one below). It took me less then an hour to get the panels and all the widgets I wanted. While typing the response I found some new ones I like. 

> 
Miscellaneous
1. When I mouse over the network item in the system tray / notification area / whatever it's called, a tooltip appears: "Network Management: eth0 connected". WTF is eth0? Why can't it use human language, such as "Wired network connection is connected"? Other variations come to mind: "Ethernet connected", "Local Area Connection / Status: connected" etc. Of course, I'm no interface designer, but anything is better than eth0.


Network managers, stay away from them, whatever GUI you are using. Maybe use wicd, since I heard some positive things about it. 

But if you don't like naming conventions like eth0, don't go into /etc/network/interfaces...

eth0 can be a wireless interface as well. I had broadcom wireless card, which was eth1. Don't assume wireless cards have wlanx naming conventions. So call the interface like it is called by the OS/kernel.

> 
2. Another item in the tray notifies me that "No devices plugged in" (it seems the developers accidentally a word). How about **the item shows up only when devices are actually plugged in**? Clicking the item shows up an empty list titled "Devices recently plugged in:". How about some text instead, like "No devices recently plugged in" and no empty list?


Nit picking tbh, or I want to defend that widget since I really like it. What CD is loaded, goto my external USB disks, and the ability to umount them from that menu as well (granted, it failed to umount a disk when it wasn't used, haven't retested that in 4.3 though). If it is emtpy, then it is emtpy, no biggy.

> 
3. We're still in the tray. Some items, such as Volume, Klipper and Software Updates are grouped together, while others, like the removable device manager and the network status are not. I can't find an intuitive rule for this grouping.


Change it to your liking. It is a default which can be changed.

> 
4. Subjective observation: the icon for the "Show the Plasma Dashboard" item in the tray is ugly and difficult to understand.


Uhh, never seen this.

> 
5. During Kubuntu installation, various windows appeared on the screen. These windows communicated important information and allowed me to select important installation parameters. However, some of these windows were so small that the text in their titlebars was not completely visible. I had to manually resize them in order to view the whole text. I recommend shortening the text strings, increasing the default window size so that the whole  text is visible or a combination of both.


Didn't have these. Maybe because I upgraded from 8.04 to my current version. So it had my .kde files from 3.5.10 present. 

> 
Konqueror web browser
1. The default homepage invites me to use Google's "I'm feeling lucky" search. Apart from the fact that displaying a (thumbnailed) list of the most visited sites is much better, why on Earth would I use "I'm feeling lucky" instead of a normal Google search? Having Google directing me to the first result is arguably much better when searching from the address bar, but the search field on the homepage should perform a normal search IMHO.


FF user here, so no comments.

> 
This is what I found in just one hour of using Kubuntu. I am scared about what I might find in a week of use. Such software is, by any definition, bad, beta quality software. Some friends asked me to give another chance to KDE, because it's supposedly mature and not the pile of trash that was KDE 4.0. Things have not improved much - and the KDE obsession with huge clocks and poor interface design is still there.

Thank you for reading my rant. I won't submit bugs, because I'm lazy and I do believe KDE will never be a cool DE, no matter how many bugs are reported. I know most issues can be easily fixed, settings can be changed, but I'm an advocate for sane defaults; I'm not here to look for help, I'm here to share my Kubuntu experience. I used Kubuntu 9.04, vanilla, latest updates applied, in the latest version of VirtualBox.


That is pretty lame tbh. Ranting about a DE just for the sake of ranting and just after an hour. It took me several days to configure my PS1 (for the cli) for both bash and zsh, it took me several weeks on Windowmaker to configure to my liking and with KDE3.5 it took me also some weeks to get it just how I wanted it.
I don't expect any less with KDE4 (although some settings could have been used from kde3.5.x (like shortcuts). But ranting because you didn't like the defaults which can be changed, a shame really.

I think I would have the exact same issues with Gnome on a fresh Ubuntu install. Or Xcfe or any other DE/WM. I'm not used to it, so it is a bit different. 

Try it out longer and tweak/customize it to your likings and then tell me whether KDE is really that bad. I was sceptic of KDE4 due to the 4.0 fiasco, but 4.2.. Like 3.5 but a bit different. I love it and embrace the KDE devs for this product.

---

### Post by zugu on 2009-08-12
> **slakkie said:**
> This is something I do not have any problem with. I never install/upgrade my machine via GUI. aptitude is all you need. So I cannot comment on this. I can however say, that upgrading/installing packages via aptitude (or apt-get for that matter) is simple and it is GUI independent.Of course I could have used aptitude! I could've even compiled Ubuntu from scratch. Yet I chose to use the **official**, **recommended **way of installing the **latest stable version** of Ubuntu so that my criticism won't be slammed with "use the stable version!" or "that's what you get for installing Ubuntu using alternate, less safe methods!".


> **slakkie said:**
> Never used kate, vim rocks.Surprisingly, there are some of us who dislike the terminal and/or the steep learning curve editors like vi/vim have. vim was not present in the Applications menu by default, therefore I assumed it doesn't exist. 


> **slakkie said:**
> If you looked closer, as soon as you hover your mouse over the truncated item, the item is displayed correctly. Hovering only "selects" the item. I think it is very friendly to the user.The item should not be truncated in the first place. Imagine all the menus you constantly use started displaying truncated menu items. It's bad, and it should be fixed.

> **slakkie said:**
> It is just a header. TBH, I find this comment nit-picking. If you don't like the kicker menu, you can easily switch to a KDE3 style kicker. Nothing stopping you.Of course it's a header. The problem is the heading text is redundant. I checked out openSUSE 11.1 and they do not have this problem. You can try to minimise the issue all you want, any decent interface designer will tell you how important these "unimportant" things are.

> **slakkie said:**
> Maybe you've got a point, but what kind of name would you give to that menu, system settings and run a program are displayed (which are applications..). Um, I don't know, they could start by grouping everything called "Applications" in the same place, or they could just replace the text strings with something else **so that the redundancy is removed**. I'm not the one in charge of the menu, I'm the one criticising it.

> **slakkie said:**
> This was already the case in KDE3 and before.Is this an excuse? I don't think so.

> **slakkie said:**
> They are moving away from it though.Good.

> **slakkie said:**
> And I don't really kare what name the application has, since all applications are listed as what kind of application they are and then the application name eg Audio player - amarok, CD & DVD burning - k3b. Although this can be changed in the settings as well.I care. Users who have never heard about Krfb, KRDC, K3b, KRandRTray and Kvkbd will care. That's enough reason to criticise.

> **slakkie said:**
> It is called quick access (I just enabled it) and you can change in which folder it should look. Apparently you have a file in your home dir called screen-configurations.xml. A simple right click will allow you to change the settings.Of course I have a file called "screen-configurations.xml" in my home dir. I still don't know what is it used for, why is it there, why does no doccumentation tell me anything about it and why can I see it in Kubuntu out of the box. Honestly, I don't wish to know, I just want to show that it's wrong to dump probably important files in wrong places without proper documentation.

> **slakkie said:**
> I have no idea how you managed to do that (screenshot).. But I guess if you want it, KDE allows you to do it.In a freshly installed Kubuntu 9.04, drag the taskbar up to increase its size. See? That wasn't too difficult. Now welcome to the Official Bad User Interfaces Club.

> **slakkie said:**
> I run 4.3 atm on KarmicKarmic is alpha software I'm not interested in discussing in this thread.

> **slakkie said:**
> Network managers, stay away from them, whatever GUI you are using. Maybe use wicd, since I heard some positive things about it. 

But if you don't like naming conventions like eth0, don't go into /etc/network/interfaces...

eth0 can be a wireless interface as well. I had broadcom wireless card, which was eth1. Don't assume wireless cards have wlanx naming conventions. So call the interface like it is called by the OS/kernel.You've missed my point entirely.

> **slakkie said:**
> Nit picking tbh, or I want to defend that widget since I really like it. What CD is loaded, goto my external USB disks, and the ability to umount them from that menu as well (granted, it failed to umount a disk when it wasn't used, haven't retested that in 4.3 though). If it is emtpy, then it is emtpy, no biggy.I do not agree. The widget's main function is to show me a list of connected devices. When no devices are connected, the widget should not be present. It's that simple. Someone above you explained that due to the way the widgets are designed, it can't just disappear - this is obvious bad design, because the designer did not think it through.


> **slakkie said:**
> Change it to your liking. It is a default which can be changed.I was not interested in changing some default, but in understanding the criteria for item grouping.


> **slakkie said:**
> Uhh, never seen this.It's present in Kubuntu 9.04 and in openSUSE 11.1 (KDE edition) by default.


> **slakkie said:**
> That is pretty lame tbh. Ranting about a DE just for the sake of ranting and just after an hour. It took me several days to configure my PS1 (for the cli) for both bash and zsh, it took me several weeks on Windowmaker to configure to my liking and with KDE3.5 it took me also some weeks to get it just how I wanted it.I don't find my endeavour to be lame. Neither did other forum members. I am sorry you think like this.
> **slakkie said:**
> I don't expect any less with KDE4 (although some settings could have been used from kde3.5.x (like shortcuts). But ranting because you didn't like the defaults which can be changed, a shame really.The defaults are probably the most important settings in an application.

> **slakkie said:**
> I think I would have the exact same issues with Gnome on a fresh Ubuntu install. Or Xcfe or any other DE/WM. I'm not used to it, so it is a bit different.Fine. I chose KDE and compiled a list of issues. Are you upset I chose your pet DE?

---

### Post by zugu on 2009-08-12
> **lykwydchykyn said:**
> - ditch kate and keep kwrite.  In which case you're ditching a much more capable program for a simple one with limited options for no better reason than that you might "scare" the poor simple "average user" who is using a text editor why?
 - Put both on the disc, in which case you're wasting space with a redundant program, and people will gripe that it's just ridiculous and confusing to our "average user" to have two text editors for one DE.
 - Put the obviously more capable and robust text editor on the disc, which will please anyone who makes any kind of regular use of a text editor but might theoretically intimidate the "average user".

What's the right choice?In Windows there's a plain text editor called Notepad. No fancy stuff, no formatting, just editing. In GNOME there's Gedit - plain and easy to use and understand. Why can't KDE have something similar? Sometimes people just don't need command-lines (I just found out Kate can spawn a command-line prompt), IDE features and other advanced stuff in an editor.

> **lykwydchykyn said:**
> As for the rest, I sincerely hope you've registered your opinion on the official Kubuntu/KDE bugtrackers, since you seem to have put a lot of thought and effort into the post.  It will probably do more good there than it will here.Read my initial message again: I do not intend to submit bugs, nor am I looking for help. I just want to share my Kubuntu experience with the community.

---

### Post by slakkie on 2009-08-12
> **zugu said:**
> Of course I could have used aptitude! I could've even compiled Ubuntu from scratch. Yet I chose to use the **official**, **recommended **way of installing the **latest stable version** of Ubuntu so that my criticism won't be slammed with "use the stable version!" or "that's what you get for installing Ubuntu using alternate, less safe methods!".


Ok, fair point.

> 
Surprisingly, there are some of us who dislike the terminal and/or the steep learning curve editors like vi/vim have. vim was not present in the Applications menu by default, therefore I assumed it doesn't exist. 


Because it is not in the default install. I see. I still don't agree with your kate comments after opening kate though.

> 
The item should not be truncated in the first place. Imagine all the menus you constantly use started displaying truncated menu items. It's bad, and it should be fixed.


I don't agree with that. I think they solved that perfectly.

> 
Of course it's a header. The problem is the heading text is redundant. I checked out openSUSE 11.1 and they do not have this problem. You can try to minimise the issue all you want, any decent interface designer will tell you how important these "unimportant" things are.


I think it is just personal preference. I do not care about those headers. But, maybe they could be removed at the favorites and applications tabs. They are not redundant at the other tabs. Maybe it became redundant because they wanted consistency in the menu. So they put it everywhere. I don't see how a GUI designer would tell me me that this is really bad to do. 

> 
Um, I don't know, they could start by grouping everything called "Applications" in the same place, or they could just replace the text strings with something else **so that the redundancy is removed**. I'm not the one in charge of the menu, I'm the one criticising it.


Well, the computer tab has applications which are 2 things which are more global then the grouping in the application tabs.

Run apps, you could put in on top of applications, and the system settings, you could put that elsewhere too. But I bet you would criticize that too. I think those apps are in the correct place and the header is also fine. Should they rename the application tab to programs? Would be a valid alternative.

> 
Is this an excuse? I don't think so.
Good.
I care. Users who have never heard about Krfb, KRDC, K3b, KRandRTray and Kvkbd will care. That's enough reason to criticise.


Like someone else said, gnome has the same issue. Windows has the same issue, win$appname, winword.exe, windows defender. And besides it is not KDE's fault. Developers name their apps, not KDE.
I don't think is it a valid point in all fairness.

> 
Of course I have a file called "screen-configurations.xml" in my home dir. I still don't know what is it used for, why is it there, why does no doccumentation tell me anything about it and why can I see it in Kubuntu out of the box. Honestly, I don't wish to know, I just want to show that it's wrong to dump probably important files in wrong places without proper documentation.


I don't know either, but since you've tested opensuse as well, and I assume you have a seperate homedir. I've never seen Ubuntu install such a file in my homedir. But maybe that came with the (K)ubuntu install you did, I don't know. I upgraded to 9.04 from 8.10.

> 
In a freshly installed Kubuntu 9.04, drag the taskbar up to increase its size. See? That wasn't too difficult. Now welcome to the Official Bad User Interfaces Club.


I see, and I have the same issue. This is something I agree upon with you. Not nice. But only this item doesn't make it a bad GUI.

> 
Karmic is alpha software I'm not interested in discussing in this thread.


I know, I'm just saying that KDE 4.3 with Karmic does not have that widget anymore. I also stated that you can change the size of it in Jaunty.


> 
You've missed my point entirely.


No I did not. You want Kubuntu (or the network manager instead) to tell you that eth0 is you LAN connection. It cannot know that since I can plug in a WLAN card and the OS can recognize it as eth0 and then it should be called WLAN. So the best option is to just call it like the OS calls it: ethX, wlanX, etc, etc.

Which is fine by me. It also makes a smaller gap for explaining people what interface they are working on when we need to guide them in the cli. Which is an added bonus.

> 
I do not agree. The widget's main function is to show me a list of connected devices. When no devices are connected, the widget should not be present. It's that simple. Someone above you explained that due to the way the widgets are designed, it can't just disappear - this is obvious bad design, because the designer did not think it through.


I hate those widgets that are there and not there. Same thing with the Windows GUI where the network icons disappear when there is no network. I always want to see them, so I can click on them and see what is wrong. Easy access.

> 
I was not interested in changing some default, but in understanding the criteria for item grouping.


Ok. I told you that if you don't like the groupings, that you can change them. 

> 
It's present in Kubuntu 9.04 and in openSUSE 11.1 (KDE edition) by default.


I think I enabled it yesterday when I was looking for the show desktop widget. Like the OSX thing. Don't use it, so no further comments.

> 
I don't find my endeavour to be lame. Neither did other forum members. I am sorry you think like this.
The defaults are probably the most important settings in an application.


The defaults should be sane, which they are. And beyond that, change them. What suits you, will not suit the other 99% of the user base, so they need to make compromises... Then commenting like you did on the KDE because it doesn't suit you within the hour is.. I would have understood it better if you tried it for a week and commented on things that were buggy or you couldn't change or actions were not intuitive. 

> 
Fine. I chose KDE and compiled a list of issues. Are you upset I chose your pet DE?

No, or maybe yes. But like I said, try it out for at least a day, customize it a bit and then complain about certain things.

Just for comparison, the tone of this thread [http://ubuntuforums.org/showthread.php?t=1238514](http://ubuntuforums.org/showthread.php?t=1238514) vs this one.

---

### Post by lykwydchykyn on 2009-08-12
> **zugu said:**
> In Windows there's a plain text editor called Notepad. No fancy stuff, no formatting, just editing. In GNOME there's Gedit - plain and easy to use and understand. Why can't KDE have something similar? Sometimes people just don't need command-lines (I just found out Kate can spawn a command-line prompt), IDE features and other advanced stuff in an editor.


Sometimes people don't need a text editor.  Maybe they shouldn't include one at all.

Or maybe they should include programs that will be useful to as many people as possible.

I guess we'll just have to disagree on this point.

> 
Read my initial message again: I do not intend to submit bugs, nor am I looking for help. I just want to share my Kubuntu experience with the community.

Ah.  Ok.  Maybe you can help me see the point in such an exercise, other than to invite a lot of grief from the local KDE fans.  You've already said you didn't want to see KDE improve, so is the point just to complain?

---

### Post by zugu on 2009-08-13
> **lykwydchykyn said:**
> Ah.  Ok.  Maybe you can help me see the point in such an exercise, other than to invite a lot of grief from the local KDE fans.  You've already said you didn't want to see KDE improve, so is the point just to complain?What stops you from submitting bugs? If you agree with me on some issues, then by all means, submit bugs. I just don't want to help a desktop environment that [doesn't]("http://troy-at-kde.livejournal.com/17753.html") [need]("http://www.kdedevelopers.org/node/3535") users. OTOH, this forum is here so that I can share my Ubuntu / Kubuntu experience with other forum members. I don't really care if you or anyone else get upset about some piece of software.

---

### Post by zugu on 2009-08-13
> **slakkie said:**
> I still don't agree with your kate comments after opening kate though.Why? How do the vertical text, lack of word wrapping and that huge white space help you become more productive when all you do is simple text editing, especially when there is no other simple GUI text editor installed by default? At some point in time, one will have to edit simple config files or just write something down. Kate will probably do the job, but the experience can and should be improved.

> **slakkie said:**
> I don't agree with that. I think they solved that perfectly.How are truncated menu items better than menu items that are completely displayed? I am puzzled.

> **slakkie said:**
> I think it is just personal preference.No, it's not. Menus are supposed to be as descriptive as possible. The item grouping has to follow certain logical criteria, it has to be a well defined hierarchy. We already have an "Applications" tab. Having subsections of this tab named "Applications" is confusing.

> **slakkie said:**
> I think those apps are in the correct place and the header is also fine.Fine is not enough, and what is fine for you is not fine by my standards. In this case anything that is *better* is desirable, because it can satisfy both of us. Check out the way they named and arranged the items in the openSUSE KDE4 menu. It's BETTER.

> **slakkie said:**
> Like someone else said, gnome has the same issue. Windows has the same issue, win$appname, winword.exe, windows defender.Putting a *G* in front of everything is just as bad as putting a *K* in front of everything. But what GNOME or Windows do is not the issue here. These two desktop environments using braindead naming schemes is not a license for KDE to do the same.

> **slakkie said:**
> And besides it is not KDE's fault. Developers name their apps, not KDE.No, it's not KDE's fault; it's not Kubuntu's fault. But it's Kubuntu's _problem_.

> **slakkie said:**
> I see, and I have the same issue. This is something I agree upon with you. Not nice. But only this item doesn't make it a bad GUI.No, it doesn't make it bad, it makes it very bad. I showed the screenshot to some friends who are into Linux. They all agreed it's horrendous. Think about it: while the taskbar has many functions, the most important one is managing open windows and applications. Simply increasing the taskbar's size creates a UI SNAFU, and all the window buttons disappear. Therefore increasing the taskbar's size takes away its main function. Add the Kickoff issues in the mix. And the titlebar text during set-up issue. And Kate's interface. It's all bad interface design.

> **slakkie said:**
> You want Kubuntu (or the network manager instead) to tell you that eth0 is you LAN connection.Absolutely.
> **slakkie said:**
> It cannot know that since I can plug in a WLAN card and the OS can recognize it as eth0 and then it should be called WLAN.Yes, then it should be called WLAN. The OS should be able to tell the difference.

> **slakkie said:**
> So the best option is to just call it like the OS calls it: ethX, wlanX, etc, etc.No, the best option is to educate the OS so that it properly recognises plugged-in devices and peripherals.

> **slakkie said:**
> I hate those widgets that are there and not there.Sometimes it makes sense for stuff to disappear instead of just sitting there, doing nothing. It's better to have such a widget hidden by default. Users who need it "always on" should be able to permanently enable it somewhere. Otherwise we could fill the tray with widgets informing us that no Bluetooth connections are online, that no new email arrived, that no pop-ups were blocked and that the PC is running in normal parameters. **All turned on by default.** Imagine the horror.

I don't know how they call it in KDE, but in GNOME the tray is called "notification area" and it's there to notify the user when something HAPPENS, not the opposite.

> **slakkie said:**
> The defaults should be sane, which they are. No, they're not.
> **slakkie said:**
> What suits you, will not suit the other 99% of the user base, so they need to make compromises...I did not complain about the color of the wallpaper or about the position of the taskbar. I complained about what I believe are glaring bugs, based on common sense.

> **slakkie said:**
> Then commenting like you did on the KDE because it doesn't suit you within the hour is.. I would have understood it better if you tried it for a week and commented on things that were buggy or you couldn't change or actions were not intuitive. Should KDE/Kubuntu fix everything I complained about in this thread, I would then user it more than one hour. Using it a week in its current state would officially drive me mad™ :)

---

### Post by lykwydchykyn on 2009-08-13
> **zugu said:**
> What stops you from submitting bugs? If you agree with me on some issues, then by all means, submit bugs. I just don't want to help a desktop environment that [doesn't]("http://troy-at-kde.livejournal.com/17753.html") [need]("http://www.kdedevelopers.org/node/3535") users. OTOH, this forum is here so that I can share my Ubuntu / Kubuntu experience with other forum members. I don't really care if you or anyone else get upset about some piece of software.

I do submit bugs, thanks.  And on further reflection, I think I'm glad you don't.

Thanks for sharing, and have a nice day.

---

### Post by automaton26 on 2009-08-13
Some fair usability comments amongst that list - some of them are similar to my initial thoughts as a new user, 10 months ago. However, after putting some time & effort into exploring and experimenting, and looking online, I'm happy that I've either got workarounds or can put up with the current situation for now.

> I won't submit bugs, because I'm lazy

I won't put up with bugs, so I always check that they've been reported. I also donated to the KDE project, which is surely more constructive. KDE will hopefully get better with every release - that's the benefit of competition with other DEs.

I don't think anyone would ever find a DE that suited them perfectly and exactly, first time. Really, I think it takes longer to configure/customize Microsoft Windows on every fresh install, than KDE does.

Oh, and I'll admit that "Kate not remembering to hide the sidebar each time" is my no.1 UI usability annoyance :)

Thanks.

---

### Post by longtom on 2009-08-13
I think zugu had his day, made his testimonial and shared his experiences.

He has a very definite opinion about KDE, no doubt.  He will not move from that, as he has shown, and feels very strong about it.  KDE is obviously something he put a lot of thought to, even researching the internet to a certain extent to soilidify his feelings in regards of KDE.

I don't see any reason why one should argue his points or even answer to them.  That is his story and he will stick to it.

In the light that the op has no interest whatsoever to report any bugs or be part of a constructive process as far as KDE is concerned, one can read his thoughts, agree or not agree - and that's it really.

Somebody asked: "What's the point?"  - maybe it's therapie....

---

### Post by Ranax on 2009-08-13
> **tinivole said:**
> 
1) Konqueror is no longer the default web browser in Karmic.
2) Konqueror is no longer the default web browser in Karmic. :)
3) Konqueror is no longer the default web browser in Karmic. :D \o/


But the ironic thing is that Konqueror with the Webkit backend is better than Arora. I hope for KDE4.4 they just return to Konqueror as the default browser but fully dump KHTML, and replace it with Webkit.

---

### Post by zugu on 2009-08-14
> **Ranax said:**
> But the ironic thing is that Konqueror with the Webkit backend is better than Arora. I hope for KDE4.4 they just return to Konqueror as the default browser but fully dump KHTML, and replace it with Webkit.

There's a heated debate about this on various mailing lists and kdedevelopers.org blogs. Most users and developers agree that Webkit is clearly superior to KHTML, however the Qt Webkit implementation is not ready for prime-time. What should the KDE project do? KHTML is tightly integrated in KDE, Webkit is not. Replacing KHTML with Webkit is a lot of work. Replacing Konqueror with Arora is something a lot of KDE users don't want, because they consider Konqueror to have more features than Arora. Some others argue that Konqueror should be replaced with another Qt Webkit browser - unfortunately I can't remember its name.

It's an interesting debate, but I do know that the KDE project has no plans to replace Konqueror and KHTML at least until the release of KDE5. I understand Kubuntu will replace Konqueror in the next stable version. Other distributions might do the same.

---

### Post by Ranax on 2009-08-14
> **zugu said:**
> There's a heated debate about this on various mailing lists and kdedevelopers.org blogs. Most users and developers agree that Webkit is clearly superior to KHTML, however the Qt Webkit implementation is not ready for prime-time. What should the KDE project do? KHTML is tightly integrated in KDE, Webkit is not. Replacing KHTML with Webkit is a lot of work. Replacing Konqueror with Arora is something a lot of KDE users don't want, because they consider Konqueror to have more features than Arora. Some others argue that Konqueror should be replaced with another Qt Webkit browser - unfortunately I can't remember its name.

It's an interesting debate, but I do know that the KDE project has no plans to replace Konqueror and KHTML at least until the release of KDE5. I understand Kubuntu will replace Konqueror in the next stable version. Other distributions might do the same.

They need to do everything they can to leverage webkit into Konqueror. Otherwise what's the point?

---

### Post by Dullstar on 2009-08-15
I had problems with KDE after installing it.  Gnome doesn't seem to have as many problems.

---

### Post by bg_izrod on 2009-08-17
I also had problems with Kubuntu 9.04. Some of the system-tray icons disapeared. The system crashed several times (the last time unrepairable). The Video playback was poor as if I had a 15 year old videocard. Fedora 11 Leonidas (with KDE 4.3) was my salvation.

P.S. You should try to add more lines to the task bar than trying to enlarge it manually

---

### Post by Dipper on 2009-11-25
> **zugu said:**
> Having nothing to do this Sunday afternoon, I installed Kubuntu 9.04 in a virtual machine and decided to make a list of what I consider to be bugs, inconsistencies and defects. I am by no means an interface designer, but I did some software QA in my time. Here's what I found, unabridged:

KPackageKit software manager
1. [Blocked updates]("http://i27.tinypic.com/25uksxs.jpg") - What are they? The big red X symbol tells me: "dangerous! do not install!". If the updates are dangerous, why are they listed? Further research on the topic suggests the blocked updates are packages with unmet dependencies. If so, it's obviously dangerous to install them, but then why are dangerous updates listed? Why not list them when their dependencies will be met? [Some googling]("http://www.nabble.com/(jaunty)-What-are-blocked-updates--td23411820.html") suggested I'm seeing blocked updates because the mirror is in the process of syncing with the master repositories. If so, this is a process I, as an end-user, am not interested in. The updates should be listed after the repo sync is complete.
I've never seen this problem before.  But then I refuse to use KPackageKit.  I see no reason why Adept was discontinued as the default package manager.  It seems to me that they replaced a stable, fully-functional program with something that is beta-quality crap.  It looks like they did it "just because".

> Kate text editor
1. Kate text editor has [word wrap disabled by default]("http://i26.tinypic.com/2po8o06.jpg"). I am not comfortable with this and I believe word wrap should be enabled by default. Enabling "Dynamic word wrap", closing the document and opening it again revealed that the "Dynamic word wrap" setting is no preserved between Kate sessions. Obviously a bug.
An annoying problem, but easily solved.  Others in this thread have already discussed how it's done, so I will comment no further.

> 2. I created a new text file and I opened it for editing in Kate. On the left side of the screen there's a column listing all the open text documents. [This is a huge waste of space]("http://i26.tinypic.com/2po8o06.jpg"), listing the open documents in tabs would have conserved a lot of screen real-estate.
Come to think of it, that's never made much sense to me either.

> Kickoff Application Launcher
1. Clicking the blue K in the lower left corner of the screen opens a menu. In this menu, the Favorites tab is selected by default. In the Favorites tab, there's another menu. This menu obviously has more items than it can display, so there's a scrollbar on the left. The problem is that the last menu item, "Audio Player", is not completely visible - [it's truncated]("http://i30.tinypic.com/2e4bsib.jpg"). This makes me feel like the menu has been designed in a hurry, with no concern about presentation. I am running Kubuntu in a VM, but low screen resolution is not a valid excuse - it's obvious the menu has a lot of space to expand in order to display menu items in their entirety.
2. Next, in the Applications tab, there's another menu. [The problem]("http://i30.tinypic.com/9k7cyr.jpg") is this menu has a heading that says: "All applications". I find this redundant. Same for applies for the Favorites tab.
The kickoff menu was something that was changed for KDE4 when they should have left well enough alone.  My problem with the KDE4-style kickoff is all the clicking that needs to be done to launch a program.  I don't use the KDE4-style kickoff menu.  I stick with the classic style.  That's something that can easily be changed.  You don't have to live with the default.

> 5. Some programs listed in the Applications tab have cryptic, unappealing names. Some examples: Krfb, KRDC, K3b, KRandRTray, Kvkbd. Most program names have a K as an initial letter. I can see how this is a pun on the KDE name, but most of the time this is ridiculous. I can accept Kate, Kopete, Kontact, but I find KSnapshot, KTorrent, KMail, KWalletManager to be ridiculous and unimaginative.
Point taken.  But KDE users are used to it.  To a lesser extent, GNOME does the same thing.

> 1. Widgets do not "snap" to the margins of the screen.
That's not really important to me.  I guess I didn't notice until now.

> 2. There's no obvious way to resize the Desktop Folder widget.
3. Why does the Desktop Folder widget not occupy all the screen? Better said, why is there so much wasted space around the Desktop Widget?
Another KDE4 invention "just because".  Every desktop environment has full desktop functionality by default.  Computer users of every OS are used to working with files, folders, and documents on the desktop.  KDE developers took that away in the initial releases of KDE4.  It's something that used to drive me crazy until it became optional to use the entire desktop as a desktop again.  You can change your desktop settings to make the desktop work in a "Folder View" manner if you want your desktop to work like every other operating system in the world.

> 4. I added a Binary Clock widget to the desktop. Then I placed it over the Desktop Folder widget. Now I cannot move or interact with the Binary Clock, since only the Desktop Folder widget controls will appear on mouse over. Very frustrating.
5. What I believe to be the taskbar is cluttered with items. So many items actually, that there's little space left for window buttons. So I thought why not resize the taskbar? It will surely make more room for open windows. Here's [the extremely unfortunate result]("http://i30.tinypic.com/m7qtjo.jpg"), with comments.
The taskbar is something that has really come a long way since the KDE 4.0 release.  What puzzles me is that it seems that the KDE developers seemed to make taskbar functionality one of their last priorities.  It's still not up to where I would like it to be, but with the first KDE 4 releases, it was unacceptable.

> Miscellaneous
1. When I mouse over the network item in the system tray / notification area / whatever it's called, a tooltip appears: "Network Management: eth0 connected". WTF is eth0? Why can't it use human language, such as "Wired network connection is connected"? Other variations come to mind: "Ethernet connected", "Local Area Connection / Status: connected" etc. Of course, I'm no interface designer, but anything is better than eth0.
It's a Linux thing. Linux started as a geek operating system.  In many ways, it still is.

> 2. Another item in the tray notifies me that "No devices plugged in" (it seems the developers accidentally a word). How about **the item shows up only when devices are actually plugged in**? Clicking the item shows up an empty list titled "Devices recently plugged in:". How about some text instead, like "No devices recently plugged in" and no empty list?
The way KDE4 handles devices is screwy.  It used to be that when a device was plugged in, it simply showed up on the desktop.  Yet another change "just because".

> 3. We're still in the tray. Some items, such as Volume, Klipper and Software Updates are grouped together, while others, like the removable device manager and the network status are not. I can't find an intuitive rule for this grouping.
Beats me.  I can't figure that one out either.

> 4. Subjective observation: the icon for the "Show the Plasma Dashboard" item in the tray is ugly and difficult to understand.
Choosing "Lock Widgets" makes it disappear.

> 5. During Kubuntu installation, various windows appeared on the screen. These windows communicated important information and allowed me to select important installation parameters. However, some of these windows were so small that the text in their titlebars was not completely visible. I had to manually resize them in order to view the whole text. I recommend shortening the text strings, increasing the default window size so that the whole  text is visible or a combination of both.
I hope that someday they can come up with a way to have you select the installation parameters up front.  I did an update before going to bed so that it would be done when I woke up in the morning.  To my dismay, I woke up to find the installation process halted about 1/4 of the way through with some nag asking me a yes or no question.  I know that doesn't have much to do with your comment, but it's something I hope they fix.

> Konqueror web browser
1. The default homepage invites me to use Google's "I'm feeling lucky" search. Apart from the fact that displaying a (thumbnailed) list of the most visited sites is much better, why on Earth would I use "I'm feeling lucky" instead of a normal Google search? Having Google directing me to the first result is arguably much better when searching from the address bar, but the search field on the homepage should perform a normal search IMHO.
2. Konqueror should dump KHTML and switch to Webkit. 5 minutes of use and 4 incorrectly rendered sites, including GMail.
3. Logical push-up: let's assume there are 5 tabs open. Tab #4 is currently selected. How does one close tab #1? By clicking on tab #1, then clicking the Close button. This is like the old behavior of Firefox, inherited from Mozilla Suite. It's still present in Seamonkey today. Google Chrome and new releases of Firefox have a close button for each tab, requiring just one click to close a tab, currently selected or not. In Konqueror, one has to move back and forth: select the tab, move the mouse over the close button and click, move back and select another tab, move to the close button again... ad nauseam.
I gave up on Konqueror a long time ago.  Dolphin is a better file manager and Firefox is a better web browser.


> Thank you for reading my rant. I won't submit bugs, because I'm lazy and I do believe KDE will never be a cool DE, no matter how many bugs are reported. I know most issues can be easily fixed, settings can be changed, but I'm an advocate for sane defaults; I'm not here to look for help, I'm here to share my Kubuntu experience. I used Kubuntu 9.04, vanilla, latest updates applied, in the latest version of VirtualBox.
Kubuntu was my first Linux distro and the one I will always continue to use.  I tried Ubuntu vanilla during the intrepid era when KDE4 was so buggy it was unusable.  Generally, I find Ubuntu to be visually unappealing.  It does not have the look and feel of a modern operating system.  The default colors are something resembling human waste products.  I just don't like it.

On the other hand, KDE has done many things that don't make any sense.  I can see the need to improve things.  That's why new versions are released.  But much of KDE4's design has been change just for the sake of change.  And I don't especially like having to re-learn something I'm used to just because someone got a creative bug and thought it would be cool to make it work differently "just because".  My biggest problem right now with KDE is the transition of K3B to KDE4.  It's so buggy that it's not functional and it's been that way for a couple of releases.  Kubuntu should not be using a buggy beta-quality K3B as part of what is supposed to be an official stable Kubuntu release.

But we're talking about operating systems, not world politics.  I appreciate the insight.  I agree with some things and disagree with others.  But I refuse to get emotional about software.

---

### Post by solwic on 2009-11-25
> **automaton26 said:**
> I also donated to the KDE project...

There's a phrase for that.  It's called an "exercise in futility".  :biggrin:

But I hope KDE gets better, too.  Although the Gnome-shell is likely going to put KDE out of its misery....

---

### Post by HappyFeet on 2009-11-25
> **solwic said:**
> Although the Gnome-shell is likely going to put KDE out of its misery....

I hope so. I also hope that gnome 3 does go through the lengthy growing pains that kde did/is. If worse comes to worse, I'll just switch to Openbox. It's kind of hard to screw that up.

---

### Post by solwic on 2009-11-25
> **HappyFeet said:**
> I hope so. I also hope that gnome 3 does go through the lengthy growing pains that kde did/is. If worse comes to worse, I'll just switch to Openbox. It's kind of hard to screw that up.

Yeah, you've got to try really hard to screw up Openbox.  Personally, I like the Enlightenment desktop, if only it was a little easier to use.  

Of course, maybe I'm just spoiled by Gnome....

---

### Post by Shabakthanai on 2012-04-03
> **zugu said:**
> Having nothing to do this Sunday afternoon, I installed Kubuntu 9.04 in a virtual machine and decided to make a list of what I consider to be bugs, inconsistencies and defects. I am by no means an interface designer, but I did some software QA in my time. Here's what I found, unabridged:

KPackageKit software manager
1. [Blocked updates]("http://i27.tinypic.com/25uksxs.jpg") - What are they? The big red X symbol tells me: "dangerous! do not install!". If the updates are dangerous, why are they listed? Further research on the topic suggests the blocked updates are packages with unmet dependencies. If so, it's obviously dangerous to install them, but then why are dangerous updates listed? Why not list them when their dependencies will be met? [Some googling]("http://www.nabble.com/(jaunty)-What-are-blocked-updates--td23411820.html") suggested I'm seeing blocked updates because the mirror is in the process of syncing with the master repositories. If so, this is a process I, as an end-user, am not interested in. The updates should be listed after the repo sync is complete.

Kate text editor
1. Kate text editor has [word wrap disabled by default]("http://i26.tinypic.com/2po8o06.jpg"). I am not comfortable with this and I believe word wrap should be enabled by default. Enabling "Dynamic word wrap", closing the document and opening it again revealed that the "Dynamic word wrap" setting is no preserved between Kate sessions. Obviously a bug.
2. I created a new text file and I opened it for editing in Kate. On the left side of the screen there's a column listing all the open text documents. [This is a huge waste of space]("http://i26.tinypic.com/2po8o06.jpg"), listing the open documents in tabs would have conserved a lot of screen real-estate.
3. On the far left side of the Kate window there's some [vertical text]("http://i26.tinypic.com/2po8o06.jpg"). UI nightmare.

Kickoff Application Launcher
1. Clicking the blue K in the lower left corner of the screen opens a menu. In this menu, the Favorites tab is selected by default. In the Favorites tab, there's another menu. This menu obviously has more items than it can display, so there's a scrollbar on the left. The problem is that the last menu item, "Audio Player", is not completely visible - [it's truncated]("http://i30.tinypic.com/2e4bsib.jpg"). This makes me feel like the menu has been designed in a hurry, with no concern about presentation. I am running Kubuntu in a VM, but low screen resolution is not a valid excuse - it's obvious the menu has a lot of space to expand in order to display menu items in their entirety.
2. Next, in the Applications tab, there's another menu. [The problem]("http://i30.tinypic.com/9k7cyr.jpg") is this menu has a heading that says: "All applications". I find this redundant. Same for applies for the Favorites tab.
3. In the Computer tab, there's a submenu called "Applications". People annoyed by the redundancy mentioned above will be further annoyed and confused by [another "Applications" label]("http://i28.tinypic.com/2aflefp.jpg"). I suggest everything called "Applications" be kept in the same place, not spread around the K menu. Also, named menus or submenus with just one item are lame (see pic).
4. In the Favorites tab, I can right click an item and select "Remove from favorites", but I cannot find an obvious way to add something. There should probably be an option somewhere obvious that lets me edit the menu to my liking.
5. Some programs listed in the Applications tab have cryptic, unappealing names. Some examples: Krfb, KRDC, K3b, KRandRTray, Kvkbd. Most program names have a K as an initial letter. I can see how this is a pun on the KDE name, but most of the time this is ridiculous. I can accept Kate, Kopete, Kontact, but I find KSnapshot, KTorrent, KMail, KWalletManager to be ridiculous and unimaginative.
6. The item on the right of the K menu is [a folder with a yellow star on it]("http://i26.tinypic.com/2evtabn.jpg"). I don't even know what it does, since it shows no tooltip on mouse over (bug?). Clicking it reveals a menu consisting of locations the developers probably hope I'll make use of, similar to the My Documents folder on Windows, except I never use these special folders. My data - multimedia files, documents, and other stuff are usually kept on another partition. However, on Windows I can point the My Documents folder to where I want; in Kubuntu I could not find a way to do the same. And what possible connection is there between "Desktop, Documents, Music, Pictures" and "screen-configurations.xml"? Actually, WTF is screen-configurations.xml, why should I care about it and why is it present in this menu?
Note: I would have linked some screenshots to this issue, but unfortunately KSnapshot just crapped on me and no longer starts when invoked with Print Screen; I can't take screenshots of Kickoff and other open menus, because KSnapshot requires me to click the "New Snapshot" button in order to capture. Clicking a button anywhere closes any open menu. Lame.


Desktop
1. Widgets do not "snap" to the margins of the screen.
2. There's no obvious way to resize the Desktop Folder widget.
3. Why does the Desktop Folder widget not occupy all the screen? Better said, why is there so much wasted space around the Desktop Widget?
4. I added a Binary Clock widget to the desktop. Then I placed it over the Desktop Folder widget. Now I cannot move or interact with the Binary Clock, since only the Desktop Folder widget controls will appear on mouse over. Very frustrating.
5. What I believe to be the taskbar is cluttered with items. So many items actually, that there's little space left for window buttons. So I thought why not resize the taskbar? It will surely make more room for open windows. Here's [the extremely unfortunate result]("http://i30.tinypic.com/m7qtjo.jpg"), with comments.

Miscellaneous
1. When I mouse over the network item in the system tray / notification area / whatever it's called, a tooltip appears: "Network Management: eth0 connected". WTF is eth0? Why can't it use human language, such as "Wired network connection is connected"? Other variations come to mind: "Ethernet connected", "Local Area Connection / Status: connected" etc. Of course, I'm no interface designer, but anything is better than eth0.
2. Another item in the tray notifies me that "No devices plugged in" (it seems the developers accidentally a word). How about **the item shows up only when devices are actually plugged in**? Clicking the item shows up an empty list titled "Devices recently plugged in:". How about some text instead, like "No devices recently plugged in" and no empty list?
3. We're still in the tray. Some items, such as Volume, Klipper and Software Updates are grouped together, while others, like the removable device manager and the network status are not. I can't find an intuitive rule for this grouping.
4. Subjective observation: the icon for the "Show the Plasma Dashboard" item in the tray is ugly and difficult to understand.
5. During Kubuntu installation, various windows appeared on the screen. These windows communicated important information and allowed me to select important installation parameters. However, some of these windows were so small that the text in their titlebars was not completely visible. I had to manually resize them in order to view the whole text. I recommend shortening the text strings, increasing the default window size so that the whole  text is visible or a combination of both.

Konqueror web browser
1. The default homepage invites me to use Google's "I'm feeling lucky" search. Apart from the fact that displaying a (thumbnailed) list of the most visited sites is much better, why on Earth would I use "I'm feeling lucky" instead of a normal Google search? Having Google directing me to the first result is arguably much better when searching from the address bar, but the search field on the homepage should perform a normal search IMHO.
2. Konqueror should dump KHTML and switch to Webkit. 5 minutes of use and 4 incorrectly rendered sites, including GMail.
3. Logical push-up: let's assume there are 5 tabs open. Tab #4 is currently selected. How does one close tab #1? By clicking on tab #1, then clicking the Close button. This is like the old behavior of Firefox, inherited from Mozilla Suite. It's still present in Seamonkey today. Google Chrome and new releases of Firefox have a close button for each tab, requiring just one click to close a tab, currently selected or not. In Konqueror, one has to move back and forth: select the tab, move the mouse over the close button and click, move back and select another tab, move to the close button again... ad nauseam.

This is what I found in just one hour of using Kubuntu. I am scared about what I might find in a week of use. Such software is, by any definition, bad, beta quality software. Some friends asked me to give another chance to KDE, because it's supposedly mature and not the pile of trash that was KDE 4.0. Things have not improved much - and the KDE obsession with huge clocks and poor interface design is still there.

Don't get me wrong, Qt is a great toolkit, look at Skype on Windows, it rocks and its GUI is proof of this. Yet KDE is and has always been a UI mess.

Thank you for reading my rant. I won't submit bugs, because I'm lazy and I do believe KDE will never be a cool DE, no matter how many bugs are reported. I know most issues can be easily fixed, settings can be changed, but I'm an advocate for sane defaults; I'm not here to look for help, I'm here to share my Kubuntu experience. I used Kubuntu 9.04, vanilla, latest updates applied, in the latest version of VirtualBox.

Later edit
Another inconsistency I forgot to mention: folders in the Desktop Folder widget open up in Dolphin, with a **double-click**. Folders in Dolphin open with a **single click**. Confusing, inconsistent and frustrating behaviour.
Also, the spellchecker in KDE is counter-intuitive. When I right-click a misspelled word I expect the first items in the contextual menu to be spelling suggestions. Except that in Konqueror I have to go one menu deeper to find the suggestions. Did anyone perform any usability test before releasing this software? 99% of the people right-clicking a misspelled word do it to replace it with suggestions, not to "Add it to the dictionary" or whatever. This has to be a "won't fix" issue, it's too friggin' obvious to miss so it has to be by design. KDE devs and their curly brains...I currently use the kubuntu 11.10 Operating System.  The blue folder icon was removed from the options in the current 11.10.  I loved that plasmoid and would like to get it back.  I used it for multimedia and photographs.  I put it on the panel, then chose an appropriate Icon to represent what it represented.  For instance, I used a blue dolphin icon and had Dolphin drop down when I clicked on it.  Additionally, I used a golden DVD disk Icon that dropped down a list of movies I saved.  They were listed alphabetically and made easy finding a movie I wanted to see again.  Additionally, I chose a heart icon to represent photographs of loved ones.

Although I usually kept the panel hidden, when it opened it was quite attractive aesthetically.  I wish I had known the address of saved plasmoids, I would have saved that one to carry forward with upgraded versions of kubuntu.  It was my favorite plasmoid, highly configurable for itemized lists that could be represented by a suitable descriptive Icon of my choice.

---

### Post by overdrank on 2012-04-03
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

