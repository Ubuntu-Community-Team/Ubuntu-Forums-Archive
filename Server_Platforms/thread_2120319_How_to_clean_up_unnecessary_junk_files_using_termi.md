---
title: "How to clean up unnecessary junk files using terminal"
date: 2013-02-26
forum: Server Platforms
---

### Post by sharif_aly on 2013-02-26
How Clean up all those unnecessary junk files Using Terminal ?

I know this command :
> sudo apt-get autoclean

But if you know anything else please let us know.

---

### Post by cortman on 2013-02-26
What exactly do you mean by "unnecessary junk file"?
If you're talking about about cleaning up the package system, apt-get clean and autoclean are what you want. Other commands can be found through a brief perusal of the dpkg and apt man pages.

---

### Post by sharif_aly on 2013-02-26
> **cortman said:**
> What exactly do you mean by "unnecessary junk file"?
If you're talking about about cleaning up the package system, apt-get clean and autoclean are what you want. Other commands can be found through a brief perusal of the dpkg and apt man pages.

To clean files that is not needed, not just files of packages, like temp files and files which is not needed, mean all files.

If you able to help, show me how you clean your system with terminal.

---

### Post by cortman on 2013-02-26
You mean [this]("http://bleachbit.sourceforge.net/")?

---

### Post by sharif_aly on 2013-02-26
Yeah, But something that I can run from terminal, like the commend I mention.

---

### Post by slickymaster on 2013-02-26
_Getting rid of Residual Config packages_
In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages. Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine. To use this feature, go to **System > Administration > Synaptic Package Manager**. On the bottom left hand corner of the window, click the Status button. In the list above the Sections, Status, Search, and Custom buttons, you should see the following text:
```
Installed
Installed (local or obsolete)
Not installed
Residual config
```
Click on the "Residual config" text. If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine. If you see the packages that popped up in the window on the right, those are the Residual Config packages. To get rid of these, click on the box to the left of the package name and select _"Mark for Complete Removal"_. After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window and click the green check mark with the text "Apply" right under it. That button will flush all those Residual Config packages.

---

### Post by sharif_aly on 2013-02-26
> **slickymaster said:**
> _Getting rid of Residual Config packages_
In Synaptic Package Manger, there is a built-in feature that gets rid of old Residual Config packages. Residual Config packages are usually dependency packages that are left behind after you uninstall a package from your machine. To use this feature, go to **System > Administration > Synaptic Package Manager**. On the bottom left hand corner of the window, click the Status button. In the list above the Sections, Status, Search, and Custom buttons, you should see the following text:
```
Installed
Installed (local or obsolete)
Not installed
Residual config
```
Click on the "Residual config" text. If the "Residual config dialogue does not appear, that means you do not have any Residual Config packages on your machine. If you see the packages that popped up in the window on the right, those are the Residual Config packages. To get rid of these, click on the box to the left of the package name and select _"Mark for Complete Removal"_. After you have done that for all of the Residual Config packages, look at the top of the Synaptic Package Manger window and click the green check mark with the text "Apply" right under it. That button will flush all those Residual Config packages.


I am not using GUI version of Ubuntu, Server Platform ( Only Terminal ).

That's Why I've asked.

---

### Post by slickymaster on 2013-02-26
> **sharif_aly said:**
> I am not using GUI version of Ubuntu, Server Platform ( Only Terminal ).

That's Why I've asked.

_Getting rid of partial packages_
```
sudo apt-get autoclean && apt-get autoremove
```
_Getting rid of "orphaned" packages:_
```
sudo apt-get install deborphan
sudo deborphan | xargs sudo apt-get -y remove --purge
```

---

### Post by schragge on 2013-02-26
[deborphan](http://manpages.ubuntu.com/manpages/precise/en/man1/deborphan.1.html), [cruft](http://manpages.ubuntu.com/manpages/precise/en/man8/cruft.8.html), [debfoster](http://manpages.ubuntu.com/manpages/precise/en/man8/debfoster.8.html), *apt-get autoremove*, [tmpreaper](http://manpages.ubuntu.com/manpages/precise/en/man8/tmpreaper.8.html) (check that your /tmp filesystem isn't mounted noatime if you're planning to use this), [rdfind](http://manpages.ubuntu.com/manpages/precise/en/man1/rdfind.1.html)

---

### Post by Habitual on 2013-02-26
> **sharif_aly said:**
> To clean files that is not needed, not just files of packages, like temp files and files which is not needed, mean all files.

If you able to help, show me how you clean your system with terminal.clarify "not needed". Specific examples?

 We can't read minds. :)

---

### Post by sharif_aly on 2013-02-26
> **Habitual said:**
> clarify "not needed". Specific examples?

 We can't read minds. :)

Of course, but unnecessary junk files, and Free cache, delete cookies, clear Internet history, shred temporary files, delete logs, and discard junk, the main thing is to free more disk space, and improve performances.

hope I did explain better.

---

### Post by spynappels on 2013-02-26
> **sharif_aly said:**
> Of course, but unnecessary junk files, and Free cache, delete cookies, clear Internet history, shred temporary files, delete logs, and discard junk, the main thing is to free more disk space, and improve performances.

hope I did explain better.

Well, the internet related stuff like Cookies, internet history etc is not likely to be much of an issue on a CLI only machine, right? Unless you're using a CLI browser, but then you'd be able to control it's behaviour separately anyway.

All the other things like shredding temp files can be done with a little bit of scripting or even using cron to schedule it at a time when no-one will be using the machine.

Rotating and deleting logs is normally done by syslog, have a look at it's man pages to see if that will do what you want.

---

### Post by GordThompson on 2013-02-26
> **sharif_aly said:**
> Of course, but unnecessary junk files, and Free cache, delete cookies, clear Internet history, shred temporary files, delete logs, and discard junk, the main thing is to free more disk space, and improve performances.

hope I did explain better.
It sounds like you're looking for something along the lines of [BleachBit]("http://bleachbit.sourceforge.net/"), but...

1. I've seen a few comments on these forums suggesting that the use of (or perhaps *abuse *of) BleachBit can cause problems itself, and

2. While it does have a command-line interface it strikes me as being more suited to cleaning up the "junk" that collects on desktop systems (as opposed to servers).

---

### Post by slickymaster on 2013-02-27
There is a script for Ubuntu named [Ubucleaner]("http://opendesktop.org/content/show.php/Ubucleaner?content=71529") that keeps the system pretty clean.

```
wget http://www.opendesktop.org/CONTENT/content-files/71529-ubucleaner.sh
sudo chmod +x 71529-ubucleaner.sh
./71529-ubucleaner.sh
```

---

### Post by cortman on 2013-02-27
Frankly, a server running a CLI only system simply shouldn't acquire much in the way of "unecessary files". Like spynappels said, no cookies or browser related junk and nothing related to any graphics libraries (GTK, QT). I personally wouldn't be very excited about running a mystery "cleanup script" on my server.

---

### Post by schragge on 2013-02-27
I've looked into the script and cleaned it up a bit. The result is below:
```

#!/bin/sh
set -e

cur=$(uname -r)
prev=$(readlink -f /vmlinuz.old) && prev=${prev#*-} || prev=@
keepkernels="^linux-(headers|image|image-extra)-($cur|$prev)"
allkernels='^linux-(headers|image|image-extra)-[0-9]'

[ root != "$USER" ] && { echo Error: must be root, aborting... >&2; exit 1; }
echo Cleaning apt cache...
apt-get clean

echo Removing no longer needed automatically installed packages...
apt-get autoremove

echo Removing old config files...
dpkg --get-selections | sed -n 's/\<deinstall$/purge/p' | dpkg --set-selections
dpkg -Pa

echo Removing old kernels...
apt-get --only-upgrade purge "$allkernels" "$keepkernels"+

echo Emptying every trashes...
rm -rf /home/*/.local/share/Trash/*/* >/dev/null 2>&1
rm -rf /root/.local/share/Trash/*/*   >/dev/null 2>&1

echo Script Finished!

```

---

### Post by vikramk.ibs on 2013-05-18
> **schragge said:**
> I've looked into the script and cleaned it up a bit. The result is below:
```

#!/bin/sh
set -e

cur=$(uname -r)
prev=$(readlink -f /vmlinuz.old) && prev=${prev#*-} || prev=@
keepkernels="^linux-(headers|image|image-extra)-($cur|$prev)"
allkernels='^linux-(headers|image|image-extra)-[0-9]'

[ root != "$USER" ] && { echo Error: must be root, aborting... >&2; exit 1; }
echo Cleaning apt cache...
apt-get clean

echo Removing no longer needed automatically installed packages...
apt-get autoremove

echo Removing old config files...
dpkg --get-selections | sed -n 's/\<deinstall$/purge/p' | dpkg --set-selections
dpkg -Pa

echo Removing old kernels...
apt-get --only-upgrade purge "$allkernels" "$keepkernels"+

echo Emptying every trashes...
rm -rf /home/*/.local/share/Trash/*/* >/dev/null 2>&1
rm -rf /root/.local/share/Trash/*/*   >/dev/null 2>&1

echo Script Finished!

```


Thanks it worked like a charm. from 70.5% to 40% of usage 

Thank you.
 God bless

---

