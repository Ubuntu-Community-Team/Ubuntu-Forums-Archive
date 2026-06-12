---
title: "Securely deleting data"
date: 2011-04-22
forum: Security
---

### Post by blananaka on 2011-04-22
If i pop in a live cd with swap disabled what commands would i use to securely erase the data-i really dont dont the command line that well so will somebody please type out the command for me here? 

Is there a difference between the methods used eg between the use of secure delete and shred? 

What is the minimum erasing hard drives need to make sure the data is forensically unrecoverable? Is there any point in going beyond 3 or 7 passes per drive? should i got for the full gutmann 35 pass system?

---

### Post by stealth. on 2011-04-22
> **blananaka said:**
> If i pop in a live cd with swap disabled what commands would i use to securely erase the data-i really dont dont the command line that well so will somebody please type out the command for me here? 

Is there a difference between the methods used eg between the use of secure delete and shred? 

What is the minimum erasing hard drives need to make sure the data is forensically unrecoverable? Is there any point in going beyond 3 or 7 passes per drive? should i got for the full gutmann 35 pass system?

I don't know about shred, but srm (secure-delete) uses a 38 pass method. You might have to connect to the internet and "sudo apt-get install secure-delete" then run it from there. 

If your really worried just nuke the HDD with DBAN.

And if your *really *paranoid like me, how do you even know they work in the first place, and its not just some gimmick to make you believe its really deleting it.

---

### Post by rookcifer on 2011-04-22
OP, it depends on what it is you want to erase.  If it's an entire disk, then do this:

```
sudo dd if=/dev/zero of=/dev/sda
```

where sda is the disk you want to wipe.  It might be sdb or sdc, etc.  Just be sure you are wiping the right disk.

If you want to wipe an individual file, then you should use shred.    

```
shred -fuv filename
```

If you want to wipe the "free space" of a drive, then again, use dd.   First navigate to the disk where you want to wipe free space, then execute this command:

```
sudo dd if=/dev/zero of=ZERO_FILE
```

This command will make a file and fill it with zeros until the disk is full.  Once it finishes, then you merely remove the file like so:

```

sudo rm ZERO_FILE
```

---

### Post by blananaka on 2011-04-22
Yes basically i will use a live cd with swap disbabled and open up the program 'disk utility'. There i want to erase all detected drives-hard drives, swap space and ram if i can see that-any drive that i can see via disk quantity. 

This command   
sudo dd if=/dev/zero of=/dev/sda

how many times does this erase something? what does this command actually do? Is this command available on a live cd without internet access? 

i really need a command to just destroy any data left there on the drives so that forensically speaking nothing can be found....anyone know that command?

---

### Post by iissmart on 2011-04-22
[http://www.dban.org/](http://www.dban.org/)

Darik's Boot And Nuke is what you want. Burn to a live cd, select which hard drive and which erase method you want, and it does the rest. No command line needed.

I would at a minimum do the full US DoD method (7 passes). Anything higher seems like overkill, and anything lower and the government can get to it ;)

---

### Post by blananaka on 2011-04-22
dban wont work for me

so this command 
sudo dd if=/dev/zero of=/dev/sda

will zero out a drive yes? what does that mean? how many times will this command overwrite my data? 

can someone offer a more intensive command for secure erasure?

---

### Post by wojox on 2011-04-22
Yes that uses 0's. Why doesn't DBAN work?

Their is also:

```
shred -vfz -n 100 /dev/sda 
```

The 100 is 100 times. Adjust accordingly.

---

### Post by iissmart on 2011-04-22
> **blananaka said:**
> can someone offer a more intensive command for secure erasure?

> **wojox said:**
> Why doesn't DBAN work?

+1. Also,

```
sudo dd if=/dev/urandom of=/dev/sda
```

Writing random bytes is better than writing all zeros, but it takes longer.

---

### Post by rookcifer on 2011-04-22
> **blananaka said:**
> how many times does this erase something? 

One time, which is all that is needed to make data totally unrecoverable.

> what does this command actually do? Is this command available on a live cd without internet access? 

It overwrites the disk with zeros.  It is available on a LiveCD and doesn't need a network connection.

> i really need a command to just destroy any data left there on the drives so that forensically speaking nothing can be found....anyone know that command?

The command I gave will do that.

---

### Post by iissmart on 2011-04-22
Um...sorry, but that is just incorrect. Writing one pass of 0's over the drive won't do much. You need to write random bytes, at least three passes, to obfuscate it enough that if someone tries to recover, it wont be obvious.

I'd look into the various secure wipe methods, especially what the DoD secure wipe method does on each pass, and make a judgement call on your own. Personally, I'd do the DoD 7 pass full wipe.

---

### Post by dacoolio on 2011-04-23
I actually wrote an article about this on my website. Basically, what I do is overwrite the drive using dd with /dev/urandom, which is the pseudorandom number generator. I do this 7 times, which pretty much wipes the drive.

dd if=/dev/urandom of=/dev/--- bs=512


Of course, if it REALLY needs to be wiped, you could rent a de-gausser which permanently wipes the disk to the point where the manufacturer would have to upload firmware back onto the drive so the head could convert digital memory addresses into the respective physical address in inches and such.

---

### Post by rookcifer on 2011-04-23
> **iissmart said:**
> Um...sorry, but that is just incorrect. Writing one pass of 0's over the drive won't do much. You need to write random bytes, at least three passes, to obfuscate it enough that if someone tries to recover, it wont be obvious.

Who cares if it's obvious?  And who said one must use at least 3 passes?  [Research has shown]("http://books.google.com/books?id=qji1ilg2-pAC&pg=PA243#v=onepage&q&f=false") that even after one pass data cannot be recovered even when using MFM's.

> I'd look into the various secure wipe methods, especially what the DoD secure wipe method does on each pass, and make a judgement call on your own. Personally, I'd do the DoD 7 pass full wipe.

Can you point me to the DoD document that says one must use 7 passes?  I think you'll find such a document doesn't exist.  Most people reference DoD 5220.22-M, but they obviously have not read it.  Nowhere in that document does it mention 7 passes.  It doesn't even mention anything about how to overwrite magnetic media!

There is another document called "Unclassified Computer Hard Drive Disposition" from the DoD which does give advice, but it only mentions 3 passes (not 7).  And that document is older than the 5220.22-M (which does not provide any techniques).

[From Wikipedia:]("https://secure.wikimedia.org/wikipedia/en/wiki/Data_erasure#cite_note-12")

> According to the 2006 NIST Special Publication 800-88 Section 2.3 (p. 6): "Basically the change in track density and the related changes in the storage medium have created a situation where the acts of clearing and purging the media have converged. That is, for ATA disk drives manufactured after 2001 (over 15GB) **clearing by overwriting the media once is adequate to protect the media from both keyboard and laboratory attack."**[11]

According to the 2006 CMRR Tutorial on Disk Drive Data Sanitization Document (p. 8): "Secure erase does a single on-track erasure of the data on the disk drive. The U.S. **National Security Agency** published an Information Assurance Approval of single pass overwrite, after technical testing at CMRR **showed that multiple on-track overwrite passes gave no additional erasure.**"[22] "Secure erase" is a utility built into modern ATA hard drives that overwrites all data on a disk, including remapped (error) sectors.

Further analysis by Wright et al. seems to also indicate that one overwrite is all that is generally required.[2

So, you have NIST, NSA and independent researchers all saying that data cannot be recovered after one overwrite.  I would take their advice over that of a non-existent DoD document.

---

### Post by HermanAB on 2011-04-23
Well, pretty much everything in this thread is plain wrong.

First you have to determine what is your threat.  If your threat is your little kid sister, then just erase the file with rm.  If the threat is your hacker buddy, then overwrite the disk with dd and urandom.  If the threat is a national government with unlimited resources, then you have to shred the disk in a metal shredder or melt it in a blast furnace.

The DoD multi-pass overwrite nonsense is mostly a myth.

The DoD basically requires that if a magnetic disk will be re-used at the same or higher classification level, then it is recommended (but not required) that you overwrite the disk three times.  It is not allowed to re-use the disk at a lower classification level.  If a disk is to be decommissioned, then it must be physically destroyed.  Further, the DoD requires that all portable devices should use 'whole disk encryption' to guard against casual inspection.

---

### Post by stealth. on 2011-04-23
Btw I've used DBAN with the Gutmann method. It took around 3 days for it to finish. It runs your computer at full speed, so make sure it will stay cool.

---

