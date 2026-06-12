---
title: "[SOLVED] Major Problem Installing SeaMonkey!"
date: 2007-10-22
forum: Ubuntuzilla
---

### Post by MSchenker on 2007-10-22
I was really enjoying Ubuntu until today, when I tried to install SeaMonkey!!!

I opened a "Konsole" window (a scary experience for someone like me) and followed the directions in the "Automated Install" help posted in this forum ([https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)).  

Everything was going all right, until I hit the "Install" stage.   Then I received the following errors, and I have no idea how to solve this.

Here are the errors that appeared in the Konsole:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Can someone please help me figure this out?

Thanks,
Matthew

---

### Post by nanotube on 2007-10-22
> **MSchenker said:**
> I was really enjoying Ubuntu until today, when I tried to install SeaMonkey!!!

I opened a "Konsole" window (a scary experience for someone like me) and followed the directions in the "Automated Install" help posted in this forum ([https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)).  

Everything was going all right, until I hit the "Install" stage.   Then I received the following errors, and I have no idea how to solve this.

Here are the errors that appeared in the Konsole:

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Can someone please help me figure this out?

Thanks,
Matthew

did the install actually complete, though?
those errors are generally harmless afaik - i see them when running some kde-apps on my gnome box, with no ill effects.

---

### Post by MSchenker on 2007-10-23
nanotube,
No, the install did not work.  SeaMonkey does not show up in any of the menus.

But how could it work when I was never able to get to the "integrate" phase of the installation?

I must say, I am very interested in running Ubuntu.  But if this is what it takes to install programs, I am having second thoughts!

Thanks,
Matt

---

### Post by nanotube on 2007-10-24
what happens if you run "seamonkey" from commandline?

could you please tell me when exactly this error occurred? just run the whole install again, and post the entire output here.

if you're running the latest release of ubuntu (7.10), then a "rebranded" version of seamonkey called "iceape" is available in the repositores, that you could also try.

---

### Post by MSchenker on 2007-10-24
> **nanotube said:**
> what happens if you run "seamonkey" from commandline?

Nothing happens if I do this -- I get no messages, but nothing runs either.

> **nanotube said:**
>  could you please tell me when exactly this error occurred? just run the whole install again, and post the entire output here.

I'll do this a little later today.  But the output on all steps before "install" work fine.

> **nanotube said:**
> if you're running the latest release of ubuntu (7.10), then a "rebranded" version of seamonkey called "iceape" is available in the repositores, that you could also try.

Thank you for explaining this!  In another Ubuntu discussion, someone mentioned Iceapce, and I asked where to find it, but could not get an answer.  This explains it!

Matt

---

### Post by nanotube on 2007-10-24
hm, ok, i'm waiting for your post of complete output. :)

---

### Post by MSchenker on 2007-10-24
nanotube,
Here is what happened in the terminal while I was trying to install SeaMonkey:

Just a note: as expected, I saw "The file is already fully retrieved; nothing to do."  That makes sense, since that first step was done before.  I repeated it here anyway just to have a complete set of steps.

```
matthew@ubuntu:~$ tar zxvf seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz
./seamonkey-installer/
./seamonkey-installer/xpi/
./seamonkey-installer/xpi/spellcheck.xpi
./seamonkey-installer/xpi/regus.xpi
./seamonkey-installer/xpi/deflenus.xpi
./seamonkey-installer/xpi/inspector.xpi
./seamonkey-installer/xpi/chatzilla.xpi
./seamonkey-installer/xpi/langenus.xpi
./seamonkey-installer/xpi/mail.xpi
./seamonkey-installer/xpi/talkback.xpi
./seamonkey-installer/xpi/xpcom.xpi
./seamonkey-installer/xpi/venkman.xpi
./seamonkey-installer/xpi/reporter.xpi
./seamonkey-installer/xpi/psm.xpi
./seamonkey-installer/xpi/browser.xpi
./seamonkey-installer/README
./seamonkey-installer/config.ini
./seamonkey-installer/seamonkey-installer-bin
./seamonkey-installer/installer.ini
./seamonkey-installer/seamonkey-installer
./seamonkey-installer/MPL-1.1.txt

--16:11:00--  [http://ftp.mozilla.org/pub/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz](http://ftp.mozilla.org/pub/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz)
           => `seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz) [following]
--16:11:00--  [http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz)
           => `seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz'
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz](http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz) [following]
--16:11:01--  [http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz](http://releases.mozilla.org/pub/mozilla.org/seamonkey/releases/1.1.1/seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz)
           => `seamonkey-1.1.1.en-US.linux-i686.installer.tar.gz'
Resolving releases.mozilla.org... 207.200.66.54, 204.152.184.113, 156.56.247.196, ...
Connecting to releases.mozilla.org|207.200.66.54|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

matthew@ubuntu:~$ cd seamonkey-installer
matthew@ubuntu:~/seamonkey-installer$ gksudo ./seamonkey-installer
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
matthew@ubuntu:~/seamonkey-installer$
```

Note that I was following the directions on the Ubuntu site for installing SeaMonkey ([https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)).

Thanks,
Matt

---

### Post by nanotube on 2007-10-24
hi,

oh, well, you are not using ubuntuzilla at all! you are using the seamonkey installer (which this project has nothing at all to do with, and i know next to nothing about), following the "manual install" instructions from that SeaMonkey page.

if you want to use ubuntuzilla, then you should actually download the ubuntuzilla script and use that to install. hopefully that would meet with better success. (just click on the "ubuntuzilla" link in that page, and then follow the ubuntuzilla usage instructions from there).

let me know how it goes, and if you have any questions. :)

---

### Post by MSchenker on 2007-10-24
I'm confused...I'll check Ubuntuzilla out now.
Thanks,
Matt

---

### Post by jviscosi on 2007-10-25
I don't think you have to use gksudo when you're installing Seamonkey via the installer ... I always used to just use plain old **sudo ./seamonkey-installer **and the graphical installer would run fine.  Have you tried that?  (I posted more extensive notes in [this thread]("http://ubuntuforums.org/showthread.php?t=583067").)

I recently switched to IceApe from the repositories and it works just the same as Seamonkey.  I hate the name (and the icon, for that matter), but it's more convenient than manually installing every time an update for Seamonkey comes out.  But I certainly wouldn't recommend upgrading to Gutsy just to get IceApe.

---

### Post by MSchenker on 2007-10-26
jviscosi,
I tried Sudo, and got more errors.
My hope is to install Wubi Ubuntu 7.10 so I can get IceApe, which sounds like an easier installation.
Thanks,
Matt

---

### Post by nanotube on 2007-10-26
> **MSchenker said:**
> jviscosi,
I tried Sudo, and got more errors.
My hope is to install Wubi Ubuntu 7.10 so I can get IceApe, which sounds like an easier installation.
Thanks,
Matt

so, have you tried using ubuntuzilla?

---

### Post by MSchenker on 2007-10-26
> **nanotube said:**
> so, have you tried using ubuntuzilla?

I was told that Ubuntuzilla is for servers.  I'm trying to install SeaMonkey on my desktop.

Matt

---

### Post by nanotube on 2007-10-26
> **MSchenker said:**
> I was told that Ubuntuzilla is for servers.  I'm trying to install SeaMonkey on my desktop.

Matt

well, who told you that? to be blunt, they didn't know what they were talking about. :) ubuntuzilla is primarily for the desktop - because that's where you would /want/ to install browsers and email clients. (though of course it would work on a "server", too - installing software on a "server" and on a "desktop" is exactly the same.)

anyway, i'm not trying to make you use ubuntuzilla - do whatever you prefer. upgrading to gutsy and installing iceape from the repos is a valid alternative - if you were planning on upgrading to gutsy anyway. but you posted to the ubuntuzilla forum, asking about using ubuntuzilla, hence, the info about ubuntuzilla. :)

---

### Post by jviscosi on 2007-10-26
You could also try running the installer as a normal user and putting it somewhere that you have full access to, like your home directory.  Then you could move the install folder elsewhere with sudo.

> **MSchenker said:**
> jviscosi,
I tried Sudo, and got more errors.
My hope is to install Wubi Ubuntu 7.10 so I can get IceApe, which sounds like an easier installation.
Thanks,
Matt

I'm not familiar with Wubi Ubuntu but if it's easy enough, go for it.

---

### Post by MSchenker on 2007-10-26
> **nanotube said:**
> well, who told you that? to be blunt, they didn't know what they were talking about. :) ubuntuzilla is primarily for the desktop - because that's where you would /want/ to install browsers and email clients. (though of course it would work on a "server", too - installing software on a "server" and on a "desktop" is exactly the same.)

To be honest, I've received so many different kinds of conflicting advice from so many people regarding installing applications, I can hardly  keep track any more.  I'm new at Linux, and I must say the whole process of installing applications is quickly driving me away.

---

### Post by jviscosi on 2007-10-26
You can do a "manual" install of Seamonkey without running the installer by following these instructions from Mozilla.  (I haven't done it this way myself.)  This is taken from [http://www.mozilla.org/projects/seamonkey/releases/seamonkey1.1/installation.html#linux_install_installer](http://www.mozilla.org/projects/seamonkey/releases/seamonkey1.1/installation.html#linux_install_installer).  None of it appears to involve having to invoke sudo on a graphical program.

**Manual Installation With the tar.gz Archive**

 To install SeaMonkey by downloading the .tar.gz archive file:[LIST=1]
[*]Create a directory named "seamonkey1.1" (mkdir seamonkey1.1) and     change to that directory (cd seamonkey1.1).
[*]Click the link to download the non-installer seamonkey*.tar.gz file into the     seamonkey1.1 directory.
[*]Change to the seamonkey directory (cd seamonkey1.1) and decompress     the file with the following command:
     gunzip -dc sea*.tar.gz | tar -xvf -  (This creates a "seamonkey"     subdirectory under your seamonkey1.1 directory.)
[*]Change to the seamonkey directory (cd seamonkey).
[*]Run SeaMonkey with the ./seamonkey run script.[/LIST]> **MSchenker said:**
> To be honest, I've received so many different kinds of conflicting advice from so many people regarding installing applications, I can hardly  keep track any more.  I'm new at Linux, and I must say the whole process of installing applications is quickly driving me away.

The advice most people would give is probably "stick to installing from the repositories", which is fine until there's an app you want that isn't in them.  At that point the easiest thing to do is find a prepared package (from a legitimate source!) that you can download and install.  For instance, it looks like you can get IceApe .DEB files from [http://packages.debian.org/sid/iceape](http://packages.debian.org/sid/iceape).  (I'm pointing you at Sid because that's the version that seems to be included in the repositories.)  There are links from there to the other components of IceApe.  You would download these DEB files to wherever and then install them with:

[B]sudo dpkg -i iceape_1.1.4-1_all.deb
[/B]
And so on for the other packages. (I should point out that I haven't tried these DEBs myself.)  There is nothing graphical about this procedure so you shouldn't get those sudo errors, which appear to be coming off of X. (Those may be problematic for you if you try to run other GUIs with sudo in the future, BTW.)  This method may run into dependency problems, though, in which case the app might fail to install.

If you can't find a DEB but you can find an RPM, you can use alien to convert the RPM to a DEB and then install the DEB as above.  I've done this once or twice.

If you can't find a DEB or an RPM package, the next way to install is compiling from source.  I'm not going to suggest you try that right now as you'll probably find it frustrating.  (I've been doing it for years and I still find it frustrating at times.)  Eventually you might want to give it a try, but be sure to read the instructions for each program.

---

### Post by MSchenker on 2007-11-02
I succeeded in installing SeaMonkey in Kubuntu!

All I really had to do was follow the directions on the Ubuntuzilla wiki ([http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)).  Just wanted to post it here for anyone else who is looking to install SeaMonkey.

I've still got a couple of questions:
[LIST]
[*]How do I install a separate icon on the desktop for SeaMonkey mail?
[*]Is Ubuntuzilla invisible, behind the scenes, keeping track of my SeaMonkey version?[/LIST]But I have my favorite Internet suite up and running on Kubuntu!

Thanks,
Matt

---

### Post by nanotube on 2007-11-05
> **MSchenker said:**
> I succeeded in installing SeaMonkey in Kubuntu!
excellent! :)

> 
All I really had to do was follow the directions on the Ubuntuzilla wiki ([http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)).  Just wanted to post it here for anyone else who is looking to install SeaMonkey.

I've still got a couple of questions:
[LIST]
[*]How do I install a separate icon on the desktop for SeaMonkey mail?
[*]Is Ubuntuzilla invisible, behind the scenes, keeping track of my SeaMonkey version?[/LIST]But I have my favorite Internet suite up and running on Kubuntu!

Thanks,
Matt

to answer your two questions:
to make an icon to start mail directly, make a shortcut to 
```
seamonkey -mail
```

yes, ubuntuzilla is invisibly behind the scenes keeping track of your seamonkey version - if you chose "yes" at the end of installation when it asked you whether you want to install the update checker job.

---

### Post by ADH on 2007-11-05
I just installed Ubuntuzilla (downloaded it, saved it to desktop, double-clicked, and it installed what it needed.  It remains on my desktop - I guess it stays there?)  I don't see a way to tell it what I want to download and install - Seamonkey, in this case.  Is there a something simple I'm missing?

Thanks,

---

### Post by nanotube on 2007-11-06
> **ADH said:**
> I just installed Ubuntuzilla (downloaded it, saved it to desktop, double-clicked, and it installed what it needed.  It remains on my desktop - I guess it stays there?)  I don't see a way to tell it what I want to download and install - Seamonkey, in this case.  Is there a something simple I'm missing?

Thanks,

hi,
please see the instructions on the ubuntuzilla website for details
(link in my sig)

in brief, to install seamonkey, run the following command:
```
ubuntuzilla.py -a install -p seamonkey
```

(also, feel free to delete the ubuntuzilla.deb from your desktop - it's only needed for the initial install of ubuntuzilla).

post back if you run into any problems :)

---

### Post by ADH on 2007-11-11
Thanks - that seems to have worked.

---

