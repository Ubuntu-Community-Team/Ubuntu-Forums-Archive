---
title: "Remastersys and Security"
date: 2011-03-17
forum: Security
---

### Post by libssd on 2011-03-17
This was the final post in a thread that was just closed:

> Just a note that the <remastersys>program is not supported by Canonical and that allowing that program may allow an unauthenticated attacker also to take control over your system.

At least that's what Ubuntu 10.10 Synaptic Package Manager pop-up reports.

Since the thread has been closed, I can't follow up. My take is that this warning is a standard disclaimer by Canonical [translation: Don't use software from untrusted sources], but I would be interested in hearing from others with more experience.

---

### Post by bodhi.zazen on 2011-03-17
I do not know the vulnerability they are referring to , nor did it come up on a google search.

You could post a bug on LP or email canonical with the question, but, no that is not a "standard disclaimer" in synaptic, at least I have not seen it before.

---

### Post by libssd on 2011-03-17
Thank you, bodhi.zazen. Yours is the voice I most trust here regarding security advice. I had been similarly unable to find anything on the web, and since Remastersys shows up in the Ubuntu Software Center, where the only warning is:

"Application remastersys has an unknown maintenance status."

I'm not going to worry about it unless someone comes up with a smoking gun.

---

### Post by cariboo on 2011-03-17
> **libssd said:**
> This was the final post in a thread that was just closed:



Since the thread has been closed, I can't follow up. My take is that this warning is a standard disclaimer by Canonical [translation: Don't use software from untrusted sources], but I would be interested in hearing from others with more experience.

The remastersys web site was cracked several months ago, but that shouldn't have anything to do with the message you are seeing. Remastersys is not in the repositories, so I would suggest you have a ppa of some sort enabled.

---

### Post by bodhi.zazen on 2011-03-17
> **libssd said:**
> Thank you, bodhi.zazen. Yours is the voice I most trust here regarding security advice. I had been similarly unable to find anything on the web, and since Remastersys shows up in the Ubuntu Software Center, where the only warning is:

"Application remastersys has an unknown maintenance status."

I'm not going to worry about it unless someone comes up with a smoking gun.

There are only 2 potential problems I have had with remastersys ...

1. It will alter your (host) OS if you run it with the "distro" option. Specifically it will delete users from the system.

2. If you do not run with the "distro" option, it then includes potentially private information on the resulting live iso.

If you have the time and interest, more recently I found the debian live scripts to be a superior option, although there is a learning curve with them. They do not alter the host and with proper hooks you get a clean iso , with as many customizations as you might wish, so long as you script them, and an installer on the iso.

Of course it help if you already understand the basics of a live CD first. The live scripts simply automate the process.

[http://live.debian.net/](http://live.debian.net/)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

If you just want a "simple" snapshot of your system, remastersys is fine, just make sure you read and understand the documentation.

If you are using it for backup , I personally would look at an alternate.

If you are wanting to make custom iso with any regularity, look at the links I gave you, they are "easier" and cleaner.

---

### Post by libssd on 2011-03-17
**cariboo907**: Correct, I added the remastersys ppa to my sources list more than a year ago; I didn't realize that this would make it appear in the Ubuntu Software Center as well as in Synaptic.

**Bodhi.zazen**: I use Remastersys only to create a restorable snapshot of my system. I've shot myself in the foot enough times with experiments gone wrong, and knowing that I can restore my system to exactly the same state as my latest image backup is a great comfort. I'm a strong believer in "if it ain't broke, don't fix it," and Remastersys has served my limited needs well.

---

### Post by bodhi.zazen on 2011-03-17
> **libssd said:**
> **cariboo907**: Correct, I added the remastersys ppa to my sources list more than a year ago; I didn't realize that this would make it appear in the Ubuntu Software Center as well as in Synaptic.

**Bodhi.zazen**: I use Remastersys only to create a restorable snapshot of my system. I've shot myself in the foot enough times with experiments gone wrong, and knowing that I can restore my system to exactly the same state as my latest image backup is a great comfort. I'm a strong believer in "if it ain't broke, don't fix it," and Remastersys has served my limited needs well.

If it is of any assistance, what I do for backups is:

1. I keep a data partition, separate from root, so anything I want to "keep" as far as data is there, and backup the data partition.

2. For system files that I manually write or edit:
[list][*]Keep a copy of the original file in /data/etc.
[*]Keep a copy of the modified file in /data/etc (keep the directory organized of course).[/list]

3. For all the rest, I just generate a package list and use that to re-install.

There are several tutorials for how to do this, see:

[http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

[http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)

So basically, the size of the backups is much smaller (just /home and /data and a package list).

I used to use other techniques, partimage, etc, but the backups are huge, sometimes more then a DVD, especially if the image is not compressed.

Try the above with a virtual machine, it is simple, reliable, and easy.

You can also look at rsync , rsync has the advantage of only backing up what has changed. This is extremely helpful if you have an old box to use as a "server".

---

### Post by .Guest. on 2011-05-26
> **bodhi.zazen said:**
> There are only 2 potential problems I have had with remastersys ...

1. It will alter your (host) OS if you run it with the "distro" option. Specifically it will delete users from the system.

2. If you do not run with the "distro" option, it then includes potentially private information on the resulting live iso.

If you have the time and interest, more recently I found the debian live scripts to be a superior option, although there is a learning curve with them. They do not alter the host and with proper hooks you get a clean iso , with as many customizations as you might wish, so long as you script them, and an installer on the iso.

Of course it help if you already understand the basics of a live CD first. The live scripts simply automate the process.

[http://live.debian.net/](http://live.debian.net/)

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)


If you just want a "simple" snapshot of your system, remastersys is fine, just make sure you read and understand the documentation.

If you are using it for backup , I personally would look at an alternate.

If you are wanting to make custom iso with any regularity, look at the links I gave you, they are "easier" and cleaner.
-> Newbie asking basic questions. <- 

Thanks for the links to the debian live project. 

Can you please refer to the documentation about remastersys altering the host os? 

How does it alter the host os? 

Do you mean that once remastersys is run, the os that ran it to create the .iso is altered?

If the goal is to create an .iso that includes several wanted application, and excludes others, using the "host os", how is this done?

Read the debian-live documentation. That seems like a good process, but can it be simplified, to something like

--> This is how to include wanted folders/applications in the .iso to be burned.

--> This is how to exclude unwanted folders/application in the .iso to be burned.

--> This is how to check the final compilation of folders/applications in the .iso to be burned.

-- This is how to check the total size of the .iso to be burned.

? 

Thanks.

---

### Post by bodhi.zazen on 2011-05-26
> **.Guest. said:**
> -> Newbie asking basic questions. <- 

Thanks for the links to the debian live project. 

Can you please refer to the documentation about remastersys altering the host os? 

How does it alter the host os? 

Do you mean that once remastersys is run, the os that ran it to create the .iso is altered?

If the goal is to create an .iso that includes several wanted application, and excludes others, using the "host os", how is this done?

Read the debian-live documentation. That seems like a good process, but can it be simplified, to something like

--> This is how to include wanted folders/applications in the .iso to be burned.

--> This is how to exclude unwanted folders/application in the .iso to be burned.

--> This is how to check the final compilation of folders/applications in the .iso to be burned.

-- This is how to check the total size of the .iso to be burned.

? 

Thanks.

For documentation of remastersys see the remastersys documentation

[http://geekconnection.org/remastersys/info.html](http://geekconnection.org/remastersys/info.html)

Which is of course in as good order as any other documentation on live CD, which is to say, poor (IMHO).

I have not run remastersys in a while, but you will need to carefully read and understand the man page.

The debian live documentation is similar, those pages are as good as it gets.

On the bright side, I am working on a web page to fill in some of the details of building a live CD, but I have not finished it yet.

with debian live, read the documentation and the man pages.

then start running the commands and you will probably sort it out. If you have a specific question about a specific file or step of running remastersys or debian live, ask, but recreating the existing documentation is beyond what I can post on these forums.

Edit - learning to build a custom CD requires a lot of reading and learning the various components. Once you understand the components, building the CD is easy ;)

you need to understand at least the basics of a chroot, syslinux or grub (at least where grub pertains to booting a CD), squashfs, casper, initrd, mkisofs, and a kernel.

Edit2: the reason / purpose of the debian live scripts is that it automates the process for you.

---

### Post by .Guest. on 2011-05-26
Thanks.

---

### Post by .Guest. on 2011-07-27
[quote=bodhi.zazen]On the bright side, I am working on a web page to fill in some of the details of building a live CD, but I have not finished it yet.[/quote]
Have you done further work on the detailed tutorial and the web page?

Tried to complete the tutorial from the 'LiveCDCustomizationFromScratch - Community Ubuntu Documentation' tutorial. Did not get all the way through without errors, most likely during the 'chroot' parts.

Could not get 'Remastersys' to work. Kept getting error message '.iso is too large'.

'UCK' worked to customize a LiveCd, adding and substracting packages.

'dd' commands worked to copy an installed and customized system to .iso, then to DVD.

However, it would be fun to learn how to start with a kernel, and finish with a complete system, from the terminal.

The 'visitor message' system requires 75 posts, or this post would be placed on your user page. 

Thanks.

---

### Post by libssd on 2011-07-27
> **.Guest. said:**
> Could not get 'Remastersys' to work. Kept getting error message '.iso is too large'.
I'm reasonably certain that a Remastersys image cannot span multiple DVDs, therefore, ~4.4gb is the largest image you can create. Use the customize options to exclude certain directories until you get it down under that size. The easiest way to do this without using command line is to select a directory, then Ctrl-C to copy, then Ctrl-V to paste it into the exclude string. Separate each entry with a blank space.

---

