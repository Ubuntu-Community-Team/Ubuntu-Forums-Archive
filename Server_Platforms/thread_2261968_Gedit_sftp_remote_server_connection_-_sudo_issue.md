---
title: "Gedit sftp remote server connection - sudo issue"
date: 2015-01-22
forum: Server Platforms
---

### Post by scott.bouch on 2015-01-22
Hi,

I've just had some lovely success accessing my server from my workplace using an Ubuntu 12.10 laptop (gnome) - Under Places, I clicked Connect to server... set up my server's details and connected. Wonderful! I can now easily in a GUI access all of my home files.

As a test, I opened up an image (from my NAS, mounted to my server), edited it with GIMP, saved it as a new file (on the mounted NAS location)... Great!

So, on to test 2.... I want to use Gedit to edit html files on my server.

I simply opened up gedit from the gnome menu, browsed to my server, opened up one of my html files from (var/www/html)... Great... But now comes the trouble...

Upon trying to save changes to the file, or indeed save it as a new file name to var/www/html, Gedit can't because of permissions, fair enough, i'm not sudo. I can save it to my mounted NAS location though as not sudo.

So, I thought I'd run Gedit as sudo. When I go to File, Open, I don't see my network locations, in fact, the file browser is much restricted compared to a non-sudo instance of gedit.

Trying Workarounds...

I then dragged and dropped an html file from a nautilus window onto my sudo'd gedit window, only for it to fail, declaring that: "gedit cannot handle sftp: locations." which is daft, as it can when not opened as sudo.

How can I make this sudo instance of gedit work with sftp locations, as it clearly can when not sudo?

Cheers, Scott.

---

### Post by steeldriver on 2015-01-22
When you use "Nautilus --> Connect to server..." it mounts the remote filesystem as a Gnome Virtual Filesystem (gvfs) mount that is owned by you and has very restrictive permissions (root can't even read the mounted files)

---

### Post by Lars Noodén on 2015-01-22
> **scott.bouch said:**
> I simply opened up gedit from the gnome menu, browsed to my server, opened up one of my html files from (var/www/html)... Great... But now comes the trouble...

It would probably be easier to fix your directory permissions.  If you are the only user on that system, you can just take ownership of the directories and then you can run gedit as a normal user.

```

sudo chown -R scott:scott /var/www/html

```

In that way you can avoid running a graphical program as root, which is generally undesirable.  

If you are sharing the directory and files with others then something similar can be done using groups instead.

---

### Post by scott.bouch on 2015-01-22
Lars - good work!

As I'm the only user, I gave myself permissions over the directory as you said, and it's fixed it!

Now I can edit my website [www.scottbouch.com](www.scottbouch.com) remotely using the lovely gedit instead of Nano over SSH!

Thanks for the help chaps! Scott.

---

