---
title: "rsync problem"
date: 2006-07-10
forum: Server Platforms
---

### Post by leaded on 2006-07-10
I'm having a weird issue with rsync. I'm guessing it can't be resolved because I'm attempting to work with a Red Hat 7.2 box, but here goes...

I'm using rsnapshot, which is a bunch of perl scripts for rsync, for multiple development machines. I'm running Ubuntu server PPC Dapper. It's 100% up-to-date using the default sources.

My Dapper host server shows...```
root@snapshot:~# rsync --version
rsync  version 2.6.6  protocol version 29
Copyright (C) 1996-2005 by Andrew Tridgell and others
<http://rsync.samba.org/>
Capabilities: 64-bit files, socketpairs, hard links, symlinks, batchfiles,
              inplace, IPv6, 64-bit system inums, 64-bit internal inums

rsync comes with ABSOLUTELY NO WARRANTY.  This is free software, and you
are welcome to redistribute it under certain conditions.  See the GNU
General Public Licence for details.
```

Two machines I'm rsync-ing are CentOS 4.3, fully-updated, using the following version...```
$ rsync --version
rsync  version 2.6.3  protocol version 28
Copyright (C) 1996-2004 by Andrew Tridgell and others
<http://rsync.samba.org/>
Capabilities: 64-bit files, socketpairs, hard links, symlinks, batchfiles,
              inplace, IPv6, 64-bit system inums, 64-bit internal inums
```
*Note, those two versions are different, yet the rsync worked fine.

This works successfully on a Solaris 8 machine with version 2.6.8 protocol version 29.

The problem comes with this stone-age Red Hat 7.2 (not 7.3!) machine. Upon running initially, rsync died on an error code 2, which is a protocol mismatch. I went to Dag and grabbed the latest rsync rpm and upgraded it. Same error. I went back to Dag and got the open-ssh rpms. Same problem.

Here's the output from the RH7.2 box```
$ rsync --version
rsync  version 2.6.8  protocol version 29
```

Any ideas? The verion that Dapper provides is 2.6.6, but it works fine on the 2.6.8/Solaris 8 rsync. Should I just assume that some other packages for Red Hat 7.2 are just too old?

I don't feel comfortable doing too much more to the old box beyond what I've already done. It's not my box. I just don't understand why they keep Subversion running with their important code on this old machine with no backups! If I can't get this to work, I'm just going to tell them to upgrade! /rant

Thanks!

**Edit:** Below is the error message that I'm receiving after I try and do any kind of rsync command with --rsh=ssh server:folder to this old machine...
```
protocol version mismatch -- is your shell clean?
(see the rsync man page for an explanation)
rsync error: protocol incompatibility (code 2) at compat.c(64)
```

**Edit 2:** I did some more searching on Google and it was a banner problem. I thought it was the SSH login banner, but it was actually the output of Bash when you switched to bash. I couldn't find anything that looked like it would 'echo' the contents of /etc/redhat-release, which is what I saw on the screen everytime, so I just changed root's shell to /bin/sh. I don't think the box's owner will even notice. :)

---

### Post by MJN on 2006-07-10
[LEFT][COLOR=black]RTFM! *(before* asking the question!)[/COLOR][/LEFT]
 
[LEFT][COLOR=black][http://samba.anu.edu.au/rsync/FAQ.html#3](http://samba.anu.edu.au/rsync/FAQ.html#3)[/COLOR][/LEFT]

---

### Post by leaded on 2006-07-10
I *DID* and it didn't explain anything! I spent a couple hours looking on Google and disabling random things before it worked. Thanks for your needless comment...

---

### Post by MJN on 2006-07-10
[LEFT]Perhaps I should've put a smiley on. :)
 
Anyway, it does give you the solution insofar as your test.dat file would've told you exactly what the shell was sending.
 
Mathew[/LEFT]

---

