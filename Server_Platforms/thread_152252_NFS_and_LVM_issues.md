---
title: "NFS and LVM issues"
date: 2006-03-29
forum: Server Platforms
---

### Post by Giancarlo on 2006-03-29
Hi,

I setup a server using Breezy Badger.  I'm using LVM sitting on a RAID-5 array and created several volumes, all using reiserfs.  They're all mounted to a directory off root called /netshare, so I have, for instance

[INDENT]
/dev/mapper/vg00-common on /netshare/common type reiserfs (rw)
/dev/mapper/vg00-music on /netshare/music type reiserfs (rw)
/dev/mapper/vg00-pictures on /netshare/pictures type reiserfs (rw)
[/INDENT]

I'm exporting /netshare (tried various /etc/exports combinations including
/netshare      192.168.123.0/255.255.255.0(rw,no_root_squash,no_all_squash,sync)
my current setting is **/netshare       192.168.123.0/255.255.255.0(rw,sync,no_subtree_check)**

and can see the directories from my client, but I don't see the content of the directories, can't create files, etc.  I assumed it was something with permissions and gave access to everything, verified that the user and group ids between the client and server match, etc., and was about to throw in the towel.

Then, on the server, I created a directory in /nesthare (/netshare/test), copied some files from the /netshare/common directory that I can't see from the client, and then checked things out.  Now, I can see those /netshare/test files on the NFS mount from my client, I can create files, etc.  

Thinking maybe I screwed the permissions up, I did a chown -R --reference=/netshare/test /netshare/common (and the same syntax for chgrp and chmod) figuring I'd set them to something I knew was working.  No dice.

Back to google, I found some hits that suggested there were (are?) issues with some combination of reiserfs and NFS and/or LVM, so I created another volume as ext3

/dev/mapper/vg00-NonReiser on /netshare/NonReiser type ext3 (rw)

Couldn't see or do anything in this one from the client either.  Just for sanity's sake, I created another non-LVM directory in /netshare, and that one I can work with from the client.

So I'm left with the conclusion that either I'm on crack or there's something up with NFS and LVM.  Does anybody have this configuration working, and if so, how'd you get it that way!?  Are there mount or nfs options I should be aware of?  Any other ideas??  

I'd say I'm not much more than a Linux newbie but I tried to do as much googling, man page reading, etc. before posting and hope someone can help out.

TIA!

---

