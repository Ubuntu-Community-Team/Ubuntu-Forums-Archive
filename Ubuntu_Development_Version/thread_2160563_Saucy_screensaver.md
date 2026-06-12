---
title: "Saucy screensaver"
date: 2013-07-07
forum: Ubuntu Development Version
---

### Post by Cavsfan on 2013-07-07
When I try to remove gnome-screensaver and install xscreensaver like in the past several distros it wants to take the gnome session with it:

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get remove gnome-screensaver
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-screensaver [COLOR=#ff0000]gnome-session-fallback gnome-session-flashback[/COLOR]
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
After this operation, 941 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

I don't want to remove the other 2 just the gnome-screensaver. Xscreensaver has to be manually started up at each login. :(
Any ideas?

---

### Post by Harry33 on 2013-07-08
> **Cavsfan said:**
> When I try to remove gnome-screensaver and install xscreensaver like in the past several distros it wants to take the gnome session with it:

```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get remove gnome-screensaver
[sudo] password for cavsfan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-screensaver [COLOR=#ff0000]gnome-session-fallback gnome-session-flashback[/COLOR]
0 upgraded, 0 newly installed, 3 to remove and 4 not upgraded.
After this operation, 941 kB disk space will be freed.
Do you want to continue [Y/n]? 

```

I don't want to remove the other 2 just the gnome-screensaver. Xscreensaver has to be manually started up at each login. :(
Any ideas?

This is because the gnome-session-flashback depends on gnome-screensaver.
However, I do not know why.
You can remove the transitional package gnome-session-fallback.

---

### Post by jbicha on 2013-07-08
> **Harry33 said:**
> This is because the gnome-session-flashback depends on gnome-screensaver.
However, I do not know why.
You can remove the transitional package gnome-session-fallback.

Look at
```
/usr/share/gnome-session/sessions/gnome-flashback.session
```

You're welcome to file a bug. It might be possible to use Debian's alternative system to handle this use case.

---

### Post by Cavsfan on 2013-07-08
> **Harry33 said:**
> This is because the gnome-session-flashback depends on gnome-screensaver.
However, I do not know why.
You can remove the transitional package gnome-session-fallback.

I do now see that gnome-session-fallback is just a transitional package and can be safely removed. I'll do that. Thanks. 

> **jbicha said:**
> Look at
```
/usr/share/gnome-session/sessions/gnome-flashback.session
```

You're welcome to file a bug. It might be possible to use Debian's alternative system to handle this use case.

```
cavsfan@cavsfan-MS-7529:~$ cat /usr/share/gnome-session/sessions/gnome-flashback.session
[GNOME Session]
Name=GNOME Flashback (No effects)
RequiredComponents=gnome-panel;gnome-settings-daemon;gnome-screensaver;metacity;

```

This is going to sound kind of lame but, I don't know how to file a bug or use Debian's alternative system. All I have ever done is add my name to an already existing bug that also affects me. :???:

Can I just edit that file and remove "gnome-screensaver"? Is that the fix so that I can uninstall it and have xscreensaver work at startup?

I guess this one too:
```
cavsfan@cavsfan-MS-7529:/usr/share/gnome-session/sessions$ cat /usr/share/gnome-session/sessions/gnome-flashback-compiz.session
[GNOME Session]
Name=GNOME Flashback
RequiredComponents=gnome-panel;gnome-settings-daemon;gnome-screensaver;compiz;
```

---

### Post by Cavsfan on 2013-07-08
I edited those two files and still get the same results when attempting to remove gnome-screensaver.
It still wants to take gnome-session-flashback with it.

```
cavsfan@cavsfan-MS-7529:~$ cat /usr/share/gnome-session/sessions/[COLOR=#ff0000]gnome-flashback.session [/COLOR]
[GNOME Session]
Name=[COLOR=#ff0000]GNOME Flashback (No effects)[/COLOR]
RequiredComponents=gnome-panel;gnome-settings-daemon;metacity;
```


```
cavsfan@cavsfan-MS-7529:~$ cat /usr/share/gnome-session/sessions/[COLOR=#ff0000]gnome-flashback-compiz.session [/COLOR]
[GNOME Session]
Name=[COLOR=#ff0000]GNOME Flashback[/COLOR]
RequiredComponents=gnome-panel;gnome-settings-daemon;compiz;
```

BTW I am logging into Gnome Flashback which is odd according to the file name of the session. It also has no icon on the white dot on the login screen while all of the others do.
Another odd thing is that in SPM when I click on gnome-screensaver properties and then dependencies it says that it conflicts with gnome-screensaver.

While the properties for gnome-session-flashback lists gnome-screensaver as it's first dependency.

---

### Post by zika on 2013-07-08
Dpkg/apt-get and others do not check files You're trying to edit...
Did You try to use dpkg with --ignore-depends...?
I think I did manage to purge one package long time ago with that switch...
Use --simulate before You do commit...

---

### Post by Cavsfan on 2013-07-08
> **zika said:**
> Dpkg/apt-get and others do not check files You're trying to edit...
Did You try to use dpkg with --ignore-depends...?
I think I did manage to purge one package long time ago with that switch...
Use --simulate before You do commit...

Thanks zika. I'll try that.

Here is the bug I finally figured out how to file it.  [https://bugs.launchpad.net/ubuntu/+bug/1199074](https://bugs.launchpad.net/ubuntu/+bug/1199074)

---

### Post by Cavsfan on 2013-08-01
Would this be the command to remove gnome-screensaver?

```
sudo dpkg -P gnome-screensaver --ignore-depends=gnome-session-fallback, gnome-session-flashback
```

Looked at the man page for dpkg and came up with the above. But, I would like some positive feedback before I do it. :redface:

I already have xscreensaver installed.

---

### Post by mc4man on 2013-08-01
Your command is backwards  - more like 
sudo dpkg   --ignore-depends=gnome-session-flashback -P gnome-screensaver
While that will remove gnome-screensaver you'll still end up with broken package

I'd just the unpack gnome-session-flashback .deb, edit the control file to remove the dependency, repack & install the edited .deb
gnome-session-fallback can be removed, no need to keep installed.
If inclined to do so I'll point you to a script or it can be done manually (best would be to rebuild gnome-session-fallback without the dep

---

### Post by Cavsfan on 2013-08-01
> **mc4man said:**
> Your command is backwards  - more like 
sudo dpkg   --ignore-depends=gnome-session-flashback -P gnome-screensaver
While that will remove gnome-screensaver you'll still end up with broken package

I'd just the unpack gnome-session-flashback .deb, edit the control file to remove the dependency, repack & install the edited .deb
gnome-session-fallback can be removed, no need to keep installed.
If inclined to do so I'll point you to a script or it can be done manually (best would be to rebuild gnome-session-fallback without the dep

Thanks for that! I am glad I didn't just jump on it. I can just remove gnome-session-fallback as it is a transitional package right?
Then I haven't a clue how to unpack gnome-session-flashback .deb, edit it, etc.
Thanks for the help! :D

---

### Post by Cavsfan on 2013-08-02
**mc4man**, if it is not too much trouble I would very much appreciate learning how to do the steps above to fix this problem.
I like learning new things and you'll only have to tell me once.
Thanks :D

---

### Post by mc4man on 2013-08-02
> **Cavsfan said:**
> **mc4man**, if it is not too much trouble I would very much appreciate learning how to do the steps above to fix this problem.
I like learning new things and you'll only have to tell me once.
Thanks :D
Sorry - i was involved in seeing if I like this change to ambiance (dark toolbars all around) & how much work it would be to keep reverting if I don't.
(actually don't like in nautilus, prefer just dark window deco & to color toolbar & sidebar the same. Oh well...

I wanted to test a bit on the removing of the dep & actual removal of gnome-screensaver, doesn't seem to be any issue. 
Actually went ahead & built a patched gnome-panel in my saucy testing ppa but it'll not be suitable for you as you're using a gnome-panel .deb that was was attached to a bug report & in the case of ppa all panel packages must be updated
(if you know of the patch to fix white panels post a link ..

So anyway - 
to do manually & just edit gnome-flashback's control file

Thread with script - you'll want to use the one in post 4 as it uses gedit
[http://ubuntuforums.org/showthread.php?t=636724](http://ubuntuforums.org/showthread.php?t=636724)

You don't have to do this way - just easier for me to relay
(you could just use a command of
 /path/to/scriptname  /path/to/exact/packagename

```
mkdir -p ~/bin && gedit ~/bin/editdeb
```
copy & paste script into gedit from post 4, save, close gedit (make sure you get the whole script
```
chmod u+x ~/bin/editdeb
```

Do a restart to add ~/bin to your path

Now open a terminal & run 
editdeb /path/to/exactnameofdebianpackage

Easiest is to just type editdeb in terminal, hit spacebar. Locate the .deb in nautilus &  drag & drop the .deb on to terminal. Then click on terminal to return focus, hit enter to run.

gedit should open with the .deb's control file. 
On the Depends: line remove gnome-screensaver, see screen (leave a single space between Depends: gnome-settings-daemon.., screen 2.

If desired to prevent an upgrade back to repo version append a .1 to Version: 1:3.6.2-0ubuntu11 or whatever yours is, again see screen 2

Then save gedit & close, there should be a new .deb in your home folder, install with dpkg

Ex. of what I see in terminal here, start to finish - 
> $ editdeb  '/var/cache/apt/archives/gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb'

** (gedit:7501): WARNING **: Could not load Gedit repository: Typelib file for namespace 'GtkSource', version '3.0' not found
Building new deb...
dpkg-deb: warning: '/tmp/deb.xohTsJGax4/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `gnome-session-flashback' in `gnome-session-flashback_1%3a3.6.2-0ubuntu11.1_all.modfied.deb'.

Do note that editing a .deb is not always a good idea, in this case is ok, rebuilding source is usually preferred
(hopefully you'll have no issue doing this while using that ppa modded .deb's, let me know...

---

### Post by muktupavels on 2013-08-03
> **mc4man said:**
> Actually went ahead & built a patched gnome-panel in my saucy testing ppa but it'll not be suitable for you as you're using a gnome-panel .deb that was was attached to a bug report & in the case of ppa all panel packages must be updated
(if you know of the patch to fix white panels post a link ..

Attached zip archive with patch. :)

---

### Post by Cavsfan on 2013-08-03
**Mc4man**, I'm a little confused on where the deb is. It is not in /var/cache/apt/archives/ like one would think.

```
cavsfan@cavsfan-MS-7529:~$ apt-cache policy gnome-session-flashback
gnome-session-flashback:
  Installed: 1:3.6.2-0ubuntu11
  Candidate: 1:3.6.2-0ubuntu11
  Version table:
 *** 1:3.6.2-0ubuntu11 0
        500 http://us.archive.ubuntu.com/ubuntu/ saucy/universe amd64 Packages
        100 /var/lib/dpkg/status
```

That status file is just a long text file with some of the same stuff from your picture but it is not the deb.
I wonder why I do not have the .deb file? :confused:

Also here is the bug for the white panel problem and towards the bottom is **albertsmuktupavels**'s fix for it.

[https://bugs.launchpad.net/gnome-panel/+bug/1196177](https://bugs.launchpad.net/gnome-panel/+bug/1196177)

Which I might say works great if you install both deb packages at the same time. :D

---

### Post by mc4man on 2013-08-03
> **Cavsfan said:**
> **Mc4man**, I'm a little confused on where the deb is. It is not in /var/cache/apt/archives/ like one would think.


Did you browse to /var/cache/apt/archives/ & confirm it's not there ? (as I mentioned DnD is easier than typing name correctly..
If not there then just re-install & it will show up 
```
sudo apt-get install --reinstall gnome-session-flashback
```

---

### Post by Cavsfan on 2013-08-03
> **mc4man said:**
> Did you browse to /var/cache/apt/archives/ & confirm it's not there ? (as I mentioned DnD is easier than typing name correctly..
If not there then just re-install & it will show up 
```
sudo apt-get install --reinstall gnome-session-flashback
```

That worked and I was able to edit it too. But, I got this in terminal
```
cavsfan@cavsfan-MS-7529:/var/cache/apt/archives$ editdeb '/var/cache/apt/archives/gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb'

** (gedit:2918): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-TXTT1FsTwZ: Connection refused
Not modfied.
```
I had to "save as" gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb in my home directory.

Then trying to install the deb I got this:
```
cavsfan@cavsfan-MS-7529:~$ sudo dpkg -i gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb
dpkg-deb: error: `gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb' is not a debian format archive
dpkg: error processing gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb
cavsfan@cavsfan-MS-7529:~$
```

Thinking is is a permissions or ownership issue I chmod and chown them to be the same root:
```
cavsfan@cavsfan-MS-7529:~$ ls -l /var/cache/apt/archives/gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb /home/cavsfan/gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb
-rw-r--r-- 1 root root  1271 Aug  3 14:43 /home/cavsfan/gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb
-rw-r--r-- 1 root root 71026 Jun 21 00:35 /var/cache/apt/archives/gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb

```

Yet I still get the same error. :confused:

Thanks for you help and patience! :)

---

### Post by mc4man on 2013-08-03
You do Not want to be at a /var/apt/... prompt when running the script, just open a terminal at your normal user prompt.
Refer back to what I posted "Ex. of what I see in terminal here, start to finish - " & orig. instr.

> Now open a terminal & run
editdeb /path/to/exactnameofdebianpackage

Easiest is to just type editdeb in terminal, hit spacebar. Locate the .deb in nautilus & drag & drop the .deb on to terminal. Then click on terminal to return focus, hit enter to run.

gedit should open with the .deb's control file. 

If you look at what you posted in first code box it says "not modified" (you don't have permission to do so at that prompt.

Technically  you don't even need the script, I thought it would be easier, do you want to abandon it??

---

### Post by Cavsfan on 2013-08-03
I am not sure what to do. :???:

I deleted the .deb file from my home directory and tried it again from the home directory:
```
cavsfan@cavsfan-MS-7529:~$ editdeb '/var/cache/apt/archives/gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb'
Not modfied.

```
It still opens the file up in gedit but it changes the name to "control" and it is my tmp directory. That is why I said I had to "save as" to get it to my home directory.

I didn't do anything except reboot to put that script in my PATH. That seemed to be what you told me to do. Was that wrong? Should I have done something else to put it in my PATH?

---

### Post by mc4man on 2013-08-03
> **Cavsfan said:**
> I am not sure what to do. :???:


It still opens the file up in gedit but it changes the name to "control" and it is my tmp directory. That is why I said I had to "save as" to get it to my home directory.

It's not changing  the .deb to "control", **it's opening the control file in gedit so you can edit it**. (the whole point of this endeavor
So to repeat - 
when the control file opens in gedit,  **edit it **as i mentioned  & showed in the 2 screenshots.
After editing the control file in gedit,  **save **(just save, nothing else. 
Then close gedit & the new  "gnome-session-flashback_1%3a3.6.2-0ubuntu11.1_all.**modfied**.deb" will be created & saved to your home folder ready to be installed with dpkg.
Maybe go back & read my post & look at the screens...

---

### Post by mc4man on 2013-08-03
Maybe this will help
```
wget http://ubuntuone.com/6SkxW3cqYHWg6LQGRdWtc0
```

Play it in totem, vlc, whatever (fullscreen would be better

---

### Post by Cavsfan on 2013-08-03
> **mc4man said:**
> It's not changing  the .deb to "control", **it's opening the control file in gedit so you can edit it**. (the whole point of this endeavor
So to repeat - 
when the control file opens in gedit,  **edit it **as i mentioned  & showed in the 2 screenshots.
After editing the control file in gedit,  **save **(just save, nothing else. 
Then close gedit & the new  "gnome-session-flashback_1%3a3.6.2-0ubuntu11.1_all.**modfied**.deb" will be created & saved to your home folder ready to be installed with dpkg.
Maybe go back & read my post & look at the screens...

Sorry about this. I know I must appear pretty dense by now but it worked that time and I did the same as before. Plus I am almost positive that when I edited the file (removing gnome-screensaver), the save button grayed out and I could not save it as is.
That is why I say I had to click "save as" as I could not click on save but this time it did. 
```
cavsfan@cavsfan-MS-7529:~$ editdeb '/var/cache/apt/archives/gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.deb'
Building new deb...
dpkg-deb: warning: '/tmp/deb.xLgbxnNxRJ/DEBIAN/control' contains user-defined field 'Original-Maintainer'
dpkg-deb: warning: ignoring 1 warning about the control file(s)

dpkg-deb: building package `gnome-session-flashback' in `gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.modfied.deb'.
```

```
cavsfan@cavsfan-MS-7529:~$ sudo dpkg -i gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.modfied.deb
[sudo] password for cavsfan: 
(Reading database ... 209811 files and directories currently installed.)
Preparing to replace gnome-session-flashback 1:3.6.2-0ubuntu11 (using gnome-session-flashback_1%3a3.6.2-0ubuntu11_all.modfied.deb) ...
Unpacking replacement gnome-session-flashback ...
Setting up gnome-session-flashback (1:3.6.2-0ubuntu11.1) ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for mime-support ...
```

And I was finally able to remove the gnome screensaver:
```
cavsfan@cavsfan-MS-7529:~$ sudo apt-get purge gnome-screensaver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-screensaver*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 426 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 209810 files and directories currently installed.)
Removing gnome-screensaver ...
Purging configuration files for gnome-screensaver ...
Processing triggers for man-db ...
```

Problem solved! Whoot!
Plus I learned something and will never have to bother you or anyone else to remove a file dependency when it is unneeded in a development system.
I'm not going to go jacking with stuff on a production system because I have already borked an install or two and had to reinstall because of something I had done.
That's not fun and it felt like I had failed. :( So, I watch what I am doing pretty well. ;)

Any way thanks for your patience, help and tolerance!

Now I can add **xscreensaver -no-splash** to my startup applications. :guitar:

---

### Post by Cavsfan on 2013-08-03
Did you get your white panels fixed?

---

### Post by mc4man on 2013-08-03
> **Cavsfan said:**
> Did you get your white panels fixed?
I did. 
(put up a gnome-panel patched build in a ppa, was going to mention but thought better to see this thru.
The reason why your first attempt, ( where you may have actually edited the control file), failed is the script creates the new .deb in the directory it is run from. So in that case, /var/apt/... it didn't have permission to write there...

Overall flashback works ok though the indicators seem to swap positions on some logins & a few other oddites.

---

### Post by Cavsfan on 2013-08-04
> **mc4man said:**
> I did. 
(put up a gnome-panel patched build in a ppa, was going to mention but thought better to see this thru.
The reason why your first attempt, ( where you may have actually edited the control file), failed is the script creates the new .deb in the directory it is run from. So in that case, /var/apt/... it didn't have permission to write there...

Overall flashback works ok though the indicators seem to swap positions on some logins & a few other oddites.

Good. I did not reboot until a little while ago and when I tried to login to flashback, all I got was a black screen and that was it. 
I logged into Unity just fine then logged out and selected flashback and still nothing.
So, I logged into console (ALT+ CNTL + F1) and removed then re-installed gnome-session-flashback and then could login to 
flashback but gnome-screensaver is again installed and again a dependency.

I will try this again when I have time. I have no doubt you have the fix. I think it was probably something I did. So, I'll try it again later. :)

---

### Post by mc4man on 2013-08-04
I was going to mention the black screen at login but I don't believe it's from a modified or patched gnome-panel per se. There seems to be something else going on as I've seen it even with the default repo gnome-panel packages.

Also to note usually it's not that the login won't happen, it's just going to take 25 -30 sec's. 
If inclined test & see, just wait it out.
I've also seen it when going from a gnome-panel (with compiz) session back to a unity session, same deal, about 25+ seconds.

I believe that this bit is relevant, seen in either .xsession-errors or .cache/upstart/gnome-session.log depending on whether extended login time occured with gnome-panel or unity sessions respectively. (the warnings & error are exact same for both when getting extended login time.
```
stdout: 
stderr: 
** (process:5635): WARNING **: (../../gi/pygi-marshal-from-py.c:641):_pygi_marshal_from_py_basic_type: runtime check failed: (transfer == GI_TRANSFER_NOTHING)
TypeError: Pointer assignment is restricted to integer values. See: [https://bugzilla.gnome.org/show_bug.cgi?id=683599](https://bugzilla.gnome.org/show_bug.cgi?id=683599)

** (process:5635): WARNING **: (../../gi/pygi-marshal-from-py.c:641):_pygi_marshal_from_py_basic_type: runtime check failed: (transfer == GI_TRANSFER_NOTHING)
TypeError: Pointer assignment is restricted to integer values. See: [https://bugzilla.gnome.org/show_bug.cgi?id=683599](https://bugzilla.gnome.org/show_bug.cgi?id=683599)

** (process:5635): WARNING **: (../../gi/pygi-marshal-from-py.c:641):_pygi_marshal_from_py_basic_type: runtime check failed: (transfer == GI_TRANSFER_NOTHING)
TypeError: Pointer assignment is restricted to integer values. See: [https://bugzilla.gnome.org/show_bug.cgi?id=683599](https://bugzilla.gnome.org/show_bug.cgi?id=683599)

(process:5635): GLib-GIO-ERROR **: The mapping function given to g_settings_get_mapped() for key 'favorites' in schema 'com.canonical.Unity.Launcher' returned FALSE when given a NULL value.
```



Possible solution on install where this occurs - 
delete ~/.dbus

also note that this seems more likely to occur on an older install then a new one...
(personally I think 13.10 is currently a bit of a mess..

---

### Post by Cavsfan on 2013-08-04
> **mc4man said:**
> I was going to mention the black screen at login but I don't believe it's from a modified or patched gnome-panel per se. There seems to be something else going on as I've seen it even with the default repo gnome-panel packages.

Also to note usually it's not that the login won't happen, it's just going to take 25 -30 sec's. 
If inclined test & see, just wait it out.
I've also seen it when going from a gnome-panel (with compiz) session back to a unity session, same deal, about 25+ seconds.

I believe that this bit is relevant, seen in either .xsession-errors or .cache/upstart/gnome-session.log depending on whether extended login time occured with gnome-panel or unity sessions respectively. (the warnings & error are exact same for both when getting extended login time.
```
stdout: 
stderr: 
** (process:5635): WARNING **: (../../gi/pygi-marshal-from-py.c:641):_pygi_marshal_from_py_basic_type: runtime check failed: (transfer == GI_TRANSFER_NOTHING)
TypeError: Pointer assignment is restricted to integer values. See: [https://bugzilla.gnome.org/show_bug.cgi?id=683599](https://bugzilla.gnome.org/show_bug.cgi?id=683599)

** (process:5635): WARNING **: (../../gi/pygi-marshal-from-py.c:641):_pygi_marshal_from_py_basic_type: runtime check failed: (transfer == GI_TRANSFER_NOTHING)
TypeError: Pointer assignment is restricted to integer values. See: [https://bugzilla.gnome.org/show_bug.cgi?id=683599](https://bugzilla.gnome.org/show_bug.cgi?id=683599)

** (process:5635): WARNING **: (../../gi/pygi-marshal-from-py.c:641):_pygi_marshal_from_py_basic_type: runtime check failed: (transfer == GI_TRANSFER_NOTHING)
TypeError: Pointer assignment is restricted to integer values. See: [https://bugzilla.gnome.org/show_bug.cgi?id=683599](https://bugzilla.gnome.org/show_bug.cgi?id=683599)

(process:5635): GLib-GIO-ERROR **: The mapping function given to g_settings_get_mapped() for key 'favorites' in schema 'com.canonical.Unity.Launcher' returned FALSE when given a NULL value.
```



Possible solution on install where this occurs - 
delete ~/.dbus

also note that this seems more likely to occur on an older install then a new one...
(personally I think 13.10 is currently a bit of a mess..

I tried it once and gave it about a minute maybe then brought up console logged in and **sudo reboot**. 
The 2nd time I did it I just walked away for about 20-30 minutes and came back and it was still at the black screen.
I'll try it again and see what happens. At least I know how to get it back like it was. Saucy has been acting pretty good for me. 
I never have any 25 second delay on logging in but I only login to gnome flashback unless I cannot get there.
My install was from a daily iso in July:
```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Jul 8 14:34
```

But, I think you are right it is a bit of a mess right now.

Here goes nothing :) *sigh*

---

### Post by Cavsfan on 2013-08-04
Seems to have worked well that time. It was pretty fast logging in too - just a few seconds. 
Thanks. :)

---

### Post by Cavsfan on 2013-08-04
> **mc4man said:**
> Maybe this will help
```
wget http://ubuntuone.com/6SkxW3cqYHWg6LQGRdWtc0
```

Play it in totem, vlc, whatever (fullscreen would be better

That was pretty sweet too! I just now did that and watched it with vlc. Very well done! 
Thanks.

---

### Post by Cavsfan on 2013-08-05
It's still working pretty well! :D

---

### Post by Cavsfan on 2013-08-13
Guess I'll have to do this all over again. Today's updates installed an updated **gnome-session-fallback** and **gnome-screensaver**. :rolleyes:

---

### Post by Cavsfan on 2013-08-13
Got it accomplished but got the same [COLOR=#000000][FONT=Ubuntu Mono]Not modfied.[/FONT][/COLOR] error when trying to edit it from my home directory.
Also got an error when I tried to save the control file so I tried to dpkg the other deb that was still in my home directory but got a blank screen after logout.

So, I rebooted into Unity and did it there and did not get any errors. Then logged out and back into Flashback and all is back to normal.

---

### Post by Cavsfan on 2013-08-14
Broke again this morning. Looked at a blank screen. :neutral: Re-installed gnome-session-flashback and gnome-screensaver came with it.
I'll just live with it.

---

### Post by Cavsfan on 2013-09-24
Thanks again **mc4man** for the instructions on how to take the dependancy out of gnome-session-flashback for gnome-screensaver.
I rebooted and it seems to be working well. Have to see how it goes but, I could not take another day of looking at that black screen when the screensaver kicked in. :)

I hope they fix this before final release. I am suprised I am the only one using flashback that wants a working screensaver.

---

### Post by muktupavels on 2013-09-25
You can remove gnome-screensaver package without removing gnome-session-flashback with this command:
```
sudo dpkg --ignore-depends=gnome-session-flashback -r gnome-screensaver
```

Edit: Sorry, apt-get won't like this. So this is not solution...

---

### Post by Cavsfan on 2013-09-25
> **albertsmuktupavels said:**
> You can remove gnome-screensaver package without removing gnome-session-flashback with this command:
```
sudo dpkg --ignore-depends=gnome-session-flashback -r gnome-screensaver
```

Edit: Sorry, apt-get won't like this. So this is not solution...


Right, this post is the solution post #20 in this thread [http://ubuntuforums.org/showthread.php?t=2160563&page=2&p=12744777#post12744777](http://ubuntuforums.org/showthread.php?t=2160563&page=2&p=12744777#post12744777) by **mc4man** and it's still holding up. 
I presume it will until another update to gnome-session-flashback gets installed. Then one would just have to repeat that step, reboot and viola.

---

### Post by mc4man on 2013-09-25
A while back I just went ahead & rebuilt the source removing the dep on gnome-screensaver as that seemed easiest & as a means to see if there where any ill-effects. 
Didn't see any but since haven't used gnome-flashback at all so removed the build from a saucy proposed ppa.

It's unlikely that the dep would be officially removed but I guess it could be handled in a ppa if there was more than extremely limited interest
(and a bit wider testing to confirm it causes no issues

---

### Post by Cavsfan on 2013-09-26
> **mc4man said:**
> A while back I just went ahead & rebuilt the source removing the dep on gnome-screensaver as that seemed easiest & as a means to see if there where any ill-effects. 
Didn't see any but since haven't used gnome-flashback at all so removed the build from a saucy proposed ppa.

It's unlikely that the dep would be officially removed but I guess it could be handled in a ppa if there was more than extremely limited interest
(and a bit wider testing to confirm it causes no issues).

It's working great so far for the past couple of days and I don't see any problems arising as it was such a minor change.
I would hope that this is fixed before release as Jeremy Bicha stated in post #3 [http://ubuntuforums.org/showthread.php?t=2160563&p=12722548#post12722548](http://ubuntuforums.org/showthread.php?t=2160563&p=12722548#post12722548)

I do not like the wasted space that the Unity bar takes up on my screen and I have a huge screen.
I am also surprised at the lack of interest in resolving this major issue caused by this subtle dependency on gnome-screensaver.

Gnome-screensaver no longer seems to perform any actual screensaver functionality; just a locked screen requiring a password to unlock.
But, in Flashback it makes xscreensaver unusable without being able to remove gnome-screensaver as we could in several of the previous installations.
If I am forced to use Unity I will use another installation/DE that doesn't force Unity. I like Unity about like my son likes Windows 8; which isn't much.

---

