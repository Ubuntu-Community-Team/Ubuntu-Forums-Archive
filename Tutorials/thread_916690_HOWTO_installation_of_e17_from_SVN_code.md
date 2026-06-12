---
title: "HOWTO: installation of e17 from SVN code"
date: 2008-09-11
forum: Tutorials
---

### Post by Rui Pais on 2008-09-11
Hi all. 

This HowTo propose a simple way to install a fresh and stable enlightenment, known as e17, compiled and updated from source, on Ubuntu or any Debian based distro.It's based on the SVN source repo

All it's done automatically from a single deb package, based
on a famous script, **easy_e17.sh** from [morlenxus]("http://omicron.homeip.net"), one of the e17 developers. 
This script it's well known for it's developer care for quality and continued maintenance, made it one of the best available (besides the fact that it's the one used "inside" for e developers tests).

**This package should work with (X/K/Edu/G)Ubuntu from Edgy to Karmic (Dapper has dependency issues with some old libs and should be avoid) as with Debian and any recent Debian derivative. **


 **WARNING: **
[COLOR="DarkRed"]  [B]This method it's not compatible with OpenGEU/Geubuntu, Maryan linux, elive, old gOS 
or others distros with an already implemented e17. 
  Please do not try it with those distros.[/B][/COLOR]

So, what's the advantage of compile from source? well, 
[LIST]
[*]  you can be as updated as you wish, 
[*]  you can be as outdated as you wish (using the date or revision option you can go back to any specific date or revision... searching for specific features or avoiding a broken version)
[*]  you will have everything installed on /opt/ directory. That's the correct location for testing/beta software. It will not mix libs and apps from enlightenment with your system. It's easier to clean and make backups or even run different versions side by side.
[*] you can make your own Ubuntu flavor, by installing a minimal base system (like [MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD") or [ubuntulite]("http://ubuntulite.tuxfamily.org/?q=node/2")) and e17 over it.
[*]  you can set your own compile options.
[/LIST]

Essentially, what I propose is, reduce the number of available e apps to a minimum stable core, that gives the environment, 
and use apps more stable to the common tasks like file-manager, terminal, etc., available at repos.



**INSTALLATION**
Add the following repos to your /etc/apt/sources.list:
> deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main

To do it automatically, copy+paste the above to a command line:
```
 sudo sh -c "echo 'deb http://cafelinux.org/Downloads/oz-os tinwoodman main' >> /etc/apt/sources.list"
```
and add the authenticated key with:
```
wget -q http://cafelinux.org/Downloads/oz-os/key.asc -O- | sudo apt-key add -
```

Update the repos:
```
sudo apt-get update
```

Install e17 it with:
```
sudo apt-get install e17-svn
```
And thats all.
:)


**[COLOR="Lime"]NOTE[/COLOR]** To start enlightenment logout from your current Desktop Environment, and at Login Manger window 
choose: Options/Session > choose: Enlightenment.



**AN ALTERNATIVE METHOD (more control):**
If wanted compilation can be done after the installation of e17-svn. Just do _before_ install:
```
touch $HOME/_skip_easy_e17_install
```
and then:
```
sudo apt-get update && sudo apt-get install e17-svn
sudo easy_e17.sh -i
rm $HOME/_skip_easy_e17_install
```
Hope you enjoy it.
:)
__________________________________________

If you want to try some of my themes you can also install:
```
sudo apt-get install e17-themes
```


**UPDATES**
After installed updates are handle with:
```
sudo easy_e17.sh -u 
```

**If you have any issues either on install or updates please check the second post for tips and suggestions.**

[COLOR="DarkGreen"]**NOTE:**[/COLOR]
[COLOR="DimGray"]If you had already installed with the old manual method or using Morlenxus script directly, no problem, it is fully compatible.
[/COLOR]

If you later want to try other enlightenment apps not installed by this package, you need to edit config file at /etc/easy_e17.conf or create a new ~/.easy_e17.conf that will overwrite the defaults sets.
Please see TIPS and NOTES below and check.

**[COLOR="Green"]UPDATE FROM OLD METHOD[/COLOR]** 
Default path for downloaded code has changed to /var/cache/e17_src.


**REMOVE**
If you decided that e17 it's not for you you can remove it:
```
sudo apt-get remove e17-svn
```
or 
```
sudo apt-get remove --purge e17-svn
```
to delete all compiled/installed e17 files.

_____________________________________________

[COLOR="DimGray"]Don't forget to check the below section TIPS AND NOTES for any references on code breakage or specific issues of the moment 
(i will try to keep it updated)[/COLOR]
_____________________________________________



**STARTUP APPLICATIONS**
- Something very basic but not immediate is how to run an application automatically at start up.
One can edit the .order file under ~/.e/e/applications/startup/.order or just run from Main menu: 
**Settings -> Settings Panel -> Apps -> Startup Applications** and choose what we want.

If the desired app don't exist on the list you need to create a .desktop launcher for it first. 
At Enlightenment Configuration window, under Applications, there are an entry called 'New Application' to do exactly that :)
It's plain simple, so just 2 comments. 
New launchers will be create under ~/.local/share/applications/ and will have an unfriendly name like _new_app-1.desktop... you can change the name manually (from command line or a file manager) if you want.
 
One nice trick to control start up apps is to make a script, make it executable and then create a .desktop for it like described above. That way you just run one startup "app" that can launch what ever you want and how you want and editable with any text editor. Here an example (start oofice quick launcher and numlockX):
```
#!/bin/sh
# <- this symbol makes the line just a comment, remove it to launch the app:
        gnome-settings-daemon &
        # gnome-volume-manager &
        # ooffice -quickstart -nologo -nodefault &
```

**CONFIGURATION LOOK**
- Controlling the look of Applications is another aspect that it's not obvious. 
E17 Apps use it's own controls/widgets, but gtk apps don't know nothing about it. That means they will have the look (kind of ugly) of default gtk/gnome.

There are 2 ways of tweak this. 
1st way, if you have gnome or xfce installed, is simply run the daemons of those environment, **gnome-settings-daemon** or **xfce-mcs-manager** respectively, on startup (like described above). That will set the theme we choose for gnome/xfce for all gtk apps, runs some basic services and start a few things like screensaver. Appearance can then be tuned by running gnome-control-center or xfce-setting-show, according the daemon used.
The 2nd way is lighter. Simply create a file named: **.gtkrc-2.0.mine** on your home folder, that would control gtk look.
As an example of a possible .gtkrc-2.0 file:
```
 gtk-theme-name = "Human"
 gtk-icon-theme-name = "Tango"
 gtk-font-name = "Bitstream Vera Sans 11"
```

You can tune the icon theme used for menu and desktop icons on:
Settings > Settings Panel > Appearance > Icon theme (that won't change icon theme used by gtk apps, see tip above)

Hope that helps make your e17 even more beautiful :) 


-------------------


**TIPS AND NOTES:**

- On clean installs (no other DE) you will find that you have no Application menus.
On that case check my suggestions on [this post here]("http://ubuntuforums.org/showthread.php?p=4153905&highlight=menus#post4153905").

- If, for any reason, you need a previous version of e17, check here to get an idea on how to get it:
[http://ubuntuforums.org/showpost.php?p=2965800&postcount=461](http://ubuntuforums.org/showpost.php?p=2965800&postcount=461)
(I will elaborate on this tip, if svn tree get broken one of this days)

- You can install original skipped packages, by editing /etc/easy_e17.conf file, remove them from --skip list and do:
   **sudo easy_e17.sh --only=*<skipped_package_name>***

- A situation that sometimes arise is that we want an application not listed on script. 
What i do is simply add manually the app to the correct entry list on script (and check on script updates if that has been added or not)
Example: 
I like to use the old e17setroot to make and set my backgrounds (.edj files) from jpg pics. That app is part of the obsolete e_utils package. It still compiles fine, so i add it to "apps" list on easy_e17.sh and install it normally.

- You can turn icon desktops visibility on/off by loading/unloading 'File Manager' module (on Configuration menu). 

-------------------
For more information on e17, the Enlightenment Foundation Libraries and the applications that use them, please see: 
[http://www.enlightenment.org](http://www.enlightenment.org).

For browsing SVN code see here:
[http://trac.enlightenment.org/e/browser/trunk](http://trac.enlightenment.org/e/browser/trunk)


Information, themes, icons, eye-candy and alike:
[http://exchange.enlightenment.org](http://exchange.enlightenment.org) and [http://e17-stuff.org](http://e17-stuff.org)


[This Howto it's also in CafeLinux Forum (click here).]("http://cafelinux.org/forum/index.php/topic,1899.0.html")

I posted too a mini-how on how to edit/change/create an e17 theme.
[* check it here *]("http://ubuntuforums.org/showpost.php?p=3530286&postcount=57")
_________________________________________________
[COLOR="Red"]**THE BELOW HOW-TO IT'S ONLY FOR SPECIAL INSTALLATIONS AND REFERENCE PURPOSES.**[/COLOR]
THE DEB PACKAGE MAKE INSTALL PROCESS MUCH SIMPLER.

[latest_old_HOWTO.pdf]("http://cafelinux.org/forum/index.php?action=dlattach;topic=881.0;attach=2693")

_________________________________________________

---

### Post by Rui Pais on 2008-09-14
**[COLOR="DarkRed"]- KNOWN ISSUES -[/COLOR]**

.Recently updates brake due to intense changes on svn code tree, and some old packages being deprecated been moved to OLD section of tree. 
**_This should be corrected by latest update of e17-svn. _**
Please see post here for details:
[http://ubuntuforums.org/showpost.php?p=8057639&postcount=498](http://ubuntuforums.org/showpost.php?p=8057639&postcount=498)


**[COLOR="DarkGreen"]- ** NEWS ** -[/COLOR]**

- Systray it's now part of default ***e*** as inside module (no need of extra compilation).


[COLOR="Blue"]**- ** NOTES ** -**[/COLOR]

- The easy_e17 script used on e17-svn it's not the original from Morlenxus, but a patched version for OzOS.
Changes include:
 Downloads only selected needed packages (downloads less ~250Mb at least).
 Some different paths, to make it more compliant with Debian based paths.
 
- Some paths changed (either from old cvs as original easy_e17.sh script):
Source code it's now on: /var/cache/e17-src
Config file it's now on: /etc/easy_e17.conf

- You can overwrite default config options by editing default config file /etc/easy_e17.conf
or by creating a new file ~/.easy_e17.conf with your personal choices.

-OzOS users: [update procedure here]("http://cafelinux.org/forum/index.php?topic=69.msg554#msg554").

---

### Post by ubuuntu9897 on 2008-09-14
iget this error i really want to run e17 i heard it was very good:(

------------------------------- Easy_e17.sh 1.2.0.4-OzOS ------------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      [http://svn.enlightenment.org/svn/e/trunk](http://svn.enlightenment.org/svn/e/trunk)
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w
  Skipping:        engrave esmart enhance exml imlib2 edb scrot edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification 

  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks
- source checkout/update
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok
- 'automake' available ....... ok
- 'gcc' available ............ ok
- 'make' available ........... ok
- 'svn' available ............ ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok (path has been added to /etc/ld.so.conf.d/e17.conf)
- setting compile options .... ok
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
- checkout sources ...
   downloading eet source ...
   downloading evas source ...
   downloading ecore source ...
   downloading efreet source ...
   downloading embryo source ...
   downloading edje source ...
   downloading epsilon source ...
   downloading esmart source ...
   downloading emotion source ...
   downloading etk source ...
   downloading etk_extra source ...
   downloading ewl source ...
   downloading exml source ...
   downloading enhance source ...
   downloading e_dbus source ...
   downloading e source ...
   downloading entrance source ...
   downloading edje_editor source ...
   downloading edje_viewer source ...
   downloading elicit source ...
   downloading elitaire source ...
   downloading emphasis source ...
   downloading empower source ...
   downloading emprint source ...
   downloading ephoto source ...
   downloading estickies source ...
   downloading exhibit source ...
   downloading expedite source ...
   downloading exquisite source ...
   downloading E-MODULES-EXTRA source ...
   downloading MISC source ...
   downloading rage source ...
   downloading THEMES source ...

--------------------------------------------------------------------------------

-> PREPARING FOR PHASE 2...
------------------------------- Easy_e17.sh 1.2.0.4-OzOS ------------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      [http://svn.enlightenment.org/svn/e/trunk](http://svn.enlightenment.org/svn/e/trunk)
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w
  Skipping:        engrave esmart enhance exml imlib2 edb scrot edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification 

  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation
- apps-compilation and installation
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- eet ........................ ok          
- evas ....................... make   : [|]
ok          
- ecore ...................... ok          
- efreet ..................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.0.4-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running autopoint...
autopoint: *** cvs program not found
autopoint: *** Stop.
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/etk.log'!


Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by Rui Pais on 2008-09-14
ubuuntu9897 please see the KNOWN ISSUES section of the [2nd post]("http://ubuntuforums.org/showpost.php?p=5786141&postcount=2").

Thanks.

---

### Post by ubuuntu9897 on 2008-09-14
ugh i guess thats the problem any help?

---

### Post by binbash on 2008-09-14
Thanks i am going to try it at my virtual box

---

### Post by smartboyathome on 2008-09-14
Rui, that seems to be a problem with the package. :(

ubuuntu: try running this in a terminal and seeing if it works for you:
```
sudo easy_e17.sh --skip=etk
```
I haven't used easy_e17 in a while, though that should do it.

---

### Post by Rui Pais on 2008-09-14
> **ubuuntu9897 said:**
> ugh i guess thats the problem any help?

> **smartboyathome said:**
> Rui, that seems to be a problem with the package. :(

ubuuntu: try running this in a terminal and seeing if it works for you:
```
sudo easy_e17.sh --skip=etk
```
I haven't used easy_e17 in a while, though that should do it.


Well, the problem seems to be in etk source configuration that have an old reference to cvs as requirement. we should just have to wait till the code maintainer clean it.

Meanwhile it's just need:
```
sudo apt-get install cvs
```  

I dont' put it as a dependency, because that don't make much sense. Source requirement must be fixed, instead of create a dependency of cvs *after* it has been moved from cvs ;)

Just a note, smartboyathome, i don't think etk can be skipped, it's a fundamental library. But cvs can be safelly removed after etk been compiled.

hth


@binbash: Great. Let us know how it goes, ok?

---

### Post by ubuuntu9897 on 2008-09-14
It works now thanks guys
but i see not to have any programs to go with it form enlightment compared to genome or kde i guess. I happy with it hough still can use the old apps so im okay

---

### Post by smartboyathome on 2008-09-14
E17 doesn't have many apps, as there hasn't been much interest yet. It seems to be slowly picking up though. :)

---

### Post by Rui Pais on 2008-09-16
> **ubuuntu9897 said:**
> It works now thanks guys
but i see not to have any programs to go with it form enlightment compared to genome or kde i guess. I happy with it hough still can use the old apps so im okay

Glad to know you get work!


Please note that i tried to reduce the e applications to the minimum to avoid stability issues (as you may imagine, apps done for libs/environment with api code not frozen may suffer extra instability as the base code evolves). 
You can install extra apps anytime by editing the conf file at **/etc/easy_e17.conf** 


All other applications can of course be installed with apt/synaptic.
:)

---

### Post by nemlah on 2008-09-18
Thanks a lot for the work done. Worked very nice..

Is there a list with the state of the different modules right now. I would like to add some to the installation, can't find uptodate info on their stability though

Thanks again

---

### Post by SuperBo on 2008-09-18
Before the installation, My disk had 2.2 GB space left. But after install & remove, now it only has 1.8 GB space left. Although I deleted /var/cache/e17_src.

---

### Post by Rui Pais on 2008-09-18
> **nemlah said:**
> Thanks a lot for the work done. Worked very nice..

Is there a list with the state of the different modules right now. I would like to add some to the installation, can't find uptodate info on their stability though

Thanks again

Hi nemlah, glad you like it :)

I'm not sure but i think by modules you mean other e17 apps (eapps like some call it) and not the modules itself...
anyway, unfortunately there's no place with such a list, at leaste that i know.
You can try e17 mail lists i think... and you can check this thread, i usually put info when thinks broken (the ones installed by e17-svn usually get fixes in a few hours...) and cafelinux forum it's another place very e17 focus, me or Aubrey usually put alerts on code breakage.  

You can check whats going on code here:
[http://trac.enlightenment.org/e/browser](http://trac.enlightenment.org/e/browser) (browse trunk)

Anyway, remember that it's all installed in /opt/e17 so it's very easy to either clean as make backups. 
If you are interested you can try oz-e17-tools that have a nice e17 backup tool.

hope that helps somehow...

---

### Post by Rui Pais on 2008-09-18
> **SuperBo said:**
> Before the installation, My disk had 2.2 GB space left. But after install & remove, now it only has 1.8 GB space left. Although I deleted /var/cache/e17_src.

Yes, that's normal. Source code it's big (looks even bigger on SVN), around 0.5G with easy_17.sh version of e17-svn.
Original morlenxus version gives you the full trunk source with more ~250M.

If you want you can remove it. And update only after some large periods of time (1, 2 months)... 
Or maybe save/compress code tree, on /var/cache/e17_src, to a pen or external disc...

---

### Post by Tux Aubrey on 2008-09-19
Thanks Rui!

I have updated the related OzOS "How to" [**HERE**]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os") and tested it on a clean 32bit install of Xubuntu 8.04.1.  Everything went as expected except for an error installing the b_and_w theme right at the end of the build - apparently the ~/.e/e/themes directory had not been created first (it was there at the end of the install, but empty).  This is a very minor "bug" and I'm pretty sure the next time I update e17 it will install correctly.

Your backup and update scripts make this a "bullet-proof" but still bleeding edge e17 install!

---

### Post by baphomet420 on 2008-09-20
> **Tux Aubrey said:**
> Thanks Rui!

I have updated the related OzOS "How to" [**HERE**]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os") and tested it on a clean 32bit install of Xubuntu 8.04.1.  Everything went as expected except for an error installing the b_and_w theme right at the end of the build - apparently the ~/.e/e/themes directory had not been created first (it was there at the end of the install, but empty).  This is a very minor "bug" and I'm pretty sure the next time I update e17 it will install correctly.

Your backup and update scripts make this a "bullet-proof" but still bleeding edge e17 install!

I had the same problem, looked into it, its a stray line in the easy e17 script...  it removes the source files directory for b_and_w just before it tries to compile...

---

### Post by elli222 on 2008-09-20
hi!
Im using the original easy_e17 script version 1.20 and i cant compile eyesight for some reason, i taught someone here might be able to help,

error in script...
```
- eyesight ................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I../../src -I../../src/bin -DPACKAGE=\"eyesight\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/eyesight\" -DPACKAGE_PLUGIN_DIR=\"/opt/e17/lib/eyesight/plugins\" -DLOCALEDIR=\"/opt/e17/share/locale\" -Wall -Werror -g -I/opt/e17/include -I/opt/e17/include/efreet   -I/opt/e17/include   -MT error.o -MD -MP -MF .deps/error.Tpo -c -o error.o error.c
cc1: warnings being treated as errors
error.c: In function ‘append_startup_error’:
error.c:17: warning: implicit declaration of function ‘malloc’
error.c:17: warning: incompatible implicit declaration of built-in function ‘malloc’
error.c: In function ‘append_startup_error2’:
error.c:28: warning: incompatible implicit declaration of built-in function ‘malloc’
error.c: In function ‘display_startup_error_dialog’:
error.c:54: warning: implicit declaration of function ‘calloc’
error.c:54: warning: incompatible implicit declaration of built-in function ‘calloc’
cc1: warnings being treated as errors
main.c: In function ‘main’:make[3]: 
*** [error.o] Error 1
main.c:27: warning: implicit declaration of function ‘setlocale’
main.c:27: error: ‘LC_ALL’ undeclared (first use in this function)
make[3]: *** Waiting for unfinished jobs....
main.c:27: error: (Each undeclared identifier is reported only once
main.c:27: error: for each function it appears in.)
make[3]: *** [main.o] Error 1
make[3]: Leaving directory `/home/elliot/e17_src/PROTO/eyesight/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elliot/e17_src/PROTO/eyesight/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elliot/e17_src/PROTO/eyesight'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/eyesight.log'!

```

gonna try clearing my system of e17 and reinstall...

NOTE: ignoring errors isnt an option, and nor is skipping packages...

---

### Post by Tux Aubrey on 2008-09-20
> I had the same problem, looked into it, its a stray line in the easy e17 script... it removes the source files directory for b_and_w just before it tries to compile...

Great!  Thanks for the info - I'll pass it on to Rui.  

Others (and me) are also reporting errors when we try to do an update - but these seem to be on svn rather than in the scripts.  The errors are "fatal" to the update but don't cause problems with a good install.

---

### Post by whyette on 2008-09-22
I am running into a problem with the install. It seems to be a problem with dpkg, and now I can't install anything via comline.

I get an error that there's a 404 error when updating sources. 
```

 sudo dpkg --configure -a
Setting up e17-svn (0.9.4) ...

--------------------------- Easy_e17.sh 1.2.0.4-OzOS ---------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w
  Skipping:        esmart enhance exml imlib2 edb scrot edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification 

  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks
- source checkout/update
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok
- 'automake' available ....... ok
- 'gcc' available ............ ok
- 'make' available ........... ok
- 'svn' available ............ ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)
- setting compile options .... ok
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
- updating sources (please wait, this won't output much) ...
Checking eet source ... svn: REPORT request failed on '/svn/e/!svn/vcc/default'
svn: REPORT of '/svn/e/!svn/vcc/default': 400 Bad Request (http://svn.enlightenment.org)

```

Any ideas? It makes me run dpkg --configure -a whenever I want to install anything.

---

### Post by Rui Pais on 2008-09-22
> **Tux Aubrey said:**
> Great!  Thanks for the info - I'll pass it on to Rui.  

Others (and me) are also reporting errors when we try to do an update - but these seem to be on svn rather than in the scripts.  The errors are "fatal" to the update but don't cause problems with a good install.

Thank you for the reports.

Unfortunately that's a bad/buggy Makefile to build the theme, the only way would be patch it out after svn update... any changes would of course be lost on next update, so... :(

And it installs only at user level (not system wide) but with root ownerships!
 

I made a new e17-svn version that leave b_and_w out for the time been.
Users that want it must either remove it from skip list and fixes things by hand, keep it on skip, get the code and compile directly with build.sh script included (for edje_cc) or use the OzOS update_e17 tool to update that ensures sane install of the theme.

I'll keep an eye on it to see if Makefile gets fixed so i can put it back by default.

---

### Post by Rui Pais on 2008-09-22
> **whyette said:**
> I am running into a problem with the install. It seems to be a problem with dpkg, and now I can't install anything via comline.

I get an error that there's a 404 error when updating sources. 
```

 sudo dpkg --configure -a
Setting up e17-svn (0.9.4) ...

--------------------------- Easy_e17.sh 1.2.0.4-OzOS ---------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w
  Skipping:        esmart enhance exml imlib2 edb scrot edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification 

  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks
- source checkout/update
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok
- 'automake' available ....... ok
- 'gcc' available ............ ok
- 'make' available ........... ok
- 'svn' available ............ ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)
- setting compile options .... ok
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
- updating sources (please wait, this won't output much) ...
Checking eet source ... svn: REPORT request failed on '/svn/e/!svn/vcc/default'
svn: REPORT of '/svn/e/!svn/vcc/default': 400 Bad Request (http://svn.enlightenment.org)

```

Any ideas? It makes me run dpkg --configure -a whenever I want to install anything.

Hi, sorry to know you get problems :(

It sems that you can't get svn. We try to look at that later, now to fix dpkg.
Run:
```
touch $HOME/_skip_easy_e17_install
```
then
```
sudo apt-get update && sudo apt-get install e17-svn
```
That should fix the dpkg issue. (Let me know)


To check svn problem
What happens when you run this:
 ```
svn co http://svn.enlightenment.org/svn/e/trunk/eet
```
?

---

### Post by Rui Pais on 2008-09-22
> **elli222 said:**
> hi!
Im using the original easy_e17 script version 1.20 and i cant compile eyesight for some reason, i taught someone here might be able to help,

error in script...
```
- eyesight ................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
gcc -DHAVE_CONFIG_H -I. -I../..  -I../.. -I../../src -I../../src/bin -DPACKAGE=\"eyesight\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/eyesight\" -DPACKAGE_PLUGIN_DIR=\"/opt/e17/lib/eyesight/plugins\" -DLOCALEDIR=\"/opt/e17/share/locale\" -Wall -Werror -g -I/opt/e17/include -I/opt/e17/include/efreet   -I/opt/e17/include   -MT error.o -MD -MP -MF .deps/error.Tpo -c -o error.o error.c
cc1: warnings being treated as errors
error.c: In function &#8216;append_startup_error&#8217;:
error.c:17: warning: implicit declaration of function &#8216;malloc&#8217;
error.c:17: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
error.c: In function &#8216;append_startup_error2&#8217;:
error.c:28: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
error.c: In function &#8216;display_startup_error_dialog&#8217;:
error.c:54: warning: implicit declaration of function &#8216;calloc&#8217;
error.c:54: warning: incompatible implicit declaration of built-in function &#8216;calloc&#8217;
cc1: warnings being treated as errors
main.c: In function &#8216;main&#8217;:make[3]: 
*** [error.o] Error 1
main.c:27: warning: implicit declaration of function &#8216;setlocale&#8217;
main.c:27: error: &#8216;LC_ALL&#8217; undeclared (first use in this function)
make[3]: *** Waiting for unfinished jobs....
main.c:27: error: (Each undeclared identifier is reported only once
main.c:27: error: for each function it appears in.)
make[3]: *** [main.o] Error 1
make[3]: Leaving directory `/home/elliot/e17_src/PROTO/eyesight/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/elliot/e17_src/PROTO/eyesight/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/elliot/e17_src/PROTO/eyesight'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/eyesight.log'!

```

gonna try clearing my system of e17 and reinstall...

NOTE: ignoring errors isnt an option, and nor is skipping packages...


Hi elli222.

You must know that e17 it's pre-alpha code. Parts of the "official" tree code it's even more beyond that, either done for some api that meanwhile changed or just at prototype stage.
Thats the case of some folders inside the source tree, specially PROTO.
They are not suppose to be of any use unless you want to work (as a developer) on it.

Regrettably the original morlenxus script it's for a much advanced users (internal e17 devs) than the usual desktop users and get such things...

The app you mention it's from PROTO section and it's an exact illustration of that.
Just a quick look at error output shows some bad C code (not even related with e17) around malloc functions, even if you managed to compile you will face bad issues like memory leaks.

You are right, skipping packages are not an option, but a must, the only sane way :)

---

### Post by whyette on 2008-09-22
All fixed! Thanks! It's installed, I'm off to attempt it now!

---

### Post by whyette on 2008-09-22
One more issue (let's hope this is the last one). When I attempted to log in under enlightenment, I got an error saying "No exec line in enlightenment." It then loaded the failsafe Gnome.

I'm just interested in experimenting with Enlightenment, I'm a rather avid fan of Gnome, otherwise.

---

### Post by Rui Pais on 2008-09-22
> **whyette said:**
> All fixed! Thanks! It's installed, I'm off to attempt it now!

No problem, glad it's ok.
(That's a fragility of dpkg, when an install have a problem, sometimes a simple nonexistent path or a failure command, it can stay "broken" due to the unfinished package installation... )


> **whyette said:**
> One more issue (let's hope this is the last one). When I attempted to log in under enlightenment, I got an error saying "No exec line in enlightenment." It then loaded the failsafe Gnome.

I'm just interested in experimenting with Enlightenment, I'm a rather avid fan of Gnome, otherwise.

Ok. The above command make dpkg finish the installation, overpassing the issue, by skipping the e17 compilation. You shouldn't have e17 install it yet.

You need to see if it's a svn problem, if you get some broken revision  of the sources or have any network issue...

Can you tell me whats the output of:
```
ls /var/cache/e17_src/
```
?
If you have 26 folders, including one called "e", then try:
```
sudo easy_e17.sh -i
```
otherwise post here.

---

### Post by whyette on 2008-09-22
Only one item was listed under ls:

eet.

---

### Post by Rui Pais on 2008-09-23
> **whyette said:**
> Only one item was listed under ls:

eet.

Ah. so your previous installation aborted (for some reason...) at 1st package. But seems to at least connect to svn server.

I think the best option now would be clean any possible borked code and then install from new source:
```
sudo rm -rf /var/cache/e17_src
sudo easy_e17.sh -i
```

(check if you have cvs installed too, since there's an old dependency left on etk package that require it. It can be deleted after e17 installs) 

Hope it runs well this time!

---

### Post by djvantri on 2008-09-26
is there any way i can try out entropy ? i seemed to remember being able to use it when compiling from cvs awhile back, but now when i try
but running the script with only entropy doesnt seem to install.
Is ths because they moved the folder to OLD or something?
Thanks
Dave

---

### Post by smartboyathome on 2008-09-26
> **djvantri said:**
> is there any way i can try out entropy ? i seemed to remember being able to use it when compiling from cvs awhile back, but now when i try
but running the script with only entropy doesnt seem to install.
Is ths because they moved the folder to OLD or something?
Thanks
Dave

Yes, Entropy is old so it was moved to old. The script might be broken for those apps since they are in old.

---

### Post by djvantri on 2008-09-26
Is there anyway to change this to point to the new directory?

---

### Post by Rui Pais on 2008-09-26
> **djvantri said:**
> is there any way i can try out entropy ? i seemed to remember being able to use it when compiling from cvs awhile back, but now when i try
but running the script with only entropy doesnt seem to install.
Is ths because they moved the folder to OLD or something?
Thanks
Dave


Well since entropy it's a completed abandoned project naturally was moved to OLD. 
It will never get more updates so don't make much sense use a script for it (no updates<-> no maintaining need).

You can get it by hand (since you know theres an /OLD on trunk you should know it's path). 
Just svn co the code, autogen.sh --prefix=/opt/e17 && make && sudo make install.
Note that it depends now on old an equally unmaintained evfs, also in OLD. SO you'll need (at least) that one too...

NOTE: There's several posts on net where users reported random deletion (and complete lost) of files on they disk!!
Besides old, even if it compiles and run looks quite a too dangerous thing to have/play with.

---

### Post by djvantri on 2008-09-26
Oh, ok then, i dont think i will be installing... Is there another
file manager that is stable enough for e17 (other than all the gnome ones)
thanks
dave

---

### Post by Rui Pais on 2008-09-26
> **djvantri said:**
> Oh, ok then, i dont think i will be installing... Is there another
file manager that is stable enough for e17 (other than all the gnome ones)
thanks
dave

Nautilus it's the only gnome one... you mean gtk ones (like thunar and pcmanfm)?

Anyway, if size matters give a look at pcmanfm, it's very light and small, but somehow limited.

Rox it's very good. Excellent, in fact. Light, fast and super featured.

You can try internal e_fm, but it's kinda strange, buggy and very limited...

---

### Post by djvantri on 2008-09-26
sorry i meant other than gtk ones.
like is there another one that is replacing entropy?

---

### Post by Rui Pais on 2008-09-26
> **djvantri said:**
> sorry i meant other than gtk ones.

No prob :) that's what i thought.
Try rox, no gtk nor qt dependent. Very good.

Xfe it's another light one, very independent (although it looks a little to much to Window Manager)

> **djvantri said:**
> like is there another one that is replacing entropy?

It's build with one efm, but not very good. 
Enable it on:
Configuration > Modules > File Manager

hth

---

### Post by smartboyathome on 2008-09-26
> **Rui Pais said:**
> No prob :) that's what i thought.
Try rox, no gtk nor qt dependent. Very good.

Xfe it's another light one, very independent (although it looks a little to much to Window Manager)



It's build with one efm, but not very good. 
Enable it on:
Configuration > Modules > File Manager

hth

I don't know if you include it Rui, but if you do also enable the Path and Navigation toolbars for EFM, that helps me a lot.

---

### Post by djvantri on 2008-09-27
Just wondering if anyone else has tried itask ng...
because i was wondering how to turn the composite option off

---

### Post by TomeRaider2 on 2008-09-27
> **Rui Pais said:**
> 
Can you tell me whats the output of:
```
ls /var/cache/e17_src/
```
?
If you have 26 folders, including one called "e", then try:
```
sudo easy_e17.sh -i
```
otherwise post here.

I'm having the same issue...
Here is my ls output:
```
e
ecore
e_dbus
edje
edje_editor
edje_viewer
eet
efreet
elicit
elitaire
embryo
E-MODULES-EXTRA
emotion
emphasis
empower
emprint
enhance
entrance
ephoto
epsilon
esmart
estickies
etk
etk_extra
evas
ewl
exhibit
exml
expedite
exquisite
MISC
rage
THEMES


```

After running easy_e17.sh -i I get an error on etk here is the etk.log:

```
-------------------------------------------------------------------------------
EASY_E17 1.2.0.4-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running autopoint...
autopoint: *** cvs program not found
autopoint: *** Stop.

```

---

### Post by smartboyathome on 2008-09-27
You need to install CVS from the repos, and then compile. It says that because ETK still has a dependancy on CVS, which can only be resolved by installing CVS.

---

### Post by TomeRaider2 on 2008-09-27
Thanks. I guess I should have re-read the entire thead before I posted. It is working now.

---

### Post by djvantri on 2008-10-03
anyone know how to turn off itask ng using composite? i set the module
to one as described on the google code page, but now i want to set it back...any ideas?

---

### Post by smartboyathome on 2008-10-03
> **djvantri said:**
> anyone know how to turn off itask ng using composite? i set the module
to one as described on the google code page, but now i want to set it back...any ideas?

Go to Menu > Settings > Modules and disable Itask (from the right side). :)

---

### Post by djvantri on 2008-10-03
haha, sorry i meant how to use the itask ng again without having a composite manager turned on 
do i just take this line to turn it on :
enlightenment_remote -use-composite-set 1
but set it to 0?
thanks

---

### Post by smartboyathome on 2008-10-03
you can't use itask-ng without a compositor, or else you get a black box around it and as it's background.

---

### Post by djvantri on 2008-10-05
i ran it at first without composite, just doesnt look as nice
you only get the black box when you set the composite to 1 or whatever in the line i wrote above. i ended up keeping the composite on anyways, didnt slow down my computer that much it didnt look as nice when i took it off

---

### Post by jdinosaurus on 2008-10-06
i have a problem. I have ubuntu hardy, but i am using XFCE. the installation of e17-svn went well without any errors, but when i try to load enlightenment session from gdm it takes a lot of CPU and shows nice e17 splash screen for about 5 minutes; and when finally it's loaded, i have only empty desktop and i can't do anything. How can i fix it? :confused:

---

### Post by wangjiahua on 2008-10-07
Cindy, is this the thing you were looking for?
[www.liangdianup.com/computeraccessories_1.htm](www.liangdianup.com/computeraccessories_1.htm)
It's on the list of computer accessories and parts. They have the DVI video thing to convert that jap monitor to work with your other computer. Just about any other kind of wire adaptor, usb connectors, monitor extension wires, ps2 extention wires, and all kinds of female and male swap connectors and things that I think would help your shop. If that above link don't work then goto [www.lducompany.com](www.lducompany.com) and click on computer accessories. Let me know if that is what you need and give me your email address again.
:guitar::lolflag:

---

### Post by prof.morbius on 2008-10-13
I'm having what seems to be a new and different problem; I read the whole thread, and searches didn't turn anything up...

I followed the instructions in the first post, and everything went fine through the downloads and compilation of eet, but evas fails with the following:

```

checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EINA... configure: error: Package requirements (eina-0) were not met:

No package 'eina-0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EINA_CFLAGS
and EINA_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I'm at a loss here.  I tried deleting the /var/cache/e17_src directory and then invoking "easy_e17.sh -i", which reproduced the problem.  I'm just trying Enlightenment for the first time (and have a sick compulsion to install pre-release software), so I have no idea how to proceed (e.g., --skip seems risky if this is an EFL library, but I don't know if it is).

Any suggestions?

---

### Post by worldwithoutgurus on 2008-10-13
Core EFL libraries (evas, ecore...) now need eina to compile.
Just wait for the update...

---

### Post by Rui Pais on 2008-10-14
Hi all,

Yes, eina a new e17 package, was moved from proto a couple of days ago and now it's a dependency of some of the libs and main e.

I uploaded a new e17-svn (and oz-e17-tools) already set for that change a few minutes ago.
Regrettably due to the way my patched easy_e17.sh works and svn internals (and my short time at moment to digg the subject more)
users with an already installed e17 must have to redownload the all code again and recompile it.

Of course it won't affect new users.
Users with an already installed e17 can just recompile without desinstallation or extra complicated steps. No need to log out, go to console or anything.
Here the basic simple steps:

#get the new e17-svn
```
sudo apt-get update && sudo apt-get upgrade
```


#remove old code tree:
```
sudo rm -rf /var/cache/e17_src
```

#reinstall
```
sudo easy_e17.sh -i
```

(OzOS users preferably should run update_e17.sh)

should work without issues.

---

### Post by Tux Aubrey on 2008-10-14
> i have a problem. I have ubuntu hardy, but i am using XFCE. the installation of e17-svn went well without any errors, but when i try to load enlightenment session from gdm it takes a lot of CPU and shows nice e17 splash screen for about 5 minutes; and when finally it's loaded, i have only empty desktop and i can't do anything. How can i fix it?

This really sounds like a failed installation.

Enlightenment should not be taking so much cpu (here's my "top" - typically, unless an enlightenment dialog has focus and is processing, it should be very low on both cpu and memory)

```
 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND               
 6624 paul      20   0  238m  97m  25m S    2  4.8   0:47.52 firefox               
 5919 root      20   0 60956  27m 7924 S    1  1.4   1:06.19 Xorg                  
 6174 paul      20   0 70096  33m  12m S    1  1.6   1:02.32 enlightenment         
    1 root      20   0  2844 1692  544 S    0  0.1   0:01.14 init                  
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd              
```

Do you have any menus (right or left mouse click) on your desktop?

---

### Post by jdinosaurus on 2008-10-16
no i don't have any menus on the right click. i can drag the mouse but nothing happened. i can just see clean desktop.:(

---

### Post by gaspard.leon on 2008-10-16
Hi...

The below text should probably read:
"To do it automatically, copy+past**e** the **below** to a command line:"
> **Rui Pais said:**
> 
...
To do it automatically, copy+past the above to a command line:
```
 sudo sh -c "echo 'deb http://cafelinux.org/Downloads/oz-os tinwoodman main' >> /etc/apt/sources.list"
```
and add the authenticated key with:
```
wget -q http://cafelinux.org/Downloads/oz-os/key.asc -O- | sudo apt-key add -
```
[COLOR="SlateGray"][SIZE="1"]Please if you have any link to this method, please update it as soon as possible. Many Thanks.[/SIZE][/COLOR]
...

---

### Post by doorman on 2008-10-19
I have a "strange" problem with e17.

Everything was working fine until about a week ago when I updated e17 (unfortunately I can't remember the revision number at which the problem started manifesting itself).

I have 9 workspaces (yes, I'm a workspace masochist), and every once in a while when i want to move from the upper-left one (0,0) to its immediate right (1,0) or to the one diagonally (1,1), e17 (or X) just restarts, i.e., it acts as if i pressed Ctrl-Alt-Bksp. I tried to debug it a little bit but found no suspicious messages in the X log. It doesn't matter whether I want to navigate to the other workspace clicking on it in the pager or using the keyboard shortcuts...

Anyone ran into this problem or has a possible solution?

I switched to fluxbox for a while, but I want e17 back! I got addicted to it!

---

### Post by phishbone on 2008-10-21
I cant seem to get b_and_w installed with easy_e17.sh --only=b_and_w

Any suggestions?

Tried to edit the easy_e17.conf last night aswell and the theme showed up in the theme selector but wasnt functional

---

### Post by Cyberponcho on 2008-10-24
I'm trying to install 'lightnement on my laptop, running Gutsy but it keeps asking me to insert the cd on the drive... is this some sort of windows control thing? i thought i could just apt-get install and that's it :confused: anybody got an answer or sugestion? TIA :)

---

### Post by Daddy_Cavy on 2008-10-27
Hi all,

I've been running e17 on hardy for a while now, and wondered why I wasn't seeing any updates, till I saw you move from cvs to svn.

So I followed the steps to upgrade, removed e17_cvs installed e17_svn, still nothing new. I did use apt-get update and dist-upgrade.

So then I ran easy_e17.sh -u after rm the cache, and still no updates.

Odd I thought, so I ran easy_e17.sh -i and it started building, cool, till I got to exhibit, and got this build error,

<snip>
gcc -o exhibit exhibit_file.o exhibit_image.o exhibit_main.o exhibit_menus.o exhibit_sort.o exhibit_thumb.o exhibit_tab.o exhibit_slideshow.o exhibit_favorites.o exhibit_options.o exhibit_comment.o exhibit_comment_jpeg.o exhibit_model_wobbly.o  -L/opt/e17/lib /opt/e17/lib/libetk.so /opt/e17/lib/libecore_imf_evas.so /opt/e17/lib/libedje.so /opt/e17/lib/libecore_imf.so /opt/e17/lib/libembryo.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libeet.so /opt/e17/lib/libefreet.so /opt/e17/lib/libefreet_mime.so /opt/e17/lib/libecore_file.so -lssl -lcrypto /usr/lib/libcurl.so -lgssapi_krb5 /opt/e17/lib/libepsilon.so /opt/e17/lib/libengrave.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore.so /opt/e17/lib/libevas.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libeina.so  
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_append'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_data'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_remove'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_count'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_nth'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_free'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_last'
collect2: ld returned 1 exit status
make[3]: *** [exhibit] Error 1
make[3]: Leaving directory `/var/cache/e17_src/exhibit/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/exhibit/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/exhibit'
make: *** [all] Error 2

</snip>

Can anyone shed some light on this please?

I've checked cafelinux forums too and not found anything with this error.

PS What does 'exhibit' do and can I skip it?

---

### Post by Rui Pais on 2008-10-28
> **gaspard.leon said:**
> Hi...

The below text should probably read:
"To do it automatically, copy+past**e** the **below** to a command line:"

Done! Thanks.

> **jdinosaurus said:**
> no i don't have any menus on the right click. i can drag the mouse but nothing happened. i can just see clean desktop.:(

Hi. 
Are you sure your installation finished successfully? Do you have done it on a clean install (or do you have e17 installed before)?

Btw, did that happen with any mouse button or your left mouse click have the main menu?

---

### Post by Rui Pais on 2008-10-28
> **doorman said:**
> I have a "strange" problem with e17.

Everything was working fine until about a week ago when I updated e17 (unfortunately I can't remember the revision number at which the problem started manifesting itself).

I have 9 workspaces (yes, I'm a workspace masochist), and every once in a while when i want to move from the upper-left one (0,0) to its immediate right (1,0) or to the one diagonally (1,1), e17 (or X) just restarts, i.e., it acts as if i pressed Ctrl-Alt-Bksp. I tried to debug it a little bit but found no suspicious messages in the X log. It doesn't matter whether I want to navigate to the other workspace clicking on it in the pager or using the keyboard shortcuts...

Anyone ran into this problem or has a possible solution?

I switched to fluxbox for a while, but I want e17 back! I got addicted to it!

Hi, 
that should be in fact very annoying :(

I don't have a solution, and i never seen that (only similar behavior but with screensaver, so not related).

Maybe a svn bad time code. Have you tried update after that?

Or maybe some change on e (been a lot lately, with some modules breakage...) create some incompatibility with you configuration...
Try to remove, from another DE or from console and with all your e sessions closed, the folder ~/.e/e/config and then log in to e17 again, to see if it gets better.

good luck

---

### Post by Rui Pais on 2008-10-28
> **phishbone said:**
> I cant seem to get b_and_w installed with easy_e17.sh --only=b_and_w

Any suggestions?

Tried to edit the easy_e17.conf last night aswell and the theme showed up in the theme selector but wasnt functional

Hi, 
that's a know problem. 
The b_and_w it's configured (bad option by it's dev!) to install on user config folder, not on system. 
But themes on user folder must belong to user, and that don't happen because install it's done with root power.
You can either move ~/.e/e/themes/b_and_w.edj to /opt/e17/share/enlightenment/data/themes/
or run:
```
sudo chown $USER:$USER -R .e/e/themes/*
```
to make it teh correct ownership.
That last will be overwritten next time b_and_w updates.
You can install oz-e17-tools (an OzOS tool) with apt-get/synaptic and update by run sudo update_e17.sh instead of easy_e17.sh -u taht will check ownerships automatically on each update.

hth

---

### Post by Rui Pais on 2008-10-28
> **Cyberponcho said:**
> I'm trying to install 'lightnement on my laptop, running Gutsy but it keeps asking me to insert the cd on the drive... is this some sort of windows control thing? i thought i could just apt-get install and that's it :confused: anybody got an answer or sugestion? TIA :)

Sorry, don't quite understand... can you explain it differently :confused:

---

### Post by Rui Pais on 2008-10-28
> **Daddy_Cavy said:**
> Hi all,

I've been running e17 on hardy for a while now, and wondered why I wasn't seeing any updates, till I saw you move from cvs to svn.

Hi. Well, not me... e17 devs. 
I just forced to move with. 
(believe me i didn't like it a bit :()

> **Daddy_Cavy said:**
> 
So I followed the steps to upgrade, removed e17_cvs installed e17_svn, still nothing new. I did use apt-get update and dist-upgrade.

So then I ran easy_e17.sh -u after rm the cache, and still no updates.

Odd I thought, so I ran easy_e17.sh -i and it started building, cool, till I got to exhibit, and got this build error,

<snip>
gcc -o exhibit exhibit_file.o exhibit_image.o exhibit_main.o exhibit_menus.o exhibit_sort.o exhibit_thumb.o exhibit_tab.o exhibit_slideshow.o exhibit_favorites.o exhibit_options.o exhibit_comment.o exhibit_comment_jpeg.o exhibit_model_wobbly.o  -L/opt/e17/lib /opt/e17/lib/libetk.so /opt/e17/lib/libecore_imf_evas.so /opt/e17/lib/libedje.so /opt/e17/lib/libecore_imf.so /opt/e17/lib/libembryo.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libeet.so /opt/e17/lib/libefreet.so /opt/e17/lib/libefreet_mime.so /opt/e17/lib/libecore_file.so -lssl -lcrypto /usr/lib/libcurl.so -lgssapi_krb5 /opt/e17/lib/libepsilon.so /opt/e17/lib/libengrave.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore.so /opt/e17/lib/libevas.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libeina.so  
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_append'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_data'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_remove'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_count'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_nth'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_free'
/opt/e17/lib/libengrave.so: undefined reference to `evas_list_last'
collect2: ld returned 1 exit status
make[3]: *** [exhibit] Error 1
make[3]: Leaving directory `/var/cache/e17_src/exhibit/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/exhibit/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/exhibit'
make: *** [all] Error 2

</snip>

Can anyone shed some light on this please?

That strange indeed... but the move from cvs to svn didn't always go nicely on already installed enlightenment :( 
Anyway, recompile all (easy_e17.sh -i) it's in fact the best approach to that case.
In relation to your error, let me tell you that since the SVN moves that code has been changed and updated quite wildly, and bad days/revisions has been quite frequent (have the faintest idea why? had devs gone insane?... ) 
Usually the only solution it's wait a couple of hours/days and try again. Or go back to a date/revision that you know it works...

Sorry about it, but that's not in my hands, i suffer like you and any other user with e17 insane code updates... 

> **Daddy_Cavy said:**
> 
I've checked cafelinux forums too and not found anything with this error.

PS What does 'exhibit' do and can I skip it?

Exibit it's the file viewer of e17. Yes it can be skipped, no problem (if you don't know it you probably never use it anyway)

Your problem seems to be related with eina, a new lib package/dependency that recently moved to main trunk. Some stuff broke when that moved... till all dependencies on other packages get updated.

Good luck on updates.

---

### Post by Daddy_Cavy on 2008-10-29
Hey,

Ok thanks Rui, running new e17 now, very nice.

Maybe some pointers you can give me please.

For powermanagement I used KDE guidence py scripts, they worked good on hardy, but not in intrepid.

Does e17 have a module that works with HAL and powermanagement, ie suspending etc (as I'm using a lappy)?

And for wlan/eth management, I used KDE knetworkmanager, works good, but would like goto pure e17, so a module that works with NetworkManager?

:guitar:

---

### Post by Cyberponcho on 2008-10-31
> **Rui Pais said:**
> Sorry, don't quite understand... can you explain it differently :confused:

Nevermind Rui Pais, it was partly my own stupidity, i just had to uncheck the cd in the software sources :oops:, i just did and i'm right this minute installing enlightenment using the Easy_e17 script, will let you know how it goes once is done :)
Thank you for this excellent and helpful thread.

---

### Post by jdinosaurus on 2008-11-03
Where can see the e17 boot log or something like that? i couldn't find anything in /var/log/* 
I followed the guide and installation finished successfully but I still cannot start e17. (It looks like it just freezes half way ...) 
Thank a lot for the help in advance!

---

### Post by cracks on 2008-11-04
~ [COLOR="Blue"]The most incredible and really unbelievable dream has become true:
You compiled e17 successfully![/COLOR] ~

This Script worked perfectly (after adding CVS for the etk issue), and I just wanted to pass on my sincere thanks for all your hard work.

I'm no stranger to Enlightenment, having run e16 on many different distros before, but this was **by far** the easiest install ever.  Great job, thanks!

---

### Post by Tux Aubrey on 2008-11-05
> **jdinosaurus said:**
> Where can see the e17 boot log or something like that? i couldn't find anything in /var/log/* 
I followed the guide and installation finished successfully but I still cannot start e17. (It looks like it just freezes half way ...) 
Thank a lot for the help in advance!

I'm not sure where to start, but see if there any clues in ~/.xsession-errors to see what fails during boot.

This could be one of those "bad code day" problems, in which case you need to re-download and compile (deleting /var/cache/e17_src and running

```
easy_e17.sh -i
```

---

### Post by jdinosaurus on 2008-11-06
Thank you very much Tux Aubrey for the response! I will try to make a clean install again. By the way, just to make sure - I suppose there will not be a problem if i use currently the e16?

---

### Post by nikk^ on 2008-11-06
Hi!

I had no problems with installing E17. Everything went shmoothly. But I have problems to install engage.

I tried it, how it was described here:


- You can install original skipped packages, by editing /etc/easy_e17.conf file, remove them from --skip list and do:
sudo easy_e17.sh --only=<skipped_package_name>.

I delete the entry in the "skip list", but if i run the script like this: easy_e17.sh --only=engage, the scripts starts and goes through the steps, but doesn't compile or install anything:

```
----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17                                                     
  Source path:     /var/cache/e17_src                                           
  Source url:      http://svn.enlightenment.org/svn/e/trunk                     
  Logs path:       /tmp/easy_e17/install_logs                                   

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w                                             
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt enthrall rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification b_and_w                                                 
  Only:            engage                                                       

  Script action:   only
--------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks                                              
- source checkout/update                                                        
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok                                               
- 'automake' available ....... ok                                               
- 'gcc' available ............ ok                                               
- 'make' available ........... ok                                               
- 'svn' available ............ ok                                               
- build-user ................. root                                             
- adding path to env ......... ok                                               
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)                  
- setting compile options .... ok                                               
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
--------------------------------------------------------------------------------

--------------------------- Easy_e17.sh 1.2.1.1-OzOS ---------------------------
  Developers:      Brian 'morlenxus' Miculcy                                    
                   David 'onefang' Seikel                                       
  Contributors:    Tim 'amon' Zebulla                                           
                   Daniel G. '_ke' Siegel                                       
                   Stefan 'slax' Langner                                        
                   Massimiliano 'Massi' Calamelli                               
                   Thomas 'thomasg' Gstaedtner                                  
                   Roberto 'rex' Sigalotti                                      

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17                                                     
  Source path:     /var/cache/e17_src                                           
  Source url:      http://svn.enlightenment.org/svn/e/trunk                     
  Logs path:       /tmp/easy_e17/install_logs                                   

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w                                             
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt enthrall rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification b_and_w                                                 
  Only:            engage                                                       

  Script action:   only
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation                                              
- apps-compilation and installation                                             
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- eina ....................... SKIPPED                                          
- eet ........................ SKIPPED                                          
- evas ....................... SKIPPED                                          
- ecore ...................... SKIPPED                                          
- efreet ..................... SKIPPED                                          
- embryo ..................... SKIPPED                                          
- edje ....................... SKIPPED                                          
- epsilon .................... SKIPPED                                          
- esmart ..................... SKIPPED                                          
- emotion .................... SKIPPED                                          
- etk ........................ SKIPPED                                          
- etk_extra .................. SKIPPED                                          
- ewl ........................ SKIPPED                                          
- exml ....................... SKIPPED                                          
- enhance .................... SKIPPED                                          
- e_dbus ..................... SKIPPED                                          
- e .......................... SKIPPED                                          
- entrance ................... SKIPPED                                          
- edje_editor ................ SKIPPED                                          
- edje_viewer ................ SKIPPED                                          
- elicit ..................... SKIPPED                                          
- elitaire ................... SKIPPED                                          
- emphasis ................... SKIPPED                                          
- empower .................... SKIPPED                                          
- emprint .................... SKIPPED                                          
- ephoto ..................... SKIPPED                                          
- estickies .................. SKIPPED                                          
- exhibit .................... SKIPPED                                          
- expedite ................... SKIPPED                                          
- exquisite .................. SKIPPED                                          
- extrackt ................... SKIPPED                                          
- e_phys ..................... SKIPPED                                          
- enthrall ................... SKIPPED                                          
- rage ....................... SKIPPED                                          
- alarm ...................... SKIPPED                                          
- bling ...................... SKIPPED                                          
- calendar ................... SKIPPED                                          
- cpu ........................ SKIPPED                                          
- deskshow ................... SKIPPED                                          
- efm_nav .................... SKIPPED                                          
- efm_path ................... SKIPPED                                          
- emu ........................ SKIPPED                                          
- execwatch .................. SKIPPED                                          
- flame ...................... SKIPPED                                          
- forecasts .................. SKIPPED                                          
- iiirk ...................... SKIPPED                                          
- language ................... SKIPPED                                          
- mail ....................... SKIPPED                                          
- mem ........................ SKIPPED                                          
- moon ....................... SKIPPED                                          
- mpdule ..................... SKIPPED                                          
- net ........................ SKIPPED                                          
- news ....................... SKIPPED                                          
- notification ............... SKIPPED                                          
- penguins ................... SKIPPED                                          
- photo ...................... SKIPPED                                          
- rain ....................... SKIPPED                                          
- screenshot ................. SKIPPED                                          
- slideshow .................. SKIPPED                                          
- snow ....................... SKIPPED                                          
- taskbar .................... SKIPPED                                          
- tclock ..................... SKIPPED                                          
- tiling ..................... SKIPPED                                          
- uptime ..................... SKIPPED                                          
- weather .................... SKIPPED                                          
- winselector ................ SKIPPED                                          
- wlan ....................... SKIPPED                                          
- b_and_w .................... SKIPPED                                          
--------------------------------------------------------------------------------

----------------------------- Finishing installation ---------------------------
- registering libraries ...... ok                                               
- post install script ........ skipped                                          
--------------------------------------------------------------------------------

--------------------------- Easy_e17.sh 1.2.1.1-OzOS ---------------------------
  Developers:      Brian 'morlenxus' Miculcy                                    
                   David 'onefang' Seikel                                       
  Contributors:    Tim 'amon' Zebulla                                           
                   Daniel G. '_ke' Siegel                                       
                   Stefan 'slax' Langner                                        
                   Massimiliano 'Massi' Calamelli                               
                   Thomas 'thomasg' Gstaedtner                                  
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_pathemu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt enthrall rage emuflame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification b_and_w
  Only:            engage

  Script action:   only
--------------------------------------------------------------------------------

-------------------------------- Build phase 3/3 -------------------------------
- cleaning
- install notes
--------------------------------------------------------------------------------


-------------------------------- Cleaning temp dir -----------------------------
- deleting temp dir .......... ok
--------------------------------------------------------------------------------
```

---

### Post by jdinosaurus on 2008-11-07
I tried the clean installation but still have the same issue :
I can see only black wallpaper - Enlightenment written on top and disabled "Next" button on the bottom. And i can only move mouse.
If I push f5 and check processes - "enlightenment" process eats 100% of my resources.
Here is my .xsession-errors but i don't see obvious errors here:

```
/etc/gdm/Xsession: Beginning session setup...
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
/usr/bin/xmodmap:  unable to open file '/usr/share/apps/kxkb/ubuntu.xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
ESTART: 0.00001 [0.00001] - begin
ESTART: 0.00009 [0.00009] - signals done
ESTART: 0.00013 [0.00004] - determine prefix
DYNAMIC DETERMINED PREFIX: /opt/e17
ESTART: 0.00037 [0.00024] - prefix done
ESTART: 0.00042 [0.00004] - intl init
ESTART: 0.00046 [0.00004] - parse args
ESTART: 0.00047 [0.00001] - arg parse done
ESTART: 0.00050 [0.00002] - ecore init
ESTART: 0.00453 [0.00403] - ecore_file init
ESTART: 0.00474 [0.00021] - more ecore
ESTART: 0.00476 [0.00002] - x connect
ESTART: 0.03685 [0.03209] - ecore_con
ESTART: 0.04074 [0.00388] - xinerama
E17 INIT: XINERAMA SCREEN: [0], 1440x900+0+0
E17 INIT: XINERAMA CHOSEN: [0], 1440x900+0+0
ESTART: 0.04106 [0.00033] - x hints
ESTART: 0.04129 [0.00023] - x hints done
ESTART: 0.04131 [0.00001] - ecore_evas init
ESTART: 0.04168 [0.00038] - test done
ESTART: 0.04169 [0.00001] - efreet
ESTART: 0.04188 [0.00019] - efreet done
ESTART: 0.04189 [0.00001] - configure
ESTART: 0.04194 [0.00005] - dirs
ESTART: 0.04210 [0.00015] - filereg
ESTART: 0.04211 [0.00001] - config
ESTART: 0.04324 [0.00113] - scale
ESTART: 0.04327 [0.00003] - pointer
ESTART: 0.04328 [0.00001] - path
ESTART: 0.04333 [0.00005] - ipc
INFO: E_IPC_SOCKET=/tmp/enlightenment-skondratenko/disp-:0.0-9878
ESTART: 0.04377 [0.00044] - font
ESTART: 0.04381 [0.00004] - theme
ESTART: 0.05446 [0.01065] - splash
ESTART: 0.05448 [0.00002] - test file format support
ESTART: 0.05893 [0.00446] - msgbus
ESTART: 0.06049 [0.00156] - intl post
ESTART: 0.06473 [0.00424] - efreet paths
ESTART: 0.06478 [0.00005] - efreet paths done
ESTART: 0.06479 [0.00001] - thumb init
ESTART: 0.06480 [0.00001] - sys init
ESTART: 0.06482 [0.00002] - actions
ESTART: 0.06547 [0.00065] - bindings
ESTART: 0.06557 [0.00010] - popup
ESTART: 0.06558 [0.00001] - bg
ESTART: 0.06560 [0.00002] - screens
ESTART: 0.06562 [0.00001] - screens: atoms
ESTART: 0.06587 [0.00025] - screens: manager
ESTART: 0.06589 [0.00002] - screens: container
ESTART: 0.06590 [0.00001] - screens: zone
ESTART: 0.06591 [0.00001] - screens: desk
ESTART: 0.06593 [0.00001] - screens: menu
ESTART: 0.06594 [0.00001] - screens: exehist
ESTART: 0.06595 [0.00001] - screens: get roots
ESTART: 0.06596 [0.00001] - screens: focus
ESTART: 0.06596 [0.00001] - screens: border
ESTART: 0.06598 [0.00002] - screens: win
ESTART: 0.06599 [0.00001] - screens: manage roots
ESTART: 0.14505 [0.07906] - screens: sync
ESTART: 0.14519 [0.00014] - exec
ESTART: 0.14523 [0.00003] - remember
ESTART: 0.14524 [0.00002] - container freeze
ESTART: 0.14526 [0.00002] - fm2
ESTART: 0.15365 [0.00839] - msg
ESTART: 0.15368 [0.00003] - dnd
ESTART: 0.15373 [0.00005] - grabinput
ESTART: 0.15375 [0.00002] - modules
ESTART: 0.15377 [0.00002] - colorclasses
ESTART: 0.15379 [0.00002] - gadcon
ESTART: 0.15380 [0.00001] - shelves
ESTART: 0.15381 [0.00001] - dpms
ESTART: 0.15385 [0.00004] - screensaver
ESTART: 0.15388 [0.00003] - mouse
ESTART: 0.15407 [0.00019] - desklock
ESTART: 0.15412 [0.00005] - order
ESTART: 0.15415 [0.00003] - powersave
ESTART: 0.15416 [0.00002] - add idle enterers
ESTART: 0.15418 [0.00001] - init properites
ESTART: 0.15426 [0.00008] - test code
ESTART: 0.15428 [0.00002] - load modules
ESTART: 0.26846 [0.11418] - shelf config init
ESTART: 0.26854 [0.00009] - MAIN LOOP AT LAST
ESTART: 0.31395 [0.04541] - SLEEP

```

---

### Post by smartboyathome on 2008-11-07
> **nikk^ said:**
> Hi!

I had no problems with installing E17. Everything went shmoothly. But I have problems to install engage.

I tried it, how it was described here:


- You can install original skipped packages, by editing /etc/easy_e17.conf file, remove them from --skip list and do:
sudo easy_e17.sh --only=<skipped_package_name>.

I delete the entry in the "skip list", but if i run the script like this: easy_e17.sh --only=engage, the scripts starts and goes through the steps, but doesn't compile or install anything:

```
----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17                                                     
  Source path:     /var/cache/e17_src                                           
  Source url:      http://svn.enlightenment.org/svn/e/trunk                     
  Logs path:       /tmp/easy_e17/install_logs                                   

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w                                             
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt enthrall rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification b_and_w                                                 
  Only:            engage                                                       

  Script action:   only
--------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks                                              
- source checkout/update                                                        
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok                                               
- 'automake' available ....... ok                                               
- 'gcc' available ............ ok                                               
- 'make' available ........... ok                                               
- 'svn' available ............ ok                                               
- build-user ................. root                                             
- adding path to env ......... ok                                               
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)                  
- setting compile options .... ok                                               
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
--------------------------------------------------------------------------------

--------------------------- Easy_e17.sh 1.2.1.1-OzOS ---------------------------
  Developers:      Brian 'morlenxus' Miculcy                                    
                   David 'onefang' Seikel                                       
  Contributors:    Tim 'amon' Zebulla                                           
                   Daniel G. '_ke' Siegel                                       
                   Stefan 'slax' Langner                                        
                   Massimiliano 'Massi' Calamelli                               
                   Thomas 'thomasg' Gstaedtner                                  
                   Roberto 'rex' Sigalotti                                      

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17                                                     
  Source path:     /var/cache/e17_src                                           
  Source url:      http://svn.enlightenment.org/svn/e/trunk                     
  Logs path:       /tmp/easy_e17/install_logs                                   

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w                                             
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt enthrall rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification b_and_w                                                 
  Only:            engage                                                       

  Script action:   only
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation                                              
- apps-compilation and installation                                             
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- eina ....................... SKIPPED                                          
- eet ........................ SKIPPED                                          
- evas ....................... SKIPPED                                          
- ecore ...................... SKIPPED                                          
- efreet ..................... SKIPPED                                          
- embryo ..................... SKIPPED                                          
- edje ....................... SKIPPED                                          
- epsilon .................... SKIPPED                                          
- esmart ..................... SKIPPED                                          
- emotion .................... SKIPPED                                          
- etk ........................ SKIPPED                                          
- etk_extra .................. SKIPPED                                          
- ewl ........................ SKIPPED                                          
- exml ....................... SKIPPED                                          
- enhance .................... SKIPPED                                          
- e_dbus ..................... SKIPPED                                          
- e .......................... SKIPPED                                          
- entrance ................... SKIPPED                                          
- edje_editor ................ SKIPPED                                          
- edje_viewer ................ SKIPPED                                          
- elicit ..................... SKIPPED                                          
- elitaire ................... SKIPPED                                          
- emphasis ................... SKIPPED                                          
- empower .................... SKIPPED                                          
- emprint .................... SKIPPED                                          
- ephoto ..................... SKIPPED                                          
- estickies .................. SKIPPED                                          
- exhibit .................... SKIPPED                                          
- expedite ................... SKIPPED                                          
- exquisite .................. SKIPPED                                          
- extrackt ................... SKIPPED                                          
- e_phys ..................... SKIPPED                                          
- enthrall ................... SKIPPED                                          
- rage ....................... SKIPPED                                          
- alarm ...................... SKIPPED                                          
- bling ...................... SKIPPED                                          
- calendar ................... SKIPPED                                          
- cpu ........................ SKIPPED                                          
- deskshow ................... SKIPPED                                          
- efm_nav .................... SKIPPED                                          
- efm_path ................... SKIPPED                                          
- emu ........................ SKIPPED                                          
- execwatch .................. SKIPPED                                          
- flame ...................... SKIPPED                                          
- forecasts .................. SKIPPED                                          
- iiirk ...................... SKIPPED                                          
- language ................... SKIPPED                                          
- mail ....................... SKIPPED                                          
- mem ........................ SKIPPED                                          
- moon ....................... SKIPPED                                          
- mpdule ..................... SKIPPED                                          
- net ........................ SKIPPED                                          
- news ....................... SKIPPED                                          
- notification ............... SKIPPED                                          
- penguins ................... SKIPPED                                          
- photo ...................... SKIPPED                                          
- rain ....................... SKIPPED                                          
- screenshot ................. SKIPPED                                          
- slideshow .................. SKIPPED                                          
- snow ....................... SKIPPED                                          
- taskbar .................... SKIPPED                                          
- tclock ..................... SKIPPED                                          
- tiling ..................... SKIPPED                                          
- uptime ..................... SKIPPED                                          
- weather .................... SKIPPED                                          
- winselector ................ SKIPPED                                          
- wlan ....................... SKIPPED                                          
- b_and_w .................... SKIPPED                                          
--------------------------------------------------------------------------------

----------------------------- Finishing installation ---------------------------
- registering libraries ...... ok                                               
- post install script ........ skipped                                          
--------------------------------------------------------------------------------

--------------------------- Easy_e17.sh 1.2.1.1-OzOS ---------------------------
  Developers:      Brian 'morlenxus' Miculcy                                    
                   David 'onefang' Seikel                                       
  Contributors:    Tim 'amon' Zebulla                                           
                   Daniel G. '_ke' Siegel                                       
                   Stefan 'slax' Langner                                        
                   Massimiliano 'Massi' Calamelli                               
                   Thomas 'thomasg' Gstaedtner                                  
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor edje_viewer elicit elitaire emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt e_phys enthrall rage alarm bling calendar cpu deskshow efm_nav efm_pathemu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan b_and_w
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt enthrall rage emuflame moon news penguins rain snow language photo efm_path efm_nav e_phys execwatch mpdule notification b_and_w
  Only:            engage

  Script action:   only
--------------------------------------------------------------------------------

-------------------------------- Build phase 3/3 -------------------------------
- cleaning
- install notes
--------------------------------------------------------------------------------


-------------------------------- Cleaning temp dir -----------------------------
- deleting temp dir .......... ok
--------------------------------------------------------------------------------
```

Engage has not been maintained for quite some time, and so is not included as an option with the script. Instead, what is recommended is that you install [ItaskNG]("http://code.google.com/p/itask-module/wiki/ItaskNG") instead.

---

### Post by doorman on 2008-11-10
In case anybody tried to update e17 lately and got an error from svn such as:
```
svn: failed to add directory 'e/data/backgrounds'
```
or a similar error, all you have to do is go to the e17 src dir and delete the file/directory svn is unable to add:
```
$ sudo su
# cd /var/cache/e17_src
# rm -rf e/data/backgrounds

```

---

### Post by smartboyathome on 2008-11-10
By the way doorman, the prefered way for Ubuntu to get a superuser console is to use sudo -i. Just letting you know for the future. Thanks for the tip though, saves me the trouble of finding it. :)

---

### Post by Cyberponcho on 2008-11-11
Well, it finally happened, after doing a lot of apt-get remove/purge/install i got last night around 01:30 am the message 'The most incredible and really unbelievable dream has become true: You compiled e17 successfully!'
The easy script worked this time wonderfully, now i finally got a working Enlightenment enviroment in my laptop and all the things tested (which weren't many, i need my sleep too!!) are working properly :)
Thanks Rui Pais for this thread and thanks for pointing the script out.

---

### Post by pipou24 on 2008-11-11
Hi everyone. I'm trying to update my install. I met this error :

(sorry for the translation, the erreor message is in my own language)

```
svn: Failed to add 'eina/eina-0.pc.in' : this object already exist

```

I've tried to run easy_e17.sh with -c and -f options but it doesn't change anything. Do I have to delete eina/eina-0.pc.in by myself ?
*I've done as doorman indicated, but it's not fully updating ...*

---

### Post by worldwithoutgurus on 2008-11-12
Hey pipou24, next time try my method (see signature)...  I mean easy_e17 is cool, all right, but why don't you use the french forums and localized (and hmm... 100 % functional) scripts ?

---

### Post by Crafty Kisses on 2008-11-12
Thanks for sharing my friend.

---

### Post by pipou24 on 2008-11-12
> **worldwithoutgurus said:**
> Hey pipou24, next time try my method (see signature)...  I mean easy_e17 is cool, all right, but why don't you use the french forums and localized (and hmm... 100 % functional) scripts ?
:lolflag: I've seen your method, and it seems cleener and to have much packages (and, thank to you, I also use Xephyr now) .... but easy_e17 is the way I installed it the first time.

Anyway, you're right. Tonight it doesn't seem to work. I'm going to install Intrepid by the end of the week. I'll install e17 from svn with your method

(P****, qu'est-ce qui me prend de te parler en anglais ...)

---

### Post by christoforever on 2008-11-20
after installing e17 and then booting into it, my wifi does not work... It works however when booting back into gnome, but does not work when i boot into enlightenment... anyone else have this issue or know a fix?

Thanks ahead of time,
Christopher Dancy

---

### Post by smartboyathome on 2008-11-21
> **christoforever said:**
> after installing e17 and then booting into it, my wifi does not work... It works however when booting back into gnome, but does not work when i boot into enlightenment... anyone else have this issue or know a fix?

Thanks ahead of time,
Christopher Dancy

You need to install WICD instead of Network Manager. Network Manager operates off of the system tray (E17 has none), while WICD has a separate GUI. Only other way to do this is to install trayer or stalonetray, which are external tray programs which you can run network manager with.

---

### Post by Cyberponcho on 2008-11-21
> **worldwithoutgurus said:**
> Hey pipou24, next time try my method (see signature)...  I mean easy_e17 is cool, all right, but why don't you use the french forums and localized (and hmm... 100 % functional) scripts ?

Now that's a mean comment (no offenses and not meaning to start a flame war here), the easy script didn't work for me @ the beginning but after i figure out a couple of things it worked out just fine, that's the beauty of Linux, you actually HAVE to think and learn in order to figure out things and not be a windows-autorun-feed-me-like-a-braindead-moron 'user'.
Just my 2 cents

PS=I want to point out again that i don't mean to offend anybody and don't want to start a flame war here, it's just an opinion.:)

---

### Post by christoforever on 2008-11-21
Another e17 question if anyone knows the answer... When using gtk apps it uses an ugly system theme, is there anyway to change the gtk theme e17 uses by default? I tried opening the gnome-application-properties app but that was just a bad idea. The screen went hay-wire and I had to refresh e17. So just wondering if anyone had any ideas?

---

### Post by smartboyathome on 2008-11-21
> **christoforever said:**
> Another e17 question if anyone knows the answer... When using gtk apps it uses an ugly system theme, is there anyway to change the gtk theme e17 uses by default? I tried opening the gnome-application-properties app but that was just a bad idea. The screen went hay-wire and I had to refresh e17. So just wondering if anyone had any ideas?

Install and use an application like gtk-chtheme. That way, you get your GTK theme set to how you want it. Want to set your icon theme too after you set your theme? Type this in a terminal:
```
nano .gtkrc.mine
```
And then put this in the resulting text file, saving it after you do with control+x:
```
gtk-icon-theme-name="Tango"
```
Change Tango to the name of your icon theme.

---

### Post by Dodongo Dislikes Smoke on 2008-11-26
Attempting to run then uninstall this script seems to have broke Python.  MFE, a Python-based emulator launcher exits with:
OSError: [Errno 2] No such file or directory: '/opt/e17/bin'

If I have the e17-svn package installed (although not all the checked-out code properly compiled), MFE runs fine.  After uninstalling it, MFE dies with the above error.  I can leave Enlightenment half installed and MFE gets along fine, but I'd rather know how to completely rid myself of it as purging e17-svn doesn't seem to be doing the trick.

ADDENDUM:
I figured it out.  I had to get rid of the /opt/e17/bin part from my $PATH in /etc/environment.  You might want to add that to the uninstall directions on the first page.

---

### Post by nickadam on 2008-11-26
Hi Rui Pais

Thanks for this useful information.

Nick

---

### Post by Rui Pais on 2008-11-28
> **pipou24 said:**
> Hi everyone. I'm trying to update my install. I met this error :

(sorry for the translation, the erreor message is in my own language)

```
svn: Failed to add 'eina/eina-0.pc.in' : this object already exist

```

I've tried to run easy_e17.sh with -c and -f options but it doesn't change anything. Do I have to delete eina/eina-0.pc.in by myself ?
*I've done as doorman indicated, but it's not fully updating ...*

> **worldwithoutgurus said:**
> Hey pipou24, next time try my method (see signature)...  I mean easy_e17 is cool, all right, but why don't you use the french forums and localized (and hmm... 100 % functional) scripts ?


Hi.
Strangely enough, sometimes svn don't update code correctly or can't manage certain kind of updates, like it happen a lot lately with pot (translations) files, or devs simply forget (they all tends to be human)  
 to upadte some dependency, like the cases of the pc.in file. 
Search the logs and you will see plenty of oops ...

That, of course, will not be solved by choose this or that script, no matter the percentage of "functionality", and will require a devs fix or special intervention by the user.

pot files has been specially dramatic, requiring users deletion of old files... but recently, running intrepid, i (and others) has been presented with a svn option (a recent feature on intrepid svn version? don't know) that ask/allow to merge changes and proceed with the update.
See pic attach. In those cases a simple pressing of 'R' key (for resolved) at each conflicting solved the problem.

[ATTACH]94478[/ATTACH]

---

### Post by Rui Pais on 2008-11-28
> **nickadam said:**
> Hi Rui Pais

Thanks for this useful information.

Nick
:)
Glad you like it!


> **Dodongo Dislikes Smoke said:**
> Attempting to run then uninstall this script seems to have broke Python.  MFE, a Python-based emulator launcher exits with:
OSError: [Errno 2] No such file or directory: '/opt/e17/bin'

If I have the e17-svn package installed (although not all the checked-out code properly compiled), MFE runs fine.  After uninstalling it, MFE dies with the above error.  I can leave Enlightenment half installed and MFE gets along fine, but I'd rather know how to completely rid myself of it as purging e17-svn doesn't seem to be doing the trick.

ADDENDUM:
I figured it out.  I had to get rid of the /opt/e17/bin part from my $PATH in /etc/environment.  You might want to add that to the uninstall directions on the first page.


Hi.
Thanks for call my attention to that! It completly scape my attention.

Fixed now!!
**(please all users, you should update+upgrade to the latest version)**

Many thanks, for the report.

BTW. Thats really a MFE issue. 
I don't know that app, but PATHs are things eventually over-written by many apps and even by users directly. No application should fail just because of an inexistent path on it.
You may want to consider report such problem to MFE devs/maintainers.
Rui

---

### Post by trevelyn on 2008-12-01
i was wondering, i downloaded xubuntu and installed e17 perfectly with your tutorial via e17-svn.  i then used the psychocats method of completely removing xfce (which left gdm in place).  

[http://www.psychocats.net/ubuntu/puregnomehardy](http://www.psychocats.net/ubuntu/puregnomehardy)

I searched the removal of xfce and didnt see "enlightenemt" or "e17" or "starte17" etc, so i figured it was still there after the procedure.  i was wrong, somehow it is gone or theres a secret way of starting it?? 
now enlightement is missing from gdm session chooser, and there's no command line way of starting it. (i guess)  Then, i can apt-get install enlightenment - but that just installs e16... ??? i'm confused..


i dont want bloated xfce or gnome or kde at all, just ubuntu and e17 - that's it.. what's the easiest way of doing that? 

EDIT: whoops, i forgot to mention, i didn't do the "&& apt-get install ubuntu-desktop" part cos it wanted to install like 400MB worth of crap i didn't want.

---

### Post by trevelyn on 2008-12-01
awesome, i got it! i had to do

apt-cache purge e17-svn && apt-get install e17-svn

and since i had all the source already it simply configured (autogen.sh'd) them and make && make installed them!

Yay it works great! :D

---

### Post by Capt_Zaphod on 2008-12-02
Greetings friends;
  I've been trying to follow this, but, invariably end up here:
> W: GPG error: [http://apt.wicd.net](http://apt.wicd.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FEC820F4B8C0755A
W: Failed to fetch [http://edevelop.org/pkg-e/ubuntu/dists/edgy/Release.gpg](http://edevelop.org/pkg-e/ubuntu/dists/edgy/Release.gpg)  Could not resolve 'edevelop.org'

W: Failed to fetch [http://edevelop.org/pkg-e/ubuntu/dists/edgy/e17/i18n/Translation-en_US.bz2](http://edevelop.org/pkg-e/ubuntu/dists/edgy/e17/i18n/Translation-en_US.bz2)  Could not resolve 'edevelop.org'

W: Some index files failed to download, they have been ignored, or old ones used instead.

Any suggestions please?

Thank you

---

### Post by Rui Pais on 2008-12-02
> **trevelyn said:**
> 
EDIT: whoops, i forgot to mention, i didn't do the "&& apt-get install ubuntu-desktop" part cos it wanted to install like 400MB worth of crap i didn't want.

That's very understandable! :)
Another way would be start [from minimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD"), add X server, gdm, and e17-svn. And later what ever you need for. That's the cleaner, but in aspects not the easier way.


> **trevelyn said:**
> awesome, i got it! i had to do

apt-cache purge e17-svn && apt-get install e17-svn

and since i had all the source already it simply configured (autogen.sh'd) them and make && make installed them!

Yay it works great! :D

:KS 
Yes. That's right.  
You don't even need to neither purge or remove.
A plain 
```
sudo aptitude reinstall e17-svn
```
would work.
Or manually create the link for Enlightenment.desktop on gdm folder.
That was what was incorrectly deleted, i presume.

Have fun!

---

### Post by Rui Pais on 2008-12-02
> **Capt_Zaphod said:**
> Greetings friends;
  I've been trying to follow this, but, invariably end up here:

Any suggestions please?

Thank you

Hi Capt_Zaphod!

Your problems are quite weird.
None of those are related, in any way with this method... but i can try to help.

For the WICD it's easy. Just run (copy+paste) this:
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

The other, the e-develop error, should be some old entry on your sources.list.

**You should not mix e17 installations, or you may run into bad problems, sometimes hard to detect.** 

Where do you get/set those repos? Have you installed on your Box from there?
If you never used that repo, and want to try this method, remove previously those entries from your /etc/apt/sources.list, follow the 1st post carefully and you will end up with a completely up-to-date e17.

Hope that helps.

---

### Post by cshaobui640990 on 2008-12-02
i always saw a guy selling [runescape money](http://www.runescape-shop.com/runescape-gold/runescape-gold.php) .but dont know if my account will be banned when i bought?

---

### Post by barkley128 on 2008-12-02
Hi, nice work you're doing here :)
It seems, installation went fine for me, but I do have a problem with gdm session file. enlightenment.desktop is blank, it contains nothing. So when I try to start e17, it outputs some error and starts gnome instead.
I've tried to
```
sudo rm /usr/share/xsessions/enlightenment.desktop
```
and
```
sudo  ln -s /opt/e17/share/xsessions/enlightenment.desktop /usr/share/xsessions/enlightenment.desktop

```
With no luck, file is the same ..blank.
I don't even have /opt/e17/share/xsessions/ directory. :(

---

### Post by Rui Pais on 2008-12-02
> **barkley128 said:**
> Hi, nice work you're doing here :)
It seems, installation went fine for me, but I do have a problem with gdm session file. enlightenment.desktop is blank, it contains nothing. So when I try to start e17, it outputs some error and starts gnome instead.
I've tried to
```
sudo rm /usr/share/xsessions/enlightenment.desktop
```
and
```
sudo  ln -s /opt/e17/share/xsessions/enlightenment.desktop /usr/share/xsessions/enlightenment.desktop

```
With no luck, file is the same ..blank.
I don't even have /opt/e17/share/xsessions/ directory. :(

You don't??:???:

Ok are you sure that e17 compilation/installation finished well?

It should say something like
> The most incredible and really unbelievable dream has become true:
You compiled e17 successfully!

 can you put the output of:
```
ls /opt/e17
```
and
```
ls /opt/e17/bin
```
Please?

Thank you

---

### Post by barkley128 on 2008-12-02
Well I think it installed fine, but I can't say I'm 100% sure..
Okay here's the output:
```
barkley128@barkley128-desktop:~$ ls /opt/e17
bin  include  lib  share

```
and
```
barkley128@barkley128-desktop:~$ ls /opt/e17/bin
ecore_config  efreet_alloc       embryo_cc           etk_test
edje_cc       efreet_cache_test  epsilon             inkscape2edc
edje_decc     efreet_menu_alloc  epsilon_thumbd
edje_recc     efreet_spec_test   epsilon_thumb_test
eet           efreet_test        etk_prefs

```
I'm using Ubuntu 8.10 btw.

---

### Post by smartboyathome on 2008-12-02
I can help out here Rui. You need to install cvs then reinstall e17-svn. The etk cvs bug bites again! :(

---

### Post by barkley128 on 2008-12-02
Tried reinstalling, still the same problem. I have cvs installed. And the installation ended with "The most incredible and really unbelievable dream has become true:
You compiled e17 successfully!"

---

### Post by smartboyathome on 2008-12-02
> **barkley128 said:**
> Tried reinstalling, still the same problem. I have cvs installed. And the installation ended with "The most incredible and really unbelievable dream has become true:
You compiled e17 successfully!"

Can you post the output of ls /opt/e17/bin again? It should have a command called "enlightenment_start" in it.

---

### Post by Rui Pais on 2008-12-02
> **smartboyathome said:**
> I can help out here Rui. You need to install cvs then reinstall e17-svn. The etk cvs bug bites again! :(

Thanks smartboyathome :)
I suspected the same thing...


> **barkley128 said:**
> Tried reinstalling, still the same problem. I have cvs installed. And the installation ended with "The most incredible and really unbelievable dream has become true:
You compiled e17 successfully!"

And can you tell us what command did you run to reinstall?
Probably it just run an update on your half installed e17.
If your /opt/e17/bin still have less than 40 items installations it's not complete.
In that case run:
```
sudo easy_e17.sh -i
```
to reinstall all from the beginning.

good luck

---

### Post by barkley128 on 2008-12-03
Okay.
I tried to reinstall with aptitude
```
sudo aptitude reinstall e17-svn
```
Now I tried to reinstall it with
```
sudo easy_e17.sh -i
```
Still no luck, maybe I should try to redownload the sources?
My /opt/e17/bin is the same, as I posted in previous comments, there is no "enlightenment_start" in it.. :(

---

### Post by trevelyn on 2008-12-03
thanks Rui Pais!  i tried the minimalist cd but i it turned out to be the same size after making it into a live ISO from remastersys, and if i start with one like xubuntu, or ubuntu, it has all the drivers preinstalled people actually use.  After doing the psychocats way of uninstalling gnome i do have to reinstall a lot of stuff like gdm, x, etc. 

Hey anyone familiar with e17, I have created a custom wallpaper, but when i use the "fit on desktop" function it leaves the top and bottom of the desktop background "white."  Is there a way to make it another color to match my theme?  I have been googling for a while now..

---

### Post by smartboyathome on 2008-12-03
> **trevelyn said:**
> thanks Rui Pais!  i tried the minimalist cd but i it turned out to be the same size after making it into a live ISO from remastersys, and if i start with one like xubuntu, or ubuntu, it has all the drivers preinstalled people actually use.  After doing the psychocats way of uninstalling gnome i do have to reinstall a lot of stuff like gdm, x, etc. 

Hey anyone familiar with e17, I have created a custom wallpaper, but when i use the "fit on desktop" function it leaves the top and bottom of the desktop background "white."  Is there a way to make it another color to match my theme?  I have been googling for a while now..

There is, but it involves editing the wallpaper's .edj file and adding the color you want as a paramater in it's .edc. I'm not sure exactly how, but I know its possible. Perhaps you can catch Toma on the E17 IRC channel (#e on freenode) and see if he will tell you.

---

### Post by Capt_Zaphod on 2008-12-04
> **Rui Pais said:**
> Hi Capt_Zaphod!

Your problems are quite weird.
None of those are related, in any way with this method... but i can try to help.

For the WICD it's easy. Just run (copy+paste) this:
```
wget -q http://apt.wicd.net/wicd.gpg -O- | sudo apt-key add -
```

The other, the e-develop error, should be some old entry on your sources.list.

**You should not mix e17 installations, or you may run into bad problems, sometimes hard to detect.** 

Where do you get/set those repos? Have you installed on your Box from there?
If you never used that repo, and want to try this method, remove previously those entries from your /etc/apt/sources.list, follow the 1st post carefully and you will end up with a completely up-to-date e17.

Hope that helps.

Thank you for your advice. I started to install, and it failed.  So, I came to the forum for advice, and tried again ... without initially deleting.  I have deleted those entries and will start again.  Hopefully that does the trick.

Thanks again!

---

### Post by Capt_Zaphod on 2008-12-04
I went and followed the 1st post of this thread.
Logged out, and when I tried to log into enlightenment, I got an error of no Exec file found ... and it started in default mode.

Any suggestions, please?

---

### Post by smartboyathome on 2008-12-04
Capt, did you install CVS before installing e17? If not, you need to and then need to install e17-svn.

---

### Post by Capt_Zaphod on 2008-12-05
> **smartboyathome said:**
> Capt, did you install CVS before installing e17? If not, you need to and then need to install e17-svn.

I had deleted everything, and then followed the instructions of the 1st post and got this:
> 
------------------------------ Installing packages -----------------------------
- eina ....................... ok          
- eet ........................ SKIPPED
- evas ....................... ok          
- ecore ...................... SKIPPED
- efreet ..................... SKIPPED
- embryo ..................... SKIPPED
- edje ....................... SKIPPED
- epsilon .................... SKIPPED
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ SKIPPED
- etk_extra .................. SKIPPED
- ewl ........................ ok          
- exml ....................... SKIPPED
- enhance .................... SKIPPED
- e_dbus ..................... SKIPPED
- exalt ...................... SKIPPED
- e .......................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.2.4-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running autopoint...
autopoint: *** cvs program not found
autopoint: *** Stop.
Running aclocal...
Running autoconf...
Running autoheader...
Running libtoolize...
Running automake...
configure.ac:17: installing `./compile'
configure.ac:164: required file `./config.rpath' not found
configure.ac:11: installing `./install-sh'
configure.ac:11: installing `./missing'
config/Makefile.am:12: `%'-style pattern rules are a GNU make extension
config/default/Makefile.am:16: `%'-style pattern rules are a GNU make extension
config/illume/Makefile.am:26: `%'-style pattern rules are a GNU make extension
config/minimalist/Makefile.am:32: `%'-style pattern rules are a GNU make extension
config/netbook/Makefile.am:32: `%'-style pattern rules are a GNU make extension
config/scaleable/Makefile.am:32: `%'-style pattern rules are a GNU make extension
config/standard/Makefile.am:32: `%'-style pattern rules are a GNU make extension
src/bin/Makefile.am: installing `./depcomp'

So ... no, I guess I hadn't installed CVS 1st.  Though I thought I followed the 1st posts instructions completely.

---

### Post by smartboyathome on 2008-12-05
Its an svn breakage. Try installing again in a while.

---

### Post by Capt_Zaphod on 2008-12-05
> **smartboyathome said:**
> Its an svn breakage. Try installing again in a while.
Thank you.
Can I reinstall over the previous one, or do I have to uninstall the previous?  I figure the latter, but, thought I'd ask.

---

### Post by darkenedday on 2008-12-05
I have a new problem

first off for some reason i had to create my own enlightenment.desktop file and link it to the /opt/e17/bin/enlightenment_start, which isnt a big deal being it works fine now (except I can't seem to add apps to my ibar) 

but my school has a hidden wifi network, that I have to enter the name manually to connect to, I can't seem to figure out how to do this, the module "conection manager" has a button that says "networks" but whenever I click it it just closes the window?

---

### Post by smartboyathome on 2008-12-05
> **Capt_Zaphod said:**
> Thank you.
Can I reinstall over the previous one, or do I have to uninstall the previous?  I figure the latter, but, thought I'd ask.

You can reinstall over the previous one. Just run sudo easy_e17.sh -i and it will try installing it again.

> **darkenedday said:**
> I have a new problem

first off for some reason i had to create my own enlightenment.desktop file and link it to the /opt/e17/bin/enlightenment_start, which isnt a big deal being it works fine now (except I can't seem to add apps to my ibar) 

but my school has a hidden wifi network, that I have to enter the name manually to connect to, I can't seem to figure out how to do this, the module "conection manager" has a button that says "networks" but whenever I click it it just closes the window?

The connection manager is just beginning its life as part of E17, so it isn't ready yet for anything. Instead, I recommend using WICD. It works great with E17 since it doesn't have a system tray. Just run it with wicd-client --no-tray.

---

### Post by darkenedday on 2008-12-05
alright and I've come across yet another problem, my e17 session doesn't save, I logged in and made everything look how I wanted it to, yet when i log out and back in it starts all over even with the first run wizard, any ideas?

---

### Post by smartboyathome on 2008-12-05
Try unloading the "First Run" module maybe in Settings > Modules?

---

### Post by darkenedday on 2008-12-05
> **smartboyathome said:**
> You can reinstall over the previous one. Just run sudo easy_e17.sh -i and it will try installing it again.



The connection manager is just beginning its life as part of E17, so it isn't ready yet for anything. Instead, I recommend using WICD. It works great with E17 since it doesn't have a system tray. Just run it with wicd-client --no-tray.


what package is WICD? I tried running the command you gave and i got the error command not found, and I tried sudo apt-get install wicd and wicd client, even searched for wicd in synaptic and didnt get anything. . .

thanks for the help btw

---

### Post by darkenedday on 2008-12-05
aptitude search returns nada as well

---

### Post by darkenedday on 2008-12-05
alright I tried unloading the first run module, turns out it unloads itself by default after you do it, I tried loading and unloading it as well, still I log out and log back in and start all over and have to move everything around again, 

in case I forgot something in my .desktop file here's a look at that
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/opt/e17/bin/enlightenment_start	
Name=Enlightenment


also here's these::

mike@DellBook-m1530n:~$ ls /opt/e17
bin  etc  include  lib  share
mike@DellBook-m1530n:~$ ls /opt/e17/bin
ecore_config                efreet_menu_alloc      enlightenment_sys
e_dbus_hal                  efreet_spec_test       enlightenment_thumb
e_dbus_nm                   efreet_test            e-notify-send
e_dbus_notification_daemon  embryo_cc              epsilon
e_dbus_notify               emprint                epsilon_thumbd
e_dbus_test                 enlightenment          epsilon_thumb_test
e_dbus_test_client          enlightenment_fm       etk_prefs
edje_cc                     enlightenment_fm_op    etk_test
edje_decc                   enlightenment_fm_open  ewl_config
edje_recc                   enlightenment_imc      ewl_embed_test
eet                         enlightenment_init     ewl_simple_test
efreet_alloc                enlightenment_remote   ewl_test
efreet_cache_test           enlightenment_start    inkscape2edc

---

### Post by smartboyathome on 2008-12-05
> **darkenedday said:**
> what package is WICD? I tried running the command you gave and i got the error command not found, and I tried sudo apt-get install wicd and wicd client, even searched for wicd in synaptic and didnt get anything. . .

thanks for the help btw

Get WICD [here]("http://wicd.sourceforge.net/"). :KS

---

### Post by Capt_Zaphod on 2008-12-06
> **smartboyathome said:**
> You can reinstall over the previous one. Just run sudo easy_e17.sh -i and it will try installing it again. 

I don't get it.

I started with this:

> **Rui Pais said:**
> 


To do it automatically, copy+paste the above to a command line:
```
 sudo sh -c "echo 'deb http://cafelinux.org/Downloads/oz-os tinwoodman main' >> /etc/apt/sources.list"
```
and add the authenticated key with:
```
wget -q http://cafelinux.org/Downloads/oz-os/key.asc -O- | sudo apt-key add -
```
[COLOR="SlateGray"][SIZE="1"]Please if you have any link to this method, please update it as soon as possible. Many Thanks.[/SIZE][/COLOR]

Install it with:
```
sudo apt-get update && sudo apt-get install e17-svn
```
And thats all.
:)




I re-installed with the code you gave me, and I still get this...


> ------------------------------ Installing packages -----------------------------
- eina ....................... ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.2.4-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running autopoint...
autopoint: *** cvs program not found
autopoint: *** Stop.


BTW ... I _do_ appreciate your time and patience with this.

---

### Post by Rui Pais on 2008-12-06
> **Capt_Zaphod said:**
> I don't get it.

I started with this:



I re-installed with the code you gave me, and I still get this...




BTW ... I _do_ appreciate your time and patience with this.


Please, [read this here.]("http://ubuntuforums.org/showpost.php?p=5788241&postcount=8")
I will change my first post to prevent repetions of this.



Right now SVN it's broken, anyway (revision 37962).
You need a previous revision!
If you already had at least downlaod code you can after:
```
sudo apt-get install cvs
```
try:
```
sudo easy_e17.sh  --skip-srcupdate
```

If your revision it's already 37962, you may need to wait or install a previous revision.

---

### Post by Rui Pais on 2008-12-06
> **darkenedday said:**
> alright I tried unloading the first run module, turns out it unloads itself by default after you do it, I tried loading and unloading it as well, still I log out and log back in and start all over and have to move everything around again, 

in case I forgot something in my .desktop file here's a look at that
[Desktop Entry]
Encoding=UTF-8
Type=XSession
Exec=/opt/e17/bin/enlightenment_start	
Name=Enlightenment


You shouldn't make a .desktop yourself. It's better to have a link for the already existent desktop file on e17 installation.
e17-svn should had take care of that. 
You can replace it by:
sudo rm /usr/share/xsessions/enlightenment.desktop
sudo ln -s /opt/e17/share/xsessions/enlightenment.desktop /usr/share/xsessions/enlightenment.desktop



> **darkenedday said:**
> 
also here's these::

mike@DellBook-m1530n:~$ ls /opt/e17
bin  etc  include  lib  share
mike@DellBook-m1530n:~$ ls /opt/e17/bin
ecore_config                efreet_menu_alloc      enlightenment_sys
e_dbus_hal                  efreet_spec_test       enlightenment_thumb
e_dbus_nm                   efreet_test            e-notify-send
e_dbus_notification_daemon  embryo_cc              epsilon
e_dbus_notify               emprint                epsilon_thumbd
e_dbus_test                 enlightenment          epsilon_thumb_test
e_dbus_test_client          enlightenment_fm       etk_prefs
edje_cc                     enlightenment_fm_op    etk_test
edje_decc                   enlightenment_fm_open  ewl_config
edje_recc                   enlightenment_imc      ewl_embed_test
eet                         enlightenment_init     ewl_simple_test
efreet_alloc                enlightenment_remote   ewl_test
efreet_cache_test           enlightenment_start    inkscape2edc

Seems good and finished. Thats natural, since you alread been able of run a session... 
Maybe a permission issue.
Try, with all Enlightenment sessions closed (log out), go for a console (Ctrl+Alt+F1), log there and run:
```
sudo rm -rf .e
``` 
Go back to Login Window (CTRL+ALt+F7)
and log to Enlightenment, to see if that work.

Good luck

---

### Post by jcrus on 2008-12-06
):P Thanks for your awesome work! I'm new to the Linux community (was on a mac, recently bought a Dell, hated Vista), and am loving Ubuntu so far. I especially like E17 as a WM. However, there's been a few problems that I have that I wanted to run by you to see if you or anyone reading this has had similar problems. The graphics transitions seem to be really slow. I know this is a bit more resource-intensive with the eye-candy, but I would imagine my system configuration would allow for a snappier user experience on E17. Also, every once in a while, I'll try to click to get to another window, the system lags entirely to the point I have to restart Ubuntu. Mouse moves and all, but nothing inside E17 responds to clicks or types. Here's my current system configuration:

Dell Studio 1536
AMD Turion X2 64 Bit Processor (RM-70)
3GB DDR2 Ram
ATI Radeon HD 3200

I'd love to get everything running smoothly, as I do prefer E17's scheme over Gnomes. I have some Unix experience, but no where experienced enough to mess around with programming without some guidance. Thanks for your guide and your help!

---

### Post by darkenedday on 2008-12-06
alright guys, btw rui pais, your solution to my session problem worked beautifully 

the wicd on the other hand smartboyathome, looks like it would be a wonderful app (altho I found out why the default connection manager to enlightenment would not work, a connection manager has to be run as root to see any connections) 
however, wicd, even though I can get it to see connections will not connect to anything, I think it may be due to the things I had to go through getting my wireless to detect everything is roaming mode before but I can't be sure, I do know this:

under preferances in WICD client it says "eth0" and "wlan0" for the wired and wireless connections, ifconfig will show eth0 when it is plugged in, I don't know about wlan0 being I can't get it working, in wicd client the eth0 wnt even connect though, and I see it says "putting interface down" which I'm assuming is ifdown?

so i ran ifconfig, it shows eth0 and lo, but, new problem 
I run ifup eth0 and I get something along the lines of:
"ignoring unkown interface eth0=eth0" when it should have said "eth0 is already configured"
i run "ifdown eth0" and get "eth0 is not configured"

I'm confused. . . any ideas?

---

### Post by kevdog on 2008-12-06
Using Intrepid and running your script.  Is this svn breakage??:

------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/var/cache/e17_src/eet'
Making all in src
make[2]: Entering directory `/var/cache/e17_src/eet/src'
Making all in lib
make[3]: Entering directory `/var/cache/e17_src/eet/src/lib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/var/cache/e17_src/eet/src/lib'
Making all in bin
make[3]: Entering directory `/var/cache/e17_src/eet/src/bin'
/bin/bash ../../libtool --tag=CC   --mode=link gcc -std=gnu99   -Wl,--as-needed -L/opt/e17/lib -o eet eet-eet_main.o ../../src/lib/libeet.la 
libtool: link: gcc -std=gnu99 -Wl,--as-needed -o .libs/eet eet-eet_main.o  -L/opt/e17/lib ../../src/lib/.libs/libeet.so -L/usr/lib /usr/lib/libgnutls.so /usr/lib/libtasn1.so /lib/libgcrypt.so -lssl -lcrypto /opt/e17/lib/libeina.so -lrt -ldl -lz /usr/lib/libjpeg.so -lm
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setiv'
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setkey'
collect2: ld returned 1 exit status
make[3]: *** [eet] Error 1
make[3]: Leaving directory `/var/cache/e17_src/eet/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/eet/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/eet'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/eet.log'!

---

### Post by smartboyathome on 2008-12-06
> **darkenedday said:**
> the wicd on the other hand smartboyathome, looks like it would be a wonderful app (altho I found out why the default connection manager to enlightenment would not work, a connection manager has to be run as root to see any connections) 
however, wicd, even though I can get it to see connections will not connect to anything, I think it may be due to the things I had to go through getting my wireless to detect everything is roaming mode before but I can't be sure, I do know this:

under preferances in WICD client it says "eth0" and "wlan0" for the wired and wireless connections, ifconfig will show eth0 when it is plugged in, I don't know about wlan0 being I can't get it working, in wicd client the eth0 wnt even connect though, and I see it says "putting interface down" which I'm assuming is ifdown?

so i ran ifconfig, it shows eth0 and lo, but, new problem 
I run ifup eth0 and I get something along the lines of:
"ignoring unkown interface eth0=eth0" when it should have said "eth0 is already configured"
i run "ifdown eth0" and get "eth0 is not configured"

I'm confused. . . any ideas?

So you only see eth0 when you run ifconfig? In that case, then it isn't recognising your wireless card. Can you post the exact output of ifconfig?

---

### Post by darkenedday on 2008-12-06
I'm using my Mac OS X partition on my dell laptop to post these atm I don't have another pc to use. . .

ifconfig doesn't show wlan0 however wicd does show wireless networks, and will get as far as getting an IP address but won't connect

I previously blacklisted the driver for my wireless card and used the ndiswrapper windows driver instead, it gets better bandwidth. . . it's a WPA2 encrypted network, if that helps, I've been having trouble ever since I installed kubuntu-desktop to try out kde 4.1 (a huge letdown btw) 

I just can't understand why it gets so far and then nothing. . . 
and even my wired connection won't work. . .

I'll see what I can do about getting you the exact output of ifconfig and all that. . .

thanks for the help, how late will you be on?

---

### Post by smartboyathome on 2008-12-06
Ok, thats the problem. Preferences > WPA Supplicant Driver drop-down > Select ndiswrapper instead of wext. Then it should work for you. :)

---

### Post by darkenedday on 2008-12-06
i tried that, it didn't work. . .

update though, it seems if i log in to a something first, wlan0 does show up however i still get the error 

"ignoring unknown device wlan0=wlan0"

on issuing the ifup command. . .

also another device shows up in ifconfig now 

wlan0:avahi

---

### Post by smartboyathome on 2008-12-07
I know that WICD locks up the network connections its using, so thats why it gives you that message.

As for how to connect, have you tried other WPA Supplicant Drivers? Sounds like you're card may either have a bug or the amount of time to obtain your IP is too long (the latter I had a problem with for a while, but then dissapeared).

---

### Post by Capt_Zaphod on 2008-12-07
> **Rui Pais said:**
> Please, [read this here.]("http://ubuntuforums.org/showpost.php?p=5788241&postcount=8")
I will change my first post to prevent repetions of this.



Right now SVN it's broken, anyway (revision 37962).
You need a previous revision!
If you already had at least downlaod code you can after:
```
sudo apt-get install cvs
```
try:
```
sudo easy_e17.sh  --skip-srcupdate
```

If your revision it's already 37962, you may need to wait or install a previous revision.
At this point, I'm not sure what version I've got ...
I tried this bit of code, that you posted and got this:
> --------------------------- Easy_e17.sh 1.2.2.4-OzOS ---------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      [http://svn.enlightenment.org/svn/e/trunk](http://svn.enlightenment.org/svn/e/trunk)
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus exalt e entrance edje_editor edje_viewer elicit elitaire enthrall emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu deskshow diskio efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt exhibit rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w 

  Skip src update: yes
  Script action:   MISSING!
--------------------------------------------------------------------------------

----------------- Short help 'easy_e17.sh <ACTION> <OPTIONS...>' ---------------
  -i, --install    = action: compile and install ALL of e17
  -u, --update     = action: update your installed e17
      --help       = full help
--------------------------------------------------------------------------------


Thank you again.

---

### Post by Aquastus on 2008-12-07
Hello!
I'm using debian sid.
I get an error while installing elitaire. Also it doesn't seem to find exalt.

```

------------------------------ Installing packages -----------------------------
- eina ....................... ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... ok          
- emotion .................... SKIPPED
- etk ........................ ok          
- etk_extra .................. ok          
- ewl ........................ ok          
- exml ....................... SKIPPED
- enhance .................... SKIPPED
- e_dbus ..................... ok          
- exalt ...................... NOT FOUND
- e .......................... ok          
- entrance ................... ok          
- edje_editor ................ SKIPPED
- edje_viewer ................ ok          
- elicit ..................... SKIPPED
- elitaire ................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/var/cache/e17_src/elitaire/data'
make[2]: Leaving directory `/var/cache/e17_src/elitaire/data'
Making all in src
make[2]: Entering directory `/var/cache/e17_src/elitaire/src'
g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include/ewl -I/opt/e17/include/efreet -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/e17/include -Wall -O2 -g -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.cpp
g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include/ewl -I/opt/e17/include/efreet -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/e17/include -Wall -O2 -g -g -O2 -MT eli_app.o -MD -MP -MF .deps/eli_app.Tpo -c -o eli_app.o eli_app.cpp
In file included from /opt/e17/include/Evas.h:35,
                 from /opt/e17/include/Ecore_Config.h:37,
                 from Eli_App.h:2,
                 from eli_app.cpp:2:
/opt/e17/include/Evas_Data.h: In function &#8216;void evas_hash_free(Eina_Hash*)&#8217;:
/opt/e17/include/Evas_Data.h:118: error: return-statement with a value, in function returning 'void'
In file included from /opt/e17/include/Evas.h:35,
                 from /opt/e17/include/Ecore_Evas.h:51,
                 from main.cpp:3:
/opt/e17/include/Evas_Data.h: In function &#8216;void evas_hash_free(Eina_Hash*)&#8217;:
/opt/e17/include/Evas_Data.h:118: error: return-statement with a value, in function returning 'void'
make[2]: *** [eli_app.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/var/cache/e17_src/elitaire/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/elitaire'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/elitaire.log'!


```

---

### Post by smartboyathome on 2008-12-07
> **Aquastus said:**
> Hello!
I'm using debian sid.
I get an error while installing elitaire. Also it doesn't seem to find exalt.

```

------------------------------ Installing packages -----------------------------
- eina ....................... ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... ok          
- emotion .................... SKIPPED
- etk ........................ ok          
- etk_extra .................. ok          
- ewl ........................ ok          
- exml ....................... SKIPPED
- enhance .................... SKIPPED
- e_dbus ..................... ok          
- exalt ...................... NOT FOUND
- e .......................... ok          
- entrance ................... ok          
- edje_editor ................ SKIPPED
- edje_viewer ................ ok          
- elicit ..................... SKIPPED
- elitaire ................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/var/cache/e17_src/elitaire/data'
make[2]: Leaving directory `/var/cache/e17_src/elitaire/data'
Making all in src
make[2]: Entering directory `/var/cache/e17_src/elitaire/src'
g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include/ewl -I/opt/e17/include/efreet -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/e17/include -Wall -O2 -g -g -O2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.cpp
g++ -DHAVE_CONFIG_H -I. -I.. -D_REENTRANT -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include/ewl -I/opt/e17/include/efreet -I/usr/include/cairo -I/usr/include/freetype2 -I/usr/include/directfb -I/usr/include/libpng12 -I/usr/include/pixman-1    -I/opt/e17/include -Wall -O2 -g -g -O2 -MT eli_app.o -MD -MP -MF .deps/eli_app.Tpo -c -o eli_app.o eli_app.cpp
In file included from /opt/e17/include/Evas.h:35,
                 from /opt/e17/include/Ecore_Config.h:37,
                 from Eli_App.h:2,
                 from eli_app.cpp:2:
/opt/e17/include/Evas_Data.h: In function ‘void evas_hash_free(Eina_Hash*)’:
/opt/e17/include/Evas_Data.h:118: error: return-statement with a value, in function returning 'void'
In file included from /opt/e17/include/Evas.h:35,
                 from /opt/e17/include/Ecore_Evas.h:51,
                 from main.cpp:3:
/opt/e17/include/Evas_Data.h: In function ‘void evas_hash_free(Eina_Hash*)’:
/opt/e17/include/Evas_Data.h:118: error: return-statement with a value, in function returning 'void'
make[2]: *** [eli_app.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/var/cache/e17_src/elitaire/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/elitaire'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/elitaire.log'!


```

About Exalt: Its not included with the script since its not been fully migrated to the main E17 svn server, and is still hosted on its own SVN server.

About the error: I think Elitaire hasn't been updated since Evas was updated. Which means elitaire won't compile until it is unless you have an older Evas lib installed. :(

---

### Post by darkenedday on 2008-12-07
alright thanks for the help smartboyathome, I seem to have fixed the problem

I unloaded my ndiswrapper driver, and loaded the wl proprietary driver, it would seem when I upgraded from hardy to intrepid it must have caused a conflict with the ndiswrapper driver and the original opensource driver, it connects in seconds now, I only have one more question to ask you

The client must be run as root, but I would like to add it to my start up programs in enlightenment, is it possible to simple use sudo in the file I have to create and have it bring up a password prompt? I tried using the run command and typing "gksu wicd-client --no-tray" but no prompt comes up for my password and nothing happens, I would like to simply have the client open on start up so that my fiance who knows nothing about the command line can still access the internet when I remove gnome. . .

thanks again!
~darkenedday

---

### Post by smartboyathome on 2008-12-07
I think you can make gksu come up by adding sleep before the gksu command. Try something like this:
sleep 10 && gksu wicd-client --no-tray

May I ask you why you need to run it as root though? On my laptop, it runs fine as a normal user. I do have to admit though, I'm on Arch Linux and my laptop uses an Intel 4965 wireless card.

---

### Post by kevdog on 2008-12-08
I'm going to ask for help one more time.  Thanks


Using Intrepid and running your script. Is this svn breakage??:

------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make all-recursive
make[1]: Entering directory `/var/cache/e17_src/eet'
Making all in src
make[2]: Entering directory `/var/cache/e17_src/eet/src'
Making all in lib
make[3]: Entering directory `/var/cache/e17_src/eet/src/lib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/var/cache/e17_src/eet/src/lib'
Making all in bin
make[3]: Entering directory `/var/cache/e17_src/eet/src/bin'
/bin/bash ../../libtool --tag=CC --mode=link gcc -std=gnu99 -Wl,--as-needed -L/opt/e17/lib -o eet eet-eet_main.o ../../src/lib/libeet.la
libtool: link: gcc -std=gnu99 -Wl,--as-needed -o .libs/eet eet-eet_main.o -L/opt/e17/lib ../../src/lib/.libs/libeet.so -L/usr/lib /usr/lib/libgnutls.so /usr/lib/libtasn1.so /lib/libgcrypt.so -lssl -lcrypto /opt/e17/lib/libeina.so -lrt -ldl -lz /usr/lib/libjpeg.so -lm
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setiv'
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setkey'
collect2: ld returned 1 exit status
make[3]: *** [eet] Error 1
make[3]: Leaving directory `/var/cache/e17_src/eet/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/eet/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/eet'
make: *** [all] Error 2
--------------------------------------------------------------------------------

---

### Post by smartboyathome on 2008-12-08
kevdog: Seems like it. Though if I were you I would wait for Rui to answer, since he's better at knowing that stuff than I am since I am on arch. ;)

---

### Post by Aquastus on 2008-12-08
OK, now I got another error while installing emotion.
```

------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... previously installed
- emotion .................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking whether to build static libraries... yes
configure: creating libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EVAS... yes
checking for EDJE... yes
checking for ECORE... yes
checking Ecore_X.h usability... yes
checking Ecore_X.h presence... yes
checking for Ecore_X.h... yes
checking Ecore_Fb.h usability... no
checking Ecore_Fb.h presence... no
checking for Ecore_Fb.h... no
checking for VLC... no
checking for XINE... configure: error: Package requirements (libxine >= 1.1.1) were not met:

No package 'libxine' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XINE_CFLAGS
and XINE_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/emotion.log'!

```

---

### Post by smartboyathome on 2008-12-08
Install libxine-dev (or whatever its called) and it will use that.

---

### Post by darkenedday on 2008-12-08
> **smartboyathome said:**
> I think you can make gksu come up by adding sleep before the gksu command. Try something like this:
sleep 10 && gksu wicd-client --no-tray

May I ask you why you need to run it as root though? On my laptop, it runs fine as a normal user. I do have to admit though, I'm on Arch Linux and my laptop uses an Intel 4965 wireless card.

it actually runs fine as a normal user now, but before with whatever driver it was using, or whatever it was doing (I honestly have no idea) it wouldn't show any networks as a normal user and it would as root, wierd huh? thanks for the help :-)

btw how is arch linux? it's one of the ones i never gave a try, I thought it would be something like using slackware but wasn't sure, my two favorite were slackware and gentoo, but I use ubuntu because my fiance uses this computer as well, and it's easier to show someone how to use, people always forget they had to learn to use windows, and despise having to learn something new

---

### Post by smartboyathome on 2008-12-08
> **darkenedday said:**
> btw how is arch linux? it's one of the ones i never gave a try, I thought it would be something like using slackware but wasn't sure, my two favorite were slackware and gentoo, but I use ubuntu because my fiance uses this computer as well, and it's easier to show someone how to use, people always forget they had to learn to use windows, and despise having to learn something new

Arch Linux is good. Its actually a lot easier than it seems, and is more like an Ubuntu minimal install than anything else. :)

---

### Post by kevdog on 2008-12-08
Dang Rui Pais -- What's taking so long??  I'll admit it, I'm impatient!!

---

### Post by darkenedday on 2008-12-08
alright so I'm not out of the woods yet. . .

at this point I may as well be using slackware lol

2 new problems


1.)BIGGEST PROBLEM: rebooted my laptop today, and somehow the wireless switch got turned off, so I turned it back on, and still no wifi light on the laptop, so I reboot, still no light, nor wireless networks, so, I log back into gnome, look at the restricted device manager, and it says my Wl driver is activated but not in use, this is strange. . . .
          So I deactive and reactivate it, still nothing but it says the driver is in use now, and the light came back on. . . think there could be some kind of conflict with the standard driver and the restricted? Every time I restart it sets the resitricted driver to not in use but active. . .

2.)BIG ANNOYANCE, I added the gnome settings to my start up programs in enlightenment, now, when I start up enlightenment when the gnome settings get loaded the main bar (I have it on the top filling the screen left to right with the icon in the left corner like a mac) gets extended out of the screen, the other two "shelves" I have (one invisible one on the right with a clock in the top right corner on the right side and one in the center with icons on the bottom) seem fine, the top one just seems off, and the center of the splash screen shifts to the right. . .

any ideas?

---

### Post by Rui Pais on 2008-12-09
> **kevdog said:**
> I'm going to ask for help one more time.  Thanks


Using Intrepid and running your script. Is this svn breakage??:

------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make all-recursive
make[1]: Entering directory `/var/cache/e17_src/eet'
Making all in src
make[2]: Entering directory `/var/cache/e17_src/eet/src'
Making all in lib
make[3]: Entering directory `/var/cache/e17_src/eet/src/lib'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/var/cache/e17_src/eet/src/lib'
Making all in bin
make[3]: Entering directory `/var/cache/e17_src/eet/src/bin'
/bin/bash ../../libtool --tag=CC --mode=link gcc -std=gnu99 -Wl,--as-needed -L/opt/e17/lib -o eet eet-eet_main.o ../../src/lib/libeet.la
libtool: link: gcc -std=gnu99 -Wl,--as-needed -o .libs/eet eet-eet_main.o -L/opt/e17/lib ../../src/lib/.libs/libeet.so -L/usr/lib /usr/lib/libgnutls.so /usr/lib/libtasn1.so /lib/libgcrypt.so -lssl -lcrypto /opt/e17/lib/libeina.so -lrt -ldl -lz /usr/lib/libjpeg.so -lm
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setiv'
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setkey'
collect2: ld returned 1 exit status
make[3]: *** [eet] Error 1
make[3]: Leaving directory `/var/cache/e17_src/eet/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/eet/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/eet'
make: *** [all] Error 2
--------------------------------------------------------------------------------

> **kevdog said:**
> Dang Rui Pais -- What's taking so long??  I'll admit it, I'm impatient!!


Hi kevdog.
Sorry but the last days i've been busy as a hell with work.

Yes that looks like a SVN breakage. As long as script runs and compilation starts, any issues are generally code breakage. 
Since the move to SVN it happens a lot ... :(

In last week they seems to be make some deep changes in look&feel, mainly with configuration windows and main menus. It's a bit unstable now, some things don't work with old themes, and devs seems to uploading code without much checking on code breakage.

On these situation, one either waits a couple of hours to see if breakage has been solved or get back to some stable revision and wait a couple of days (or even more) before updating again.

Please you can check Cafelinux announcements for breakage (when we detect them) here:
[http://cafelinux.org/forum/index.php/topic,2232.0.html](http://cafelinux.org/forum/index.php/topic,2232.0.html)

 
Anyway, I just finish update now and all compile normally.

---

### Post by Rui Pais on 2008-12-09
> **darkenedday said:**
> alright so I'm not out of the woods yet. . .

at this point I may as well be using slackware lol

2 new problems


1.)BIGGEST PROBLEM: rebooted my laptop today, and somehow the wireless switch got turned off, so I turned it back on, and still no wifi light on the laptop, so I reboot, still no light, nor wireless networks, so, I log back into gnome, look at the restricted device manager, and it says my Wl driver is activated but not in use, this is strange. . . .
          So I deactive and reactivate it, still nothing but it says the driver is in use now, and the light came back on. . . think there could be some kind of conflict with the standard driver and the restricted? Every time I restart it sets the resitricted driver to not in use but active. . .


Sorry i can't help much here, i don't have much experience with wireless/wicd.
May i suggest you make a post on Network section of forum, where you should get much more experienced users on such subject. 
You can post a link here to it so smartboyathome can continue helping you, if he knows the issue.
Thanks.


> **darkenedday said:**
> 
2.)BIG ANNOYANCE, I added the gnome settings to my start up programs in enlightenment, now, when I start up enlightenment when the gnome settings get loaded the main bar (I have it on the top filling the screen left to right with the icon in the left corner like a mac) gets extended out of the screen, the other two "shelves" I have (one invisible one on the right with a clock in the top right corner on the right side and one in the center with icons on the bottom) seem fine, the top one just seems off, and the center of the splash screen shifts to the right. . .

any ideas?

I'm not sure ... 
How do you load gnome settings? (gnome-settings-daemon? from start desktop? script?)
Have you configure your shelves with the gnome settings loaded? Can you edit the configuration after gnome-settings load? 
Would be easier if you just set a .gtkrc-2.0/.gtkrc-2.0.mine file?
Btw, what splash screen are you referring?

---

### Post by amrlima on 2008-12-09
I'm running to some problems installing e17 using the script. Last night I installed it and everything went fine, but when I logged in it outputted an error which I couldn't read well because the window was nor visible but the options where F1(recover) and F2(exit). I suspect this was an error from a previous e17 installation which gave the same error. It was installed from another repository.

Now trying to purge and reinstall I get the following error:

```
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/var/cache/e17_src/ecore'
Making all in src
make[2]: Entering directory `/var/cache/e17_src/ecore/src'
Making all in lib
make[3]: Entering directory `/var/cache/e17_src/ecore/src/lib'
Making all in ecore
make[4]: Entering directory `/var/cache/e17_src/ecore/src/lib/ecore'
/bin/bash ../../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../..   -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina     -MT ecore_getopt.lo -MD -MP -MF .deps/ecore_getopt.Tpo -c -o ecore_getopt.lo ecore_getopt.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../../.. -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -MT ecore_getopt.lo -MD -MP -MF .deps/ecore_getopt.Tpo -c ecore_getopt.c  -fPIC -DPIC -o .libs/ecore_getopt.o
In file included from ecore_getopt.c:1:
Ecore_Getopt.h:375: error: expected ‘)’ before ‘*’ token
make[4]: *** [ecore_getopt.lo] Error 1
make[4]: Leaving directory `/var/cache/e17_src/ecore/src/lib/ecore'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/var/cache/e17_src/ecore/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/ecore'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/ecore.log'!

```

SVN problem also?

Thanks!

---

### Post by Rui Pais on 2008-12-09
> **amrlima said:**
> I'm running to some problems installing e17 using the script. Last night I installed it and everything went fine, but when I logged in it outputted an error which I couldn't read well because the window was nor visible but the options where F1(recover) and F2(exit). I suspect this was an error from a previous e17 installation which gave the same error. It was installed from another repository.

Now trying to purge and reinstall I get the following error:

```
touch config.h.in
cd . && /bin/bash ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/var/cache/e17_src/ecore'
Making all in src
make[2]: Entering directory `/var/cache/e17_src/ecore/src'
Making all in lib
make[3]: Entering directory `/var/cache/e17_src/ecore/src/lib'
Making all in ecore
make[4]: Entering directory `/var/cache/e17_src/ecore/src/lib/ecore'
/bin/bash ../../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../../..   -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina     -MT ecore_getopt.lo -MD -MP -MF .deps/ecore_getopt.Tpo -c -o ecore_getopt.lo ecore_getopt.c
libtool: compile:  gcc -DHAVE_CONFIG_H -I. -I../../.. -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -MT ecore_getopt.lo -MD -MP -MF .deps/ecore_getopt.Tpo -c ecore_getopt.c  -fPIC -DPIC -o .libs/ecore_getopt.o
In file included from ecore_getopt.c:1:
Ecore_Getopt.h:375: error: expected ‘)’ before ‘*’ token
make[4]: *** [ecore_getopt.lo] Error 1
make[4]: Leaving directory `/var/cache/e17_src/ecore/src/lib/ecore'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/var/cache/e17_src/ecore/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/ecore'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/ecore.log'!

```

SVN problem also?

Thanks!


Yes, thats right! Again!
Revision 38063 it's broken for ecore 
(i think it was the update for eina that create some incompatibility with when ecore compiles against).
Revision 38056 it's good!


You either install a that one or wait a little and see if this get fixed soon.
:(


(OT, Just curious, what part of Açores?)

---

### Post by amrlima on 2008-12-09
> **Rui Pais said:**
> Yes, thats right! Again!
Revision 38063 it's broken for ecore 
(i think it was the update for eina that create some incompatibility with when ecore compiles against).
Revision 38056 it's good!


You either install a that one or wait a little and see if this get fixed soon.
:(

(OT, Just curious, what part of Açores?)

I guess I'll wait a bit.... hopefully not long :)

OT: São Miguel, Ponta Delgada nowadays. You're from Azores as well?

---

### Post by Rui Pais on 2008-12-09
> **amrlima said:**
> I guess I'll wait a bit.... hopefully not long :)

Ok. I'll post here when they fix it.
:)


> **amrlima said:**
> 
OT: São Miguel, Ponta Delgada nowadays. You're from Azores as well?
Well once i visited Açores and... i think i lost part of my soul somewhere there (if you see it don't send it home ok? ;))
Since then it's my favorite holiday destiny, every 2-3 years i go to Açores. Usually Pico, but i know Terceira and visit briefly São Jorge, Faial and Graciosa. One of these days we will visit yours... Like a chocolate box, we leave the shinning ones to the end :)

---

### Post by darkenedday on 2008-12-09
> **Rui Pais said:**
> Sorry i can't help much here, i don't have much experience with wireless/wicd.
May i suggest you make a post on Network section of forum, where you should get much more experienced users on such subject. 
You can post a link here to it so smartboyathome can continue helping you, if he knows the issue.
Thanks.




I'm not sure ... 
How do you load gnome settings? (gnome-settings-daemon? from start desktop? script?)
Have you configure your shelves with the gnome settings loaded? Can you edit the configuration after gnome-settings load? 
Would be easier if you just set a .gtkrc-2.0/.gtkrc-2.0.mine file?
Btw, what splash screen are you referring?

I'm referring to the defualt enlightenment splash screen, and I added gnome-settings-daemon to my applications via the settings menu then added that to start up, I wouldn't really know where to begine with the .gtkrc-2.0 file. . .

---

### Post by Rui Pais on 2008-12-09
> **darkenedday said:**
> I'm referring to the defualt enlightenment splash screen, and I added gnome-settings-daemon to my applications via the settings menu then added that to start up, I wouldn't really know where to begine with the .gtkrc-2.0 file. . .

See my notes "STARTUP AND CONFIGURATION LOOK" on the end of 1sr post.

Essentially just edit/create a file ~/.gtkrc-2.0 with your preferences.
Something like:```

 gtk-theme-name = "Human"
 gtk-icon-theme-name = "Tango"
 gtk-font-name = "Bitstream Vera Sans 11"
```

Another way, to prevent overwriting from other apps/configurators, it's to create a ~/.gtkrc-2.0.mine instead with the preferences and just add to .gtkrc-2.0:
```
include "/home/<your_user_name_here>/.gtkrc-2.0.mine"
```


I test gnome-settings-daemon and it wont do no bad behavior, except make fonts look to big on gtk apps... I don't know what could be causing your problems, sorry.
Let me know how your experiences with .gtkrc goes. Don't forget to remove gnome-settings daemon to test the .gtkrc way.

---

### Post by Rui Pais on 2008-12-09
Just an update to inform that the ecore issue it's fixed. 
Revision 38068.
:)

---

### Post by amrlima on 2008-12-09
> **Rui Pais said:**
> Ok. I'll post here when they fix it.
:)

Good to see it's ready now :). I'll try to install later. Right now I'm using e17 in Fedora 10 which from it's repositories. It's quite stable here but there are quite a few modules missing tough.



> **Rui Pais said:**
> Well once i visited Açores and... i think i lost part of my soul somewhere there (if you see it don't send it home ok? ;))
Since then it's my favorite holiday destiny, every 2-3 years i go to Açores. Usually Pico, but i know Terceira and visit briefly São Jorge, Faial and Graciosa. One of these days we will visit yours... Like a chocolate box, we leave the shinning ones to the end :)

You've been around a lot I see. I hope you like S.Miguel, somethings here are overwhelming and there is a LOT to see around.

---

### Post by amrlima on 2008-12-09
I managed to install e17 from svn now. But I'm having the same as I did with e17 from another repository: e17 just crashes at startup and I have the option to restart F1 or quit F2. I've purged e17 and reinstalled but the problem persists... All modules are unloaded when I login.

Anyone as a clue of what this could be?

---

### Post by Rui Pais on 2008-12-09
> **amrlima said:**
> I managed to install e17 from svn now. But I'm having the same as I did with e17 from another repository: e17 just crashes at startup and I have the option to restart F1 or quit F2. I've purged e17 and reinstalled but the problem persists... All modules are unloaded when I login.

Anyone as a clue of what this could be?

Maybe you got a broken configuration.
Try from another desktop or from a console (press ctrl+Alt+F1)
```
rm -rf ~/.e
```
and after that try to log at Enlightenment again.

If that don't fix it, i can only imagine that some e17 libs from your previous installation still lie somewhere on your system, and compilation by easy_e17sh was made against those, instead of correct ones...

Check first configuration issues. 



> **amrlima said:**
> I hope you like S.Miguel, somethings here are overwhelming and there is a LOT to see around.
What in Açores it's not overwhelming!? :lol:

---

### Post by amrlima on 2008-12-09
> **Rui Pais said:**
> Maybe you got a broken configuration.
Try from another desktop or from a console (press ctrl+Alt+F1)
```
rm -rf ~/.e
```
and after that try to log at Enlightenment again.

That did not work :( still crashes at startup

> **Rui Pais said:**
> If that don't fix it, i can only imagine that some e17 libs from your previous installation still lie somewhere on your system, and compilation by easy_e17sh was made against those, instead of correct ones...

Yes, that must be it. I propably didn't remove them wen I removed the e17 package... my mistake. Now how do you think it's the best way to remove these libs?

Thanks!!

---

### Post by Rui Pais on 2008-12-09
> **amrlima said:**
> 
Yes, that must be it. I propably didn't remove them wen I removed the e17 package... my mistake. Now how do you think it's the best way to remove these libs?

Thanks!!

How do you install it? a deb package? check with synaptic if it still on listed either on Installed software or the other option (don't remember the name) of not entirely purge it. 
Delete and purge all.

After that do a search for libe* (things like libecore*, libetk*, libefreet*) They must be all on /opt/e17/lib/ if you still have e17-svn installed. Other paths like /usr/lib /usr/local/ etc. are leftovers of another install!

Good luck!

---

### Post by amrlima on 2008-12-09
> **Rui Pais said:**
> How do you install it? a deb package? check with synaptic if it still on listed either on Installed software or the other option (don't remember the name) of not entirely purge it. 
Delete and purge all.

After that do a search for libe* (things like libecore*, libetk*, libefreet*) They must be all on /opt/e17/lib/ if you still have e17-svn installed. Other paths like /usr/lib /usr/local/ etc. are leftovers of another install!

Good luck!

I installed from [http://xsm.alphagemini.org/E17/repository/](http://xsm.alphagemini.org/E17/repository/).

I've removed all the libs and gonna try to reinstall now. Thanks for the help Rui!

---

### Post by amrlima on 2008-12-09
> **amrlima said:**
> I installed from [http://xsm.alphagemini.org/E17/repository/](http://xsm.alphagemini.org/E17/repository/).

I've removed all the libs and gonna try to reinstall now. Thanks for the help Rui!

Didn't work, still got the same crash at startup :(. I really don't know what I'm missing here... Guess I'll have to dig some more..

---

### Post by kevdog on 2008-12-09
I have to say this is really p***ing me off!  Ok after receiving an infraction for that statement.   I just upgraded the svn sources and still cannot compile eet.  Here is the error:

../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setiv'
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setkey'
collect2: ld returned 1 exit status
make[3]: *** [eet] Error 1
make[3]: Leaving directory `/var/cache/e17_src/eet/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/eet/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/eet'
make: *** [all] Error 2

gcry_cipher_**** is part of the libgcrypt library which I do have installed.  So where exactly is the problem?

---

### Post by darkenedday on 2008-12-10
hey smartboyathome, or anyone who is good with wicd and networking, take a look at this and let me know if you can help, please?

[http://ubuntuforums.org/showthread.php?p=6343475#post6343475](http://ubuntuforums.org/showthread.php?p=6343475#post6343475)

---

### Post by jcrus on 2008-12-10
EDIT: Also, there's a really slow download transfer rate from the cafelinux repo. Transfers average around 3000 B/sec for me. My usual rate for other repos and internet in general is 450+KB/Sec.

Guess I was forgotten in the midst?

Anyhow, I tried with a reinstall, and still having issues with E17 and lock ups. It seems to happen a lot when I try to pull up the menu by right clicking on the desktop. It'll freeze right there and just stop. I can still ctrl-alt-backspace and launch back into it from the startup manager. Some things I forgot to mention is I am using the fglrx driver for my ATI card from the ubuntu repositories rather than ATI itself, just because I was having headaches with ATI's newest driver. Also, I had compiz installed for my GNOME desktop, and I think it was causing errors with that as well. The desktop wouldn't crash per se, but I couldn't click on anything except in the taskbar nor enter any text. Again, ctrl-alt-backspace worked. I'm trying without compiz installed to see if that helps for Gnome at least, if that gets stable I'll try E17 again. I did download the update for E17 (38088) today, so maybe that will fix my problem too. Any insights??


> **jcrus said:**
> ):P Thanks for your awesome work! I'm new to the Linux community (was on a mac, recently bought a Dell, hated Vista), and am loving Ubuntu so far. I especially like E17 as a WM. However, there's been a few problems that I have that I wanted to run by you to see if you or anyone reading this has had similar problems. The graphics transitions seem to be really slow. I know this is a bit more resource-intensive with the eye-candy, but I would imagine my system configuration would allow for a snappier user experience on E17. Also, every once in a while, I'll try to click to get to another window, the system lags entirely to the point I have to restart Ubuntu. Mouse moves and all, but nothing inside E17 responds to clicks or types. Here's my current system configuration:

Dell Studio 1536
AMD Turion X2 64 Bit Processor (RM-70)
3GB DDR2 Ram
ATI Radeon HD 3200

I'd love to get everything running smoothly, as I do prefer E17's scheme over Gnomes. I have some Unix experience, but no where experienced enough to mess around with programming without some guidance. Thanks for your guide and your help!

---

### Post by amrlima on 2008-12-10
I keep getting a SEGV message at boot and all modules are unloaded:

```
This is very bad. Enlightenment SEGV'd
This is not meant to happen and is likely a sign of a bug in
Enlightenment or the libraries it relies on. You can gdb attach to
this process now to try debug it or you could exit, or just hit
restart to try and get your desktop back the way it was.
```

---

### Post by darkenedday on 2008-12-10
----------------------------- Source checkout/update ---------------------------
- checkout sources ...
   downloading eina source ...
svn: OPTIONS of 'http://svn.enlightenment.org/svn/e/trunk/eina': could not connect to server ([http://svn.enlightenment.org](http://svn.enlightenment.org))


I don't get it, I'm browsing online while it's going, so it's not my connection

btw I got wicd working fine, but had to reinstall

---

### Post by smartboyathome on 2008-12-11
Could it be you are behind a proxy? Thats the only thing I can think of which would block that.

---

### Post by darkenedday on 2008-12-11
nope, no proxy no firewall (except the usual one on the router)

works today though :-)

---

### Post by darkenedday on 2008-12-12
alright everything up and running on ubuntu 8.04, it would seem that e17 doesn't work so well with 8.10 (then again I had a huge ammount of problems with 8.10, no sound nvidia was somehow a pain again, etc. etc.) I'll be sticking with the lts untill the next version. Great svn! loving my new e17 desktop, so much prettier and more efficient than Gnome!

---

### Post by worldwithoutgurus on 2008-12-12
No problems with Ubuntu 8.10 + E17 svn.
Works fine here.

---

### Post by nublaii on 2008-12-14
I am running a clean 8.10 install and I was able to install it with no problems. I followed the instructions to create and symlink .xinitrc and .xsession files but it crashes on load with an error about the 'Sans' font... any idea how to fix that?

This is the error:

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
ESTART: 0.00000 [0.00000] - begin
ESTART: 0.00009 [0.00009] - signals done
ESTART: 0.00013 [0.00004] - determine prefix
DYNAMIC DETERMINED PREFIX: /opt/e17
ESTART: 0.00042 [0.00029] - prefix done
ESTART: 0.00245 [0.00203] - intl init
ESTART: 0.00260 [0.00015] - parse args
ESTART: 0.00263 [0.00004] - arg parse done
ESTART: 0.00268 [0.00005] - ecore init
ESTART: 0.00701 [0.00433] - ecore_file init
ESTART: 0.01048 [0.00346] - more ecore
ESTART: 0.01059 [0.00011] - x connect
ESTART: 0.07489 [0.06431] - ecore_con
ESTART: 0.07549 [0.00060] - xinerama
E17 INIT: XINERAMA CHOSEN: [0], 1680x1050+0+0
ESTART: 0.07573 [0.00024] - x hints
ESTART: 0.07600 [0.00027] - x hints done
ESTART: 0.07604 [0.00004] - ecore_evas init
ESTART: 0.07650 [0.00046] - test done
ESTART: 0.07655 [0.00005] - efreet
ESTART: 0.07677 [0.00022] - efreet done
ESTART: 0.07680 [0.00003] - configure
ESTART: 0.07688 [0.00008] - dirs
ESTART: 0.07706 [0.00019] - filereg
ESTART: 0.07709 [0.00003] - config
ESTART: 0.07831 [0.00122] - scale
ESTART: 0.07845 [0.00013] - pointer
ESTART: 0.07848 [0.00004] - path
ESTART: 0.07857 [0.00009] - ipc
INFO: E_IPC_SOCKET=/tmp/enlightenment-pan/disp-:0.0-7452
ESTART: 0.07886 [0.00030] - font
ESTART: 0.07892 [0.00006] - theme
ESTART: 0.09391 [0.01499] - intl post
ESTART: 0.10227 [0.00836] - splash
ESTART: 0.10253 [0.00026] - test file format support
<<<< Enlightenment Error >>>>
Enlightenment found Evas can't load the 'Sans' font. Check Evas has fontconfig
support and system fontconfig defines a 'Sans' font.

E17: Begin shutdown procedure!

```

---

### Post by kevdog on 2008-12-17
Ok guys thanks for tolerating my complaints and I finally got everything to install.

Here is a problem with the script.  If you have previously installed libgcrypt (such as when compiling gpg2 from source), your script chokes.

I had to uninstall libgcrypt and then reinstall the repository version.  

There was also another workaround but I cant remember

Is there a tutorial how to actually use enlightenment?  I'm finding for example the lack of a cut and paste shortcut in the terminal window to be an annoyance.  Also I did install a system tray app.  Basically I need a tutorial on how to customize the desktop!  I like what I see so far however it does take some getting used to

---

### Post by smartboyathome on 2008-12-17
> **kevdog said:**
> Is there a tutorial how to actually use enlightenment?  I'm finding for example the lack of a cut and paste shortcut in the terminal window to be an annoyance.  Also I did install a system tray app.  Basically I need a tutorial on how to customize the desktop!  I like what I see so far however it does take some getting used to

See [here]("http://cafelinux.org/OzOs/content/how-index") for a bunch of OzOs tutorials. I find I don't need a system tray anymore, you can check out [my Iiirk tutorial]("http://cafelinux.org/OzOs/content/how-simulate-system-tray-iiirk") to see how. Another one which is recommended are the Gadgets, Modules, and Shelves tutorials, [part 1]("http://cafelinux.org/OzOs/content/how-use-gadgets-modules-and-shelves") and [part 2]("http://cafelinux.org/OzOs/content/how-use-gadgets-modules-and-shelves-part-2").

---

### Post by kevdog on 2008-12-17
Awesome tutorials written by you.  The best I have found.  Does everything I want to do.

Just a quick note -- What happened to my Firefox Icon?  Where do I get one of these?

Thanks

---

### Post by smartboyathome on 2008-12-17
> **kevdog said:**
> Awesome tutorials written by you.  The best I have found.  Does everything I want to do.

Just a quick note -- What happened to my Firefox Icon?  Where do I get one of these?

Thanks

They aren't all by me, only the Iiirk one. The rest are by the OzOs devs.

About the firefox icon: Use ibar to add Firefox to it, and right click the icon then click ok in the window that pops up to change it.

---

### Post by super.rad on 2008-12-17
Does anyone know when e17 will be officially released and in the ubuntu repos?

---

### Post by smartboyathome on 2008-12-17
> **super.rad said:**
> Does anyone know when e17 will be officially released and in the ubuntu repos?

E17 won't be officially released anytime soon, so it won't be in the Ubuntu repos anytime soon. Don't talk to raster about it either, he gets grumpy.

---

### Post by kevdog on 2008-12-18
How to I install and run EHB?
[https://www.ohloh.net/rss_feeds/3406/rss_articles](https://www.ohloh.net/rss_feeds/3406/rss_articles)

Just wondering how to install apps since I'm very confused.  I downloaded both the source and svn code, but the standard ./configure didn't work.

---

### Post by smartboyathome on 2008-12-19
Is EHB even in SVN anymore? I can't find it at all. I think EHB is old and broken.

---

### Post by kevdog on 2008-12-26
I seem now to be getting this error when upgrading:

sudo easy_e17.sh -u

..
...
Checking E-MODULES-EXTRA source ... U    E-MODULES-EXTRA/drawer/src/plugins/sources/directory_watcher.c
svn: Failed to add directory 'E-MODULES-EXTRA/notification/m4': an unversioned directory of the same name already exists
svn: Failed to add directory 'E-MODULES-EXTRA/notification/m4': an unversioned directory of the same name already exists
FAILED! Next attempt 3 in 5 second

I didn't do anything to the sources that I am aware of. How do I make this error go away?

Lastly using this eterm is tricky giving multiline cut and paste.  Any tips?

---

### Post by smartboyathome on 2008-12-26
I think deleting the folder would solve your update error for you.

I think eterm is a little dated. Personally, I gave up on using most E17 programs. I just use GTK+ programs on E17, though you could use Qt only just as easily (I think).

---

### Post by nico_h on 2008-12-29
Hello and thank you Rui Pais for this deb, it makes the installation really nice and without any worry !

I just want to precise that in the first post, you mistyped the name of configuration file (you wrote /etc/easy_e17.sh instead of /etc/easy_e17.conf)

And I would like to know why you changed the src path to /var/cache. Is it to be more compliant with usual debian paths ?

I wanted to add the module "places", which is not in the current easy_e17.sh. I didn't know where e17-svn installed the script itself, so I downloaded easy_e17.sh, added the name "places" to the list of packages (in the variable packages at the beginning of easy_e17.sh) and ran it so :

```
# ./easy_e17.sh --only=places --srcpath=/var/cache
```

And it worked perfectly well. Maybe I should precise that my laptop is running UbuntuStudio 8.04.

By the way, [[COLOR="RoyalBlue"]places[/COLOR]]("http://code.google.com/p/e17mods/wiki/Places") is a very nice module. I hope a next easy_e17.sh -u won't break everything !

---

### Post by smartboyathome on 2008-12-29
> **nico_h said:**
> Hello and thank you Rui Pais for this deb, it makes the installation really nice and without any worry !

I just want to precise that in the first post, you mistyped the name of configuration file (you wrote /etc/easy_e17.sh instead of /etc/easy_e17.conf)

And I would like to know why you changed the src path to /var/cache. Is it to be more compliant with usual debian paths ?

I wanted to add the module "places", which is not in the current easy_e17.sh. I didn't know where e17-svn installed the script itself, so I downloaded easy_e17.sh, added the name "places" to the list of packages (in the variable packages at the beginning of easy_e17.sh) and ran it so :

```
# ./easy_e17.sh --only=places --srcpath=/var/cache
```

And it worked perfectly well. Maybe I should precise that my laptop is running UbuntuStudio 8.04.

By the way, [[COLOR="RoyalBlue"]places[/COLOR]]("http://code.google.com/p/e17mods/wiki/Places") is a very nice module. I hope a next easy_e17.sh -u won't break everything !

It was changed to /var/cache because, when it is run as root (like when it installs), it would put the source in ~/.e17_svn, which would put it in /root/ (since that is the root user's home). It is much friendlier to put it in /var/cache/e17_src because it is easier to find.

---

### Post by Tux Aubrey on 2008-12-29
> **nico_h said:**
> Hello and thank you Rui Pais for this deb, it makes the installation really nice and without any worry !

I just want to precise that in the first post, you mistyped the name of configuration file (you wrote /etc/easy_e17.sh instead of /etc/easy_e17.conf)

And I would like to know why you changed the src path to /var/cache. Is it to be more compliant with usual debian paths ?

I wanted to add the module "places", which is not in the current easy_e17.sh. I didn't know where e17-svn installed the script itself, so I downloaded easy_e17.sh, added the name "places" to the list of packages (in the variable packages at the beginning of easy_e17.sh) and ran it so :

```
# ./easy_e17.sh --only=places --srcpath=/var/cache
```

And it worked perfectly well. Maybe I should precise that my laptop is running UbuntuStudio 8.04.

By the way, [[COLOR="RoyalBlue"]places[/COLOR]]("http://code.google.com/p/e17mods/wiki/Places") is a very nice module. I hope a next easy_e17.sh -u won't break everything !

Hi nico_h and thanks for the info on places - I have been tempted to try it and will now do so.  svn code has been very fragile for the past few weeks - it is being updated several times a day and there seems to be a >50% chance of updating to bad code.  

Some older modules seem to be becoming orphaned in this process (eg taskbar and slideshow) and even some of the more recent third-party ones (extra-menus, edgar and friends) seem to miss out.  It will be interesting to watch "places" in this. 

All this means that chronic updaters (guilty) need to be vigilant about finding the cause of any breakage and be prepared to "turn-off" anything non-essential that falls behind.  

Rui's update_e17.sh script makes it particularly easy to maintain a working installation.  The backup and restore functions mean that you can have a "bad code day" and recover immediately.  If you haven't already, do run:

```
update_e17.sh -H 
```

some time and keep the output for reference.

update_e17.sh now checks a flag in a thread at cafelinux.org/forum about whether updating is recommended or not.  But with the speed of changes to svn code recently, we haven't been quick enough to catch every error! 

Just for reference, the list of packages to be downloaded and compiled is in the usr/bin/easy_e17.sh script and the etc/easy_e17.conf file contains the "skip" list.  (Rui's update_e17.sh (also in /usr/bin/) calls easy_17.sh which refers to easy_e17.conf.)

---

### Post by smartboyathome on 2008-12-29
Tux, you will have to post a howto for getting the *other* OzOs repo in order to get update_e17.sh. This howto only gives you easy_e17.sh. :(

---

### Post by barkley128 on 2008-12-30
Well, it seems, there is something wrong.
I tried to reinstall, redownload the sources, but the scipt is not downloading all of them.
When the installation turns to installing packages it outputs:
```

...
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ ok          
- etk_extra .................. NOT FOUND
- ewl ........................ NOT FOUND
...

```
and so on..
But I'd like to know the reason why it can't install some of the packages like ewl, etk_extra..
Why they are not found? I looked at the source dir, there are only a few of necessary packages.
What should I do in order to get this script to download all of them?
After the installation, script says, that everything is fine, but it's not :/

---

### Post by smartboyathome on 2008-12-30
> **barkley128 said:**
> Well, it seems, there is something wrong.
I tried to reinstall, redownload the sources, but the scipt is not downloading all of them.
When the installation turns to installing packages it outputs:
```

...
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ ok          
- etk_extra .................. NOT FOUND
- ewl ........................ NOT FOUND
...

```
and so on..
But I'd like to know the reason why it can't install some of the packages like ewl, etk_extra..
Why they are not found? I looked at the source dir, there are only a few of necessary packages.
What should I do in order to get this script to download all of them?
After the installation, script says, that everything is fine, but it's not :/

1) ewl and etk_extra are not vital to E17 and shouldn't mess it up.
2) It is recommended to use revision 38337 instead of the most recent revision. To do this, move /var/cache/e17_src to /var/cache/e17_src_backup, and then type this command:
```
sudo svn co -r 38337 http://svn.enlightenment.org/svn/e/trunk /var/cache/e17_src
```
Then, after that's done, run:
```
sudo easy_e17.sh -i
```
To reinstall it. Right now, SVN is going through many changes, which frequently break E17. So, stay tuned and pay attention to cafelinux.org/forum to see which revision is recommended.

---

### Post by spajix on 2009-01-01
I got this after following this
```
~$ sudo apt-get install e17-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17-svn: Depends: giblib-dev but it is not installable
           Depends: libgtk1.2-dev but it is not installable
E: Broken packages

```
Any ideas?

---

### Post by Tux Aubrey on 2009-01-01
> **spajix said:**
> I got this after following this
```
~$ sudo apt-get install e17-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17-svn: Depends: giblib-dev but it is not installable
           Depends: libgtk1.2-dev but it is not installable
E: Broken packages

```
Any ideas?


What distro and version are you installing it on?  (I got something similar installing e17-svn onto Dreamlinux but haven't seen this happen with X/Ubuntu)

---

### Post by spajix on 2009-01-01
> **Tux Aubrey said:**
> What distro and version are you installing it on?  (I got something similar installing e17-svn onto Dreamlinux but haven't seen this happen with X/Ubuntu)

Ubuntu 8.10
Was you able to fix it?
If so, how?

---

### Post by smartboyathome on 2009-01-01
> **spajix said:**
> Ubuntu 8.10
Was you able to fix it?
If so, how?

Get libgtk1.2-dev from [here]("http://packages.ubuntu.com/intrepid/libgtk1.2-dev"), and then install it. Should work for you then.

---

### Post by spajix on 2009-01-01
> **smartboyathome said:**
> Get libgtk1.2-dev from [here]("http://packages.ubuntu.com/intrepid/libgtk1.2-dev"), and then install it. Should work for you then.

Thanks Much
Seems to be working

---

### Post by Genotrius on 2009-01-04
The other day, compilation of e failed due to some sort of unfathomable source conflict. After fiddling with it quite a bit, I eventually uninstalled e17-svn, removed the sources, and reinstalled. Everything appears to have gone fine, but my enlightenment.desktop file seems to be corrupted somehow, as I can't load into E17 through GDM. 
Any idea how I could fix this?

---

### Post by Rui Pais on 2009-01-04
> **nico_h said:**
> Hello and thank you Rui Pais for this deb, it makes the installation really nice and without any worry !

I just want to precise that in the first post, you mistyped the name of configuration file (you wrote /etc/easy_e17.sh instead of /etc/easy_e17.conf)

Thank you nico_h. Glad you like it!
Thanks too for the correction. Fixed :)

> **nico_h said:**
> 
And I would like to know why you changed the src path to /var/cache. Is it to be more compliant with usual debian paths ?

I wanted to add the module "places", which is not in the current easy_e17.sh. I didn't know where e17-svn installed the script itself, so I downloaded easy_e17.sh, added the name "places" to the list of packages (in the variable packages at the beginning of easy_e17.sh) and ran it so :

```
# ./easy_e17.sh --only=places --srcpath=/var/cache
```

And it worked perfectly well. Maybe I should precise that my laptop is running UbuntuStudio 8.04.

By the way, [[COLOR="RoyalBlue"]places[/COLOR]]("http://code.google.com/p/e17mods/wiki/Places") is a very nice module. I hope a next easy_e17.sh -u won't break everything !


Well, when code it's not much unstable, like it happens lately, i tend to avoid try other stuff not much tested... it's usually ask for (more) troubling. But it's interesting to know such project. Very promising!
BTW. To install other stuff in main SVN tree, not on easy_e17.sh script list, you can simply edit easy_e17.sh, add the file to the list and then do:
```
sudo easy_e17.sh --only=<new_package>
``` 
Easy :)


About the move to /var/cache/e17_src, besides what smartboyathome already pointed, a single global place solves too the problem of the case of several users with admin powers that that run updates from different homes... that would result on different SVN copies (huge!!) on disk.


> **smartboyathome said:**
> Tux, you will have to post a howto for getting the *other* OzOs repo in order to get update_e17.sh. This howto only gives you easy_e17.sh. :(
:)
In case anyone want need it, 
just add the following repo:
```
deb http://cafelinux.org/Downloads/oz-os hungrytiger main
``` 
and do a 
```
sudo apt-get update
```
:)

---

### Post by Rui Pais on 2009-01-04
> **Genotrius said:**
> The other day, compilation of e failed due to some sort of unfathomable source conflict. After fiddling with it quite a bit, I eventually uninstalled e17-svn, removed the sources, and reinstalled. Everything appears to have gone fine, but my enlightenment.desktop file seems to be corrupted somehow, as I can't load into E17 through GDM. 
Any idea how I could fix this?

Hi Genotrius.
Are you sure script finish compilation/installation correctly?

Check if enlightenment.desktop file it's ok:
```
ls -l /usr/share/xsessions/enlightenment.desktop
```
it should be a symlink to /opt/e17/share/xsessions/enlightenment.desktop
If not you can do it with:
```
sudo ln -s /opt/e17/share/xsessions/enlightenment.desktop /usr/share/xsessions/enlightenment.desktop

```

Check too if file exist:
```
ls -l /opt/e17/share/xsessions/enlightenment.desktop
```
if not you're installation it's not complete or have problems.
You can try to reinstall:
```
sudo easy_e17.sh -i
```

Good luck. Let me know.

---

### Post by Tux Aubrey on 2009-01-04
Just a report:

I installed e17-svn and the oz-desktop packages (from the cafelinux repos) onto a Jaunty Jackalope alpha over the weekend - After working through a few error messages, it works fine!

Doing "sudo aptitude install oz-desktop" does return an error telling me that oz-desktop won't be installed because oz-desktop-base isn't installed or being installed.  Running "sudo apt-get install oz-desktop-base" fixes it in one go.  

After going through the new e17 set-up screens (language, profile and menu settings) the desktop is loaded with the (e17 default) b_and_w theme - but "ozprofiler all" brings up Rui's OzOS desktop and all the OzOS tools (e17 update and backup etc).

A strange effect I've noticed on other recent installs from svn is that the e17 splash "start-up") screen is just a black screen that takes a few seconds to go away - this gives the impression that e17 is taking a long time load.  It is easy to turn it off or change it to one that works via the menu Settings>Appearance>Start-up.  Without any splash screen, e17 loads incredibly quickly - almost an "instant on" experience.

For those who haven't used or updated e17 for a few months, I'd say that, apart from a few new features (some of them actually useful!), the big changes have been in stability.  It is very rare to get a seg fault on recent builds from svn and even some of the long-standing bugs (eg, the Advanced mode of the Theme Selector)have gone away.

svn code seems surprisingly stable at the moment too (after two or three weeks pre-Christmas of it being bad more often than good) but there are problems using some "third-party" modules (like itask-ng).  Updates are coming thick and fast right now and you get the impression (probably an illusion brought on by New Year optimism) that it might be close to a new release point or something significant.  Imagine that! Feel free to start a rumor!

Jaunty itself is quite slow for me - but that's often the case with pre-release builds of Ubuntu.

Happy New Year!

---

### Post by Rui Pais on 2009-01-04
> **Tux Aubrey said:**
> Just a report:

I installed e17-svn and the oz-desktop packages (from the cafelinux repos) onto a Jaunty Jackalope alpha over the weekend - After working through a few error messages, it works fine!

Doing "sudo aptitude install oz-desktop" does return an error telling me that oz-desktop won't be installed because oz-desktop-base isn't installed or being installed.  Running "sudo apt-get install oz-desktop-base" fixes it in one go.  

Thansk for the report Aubrey 
(i'm still using only Hardy and Lenny... not even Intrepid :()
It's nice to have this tested as new releases evolves :)

I'll give a look at installation steps and see what may be missing.

> **Tux Aubrey said:**
> 
A strange effect I've noticed on other recent installs from svn is that the e17 splash "start-up") screen is just a black screen that takes a few seconds to go away - this gives the impression that e17 is taking a long time load.  It is easy to turn it off or change it to one that works via the menu Settings>Appearance>Start-up.  Without any splash screen, e17 loads incredibly quickly - almost an "instant on" experience.

:shock:
I had experienced that on my test machine (plain Intrepid+e17-svn) and once and then when configuration changed and always thought it was some code issue!!
Glad to know that it was just an "empty" e17 start up splash!

> **Tux Aubrey said:**
> 
svn code seems surprisingly stable at the moment too (after two or three weeks pre-Christmas of it being bad more often than good) but there are problems using some "third-party" modules (like itask-ng).  Updates are coming thick and fast right now and you get the impression (probably an illusion brought on by New Year optimism) that it might be close to a new release point or something significant.  Imagine that! Feel free to start a rumor!

Happy New Year!
I wouldn't be so optimistic, but... how knows.
Strange, the way code goes now. Devs update much more broken code since the SVN move, sometimes completely broking things around, but after fixes (usually fast) e17 really looks very stable lately.
I'm only sorry, about the System functions (i would prefer the old menus' way) and the annoying 1st run wizard, that still have no way to skip...
I now opt by minimalist and then use the Profile chooser to get my saved preferences :)
Simpler and more flexible than the wizard.


Oh, and Happy new year to you too and to all!!
:D

---

### Post by kevdog on 2009-01-05
Is there a way to run the update switch with an arch installation?  There must be since I know those who post on this thread use Arch.

---

### Post by Rui Pais on 2009-01-05
> **kevdog said:**
> Is there a way to run the update switch with an arch installation?  There must be since I know those who post on this thread use Arch.

Hi kevdog.
Sorry, not sure what you mean by 'update switch'...
You mean the update_e17.sh script? 
If that's the case, just download the most recent deb from here:
[http://cafelinux.org/Downloads/oz-os/pool/main/o/oz-e17-tools/](http://cafelinux.org/Downloads/oz-os/pool/main/o/oz-e17-tools/)
open it wit an archive manager, and extract the script.
:)

(let me know if it's another thing you have in mind)

---

### Post by Rui Pais on 2009-01-05
**[COLOR="Navy"]Hi all.[/COLOR]**

I uploaded a new version, based on most recent easy_e17.sh by morlenxus.

This new version essentially, make --fix-conflict flag obsolete (not supported anymore in fact) by add by default a general SVN fix handler.

Update process must take care of that, without problems.

**If you have a personalized conf file at ~/.easy_e17.conf you must edit by hand and delete that flag (if you have put it there).**


The "anti" equivalent flag now its: 
--ask-on-src-conflicts
that make SVN asks you on conflicts (DO NOT SET IT! only needed by devs and masochist people :))
So the default, fix immediately, will make things easier to users (remember those annoying po files requiring your intervention?... well not anymore!)

---

### Post by s3kt0r on 2009-01-05
Well this topic has a lot of pages, the most of it i didn't read, just the essentials eheh. 
More of a gnome user, this is the first i decided to go through the whole process of installing and configuring enlightenment, and i just want to  say big thanks to Rui Pais, great howto, was really helpfull. 
Can't seem to enjoy enough of this. :P Don't think it will be long before i switch completely of wm's lol.

edit: Perhaps someone can enlighten me (eheh)... can themes install modules/gadgets/widgets by themselves? do i have anything to say in the matter? Another quick one: is module Entrance like a substitute for gdm?

regards,

---

### Post by smartboyathome on 2009-01-06
> **s3kt0r said:**
> edit: Perhaps someone can enlighten me (eheh)... can themes install modules/gadgets/widgets by themselves?

No, they can't. They do just one thing: theme. They will change the look of modules/gadgets/widgets, though.

> **s3kt0r said:**
> do i have anything to say in the matter?

Completely. E17 doesn't try to do it for you unless there is a bug (ie, some modules will get deleted if they are broken).

> **s3kt0r said:**
> Another quick one: is module Entrance like a substitute for gdm?

Entrance isn't a module, it is a login manager based on the EFL libraries. It is a substitute for GDM, though.

---

### Post by originalsynthesis on 2009-01-06
Hiya! 

Im trying the installation you gave and ran into an issue: in first phase of download, it gets to the 'edje_player source and tells me it doesn't exist and continues to try and download it every 2 min or so. can i skip this file? i can't seem to enter any commands while its doing this.  (i may have bit off more than i can chew on with e17, i am a new linux user)

---

### Post by Rui Pais on 2009-01-06
> **originalsynthesis said:**
> Hiya! 

Im trying the installation you gave and ran into an issue: in first phase of download, it gets to the 'edje_player source and tells me it doesn't exist and continues to try and download it every 2 min or so. can i skip this file? i can't seem to enter any commands while its doing this.  (i may have bit off more than i can chew on with e17, i am a new linux user)


Hi originalsynthesis.
My bad! 
I forget to remove that one (it's on original script, but that ones it's from proto section, less stable stuff, that my patched script avoids...)

That error only happens on new installations (no code ever downloaded), so i didn't note it on my tests :(

I uploaded a new version, right now.
Do:
```
sudo apt-get update && sudo apt-get upgrade
```

That should make it run properly.
Thanks

---

### Post by originalsynthesis on 2009-01-06
whoops! i jumped the gun a bit and just closed the install, and used sudo dpkg config and finished it that way. It installed ok, minus the file mentioned and everything listed after it. can i use the command you gave to finish it, or should i wipe the whole shebang and start a fresh install?

thanks for the quick response!

---

### Post by Rui Pais on 2009-01-06
> **originalsynthesis said:**
> whoops! i jumped the gun a bit and just closed the install, and used sudo dpkg config and finished it that way. It installed ok, minus the file mentioned and everything listed after it. 
No Problem. Glad to know you manage to finish it :)

> **originalsynthesis said:**
> 
can i use the command you gave to finish it, or should i wipe the whole shebang and start a fresh install?


Yes. You can and you should, to avoid any possible issues with that app in the future. The reference to it was, plainly, my mistake.


> **originalsynthesis said:**
> 
thanks for the quick response!
Quite rare on me these days... :lol: 

No prob. Glad i could help.
:)

---

### Post by kevdog on 2009-01-06
Possibly you can help me since Ive run into this problem before

On running 

sudo easy_e17.sh -u 
tonight I get the following (and I've had this with other packages):

svn: Failed to add directory 'edje_viewer/debian': an unversioned directory of the same name already exists

In the past I just went and deleted this directory (this occurs with other packages), however it would be much nicer if a force option was in place to override.  I dont change the sources -- trust me on this one!

Is there a good workaround?

---

### Post by s3kt0r on 2009-01-06
> **smartboyathome said:**
> No, they can't. They do just one thing: theme. They will change the look of modules/gadgets/widgets, though.



Completely. E17 doesn't try to do it for you unless there is a bug (ie, some modules will get deleted if they are broken).



Entrance isn't a module, it is a login manager based on the EFL libraries. It is a substitute for GDM, though.

Oh ok, I just got confused by something at Exchange, on the themes thing.
As for the Entrance question..I didn't realize it was a login manager, my bad. Could I use it to completely replace GDM but still being able to log into Gnome if I wanted to? (Makes sense, right?)

thanks for bits of your time, smartboyathome

---

### Post by originalsynthesis on 2009-01-07
well i have to say im really digging what e17 is doing. i definately is quicker and more sleek than gnome is.  but ive run into a few major problems.  

If i remove icons from, or change the size of the shelf, enlight. completely freezes up. 

 I also cannot get E to see the rest of my hard drive.(i.e. the other 50 gigs aside from the linux partition!) i thought maybe that could be due to E running alongside gnome?.

 any change to the desktop wallpaper will elicit an error that reads:There was an error trying to set the cpu frequency governor via the module's setfreq utility.  

oh, and a couple times i got the "this is very bad" crash recovery window by changing window settings.   
 
There were a couple other things, but i think the types of errors im getting here have priority. Ive been looking at e.org's forums and haven't found much of anything similar to this, anyone seen this stuff before?

---

### Post by s3kt0r on 2009-01-07
> **originalsynthesis said:**
> 
 any change to the desktop wallpaper will elicit an error that reads:There was an error trying to set the cpu frequency governor via the module's setfreq utility.  

oh, and a couple times i got the "this is very bad" crash recovery window by changing window settings.   
 


This happened to me too, about the cpu frequency module, i just removed it from the modules dialog configuration. But that didn't happen when changing wallpapers, but when I would log in into Enlightenment.

When I tried to change some windows properties stuff, windows stacking I think, it showed the same "very bad crash".

Don't know why it does that...but it also happened to me. Anybody knows more and care to share with us?

---

### Post by Tux Aubrey on 2009-01-07
> **originalsynthesis said:**
> 
If i remove icons from, or change the size of the shelf, enlight. completely freezes up.  

I'm not sure about this one at all - I can't seem to crash a shelf no matter what I do to it.  Does it happen to ANY shelf? (or just to a particular one)

A couple of suggestions 

1. run an update (it may just have been a passing issue with a particular revision)

2. delete and remake the offending shelf (try t with different gadgets as you go to work out if it is just a particular gadget making the whole thing shaky)

3. use the components of the shelf directly on the desktop (ie load the Gadgets module and treat them as individual components (shelves are just soooo 2008 anyway)

> **originalsynthesis said:**
> 
I also cannot get E to see the rest of my hard drive.(i.e. the other 50 gigs aside from the linux partition!) i thought maybe that could be due to E running alongside gnome?.

That's bad, but I doubt it is related to having Gnome alongside (I have several WMs loaded including Gnome and they are often running in concurrent sessions)

Can you mount the partition manually?  fstab normally works fine in all WMs.


> **originalsynthesis said:**
> any change to the desktop wallpaper will elicit an error that reads:There was an error trying to set the cpu frequency governor via the module's setfreq utility.  

As s3kt0r said - unload the cpufreq module.

There have been a lot of updates to e17 over the past two weeks and some of the modules have fallen behind.  (I had the same problem with taskbar for a couple of days).  Don't use any that are broken until testing them after updating e17.

> **originalsynthesis said:**
> oh, and a couple times i got the "this is very bad" crash recovery window by changing window settings.   


I love that message!  I suspect it has nothing to do with Window Settings but is a by-product of a naughty module.  Maybe unloading cpufreq will fix this too.

Hang in there, originalsynthesis.  You are three centimeters from the Bleeding Edge but close to nirvana.  I can assure you that a) the fix will be simple but not obvious, and that b) once you fix it you will be amazed by the stability and speed of e17.

---

### Post by BGFG on 2009-01-09
Very easy install, very easy uninstall. It's a great environment, but i couldn't quite get my bearings with tweaking :) and only after i uninstalled i saw your post on ugly default gnome look and how to change it....

E17 will be my first choice once i get around to building a machine and installing arch or gentoo. By that time, i can only imagine...

Thanks again for the Howto. Look forward to more updates....

---

### Post by lukjad on 2009-01-10
Bookmarking. Thanks to the tutorial.

---

### Post by doorman on 2009-01-11
Hy guys!

After updating I lost the *System* menu entry, so I enabled the System module in order to get that menu back, but it doesn't show much: there's just a small window with a cancel button on it and that's it. (I would upload the screenshot but for some reason I can't attach a file to this post)

I have the same problem on both of my computers. On my home computer I don't mind it happening, but I use the other one at the office, which is a potential security risk, since I can't lock the screen any more. Is there another way to lock the screen other than through the System module?

---

### Post by smartboyathome on 2009-01-11
From what I understand, you need to rename your .e folder in your user directory (it is hidden) to .e-bkup, and then that will reset the enlightenment system menu. [This topic on OzOs's forums]("http://cafelinux.org/forum/index.php/topic,2476.0.html") should help you, it details the problem thoroughly.

---

### Post by doorman on 2009-01-11
Thnx smartboyathome. I managed to get the system menu back, but at a very high cost - all my settings are lost, and I haven't got the time right now to reconfigure it all over again.

It actually seems to be the problem with the system menu being called from the *default* profile... Kinda silly - the menu mentioned can work under any other profile but this one... I suppose I'll wait to see if the dev team plans to correct this bug...

---

### Post by Tux Aubrey on 2009-01-11
> **doorman said:**
> .. I suppose I'll wait to see if the dev team plans to correct this bug...

That's unlikely, unfortunately.  The e-devs changed the name of the "default" profile to "standard" and left "default" orphaned from receiving new code. I think Rui has now updated the oz-desktop script to deal with it (which should at least help new users avoid this problem).

---

### Post by digitalbrain on 2009-01-11
Hi. I have a problem too. I was using the classic version of E17. After an update from e17.dunnewind.net repos (by update manager), the version upgraded to svn. And after that I can't delete, copy, cut or paste files any more!! I can do it by terminal commands but cannot do by mouse or keyboard. I can't even rename a file. A weird problem.  I don't want to uninstall E17 completely and delete all files related to E17 and then install using the script. What might have caused that problem? Who can give me an advice? Thanks.

---

### Post by Tux Aubrey on 2009-01-11
> 
Hi. I have a problem too. I was using the classic version of E17. After an update from e17.dunnewind.net repos (by update manager), the version upgraded to svn. And after that I can't delete, copy, cut or paste files any more!! I can do it by terminal commands but cannot do by mouse or keyboard. I can't even rename a file. A weird problem. I don't want to uninstall E17 completely and delete all files related to E17 and then install using the script. What might have caused that problem? Who can give me an advice? Thanks.


Hi digitalbrain

I didn't know that dunnewind had upgraded the .deb (or why an svn upgrade would be relevant to a binary).  But that's great news and confirms my impression that the debian packagers have been working on e17! 

The version you get from Rui's (e17-svn/update_e17) or morlenxus' (easy_e17) scripts is going to quite different from that one anyway - not just that it is built from current code, but in terms of where e17 is installed (/opt for the script version, /usr for .deb).  DON'T MIX THE TWO! Their config files will fight to the death - either stay with the .deb or uninstall and clean it completely and install via a script.

I suggest you find out whether other dunnewind .deb users are having the same problem (do they have a forum?). Don't go to the e17 mailing list - it is a "little intolerant" of struggling users. 

Nothing like your problem has ever happened to me using the svn version via script - just a lot of other weird problems! - and I tend to update daily so I probably would have seen it if it was in the e17 code base.

Did you install the dunnewind version on Ubuntu?  I tried that a couple of months ago and had problems with incompatible dependencies and the mpdule module.  I got there eventually but it was actually more difficult than doing it Rui's way.

Sorry if that's not much help - maybe someone else who is using the .deb version can help (maybe by posting in "Desktop Environments"?)

---

### Post by digitalbrain on 2009-01-12
@Tux Aubrey
Thank you very much for your long answer. As I can see, E17 has still some problems (doesn't matter which version it is). .I really love it. But for a while I think I'll stop using it. I don't want to post anywhere else. (Anyway, I will be waiting for different ideas.)
Thanks again...

---

### Post by smartboyathome on 2009-01-12
I think that Rui needs to post that E17 is pre-alpha software and still in heavy development, meaning it can break at any time (I didn't see that in the first post).

---

### Post by phishbone on 2009-01-12
Source conflict: solve automatically
Script action:   MISSING

Unknown argument '--fix-src-conflicts'

Whats up with that?

Never had any problems with the script before.

I have no source in /var/cache either. Was about a week since i updated. Any package i should remove?

---

### Post by phishbone on 2009-01-12
> **Rui Pais said:**
> Hi, 
that's a know problem. 
The b_and_w it's configured (bad option by it's dev!) to install on user config folder, not on system. 
But themes on user folder must belong to user, and that don't happen because install it's done with root power.
You can either move ~/.e/e/themes/b_and_w.edj to /opt/e17/share/enlightenment/data/themes/
or run:
```
sudo chown $USER:$USER -R .e/e/themes/*
```
to make it teh correct ownership.
That last will be overwritten next time b_and_w updates.
You can install oz-e17-tools (an OzOS tool) with apt-get/synaptic and update by run sudo update_e17.sh instead of easy_e17.sh -u taht will check ownerships automatically on each update.

hth

Figured it out before i was checking back, and i think every e17 user should try this theme, its so nice! :popcorn:

---

### Post by smartboyathome on 2009-01-13
> **phishbone said:**
> Source conflict: solve automatically
Script action:   MISSING

Unknown argument '--fix-src-conflicts'

Whats up with that?

Never had any problems with the script before.

I have no source in /var/cache either. Was about a week since i updated. Any package i should remove?

That option was recently removed, as the script now does it automatically. Remove it from your /etc/easy_e17.conf file. :)

---

### Post by phishbone on 2009-01-14
> **smartboyathome said:**
> That option was recently removed, as the script now does it automatically. Remove it from your /etc/easy_e17.conf file. :)

Thanks man. :P

---

### Post by Cyberponcho on 2009-01-14
> **smartboyathome said:**
> I think that Rui needs to post that E17 is pre-alpha software and still in heavy development, meaning it can break at any time (I didn't see that in the first post).

I did a fresh install of E-17 using Rui's directions and since then my install works wonderfuly, ther are a few things that need a bit of 'tuning' but that's more because of my lack of knowledge @ some 'internals' than problems with the software itself :confused:
I don't know, maybe i was just lucky??

---

### Post by digitalbrain on 2009-01-17
OK. Here is a problem again: I installed E17 by Rui's method. When it came to "Installing packages" stage, I got that error:
```

------------------------------ Installing packages
- eina ....................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.3.3-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
configure.ac:14: error: possibly undefined macro: AC_LIBTOOL_WIN32_DLL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:17: error: possibly undefined macro: AC_PROG_LIBTOOL  
```
I removed the old version completely and the directories '.e' and '/var/cache/e17_src' before installing. I also checked if cvs was installed or not. It was already installed. I followed the steps one by one. So, what is the problem here? What does that error tell me? I tried skipping "eina" package but I got the same error again with the next package. I can't get rid of that error. I need help. I can't use E17.

---

### Post by smartboyathome on 2009-01-17
That is because of SVN breakage. You will have to wait and see if it gets fixed soon. :(

---

### Post by Rui Pais on 2009-01-23
> **digitalbrain said:**
> OK. Here is a problem again: I installed E17 by Rui's method. When it came to "Installing packages" stage, I got that error:
```

------------------------------ Installing packages
- eina ....................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.3.3-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
configure.ac:14: error: possibly undefined macro: AC_LIBTOOL_WIN32_DLL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:17: error: possibly undefined macro: AC_PROG_LIBTOOL  
```
I removed the old version completely and the directories '.e' and '/var/cache/e17_src' before installing. I also checked if cvs was installed or not. It was already installed. I followed the steps one by one. So, what is the problem here? What does that error tell me? I tried skipping "eina" package but I got the same error again with the next package. I can't get rid of that error. I need help. I can't use E17.

Hi digital brain check this thread here to see if it's your problem:
[http://cafelinux.org/forum/index.php/topic,2561.new.htm](http://cafelinux.org/forum/index.php/topic,2561.new.htm)

Let us know.

---

### Post by cov on 2009-01-25
Thanks very much for the howto.

I am currently installing e-17 as per your instructions.

I am a little dismayed however to find that, although the initial download is 3 or 4 meg, the subsequent SVN download is taking some time (I would estimate 20 to 30 Meg?).

<rant mode>
I am in South Africa where, in a bid to maximize their profits and squeeze the consumer the National Telcomm Monopoly charge an exorbitant fee for monthly bandwidth usage in excess of 1 gig per month and it burns my butt to go over my monthly allocation a week before the end of the month.
</rant>

:(

---

### Post by smartboyathome on 2009-01-25
> **cov said:**
> Thanks very much for the howto.

I am currently installing e-17 as per your instructions.

I am a little dismayed however to find that, although the initial download is 3 or 4 meg, the subsequent SVN download is taking some time (I would estimate 20 to 30 Meg?).

<rant mode>
I am in South Africa where, in a bid to maximize their profits and squeeze the consumer the National Telcomm Monopoly charge an exorbitant fee for monthly bandwidth usage in excess of 1 gig per month and it burns my butt to go over my monthly allocation a week before the end of the month.
</rant>

:(

The reason that it takes so long is that SVN is checking out a copy of each individual file, rather than one archive with everything in it.

---

### Post by MALDATA on 2009-01-25
Hi everyone... I just installed e17 to check it out... I used the 

[http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main

repo to do "apt-get install e17-svn" and everything seems to work just fine right after. I can start e17 from startx (it's a fresh install without xdm or gdm). I'd like to install entrance, but it doesn't seem like it's in the repo... in fact, if I do "apt-cache search e17" all I get back is e17-svn, e17-themes, and e17-themes-extra.

All of my googling seems to suggest that entrance should get installed with the rest of it. The threads are all so long that I couldn't possibly dig through them all. Sorry if this has already been asked.

Thanks.

---

### Post by smartboyathome on 2009-01-25
> **MALDATA said:**
> Hi everyone... I just installed e17 to check it out... I used the 

[http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main

repo to do "apt-get install e17-svn" and everything seems to work just fine right after. I can start e17 from startx (it's a fresh install without xdm or gdm). I'd like to install entrance, but it doesn't seem like it's in the repo... in fact, if I do "apt-cache search e17" all I get back is e17-svn, e17-themes, and e17-themes-extra.

All of my googling seems to suggest that entrance should get installed with the rest of it. The threads are all so long that I couldn't possibly dig through them all. Sorry if this has already been asked.

Thanks.

You have to edit /etc/easy_e17.conf and remove entrance from the skip list. Then you can install it. Be warned, though, that I never could get it to work with this script. :(

---

### Post by JordyD on 2009-01-25
I've installed e17-svn and cvs, but I still can't run it at login. It says something about there being no exec line for it. I've already tried reinstalling it, and I've run easy_e17.sh as root, but it keeps skipping things during install.

Thanks,
Jordy

---

### Post by smartboyathome on 2009-01-25
> **JordyD said:**
> I've installed e17-svn and cvs, but I still can't run it at login. It says something about there being no exec line for it. I've already tried reinstalling it, and I've run easy_e17.sh as root, but it keeps skipping things during install.

Thanks,
Jordy

Try running this and post what it outputs:
```
sudo easy_e17.sh -i
```
It will try to install E17 all over again.

---

### Post by MALDATA on 2009-01-25
> You have to edit /etc/easy_e17.conf and remove entrance from the skip list. Then you can install it. Be warned, though, that I never could get it to work with this script.

Ah. Didn't even know that file was in there. Thanks for that... but your wording has me wondering, you can't get it to work with THIS script, but can you get it to work some other way? Also, to what script are you referring? easy_e17.sh, I assume?

If I can't get entrance to work it's no big deal, my only real concerns are having a decent battery monitor and a NetworkManager-type app. This is going on a laptop that I carry around with me at work, and I often need to connect to other people's wireless networks. Any suggestions for a nice light-weight network app that works well in e? From what I can tell, exalt is still a little shady. I've been having trouble figuring out what is and isn't working in enlightenment.

Thanks a lot for the help, I appreciate it!

---

### Post by JordyD on 2009-01-25
This is the output of the script, in full:
```
---------------------------- Easy_e17.sh 1.2.3.3-OzOS --------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus exalt e entrance edje_editor elicit elitaire enna enthrall emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu deskshow diskio drawer efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt exhibit rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w 

  Source conflict: solve automatically
  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks
- source checkout/update
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok
- 'automake' available ....... ok
- 'gcc' available ............ ok
- 'make' available ........... ok
- 'svn' available ............ ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)
- setting compile options .... ok
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
- updating sources (please wait, this won't output much) ...
Checking e source ... At revision 38787.
Checking ecore source ... At revision 38787.
Checking e_dbus source ... At revision 38787.
Checking edje source ... At revision 38787.
Checking edje_editor source ... At revision 38787.
Checking eet source ... At revision 38787.
Checking efreet source ... At revision 38787.
Checking eina source ... At revision 38787.
Checking elicit source ... At revision 38787.
Checking elitaire source ... At revision 38787.
Checking embryo source ... At revision 38787.
Checking E-MODULES-EXTRA source ... At revision 38787.
Checking emotion source ... At revision 38787.
Checking emphasis source ... At revision 38787.
Checking empower source ... At revision 38787.
Checking emprint source ... At revision 38787.
Checking enhance source ... At revision 38787.
Checking entrance source ... At revision 38787.
Checking ephoto source ... At revision 38787.
Checking epsilon source ... At revision 38787.
Checking esmart source ... At revision 38787.
Checking estickies source ... At revision 38787.
Checking etk source ... At revision 38787.
Checking etk_extra source ... At revision 38787.
Checking evas source ... At revision 38787.
Checking ewl source ... At revision 38787.
Checking exhibit source ... At revision 38787.
Checking exml source ... At revision 38787.
Checking expedite source ... At revision 38787.
Checking exquisite source ... At revision 38787.
Checking MISC source ... At revision 38787.
Checking rage source ... At revision 38787.
Checking THEMES source ... At revision 38787.

--------------------------------------------------------------------------------

-> PREPARING FOR PHASE 2...
---------------------------- Easy_e17.sh 1.2.3.3-OzOS --------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus exalt e entrance edje_editor elicit elitaire enna enthrall emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu deskshow diskio drawer efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt exhibit rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w 

  Source conflict: solve automatically
  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation
- apps-compilation and installation
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- eina ....................... ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ ok          
- etk_extra .................. ok          
- ewl ........................ ok          
- exml ....................... SKIPPED
- enhance .................... SKIPPED
- e_dbus ..................... ok          
- exalt ...................... SKIPPED
- e .......................... ok          
- entrance ................... SKIPPED
- edje_editor ................ SKIPPED
- elicit ..................... SKIPPED
- elitaire ................... SKIPPED
- enna ....................... ok          
- enthrall ................... SKIPPED
- emphasis ................... SKIPPED
- empower .................... SKIPPED
- emprint .................... ok          
- ephoto ..................... SKIPPED
- estickies .................. SKIPPED
- exhibit .................... SKIPPED
- expedite ................... SKIPPED
- exquisite .................. SKIPPED
- extrackt ................... SKIPPED
- eyesight ................... NOT FOUND
- e_phys ..................... SKIPPED
- rage ....................... SKIPPED
- alarm ...................... ok          
- bling ...................... ok          
- calendar ................... ok          
- cpu ........................ ok          
- deskshow ................... ok          
- diskio ..................... ok          
- drawer ..................... ok          
- efm_nav .................... SKIPPED
- efm_path ................... SKIPPED
- emu ........................ SKIPPED
- execwatch .................. ok          
- flame ...................... SKIPPED
- forecasts .................. ok          
- iiirk ...................... ok          
- language ................... SKIPPED
- mail ....................... ok          
- mem ........................ ok          
- moon ....................... SKIPPED
- mpdule ..................... SKIPPED
- net ........................ ok          
- news ....................... SKIPPED
- notification ............... SKIPPED
- penguins ................... SKIPPED
- photo ...................... SKIPPED
- places ..................... ok          
- rain ....................... SKIPPED
- screenshot ................. ok          
- slideshow .................. ok          
- snow ....................... SKIPPED
- taskbar .................... ok          
- tclock ..................... ok          
- tiling ..................... ok          
- uptime ..................... ok          
- weather .................... ok          
- winselector ................ ok          
- wlan ....................... ok          
--------------------------------------------------------------------------------

----------------------------- Finishing installation ---------------------------
- registering libraries ...... ok
- post install script ........ skipped
--------------------------------------------------------------------------------

-> PREPARING FOR PHASE 3...
---------------------------- Easy_e17.sh 1.2.3.3-OzOS --------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Logs path:       /tmp/easy_e17/install_logs

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus exalt e entrance edje_editor elicit elitaire enna enthrall emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu deskshow diskio drawer efm_nav efm_path emu execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places rain screenshot slideshow snow taskbar tclock tiling uptime weather winselector wlan
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt exhibit rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w 

  Source conflict: solve automatically
  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 3/3 -------------------------------
- cleaning
- install notes
--------------------------------------------------------------------------------


-------------------------------- Cleaning temp dir -----------------------------
- deleting temp dir .......... ok
--------------------------------------------------------------------------------

INSTALL NOTES:
-----------------------------------------------------------------------------
The most incredible and really unbelievable dream has become true:
You compiled e17 successfully!

Starting e17:
If you're using a login manager (GDM/KDM), select the session type 'Enlightenment' in them.

Rasterman didn't write this script so don't ask him for help with it.

We hope you will enjoy your trip into e17... Have fun!
--------------------------------------------------------------------------------

```

---

### Post by MALDATA on 2009-01-25
> You have to edit /etc/easy_e17.conf and remove entrance from the skip list. Then you can install it. Be warned, though, that I never could get it to work with this script. 

Well, for what it's worth, entrance seems to work OK for me.

I took it off the skip list in /etc/easy_e17.conf and tried to compile it, but it choked during the configure step. It needed esmart also, so I took that off the list, and both compiled and installed just fine (easy_e17.sh --only=esmart, then easy_e17.sh --only=entrance).

Then it got a little bizarre. If I did startx /opt/e17/bin/entrance, it would come up, I could log in just fine, but then 30 seconds after e17 started (I timed it... it was startlingly regular) it would crash and dump me back to the CLI. What was weird was that if I started X and just went straight to e17, it didn't happen. Only when logging in through entrance.

So then rather than using entrance, I set up a symlink in /etc/init.d/ pointing to /opt/e17/**s**bin/entrance**d**
and now it doesn't crash. Very strange.

Anyway, it's working now. The only thing I'm missing is exalt or some other wireless manager. Seems like people are saying good things about wicd.

Thanks for the help!

---

### Post by cov on 2009-01-26
> **smartboyathome said:**
> The reason that it takes so long is that SVN is checking out a copy of each individual file, rather than one archive with everything in it.

Ah.

Okay.

I reached my cap and the ISP cut me off just after I'd posted, so I was a bit annoyed. But you say that had nothing to do with the SVN?

Still, when they cut me off, the installation had not completed.

I am trying to resume the installation with:
sudo apt-get install e17-svn

but I get the following error message:```

 E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

So I tried:
sudo dpkg --configure -a e17-svn

which resulted in the following:
```
dpkg: --configure --pending does not take any non-option arguments

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !

```

Can anyone suggest what I should do? Bearing in mind that I have just shelled out the equivelant of 20-30 Dollars US for an additional 1 gig which will expire on the last day of the month if it's not used up.

Monopolies! Don't you just love 'em?

---

### Post by cov on 2009-01-26
Sorry, belay that!

The correct command was simply 'sudo dpkg --configure -a'
rather than the 'dpkg --configure -a e17-svn'.

Thank you.

---

### Post by cov on 2009-01-26
I get this error:
```
/sbin/ldconfig.real: /opt/e17/lib/libecore.so is not an ELF file - it has the wrong magic bytes at the start.

```

E-17 doesn't start.

I'm trying the command:
sudo easy_e17.sh -i

I'll let you know how I got on...

---

### Post by Tux Aubrey on 2009-01-26
> **MALDATA said:**
> 
If I can't get entrance to work it's no big deal, my only real concerns are having a decent battery monitor and a NetworkManager-type app. This is going on a laptop that I carry around with me at work, and I often need to connect to other people's wireless networks. Any suggestions for a nice light-weight network app that works well in e? From what I can tell, exalt is still a little shady. I've been having trouble figuring out what is and isn't working in enlightenment.


[Wicd]("http://www.wicd.net/") works well as as network manager with e17. I use it to connect to lots of different wireless networks.:redface:

You can get it by adding the following to your /etc/apt/sources.list
> 
deb [http://apt.wicd.net/](http://apt.wicd.net/) intrepid extras

(change "intrepid" to whatever version of ubuntu you are using.)

and then do:

```
sudo apt-get update

sudo apt-get install wicd
```

Get it running from the cli and then add it to menu or launcher (right click on the title bar - create icon - right click again and "Add Application...")

You'll find the battery module (and many others) under "modules".  Load it and then add it to a shelf or create a desktop gadget.

---

### Post by cov on 2009-01-26
> **cov said:**
> I get this error:
```
/sbin/ldconfig.real: /opt/e17/lib/libecore.so is not an ELF file - it has the wrong magic bytes at the start.

```

E-17 doesn't start.

I'm trying the command:
sudo easy_e17.sh -i

I'll let you know how I got on...

Errors as follows:
> make[5]: Entering directory `/var/cache/e17_src/ecore/src/lib/ecore_x/xlib'
.deps/ecore_x_atoms.Plo:2: *** missing separator.  Stop.
make[5]: Leaving directory `/var/cache/e17_src/ecore/src/lib/ecore_x/xlib'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/var/cache/e17_src/ecore/src/lib/ecore_x'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/var/cache/e17_src/ecore/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/ecore'
make: *** [all] Error 2


---

### Post by smartboyathome on 2009-01-27
> **cov said:**
> Errors as follows:

That may have been SVN breakage (happens *at least* once in a while, more often usually).

---

### Post by cov on 2009-01-27
> **smartboyathome said:**
> That may have been SVN breakage (happens *at least* once in a while, more often usually).

I removed all the /var/cashe/e17_src/ files and started again.

HUGE DOWNLOAD.

I reckon I'll have to shell out for another Gig pretty soon. :(

To compound my problems my machine suddenly cut out halfway through the install, which I think is where my error is. My fan is giving trouble and with the heatwave we've been having, my box is obviously overheating.

I don't want to start the download from scratch again, but there are obviously corrupted files in my /var/cache/e17_src (partially compiled packages, I would guess).

What a bummer.

---

### Post by smartboyathome on 2009-01-27
> **cov said:**
> I removed all the /var/cashe/e17_src/ files and started again.

HUGE DOWNLOAD.

I reckon I'll have to shell out for another Gig pretty soon. :(

To compound my problems my machine suddenly cut out halfway through the install, which I think is where my error is. My fan is giving trouble and with the heatwave we've been having, my box is obviously overheating.

I don't want to start the download from scratch again, but there are obviously corrupted files in my /var/cache/e17_src (partially compiled packages, I would guess).

What a bummer.

That reminds me, Rui, would you be able to modify the script so that it builds in a different directory than the sources to keep things clean? For example, in /var/cache/e17_build. Then erase all the files in the build directory each time a program is updated. That would keep stuff like above from being a problem.

---

### Post by JordyD on 2009-01-27
> **JordyD said:**
> This is the output of the script, in full:
*snip

No ideas?

---

### Post by smartboyathome on 2009-01-27
> **JordyD said:**
> No ideas?

Sorry, I missed it. First, enter this in your .xinitrc (using gedit .xinitrc, for example):
```
exec /opt/e17/bin/enlightenment_start
```
Try running these commands in a virtual terminal after logging in (ctrl-alt-f1):
```
sudo killall gdm
startx
```
That should start E17 directly (no login manager). If it suceeds, we know it is the .desktop file which is to blame. If it fails, we know E17 is to blame.

---

### Post by cov on 2009-01-28
Good Grief I'm thick!

I didn't have to remove the entire installation.

I just removed the offending directory :oops:

Anyway, I have a new error
```
Making all in ecore_evas
make[4]: Entering directory `/var/cache/e17_src/etk/src/engines/ecore_evas'
make[4]: *** virtual memory exhausted.  Stop.
make[4]: Leaving directory `/var/cache/e17_src/etk/src/engines/ecore_evas'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/var/cache/e17_src/etk/src/engines'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/etk/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/etk'
make: *** [all] Error 2

```

---

### Post by smartboyathome on 2009-01-28
That error (virtual memory exhausted) usually only shows up when you have corrupt ram. I would recommend running memtest on your ram to make sure it isn't corrupt.

---

### Post by cov on 2009-01-28
Double bummer.

I suppose that the box switching itself off isn't a good sign. :(

The fan has stopped working, I reckon it's been overheating.

The memtest doesn't get to finish before it reboots itself.

---

### Post by barkley128 on 2009-01-28
Got everything working.
Guess that had something to do with one of the script updates.
It downloaded the missing necessary source files and installed just fine! :)
I'm writing, logged in my enlightenment session.
Thanks for all the help. And thanks Rui for the script.

---

### Post by mpsii on 2009-01-30
I am just now following this HOWTO and am getting the following (been getting it all day):

```
----------------------------- Source checkout/update ---------------------------
- checkout sources ...
   downloading eina source ...
svn: OPTIONS of 'http://svn.enlightenment.org/svn/e/eina': could not connect to server (http://svn.enlightenment.org)
svn: OPTIONS of 'http://svn.enlightenment.org/svn/e/eina': could not connect to server (http://svn.enlightenment.org)
FAILED! Next attempt 3 in 7 seconds^Cdpkg: error processing e17-svn (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 e17-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)
mschemer@ubuntu-vm:~$ 

```

---

### Post by smartboyathome on 2009-01-31
> **mpsii said:**
> I am just now following this HOWTO and am getting the following (been getting it all day):

```
----------------------------- Source checkout/update ---------------------------
- checkout sources ...
   downloading eina source ...
svn: OPTIONS of 'http://svn.enlightenment.org/svn/e/eina': could not connect to server (http://svn.enlightenment.org)
svn: OPTIONS of 'http://svn.enlightenment.org/svn/e/eina': could not connect to server (http://svn.enlightenment.org)
FAILED! Next attempt 3 in 7 seconds^Cdpkg: error processing e17-svn (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 e17-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)
mschemer@ubuntu-vm:~$ 

```

Enlightenment's SVN server is down (can't use the SVN browser either).

EDIT: It's back now. :)

---

### Post by JordyD on 2009-02-01
> **smartboyathome said:**
> Sorry, I missed it. First, enter this in your .xinitrc (using gedit .xinitrc, for example):
```
exec /opt/e17/bin/enlightenment_start
```
Try running these commands in a virtual terminal after logging in (ctrl-alt-f1):
```
sudo killall gdm
startx
```
That should start E17 directly (no login manager). If it suceeds, we know it is the .desktop file which is to blame. If it fails, we know E17 is to blame.

It worked after I added that line to .xinitrc (which didn't even exist before now). This WM looks beautiful, but it seems that all of my GNOME applications have an old Windows 98 look (screenshot attached), as opposed to the Enlightenment look I see everywhere else. Is there a way to fix this?

Thanks,
Jordy

---

### Post by smartboyathome on 2009-02-01
> **JordyD said:**
> It worked after I added that line to .xinitrc (which didn't even exist before now). This WM looks beautiful, but it seems that all of my GNOME applications have an old Windows 98 look (screenshot attached), as opposed to the Enlightenment look I see everywhere else. Is there a way to fix this?

Thanks,
Jordy

Install gtk-chtheme or lxappearance, and use one of those to change the GTK theme. You need to install one to go with the Enlightenment theme, as Enlightenment uses an completely different toolset from GTK. To install a GTK theme, extract it into your .themes folder, then it will be able to be chosen by the aforementioned applictaions.

---

### Post by JordyD on 2009-02-01
> **smartboyathome said:**
> Install gtk-chtheme or lxappearance, and use one of those to change the GTK theme. You need to install one to go with the Enlightenment theme, as Enlightenment uses an completely different toolset from GTK. To install a GTK theme, extract it into your .themes folder, then it will be able to be chosen by the aforementioned applictaions.

Thanks, I found a nice one that went with e17's default theme.

---

### Post by vegetarianshrimp on 2009-02-01
> Before the installation, My disk had 2.2 GB space left. But after install & remove, now it only has 1.8 GB space left. Although I deleted /var/cache/e17_src.REPLY:
> **Rui Pais said:**
> Yes, that's normal. Source code it's big (looks even bigger on SVN), around 0.5G with easy_17.sh version of e17-svn.
Original morlenxus version gives you the full trunk source with more ~250M.

If you want you can remove it. And update only after some large periods of time (1, 2 months)... 
Or maybe save/compress code tree, on /var/cache/e17_src, to a pen or external disc...

Ya I had the same problem (didn't completely uninstall) You say you can remove the source code..how?

---

### Post by smartboyathome on 2009-02-01
Check that both /opt/e17 and /var/cache/e17_src are deleted, and if they aren't, delete them.

---

### Post by vegetarianshrimp on 2009-02-02
> **smartboyathome said:**
> Check that both /opt/e17 and /var/cache/e17_src are deleted, and if they aren't, delete them.

the var one I deleted, and the opt one does not exist (actually, there is nothing in /opt at all...)

When I started out, there was 9.8 GB left, now, after install, remove, AND deleting the /var e17 thing, there is only 9.2 GB left

---

### Post by Tux Aubrey on 2009-02-02
> **vegetarianshrimp said:**
> 

When I started out, there was 9.8 GB left, now, after install, remove, AND deleting the /var e17 thing, there is only 9.2 GB left

Do you still have an /.e folder in your home directory?  If you aren't running e at all you can delete it.

---

### Post by vegetarianshrimp on 2009-02-02
> **Tux Aubrey said:**
> Do you still have an /.e folder in your home directory?  If you aren't running e at all you can delete it.

I did, and I deleted it...plus a bunch of other /.x i didn't need. I then emptied trash...still the same

[EDIT]

Its weird, even though I empty trash, it still lets me click empty trash, usually if the trash is empty, it doesn't let you click empty trash...

---

### Post by smartboyathome on 2009-02-03
> **vegetarianshrimp said:**
> I did, and I deleted it...plus a bunch of other /.x i didn't need. I then emptied trash...still the same

[EDIT]

Its weird, even though I empty trash, it still lets me click empty trash, usually if the trash is empty, it doesn't let you click empty trash...

Try emptying root's trash by doing "gksudo nautilus".

---

### Post by vegetarianshrimp on 2009-02-03
Alt-F2 "gksudo nautilus"
Trash:
> The folder contents could not be displayed.
Sorry, could not display all the contents of "trash": Operation not supportedIs there a way to do it through the terminal maybe?

[EDIT]

also, it doesn't lat me press empty trash anymore, root or regular....
in root, after i click ok on the error message, it then says its loading the trash...

---

### Post by 4pr1l on 2009-02-05
there's a folder .trash ...
rm .trash/* -r should do it ..

---

### Post by vegetarianshrimp on 2009-02-05
```
rm: cannot remove `.trash/*': No such file or directory

```

---

### Post by smartboyathome on 2009-02-06
> **vegetarianshrimp said:**
> ```
rm: cannot remove `.trash/*': No such file or directory

```

it should be:
```
rm -r ~/.trash/
```

---

### Post by vegetarianshrimp on 2009-02-06
```
rm: cannot remove `/home/daniel/.trash/': No such file or directory

```

---

### Post by smartboyathome on 2009-02-06
In that case, I don't know where the extra 600mbs of space has gone. Seems really weird how that can just dissapear. Perhaps try using something like baobab?

---

### Post by vegetarianshrimp on 2009-02-06
sorry, im kind of a newb...whats baobab?

p.s. I installed cairo-dock and virtualbox in the midst of all this...is that what could have brought it down to 9.1 from 9.8?

---

### Post by smartboyathome on 2009-02-06
> **vegetarianshrimp said:**
> sorry, im kind of a newb...whats baobab?

p.s. I installed cairo-dock and virtualbox in the midst of all this...is that what could have brought it down to 9.1 from 9.8?

Probably. That would make sense.

By the way, baobab is just the disk analyzer in Ubuntu which tells you what folders are taking up the most space on your HDD.

---

### Post by vegetarianshrimp on 2009-02-06
ok thanks. sorry for all the trouble.

---

### Post by Gotaro on 2009-02-07
```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60487016493B3065
W: You may want to run apt-get update to correct these problems
```
Did I do something wrong?  I've done "wget -q [http://cafelinux.org/Downloads/oz-os/key.asc](http://cafelinux.org/Downloads/oz-os/key.asc) -O- | sudo apt-key add -" already.

---

### Post by smartboyathome on 2009-02-07
> **Gotaro said:**
> ```
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 60487016493B3065
W: You may want to run apt-get update to correct these problems
```
Did I do something wrong?  I've done "wget -q [http://cafelinux.org/Downloads/oz-os/key.asc](http://cafelinux.org/Downloads/oz-os/key.asc) -O- | sudo apt-key add -" already.

It is because of another repo that you are using, not because of OzOs's repo. Try disabling all launchpad repos one by one to see which is the culprit.

---

### Post by cyberneticdna on 2009-02-18
I hope I'm asking this question on the right forum if not I'm sorry.  I been trying to install the flame and Rain module on OzOS 64 bit, but I cannot seem to figure it out.  I have searched all over google and I cannot seem to get it right.  The last command I used thinking I was installing Flame was ```
sudo easy_e17.sh --only=flame
```

Which I know probably didn't install it either!  I'm a noob when it come on linux commands so please bear with me.  I have done other things dealing with terminal but compiling isn't something I do while neither is SVN or CVS...

So if anyone could please help me install Rain and Flame Modules I would really appreciate it!!

---

### Post by Tux Aubrey on 2009-02-18
Hi cyberneticdna

You are on the right track but need to first edit the easy_e17 configuration file that tells the script which packages to skip.

Open it with:

```
sudo <your fave text editor> /etc/easy_e17.conf
```

delete "flame" and "rain" from the list then save.

The command you want is:
```

sudo easy_e17.sh --only=flame,rain
```

(BTW, I have no idea what those packages do or how to invoke them!)

---

### Post by cyberneticdna on 2009-02-18
They are just eye candy modules.  So after I delete the flame and rain for that conf file and do that command will it just download the the source code and I would have to manually compile it or would it automatically install it?  That is where I'm stuck.

I don't know if I need to compile it or if it automatically installs it.  

Also why didn't it install when I did the command just for flame is it because I didn't delete it from the conf file?  

As you can see I'm a little lost here with that.:(

---

### Post by smartboyathome on 2009-02-18
You need to delete them from the conf file because it overrides the commands given to it. If that conf file weren't existing, then the script would try to install everything from E17's SVN repo, which would be a mess since something could break something else.

Just do what Tux said above, as that will download the source and install it for you.

---

### Post by cyberneticdna on 2009-02-18
> Hello and thank you Rui Pais for this deb, it makes the installation really nice and without any worry !

I just want to precise that in the first post, you mistyped the name of configuration file (you wrote /etc/easy_e17.sh instead of /etc/easy_e17.conf)

And I would like to know why you changed the src path to /var/cache. Is it to be more compliant with usual debian paths ?

I wanted to add the module "places", which is not in the current easy_e17.sh. I didn't know where e17-svn installed the script itself, so I downloaded easy_e17.sh, added the name "places" to the list of packages (in the variable packages at the beginning of easy_e17.sh) and ran it so :

Code:

# ./easy_e17.sh --only=places --srcpath=/var/cache

And it worked perfectly well. Maybe I should precise that my laptop is running UbuntuStudio 8.04.

By the way, places is a very nice module. I hope a next easy_e17.sh -u won't break everything !

I read this post and was wondering if there is anything else I would need to do to install this module?  It looks as if I would just enter this code in terminal and that is it, is that correct?

---

### Post by smartboyathome on 2009-02-18
correct. You need to run it as root though. Also, you don't need to use that "srcpath" option, it is just for people who don't want the source to go into /var/cache/e17_svn.

---

### Post by cyberneticdna on 2009-02-18
I didn't enable root during install, so would I enable superuser in console? I think the command is 

```
sudo -i
```

Please correct me if I'm wrong.  Also I'm interested in installing Virtualbox so in and install windows so I can use some of my media streaming software to stream movies to my ps3.  I read through the install instructions for ubuntu briefly is there anything special I need to take note about since I'm using OzOS 64-bit?  Thanks for the help I really appreciate it!!

---

### Post by smartboyathome on 2009-02-18
Use sudo followed by the command you want to run to run the command as root. sudo -i lets you log into a root shell. If you want to install virtualbox, run this command:
sudo apt-get install virtualbox
Or download and run the .deb from Virtualbox's site.

---

### Post by cyberneticdna on 2009-02-18
Thanks for letting me pick your brain.  Got another question.  very simple one.  How would I go by replacing GDM with SLiM (simple login manager) or if possible Entrance.  I remember reading a post about Entrance not wanting to play right with the easy e17 script.  Is there a way to by past this?

---

### Post by smartboyathome on 2009-02-18
> **cyberneticdna said:**
> Thanks for letting me pick your brain.  Got another question.  very simple one.  How would I go by replacing GDM with SLiM (simple login manager) or if possible Entrance.  I remember reading a post about Entrance not wanting to play right with the easy e17 script.  Is there a way to by past this?

There is one way past this: compile entrance manually from the sources on your comp. Just type this into a terminal, and it should install:
```
sudo -i
cd /var/cache/e17_src
PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/opt/e17/lib ./configure --prefix=/usr
make
make install
```

---

### Post by whoop on 2009-02-23
I have been getting:
```

svn: Failed to add file 'E-MODULES-EXTRA/screenshot/INSTALL': object of the same name already exists

```

for some time now when executing 
```

sudo easy_e17.sh -u

```

What can I do about this?

---

### Post by Tux Aubrey on 2009-02-23
> **whoop said:**
> I have been getting:
```

svn: Failed to add file 'E-MODULES-EXTRA/screenshot/INSTALL': object of the same name already exists

```

for some time now when executing 
```

sudo easy_e17.sh -u

```

What can I do about this?

Bad coders!  You have to fix this one manually - but it is easy.

1. delete the file /var/cache/e17_src/E-MODULES-EXTRA/screenshot/INSTALL

```
cd /var/cache/e17_src/E-MODULES-EXTRA/screenshot
sudo rm INSTALL
```

2. run easy_e17.sh to update:

```
sudo easy_e17.sh -u
```


That's it.

---

### Post by whoop on 2009-02-23
> **Tux Aubrey said:**
> Bad coders!

:lolflag:

---

### Post by neatojones on 2009-02-28
How can I re-install a module?  I installed ecore and it succesfully installed, but I would like to reinstall that part only.  Is there a way to do this with the script?  

Thanks.

---

### Post by Tux Aubrey on 2009-02-28
> **neatojones said:**
> How can I re-install a module?  I installed ecore and it succesfully installed, but I would like to reinstall that part only.  Is there a way to do this with the script?  

Thanks.

Sure:

```
sudo easy_e17.sh --only=ecore
```

That will bring ecore up to the current revision and recompile/install it.

---

### Post by linuxchuck on 2009-03-04
> **originalsynthesis said:**
> If i remove icons from, or change the size of the shelf, enlight. completely freezes up. 


I've seen a very similar issue, and was able to determine that the problem (at least with ibar) had to do with the way the icons were referenced in the ~/.e/e/applications/bar/default/.order file.  It seems the ones (and it was only a few, wish I had written down which ones) causing the issue were listed without a full path to the .desktop file.

For example, take a look the following .order file:

```
/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Applications-System-Package-Management-synaptic_package_manager.desktop
VirtualBox.desktop
kde-filebrowser.desktop
iceweasel.desktop
icedove.desktop
skype.desktop
pidgin.desktop
kde-krdc.desktop
keepassx.desktop
/var/lib/menu-xdg/applications/menu-xdg/X-Debian-Applications-Graphics-ksnapshot.desktop
blackjack_connect.desktop

```

If I remember correctly, I had to add the absolute path information to the ksnapshot icon to avoid problems when I tried to reposition it in the bar.  Before doing so, the icon (and several others) would disappear when I tried to reposition it, and e17 would lock up on me, forcing me to use CTRL-ALT-BKSP to regain control of my system.

YMMV, but hopefully this helps shed a little light on the issue you've been having.

---

### Post by linuxchuck on 2009-03-05
Ok...

While we're on the topic of menus, I have a question:  During the initial config wizard of e17, you are presented with selecting which menu set to include in your enlightenment menu.  I tend to select "KDE Applications" because it is typically the most inclusive set that I can find out of the choices.  However, I wind up with a "lost and found" menu that spans 3-4 screens worth of entries.  I've looked into the xdg menu standards from freedesktop.org, and learned a bit of how things work, but I'm still not very strong in the creation or inclusion of existing menus on debian-based distros.  Has anyone come up with a process to reclaim all the lost menu entries and re-categorize them so the e17 menus are a bit more organized?

TIA

---

### Post by smartboyathome on 2009-03-05
I don't know how to change it after initial setup. I would just recommend using the standard menu, since it is the freedesktop.org standard-based menu which works with Alacarte. Anyway, have you tried asking on E17's IRC channel? The devs would probably be happy to help. It is #e on freenode.net.

---

### Post by Tux Aubrey on 2009-03-12
Just a note to say that it is NOT a good time to be installing e17 from svn - the current and recent revisions have major problems with "phantom" windows (apps not shutting down correctly).  It is still useable but requires restarting to clear the windows list before shutting down.

The bug with the screenshot module's INSTALL file not updating also persists (for those still tempted to update an existing e17 installation).

:(

---

### Post by linuxchuck on 2009-03-12
Something else that seems to be happening with recent builds is that if I log out of e17, and delete my profile (the ~/.e directory) in an attempt to force the "first start module" to run, my mouse seems to be "trapped" against the right side of the screen in a small area.  No menus or applications are available, and the first-start module does not start up.  As a further experiment, I tried to manually run the first-start module from inside e17 (yes, I've read the warning) and wound up with the exact same result.  This leads me to believe that the issue may be inside the first-start module itself.

Fortunately, I had the foresight to create a backup of my ~/.e directory before playing around with this.  ;)  A quick restore of the directory and I'm back in business...

If this is happening with the current SVN downloads, it may mean that nobody will be able to get a new install of e17 working until it is resolved.

I found this issue because I wanted to make a new attempt at re-creating my menu structure as suggested in previous posts.  Looks like I'll have to figure out a way to roll back to a previous SVN version to be able to do that.  Is there any way to get the easy_e17.sh script to do that?  I can't find anything listed in the help for it to specify a given SVN version to download...

---

### Post by smartboyathome on 2009-03-13
linuxchuck, you need to use update_e17.sh from the oz-e17-tools package in the OzOs repos. Here is the "easy way", paste these commands into the terminal.
```
sudo sh -c "echo 'deb http://cafelinux.org/Downloads/oz-os hungrytiger main' >> /etc/apt/sources.list"
wget -q http://cafelinux.org/Downloads/oz-os/key.asc -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install oz-e17-tools
update_e17.sh --revision {number}
#OR
update_e17.sh --date {date}
```
Replace {number} with the revision number, or {date} with the date you want to use. That should do it for you. :)

---

### Post by Tux Aubrey on 2009-03-13
> If this is happening with the current SVN downloads, it may mean that nobody will be able to get a new install of e17 working until it is resolved.

Thanks for the heads-up.  I'll check this out tonight with a fresh install.

And, yes, update_e17.sh also has a profile backup mode that is very useful for those time you want to muck around with profiles (especially if you are silly enough to try illume!).  Having both update_e17 and easy_e17 gives you a lot of options to manage svn installs - there is some overlap between them, but together they are great.

---

### Post by linuxchuck on 2009-03-13
> **smartboyathome said:**
> linuxchuck, you need to use update_e17.sh from the oz-e17-tools package in the OzOs repos. Here is the "easy way", paste these commands into the terminal.


Outstanding!  I'll give this a shot today and see what I can come up with.  Thanks for the info.  Somehow, I must have missed this script being mentioned earlier in the thread or I would have already tried it.

TYVM!

---

### Post by linuxchuck on 2009-03-13
FYI, tonight's build seems to have fixed the profile creation issue.  I can now create a new profile from scratch without any problems.


In reference to my earlier menu problem:

> **smartboyathome said:**
> I don't know how to change it after initial setup. I would just recommend using the standard menu, since it is the freedesktop.org standard-based menu which works with Alacarte. Anyway, have you tried asking on E17's IRC channel? The devs would probably be happy to help. It is #e on freenode.net.

I do still have the menu issue...

I have tested it by skipping the "pick an applications menu" in the beginning, and wound up with (surprise) a blank applications menu.

Out of curiosity, smartboyathome, how do you choose to just use the "standard menu"?  As I've mentioned before, I tried choosing the KDE applications menu, the Gnome applications menu, and the others offered on the list, and still wind up with a *HUGE* lost-and-found menu full of un-sorted items.

If it makes any difference, I'm running Debian Lenny.

---

### Post by vahnx on 2009-03-13
Using easy_e17 I'm getting:

> sudo sh easy_e17.sh 
easy_e17.sh: 45: Syntax error: "(" unexpected

Can't find where that bracket is, line 45 seems correct.

---

### Post by linuxchuck on 2009-03-13
> **vahnx said:**
> Using easy_e17 I'm getting:



Can't find where that bracket is, line 45 seems correct.


hrm...  Do you have the latest version of the script?

---

### Post by smartboyathome on 2009-03-14
Also, what shell are you using? Ie, bash, dash, zsh, etc.

---

### Post by evets on 2009-03-14
[QUOTE=Tux Aubrey;6886510]Thanks for the heads-up.  I'll check this out tonight with a fresh install.

I'm having a problem. When I enter sudo apt-get install e17-svn, I get a list-but-they all say...

{example}
 Depends: build essential but it is not going to be installed
E. Broken packages.

Any idea where I borked it? 

Thanks for your work and your help.

---

### Post by smartboyathome on 2009-03-14
You have any extra repos besides the main repos and the repo in the first post? If so, disable them. That would be what is causing the conflict.

---

### Post by evets on 2009-03-14
> **smartboyathome said:**
> You have any extra repos besides the main repos and the repo in the first post? If so, disable them. That would be what is causing the conflict.

I have the following, which is incorrect? I added HungryTiger after I tried Tinwoodman and it failed, should I remove it now? I'm running Intrepid.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) hungrytiger main

Thanks for your help.

I'll be back in a few hours, appt. with accountant right now. LOL

---

### Post by smartboyathome on 2009-03-15
> **evets said:**
> I have the following, which is incorrect? I added HungryTiger after I tried Tinwoodman and it failed, should I remove it now? I'm running Intrepid.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) hungrytiger main

Thanks for your help.

I'll be back in a few hours, appt. with accountant right now. LOL

Can you post your whole /etc/apt/sources.list, please? That way I can see if there is anything at all wrong with it. :)

---

### Post by evets on 2009-03-15
> **smartboyathome said:**
> Can you post your whole /etc/apt/sources.list, please? That way I can see if there is anything at all wrong with it. :)

> 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid main

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.



deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid-security multiverse
deb [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) intrepid main
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) intrepid non-free
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main
deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) hungrytiger main



Thanks!

---

### Post by smartboyathome on 2009-03-15
Try this one:
```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid main

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.



deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner
deb http://archive.ubuntu.com/ubuntu/ intrepid-security main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security main
deb http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security universe
deb http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
deb-src http://archive.ubuntu.com/ubuntu/ intrepid-security multiverse
#deb http://ppa.launchpad.net/reacocard-awn/ubuntu intrepid main
#deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
deb http://cafelinux.org/Downloads/oz-os tinwoodman main
deb http://cafelinux.org/Downloads/oz-os hungrytiger main
```

---

### Post by evets on 2009-03-15
Same thing, "is not going to be installed."

Thanks for trying. I need to put this on the back burner to get some other work done now.

Again, thanks for the help. I appreciate it.

---

### Post by whoop on 2009-03-19
I got an error today trying to update using sudo easy_e17.sh -u

here is the output:
```

-------------------------------------------------------------------------------
EASY_E17 1.2.3.3-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running autopoint...
Running aclocal...
Running autoconf...
Running autoheader...
Running libtoolize...
Running automake...
config/Makefile.am:12: `%'-style pattern rules are a GNU make extension
config/default/Makefile.am:16: `%'-style pattern rules are a GNU make extension
config/illume/Makefile.am:26: `%'-style pattern rules are a GNU make extension
config/minimalist/Makefile.am:32: `%'-style pattern rules are a GNU make extension
config/netbook/Makefile.am:32: `%'-style pattern rules are a GNU make extension
config/scaleable/Makefile.am:32: `%'-style pattern rules are a GNU make extension
config/standard/Makefile.am:32: `%'-style pattern rules are a GNU make extension
checking build system type... x86_64-unknown-linux-gnu
checking host system type... x86_64-unknown-linux-gnu
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for strerror in -lcposix... no
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking whether byte ordering is bigendian... no
checking for gcc option to accept ISO C99... -std=gnu99
checking whether gcc -std=gnu99 and cc understand -c and -o together... yes
checking for an ANSI C-conforming const... yes
checking for working alloca.h... yes
checking for alloca... yes
checking for __attribute__... yes
checking for a sed that does not truncate output... /bin/sed
checking for fgrep... /bin/grep -F
checking for ld used by gcc -std=gnu99... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for BSD- or MS-compatible name lister (nm)... /usr/bin/nm -B
checking the name lister (/usr/bin/nm -B) interface... BSD nm
checking whether ln -s works... yes
checking the maximum length of command line arguments... 1572864
checking whether the shell understands some XSI constructs... yes
checking whether the shell understands "+="... yes
checking for /usr/bin/ld option to reload object files... -r
checking how to recognize dependent libraries... pass_all
checking for ar... ar
checking for strip... strip
checking for ranlib... ranlib
checking command to parse /usr/bin/nm -B output from gcc -std=gnu99 object... ok
checking for dlfcn.h... yes
checking for objdir... .libs
checking if gcc -std=gnu99 supports -fno-rtti -fno-exceptions... no
checking for gcc -std=gnu99 option to produce PIC... -fPIC -DPIC
checking if gcc -std=gnu99 PIC flag -fPIC -DPIC works... yes
checking if gcc -std=gnu99 static flag -static works... yes
checking if gcc -std=gnu99 supports -c -o file.o... yes
checking if gcc -std=gnu99 supports -c -o file.o... (cached) yes
checking whether the gcc -std=gnu99 linker (/usr/bin/ld -m elf_x86_64) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
checking for setenv... yes
checking for unsetenv... yes
checking fnmatch.h usability... yes
checking fnmatch.h presence... yes
checking for fnmatch.h... yes
checking for fnmatch... yes
checking security/pam_appl.h usability... yes
checking security/pam_appl.h presence... yes
checking for security/pam_appl.h... yes
checking for X... libraries , headers 
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking X11/X.h usability... yes
checking X11/X.h presence... yes
checking for X11/X.h... yes
checking CFBase.h usability... no
checking CFBase.h presence... no
checking for CFBase.h... no
checking whether NLS is requested... yes
checking for msgfmt... /usr/bin/msgfmt
checking for gmsgfmt... /usr/bin/msgfmt
checking for xgettext... /usr/bin/xgettext
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for dlopen in -ldl... yes
checking whether to enable Files menu item... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for E_REMOTE... yes
checking for E_IMC... yes
checking for E_THUMB... configure: error: Package requirements (
  evas
  ecore
  ecore-evas
  edje
  ecore-file
  ecore-ipc
  eet >= 1.0.1
  efreet
) were not met:

Package input was not found in the pkg-config search path.
Perhaps you should add the directory containing `input.pc'
to the PKG_CONFIG_PATH environment variable
Package 'input', required by 'ecore-x', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables E_THUMB_CFLAGS
and E_THUMB_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Any ideas on how to solve this? Is anybody else getting this? I am using jaunty.

---

### Post by Evomaster on 2009-04-03
Hello all
I'm new here and I try to install e17.
When I do : sudo apt-get install e17-svn I have this message

- checkout sources ...
   downloading eina source ...
svn: Le serveur a envoyé une valeur inattendue (400 ) en réponse à la requête PROPFIND pour '/svn/e/trunk/eina'
svn: Le serveur a envoyé une valeur inattendue (400 ) en réponse à la requête PROPFIND pour '/svn/e/trunk/eina'
svn: Le serveur a envoyé une valeur inattendue (400 ) en réponse à la requête PROPFIND pour '/svn/e/trunk/eina'

It's in french, but it says that the server send an inattempted response for teh PROFIND request for /svn/e/trunk/eina

Thanks

---

### Post by smartboyathome on 2009-04-03
Odd, it might be SVN breakage. My recommendation would be to try again in a few hours and see if it works.

---

### Post by Evomaster on 2009-04-03
I don't thimk so, i have this problem for days

---

### Post by smartboyathome on 2009-04-03
> **Evomaster said:**
> I don't thimk so, i have this problem for days

If that is the case, then you can try running the command:
```
sudo rm -r /var/cache/e17_src
```
And then try installing again.

---

### Post by Evomaster on 2009-04-06
Not better with this command.
I think it's perhaps a problem with the firewall

---

### Post by smartboyathome on 2009-04-06
> **Evomaster said:**
> Not better with this command.
I think it's perhaps a problem with the firewall

If it is a problem with the firewall, not much this script can do to help, I'm afraid. The script is simpler in that reguard, only offering to go through the one port. Perhaps disabling the firewall while trying to download the stuff, just to see if it is indeed the problem? Or if you can't, you can always download the source from another computer and bring it to the computer to be installed on via flash drive.

---

### Post by Evomaster on 2009-04-06
I can't switch off the firewall.
Do you know which port is used to dl the sources ?

---

### Post by smartboyathome on 2009-04-06
> **Evomaster said:**
> I can't switch off the firewall.
Do you know which port is used to dl the sources ?

No, sorry, I don't. Do you have another computer you can download the sources on, though? It really doesn't matter what OS you run, all should work.

---

### Post by Evomaster on 2009-04-07
OK thanks, I will try this way

---

### Post by mmarti on 2009-04-07
Hi all,

I'm trying to install e17 with the easy_17.sh script on my Gutsy Ubuntu and have the following error:

- enthrall ................... make   : ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.4 CMD: make PREFIX=/opt/e17 -j 2
-------------------------------------------------------------------------------
cc -g -Wall `pkg-config --cflags libavformat libavcodec` -c -o src/ffmpeg.o src/ffmpeg.c
src/ffmpeg.c: In function ‘enthrall_ffmpeg_finish’:
src/ffmpeg.c:245: error: incompatible type for argument 1 of ‘url_fclose’
src/ffmpeg.c: In function ‘enthrall_ffmpeg_encode_frame’:
src/ffmpeg.c:270: warning: ‘img_convert’ is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)
make: *** [src/ffmpeg.o] Error 1

Can you hellp me?

Regards

Mike

---

### Post by Tux Aubrey on 2009-04-07
> **mmarti said:**
> Hi all,

I'm trying to install e17 with the easy_17.sh script on my Gutsy Ubuntu and have the following error:

- enthrall ................... make   : ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.4 CMD: make PREFIX=/opt/e17 -j 2
-------------------------------------------------------------------------------
cc -g -Wall `pkg-config --cflags libavformat libavcodec` -c -o src/ffmpeg.o src/ffmpeg.c
src/ffmpeg.c: In function &#8216;enthrall_ffmpeg_finish&#8217;:
src/ffmpeg.c:245: error: incompatible type for argument 1 of &#8216;url_fclose&#8217;
src/ffmpeg.c: In function &#8216;enthrall_ffmpeg_encode_frame&#8217;:
src/ffmpeg.c:270: warning: &#8216;img_convert&#8217; is deprecated (declared at /usr/include/ffmpeg/avcodec.h:2575)
make: *** [src/ffmpeg.o] Error 1

Can you hellp me?

Regards

Mike

Hi Mike

"enthrall" is a known baddy (I have no idea what it does, but it isn't required)

The best remedy I know is to edit the easy_e17 config file and add it to the list of packages to skip.

```
sudo gedit /etc/easy_e17.conf

You could just add enthrall to the list or overwrite the whole file with this one:
[CODE]--
--skip=esmart,enhance,exml,imlib2,edb,edje_player,edje_viewer,emotion,entrance,eclair,evfs,evolve,elicit,elitaire,emphasis,empower,engycad,entrance_edit_gui,entropy,ephoto,estickies,expedite,exquisite,extrackt,engage,enthrall,exalt,exhibit,rage,emu,moon,news,penguins,rain,snow,language,photo,efm_path,efm_nav,e_phys,mpdule,notification,

```
Those "skipped" packages are either broken or not required (you can always delete them from this list later to try them out)

Note the two "-" marks on the first line.  It isn't relevant to your particular problem, but if there is a "conflicts" statement there in your version, replace it (this relates to a fairly recent change in svn itself and specific "conflict" flags are not required or useful anymore)

---

### Post by Rui Pais on 2009-04-07
> **Evomaster said:**
> Not better with this command.
I think it's perhaps a problem with the firewall

Hi Evomaster, i think an user had the same issue and solve it by using another (secure) server path. 
Try edit your /etc/easy_e17.sh and add the following line:
```
--srcurl="https://svn.enlightenment.org/svn/e/trunk"
```
and see if that helps.

Good luck

---

### Post by Evomaster on 2009-04-08
It works
Thanks :popcorn:

---

### Post by DrSB on 2009-04-16
Hello All new to this forum and only been using Ubuntu 8.10 for a month now but loving it!! am trying to install e17 as described by the method in the first post. Despite following the instructions to the letter i get the following error:

sameer@Ubuntu:~$ sudo sh -c "echo 'deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main' >> /etc/apt/sources.list"

sameer@Ubuntu:~$ wget -q [http://cafelinux.org/Downloads/oz-os/key.asc](http://cafelinux.org/Downloads/oz-os/key.asc) -O- | sudo apt-key add -OK

sameer@Ubuntu:~$ sudo apt-get install e17-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  e17-svn: Depends: giblib-dev but it is not installable
           Depends: libgtk1.2-dev but it is not installable
E: Broken packages



I not a computer expert by any means just learning how to use the command line with the help of a friend, so please be gentle ;) but any help would be greatly appreciated.

Thanks

---

### Post by shohart on 2009-04-17
guys got a problem: 

with e packadge
Running autopoint...
Running aclocal...
Running autoconf...
Running autoheader...
Running libtoolize...
Running automake...
EXTRA_DIST: variable `kbds_DATA' is used but `kbds_DATA' is undefined
EXTRA_DIST: variable `dicts_DATA' is used but `dicts_DATA' is undefined

with eet packadge
checking zlib.h usability... yes
checking zlib.h presence... yes
checking for zlib.h... yes
checking jpeglib.h usability... no
checking jpeglib.h presence... no
checking for jpeglib.h... no
configure: error: "Cannot find jpeglib.h. Make sure your CFLAGS environment variable contains include lines for the location of this file"

what should i do?

---

### Post by smartboyathome on 2009-04-17
E17 is in a constant state of flux right now, as it is being prepared for a development snapshot and the developers are trying to get everything in. It will be unstable for a few days. I recommend only upgrading when they will be having stability only updates as noted [here]("http://trac.enlightenment.org/e/wiki/ReleaseSchedule").

---

### Post by DrSB on 2009-04-17
Thanks will wait for the stable version

---

### Post by linuxchuck on 2009-04-29
I have a quick xdg-menu question:

The first time you start up e17 with no profile available, their version of a "first run wizard" is run via a module.  One of the first steps is to choose a set of menus to incorporate into the menu available to e17.

I have a friend that I recently converted over to e17, and he's loving it.  However, it appears he chose the wrong menu set during that first-run wizard, and has some very limited menu choices available.  I would like to know if any of you are aware of a simple way to re-select the menu setup without blowing away the current profile.

Thanks in advance...

---

### Post by Tux Aubrey on 2009-04-30
> **linuxchuck said:**
> I have a quick xdg-menu question:

The first time you start up e17 with no profile available, their version of a "first run wizard" is run via a module.  One of the first steps is to choose a set of menus to incorporate into the menu available to e17.

I have a friend that I recently converted over to e17, and he's loving it.  However, it appears he chose the wrong menu set during that first-run wizard, and has some very limited menu choices available.  I would like to know if any of you are aware of a simple way to re-select the menu setup without blowing away the current profile.

Thanks in advance...

Your friend could try alacarte or gmenu-simple-editor to manually fix the Applications menu entries.  Both will run from the CLI in e17 on an Ubuntu install.

---

### Post by [JCD] on 2009-05-01
Hello, everyone! Building e17 I've got some problems, and one of them comes here (the others are already solved):

```

- expedite ................... autogen: ERROR!

------ Last loglines ------

EASY_E17 1.2.4 CMD: ./autogen.sh --prefix=/opt/e17  
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
libtoolize: You should add the contents of `m4/libtool.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltoptions.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltsugar.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltversion.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/lt~obsolete.m4' to `aclocal.m4'.
Running automake...
/usr/share/automake-1.9/am/depend2.am: am__fastdepOBJC does not appear in AM_CONDITIONAL

```

How to solve this?

---

### Post by Tux Aubrey on 2009-05-01
> **'[JCD] said:**
> Hello, everyone! Building e17 I've got some problems, and one of them comes here (the others are already solved):

```

- expedite ................... autogen: ERROR!

------ Last loglines ------

EASY_E17 1.2.4 CMD: ./autogen.sh --prefix=/opt/e17  
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
libtoolize: You should add the contents of `m4/libtool.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltoptions.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltsugar.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/ltversion.m4' to `aclocal.m4'.
libtoolize: You should add the contents of `m4/lt~obsolete.m4' to `aclocal.m4'.
Running automake...
/usr/share/automake-1.9/am/depend2.am: am__fastdepOBJC does not appear in AM_CONDITIONAL

```

How to solve this?

**expedite** is a known baddie.  Best practice is to skip it by opening /etc/easy_e17.conf and adding it to the list.

That file should be a single line with the names of all the unwanted components in a simple comma separated list.

Here's my current /etc/easy_e17.conf

```
--skip=esmart,enhance,exml,imlib2,edb,edje_player,edje_viewer,emotion,entrance,eclair,evfs,evolve,elicit,elitaire,emphasis,empower,engycad,entrance_edit_gui,entropy,ephoto,estickies,expedite,exquisite,extrackt,engage,enthrall,exalt,exalt-client,exhibit,rage,emu,moon,news,penguins,rain,snow,language,photo,efm_path,efm_nav,e_phys,mpdule,notification,

```

---

### Post by MyR on 2009-05-01
Hello, I have a few questions:

1. How do I find out what each of those skipped modules do so I can decide whether or not I want them?

2. How do I connect to wireless since network-manager doesn't work?

3. Would it be faster to use entrance rather than gdm, could I auto login using this, and are there any disadvantages?

I'm running 9.04.
thanks

---

### Post by smartboyathome on 2009-05-01
> **MyR said:**
> Hello, I have a few questions:

1. How do I find out what each of those skipped modules do so I can decide whether or not I want them?

2. How do I connect to wireless since network-manager doesn't work?

3. Would it be faster to use entrance rather than gdm, could I auto login using this, and are there any disadvantages?

I'm running 9.04.
thanks

1. Try each one out, or read the READMEs in the appropriate /var/cache/e17_src/ directory.

2. The recommended method by the OzOs team (which is the team which uses this right now) is to use WICD, but you can try the very experimental system tray which is now being developed for E17 so that you can continue to use NM.

3. The fastest way if you are autologging in is to use a method similar to [Method 3 for Arch Linux here]("http://wiki.archlinux.org/index.php/Start_X_at_boot#Method_3:_.7E.2F.bash_profile"). It should work pretty much the same if you follow that plus the link it gives you for autologing in, as the inittab files are very similar.
The main disadvantages of Entrance, though, is that it is more unstable, and doesn't offer the autologin feature. Add in the lack of themes (you have to create them yourself, not that hard once you get used to it), and to me it isn't worth it over GDM or the aforementioned method.

---

### Post by |{urse on 2009-05-02
Im back to e17 again after a love affair with openbox. Thanks for all your ongoing efforts SmartBoyAtHome and RuiPais. :)

---

### Post by smartboyathome on 2009-05-02
> **|{urse said:**
> Im back to e17 again after a love affair with openbox. Thanks for all your ongoing efforts SmartBoyAtHome and RuiPais. :)

Actually, now I am the "maintainer", as Rui Pais doesn't have enough time on his hands to do anything right now. Right now it doesn't need maintaining, but oh well, it is good to have an official maintainer in case something breaks. :P

---

### Post by Hendershot on 2009-05-03
Sorry if this has been covered before, but I'm a noob, and I didn't want to sift through 30 pages of post to find if this was already covered or not.  My problem:   When I start and Enlightenment session from the GDM I get the error  "No Exec line in session file: Enlightenment"  and it switches to GNOME failsafe mode.   Please help, I'm new at this stuff and I want to get the E DE working on ubuntu. I originally got interested in linux after using Elive, and since then I have tried to install E17 in ubuntu numerous times, and this tutorial is the closest I've gotten.   Thankyou much

---

### Post by Tux Aubrey on 2009-05-03
> **Hendershot said:**
> Sorry if this has been covered before, but I'm a noob, and I didn't want to sift through 30 pages of post to find if this was already covered or not.  My problem:   When I start and Enlightenment session from the GDM I get the error  "No Exec line in session file: Enlightenment"  and it switches to GNOME failsafe mode.   Please help, I'm new at this stuff and I want to get the E DE working on ubuntu. I originally got interested in linux after using Elive, and since then I have tried to install E17 in ubuntu numerous times, and this tutorial is the closest I've gotten.   Thankyou much

Hi Hendershot

You most likely struck a bad revision of the source code - one of the key components "ecore" has been naughty for the last 24 hrs or so.  The good news is that it seems to be fixed now - as at revision 40503.

The bad news is that you have a bad (and probably incomplete) install and need to run the easy_e17.sh script again. 

From the gnome terminal session, do this:

```
sudo easy_e17.sh -i
```

and then go and have a coffee, watch a movie or visit a friend - it will update and reinstall e17.  If you do get any error messages, post here.

Good luck.

---

### Post by MyR on 2009-05-03
I went ahead and installed [OpenGEU]("http://opengeu.intilinux.com/Home.html") -- a distribution based on Ubuntu using e17 by default.  I would definitely recommend it.

---

### Post by Hendershot on 2009-05-03
HA 

I'm sitting here laughing my *** off.

Because my box crashed and I couldn't fix it so I did a complete reinstall of 9.04. (well 8.10 then updated to 9.04 so it took twice as long, gotta burn another copy)

So I get to do it over no matter what. If I have any more problems... well you get the rest.

Thank you much!

---

### Post by Hendershot on 2009-05-03
I'm in stage two of the install ecore installed but it skipped esmart and emotion, will this end well?

---

### Post by Tux Aubrey on 2009-05-03
> **Hendershot said:**
> I'm in stage two of the install ecore installed but it skipped esmart and emotion, will this end well?

No problem!  "Skipping" is built into the script - these are source packages that are non-essential **and**:

a) possibly broken or poorly maintained, 
b) "just" eye-candy demos with no real functionality (flame, snow), or
c) still fairly experimental little apps and gadgets that haven't really reached the level of functionality of their gtk (gnome/xfce) equivalents.

It is possible to try them out, but there's an extra level of risk involved.  Rui (who created this version of the easy_e17 script) and smartboyathome (who looks after maintenance) will occasionally change the skip list if new issues arise (or things look like they are now well maintained).

The "skip" list is defined in a config file called /etc/easy_e17.conf.  It can be amended with a text editor (with sudo) if you are inclined to do that.

I'd suggest getting comfortable with the "default" install before you do this.

---

### Post by Hendershot on 2009-05-03
Thank you so much, it skipped a lot of packages and eventually errored so i read through the original posts and some additional tricks,  and i now feel more confident. 

But it takes forever! especial after the jaunty reinstall.

---

### Post by dros74 on 2009-05-03
I have been trying this for hours without success. I always run into the same error.
Any clues?


```
dros@netstorm:~$ sudo easy_e17.sh -i
---------------------------- Easy_e17.sh 1.2.4.2-OzOS --------------------------
  Developers:      Brian 'morlenxus' Miculcy                                    
                   David 'onefang' Seikel                                       
  Contributors:    Tim 'amon' Zebulla                                           
                   Daniel G. '_ke' Siegel                                       
                   Stefan 'slax' Langner                                        
                   Massimiliano 'Massi' Calamelli                               
                   Thomas 'thomasg' Gstaedtner                                  
                   Roberto 'rex' Sigalotti                                      

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17                                                     
  Source path:     /var/cache/e17_src                                           
  Source url:      http://svn.enlightenment.org/svn/e/trunk                     
  Logs path:       /tmp/easy_e17/install_logs                                   

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor elicit elitaire enna enthrall emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu deskshow diskio drawer efm_nav efm_path emu exalt-client execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places rain screenshot slideshow snow systray taskbar tclock tiling uptime weather winselector wlan                                                 
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt-client exhibit rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w                                                                                                   

  Source conflict: solve automatically
  Script action:   install            
--------------------------------------------------------------------------------

-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks                                              
- source checkout/update                                                        
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok                                               
- 'automake' available ....... ok                                               
- 'gcc' available ............ ok                                               
- 'make' available ........... ok                                               
- 'svn' available ............ ok                                               
- build-user ................. root                                             
- adding path to env ......... ok                                               
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)                  
- setting compile options .... ok                                               
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
- checkout sources ...                                                          
   downloading eina source ...                                                  
   downloading eet source ...                                                   
   downloading evas source ...                                                  
   downloading ecore source ...                                                 
   downloading efreet source ...                                                
   downloading embryo source ...                                                
   downloading edje source ...                                                  
   downloading epsilon source ...                                               
   downloading esmart source ...                                                
   downloading emotion source ...                                               
   downloading etk source ...                                                   
   downloading etk_extra source ...                                             
   downloading ewl source ...                                                   
   downloading exml source ...                                                  
   downloading enhance source ...                                               
   downloading e_dbus source ...                                                
   downloading e source ...                                                     
   downloading entrance source ...                                              
   downloading edje_editor source ...                                           
   downloading elicit source ...                                                
   downloading elitaire source ...                                              
   downloading emphasis source ...                                              
   downloading empower source ...                                               
   downloading emprint source ...                                               
   downloading ephoto source ...                                                
   downloading estickies source ...                                             
   downloading exhibit source ...                                               
   downloading expedite source ...                                              
   downloading exquisite source ...                                             
   downloading E-MODULES-EXTRA source ...                                       
   downloading MISC source ...                                                  
   downloading rage source ...                                                  
   downloading THEMES source ...                                                

--------------------------------------------------------------------------------

---------------------------- Easy_e17.sh 1.2.4.2-OzOS --------------------------
  Developers:      Brian 'morlenxus' Miculcy                                    
                   David 'onefang' Seikel                                       
  Contributors:    Tim 'amon' Zebulla                                           
                   Daniel G. '_ke' Siegel                                       
                   Stefan 'slax' Langner                                        
                   Massimiliano 'Massi' Calamelli                               
                   Thomas 'thomasg' Gstaedtner                                  
                   Roberto 'rex' Sigalotti                                      

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17                                                     
  Source path:     /var/cache/e17_src                                           
  Source url:      http://svn.enlightenment.org/svn/e/trunk                     
  Logs path:       /tmp/easy_e17/install_logs                                   

  Packages:        eina eet evas ecore efreet embryo edje epsilon esmart emotion etk etk_extra ewl exml enhance e_dbus e entrance edje_editor elicit elitaire enna enthrall emphasis empower emprint ephoto estickies exhibit expedite exquisite extrackt eyesight e_phys rage alarm bling calendar cpu deskshow diskio drawer efm_nav efm_path emu exalt-client execwatch flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places rain screenshot slideshow snow systray taskbar tclock tiling uptime weather winselector wlan                                                 
  Skipping:        esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt-client exhibit rage emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w                                                                                                   

  Source conflict: solve automatically
  Script action:   install            
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation                                              
- apps-compilation and installation                                             
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- eina ....................... ok                                               
- eet ........................ ok                                               
- evas ....................... ok                                               
- ecore ...................... ok                                               
- efreet ..................... ok                                               
- embryo ..................... ok                                               
- edje ....................... ok                                               
- epsilon .................... ok                                               
- esmart ..................... SKIPPED                                          
- emotion .................... SKIPPED                                          
- etk ........................ ok                                               
- etk_extra .................. ok                                               
- ewl ........................ ok                                               
- exml ....................... SKIPPED                                          
- enhance .................... SKIPPED                                          
- e_dbus ..................... ok                                               
- e .......................... make   : ERROR!                                  
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
e_int_config_wallpaper_import.c:150: warning: ignoring return value of ‘evas_object_key_grab’, declared with attribute warn_unused_result                                                                                                       
e_int_config_wallpaper_import.c:152: warning: ignoring return value of ‘evas_object_key_grab’, declared with attribute warn_unused_result                                                                                                       
e_int_config_wallpaper_import.c:154: warning: ignoring return value of ‘evas_object_key_grab’, declared with attribute warn_unused_result                                                                                                       
/bin/bash ../../../libtool --tag=CC   --mode=compile gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../../.. -I. -I../../.. -I../../../src/modules/conf_wallpaper -I../../../src/bin -I../../../src/lib -I../../../src/modules -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include/efreet -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include   -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include -I/usr/include/exchange -I/usr/include/libxml2    -I/opt/e17/include   -MT e_int_config_wallpaper_web.lo -MD -MP -MF .deps/e_int_config_wallpaper_web.Tpo -c -o e_int_config_wallpaper_web.lo e_int_config_wallpaper_web.c                                                                                    
e_int_config_wallpaper_import.c: In function ‘e_int_config_wallpaper_fsel’:                                             
e_int_config_wallpaper_import.c:294: warning: ignoring return value of ‘evas_object_key_grab’, declared with attribute warn_unused_result                                                                                                       
e_int_config_wallpaper_import.c:296: warning: ignoring return value of ‘evas_object_key_grab’, declared with attribute warn_unused_result                                                                                                       
e_int_config_wallpaper_import.c:298: warning: ignoring return value of ‘evas_object_key_grab’, declared with attribute warn_unused_result                                                                                                       
e_int_config_wallpaper_import.c:300: warning: ignoring return value of ‘evas_object_key_grab’, declared with attribute warn_unused_result                                                                                                       
libtool: compile:  gcc -std=gnu99 -DHAVE_CONFIG_H -I. -I../../.. -I. -I../../.. -I../../../src/modules/conf_wallpaper -I../../../src/bin -I../../../src/lib -I../../../src/modules -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include/efreet -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include -I/usr/include/exchange -I/usr/include/libxml2 -I/opt/e17/include -MT e_int_config_wallpaper_web.lo -MD -MP -MF .deps/e_int_config_wallpaper_web.Tpo -c e_int_config_wallpaper_web.c  -fPIC -DPIC -o .libs/e_int_config_wallpaper_web.o
mv -f .deps/e_int_config_wallpaper_import.Tpo .deps/e_int_config_wallpaper_import.Plo
mv -f .deps/e_int_config_wallpaper_web.Tpo .deps/e_int_config_wallpaper_web.Plo
/bin/bash ../../../libtool --tag=CC   --mode=link gcc -std=gnu99   -module -avoid-version -L/opt/e17/lib -o module.la -rpath /opt/e17/lib/enlightenment/modules/conf_wallpaper/linux-gnu-x86_64-ver-pre-svn-01 e_mod_main.lo e_int_config_wallpaper.lo e_int_config_wallpaper_gradient.lo e_int_config_wallpaper_import.lo e_int_config_wallpaper_web.lo -L/opt/e17/lib-L//lib -lecore_evas -lecore_x -lecore_txt -lecore_input -lecore_ipc -lecore_con -ledje -lembryo -lecore_job -levas -leet -lefreet -lefreet_mime -lecore_file -lgnutls -lcurl -lehal -ledbus -lecore -ldbus-1 -leina     -L/opt/e17/lib -lecore_imf_evas -lecore_imf -levas -lecore -leina   -ldl -L/opt/e17/lib -lexchange -lecore_evas -lecore_file -ledje -lxml2 -lecore_x -lecore_input -lecore_txt -lcurl -lembryo -lecore_job -levas -leet -lecore -lgnutls -leina   -lpam
libtool: link: gcc -std=gnu99 -shared  .libs/e_mod_main.o .libs/e_int_config_wallpaper.o .libs/e_int_config_wallpaper_gradient.o .libs/e_int_config_wallpaper_import.o .libs/e_int_config_wallpaper_web.o   -L/opt/e17/lib -L//lib -L/usr/X11R6/lib -L/usr/lib /opt/e17/lib/libecore_ipc.so -L/lib /opt/e17/lib/libefreet_mime.so /opt/e17/lib/libefreet.so /opt/e17/lib/libehal.so /opt/e17/lib/libedbus.so -ldbus-1 /opt/e17/lib/libecore_imf_evas.so /opt/e17/lib/libecore_imf.so /usr/lib/libexchange.so -lecore_fb /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_con.so -lssl -lcrypto /opt/e17/lib/libedje.so /usr/lib/libxml2.so /opt/e17/lib/libecore_x.so -lXcursor -lXdamage -lXcomposite -lXfixes -lXinerama -lXrandr -lXrender -lXtst -lX11 -lXext /opt/e17/lib/libecore_input.so /opt/e17/lib/libecore_txt.so /usr/lib/libcurl.so /opt/e17/lib/libembryo.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libevas.so /usr/lib/libfreetype.so -lfontconfig -lpthread /opt/e17/lib/libeet.so /usr/lib/libjpeg.so /opt/e17/lib/libecore.so /usr/lib/libgnutls.so /usr/lib/libtasn1.so -lz /lib/libgcrypt.so /opt/e17/lib/libeina.so -lrt -lm -ldl -lpam    -Wl,-soname -Wl,module.so -o .libs/module.so
/usr/bin/ld: cannot find -lecore_fb
collect2: ld returned 1 exit status
make[4]: *** [module.la] Error 1
make[4]: Leaving directory `/var/cache/e17_src/e/src/modules/conf_wallpaper'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/var/cache/e17_src/e/src/modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/e'
make: *** [all] Error 2
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/e.log'!
```

---

### Post by Hendershot on 2009-05-03
[LEFT]This is awesome!
[/LEFT]

---

### Post by dros74 on 2009-05-04
Oh well, I still don´t know what that error was about but I managed to install it with the original script:

[http://omicron.homeip.net/projects/#easy_e17.sh](http://omicron.homeip.net/projects/#easy_e17.sh)

Now, the challenge is to get [ecomorph]("http://code.google.com/p/itask-module/wiki/Stuff"), the OpenGL compositing manager, working...

I am failing to build the module...
Did someone try to do this?

---

### Post by farmerf on 2009-05-08
Hi guys,

I'm installing e17 on my system and so far had it pretty easy. It just worked on Sabayon 4.1 and Ubuntu 9.4. But now i'm installing it on my laptop running xubuntu 9.4 and it doesn't work... Not sure if there are differences in the standard compile settings between ubuntu and xubuntu but might also be a change in the e17 scrip/sources... Any clue how to fix this:

```
- deskshow ................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.4.2-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
Makefile.am:38: `%'-style pattern rules are a GNU make extension
checking build system type... configure: error: cannot guess build type; you must specify one
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/deskshow.log'!


```thnx in advance.

Ps. '/tmp/easy_e17/install_logs/deskshow.log' shows the exact same message.

---

### Post by Tux Aubrey on 2009-05-09
> I'm installing e17 on my system and so far had it pretty easy. It just worked on Sabayon 4.1 and Ubuntu 9.4. But now i'm installing it on my laptop running xubuntu 9.4 and it doesn't work... Not sure if there are differences in the standard compile settings between ubuntu and xubuntu but might also be a change in the e17 scrip/sources... Any clue how to fix this:

I can't be sure, but that could just be a problem with a bad revision of deskshow code.  Try:

```
 sudo easy_e17.sh --only=deskshow
```

and see if it recurs.

If it doesn't, you should then be able to complete the install with

```
 sudo easy_e17.sh -i
```

I've not had any issues between Ubuntu and Xubuntu with 9.04.  I'm assuming here you are using the version of the script in the cafelinux e17_svn package - and not the original one from the e17 site.

---

### Post by Hendershot on 2009-05-09
I've been using e17 in jaunty for a while now, and every time I use the synaptic package manager I get a message saying I don't have permission to make any changes. 
How can I make it so I have full permission in the e17 shell?

---

### Post by Tux Aubrey on 2009-05-09
> **Hendershot said:**
> I've been using e17 in jaunty for a while now, and every time I use the synaptic package manager I get a message saying I don't have permission to make any changes. 
How can I make it so I have full permission in the e17 shell?

When you open synaptic (from either the menu item or from a launcher icon), right-click on the title bar and select "Edit Icon" - then, in the second box ("Executable"), just add "gksudo" before "synaptic".  That will change the .desktop file for synaptic and you will be asked for your password before it opens.

---

### Post by Hendershot on 2009-05-09
thanks much!

---

### Post by farmerf on 2009-05-10
> **Tux Aubrey said:**
> I can't be sure, but that could just be a problem with a bad revision of deskshow code. Try: 
 
```
 sudo easy_e17.sh --only=deskshow
```and see if it recurs. 
 
If it doesn't, you should then be able to complete the install with 
 
```
 sudo easy_e17.sh -i
```I've not had any issues between Ubuntu and Xubuntu with 9.04. I'm assuming here you are using the version of the script in the cafelinux e17_svn package - and not the original one from the e17 site. 
 
 
Well you are right about the problem being with deskshow, if I do the deskshow only the problem occurs again. Tried the -i anyway (source revision 40580)  but still the same problem.
 
As for the script, I follow the instructions at the start of this thread and installed with apt-get install e17-svn . After this I have the easy_e17.sh script in /usr/bin/ and the script itself says tat its the patched version for ozos (version1.2.4.2-ozos).  
 
After the error if I try to apt-get e17 again I get the message that its already installed so I do a remove --purge on e17. Then if i install again I noticed that it does not download the source again and the error is still there. 

Perhaps I should clean out the source files and re download them? or get another revision for the time being?  I assume it is possible to tell apt-get to get a specific version or am i wrong there?

---

### Post by Tux Aubrey on 2009-05-10
> **farmerf said:**
> Well you are right about the problem being with deskshow, if I do the deskshow only the problem occurs again. Tried the -i anyway (source revision 40580)  but still the same problem.
 
As for the script, I follow the instructions at the start of this thread and installed with apt-get install e17-svn . After this I have the easy_e17.sh script in /usr/bin/ and the script itself says tat its the patched version for ozos (version1.2.4.2-ozos).  
 
After the error if I try to apt-get e17 again I get the message that its already installed so I do a remove --purge on e17. Then if i install again I noticed that it does not download the source again and the error is still there. 

Perhaps I should clean out the source files and re download them? or get another revision for the time being?  I assume it is possible to tell apt-get to get a specific version or am i wrong there?

Ahhh!  Mixing e17 from Ubuntu repos (with apt-get install) and via the e17_svn script is not possible and will only lead to tears before bedtime.  The versions are now so far apart (4 years +) that they have virtually nothing in common except the names of their config files.  

That doesn't actually explain the deskshow problem, but I'd predict that e17 won't run if there is any trace of the repo version on your system.  I suggest a complete uninstall and purge and then "sudo easy_e17.sh -i".  Use Synaptic to do a complete removal of the repo version.

This is a bit weird because I have done "easy_e17.sh --only=deskshow" on 
several installs now (Ubuntu and Xubuntu) and don't get errors.

If this fails, I would suggest opening the file /etc/easy_e17.conf (as root) and adding "deskshow" to the list of apps to be skipped in the install - it is not actualy required anyway.

Hope this helps.

---

### Post by farmerf on 2009-05-11
The most incredible thing happened. It worked... Not quite sure what the problem was or how I fixed it but I did a purge, deleted the sources in /var/cache and then installed e17 by going into synaptic and selecting e17_svn. Not sure why it worked this time... 

Thanks for the help.

---

### Post by Tux Aubrey on 2009-05-11
> **farmerf said:**
> The most incredible thing happened. It worked... Not quite sure what the problem was or how I fixed it but I did a purge, deleted the sources in /var/cache and then installed e17 by going into synaptic and selecting e17_svn. Not sure why it worked this time... 

Thanks for the help.

phew.  :guitar:

Enlightenment is a mystery sometimes.

---

### Post by c.b.simas on 2009-05-11
--

---

### Post by c.b.simas on 2009-05-11
I encountered a problem with installing via the first posts instructions (now that I'm looking at recent posts it seems like there is the latest version in synaptic which I hadn't seen before :-/). It never got past the installation section where it was trying to download eina so I tried to start it over but then it told me this: (see second attachment). I've tried some random stuff but keep getting the same thing. I try to open Synaptic Package Manager and I get this: (see first attachment). I follow what that message tells me to do and I get the same screen as before (attachment #2).

Since trying to run svn cleanup on the file and being rejected I've tried to delete it manually by going to that location in the file browser but it wont let me delete it. How can I delete it so that I can start from scratch with Synaptic?

Thanks in advance!

---

### Post by Tux Aubrey on 2009-05-11
> **c.b.simas said:**
> I encountered a problem with installing via the first posts instructions (now that I'm looking at recent posts it seems like there is the latest version in synaptic which I hadn't seen before :-/). It never got past the installation section where it was trying to download eina so I tried to start it over but then it told me this: (see second attachment). I've tried some random stuff but keep getting the same thing. I try to open Synaptic Package Manager and I get this: (see first attachment). I follow what that message tells me to do and I get the same screen as before (attachment #2).

Since trying to run svn cleanup on the file and being rejected I've tried to delete it manually by going to that location in the file browser but it wont let me delete it. How can I delete it so that I can start from scratch with Synaptic?

Thanks in advance!

This looks like a failed initial install - probably interupted - but it does look like you have e17_svn installed OK.

You could try this:

Firstly, do as the dpkg error message suggests:

```
sudo dpkg --configure -a
```

(that will fix the apt-get/synaptic cache problem that happens if an update or install is interupted)

Then get rid of the e17 source code (which is now locked and possibly incomplete anyway)

```
sudo rm -rf /var/cache/e17_src
```

Then do the full install again:

```
sudo easy_e17.sh -i
```

At this point, you could probably get a coffee or visit a relative interstate while the install happens (hopefully without errors).  At the end you will get the funny message about the incredible thing that just happened and not to blame Rasterman if it didn't work. :)

---

### Post by c.b.simas on 2009-05-11
I've tried what you said. The "sudo dpkg --configure -a" did not work. It told me "dpkg: status database area is locked by another process". I have no othe rprocesses running except some simple apps. Any ideas about that?

Next, when I tried the other two commands you gave me, the first worked and the second got me past downloading the eina source but gave the the same "svn: Working copy '/var/cache/e17_src/eet' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)" when it started to download eet source.

Is there a way I can cancel everything I've done with e17 to this point and start over with Synaptic? Any recommendations?
 [EDIT]
AAIE!  I have a ghost in my machine! I looked up the e17_src folder in my file browser, removed again it with the command that you gave me and before my eyes *pop* it reappears! This is maybe a manifestation of my problem with the database being locked by another process?

---

### Post by Tux Aubrey on 2009-05-12
> **c.b.simas said:**
> I've tried what you said. The "sudo dpkg --configure -a" did not work. It told me "dpkg: status database area is locked by another process". I have no othe rprocesses running except some simple apps. Any ideas about that?

Next, when I tried the other two commands you gave me, the first worked and the second got me past downloading the eina source but gave the the same "svn: Working copy '/var/cache/e17_src/eet' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)" when it started to download eet source.

Is there a way I can cancel everything I've done with e17 to this point and start over with Synaptic? Any recommendations?
 [EDIT]
AAIE!  I have a ghost in my machine! I looked up the e17_src folder in my file browser, removed again it with the command that you gave me and before my eyes *pop* it reappears! This is maybe a manifestation of my problem with the database being locked by another process?

This is all VERY STRANGE [SIZE="1"](TM)[/SIZE].  There is definitely a ghost (or a daemon) involved somewhere.

Try "sudo dpkg --configure -a" after a reboot.  Maybe apt or update manager is hanging around in the background.

For the /var/cache/e17_src issue, maybe if you open your filemanager as root (eg. "gksudo nautilus") you can "visually" delete it.  You could also delete anything in /opt/e17  - where the compiled programs live -and the ~/.e17 directory (personal settings files) - just to be absolutely sure.  

In synaptic, you should be able to reinstall e17_svn (but I doubt there's a problem there as it is obviously _trying_ to work).  Just check that there are no other packages with e17 in their name installed (see above posts for problems mixing e17_svn with the Ubuntu repo version of e17).

Also, just check that cvs is installed too (as per the original post here).  For some reason it is still required for one e17 package (it really shouldn't be and that's why we haven't included in e17_svn).

---

### Post by c.b.simas on 2009-05-12
> **Tux Aubrey said:**
> This is all VERY STRANGE [SIZE=1](TM)[/SIZE].  There is definitely a ghost (or a daemon) involved somewhere.

Try "sudo dpkg --configure -a" after a reboot.  Maybe apt or update manager is hanging around in the background.

For the /var/cache/e17_src issue, maybe if you open your filemanager as root (eg. "gksudo nautilus") you can "visually" delete it.  You could also delete anything in /opt/e17  - where the compiled programs live -and the ~/.e17 directory (personal settings files) - just to be absolutely sure.  

In synaptic, you should be able to reinstall e17_svn (but I doubt there's a problem there as it is obviously _trying_ to work).  Just check that there are no other packages with e17 in their name installed (see above posts for problems mixing e17_svn with the Ubuntu repo version of e17).

Also, just check that cvs is installed too (as per the original post here).  For some reason it is still required for one e17 package (it really shouldn't be and that's why we haven't included in e17_svn).


Alright. So I tried what you said again. Restarted and "sudo dpkg --configure -a". Once again it failed and kept retrying for YEARS of my life so I closed the terminal (is this a silly thing to do?). I tried to open Synaptic and of course it didn't open because another process was running.

So I did the other things you said, restarted, tried to open Synaptic and of course it still wanted me to "sudo dpkg --configure -a" so I tried it again and as it was going through the same "Source checkout/update" section of the e_17 installation it gave me "svn: REPORT of '/svn/e/!svn/vcc/default': Could not read response body: connection was closed by server (http://svn.enlightenment.org" while it was trying to d/l eina source. I think my internet connection went haywire at that time.

After that first problem things have been good. The process is like 15 downloads later (currently downloading e source).

So, I'll let this finish and then pick up on your above mentioned instructions. I'll repost to give an update if I have a problem or it completes flawlessly.

Thanks!

[EDIT]
OK, so it's been trying to download e source for the past hour or so. Is this normal? Just leave it alone?

[EDIT]
Well, I got the same "svn: REPORT of '/svn/e/!svn/vcc/default': Could not read response body: connection timed out (http://svn.enlightenment.org)" as mentioned above for the download of e source. Currently the cursor is just blinking with no explanation of what is going on at this time. :-/

---

### Post by c.b.simas on 2009-05-12
The same "svn: REPORT of '/svn/e/!svn/vcc/default': Could not read response body: connection timed out (http://svn.enlightenment.org)" showed up yet again after the attempted download of "e source" and the cursor is just blinking. What should I do? (see attachment)

---

### Post by c.b.simas on 2009-05-12
OK, so I "sudo dpkg --configure -a" finally worked.

Now my question is:
1) Is it a silly idea to close the terminal while a process is running like  I did when I thought it wasn't working?
2) What is the difference between Ubuntu's repos and Synaptic Package Manager? Is Synaptic for all third-party installations while Ubuntu repos are strictly their sanctioned programs under add/remove programs?
3) Could you give me a link to a set of current instructions for installing e17_svn? I have looked and searched through this thread but I get lost among everything...

---

### Post by Tux Aubrey on 2009-05-13
> **c.b.simas said:**
> OK, so I "sudo dpkg --configure -a" finally worked.

Now my question is:
1) Is it a silly idea to close the terminal while a process is running like  I did when I thought it wasn't working?...

If it is genuinely frozen or crashed, there's not much else you can do. You could always open another terminal and use "top" to tell you what is actally running.  In this case, you were probably caught unawares because running "sudo apt-get install e17_svn" will open another terminal that runs the script to download and install e17 from the source code.  That takes a while (!) and the original terminal can appear to "hang" while the script runs.

> 2) What is the difference between Ubuntu's repos and Synaptic Package Manager? Is Synaptic for all third-party installations while Ubuntu repos are strictly their sanctioned programs under add/remove programs?

Ubuntu's repos are those servers enabled by default when you do a fresh install.  They are hosted by Canonical and are generally considered "safe" and quite comprehensive.  They are all listed (as urls) in the file /etc/apt/sources.list.  Synaptic, Add/Remove and apt (and aptitude) all use the same list of repos.  They are just different front-ends for the package manager (which is dpkg).

e17_svn is not in any of the Ubuntu repos.  It is a genuine "Third Party" contribution. It is currently hosted by cafelinux.org (just a motely bunch of e-tards).  In the instructions (post #1), you are told how to add this repo to sources.list - which means that e17_svn will be available to apt and Synaptic _as if_ it was actually in the Ubuntu repos.

> 3) Could you give me a link to a set of current instructions for installing e17_svn? I have looked and searched through this thread but I get lost among everything....


I'll reproduce the important parts here:


**INSTALLATION**

Add the following repos to your /etc/apt/sources.list:

*deb [http://cafelinux.org/Downloads/oz-os](http://cafelinux.org/Downloads/oz-os) tinwoodman main  *

To do it automatically, copy+paste the following to a command line:

```
sudo sh -c "echo 'deb http://cafelinux.org/Downloads/oz-os tinwoodman main' >> /etc/apt/sources.list"
```

and add the authenticated key with:

```
wget -q http://cafelinux.org/Downloads/oz-os/key.asc -O- | sudo apt-key add -
```

Update the repos:

```
sudo apt-get update
```

EXTRA STEP:
Due to an annoying dependence left to etk package it's still required to have cvs installed (although it not use CVS anymore):

```
sudo apt-get install cvs
```

Install e17 it with:

```
sudo apt-get install e17-svn
```

And thats all.


If you simply cut and paste the CODE lines above into a terminal (and let them run :) ) you should be able to log into an "Enlightenment" session next time you startup.  

There's a slightly different "How-To" [here]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os") - but it covers additional stuff you can add to the basic install (the "OzOS" desktop, which is in yet another cafelinux.org repo) but which you may not need or want right now.

I have also done a series of how-tos that are more generally about using (and playing with) e17 features that are not well documented elsewhere.  The index page is [here]("http://cafelinux.org/OzOs/content/how-index").

Good Luck!

---

### Post by c.b.simas on 2009-05-13
> **Tux Aubrey said:**
> 

There's a slightly different "How-To" [here]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os") - but it covers additional stuff you can add to the basic install (the "OzOS" desktop, which is in yet another cafelinux.org repo) but which you may not need or want right now.

I have also done a series of how-tos that are more generally about using (and playing with) e17 features that are not well documented elsewhere.  The index page is [here]("http://cafelinux.org/OzOs/content/how-index").

Good Luck!

Thank you for all your helpful advice. It's in the process of downloading sources and things are going flawlessly so far.

I have another question for you (if forum manners shun me asking questions that are more general informational, just inform me): what is the difference between installing e17_svn and installing OpenGEU 8.10? I think that e17 just changes the GUI (the appearance of everything) but OpenGEU would not only change the appearance but would change the functionality, the way the system works, right? Is it a completely different OS?

Thanks again.

Conrad

---

### Post by Tux Aubrey on 2009-05-13
> **c.b.simas said:**
> Thank you for all your helpful advice. It's in the process of downloading sources and things are going flawlessly so far.

I have another question for you (if forum manners shun me asking questions that are more general informational, just inform me): what is the difference between installing e17_svn and installing OpenGEU 8.10? I think that e17 just changes the GUI (the appearance of everything) but OpenGEU would not only change the appearance but would change the functionality, the way the system works, right? Is it a completely different OS?

Thanks again.

Conrad

That's about right, Conrad.

OpenGeu is an Ubuntu-based distro that uses a precompiled e17 desktop (ie. a .deb package).  e17_svn installs JUST e17 directly from the developers source repository ("svn" is the version control program they use to track changes).  All you get is the e17 environment to put over the top of whatever you already have installed.

e17 code is only rarely "frozen" and packaged as a .deb for "normal" use.  e17_svn (which is just a script based on easy_e17.sh - a script one of the e17 developers made to automate their own downloading) was developed for those of us who like e17 but find the perpetual "alpha" development cycle and the long times between updates to be a bit frustrating.  

Having said that, there _was_ a recent freeze and a new .deb package will be available soon.  Hopefully, OpenGeu and other experimental distros will adopt it quickly (although I doubt that a simple apt-get update will suffice because it has been a long time since the last one and so much has changed)

Getting any package as source code has pluses and minuses for the user.  You get the latest code and some great (if undocumented) features that .deb users may have to wait years (literally) for.  On the other hand, breakage is more likely if, like me, you get obsessive about updating and the fixes are a little more difficult.

If you ever want to get on the update rollercoaster (or stike a particular problem with e17), check out the OzOS forum link in my sig.

The OzOS packages (which we periodically package as a standalone iso distro based on Xubuntu) include a few extra tools to make maintenance a bit easier - like backup and restore of e17.  We (the cafelinux e-tards) also have a notification system that can warn users of "bad code days".  It isn't perfect but I think it has saved a few people some heartache.

I'd say that most people who use e17 via the e17_svn package should probably just leave it alone if they get a good install.  Current code (I'm updating to revision 40614 as I type this) is pretty good and it is already well ahead of the frozen version (revision 40284) that will eventually come out as a .deb package.

By the way - I really like OpenGeu and would recommend it to anyone who wants a simple way to test out an e17 desktop.  e17_svn (and OzOS) are a little more challenging for new users but I use them exclusively on all my setups now. 

One day, e17 will take over the world - it will be on mobile phones, netbooks, desktops and anything else with a chip and LCD screen - but until then we have to make do.

:popcorn:

---

### Post by c.b.simas on 2009-05-13
Thanks again for the help.

I installed OpenGEU but I can't say I was pleased. Maybe I just got overloaded with the overloaded menus and seemingly poor configuration program GUIs. Maybe OpenGEU is just for competent terminal users at this time?

---

### Post by Tux Aubrey on 2009-05-14
> **c.b.simas said:**
> Thanks again for the help.

I installed OpenGEU but I can't say I was pleased. Maybe I just got overloaded with the overloaded menus and seemingly poor configuration program GUIs. Maybe OpenGEU is just for competent terminal users at this time?

If you have e17 from the svn running, you will find a lot of differences in the configuration options available compared to distros using older .deb packages (like OpenGeu or eLive).  There has been a lot of work done since those .debs were last updated and, in my opinion, it has significantly improved the usability of e17 - but it is still quite different from other WMs and DEs to the point of requiring a mind shift to really get efficient with it.

The other thing that has happened is much better integration with GTK apps and greater adherence to the Freedesktop standards.  That means, for example, that you can use the Gnome menu editor (alacarte) to fix up (most) e17 menus and there is now a working system tray available as a module/gadget.  

There are still a few things that suck big time.  For example, the native e17 filemanager (efm) is still awful (I use Thunar or pcmanfm) and the network app is "less than fully featured" (try WICD if you want a good wireless app).

---

### Post by pgmario on 2009-05-18
Hey, thanks for the how-to. Unfortunately, I keep getting the following error:

```
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ ok          
- etk_extra .................. ok          
- ewl ........................ ok          
- exml ....................... SKIPPED
- enhance .................... SKIPPED
- e_dbus ..................... ok          
- e .......................... ok          
- entrance ................... SKIPPED
- edje_editor ................ SKIPPED
- elicit ..................... SKIPPED
- elitaire ................... SKIPPED
- enna ....................... ok          
- enthrall ................... SKIPPED
- emphasis ................... SKIPPED
- empower .................... SKIPPED
- emprint .................... ok          
- ephoto ..................... SKIPPED
- estickies .................. SKIPPED
- exhibit .................... SKIPPED
- expedite ................... SKIPPED
- exquisite .................. SKIPPED
- extrackt ................... SKIPPED
- eyesight ................... NOT FOUND
- e_phys ..................... SKIPPED
- rage ....................... SKIPPED
- alarm ...................... ok          
- bling ...................... ok          
- calendar ................... ok          
- cpu ........................ ok          
- deskshow ................... ok          
- diskio ..................... ok          
- drawer ..................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EPSILON... yes
checking for E... yes
checking for EDJE... yes
checking Which edje_cc to use... /opt/e17/bin/edje_cc
checking for XPIXMAP... configure: error: Package requirements (esmart_xpixmap) were not met:

No package 'esmart_xpixmap' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XPIXMAP_CFLAGS
and XPIXMAP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```Any help would be appreciated! :D

---

### Post by Tux Aubrey on 2009-05-18
> Hey, thanks for the how-to. Unfortunately, I keep getting the following error:

Code:

- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... SKIPPED
- emotion .................... SKIPPED
- etk ........................ ok          
- etk_extra .................. ok          
- ewl ........................ ok          
- exml ....................... SKIPPED
- enhance .................... SKIPPED
- e_dbus ..................... ok          
- e .......................... ok          
- entrance ................... SKIPPED
- edje_editor ................ SKIPPED
- elicit ..................... SKIPPED
- elitaire ................... SKIPPED
- enna ....................... ok          
- enthrall ................... SKIPPED
- emphasis ................... SKIPPED
- empower .................... SKIPPED
- emprint .................... ok          
- ephoto ..................... SKIPPED
- estickies .................. SKIPPED
- exhibit .................... SKIPPED
- expedite ................... SKIPPED
- exquisite .................. SKIPPED
- extrackt ................... SKIPPED
- eyesight ................... NOT FOUND
- e_phys ..................... SKIPPED
- rage ....................... SKIPPED
- alarm ...................... ok          
- bling ...................... ok          
- calendar ................... ok          
- cpu ........................ ok          
- deskshow ................... ok          
- diskio ..................... ok          
- drawer ..................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for msgmerge... /usr/bin/msgmerge
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... done
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EPSILON... yes
checking for E... yes
checking for EDJE... yes
checking Which edje_cc to use... /opt/e17/bin/edje_cc
checking for XPIXMAP... configure: error: Package requirements (esmart_xpixmap) were not met:

No package 'esmart_xpixmap' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables XPIXMAP_CFLAGS
and XPIXMAP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

Any help would be appreciated! 

hi pgmario

Yep.  This is a brand new one!  Coders! ;)

The "drawer" module is suddenly now dependent on "esmart" which is "skipped" in the e17_svn standard install.  Nobody ever really needed it before!

The fix is easy.

Open the file /etc/easy_e17.conf in a text editor as root:

eg

```
gksudo gedit /etc/easy_e17.conf
``` 
(use whatever is your standard text editor)

It is just a single (long) line of application names separated by commas.

Delete "esmart," and save the file.

then run:

```
sudo easy_e17.sh -u
```

The install should now go through.

(Note: we'll fix this with an update to e17_svn very soon, but this fix should keep everything happening in the meantime)

---

### Post by pgmario on 2009-05-19
Thanks Aubrey! Works fine now.

---

### Post by linuxchuck on 2009-05-19
This is more for my own reference since I'm regularly curious about the function of some of the skipped modules, apps, and gadgets during the compilation process of e17.  However, for the sake of hopefully helping some of the others out there who would also like to know, I've compiled a list of them.

Please keep in mind that entries the following list may based on any of the following infomation sources, and as a result should be considered "questionable" at best:
[LIST]
[*]Included README files
[*]Author websites
[*]Source code comments
[*]3rd party references
[*]SWAG (Scientific Wild A$$ Guesses)
[*]Consultations with the Internet Oracle
[/LIST]

Several of these items may not show up as "ok", "SKIPPED", or on any other list, and may or may not even be included in e17 anymore, but are listed here for historical purposes.

They are also in no order whatsoever...

```
**_e_dbus_** is the start of some basic convenience
 wrappers around dbus to ease integrating dbus with EFL based
 applications.

**_eina_** is a data types library for use with lists, hashes,
 et-cetera.

**_Eet_** is a tiny library designed to write an arbitary set of
 chunks of data to a file and optionally compress each chunk (very much
 like a zip file) and allow fast random-access reading of the file later
 on. It does not do zip as a zip itself has more complexity than is
 needed, and it was much simpler to implement this once here.

**_Evas_** is a clean display canvas API for several target
 display systems that can draw anti-aliased text, smooth super and
 sub-sampled scaled images, alpha-blend objects much and more.

**_Ecore_** is the event/X abstraction layer that makes doing
 selections, Xdnd, general X stuff, event loops, timeouts and idle
 handlers fast, optimized, and convenient. It's a separate library so
 anyone can make use of the work put into Ecore to make this job easy for
 applications.

**_efreet_** is an implementation of several specifications from
 freedesktop.org intended for use in Enlightenment DR17 (e17) and other
 applications using the Enlightenment Foundation Libraries (EFL).
 Currently, the following specifications are included:
  o Base Directory
  o Desktop Entry
  o Icon Theme
  o Menu

**_Embryo_** is primarily a shared library that gives you an API
 to load and control interpreted programs compiled into an abstract
 machine bytecode that it understands.  This abstract (or virtual)
 machine is similar to a real machine with a CPU, but it is emulated in
 software.

**_Edje_** is graphical layout and animation library for animated
 resizable, compressed and scalable themes.

**_Epsilon_** is a small, display independent, and quick
 thumbnailing library.

**_esmart_** is a collection of evas smart objects.

**_Emotion_** is a video and media object library designed to
 interface with Evas and Ecore to provide autonomous "video" and "audio"
 objects that can be moved, resized and positioned like any normal
 object, but instead they can play video and audio and can be controlled
 from a high-level control API allowing the programmer to quickly piece
 together a multi-media system with minimal work.

**_Etk_** is a toolkit based on the EFL.

**_Etk_extra_** is a collection of extra widgets, models, or
 anything that doesnt fit directly in the Etk source tree. Every
 component is in the form of a shared object that can be linked against
 by your application.

**_edje_editor_** is a visual editor for edje files.

**_Elicit_** is a screen zoomer / color picker written with the
 Enlightenment Foundation Libraries.

**_Elitaire_** is a game for Enlightenment like Solitaire.

**_alarm_** - Sets reminders and timer.  (Replaces eveil.)

**_bling_** - EFLized Composite Manager for E17. (Not for users
 right now).

**_calendar_** - A module to show the current day.

**_cpu_** - A module to monitor cpu load.  (Will be replaced by
 something better.)

**_deskshow_** - A module to iconify/uniconify all current
 windows to show the desktop.  This is probably obsolete, the
 functionality is now in E.

**_diskio_** - visualize disk i/o.

**_echo_** - A module to replace the broken 'mixer' module for
 E17.

**_emu_** - Experimental generic scriptable module for E17.

**_exalt-client_** - A frontend module for exalt network manager.

**_flame_** - A module to display flames on the desktop.

**_forecasts_** - A module to display the current condition and
 forecasts.

**_language_** - A module to control active keyboard/keyboard
 layout/layout variant.

**_mail_** - A module to periodically check for new email.

**_mem_** - A module to monitor memory and swap usage.  (Will be
 replaced by something better.)

**_mixer_** - A module to control volume for some mixers.  (Will
 be replaced by something better.)

**_moon_** - A module to display moon phase information.

**_mpdule_** - A module to display what's playing in MPD.

**_net_** - A module to monitor traffic on a network device.

**_news_** - A module to display rss feeds.

**_penguins_** - A module to display fancy penguins on your
 desktop.

**_photo_** - A module to display pictures on the desktop.

**_places_** - manage volumes attached to the system.

**_rain_** - A module to display rain on the desktop.

**_screenshot_** - A module to take screenshots, utilizing scrot
 or import.

**_slideshow_** - A module to cycle desktop backgrounds.

**_snow_** - A module to display snow on the desktop.

**_taskbar_** - A taskbar module.  (Will be replaced by something
 better.)

**_tclock_** - A module to display a digital clock on the
 desktop.  (Will be replaced by something better.)

**_uptime_** - A module to monitor computer uptime.

**_weather_** - A module to display a weather forecast.

**_winselector_** - A module to show menu-based access to open
 windows.

**_wlan_** - A module to monitor a wlan device.

**_Emphasis_** is a simple MPD (Music Player Daemon) client
 writen in C/Etk.

**_Empower_** - A graphical sudo tool based on the Enlightenment
 Foundation Libraries.

**_Emprint_** is a utility for taking screenshots of the entire
 screen, a specific window, or a specific region.

**_Enhance_** is a library that takes advantage of Glade's .glade
 XML files, EXML, and Etk to ease application GUI development and cut
 down on its time.

**_Entrance_** is a login/display manager for UNIX X11 displays.

**_Ephoto_** is an Image Viewer/Editor/Manipulator/Slideshow
 creator.

**_Estickies_** is a sticky notes application that uses Etk.

**_Evas_** is a clean display canvas API for several target
 display systems that can draw anti-aliased text, smooth super and
 sub-sampled scaled images, alpha-blend objects much and more.

**_EWL_** is a toolkit for creating graphical user interfaces
 based on the Enlightenment Foundation Libraries.

**_Exhibit_** is an image viewer that uses Etk as its toolkit.
 Exhibit supports image previews for image types supported by Evas and
 allows for directory changing using a point and click interface or a
 text input box with tab autocompletion support.

**_Expedite_** is meant to be a detailed and comprehensive
 benchmark suite for Evas.

**_Exquisite_** is a psplash replacement that is very simple and
 uses EFL (Evas, Edje, Ecore etc.) for display - thus having immensely
 powerful theme abilities without needing any platform-specific compiled
 themes or modules. It is compatible with psplash with the same message
 commands (and more). The difference is that it requires libraries like
 evas, edje, ecore, eet and embryo. These also have loadable modules of
 their own - thus this isn't perfect for systems that can't have these
 libraries available and working at boot, but if you can, it's a lot more
 capable than other splash engines, while still running in the
 framebuffer.

**_Rage_** is a media center designed mostly for use on a
 television hooked up to your pc via a remote control.

**_EXML_** is an abstracted, generalized interface to an xml
 parser/writer, using ecore data structures and making things generally
 easy to get around in.

**_Enna_** is a software originally designed and created by
 Nicolas Aguirre. It consists of a nice UI based around Enlightenment E17
 librairies (Evas, Ecore …) and will be part of the latter one the time
 has come. Its purpose is to implement all the necessary features to act
 as a Media Center.

**_Enthrall_** is an application to take video captures from your
 screen.

**_Extrackt_** is an ETK based audio CD ripper and encoder tool.

**_Eyesight_** is a plugin-based file viewer application

```

---

### Post by Tux Aubrey on 2009-05-19
> **pgmario said:**
> Thanks Aubrey! Works fine now.

You're welcome!  This fix is relevant to anyone installing/updating e17 via e17_svn, easy_e17 or update_e17 (the OzOS script).

> e17 Modules, apps, and gadgets list....

Thanks for this, linuxchuck.  I've been meaning to compile a similar guide for almost a year!  If you don't mind, I'd like to use yours as the basis for a new web page at cafelinux.org - probably with some added comments on whether each package is absolutely required or why a package might be skipped (or avoided like the plague).

---

### Post by linuxchuck on 2009-05-19
> **Tux Aubrey said:**
> Thanks for this, linuxchuck.  I've been meaning to compile a similar guide for almost a year!  If you don't mind, I'd like to use yours as the basis for a new web page at cafelinux.org - probably with some added comments on whether each package is absolutely required or why a package might be skipped (or avoided like the plague).

Feel free.  It's not like it's my original content.  ;)

You're welcome to do with it as you please.  As I said, it's there so I would have an easy place to look up an "all in one place" list.  However, once you finish your page, I feel it will be much more valuable than this little list, and look forward to it.  Make sure and let us know when it's up and available.

---

### Post by pgmario on 2009-05-21
So, I've had some time to toy around with E17. I like what I see. It's fast and the default theme is beautiful (if you like minimalist themes). Configuration was very easy, no editing of any files whatsoever.
The only thing I don't like so far is the file-manager. Maybe I just have not found the correct settings, but it isn't capable of anything, except browsing your files, deleting, copying, etc. No creation of symlinks, no toolbar (or just an empty one), and sorting of files does not really work. Am I doing something terribly wrong? Any recommendations for an alternative (and how it could use the Enlightenment icon-theme)?
But let me emphasize this: I really like the environment! I have made it my default for now to check things out a little more. Nice work!

---

### Post by diconexiuni on 2009-05-21
thank for the info

---

### Post by Tux Aubrey on 2009-05-21
> **pgmario said:**
> So, I've had some time to toy around with E17. I like what I see. It's fast and the default theme is beautiful (if you like minimalist themes). Configuration was very easy, no editing of any files whatsoever.
The only thing I don't like so far is the file-manager. Maybe I just have not found the correct settings, but it isn't capable of anything, except browsing your files, deleting, copying, etc. No creation of symlinks, no toolbar (or just an empty one), and sorting of files does not really work. Am I doing something terribly wrong? Any recommendations for an alternative (and how it could use the Enlightenment icon-theme)?
But let me emphasize this: I really like the environment! I have made it my default for now to check things out a little more. Nice work!

I personally agree about the filemanager (efm).  I turn it off completely (unload the module) and use **Thunar** on most of my e17 installs. Apart from its retro look and lack of network browsing, it is a very capable fm.  The only problem I find is that the Ubuntu repo version of Thunar for Jaunty does a nasty little crash on closing.  Apparently (I haven't tried it yet), there is an updated version available from the Thunar svn that fixes this. 

Another alternative is **pcmanfm** (sudo apt-get install pcmanfm).  It is very similar in most ways to Thunar and does have tabbed browsing.  I want to like it a lot, but can't quite get used to a few of its menus.

Neither, IMO, is perfect (but your filemanager preference is such a personal thing!).  What I really want is a Linux port of Windows Explorer. ;)

---

### Post by VCoolio on 2009-05-21
> **pgmario said:**
> The only thing I don't like so far is the file-manager. [...] Any recommendations for an alternative?

If you installed e17 on top of ubuntu you may want to use nautilus, but use following command to prevent loading complete desktop (wallpaper etc):
nautilus --no-desktop /home/username
or whatever folder you want to start with. I like nautilus because of the scripts-options, and in general I'm used to it now, but it's a pity it has no embedded terminal.

---

### Post by originalsynthesis on 2009-05-24
has anyone used the easy e17 repo lately? I tried to download it recently and as it goes through the Source checkout/update process, it borks out. The process looks like this:

```
Checking e source ... svn: PROPFIND request failed on '/svn/e/trunk/e'
svn: PROPFIND of '/svn/e/trunk/e': Could not resolve hostname 'svn.enlightenment.org': Host not found (http://enlightenment.org)
```

it's permanently stuck in this loop, and I dont know how to get out of it, except just to close terminal. This, I find, screws up dpkg and wont let me use package manager or even apt-get. How do I get out of this loop? 

granted, I dont know if the repos have changed, at all since the last several months since i tried e17 last, so maybe that could be why it did this.

I was downloading from: [http://cafelinux.org/Downloads/oz-os/tinwoodman/Release.gpg](http://cafelinux.org/Downloads/oz-os/tinwoodman/Release.gpg)



edit: whoops! seems like c.b simas was dealing with this not too long ago. gonna go through that dialogue n see if that works. sorry!

---

### Post by originalsynthesis on 2009-05-24
ok, c.b simas's issue was nothing like what i've got after all. doing sudo dpkg --configure -a  just brings up the loop i described before. Hope this isn't too stupid of a problem, I've been slacking on my Linuxing lately:icon_frown:.

---

### Post by Tux Aubrey on 2009-05-24
Hi originalsynthesis

The e17 svn has been up and running fine lately.

**WILD GUESS :** Did you version upgrade your Ubuntu install since you last used easy_e17?


If so, you need to check /etc/apt/sources.list to make sure the ozos repo hasn't been commented out (#)

Your /etc/apt/sources.list should have a line that says:

```
deb http://cafelinux.org/Downloads/oz-os hungrytiger main
``` 

Then do a 

```
sudo apt-get update
sudo apt-get upgrade
```

and finally:

```
sudo easy_e17.sh -u
```

---

### Post by originalsynthesis on 2009-05-24
> WILD GUESS : Did you version upgrade your Ubuntu install since you last used easy_e17?

---nope. Still using the heron right now. My sources.list entry wasn't commented out, but it did read different from the one you gave. It used to be ```
...../oz-os tinwoodman main
``` right?

I changed my previous source entry to the one you gave. However, I cant do anything with apt-get because dpkg is tied up with the unfinished easy e17.sh i tried before.....the only thing I know to do for that is to do dpkg --configure -a, which prompts dpkg to try to continue the download.

This may also be overlapped by some basic networking issues i've been having, so my main question is... is there a way to tell dpkg to drop the easy_e17 download so that i can use apt?

---

### Post by VCoolio on 2009-05-24
dpkg --configure -a tries to fix broken packages, but in this case it's no use since it will try to do so by connecting to the unreachable. To fix apt try deleting the bin files in /var/cache/apt, that's where apt stores files before using them. Or move them to be safe: 
sudo mkdir /var/cache/apt/backup
sudo mv /var/cache/apt/*.bin /var/cache/apt/backup 
and remove the backup folder if all is well.

---

### Post by originalsynthesis on 2009-05-24
Alright, following Dcoolio's suggestion, I moved all the .bins from /var/cache/apt into a backup folder. When I tried dpkg --configure -a again, it still tried to continue easy_e17. It didn't get hung up where it had before, but rather it made its way through the sources update part of the installer and got stuck on this: 



```
Updated to revision 40823.



Checking etk source ... 

U    etk/debian/control

U    etk/po/LINGUAS

A    

etk/po/eo.po

svn: Failed to add file 'etk/po/Makefile.in.in': object of the same name 

already exists
```



I think I then made a medium sized mistake, by trying to do apt-get update after the dpkg --config. Doing apt-get update outputs this:


```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

And after this, dpkg --configure -a cant even pick up from where it left off because it says "status database area is locked by another process."---i.e. apt-get.

As far as I can tell, I've got to get one of these processes to finish, or at least to cancel them out properly so they stop locking each other up. Any way I can do that?

---

### Post by digitalbrain on 2009-05-26
@originalsynthesis

Delete that file: etk/po/Makefile.in.in  (or move it to another place so that if anything goes wrong, you can put it again into the same folder). Then try updating again. It should update properly. 

And about the second error you get: Is synaptic open at the same time? Close synaptic (or another package manager) and then try again. I hope these help you.

---

### Post by digitalbrain on 2009-05-26
And now, I have a question. After updating, E17 does not work properly. As far as I see, there are developments in E17 (thanks to OzOs  team !!) but every time I update, I have problems. Then I restore an old configuration and keep on using it. Here are the problems after update:

1. A lot of the modules don't work. Only a few work. The error I get is something like: "This module can't be found in the modules directory." And it asks "Would you like to unload this module?" 

2. Folder icons and menu change (I'm using A-ESky0 theme for file manager and cerium theme for menus). But they become different after update.

Help please.. Thanks

---

### Post by originalsynthesis on 2009-05-28
Thanks DB, I was thinking about doing that, just wanted someone else to say it first. Guess im over-cautious. 

> And about the second error you get: Is synaptic open at the same time? Close synaptic (or another package manager) and then try again. I hope these help you.

no, actually synaptic had been refusing to start up because of the broken e17 package(i think) in dpkg. I was kind of under the impression (i am a bit of a linux newb) that apt and synaptic all relied on dpkg to run properly. So it made sense to me that leaving dpkg tied up with an unfinished process would prevent any other download client that relied on it useless. Am I wrong? Anyway, e17 is downloading right now, so when it's done I'll see if apt and synaptic work again.

yep, all seems good again. Thanks for your help!

---

### Post by digitalbrain on 2009-05-29
Hey, you're welcome. :) It's good you solved your problem.

---

### Post by digitalbrain on 2009-06-15
But I couldn't solve mine... It's been more than 2 weeks, but no reply... My message again:

After updating, E17 does not work properly. As far as I see, there are developments in E17 (thanks to OzOs team !!) but every time I update, I have problems. Then I restore an old configuration and keep on using it. Here are the problems after update:

1. A lot of the modules don't work. Only a few work. The error I get is something like: "This module can't be found in the modules directory." And it asks "Would you like to unload this module?"

2. Folder icons and menu change (I'm using A-ESky0 theme for file manager and cerium theme for menus). But they become different after update.

(I updated again recently, this time  I got a list of errors. So, I turned back to the old revision again:
My installation revision is: 40751
My local sources revision is: 40917)

Help please.. Thanks

---

### Post by Tux Aubrey on 2009-06-15
> **digitalbrain said:**
> But I couldn't solve mine... It's been more than 2 weeks, but no reply... My message again:

After updating, E17 does not work properly. As far as I see, there are developments in E17 (thanks to OzOs team !!) but every time I update, I have problems. Then I restore an old configuration and keep on using it. Here are the problems after update:

1. A lot of the modules don't work. Only a few work. The error I get is something like: "This module can't be found in the modules directory." And it asks "Would you like to unload this module?"

2. Folder icons and menu change (I'm using A-ESky0 theme for file manager and cerium theme for menus). But they become different after update.

(I updated again recently, this time  I got a list of errors. So, I turned back to the old revision again:
My installation revision is: 40751
My local sources revision is: 40917)

Help please.. Thanks

Apologies for not picking up on your continuing problems, digitalbrain.

Strangely, I had the "Module can't be found" error myself today - but I was only updating by a couple of revisions.

The solution, for me, was to use the easy_e17.sh script in "--only" mode and recompile those modules that were "broken".

First run a normal update.

If that goes through OK, then do:

> sudo easy_e17.sh --only=taskbar,places,screenshot,tclock,execwatch,iirk,mail

Add any others to the list or run easy_e17.sh --only with them separately - use commas but no spaces to separate the names.

You will then need to load the modules manually - or logout and in again.

Let me know if that works (if not, a reinstall is probably indicated!).

The corrupted menus and icons issue is a weird one that I also experience now and again after updates - but it disappears for me by restarting e (Enlightenment>Restart from the main menu).

If it is persistent, then it is probably a theme issue.  Several really great changes in recent code have not been compatible with some themes (mine included :( ).  Reverting to b_and_w (at least for menus, will generally fix it.  (and while I'm on THAT subject, the systray module - which is BRILLIANT imo - will only work properly with b_and_w)

---

### Post by bluemarbl on 2009-06-16
Thanks for the neat HOWTO.

I am trying this out on a fresh Ubuntu 9.04 on an amd64 machine. I cant seem to get ecore to compile. 

A quick search was futile, the GLIBC version is newer than whats expected? Has anyone else has success lately?


```


..

Checking ecore source ... At revision 41065.

..

- eina ....................... ok          
- eet ........................ ok          
- evas ....................... ok

...

make[3]: Entering directory `/var/cache/e17_src/ecore/src/bin'
gcc -DHAVE_CONFIG_H -I. -I../..  -I../../src/lib/ecore -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_config -DPACKAGE_BIN_DIR=\"/opt/e17/bin\" -DPACKAGE_LIB_DIR=\"/opt/e17/lib\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/ecore\" -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina -I/opt/e17/include -I/opt/e17/include/eina-0 -I/opt/e17/include/eina-0/eina   -I/opt/e17/include   -MT ecore_config.o -MD -MP -MF .deps/ecore_config.Tpo -c -o ecore_config.o ecore_config.c
mv -f .deps/ecore_config.Tpo .deps/ecore_config.Po
/bin/bash ../../libtool --tag=CC   --mode=link gcc    -L/opt/e17/lib -o ecore_config ecore_config.o ../../src/lib/ecore_config/libecore_config.la ../../src/lib/ecore_ipc/libecore_ipc.la ../../src/lib/ecore_con/libecore_con.la ../../src/lib/ecore/libecore.la 
libtool: link: gcc -o .libs/ecore_config ecore_config.o  -L/opt/e17/lib ../../src/lib/ecore_config/.libs/libecore_config.so /var/cache/e17_src/ecore/src/lib/ecore_ipc/.libs/libecore_ipc.so /opt/e17/lib/libevas.so /usr/lib/libfreetype.so /opt/e17/lib/libeet.so -lz /usr/lib/libjpeg.so -lfontconfig -lpthread ../../src/lib/ecore_ipc/.libs/libecore_ipc.so /var/cache/e17_src/ecore/src/lib/ecore_con/.libs/libecore_con.so ../../src/lib/ecore_con/.libs/libecore_con.so /var/cache/e17_src/ecore/src/lib/ecore/.libs/libecore.so -lssl -lcrypto /usr/lib/libcurl.so ../../src/lib/ecore/.libs/libecore.so /opt/e17/lib/libeina.so -lrt -ldl -lm
/usr/lib/libkrb5.so.3: undefined reference to `ns_name_uncompress@GLIBC_2.9'
/usr/lib/libkrb5.so.3: undefined reference to `ns_parserr@GLIBC_2.9'
/usr/lib/libkrb5.so.3: undefined reference to `ns_initparse@GLIBC_2.9'
collect2: ld returned 1 exit status
make[3]: *** [ecore_config] Error 1


```

---

### Post by digitalbrain on 2009-06-19
@Tux Aubrey 

I updated and got no errors. After update, only a few modules could not be loaded but no problem. Thank You for your reply.

---

### Post by Neo40 on 2009-06-19
I'm trying to install e17-svn, but I got this error:

...
...
...
downloading etk_extra source ...
svn: L'URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' n'existe pas
svn: L'URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' n'existe pas
svn: L'URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' n'existe pas
FAILED! Next attempt 4 in 10 seconds^Cdpkg*: erreur de traitement de e17-svn (--configure)*:


Do I need this file? If not, how can I disable it?
Thanks

---

### Post by ives on 2009-06-19
> **Neo40 said:**
> I'm trying to install e17-svn, but I got this error:

...
...
...
downloading etk_extra source ...
svn: L'URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' n'existe pas
svn: L'URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' n'existe pas
svn: L'URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' n'existe pas
FAILED! Next attempt 4 in 10 seconds^Cdpkg*: erreur de traitement de e17-svn (--configure)*:


Do I need this file? If not, how can I disable it?
Thanks

Same problem here! I have no idea why the developers removed etk_extra from trunk...

---

### Post by solitaire on 2009-06-19
I'm getting the same error
```

svn: URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' doesn't exist

```

any way around this?

---

### Post by VCoolio on 2009-06-19
[Here]("http://cafelinux.org/forum/index.php?topic=3.msg267#msg267") you can read that there have been developments in the svn version of enlightenment. The solution seems to be to delete certain folders from /var/cache/e17_src:```

cd /var/cache/e17_src
sudo rm -rf enhance emphasis etk_extra exhibit
and then redo the update
```

Just copypasting, credits go to Tux Aubrey.
Also you can try to skip the obsolete packages from the script: 
gksudo gedit /etc/easy_e17.conf
add ,enhance,emphasis,etk_extra,exhibit (without spaces) to the list of packages to skip.
If this happens on fresh install of e17-svn (which according to link above shouldn't) I don't know.

---

### Post by solitaire on 2009-06-19
Those 2 fixes only work if you are using the script.

For me when i use the .deb file, the easy_e17.conf file apparently ignored (the dir's are listed but they installer still looks for them!!!)


I decided to just use the script from [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/) insted of the deb file and see how that goes... ^_^

---

### Post by Neo40 on 2009-06-19
> **VCoolio said:**
> [Here]("http://cafelinux.org/forum/index.php?topic=3.msg267#msg267") you can read that there have been developments in the svn version of enlightenment. The solution seems to be to delete certain folders from /var/cache/e17_src:```

cd /var/cache/e17_src
sudo rm -rf enhance emphasis etk_extra exhibit
and then redo the update
```

Just copypasting, credits go to Tux Aubrey.
Also you can try to skip the obsolete packages from the script: 
gksudo gedit /etc/easy_e17.conf
add ,enhance,emphasis,etk_extra,exhibit (without spaces) to the list of packages to skip.
If this happens on fresh install of e17-svn (which according to link above shouldn't) I don't know.

I did that but its still looking for etk_extra

---

### Post by Tux Aubrey on 2009-06-20
Sorry for the delay in replying.

This is a response to those having trouble installing or updating e17 using e17-svn.

The script throws errors on several packages including etk-extras and enhance because these have been removed from the main trunk of the Enlightenment svn.

I have attached a version of the script easy_e17.sh as a tar.gz to replace the one used by e17-svn.
  
**FOR THOSE WHO HAVE INSTALLED e17-svn AND GOT A "doesn't exist" ERROR**

1. Un-archive the attached file and copy it to /usr/bin/ and make it executable.

2. Open your file manager with gksudo and navigate to /var/cache/e17_src

3. Delete the folders (if any of these exist):

enhance
emphasis
etk_extra
exhibit

(Note: steps 2 and 3 can be done from the terminal with two commands:
```

cd /var/cache/e17_src
```
and
```
sudo rm -rf enhance emphasis etk_extra exhibit
```

4. As a precaution, install the doxygen package (it seems to be now a dependency of e17)

```
sudo apt-get install doxygen
```

5. Run easy_e17 with the "-i" flag to update your source code and start installing again

```
sudo easy_e17.sh -i
```
[B]
FOR FIRST TIME USERS WHO HAVEN'T YET INSTALLED e17-svn[/B]

Follow the How-TO (first post here)

After adding the cafelnux repos and the key, enter (copy) this command:

```
touch $HOME/_skip_easy_e17_install
```

This will stop the easy_e17 script from running.

You should then:

1. Un-archive the attached file and copy it to /usr/bin/ and make it executable.

2. install the doxygen package (it seems to be now a dependency of e17)

```
sudo apt-get install doxygen
```

3. Run easy_e17 with the "-i" flag to download source code and start installing

```
sudo easy_e17.sh -i
```

FOR USERS WHO ARE GETTING ERRORS WITH enhance emphasis etk_extra exhibit WHEN UPDATING:

1. Delete the dead directories

```

cd /var/cache/e17_src
```

and

```
sudo rm -rf enhance emphasis etk_extra exhibit
```

2. As a precaution, install the doxygen package (it seems to be now a dependency of e17)

3. Run easy_e17 with the "-i" flag to update your source code and start installthe updated packages.

```
sudo easy_e17.sh -i
```


Now, that should all work with Jaunty, Intrepid etc - BUT Karmic is more difficult because of the gtklib dependency.  I'll work on that one (but in the meantime, there are some very nice fresh e17 binaries over at [http://packages.enlightenment.org/](http://packages.enlightenment.org/) you might like to try - use the "jaunty" repo and get e17 and the modules metapackage.  It works a treat and is only a few weeks behind the svn version right now. Karmic alpha plus e17 alpha is very cool!)

By way of explanation - there's lots happening in the e17 code base right now as the devs work towards a formal beta release. Deleting old and unmaintained packages is part of that process and I'm pretty sure this won't be last time it happens.  If you want to stay with e17-svn, stay tuned for further news.  Remember: "Evolution Kills"

---

### Post by solitaire on 2009-06-20
I'm getting the following error when trying to install e17 via the script...

```

- exalt ...................... make   : ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
'make install'. Change users with 'su' or 'sudo' appropriately.

-------------------------------------------------------------------------------
EASY_E17 1.2.4 CMD: make  -j 2
-------------------------------------------------------------------------------
Making all in src
config.status: creating src/config.h
config.status: src/config.h is unchanged
Making all in lib
  CC    libexalt.o
  CC    exalt_dns.o
  CC    exalt_regexp.o
  CC    exalt_ethernet.o
  CC    exalt_sys_conf.o
exalt_sys_conf.c: In function &#8216;_exalt_eth_save_edd_new&#8217;:
exalt_sys_conf.c:164: error: &#8216;evas_hash_foreach&#8217; undeclared (first use in this function)
exalt_sys_conf.c:164: error: (Each undeclared identifier is reported only once
exalt_sys_conf.c:164: error: for each function it appears in.)
exalt_sys_conf.c:165: error: &#8216;evas_hash_add&#8217; undeclared (first use in this function)
exalt_sys_conf.c:166: error: &#8216;evas_hash_free&#8217; undeclared (first use in this function)
make[3]: *** [exalt_sys_conf.lo] Error 1
make[3]: *** Waiting for unfinished jobs....
make[2]: *** [all-recursive] Error 1
make[1]: *** [all] Error 2
make: *** [all-recursive] Error 1
--------------------------------------------------------------------------------


```am I missing a dependency or something?

---

### Post by LeHomard on 2009-06-20
Exact same error here.

---

### Post by Tux Aubrey on 2009-06-20
For those with a problem with exalt - 

What script are you using?  exalt is skipped in the version in e17-svn.  I don't think it is a maintained or supported package and is certainly not necessary.

The list of skipped packages is in the file /etc/easy_e17.conf

Open it as root and add "exalt,exalt-client"

ie:

```
gksudo gedit /etc/easy_e17.conf
```

---

### Post by worldwithoutgurus on 2009-06-22
Exalt and Exalt-client are maintained and working.
Update svn.

---

### Post by Neo40 on 2009-06-22
Hi,

ok, so I have e17-svn working fine.;)
I'd to know if its possible to have a desktop like (elive, moono or opengeu, etc...) without to configure each gadgets or modules manually?..I know, I'm a lazy!
I thought something like copy a config file from a specific distro and paste it..?
How can I do it?
Thanks!

---

### Post by Tux Aubrey on 2009-06-22
> I'd to know if its possible to have a desktop like (elive, moono or opengeu, etc...) without to configure each gadgets or modules manually?..I know, I'm a lazy!
I thought something like copy a config file from a specific distro and paste it..?

Hmmm.  Nice idea, Neo40, and I have thought about doing something similar myself - basically packaging different e17 Profiles and offering them as pre-set desktops (after all, that's essentially what a distro is anyway).  It would actually be pretty easy to do _IF_ (and its a big IF) e17 was stable (as in the codebase didn't change so often).  

I would not attempt this with the current batch of distros as they are very different versions from the svn one and I suspect that important things will not work at all if ported over.  Wallpapers will port easily and many recent Themes will also be OK (mostly).

The GOOD NEWS is that the code base is "settling" and even the latest binaries are looking very neat and full of features that will allow this sort of tinkering to happen.

Just for reference, I wrote a series of  "How Tos" about e17 desktop tweaks and features ([here]("http://cafelinux.org/OzOs/content/how-index")) - but the screenshots have disappeared from that version.  I'm in the process of updating these guides.

User-generated Profiles are kept in the ~.e/e/config directory as a set of files and folders under each profile name.  When you do get a desktop you like you can save it as a Proile and then return to it whenever you stuff up your desktop (you need to enable the Settings-Profiles module to have that ability).  
.

---

### Post by Neo40 on 2009-06-24
I saw to elive forum there is a command with e17 to adjust fonts hinting for gtk applications. Something like this:

```
e17-daemon-control FontHinting '1' - Enable font hinting, '0' will disable it

e17-daemon-control FontHintStyle 'hintfull' - Enable full font hinting, possible values are
hintnone - No hinting style
hintslight - Slight hinting
hintmedium - Medium hinting
hintfull - Full hinting

e17-daemon-control FontSubpixelHint 'rgb' - Subpixel hinting style, possible values are
rgb
bgr
vrgb - vertical rgb
vbgr - vertical bgr
none - no subpixel hinting 
```

Does this command exist too with e17-svn?

---

### Post by atomizer on 2009-06-25
> **Tux Aubrey said:**
> Sorry for the delay in replying.

This is a response to those having trouble installing or updating e17 using e17-svn.

The script throws errors on several packages including etk-extras and enhance because these have been removed from the main trunk of the Enlightenment svn.



Thanks Tux Aubrey, your solution worked.
Googled for solution, but most posts seem out of date.
Followed your instuctions and passed the point when it was looking for etk_extras

---

### Post by Tux Aubrey on 2009-06-25
> **atomizer said:**
> Thanks Tux Aubrey, your solution worked.
Googled for solution, but most posts seem out of date.
Followed your instuctions and passed the point when it was looking for etk_extras

I'm so glad it worked! This stuff is happening in "real time" and we only find out about it when stuff actually breaks.  Sometimes these are just passing bugs and, at others (like these ones), they are genuine deliberate and permanent changes.  That means that any instructions more than a week old are likely to be out of date.  Oh, the joys of following an active development svn!  Ubuntu's alphas and betas are boring by comparison.:D

---

### Post by Neo40 on 2009-06-26
Hi,

I have e17-svn running fine but I'd like my desktop looks like the one from ozos home page.
[http://www.cafelinux.org/OzOs/](http://www.cafelinux.org/OzOs/)

Is there a easy way configure it?
Thanks!

---

### Post by pierrejardin on 2009-06-30
Hi!

I tried to install the e17 via Easy_e17.sh and had problems (as many others) with 

"http://svn.enlightenment.org/svn/e/trunk/etk_extra"

I wan't to cancel the installation, but when I'm using Ctrl + C it stops the installation, but I can't use aptitude. It just says

you have to manually bla bla bal sudo dpkg --configure -a

But then the installation starts over again, and of course I can't find the files. 

How do I cancel the installation? So it won't start all over again.

/PJ

---

### Post by lekremyelsew on 2009-07-01
> **pierrejardin said:**
> Hi!

I tried to install the e17 via Easy_e17.sh and had problems (as many others) with 

"http://svn.enlightenment.org/svn/e/trunk/etk_extra"

I wan't to cancel the installation, but when I'm using Ctrl + C it stops the installation, but I can't use aptitude. It just says

you have to manually bla bla bal sudo dpkg --configure -a

But then the installation starts over again, and of course I can't find the files. 

How do I cancel the installation? So it won't start all over again.

/PJ

I had the same issue. I did Ctrl+C then:
```

sudo apt-get remove e17-svn

```
Then I purged all the extra packages that it installed before it failed (I just copied them from the list when it asked for install conformation).

You could probably do that dpkg crap if it still wont start.

---

### Post by stanks on 2009-07-05
same problem...etk_extra doesn't exist

---

### Post by Tux Aubrey on 2009-07-06
For the etk-related problems, please see [THIS POST]("http://ubuntuforums.org/showpost.php?p=7488509&postcount=392")

---

### Post by stanks on 2009-07-06
thanks. it worked. hm but i have problems with my keyboard. cursor keys doesn't work, AltGr+Some_Key doesn't work :( And it seems that they solve already this problem a few months ago

---

### Post by Tux Aubrey on 2009-07-06
> **stanks said:**
> thanks. it worked. hm but i have problems with my keyboard. cursor keys doesn't work, AltGr+Some_Key doesn't work :( And it seems that they solve already this problem a few months ago
Hhave you tried to reassign your keybindings in System>Input>KeyBindings?  (You may need to load the Module first)

---

### Post by stanks on 2009-07-06
there is no cursor keys, altgr+some_key in key bindings list. altgr is same as enter in terminal. lol.

---

### Post by stanks on 2009-07-07
When i load language module then i get that problem. Before that my mother language is ok and all keys work ok. Bug or something else? And how to reverse to previous state when everything was ok?

thanks

---

### Post by digitalbrain on 2009-07-07
When I tried to update today, I got this error:
```
Checking emphasis source ... svn: REPORT request failed on '/svn/e/!svn/vcc/default'
svn: Target path does not exist
svn: REPORT request failed on '/svn/e/!svn/vcc/default' 
```

Is this error related with the issue which Tux Aubrey mentioned on page 40 (message #392) with the title "FOR THOSE WHO HAVE INSTALLED e17-svn AND GOT A 'doesn't exist' ERROR"? I mean, should I follow the steps there to avoid getting this error? Thanks.

---

### Post by Tux Aubrey on 2009-07-07
> **digitalbrain said:**
> When I tried to update today, I got this error:
```
Checking emphasis source ... svn: REPORT request failed on '/svn/e/!svn/vcc/default'
svn: Target path does not exist
svn: REPORT request failed on '/svn/e/!svn/vcc/default' 
```

Is this error related with the issue which Tux Aubrey mentioned on page 40 (message #392) with the title "FOR THOSE WHO HAVE INSTALLED e17-svn AND GOT A 'doesn't exist' ERROR"? I mean, should I follow the steps there to avoid getting this error? Thanks.

Could be the same - any and all the following packages will throw the "Target path does not exist" error:

enhance
emphasis
etk_extra
exhibit

try the fix.

---

### Post by denied39 on 2009-07-09
**Nevermind <me>RTFM</me>**](*,)

---

### Post by Damnitsjoe on 2009-07-18
Ok so this happened, Idk what I did. 


joseph@joseph-laptop:~$ sudo mv ~/.e17_cvs /var/cache/e17_cvs
mv: cannot stat `/home/joseph/.e17_cvs': No such file or directory
joseph@joseph-laptop:~$ sudo apt-get update && sudo apt-get install e17-cvs
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release.gpg
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Translation-en_US
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty Release
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
Ign cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1) jaunty/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://cafelinux.org](http://cafelinux.org) tinwoodman Release.gpg                                
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg                            
Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_US              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US          
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg [197B]                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release.gpg                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US    
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Translation-en_US       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release                         
Get:2 [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty Release.gpg [197B]              
Ign [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty/main Translation-en_US            
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Translation-en_US                     
Ign [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty/extras Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release.gpg                   
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US             
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release [11.7kB]                     
Get:4 [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty Release [1180B]                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Translation-en_US        
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/multiverse Translation-en_US  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/universe Translation-en_US    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release                                
Hit [http://cafelinux.org](http://cafelinux.org) tinwoodman Release                                    
Ign [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty Release                           
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports Release                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Ign [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty/main Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Sources                        
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed Release                       
Ign [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty/extras Packages                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages             
Hit [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty/main Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages                    
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages                      
Hit [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty/extras Packages                   
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Packages                    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/restricted Packages   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/universe Packages     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-backports/multiverse Packages   
Hit [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-proposed/universe Packages
Fetched 396B in 1s (287B/s)
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://packages.enlightenment.org](http://packages.enlightenment.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6B2226D9969C86CA
W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

---

### Post by luposolo on 2009-07-22
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' doesn't exist
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' doesn't exist
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra' doesn't exist

now i cant install anything on my system

---

### Post by luposolo on 2009-07-22
thats why people should just run the script from here [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/)

---

### Post by kag9000 on 2009-07-23
> **luposolo said:**
> thats why people should just run the script from here [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/)

Nope, same error.

Edit: seems to be working now.

---

### Post by TheNosh on 2009-07-23
> **luposolo said:**
> thats why people should just run the script from here [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/)

i just did that, it finished and said something like "enjoy your venture into e17" 

but then i log out to log back in into e17 and it doesn't appear in the "session" options
[U]
EDIT:[/U] sorry, i was looking for e17, so i didn't see it because it's labeled "enlightenment"

how do i get it to connect to wifi?
[U]
EDIT 2:[/U] i installed wict, it seems to be performing better than the gnome network manager anyway, AND it works in e17 (woot! double awesome!\\:D/)

---

### Post by The Recorder on 2009-07-25
My installation of E17 went fine.  However, I have one annoying problem.  I am using two monitors, and E17 extends them correctly.  But, as my below xog.conf file shows, I have DVI-I-1 to the left of DVI-I-0.  This is no problem in my Gnome, KDE4, Xfce, and LXDE desktops; they use the left screen (DVI-I-1) as the primary screen. But, E17 uses my right screen (DVI-I-0) as my primary; the splash screen and shelf_1 show on the right screen, and I have found no way to change this, even with (g)randr, after entry.  In fact, I can't even add a shelf to the left screen.  Since my xorg.conf file is working fine with my other desktops, I don't want to mess with it.  Is there any way to "tell" E17 to use DVI-I-1 as my primary screen?

*********************

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
        Identifier      "Dual Head Layout"
        Screen          0       "Default Screen"        0 0
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us,il"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2048 768
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option          "monitor-DVI-I_2/analog"        "DVI-0"
        Option          "monitor-DVI-I_1/analog"        "DVI-1"
        Option          "RROutputOrder"                         "DVI-I_2"
	Option          "DPI"                           "96x96"
EndSection

Section "Monitor"
        Identifier      "DVI-0"
        Option          "Position"      "1024 0"
EndSection

Section "Monitor"
        Identifier      "DVI-1"
        Option          "LeftOf"        "DVI-0"
EndSection

Section "ServerFlags"
        Option  "DontZap"       "True"
 #       Option  "Xinerama"      "True"
EndSection

---

### Post by mitch_77 on 2009-07-25
hi all,
i tried to install e17 with the script from [http://omicron.homeip.net/projects/]("http://omicron.homeip.net/projects/") but at the step 11/12 i get this error:

```
------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- e_dbus ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- esmart ..................... previously installed
- exchange ................... ok          
- e .......................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.6 CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running autopoint...
./autogen.sh: 9: autopoint: not found
Running aclocal...
configure.ac:155: warning: macro `AM_GNU_GETTEXT' not found in library
configure.ac:156: warning: macro `AM_GNU_GETTEXT_VERSION' not found in library
Running autoconf...
configure.ac:157: error: possibly undefined macro: AM_GNU_GETTEXT
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:158: error: possibly undefined macro: AM_GNU_GETTEXT_VERSION
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/e.log'!
```

..and that log file is empty!

thanks,
mitch

---

### Post by Tux Aubrey on 2009-07-25
mitch_77

I'm afraid that the script you are using is outside the (original) intention and purpose of this thread.  

While I assume it is based on the easy_e17 script by Morlenxus, it is obviously different enough from Rui Pais' version that debugging is a different task.

You might want to try starting a new thread for users of that script.

Alternatively, you could try Rui's version - following the hacks in this thread if you strike problems - **OR** try installing one of the newer e17 binary packages from repositories at  [http://xsm.alphagemini.org/E17/repository/](http://xsm.alphagemini.org/E17/repository/) or [http://packages.enlightenment.org/](http://packages.enlightenment.org/) .

Both are now fairly up to date and newer versions are being uploaded pretty regularly now.  The suitability of one version over the other depends on which version you are currently using.  packages.enlightenment.org is more official, but (I believe) not as up-to-date and will have problems with Karmic alphas.

Right _now_, the alphagemini binaries are working well with both karmic and jaunty - but there is no guarantee of continued stability unless you lock the packages (there are some shared libraries in the Ubuntu multiverse repo that are not necessarily synced with newer e17 versions).

Never, under any circumstances, mix a svn compiled version of e17 (via any of the easy-e17 scripts) with a binary version (from the repos above or on OpenGeu) - unless you want hours of fun untangling the mess.

---

### Post by mitch_77 on 2009-07-27
> **Tux Aubrey said:**
> mitch_77

I'm afraid that the script you are using is outside the (original) intention and purpose of this thread.  

While I assume it is based on the easy_e17 script by Morlenxus, it is obviously different enough from Rui Pais' version that debugging is a different task.

You might want to try starting a new thread for users of that script.

thanks for replying Tux Aubrey

i'm sorry, i thought it was the same script (the link provided by Rui in the first post sent me to the same web page i mentioned in mine :confused:).

> **Tux Aubrey said:**
> Alternatively, you could try Rui's version - following the hacks in this thread if you strike problems - **OR** try installing one of the newer e17 binary packages from repositories at  [http://xsm.alphagemini.org/E17/repository/](http://xsm.alphagemini.org/E17/repository/) or [http://packages.enlightenment.org/](http://packages.enlightenment.org/) .

Both are now fairly up to date and newer versions are being uploaded pretty regularly now.  The suitability of one version over the other depends on which version you are currently using.  packages.enlightenment.org is more official, but (I believe) not as up-to-date and will have problems with Karmic alphas.

Right _now_, the alphagemini binaries are working well with both karmic and jaunty - but there is no guarantee of continued stability unless you lock the packages (there are some shared libraries in the Ubuntu multiverse repo that are not necessarily synced with newer e17 versions).

Never, under any circumstances, mix a svn compiled version of e17 (via any of the easy-e17 scripts) with a binary version (from the repos above or on OpenGeu) - unless you want hours of fun untangling the mess.

fair enough...i just wanted to give e17 a shot and the official repository made it possible without messing with subversions :D

thanks again,
mitch

---

### Post by Tux Aubrey on 2009-07-27
> **mitch_77 said:**
> thanks for replying Tux Aubrey

fair enough...i just wanted to give e17 a shot and the official repository made it possible without messing with subversions :D

thanks again,
mitch

No worries.  Perhaps we need a new "How-To" thread on e17.  As it approaches an official beta release, the binaries offer a better way for people to dip their toes in the water.  That wasn't case when Rui started this thread (and some of us do continue to punish ourselves with the scipt/s for reasons best known only to our psycologists). But svn is no longer the only or best option for those with a hankering for some up to date e17 magic.

---

### Post by JohnMac on 2009-07-29
It doesn't work for me I have tried to follow your instructions and all I get when I try to configure is "......./etk_extra does not exist"

My set up is:

Jaunty running as a guest on an XP host using VMWare

Sorry I didn,t read the more recent posts. I'll probably have a go at using the official repositories to install e17.

Can anyone tell me how to purge the svn scripts?

---

### Post by djvantri on 2009-08-06
wondering if someone can help me with compiling itask-ng.
downloaded the latest version from svn

when running autogen.sh i get this far

Running autopoint...
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
data/themes/Makefile.am:12: `%'-style pattern rules are a GNU make extension
Makefile.am:18: `%'-style pattern rules are a GNU make extension
Makefile.am: required file `./NEWS' not found
Makefile.am: required file `./README' not found
Makefile.am: required file `./AUTHORS' not found

not sure if this is a problem on my end or in the download, any help 
would be greatly appreciated.

---

### Post by VCoolio on 2009-08-07
That's strange, aren't those files inside the itask-ng folder? They sure should be, look [here]("http://itask-module.googlecode.com/svn/trunk/itask-ng/"). Try downloading again: "svn checkout http://itask-module.googlecode.com/svn/trunk/itask-ng".

Also, why don't you use the script? Copy the itask-ng folder to /var/cache/e17_src (using "sudo cp -r /path/to/itask-ng /var/cache/e17_src"), then add itask-ng to the packages list inside /usr/bin/easy_e17.sh (using "gksudo gedit /usr/bin/easy_e17.sh") and then run "sudo easy_e17.sh --only=itask-ng".
If you still want to compile but installed e17 with the svn script, don't forget the prefix on autogen: 
./autogen.sh --prefix=/opt/e17

---

### Post by Neo40 on 2009-08-09
I ran the script from [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/)
and I got this error:

```
------------------------------ Installing packages -----------------------------
- eina ....................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.2.6 CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
configure.ac:15: error: possibly undefined macro: AC_LIBTOOL_WIN32_DLL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:18: error: possibly undefined macro: AC_PROG_LIBTOOL
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/eina.log'!
```


Any idea? I have Ubuntu 8.04.
Thanks

---

### Post by digitalbrain on 2009-08-11
@Neo40

I'm not sure but it can be about your automake version (because I had a similar problem in Hardy). You must have automake version 1.10 to install E17. Check it out.

---

### Post by kevdog on 2009-08-23
It keeps trying to svn the emphasis package, and I have this listed in the skip list.  Why?

---

### Post by kevdog on 2009-08-24
Where did Aubrey go?? Help!

---

### Post by Tux Aubrey on 2009-08-25
> Where did Aubrey go?? Help! 

The short answer is "flu".  But I shall drag myself (cough, cough) to the old monitor and (wheeze, cough) and try to answer your question (hachhhhk)

I think what happened was that emphasis was demoted to the "old" part of the svn, which means the script is looking for it and not finding it (the "skip" list in easy_e17.conf only refers to the build-install process, not the download).  This also affects enhance, etk_extra and exhibit

The fix is mercifully easy.  I wrote it out (with a replacement script attached) in [post 392]("http://ubuntuforums.org/showpost.php?p=7488509&postcount=392") 

(Basically it is a matter of removing those deprecated packages from the list in the easy_e17.sh file - but I provided an edited version in that post to make it a bit easier for new players)

**But** there is now one more step before you run the new script - the edje package has a new dependency - lua - and you will need to do
```

sudo apt-get install liblua5.1-0-dev
```

to install the right version.

Hope that helps! (cough)

---

### Post by kevdog on 2009-08-25
Aubrey

I will try this today, but in the meantime I hope you feel better.  I hope your flu isn't of the Mexican pig variety?

---

### Post by Tux Aubrey on 2009-08-25
> I hope your flu isn't of the Mexican pig variety?

No - far worse.  It is a [Man Cold]("http://www.youtube.com/watch?v=rXLHWmjA5IE").

---

### Post by kevdog on 2009-08-26
What's the best strategy to do when I keep getting messages like this from your new install script -- and FYI I've never used anything to upgrade e17 other than an install script:

svn: Failed to add directory 'etk/data/themes/default': an unversioned directory of the same name already exists

I hate when things like this happen too  (dang linker error):
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setiv'
../../src/lib/.libs/libeet.so: undefined reference to `gcry_cipher_setkey'
collect2: ld returned 1 exit status
make[3]: *** [eet] Error 1
make[3]: Leaving directory `/var/cache/e17_src/eet/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/var/cache/e17_src/eet/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/var/cache/e17_src/eet'
make: *** [all] Error 2

---

### Post by Stan_1936 on 2009-08-26
> **Tux Aubrey said:**
> ...Perhaps we need a new "How-To" thread on e17....

Quite honestly, it's about time someone knowledgeable wrote an updated detailed description of how to go about doing this and then kept updating it every 2-3 months.  I'm sorry but using the first post in an 8 to 10 month old thread is SIMPLY NOT the way to go.......

I think you should be the one who writes a new post(in this thread will be just fine), listing the commands required.

Please avoid writing a script.  Just list the commands.

---

### Post by Hoshikage on 2009-08-27
Alright, so I'm attempting to install e17, and I followed the proper steps in the first post, however, I got an error, I can't post the terminal output without making my comp damn near unusable until I reboot it, however, I can tell you that it cannot find [http://svn.enlightenment.org/svn/e/trunk/etk_extra](http://svn.enlightenment.org/svn/e/trunk/etk_extra) and when I enter that into my browser, I get a 404 error, so I've got a feeling like it doesn't exist.  When I try to run a sudo apt-get.., anything I get the error [code[dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. [/code] but when I run the command, It gets stuck at the same place. Please, help a newb out?

 I dug through the thread and already tried doing both 
```
touch $HOME/_skip_easy_e17_install

and

sudo apt-get update && sudo apt-get install e17-svn
```and still cannot get past it telling me I need to run the sudo dpkg.

Oh, and does it matter that I'm using the 64 bit version of Jaunty?

---

### Post by worldwithoutgurus on 2009-08-27
Who cares about etk_extra ?
If you can read French, use a reliable method: check out my sig...

---

### Post by mukul_s on 2009-08-27
> **Stan_1936 said:**
> Quite honestly, it's about time someone knowledgeable wrote an updated detailed description of how to go about doing this and then kept updating it every 2-3 months.  I'm sorry but using the first post in an 8 to 10 month old thread is SIMPLY NOT the way to go.......

I think you should be the one who writes a new post(in this thread will be just fine), listing the commands required.

Please avoid writing a script.  Just list the commands.

so is someone knowledgeable n expert enough to write the new tutorial? I don't want to go through some 40 odd pages of posts and in the end say that it didn't work.

---

### Post by custos on 2009-08-27
I get the following error during Source checkout/update:

```
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/etk_extra doesn't exist
```

which sends the installer into a (to all appearances infinite) loop of reattempting the download and redisplaying the error.

Any thoughts?
Thanks

EDIT: Whoops, just realized this is the exact same problem as the poster a few above me. No apparent answer, though: I don't read French.

EDIT 2: I was running on a virtual box to test a few installations, so I just nuked the virtual drive and started over, but it would be good to have a solution to get out of the dpkg loop. Like Hoshikage, the 'touch' method above didn't work for me.

---

### Post by Tux Aubrey on 2009-08-27
**This thread really needs to be closed** - the original tutorial and even the various hacks through the replies WILL NOT WORK (at least consistently).

You are all right about the need for a new tutorial but now is not the time (for me, anyway).  There are simply too many changes in the e17 svn and dependencies for this to be a simple matter of listing commands. The script itself needs a complete overhaul (and this is being done and tested "elsewhere" right now).  When that has been done, I'll do a new tutorial or post a link to working method/s.

For those just starting out, I'll repeat my earlier advice about finding some updating packages in either the [enlightenment]("http://packages.enlightenment.org/") repos or at [alphagemini]("http://xsm.alphagemini.org/E17/repository/").  These are a couple of months old now and there are some problems with some versions of Ubuntu (particularly Karmic), but they are more reliable than using the existing svn scripts.

For those with problems with emphasis, etk_extra, exhibit and enhance - _please_ read the recent posts on this topic.  (OMG, I am become Rasterman!:)).  

The GOOD NEWS is that a beta of e17 should be available soon (and those of us with working svn versions think it is pretty darn close to being a perfect Linux desktop).

---

### Post by custos on 2009-08-27
In response to Aubrey's suggestion to try different methods, I can confirm that the packages.enlightenment.org repos can be used to successfully install e17 on a Ubuntu mini (9.04) install. I did this relatively issue free. (You need to install HAL and xserver yourself, though.) I've been so far unable to install entrance from the repos, but that's not a big deal, since I was using SLiM anyway.

I was thinking about doing a Ubuntu mini tutorial myself, so if I do, I'll include e17 info in it.

---

### Post by xyverz on 2009-09-09
*sigh* I installed using the repos you listed here, using the ecomorph-e17 packages (compiz-enabled), and decided I didn't like it.  However, upon returning to gnome my window decorations disappear when desktop effects are selected... Any suggestions other than running the following, which doesn't fix the problem for me?

```
sudo nvidia-xconfig --add-argb-glx-visuals --depth=24
```

It's like compiz just decided to stop working in gnome for me.

If you could point me to the correct thread, that would be awesome.

---

### Post by VCoolio on 2009-09-09
It's a common problem but I never really narrowed it down to the cause. You can try the following:
1. in compiz, window decorator plugin, fill in 'metacity --replace' for decorator command. The same can be achieved by installing and running fusion-icon, which is a very useful systray icon that you can rightclick to easily switch window managers and decorators.
2. use emerald for window decoration. This option always works for me. (don't forget to apply emerald with 'emerald --replace' or using the methods mentioned in option 1).

---

### Post by xyverz on 2009-09-09
Well, that didn't work very well for me, but I noticed that when I tried to do `emerald --replace` I got errors for libdecorator, so I did `apt-get remove compiz` and then reinstalled all the packages removed by that operation. In playing around after that, I ended up getting my normal window decorations back.

Thank you for your assistance, they got me pointed in the right direction.

I'll give e17 a try again in the future, after it's been given the final release.

Thanks again!

---

### Post by Cortux on 2009-09-15
Hi, I get this error while installing 


-------------------------------- Build phase 1/3 -------------------------------
- running some basic system checks
- source checkout/update
--------------------------------------------------------------------------------


------------------------------- Basic system checks ----------------------------
- creating script dirs ....... ok
- 'automake' available ....... ok
- 'gcc' available ............ ok
- 'make' available ........... ok
- 'svn' available ............ ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok (/etc/ld.so.conf.d/e17.conf)
- setting compile options .... ok
--------------------------------------------------------------------------------

----------------------------- Source checkout/update ---------------------------
- checkout sources ...
   downloading eina source ...
   downloading eet source ...
   downloading evas source ...
   downloading ecore source ...
   downloading efreet source ...
   downloading embryo source ...
   downloading edje source ...
   downloading epsilon source ...
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/epsilon' doesn't exist
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/epsilon' doesn't exist
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/epsilon' doesn't exist
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/epsilon' doesn't exist
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/epsilon' doesn't exist
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/epsilon' doesn't exist
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/epsilon' doesn't exist
FAILED! Next attempt 8 in 264 seconds^Cdpkg: error processing e17-svn (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 e17-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)


Please help

---

### Post by VCoolio on 2009-09-15
Epsilon was removed according to [someone who is usually right]("http://cafelinux.org/forum/index.php?topic=62.msg468#msg468"). So remove epsilon from the packages line in /usr/bin/easy_e17.sh, then remove it from the the folder /var/cache/e17_src if it's there and then try again (don't forget to install liblua5.1-0-dev which is a dependency now).

---

### Post by Cortux on 2009-09-15
Thanks for that.

Just need to know one thing, how would you tell a newbie to do that.

---

### Post by VCoolio on 2009-09-15
> **Cortux said:**
> Thanks for that.

Just need to know one thing, how would you tell a newbie to do that.

Either make a step-by-step tutorial with graphical apps and gksudo, or tell him / her to wait for the stable release. But I agree that compiling from svn has seen some issues over time. Nothing that couldn't be solved though, just wait for someone to explain. And make sure you know how to get your backup when upgrading doesn't work.

---

### Post by Cortux on 2009-09-15
I meant, im the newbie, but its cool. I have a friend who is helping me with the process. There seems to be many discontinued packages, is this normal.

---

### Post by Tux Aubrey on 2009-09-15
> I meant, im the newbie, but its cool. I have a friend who is helping me with the process. There seems to be many discontinued packages, is this normal.

There is nothing "normal" about e17 or its development! Seriously - it is very innovative software and still very much "in development".  The discontinued packages issue is just part of the deal, I'm afraid.  When something like "epsilon" (which is a graphics library) disappears from the main trunk of the svn it probably means that those functions have been replaced by something more elegant and better integrated.  The devs (well, some of them) are absolutely obsessed with elegance, minimalism and speed - which is why some of us (ie. me) are willing to put up with the inevitable problems of following its development so closely.

Also bear in mind that using the svn version is frowned upon by those same devs for these reasons and it is only idiots (me and few others) who are so damn hooked on e17 that subject ourselves to it. It is one of those love/hate things.

e17 has been known to send distro developers completely mad and that is why there are very few that include it even as an "alternative" desktop. 

The good side of all this for newbies, those with limited patience or people with a normal dose of common sense is that e17 is very close (after > 4years) to an official beta release.  The current pre-beta packages in the e17 repos are actually very good (IMO) and I'm using them on two machines now.  I can almost guarantee that a beta of e17 will be far, far more stable, usable and polished than final release versions of most other desktop environments.  Hopefully, that will be enough to reignite user and distro-builder interest.  If not, I will continue to gnaw through my restraints each morning to update mine from svn.

:P

---

### Post by VCoolio on 2009-09-15
> **Tux Aubrey said:**
> ... it is only idiots (me and few others) who are so damn hooked on e17 that subject ourselves to it. It is one of those love/hate things.


:lolflag: Yes, true. But it's definitely worth the occasional "sigh".

---

### Post by mukul_s on 2009-09-17
> **Tux Aubrey said:**
> Karmic alpha plus e17 alpha is very cool!)
May I've the recipe for this :P

Regards
Mukul

---

### Post by Tux Aubrey on 2009-09-17
> May I've the recipe for this 

Just for the record, Post #3 in this thread [http://ubuntuforums.org/showthread.php?t=1245480](http://ubuntuforums.org/showthread.php?t=1245480) (with "Karmic" substituted for "Jaunty") is the basic repo recipe.

---

### Post by kevdog on 2009-09-17
What about a basic recipie for those of us not on Jaunty or Karmic?

---

### Post by Tux Aubrey on 2009-09-17
> **kevdog said:**
> What about a basic recipie for those of us not on Jaunty or Karmic?

Bit difficult right now as the official repos for earlier releases recently disappeared.  There is at least one unofficial Debian repo (see [http://xsm.alphagemini.org/E17/repository/](http://xsm.alphagemini.org/E17/repository/)) that may work.  I'd still avoid using emodules-all and install them individually as there is at least one in this build (emule from memory) that crashes Ubuntu.

---

### Post by kevdog on 2009-09-18
Still using the damn update script on Intrepid .. now eet isn't compiling -- I love e17 but honestly, its really a pain to update.

---

### Post by Tux Aubrey on 2009-09-18
> **kevdog said:**
> Still using the damn update script on Intrepid .. now eet isn't compiling -- I love e17 but honestly, its really a pain to update.

+1 :)

I had the same problem with etk this morning (and epsilon last week).  This is precisely why I am not trying to put togther a new script right now.  No sooner have we got it "right" than the svn changes fundamentally or a new dependency arises (like the liblua one a couple of weeks ago).  I also had problems with the script in Karmic because of version problems with dependencies.

There is no effective medication for this type of frustration (trust me on this; I have tried many things).  But I also find abstinence to be impossible.

On the plus side (as I have said elsewhere) all this is happening due to code cleaning that will result in an even more efficient and elegant e17.  

Try to smile. :popcorn:

---

### Post by mukul_s on 2009-09-18
> **Tux Aubrey said:**
> Just for the record, Post #3 in this thread [http://ubuntuforums.org/showthread.php?t=1245480](http://ubuntuforums.org/showthread.php?t=1245480) (with "Karmic" substituted for "Jaunty") is the basic repo recipe.
Hi Tux,

The problem with that is, it contains packages dating july 29th and that's pretty old.

---

### Post by Tux Aubrey on 2009-09-18
> **mukul_s said:**
> Hi Tux,

The problem with that is, it contains packages dating july 29th and that's pretty old.

That's the last known .deb package.  I believe that new ones will be done in the next couple of weeks as there was a freeze of the svn last weekend. Nothing much has happened to the user interface since the July freeze so any differences will be undetectable (unless you are using a language other than English)

---

### Post by mukul_s on 2009-09-20
Hi Tux,

so i got E17 through the repos. But somehow I am not able to connect my wireless network in Enlightenment. Do u know any workaround?? 
The network is working fine in Xubuntu though.

Regards
Mukul

---

### Post by Tux Aubrey on 2009-09-20
> **mukul_s said:**
> Hi Tux,

so i got E17 through the repos. But somehow I am not able to connect my wireless network in Enlightenment. Do u know any workaround?? 
The network is working fine in Xubuntu though.

Regards
Mukul

this happens - best solution I've found is to install wicd (but it will uninstall the gnome-network-manager, which is no great loss IMO):

```
sudo apt-get install wicd
```

It is actually a brilliant network manager - but you'll need to set it up for your own wireless network.

To start the gui:

```
wicd-client
```

I have it as a start-up application.  It uses the enlightenment system tray (the systray gadget) quite well.

---

### Post by mukul_s on 2009-09-20
I tried wicd however it was not able to connect to my WPA2-PSK network.
I'll give it another try.

---

### Post by kevdog on 2009-09-20
You may have to modify the template in wicd for your wpa2 network.  Im using wpa2psk at home along with wicd and it receives a dhcp lease without a problem.

---

### Post by mukul_s on 2009-09-20
> **kevdog said:**
> You may have to modify the template in wicd for your wpa2 network.  Im using wpa2psk at home along with wicd and it receives a dhcp lease without a problem.
How to do that?
can you post urs here...

---

### Post by kevdog on 2009-09-20
I didn't change mine from the default, however the template is located in /etc/wicd/encryption/templates

Just a few things to keep in mind from my humble experience

Get WPA(1) up and working first

Then try wpa2-psk with the tkip cipher sets.  Then change to CCMP or add CCMP back in (which represents AES).

---

### Post by Cortux on 2009-09-24
I am currently doing a new installation of E17, I get this error:


svn: Working copy '/var/cache/e17_src/eet' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)

it keeps repeating itself over again, please help as soon as possible, i would like to get this right away.

Thanks

---

### Post by Cortux on 2009-09-24
Someone, please

---

### Post by smartboyathome on 2009-09-24
> **Cortux said:**
> I am currently doing a new installation of E17, I get this error:


svn: Working copy '/var/cache/e17_src/eet' locked
svn: run 'svn cleanup' to remove locks (type 'svn help cleanup' for details)

it keeps repeating itself over again, please help as soon as possible, i would like to get this right away.

Thanks

Run this:
```
cd /var/cache/e17_src/eet
sudo svn cleanup
sudo easy_e17.sh -i
```
That should fix it. :)

Have any more questions, I suggest contacting us at [the official forum](http://cafelinux.org/forum/index.php), as I don't usually come on here often.

---

### Post by Cortux on 2009-09-24
After    sudo svn cleanup


I get :

svn: In directory 'doc'
svn: Error processing command 'modify-wcprop' in 'doc'
svn: 'doc/Doxyfile' is not under version control

---

### Post by worldwithoutgurus on 2009-09-25
Never used "easy_e17", but when something like this happens on my system, I simply delete the directory in question, re-run svn cleanup then update again.

---

### Post by Cortux on 2009-09-25
> **worldwithoutgurus said:**
> Never used "easy_e17", but when something like this happens on my system, I simply delete the directory in question, re-run svn cleanup then update again.

Can you tell me how to do that cause im still getting the same error.

---

### Post by worldwithoutgurus on 2009-09-26
What directory does this 'doc/Doxyfile' belong to? If you know the directory, it's easy to delete it. 

Delete, cleanup and update as many times as necessary. If nothing works, you probably should uninstall then reinstall the whole thing...

---

### Post by cheater1034 on 2009-09-26
nevermind

---

### Post by Cortux on 2009-09-26
> **cheater1034 said:**
> nevermind


????????????????????

Now i am getting te epsilon missing retrying error and cant seem to delete it (epsilon)

Someone please help

---

### Post by VCoolio on 2009-09-26
Epsilon is deprecated, so my guess: remove epsilon (and also etk, but I assume you solved that already) from the packages line in /usr/bin/easy_e17.sh and to be sure add it to the skip list in /etc/easy_e17.conf.  Then remove the epsilon folder from /var/cache/e17_src/ if existing and try again.

Btw I found out that installing from the e17 repo is done in a few minutes; you're not cutting edge and not every module works ok (in my case the "open everything" module crashes x, but I use kupfer so I don't care) but on the other hand you get the feature of downloadable online themes and wallpapers directly in the theme configuration window. I'm done compiling for the moment.

---

### Post by Tux Aubrey on 2009-09-26
> **VCoolio said:**
> 
Btw I found out that installing from the e17 repo is done in a few minutes..... I'm done compiling for the moment.

+1

I have been installing e17 from the [packages.enlightenment karmic repos]("http://packages.enlightenment.org/ubuntu/dists/karmic/") on everything I can plug a CD drive into for the past week and haven't struck major problems.

Here's one on the alpha build of karmic-moblin-netbook-remix - not recommended (the moblin apps are appalling on e17!) but it is the fasted bootin' virtual machine I have ever produced.

[[IMG]http://www.cafebotanical.com/various/e17_on_moblin_karmic_thumb.png[/IMG]]("http://www.cafebotanical.com/various/e17_on_moblin_karmic.png")

---

### Post by worldwithoutgurus on 2009-09-27
**-1**

E17 is *not* GNOME or KDE, it's all about modularity, vitality, control and unbloated software! : Binary packages have always been the second choice when speaking of running E17... And I've been compiling E17 from CVS/SVN for years, on various distros.

And it let's me update my installation on a daily basis.

So don't think "cutting edge", think fine control and freedom!

The script you were using is obsolete/umaintained... So what?  Write your own or compile manually! Svn is *still* kicking and alive!

Alternatively if you can read French, try my method (beginners welcome)! - See my signature.

Enlightenment hasn't even been released yet, if you want to follow/help/speed up the development of E17, installing from SVN is the way to go. And it's fun!

@ VCoolio:

Run everything is ok in current svn - no crash.

"You get the feature of downloadable online themes and wallpapers directly in the theme configuration window." 

Hum... it's just a matter of compiling PROTO/exchange. What with that?

---

### Post by Tux Aubrey on 2009-09-27
> **worldwithoutgurus said:**
> **-1**


So don't think "cutting edge", think fine control and freedom!



True - I have machines on which I do both - but I'm increasingly recommending the binary route for newbies because:

[LIST]
[*]The fine control needed over the svn, via any script, means that people need to understand the structure of the svn and the way the script handles deprecated packages.

[*]There have been too many of these fundamental changes in e17 over the past couple of months to make this a "pleasant" or "easy" experience; and

[*]The differences between the current repo version and the bleeding edge are very minor for the vast majority of users (I have been monitoring the code changes daily and, while we can see performance-related changes, code tidy-up and lots of work on language (.po) files, there's very little relevant to the user experience)
[/LIST]

Certainly when things settle down - after the beta or RC - I'll help out with the scripting and maybe even do a new iso of "OzOS" featuring e17 from svn on a very lightweight xubuntu base (or even the moblin netbook remix).

---

### Post by worldwithoutgurus on 2009-09-27
"People need to understand the structure of the svn"... 

Indeed! It's the responsiblity of experienced users to teach less experienced users - and maintain up-to-date scripts and docs... We all want educated and active users.

Enlightenment needs themers, translators, more bug reports and feedback, etc. I'm not talking about E17 niche distros (some are even fun to use...) but mainstream Ubuntu: Using/promoting svn is the best way to attract active users and improving software quality.

---

### Post by Cortux on 2009-09-27
Ok, SUCCESS  in getting e17 installed and running

Thanks to all the guys who input, whether it worked or not, it was part of my way forward, I appreciate it. You guys have no idea how important your help is to us newbies, myself in particular.

I have just a couple not so big issues, if you dont mind giving me more assistance.

1. I cant shut down from system menu, even though I have no other window manager running at the time, the power off button cant be clicked (faded). The only way I can shut down from e17 is by pressing power key on laptop.

2. File manager, I cant go up or back a directory. For eg. once in music/rap music, i cant go back to music, i have to go to files/music again. And there is no toolbar with the directories at the top like in gnome.

3. Folder Size, when I right click a folder > properties, i see the folder size of 4kb and not the total size of the contents in the folder which im use to seeing.

4. When i close skype window by mistake, although its still running, how do i bring it back, if i click on the app icon, it says another instance of it already running. BTW its not minimised

5. how do I enable my 2nd monitor attached

There are probably more issues but this is all i am experiencing at the moment, any fixes if any would be highly appreciated.

Thanks Again

---

### Post by linuxchuck on 2009-09-27
> **Cortux said:**
> Ok, SUCCESS  in getting e17 installed and running

Thanks to all the guys who input, whether it worked or not, it was part of my way forward, I appreciate it. You guys have no idea how important your help is to us newbies, myself in particular.

I have just a couple not so big issues, if you dont mind giving me more assistance.

1. I cant shut down from system menu, even though I have no other window manager running at the time, the power off button cant be clicked (faded). The only way I can shut down from e17 is by pressing power key on laptop.

2. File manager, I cant go up or back a directory. For eg. once in music/rap music, i cant go back to music, i have to go to files/music again. And there is no toolbar with the directories at the top like in gnome.

3. Folder Size, when I right click a folder > properties, i see the folder size of 4kb and not the total size of the contents in the folder which im use to seeing.

4. When i close skype window by mistake, although its still running, how do i bring it back, if i click on the app icon, it says another instance of it already running. BTW its not minimised

5. how do I enable my 2nd monitor attached

There are probably more issues but this is all i am experiencing at the moment, any fixes if any would be highly appreciated.

Thanks Again

Glad to hear you worked it out.  Here are my suggestions to your problems:

1.  This is most likely due to a basic linux systems permission issue.  Make sure the user you are logged in as is a member of the proper groups that allow for shutting down/rebooting the system.  Typically, this is the "adm" group on your system.

2.  The file manager in e17 leaves quite a bit to be desired.  Stick with the earlier suggestions in this forum and use an alternate file manager.

3.  This could be solved using the suggestion in answer 2 above.

4.  As is also suggested earlier in this forum, install a system tray application, and have it running before you use skype.  Personally, I use stalonetray for this.  Others on here have different tray app preferences.  Just test them out and see which work best for your needs.

5.  This is not an e17 question.  This is an xorg.conf question.  This will depend *heavily* on what your hardware setup is, and you will have to google for yourself to find the proper technique.  If you are using a single adapter with multiple outputs such as an Nvidia, ATI, or Matrox card, then there are specific drivers and utilities you will be required to compile and use to achieve your goal.  If you have two separate video cards then you will need to get both properly working with the right drivers, and modify your xorg.conf to set up individual screens, or even run multiple instances of X11 displays.  I am positive that there will be a very specific HOWTO already written out there for your particular needs in this area.

Best of luck.

:)

---

### Post by Cortux on 2009-09-27
> **linuxchuck said:**
> Glad to hear you worked it out.  Here are my suggestions to your problems:

1.  This is most likely due to a basic linux systems permission issue.  Make sure the user you are logged in as is a member of the proper groups that allow for shutting down/rebooting the system.  Typically, this is the "adm" group on your system.

2.  The file manager in e17 leaves quite a bit to be desired.  Stick with the earlier suggestions in this forum and use an alternate file manager.

3.  This could be solved using the suggestion in answer 2 above.

4.  As is also suggested earlier in this forum, install a system tray application, and have it running before you use skype.  Personally, I use stalonetray for this.  Others on here have different tray app preferences.  Just test them out and see which work best for your needs.

5.  This is not an e17 question.  This is an xorg.conf question.  This will depend *heavily* on what your hardware setup is, and you will have to google for yourself to find the proper technique.  If you are using a single adapter with multiple outputs such as an Nvidia, ATI, or Matrox card, then there are specific drivers and utilities you will be required to compile and use to achieve your goal.  If you have two separate video cards then you will need to get both properly working with the right drivers, and modify your xorg.conf to set up individual screens, or even run multiple instances of X11 displays.  I am positive that there will be a very specific HOWTO already written out there for your particular needs in this area.

Best of luck.

:)


Thanks, That seemed to have sorted out just about all my issues, I will get the file manager and system tray, and I have managed to access the Nvidia settings which instantly allowed me to configure my monitors. Brilliant.

Regarding no.1 where i am unable to shutdown, could you give me a bit more detail on how to sort this out. I am currently the only user and would assume administrator for this machine. I log in as normal with username and password.

---

### Post by kevdog on 2009-09-27
I'm using pypanel for a system tray just to give you an idea.

---

### Post by linuxchuck on 2009-09-27
> **Cortux said:**
> Regarding no.1 where i am unable to shutdown, could you give me a bit more detail on how to sort this out. I am currently the only user and would assume administrator for this machine. I log in as normal with username and password.

As root, execute the following:

```
usermod -a -G adm your_username
```

Just substitute "your_username" with the login you use on your system.  Once you have made the change, you will need to log out, and log back in for the changes to take effect.

---

### Post by Cortux on 2009-09-27
> **linuxchuck said:**
> As root, execute the following:

```
usermod -a -G adm your_username
```Just substitute "your_username" with the login you use on your system.  Once you have made the change, you will need to log out, and log back in for the changes to take effect.


Have done so, still no luck

---

### Post by Cortux on 2009-09-27
> **kevdog said:**
> I'm using pypanel for a system tray just to give you an idea.

Could you brief me on how to install a system tray

---

### Post by linuxchuck on 2009-09-27
> **Cortux said:**
> Have done so, still no luck

Ok then, take a look at this file:

```
/opt/e17/etc/enlightenment/sysactions.conf
```

That is ultimately what determines which options are available to you when you start Enlightenment.  Read the file, and it explains how to set up your system to allow a specific group access to different functions such as shutdown.  The default file shipped from SVN (at least on my machine) gives the following groups access to the shutdown/reboot functions:

operator
staff
admin
sys
dialout
disk
adm
cdrom
floppy
audio
dip
plugdev

If I am reading the file correctly, any member of one of those groups will be given permission to halt/reboot/suspend/hibernate the system.

FWIW:  I actually didn't even know this file existed until about 15 minutes ago when I did a google search for the problems you are having.  Searching, and researching things yourself is usually a fairly easy task, and most people tend to learn much better when they locate a solution to a problem on their own.

Here's a link to the search I made:

[http://www.lmgtfy.com/?q=%2Be17+%2Bgroup+%2Bshutdown+%2Breboot](http://www.lmgtfy.com/?q=%2Be17+%2Bgroup+%2Bshutdown+%2Breboot)

That search found this information for me on the first hit.

Regards...

---

### Post by VCoolio on 2009-09-27
> **Cortux said:**
> Ok, SUCCESS  in getting e17 installed and running

1. I cant shut down from system menu.

2. File manager, I cant go up or back a directory. 

4. When i close skype window by mistake, although its still running, how do i bring it back, if i click on the app icon, it says another instance of it already running. BTW its not minimised



@ 1: can't help, but as a workaround you can try the following command (make a launcher or keybinding or whatever until you sort out the real problem):
to shutdown: gdm-control --shutdown && enlightenment_remote -exit
to logout: enlightenment_remote -exit

@ 2: try the backspace key. Also, if running nautilus, use nautilus --no-desktop to prevent launching the gnome settings like wallpaper and stuff that nautilus does there. I recommend thunar though.

@ 4: use the systray module on your panel as said, but I found some bugs there with eg. claws-mail and alltray. The systray with [tint2 panel]("http://code.google.com/p/tint2/wiki/Welcome") works perfectly though.

---

### Post by VCoolio on 2009-09-27
> **VCoolio said:**
> @ 4: use the systray module on your panel as said, but I found some bugs there with eg. claws-mail and alltray. The systray with [tint2 panel]("http://code.google.com/p/tint2/wiki/Welcome") works perfectly though.

Scratch that, it doesn't (is a wm problem, not a systray thing; e17 somewhere doesn't follow the standards). Most apps works with e17-systray (parcellite, update-notifier, transmission, kupfer, sonata), others don't (alltray, claws-mail with systray plugin).

---

### Post by Cortux on 2009-09-28
> **VCoolio said:**
> @ 1: can't help, but as a workaround you can try the following command (make a launcher or keybinding or whatever until you sort out the real problem):
to shutdown: gdm-control --shutdown && enlightenment_remote -exit
to logout: enlightenment_remote -exit

@ 2: try the backspace key. Also, if running nautilus, use nautilus --no-desktop to prevent launching the gnome settings like wallpaper and stuff that nautilus does there. I recommend thunar though.

@ 4: use the systray module on your panel as said, but I found some bugs there with eg. claws-mail and alltray. The systray with [tint2 panel]("http://code.google.com/p/tint2/wiki/Welcome") works perfectly though.


I have thunar, the problem is, it looks horrible, and i cant change the look. I use a dark (crude theme). When opening thunar, its an eyesore compared to the theme in use.

But will try the backspace when back home, The default filemanager does look neat, so it deserves some credit.

Im cool on the shutdown thing, I guess I will just use the power button on the laptop.

---

### Post by Cortux on 2009-09-28
> **linuxchuck said:**
> Ok then, take a look at this file:

```
/opt/e17/etc/enlightenment/sysactions.conf
```That is ultimately what determines which options are available to you when you start Enlightenment.  Read the file, and it explains how to set up your system to allow a specific group access to different functions such as shutdown.  The default file shipped from SVN (at least on my machine) gives the following groups access to the shutdown/reboot functions:

operator
staff
admin
sys
dialout
disk
adm
cdrom
floppy
audio
dip
plugdev

If I am reading the file correctly, any member of one of those groups will be given permission to halt/reboot/suspend/hibernate the system.

FWIW:  I actually didn't even know this file existed until about 15 minutes ago when I did a google search for the problems you are having.  Searching, and researching things yourself is usually a fairly easy task, and most people tend to learn much better when they locate a solution to a problem on their own.

Here's a link to the search I made:

[http://www.lmgtfy.com/?q=%2Be17+%2Bgroup+%2Bshutdown+%2Breboot](http://www.lmgtfy.com/?q=%2Be17+%2Bgroup+%2Bshutdown+%2Breboot)

That search found this information for me on the first hit.

Regards...

That command giving me a no permission granted even when in root.

But its cool, no hassle on me using the power key

---

### Post by Tux Aubrey on 2009-09-28
> 1. I cant shut down from system menu, even though I have no other window manager running at the time, the power off button cant be clicked (faded). The only way I can shut down from e17 is by pressing power key on laptop.


Just a couple of thoughts:

The "system" functions (Power Off, Suspend, Logout etc) are controlled by the "system controls" module.  It needs to be loaded to get the dialog working: See attached Modules window.

It is also "theme-sensitive" - Older themes don't render it properly - but I assume you are using the default b_&_w theme.

Secondly, the GDM session switch works fine for me (as does Enlightenemnt>Exit from the main menu).  See the attached setup box for the session switcher - I have it set up as a launcher.

---

### Post by KriZo on 2009-09-30
I ran into problems while trying to install E17 using the How to in this thread. Now I can't use apt-get without the e17 script starting to run, and it can't get the dependencies so it just start looping trying to download the packages.

I get this error when i try installing things in the terminal using sudo apt-get

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

So i tried sudo dpkg --configure -a and get this

dpkg: status database area is locked by another process


What should i do? I have tried rebooting as a friend of mine suggested.

---

### Post by VCoolio on 2009-09-30
Create a file in your home folder to prevent e17 from compiling when you do "install e17-svn"
touch $HOME/_skip_easy_e17_install

Now remove source packages that were already downloaded (if any):
sudo rm -rf /var/cache/e17_src

Then fix dpkg and get the e17 install scripts:
sudo apt-get update && sudo apt-get install e17-svn

Now if you want to retry compiling:
rm $HOME/_skip_easy_e17_install
sudo easy_e17.sh -i

But see what was the problem when you first tried. There are some deprecated packages in the easy_e17 script that cause problems with the current svn tree (emphasis, etk, maybe others), so edit the packages=blabla line in /usr/bin/easy_e17.sh accordingly.

---

### Post by Cortux on 2009-09-30
> **Tux Aubrey said:**
> Just a couple of thoughts:
 
The "system" functions (Power Off, Suspend, Logout etc) are controlled by the "system controls" module. It needs to be loaded to get the dialog working: See attached Modules window.
 
It is also "theme-sensitive" - Older themes don't render it properly - but I assume you are using the default b_&_w theme.
 
Secondly, the GDM session switch works fine for me (as does Enlightenemnt>Exit from the main menu). See the attached setup box for the session switcher - I have it set up as a launcher.
 
 
Thanks for that, the system module was loaded , but it seems to work now. What I did is changed the default session to gnome, and now when booting into e17, the option to shutdown from system menu is selectable.

---

### Post by Tux Aubrey on 2009-10-01
> **Cortux said:**
> ...t it seems to work now. 


Good to know!  Strange about the Gnome session setting.  With a number of recent installs, I have started with Xubuntu, installed e17, made sure everything works OK and then started culling/replacing the default apps and the features I don't need.  As final step, I remove Xfce.  This leaves me with a very lightweight install with little or no baggage.  I've never found any relationship between e17 and the other WM, except for specific menu entries for Xfce or Gnome utilities.

The only time this approach has failed for me is with the Karmic Moblin Netbook Remix.  I uninstalled a couple of moblin apps and suddenly I have lost synaptic, update manager and a whole heap of other "core" apps.  apt also wants to actually uninstall about a dozen other essential packages inluding gdm.  I guess the moblin bit glues stuff together differently.

---

### Post by KriZo on 2009-10-01
> **VCoolio said:**
> Create a file in your home folder to prevent e17 from compiling when you do "install e17-svn"
touch $HOME/_skip_easy_e17_install

Now remove source packages that were already downloaded (if any):
sudo rm -rf /var/cache/e17_src

Then fix dpkg and get the e17 install scripts:
sudo apt-get update && sudo apt-get install e17-svn

Now if you want to retry compiling:
rm $HOME/_skip_easy_e17_install
sudo easy_e17.sh -i

But see what was the problem when you first tried. There are some deprecated packages in the easy_e17 script that cause problems with the current svn tree (emphasis, etk, maybe others), so edit the packages=blabla line in /usr/bin/easy_e17.sh accordingly.


Thank you, it solved the problem. But i still don't know how to install E17 :(

---

### Post by Rui Pais on 2009-10-05
> **KriZo said:**
> Thank you, it solved the problem. But i still don't know how to install E17 :(

Hi all, KriZo,

1st, my huge ***Thank You!*** for Tux Aubrey and Smartboyathome (and Bro.Tiag beyond the scene) for keep things rolling and help users on this topic.

This package have now 2 maintainers, me and Bro.Tiag (a debian user), I hope we can give it more attention then it had received lately.

Sorry for all inconveniences. 

A new updated version it's available on repos.
To update please do:
```
sudo apt-get upgrade & sudo apt-get update
```
if at that point apt asks for keep conf file or install package maintainer's version opt by the maintainer's version (Option I or Y).
Then just update from a fresh svn tree:
```
sudo rm -rf /var/cache/e17_src
sudo easy_e17.sh -i
```

Should be all needed

Check for more details on CLF [here]("http://cafelinux.org/forum/index.php?topic=69.0").

Thank you all,
Rui

---

### Post by Tux Aubrey on 2009-10-05
> This package have now 2 maintainers, me and Bro.Tiag (a debian user)

OMG, this is one happy penguin!  Normal Service has resumed!

And I can confirm, for existing users, that these fixes will bring your systems completely up-to-date.  If you manually modified easy_e17.conf (as suggested by many of the posts above), you should accept the new ("package maintainer's") version.

I'll be testing the new packages on fresh installs of Ubuntu over the next couple of days and will report back.

Oh joy, oh joy.

---

### Post by kevdog on 2009-10-05
Huge news -- thanks to all you guys for your help!!!!

---

### Post by Rui Pais on 2009-10-09
> **Tux Aubrey said:**
>  If you manually modified easy_e17.conf (as suggested by many of the posts above), you should accept the new ("package maintainer's") version.

Thanks for the suggestions, Aubrey (you're always helpful!).
I add it to my post. 

I also toke the chance and update 1st post to do some cleanings and add a link to pertinent later posts on suggestions and workaround for any problems that may exist at time (this thread can be hard to read for new users due to it's size, so it will make things easier on new users).

Thank you All!

---

### Post by Aquastus on 2009-11-20
I need help. I installed entrance but I cant get it to work. Entrance says it needs an existing x session and entranced doesn't seem to exist.

---

### Post by nico_h on 2009-12-12
@Aquastus, I'm sorry I can't help you much.

Thanks again Rui Pais for your helpful post. I always find what I'm looking for !!

Well, almost : as I installed karmic, I would like to get rid of the ugly gdm and would like to try entrance, but I can't manage to get it compiled because the script (sudo easy_e17.sh --only=entrance) stops on that :

```
- entrance ................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for ANSI C header files... (cached) yes
checking for X... /usr/bin/X
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EVAS... yes
checking for ECORE... yes
checking for EDJE... yes
checking for ESMART... configure: error: Package requirements (
  esmart_container >= 0.9.0
  esmart_text_entry >= 0.9.0
) were not met:

No package 'esmart_container' found
No package 'esmart_text_entry' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables ESMART_CFLAGS
and ESMART_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/entrance.log'!

```

So I tried to set the PKG_CONFIG_PATH to /opt/e17/lib/pkgconfig (it exists, of course) but I get exactly the same result. Also I checked the pkg-config man page but have absolutely no idea how I can use it to solve the problem. And the /tmp/easy_e17/install_logs/entrance.log file contains more details on what it checked before stopping on the error, which doesn't bring much.

So, any clue ?

---

### Post by Tux Aubrey on 2009-12-12
Hi nico_h

I can't guarantee entrance (as I don't use it myself), but this should allow you to compile it with easy_e17.sh --only (but it may depend on which version of easy_e17.sh you are using and how up to date it is)

Open the easy_e17.conf file with a text editor as root:

eg:

```
gksudo gedit /etc/easy_e17.conf
```

Find "entrance," and delete it

Run

sudo easy_e17.sh --only=entrance

It _should_ make-install for you

I have no idea how to replace gdm with entrance - let us know if you can get it to work!

---

### Post by nico_h on 2009-12-12
Oh thanks, but well, I forgot to mention that, in order to run sudo easy_e17.sh --only=entrance, I first already deleted entrance from the easy_e17.conf file.

Now I'm running sudo easy_e17.sh -u just to see if it compiles better (maybe it will compile this missing dependance first ?).


EDIT: OH it writes it skips esmart, that's probably the reason it doesn't work !!! so I'll wait till it's done and rerun it with esmart also deleted from the easy_e17.conf
EDIT2 : yes, it did work ! after having deleted esmart from the skip list (in /etc/easy_e17.conf) I ran sudo easy_e17.sh --only=esmart and then sudo easy_e17.sh --only=entrance don't know how i hadn't found it alone earlier, too tired probably...

---

### Post by VCoolio on 2009-12-12
I think you need to delete esmart from the skipping list and / or add it to the packages list. Also a warning: I managed to get entrance working a few weeks ago, but when in e17 (or any other wm) I couldn't sudo or gksudo anything. Also there was a sound issue if I recall correctly. Anyway, I reinstalled karmic and vowed to never try entrance again. Then again, let us know if you get it going and how. It was way faster than gdm so with a right howto I might still break my oath.

---

### Post by nico_h on 2009-12-12
Installation worked fine.

About the getting it to work well I tried different ways but I'm still looking for an answer. There are many different ways depending on the year... moreover I have no idea if entrance is even bug-free enough to be used. Well... if I find a solution I'll post it here !

---

### Post by worldwithoutgurus on 2009-12-13
@nico_h

Entrance is old and buggy: DON'T use it!

Or use a specialized/hacked distro like Elive...

---

### Post by nico_h on 2009-12-13
:D you're everywhere, worldwithoutgurus ! very funny !! and so, thanks to you i've also got the answer for this topic :
[http://forum.ubuntu-fr.org/viewtopic.php?id=365477](http://forum.ubuntu-fr.org/viewtopic.php?id=365477) [fr]
so, thanks a lot ! et bonne journée ;)

---

### Post by bapoumba on 2010-01-03
Ping Rui Pais , smartboyathome and Tux Aubrey:

[http://ubuntuforums.org/showpost.php?p=8602579&postcount=69](http://ubuntuforums.org/showpost.php?p=8602579&postcount=69)
:KS

---

### Post by Triple Threat on 2010-01-10
After trying the easy_e17 script i found on the enlightenment page, i got an error when building eina:

```
- eina ....................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.3.1 CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
configure.ac:17: error: possibly undefined macro: AC_LIBTOOL_WIN32_DLL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:20: error: possibly undefined macro: AC_PROG_LIBTOOL
```

I found this page (and the other old one for cvs) mentioning this repo:

```
deb http://cafelinux.org/Downloads/oz-os tinwoodman main
```

I tried reloading my repo lists from synaptic and it timed out on this repo. Can anyone help me?

---

### Post by stanca on 2010-01-22
Rather E17-Ecomorph in Ubuntu Karmic Amd64? ;)

---

### Post by __init__ on 2010-01-27
> **Triple Threat said:**
> After trying the easy_e17 script i found on the enlightenment page, i got an error when building eina:

```
- eina ....................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.3.1 CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
configure.ac:17: error: possibly undefined macro: AC_LIBTOOL_WIN32_DLL
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.ac:20: error: possibly undefined macro: AC_PROG_LIBTOOL
```


Exactly the same problem here. Have any ideas?

---

### Post by alvarko on 2010-01-27
> **__init__ said:**
> Exactly the same problem here. Have any ideas?

Install libtool package.

---

### Post by __init__ on 2010-01-29
> **alvarko said:**
> Install libtool package.

Thank you!
Shame on me, I could have figured it out myself. For some reason I was sure I had libtool installed and thought it was autoconf issue.

---

### Post by Tux Aubrey on 2010-01-30
I can confirm that the cafelinux repos are back on line (and the forums) so any new install of e17 via Post#1 (or my tutorial at [http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os](http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os)) will work (tested on Karmic and Lucid alpha).

If you are having trouble updating because of error messages about "unversioned directories/folders", this is an issue with recent updates of e17 code.  You can safely delete those directories (from another terminal window or from your filemanager opened as root - they are all "illume..." directories in /var/cache/e17_src/e/src/modules/).

I am also having trouble with "ethumb" not compiling - but this is probably due to something I did to my setup because a new install on Lucid didn't have this problem.  If anyone else is experiencing this problem and has a solution I'd like to hear it.

---

### Post by joplass on 2010-02-09
After installing e17 I have my partitions on the desktop.  I can't mount them and I can't remove them.  Is there a way to mount partitions in e17?  If not, is there a way to stop them from appearing as icons on the desktop?

My installation did not install the trash module anybody knows the package or any other name of program that will give me trash?

Thank you,

---

### Post by joplass on 2010-02-11
solved

---

### Post by emendelson on 2010-02-13
> **joplass said:**
> solved

How???

---

### Post by Znix on 2010-02-16
svn: URL 'http://svn.enlightenment.org/svn/e/trunk/edje_editor' doesn't exist

Down?

---

### Post by Tux Aubrey on 2010-02-16
> **Znix said:**
> svn: URL 'http://svn.enlightenment.org/svn/e/trunk/edje_editor' doesn't exist

Down?

No, just someone decided to move the furniture without telling us blind people.

Unless you actually want or need the edje_editor tool (fairly useless IMO), the fix to use depends whether this is a new install or you are updating.

Both involve editing the easy_e17.sh file as root:

```

gksudo *yourtexteditor* /usr/bin/easy_e17.sh
```

eg. gksudo gedit /usr/bin/easy_e17.sh

Find and delete both references to edje_editor.

If you are updating a previously installed e17, you also need to delete the edje_editor directory in /var/cache/e17_src/

eg.

```
sudo rm -rf /var/cache/e17_src/edje_editor
```

You should then be able to use:

```
sudo easy_e17.sh -i
```

to fully update and (re)install e17.

Future updates won't require the editing (until the phantom furniture mover reappears)

---

### Post by Znix on 2010-02-17
Thank You!
Install completed as per your instructions!
-RZ-

---

### Post by joplass on 2010-03-07
> **emendelson said:**
> How???
Oh right.  Sorry about that I should have returned with my resolution steps.  Can't remember now.

---

### Post by yankeeDDL on 2010-03-12
Hello,

I'm trying to install this on Xubuntu 9.10.
Once I launch the installation, I get this:

searching for direct source url for 'eina'

The system just hangs there. Does it just take a long time (hours) or is it stuck somehow?

I think I'm using the right files: I searched for "edje_editor" in easy_e17.sh and I could not find any occurrence, therefore I suspect it has already been edited since the post above (by Tux Aubrey).

Suggestions?

---

### Post by TheZeusJuice on 2010-03-21
> **Tux Aubrey said:**
> No, just someone decided to move the furniture without telling us blind people.

Future updates won't require the editing (until the phantom furniture mover reappears)

Well, phantom furniture mover has struck again; esmart can no longer be found at [http://svn.enlightenment.org/svn/e/trunk/esmart](http://svn.enlightenment.org/svn/e/trunk/esmart)

edit:
Or to be more precise, easy_e17.sh right now hangs at "searching for direct source url for 'esmart' "

---

### Post by kevdog on 2010-03-21
I love this thread but wish it were updated.  Aubrey I need your help PLEASE!!

---

### Post by Tux Aubrey on 2010-03-22
Kevdog!  What is the problem?

I know that there have been changes to the svn but the new script appears to be able to cope with things moving around.  It does SEEM to hang for a while (eg looking for esmart) but it does (for me) eventually get things sorted out.

I'm also having some icon problems with some installs (but not others!).

Let me know what is troubling you and I'll try to help.

UPDATE: I have done a fresh install with the Lucid Xubuntu beta and the e17_svn script worked fine - but the "icon" problem is real - no ability to create new launch icons or edit existing ones via the built-in "Change Icon Properties" or "Create Icon" e17 tools. The cafelinux oz-e17-tools package is working fine (for better update control and backups)

---

### Post by Tux Aubrey on 2010-03-29
Further to my last update, the icon problem now seems to be fixed.  For me, that's the last annoying bug in e17 now gone bye-bye.  I therefore pronounce e17 (from svn) Absolutely Perfect, until the next breakage.

---

### Post by vallsit on 2010-04-01
Hi all!

I'm following the steps in the guide and it also hangs many time while "- searching for direct source url for 'esmart' ..."

How many time does it hangs? It's been hanged for more than fifteen minutes.

It seems that the problem is the easy_e17.sh found in the repo, it's outdated. I've done the following steps:

[FONT="Courier New"]sudo apt-get remove purge e17-svn
rm -rf /var/cache/e17_src
wget [http://omicron.homeip.net/projects/easy_e17/easy_e17.sh](http://omicron.homeip.net/projects/easy_e17/easy_e17.sh)
/bin/bash easy_e17.sh -i[/FONT]

And now it's perfectly installed, I just have one problem... I'm installing e17 in a Ubuntu Server and have installed the xserver-xorg and gdm through synaptics. But after a restart the login screen doesn't shows up. What could be happening?

Searching a little bit I saw the package xfonts-base was missing, so I performed 
[FONT="Courier New"]sudo apt-get install xfonts-base[/FONT]
and startx worked fine.

Now I have another problem, I don't see the icons in the application taskbar. I only see the Terminal (normal and as root) and Python icons. What could be happening?

---

### Post by Sylchat on 2010-04-19
I got the "searching for direct source url for esmart" message hanging during my "sudo apt-get install e17-svn"... So I CTRL+C, then "vi /usr/bin/easy_e17.sh" to remove 'esmart', and did "sudo easy_e17.sh -i".

Now I have the "searching for direct source url for 'exchange'" message hanging... so, CTRL+C, removed "exchange", launched "sudo easy_e17.sh -i" again...

Looking at "svn co", esmart and exchange are in e/trunk/packaging/debian/extras/, so the script may need to be adapted to install these.

---

### Post by VCoolio on 2010-04-19
> **Sylchat said:**
> I got the "searching for direct source url for esmart" message hanging during my "sudo apt-get install e17-svn"... So I CTRL+C, then "vi /usr/bin/easy_e17.sh" to remove 'esmart', and did "sudo easy_e17.sh -i".

Now I have the "searching for direct source url for 'exchange'" message hanging... so, CTRL+C, removed "exchange", launched "sudo easy_e17.sh -i" again...

Looking at "svn co", esmart and exchange are in e/trunk/packaging/debian/extras/, so the script may need to be adapted to install these.

No, the packaging stuff is probably a snapshot release (svn 45887); in the meantime esmart and apparently also exchange were removed (we're currently on svn 48133), so if you're building from bleeding edge svn like with the easye17 scripts you should remove them from the script like you did. 
If you suspect the script to be outdated, install e17-svn without building e17 immediately (you can do that by creating an empty file $HOME/_skip_easy_e17_install before you install e17-svn), then install e17-svn, compare the packages in the script with the svn tree [here]("http://trac.enlightenment.org/e/browser/trunk") and remove packages that aren't there anymore; then delete the skip file you created and run easy17.sh to build e.

---

### Post by Sylchat on 2010-04-21
I could find another repository on alphagemini.org (see [http://xsm.alphagemini.org/E17/repository/index.html](http://xsm.alphagemini.org/E17/repository/index.html)). It got installed easily on a clean Xubuntu 9.10 install (in VirtualBox). :popcorn:

---

### Post by Tux Aubrey on 2010-04-23
> **Sylchat said:**
> I could find another repository on alphagemini.org (see [http://xsm.alphagemini.org/E17/repository/index.html](http://xsm.alphagemini.org/E17/repository/index.html)). It got installed easily on a clean Xubuntu 9.10 install (in VirtualBox). :popcorn:

That repo is fine, but the build is nearly a year old - like the one in the official e17 repos.

The easy_e17 script installs the latest (to the minute) code - with all the enhancements and risks that entails. I do not recommend it for newbies!

While the current version of the script does take quite a long while to find any components that have been moved around in the svn (eg. esmart), my experience is that they WILL be found and installed OK.

I have run it on several installs of both karmic and lucid and the results have been excellent.  There have been recent problems with e17 but these are unrelated to the script AFAIK.  They have all disappeared with updates.

I'm pretty sure there will be another binary build of e17 "any day now" ;-) for those who prefer their installs via a simple apt-get.

---

### Post by chaosx9 on 2010-05-09
I have a problem in the scripe using the full package list, where elementary doesn't install (no build system error) and this causes a problem with python-elementary and shellementary

I've set the script to skip them as i'm typing this, but i'm not sure if anything will go wrong because of this.

Does anyone know how to do this?

---

### Post by VCoolio on 2010-05-09
Nothing will go wrong; you'll miss shellementary which is nice but you can just use zenity in your scripts. I don't know if python-elementary is used at the moment (shellementary is in C now). 
If you want them, you'll need to add TMP and PROTO to the 'trunk=' line (+/- line 35) in /usr/bin/easy_e17.sh. In the svn tree, elementary is in TMP/st/elementary, shellementary is in PROTO/shellementary. If you need python-elementary, it's in BINDINGS/python/python-elementary. 
You can also create those folders in /var/cache/e17_src and e.g. in /var/cache/e17_src/TMP/st/elementary do:
```
sudo svn co -r <your current svn chechout> http://svn.enlightenment.org/svn/e/trunk/TMP/st/elementary
```
Then run the script like 'sudo easy_e17.sh -s --only=elementary'. This way you don't have to rebuild all of e17 and you make sure elementary is the same svn version as the rest. Find your current svn build number by: 'head -n4 /var/cache/e17_src/e/.svn/entries | tail -n1' (unless you updated the source without building it).

---

### Post by chaosx9 on 2010-05-09
i don't see that line in the script i downloaded (i didn't use the same process as described, but downloaded easy_e17.sh from [http://omicron.homeip.net/](http://omicron.homeip.net/) )

---

### Post by VCoolio on 2010-05-09
The script this thread is about is a modified version of the one you have. Anyway, elementary is skipped now, only the packages on the lines with efl_basic= and bin_basic= will get installed (because they are included in packages_basic, which is default). So try this:

```
sudo easy_e17.sh -s --packages=packages_full --only=elementary
```

---

### Post by jacksterson on 2010-05-10
I get this error when trying to add the repos and update:

> Err [http://cafelinux.org](http://cafelinux.org) tinwoodman Release.gpg                                
  Could not connect to cafelinux.org:80 (70.89.127.134). - connect (110: Connection timed out)
Err [http://cafelinux.org/Downloads/oz-os/](http://cafelinux.org/Downloads/oz-os/) tinwoodman/main Translation-en_US
  Unable to connect to cafelinux.org:http:
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman Release
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Packages
Ign [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Packages
Err [http://cafelinux.org](http://cafelinux.org) tinwoodman/main Packages
  Unable to connect to cafelinux.org:http:
Fetched 3,942B in 26s (151B/s)
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6E871C4A881574DE
W: Failed to fetch [http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/Release.gpg](http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/Release.gpg)  Could not connect to cafelinux.org:80 (70.89.127.134). - connect (110: Connection timed out)

W: Failed to fetch [http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/main/i18n/Translation-en_US.bz2](http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/main/i18n/Translation-en_US.bz2)  Unable to connect to cafelinux.org:http:

W: Failed to fetch [http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/main/binary-i386/Packages.gz](http://cafelinux.org/Downloads/oz-os/dists/tinwoodman/main/binary-i386/Packages.gz)  Unable to connect to cafelinux.org:http:

E: Some index files failed to download, they have been ignored, or old ones used instead.
kaji@Katsuragi:~$ wget -q [http://cafelinux.org/Downloads/oz-os/key.asc](http://cafelinux.org/Downloads/oz-os/key.asc) -O- | sudo apt-key add -


And then its just hanging there without doing anything, any ideas why?

*EDIT* It appears cafelinux.org is down. :/

*EDIT 2*  Well, I tried installing using the easy_e17.sh from omicron following the instructions from the official wiki, but i keep getting a lua dependency error.  I'm just going to wait for the site to work, do I need to remove all the stuff i installed during it or ... what?  I'm not very good with the terminal and stuff, so Im not looking forward to this :/

*EDIT 3*
[COLOR="Red"]Ok I finally got it installed.  But its not showing up in the session manager in the login screen.  What do I do? :/[/COLOR]

---

### Post by stanks on 2010-06-04
[http://trac.enlightenment.org/e/wiki/Starting_from_a_graphical_login_manager](http://trac.enlightenment.org/e/wiki/Starting_from_a_graphical_login_manager)

---

### Post by Genesius on 2010-06-10
I installed e17-svn on a clean Lucid install. Only one problem - I can't get the regular Ubuntu Applications menu under E17. I found /etc/xdg/menus/applications.menu, but how do I get it to work with e17?

---

### Post by neonl on 2010-08-01
Haven't been here for a while! How alive is this project?

---

### Post by worldwithoutgurus on 2010-08-04
It's alive and kicking.

Alpha is just around the corner!

---

### Post by neonl on 2010-08-04
> **worldwithoutgurus said:**
> It's alive and kicking.

Alpha is just around the corner!

Great to hear. Also noticed that e17 evolved a lot since the last time I was active in these seas (back in the e17 CVS from Morlenxus scrip)! :popcorn:

---

### Post by worldwithoutgurus on 2010-08-06
Yep.

The libraries (EFL) are actively being worked upon by the devs - clean & polish, mostly. We'll have to wait a bit longer for an alpha of E though.

Raster's mail:
[http://marc.info/?l=enlightenment-devel&m=128113780709769&w=2](http://marc.info/?l=enlightenment-devel&m=128113780709769&w=2)

Stay tuned!

---

### Post by Khonsu on 2010-08-10
Hey,

So I'm running debian squeeze 64-bit. I used the svn code to install e17 and everything installed fine and everything seems to work perfectly except themes. It's using Black&White which I assume is the default theme for e17 and it won't let me install any new themes. I've tried importing them and get a error saying:

"Enlightenment was unable to import the theme.
Are you sure this is a valid theme?"

I've also tried moving them directly to the /themes folder and while they show up on the list, there is no preview and when I click okay, it refreshes, but keeps the default theme. I've tried the alternate themes that come in the repository as well as themes from various websites to the same effect.

Thank you for any help,
Khonsu

---

### Post by VCoolio on 2010-08-10
What kind of themes do you try? They should be .edj files; you can put them in ~/.e/e/themes and you can get them [here](http://exchange.enlightenment.org/) or [here](http://e17-stuff.org/) and one [here](http://code.google.com/p/detour/). Since development is fast, themes that aren't maintained can get outdated. If a theme has omissions, e falls back on the default theme for those items. Try themes starting with A- (by a guy that calls himself Agust) or detour; they are recent and/or maintained and should work.
If this doesn't work, try an update with the script (easy_e17.sh -u) and see if something was fixed.

---

### Post by Khonsu on 2010-08-10
Yes, I was using .edj files and ones by Agust. I've also tried updating as well as reinstalling e17 to no avail.

Okay, I noticed when updating I got this error:

> CRI: ecore_main.c:156 _ecore_main_fdh_epoll_add() eina_log_print() unknown domain -1, original message format 'adding poll on %d %08x'
CRI: ecore_main.c:375 ecore_main_fd_handler_add() eina_log_print() unknown domain -1, original message format 'Failed to add epoll fd %d!'


Could that have something to do with it? I f so, how would I go about fixing it?

---

### Post by worldwithoutgurus on 2010-08-11
There have been important changes in the edje file format recently. Wait until themers catch up with those changes.

[http://marc.info/?l=enlightenment-users&m=128146545018377&w=2](http://marc.info/?l=enlightenment-users&m=128146545018377&w=2)

E devs are busy cleaning/optimizing their code, so turbulences are expected before the alpha release... E svn freeze this weekend!

---

### Post by worldwithoutgurus on 2010-08-21
[B]ALPHA release of core Enlightenment Foundation Libraries (EFL)!

[http://marc.info/?l=enlightenment-devel&m=128236355428799&w=2](http://marc.info/?l=enlightenment-devel&m=128236355428799&w=2)

Enjoy![/B]

---

### Post by vadim s. sabinich on 2010-08-22
i have some problems ;-\

-> PREPARING FOR PHASE 2...
------------------------------- Easy_e17.sh 1.3.2 ------------------------------
...
--------------------------------------------------------------------------------
  Updates:         [http://omicron.homeip.net/projects/#easy_e17.sh](http://omicron.homeip.net/projects/#easy_e17.sh)
  Support:         #e.de, #get-e (irc.freenode.net)
                   [email]morlenxus@gmx.net[/email]
  Patches:         Generally accepted, please contact me!
--------------------------------------------------------------------------------


----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /home/vadim/e17_src/
  Source url:      [http://svn.enlightenment.org/svn/e/trunk](http://svn.enlightenment.org/svn/e/trunk)
  Source mode:     packages
  Logs path:       /tmp/easy_e17/install_logs
  OS:              Linux (Distribution: debian)

  Packages:        eina eet evas ecore efreet e_dbus embryo edje imlib2 ethumb emotion elementary enlil ewl libast libeweather python-evas python-ecore python-e_dbus python-edje python-ethumb python-emotion python-elementary shellementary exchange e e_phys eyelight editje elicit elitaire empower emprint enki ephoto Eterm expedite exquisite exalt image-viewer rage alarm calendar cpu deskshow diskio drawer efm_nav efm_path efm_pathbar emu exalt-client execwatch eweather flame forecasts iiirk language mail mem moon mpdule net news notification penguins photo places quickaccess rain screenshot skel slideshow snow taskbar tclock tiling uptime weather winselector wlan

  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation
- apps-compilation and installation
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- e_dbus ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- imlib2 ..................... previously installed
- ethumb ..................... previously installed
- emotion .................... previously installed
- elementary ................. no build system
- enlil ...................... previously installed
- ewl ........................ no build system
- libast ..................... previously installed
- libeweather ................ previously installed
- python-evas ................ python:  ERROR!
--------------------------------------------------------------------------------
----------------------------------- Last loglines ------------------------------
evas/evas.c_evas.c:81879: warning: implicit declaration of function &#8216;PyThreadState_GET&#8217;
evas/evas.c_evas.c:81886: warning: implicit declaration of function &#8216;PyTraceBack_Here&#8217;
evas/evas.c_evas.c: In function &#8216;__Pyx_InitStrings&#8217;:
evas/evas.c_evas.c:81896: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;p&#8217;
evas/evas.c_evas.c:81898: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;is_unicode&#8217;
evas/evas.c_evas.c:81898: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;is_identifier&#8217;
evas/evas.c_evas.c:81899: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;p&#8217;
evas/evas.c_evas.c:81899: warning: implicit declaration of function &#8216;PyUnicode_DecodeUTF8&#8217;
evas/evas.c_evas.c:81899: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;s&#8217;
evas/evas.c_evas.c:81899: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;n&#8217;
evas/evas.c_evas.c:81900: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;intern&#8217;
evas/evas.c_evas.c:81901: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;p&#8217;
evas/evas.c_evas.c:81901: warning: implicit declaration of function &#8216;PyString_InternFromString&#8217;
evas/evas.c_evas.c:81901: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;s&#8217;
evas/evas.c_evas.c:81903: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;p&#8217;
evas/evas.c_evas.c:81903: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;s&#8217;
evas/evas.c_evas.c:81903: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;n&#8217;
evas/evas.c_evas.c:81914: error: &#8216;__Pyx_StringTabEntry&#8217; has no member named &#8216;p&#8217;
evas/evas.c_evas.c: At top level:
evas/evas.c_evas.c:81923: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
evas/evas.c_evas.c:81929: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
evas/evas.c_evas.c:81975: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
evas/evas.c_evas.c:81984: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;*&#8217; token
evas/evas.c_evas.c:81998: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
error: command 'gcc' failed with exit status 1
--------------------------------------------------------------------------------

---

### Post by xircon on 2010-09-02
Have compiled E17, how the hell do I run it?  Logged off - no entry in my desktops menu.

:Edit: found it [https://help.ubuntu.com/community/InstallingE17Howto](https://help.ubuntu.com/community/InstallingE17Howto)

---

### Post by aircooledbusnut on 2010-09-03
used : sudo easy_e17.sh --only-elitaire

ended with this:
CRI: ecore_main.c:164 _ecore_main_fdh_epoll_add() eina_log_print() unknown domain -1, original message format 'adding poll on %d %08x'
CRI: ecore_main.c:585 ecore_main_fd_handler_add() eina_log_print() unknown domain -1, original message format 'Failed to add epoll fd %d (errno = %d)!'


Exalt doesnt seem to be installed.

Any ideas appreciated.

Clint

---

### Post by kaotika on 2010-09-09
I got the same errors after every install process. Obviously the most things are working correctly. After the Update i can't see any icons in the taskbar (TClock, Mem, IBox...) and no only the standard theme is working. Anyone with the same errors?

---

### Post by VCoolio on 2010-09-09
> **kaotika said:**
> I got the same errors after every install process. Obviously the most things are working correctly. After the Update i can't see any icons in the taskbar (TClock, Mem, IBox...) and no only the standard theme is working. Anyone with the same errors?

There were changes in the theme (edc) syntax, so you need to convert the old themes:
```
edje_convert theme.edj
```
I hope that helps.

---

### Post by kaotika on 2010-09-09
Wonderful, this solved the theme problem! :)

---

### Post by celticbhoy on 2010-09-15
Hi guys, no matter what method I try I keep getting 


- searching for direct source url for 'esmart' ...

and it just sits there.

Anyone know how to get round this ???

---

### Post by VCoolio on 2010-09-15
> **celticbhoy said:**
> Hi guys, no matter what method I try I keep getting 


- searching for direct source url for 'esmart' ...

and it just sits there.

Anyone know how to get round this ???

Delete it from /usr/bin/easy_e17.sh, it's no longer among us. You can check [here](http://trac.enlightenment.org/e/browser/trunk) if packages still exist or not, and where. The only really required packages are eina eet evas ecore efreet e_dbus embryo edje ethumb e, and eeze has been added lately, don't know if that's really necessary. The rest is for usability (some modules) and fun, and there are some applications you may or may not like.
Also consider a more up-to-date script, find it [here](http://omicron.homeip.net/projects/easy_e17/easy_e17.sh) or if you feel adventurous use the preview version [here](http://omicron.homeip.net/files/easy_e17_preview.sh)

---

### Post by celticbhoy on 2010-09-15
> **VCoolio said:**
> Delete it from /usr/bin/easy_e17.sh, it's no longer among us. You can check [here](http://trac.enlightenment.org/e/browser/trunk) if packages still exist or not, and where. The only really required packages are eina eet evas ecore efreet e_dbus embryo edje ethumb e, and eeze has been added lately, don't know if that's really necessary. The rest is for usability (some modules) and fun, and there are some applications you may or may not like.
Also consider a more up-to-date script, find it [here](http://omicron.homeip.net/projects/easy_e17/easy_e17.sh) or if you feel adventurous use the preview version [here](http://omicron.homeip.net/files/easy_e17_preview.sh)

Cheers mate :)

---

### Post by celticbhoy on 2010-09-15
OK, another problem, I am trying the preview build, but I have an issue when I create a .desktop file. I have no enlightenment_start in /opt/e17/bin how do I setup my .desktop file?

Sorry for being a pain in the **** :)

---

### Post by xircon on 2010-09-16
Just checked my install and yes the file is there.  You using 64 or 32 bit install?  If it is 64bit, I have it zipped (/opt/e17) 10mb:

[http://dl.dropbox.com/u/1286239/e17.zip](http://dl.dropbox.com/u/1286239/e17.zip)

Might work, might not :)

---

### Post by aircooledbusnut on 2010-09-18
Hi All,

I use slideshow for my desktop background.  I have looked and searched everywhere for information on batch conversion of .jpeg to .edj, any help would be greatly appreciated.  I will continue to do one picture at a time using add wallpaper for now.

Thanks
Clint

---

### Post by worldwithoutgurus on 2010-10-03
The Enlightenment Foundation Libraries (EFL) go beta:
[http://www.enlightenment.org/p.php?p=news/show&l=en&news_id=24](http://www.enlightenment.org/p.php?p=news/show&l=en&news_id=24)

Enjoy!

---

### Post by stanks on 2010-10-04
> **celticbhoy said:**
> OK, another problem, I am trying the preview build, but I have an issue when I create a .desktop file. I have no enlightenment_start in /opt/e17/bin how do I setup my .desktop file?

Sorry for being a pain in the **** :)

If you start from GDM/KDM/whatever, you simply copy enlightenment.desktop file from /opt/e17/share/xsessions/ into /usr/share/xsessions/ and restart gdm. you will need root perm for this.

---

### Post by KLStringer on 2010-10-10
Started working through the OP on a clean install and got to 



```

------------------------------ Installing packages -----------------------------
- eina ....................... ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.3.1.1-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------

Running autopoint...
./autogen.sh: 8: autopoint: not found
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.ac:25: installing `./config.guess'
configure.ac:60: required file `./config.rpath' not found
configure.ac:25: installing `./config.sub'
configure.ac:29: installing `./install-sh'
configure.ac:29: installing `./missing'
doc/Makefile.am:32: wildcard img/*.*: non-POSIX variable name
doc/Makefile.am:32: (probably a GNU make extension)
src/bin/Makefile.am: installing `./depcomp'
configure.ac:60: required file `./ABOUT-NLS' not found
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/ecore.log'!

dpkg: error processing e17-svn (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 e17-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Any help figuring this out is greatly appreciated

---

### Post by VCoolio on 2010-10-10
You'll need autopoint if you have maverick (ubuntu 10.10), else gettext; the problem is pointed out (or, autopointed) in this line:```
./autogen.sh: 8: autopoint: not found
``` You can use [this site](http://packages.ubuntu.com/search?suite=lucid&arch=any&searchon=contents&keywords=autopoint) to search for packages or package contents.
Edit: I see that maverick has the package e17 in the universe repo; that is outdated of course; but if you have maverick and universe repo enabled, do 'sudo apt-get build-dep e17' which will get you all building dependencies and then run the script again.

---

### Post by KLStringer on 2010-10-10
> **VCoolio said:**
> You'll need autopoint if you have maverick (ubuntu 10.10), else gettext; the problem is pointed out (or, autopointed) in this line:```
./autogen.sh: 8: autopoint: not found
``` You can use [this site]("http://packages.ubuntu.com/search?suite=lucid&arch=any&searchon=contents&keywords=autopoint") to search for packages or package contents.


Yes on 10.10 should have put that in my op, am running ```
sudo aptitude intall autopoint
``` now and its made it passed ecore, and pushing onward.

Thanks for the tip, been learning Linux by building Ubuntu servers at work over the last year and decided last night to put in on my laptop and get rid of 7.

Will post back on how it goes.

---

### Post by KLStringer on 2010-10-10
Got 2 Phase 2 and then things started going bad:


```

-> PREPARING FOR PHASE 2...ERR<12793>:e_dbus e_dbus.c:469 e_dbus_bus_get() Error connecting to bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/easy_e17.sh: line 766: 12793 Segmentation fault      $notifier -u "$urgency" -t 5000 -i "$install_path/share/enlightenment/data/images/enlightenment.png" -n "easy_e17.sh" "easy_e17.sh" "$text"

------------------------------- Easy_e17.sh 1.3.1.1-OzOS ------------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'amon' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
                   Roberto 'rex' Sigalotti

----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  Source path:     /var/cache/e17_src/
  Source url:      http://svn.enlightenment.org/svn/e/trunk
  Source mode:     packages
  Logs path:       /tmp/easy_e17/install_logs
  OS:              Linux (Distribution: debian)

  Packages:        eina eet evas ecore efreet e_dbus embryo edje esmart ethumb exchange e emprint alarm calendar cpu deskshow diskio drawer execwatch forecasts language mail mem net news notification places screenshot slideshow taskbar tclock uptime winselector wlan
  Skipping:        etk_extra esmart enhance exml imlib2 edb edje_editor edje_player edje_viewer emotion entrance eclair evfs evolve elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies expedite exquisite extrackt engage enthrall exalt exalt-client exhibit rage drawer emu flame moon news penguins rain snow language photo efm_path efm_nav e_phys mpdule notification b_and_w 

  Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation
- apps-compilation and installation
--------------------------------------------------------------------------------


------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- e_dbus ..................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- esmart ..................... SKIPPED
- ethumb ..................... autogen: ERROR!
ERR<14492>:e_dbus e_dbus.c:469 e_dbus_bus_get() Error connecting to bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/bin/easy_e17.sh: line 766: 14492 Segmentation fault      $notifier -u "$urgency" -t 5000 -i "$install_path/share/enlightenment/data/images/enlightenment.png" -n "easy_e17.sh" "easy_e17.sh" "$text"
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for ECORE_EVAS... yes
checking for ECORE_FILE... yes
checking for EDJE... yes

checking optional module emotion:
checking for EMOTION... no
no
optional module emotion failed checks.

Warning: optional module emotion disabled by extra checks.

checking optional module epdf:
checking for EPDF... no
no
optional module epdf failed checks.

Warning: optional module epdf disabled by extra checks.

checking optional module ethumbd:
checking for EDBUS... yes
optional module ethumbd passed checks.

checking whether libexif is built... yes
checking for LIBEXIF... no
configure: error: you need libexif development installed!
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/ethumb.log'!

dpkg: error processing e17-svn (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 e17-svn


```


EDIT:

In the ethumb.log it says

```
checking for doxygen... no
WARNING:
The doxygen program was not found in your execute path.
You may have doxygen installed somewhere not covered by your path.

If this is the case make sure you have the packages installed, AND
that the doxygen program is in your execute path (see your
shell manual page on setting the $PATH environment variable), OR
alternatively, specify the program to use with --with-doxygen.
configure: WARNING: no doxygen detected. Documentation will not be built
```

 and also 

```
checking whether libexif is built... yes
checking for LIBEXIF... no
configure: error: you need libexif development installed!

```

---

### Post by VCoolio on 2010-10-10
Again, use the site, or do 'sudo apt-get build-dep e17-svn'. I think that should get things running. Anyway, in this case, you need libexif-dev. Don't worry about the dbus errors.
Edit; I'm going to bed, so at least don't expect fast response from me from now on

---

### Post by KLStringer on 2010-10-10
```
INSTALL NOTES:
--------------------------------------------------------------------------------
The most incredible and really unbelievable dream has become true:
You compiled e17 successfully!

Starting e17:
If you're using a login manager (GDM/KDM), select the session type 'Enlightenment' in them.

Rasterman didn't write this script so don't ask him for help with it.

We hope you will enjoy your trip into e17... Have fun!

```


:guitar:\\:D/=D>

---

### Post by Genesius on 2010-10-18
Trying to install e17 on a new laptop, and get the following error:

```

------------------------------ Installing packages -----------------------------
- eina ....................... ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- eio ........................ ok          
- eeze ....................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ISO C89... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking whether to build documentation... yes
checking for doxygen... yes
checking for ECORE... yes
checking for LIBUDEV... no
configure: error: Package requirements (libudev) were not met:

No package 'libudev' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBUDEV_CFLAGS
and LIBUDEV_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Udev is installed, synaptic shows a package called libudev0 installed, but nothing just called libudev. Tried running "sudo apt-get build-dep e17" and get an error "E: Unable to find a source package for e17"

Any suggestions?

---

### Post by Genesius on 2010-10-18
*sigh* fix one problem and come up with another. . .

Went back into Synaptic and found a package called libudev-dev. Installing that fixed  the install problem. Logged out of Gnome & into E17, happy happy joy joy.

Shut down, came back a little later, Now when I log into E, I get a black screen. If I click, the menu pops up and I can launch programs. Tried to change to the default theme, my Gnome wallpaper flashed up briefly, then back to black.Since my Gnome wallpaper popped up, I assume something in E is tangled up with gdm, just not sure what to do about it.

---

### Post by VCoolio on 2010-10-19
You don't really need eeze (yet?), it's the e17 udev-based replacement for hal. Hal works just as well with e17 though (in some aspects even better; the places module needs hal afaik), but in the long run hal will be left. Also when compiling stuff, you always need to look for a -dev package when the process complains about a missing dependency. 

As for your problem, I'm not sure. The popping wallpaper is probably your root window; not to worry (if you do, use feh to change it, but you'll only profit from that with semi-transparant apps). Try to (re)move $HOME/.e and login to e again for a fresh start. If that doesn't help, it's something deeper than your current user settings.

---

### Post by Genesius on 2010-10-19
Yep, clearing out .e fixed it . . . for now, anyway.:)

---

### Post by maver1ck4000 on 2010-10-19
If anyone has been having problems getting ecore to run you might have to make a change to the configure.ac file. I kept getting an error about not being able to find Makefile.in.in

```

sudo nano /var/cache/e17_src/ecore/configure.ac

```
Line 1413
```

$po_makefile_in

```
Replace with:
```

po/Makefile.in

```

I was able to run the script and ecore worked. I am now failing at a different point. I have a feeling its going to be a similar problem.

---

### Post by Clint_Thomas on 2010-10-26
I get the following when building.

CRI: ecore_main.c:513 _ecore_main_loop_init() eina_log_print() unknown domain -1, original message format 'enter'
CRI: ecore_main.c:550 _ecore_main_loop_init() eina_log_print() unknown domain -1, original message format 'leave'
CRI: ecore_main.c:174 _ecore_epoll_add() eina_log_print() unknown domain -1, original message format 'adding poll on %d %08x'
CRI: ecore_main.c:238 _ecore_main_fdh_poll_del() eina_log_print() unknown domain -1, original message format 'removing poll on %d'

everything still seems to build Ok

---

### Post by slackthumbz on 2010-11-19
```
- ecore ...................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.3.1.1-OzOS CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
Running autopoint...
./autogen.sh: 8: autopoint: not found
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.ac:25: installing `./config.guess'
configure.ac:60: required file `./config.rpath' not found
configure.ac:25: installing `./config.sub'
configure.ac:29: installing `./install-sh'
configure.ac:29: installing `./missing'
doc/Makefile.am:32: wildcard img/*.*: non-POSIX variable name
doc/Makefile.am:32: (probably a GNU make extension)
src/bin/Makefile.am: installing `./depcomp'
configure.ac:60: required file `./ABOUT-NLS' not found
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/ecore.log'!

dpkg: error processing e17-svn (--configure):
 subprocess installed post-installation script returned error exit status 2
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 e17-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


:(

UPDATE: Installing autopoint seems to have fixed the initial problem now I'm getting:
```
./configure: line 28419: syntax error near unexpected token `;;'
./configure: line 28419: `$as_echo "$as_me: WARNING: cache variable $ac_var contains a newline" >&2;} ;;'
```

---

### Post by kevdog on 2010-12-19
Its sad when this post isnt maintained anymore.

---

### Post by VCoolio on 2010-12-19
> **kevdog said:**
> Its sad when this post isnt maintained anymore.

It's also that the repos aren't maintained anymore (or are they?). Anyway, you can still compile efl+e17 using an up to date [script](http://omicron.homeip.net/files/easy_e17_preview.sh), which is what installing e17-svn would do too. Copy the script to $HOME/bin or /usr/local/bin, make executable (chmod +x script) then run with --help flag for instructions, or to install for example with -i --srcrev=55246 (don't use sudo; wait for the script to ask for your password; else all will be built as root and sources downloaded to /root) to install efl beta 3 and snapshot version of the rest. Check for [dependencies](http://www.enlightenment.org/p.php?p=download&l=en) and [support](http://www.enlightenment.org/p.php?p=support&l=en). The script isn't officially supported, but you can ask about build failures.

---

### Post by Zezu on 2011-01-14
> **VCoolio said:**
> It's also that the repos aren't maintained anymore (or are they?).

Ive noticed that too. Is anyone else noticing a lack of updates? It seems like my e17 build is becoming less and less stable as other programs are upgraded....

---

### Post by Zezu on 2011-01-14
> **Zezu said:**
> Ive noticed that too. Is anyone else noticing a lack of updates? It seems like my e17 build is becoming less and less stable as other programs are upgraded....

The more i read the more i realize im behind the times and out of touch with current events. It looks to me like the developers are focusing on ubuntu 10.10 and 11.04. what about good old 10.04 lts? i left 10.10 because it was a headach to me. maybe things have changed in the last few months, but oy!

---

### Post by PelPix on 2011-03-18
I really like E17.  The repos are completely 404'd now.  Can someone make an easy guide for compiling and installing from SVN?  Or better yet, a PPA to do it for us?

---

### Post by VCoolio on 2011-03-18
[this](http://ubuntuforums.org/showpost.php?p=10258002&postcount=578) is easy, isn't it? Or [try bodhi](http://ubuntuforums.org/showthread.php?t=1693976).

---

### Post by smartboyathome on 2011-04-21
I just wanted to stop by and say that this should really be closed. The Cafelinux site went completely dead a while ago and I couldn't keep my server stable so I just shut it down as well. When Rui Pais left the project, it really died. As Vcoolio pointed out, there are better alternatives anyway.

---

### Post by sbubba on 2011-08-21
Hello
I've used easy_e17 script to compile e17 svn on ubuntu 10.04.3.
I've got several dependencies errors that I've solved with this topic, but now I got this error:
```
------------------------------ Installing packages -----------------------------
- eina ....................... previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- eio ........................ previously installed
- eeze ....................... previously installed
- e_dbus ..................... previously installed
- embryo ..................... previously installed
- edje ....................... autogen: ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
-------------------------------------------------------------------------------
EASY_E17 1.4.0 CMD: ./autogen.sh --prefix=/opt/e17  
-------------------------------------------------------------------------------
rm: impossibile rimuovere "autom4te.cache/output.0": Permesso negato
rm: impossibile rimuovere "autom4te.cache/traces.1": Permesso negato
rm: impossibile rimuovere "autom4te.cache/traces.0": Permesso negato
rm: impossibile rimuovere "autom4te.cache/requests": Permesso negato
rm: impossibile rimuovere "autom4te.cache/output.1": Permesso negato
Running aclocal...
autom4te: cannot open autom4te.cache/requests: Permesso negato
aclocal: autom4te failed with exit status: 1
--------------------------------------------------------------------------------

```
Google search didn't help me. Have you any ideas?
Thanks

ps: I apologize if I'm off topic, if necessary I'll open a new one :-P

---

### Post by VCoolio on 2011-08-22
Better start new topic, this one is all but closed. Anyway, a list of dependencies to build e on ubuntu: ```
apt-get install automake gcc make subversion pkg-config build-essential libtool doxygen zlib1g-dev libjpeg8 libjpeg8-dev libfreetype6-dev libudev-dev libdbus-1-dev liblua5.1-0-dev libxml2-dev libxext-dev libxrandr-dev dbus-x11 libxcomposite-dev libxcomposite1 libxdamage-dev libxdamage1 libxkbfile-dev libxkbfile1 libxkbfile-dev libxkbfile1 libxinerama-dev libxcursor-dev libxslt1-dev gettext mesa-common-dev libiptcdata-dev libexif-dev libpam-dev flex bison byacc libsdl1.2-dev
```
You should run the script without sudo; then it will ask for the sudo password itself and build stuff as user and only install as root. The build dirs will then be in ~/e17_src; if you ran the script with sudo before, you can "sudo rm -r /root/e17_src" (btw, always be careful with rm -r).
Try to "make clean distclean" inside the edje folder before trying again, or let the script do it: easy_e17.sh -c -c --only=edje.
Also make sure everything has the same svn revision. So for example check what revision is current (something like 62695) and then run the script like "easy_e17.sh --srcrev=62695 -i".
These are just general tips; your error sounds like it may not be solved by the above (except the run without sudo part maybe).

---

### Post by HappinessNow on 2011-12-23
> **Rui Pais said:**
> 

Essentially, what I propose is, reduce the number of available e apps to a minimum stable core, that gives the environment, 
and use apps more stable to the common tasks like file-manager, terminal, etc., available at repos.



**INSTALLATION**
Add the following repos to your /etc/apt/sources.list:


To do it automatically, copy+paste the above to a command line:
```
 sudo sh -c "echo 'deb http://cafelinux.org/Downloads/oz-os tinwoodman main' >> /etc/apt/sources.list"
```
and add the authenticated key with:
```
wget -q http://cafelinux.org/Downloads/oz-os/key.asc -O- | sudo apt-key add -
```



I get this message with that URL:

> Oops! Google Chrome could not find cafelinux.org

I think this thread may be obsolete?

---

