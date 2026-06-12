---
title: "Hdd mout fail"
date: 2013-05-14
forum: Server Platforms
---

### Post by icedragon34 on 2013-05-14
mountall: Did not receive a reply. Possible causes include: the remote applicati   on did not send a reply, the message bus security policy blocked the reply, the    reply timeout expired, or the network connection was broken.
mountall: Connection is closed
fsck from util-linux 2.20.1
mountall: Connection is closed
Usage: fsck.ext3 [-panyrcdfvtDFV] [-b superblock] [-B blocksize]
                [-I inode_buffer_blocks] [-P process_inode_size]
                [-l|-L bad_blocks_file] [-C fd] [-j external_journal]
                [-E extended-options] device

Emergency help:
 -p                   Automatic repair (no questions)
 -n                   Make no changes to the filesystem
 -y                   Assume "yes" to all questions
 -c                   Check for bad blocks and add them to the badblock list
 -f                   Force checking even if filesystem is marked clean
 -v                   Be verbose
 -b superblock        Use alternative superblock
 -B blocksize         Force blocksize when looking for superblock
 -j external_journal  Set location of the external journal
 -l bad_blocks_file   Add to badblocks list
 -L bad_blocks_file   Set badblocks list
mountall: fsck /samba [2141] terminated with status 16
mountall: Unrecoverable fsck error: /samba
mountall: Skipping mounting /samba since Plymouth is not available
mountall: Disconnected from Upstart

that was after attempting mountall just happened after restarting the server. Need help quickly

I checked everything and found a solution for now anyways, as far as I know what had happened was when I tried to change the mount before restarting It failed to change and then I restarted it causing it to have a bad mount location and I just remounted it on the old directory and I will live with it for now.

---

