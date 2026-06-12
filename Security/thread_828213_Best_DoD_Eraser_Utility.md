---
title: "Best DoD Eraser Utility?"
date: 2008-06-13
forum: Security
---

### Post by yizuman on 2008-06-13
I'm looking for a software that runs with Ubuntu 7.10 that can "clean" erase any data that had been deleted or can do a DoD Erase a file on the spot as it is being deleted.

Anyone know of such a program?

Thanks in advance,

Yiz

---

### Post by cdenley on 2008-06-13
```

sudo apt-get install secure-delete
man srm
man sfill

```

---

### Post by KingTermite on 2008-06-13
I believe the built in "shred" command can do that...and I believe it is DoD compliant as well.

---

### Post by cdenley on 2008-06-13
I think DoD compliance is sort of a myth. There is no specific method in the standard to comply with for erasing data. The shred command is basically the same as srm. The difference is shred does 25 passes with random data where srm does "27 passes with special values defined by Peter Gutmann" in between 10 passes of random data.

---

### Post by HermanAB on 2008-06-13
Sigh, there is no such thing as a DoD erase utility.  It is not possible to completely erase data off a disk using ordinary erase commands, no matter how many times you try to overwrite it.  One reason being the log structure of modern file systems.

The only way to permanently erase data, is to ensure that all data on the disk is encrypted and then when you wish to erase it, simply forget the key.

However, the next best method to erase a disk is by using a utility built into the drive controller:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

All other erase methods are simply snake oil.

Cheers,

Herman

---

### Post by bla on 2008-06-15
> It is not possible to completely erase data off a disk using ordinary erase commands, no matter how many times you try to overwrite it.

If you say so.  haha
Nice to know I have unlimited storage space on any HD. If I knew this before I would have never bough more than 1 HD.

---

### Post by /etc/init.d/ on 2008-06-16
> **bla said:**
> If you say so.  haha
Nice to know I have unlimited storage space on any HD. If I knew this before I would have never bough more than 1 HD.
I first heard a comment like that on Slashdot, and it made me smile, and is also completely true.

For those who don't get it.  If it is not possible to ever overwrite data on magnetic media, then it would be theoretically possible to create a drive with unlimited storage space.  The idea being when the drive gets full, you delete something and write over it.  Then you have the new data, but if you want the old data, you just use this magical recovery technique that everyone witters about to get the overwritten data back.  Since these people claim that the magnetic media remembers infinite levels of overwrites, you now have infinite storage space.

Take that, FUD'ers.

---

### Post by cdenley on 2008-06-16
It is theoretically possible to retrieve data which has been overwritten using an electron microscope and some complicated math formulas. However, I don't think this has been demonstrated to successfully recover a file that has been overwritten multiple times with random data. Overwriting with anything besides an enhanced secure erase with hdparm or the tool linked by HermanAB would leave you vulnerable to previously used sectors which have been marked as bad. After overwriting data once, it is impossible to recover without removing and analyzing the platters.

---

### Post by Woei on 2008-06-16
> **yizuman said:**
> I'm looking for a software that runs with Ubuntu 7.10 that can "clean" erase any data that had been deleted or can do a DoD Erase a file on the spot as it is being deleted.

Anyone know of such a program?

Thanks in advance,

Yiz

Boot from some live-cd, determine what the device name of the hard drive you want to erase is, and issue something like the following:

```

i=0
while [ $i -lt 30 ];
do
  dd if=/dev/random of=/dev/sda;
  i=$(($i+1));
done

```

Note that this scribbles over your entire harddisk, *destroying all data*. Depending on how the kernel on the live-cd you booted from is configured to gather its entropy, this may take a *very long* time, and it might not even complete if there's nothing to feed the entropy pool (e.g. you typing on the keyboard, moving your mouse, generating interrupts, etc). You might as well use /dev/urandom, which uses a pseudo random number generator, which should be good enough. If you think it doesn't and you can't wait, then your only recourse would be to burn the harddrive.

---

### Post by cdenley on 2008-06-16
> **Woei said:**
> Boot from some live-cd, determine what the device name of the hard drive you want to erase is, and issue something like the following:

```

i=0
while [ $i -lt 30 ];
do
  dd if=/dev/random of=/dev/sda;
  i=$(($i+1));
done

```

Note that this scribbles over your entire harddisk, *destroying all data*. Depending on how the kernel on the live-cd you booted from is configured to gather its entropy, this may take a *very long* time, and it might not even complete if there's nothing to feed the entropy pool (e.g. you typing on the keyboard, moving your mouse, generating interrupts, etc). You might as well use /dev/urandom, which uses a pseudo random number generator, which should be good enough. If you think it doesn't and you can't wait, then your only recourse would be to burn the harddrive.

That's the same as shred
```

shred -n 30 --random-source=/dev/random /dev/sda

```

---

### Post by /etc/init.d/ on 2008-06-16
> **Woei said:**
> ```

i=0
while [ $i -lt 30 ];
do
  dd if=/dev/random of=/dev/sda;
  i=$(($i+1));
done

```

You're joking right?  With a good amount of mouse and keyboard input, I got about 11 kilobytes of data from /dev/random in one hour.  So, for a 50 gigabyte hard drive, that's about 543 years, and 30 passes would mean 16,290 years.  Again, assuming constant keyboard and mouse input.

---

### Post by Pepse3 on 2008-06-17
So, after reading these posts am I to assume that back in the late '90's when Maxtor had me download a small file to a 3 1/2 floppy called Zero Fill it really didn't do anything?  As they told me it would fill in ALL areas of my hard drive with zeros; hence returning it to factory "clean".  Mind you about a year or two later I bought a brand new Western Digital hard drive and it came with a floppy that did an erase similar to Maxtor's.  But about a year or so later I had bought another new WD hdd and that utility was no longer on the floppy.  Seagate also had a similar program for a short while.  I wish I had those floppies now.  I know there is/was a company that sold such software but it was around $450 USD and that was about 5 years ago.  Unless these were "snake oil products" from the manufacturer I beg to differ from those claiming "hog wash".

Later. Pepse.

---

### Post by gmendoza on 2008-06-17
For anyone that actually wants to read up on the matter, there's some interesting information by Peter Gutmann that's been floating around for years.

[http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html)
[http://www.cypherpunks.to/~peter/usenix01.pdf](http://www.cypherpunks.to/~peter/usenix01.pdf)

DBAN is a popular project that is quite useful, and has a decent FAQ you should check out.

[http://dban.sourceforge.net](http://dban.sourceforge.net)

As someone mentioned previously, your best off starting off with a blank hard disk and encrypting the entire volume right from the start.  But remember, at some point you have to store the keys in memory where there are similar vulnerabilities.  There's no perfect solution, but the goal is simply to create as much distance as you can between what is "possible" and what is "probable".

So... "secure" wipe the entire disk whenever you can... encrypt when and how it's appropriate... but don't bet your life on any of it.  :-)

---

### Post by /etc/init.d/ on 2008-06-17
> **gmendoza said:**
> For anyone that actually wants to read up on the matter, there's some interesting information by Peter Gutmann that's been floating around for years.

[http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/secure_del.html)
[http://www.cypherpunks.to/~peter/usenix01.pdf](http://www.cypherpunks.to/~peter/usenix01.pdf)
While I agree with all of your points, Gutmann's paper is irrelevant today.  He (vaguely) described a purely theoretical attack that has never been publicly demonstrated and was written in the day when hard drives used completely different signal technologies (RLL/MFM) and the areal density was several orders of magnitude smaller than what we have today.

In fact, Gutmann has pretty much rebuked his own paper in years since.

---

### Post by cdenley on 2008-06-17
> **Pepse3 said:**
> So, after reading these posts am I to assume that back in the late '90's when Maxtor had me download a small file to a 3 1/2 floppy called Zero Fill it really didn't do anything?  As they told me it would fill in ALL areas of my hard drive with zeros; hence returning it to factory "clean".  Mind you about a year or two later I bought a brand new Western Digital hard drive and it came with a floppy that did an erase similar to Maxtor's.  But about a year or so later I had bought another new WD hdd and that utility was no longer on the floppy.  Seagate also had a similar program for a short while.  I wish I had those floppies now.  I know there is/was a company that sold such software but it was around $450 USD and that was about 5 years ago.  Unless these were "snake oil products" from the manufacturer I beg to differ from those claiming "hog wash".

Later. Pepse.

You can zero fill with a simple linux command
```

sudo dd if=/dev/zero of=/dev/sda

```
This would stop 99.9% of people from recovering any data. If you want that number to approach 100%, then use any tool which implements the "enhanced secure erase" function built-in to the drives firmware. Older drives didn't include this function. I'm not sure when it was implemented. I'm sure there are/were products sold which started the "enhanced secure erase" function, even though the same thing can be accomplished with free tools. Probably most tools just filled the disk with zeros or random data with multiple passes. The "enhanced secure erase" is better because it erases with a track offset to erase the track edges, and erases sectors which can no longer be accessed by any software since they may have been written to previously before being marked as "bad". The "enhanced secure erase" function nearly eliminates the possibility of any data recovery, but anything is possible.

If the tools came from the drive manufacturer, it probably would have used the "secure erase" or "enhanced secure erase" functions in the drives firmware, if they were used at the time.

---

### Post by gmendoza on 2008-06-17
> **/etc/init.d/ said:**
> 
In fact, Gutmann has pretty much rebuked his own paper in years since.

An most excellent point, indeed.

---

### Post by HermanAB on 2008-06-17
Note that if you really want to overwrite something with random numbers, then you should use /dev/urandom, since it is a helluvalot faster than /dev/random.

Eg:
dd if=/dev/urandom of=sdd bs=100K

---

### Post by John M2009 on 2009-06-24
> **cdenley said:**
> You can zero fill with a simple linux command
```

sudo dd if=/dev/zero of=/dev/sda

```This would stop 99.9% of people from recovering any data. If you want that number to approach 100%, then use any tool which implements the "enhanced secure erase" function built-in to the drives firmware. Older drives didn't include this function. I'm not sure when it was implemented. I'm sure there are/were products sold which started the "enhanced secure erase" function, even though the same thing can be accomplished with free tools. Probably most tools just filled the disk with zeros or random data with multiple passes. The "enhanced secure erase" is better because it erases with a track offset to erase the track edges, and erases sectors which can no longer be accessed by any software since they may have been written to previously before being marked as "bad". The "enhanced secure erase" function nearly eliminates the possibility of any data recovery, but anything is possible.

If the tools came from the drive manufacturer, it probably would have used the "secure erase" or "enhanced secure erase" functions in the drives firmware, if they were used at the time.


Does this command actually wipe the WHOLE disk,  or just fill the free space,  as I am also looking for a simple eraser program which will just fill the free disk space.

---

### Post by cdenley on 2009-06-24
> **John M2009 said:**
> Does this command actually wipe the WHOLE disk,  or just fill the free space,  as I am also looking for a simple eraser program which will just fill the free disk space.

```

sudo apt-get install secure-delete
man sfill

```

---

### Post by John M2009 on 2009-06-24
> **cdenley said:**
> ```

sudo apt-get install secure-delete
man sfill

```


Thanks :)

---

### Post by rookcifer on 2009-06-24
> **cdenley said:**
> It is theoretically possible to retrieve data which has been overwritten using an electron microscope and some complicated math formulas. 

[No it's not.]("http://sansforensics.wordpress.com/2009/01/15/overwriting-hard-drive-data/")

---

### Post by HermanAB on 2009-06-25
I think this thread needs to be erased with the Mythical DoD Eraser.
;)

---

