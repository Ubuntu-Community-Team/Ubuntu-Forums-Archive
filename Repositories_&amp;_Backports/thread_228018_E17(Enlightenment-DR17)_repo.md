---
title: "E17(Enlightenment-DR17) repo"
date: 2006-08-02
forum: Repositories &amp; Backports
---

### Post by Hawkwind on 2006-08-02
I run the website [http://seerofsouls.com](http://seerofsouls.com) which for years has been the largest 3rd party repo for Mandriva.  Now, I'm proud to announce that I'm expanding and building deb packages.

The first repo is now up and running and everyone is welcome to give it a try.  The repo is for the E17 (Enlightenment-DR17) window manager.  

E17 is a window manager that many users have requested there be debs for over the past year or so.  So here they are.  SoS will be building weekly builds if not more than just once a week.  These debs are built directly from a daily/nightly CVS checkout so that the latest and greatest stuff is always built into the packages.  We encourage you to try these packages and let us know what you think about them, or even if you have any problems.

All you have to do is visit [http://seerofsouls.com](http://seerofsouls.com) and click on the 'Deb Packages' tab at the top of the page.  It explains how to add the repo and what command you should do to install the majority of E17.  I have a contact form on the site as well if you have any issues or comments.

I hope to see much feedback from everyone about this new E17 repo.

```
deb http://SeerOfSouls.com/ dapper e17
```

Then to install the basics, perform this command:

```
sudo apt-get install enlightenment emodules0-all
```

Enjoy and can't wait for everyones responses to these great packages!

---

### Post by Kelvin on 2006-08-02
Thank you Hawkwind!  =D> =D> =D> 

It's very gracious of you to give server room to this and the E17 debs are a fantastic beginning!

Thanks again. I look forward to loading and new set of E17 debs tonight.

Kelvin

---

### Post by mgsfan on 2006-08-02
I get this when trying to install the packages
(Reading database ... 147173 files and directories currently installed.)
Unpacking enlightenment (from .../enlightenment_1%3a0.16.999.032-0cvs20060801_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/enlightenment_1%3a0.16.999.032-0cvs20060801_i386.deb (--unpack):
 trying to overwrite `/usr/share/xsessions/enlightenment.desktop', which is also in package enlightenment-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/enlightenment_1%3a0.16.999.032-0cvs20060801_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by philip5 on 2006-08-02
Looks like you have an old version (E16 or E17) of Enlightment installed that the install want to write a session file for your DM in the same place:

/usr/share/xsessions/enlightenment.desktop

If you are also using E16 then maybe you could rename or delete that file before trying to install E17. If you delete it then you might not to be able to log into E16 if that's what you are using. So renameing it and the session variables in it might be a better choice. If you have an old verision of E17 installed then you can just delete the file.

Hope this helps.

/Phil

---

### Post by mgsfan on 2006-08-02
well seeing as I never had any version of enlightenment installed..its odd how I got it..

---

### Post by ElvisThePelvis on 2006-08-02
Same basic error below. Your repo is using the name "enlightenment" for the e17 packages. That is the same name used by e16 in the multiverse repo. You need to change the name from enlightenment to something else to avoid confusion.

```

(Reading database ... 91146 files and directories currently installed.)
Unpacking enlightenment (from .../enlightenment_1%3a0.16.999.032-0cvs20060801_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/enlightenment_1%3a0.16.999.032-0cvs20060801_i386.deb (--unpack):
 trying to overwrite `/usr/share/xsessions/enlightenment.desktop', which is also in package enlightenment-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/enlightenment_1%3a0.16.999.032-0cvs20060801_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Hawkwind on 2006-08-02
You need to include in your install command the enlightenment-data app as well.  That will fix the problem.

---

### Post by Hawkwind on 2006-08-02
I have both installed currently.  E17 installs to /usr/local/bin and enlightenment installs to /usr/bin

---

### Post by Hawkwind on 2006-08-02
Though I do agree I think we need to change the name to stop confusion.  Hopefully we will have a new build tomorrow to help eleviate this problem.  Thanks for the suggestion as it only makes the repo better for everyone :)

---

### Post by philip5 on 2006-08-03
the namething should be resolved so you don't get confused when installing E17 as a few files remain in the apt-cache from E16, among them is enlightenment-data which is a E16 package and seam to conflict with enlightenment which is the Enlightenment 17 main app. The easiest thing might include a conflict setting between those packages we enlightenment (E17) is built on our part.

Right now the solution is not to install or have the enlightment-data package installed as it's not part of E17 but old E16 and conflicts with the sessionfile.

Regards,

Phil

---

### Post by MegaHz on 2006-08-03
i got the same error
apt-get remove enlightenment 
apt-get -f install
does not work
how do I reinstall/remove it sot hat I dont get any errors in apt-get?

thanks in advance

---

### Post by Hawkwind on 2006-08-03
The new 'enlightenment' package has been built and should now fix the problem with the enlightenment-data error everyone was getting.

Sorry for the problems as this is a learning experience and I do hope to get feedback once again from everyone.

---

### Post by AndyAWS on 2006-08-03
```
enlightenment:

Package enlightenment has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

```

```
enlightenment-data:

Package enlightenment-data has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

```

Looks like your repo's package list may need to be updated.

Looking at your Packages.gz and .bz2, enlightenment and enlightenment-data are not listed.

---

### Post by Hawkwind on 2006-08-04
Sorry guys, seems rsync didn't do the job it was supposed to.  It looks like the list is now updated once again.

Please bear with me as this is all new to me so I'm still in the learning stages.

Let me know if there are any further problems/issues.

---

### Post by up2date on 2006-08-04
hi thanks it didn't work for me last night, but it worked for me this morning like seven hours ago
could you also add other modules like engage so it will be easy to install?
:eek:

---

### Post by Hawkwind on 2006-08-04
sudo apt-get install engage   That should install it for you as it's in the repo :)

---

### Post by Adler on 2006-08-05
Hawkwind,

I discovered E17 when I was looking @ eLIVE -- [http://www.elivecd.org/](http://www.elivecd.org/), which was a pure Debian based project. I never got the install going because of Hardware issues, but the Desktop was better than anything that I'd ever seen and that included MAC. And better than aything Linux or M$ out of the box.

I've done your install, but have found there is no main menu and can not add the apps that I have running with Dapper. 

This is not a complaint, just a little feedback. 

Adler

---

### Post by philip5 on 2006-08-05
Adler
You should have a shelf (name of the main taskbar in E) at the bottom of your screen with a yellow E to press for startmenu or just click with your left mouse button on any empty space on your desktop and the menu should roll out. If not, did you get any error when you installed? You could try with backing upp your /home/user/.e directory before deleting it and logg into e17 again and let it config a new .e which will be with default settings. 

When it comes to menuediting then the best way is to use the Entangle app that for this moment isn't included in the build just yet. I have it built here and will get it uploaded on the SoS repo this weekend. Just want to test this new build first before it goes into the main repo.

Then just a pointer. E17 is still in development and everything that is built does not work as it should, are unfinished or are very unstable so the repo should only be used to get around to see what is to come. Some apps and features might not be in the final so just keep that in mind when using the cvs build.

Hope this helps and as always, have fun!

Phil

---

### Post by Adler on 2006-08-05
Phil,

Firstly, great work in bringing this to UBUNTU! Enlightenment is a great Desktop. 

When I received your reply I dropped out of GNOME and went to E17. I can't find /Home, or any apps other than Terminal, FF, GIMP, and some type of e-Mail app. I did play around a bit, and I had rain coming down from the clouds into fire. 

[IMG]http://img262.imageshack.us/img262/9383/20060805102137lo8.png[/IMG]

I took this screen shot with the E17 app and it did save it to my /Home directory.

Having fun? Always... And, thanks for your efforts.

---

### Post by philip5 on 2006-08-05
Adler
I see that you like bling bling on your desktop with fire, rain and stuff. Have you tried the Bling module too? It need the Composite extension in X11 enabled to work. If you don't know how to do it then just:

```
sudo apt-get install libxcomposite1 xcompmgr transset
```

and then add the following to your /etc/X11/xorg.conf in an own new section  or to a previous 'Section "Extensions"' if you have one in the conf. It doesn't matter where in the conf you add it as long as it's not in an other section of settings for something else.

```
Section "Extensions"
	Option "Composite" "true"
EndSection
```

That will give you nicer dropshadow effects that you can tweek in the Bling module settings.

Effects with composite extension also work in KDE 3.5.4 (only version i tried with) and if you want to see what it looks like then after this start KDE (or E17), Open Konsole and type 'xcompmgr -c' and you will have drop shadows in KDE. To stop the effects hit ctrl+c in the konsole where xcompmgr is running. Read the man pages for more options with compmgr and you can tweak its settings and behaviour. Then with xcompgr running type 'transset .2' in a konsole (where .2 is the amout of transparency) then click on a window on screen for the effect. If you are happy with a xcompmgr setting then end the command with '&' and xcompmgr will run in the background untill killed. To kill manually do 'killall xcompmgr'.

Example settings for run and set xcompmgr in the background with fade and shadow effects:

```
xcompmgr -cCfF -r7 -o.65 -l-10 -t-8 -D7 &
```

That was abit about that.

Nice with feedback on the build but the real glory goes to the developers...

As always, have fun!

Phil

---

### Post by Adler on 2006-08-05
Phil,

I seem to have all the latest code. But, have no luck with getting the menus or apps that I want. Here I mean a full menu of apps.

Meanwhile, back to UBUNTU and trying to edit the Banner @ [www.jjmacey.net](www.jjmacey.net). I'm dedicating the site to Linux and all the help -- or as you say -- the people that have done all the *hard*work before us.

As I used to say in the SuSE Forums. I'm still having fun!

---

### Post by Hawkwind on 2006-08-05
Are you talking about customizing your menu you get when you left click on the desktop ?  If so, you can go to ~/.e/e/applications/favorite/ and put things there.  You can add directories and/or files and then they will show up on the left click menu under the top option Favorite Applications.

There is also an app on sourceforge.net called e17genmenu that you can use to create these for you from your system.

---

### Post by philip5 on 2006-08-05
e17genmenu is part of the e_utils package and will be available when the repo is updated with the new builds.

/Phil

---

### Post by Adler on 2006-08-05
Hawkwind,

I can not leave my UBUNTU Desktop right now. I did pull down and tried to install e17genmenu, but it did not work. As it stands I'm not able to find Home or a Main Menu.

I do know that this is a work in progress and I'll now go back to listening to --

sudo apt-get install streamtuner
sudo apt-get install streamripper

Good work from your side.

Adler

---

### Post by Adler on 2006-08-05
Phil,

Thanks -- great work. BTW -- do you know Streamtuner? Great music to record.

Adler

---

### Post by Hawkwind on 2006-08-06
New build has been uploaded tonight.  This now includes the e_utils stuff which includes e17genmenu for those of you who are wanting to populate your menus.  This also includes entangle which can help you do the same.

---

### Post by timfelgentreff on 2006-08-06
Trouble is, enlightenment always kept its name (as a package) when moving onto a new realease. And the official repo will be set up just the same. Besides: E-17 works great here, luv it - I just switched to Dapper from Elive (which I had been using for over a year), but the elive repo didnt have the new shelf-code. And I LOVE the shelf

---

### Post by philip5 on 2006-08-06
timfelgentreff
Nice that you like the builds even though not everything is stable yet and can be broken from build to build when unlucky.

Your concern about when final E17 get released and these builds shouldn't be a problem as you will get the highest (and latest) version number when keeping E17 in a repo. If you have it in more than one repo apt will automatically fetch the one with the highest version number if not told otherwise. The cvs build of E17 have a version number of 16.999.032 so far and when the final is out on official repos it will have 17.x and will override these files. 

The first goal of the E17 repo on SoS is to deliver cvs builds untill E17 is in official repos and then we'll see if there is any demand after more cvs builds after that.

Hope this clears out any questions about that.

As always, have fun!

Phil

---

### Post by Adler on 2006-08-06
Hi,

I still can not manage to get a "Menu" going with all the apps that I have or find /Home.

What I think I'll do is a complete un-install and try again. Can some one let me know how to remove Enlightenment? TIA.

Adler

---

### Post by philip5 on 2006-08-07
adler,
if you want to remove the e17 debs then run:
```
sudo apt-get remove enlightenment libeet0 libepeg0 
```
That should remove all debs with dependencies in the builds.

Then you could reinstall everything you like to make sure you have the latest debs installed and as you want them.

/Phil

---

### Post by up2date on 2006-08-07
e17genmenu segfaulted for me but seems to have generated the menu properly..
entangle seems to crash when i right click on the icons
everything else seems good
is it possible to also have an engage-dev version
because i want a transparent-black background and i read that i have to change the sources then compile it

---

### Post by Hawkwind on 2006-08-07
Adler...

What exactly are you referring to when you say you can't find /home ??  Are you referring to a file manager like konqueror or something ?  If so, you can run konqueror or whatever other file manager within E17.  Also, if you left click on the desktop and in that menu go to Configuration -> Test File Manager that is E17's file manager.  As far as apps i the menu, you need to run e17genmenu to populate the 'Favorite Applications' you see when you left click on the desktop.  That is the top option.

---

### Post by szadek on 2006-08-07
I'm getting this error when trying to use the Software Preferences installation program from within Ubuntu

> [i]
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

---------
[http://SeerOfSouls.com/dists/dapper/e17/binary-amd64/Packages.gz:](http://SeerOfSouls.com/dists/dapper/e17/binary-amd64/Packages.gz:) 302 Found
---------
[/i]

Also, I recieved this error with one of your commands.

>  **Terminal**
[i]szadek@szadek-laptop:~$ sudo apt-get install enlightenment emodules0-all
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package emodules0-all[/i]


I'm beginning to believe that the amd64 distro of Ubuntu isn't ready for prime time due to barely anything working with it.

---

### Post by Adler on 2006-08-08
Hi Hawkwind,

I've just run -- sudo aptitude remove enlightenment libeet0 libepeg0, and also uncommented SoS from from apt sources list. Then did a sudo aptitude update, sudo aptitude dist-upgrade.

I was not able to find a home directory / menu no matter what I tried. **This** is a fully updated UBUNTU Box. I have had experience with eLive and am not sure if that was E17 or E18. That is a thing of beauty, but didn't want to install it. It had none of the support that UBUNTU -- or guys like you -- offer.

I'll wait a few days and then try the install again.

Adler

---

### Post by loell on 2006-08-08
i believe e18 has not yet started as e17 is not finish.

---

### Post by Adler on 2006-08-08
Loell,

As I mentioned -- in my corrected post -- I wasn't sure if I worked with eLive E17 or E18. Thanks for the comments.

**This** is a cool new Desktop offering!

Adler

---

### Post by loell on 2006-08-08
its been quiet a while now, e17 started 3 to 4 years ago, i'm not just sure though. what makes my jaw drop is its meticuluos developers who carefully selects code algorithms, thats makes it fast and eye candy possible :)

---

### Post by Hawkwind on 2006-08-08
szadek - Unfortunately we do *not* have 64Bit packages so the URL you used above isn't valid because we don't offer them.

Adler - I'm still a bit confused as to what you are meaning when you say you can't find a */home*  If you are familiar with konqueror, run it and you can browse your files like normal.  Or even with nautilus as E17's file manager is *not* completed yet.  There is one that works very well, but it's missing a lot of the features that nautilus or konqueror have, mainly because they've been around so long.

When you left click on your desktop(as in left click on the wallpaper) what happens ?  I don't see how you aren't getting a menu as that is default.  If E is installed, then the menu is there.   Is there a way you can take a screenshot of your desktop once inside of E17 ??  I'd like to see what all you have there currently and maybe that can help me a bit more see what's going on.

---

### Post by Adler on 2006-08-08
Hawkwind,

Let me do a fresh install of E17 and I'll get back to you. I do not think that Konquerer was an option in the menu that was given to me -- only Firefox. There was no file browser, and before I came to UBUNTU I used SuSE and KDE as my Desktop. I'm pretty well known in both the SuSE Forums, but sort of new to posting in the UBUNTU Forum. But, I have to say UBUNTU is far better than either openSuSE or SLED (SuSE Linux Enterprise Desktop), that I bought!

Please let me know the full install instructions. And, I'll try again.

Adler

---

### Post by Kiwi-Hawk on 2006-08-08
Hi All

I'm not sure where I should be but this is as close as I have been for a bit getting at E17,.. I run Mepis,,. which I belive is now Ubuntu based and all my repo's are from Ubuntu

I'm going to give you a screen cap of the term responce I got try it install from the update point:

root@0[Kiwi-Hawk]# apt-get update
Get:1 [http://apt.mepis.org](http://apt.mepis.org) mepis Release.gpg [191B]                                                                             
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]                                                                       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]                                  
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]                          
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [189B]                        
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis Release                                                            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release                                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release                                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages                                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages                                              
Ign [http://SeerOfSouls.com](http://SeerOfSouls.com) dapper Release.gpg                                              
Hit [http://SeerOfSouls.com](http://SeerOfSouls.com) dapper Release                            
Hit [http://SeerOfSouls.com](http://SeerOfSouls.com) dapper/e17 Packages 
Ign [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages   
Hit [http://SeerOfSouls.com](http://SeerOfSouls.com) dapper/contrib Packages
Hit [http://SeerOfSouls.com](http://SeerOfSouls.com) dapper/contrib Packages                   
Hit [http://SeerOfSouls.com](http://SeerOfSouls.com) dapper/e17 Packages                       
Hit [http://apt.mepis.org](http://apt.mepis.org) mepis/main Packages                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages                                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages                                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages                                                                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages                                                                
Fetched 5B in 6s (1B/s)                                                                                                         
Reading package lists... Done
root@0[Kiwi-Hawk]# apt-get install enlightenment emodules0-all
Reading package lists... Done
E: Invalid record in the preferences file, no Package header
root@0[Kiwi-Hawk]# 

I'm not sure I can use emodules0-all to search in Snyaptic and get a differnt responce,.. but I figure if it's broke in Apt it's all broke right?

Now befor you kick me out I guess we become a bit like the half breed,.. no place to go,.. Mum's a Mepis and dad's an Ubuntu and the repos start and finish with Ubuntu sources. So hope you don't mind me dropping by

Edit:
heres my preferences File case it helps
Package: *
Pin: release o=MEPIS
Pin-Priority: 901

Package: *
Pin: release o=Ubuntu
Pin-Priority: 800

# Package: enlightenment
# Pin: version 0.16.999*
# Pin-Priority: 999

# Package: libimlib2
# Pin: version 1.2.2*
# Pin-Priority: 999

I commented out the other E-17 Repo I had there

Comments don't work I found it's downloading as I type,.. I cut the commented part out
altogether

Cheers
Kiwi-hawk

---

### Post by Adler on 2006-08-08
Kiwi-Hawk,

I almost have to laugh -- this is not a reflection on your post -- but my total confusion -- I'm dealing right now with both my Site Hosting service and looking at your post. Man, Do I know what I'm doing any more? Consider me a SuSE escapee. Again, LOL.

As I said before I'll wait a few days to get back to E17. But, I'm sure that it will be there.

Meanwhile, trying to get my site up or at least editable.

Adler

---

### Post by Kiwi-Hawk on 2006-08-08
Hi

I got an Install of E BUT it's DR-16-7.2 not E-17

So I guess im back to the drawing board again

Cheers
Kiwi-Hawk

---

### Post by szadek on 2006-08-08
> **Hawkwind said:**
> szadek - Unfortunately we do *not* have 64Bit packages so the URL you used above isn't valid because we don't offer them.


k, That's what I figured.  That url came from copying and pasting your instructions, seems Ubuntu AMD64 automatically adds that directory.

Looks like I'll be going back to Windows XP L8s!

---

### Post by xplode_me on 2006-08-08
I did a  sudo apt-get install engage but only get this when starting engage (apt-get install did well):

```
joel@boxy:~$ engage
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        In function:

        ewl_engine_new();

Given engine name dosen't exist.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        In function:

        ewl_init();

Unable to initialize engine.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_destroy();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.

*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_title_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_name_class_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_borderless_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_shaped_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_post_render_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_pre_render_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_delete_request_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_mouse_out_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_mouse_in_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_focus_out_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_get()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!

Falha de segmentação

```

Falha de segmentação = segmentation fault :)

---

### Post by Hawkwind on 2006-08-08
Kiwi-Hawk - First of all, E17 won't be labeled as E17.  It's actually 0.16.999.032 at the moment.  Secondly, I honestly doubt the build we built for Ubuntu is compatible with Mepis or not.  I truly don't know the answer.

Adler - Konqueror will *not* be an option in E17 from any menu by default until you run e17genmenu and populate your menus.  You can however hit alt-esc and that will bring up a run dialog box just like alt-f2 does in KDE.  Then you can type 'konqueror' to start konqueror from there.  This 'run command' is also available when you left click on the desktop and you'll see the option there for it too.

---

### Post by Kiwi-Hawk on 2006-08-08
Hi

Hawkwind 

I understand and am aware of what you say as far as version numbering goes,.. but I am lostas to how I got 16.7.2 as a version number. I would have exspected 0.16.999.032 as you say. This build of Mepis is using Ubuntu 6 files I believe my repo list is mostly Ubuntu sources.

The install went like a charm and there was not a hitch at all I'm jus lost as to the version I got should I have had the preference's for E-17 added before i started do you think, I took them out as you had not mentioned them

Edit:
Hawkwind sujested I do the following command: (command and result)

root@0[Kiwi-Hawk]# apt-cache policy enlightenment
enlightenment:
  Installed: 1:0.16.7.2-3ubuntu1
  Candidate: 1:0.16.7.2-3ubuntu1
  Version table:
     1:0.16.999.032-0cvs20060806 0
        500 [http://SeerOfSouls.com](http://SeerOfSouls.com) dapper/e17 Packages
 *** 1:0.16.7.2-3ubuntu1 0
        800 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
        100 /var/lib/dpkg/status


I had to remove  [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages from my repo list
and apt-get update

then same command: (and result)

root@0[Kiwi-Hawk]# apt-cache policy enlightenment
enlightenment:
  Installed: (none)
  Candidate: 1:0.16.999.032-0cvs20060806
  Version table:
     1:0.16.999.032-0cvs20060806 0
        500 [http://SeerOfSouls.com](http://SeerOfSouls.com) dapper/e17 Packages
     1:0.16.7.2-3ubuntu1 0
        100 /var/lib/dpkg/status

then 

root@0[Kiwi-Hawk]# apt-get install enlightenment emodules0-all

and it's all there the only thing to fix now is segfault with gant theme thats easy don't use it for now <smile>

Edit: Gant theme was a bad download and is fine now

Hope this will help others that still get E16 Like maybe Adler

Cheers
Kiwi-Hawk

---

### Post by Kiwi-Hawk on 2006-08-09
> **xplode_me said:**
> I did a  sudo apt-get install engage but only get this when starting engage (apt-get install did well):

```
joel@boxy:~$ engage
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        In function:

        ewl_engine_new();

Given engine name dosen't exist.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        In function:

        ewl_init();

Unable to initialize engine.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_destroy();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.

*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_title_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_name_class_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_borderless_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_shaped_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_post_render_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_pre_render_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_delete_request_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_mouse_out_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_mouse_in_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_callback_focus_out_set()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!


*** ECORE ERROR: Ecore Magic Check Failed!!!
*** IN FUNCTION: ecore_evas_get()
  Input handle pointer is NULL!
*** NAUGHTY PROGRAMMER!!!
*** SPANK SPANK SPANK!!!
*** Now go fix your code. Tut tut tut!

Falha de segmentação

```

Falha de segmentação = segmentation fault :)

Looks like what I get when I try run edj_edit <filename>.edj to make edj's for apps
not the same but close

Cheers
Kiwi-Hawk

---

### Post by philip5 on 2006-08-11
There are some problems with segment fault and errors with ewl engines in tha past few builds but this next build will fix most of those problems. 

Uploaded a screenshot of what the latest builds look like that I hope will be up on the repo this weekend after a few tweaks with them. Hope you like what you see. It's just too bad the screencapture module catch some artifacts and doesn't catch the nice translucent dropshadow effects from the Bling module so you need to try that yourself to see that... :)

As always, have fun!

Phil

PS. You see E17s mediaplayer eclair, the file manager entropy, and the image viewer also in the e17 cvs. Only firefox in the screen that's not a E17 app...

---

### Post by loell on 2006-08-12
wow the shelf is nice, in the menus, the labeled "Generated menus" is from e17genmenu?

---

### Post by Kiwi-Hawk on 2006-08-14
Hi

I tried to run entropy and got the following code. my install seed to go well but I'm thinking simoit underneath is very badly broken

_________________________________________________________________

Kiwi-Hawk@0[~]$ entropy
Config dir is: '/home/Kiwi-Hawk//.e/entropy'
Looking for version in '/home/Kiwi-Hawk//.e/entropy/eetentropy.cfg'..
Size ret is: 10
***** Config fine - 14 matches 14
Loading '/usr/share/entropy/plugins//posix.so'...
Cannot connect to evfs server with 'evfs_fs', making new server and trying again..
Failure to start evfs server!
Reading plugins from: /usr/lib/evfs/plugins/file
Loading plugin: /usr/lib/evfs/plugins/file/samba.so
The plugin at '/usr/lib/evfs/plugins/file/samba.so' handles 'smb'
Initialising the samba plugin..
Samba stat func at '0xb7fdca50'
Loading '/usr/share/entropy/plugins//mime.so'...
Loading '/usr/share/entropy/plugins//imlib_thumbnailer.so'...
Loading '/usr/share/entropy/plugins//layout_ewl_simple.so'...
Loading plugin: /usr/lib/evfs/plugins/file/posix.so

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        In function:

        ewl_engine_new();

Given engine name dosen't exist.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        In function:

        ewl_init();

Unable to initialize engine.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_destroy();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_list_destroy();

        With the parameter:

        list

        being NULL. Please fix your program.
Loading '/usr/share/entropy/plugins//ewl_local_icon.so'...
The plugin at '/usr/lib/evfs/plugins/file/posix.so' handles 'file'
Initialising the file plugin..
Reading plugins from: /usr/lib/evfs/plugins/meta
Loading plugin: /usr/lib/evfs/plugins/meta/extractor_tagger.so
Loading '/usr/share/entropy/plugins//structure_viewer.so'...
Loading '/usr/share/entropy/plugins//system_thumbnailer.so'...
Loading '/usr/share/entropy/plugins//action_simple.so'...
Loading '/usr/share/entropy/plugins//layout_etk_simple.so'...
Etk Warning: etk_main.c, 88: etk_init: Edje initialization failed!
Loading '/usr/share/entropy/plugins//ewl_list.so'...
Loading '/usr/share/entropy/plugins//remote_thumbnailer.so'...
Loading '/usr/share/entropy/plugins//distrib_thumbnailer.so'...
Loading '/usr/share/entropy/plugins//etk_structure_viewer.so'...
Loading '/usr/share/entropy/plugins//etk_list.so'...
Loading '/usr/share/entropy/plugins//metadata_extract.so'...
Loading '/usr/share/entropy/plugins//etk_metadata.so'...
Loading '/usr/share/entropy/plugins//etk_iconbox.so'...
Loading '/usr/share/entropy/plugins//etk_trackback.so'...
Registered layout: 0x8061db8
Registered global layout 0x8061db8...
Plugin IDs as: 'Simple file backend'
Going to next plugin.../usr/share/entropy/plugins//posix.so
Plugin IDs as: 'Simple MIME identifier'
Going to next plugin.../usr/share/entropy/plugins//mime.so
Plugin IDs as: 'Simple MIME plugin for images'
Going to next plugin.../usr/share/entropy/plugins//imlib_thumbnailer.so
Plugin IDs as: 'ewl'
Removing plugin from list../usr/share/entropy/plugins//layout_ewl_simple.so
Plugin IDs as: 'Icon View'
GUI event callback (Icon View) registered as: 0xb7e34a47
Going to next plugin.../usr/share/entropy/plugins//ewl_local_icon.so
Plugin IDs as: 'File system tree structure viewer'
GUI event callback (File system tree structure viewer) registered as: 0xb7e2e12c
Going to next plugin.../usr/share/entropy/plugins//structure_viewer.so
Plugin IDs as: 'Simple system thumbnailer (folders, known types, etc)'
Going to next plugin.../usr/share/entropy/plugins//system_thumbnailer.so
Plugin IDs as: 'Simple action execution plugin'
Going to next plugin.../usr/share/entropy/plugins//action_simple.so
Plugin IDs as: 'etk'
Going to next plugin.../usr/share/entropy/plugins//layout_etk_simple.so
Plugin IDs as: 'List View'
GUI event callback (List View) registered as: 0xb7e17d1a
Going to next plugin.../usr/share/entropy/plugins//ewl_list.so
Plugin IDs as: 'Simple MIME plugin for images'
Going to next plugin.../usr/share/entropy/plugins//remote_thumbnailer.so
Plugin IDs as: 'Central object distribution thumbnailer'
Going to next plugin.../usr/share/entropy/plugins//distrib_thumbnailer.so
Plugin IDs as: 'File system tree structure viewer'
GUI event callback (File system tree structure viewer) registered as: 0xb7da7d38
Going to next plugin.../usr/share/entropy/plugins//etk_structure_viewer.so
Plugin IDs as: 'listviewer'
GUI event callback (listviewer) registered as: 0xb7d9c70f
Going to next plugin.../usr/share/entropy/plugins//etk_list.so
Plugin IDs as: 'libextract based metadata provider'
Going to next plugin.../usr/share/entropy/plugins//metadata_extract.so
Plugin IDs as: 'ETK slide metadata plugin'
GUI event callback (ETK slide metadata plugin) registered as: 0xb7d961d9
Going to next plugin.../usr/share/entropy/plugins//etk_metadata.so
Plugin IDs as: 'iconviewer'
GUI event callback (iconviewer) registered as: 0xb7d9060a
Going to next plugin.../usr/share/entropy/plugins//etk_iconbox.so
Plugin IDs as: 'trackback'
GUI event callback (trackback) registered as: 0xb7d8b69b
Going to next plugin.../usr/share/entropy/plugins//etk_trackback.so
Registered layout: 0x808e4b0
 ******* Layout registered itself to receive events
 ******* Layout registered itself to receive events
 ******* Layout registered itself to receive events
 ******* Layout registered itself to receive events
 ******* Layout registered itself to receive events
 ******* Layout registered itself to receive events
  Registered meta plugin for 'image/png'...
  Registered meta plugin for 'images/jpeg'...
  Registered meta plugin for 'image/gif'...
  Registered meta plugin for 'video/x-ms-wmv'...
  Registered meta plugin for 'application/msword'...
  Registered meta plugin for 'application/pdf'...
  Registered meta plugin for 'application/vnd.ms-excel'...
  Registered meta plugin for 'application/x-gtar'...
  Registered meta plugin for 'text/html'...
  Registered meta plugin for 'video/mpeg'...
  Registered meta plugin for 'video/x-msvideo'...
  Registered meta plugin for 'application/x-gtar'...
  Registered meta plugin for 'application/x-bzip2'...
  Registered meta plugin for 'video/quicktime'...
  Registered meta plugin for 'video/x-ms-asf'...
  Registered meta plugin for 'object/undefined'...
Loading plugin: /usr/lib/evfs/plugins/meta/audio_tagger.so
Object for // is 0x809f5d0....
ETK stuff setup! *******
Initialising ETK structure viewer...0x80a07a0
Object for /home/Kiwi-Hawk is 0x80a1e10....
Initialising ETK structure viewer...0x80a31e8
Object for // is 0x80a4488....
Initialising ETK structure viewer...0x80a5678
Initialising ETK list viewer...0x80a6ac8
Going to main..
Init ETK main...
Kiwi-Hawk@0[~]$   Registered meta plugin for 'audio/x-mp3'...
. EVFS metadata initialise..
Loading pre-existing metadata root..
..Loaded group list..
Printing group list:
Name: Pictures, Desc: Pictures
Name: Video, Desc: Video
Name: Audio, Desc: Audio
Done..
Current version is: 4
DB Init complete..
Allocated 0
Client 0, Client Disconnected!!!
Received disconnect for client at evfs_fs_samba.c for client 0
Received disconnect for client at evfs_fs_posix.c for client 0
Scanning monitors for client and removing...
Scanning file:///home/Kiwi-Hawk..
List returned: 88
Kiwi-Hawk@0[~]$ 

_________________________________________________________________

I'm not a programmer so I don't know where to start to work this out

Cheers
Kiwi-Hawk

---

### Post by philip5 on 2006-08-18
You can't fix the ewl problem that with what you have as the problem depends on that it miss a module for evas. It will be fixed with the updates that will be up on the repo soon. Right now I only can say, be patient... :)

Regards,

Phil

---

### Post by fuscia on 2006-08-21
pass the crack pipe, i'm in! 

thanks.

---

### Post by Adler on 2006-08-21
philip5,

I'm still listening here...

Adler

---

### Post by philip5 on 2006-08-22
the reason why the update takes some time is that e17 is taking some api changes right now that breaks parts of the software. I'm waiting a bit so the developers get things back on track again. We could release builds without the modules if that is something you would like anyway? I think it's better to give it a little more time...

Adler, was you thinking about something else?

/Phil

---

### Post by tzulberti on 2006-08-23
Thanks for the debs. I have installed and it is very eye candy.

---

### Post by philip5 on 2006-08-27
There will likely be new debs from yesterdays cvs of e17 up on the SoS repo during this Sunday. They are just going through a few final tests before hitting the main repo. There are though some things to know about the recent builds of e17. It have taken some api changes and it also have change where (and I also think how) configs for e17 are written. You might want to backup your old $home/.e and $home/.ecore also delete them before the update and then let e17 make you a new configset when you login to your brand new e17 builds.

If you 'sudo apt-get install eutils' then you can run e17genmenu to make you a menu from items found on your system. There is also a file manager (entropy) in the works that are more or less stable but tryable. It installs by 'sudo apt-get install entropy'.

You will need new updated versions of your themes too as due to the changes the previous versions of themes will not work or render e17 more unstable. 

This release of new build also lacks some modules and they are: engage, cpu, evolume, calendar, devian, mbar and wlan. These modules are not properly fixed to work with the new api:s yet so they will be added as soon as they work again.

The problem with ewl that was in the previous build is fixed so you can now try e17 apps that use the ewl libs. Remember that those are also under development and more or less unstable. You can find apps built for e17 in the repo packagelist or make a 'apt-cache search enlightenment' to have a list of old and new stuff. (Old stuff won't work with new though...)

As always, have fun!

/Phil

---

### Post by tzulberti on 2006-08-27
The following error appears when i try to open exhibit:
Etk Warning: etk_main.c, 96: etk_init: Etk_Engine initialization failed!
Could not init etk. Exiting...

---

### Post by philip5 on 2006-08-27
exhibit and some other apps are a little messy in the build that are on the site right now but that will be fixed when the new builds get up there...

---

### Post by tzulberti on 2006-08-28
I have tried to update e17 today, and i gettin this error:

"
The following NEW packages will be installed:
  emodule0-winselector libdirectfb-0.9-22 libecore0-desktop libecore0-directfb
  libetk0-engine-evas libetk0-engine-evas-software-x11 libetk0-engine-evas-x11
  libevas0-engine-fb libevfs0-plugin-file-posix libewl0-engine-evas
  libewl0-engine-evas-software-x11 libewl0-engine-x11
The following packages will be upgraded:
  eclair edb-tools edje0-bin elicit embryo0-bin emodule0-screenshot
  emodules0-all emotion0-bin enlightenment entropy epeg0-bin eutils evfs0-bin
  ewl0-bin examine exhibit libecore0 libecore0-con libecore0-config
  libecore0-dbus libecore0-evas libecore0-fb libecore0-file libecore0-ipc
  libecore0-job libecore0-txt libecore0-x libedb1 libedje0 libeet0 libembryo0
  libemotion0 libengrave0 libepeg0 libepsilon0 libesmart0 libetk0 libevas0
  libevas0-engine-buffer libevas0-engine-software-generic
  libevas0-engine-software-x11 libevas0-loader-eet libevas0-loader-jpeg
  libevas0-loader-png libevas0-saver-eet libevas0-saver-jpeg
  libevas0-saver-png libevfs0 libewl0 libexml0 libimlib2
51 upgraded, 12 newly installed, 0 to remove and 0 not upgraded.
Need to get 16.7MB/16.7MB of archives.
After unpacking 5763kB of additional disk space will be used.
Do you want to continue [Y/n]? y
"

Then it downloads all the files, but there is this message:
"Unpacking replacement libexml0 ...
Errors were encountered while processing:
 /var/cache/apt/archives/libevfs0-plugin-file-posix_0.0.1-0cvs20060826_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
"

How can i solve it?

---

### Post by philip5 on 2006-08-29
my guess is that the deb packages somehow got damaged/corrupted during download. try to manually delete /var/cache/apt/archives/libevfs0-plugin-file-posix_0.0.1-0cvs20060826_i386.deb and make a new update and it will download it again. (or maybe a bit overkill run a 'sudo apt-get clean'. If that doesn't work then let me no as there should be anything wrong with it.



/Phil

---

### Post by hollowhead on 2006-08-29
Thanks you guys installed E17 last night without issues.  Prefer it to DR16.9 which I never could get my head round.  Seems OK don't like the default theme though and trying to work out how to use it the guide at getE org is pretty good though.  Is it possible to put icons the desktop and whare can I get e icons?  how do I update E peroidically from your site?

---

### Post by philip5 on 2006-08-29
Hallowhead, good to hear that you like it and that the debs from the repo worked as they should for you.

If you want to get automatically updates the just add a line with:

```
deb http://SeerOfSouls.com/ dapper e17
```
to your /etc/apt/source.list and then you will get notice about availiable updates of E17 from the SoS site as with any other update from the main *ubuntu repo. (there should be a space before and after "dapper" in that line)

/Phil

---

### Post by Duncan_Idaho on 2006-08-29
thanks for the repo man!
I installed E17 the other day with no problems at all
today I upgraded the packages and didn't get any errors in the installation, but I haven't tested it today, I mean the upgraded E17
for the little I have used it so far it has worked flawlessly so thank you very much for the packages and I really apreciate your work mantaining the repo! :mrgreen:

---

### Post by hollowhead on 2006-08-30
Cheers mate.

---

### Post by Shane10101 on 2006-08-30
Grrr!  Don't you hate when you take too long to write a post, & it disappears into the ether(net)?!  :mad: 

Okay, the gist of my long-lost question:

I'm really diggin' e17, and I'm trying to find out what I gain (or give up) by running Ubuntu with e17 (instead of Gnome), vs running the Debian-based eLive distro.  

I like the fact that, as a n00bie, Ubuntu seems so "easy to use" in terms of updating/upgrading, with regular releases from the well-established Ubuntu team, & things like "sudo" to keep it dummy-proof.  Unfortunately, I also want to have the lightest-possible OS; and by uninstalling all the packages that I _don't_ need from Ubuntu, I have to uninstall "ubuntu-desktop" as well...which I think means I'm missing out on some of the "ease-of-use" that drew me to Ubuntu in the first place.  (What exactly am I giving up by uninstalling "ubuntu-desktop"?? I'm not clear on that.)

Given these concerns, are there any significant disadvantages to running eLive (installed -- not from the live CD), vs running an e17-modified Ubuntu??  

Also, how the hell do you edit the mouse settings & font sizes in eLive??  I'm going blind & getting carpal-tunnel as we speak ;)   
 
Thanks for the help!

Shane

---

### Post by Adler on 2006-08-30
> I'm really diggin' e17, and I'm trying to find out what I gain (or give up) by running Ubuntu with e17 (instead of Gnome), vs running the Debian-based eLive distro.


Shane10101,

I ran acrooss Enlightenment via eLive and the Desktop blew me away. I didn't feel that there was the support that I would need -- Forums, up-dates, etc. that I get with UBUNTU. But, that is my opinion. I do a lot of things with my workstation, and I really had some issues running eLive. 

I'm hanging back here watching this thread waiting for everything to come together.

Adler

---

### Post by simpleclosure on 2006-08-31
**anybody know how i can take a screen capture in ubuntu?**

---

### Post by simpleclosure on 2006-08-31
nevermind.. i totally didn't see the built in screencap in accessories.

---

### Post by Adler on 2006-08-31
simpleclosure,

Sure -- I use KSnapshot from the KDE side of things. Hit Synaptic and search for it. Then do the install. If you are looking for Snapshot hosting look @ ImageShack.

Are you off topic here? LOL!

Adler

---

### Post by indiolush on 2006-08-31
I have seemingly backed myself into a corner!  I started with this install method for e17 from CVS here > [http://ubuntuforums.org/showthread.php?t=97199&highlight=dr17](http://ubuntuforums.org/showthread.php?t=97199&highlight=dr17)

And now im getting this message at the end of running the  ./easy_e17.sh script```

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engage.log:
-----------------------------------------------------------------------------
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for fmemopen... yes
checking for open_memstream... yes
checking for esmart-config... no
checking for esmart - version >= 0.0.2... no
*** The esmart-config script installed by esmart could not be found
*** If esmart was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ESMART_CONFIG environment variable to the
*** full path to esmart-config.
configure: error: Cannot find esmart: Is esmart-config in path?
make: *** [config.status] Error 1
```


So, now I'm trying to figure out how to uninstall per say, this CVS script's doing and try the method described here with .deb's.  I have been unsuccesful so far.  When I try to use the method here I get this ```
 
indio@ThEpOrTaL:~/Desktop$ sudo apt-get install enlightenment emodules0-all Reading package lists... Done Building dependency tree... Done Package enlightenment is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate
indio@ThEpOrTaL:~/Desktop$

```

Any and all help is appreciated!

Thx, indio

---

### Post by philip5 on 2006-08-31
Hi indo,

my guess why you can't add the debs as you try is that you haven't added the repo to your source.list and if you have then you haven't ran an 'sudo apt-get update' before trying to install the e17 debs.

about building engage with script or not is not possible with cvs code that are newer than about 1,5 week as the api broke and have had changes that doesn't make engage to work/build until it get fixed. that's why it's not included in the latest debs. it's not why your build didn't work though as it say that you haven't compiled and installed esmart before engage, but if you have a rather new cvs tree of code it will brake during build in a step later...

if you have an installation of e17 from script and install the debs make sure that you either uninstalled the script version or make sertain that it's not in your PATH and refered to in ld.so.config, otherwise you will run into trouble with duplicated files.

/phil

---

### Post by loell on 2006-09-03
I think these icons goes best with E

[http://www.customize.org/details/46759]("http://www.customize.org/details/46759")

using those icons is through entangle , but first you'll thave to make an eap
[http://deepcode.atspace.org/make-eap.html]("http://deepcode.atspace.org/make-eap.html")

---

### Post by gordho on 2006-09-03
Thanks for the repo, worked like a charm. I had been using the ubuntu e17 cvs script but this is so much faster! Have one question and a suggestion. 

Anyone else getting duplicates in their Generated Menus after running e17genmenu? Makes a bit of a mess for me, getting this on the cvs install as well as the SoS repo install. If you wanted to manually clean this up how would you do it?

How about making a deb in the repo called eapps-all that will install all working apps?

---

### Post by gordho on 2006-09-03
Figured out how to manually remove the dupliates by editing the .order file in each respective dir in .e/e/applications/menu/favorite/Generated Menus.

---

### Post by philip5 on 2006-09-04
gordho,
thanks for the feedback. It's always nice to hear that the repo is appreciated. Maybe a dummy package for all the e17 apps in the repo could be arranged as an alternative. Might add it in a coming update. Suggestions and more feedback is always welcomed. 

As always, have fun!

/Phil

---

### Post by Duncan_Idaho on 2006-09-04
> **loell said:**
> I think these icons goes best with E

[http://www.customize.org/details/46759]("http://www.customize.org/details/46759")

using those icons is through entangle , but first you'll thave to make an eap
[http://deepcode.atspace.org/make-eap.html]("http://deepcode.atspace.org/make-eap.html")

oh man!! that icon set is really awesome!! it's a great finding you did, and thanks for sharing it here, I'm going to use it right away ;) 

btw, thanks for the how-to eap :p

---

### Post by Shane10101 on 2006-09-04
Adler,

>>I ran acrooss Enlightenment via eLive and the Desktop blew me away. I didn't feel that there was the support that I would need -- Forums, up-dates, etc. that I get with UBUNTU....I do a lot of things with my workstation, and I really had some issues running eLive...I'm hanging back here watching this thread waiting for everything to come together.<<

I think I'm with you.  It _is_ a beautiful & efficient desktop, and I'll definitely keep an eye on it's progress...but I'm starting to think that (for now) it's just too incomplete for what I need.

I could probably tolerate the bugginess (esp. with the option to boot e16 if it gets too bad), if only I could figure out how to make the menu font size, & "minimize/maximize/close" buttons a little bit bigger; and if I find a way to adjust the mouse settings.  As it is, I'm using my tiny & cheap 12" Averatec laptop, and the mouse sensitivity & speed are set so freakin' high under eLive that I could use a postage stamp for a mousepad with room to spare.  Hitting those tiny targets with enough accuracy to function is a real test of patience!  My mouse hand is killing me, and it's ruining my love-life.  ;) 

Again, **any suggestions for adjusting the mouse settings & font sizes??**  I'm thinking I'll give eLive about another 24-hours, and, if I can't get   it worked out, I'll give Openbox a shot instead.  (No 'dis to Ubuntu -- I'm running it on my midtower (& my mom's laptop & my dad's box too) -- I just need to squeeze every ounce of power I can get out of this little machine, and Gnome, while clean & classy, just isn't doing it for me.)

Thanks Again,

Shane

---

### Post by ramasdf123 on 2006-09-06
> **philip5 said:**
> adler,
if you want to remove the e17 debs then run:
```
sudo apt-get remove enlightenment libeet0 libepeg0 
```
That should remove all debs with dependencies in the builds.

Then you could reinstall everything you like to make sure you have the latest debs installed and as you want them.

/Phil

what if i installed it through CVS?

---

### Post by almahtar on 2006-09-07
Loving the debs.  Thanks a lot.  Runs like a charm.  I've been using the easy_e17.sh method for a while, but this rocks its face off.

Oh, and I have a mouse theme that I really like that I use in Gnome and KDE.  Any idea how I change my mouse theme for E?

---

### Post by Duncan_Idaho on 2006-09-07
> **loell said:**
> I think these icons goes best with E

[http://www.customize.org/details/46759]("http://www.customize.org/details/46759")



excuse me but, what do I do with the asdf.iconpackage file? how can I extract  the icons? and more important, what [the heck!?] is an .iconpackage file?

---

### Post by Adler on 2006-09-07
Guys -- 

Can I change my Desktop? I'm always changing what I have. Lot's of work on my site. Is everything final here? I do a lot on my site.

Adler

---

### Post by Feanor on 2006-09-08
First of all, Hawkwind great job! Your repository is really useful I must say ;) 

Anyway there's also this way to get enlightenment working on our ubuntu desktop:

[http://www1.get-e.org/Main/News/_articles/334.html](http://www1.get-e.org/Main/News/_articles/334.html)

I've just installed e17 from that repo and works fine... But there aren't all the apps that hawkwind holds on his repository... Don't try to use both repos at same time, there are problems with the dependency. It will be very very cool if there's a kind of join between edevelop.org's repos and seerofsouls.com ^^

However, this is the result

[http://ubuntuforums.org/gallery/showphoto.php?photo=3455&size=big&cat=4](http://ubuntuforums.org/gallery/showphoto.php?photo=3455&size=big&cat=4)

I love enlightenment *_*

---

### Post by philip5 on 2006-09-08
In the future there shouldn't be two competing repos and we are talking with the guys at get-e.org. I think there will be a merge of the repos and that the SoS and get-e repo will be mirrors of each other. It's not final yet as we need to sync debian trees for building packages and stuff like that. Right now the naming of packages and what are in the repos differ a little bit, the final user expericense should be the same though.

There is also plans that at least SoS will have 64bit versions of the e17 debs soon and also builds for edgy.

We will keep you all posted about what will happen when things are for sure.

As always, have fun!

/Philip

PS. I have been out of town for a couple of days but will build new packages of the latest cvs code this weekend on a brand new system at my delight... :)

---

### Post by Feanor on 2006-09-09
You're right! My problem with dependency and broken packages depends on a failed installation of entrance, I'm glad to see that I can have SoS e edevelop.org sources in my sources.list at same time, installation doesn't make any mistake! :-D Now I must see if all works fine :cool: 

Anyway, when installing entrance I get an error in gdm "gdm: not valid user"... I think this is some kind of problem due to I've kdm installed, I dunno.

Philip5 thanks a lot!

---

### Post by philip5 on 2006-09-09
Feanor,
SoS doesn't have entrance built in its repo and that's mostly because I don't like it so far and it have been a bit messy to package. I'm not sure how the get-e guys have set it up and if it needs gdm in some way as it seam from your post. I prefer to use kdm/gmd/xdm for e17 so far.

The other thing is that I shouldn't have both the SoS and the get-e repo listed in my source.list as even though they come from the same code the cvs build date can differ and that might render some problems from time to time. Until we merge them I would choose either repo and not both at the same time.

/Phil

---

### Post by Gamebeavis on 2006-09-09
First off, thank you for creating this Repo, it is EXTREAMLY usefull. But I have 2 questions. First, why cant I load the "engage" module. When I try, it tells me that the engage module cannot be found in the search path. I had this problem once before with ALL my modules, but I simply uninstalled/reinstalled E17 and then they worked fine, but engage still wont load. Is it simply not included in this repo?? Second, I understand why there is no native "systray" support for E17, but, I have to have one in order to run knetworkmanager otherwise I have to sign into KDE, connect to my network, then sign out of KDE and into E17 (seems kind of pointless to me). I know that engage has a "systray" function (hence the reason I would like to know how to load it), but if there is another alternative that works just as well, I am open to suggestions. 


:-k

---

### Post by philip5 on 2006-09-09
Gamebeavis,
Engage is taking a forktrip as it will be one standalone version and a module version. Before i went away during this week the module version of engage was broken and the standalone had a bug but should work now. There will be a new update if e17 this weekend of it all builds as it should and that will include (hopefully) a working standalone enage package. The standalone starts by running the engage command in commandline and not via the the modules config panel (if you have installed the standalone that is...).

/Phil

---

### Post by Lut!n on 2006-09-13
Feanor : as philip5 said, you should not use both repos in your source.list, it may be cause issues depending on the difference between the cvs versions. Moreover, DO NOT use entrance. I didn't package it -Sp4rKy did, so I don't know how it is set up, but it is there for _packaging testing_ purposes. please, don't use it atm

---

### Post by Feanor on 2006-09-14
Don't worry, I know well the kind of issues I'm going to have, but this isn't frightening me. Also entrance, its look'n'feel is very awesome, now I've solved the problem I had (it depends on a configuration file) but I can't see it in fullscreen. Is not a problem for me, I switch kdm/entrance everytime I want. I'm not searching solutions for issues, it's a silly request for applications that often are pre-alphas. But I want to use this desktop shell, and if I'll be able to do it, send some useful report to the developers. Anyway I can say that use both repos at the moment causes only a problem with the emodules: it's impossible to load the module provided by SoS, so I can use only that come from edevelop.org. The apps like eclair (very very very nice music app) exhibit etc. works fine! I want to try and I'm no worried for some problem that can come in the future. ;)

---

### Post by Uncle Spellbinder on 2006-09-14
I was getting ready to give Enlightenment a go. I added the repo and public key. updated and then:

```
unclespellbinder@Wombat:~$ sudo aptitude install enlightenment emodules0-all
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  edje0-bin embryo0-bin libdirectfb-0.9-22 libecore0 libecore0-con
  libecore0-config libecore0-dbus libecore0-desktop libecore0-directfb
  libecore0-evas libecore0-file libecore0-ipc libecore0-job libecore0-txt
  libecore0-x libedje0 libeet0 libembryo0 libevas0 libevas0-engine-buffer
  libevas0-engine-software-generic libevas0-engine-software-x11
  libevas0-engine-xrender libevas0-loader-eet libevas0-loader-jpeg
  libevas0-loader-png libevas0-saver-eet libevas0-saver-jpeg
  libevas0-saver-png
[color=#CC0000][b]The following packages have been kept back:
  libimlib2[/b][/color]
The following NEW packages will be installed:
  edje0-bin embryo0-bin emodules0-all enlightenment libdirectfb-0.9-22
  libecore0 libecore0-con libecore0-config libecore0-dbus libecore0-desktop
  libecore0-directfb libecore0-evas libecore0-file libecore0-ipc
  libecore0-job libecore0-txt libecore0-x libedje0 libeet0 libembryo0
  libevas0 libevas0-engine-buffer libevas0-engine-software-generic
  libevas0-engine-software-x11 libevas0-engine-xrender libevas0-loader-eet
  libevas0-loader-jpeg libevas0-loader-png libevas0-saver-eet
  libevas0-saver-jpeg libevas0-saver-png
0 packages upgraded, 31 newly installed, 0 to remove and **[color=#CC0000]1 not upgraded[/color]**.
Need to get 9448kB of archives. After unpacking 18.0MB will be used.
Do you want to continue? [Y/n/?] n
Abort.
unclespellbinder@Wombat:~$
```

Ideas?


.

---

### Post by Uncle Spellbinder on 2006-09-14
^   ^   ^

Nevermind, I got it. Dist-upgrade updated *libimlib2* and the install wen flawlessly. Now I need to learn how to use it. I have no idea on how to make a custom launcher. Each time I input it's location in icon properties, it says it cannot launch.

---

### Post by philip5 on 2006-09-15
Uncle Spellbinder,
You don't start enlightenment from within i.e KDE och Gnome as it's a window manager of it own. You log out to your DM (i.e KDM, GDM, XDM), select the user you want to be and select Enlightenment as your session instead of KDE, Gnome or what ever you otherwise use. Then login and Enlightenment should start for you...

Have fun!

Phil

---

### Post by whizbaby on 2006-09-15
Hi hawk and phil, thank you for all the work on the *.deb. All installs fine, leaving only a few questions:
- when I *sudo apt-get update* I get this message
```
Unable to find expected entry  e17/source/Sources in Meta-index file (malformed Release file?)
```
do you have a hint what's my error here (seems I'm the only one getting it)?
- some of the modules don't do anything (moonclock,taskbar,wheather,digitalclock), are these supposed to work?
- here's another little problem
```

#######@######:~$ e17genmenu
Generating menus.

Checking For /usr/share/applications...
Segmentation fault
#######@######:~$ sudo e17genmenu
Generating menus.

Checking For /usr/share/applications...
Segmentation fault

```
- Is there any kind of *E17 Manual* or doc-tool (like edocs)? Can't find one on enlightenment.org ...
Apart from that I'm completely enjoying E17 thanks to you making it so easy to install!

---

### Post by whizbaby on 2006-09-15
> **whizbaby said:**
> 
- some of the modules don't do anything (moonclock,taskbar,wheather,digitalclock), are these supposed to work?

*some of the modules* have to be added manually to the shelf...
> 
- Is there any kind of *E17 Manual* or doc-tool (like edocs)? Can't find one on enlightenment.org ...

found one on
[http://www1.get-e.org/E17_User_Guide/English/](http://www1.get-e.org/E17_User_Guide/English/)
instead.

---

### Post by whizbaby on 2006-09-16
Still having the *malformed Release file* and the segfault, though.

---

### Post by Feanor on 2006-09-17
e17genmenu generated segmentation fault also to me even if I'm using the edevelop.org repositories so I think it's a bug...

---

### Post by shinkaide on 2006-09-18
Hi, I tried following the instructions on the SOS website, doing:

 sudo apt-get install emodules0-all enlightenment

but I got this error:

 E: Couldn't find package emodules0-all

It's not there?

---

### Post by JeevesBond on 2006-09-18
> **shinkaide said:**
> Hi, I tried following the instructions on the SOS website, doing:

 sudo apt-get install emodules0-all enlightenment

but I got this error:

 E: Couldn't find package emodules0-all

It's not there?
You got it the wrong way round, you silly sausage. :D You should do this:
```
sudo apt-get install enlightenment emodules0-all
```

Personally, am having trouble with another repo that supplies e17 ( deb [http://edevelop.org/ubuntu](http://edevelop.org/ubuntu) dapper e17 ) as it doesn't seem to contain the module version of engage (a Mac OS X style dockbar for *nix), which works in e17. Only the standalone is available, which works with anything but e17

Does this repo have engage available?

---

### Post by Feanor on 2006-09-18
The order of parameters in `apt-get install` is not relevant

Often the repos are not available, I think it's due to updates...

Anyway the engage is available in SoS, it isn't a module but a stand-alone application so you can install it by

```
sudo apt-get install engage
```

I can't remember if it is present also in edevelop.org, I have it installed but I don't know if I took it from edevelop.org

Cheers, Feanor

---

### Post by czynski on 2006-09-18
Thanks for the repo! i haven't used e17 in a while and the new features are 

cool. the only problem i'm having with your repo is e17genmenu always

segfaults. i'd like to get this working cause it would be quick than manual 

i'm sure.

---

### Post by whizbaby on 2006-09-19
> **whizbaby said:**
> Still having the *malformed Release file* 
Solved by switching to edevelop.org. Leaves the segfault. Sorry for ingeborging.

---

### Post by philip5 on 2006-09-19
Ok, here comes a couple of things...

Engage as module doesn't work in any repo as it's a broken module in code and it will be up on the repo as soon as the developers fix it. Until then you have to use standalone engage if you really want it. The standalone is on the SoS repo and if it's on the other I'm not sure but would think so.

Then about e17genmenu. E17 have changed how the menu works and are now using .desktop files as standard. e17genmenu doesn't support that format what I know of so you will have to use the new features that are developing inside the config panel and it will mature more.

I have been a busy with other stuff the past week but am hoping to upload new deb packages of the latest code any day now.

I also don't recommend using both repos at the same time, but it's up to you...

As always, have fun!

/Phil

---

### Post by Qrawler on 2006-10-11
Im getting also this Meta-index file error when i run apt-get update
anyone got a clue what to do? :) 


Failed to fetch [http://SeerOfSouls.com/dists/dapper/Release](http://SeerOfSouls.com/dists/dapper/Release)  Unable to find expected entry  e17/source/Sources in Meta-index file (malformed Release file?)
Failed to fetch [http://SeerOfSouls.com/dists/edgy/Release](http://SeerOfSouls.com/dists/edgy/Release)  Unable to find expected entry  e17/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done

---

### Post by Feanor on 2006-10-12
I think you should have active or edgy or dapper repository, not both... Anyway the problem remains, I'm affected even if I've only dapper repo.

---

### Post by Adler on 2006-10-12
philip5,

I've been *lurking* here for a while. And, want to show your efforts.

Have you a good Site going based off your efforts? And, install?

Adler

---

### Post by philip5 on 2006-10-14
Adler,
nope, not a site i general. Only the files you find at the SoS site. Something you wanted to read more about??? What efforts do you want to show?

Not sure about the Meta-index file on the repo as I don't update those files on SoS. But as Feanor said you shouldn't use both repos as you only should use the repo responding to the version of *ubuntu you use.

Hope this was of any help,

As always, have fun...

/Phil

---

### Post by whizbaby on 2006-10-15
> **philip5 said:**
> Not sure about the Meta-index file on the repo as I don't update those files on SoS. But as Feanor said you shouldn't use both repos as you only should use the repo responding to the version of *ubuntu you use.Hope this was of any help,

Not really, multiple repositories are not the problem since
- I *first* installed e17 from SoS and experienced the problem, then switched to another repository (like I wrote) commenting out the SoS entry before. They don't have this problem there.
- I switched back to SoS (of course with commenting out edevelop) and have this problem again.
So I guess the problem is not originating on the client side (especially with other people experiencing the same) or I'm missing a piece of information (please tell me/us then).
Thanx for trying anyways ...

---

### Post by fdoving on 2006-10-15
> **Hawkwind said:**
> I have both installed currently.  E17 installs to /usr/local/bin and enlightenment installs to /usr/bin

Packages should never install to /usr/local/bin. That breaks the idea of package manager and home-compiled stuff.

The idea is that /usr/local/ is the place you put stuff you compile yourself. the package manager shoudn't touch it. It's generally a bad idea to break that policy.

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.1](http://www.debian.org/doc/debian-policy/ch-opersys.html#s9.1)


- Frode

---

### Post by Adler on 2006-10-15
> Adler,
nope, not a site i general. Only the files you find at the SoS site. Something you wanted to read more about??? What efforts do you want to show?

Well, way back in the beginning of this thread I had found "E" as the default Desktop with another Debian based Distro. And, thought is is fantastic!

I've been building a Site about Linux (UBUNTU), and wanted to add an easy *"How-To"*install "E" into it. I'm not sure how I should profile your work, but would want to make sure that everything was a "no-brainer", if you know what I mean e.g. AUTOMTIX install type of thing. 

Is that making some sense?

Adler

---

### Post by philip5 on 2006-10-20
Adler,
You can link to the SoS repo from your site if you like or give instruction on how to add it to users apt-source. Right now there is no special automatix-like installation of SoS repo but there is talk about adding it to the EasyUbuntu installer. That will make it easy to install and bring it closer to the masses that use Ubuntu. The thing is also that the E17 developer team doesn't want it in any distro yet (or offical repo) as it's still in a heavy development phase and can (and surely will) break and/or change in big parts before it goes into a real alpha or beta phase. So the SoS E17 repo should be more of a sneak peek of the future in an easy way.

Hope this answered a few questions and maybe raised some others...

As always, have fun...

/Phil

---

### Post by Adler on 2006-10-21
philip5,

Thanks -- as time allows I'll see what I can come up with here.

Adler

---

### Post by jharbert on 2006-10-22
I've been using e17 on edgy for the last month and like it a lot.  I installed it using the edevelop repos.  However, I can't seem to find entropy or e17genmenu using apt-get.  What do I need to do to download these.

---

### Post by Hawkwind on 2006-10-22
Failed to fetch [http://SeerOfSouls.com/dists/dapper/Release](http://SeerOfSouls.com/dists/dapper/Release) Unable to find expected entry e17/source/Sources in Meta-index file (malformed Release file?)

For those of you getting the above message, please remove the deb src repo from your sources.list and this will go away.  I'm trying to find out what keeps causing this and I can't seem to figure it out.

As far as e17genmenu, it's obsolete now.  It was used when .eap files were used, and now that E17 has gone to .desktop files e17genmenu doesn't work anymore.  I'm not even sure it'll be updated again.

Entropy is in the repos so you should be able to just do sudo apt-get install entropy if it's not already installed.

As soon as I find out what's wrong with the source section of the repo I'll definitely post here and let everyone know.  For now, please remove it and then sudo apt-get update again all should be well.

---

### Post by Hawkwind on 2006-10-22
Ok, everyone can either leave the deb-src lines in there, or you can remove them if you don't ever plan on downloading the source packages.  This problem has now been fixed.  Was simply missing a simpel . in a script and kept over looking it.  

Please let me know of any further problems.  sudo apt-get update should now not cause any errors/warnings :)

---

### Post by Lut!n on 2006-10-22
> **jharbert said:**
> I've been using e17 on edgy for the last month and like it a lot.  I installed it using the edevelop repos.  However, I can't seem to find entropy or e17genmenu using apt-get.  What do I need to do to download these.
Sorry, we didn't have the time to make clean packages of entropy and evfs, so this package will come later. it is planned though
talking about e17genmenu, this is deprecated as all the menu generetion code as been moved into E itself. So, e17genmenu no longer exists. (or it still exists but does nothing)
Cheers
Lut!n

---

### Post by philip5 on 2006-10-23
Jharbert (and others who are interested),
Entropy is part of the SoS E17 repo but not in the edevelop repo. You are recommended to use either repo and not both at the same time. It's also true what Lut!n say that e17genmenu is deprecated and stopped being usable about when E17 went the path of using the desktop-fileformat. You find e17genmenu (but will likely segment fault or being unusable as it wasn't built for handling the desktop-fileformat) in the eutils package in the SoS repo with the eapp_editor, e17setroot, entangle, emblem, exige and ethemes. Some of these E-apps are more or less usable today but still there.

As always, have fun!

/Phil

---

### Post by Hawkwind on 2006-10-23
I think a couple of things need to be cleared up here....

First and foremost, this is not a competition, battle, war or anything else.  This thread was posted here to alert users who wanted to know about E17 packages that the SoS repo was available.  IMO there shouldn't have been a post of another persons repo within this thread.  All it has seem to do is cause issues, problems and much confusion with a lot of users.

I respect Lutin for maintaining the edevelop.org repo and speak to him on a somewhat regular basis.  We don't hate each other or anything remotely close.  What everyone needs to realize is that these two repos are completely seperate from each other.  We offer packages edevelop doesn't and possibly edevelop offers packages that we at SoS don't offer.  

I'm getting emails everyday stating they are getting dep issues, or file problems and come to find out they have or are using both repos in their sources.list.

To make things clear for everyone who reads this post from here on out, this thread is about the SoS repo *only*.  If you are using the edevelop.org packages, it might be best to start a seperate thread on these very forums to post any comments, suggestions, issues there so that we aren't constantly telling people: "That's not our repo so I don't know how to help you."  I don't mind helping if I know the answer, but the emails I'm getting I can't help with as they are edevelop package specific questions.  I apologize in advance for not being able to help with their repo.  They build theirs, we build ours.

For those of you who are using the SoS repo, it appears that the SoS repo will be added to easysource, source-o-matic and possibly others very soon as several people who are involved with packaging for *Ubuntu enjoy our SoS packages and find them very stable after a couple of months of testing.  This will bring the repo to many more users which in turn gives us much more feedback and information and ideas of how to make our packages better.

Please don't take this as a bash, flame war or anything towards any other packagers of E17.  I just feel we need to stop confusing the user by mixing this thread with more than one repo and by supporting more than one repo especially since they both can't be used at the same time.

---

### Post by jharbert on 2006-10-23
Thanks very much for your help and for clarifying things about the two repos.

---

### Post by whizbaby on 2006-10-24
> **Hawkwind said:**
> Failed to fetch [http://SeerOfSouls.com/dists/dapper/Release](http://SeerOfSouls.com/dists/dapper/Release) Unable to find expected entry e17/source/Sources in Meta-index file (malformed Release file?)

Fix confirmed.
Many thanks for spending time finding that typo (mean little thingy).

---

### Post by jharbert on 2006-10-24
What's the status of engage as a module?  Earlier in this thread it was mentioned that at this point it could only be used as a standalone (which is no good for me because I make use of E17's beautiful virtual desktops).

---

### Post by Hawkwind on 2006-10-24
Engage as a module is completely dead.  It will never be maintained again.  Only the standalone version is still maintained, and even that might not be maintained much longer if things continue to move along as they are.  There will be something to replace it though you can guarantee.

---

### Post by Adler on 2006-10-25
Hi All,

I joined this thread a while back, and the efforts made here have been great.

For the simple minded -- like me -- what should be either added to the repositories. Basically edit sources, then run in Command Line to get the latest?

Adler

---

### Post by Hawkwind on 2006-10-25
All of the information is here:  [http://seerofsouls.com/ubuntu.html](http://seerofsouls.com/ubuntu.html)

If you use Dapper, then use the Dapper information.  If you use Edgy, then use the Edgy information.  If you look at the top of that page you'll see some info written there of what you need to do to get our E17 installed.  Once it's installed, a simple:

```
sudo apt-get update && sudo apt-get upgrade
```

Will keep you current and update your E17 as we at SoS update it on our end.  That's all you have to do :)

---

### Post by almahtar on 2006-10-30
Sweet! They've posted an Edgy repo already.

---

### Post by QUASAR_FREAK on 2006-10-31
thanks man!! =)

---

### Post by ner0tic on 2006-11-06
> **Hawkwind said:**
> All of the information is here:  [http://seerofsouls.com/ubuntu.html](http://seerofsouls.com/ubuntu.html)

If you use Dapper, then use the Dapper information.  If you use Edgy, then use the Edgy information.  If you look at the top of that page you'll see some info written there of what you need to do to get our E17 installed.  Once it's installed, a simple:

```
sudo apt-get update && sudo apt-get upgrade
```

Will keep you current and update your E17 as we at SoS update it on our end.  That's all you have to do :)

I followed the instructions per the site but i get this:
> sudo apt-get install emodules0-all enlightenment
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package enlightenment is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  enlightenment-data
E: Package enlightenment has no installation candidate


---

### Post by whizbaby on 2006-11-06
Did you

sudo apt-get update 

before trying?

---

### Post by ner0tic on 2006-11-06
> **whizbaby said:**
> Did you

sudo apt-get update 

before trying?

yes

---

### Post by ner0tic on 2006-11-06
i forgot to mention i tried then doing enlightenment-data and it gives me the same error as enlightenment (minus the alternate package name of course)
> sudo apt-get install emodules0-all enlightenment-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package enlightenment-data is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package enlightenment-data has no installation candidate


---

### Post by Adler on 2006-11-06
Hi All,

Anybody have screenshots of it on Dapper?

Adler

---

### Post by philip5 on 2006-11-07
ner0tic,
you shouldn't install enlightenment-data as it's a E16 data-package. If you install the enlightenment package it will include the files you need as "data"-files too. Just follow Hawkwinds instructions for installation.

/Phil

---

### Post by ner0tic on 2006-11-07
> **philip5 said:**
> ner0tic,
you shouldn't install enlightenment-data as it's a E16 data-package. If you install the enlightenment package it will include the files you need as "data"-files too. Just follow Hawkwinds instructions for installation.

/Phil

i tried and that's where the errors are coming from.

---

### Post by sphere02 on 2006-11-07
i can only move modules but how to RESIZE them?

---

### Post by ner0tic on 2006-11-07
> **ner0tic said:**
> i tried and that's where the errors are coming from.

When i do ```
apt-cache pkgnames enlightenment
```
it shows enlightenment listed but hen i do the install attempt it says it's not found.

---

### Post by Lut!n on 2006-11-08
> **ner0tic said:**
> When i do ```
apt-cache pkgnames enlightenment
```
it shows enlightenment listed but hen i do the install attempt it says it's not found.

Do you have a pin for enlightenment (version 0.16.999*) in /etc/apt/preferences ? If it is the case, removing it might help.

---

### Post by ner0tic on 2006-11-08
> **Lut!n said:**
> Do you have a pin for enlightenment (version 0.16.999*) in /etc/apt/preferences ? If it is the case, removing it might help.

no i set up the pin for 0.17 per instructions from another attempt where the sources were gone.
> Package: enlightenment
Pin: version 0.17.*
Pin-Priority: 999

Package: enlightenment-data
Pin: version 0.17.*
Pin-Priority: 999


---

### Post by ner0tic on 2006-11-08
when i do a 
> sudo apt-cache show -a enlightenment

its saying that 0.16 is the only one in the repos.

> sudo apt-cache show -a enlightenment
Package: enlightenment
Priority: optional
Section: x11
Installed-Size: 10332
Maintainer: E17 Debian Team <debian@edevelop.org>
Architecture: i386
Version: 1:0.16.999.033-0cvs20061011


---

### Post by Lut!n on 2006-11-08
> **ner0tic said:**
> its saying that 0.16 is the only one in the repos. :
 Version: 1:0.16.999.033-0cvs20061011

Actually you are confused.
enlightenment DR17 is the name commonly used for the developement version of enlightenment, which is numbered 0.16.999.*
So the version you have in the repo _is_ e17, and your install fails because the pin in /etc/apt/preferences matches no package, because E version 0.17 does not exist yet ;). Just remove those pins and go on :D

---

### Post by ner0tic on 2006-11-08
> **Lut!n said:**
> Actually you are confused.
enlightenment DR17 is the name commonly used for the developement version of enlightenment, which is numbered 0.16.999.*
So the version you have in the repo _is_ e17, and your install fails because the pin in /etc/apt/preferences matches no package, because E version 0.17 does not exist yet ;). Just remove those pins and go on :D

i realized this this morning after i posted this stuff but it still fails with the same errors.


edit: now i'm getting broken package errors.

---

### Post by Hawkwind on 2006-11-09
Once you remove the pin you need to do a sudo apt-get update again.  Also, if you say you're getting broken packages, can you paste the complete error messages so we can all see them.

---

### Post by drnickesq on 2006-11-09
Just wanted to say thanks for the instructions.  I was having the same problem as neurotic, but when I removed the pin, I was able to install flawlessly.  Thanks!

---

### Post by ner0tic on 2006-11-09
> **Hawkwind said:**
> Once you remove the pin you need to do a sudo apt-get update again.  Also, if you say you're getting broken packages, can you paste the complete error messages so we can all see them.

i did the update and still got this:
> $ sudo apt-get install emodules0-all enlightenment
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  emodules0-all: Depends: emodule0-language but it is not going to be installed
  enlightenment: Depends: libecore0 but it is not going to be installed
                 Depends: libecore0-con but it is not going to be installed
                 Depends: libecore0-config but it is not going to be installed
                 Depends: libecore0-dbus but it is not going to be installed
                 Depends: libecore0-desktop but it is not going to be installed
                 Depends: libecore0-evas but it is not going to be installed
                 Depends: libecore0-file but it is not going to be installed
                 Depends: libecore0-ipc but it is not going to be installed
                 Depends: libecore0-job but it is not going to be installed
                 Depends: libecore0-txt but it is not going to be installed
                 Depends: libecore0-x but it is not going to be installed
                 Depends: libedje0 but it is not going to be installed
                 Depends: libeet0 but it is not going to be installed
                 Depends: libembryo0 but it is not going to be installed
                 Depends: libevas0 but it is not going to be installed
                 Depends: libevas
                 Depends: libecore
                 Depends: libecore-con
                 Depends: libecore-evas
                 Depends: libecore-file
                 Depends: libecore-ipc
                 Depends: libecore-job
                 Depends: libecore-txt
                 Depends: libecore-x
                 Depends: libeet
                 Depends: libembryo
                 Depends: embryo-bin
                 Depends: edje-bin
                 Depends: libedje
                 Depends: libevas-loader-eet
                 Depends: libevas-loader-jpeg
                 Depends: libevas-loader-png
                 Depends: libevas-saver-eet
                 Depends: libevas-saver-jpeg
                 Depends: libevas-saver-png
                 Depends: libevas-engine-buffer
                 Depends: libevas-engine-software-x11
E: Broken packages


my sources:
```
 deb http://us.archive.ubuntu.com/ubuntu/ edgy main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
 deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

 deb http://security.ubuntu.com/ubuntu edgy-security main restricted
 deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted
# deb http://security.ubuntu.com/ubuntu dapper-security universe
 deb-src http://security.ubuntu.com/ubuntu edgy-security universe
 deb http://www.getautomatix.com/apt edgy main

#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

# deb http://archive.canonical.com/ubuntu dapper-commercial main

 deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

 deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

 deb http://archive.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

 deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
#AUTOMATIX REPOS END

## e17 repos
deb http://SeerOfSouls.com/ edgy e17

deb-src http://SeerOfSouls.com/ edgy e17
## e17 contrib repos
deb http://SeerOfSouls.com/ edgy contrib

deb-src http://SeerOfSouls.com/ edgy contrib

```

---

### Post by ner0tic on 2006-11-09
our of boredom really, i tried with aptitude and i get this.

> $ getme enlightenment
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  efl-all 
The following NEW packages will be automatically installed:
  edje0-bin embryo0-bin libecore0 libecore0-con libecore0-config libecore0-dbus libecore0-desktop libecore0-directfb libecore0-evas libecore0-file 
  libecore0-ipc libecore0-job libecore0-txt libecore0-x libedje0 libeet0 libembryo0 libevas0 libevas0-engine-buffer libevas0-engine-software-generic 
  libevas0-engine-software-x11 libevas0-engine-xrender libevas0-loader-eet libevas0-loader-jpeg libevas0-loader-png libevas0-saver-eet 
  libevas0-saver-jpeg libevas0-saver-png 
The following NEW packages will be installed:
  edje0-bin embryo0-bin enlightenment libecore0 libecore0-con libecore0-config libecore0-dbus libecore0-desktop libecore0-directfb libecore0-evas 
  libecore0-file libecore0-ipc libecore0-job libecore0-txt libecore0-x libedje0 libeet0 libembryo0 libevas0 libevas0-engine-buffer 
  libevas0-engine-software-generic libevas0-engine-software-x11 libevas0-engine-xrender libevas0-loader-eet libevas0-loader-jpeg libevas0-loader-png 
  libevas0-saver-eet libevas0-saver-jpeg libevas0-saver-png 
0 packages upgraded, 29 newly installed, 0 to remove and 0 not upgraded.
Need to get 8054kB of archives. After unpacking 14.6MB will be used.
The following packages have unmet dependencies:
  efl-all: Conflicts: libecore0 but 0.9.9.033-0cvs20061011 is to be installed.
           Conflicts: edje0-bin but 0.5.0.033-0cvs20061011 is to be installed.
           Conflicts: libedje0 but 0.5.0.033-0cvs20061011 is to be installed.
           Conflicts: libeet0 but 0.9.10.033-0cvs20061011 is to be installed.
           Conflicts: embryo0-bin but 0.9.1.033-0cvs20061011 is to be installed.
           Conflicts: libembryo0 but 0.9.1.033-0cvs20061011 is to be installed.
           Conflicts: libevas0 but 0.9.9.033-0cvs20061011 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
enlightenment [1:0.16.7.2-3ubuntu1 (edgy, edgy)]
enlightenment-data [1:0.16.7.2-3ubuntu1 (edgy, edgy)]

Keep the following packages at their current version:
edje0-bin [Not Installed]
embryo0-bin [Not Installed]
libecore0 [Not Installed]
libecore0-con [Not Installed]
libecore0-config [Not Installed]
libecore0-dbus [Not Installed]
libecore0-desktop [Not Installed]
libecore0-directfb [Not Installed]
libecore0-evas [Not Installed]
libecore0-file [Not Installed]
libecore0-ipc [Not Installed]
libecore0-job [Not Installed]
libecore0-txt [Not Installed]
libecore0-x [Not Installed]
libedje0 [Not Installed]
libeet0 [Not Installed]
libembryo0 [Not Installed]
libevas0 [Not Installed]
libevas0-engine-buffer [Not Installed]
libevas0-engine-software-generic [Not Installed]
libevas0-engine-software-x11 [Not Installed]
libevas0-engine-xrender [Not Installed]
libevas0-loader-eet [Not Installed]
libevas0-loader-jpeg [Not Installed]
libevas0-loader-png [Not Installed]
libevas0-saver-eet [Not Installed]
libevas0-saver-jpeg [Not Installed]
libevas0-saver-png [Not Installed]

Score is 143


i wasn't really sure if 0.16.7.2 was the e17 version or not so i held off

---

### Post by Lut!n on 2006-11-12
> **ner0tic said:**
> Conflicts: edje0-bin but 0.5.0.033-0cvs20061011 is to be installed.
Conflicts: libedje0 but 0.5.0.033-0cvs20061011 is to be installed.
Conflicts: libeet0 but 0.9.10.033-0cvs20061011 is to be installed.
Conflicts: embryo0-bin but 0.9.1.033-0cvs20061011 is to be installed.
Conflicts: libembryo0 but 0.9.1.033-0cvs20061011 is to be installed.
Conflicts: libevas0 but 0.9.9.033-0cvs20061011 is to be installed.


Did you try to install some of these packages using apt, to see what are the error logs for those packages ? That might be helpful

---

### Post by ner0tic on 2006-11-12
i tried and it was a dependency conflict.

i worked passed it but now i get this:> getme emodules0-all enlightenment
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for enlightenment
The following packages are BROKEN:
  emodule0-cpu emodule0-deskshow emodule0-eveil emodule0-flame emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon emodule0-net 
  emodule0-photo emodule0-rain emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock emodule0-uptime emodule0-weather 
  emodule0-winselector emodule0-wlan emodules0-all 
The following NEW packages will be automatically installed:
  libexml1 
The following NEW packages will be installed:
  libexml1 
0 packages upgraded, 23 newly installed, 0 to remove and 0 not upgraded.
Need to get 2928kB of archives. After unpacking 6083kB will be used.
The following packages have unmet dependencies:
  emodule0-screenshot: Depends: enlightenment but it is not installable
  emodule0-wlan: Depends: enlightenment but it is not installable
  emodule0-language: Depends: enlightenment but it is not installable
  emodules0-all: Depends: enlightenment (>= 0.16.999) but it is not installable
  emodule0-mail: Depends: enlightenment but it is not installable
  emodule0-photo: Depends: enlightenment but it is not installable
  emodule0-deskshow: Depends: enlightenment but it is not installable
  emodule0-taskbar: Depends: enlightenment but it is not installable
  emodule0-flame: Depends: enlightenment but it is not installable
  emodule0-moon: Depends: enlightenment but it is not installable
  emodule0-mixer: Depends: enlightenment but it is not installable
  emodule0-rain: Depends: enlightenment but it is not installable
  emodule0-cpu: Depends: enlightenment but it is not installable
  emodule0-uptime: Depends: enlightenment but it is not installable
  emodule0-mem: Depends: enlightenment but it is not installable
  emodule0-net: Depends: enlightenment but it is not installable
  emodule0-eveil: Depends: enlightenment but it is not installable
  emodule0-tclock: Depends: enlightenment but it is not installable
  emodule0-snow: Depends: enlightenment but it is not installable
  emodule0-winselector: Depends: enlightenment but it is not installable
  emodule0-slideshow: Depends: enlightenment but it is not installable
  emodule0-weather: Depends: enlightenment but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
enlightenment [1:0.16.7.2-3ubuntu1 (edgy, edgy)]
enlightenment-data [1:0.16.7.2-3ubuntu1 (edgy, edgy)]

Score is -128

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  emodule0-cpu emodule0-deskshow emodule0-eveil emodule0-flame emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon emodule0-net 
  emodule0-photo emodule0-rain emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock emodule0-uptime emodule0-weather 
  emodule0-winselector emodule0-wlan enlightenment enlightenment-data libexml1 
The following NEW packages will be installed:
  emodule0-cpu emodule0-deskshow emodule0-eveil emodule0-flame emodule0-language emodule0-mail emodule0-mem emodule0-mixer emodule0-moon emodule0-net 
  emodule0-photo emodule0-rain emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar emodule0-tclock emodule0-uptime emodule0-weather 
  emodule0-winselector emodule0-wlan emodules0-all enlightenment enlightenment-data libexml1 
0 packages upgraded, 25 newly installed, 0 to remove and 0 not upgraded.
Need to get 5984kB of archives. After unpacking 12.2MB will be used.
Do you want to continue? [Y/n/?] y
Segmentation fault (core dumped)on... 1%



getme is my alias for sudo aptitude install

---

### Post by Lut!n on 2006-11-18
> **ner0tic said:**
> i tried and it was a dependency conflict.

i worked passed it but now i get this:


getme is my alias for sudo aptitude install

What happens when you try to install enlightenment ?

---

### Post by Adler on 2006-11-18
Hi All,

I've been here a few times, or two. 

I'd like to add the video of Enlightenment to [www.jjmacey.net]("http://www.jjmacey.net"), Main Menu, Linux Videos.

Does anyone have a Video capture using UBUNTU?

---

### Post by costis on 2006-11-26
Everything seems to work fine with 016.999.036, but the flame module has a really awkward look  according to the attached picture. How could I fix it?

---

### Post by ner0tic on 2006-11-27
> **Lut!n said:**
> What happens when you try to install enlightenment ?

i gave up. wasn't worth all the effort, i'm happy with gnome and beryl.

---

### Post by bloodfyr on 2006-12-04
Okay. 

From my minimal usage thus far of E, I'm REALLY enjoying what I'm seeing. Reminds me a lot of the flexibility of Litestep, and that's probably the one thing keeping me tied to Windows. So if I can get this as customized and tweaked as my old theme, I would be utterly set.

I'm a novice Linux user, so please go easy on me. 

I'm looking at get-e.org's docs, and the user guide is different than the Enlightenment I'm seeing in front of me. Is there a location where there are docs for THIS version of Englightenment?

If not...I just have a couple major questions. 

As far as editing the menu goes (almost called it the popup...I really miss Litestep. :3) - How much of it is editable? All of it, or just the application parts? If the rest of it is editable, how would I go about, for example, removing things like the "Desktops" menu?

Is there a way of activating a sort of...KDE/GNOME style taskbar, as GAIM windows don't call attention to themselves when I get a new message.

And finally...where can I find more modules?

Other than that...this seems like it'll be my new desktop environment. Thanks Hawkwind. ^^

EDIT - Okay. One last question, as far as Engage goes. I have it installed, and's there...but it's rather...odd.

[IMG]http://pics.livejournal.com/bloodfyr/pic/000bb11c/[/IMG]

That's cropped from my desktop. The green is part of my desktop background. Engage appears as that massive black bar. Clicking config does nothing (literally...nothing happens when I click it) ANY help would be appreciated. ](*,)

---

### Post by BLTicklemonster on 2006-12-12
Isn't there like just a deb file somewhere? This is crazy. I tried enlightenment before, and it's really pretty, but there's not a single way I have found to use the left mouse button in it unless you use ctrl or something totally off the wall like that, and to top it off, there's not a single place anywhere where I could find any place to launch a single application. Anywhere. And trying to find documentation to help was like the ultimate "it's linux, if you don't get it, install windows" experience. 

And there's no way I have found, looking through this entire thread, to get past 

Do you want to continue? [Y/n/?] y
Segmentation fault (core dumped)on... 1%

at all.

I went to the enlightenment web site, and was thinking I'd install e16 or 17, but man, that was a total wash out. The logic linux folks use in determining to tell the world, "here, download this specific stuff" is mind boggling. I really wish they could learn that there are people out here who would enjoy the fruits of their labor if only they'd LEARN TO FREAKING TONE IT DOWN and put stuff out there that any average Joe walking down the street would be able to use!

Rant over.

Now is there a deb file that I can install, and a list of dependencies that don't bring up other dependency issues when I try to install them? Yep, I tried the deb from enlightenment.com, and the other associated files, and let me tell you, it's a total nightmare for me. I've been using ubuntu for over a year, and this is "the beatingest thing" I've ever seen.

If this is enlightenment, leave me in a blackbox. (pun intended, but the nature of the remark was solely for humor :) )

---

### Post by BLTicklemonster on 2006-12-13
After installing the dependencies listed on enlightenment's site:

```
bill@bill-desktop:~$ sudo aptitude clean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
bill@bill-desktop:~$ sudo aptitude install enlightenment emodules0-all
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No candidate version found for enlightenment
The following packages are BROKEN:
  emodule0-bling emodule0-cpu emodule0-deskshow emodule0-emu emodule0-eveil 
  emodule0-flame emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan emodules0-all 
The following NEW packages will be automatically installed:
  libecore0 libecore0-con libecore0-config libecore0-dbus libecore0-desktop 
  libecore0-directfb libecore0-evas libecore0-file libecore0-ipc 
  libecore0-job libecore0-txt libecore0-x libeet0 libevas0 libexml0 
The following NEW packages will be installed:
  libecore0 libecore0-con libecore0-config libecore0-dbus libecore0-desktop 
  libecore0-directfb libecore0-evas libecore0-file libecore0-ipc 
  libecore0-job libecore0-txt libecore0-x libeet0 libevas0 libexml0 
0 packages upgraded, 39 newly installed, 0 to remove and 0 not upgraded.
Need to get 4351kB of archives. After unpacking 9466kB will be used.
The following packages have unmet dependencies:
  emodule0-screenshot: Depends: enlightenment but it is not installable
  emodule0-wlan: Depends: enlightenment but it is not installable
  emodule0-language: Depends: enlightenment but it is not installable
  emodules0-all: Depends: enlightenment but it is not installable
  emodule0-mail: Depends: enlightenment but it is not installable
  emodule0-bling: Depends: enlightenment but it is not installable
  emodule0-photo: Depends: enlightenment but it is not installable
  emodule0-deskshow: Depends: enlightenment but it is not installable
  emodule0-taskbar: Depends: enlightenment but it is not installable
  emodule0-flame: Depends: enlightenment but it is not installable
  emodule0-moon: Depends: enlightenment but it is not installable
  emodule0-mixer: Depends: enlightenment but it is not installable
  emodule0-rain: Depends: enlightenment but it is not installable
  emodule0-cpu: Depends: enlightenment but it is not installable
  emodule0-uptime: Depends: enlightenment but it is not installable
  emodule0-emu: Depends: enlightenment but it is not installable
  emodule0-mem: Depends: enlightenment but it is not installable
  emodule0-net: Depends: enlightenment but it is not installable
  emodule0-eveil: Depends: enlightenment but it is not installable
  emodule0-tclock: Depends: enlightenment but it is not installable
  emodule0-snow: Depends: enlightenment but it is not installable
  emodule0-winselector: Depends: enlightenment but it is not installable
  emodule0-slideshow: Depends: enlightenment but it is not installable
  emodule0-weather: Depends: enlightenment but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
enlightenment [1:0.16.7.2-3ubuntu1 (edgy)]
enlightenment-data [1:0.16.7.2-3ubuntu1 (edgy)]
libimlib2 [1.3.0-0cvs20061011 (edgy)]

Score is -197

Accept this solution? [Y/n/q/?] y
The following NEW packages will be automatically installed:
  emodule0-bling emodule0-cpu emodule0-deskshow emodule0-emu emodule0-eveil 
  emodule0-flame emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan enlightenment enlightenment-data libecore0 libecore0-con 
  libecore0-config libecore0-dbus libecore0-desktop libecore0-directfb 
  libecore0-evas libecore0-file libecore0-ipc libecore0-job libecore0-txt 
  libecore0-x libeet0 libevas0 libexml0 libimlib2 
The following NEW packages will be installed:
  emodule0-bling emodule0-cpu emodule0-deskshow emodule0-emu emodule0-eveil 
  emodule0-flame emodule0-language emodule0-mail emodule0-mem 
  emodule0-mixer emodule0-moon emodule0-net emodule0-photo emodule0-rain 
  emodule0-screenshot emodule0-slideshow emodule0-snow emodule0-taskbar 
  emodule0-tclock emodule0-uptime emodule0-weather emodule0-winselector 
  emodule0-wlan emodules0-all enlightenment enlightenment-data libecore0 
  libecore0-con libecore0-config libecore0-dbus libecore0-desktop 
  libecore0-directfb libecore0-evas libecore0-file libecore0-ipc 
  libecore0-job libecore0-txt libecore0-x libeet0 libevas0 libexml0 
  libimlib2 
0 packages upgraded, 42 newly installed, 0 to remove and 0 not upgraded.
Need to get 7594kB of archives. After unpacking 16.2MB will be used.
Do you want to continue? [Y/n/?] y
Segmentation fault (core dumped)on... 1%
bill@bill-desktop:~$ 
```

What where how and why?

---

### Post by Lut!n on 2006-12-13
because you may have a pin on enlightenment in /etc/apt/preferences. If it is the cas, remove it and try again

---

### Post by BLTicklemonster on 2006-12-13
I was up until two in the morning trying to compile eet and jpeg-6 and all kinds of garbage. One of the most linuxy frustrating darned times I have ever seen!








pins in preferences huh?




Now how in the name of Sam Hill did those get in there? 


Thanks Lut!n. This is amazing how fast it is!

---

### Post by BLTicklemonster on 2006-12-13
Okay, I use xmodmap to get my forward/back buttons on my mouse to work, adding it to startup in fluxbox, and it loads automagically in gnome. How would I get it to load up on start up in E17? (which is way cool. I can't believe there's this much eye candy and it is still this fast.)

---

### Post by whizbaby on 2006-12-13
> **BLTicklemonster said:**
> 
I went to the enlightenment web site, and was thinking I'd install e16 or 17, but man, that was a total wash out. The logic linux folks use in determining to tell the world, "here, download this specific stuff" is mind boggling. I really wish they could learn that there are people out here who would enjoy the fruits of their labor if only they'd LEARN TO FREAKING TONE IT DOWN and put stuff out there that any average Joe walking down the street would be able to use!


Then 'average Joe' perhaps should install e16 (enlightenment, no need to compile) from the repos instead of using the not even officially released (so sometimes broken) e17...(I think it's stated a few times on the enlightenment site and in this thread)
BTW for me e16 from repos worked out-of-the-box like 20 times on different machines. If you want software that you don't have to care so much about install from repos and don't use beta stuff.

---

### Post by BLTicklemonster on 2006-12-13
Good points, all, but around here, your (our) average Joe tweaks and customized every cotton picking thing they can get their cotton picking hands on, from Honda Civics with those obnoxious mosquito fart mufflers to mobile homes with low profile Pirellis and chrome wheels. So yeah, I guess I keep forgetting about the average average Joe.

:)

---

### Post by BLTicklemonster on 2006-12-13
> **costis said:**
> Everything seems to work fine with 016.999.036, but the flame module has a really awkward look  according to the attached picture. How could I fix it?

When you go to where you set the flames, just click on configure, then check anything but "gold". :)

Have you tried snow and rain yet? Looks pretty neat when you have snow falling, turning to rain, then flames below it. Heavy on the system, though...

---

### Post by BLTicklemonster on 2006-12-14
Okay, this is cool. But I need to know how to get xmodmap to work so I have mouse buttons to navigate web pages. Anyone know how to do this?

---

### Post by easytiger on 2007-03-15
These instructions don't work: don't waste your time.

Also, hasnt e17 been in devolpment for 6  or 7 years? Really should get their act together before they get left behind.

---

### Post by Adler on 2007-03-15
> These instructions don't work: don't waste your time.

easytiger,

Wow, that was harsh. But, I'd forgotten about trying E17 as a Desktop. I'd not been aware that it was sill around as an option.

Adler

---

### Post by whizbaby on 2007-03-16
> **easytiger said:**
> 
Also, hasnt e17 been in devolpment for 6  or 7 years? Really should get their act together before they get left behind.
Yo. But theres only few developers and they got lives, too...
And its better to release a well done thing than to stick to dates (like MS does...). Nevertheless I'm getting a little impatient novadays ;)

---

### Post by loell on 2007-03-16
don't bother asking the final release , carsten (the lead developer) has already been numb , for years on users asking the final release. despite the fact that he invested so much effort, time , and sometimes money for the enlightenment development , some users just doesn't want to understand. that this how open source development works, it could take a decade and it will still be alpha.


    you can speed up some work by supporting the project.

---

### Post by BLTicklemonster on 2007-03-16
So if I try to install this in Feisty using edgy repos, will it dork out my system?

---

### Post by Kiwi-Hawk on 2007-08-18
Hi all

I came back

I jus updated my machine a wee bit and had to reinstall my OS still running Mepis but this version is 6.5.02 out of the box almost,..

I got me a PX8800 GTS DHT video card so had a wee hasslet getting the drivers sorted but thats do and re did my repos and installed E17 and it's running fine,.. but small problem is (guess) Linux / Windoz and my duel screen setup.

Windoz puts screen 0 on the left hand side and Linux puts it on the right,.. so I managed to swap stuff over on my KDE deasktop but E17 puts the main screen on my right and I need to change that back to my left monitor,. I right clicked and selected resize/move for the shelf but it's not moving anywhere, so I have not been able to swap the main shelf over to my left screen.

I also wish to load my dir of jpg's for my wallpaper but I'm unsure now how to import them as it's been quite a while since I used Linux never mind E and need to catch up a bit

I managed to sort most stuff out now,.. but I'm getting an error trying to import wallpaper in jpg form,.. I'v checked and install all the eet stuff and made sure linjpeg is installed
and stiff have issues

Cheers
Kiwi-Hawk

---

