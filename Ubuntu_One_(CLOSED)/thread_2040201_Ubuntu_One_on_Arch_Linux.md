---
title: "Ubuntu One on Arch Linux"
date: 2012-08-10
forum: Ubuntu One (CLOSED)
---

### Post by OakRaider4Life on 2012-08-10
[s]Hello,

I'm a once-upon-a-time Ubuntu user who has since moved on to Arch Linux.  When I moved though, I was happy to discover that I could take Ubuntu  One with me to backup my most important files (Ubuntu One and its  clients are available in the trusted community portion of the Arch  repositories).

However, I've hit a confusing snag with Ubuntu One. Any time I open the  SSO client to sync my folders locally, checking the "sync locally"  checkbox results in an "IPC Error".

I am not having this same problem with my Ubuntu One folder, which syncs with no problems whatsoever.

In an attempt to diagnose the problem in greater detail, I tried a few  things in the u1sdtool command line tool, and here were my results.

Immediately after the execution of any and every u1sdtool comand, I  receive an "ERROR:root:Could not find any typelib for Unity." Not  surprising, considering I'm in a KDE environment. The u1sdtool -c  command results only in this error, and no other output; there is no  indication of why it is no syncing my folders locally, or whether it  really even tried.

The u1sdtool --subscribe-folder=[folder id] results in "Oops, an error occured: need more than 0 values to unpack"

There is noting in my log files from Ubuntu One.

Any help in troubleshooting these errors is greatly appreciated, as my  attempts to seek help in the Arch forums met with no response.

[EDIT: I also tried removing the folder from sync, and resyncing the  folder through the SSO client, which resulted in the error "The chosen  directory is not valid. Please choose a folder inside of your home  directory and not overlapping with any other cloud folder." Trying to  re-add the folder as a cloud folder through u1sdtool results in the  "need more than 0 values" error again.

The folder I'm trying to upload is my documents folder, but it is in  fact a symlink to a shared directory on my home partition which I share  between multiple distros. Could this be my error? Although when I had  Ubuntu syncing the symlinked directory was not a problem.

I really don't want to have to resort to using google drive :sad:][/s]

[EDIT #2: It would appear that the symlinking is in fact the problem. Because the folders I am trying to sync are symlinks to a different part of the partition which is outside of my user's home directory, the syncing was not working. Is there any way to work around this?]

---

### Post by OakRaider4Life on 2012-08-10
SOLUTION:

Since U1 cannot follow symlinks, and both my documents and pictures are symlinks which point to a shared folder on my /home partition, I had to work out an alternate method to setup those shared folders in my ~ directory.

I did this by using the mount --bind option to mount the shared folders inside of my home directory, then added fstab entries for each folder to mount them at boot time.

U1 has displayed no problem syncing the mounts, and I'm back to having a working U1 installation.

Hopefully this thread can help someone.

---

