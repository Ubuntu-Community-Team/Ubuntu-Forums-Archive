---
title: "ubuntu 6 and lotus notes"
date: 2006-07-22
forum: The Cafe
---

### Post by LINUXBEN on 2006-07-22
Hi all,

I hope this is the right place to post my question. 
I have just installed ubuntu 6 on my work PC and was wondering if lotus notes would work on this version. I've tried googling and found an installation guide but it was created for ubuntu 5. Any help would be greatly appreciated.

---

### Post by sethmahoney on 2006-07-22
I wouldn't be surprised if the installation guide for an earlier version works for something like that.

---

### Post by LINUXBEN on 2006-07-22
This is my first time to try Ubuntu/linux so please bear with me. 

I've tried, but I was lost when the guide says something like

"Hoary Hedgehog (binary)", with the subtitle "Community maintained (Universe)"

I just could not find those words.

---

### Post by sethmahoney on 2006-07-22
Could you post a link to the guide?

---

### Post by LINUXBEN on 2006-07-22
> **sethmahoney said:**
> Could you post a link to the guide?

Here's the link:
[http://www.nsftools.com/tips/UseNotesWithWine.htm](http://www.nsftools.com/tips/UseNotesWithWine.htm)

---

### Post by LINUXBEN on 2006-07-22
> **LINUXBEN said:**
> Here's the link:
[http://www.nsftools.com/tips/UseNotesWithWine.htm](http://www.nsftools.com/tips/UseNotesWithWine.htm)

I got stucked on  step no. 3.
By the way, I am following the long instruction.

---

### Post by sethmahoney on 2006-07-22
Instead of step 3, open a terminal and type

sudo gedit /etc/apt/sources.list

Look for the line that says

## Uncomment the following two lines to add software from the 'universe'
## repository.

Below that will be two lines that look like

##deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted 
##deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

Remove the ## before each of those lines and type

multiverse

at the end of both lines.  Save, exit gedit, and then at the terminal type

sudo apt-get update

When it is done, close the terminal window, and go on to the next step in your guide.

---

### Post by LINUXBEN on 2006-07-22
Thanks a lot sethmahoney. I'm gonna try it when I get back to work. Again, thanks for your time and help.

---

### Post by LINUXBEN on 2006-07-23
here's what I got executing the command you mentioned:
not certain which ones to change


deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

---

### Post by sethmahoney on 2006-07-23
> **LINUXBEN said:**
> 
deb [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper universe multiverse
# deb-src [http://ph.archive.ubuntu.com/ubuntu/](http://ph.archive.ubuntu.com/ubuntu/) dapper universe


Both these lines should be uncommented (which means that neither should start with #), and both should have

multiverse

at the end.

---

### Post by LINUXBEN on 2006-07-24
can you tell me why I'm getting this error?

ruben@linux-ben:~$ sudo gedit /etc/apt/sources.list
Password:

(gedit:5086): Gdk-WARNING **: locale not supported by Xlib

(gedit:5086): Gdk-WARNING **: cannot set locale modifiers
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default



ruben@linux-ben:~$ sudo apt-get install winesetuptk
Reading package lists... Done
Building dependency tree... Done
Package winesetuptk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  wine
E: Package winesetuptk has no installation candidate
ruben@linux-ben:~$

---

### Post by 3rdalbum on 2006-07-24
The Gdk-WARNING stuff doesn't mean diddly-squat, so ignore it.

If you can still get sound in and out of your computer, then ignore the ALSA one too. Exactly when is the ALSA message coming up?

The last message says that winesetuptk is not in the repositories. I got the same message. You don't need winesetuptk; if you really want a GUI frontend to WINE's configuration, try looking up Wine Doors (it's not in repositories).

---

### Post by LINUXBEN on 2006-07-24
> **3rdalbum said:**
> The Gdk-WARNING stuff doesn't mean diddly-squat, so ignore it.

If you can still get sound in and out of your computer, then ignore the ALSA one too. Exactly when is the ALSA message coming up?

The last message says that winesetuptk is not in the repositories. I got the same message. You don't need winesetuptk; if you really want a GUI frontend to WINE's configuration, try looking up Wine Doors (it's not in repositories).


I need winesetuptk as what the guide says in the installation of lotus notes. I am so sorry I am a newbie when it comes to ubuntu. 

So ALSA is audio related error? I don't need sound right now, I should just ignore it.

---

### Post by sethmahoney on 2006-07-24
> **LINUXBEN said:**
> I need winesetuptk as what the guide says in the installation of lotus notes. I am so sorry I am a newbie when it comes to ubuntu. 

So ALSA is audio related error? I don't need sound right now, I should just ignore it.

You can skip installing winesetuptk - all it does is give you a graphical way to configure wine.  It doesn't actually add any functionality.  Just make sure you install wine.  If you run into any problems setting up without winesetuptk, just leave us a message here and we'll get you through it.

---

### Post by LINUXBEN on 2006-07-25
Okay I skipped step 3 and 4.

On step 5, do I need to skip this too. I've tried the command and got an error command not found.



5. Open a terminal window (Application - System Tools - Terminal on Ubuntu 5.04), type winesetup, and follow the prompts and accept the defaults.

Make sure you do not do this as root (using either the "sudo" command, the "su" command, or the root terminal). If you just open a normal terminal window and run "winesetup", you'll be fine.

6. Copy the Notes folder and all subfolders from a working copy of the Lotus Notes [6.5.1 or later] client on Windows to the equivalent directory in your wine installation (for example, if it was "c:\lotus\notes" under Windows, it should be copied to "~/.wine/c/lotus/notes" on Linux).

Make sure that your notes.ini file is in your Notes program directory (the same directory that nlnotes.exe is in). If it's not, you should find it (probably in the Windows directory) and copy it there. Also, while you're looking at the notes.ini file, make sure that any AddinMenus= or EXTMGR_ADDINS= settings are commented out. They may not hurt anything if they're there, but you should definitely test without them first.

The easiest way to copy the files is probably to burn the files to a CD (since everyone seems to have a CD burner these days). If this is the method you choose, make sure you remove the "read-only" flag from the files after you copy them to Linux (because it will be set by default when copying from a CD). To do this:

    * Open a terminal window (Application - System Tools - Terminal on Ubuntu 5.04)
    * Navigate to the Notes directory you just copied over (for example, "cd ~/.wine/c/Program Files/lotus/notes")
    * type the command: chmod u+w,g+w -R *

7. Copy mfc42.dll and msvcp60.dll from your "c:\windows\system32" directory in Windows to "~/.wine/c/windows/system" on Linux. Use a rewritable CD, a USB memory stick, a floppy disk, or whatever.

8. Open the ~/.wine/config file in a text editor (Applications - Accessories - Text Editor), and add the following sections to the end (just before the "# [/wineconf]" line):

---

### Post by frodon on 2006-07-25
There's a guide here : [http://ubuntuforums.org/showthread.php?t=222492](http://ubuntuforums.org/showthread.php?t=222492)

Don't know if it works but it may help.

---

### Post by LINUXBEN on 2006-07-25
6. Copy the Notes folder and all subfolders from a working copy of the Lotus Notes [6.5.1 or later] client on Windows to the equivalent directory in your wine installation (for example, if it was "c:\lotus\notes" under Windows, it should be copied to "~/.wine/c/lotus/notes" on Linux).

i could not find wine directory. Does searching works the same way as MSwindows?

---

### Post by graabein on 2006-07-25
There are several ways to search but I suggest you open a terminal and just type **cd ~/.wine/** and then **ls** from there.

---

### Post by LINUXBEN on 2006-07-25
ruben@linux-ben:~$ cd ~/.wine/
bash: cd: /home/ruben/.wine/: No such file or directory


Any ideas?

---

### Post by JoWilly on 2006-07-25
> **LINUXBEN said:**
>  and was wondering if lotus notes would work on this version. 

According to IBM, the native linux version of Lotus Notes 7.0.1 was supposed to be released yesterday, July 24th.

Version 7 is free for people who have a previous version's serial.

---

### Post by kripkenstein on 2006-07-25
LINUXBEN, the .wine directory is created the first time wine is run, AFAIK. Perhaps something in the skipped steps would have done this for you, I am not sure. In any case, you can try to run wine (just do "wine" in the command line), and it will create ~/.wine.

I believe this will work - however, it does go outside the listed steps there... so perhaps it won't. If not, worst come to worst you may need to start from the beginning (after uninstalling the installed packages). 

But, as I said before, I think it'll be ok.

Btw, I agree with JoWilly about the native Notes - it's free, should be out by now... perhaps you can consider that (there are advantages to running a native version, and not under wine).

---

### Post by LINUXBEN on 2006-07-25
thanks for the replies. yeah, I've visited IBM's website hoping for a downloadlink but I couldn't find one. 


I'm gonna try checking wine once again when I get back to work tomorrow.

---

### Post by LINUXBEN on 2006-07-26
> **kripkenstein said:**
> LINUXBEN, the .wine directory is created the first time wine is run, AFAIK. Perhaps something in the skipped steps would have done this for you, I am not sure. In any case, you can try to run wine (just do "wine" in the command line), and it will create ~/.wine.

I believe this will work - however, it does go outside the listed steps there... so perhaps it won't. If not, worst come to worst you may need to start from the beginning (after uninstalling the installed packages). 

But, as I said before, I think it'll be ok.

Btw, I agree with JoWilly about the native Notes - it's free, should be out by now... perhaps you can consider that (there are advantages to running a native version, and not under wine).

I thought wine directory was created when wine was first installed:-D .   Just did wine command, and yeah it was created. Thanks alot.

---

### Post by LINUXBEN on 2006-07-26
Now, How do I copy files to wine directory?  I could see wine directory in the terminal but I could not locate wine directory in Windows? I'm thinking of dragging and dropping lotus to wine.

---

### Post by LINUXBEN on 2006-07-26
anyone? please.

---

### Post by kripkenstein on 2006-07-26
I'm not sure where you want to drag&drop it **from** (no idea what your current setup is). But, in general, the convenient way to access your wine 'virtual windows drive' is to use winefile (just do 'winefile' from the terminal). Inside winefile, press "c:\" on the toolbar, to see the virtual windows drive. Then copy whatever stuff you want.

---

### Post by LINUXBEN on 2006-07-26
I  figured out that the wine folder was hidden. I could browse the folders now and succesfully copied the lotus folder. 

 I am on step 8 and I am once again stuck on searching :-k config:(  file in wine. 

8. Open the ~/.wine/config file in a text editor (Applications - Accessories - Text Editor), and add the following sections to the end (just before the "# [/wineconf]" line):

---

### Post by kripkenstein on 2006-07-26
If I recall correctly, old versions of wine used the 'config' file, newer versions use registry files (.reg) inside .wine. Are you using the same version of wine they said to use in the howto?

Regardless, you can just try to run Notes now, it might work. If not, tell us and we'll figure out what .reg file you need to edit.

Offhand, I can tell you that the first line (windows = 98 ) that the howto says to add, can be done by running winecfg, and selecting "windows 98" there, so no need to edit anything in this case. But again, perhaps just try to run it, and see.

---

### Post by LINUXBEN on 2006-07-26
I guess I am using the latest version of wine. I am off at work now, and hopefully tomorrow could check that out.

Thanks a bunch for your help.

---

