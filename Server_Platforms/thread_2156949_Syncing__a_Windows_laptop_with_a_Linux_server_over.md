---
title: "Syncing  a Windows laptop with a Linux server over the web"
date: 2013-06-23
forum: Server Platforms
---

### Post by MG2R on 2013-06-23
Here is my situation: I have a home server running Linux, I have a VPS in a database somewhere in The netherlands running Linux, I have a laptop running Windows. I wrote a script which syncs a folder on my home server with a folder on my VPS bidirectionally. I now need to figure out how to sync a folder on my Windows laptop to that synced folder on my VPS over the Internet. That way all of my documents are always in sync with my home network, no matter where I am.

Does anyone know of an application that allows me to do this (preferrably via a secure connection)? I've used ownCloud for a while to test it out, but that seemed rather slow and doesnt allow my to sync files between my two servers. It also has it's own file structure, which isn't preferred.

Any ideas?

---

### Post by CharlesA on 2013-06-23
This might help: [http://www.cygwin.com/](http://www.cygwin.com/)

I haven't used it, but I think you can run rsync and sync the files that way.

---

### Post by koenn on 2013-06-24
it would be helpful f you explained how your script does its syncing, so we know what we're talking about. 

rsync ? there are rsync implementations for windows.

---

### Post by 3L33T on 2013-06-24
Keep it simple, install Dropbox for Ubuntu and Windows and be done with it.

---

### Post by MG2R on 2013-06-25
I'll have a look into Cygwin, thanks!

I was thinking it might also be possible to set up a WebDAV share on my VPS and connect to that with my laptop, then I can simply sync a folder on my laptop to the WebDAV share using DirSync Pro...

Dropbox is a no-go. I do not trust any organization/authority/third party with my documents. My data stays on my servers.

---

### Post by SeijiSensei on 2013-06-25
An OpenVPN tunnel to your VPS is another possibility to consider, or using something like WinSCP to transfer files over SSH.  It's not a syncing solution, but if only a few files are being used, it's not that hard just to copy them manually.

---

### Post by CharlesA on 2013-06-25
> **SeijiSensei said:**
> An OpenVPN tunnel to your VPS is another possibility to consider, or using something like WinSCP to transfer files over SSH.  It's not a syncing solution, but if only a few files are being used, it's not that hard just to copy them manually.

I found this in the WinSCP manual, but I have never used it, so I don't know how good it is.
[http://winscp.net/eng/docs/task_synchronize_full](http://winscp.net/eng/docs/task_synchronize_full)

---

### Post by trundlenut on 2013-06-25
> **MG2R said:**
> I'll have a look into Cygwin, thanks!

I was thinking it might also be possible to set up a WebDAV share on my VPS and connect to that with my laptop, then I can simply sync a folder on my laptop to the WebDAV share using DirSync Pro...

Dropbox is a no-go. I do not trust any organization/authority/third party with my documents. My data stays on my servers.

Spideroak may be a more paletable option as the data is encrypted and they don't have access.  It will also run on ubuntu server.

I use Dropbox for things I don't mind being visible/readable by others and Spideroak for those I am less keen on sharing.

---

### Post by mozkill on 2013-06-25
For sure, the best way to sync files between a Ubuntu system and Windows/Mac  is to use  [**AeroFS**]("https://aerofs.com/") .  It has unlimited file syncing and doesn't use the cloud.

---

### Post by SeijiSensei on 2013-06-25
> **CharlesA said:**
> I found this in the WinSCP manual, but I have never used it, so I don't know how good it is. [http://winscp.net/eng/docs/task_synchronize_full](http://winscp.net/eng/docs/task_synchronize_full)

That certainly looks promising, doesn't it, Charles?  I've only used WinSCP a couple of times, mostly to help people on Windows post files to a web server.  It's basically a standard two-window file manager with local and remote directory trees.  It's a cinch to use if you are connecting to a machine where SSH is supported.

---

### Post by CharlesA on 2013-06-25
> **SeijiSensei said:**
> That certainly looks promising, doesn't it, Charles?  I've only used WinSCP a couple of times, mostly to help people on Windows post files to a web server.  It's basically a standard two-window file manager with local and remote directory trees.  It's a cinch to use if you are connecting to a machine where SSH is supported.

Aye. I have WinSCP on a thumb drive for transferring stuff from my Windows laptop when I am away, but I've never used it as a sync tool. Sounds quite handy.

---

### Post by MG2R on 2013-06-25
Okay, thanks guys! You're being tremendous as always :)

With these suggestions, I might be able to set something up. It's going to take a while to get through it all though... Busy life :)

---

