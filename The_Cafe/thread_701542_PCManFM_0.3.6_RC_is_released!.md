---
title: "PCManFM 0.3.6 RC is released!"
date: 2006-09-07
forum: The Cafe
---

### Post by PCMan on 2006-09-07
Homepage: [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)
More info:[http://www.gnomefiles.org/app.php?soft_id=1263](http://www.gnomefiles.org/app.php?soft_id=1263)
Project page: [http://sourceforge.net/projects/pcmanfm/](http://sourceforge.net/projects/pcmanfm/)

[IMG]http://pcmanfm.sourceforge.net/screenshot0.png[/IMG]

PCManFM is an extremly fast and lightweight gtk+2 file manager which features tabbed browsing and user-friendly interface.
It's aimed to be a lightweight replacement for nautilus or other heavy file managers.
For full introduction of PCManFM, please go to our homepage.

The latest version 0.3.2 beta has supports for volume management(mount/umount) and displaying icons on desktop.

Here is a screenshot of my current desktop environment:
[http://pcman.sayya.org/pcmanfm/pcmanfm_fbpanel.png](http://pcman.sayya.org/pcmanfm/pcmanfm_fbpanel.png)
The desktop icons are proviede by PCManFM.
The window manager used is IceWM, and the panel at the bottom is a special version of fbpanel modified by me (Adding a much better menu to original fbpanel).
Note: All these 3 programs have no gnome dependencies.

For those who wants to replace nautilus with pcmanfm, I'll write some HOWTO when I have time. The most easy way is uninstalling nautilus, or remove its *.desktop files on the system, and then, run "sudo update-mime-database /usr/share/mime". This might work or might not. If this doesn't work, try "sudo ln -s /usr/bin/pcmanfm /usr/bin/nautils".  <--- This is the worst but effective way.

---

### Post by Onyros on 2006-09-07
Sweeeeeeeeeet! I've been using it since version 0.2.2, and it's my file manager of choice :D

Very cool new features, btw. I'll give it a spin and give some feedback soon.

---

### Post by CostinChirvasuta on 2007-02-04
My favourite as well... I hate nautilus!

---

### Post by SunnyRabbiera on 2007-02-04
Not bad...
a few things I dont like though, for one I would want a feature to send objects to my trash bin as opposed to just flat out deleting them.
another feature I would like is to use a better wallpaper uploader.
I hope thats on the drawing table, as its the same issues i have with other some other file managers like thunar.
But its beta so I can give you your leeway :D

---

### Post by K.Mandla on 2007-02-04
> **CostinChirvasuta said:**
> My favourite as well...
I agree. This is much more fun than Nautilus or Thunar. I love the tabbed explorer windows and -- believe it or not -- I prefer not to have a trash can. :D

---

### Post by PCMan on 2008-01-24
[IMG]http://pcmanfm.sourceforge.net/screenshot0.png[/IMG]

Homepage: [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)
GnomeFiles: [http://www.gnomefiles.org/app.php/PCMan_File_Manager](http://www.gnomefiles.org/app.php/PCMan_File_Manager)

There is no new release for more than one year, but the project is NOT dead. The author was very busy, and currently focus on his work.

To see the current status and future plan of the project, please refer to this page.
[http://pcmanfm.sourceforge.net/plan.html](http://pcmanfm.sourceforge.net/plan.html)

There the new feature is not exciting enough, but this release comes with lots of important fixes.

* The underlying mime-type system was completely re-designed and re-written from scratch. Now it's faster, more robust, and more standard compliant. The memory usage was reduced, too. By installing a xml file to the shared-mime-database, mime-type detection was enhanced.

* New shortcut keys are supported: Now both 'Alt+D' and 'Ctrl+L' can focus the path bar, and 'Backspace' brings you to parent folder.

* Left click on the text of path bar with 'Ctrl' key held down now brings you to parent folders quickly.
  Here is a demo. [http://tw.youtube.com/watch?v=aGUOvSMWm6c](http://tw.youtube.com/watch?v=aGUOvSMWm6c)

* Add some new locales: tr, eu, ja

* Folder views are correctly updated when files get deleted or created. Some FAM-related bugs were fixed.

* Command line arguments handling was improved. Now you can open multiple files with pcmanfm through command line.

* Correctly handle desktop directory in the side pane. (Get the path of desktop directory from ~/.config/user-dirs.dirs. Hide the item if the directory didn't exist.)

* config files were moved to ~/.config/pcmanfm to follow the new standard.

* Better-looking about dialog, a must-have for every program. :-P

* BTW, personally I think this is the most suitable default file manager for EeePC. Anyone wants to try it?

Tips and Tricks:
Gnome didn't completely follow the spec of FreeDesktop.org, and ignores the settings for default file manager.
The default file manager of Gnome was hard-coded and tight to Nautilus. It cannot be changed even if you set other programs to default handler of folders.
So, here's 2 ways:

1. manually edit the config file of gconf, add a URI handler for "file://". This should be done under console or Gnome will overwrite your change before shutting down.

2. Simply create a symlink.
ln -s "your file manager" to /usr/bin/nautilus. I know this is very dirty, but this way is easier. To use pcmanfm as your default, just  ln -s /usr/bin/pcmanfm /usr/bin/nautilus.
PCManFM can recognize the --no-desktop argument of Nautilus, so there won't be problems.

General info about PCManFM:

PCManFM is an extremly fast and lightweight file manager which features tabbed browsing and user-friendly interface.
It's desktop-dependent, and has only minimal dependencies.
 
* Extremly fast and lightweight
* Can be started in one second on normal machine
* Tabbed browsing (Similiar to Firefox)
* Drag & Drop support
* Support mount/umount/eject for volumes (Linux-only, requires HAL)
* Provide desktop icons (with basic wallpaper support)
* Files can be dragged among tabs
* Load large directories in reasonable time
* File association support (Default application)
* Basic thumbnail support
* Bookmarks support
* Handles non-UTF-8 encoded filenames correctly
* Provide icon view and detailed list view
* Standard compliant (Follows FreeDesktop.org)
* Clean and user-friendly interface (GTK+ 2)

---

### Post by ice60 on 2008-01-24
coool, thanks. there's a thread about PCManFM now.
[http://ubuntuforums.org/showthread.php?t=675881](http://ubuntuforums.org/showthread.php?t=675881)

---

### Post by PCMan on 2008-01-24
OK, here is a ubuntu package for ubnutu gutsy.
[http://www.gnomefiles.org/download.php?soft_id=1263&where=http%3A%2F%2Fdownloads.sourceforge.net%2Fpcmanfm%2Fpcmanfm_0.3.5.3b-1ubuntu2_i386.deb%3Fuse_mirror%3Djaist](http://www.gnomefiles.org/download.php?soft_id=1263&where=http%3A%2F%2Fdownloads.sourceforge.net%2Fpcmanfm%2Fpcmanfm_0.3.5.3b-1ubuntu2_i386.deb%3Fuse_mirror%3Djaist)

---

### Post by KThrace on 2008-01-24
You the MAN PCMan!

/yes I know that's lame. :)

---

### Post by ice60 on 2008-01-24
is there any chance of having columns like this if you want that kind of view? i think it would make PCManFM very popular!
[http://thunar.xfce.org/wiki/ui:columns-view](http://thunar.xfce.org/wiki/ui:columns-view)

---

### Post by Mateo on 2008-01-24
does this do desktop icons?

---

### Post by smartboyathome on 2008-01-24
> **Mateo said:**
> does this do desktop icons?

Surprisingly, yes it does. Though I still prefer Thunar over it. The one thing I miss in PCManFM is the ability to use scripts like in Nautilus and Thunar. :(

---

### Post by K.Mandla on 2008-01-24
Fantastic news; I really love PCManFM. Thanks!

---

### Post by TeaSwigger on 2008-01-24
Thank you, PCMan, for your apps. They are very useful and greatly appreciated by myself and many others.

---

### Post by K.Mandla on 2008-01-24
Another screenie, this one running with Openbox and compiled on Arch.

[attach]57435[/attach]

It seems very fast.

---

### Post by PCMan on 2008-01-25
Version 0.3.5.4 beta was released.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=57538&stc=1&d=1201300899[/IMG]

Pleaese go to project page for download.
deb package is available for ubuntu.
[https://sourceforge.net/projects/pcmanfm/](https://sourceforge.net/projects/pcmanfm/)

Changes:

* Left click on the text of path bar with 'Ctrl' key held down now brings you to parent folders quickly.

Here is a DEMO on youtube.
[http://tw.youtube.com/watch?v=aGUOvSMWm6c](http://tw.youtube.com/watch?v=aGUOvSMWm6c)

* New shortcut keys are supported: Now both 'Alt+D' and 'Ctrl+L' can focus the path bar, and 'Backspace' brings you to parent folder.

* Remove the useless "Address" label on the path bar.

* Fix segfault in app chooser dialog.

---

### Post by Polygon on 2008-01-26
how do i make this default? and how do i change it back in case i dont like it? =P

---

### Post by graabein on 2008-01-26
Thanks PCMan, great news! I was afraid the project was dead.

> **ice60 said:**
> is there any chance of having columns like this if you want that kind of view? i think it would make PCManFM very popular!
[http://thunar.xfce.org/wiki/ui:columns-view](http://thunar.xfce.org/wiki/ui:columns-view)

I agree on this. Having both tabs and columns would be fantastic.

> **K.Mandla said:**
> Another screenie, this one running with Openbox and compiled on Arch.

[Still Life]("http://art.gnome.org/themes/icon/1111") icons! Now there's a project I'd love to see come back to life!!

---

### Post by graabein on 2008-02-02
I have a question. In my *Places* menu in **Nautilus** my *sdc1* drive is called *store* (as I named it) but in **PCManFM** there's no name for it, it just shows up as *sdc1*. How do I rectify this?

---

### Post by PCMan on 2008-02-02
> **graabein said:**
> I have a question. In my *Places* menu in **Nautilus** my *sdc1* drive is called *store* (as I named it) but in **PCManFM** there's no name for it, it just shows up as *sdc1*. How do I rectify this?
There is no standard way to generate display name of volumes, so every program has its own way to do this. As a result, there will be lots differences.

---

### Post by PCMan on 2008-02-02
BTW, version 0.3.5.7 is out.
Volume management part is completely re-written.
Besides there are some minor fixes for the UI.
Please give it a try.

---

### Post by graabein on 2008-02-03
Installed version 0.3.5.7 and instead of *sdc1* it is now called *225.4 GB Volume*.




Another thing: Some images are not previewed but shown with their mimetype icon. Not even when I press refresh (F5) and restart the file manager. How come? Is this a bug? Or is it because of the file size?

---

### Post by bonzodog on 2008-02-03
I am having major problems here with a Zenwalk compile of pcmanfm - It segfaults as user, but runs fine when run as root, though the icons are not displayed. Someone has also mentioned this in the bugs list. An strace for me did not solve anything.
I actually suspect that this is because I, like others running light desktops, do not run a settings manager of any sort, and instead all my themes and icons are set through the gtkrc files. I have spoken to others running it and they are not having this problem, it runs fine for them. However, the greater majority of them run the xfce-settings-manager.
I am currently trying to get it confirmed that this is indeed the problem.
This is a code change you have implemented since 0.3.2.2, as that version runs fine on my system.

---

### Post by Ebuntor on 2008-02-03
PCMan, I have to say it's an excellent file manager, very fast.
If I have any suggestions or feature requests should I post them on your SourceForge forum or can I post them here?

---

### Post by SunnyRabbiera on 2008-02-03
I do like this, but I still wish there was a "send to trash" in there instead of the delete menu

---

### Post by Freddy on 2008-02-08
I successfully compiled this on a OzOS setup witch is based on Ubuntu amd64 but with Enlightenment17 instead of Gnome. I cant start Pcman FM, segmentation fault.

---

### Post by rocknrolf77 on 2008-02-09
Thank you for an exellent filemanager :) 

Was going too check for the beta on aur in arch but archlinux.org is down for the moment :(

---

### Post by bonzodog on 2008-02-10
> **Freddy said:**
> I successfully compiled this on a OzOS setup witch is based on Ubuntu amd64 but with Enlightenment17 instead of Gnome. I cant start Pcman FM, segmentation fault.

Yeah, I think we may have pinned the bug down;
It appears to run fine on systems that use either the gnome settings manager or the xfce settings manager or the KDE version of it, but it will not run on a system that is not running on these, thus it won't run on one of the other WM's that isn't running a settings manager in the background. For some reason, it will run as root though (try sudo pcmanfm).
I have reverted to 3.2.2 for now as that works.

---

### Post by zOUTHEN on 2008-02-10
(EDIT: **********)- ahh,nvm,,,

---

### Post by PCMan on 2008-02-10
> **bonzodog said:**
> Yeah, I think we may have pinned the bug down;
It appears to run fine on systems that use either the gnome settings manager or the xfce settings manager or the KDE version of it, but it will not run on a system that is not running on these, thus it won't run on one of the other WM's that isn't running a settings manager in the background. For some reason, it will run as root though (try sudo pcmanfm).
I have reverted to 3.2.2 for now as that works.
That's impossible.
This program is desktop independent.
GTK+ itself doesn't require setting manager, but if you don't run a setting manager, there should be a properly configured ~/.gtkrc-2.0.
I use it under icewm and it works fine without any problems.

So, would you please provide any error messages?

---

### Post by bonzodog on 2008-02-10
The problem is that it segfaults as user, but works ok as root.
The main problem with a segfault is that you don't get error messages.
Another user on your sourceforge bugs list has provided a gdb bug trace.

I tried to run it past strace, but the most I got was a complaint about the locale settings, as I have my locale set to en_ie@uft8. However, i tried setting it back to en_us, and it didn't change anything.

How we came to the settings manager conclusion is when I discovered people in my own distro community using it without problems then trying to fault find by comparing differences. the ONLY thing we could find that could possibly be linked was the fact that they ran settings managers.

I have just confirmed this as I have now got an xfce fresh zen install on my laptop, and your latest release works fine with it. However it does not work with my Zen core with openbox only on it.

Another thing I have just stumbled across; could it be connected to gconfd? I have just discovered that I do not run gconfd in the background as user, but that still does not explain why it will run under su as root.

---

### Post by xZaiN on 2008-02-11
I used to get a segmentation fault on my ArchLinux box (wm: openbox), i couldn't even start pcmanfm, and when i tried to start from terminal i would get a clean "segmentation fault" error message

Two things i had to do, was first.
Create a Desktop folder in your home folder, pcmanfm didn't create one when i installed it.

And the second thing  i had to do was, chmod the /tmp/ folder.
"sudo chmod 1777 /tmp/"

After i did that i didn't get any more errors and it looks like everything works,
no crashes...

---

### Post by PCMan on 2008-02-11
> **xZaiN said:**
> I used to get a segmentation fault on my ArchLinux box (wm: openbox), i couldn't even start pcmanfm, and when i tried to start from terminal i would get a clean "segmentation fault" error message

Two things i had to do, was first.
Create a Desktop folder in your home folder, pcmanfm didn't create one when i installed it.

And the second thing  i had to do was, chmod the /tmp/ folder.
"sudo chmod 1777 /tmp/"

After i did that i didn't get any more errors and it looks like everything works,
no crashes...

Thanks a lot!  Nice hint!
Problem related to desktop dir is fixed in the svn repo.
The /tmp problem is not as easy since pcmanfm created a UNIX socket in /tmp. Maybe I have to change the file path?

---

### Post by PCMan on 2008-02-11
We are close to 0.3.6 stable release now.
There is few new feature. However, upgrade to this version is highly recommended.

1. Thumbnail support is re-written, and both the speed and stability are improved. Random crashes during thumbnail loading is already fixed.

2. Minor UI improvements and bug fixes

For detail:  
[http://www.gnomefiles.org/app.php/PCMan_File_Manager](http://www.gnomefiles.org/app.php/PCMan_File_Manager)

Ubuntu package is available.

---

### Post by bonzodog on 2008-02-11
Yes!
Do'h
I feel SO stupid now.
oh, well, even the more experienced of us make mistakes. 
The missing Desktop dir problem fixed my install. I created the Desktop dir and it now works fine.

---

### Post by Freddy on 2008-02-11
> **bonzodog said:**
> Yes!
Do'h
I feel SO stupid now.
oh, well, even the more experienced of us make mistakes. 
The missing Desktop dir problem fixed my install. I created the Desktop dir and it now works fine.
That makes two of us. Creating a 'Desktop' dir made it for me two :).

---

### Post by PCMan on 2008-02-11
> **bonzodog said:**
> Yes!
Do'h
I feel SO stupid now.
oh, well, even the more experienced of us make mistakes. 
The missing Desktop dir problem fixed my install. I created the Desktop dir and it now works fine.
Well, I felt so stupid, too.
I remember to return NULL from vfs_get_desktop_dir to indicate there is no ~/Desktop dir, but I forgot to check if the returned value is NULL.. (What a stupid programmer...)
So it's fixed in the svn repo now.
Please check it out.
Thank you all.

---

### Post by Freddy on 2008-02-11
Will you add 'Move to Trashcan' in a future release?

---

### Post by PCMan on 2008-02-11
> **Freddy said:**
> Will you add 'Move to Trashcan' in a future release?
Yes, in the "FUTURE".
Trash can will not show up in 0.3.6, but it's already planned.

Future plan of PCManFM 0.4:
1. File search tool
2. Trash can support
3. Improve UI

Future plan of PCManFM 0.5:
1. Improve desktop icons
2. Mounting support for FUSE.

---

### Post by Freddy on 2008-02-11
That sounds like a nice 'feature plan', PCManFM will become even better.

---

### Post by TeaSwigger on 2008-02-12
Alas, I've been having troubles with the newer (after the mime-type rewrite) versions. It completely ignores anything I do when choosing default apps to open a file type. It will open a given file in a given app one time, but does not remember the choice. I'm using it as my file manager when using Fluxbox on Kubuntu. If anyone knows what might be wrong, I would appreciate the suggestions.

---

### Post by PCMan on 2008-02-12
> **TeaSwigger said:**
> Alas, I've been having troubles with the newer (after the mime-type rewrite) versions. It completely ignores anything I do when choosing default apps to open a file type. It will open a given file in a given app one time, but does not remember the choice. I'm using it as my file manager when using Fluxbox on Kubuntu. If anyone knows what might be wrong, I would appreciate the suggestions.
Check your ~/.local/share/mime/defaults.list
Maybe the problem is due to you don't have that directory?
If that is the case, create the dir and try again.
I don't know the answer yet, but I think this is the possible cause.
I'll work on this later.

About the default app, currently there is no standard for this.
KDE, gnome, xfce, and rox desktop all use their own mechanism.
PCManFM previously use our own implementation which works well, but now I try to be as compatible with gnome as much in this version.
In my opinion, the gnome way is horrible, but I still have to follow it for maximal compatibility.

---

### Post by TeaSwigger on 2008-02-12
Thank you for the reply. I did not have ~/.local/share/mime/ in Kubuntu, I only had ~/.local/share/ so I created ~/.local/share/mime/. Unfortunately this did not change the problem. 

I understand the problem of compatibility and know it must be frustrating. I'll understand if you can't fix this, but hopefully there will be some way to fix or to work around the problem. :)

---

### Post by PCMan on 2008-02-12
> **TeaSwigger said:**
> Thank you for the reply. I did not have ~/.local/share/mime/ in Kubuntu, I only had ~/.local/share/ so I created ~/.local/share/mime/. Unfortunately this did not change the problem. 

I understand the problem of compatibility and know it must be frustrating. I'll understand if you can't fix this, but hopefully there will be some way to fix or to work around the problem. :)

Sorry, my mistake.
Please create ~/.local/share/applications, if you don't have one.

---

### Post by PCMan on 2008-02-12
> **PCMan said:**
> Sorry, my mistake.
Please create ~/.local/share/applications, if you don't have one.
BTW, can anyone test the latest code in svn repo?
I think this was fixed.

---

### Post by TeaSwigger on 2008-02-12
> **PCMan said:**
> Sorry, my mistake.
Please create ~/.local/share/applications, if you don't have one.

Yes I have had ~/.local/share/applications. It contains: defaults.list and mimeinfo.cache. defaults.list is empty and settings in mimeinfo.cache are ignored. Unfortunately I don't know how to use a svn yet.

Thank you again for all the work on this :)

---

### Post by yabbadabbadont on 2008-02-12
> **PCMan said:**
> BTW, can anyone test the latest code in svn repo?
I think this was fixed.

I haven't built the code yet (and I run Gentoo), but I found that the subversion instructions on the project webpage list the old, and incorrect, svn address at sourceforge.  I opened a bug about it on the tracker.

The correct svn address is:

[http://pcmanfm.svn.sourceforge.net/svnroot/pcmanfm/trunk/pcmanfm/pcmanfm](http://pcmanfm.svn.sourceforge.net/svnroot/pcmanfm/trunk/pcmanfm/pcmanfm) pcmanfm

Sourceforge must have rearranged their repo (again).

---

### Post by yabbadabbadont on 2008-02-12
Well, it seems to work fine so far.  I don't use HAL so I built it without hal support and I didn't enable inotify either.  Is inotify still broken as reported by "./configure --help"?

The only annoyance I have found so far, is that clicking on a directory in the tree view pane, causes that directory to be expanded in that pane.  This is annoying if the directory contains a large number of sub-directories.  It would be nice if there were an option to control this behavior.

---

### Post by PCMan on 2008-02-12
> **yabbadabbadont said:**
> Well, it seems to work fine so far.  I don't use HAL so I built it without hal support and I didn't enable inotify either.  Is inotify still broken as reported by "./configure --help"?

The only annoyance I have found so far, is that clicking on a directory in the tree view pane, causes that directory to be expanded in that pane.  This is annoying if the directory contains a large number of sub-directories.  It would be nice if there were an option to control this behavior.
inotify support is still broken.
The problem of inotify is, it only fires notification for files with inodes. Many files on the system don't have inode. Besides, through mounting, the inode of directories might change. That means, we have to do a lot of dirty hacks to overcome these situations. So, I personally don't want to do it. Since it's a pain, why not let gamin / fam handle these for us? It's what they are designed for.

---

### Post by PCMan on 2008-02-13
Version 0.3.5.9 is there.
deb package was provided.
Have fun!

---

### Post by yabbadabbadont on 2008-02-13
> **PCMan said:**
> Version 0.3.5.9 is there.
deb package was provided.
Have fun!

Great.  Two hours after I pull the svn and build it, you release a new version...  Thanks a lot.  :lol:

I'll svn up to see if anything has changed, but I'm guessing that you are just announcing the deb availability.  ;)

---

### Post by PCMan on 2008-02-14
0.3.5.10 beta was released
Changes:
* Fix several bugs in mime-type detection.
* Add drop down menu for "back" and "forward" buttons.
* Open dir in new tab when middle clicking on dir tree.
* Other minor bug fixes.

[http://www.gnomefiles.org/app.php/PCMan_File_Manager](http://www.gnomefiles.org/app.php/PCMan_File_Manager)

deb packages for Ubuntu feisty/gutsy was already provided.

---

### Post by yabbadabbadont on 2008-02-14
Time to svn up I guess.  ;)

---

### Post by yabbadabbadont on 2008-02-14
There is a pretty big regression in this version.  I guess that, while adding the ability to middle click in the tree pane to open a directory in a new tab, the left click code was broken.  I can middle click for a new tab.  I can right click and select "Open" on the pop-up menu.  I cannot left click to select a new directory in the tree pane.  I can tab key into it to give it focus, and then use the arrow keys to navigate, but left click for focus is broken in the current code.

Should I copy and paste all this into a bug in the tracker at sourceforge?

---

### Post by PCMan on 2008-02-14
> **yabbadabbadont said:**
> There is a pretty big regression in this version.  I guess that, while adding the ability to middle click in the tree pane to open a directory in a new tab, the left click code was broken.  I can middle click for a new tab.  I can right click and select "Open" on the pop-up menu.  I cannot left click to select a new directory in the tree pane.  I can tab key into it to give it focus, and then use the arrow keys to navigate, but left click for focus is broken in the current code.

Should I copy and paste all this into a bug in the tracker at sourceforge?
God.....I'm idiot.....
It's fixed in svn repo now.

---

### Post by yabbadabbadont on 2008-02-14
:lol:

Happens to everyone now and then.  I'll svn up again.

---

### Post by yabbadabbadont on 2008-02-14
That's better.  Thanks for the quick turnaround.

---

### Post by TeaSwigger on 2008-02-14
It works! I'm able to set the default app for file types again :mrgreen: \\:D/

Thank you! I'll give it some more use now and see how it works. :)

---

### Post by TeaSwigger on 2008-02-14
Found something lol... 

In the side pane, directory tree, I can not select anything by a left click. The location pane seems to work. I didn't notice this at first because I seldom use the side pane.

---

### Post by mozetti on 2008-02-14
> **TeaSwigger said:**
> Found something lol... 

In the side pane, directory tree, I can not select anything by a left click. The location pane seems to work. I didn't notice this at first because I seldom use the side pane.

This was already discussed on the preceding page. PCMan updated the SVN version and that's now fixed.

---

### Post by PCMan on 2008-02-14
* Fix regression bug: unable to select folder in dir tree.
* Create dialog UI using new lightweight PtkUIXml system and *.glade files "without" libglade.
* Decrease memory usage and size of executable file.

[http://www.gnomefiles.org/app.php/PCMan_File_Manager](http://www.gnomefiles.org/app.php/PCMan_File_Manager)

Please get it tested.
The window titles are incorrect sometimes, and that's a known bug, and was already fixed in the svn repo at the time of this writing.

If there is no other major problems, like random crashes, it will became 0.3.6 stable.

---

### Post by TeaSwigger on 2008-02-15
> **mozetti said:**
> This was already discussed on the preceding page. PCMan updated the SVN version and that's now fixed.

I was using the provided .deb not the svns. Sorry for any misunderstanding.

Will try out the latest .deb. :)

---

### Post by TeaSwigger on 2008-02-15
Using 0.3.5.20 from the .deb on Kubuntu. If it is of interest:

In the location view, I clicked on my not-mounted NTFS Windows partition by accident, and it crashed with a seg fault.

In the directory view, when I left clicked on a directory, I saw this in the terminal:
** (pcmanfm:5216): DEBUG: HERE
but it did work fine.

Everything else including setting default apps has been working fine.

P.S. speed is fantastic.

---

### Post by meborc on 2008-02-15
just wanted to say good luck :D i really love this file manager!

it is nice to see an active development going on

you rock! :guitar:

---

### Post by PCMan on 2008-02-19
After countless hours of work, we finally have 0.3.6 release candidate.
Most of the serious bugs found in previous version are already fixed.
There are few new features, but the correctness and robustness are greatly improved in this release.

The latest deb package is already in unstable repos of debian and Fedora, and hopefully will enter ubuntu repo soon.
Please get it heavily tested, and 0.3.6 stable will be released in several days. (Maybe next week)

This is mainly an important buf-fix release since last release in 2006.
After 0.3.6 stable release, we will focus on adding new features and moving forward toward 0.3.8.

Cheers!

Here is general information about this file manager, if you don't know it yet.

[IMG]http://pcmanfm.sourceforge.net/screenshot0.png[/IMG]

Homepage: [http://pcmanfm.sourceforge.net/](http://pcmanfm.sourceforge.net/)
GnomeFiles: [http://www.gnomefiles.org/app.php/PCMan_File_Manager](http://www.gnomefiles.org/app.php/PCMan_File_Manager)

There is no new release for more than one year, but the project is NOT dead. The author was very busy, and currently focus on his work.

To see the current status and future plan of the project, please refer to this page.
[http://pcmanfm.sourceforge.net/plan.html](http://pcmanfm.sourceforge.net/plan.html)

There the new feature is not exciting enough, but this release comes with lots of important fixes.

* The underlying mime-type system was completely re-designed and re-written from scratch. Now it's faster, more robust, and more standard compliant. The memory usage was reduced, too. By installing a xml file to the shared-mime-database, mime-type detection was enhanced.

* New shortcut keys are supported: Now both 'Alt+D' and 'Ctrl+L' can focus the path bar, and 'Backspace' brings you to parent folder.

* Left click on the text of path bar with 'Ctrl' key held down now brings you to parent folders quickly.
  Here is a demo. [http://tw.youtube.com/watch?v=aGUOvSMWm6c](http://tw.youtube.com/watch?v=aGUOvSMWm6c)

* Add some new locales: tr, eu, ja

* Folder views are correctly updated when files get deleted or created. Some FAM-related bugs were fixed.

* Command line arguments handling was improved. Now you can open multiple files with pcmanfm through command line.

* Correctly handle desktop directory in the side pane. (Get the path of desktop directory from ~/.config/user-dirs.dirs. Hide the item if the directory didn't exist.)

* config files were moved to ~/.config/pcmanfm to follow the new standard.

* Better-looking about dialog, a must-have for every program. :-P

* BTW, personally I think this is the most suitable default file manager for EeePC. Anyone wants to try it?

Tips and Tricks:
Gnome didn't completely follow the spec of FreeDesktop.org, and ignores the settings for default file manager.
The default file manager of Gnome was hard-coded and tight to Nautilus. It cannot be changed even if you set other programs to default handler of folders.
So, here's 2 ways:

1. manually edit the config file of gconf, add a URI handler for "file://". This should be done under console or Gnome will overwrite your change before shutting down.

2. Simply create a symlink.
ln -s "your file manager" to /usr/bin/nautilus. I know this is very dirty, but this way is easier. To use pcmanfm as your default, just  ln -s /usr/bin/pcmanfm /usr/bin/nautilus.
PCManFM can recognize the --no-desktop argument of Nautilus, so there won't be problems.

General info about PCManFM:

PCManFM is an extremly fast and lightweight file manager which features tabbed browsing and user-friendly interface.
It's desktop-dependent, and has only minimal dependencies.
 
* Extremly fast and lightweight
* Can be started in one second on normal machine
* Tabbed browsing (Similiar to Firefox)
* Drag & Drop support
* Support mount/umount/eject for volumes (Linux-only, requires HAL)
* Provide desktop icons (with basic wallpaper support)
* Files can be dragged among tabs
* Load large directories in reasonable time
* File association support (Default application)
* Basic thumbnail support
* Bookmarks support
* Handles non-UTF-8 encoded filenames correctly
* Provide icon view and detailed list view
* Standard compliant (Follows FreeDesktop.org)
* Clean and user-friendly interface (GTK+ 2)

---

### Post by Onyros on 2008-02-19
Congratulations! It was really fun watching PCManFM grow over time, I've been using it for some time now, and it's good to see the few bugs it had being squased, as well as an incredibly improved RAM usage and overall speed.

(Good to see that the worst bug it had has been squashed a few versions before, too - the fact that if you pressed delete with nothing selected made you delete the entire folder contents and the folder itself :P)

Keep it up, mate! I was glad to be one of the earliest promoters of PCManFM as a great replacement for slow and bloated FM's, much superior to Thunar in my view, though Thunar's still a bit more popular. Not for long, though :D

---

### Post by blithen on 2008-02-19
I've been looking for a new file manager I just might have to try this out...As long as it can load my wallpaper directory faster then nautilus then it will be okay. xD

---

### Post by notwen on 2008-02-19
Thanks for the heads up, I use PCManFM on my file server.  Glad it's already in the Debian repos, no waiting to try it out.  =]

---

### Post by spamzilla on 2008-02-19
PCMan FM is in the Ubuntu repos, but only version 0.3.2.2-2.

I'm going to give it a whirl, and if I remember, report back!

edit

You don't seem to have 0.3.6rc on your site...just various older versions :confused:

---

### Post by notwen on 2008-02-19
> **spamzilla said:**
> PCMan FM is in the Ubuntu repos, but only version 0.3.2.2-2.

I'm going to give it a whirl, and if I remember, report back!

edit

You don't seem to have 0.3.6rc on your site...just various older versions :confused:

Yeah, it's not available yet except in Debian and Fedora unstable repos, coming to Ubuntu unstable soon. =]

> The latest deb package is already in unstable repos of debian and Fedora, and hopefully will enter ubuntu repo soon.
Please get it heavily tested, and 0.3.6 stable will be released in several days. (Maybe next week)

---

### Post by graabein on 2008-02-23
Yay! Can't wait to try 0.3.6 for Ubuntu. How soon is soon?

---

### Post by bobbocanfly on 2008-02-23
> **graabein said:**
> Yay! Can't wait to try 0.3.6 for Ubuntu. How soon is soon?

A bug has been registered and I confirmed it but the lack of other action and the Feature Freeze (no major updates, no new packages) that is currently in effect makes it look like this is going to be updated in Ibex not Hardy.

---

### Post by thedaemon on 2008-02-26
I have now completely switched to this file manager! Great job! Keep up the good work.

---

### Post by johnraff on 2008-02-26
0.3.6 stable is out but I haven't found any .deb files for Ubuntu yet... (fingers crossed - I haven't had a lot of joy trying to compile stuff from source lately) :)

---

### Post by PCMan on 2008-02-26
> **johnraff said:**
> 0.3.6 stable is out but I haven't found any .deb files for Ubuntu yet... (fingers crossed - I haven't had a lot of joy trying to compile stuff from source lately) :)
Don't forget to search in getdeb.net first.
[http://www.getdeb.net/app/PCMan+File+Manager](http://www.getdeb.net/app/PCMan+File+Manager)
Good luck!

---

### Post by gsiliceo on 2008-03-02
The latest stable release is out! and its awesome i dont like trash can either  =D.
I just miss the networking support but i can use Gsambad for that.

---

### Post by K.Mandla on 2008-03-02
Merged similar threads.

---

