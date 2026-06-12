---
title: "GScrot - Screenshot Tool"
date: 2008-05-19
forum: The Cafe
---

### Post by mario.kemper on 2008-05-19
Hi there, 

just want to introduce you to my little app i'm developing since a few weeks. 
Maybe someone is interested in it and will give it a try:

[https://launchpad.net/gscrot]("https://launchpad.net/gscrot")

Here comes a brief description (copied from the project page ;-) ):

GScrot is a simple (until now ;-) GTK+ 2.0 frontend for scrot written in perl. GScrot covers all features of the original scrot and adds reasonable new features combined with a comfortable GUI using the GTK+ 2.0 framework.

Features:

* take a screenshot of your complete desktop, a rectangular area or capture a website
* take screenshot directly or with a specified delay time
* save the screenshots to a specified directory and name them in a convenient way
   (using special wild-cards)
* GScrot is fully integrated into the Gnome Desktop (TrayIcon etc.)
* generate thumbnails directly when you are taking a screenshot and set a size level in %
* GScrot session collection
    --keep track of all screenshots during session
    --copy screeners to clipboard
    --print screenshots
    --delete screenshots
    --rename your file
* upload your files directly to [http://ubuntu-pics.de](http://ubuntu-pics.de), retrieve all the needed links and share them with others



I would be happy about feedback.

Greetings
Mario

---

### Post by agim on 2008-05-19
I have been looking for just this sort of app. I will let you know how it works after a few days of use...

Thanks!

---

### Post by Chokkan on 2008-05-19
This is great! Just what I need. Pressing PrintScreen is OK, but sometimes you want a more control + pretty GUI :) Haven't used it for long of course but no bugs to report as of yet.

Good work!

---

### Post by Vaelrith on 2008-05-19
I've been looking for a script that will automatically create a thumbnail of the screenshot and add a border and/or drop shadow.  I see the features of this program are that it creates a thumbnail, any way to add options for a border and drop shadow?

---

### Post by monstermudder78 on 2008-05-19
How do you pronounce GScrot?  It looks like Gee-Scrote to me lolz.

---

### Post by mario.kemper on 2008-05-20
Thanks for the response, folks.

@Vaelrith: This is planned for the next version. There will be a small script-manager to manipulate the taken screenshots just like you want. Stay tuned...


@monstermudder78: Scrot represents SCReenshOT and G just stands for GTK. Not really spectacular ;-)

---

### Post by mario.kemper on 2008-07-03
Just want to let you know that there is a new, fresh version of "GScrot - Screenshot Tool" available. 

:arrow: Release v0.38! Incl. plugins (gscrot-plugins-bash 0.0.9)

Announcement (new features briefly described here):
:idea: [https://launchpad.net/gscrot/+announcement/597](https://launchpad.net/gscrot/+announcement/597)

Project:
:idea: [https://launchpad.net/gscrot](https://launchpad.net/gscrot)

Greetings
Mario

---

### Post by K.Mandla on 2008-07-03
Have you seen gscreenshot?

[http://code.google.com/p/gscreenshot/](http://code.google.com/p/gscreenshot/)

I don't mention it to suggest you're duplicating efforts, but to suggest it as a source of ideas, if you like. Perhaps you've seen it already though. :D

---

### Post by mario.kemper on 2008-07-03
No, i've never heard of gscreenshot before and as i read at the project page...
*last revision: 4. september 2006*
...i am pretty sure it is discontinued. 

Nevertheless, GScrot offers a lot more features and options than scrot and the frontend you've discovered. 

Just give it a try, maybe you like our project more ;-)

---

### Post by marialice on 2008-07-04
Nice tool, thank you!

---

### Post by mario.kemper on 2008-07-05
@marialice: Thank you for your feedback.

---

### Post by Bou on 2008-07-05
Cool app, but the name sounds just too much like "scrotum".

---

### Post by mario.kemper on 2008-07-06
> **Bou said:**
> Cool app, but the name sounds just too much like "scrotum".
Well, the app is based on scrot. Maybe its because i am not a native speaker but i dont have this association ;-)

Nevertheless, any ideas of a name that would fit better? (please not something like gscreenshot)

---

### Post by Stu09 on 2008-07-06
> **monstermudder78 said:**
> How do you pronounce GScrot?  It looks like Gee-Scrote to me lolz.

Lol that was my first thought. Unfortunate name :lol:

---

### Post by mario.kemper on 2008-07-06
> **Stu09 said:**
> Lol that was my first thought. Unfortunate name :lol:
Any suggestions for a "fortunate" name?

---

### Post by K.Mandla on 2008-07-06
Don't change it, please. Anybody who knows scrot will have an appreciation for the name.

By the way, did the dependencies change between 0.37 and 0.38? I was looking at the Arch PKGBUILD for 0.37 to build a Crux port for 0.38, but it seems to want some things that weren't included in the dependencies for the 0.37 Arch version. Is that correct?

---

### Post by mario.kemper on 2008-07-06
> **K.Mandla said:**
> Don't change it, please. Anybody who knows scrot will have an appreciation for the name.

By the way, did the dependencies change between 0.37 and 0.38? I was looking at the Arch PKGBUILD for 0.37 to build a Crux port for 0.38, but it seems to want some things that weren't included in the dependencies for the 0.37 Arch version. Is that correct?

Some things changed, thats right. These are the current dependencies:

scrot, libgtk2-trayicon-perl, libgtk2-perl, gtklp, liblocale-gettext-perl, libglib-perl, perlmagick, libxml-simple-perl, libwww-mechanize-perl, libwww-perl, gnome-web-photo, gscrot-plugins-bash

The last (gscrot-plugins-bash) is not mandatory, of course. But i would recommend the plugins as they are very usefull. If you would like to port the plugins package as well, the only dependency for it is "imagemagick" (and gscrot ;-)).

---

### Post by nooblot on 2008-07-07
Please try to make it _easier_ for noobs to install your software - like providing DETAILED instruction and exact locations etc.

So looks like I'm stuck here , please tell me how to get this tool installed:



[IMG]http://img515.imageshack.us/img515/4757/screenshotgh6.png[/IMG]


Danke!

---

### Post by smartboyathome on 2008-07-08
> **nooblot said:**
> Please try to make it _easier_ for noobs to install your software - like providing DETAILED instruction and exact locations etc.

So looks like I'm stuck here , please tell me how to get this tool installed:



[IMG]http://img515.imageshack.us/img515/4757/screenshotgh6.png[/IMG]


Danke!

Go [here]("https://launchpad.net/~gscrot/+archive"), install the repo using System > Administration > Synaptic > Repositories > 3rd Party Software, and add it. Then reload and install it.

---

### Post by mario.kemper on 2008-07-08
@nooblot: There is no need to worry. Just do it like smartboyathome explained. 
But if you would like to install it by hand without adding the repo to your sources, you can follow three simple steps:

1) Go to: [https://launchpad.net/~gscrot/+archive]("https://launchpad.net/~gscrot/+archive")
There are 4 packages listed. (2 for Hardy and 2 for Gutsy)

2) Click on the little arrow in front of the plugins package and install the plugins package (choose hardy or gutsy)

3) Click on the little arrow in front of the gscrot package and install the gscrot package (choose hardy or gutsy)


Please tell me if you need any further assistance.

---

### Post by kaibob on 2008-07-08
> **K.Mandla said:**
> Don't change it, please. Anybody who knows scrot will have an appreciation for the name....

I agree that the current name should be retained. Scrot is the name adopted by this utility's author, and it should be retained (IMO).

---

### Post by mario.kemper on 2008-07-13
Release of GScrot v0.39 is available!

:arrow: [https://launchpad.net/gscrot/+announcement/651]("https://launchpad.net/gscrot/+announcement/651") 
Download: [https://launchpad.net/~gscrot/+archive]("https://launchpad.net/~gscrot/+archive")

By the way, there are no plans of renaming the project.

[SIZE="1"]
For those who are interested, there are two new dependencies: libgnome2-perl, libgnome2-gconf-perl >>> Not needed when installing the .deb-packages![/SIZE]

---

### Post by ryanc on 2008-07-17
Adding the repository locations does not appear to work either. See screenshots.

[IMG]http://img139.imageshack.us/img139/5050/29110458ll9.png[/IMG]
[IMG]http://img133.imageshack.us/img133/231/36246881ol1.png[/IMG]

---

### Post by chris4585 on 2008-07-17
i got the same as the above poster

---

### Post by coolglobal on 2008-07-17
excellent tool

name suggestion : screenie or screeny

say its derived from scrot in the about link?

joke here:
"scrot" is slang for scrotum as in "ballbag", gscrot would be a ballbag with a gstring added. Other wise known as "flys eyes".

---

### Post by kevdog on 2008-07-17
What ever happened just to Cntl-PrntScreen?

---

### Post by toupeiro on 2008-07-18
Cool tool, but I must concur, horrible name!  No way I'm recommending people I know to use a program called GScrot.  Sounds like there should be a cream for that.

---

### Post by kpkeerthi on 2008-07-18
Very nice app. Thanks.

Just one suggestion though, the buttons at the botton look quite dense. You may want to consider putting those in a toolbar at the top and have the tab display a preview of the image it represents.

---

### Post by dmizer on 2008-07-18
> **kevdog said:**
> What ever happened just to Cntl-PrntScreen?

heh, i'm glad i'm not the only one who thought that. ;)

---

### Post by mario.kemper on 2008-07-18
> **ryanc said:**
> Adding the repository locations does not appear to work either.

Sorry for your inconvenience. There are some problems at launchpad while copying packages. (We are copying packes from our beta-repository to the official repo)

I am working on it right now.

EDIT:

The problem should be solved. Just open a terminal:

**sudo apt-get update && sudo apt-get install gscrot**

Please let me know if it works for you as well now ;-)

---

### Post by wersdaluv on 2008-07-18
What are its advantages over gnome-screenshot?

---

### Post by mario.kemper on 2008-07-18
> **wersdaluv said:**
> What are its advantages over gnome-screenshot?

[LIST]
[*]Grab a selected area
[*]Grab a screenshot of a website
[*]Manage your screenshots during a session
[*]manipulate screenshots directly through plugins (drop shadow, grayscale, effects etc.)
[*]upload your screenshots to image-hosters
[*]print them directly
[*]draw to them using the embedded drawing tool
[*]open your screenshot automatically with a program of your choice
[*]automatically generate thumbnails
[/LIST]

Is there any special feature you are missing?

---

### Post by wersdaluv on 2008-07-18
> **mario.kemper said:**
> [LIST]
[*]Grab a selected area
[*]Grab a screenshot of a website
[*]Manage your screenshots during a session
[*]manipulate screenshots directly through plugins (drop shadow, grayscale, effects etc.)
[*]upload your screenshots to image-hosters
[*]print them directly
[*]draw to them using the embedded drawing tool
[*]open your screenshot automatically with a program of your choice
[*]automatically generate thumbnails
[/LIST]

Is there any special feature you are missing?
Thanks. I'll try it. Gnome-screenshot works for me so I was wondering if it's worth installing gscrot. I just installed it though so I'll see it for myself. :)

---

### Post by Exsecrabilus on 2008-07-18
Major letdown of gnome-screenshot is when you choose to take a active-window-only screenshot and you are running Emerald, it doesn't include the window borders no matter what you do.

I was hoping this had a "Take screenshot of the current window" feature and fixed the issue?

---

### Post by mario.kemper on 2008-07-18
> **Exsecrabilus said:**
> Major letdown of gnome-screenshot is when you choose to take a active-window-only screenshot and you are running Emerald, it doesn't include the window borders no matter what you do.

I was hoping this had a "Take screenshot of the current window" feature and fixed the issue?

You just have to activate the option "window border" in the advanced settings of gscrot and grab a screenshot with selection. When you just click on a specified window you'll get the window including the window borders.

---

### Post by Exsecrabilus on 2008-07-19
Thanks, this is one of the few, new applications for Linux I've seen that has an easy-to-install/use DEB package/repo.

---

### Post by MaxIBoy on 2008-07-19
The timer feature is excellent, I've been looking for something like that.


You think you could get this into the repositories?

---

### Post by MaxIBoy on 2008-07-19
Installing troubles:

---

### Post by mario.kemper on 2008-07-20
> **MaxIBoy said:**
> Installing troubles:
Please add the repo 

deb [http://ppa.launchpad.net/gscrot/ubuntu](http://ppa.launchpad.net/gscrot/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/gscrot/ubuntu](http://ppa.launchpad.net/gscrot/ubuntu) hardy main

to your apt sources (/etc/apt/sources.list) and use the following command to install gscrot and the plugins:

*sudo apt-get update && sudo apt-get install gscrot*


In the next version there will be only one package, because it is much easier to handle.

---

### Post by sportman1280 on 2008-07-20
Very cool tool.  The website capture is very handy :)

---

### Post by mario.kemper on 2008-07-27
:arrow: Release of GScrot v0.40 is available!

[https://launchpad.net/gscrot/+announcement/747]("https://launchpad.net/gscrot/+announcement/747")
Download: [https://launchpad.net/~gscrot/+archive]("https://launchpad.net/~gscrot/+archive")

The plugins package is now **included** and will be replaced during the installation of the new deb.


We are still discussing the name of the project. So, what do you think? 
I would not discuss the name but if the name prevents the success of the project , we must do something.
I would prefer "Cast" or "GCast".

---

### Post by Exsecrabilus on 2008-07-27
> **mario.kemper said:**
> :arrow: Release of GScrot v0.40 is available!

[https://launchpad.net/gscrot/+announcement/747]("https://launchpad.net/gscrot/+announcement/747")
Download: [https://launchpad.net/~gscrot/+archive]("https://launchpad.net/~gscrot/+archive")

The plugins package is now **included** and will be replaced during the installation of the new deb.


We are still discussing the name of the project. So, what do you think? 
I would not discuss the name but if the name prevents the success of the project , we must do something.
I would prefer "Cast" or "GCast".
GCast. Win.

---

### Post by Samizdat on 2008-08-06
Mario, my man, great tool, thank you!  The bed-<snip> too lazy to thank you, be damned.

Rick in Reno

---

### Post by mario.kemper on 2008-08-12
I am refactoring the backend of GScrot right now. 
It grows to be a standalone application and is no longer just a frontend for scrot.

I've ported the functionality of scrot and we will add further features (a desktop zoom during capturing is already implemented) in the future.


So, the name GScrot will be obsolete and GCast ist already used.


What do you (this is **especially a question to english native speakers**) think of **Gnapshot**?? Acceptable?

---

### Post by dmizer on 2008-08-13
Just used it on my new 64bit Xubuntu install.  Works like a charm.

Keep Gscrot as the name (even as a native English speaker).  Since you're using the time honored scrot as the backend for this, changing the name would be a disservice to both your project and scrot.  At the very least, keep the "scrot" base as part of the name.

I think the complaints about the name are both short sighted and uninformed.

---

### Post by binbash on 2008-08-13
Can you add a resize plugin? For instance resizing without keeping the aspect ratio to 100x70 etc ?

---

### Post by mario.kemper on 2008-08-17
> **binbash said:**
> Can you add a resize plugin? For instance resizing without keeping the aspect ratio to 100x70 etc ?
I'll put that on the list.

---

### Post by Exsecrabilus on 2008-08-17
> **mario.kemper said:**
> What do you (this is **especially a question to english native speakers**) think of **Gnapshot**?? Acceptable?
No.

---

### Post by mario.kemper on 2008-08-17
> **Exsecrabilus said:**
> No.
Ok ;-)
I think it is no longer an issue. Personally I've never had any problems with the name...

---

### Post by Exsecrabilus on 2008-08-20
> **mario.kemper said:**
> Ok ;-)
I think it is no longer an issue. Personally I've never had any problems with the name...
What's with 0.50? Link us to the announcement list of changes. Too lazy.

---

### Post by mario.kemper on 2008-08-20
> **Exsecrabilus said:**
> What's with 0.50? Link us to the announcement list of changes. Too lazy.

:arrow: Independence Day!! Release of GScrot v0.50 is available! 

[https://launchpad.net/gscrot/+announcement/919](https://launchpad.net/gscrot/+announcement/919)
Download: [https://launchpad.net/~gscrot/+archive](https://launchpad.net/~gscrot/+archive)


PS: We are looking for translators. If you have a few minutes left, please check [https://translations.launchpad.net/gscrot](https://translations.launchpad.net/gscrot) and help us to provide GScrot in different languages.

---

### Post by Firehalk on 2008-08-22
I was trying to replace the default Ubuntu Screenshot tool, for GScrot. So i actived the **binds** inside Gscrot, but when I press Print or Alt+Print, it opens the default tool.

I tried to disable the shortcuts on **Keyboards Shortcuts**, and leave enable just the binds on Gscrot, but still doesn't work (nothing happens when I click those keys).

Any ideas?

I have 3 days of Ubuntu, so maybe I'm doing something dumb and dunno.

Thanks!

---

### Post by mario.kemper on 2008-08-22
> **Firehalk said:**
> I was trying to replace the default Ubuntu Screenshot tool, for GScrot. So i actived the **binds** inside Gscrot, but when I press Print or Alt+Print, it opens the default tool.

I tried to disable the shortcuts on **Keyboards Shortcuts**, and leave enable just the binds on Gscrot, but still doesn't work (nothing happens when I click those keys).

Any ideas?

I have 3 days of Ubuntu, so maybe I'm doing something dumb and dunno.

Thanks!
Did you save your settings in GScrot after enabling the bindings? (File >> Save Settings)

---

### Post by Firehalk on 2008-08-25
Sorry the delay to answer.

Yes, it was just that. I'm used to Linux saving all automatically, and didn't think there was need to click somewhere else to save it.

Thanks a lot!

Btw, I'm not aware of what was already suggested, but one limitation that I encountered here was like: when I had some Skype little window opened (talking to someone), and selected to take SS of that area (with the "scissor" option), after I made it, it took screenshot of my desktop (which was at the background of that window). So its like, it's not detecting windows on top or something.

Well, just a feedback ;)

Overall this tool is great :D

---

### Post by binbash on 2008-08-25
i have the same issue.I CAN NOT bind a key to selection capture.I can not bind a key to print window also.Please fix bind keys section.There is a bug for sure.BTW i am using compiz-fusion it might be because of that.


Also i am still waiting for a resize plugin so i can uninstall gimp : )

---

### Post by petedct on 2008-08-26
Very nice. Seems like v0.50.1 loads faster than v0.50.0. If possible how about adding an option to save to pdf. The draw function is pretty cool too. More features here would be great also.

---

### Post by Firehalk on 2008-08-27
I dunno if it's interface limitation, but I discovered some new thing.

Let's say that I use the option "Always group windows" on may pannels. So, let's say now that I want to click and display some group of windows (for example, pidgin convos title bar), if I press to take SS, simply nothing happens.

In fact, this is a bug with menus. Let's say that I want to show to someone my start menu. If i click to open the start menu and then press **ALT + Print** to the "selection" screenshot, nothing will happen, which means it's impossible to take SS of just one menu. Well, not even fullscreen screenshot would work if I have some menu opened on my screen :(

Maybe it's a limitation, dunno.

---

### Post by mario.kemper on 2008-08-27
> **binbash said:**
> i have the same issue.I CAN NOT bind a key to selection capture.I can not bind a key to print window also.Please fix bind keys section.There is a bug for sure.BTW i am using compiz-fusion it might be because of that.


Also i am still waiting for a resize plugin so i can uninstall gimp : )

Please check your advanced compiz settings. It should look like this (Backend=GConf):
[[img]http://www.ubuntu-pics.de/thumb/2497/screenshot01NQ6Y9.png[/img]](http://www.ubuntu-pics.de/bild/2497/screenshot01NQ6Y9.png)

Metacity Keybindings are configured in GConf and Compiz should adopt this settings if configured properly.

Resize-Plugin: Would you please file a bug at [https://bugs.launchpad.net/gscrot]("https://bugs.launchpad.net/gscrot") ? Just to remember me ;-)

---

### Post by mario.kemper on 2008-08-27
> **Firehalk said:**
> I dunno if it's interface limitation, but I discovered some new thing.

Let's say that I use the option "Always group windows" on may pannels. So, let's say now that I want to click and display some group of windows (for example, pidgin convos title bar), if I press to take SS, simply nothing happens.

In fact, this is a bug with menus. Let's say that I want to show to someone my start menu. If i click to open the start menu and then press **ALT + Print** to the "selection" screenshot, nothing will happen, which means it's impossible to take SS of just one menu. Well, not even fullscreen screenshot would work if I have some menu opened on my screen :(

Maybe it's a limitation, dunno.
You can use a delay if you want to take a screenshot of your main-menu: Set up a delay (e.g. 5 seconds) >> press screenshot button >> open your menu >> wait ;-) >> screenshot will be taken

Maybe this is just a workaround...

Would you please file a bug at [https://bugs.launchpad.net/gscrot](https://bugs.launchpad.net/gscrot) for every bug/limitation you are discovering? It's quite hard to track all forums or communities.
 
Thank you very much.

---

### Post by Samizdat on 2008-08-28
[IMG]http://i52.photobucket.com/albums/g38/2Blac/screenshot01.png[/IMG]

(GScrot in action)

Awww, would you look at that generous Thanks:Thanked ratio.

---

### Post by binbash on 2008-08-28
i managed to get BINDINGS working.BUt there is a problem at the software.mouse selection is so slow it is quite impossible to capture correctly.I am using compiz fusion.

---

### Post by mario.kemper on 2008-08-30
Yes you are right. There is a performance issue with some machines. I am working on this right now.
I've opened a bug as well: [https://bugs.launchpad.net/gscrot/+bug/262263]("https://bugs.launchpad.net/gscrot/+bug/262263")

---

### Post by Pixel on 2008-08-30
I love it, I was thinking about writing a program very similar to this but you beat me to it :p

The only thing it needs is the ability to add your own custom locations to upload the images too.  If I could automatically have it upload to my webserver then I would be in heaven.

---

### Post by Exsecrabilus on 2008-08-31
> **Samizdat said:**
> [IMG]http://i52.photobucket.com/albums/g38/2Blac/screenshot01.png[/IMG]

(GScrot in action)

Awww, would you look at that generous Thanks:Thanked ratio.
Lol WTF? Made of win.

BTW, it's 134 now. :)

---

### Post by mario.kemper on 2008-09-01
Hey folks,

I've released a new version of GScrot today => 0.51. Here are the facts:

:idea: project: [https://launchpad.net/gscrot](https://launchpad.net/gscrot)

:arrow: announcement: [https://launchpad.net/gscrot/+announcement/984](https://launchpad.net/gscrot/+announcement/984)

:arrow: download: [https://launchpad.net/~gscrot/+archive](https://launchpad.net/~gscrot/+archive)


Cheers 
Romario


@binbash: This version should solve the performance problems you've reported. Btw, you have to save your keybindings again with this version because we changed the executable from gscrot.pl to gscrot.

@Pixel: Thanks for your feedback. What kind of server support would you prefer? ftp, upload to blogging systems like wordpress, anything else ? 
 
@Firehalk: Would you please check if the latest version fixes your problem(s)?

---

### Post by zugu on 2008-09-02
In my native Romanian language, "scrot" means "scrotum". Human language works in mysterious ways :))

---

### Post by Vadi on 2008-09-17
GScrot is awesome. Especially the "upload right inside the program" part.

---

### Post by onero on 2008-09-22
This is an awesome program, thanks! Just a request though, could you add an easy way to crop screenshots within the program? I realize that there's a select tool, but sometimes when capturing menus or the like, I need to set a delay and then capture the whole screen, after which I need to crop the image. It would be a huge help if I could just crop within GScrot :)

Also, this might be pushing it, but a text tool would be helpful as well :) Perhaps the Draw button could be renamed (Edit screenshot?) and include these functions (crop and text). In any case, thanks again!

---

### Post by saratchandra on 2008-09-23
Is there any way to generate thumbnails of multiple webpages?

---

### Post by mario.kemper on 2008-09-23
> **onero said:**
> Just a request though, could you add an easy way to crop screenshots within the program?

Also, this might be pushing it, but a text tool would be helpful as well :) Perhaps the Draw button could be renamed (Edit screenshot?) and include these functions (crop and text). In any case, thanks again!

Thanks for your ideas, onero. 
The requested features are already on the list for the next releases. We have to switch to an alternative technology here because the currently used widget (GnomeCanvas) is limited (e.g. to handle transparency properly). In fact this will take some time but i am sure that the needed features (crop images, draw primitives like rectangles, add text etc.) will be implemented in some of the next versions. 

btw, there will be a new major release 0.60 in the next few days (see [http://gscrot.ubuntu-projekte.de]("http://gscrot.ubuntu-projekte.de") for further information)


[QUOTE=saratchandra]
Is there any way to generate thumbnails of multiple webpages?
[/QUOTE]
What exactly do you mean? Autogenerate thumbnails of a list of websites (currently you can only capture one after the other)?

---

### Post by saratchandra on 2008-09-24
> **mario.kemper said:**
> 
What exactly do you mean? Autogenerate thumbnails of a list of websites (currently you can only capture one after the other)?

Yes, that is what I meant. Is it possible using the command line? Are you planning to add the feature in future versions?

---

### Post by mario.kemper on 2008-09-24
> **saratchandra said:**
> Yes, that is what I meant. Is it possible using the command line? Are you planning to add the feature in future versions?
Well, it is not planned in future versions but maybe we should consider doing it ;-)

But you can use gnome-web-photo directly using a simple perl script:
```


#! /usr/bin/perl

use strict;
use warnings;

open FILE, "./websites" or die $!;
my @websites = <FILE>; 
close FILE or die $!;

foreach (@websites){
	chomp;
	print "Capturing $_ ...\n";
	my $web_output = `gnome-web-photo --mode=thumbnail --format=png '$_' '$_.png'`;		
}

print "Finished!\n";



```

Put this code in an editor and save it (e.g. multi_webphoto.pl). It will open a file called "websites" in the same directory.

The file "websites" could look like this:
```


ubuntu.com
debian.org
opensuse.com


```

Finally you can execute the script:
```

perl ./multi_webphoto.pl

```

After capturing the thumbnails will be saved in the current directory.
Does this fit your needs?

Greetings
mario

---

### Post by saratchandra on 2008-09-24
Works great. Thanks:)

---

### Post by mario.kemper on 2008-09-25
Just want to let you know - GScrot 0.60 is available!

Project-Page: 
[https://launchpad.net/gscrot]("https://launchpad.net/gscrot")

Download: 
[https://launchpad.net/~gscrot/+archive]("https://launchpad.net/~gscrot/+archive")

Changelog:
[https://launchpad.net/gscrot/+announcement/1129]("https://launchpad.net/gscrot/+announcement/1129")

Greetings
Mario

---

### Post by binbash on 2008-09-25
Is slow screen capture @ selection mode fixed?

---

### Post by mario.kemper on 2008-09-25
> **binbash said:**
> Is slow screen capture @ selection mode fixed?
This is fixed since 0.51. Give it a try...

---

### Post by binbash on 2008-09-25
> **mario.kemper said:**
> This is fixed since 0.51. Give it a try...

Thanks i am going to give another try, especially after this bug fixed and new resize plugin added (i saw it at changelog 5 min ago)

---

### Post by binbash on 2008-09-25
Ok i tested it first there is still screen selection bug.

IT IS VERY SLOW WHEN CAPTURING flash files. (games movies etc)

Second,  the resize plugin does not allow custom ratio.

It is better than previous releases (a lot better) But with those bugs i will stick with gimp.Looking forward for next releases ;)

---

### Post by mario.kemper on 2008-09-25
> **binbash said:**
> 
IT IS VERY SLOW WHEN CAPTURING flash files. (games movies etc)

I'm sorry but i cannot reproduce this behavior on my machines and most of the users are not encountering any problems during selection. 
Can you please post a brief description of your hardware (especially processor and graphics-card)?

Maybe you can try to disable the zoom window (the little arrow next to the selection button). When zoom window is disabled the screen will be freezed during selection, this should improve speed.


> **binbash said:**
> 
Second,  the resize plugin does not allow custom ratio.

Just click on the "lock"-Button to release the ratio-lock.

---

### Post by binbash on 2008-09-26
> **binbash said:**
> Thanks i am going to give another try, especially after this bug fixed and new resize plugin added (i saw it at changelog 5 min ago)

> **mario.kemper said:**
> I'm sorry but i cannot reproduce this behavior on my machines and most of the users are not encountering any problems during selection. 
Can you please post a brief description of your hardware (especially processor and graphics-card)?

Maybe you can try to disable the zoom window (the little arrow next to the selection button). When zoom window is disabled the screen will be freezed during selection, this should improve speed.



Just click on the "lock"-Button to release the ratio-lock.


I tested  it on my notebook.

2gig ram , Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz, ati radeon hd 2400 , compiz enabled.

Thanks for the resize plugin, it works perfect now(resizing)

I disabled the zooming but it is still slow (around 2 secs delay to follow the mouse)

---

### Post by sdpimpy on 2008-09-26
Thank you for this app.

I was looking for something that would let me capture a region of a web page and this works perfectly.\\:D/

---

### Post by Exsecrabilus on 2008-09-27
For better integration with other GNOME applications, I suggest you change:
[list]**Edit -> Settings** to: **Edit -> Preferences**
**Help -> Info** to: **Help -> About**
**Help -> Ask a question** to: **Help -> Get Help Online...**
**Help -> Report a bug** to: **Help -> Report a Problem**
**Help -> Add a translation** to: **Help -> Translate this Application...**[/list]

And also remove shortcuts for the last three of the above items. Other GNOME applications don't have them.

Also change the order of Get Help Online..., Translate This Application..., and Report a Problem from:
[list]Get Help Online... (Ask a question)
Report a Problem ( Report a bug)
Translate This Application... (Add a translation)[/list]
to:
[list]Get Help Online...
Translate This Application...
Report a Problem[/list]

---

### Post by tommygunner on 2008-09-27
Nice tool! I had it installed and I didn't know it. It was in Accessories and not Graphics.

---

### Post by Vadi on 2008-09-27
Just like Ubuntu's screenshot tool is in Accessories, actually.

---

### Post by starcannon on 2008-09-27
[mario.kemper]("http://ubuntuforums.org/member.php?u=583793"),

Thanks, this is indeed an EXCELLENT screen grabber, finally something that does everything I want, and with no hassel; easy straight forward ability (the web screen grabber tool is worth the price of admission alone).

Thanks!

Rob, aka starcannon

---

### Post by mario.kemper on 2008-09-27
> **Exsecrabilus said:**
> For better integration with other GNOME applications, I suggest you change:
[list]**Edit -> Settings** to: **Edit -> Preferences**
**Help -> Info** to: **Help -> About**
**Help -> Ask a question** to: **Help -> Get Help Online...**
**Help -> Report a bug** to: **Help -> Report a Problem**
**Help -> Add a translation** to: **Help -> Translate this Application...**[/list]

And also remove shortcuts for the last three of the above items. Other GNOME applications don't have them.

Also change the order of Get Help Online..., Translate This Application..., and Report a Problem from:
[list]Get Help Online... (Ask a question)
Report a Problem ( Report a bug)
Translate This Application... (Add a translation)[/list]
to:
[list]Get Help Online...
Translate This Application...
Report a Problem[/list]

Good point, i'll change that.

> **binbash]
I tested it on my notebook.

2gig ram , Intel(R) Core(TM)2 Duo CPU T7250 @ 2.00GHz, ati radeon hd 2400 , compiz enabled.

Thanks for the resize plugin, it works perfect now(resizing)

I disabled the zooming but it is still slow (around 2 secs delay to follow the mouse) [/QUOTE]

Well, that should be enough to handle screencapturing  said:**
> 
Thanks, this is indeed an EXCELLENT screen grabber, finally something that does everything I want, and with no hassel; easy straight forward ability (the web screen grabber tool is worth the price of admission alone).

[QUOTE=sdpimpy]Thank you for this app.

I was looking for something that would let me capture a region of a web page and this works perfectly[/QUOTE]

[QUOTE=tommygunner]Nice tool![/QUOTE]

Nice that you alle like GScrot!

---

### Post by mario.kemper on 2008-10-09
Just want to let you know - GScrot 0.61 is available!

Project-Page:
[https://launchpad.net/gscrot](https://launchpad.net/gscrot)

Download:
[https://launchpad.net/~gscrot/+archive](https://launchpad.net/~gscrot/+archive)

Changelog:
[https://launchpad.net/gscrot/+announcement/1210](https://launchpad.net/gscrot/+announcement/1210)

Greetings
Mario

---

### Post by mario.kemper on 2008-10-22
GScrot 0.62 is available!

Project-Page:
[https://launchpad.net/gscrot](https://launchpad.net/gscrot)

Project-Blog:
[http://gscrot.ubuntu-projekte.de](http://gscrot.ubuntu-projekte.de)

Download:
[https://launchpad.net/~gscrot/+archive](https://launchpad.net/~gscrot/+archive)

Changelog:
[https://launchpad.net/gscrot/+announcement/1280](https://launchpad.net/gscrot/+announcement/1280)

Greetings
Mario

---

### Post by JemW on 2008-11-03
This is driving me nuts! I used GScrot in Hardy with no problem, but it absolutely refuses to start automatically in Intrepid. I have it added as a startup program with the &#8208;&#8208;min_at_startup switch, but nothing happens...!!

Run it manually - no problem.

Edit: the &#8208;&#8208;min_at_startup switch is the culprit it seems. No longer works. GScrot starts automatically without it, but maximized :(

---

### Post by ninocass on 2008-11-03
cant seem to bind to a key, is compiz at fault?

i have the backend set to gconf

---

### Post by mario.kemper on 2008-11-03
> **JemW said:**
> 
Edit: the &#8208;&#8208;min_at_startup switch is the culprit it seems. No longer works. GScrot starts automatically without it, but maximized :(

Please check my answer at [https://answers.launchpad.net/gscrot/+question/49977]("https://answers.launchpad.net/gscrot/+question/49977")

Does this solve your problem?

---

### Post by JemW on 2008-11-03
Yep. Thanks.

---

### Post by mario.kemper on 2008-11-03
> **ninocass said:**
> cant seem to bind to a key, is compiz at fault?
i have the backend set to gconf
This is the way my compiz settings look like (using intrepid):

GScrot:
1) [http://www.ubuntu-pics.de/bild/5160/screenshot_02_abHn34.png]("http://www.ubuntu-pics.de/bild/5160/screenshot_02_abHn34.png")

Compiz Preferences:
2) [http://www.ubuntu-pics.de/bild/5158/gconf_EQwbFD.png]("http://www.ubuntu-pics.de/bild/5158/gconf_EQwbFD.png")

Compiz Commands (General Options):
3) [http://www.ubuntu-pics.de/bild/5159/commands_89b94M.png]("http://www.ubuntu-pics.de/bild/5159/commands_89b94M.png")

The commands should be configured automatically. Anyone else having a problem with keybindings using compiz?

---

### Post by ninocass on 2008-11-04
ahh the setting says:

Capture with SELECTION

but when it takes the screen shot its using the SECTION method, so i can choose windows but not draw a selection box

---

### Post by mario.kemper on 2008-11-04
> **ninocass said:**
> ahh the setting says:

Capture with SELECTION

but when it takes the screen shot its using the SECTION method, so i can choose windows but not draw a selection box
Yes, that's a bit buggy, I know.

There is a beta version of GScrot v0.63 available at out Testing-PPA:
[https://launchpad.net/~gscrot-testing-team/+archive]("https://launchpad.net/~gscrot-testing-team/+archive")

Just add the related apt sources.list entries to your software sources or /etc/apt/sources.list file and update gscrot (you can select your specific ubuntu release: gutsy, hardy, intrepid).

```
sudo apt-get update && sudo apt-get install gscrot
```

There is an option to select the keybinding-mode in this version this should help you to configure your keybindings properly.


But please keep in mind that it is still **beta**...

---

### Post by mario.kemper on 2008-11-09
GScrot 0.63 is available!

Project-Page:
[https://launchpad.net/gscrot](https://launchpad.net/gscrot)

Home page:
[http://gscrot.ubuntu-projekte.de/](http://gscrot.ubuntu-projekte.de/)

Download:
[https://launchpad.net/~gscrot/+archive](https://launchpad.net/~gscrot/+archive)

Changelog:
[https://launchpad.net/gscrot/+announcement/1400](https://launchpad.net/gscrot/+announcement/1400)

Greetings
Mario

---

### Post by Samizdat on 2008-11-10
When I started GScrot, my entire desktop darkened a bit, then the only thing I was able to do was move my cursor around and draw rectangles with left-click.

No keys worked, no right-click worked, nor left-click on anything except GScrot, to the point that the program forced me to turn off my computer with the power switch in back.  You know -- the thing they say never to do if you want to avoid damage?

Any idea why the program did this?  Until I have a clear idea, I'm not touching GScrot again any time soon.

---

### Post by Vadi on 2008-11-10
When you just started it, or wante to take a selection screenshot?

---

### Post by mario.kemper on 2008-11-10
> **Samizdat said:**
> 
No keys worked, no right-click worked, nor left-click on anything except GScrot, to the point that the program forced me to turn off my computer with the power switch in back.

Sounds like you used the selection tool. There is a short hint displayed at the beginning ("Press Enter to take the screenshot, Escape to cancel"). Maybe you've "clicked it away" by accident.

Enter and Escape didn't work? Anyway, there is no need to switch off your computer because you can even kill the x-session by hitting Ctrl+Alt+Backspace.

I am sorry for your inconvenience, but i am pretty sure that there is a simple answer to this. Maybe you can just try it again and tell us exactly what you've done when this happens again.

---

### Post by quickfished on 2008-11-11
Excellent tool, nice plugins (but I haven't tried them all).  The only thing I'm missing is Undo after applying a plugin.
But anyway, great app.

---

### Post by ciscosurfer on 2008-11-15
Great app! I especially like the ***Selection capture*** option, the ***Draw window***, and the ***Web capture*** tool...all are very nice.  

Here's my wish list:

[LIST=1]
[*]In additon to the freehand tool that is default on the *draw* window, perhaps including **rectangle, circle, and ellipsis** tools that are also bound to the chosen width properties (if a nifty rectangular option were available...well, that would just be really cool :-D)
[*]Inclusion of a **clear** or **undo** button on the *draw* window
[*]The ability to _maximize_ the *draw *window to the size of the given capture (not just scroll)
[/LIST]
Keep up the great work!

---

### Post by inobe on 2008-11-15
for you fellas that like cli

in terminal

```
gnome-screenshot
```

thats a snapshot of your entire desk, do you just want the window ?

```
gnome-screenshot --window
```

some more stwitches

```
--delay=seconds
--include-border
--border-effect=shadow
--border-effect=border

```

```
 gnome-screenshot --help
Usage:
  gnome-screenshot [OPTION...] Take a picture of the screen

Help Options:
  -?, --help                     Show help options
  --help-all                     Show all help options
  --help-gtk                     Show GTK+ Options
  --help-bonobo-activation       Show Bonobo Activation options
  --help-gnome                   Show GNOME options
  --help-gnome-session           Show session management options

Application Options:
  -w, --window                   Grab a window instead of the entire screen
  -b, --include-border           Include the window border with the screenshot
  -B, --remove-border            Remove the window border from the screenshot
  -d, --delay=seconds            Take screenshot after specified delay [in seconds]
  -e, --border-effect=effect     Effect to add to the border (shadow, border or none)
  -i, --interactive              Interactively set options
  --display=DISPLAY              X display to use

```


okay, ya created a png image, i say lets convert it to jpg .

if the image is on your desktop' right click desktop and open terminal, if terminal is already open do' cd your desktop.

in terminal do

```
convert screenshot.png screenshot.jpg
```

i like this way because its fast and affective.

---

### Post by mario.kemper on 2008-11-17
> **quickfished said:**
> Excellent tool, nice plugins (but I haven't tried them all).  The only thing I'm missing is Undo after applying a plugin.
But anyway, great app.

> **ciscosurfer said:**
> Great app! I especially like the Selection capture option, the Draw window, and the Web capture tool...all are very nice.

Here's my wish list:

   1. In additon to the freehand tool that is default on the draw window, perhaps including rectangle, circle, and ellipsis tools that are also bound to the chosen width properties (if a nifty rectangular option were available...well, that would just be really cool )
   2. Inclusion of a clear or undo button on the draw window
   3. The ability to maximize the draw window to the size of the given capture (not just scroll)

Keep up the great work!

Thanks! I am glad you like GScrot. 
If you have any nice idea/feature request/bug please feel free to file a bug at launchpad: [https://bugs.launchpad.net/gscrot/+filebug](https://bugs.launchpad.net/gscrot/+filebug)

Greetings
Mario

---

### Post by hzFVOW00pw on 2009-03-02
I installed gscrot and edited my gconf settings to start gscrot upon pressing the print key. The first time I pressed the print key gscrot started allright, but when I pressed the key a second time there was an attempt to start gnome-screenshot (which I did not have installed, so I got an error message).

When I configure the keybindings from gscrot all is OK. But when you configure gscrot to not use the keybindings it will automatically set the default gnome-screenshot in gconf.

Maybe a message in the options screen would be appropriate. There are lots of threads about setting a different screenshot program with gconf editor, so I guess most people try it that way first after installing gscrot.

---

### Post by Vadi on 2009-03-02
Thanks, that's an interesting use case we didn't think of.

---

### Post by Vadi on 2009-03-05
Small FYI, GScrot has been renamed to Shutter, and a new release is available: [http://shutter-project.org/2009/03/shutter-070-released/](http://shutter-project.org/2009/03/shutter-070-released/)

---

