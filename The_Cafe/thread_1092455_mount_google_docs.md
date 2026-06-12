---
title: "mount google docs"
date: 2009-03-10
forum: The Cafe
---

### Post by bonfire89 on 2009-03-10
Is it possible to mount your google docs as a folder? That would be sweet.

Either that or something that syncs your google docs files with local folders.

I know there are plugins for openoffice that allow importing and exporting.. but that isn't quite the same.

It would be pretty interesting if this could be done.

---

### Post by Dragonbite on 2009-03-10
That would be really cool, might even be the idea behind the gDrive rumored.

---

### Post by arune on 2009-11-11
Have a look at google-docs-fs, [http://code.google.com/p/google-docs-fs/](http://code.google.com/p/google-docs-fs/)
I'll test when I get home from work. Looks promising.

---

### Post by Dragonbite on 2009-11-11
> **arune said:**
> Have a look at google-docs-fs, [http://code.google.com/p/google-docs-fs/](http://code.google.com/p/google-docs-fs/)
I'll test when I get home from work. Looks promising.

Oooohhh... tempting.

---

### Post by Dragonbite on 2009-11-11
Would if offer offline syncing, so the documents are cached on the local system until it can connect and sync with the upstream (on google's servers) version?  That would be awesome!

Waaaaaiiiiitt....

So on a netbook, you could; Access email via IMAP with Evolution, Synch your Contacts, Sync Calendar with Google Calendar and Open Google Doc files using OpenOffice.

So all you need to do is sync your Firefox bookmarks with Google Bookmarks and provide F-Spot with a means to access your Picasaweb account without having to store them locally and that would be the BALLS! That would be a true Netbook, where everything is on the web!

---

### Post by Dragonbite on 2009-11-13
Isn't installing for me.  I got ```
sudo ./INSTALL.py
mv: cannot stat `/usr/local/lib/python2.6/dist-packages/atom': No such file or directory
mv: cannot stat `/usr/local/lib/python2.6/dist-packages/gdata': No such file or directory
mv: cannot stat `/usr/local/lib/python2.6/dist-packages/gdata-1.3.3.egg-info': No such file or directory
Installing google-docs-fs to: /usr/lib/python2.6/dist-packages/google-docs-fs

```

I didn't find the required gdata-python-client but I did find gdata-python in the repository. I'm not sure if there is a difference. I'll have to check out the link.

---

### Post by life-on-mars on 2010-01-01
The python client in the repository doesn't seem to work.

You can download gdata-python-client from [http://code.google.com/p/gdata-python-client/]("http://code.google.com/p/gdata-python-client/").

The installer copies the files to /usr/local/lib/python2.6/ though. To use it under Ubuntu you can move the files to /usr/lib/python2.6/ or possibly change $PYTHONPATH (I haven't tried that though).


I've just tried it, and I think it's by far too slow. It reminds me a bit in mount NFS over the internet. I think [gdatacopier]("http://code.google.com/p/gdatacopier/") is a better alternative, just like scp works better over WAN than NFS.

---

### Post by nutznboltz on 2010-01-15
Better installation instructions:


Install dependencies:

```
sudo aptitude install python-fuse python-elementtree
```

Karmic only has python-gdata 1.2.4-0ubuntu2 which is too old so get gdata 2.0.6 from here:

[http://code.google.com/p/gdata-python-client/](http://code.google.com/p/gdata-python-client/)

and install that. Look for the README.txt and INSTALL.txt for info.

Once the dependencies are satisfied:
```

sudo aptitude install subversion
svn co http://google-docs-fs.googlecode.com/^Cn/trunk/ google-docs-fs
```

and install that.

Then "gmount /doc john.doe" will work without even needing sudo. Note that "/doc" has to be owned by your non-root account. Substitute your google docs account for "john.doe" (duh.)

view mounted file system:
```

mount | grep gFile
gFile.py on /doc type fuse.gFile.py (rw,nosuid,nodev,user=nutznboltz)
```

---

### Post by krismatth3 on 2010-03-27
Someone else has provided a PPA for it: [https://edge.launchpad.net/~invernizzi/+archive/google-docs-fs]("https://edge.launchpad.net/~invernizzi/+archive/google-docs-fs")

---

### Post by sis on 2010-07-29
Hi,
give google doc mount a try
[http://doctormo.org/2010/07/20/google-doc-mount/](http://doctormo.org/2010/07/20/google-doc-mount/)
Cheers

---

### Post by Dragonbite on 2010-07-29
> **sis said:**
> Hi,
give google doc mount a try
[http://doctormo.org/2010/07/20/google-doc-mount/](http://doctormo.org/2010/07/20/google-doc-mount/)
Cheers

Looks like a promising start. I hope it doesn't get abandoned, and/or makes it into other distros as well.

---

### Post by DoctorMO on 2010-08-09
Depends on if you think the method used is a way forward, I think probably not.

Although if you know any company with $2k who wants to fund the venture and get the functionality done. Let me know.

---

### Post by Nonplay on 2010-09-02
Anyone knows if using this kind of software is a violation of terms of google mail or google docs? 
I used google-docs-fs and seems work quite well, but I hope don't find my account disabled a day... 
Thanks for the replies!

---

### Post by unluckyluke on 2010-10-26
Hi everybody,

I tried google-docs-fs and I find it very interesting, but I am getting errors each time I try to send a command to the mounted filesystem.

For instance, ls command replies:
ls: reading directory .: Invalid argument

I'm working on Karmic Koala with gdata 2.0.12 installed. Any idea about what's going wrong?

Thank you guys!8-[

---

### Post by Dragonbite on 2010-10-26
It may not be mounting it in the same way, but there is an extension that allows you to import and export Google Doc files into/out of OpenOffice.org.  It's one of those things I hope they keep compatible with LibreOffice when the times comes.

[[COLOR="Blue"]_OpenOffice.org2GoogleDocs_[/COLOR]]("http://extensions.services.openoffice.org/project/ooo2gd")

It's an OpenOffice Extension, so you don't have to get a .deb or .rpm or worry about versions so much.

---

### Post by unluckyluke on 2010-10-26
Very interesting plugin!

And thanks also for your very fast reply, Dragonbite!

I just tried the install procedure on a Lucid server, and it seems not to send any kind of output errors!

I'll seriously consider upgrading the clients!

Cheers!

---

### Post by Uriel.Fanelli on 2011-06-23
> **Dragonbite said:**
> 
So all you need to do is sync your Firefox bookmarks with Google Bookmarks and provide F-Spot with a means to access your Picasaweb account without having to store them locally and that would be the BALLS! That would be a true Netbook, where everything is on the web!

There is already something like this: try here:

[http://medusaworkbench.blogspot.com/2009/06/screenshots.html](http://medusaworkbench.blogspot.com/2009/06/screenshots.html)

It is a tiny client (some MB of binary) and has everything of google built in via web.

Uriel

---

### Post by Macskeeball on 2011-06-23
old thread (2009)

---

