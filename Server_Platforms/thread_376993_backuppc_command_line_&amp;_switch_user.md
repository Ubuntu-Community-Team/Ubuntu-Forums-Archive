---
title: "backuppc command line &amp; switch user"
date: 2007-03-05
forum: Server Platforms
---

### Post by gmalac on 2007-03-05
Hi,
I installed Backuppc & it works well... I did spend some days figuring things out though and I am far from mastering it.
I am backing-up two WinXP shares from two PCs on my home network (wife and girl) on my Ubuntu box.
As I progress in my understanding of the program, I realize that I have not enabled the compression. Backuppc has a (script?) command line BackupPC_compPool that is supposed to be run, as user backuppc to fix this properly. Thus my questions:
- how to switch to user backuppc for just this one operation?
- how to run this command line (found under /usr/share/backuppc/bin/BackupPC_compPool?
Thanks for any help
Guy

---

### Post by syadnom on 2007-08-18
> ***_- how to switch to user backuppc for just this one operation?_***

become root:
> sudo -i
<enter your password>
now become backuppc:
> su backuppc

you will be at a '$' prompt. type:
> bash
to get to a normal prompt.

now, to run your command.
first, you need to stop backuppc:
> sudo /etc/init.d/backuppc stop
<enter password if asked>

next, you just need to type the command out:
> /usr/share/backuppc/bin/BackupPC_compPool

restart backuppc
> sudo /etc/init.d/backuppc start
done

NOTE: you cannot have any Pools compressed to do this, so set your compression to on in the config file FIRST, then do this right after.  otherwise you wont be able to compress the older un-compressed files.  on the bright side, they will eventually expire and get deleted!

hope it helps

---

