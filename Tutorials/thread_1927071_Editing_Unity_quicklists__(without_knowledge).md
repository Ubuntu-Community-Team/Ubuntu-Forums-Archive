---
title: "Editing Unity quicklists  (without knowledge)"
date: 2012-02-17
forum: Tutorials
---

### Post by Jacobonbuntu on 2012-02-17
[LEFT]The subject is not new, but so far, most instructions are based on manually editing the .desktop files. For my own convenience, and because I like learning Python a bit, I wrote a set of scripts to make it easy, also for new users.
[/LEFT]
 
Setup is straightforward: 

[LIST]
[*]Download the 'launcher_editor.zip' [**here**]("http://bazaar.launchpad.net/%7Evlijm/jonb.homelauncher/launchermaker/view/head:/quicklist_editor.zip")
[*]Unzip it somewhere in your Home directory
[*]Open a terminal, cd to the directory in which te 'setup.py' file is, run it by the command 'python setup.py'
[/LIST]
Basically that's all. After you log out and back in a new menu item will be placed at the bottom of your Home launcher's icon:


[CENTER][IMG]http://dl.dropbox.com/u/1155139/quicklist.png[/IMG]



[/CENTER]
[LEFT]Usage is pretty much speaking for itself:


[CENTER][IMG]http://dl.dropbox.com/u/1155139/window.png[/IMG]
[/CENTER]
 
[/LEFT]
[CENTER][IMG]http://dl.dropbox.com/u/1155139/addition.png[/IMG]

[IMG]http://dl.dropbox.com/u/1155139/Vbox.png[/IMG]

[/CENTER]
[LEFT]At this point the script covers three applications: nautilus-home, Firefox (weblinks) and VirtualBox. I am working on more (LibreOffice etc).
You can move the folder after installation, but you will have to run the setup.py again to repair the linking to- and between the scripts.
I tried the scripts on 11.10 and 12.04, (Dutch and US English), fresh installed as well as with pre- edited .desktop files, the script takes care of correct file setup and clean handling of the files, I did not run into problems, or they are corrected in this version.

To remove the scripts, first choose 'nautilus-home' from the script's menu (see above) and after that "restore". Once the original quicklist is restored, simply remove the launcher-editor folder from your system.

----------------
edit 19-2-12
----------------
just added support for LibreOffice quicklists, including a versionchecker (including LibreOffice 3.5). made some adaptions to the editor_module.py to  meet the somewhat inconsistent and changing (per version) naming of the  .desktop files of LibreOffice.

----------------
edit 20-2-12
----------------
just added support for Banshee (player controls) quicklists
 [/LEFT]

---

### Post by Jacobonbuntu on 2012-04-14
[LEFT]Hi people, the information on the script is now outdated, just finished a GUI version:

can be downloaded here: (download the QLE.zip)
[link]("http://bazaar.launchpad.net/%7Evlijm/jonb.homelauncher/launchermaker/files")

   [/LEFT]

---

### Post by Jacobonbuntu on 2012-06-14
Hi people,

just to give you an update on the Quicklist Editor I have been working on in the passed few months:
QLE Unity Quicklist Editor
 This is the second "pre-" version of the quicklist editor, coded from  zero in python 3. It has a more logical interface, better functionality  and a number of build-in precautions to prevent errors. (almost) All  editing procedures were totally changed, both at the front-end and  behind the screens.
 Editing options now include:
- adding commands
- adding dividers
- adding LibreOffice applications (from a list, to any quicklist)
- adding shortcuts to applications (creating grouped quicklists from an application list that is presented)
- adding directories
- adding virtual boxes (from a list that is presented)
- adding url's
- renaming existing entries
- changing the command of an existing entry
- moving entries up or down in the quicklist
- importing entries from textfiles or other quicklists* (experimental)
- removing entries
- resetting the quicklist to as it was before QLE editor was installed
 Additionally, the editor recognizes and corrects some possible  properties of quicklists that might cause problems (like no ";" at the  end of the entry line). The editor recognizes and edits both "old"  (<12.04) and "new" style desktop files.
"standalone" desktop files (made by the user, not representing an  application) are recognized and listed, and can be edited like any  quicklist.

This might not be the right place to present it, but as a follow up of the tutorial I placed here some time ago (and that made me work on the editor actually) I thought it would be an appropriate thing to do...

[CENTER][IMG]https://dl.dropbox.com/u/1155139/editor_window.png[/IMG]

[LEFT]The download link is in my signature.
(*the editor requires python3 / python3-tk)
[/LEFT]
[/CENTER]

---

### Post by hansdown on 2012-06-14
That looks pretty nice,Jacobonbuntu.

Good work.

---

### Post by Jacobonbuntu on 2012-06-14
> **hansdown said:**
> That looks pretty nice,Jacobonbuntu.

Good work.

Thanks!

---

### Post by Jacobonbuntu on 2012-09-10
Hi people,

Just to mention that the Unity Quicklist Editor got version 1.0, available in ppa as well:

sudo add-apt-repository ppa:vlijm/qle
sudo apt-get update
sudo apt-get install qle

all the best!
Jacob

---

### Post by jlh68 on 2012-10-08
I have installed QLE and it will not launch.

---

### Post by Jacobonbuntu on 2012-10-09
> **jlh68 said:**
> I have installed QLE and it will not launch.

Hi [jlh68]("http://ubuntuforums.org/member.php?u=273814"), I did not run into that before, but the only thing I can think of is that one or more files in ~/.qle is corrupted. could you remove the folder (hidden by default; press ctrl-h to mak it visible) and try again?
also: are you running 32 or 64 bit? did you install the ppa or the .deb installer?

edit:
could you run in a terminal:
python3 /usr/bin/qle_interface.py
 and give me the output?

---

### Post by Jacobonbuntu on 2012-10-09
Hi John,

thanks for the output on [launchpad]("https://bugs.launchpad.net/jonb.homelauncher/+bug/1063898"), and thanks for your bug report!!
the output was very helpful, and this is what causes the trouble: 
normally the local .desktop files are stored in '/home/john/.local/share/applications/'. these files overrule the ones in /usr/share/applications. if the directory  '/home/john/.local/share/applications/ does not exist, the editor creates it before the interface is loaded. in your case, a file named 'applications' already exists where a folder should be created with that name, causing the error message and preventing the interface to load.

what you should do is rename or move the file (if it is of any importance) or remove it (if it was created by accident for some reason). 
after that, when you start the quicklkist editor, everything should work well.

please let me know!

---

### Post by Jacobonbuntu on 2012-10-14
> **jlh68 said:**
> I have installed QLE and it will not launch.


Hi John, I found this post about an (assumed) error in the code of the editor:
[http://www.ubuntugeek.com/qle-unity-quicklist-editor.html/comment-page-1#comment-127279](http://www.ubuntugeek.com/qle-unity-quicklist-editor.html/comment-page-1#comment-127279)
what I don't get is why you do not reply to my latest answer, but you do post this one, which is obviously not correct.

---

### Post by jlh68 on 2012-10-15
I followed your suggestion about the ./applications folder.  I got GLE to load, but I could not figure out how to make the quick lists.  I then tried Ubuntu Tweak which also had not been working.  U-Tweaks was more intuitive in making the quick lists.  I still did not get the quick list to show up, until I restarted my computer then it was there.  Maybe that was all I had to do with QLE to make it work.

I guess some "how to use" Quick List Editor instructions would be helpful to some of us, especially me.

I do thank you for looking into my problem and your solution has helped me with several other applications that were not working and now do work.

---

### Post by Jacobonbuntu on 2012-10-15
> **jlh68 said:**
> 
I guess some "how to use" Quick List Editor instructions would be helpful to some of us, especially me.

Hi John, no problem!
you can find the helpfile under the menu:
Info > Help
...But of course you should use what is the most convenient for you.

---

