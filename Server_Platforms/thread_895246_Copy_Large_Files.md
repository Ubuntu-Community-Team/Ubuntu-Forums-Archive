---
title: "Copy Large Files"
date: 2008-08-20
forum: Server Platforms
---

### Post by mohadib on 2008-08-20
Hello,

I have a server that seems to use about 10-16 gigs of ram on average. When I try to copy a large file (162G) all the free ram is cached, then *all* of the swap is eaten up. I have swappiness set to 0 in the kernel. I have used dd to copy files, this does not eat all the ram or use any swap. But dd doesnt do directories. Can anyone help me figure out the issue here, or maybe suggest another application/command for copying large files.

Thanks,
dib

```
 root@dbserver:/share# free -m
             total       used       free     shared    buffers     cached
Mem:         24090      23964        126          0         18      23338
-/+ buffers/cache:        606      23484
Swap:         1945       1945          0

Filesystem            Size  Used Avail Use% Mounted on
/dev/md2              1.4T  981G  323G  76% /
tmpfs                  12G     0   12G   0% /lib/init/rw
udev                   10M   92K   10M   1% /dev
tmpfs                  12G  9.3G  2.8G  77% /dev/shm
/dev/md0              471M   23M  424M   6% /boot
```

---

### Post by cariboo on 2008-08-20
What program are you using to transfer files and how are you sharing directories?

Jim

---

### Post by mohadib on 2008-08-20
I have tried cp,cpio, and rsync. This happens when I move files around localy on ext3, also happens with samba shares, basically thats all I have tried.

Thanks,
dib

---

### Post by windependence on 2008-08-20
Try wget, but you have to understand that the Linux memory model is much different than Windoze. Linux will use ALL your memory and will keep files cached until more memory is needed, when it will discard old files, and load the new ones. This results in less disk usage. Don't freak out when you see this.

-Tim

---

### Post by Ximbiot on 2008-08-20
> **windependence said:**
> Try wget, but you have to understand that the Linux memory model is much different than Windoze. Linux will use ALL your memory and will keep files cached until more memory is needed, when it will discard old files, and load the new ones. This results in less disk usage. Don't freak out when you see this.

It's a feature, not a bug!  :)

Seriously.  Run a large copy twice in a row and the second time it should run much faster.

---

### Post by mohadib on 2008-08-20
Um... using up all my ram and every last bit of swap is hardly a feature. This causes the box to be slow. If Linux worked as expected, and released the cached ram when I needed it , I would have no problem. But thats not the case. With a box with 24 gigs of ram, and actually using about a gig, there is NO reason to swap, much less eat up ALL the swap. Any thoughts on fixing this? Because this is absoluetly broken. I understand file caching and how its supposed to work, so please lets not discuss it. Maybe lets discuss how it and swappines are broken.

thanks
dib

---

### Post by Ximbiot on 2008-08-20
> **mohadib said:**
> Um... using up all my ram and every last bit of swap is hardly a feature. This causes the box to be slow. If Linux worked as expected, and released the cached ram when I needed it , I would have no problem. But thats not the case.

This is how I have experienced the file cache working and it works fine for me.  My apologies for misunderstanding your problem.  I've never seen anything like it before and I'm surprised that so many copy programs are holding so much of your files in memory just to copy them.  In particular, I would have expected rsync to be optimized to transfer only a chunk at a time and I'm fairly certain that I've copied files larger than my own available memory using various means under Linux without a problem.

You could try rdist too.  That's the only other program that comes to mind for recursive copies.  If you know dd works for you, you could try something baroque like the following thrown-together and untested script, as well:

```
#! /bin/sh

ORIGWD=`pwd`
SOURCE=$1

# Correct for potentially relative $DEST
DEST=$2
cd $DEST
DEST=`pwd`
cd $ORIGWD

cd "$SOURCE"
find . -type d -exec mkdir -fp "$DEST/{}" \;
find . -type f -exec dd if={} of="$DEST/{}" \;
```

---

### Post by mohadib on 2008-08-20
Thanks for the suggestions :) I thought about making due with dd, and I still can I guess, instead of using smbget I could just mount the partitions. I'll give this a go and see how it works. Though I really wish I could just stop eating all the swap space and use traditional tools for copying directory structures.

Is it common for a box to use a lot (All) of the swap partition when lots of cached ram is available?

Thanks,
dib

---

### Post by Joeb454 on 2008-08-20
Well if you're transferring a 162 Gigabyte file then yes it wouldn't surprise me in the slightest for that to happen :)

---

### Post by Ximbiot on 2008-08-20
> **Joeb454 said:**
> Well if you're transferring a 162 Gigabyte file then yes it wouldn't surprise me in the slightest for that to happen :)

Why?  I would have expected even cp to be smart enough to use reasonably sized chunks and stop reading and wait until its output buffer stopped blocking a write.

Why would a 162GB file with 24GB RAM and 2GB swap be any different than copying a 16GB file with 1GB RAM and 3GB swap?  I've accomplished the latter without difficulty.

On a side note, the usual recommendation I have come across is to have twice as much swap as you have memory.  Don't know if the kernel would be making any assumptions to that effect that might affect your server, though I would hope it wouldn't cause problems, especially with 24GB of RAM available.

---

### Post by fjgaude on 2008-08-20
Wow, a 162GB file... that's big! I wonder if the Linux folks have tested such to make sure all the pieces work correctly?

It might be time to report a bug, eh?

---

### Post by windependence on 2008-08-20
> **mohadib said:**
> Um... using up all my ram and every last bit of swap is hardly a feature. This causes the box to be slow. If Linux worked as expected, and released the cached ram when I needed it , I would have no problem. But thats not the case. With a box with 24 gigs of ram, and actually using about a gig, there is NO reason to swap, much less eat up ALL the swap. Any thoughts on fixing this? Because this is absoluetly broken. I understand file caching and how its supposed to work, so please lets not discuss it. Maybe lets discuss how it and swappines are broken.

thanks
dib

Well in your OP you didn't mention it was slowing down your box but this may indeed be normal behavior as AFAIK there is no throttling of the transfer so the box will use whatever resources there are and transfer it as fast as it can. You could try renicing the process while it was going. 

Let me ask you, is the connection Gigabit ethernet?

-Tim

---

### Post by HermanAB on 2008-08-20
Rsync has a bandwidth parameter.  That should help.

Cheers,

Herman

---

### Post by mohadib on 2008-08-21
Hello, 
 Thanks for all the replies. All the boxes are on a gigabit network.

---

### Post by mohadib on 2008-08-21
Hmm, dd can't seem to copy from a smb mounted drive. Now I'm basically back at square 1. So, if all of my swap file is full does that mean other programs will not have room to swap, or will it also be "cleaned" as needed?

Thanks,
dib

---

### Post by windependence on 2008-08-22
How big is your swap file?

There are two schools of thought on this. I like to create a swap file even though I run a large amount of RAM. I have no concrete proof, but I think my systems are faster that way. Other people advocate turning off swap completely and just use RAM. I dunno, results are mixed at best. Theoretically, your system should give back RAM when it's needed and cache the newer stuff. Personally, I think there is some other issue going on here but I haven't figured out what it is yet.

-Tim

-Tim

---

