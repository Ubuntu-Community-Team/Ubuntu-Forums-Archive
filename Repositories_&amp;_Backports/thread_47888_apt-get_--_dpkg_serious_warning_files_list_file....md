---
title: "apt-get -- dpkg: serious warning: files list file...."
date: 2005-07-10
forum: Repositories &amp; Backports
---

### Post by weeroona on 2005-07-10
For more than a month now, when I am using apt-get or synaptic (updating/upgrading/installing), I get this warning:
> dpkg: serious warning: files list file for package `man-db' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lvm2' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `manpages' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `flex' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `python2.4-opengl' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libgnomecanvas2-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `mdadm' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `gnome-desktop-data' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `lvm10' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libwrap0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `netcat' missing, assuming package has no files currently installed.

It doesn't seem to cause a problem, but it'd be nice to have it dealt with. I've googled the message and haven't found much relating to Ubuntu and only a little general Debian references. None that made sense to me as a solution. Any thoughts?

---

### Post by Xian on 2005-07-10
My only thought is that you may have some corruption on your HD.
Maybe some bad blocks....

You might try running [fsck](http://www.die.net/doc/linux/man/man8/fsck.8.html) to check for errors.

---

### Post by weeroona on 2005-07-12
[QUOTE=Xian]My only thought is that you may have some corruption on your HD.
Maybe some bad blocks....

You might try running [fsck](http://www.die.net/doc/linux/man/man8/fsck.8.html) to check for errors.[/QUOTE]
 Thanks! 
When I ran fsck, it told me I shouldn't run fsck on a mounted drive. I need to dig up a live CD to try that. 

Is this different from what is run during the bootup if a drive is not unmounted properly? I tried having Gnome put the computer into 'standby'. It shut down very quickly and was not happy when I booted it back up.

---

### Post by bob k on 2005-08-02
I too am having the same problem and having the problem when I do an update/upgrade, and yes it was caused by a problem on the hard drive directory structure. I did a fix on the directory and lost a few files. My system runs fine, I just use it for surfing, but would like to fix the missing files.

I'm sure the files are still there and only the reference has been damaged. The files are not that big, so what I wanted to do is let APT_GET to download the missing files and update them.

Is there any to do this in APT or DPKG?

TIA

Bob

---

### Post by bob k on 2005-08-03
I found what the error message means, in the directory /var/lib/dpkg/info there are .list files for every package installed, which contains a list of all files for the package. apt-get, dselect, and dpkg use this file to determine what version and the current files installed for the package. When the .list file is missing you will get the error message.

In my case I think just the .list files are missing because the applications it complains all work (bash dpkg file). The only answer I can figure other than installing the packages is to download the Ubuntu repository .bz files and extract the .list files for each package.

I don't think this is a serious enough problem to correct until I have a day to mess around with it or an upgrade fails.

---

### Post by doclivingston on 2005-08-04
The error will occur if some of the files in /var/lib/dpkg/info have gone missing. The biggest problem it should cause is that if you remove a package with the list file missing, the files contained in the package will not actually be deleted from disk.

---

### Post by raul_ on 2007-02-04
Wow, really old thread, but it's the first to pop up in google :P 

Would reinstalling the packages help?

---

### Post by lackhead on 2008-01-30
> **raul_ said:**
> Wow, really old thread, but it's the first to pop up in google :P 

Would reinstalling the packages help?

Ok,  I know this is an ancient thread, but I ran into this same problem and found a fix.  What happened to me was that a few files in /var/lib/dpkg/info accidentally got corrupted (bad data written to a few of the .list files).  I tried removing & reinstalling via aptitude/apt-get, moving the corrupted files out of the way and starting over, everything that I could think of to recreate the mangled files, and then finally, I did this for each package that was complaining:

1) download deb file with "aptitude download <pkg>"
2) ran "dpkg -i <debfile>

That's it- that re-created the files and life seems good now. I hope that helps. 



-c

---

### Post by Taiebot65 on 2008-02-07
I think i have got the same problem but i did it delebirately... I couldn't get  upgrade and update and i found a thread who was saying to rename the /var/lib/dpkg/info to /var/lib/dpkg/info/info_old...

Since that I ve got recurrent problems to upgrade.. update..

---

### Post by alloydog on 2008-05-29
reviving old threads again...

I had the problem when I removed **gnash** manually, when for some reason neither **apt-get** or **Synaptic** wouldn't/couldn't remove it.

After a bit of digging, I found this:
> */var/lib/dpkg/status*
[INDENT]Statuses of available packages. This file contains information about whether a package is marked for removing or not, whether it is installed or not, etc.[/INDENT]
From [**_Manpage of DPKG_**](http://linuxreviews.org/man/dpkg/) (In other words, RTFM! ;) )

For **gnash** and **gnash-common** the statuses were give as [FONT="Courier New"]ok installed[/FONT].
I replaced the status line with [FONT="Courier New"]purge ok not-installed[/FONT] and no longer get the message.

---

