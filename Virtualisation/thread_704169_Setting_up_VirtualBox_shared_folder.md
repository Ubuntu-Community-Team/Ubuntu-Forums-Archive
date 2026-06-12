---
title: "Setting up VirtualBox shared folder"
date: 2008-02-22
forum: Virtualisation
---

### Post by sayakb on 2008-02-22
I cannot set-up a shared folder.. when I try to connect to the folder \\vboxsvr\foldername, my XP installed in the VBox cannot find the network location. Also, I tried to install guest additions but I get this error:
Could not find the guest additions CD image /usr/lib/virtualbox/VBoxGuestAdditions.iso

---

### Post by popch on 2008-02-22
Right now, I am nowehere near my VirtualBox machine. However, I think that using shared folders requires the guest additions to be installed.

I seem to remember that the message which states that the CD image is missing also suggests a way of fetching and installing that image. Im my case it was something really simple such as clicking on a button which said 'download' or something.

If you can not find out how to find and install that CD image, I would suggest to open another thread.

---

### Post by bodhi.zazen on 2008-02-22
You need to install the additions.

[http://doc.gwos.org/doku.php/doc:office:virtualbox#mount_the_.iso_on_your_guest_os](http://doc.gwos.org/doku.php/doc:office:virtualbox#mount_the_.iso_on_your_guest_os)

Then set it up :

[http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive](http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive)

To be honest I suggest you use a network protocol such as samba, NFS, FTP, scp (ssh), http.

---

### Post by sayakb on 2008-02-23
> **bodhi.zazen said:**
> You need to install the additions.

[http://doc.gwos.org/doku.php/doc:office:virtualbox#mount_the_.iso_on_your_guest_os](http://doc.gwos.org/doku.php/doc:office:virtualbox#mount_the_.iso_on_your_guest_os)

Then set it up :

[http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive](http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive)

To be honest I suggest you use a network protocol such as samba, NFS, FTP, scp (ssh), http.

These links say "Topic doesnot exist". Btw, I am opening them through a proxy server (since it is otherwise blocked in my college)

---

### Post by bodhi.zazen on 2008-02-23
Odd o.O

Here is the main page :

[http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

click the appropriate sections from the contents.

---

### Post by sayakb on 2008-02-24
> **bodhi.zazen said:**
> Odd o.O

Here is the main page :

[http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

click the appropriate sections from the contents.

Thank you. Nice link. I would try what it says and write here.

---

### Post by popch on 2008-02-24
> **bodhi.zazen said:**
> You need to install the additions.

[http://doc.gwos.org/doku.php/doc:office:virtualbox#mount_the_.iso_on_your_guest_os](http://doc.gwos.org/doku.php/doc:office:virtualbox#mount_the_.iso_on_your_guest_os)

Then set it up :

[http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive](http://doc.gwos.org/doku.php/doc:office:virtualbox#sharing_your_hard_drive)

To be honest I suggest you use a network protocol such as samba, NFS, FTP, scp (ssh), http.

The URLs in that post appear not to be identical to what you entered. On the processing chain from your keyboard/clipboard to the final post in the forum there's some critter which changed it.

Even my quote of your post does not look the same as the post itself. 

There are some other posts within this thread which get  'the treatment'.

> **bodhi.zazen said:**
> Odd o.O

Here is the main page :

[http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

click the appropriate sections from the contents.

After some experimentation, I can see that it's a software error in the parts of the forum software handling the smilies.

The sequence (colon, 'o') is translated into the sequence (colon, 'eek', colon) between entering the new post and displaying it when reading the thread. In some other contexts (such as quoting or in the thread summary at the bottom of the screen 'reply to thread') the sequence (before,colon,'eek',colon,after) is displayed as (before,yellowSmileyWithHorizontalStraightEyebrowsAndGapingMouth,after).

Since you are staff, can I leave it to you to report that bug to the proper place?

---

### Post by bodhi.zazen on 2008-02-24
The "solution" is to either disable smiles when you post such links (see the check boxes at the bottom when posting "disable smiles"

Or use noparse

Link : [http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

Link with noparse : [noparse]http://doc.gwos.org/doku.php/doc:office:virtualbox[/noparse]

Actual code: 
[noparse][noparse]http://doc.gwos.org/doku.php/doc:office:virtualbox[/noparse][/noparse]

The "problem" with noparse is then it is not a clickable link :(

:lollflag: I know this "fact" but i forgot it in my original post

---

