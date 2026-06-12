---
title: "Can't get started"
date: 2008-12-08
forum: Wine
---

### Post by mngsailing on 2008-12-08
Can't get anywhere in wine.

Linux is Hardy 8.04
Have installed Wine which is in my applications menu, but not in the panel above. 
1. Nothing happens when I go down Program > Accessories > Notepad
2. When I browse C:\drive, I get to drive_c.  I see Program Filea and Windows
3. When I click on "Configure Wine" nothing happens. 

In Terminal:
"wine" alone gives me a usage list, including wine --help
Now "wine --help" just gives me the same usage list. 
but "wine --version" responds with  wine-1.0 

In drive_c, within "Program Files" I have six directories
Common Files, Internet Explorer , MSNStockQuote, office10, superjpg, XLStart 

Back in Terminal, if I enter "wine iexplore.exe"
response is 
wine: chdir to /home/~/.wine
: No such file or directory

Can someone tell me the next step?  Thx

---

### Post by pytheas22 on 2008-12-08
It sounds like possibly the installation of wine got botched somehow.  Did you install it from the Ubuntu repositories (using 'apt-get' on the command-line or Synaptic Package Manager) or in some other way?

Also, if you run these commands, what happens:
```

wget http://downloads.sourceforge.net/notepad-plus/npp.5.1.1.Installer.exe?modtime=1226437459&big_mirror=0
wine npp*
```

Does an installer open?  If not, what is the output you get in the terminal?

---

### Post by mngsailing on 2008-12-08
Thanks for responding, Pytheas.  You helped me before I think. 
I did my last download from WineHQ.


I assume that was a zero at the end of the wget, not an Oh. 

After it saved the installer, it didn't go back to the prompt, so I ctl-C 'd it.  Then it said "Done"

wine app* gave the "normal" response of

wine: chdir to /home/~/.wine
 : No such file or directory.

---

### Post by mngsailing on 2008-12-08
More ....
I went through various hoops on this last installation.  I tried the GUI and got stuck putting in the respository, I think because the text was too long.  

So then I registered the repository using command line and the instructions from WineHQ. 

At one point, someone said I should set a WINEPREFIX.  So I tried to do that, but I don't know if it "stuck".

---

### Post by albinootje on 2008-12-08
Does ~/.wine not exist ? Did you run winecfg first ?

Another easy way to try different and newer wine-versions is PlayOnLinux :

[http://www.playonlinux.com/en/download.html](http://www.playonlinux.com/en/download.html)

It's not only aiming at games, i've tested Safari and some other software with it in the past. One nice thing about it is that can separate installations. Just like CrossOverOffice (bottles) and Bordeaux.

---

### Post by mngsailing on 2008-12-08
yes .wine exists
It contains 
dosdevices drive_c     system.reg userdef.reg user.reg

winecfg 
I never ran winecfg
 But I will now. 

I can run it out of ~ or out of ~/.wine 

In both cases it gives the same "normal" response.  
wine: chdir to /home/~/.wine
 : No such file or directory

---

### Post by mngsailing on 2008-12-08
My Software Sources in Synaptic Third Party lists WineHQ three times.  The third time if for Source Code.  I guess I'll delete the last two. 

Also going to bed now.  Talk more inthe morning, maybe.

---

### Post by mngsailing on 2008-12-08
When I try wineconfig it suggests I install kde-guidance

I think I don't have kde.  

In the morning, if you haven't any other suggestiosn I guess I'll uninstall wine and try again from zero.

---

### Post by pytheas22 on 2008-12-08
I'm not sure what's going on, but it is strange.

Unless you need to use a different version of wine for some reason, I would recommend just using the installer available in the standard Ubuntu repositories.  It sounds like you used an installer from a third-party site, which may be causing the problem.

To install wine using the standard package, you should first remove any third-party repositories related to wine using the utility at System>Administration>Software Sources.  Then type:
```

sudo apt-get update
```

to update your sources list.

Once that's done, install the standard version of wine by typing:
```

sudo apt-get remove --purge wine*
sudo apt-get install wine
```

If you have trouble removing the third-party repositories, please post the output of:
```

cat /etc/apt/sources.list
```

and we can figure out which ones to remove manually.

---

### Post by mngsailing on 2008-12-09
Am uncomfortable following your instructions.
Is it OK to go on?
----------------------------------------------------------------------

mng@mng-linux:~$ sudo apt-get update
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release.gpg
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Translation-en_CA                  
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy Release.gpg                           
Ign [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Translation-en_CA               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release.gpg                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                                  
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_CA                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_CA
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Release                             
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Translation-en_CA        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Translation-en_CA                        
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Translation-en_CA                          
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy Release                                                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_CA                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Translation-en_CA                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release.gpg           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Translation-en_CA
Ign [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                                      
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Translation-en_CA               
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy Release                       
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates Release                                                          
Hit [http://apt.wicd.net](http://apt.wicd.net) hardy/extras Packages                                              
Hit [http://ftp.osuosl.org](http://ftp.osuosl.org) hardy/ Packages                                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages          
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Reading package lists... Done
mng@mng-linux:~$ sudo apt-get remove --purge wine*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libwine-capi for regex 'wine*'
Note, selecting libchewing-data for regex 'wine*'
Note, selecting libchewing3-data instead of libchewing-data
Note, selecting libswing-layout-java for regex 'wine*'
Note, selecting matchbox-window-manager for regex 'wine*'
Note, selecting libopensg-windowx-dev for regex 'wine*'
Note, selecting libwine-alsa for regex 'wine*'
Note, selecting windows-el for regex 'wine*'
Note, selecting plplot9-driver-xwin for regex 'wine*'
Note, selecting libmono-winforms1.0-cil for regex 'wine*'
Note, selecting libchewing3-data for regex 'wine*'
Note, selecting winefish for regex 'wine*'
Note, selecting wxwin-i18n for regex 'wine*'
Note, selecting xwatchwin for regex 'wine*'
Note, selecting libwine-twain for regex 'wine*'
Note, selecting fte-xwindow for regex 'wine*'
Note, selecting kwin-style-comix for regex 'wine*'
Note, selecting kwin for regex 'wine*'
Note, selecting libwine-arts for regex 'wine*'
Note, selecting wxwin-doc for regex 'wine*'
Note, selecting kdeartwork-theme-window-kde4 for regex 'wine*'
Note, selecting xwininfo for regex 'wine*'
Note, selecting wings3d for regex 'wine*'
Note, selecting x-window-system-core for regex 'wine*'
Note, selecting kwin-decor-baghira for regex 'wine*'
Note, selecting avifile-win32-plugin for regex 'wine*'
Note, selecting freepwing for regex 'wine*'
Note, selecting x-window-system for regex 'wine*'
Note, selecting winesetuptk for regex 'wine*'
Note, selecting libchewing-dev for regex 'wine*'
Note, selecting scim-chewing for regex 'wine*'
Note, selecting windowlab for regex 'wine*'
Note, selecting libchewing2-dev for regex 'wine*'
Note, selecting kwin-style-suse2 for regex 'wine*'
Note, selecting libopensg-windowx for regex 'wine*'
Note, selecting libconfigwin-ocaml-dev for regex 'wine*'
Note, selecting libcameleon-ocaml-dev instead of libconfigwin-ocaml-dev
Note, selecting wine-utils for regex 'wine*'
Note, selecting libchewing for regex 'wine*'
Note, selecting libchewing3 instead of libchewing
Note, selecting kwin-style-knifty for regex 'wine*'
Note, selecting not+darwin for regex 'wine*'
Note, selecting type-handling instead of not+darwin
Note, selecting wininfo for regex 'wine*'
Note, selecting xfce4-windowlist-plugin for regex 'wine*'
Note, selecting kwin-style-alphacube for regex 'wine*'
Note, selecting libwine-jack for regex 'wine*'
Note, selecting matchbox-window-manager-maemo for regex 'wine*'
Note, selecting hwinfo for regex 'wine*'
Note, selecting grubutil-win32 for regex 'wine*'
Note, selecting wxwin2.4-doc for regex 'wine*'
Note, selecting libchewing3 for regex 'wine*'
Note, selecting xwine for regex 'wine*'
Note, selecting wxwin2.4-headers for regex 'wine*'
Note, selecting kwin-style-crystal for regex 'wine*'
Note, selecting libmono-winforms2.0-cil for regex 'wine*'
Note, selecting libopensg-windowx1 for regex 'wine*'
Note, selecting x-window-manager for regex 'wine*'
Note, selecting libchewing3-dev for regex 'wine*'
Note, selecting libwine for regex 'wine*'
Note, selecting kwin4 for regex 'wine*'
Note, selecting kwin-style-baghira for regex 'wine*'
Note, selecting libwine-ldap for regex 'wine*'
Note, selecting wine-dev for regex 'wine*'
Note, selecting avant-window-navigator for regex 'wine*'
Note, selecting wine-doc for regex 'wine*'
Note, selecting libwine-gphoto2 for regex 'wine*'
Note, selecting twinkle for regex 'wine*'
Note, selecting kwin-style-blended for regex 'wine*'
Note, selecting not+bsd-darwin for regex 'wine*'
Note, selecting type-handling instead of not+bsd-darwin
Note, selecting twin for regex 'wine*'
Note, selecting libwings-dev for regex 'wine*'
Note, selecting wine for regex 'wine*'
Note, selecting wing for regex 'wine*'
Note, selecting wink for regex 'wine*'
Note, selecting libwine-print for regex 'wine*'
Note, selecting kwin-style-dekorator for regex 'wine*'
Note, selecting openwince-jtag for regex 'wine*'
Note, selecting libgnome-window-settings1 for regex 'wine*'
Note, selecting kdeartwork-theme-window for regex 'wine*'
Note, selecting libwine-dev for regex 'wine*'
Note, selecting libwine-cms for regex 'wine*'
Note, selecting libwine-gl for regex 'wine*'
Note, selecting libswingworker-java for regex 'wine*'
Note, selecting libwine-esd for regex 'wine*'
Note, selecting kwin-kde4 for regex 'wine*'
Note, selecting libgnome-window-settings-dev for regex 'wine*'
Note, selecting wing-data for regex 'wine*'
Note, selecting kwin-style-powder for regex 'wine*'
Note, selecting wxwin2.4-i18n for regex 'wine*'
Note, selecting wxwin2.2-doc for regex 'wine*'
Note, selecting libwine-nas for regex 'wine*'
Note, selecting wxwin-headers for regex 'wine*'
Note, selecting winbind for regex 'wine*'
Note, selecting libswingworker-java-doc for regex 'wine*'
Note, selecting winpdb for regex 'wine*'
Note, selecting libswing-layout-java-doc for regex 'wine*'
Note, selecting openwince-include for regex 'wine*'
Note, selecting libchewing1-dev for regex 'wine*'
Note, selecting libwine-sane for regex 'wine*'
Note, selecting kwin-baghira for regex 'wine*'
Note, selecting kwin-style-serenity for regex 'wine*'
The following packages were automatically installed and are no longer required:
  libaudio2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte* compiz* compiz-gnome* fast-user-switch-applet* gnome-applets* gnome-control-center* gnome-panel* gnome-terminal*
  libgnome-window-settings1* nautilus* nautilus-cd-burner* nautilus-sendto* nautilus-share* ubuntu-desktop* winbind* wine*
0 upgraded, 0 newly installed, 16 to remove and 1 not upgraded.
After this operation, 75.8MB disk space will be freed.
Do you want to continue [Y/n]? 
----------------------------------------------------------------------
At this point I became distinctly uncomfortable
----------------------------------------------------------------------

---

### Post by mngsailing on 2008-12-09
Good Morning Pytheas

I am getting lost.

I have reinstalled per your instructions.  I tried a second install, because I was unsure if I had done it, and it said I had already the latest version. 

Now the Gnome Applications menu shows the Wine items under "Other" 
with the results of clicking them:
Browse C:\Drive                             Nothing happens
Configure Wine                              Nothing happens
Notepad                                     Nothing happens
Uninstall Wine Software                     Nothing happens

If, in terminal I now get
mng@mng-linux:~$ winecfg
wine: chdir to /home/~/.wine
 : No such file or directory

Worse is that the top part of the Places menu has been disabled. 
Clicking on Home Folder produces a box stating:  
Could not open location "file:///home/mng"
There is no default action associated with this location.

All the menu items show the extra /. 
It looks like nautilus has gone. Just like apt-get remove said it would remove it.  

Much of the System menu looks ok, but it is not all working. 
Preferences > preferred applications says:
Failed to execute child process "gnome-default-applications-properties" (No such file or directory) 

I'll give you a chance to think about this, and come back after lunch.

---

### Post by pytheas22 on 2008-12-09
ahhhh, I'm sorry...it seems like apt-get remove wine* matched a whole lot of things that I don't think it should have matched (and I don't know why it did), and you removed them all, which is bad.

So now we have two things to do: 1) reverse the damage that my command caused, then 2) fix the original problem.

You should be able to reinstall all the packages that you uninstalled earlier by typing:

```
sudo apt-get install libwine-capi libchewing-data libchewing3-data libswing-layout-java matchbox-window-manager libopensg-windowx-dev libwine-alsa windows-el plplot9-driver-xwin libmono-winforms1.0-cil libchewing3-data winefish wxwin-i18n xwatchwin libwine-twain fte-xwindow kwin-style-comix kwin libwine-arts wxwin-doc kdeartwork-theme-window-kde4 xwininfo wings3d x-window-system-core kwin-decor-baghira avifile-win32-plugin freepwing x-window-system winesetuptk libchewing-dev scim-chewing windowlab libchewing2-dev kwin-style-suse2 libopensg-windowx libconfigwin-ocaml-dev libcameleon-ocaml-dev wine-utils libchewing libchewing3 kwin-style-knifty type-handling wininfo xfce4-windowlist-plugin kwin-style-alphacube libwine-jack matchbox-window-manager-maemo hwinfo grubutil-win32 wxwin2.4-doc libchewing3 xwine wxwin2.4-headers kwin-style-crystal libmono-winforms2.0-cil libopensg-windowx1 x-window-manager libchewing3-dev libwine kwin4 kwin-style-baghira libwine-ldap wine-dev avant-window-navigator wine-doc libwine-gphoto2 twinkle kwin-style-blended type-handling twin libwings-dev wine wing wink libwine-print kwin-style-dekorator openwince-jtag libgnome-window-settings1 kdeartwork-theme-window libwine-dev libwine-cms libwine-gl libswingworker-java libwine-esd kwin-kde4 libgnome-window-settings-dev wing-data kwin-style-powder wxwin2.4-i18n wxwin2.2-doc libwine-nas wxwin-headers winbind libswingworker-java-doc winpdb libswing-layout-java-doc openwince-include libchewing1-dev libwine-sane kwin-baghira kwin-style-serenity
```

(This is just a list that I generated based on the output in your post showing which packages were removed by apt-get.)

Please let me know if this works, and solves the problems with broken menus, etc.  From there, it really should not be too hard to resolve the original issue of wine not working.

---

### Post by mngsailing on 2008-12-09
As a matter of precision, I didn't enter 
apt-get remove wine*
but 
apt-get remove --purge wine*

That might account for the generosity.

I put your install line in and it produced a response.  
sudo apt-get install libwine-capi libchewing-data libchewing3-data ---------  kwin-baghira kwin-style-serenity

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libwine-capi is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  wine
E: Package libwine-capi has no installation candidate
__________________________________________________________________

i.e. didn't work.  So I removed libwine-capi and submitted it again 

That complained similarly about wine pieces being already included in wine. 
So then I removed everything that included the letters -wine-
and got this. 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting libchewing3-data instead of libchewing-data
Package wxwin-i18n is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However, the following packages replace it:
  wx2.8-i18n wx2.6-i18n wx2.4-i18n
E: Package wxwin-i18n has no installation candidate

------------------------------------------------------------------------

I'm writing now on my Hardy (not Windows) and a little concerned that I could lose all of gnome if I shut down.  But so far it is holding up.

I think what we could do here is to reinstall the packages that it said it was going to remove, but using synaptic, so letting synaptic assemble the package pieces necessary at their current level. Would you agree?

---

### Post by pytheas22 on 2008-12-09
> I think what we could do here is to reinstall the packages that it said it was going to remove, but using synaptic, so letting synaptic assemble the package pieces necessary at their current level. Would you agree?

Yes, I agree.  Actually that's what I was hoping the 'apt-get' command would do (Synaptic is just a graphical front-end to apt-get).  You could try installing the individual packages via Synaptic and may have better luck, provided you have the patience to do that--but you will probably run into the same complaints about unresolvable or obsolete packages.  To get around these, you will need to do what you already tried--remove the problematic packages from the 'apt-get install' command or from the list in Synaptic.

It may make the most sense to open up Synaptic and go through the list of packages ten or so at a time.  This will make it manageable to work through package errors as they arise.  If you try to do the whole list at once, neither Synaptic nor apt-get will process any of the packages until the entire list is completely error-free, which will probably cause you a lot of frustration if you don't break the list down into smaller chunks.

Also, thanks for being patient with this; it was stupid of me not to check that 'apt-get remove --purge wine*' command myself before telling you to run it, and it's obviously screwed a lot of stuff up for you.  So thanks for not hating me too much for that mistake.

On the bright side, you're learning a lot about package management in Ubuntu :)

---

### Post by mngsailing on 2008-12-09
Don't worry, Pytheas.  I did all that Synaptic stuff (actually on my own initiative) and it seems to have worked fine.  I did not delete wicd which I use for wired connection. Everything is back. I can start a new terminal, etc, etc.  And yes, I am learning, which is one of the goals. 

I took a look at  - info apt-get remove --purge -  and could not see anything except perhaps in combination with remove it is super-powerful.  I think perhaps you might report this issue to the ubuntu people or higher up the linux chain. 

---------------------------------------------------------------------

So now we are back to how to uninstall this old wine 1.0 seeing that Applications > Other > Uninstall Wine Software   does nothing.  

I think I will see what Synaptic will do for me.  I deleted the wine package.  Programs are gone from the applications menu.
But ".wine" and its file contents remain there. Good!

There is another thread about deleting wine.  Will read it. 
It suggests that you have to RIGHT click wine in synaptic menus to get the configuration removed. Marked for complete removal. Executed.

I note that, for Hardy, 1.0.0  seems to be the latest version.  Don't think I want to move up to Intrepid.  Was there and got out. 

So now I will try to reinstall, using Synaptic.  There is sort of a problem with the Update button in Synaptic.  It is not clear how that is to be used or when. So I used it. Now I seem to have something.  Right clicking is sometimes useful, though never indicated. 

Thanks for so far. 

mngsailing

---

### Post by mngsailing on 2008-12-09
I get the feeling I have a valid installation now.  But no real progress.

If I go to an exe file in its home in drive_c, and I then RIGHT click, I get a menu that suggests I can open the exe with wine's program loader.  
But nothing happens. Is there some magic button that wine recognizes?"

---

### Post by pytheas22 on 2008-12-09
Some background information:> 
I took a look at - info apt-get remove --purge - and could not see anything except perhaps in combination with remove it is super-powerful.

> 
It suggests that you have to RIGHT click wine in synaptic menus to get the configuration removed. Marked for complete removal. Executed.

Actually the 'Mark for complete removal' option in Synaptic is the same thing as using the '--purge' argument with apt-get.  It removes configuration files as well as executables, and can be useful if you think you've broken a certain application by misconfiguring it.
> 
I think perhaps you might report this issue to the ubuntu people or higher up the linux chain.

The reason that everything went crazy doesn't have to do with the '--purge' argument.  It happened because I told you to use a regex in the apt-get command.  When you type 'apt-get remove --purge wine*', the * is supposed to tell apt-get to remove every package whose name begins with the letters 'wine'.

Unfortunately, when you ran the command, apt-get for some reason decided to match every package with the letters 'win' anywhere in their name.  I don't know why it ignored the 'e' in wine, and I don't know if this is a bug or if apt-get is supposed to behave this way.  I use regexes with apt-get a lot and have never seen it do something like this, but maybe I've just never been in the right situation.  I will check on it and report it if others can confirm that apt-get is not supposed to match regexes like that.

---

Anyway, as for the real problem, what output do you get from these commands
```

sudo apt-get remove wine
dpkg -s wine
dpkg --info wine
```

Don't actually agree to remove anything yet; please just let me know the output of those commands.

Also, please create a new user account (using the utility at System>Administration>Users and Groups) and log in under it.  Does can you run any Windows applications via wine under the new account?

---

### Post by mngsailing on 2008-12-10
Here is your point #1

---------------------------
mng@mng-linux:~$ sudo apt-get remove wine
[sudo] password for mng: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  winbind libaudio2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 55.0MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.
---------------------------------------------
mng@mng-linux:~$ dpkg -s wine       
Package: wine
Status: install ok installed
Priority: optional
Section: otherosfs
Installed-Size: 53680
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 1.0.0-1ubuntu4~hardy1
Replaces: libwine-alsa, libwine-arts, libwine-capi, libwine-cms, libwine-esd, libwine-gl, libwine-gphoto2, libwine-jack, libwine-ldap, libwine-nas, libwine-print, libwine-sane, libwine-twain, wine-doc, wine-utils, winesetuptk, xwine
Depends: binfmt-support (>= 1.1.2), libasound2 (>> 1.0.14), libaudio2, libaudiofile0 (>= 0.2.3-4), libc6 (>= 2.4), libesd-alsa0 (>= 0.2.35) | libesd0 (>= 0.2.35), libgl1-mesa-glx | libgl1, libglu1-mesa | libglu1, libgphoto2-2 (>= 2.4.0), libgphoto2-port0 (>= 2.4.0), libice6 (>= 1:1.0.0), liblcms1 (>= 1.15-1), libldap-2.4-2 (>= 2.4.7), libsm6, libx11-6, libxau6, libxext6, libxml2 (>= 2.6.27), libxslt1.1 (>= 1.1.20), libxt6, libxxf86vm1, winbind
Pre-Depends: dpkg (>= 1.14.12ubuntu3)
Suggests: msttcorefonts, xdg-utils
Conflicts: binfmt-support (<< 1.1.2), libwine, libwine-alsa, libwine-arts, libwine-capi, libwine-cms, libwine-esd, libwine-gl, libwine-gphoto2, libwine-jack, libwine-ldap, libwine-nas, libwine-print, libwine-sane, libwine-twain, wine-doc, wine-utils, winesetuptk, xwine
Conffiles:
 /etc/xdg/menus/applications-merged/wine.menu d15dadc3527b2c6dca96023a5351aedc
Description: Microsoft Windows Compatibility Layer (Binary Emulator and Library)
 Wine is a compatibility layer for running Windows applications on Linux.
 Applications are run at full speed without the need of cpu emulation. Wine
 does not require Microsoft Windows, however it can use native system dll
 files in place of its own if they are available.
 .
 This package includes a program loader for running unmodified Windows executables
 as well as the Wine project's free version of the Windows API for running programs
 ported from Windows.
 .
  Homepage: [http://www.winehq.org/](http://www.winehq.org/)
Original-Maintainer: Scott Ritchie <scottritchie@ubuntu.com>
-----------------
mng@mng-linux:~$ dpkg --info wine
dpkg-deb: failed to read archive `wine': No such file or directory

-----------------------------------------------------------------------
Your point #2 

The new member of our team is called winehunter
He has a home. 
He has wine in the Applications menu
None of the top three wine items seem to do anything.
There is no drive_c visible.  He cannot configure his wine.
/home/winehunter has 8 directories from desktop to videos

In ~/documents/superjpg there is a file superjpg.exe that I have lent him.  This file has Properties > Open With -  "Wine Windows Program Loader".  So when I right click that superjpg.exe and then OPEN - nothing happens. 
All this is to say that winehunter has the same operating situation that I have. Looks identical, except he has no c:\drive. 

He may resume this conversation.

---

### Post by mngsailing on 2008-12-10
Perhaps I should mention that this machine went through two installations of Intrepid before I abandoned that route and went with Hardy.

The Hardy installation I tried to install on top of the Intrepid (not in clean partitions) because there was a printer driver in I that I wanted to keep.  However, I never tried to install wine in the Intrepid phase.

---

### Post by pytheas22 on 2008-12-10
It looks like you can safely remove the wine package.  So I would go ahead and type:
```

sudo apt-get remove --purge wine
sudo apt-get install wine
```

This will give you a fresh installation and with any luck will clear up the whole problem.  If not, we'll try the next thing.

The point of testing out wine under a new account was to see whether the problem was user-specific or system-wide.  It's clear now that it's the latter, which makes it harder to fix, but at least we have a better idea of what we're dealing with.
> 
The Hardy installation I tried to install on top of the Intrepid (not in clean partitions) because there was a printer driver in I that I wanted to keep. However, I never tried to install wine in the Intrepid phase.

How did you downgrade from Intrepid to Hardy?  Did you force it to use the Hardy repositories or something?  That could definitely have something to do with what's going on.

---

### Post by mngsailing on 2008-12-10
I have done a new installation and everything is as before. No response.

The only change I notice is that winehunter's Applications menu shows his wine menu under Other.  And under Other, Notepad is direct, and does not go through Programs > Applications like it does for me. 

In fact, winehunter does not have any "Programs" item.  
Request to browse the C:Drive does not do anything. 
He does not seem to have a c:drive, but I do. 

------------------------------------------------------------------------

I can't tell you too much about the installation of Hardy. I am a beginner and was getting frustrated about the PPTP wired connection problem in Intrepid.  I just put in a CD that had had an MD5 check, and I no longer remember any messages.

My notes say I was then trying to get wireless to work
I tried to get driveragent_488.exe to run but it didn't go 
unshield did not help
Then I tried madwifi and installed the madwifi tools for hardy.  Then I abandoned that and installed wicd, which works for me now. 
I got an error DSDT.aml not found somewhere near here. 
I also installed subversion
My wireless driver is now ath9k, under wicd.

------------------------------------------------------------------------

Text of the recent re-installation will follow.  Sorry to take so much of your time.

---

### Post by mngsailing on 2008-12-10
The reinstallation ----------------------
mng@mng-linux:~$ sudo apt-get remove --purge wine
[sudo] password for mng: 
Sorry, try again.
[sudo] password for mng: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  winbind libaudio2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wine*
0 upgraded, 0 newly installed, 1 to remove and 1 not upgraded.
After this operation, 55.0MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 122690 files and directories currently installed.)
Removing wine ...
Purging configuration files for wine ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
mng@mng-linux:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  msttcorefonts
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/7401kB of archives.
After this operation, 55.0MB of additional disk space will be used.
Selecting previously deselected package wine.
(Reading database ... 122071 files and directories currently installed.)
Unpacking wine (from .../wine_1.0.0-1ubuntu4~hardy1_i386.deb) ...
Setting up wine (1.0.0-1ubuntu4~hardy1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

---

### Post by mngsailing on 2008-12-11
Another thing is that my machine is often running at 50% processor when it not doing anything I know of.  It might be waiting for a network printer.

---

### Post by mngsailing on 2008-12-11
Do U want to run this machine from there?  If so, pls advise how I can open it for you.

---

