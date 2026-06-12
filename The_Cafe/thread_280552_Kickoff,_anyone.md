---
title: "Kickoff, anyone?"
date: 2006-10-19
forum: The Cafe
---

### Post by Castar on 2006-10-19
Look what I've found [here]("http://forum.beryl-project.org/topic-4751-kickoff-dapper-packages")...

Install by using

```
sudo dpkg -i kicker-kickoff_1_i386.deb
```

and restart KDE.

If you don't mind the openSUSE icon and the crude (at least in my system) graphics, go on! Give it a go! It works! :cool:

EDIT: I've managed to get screenshots. Sorry for the greek ;). Enjoy.

---

### Post by awakatanka on 2006-10-20
Nice one going to try it.

---

### Post by jakster on 2006-10-22
I updated the package!

Now with nice Icons, should work better dropped down and so on (SVN update+some patches)

---

### Post by Castar on 2006-10-22
Excellent work. It works flawlessly now. 

One suggestion: do you think that the Kubuntu logo can be resized to match the panel's size automatically?

Thank you! :)

---

### Post by H.E. Pennypacker on 2006-10-22
What about Gnome users?  Can we have our own version of Kickoff?  I am not talking about the Slab, and USP (Ubuntu System Panel).

---

### Post by jakster on 2006-10-23
Don't think so, or you have to drop gnome-panel and use kicker instead (Kickoff is deeply integrated in kicker ATM).

I don't think the kubuntu logo is autosized, I'm only packaging not coding.. You can change the pictures if you like.

---

### Post by mips on 2006-10-23
Ok, I installed this package but lost my panel in the process ?

Any ideas ?

PS. I'm not running beryl, is this a requirement ?

---

### Post by Castar on 2006-10-23
Have you restarted KDE?

Can you check if you're running kicker?

---

### Post by mips on 2006-10-23
Ok cannot start kicker, looks like a dependancy issue.

```
mips@obelix:~$ sudo kicker
kicker: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by /usr/lib/libkdeinit_kicker.so)
```

---

### Post by jakster on 2006-10-23
Yeah the new version is linked against the edgy Libc so doesn't work anymore in dapper. 

You can do sudo aptitude reinstall kicker to go back I think

(or just dist-upgrade to edgy)

PS Don't run kicker as root!

---

### Post by mips on 2006-10-23
I'll just download the current build iso and install it, 3 days to final wont hurt.

---

### Post by weatherman on 2006-10-23
Cool I really the kickoff menu. A couple of remarks: 
- the kubuntu logo is indeed a little too big on my system
- I liked the "K" logo for the menu better
anyway thanks for your work!

---

### Post by mips on 2006-10-23
> **jakster said:**
> 
You can do sudo aptitude reinstall kicker to go back I think


That did not work for me. Not to worry as i also got fluxbox installed which is nice until the image has finished downloading which is in another 4hrs or so.

Nice to have a backup :)

---

### Post by maniacmusician on 2006-10-23
i'm pretty excited about edgy. I'm doing a server install and then installing the kde package this time. my only problem will be installing my card with ndiswrapper. I was worried I wouldnt be able to do it with just a command line, but I tried it on my laptop, and it worked like a charm. 

I still have to research how to do a seperate home partition and stuff, but no worries. It'll be good (methinks).

---

### Post by mips on 2006-10-23
> **maniacmusician said:**
> 
I still have to research how to do a seperate home partition and stuff, but no worries. It'll be good (methinks).

Before or during the install ?

If during then you can do it from the installer during the partitioning process. Create the partions and then set the mount points for /, /home, swap and whatever else you want. I usually do /, /boot, /home, swap.

This [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm) has some screenshots of the partitioning and setting mount points.

---

### Post by awakatanka on 2006-10-23
The preview show that i can do more than i can do with it. Is there a way to configure it our optimize it? Preview shows that it search the whole system, my kickoff search only personal files. Also the back button is in preview on top and with this version on the side. think top is a better place.

A pitty you use edgy now to compile it, some users are scared to use edgy atm.

But you doing a good job jakster to bring it to kubuntu. I wish i had those talents ;)

---

### Post by d3v1ant_0n3 on 2006-10-23
> **jakster said:**
> I updated the package!

Now with nice Icons, should work better dropped down and so on (SVN update+some patches)

I really like the update...Although now I have to have the panel set as 'normal' rather than 'small'. Ah well. Looks much better with the Kubuntu icon than the suse one- although I'd kinda got used to the lil chameleon hanging around on my desktop;) 

Seems to behave better with my color theme now too, which is nice:D 

Keep up the good work:D :D

---

### Post by maniacmusician on 2006-10-23
> **mips said:**
> Before or during the install ?

If during then you can do it from the installer during the partitioning process. Create the partions and then set the mount points for /, /home, swap and whatever else you want. I usually do /, /boot, /home, swap.

This [http://users.bigpond.net.au/hermanzone/p14.htm](http://users.bigpond.net.au/hermanzone/p14.htm) has some screenshots of the partitioning and setting mount points.
ah, cool! thanks a lot :) love how helpful we ubuntu people are. Yeah, i was going to do it during the install...but it's weird, because I have to do it on a different hard drive. I'll work out the dynamics later lol...but thanks for that link. 

Do i need a /boot partition? never had one, I don't think. And i have 1.5 GB of ram, so i'm not sure my swap ever gets used. Also, why was Logical chosen for the /home partition? couldn't it also have been a Primary? just wondering.

---

### Post by mips on 2006-10-24
> **maniacmusician said:**
> ah, cool! thanks a lot :) love how helpful we ubuntu people are. Yeah, i was going to do it during the install...but it's weird, because I have to do it on a different hard drive. I'll work out the dynamics later lol...but thanks for that link. 

Do i need a /boot partition? never had one, I don't think. And i have 1.5 GB of ram, so i'm not sure my swap ever gets used. Also, why was Logical chosen for the /home partition? couldn't it also have been a Primary? just wondering.

Yes you can make it primary, you don't need /boot, I would advise swap anyway, second drive is just as easy as it lists all drives/partitions.

We are hijacking the thread, best a new one is started.

Apologies to the OP.

---

### Post by jakster on 2006-10-24
Bad thread readers.

You can change the icon by replacing
/usr/share/apps/kicker/pics/kmenu_basic.mng
/usr/share/apps/kicker/pics/kmenu_active.png
/usr/share/apps/kicker/pics/kmenu_basic-vertical.mng

With another icon. They are the same file at the moment. If you have really nice icons or animation post them here :mrgreen:

---

### Post by Castar on 2006-10-24
That would be nice :)

---

### Post by d3v1ant_0n3 on 2006-10-24
Hmm...good idea...I've been wanting to play with the logo tools in the new gimp:D

*edit* I had a quick play, and came up with these- basic Kubuntu logo from the artwork wiki, ran thru' 'glossy' alpha to logo filter. Active icon has 'supernova' lighting effect added.

Backgrounds were stripped from both to allow for transparency.

*NOTE* file 'kmenu_basic.png' will need renaming to 'kmenu_basic.mng'

---

### Post by mips on 2006-10-25
Ok, I managed to isntall it. i don't think i like it though, to big & to much clicking going on for my liking.

I'm sure other will enjoy it though. I'll leave it installed for a while and see how it goes though

Thanks

---

### Post by mips on 2006-10-25
Ok, uninstalled kickoff. Lost my panel again and had to reinstall kicker.

Just a heads up shuold anyone else encounter a similair problem.

---

### Post by jakster on 2006-10-26
You can always rightclick on the menu button and choose switch to KMenu style to go back, no need to uninstall then

---

### Post by mips on 2006-10-26
> **jakster said:**
> You can always rightclick on the menu button and choose switch to KMenu style to go back, no need to uninstall then

Thanks, was not aware of that. Which I had asked ](*,)

---

### Post by augied on 2006-11-15
Does anyone know of a way to tone down the animations in the all programs section?

---

### Post by msak007 on 2006-11-18
Wow that's awesome. Thanks for the link, I just installed it and love the new menu. I have a couple of questions / problems though...

1. Are there any official plans to include the menu in Feisty or future versions of Kubuntu?

2. Is the normal behavior for the menu to pop up on a mouseover, instead of clicking on the logo? Can this be changed?

3. When browsing though "All Programs", is there a way to move forward / backward through the menu with a mouseover, instead of clicking on the menu groups / categories and the back arrows repeatedly?

4. When I click on "Leave", the Hibernate / Suspend options normally available in the shut down menu are not available.

---

### Post by patrick295767 on 2006-11-18
It is cool . Thank you for your thread !

---

### Post by barsanuphe on 2006-11-18
Thats a nice replacement for the old K menu. I never use it much though, preferring to rely on judiciously placed shortcuts on my toolbar; however, with this new interface, i might be tempted to focus more on the main menu. 
Thanks for the link.

---

### Post by darkhatter on 2006-11-19
KDE 4 is suppose to have their own version of kmenu so I look forward to that.

---

### Post by chaosgeisterchen on 2006-11-19
I would really much appreciate to see Kickoff or a derivate of Kickoff as new default K-Menu in the upcoming major release of KDE. It would improve the usability of the desktop environment even more.

---

### Post by msak007 on 2006-11-21
> **msak007 said:**
> 2. Is the normal behavior for the menu to pop up on a mouseover, instead of clicking on the logo? Can this be changed?
Just in case nobody else has figured it out yet, I did find the option in the "Menus" dialog of the panel configuration. There's a new option added that says "Open menu on mouse hover" that enables / disables this option. But after a couple days of using this menu, I kinda like the mouse over action now :). I still wish there was an option for a "delayed mouse hover" for navigating the menus, where if you hover over a menu item for x seconds it expands that menu.

---

### Post by Castar on 2006-11-22
Is it possible to use in Dapper? I tried to install the .deb but my kicker went dead :confused:.

---

### Post by msak007 on 2006-11-23
Now I have another problem. There were 2 entries for Firefox in "My Favorites". I was able to remove one of them, but every time I try to remove the 2nd one Kickoff crashes and takes the whole panel with it. I get a KDE crash handler dialog, and then the panel reloads. A subsequent attempt crashes it again, but the panel never comes back. I tried uninstalling Kickoff, reinstalling Kicker, restarting, and reinstalling Kickoff. The Firefox entry is still there, and it continues to crash. Anyone know where that info is stored (config file)? I would like to delete that entry manually.

EDIT: OK I figured this one out as well. I edited **kickerrc** (in /home/<username>/.kde/share/config) and deleted all the entries I didn't want. When I tried to remove Firefox again, Kickoff / Kicker crashed again. It didn't come back, so I reloaded Kicker manually through Konsole and when it came back the entries were gone.

---

### Post by ButteBlues on 2006-11-23
The window class also needs changed for it. At the moment, the window class is a Dialog, which causes conflicts with Beryl, as that SHOULDN'T be the animation assigned to the "Start Menu", even though it is the one assigned to windows of that proper class.

The new window class should be DropDownMenu or Menu rather than Dialog.

---

### Post by msak007 on 2006-11-23
> **a simple façade said:**
> The window class also needs changed for it. At the moment, the window class is a Dialog, which causes conflicts with Beryl, as that SHOULDN'T be the animation assigned to the "Start Menu", even though it is the one assigned to windows of that proper class.

The new window class should be DropDownMenu or Menu rather than Dialog.
Not sure what you mean? I just installed and started running Beryl, and Kickoff works just fine - animations and all.

---

### Post by ButteBlues on 2006-11-23
> **msak007 said:**
> Not sure what you mean? I just installed and started running Beryl, and Kickoff works just fine - animations and all.
The Animation plugin utilizes two different animations for creations and closings of windows.

The first is called Create/Close Effect 1 and is used on regular windows etc.

The second is called Create/Close Effect 2 and is used by things like drop-down menus.


Right now, because the window class of the Kickoff is incorrect, Kickoff is opening under the former (and hence the Zoom animation rather than the Fade animation) when it should be doing the latter.

Furthermore, we can't just "move Dialog to the 2nd effect" because then things like 'About KDE' and such will also open under Fade rather than Zoom.

---

### Post by msak007 on 2006-11-23
Ahh...I get what you mean now. Sorry as this was my first foray into Beryl (which kicks ***!), and I hadn't gone through the many animation options. I do agree that needs to be corrected.

---

### Post by raid517 on 2006-11-30
Hi is this still available? The link to the Beryl forum post is down. I'm trying to compile the latest code from SVN for both Kubuntu and Debian Sid (different packages on different computers) but it keeps crapping out on the 'make' part of the process with some error about keditbookmarks:

```
test -z "/usr/share/config.kcfg" || mkdir -p -- "/usr/share/config.kcfg"
/usr/bin/install -c -p -m 644 'konq_listview.kcfg' '/usr/share/config.kcfg/konq_listview.kcfg'
test -z "/usr/share/services" || mkdir -p -- "/usr/share/services"
/usr/bin/install -c -p -m 644 'konq_treeview.desktop' '/usr/share/services/konq_treeview.desktop'
/usr/bin/install -c -p -m 644 'konq_detailedlistview.desktop' '/usr/share/services/konq_detailedlistview.desktop'
/usr/bin/install -c -p -m 644 'konq_textview.desktop' '/usr/share/services/konq_textview.desktop'
/usr/bin/install -c -p -m 644 'konq_infolistview.desktop' '/usr/share/services/konq_infolistview.desktop'
test -z "/usr/share/apps/konqlistview" || mkdir -p -- "/usr/share/apps/konqlistview"
/usr/bin/install -c -p -m 644 'konq_treeview.rc' '/usr/share/apps/konqlistview/konq_treeview.rc'
/usr/bin/install -c -p -m 644 'konq_detailedlistview.rc' '/usr/share/apps/konqlistview/konq_detailedlistview.rc'
/usr/bin/install -c -p -m 644 'konq_textview.rc' '/usr/share/apps/konqlistview/konq_textview.rc'
/usr/bin/install -c -p -m 644 'konq_infolistview.rc' '/usr/share/apps/konqlistview/konq_infolistview.rc'
make[3]: Leaving directory `/home/raid517/suse_kickoff/konqueror/listview'
make[2]: Leaving directory `/home/raid517/suse_kickoff/konqueror/listview'
Making install in keditbookmarks
make[2]: Entering directory `/home/raid517/suse_kickoff/konqueror/keditbookmarks'
make[2]: *** No rule to make target `/usr/include/kbookmarknotifier.h', needed by `kbookmarknotifier.kidl'.  Stop.
make[2]: Leaving directory `/home/raid517/suse_kickoff/konqueror/keditbookmarks'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/raid517/suse_kickoff/konqueror'
make: *** [install-recursive] Error 1 
```

Is there any way to build the package without keditbookmarks?

---

### Post by darkasecas on 2006-12-03
> **raid517 said:**
> Hi is this still available? The link to the Beryl forum post is down. I'm trying to compile the latest code from SVN for both Kubuntu and Debian Sid (different packages on different computers) but it keeps crapping out on the 'make' part of the process with some error about keditbookmarks:

Hi I found the deb package in [this french forum ]("http://www.quebecos.com/modules/newbb/viewtopic.php?topic_id=2553&forum=24") :)

---

### Post by Rashid584 on 2006-12-23
Thanks for the link :D (to the french forum)

How do you integrate the search bit with Kerry? if I type the first few words of a filename it doesn't show up but just suggests opening a remote location :S

Good work novell/suse kde team ;)

-Rashid

---

### Post by Artemis3 on 2006-12-24
If this is what i think it is? (just tried it with [Sabayon Linux](http://www.sabayonlinux.org/) LiveDVD) i will say its annoying. Is this a new trend? Maybe some windows vista thingie?

This thing wastes a lot of screen space, and you need to click a lot more (to move in/out the submenus). As a gui trying to replace the current gnome/kde "start" like menu, it is much slower. On the other hand i can't also stand the time beryl takes to do its animations, i guess i'm used to instant response and can't go back anymore...

---

### Post by Rashid584 on 2006-12-24
you can always increase the speed of all beryl animations in beryl-settings

click on the "numeric values" tab for animations and slide everything to where you want it...

or if you're really scrooge-like and dont want animations...just turn them all off :)

Anyway i think kickoff is a *good idea* so far...it *definitely* needs more work...at least more choice. I agree that the method of browsing All Programs is far slower although I think the reasoning was that it will speed up the program you use most often (which it does)

The slower all programs mode is counter acted by the search functionarlity however...

OK iv gone on for a while...basically, good work, but needs a little more thought and improvement (speed wise) :up:

My list of things id like changed:

1. The wm_class needs to be fixed. It should be a menu not a dialogue
2. The names for tabs e.g. My Favourites and My Computer *need* to be changed to something better e.g. Favourites, System or something similar.
3. Needs to be made *much* faster...at the moment its a little bit sluggish
4. The All Programs method is nice but its slow...it should be turn-onable so you can have the rest of the kickoff style but a normal all programs mode somehow?
  4.5 I think the animations should be done with Beryl/aiglx? At the moment they are not very smooth...compositing would fix that. 
5. It needs to be fully themeable...most of the theme is done with images (which may be why its slow?? i dunno im not a coder)
6. The mouseover tooltip bug needs to be fixed...if i mouseover the icon the menu pops up for a split second but then the tooltip appears and the menu disappears. Very annoying...basically nullifies the one-click idea

-Rashid

---

### Post by brazzmonkey on 2007-01-18
it's in 3v1n0's repo and works fine here

---

### Post by sonoftheclayr on 2007-03-16
[http://news.softpedia.com/news/Install-Kickoff-KDE-Menu-in-Kubuntu-Ubuntu-46601.shtml](http://news.softpedia.com/news/Install-Kickoff-KDE-Menu-in-Kubuntu-Ubuntu-46601.shtml)
I'm using it and it works great! If you want to change the button image just rename the png's and mng's in /kicker/pics.
Personally I think it loads faster than the K Menu.

---

### Post by gijsterbeek on 2007-03-27
Though it is regarded as highly unethical, there are many people who want to mimic Vista artwork on their Ubuntu desktop. 

I guess their message is: "It has the same look and feel as Vista, but man, this one is free!". I do not have a problem with this. Therefore, These buttons *had* to be posted...

 [IMG]http://gijsterbeek.googlepages.com/kmenu_basic.png[/IMG][IMG]http://gijsterbeek.googlepages.com/kmenu_active.png[/IMG]

Please read usage instructions elsewhere in this post or [here]("http://gijsterbeek.googlepages.com/screenshots")
[IMG]http://http://gijsterbeek.googlepages.com/kmenu_active.png/kmenu_active-full.jpg[/IMG][IMG]http://http://gijsterbeek.googlepages.com/kmenu_basic.png/kmenu_basic-full.jpg[/IMG]

---

### Post by ButteBlues on 2007-03-27
> **gijsterbeek said:**
> Though it is regarded as highly unethical, there are many people who want to mimic Vista artwork on their Ubuntu desktop. 

I guess their message is: "It has the same look and feel as Vista, but man, this one is free!". I do not have a problem with this. Therefore, These buttons *had* to be posted...

 [IMG]http://gijsterbeek.googlepages.com/kmenu_basic.png[/IMG][IMG]http://gijsterbeek.googlepages.com/kmenu_active.png[/IMG]

Please read usage instructions elsewhere in this post or [here]("http://gijsterbeek.googlepages.com/screenshots")
[IMG]http://http://gijsterbeek.googlepages.com/kmenu_active.png/kmenu_active-full.jpg[/IMG][IMG]http://http://gijsterbeek.googlepages.com/kmenu_basic.png/kmenu_basic-full.jpg[/IMG]
In regards to your screenshots about shadows and Compiz, disable KDE's shadows on menus and such and they'll work right.

---

### Post by floke on 2007-05-06
Anyone know how to get rid of the 'Kub' in the menu - the link to the Kubuntu website?
It looks a bit naff, but I can't find it anywhere in the usr/share/apps/kicker folders to change it.

---

### Post by mech7 on 2007-05-06
Does this work on gone without beryl too? looks like allot better menu then the normal one.

---

### Post by Castar on 2007-05-06
It doesn't need beryl at all.

---

### Post by floke on 2007-05-07
So it seems that I have something missing from the kickoff menu - the Kubuntu bit only shows as 'Kub' - Any idea how I resize it, or even better, get ride of it?

Cheers

EDIT ** All Sorted! Just found the resize (top right and not completely obvious!) **

---

### Post by hrabeX on 2007-07-13
please could anybody give me a source code to build my own package for AMD64?thx.

---

### Post by JackieBrown on 2007-10-06
You have to build half of kde for it. 

I keep hoping someone smarting than me will package it for amd64 but its been a ong time coming

---

