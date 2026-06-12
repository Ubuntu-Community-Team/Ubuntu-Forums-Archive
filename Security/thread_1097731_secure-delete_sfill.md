---
title: "secure-delete sfill"
date: 2009-03-16
forum: Security
---

### Post by zaphodbblx on 2009-03-16
Ok ive gotten secure-delete to wipe the free space in my home folder...I think!
I do this: 

sudo  sfill -v / home

I get this message:


Using /dev/urandom for random input.
Wipe mode is secure (38 special passes)
Wiping now ...
Creating /oooooooo.ooo ... 

and then nothing else happens(?) I never get "wipe complete" or any kind of finish message
did it work? how do I tell?

How would I  wipe the whole disks free space (ie what do I imput here sfill -v / ******** )
yes I know I have to be root....
is there a GUI type program that works with linux? its just all kinda vague for me in the terminal :D

---

### Post by cdenley on 2009-03-16
How long did you wait for it to complete? Were you returned to a shell prompt? Keep in mind that overwriting all your free space 38 times will take a very, very long time depending on your system and free space. Unless you configured your system for an advanced partitioning scheme, your home directory probably resides on your root filesystem. Filesystems have free space, not directories.

---

### Post by hyper_ch on 2009-03-16
this will take very, very, very long...

---

### Post by zaphodbblx on 2009-03-16
cdenly:   yes I was returned to the shell prompt
hyper_ch:    my system was setup with the default install from disk(8.04) ....so if I do / home that would effectively be the whole disk? any idea how long for a 320 gb disk..24 hr? longer?
its not really an **issue** I just like knowing what im doing and how I'm getting it done!
thanks all!:KS

---

### Post by HermanAB on 2009-03-17
Note that overwriting data multiple times isn't really any better than overwriting it once only.

There are a number of dud programs with oodles of posts on these forums:
rkhunter, shred and fail2ban

Those are best avoided.  I have no idea why they are so popular but I guess it is because many users prefer to learn the hard way.

Oh, well, what the hell...

Herman

---

### Post by hyper_ch on 2009-03-17
> **zaphodbblx said:**
> so if I do / home that would effectively be the whole disk? any idea how long for a 320 gb disk..24 hr? longer?

Just from one of my earlier howtos:

> hyper@xubi:/dev$ sudo dd if=/dev/urandom of=/dev/hda
dd: writing to `/dev/hda': No space left on device
312581809+0 records in
312581808+0 records out
160041885696 bytes (160 GB) copied, 90679.8 seconds, 1.8 MB/s

It was an IDE device back then.

But what are you trying to do exactely?

---

### Post by zaphodbblx on 2009-03-17
just wipe my drives free space. its really just an exercize to see if I can figure it out...

---

### Post by sefs on 2011-05-10
> **zaphodbblx said:**
> just wipe my drives free space. its really just an exercize to see if I can figure it out...

Were you successful?

---

### Post by rookcifer on 2011-05-10
> **zaphodbblx said:**
> just wipe my drives free space. its really just an exercize to see if I can figure it out...

To wipe the free space of a drive, cd into the partition you want to wipe.  Let's say it's /home:

```
cd /home
```

Then run this:

```
dd if=/dev/urandom of=WIPE_FILE
```

Let it run.  You can check the "WIPE_FILE" every so often to see how large it is.  For instance, in Nautilus, just click on the file and hit the refresh button every so often.

Once the file takes up all the disk space, dd will stop running automatically.  You will probably get a warning that disk space is low.  That's OK, just ignore it as this means the partition/directory was wiped.  Now all you have to do is remove WIPE_FILE:

```
rm WIPE_FILE
```

---

### Post by BkkBonanza on 2011-05-11
sfill should also work fine. I've used it many times but I always use **sfill -fllz /** as writing 38 times is a ridiculous waste fo time. It works well enough writing zeros in one pass, but that can also be done as noted above using /dev/zero as input. It's all pretty much the same: fill a file until disk is full and then remove the file, freeing up the space again. Even one pass with zeros can take quite a while.

---

### Post by dargaud on 2011-05-11
> **rookcifer said:**
> Let it run.  You can check the "WIPE_FILE" every so often to see how large it is.  For instance, in Nautilus, just click on the file and hit the refresh button every so often.

A little trick: while dd is running, you can send it USR1 from another terminal and it will tell you what it's been doing:
```
$ dd if=/dev/zero of=WIPE_FILE &
$ killall -USR1 dd
1655968+0 records in
1655968+0 records out
847855616 bytes (848 MB) copied, 9.10357 s, 93.1 MB/s
```

---

### Post by Irihapeti on 2011-05-12
> **rookcifer said:**
> To wipe the free space of a drive, cd into the partition you want to wipe.  Let's say it's /home:

```
cd /home
```

Then run this:

```
dd if=/dev/urandom of=WIPE_FILE
```

Let it run.  You can check the "WIPE_FILE" every so often to see how large it is.  For instance, in Nautilus, just click on the file and hit the refresh button every so often.

Once the file takes up all the disk space, dd will stop running automatically.  You will probably get a warning that disk space is low.  That's OK, just ignore it as this means the partition/directory was wiped.  Now all you have to do is remove WIPE_FILE:

```
rm WIPE_FILE
```

Here's a humorous version of the same idea:

[http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/](http://www.marksanborn.net/howto/rick-rolling-your-hard-drive/)

Actually, you can use any file you like as the input.

---

### Post by sefs on 2011-05-16
> **BkkBonanza said:**
> ... as writing 38 times is a ridiculous waste fo time ..

You can say that again lol.  I tried the 38 past with 1.6 GB and it took a day.  Wow.  No way I am doing that again.  I'll take the 1 or 2 pass with sfill or dd.

---

### Post by tubbygweilo on 2011-05-16
Not much good against a no knock warrant but then not too much is.

---

### Post by bodhi.zazen on 2011-05-16
Thread closed.

This is an old thread from 2009. Since this thread was started the gutmann theory has been debunked.

[http://www.nber.org/sys-admin/overwritten-data-gutmann.html](http://www.nber.org/sys-admin/overwritten-data-gutmann.html)

One pass with dd is sufficient. More then one pass is excessive wear on the hard drive.

---

