---
title: "Wishes and wants for Ubuntu?"
date: 2009-03-15
forum: The Cafe
---

### Post by linuxisevolution on 2009-03-15
I finally figured out how to make my own distro (by uncompressing the squash filesystem on the install cd and extracting it to a "fake" file system and then mounting that to directory and chrooting it).

I am adding extra themes, programs, and window managers. I plan to make a light and heavy version. First, I need some feedback from the Ubuntu Community:

1. What should the name be? I was thinking something like "Hard-Core Ubuntu" kinda like "TinyCore Linux".

2. What programs, themes, files, etc, would you like to see in Ubuntu by default?

3. How should Gnome, XFCE, and KDE be setup? (the heavy version will  include all of these)?

4. What window manager/environment should come with the light version?


Thanks for your help! Dev's wanted! :D

---

### Post by linuxisevolution on 2009-03-15
I also plan to remove and replace a LOT for the light version. It should take <150mb when finished(ram-wise).

I also found a 40gb hdd for the download server.

---

### Post by blueshiftoverwatch on 2009-03-15
> **linuxisevolution said:**
> 2. What programs, themes, files, etc, would you like to see in Ubuntu by default?
A [secure empty trash]("http://ubuntuforums.org/showthread.php?t=1090749") option.

---

### Post by ArtF10 on 2009-03-15
U-Lite was originally known as ubuntu-lite....until ubuntu objected to having ubuntu in the name.

you'll haev to leave out the ubuntu from the distro name.

---

### Post by linuxisevolution on 2009-03-15
> **blueshiftoverwatch said:**
> A [secure empty trash]("http://ubuntuforums.org/showthread.php?t=1090749") option.

This shouldn't be to hard at all, and shouldn't add more than a few hundred kilobytes. When the trash is emptied a script will be run that over writes the files with 0's. But what bash commands should be in this script?

Thanks for your help!

The first release will be based on Ubuntu 8.10. Any names yet? 

If Ubuntu can't be in the name then we should find another better meaning word that sounds better. :)

---

### Post by linuxisevolution on 2009-03-15
Zephyrus Linux sounds cool and isn't taken. Any other suggestions before I start making the official site?

---

### Post by mrsteveman1 on 2009-03-15
I'm not sure what the goal here is. Unless you are focusing on a livecd environment, you can accomplish all the things you would like to change by making a deb file for ubuntu itself.

---

### Post by linuxisevolution on 2009-03-15
> **mrsteveman1 said:**
> I'm not sure what the goal here is. Unless you are focusing on a livecd environment, you can accomplish all the things you would like to change by making a deb file for ubuntu itself.

The goal? Um... To make Ubuntu more user friendly(yes I hate those words too), learn, and make Ubuntu more complete. I plan to make it similar to Linux Mint -but better.

---

### Post by Simian Man on 2009-03-15
> **linuxisevolution said:**
> I finally figured out how to make my own distro (by uncompressing the squash filesystem on the install cd and extracting it to a "fake" file system and then mounting that to directory and chrooting it).
So you're not making a "distro", you're making a custom Ubuntu spin or something.

> **linuxisevolution said:**
> 1. What should the name be? I was thinking something like "Hard-Core Ubuntu" kinda like "TinyCore Linux".
I don't think it can contain "Ubuntu" in the name without being official.

> **linuxisevolution said:**
> 2. What programs, themes, files, etc, would you like to see in Ubuntu by default?
Different things from other users surely.  If you want this to be useful, why not make it customizable so the user can choose?

> **linuxisevolution said:**
> 4. What window manager/environment should come with the light version?
I like Openbox when I need lightness, but others like different things.  See above.

Making a custom spin of Ubuntu with software you like will only be remotely useful for others with those same tastes.  And even then most would likely just download Ubuntu and customize it themselves.

Why not focus on making a customizable live DVD install where users can choose their own software?

Oh and regarding filling deleted files with zeroes, look up [shred]("http://unixhelp.ed.ac.uk/CGI/man-cgi?shred+1").

---

### Post by smartboyathome on 2009-03-15
> **linuxisevolution said:**
> The goal? Um... To make Ubuntu more user friendly(yes I hate those words too), learn, and make Ubuntu more complete. I plan to make it similar to Linux Mint -but better.

Why don't you hook up with the other Ubuntu-based distros trying to do the same thing? ;)

I think that you should try to contribute to the main Ubuntu project instead of making yet another user friendly Ubuntu-based distro.

---

### Post by linuxisevolution on 2009-03-15
> **Simian Man said:**
> So you're not making a "distro", you're making a custom Ubuntu spin or something.


I don't think it can contain "Ubuntu" in the name without being official.


Different things from other users surely.  If you want this to be useful, why not make it customizable so the user can choose?


I like Openbox when I need lightness, but others like different things.  See above.

Making a custom spin of Ubuntu with software you like will only be remotely useful for others with those same tastes.  And even then most would likely just download Ubuntu and customize it themselves.

Why not focus on making a customizable live DVD install where users can choose their own software?

Oh and regarding filling deleted files with zeroes, look up [shred]("http://unixhelp.ed.ac.uk/CGI/man-cgi?shred+1").

I already made a trash script with shred, thanks though. I know it's an Ubuntu spin. aka Variant ;)

How do I make my own installer so the user can customize? That's what I am really after. Like there could be a simple version that find the users computer specs and installs either the light or heavy packages. Or they could select advanced and then select their DE or WM. They could choose themes too, but that's a maybe.

---

### Post by linuxisevolution on 2009-03-15
> **smartboyathome said:**
> Why don't you hook up with the other Ubuntu-based distros trying to do the same thing? ;)

I think that you should try to contribute to the main Ubuntu project instead of making yet another user friendly Ubuntu-based distro.

The devs would never listen to me.

---

### Post by smartboyathome on 2009-03-15
> **linuxisevolution said:**
> I already made a trash script with shred, thanks though. I know it's an Ubuntu spin. aka Variant ;)

How do I make my own installer so the user can customize? That's what I am really after. Like there could be a simple version that find the users computer specs and installs either the light or heavy packages. Or they could select advanced and then select their DE or WM. They could choose themes too, but that's a maybe.

You'd have to remake the whole installer, as the normal installer installs the LiveCD's images with a few tweaks, and you'd need to install from packages in order to customize it without uninstalling and such (uninstalling makes it messy). I think that you should study something like the Debian net installer and Arch Linux's new profile-based installer (AIF), since it will be more along the lines of what you want. Once done, you should make one which uses "profiles" (ie, lists of packages) which a screen to customize the profile and save it to an external device. Then install using the list of packages.

> **linuxisevolution said:**
> The devs would never listen to me.

Sure they would, they just might not agree with you because it would take too much energy and/or isn't technically feasible.

---

### Post by linuxisevolution on 2009-03-15
> **smartboyathome said:**
> You'd have to remake the whole installer, as the normal installer installs the LiveCD's images with a few tweaks, and you'd need to install from packages in order to customize it without uninstalling and such (uninstalling makes it messy). I think that you should study something like the Debian net installer and Arch Linux's new profile-based installer (AIF), since it will be more along the lines of what you want. Once done, you should make one which uses "profiles" (ie, lists of packages) which a screen to customize the profile and save it to an external device. Then install using the list of packages.



Sure they would, they just might not agree with you because it would take too much energy and/or isn't technically feasible.

Not technically feasible? heh. I wrote the "secure trash" thing in under a minute. It could be added to the panel with a nice icon. Although it isn't complete at all, it works:

```

#!/bin/sh

shred -r -u -z -n 26 ~/.Trash | gmessage Trash encrypted with 26 zeros and deleted. 

exit 0


```

---

### Post by linuxisevolution on 2009-03-15
> **smartboyathome said:**
> You'd have to remake the whole installer, as the normal installer installs the LiveCD's images with a few tweaks, and you'd need to install from packages in order to customize it without uninstalling and such (uninstalling makes it messy). I think that you should study something like the Debian net installer and Arch Linux's new profile-based installer (AIF), since it will be more along the lines of what you want. Once done, you should make one which uses "profiles" (ie, lists of packages) which a screen to customize the profile and save it to an external device. Then install using the list of packages.




Are you saying simply have all the .deb files located on the dvd disc, and have a package-manager-type-thing select and install them?


--OR--

I could have several versions, like light, heavy, one for Windows users/newbies , and one for previous mac users?

For instance, have:

light.squashfs

heavy.squashfs

win.squashfs

mac.squashfs

All located on the same disc, and the user or installer would simply chose what they want? I think that would be easier, and would require minimal modification of the current installer.


Anyone know where the Ubuntu's GUI installer is located in the cdrom's file system? 

I am getting excited :D w00t!

---

### Post by smartboyathome on 2009-03-15
> **linuxisevolution said:**
> Are you saying simply have all the .deb files located on the dvd disc, and have a package-manager-type-thing select and install them?


--OR--

I could have several versions, like light, heavy, one for Windows users/newbies , and one for previous mac users?

For instance, have:

light.squashfs

heavy.squashfs

win.squashfs

mac.squashfs

All located on the same disc, and the user or installer would simply chose what they want? I think that would be easier, and would require minimal modification of the current installer.


Anyone know where the Ubuntu's GUI installer is located in the cdrom's file system? 

I am getting excited :D w00t!

I am saying you'd have to do what you said the first time. The second would require you to modify Ubuntu's default seed files and such (much more than just the seed files, but I can't remember everything) to redirect them to different locations, and have the user at boot time select what they want to use/install.

---

### Post by linuxisevolution on 2009-03-15
> **smartboyathome said:**
> I am saying you'd have to do what you said the first time. The second would require you to modify Ubuntu's default seed files and such (much more than just the seed files, but I can't remember everything) to redirect them to different locations, and have the user at boot time select what they want to use/install.

Ok, the first option, I was afraid you would say that...

So, were exactly are the .deb files for installation stored on the install disk? Is this only available on the alternate install disk?

---

### Post by smartboyathome on 2009-03-15
> **linuxisevolution said:**
> Ok, the first option, I was afraid you would say that...

So, were exactly are the .deb files for installation stored on the install disk? Is this only available on the alternate install disk?

It is only available on the alternate disk. You could always write a GUI for it though. :D

---

### Post by linuxisevolution on 2009-03-15
> **smartboyathome said:**
> It is only available on the alternate disk. You could always write a GUI for it though. :D

Sounds great, want to help? :lolflag:

I have never written a GUI before, admittedly. This would require pygtk or something along those lines, wouldn't it? And Then I would have to load a basic gui like blackbox/amiwm/openbox or similar to run the installer(and make it look pretty).

I see that the packages are sorted via alphabetically. Is this important? Could I sort them by installation type and have the installer change to that directory?

---

### Post by linuxisevolution on 2009-03-15
Okay, so here is the to-do list if anyone wants to become involved:

[B]1.Find packages that will need to be installed(.deb files)
[/B]
**2.Make installer:**

_3.Will require some help on how to make the installer include those files. Does it just install everything in the /pool directory or do I need to edit some file that will include my custom packages?_

4. Test it!

---

### Post by smartboyathome on 2009-03-15
> **linuxisevolution said:**
> Sounds great, want to help? :lolflag:

I have never written a GUI before, admittedly. This would require pygtk or something along those lines, wouldn't it? And Then I would have to load a basic gui like blackbox/amiwm/openbox or similar to run the installer(and make it look pretty).

I see that the packages are sorted via alphabetically. Is this important? Could I sort them by installation type and have the installer change to that directory?

You could use PyGTK, or something else. I wouldn't be able to help though, since I use Arch Linux, and am already part of a distro team. :(

---

### Post by Johnsie on 2009-03-15
-Better Wine so I can use more of my Windows apps
-Better support for Windows device drivers so I can plug anything in without having to restrict what hardware I can use.

---

### Post by linuxisevolution on 2009-03-15
> **smartboyathome said:**
> You could use PyGTK, or something else. I wouldn't be able to help though, since I use Arch Linux, and am already part of a distro team. :(

Oh, come on, [SIZE="6"]**PLEASE**[/SIZE]. :KS

Arch Linux, eh? Good! That means your experienced. Can you at least help me with programming an installer? Or at least help me get started? :(


I might just have to make 6 individual versions... sigh...

---

### Post by linuxisevolution on 2009-03-15
> **Johnsie said:**
> -Better Wine so I can use more of my Windows apps
-Better support for Windows device drivers so I can plug anything in without having to restrict what hardware I can use.

I can't do much with wine since I am not a dev for that team(and don't want to be btw. Copying an API Layer = Huge mess lol). I can include Wine though, thats on the list.

And, Windows Device drivers? Do you mean include more Linux-based drivers by default? That's a challenge...

---

### Post by NE Key on 2009-03-15
I want a function that deletes a file ;

Not move it to trash but DELETE.

I want to be able to clean a part of my hard drive so that there is no trace left of the file I want removed.


Secondly;

I want a function that cleans the hard drive. 

The unused part of my hard drive, which contains bits of trashed files, should be scrubbed clean so that here is no trace of the files I "deleted".

---

### Post by Simian Man on 2009-03-15
> **NE Key said:**
> I want a function that deletes a file ;

Not move it to trash but DELETE.

I want to be able to clean a part of my hard drive so that there is no trace left of the file I want removed.


Secondly;

I want a function that cleans the hard drive. 

The unused part of my hard drive, which contains bits of trashed files, should be scrubbed clean so that here is no trace of the files I "deleted".

The only way to completely remove a file from a hard drive is with a blow torch.  Things like shred make files hard to recover, but not impossible.

---

### Post by mehaga on 2009-03-15
Installer would have to have this as a first question:
- How [COLOR="Red"]tech savvy[/COLOR] are you? 

Why? To make eisenwinter mad: [http://ubuntuforums.org/showpost.php?p=6895855&postcount=10](http://ubuntuforums.org/showpost.php?p=6895855&postcount=10)
:popcorn:

I'm sorry, I couldn't resist :D

I'll be back with more serious suggestions, hopefully :)

---

### Post by linuxisevolution on 2009-03-15
> **NE Key said:**
> I want a function that deletes a file ;

Not move it to trash but DELETE.

I want to be able to clean a part of my hard drive so that there is no trace left of the file I want removed.


Secondly;

I want a function that cleans the hard drive. 

The unused part of my hard drive, which contains bits of trashed files, should be scrubbed clean so that here is no trace of the files I "deleted".

When you delete a file using the GUI in Ubuntu it goes to ~/.Trash

So the script:

shred -r -u -z -n 26 ~/.Trash | gmessage Trash encrypted with 26 zeros and deleted. 

Deletes those files and over rights them with 26 0's so they will  be very hard to get back. It also gives a message.

---

### Post by linuxisevolution on 2009-03-15
> **vekaz said:**
> Installer would have to have this as a first question:
- How [COLOR="Red"]tech savvy[/COLOR] are you? 

Why? To make eisenwinter mad: [http://ubuntuforums.org/showpost.php?p=6895855&postcount=10](http://ubuntuforums.org/showpost.php?p=6895855&postcount=10)
:popcorn:

I'm sorry, I couldn't resist :D

I'll be back with more serious suggestions, hopefully :)

Uh, very... You better be back! :D

---

### Post by mehaga on 2009-03-15
Ok, ok...

How about this. If there is a drive without any partitions on it, install there and don't ask anything about install location, partitioning etc. That would only work if, before that, you chose 'easy install', which leads us to another suggestion: have an 'easy install' installer option :) Ask minimum number of questions (zero, if possible) and just... install. Choosing 'easy install' could lead you to "What type of software do you want installed?" with options like 'office', 'web', 'multimedia' etc...
Also, only install predefined defaults for each option(not OpenOffice and KOffice and WhateverOffice, just one of them). My choice of options may not be terribly smart, but you get the idea...

---

### Post by linuxisevolution on 2009-03-15
> **vekaz said:**
> Ok, ok...

How about this. If there is a drive without any partitions on it, install there and don't ask anything about install location, partitioning etc. That would only work if, before that, you chose 'easy install', which leads us to another suggestion: have an 'easy install' installer option :) Ask minimum number of questions (zero, if possible) and just... install. Choosing 'easy install' could lead you to "What type of software do you want installed?" with options like 'office', 'web', 'multimedia' etc...
Also, only install predefined defaults for each option(not OpenOffice and KOffice and WhateverOffice, just one of them). My choice of options may not be terribly smart, but you get the idea...

I like all the ideas except for your partitioning idea, which could end badly... The first release will use the Default installer. There will be -THREE- different versions of the Distro before I get the installer and package manager worked out. It will also use the default installer for the first and possibly second release.

The versions are as follows:

Light:

Includes Fluxbox with a nice panel like fbpanel or lspanel. Abiword and some other things are to be decided. There will be only one or two apps installed by default for every subject. For example: Seamonkey is the browser. Gcalc and about 3 other things will be in the accessories menu. It will be based on Debian -not Ubuntu.

Full:

Layout is like Windows, but Uses gnome. Has some extra apps replacing the default ones and a nice theme-wallpaper-etc.. Based on Ubuntu. Uses KDE. Version undecided, but most likely 3.5.X unless I magically decide on 4.2...

Extra:

Looks like mac4lin. Has Gnome by default, but gives the option of XFCE and KDE. Will have everything I can think of. Based on Ubuntu.****

EDIT: I almost forgot, the website will be up tomorrow night, and the forums are up now, at: [http://www.linuxforums.tk](http://www.linuxforums.tk)

.tk is the domain name unless someone wants to pay $.99 for the .com domain(I don't have an online account, please don't laugh ;)

I will complete the Distros in the next week or so, and I will post the files online once I add another hard drive to the server( 550mb left lol). The drive will give 40gb+ room for development.

Since no one will help me with the name, the name is...

[COLOR="DarkOrange"]Zephyrus Linux[/COLOR]

---

### Post by linuxisevolution on 2009-03-15
The website is up at [http://www.zephyruslinux.co.nr](http://www.zephyruslinux.co.nr)

---

### Post by linuxisevolution on 2009-03-15
So...

Does anyone want to help???

Man, 790,306 people registered on this forum and not 1 offers to be a dev. Sad.

---

### Post by cirabisi2009 on 2009-03-15
my first thought. i installed unbuntu through wubi. maybe we could get a program like that for the new linux! and are we wanting to keep the gnome interface?

the thought about the wubi thing is for more newb users to want to try. if they dont have to mess with partitions them selves it may be a lil more user friendly as far as the download so an average joe can do it without hitting the books or researching alot huh

---

### Post by linuxisevolution on 2009-03-15
> **cirabisi2009 said:**
> my first thought. i installed unbuntu through wubi. maybe we could get a program like that for the new linux! and are we wanting to keep the gnome interface?

I do not now anything about wubi, but I'll do some research.

As for the desktop environment, the "extra" version will have gnome, kde, and xfce.

The full version will most likely use KDE 3.5.X, or the newest Gnome. We will have a vote soon :D

Also, Fluxbox or some other light wm will be used for the light version. I'll take care of the complex things.:P

EDIT: I'll have a howto on modding the file system structure and such so we can get started. As I said before, I have to make the layout..

---

### Post by cirabisi2009 on 2009-03-15
> **linuxisevolution said:**
> I do not now anything about wubi, but I'll do some research.



wubi basically puts ubuntu into windows like any other install. so you could remove it via control panel=>add/remove hardware. and puts it onto a partition for you.

---

### Post by smartboyathome on 2009-03-15
> **linuxisevolution said:**
> Oh, come on, [SIZE="6"]**PLEASE**[/SIZE]. :KS

Arch Linux, eh? Good! That means your experienced. Can you at least help me with programming an installer? Or at least help me get started? :(


I might just have to make 6 individual versions... sigh...

Sorry, I can't. I don't know that much programming. I mostly know scripting, not actual coding, and have just very lightly touched on Python, so i wouldn't be of much help. :(

---

### Post by linuxisevolution on 2009-03-15
> **smartboyathome said:**
> Sorry, I can't. I don't know that much programming. I mostly know scripting, not actual coding, and have just very lightly touched on Python, so i wouldn't be of much help. :(

Scripting? GOOD! So you will help me when I need a tip or some help with a script? A lot of Zephyrus Linux's settings and other things will be by scripts.


Was that a yes?

Your a dev. :D


Don't worry. I'll probably only ask like once a week..

---

### Post by cirabisi2009 on 2009-03-15
well im a go ahead and start studying python in the morning. we'll see how fast i can learn the stuff on there :tongue: by the end of tomorrow i will look like this guy => ](*,)

---

### Post by DonaldJ on 2009-03-17
> **linuxisevolution said:**
> I finally figured out how to make my own distro (by uncompressing the squash filesystem on the install cd and extracting it to a "fake" file system and then mounting that to directory and chrooting it).

I am adding extra themes, programs, and window managers. I plan to make a light and heavy version. First, I need some feedback from the Ubuntu Community:

1. What should the name be? I was thinking something like "Hard-Core Ubuntu" kinda like "TinyCore Linux".

2. What programs, themes, files, etc, would you like to see in Ubuntu by default?

3. How should Gnome, XFCE, and KDE be setup? (the heavy version will  "include all of these)?

4. What window manager/environment should come with the light version?


Thanks for your help! Dev's wanted! :D



No one has done a theme using bugs...

There are thousands of little critters...  

Butterflys, Dragonflys, beetles, crickets, Wasps, Spiders...

I'll give you a feel for the bugs...  A couple years ago, I was standing in my back yard, and a huge blue dragonfly flies by about three feet from my face, and I says an excited "Hi"..  and it turns, and circles my shoulders, decelerating, and lands right on my nose, slapping my face with its wings a little, then stayed there on my nose for more than a minute...

I saw a butterfly on a log, and I walks up to it, and says to it, "I'd like to meet you.. I'm safe, your safe, I can't hurt you, you can't hurt me"...  and when I got to it, it opened its wings a little, and let me toy with its wings...

I saw a large leaf hopper beetle crawling out of my rain barrel.. I says to it, "There's no food here for you.. step onto my thumb, and I'll take you to a better place"..  and it did...  It stood on my thumbnail, and we approached a dandelion...  A foot from the dandelion it instantly turned its back on the weed...  "OK, the rose...  A foot from the rose it flash turned its back on the rose...  "Ohhhhkay.. look over there, at that daisy.. That one looks like it might be good for something.. and it's Huge!..  Lets go see the daisy"..  8-inches from the daisy, the little bug's legs started doing a little dance...  6-inches away it was just a rocking and a bouncing side to side like how a kid looks when it really really has to pee...  4-inches away it leapt to the daisy...  Two days later, as I was walking near that daisy, the same little bug jumped to my face, and slipped off my face, and I caught it in an open hand, "Well hello my little friend.. I suppose you wants a ride to the rain barrel".. and to the rain barrel we went for a little drink...

I accidentally stepped in a solo bumble bee's nest in the sand..  and the bee returned looking for her nest...  I explained to her that I had accidentally stepped on it, while she hovered a few inches from my face while I spoke.. and I apologized...  She touched my face gently, then flew away...

Black widow spiders permit me to touch them, and to pick them up...

It's all about love and trust and honesty and caring for everything Life...

There's a Lot to bugs...  It could make for a good theme...

The bombardier beetle has a rocket engine in its bum...

Then there's the Walking Stick...

Snails (escargo)...

Cicadas, grasshoppers, locusts, katydids.. all sing tunes...

Bug build nests (files)

Bees... They make honey...  They are oh so friendly.. in my world that is...


Does this give you any ideas..?


Title:   Ummm..?   "Little Critter"


"Live Kindness"   "Love and Kindness"   "Butterfly"  "Arachnid"

---

### Post by miggols99 on 2009-03-17
> **linuxisevolution said:**
> I like all the ideas except for your partitioning idea, which could end badly... The first release will use the Default installer. There will be -THREE- different versions of the Distro before I get the installer and package manager worked out. It will also use the default installer for the first and possibly second release.

The versions are as follows:

Light:

Includes Fluxbox with a nice panel like fbpanel or lspanel. Abiword and some other things are to be decided. There will be only one or two apps installed by default for every subject. For example: Seamonkey is the browser. Gcalc and about 3 other things will be in the accessories menu. It will be based on Debian -not Ubuntu.

Full:

Layout is like Windows, but Uses gnome. Has some extra apps replacing the default ones and a nice theme-wallpaper-etc.. Based on Ubuntu. Uses KDE. Version undecided, but most likely 3.5.X unless I magically decide on 4.2...

Extra:

Looks like mac4lin. Has Gnome by default, but gives the option of XFCE and KDE. Will have everything I can think of. Based on Ubuntu.****

EDIT: I almost forgot, the website will be up tomorrow night, and the forums are up now, at: [http://www.linuxforums.tk](http://www.linuxforums.tk)

.tk is the domain name unless someone wants to pay $.99 for the .com domain(I don't have an online account, please don't laugh ;)

I will complete the Distros in the next week or so, and I will post the files online once I add another hard drive to the server( 550mb left lol). The drive will give 40gb+ room for development.

Since no one will help me with the name, the name is...

[COLOR="DarkOrange"]Zephyrus Linux[/COLOR]
Wow...that will be a lot of work. If you want to make a distro, you should really have one goal, not three. Personally I'd like:

[LIST]
[*]KDE 4.x based
[*]Gnome free (no gnome libs), or KDE free if using Gnome
[*]Available in 64-bit
[*]Based on Arch XD (but you have better experience in Ubuntu/Debian)
[*]Doesn't have ten different programs to do the same thing
[*]Includes subpixel hinting patches (I'm looking at you Debian)
[*]A unique theme
[*]Includes closed source firmware on the CD
[*]Codecs easily installable
[/LIST]
But you don't have to follow these.

No, don't ask me to be a dev, because I have to maintain my website, Archux (see sig). :D

---

### Post by DonaldJ on 2009-03-18
> **linuxisevolution said:**
> So...

Does anyone want to help???

Man, 790,306 people registered on this forum and not 1 offers to be a dev. Sad.



I really really needs to place the background pix to the far right of the screen...  I'm not getting any response to this concern, so it seems I have no option but to try to write it myself...  Point me in the direction to get started...

---

### Post by linuxisevolution on 2009-03-18
> **miggols99 said:**
> Wow...that will be a lot of work. If you want to make a distro, you should really have one goal, not three. Personally I'd like:

[LIST]
[*]KDE 4.x based
[*]Gnome free (no gnome libs), or KDE free if using Gnome
[*]Available in 64-bit
[*]Based on Arch XD (but you have better experience in Ubuntu/Debian)
[*]Doesn't have ten different programs to do the same thing
[*]Includes subpixel hinting patches (I'm looking at you Debian)
[*]A unique theme
[*]Includes closed source firmware on the CD
[*]Codecs easily installable
[/LIST]
But you don't have to follow these.

No, don't ask me to be a dev, because I have to maintain my website, Archux (see sig). :D

Nice website. I maintain all the ones in my sig. ;).

Thanks for the tips. I might just start it out with Gnome, and then include a kde version.

Codecs will be included. A unique theme? There will be lots :D

---

### Post by CrusaderAD on 2009-03-18
> 2. What programs, themes, files, etc, would you like to see in Ubuntu by default?

A Matrix Theme!!!

---

### Post by MIH1406 on 2009-03-18
ZigZag Linux a good name?!

---

