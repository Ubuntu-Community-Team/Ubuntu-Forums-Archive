---
title: "open file from SMB share without mounting"
date: 2009-10-15
forum: Server Platforms
---

### Post by TorianIronfist on 2009-10-15
Hi,

I have been running an ubuntu server for a couple years now and I have enjoyed the flexibility it gives.  I use it mainly as a file server and have samba installed so my windows machines have easy access to it.  Occasionally, I find myself logged into the server over ssh and needing a file from a shared folder on one of my windows machines.  Therefore I create a directory, mount the windows shared folder too it, copy the file out, unmount etc...

What I was wondering if is there was a way to skip a step.  If I just want to access a single file on the other machine is there a way to browse the shares of a window machine from the command line.  I know that if you use nautilus, you can achieve this, but i wasn't sure whether that was just because nautilus was temporarily mounting the shares in the background.

Any help would be appreciated.

Thanks

Torian

Edit: This may not actually be possible, but I would be glad to know either way.

---

### Post by bab1 on 2009-10-15
> **TorianIronfist said:**
> Hi,

I have been running an ubuntu server for a couple years now and I have enjoyed the flexibility it gives.  I use it mainly as a file server and have samba installed so my windows machines have easy access to it.  Occasionally, I find myself logged into the server over ssh and needing a file from a shared folder on one of my windows machines.  Therefore I create a directory, mount the windows shared folder too it, copy the file out, unmount etc...

What I was wondering if is there was a way to skip a step.  If I just want to access a single file on the other machine is there a way to browse the shares of a window machine from the command line.  I know that if you use nautilus, you can achieve this, but i wasn't sure whether that was just because nautilus was temporarily mounting the shares in the background.

Any help would be appreciated.

Thanks

Torian

Edit: This may not actually be possible, but I would be glad to know either way.

Torian,

This is the one thing that Nautilus (and the supporting libs) can do that AFAIK can't be done from the CLI; the on the fly mounting of shares.

In fact when you browse he shares and elect to open a folder or a file the share is mounted via GVFS (Gnome Virtual File System).  The mount point is in your home directory under the .gvfs directory.  The permanent Nautilus configuration of Samba is at /var/lib/samba.

This is the same sort of deal in Windows.  Microsoft even will do name resolution without a DNS or WINS server present.  It is built into the latest DLL's.  I have used this little known feature on some of my small LAN installs where I did not have access to DNS or WINS.

---

### Post by TorianIronfist on 2009-10-16
Alright,  well it it nice to know that I haven't just been missing something :) .

Thanks for your help.

Torian

---

