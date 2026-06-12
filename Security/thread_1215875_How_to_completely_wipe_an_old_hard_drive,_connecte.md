---
title: "How to completely wipe an old hard drive, connected to Ubuntu via USB"
date: 2009-07-17
forum: Security
---

### Post by tomreid on 2009-07-17
Hi, It's a long story, but I have an old hard drive recovered from a Mac that is now connected, via a USB enclosure, to my Ubuntu machine. 

I have checked out:

[http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html](http://linuxhelp.blogspot.com/2006/06/how-to-securely-erase-hard-disk-before.html)

and also DBAN looks like a good tool, but all the solutions I've seen seem to be tailored for a situation where you are erasing the data from the the main hard drive of the machine you are working on, which is the last thing I want to do. 

Can anyone help me adapt one of these solutions to wipe the old HD I now have connected via USB?

cheers

---

### Post by lykwydchykyn on 2009-07-17
I generally use shred for things like that.  I think it's installed by default.

If the drive you want to wipe is /dev/sdb, then the command would look like this:
```

sudo shred -vzn 1 /dev/sdb

```

MAKE SURE THE DRIVE IS SDB -- this can wipe out your system if you type the wrong thing!

The other option that works (albeit slowly --but with less risk of destroying a drive if you type the wrong thing) is using qemu with the dban iso:
```

sudo qemu -hda /dev/sdb -cdrom dban.iso -boot d

```

---

### Post by aesis05401 on 2009-07-17
+1 shred.  'man shred' for usage. 

The main issue is making sure you know the device designation for the external.  Provided you do:
```

sudo shred -vfz -n xxx /dev/yyy

```

where 'xxx'= numder of overwrites, and 'yyy'=the device name of the external you are fine. 

The only way to mess up would be to make 'yyy'=your internal drive.

Does this make sense?

Edit: Aha, I have been beaten to the punch.  Good luck!
Edit2: Use 'f' in your options to auto change perms on device to be destroyed.

---

### Post by grayn0de on 2009-07-17
Check out shred. It might be of use, here. See link, below.

[http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

---

### Post by tomreid on 2009-07-18
Thanks guys, one more question - how do I easily determine the path and the designation of the external drive?


cheers

---

### Post by bodhi.zazen on 2009-07-18
> **tomreid said:**
> Thanks guys, one more question - how do I easily determine the path and the designation of the external drive?


cheers

```
sudo fisdk -l
```

Or with gparted .

See also : [HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning")

---

### Post by tomreid on 2009-07-19
Hi

One question, if anyone is still able to help me. 

I ran the sudo shred commands above, it seems to be working, but how do I know when it is finished?

The terminal was outputing lines of text for a while, but now it seems to have stopped and the data is still on the hard drive.
It may still be working but the terminal is not telling me what it is doing.

Thanks

---

### Post by Dave_Connor on 2009-07-20
The files are there but the data should be overwritten and the contents of the data should be gone. Shred also has a delete command after data whipe. ```
man shred
``` in a terminal will help you out more in shred's syntax.

---

### Post by bodhi.zazen on 2009-07-20
Just let the command run.

---

### Post by bodhi.zazen on 2009-07-20
Just let the command run.

---

### Post by tomreid on 2009-07-21
Thanks all, that worked. It took around 30 hours, but it worked.

One final question, I have a friend who is sitting with two old systems she does not want to get rid of as she does not know how to wipe the hard drives. These are windows machines. 

If I extract the hard drives and plug them into my Ununtu system, as I did with the mac HD will this work just as well? i.e. is there any difference in the effectiveness of this method because of the original OS that wrote the files on the HD? Or is this essentially OS neutral?

cheers

---

### Post by lykwydchykyn on 2009-07-21
> **tomreid said:**
> Thanks all, that worked. It took around 30 hours, but it worked.

One final question, I have a friend who is sitting with two old systems she does not want to get rid of as she does not know how to wipe the hard drives. These are windows machines. 

If I extract the hard drives and plug them into my Ununtu system, as I did with the mac HD will this work just as well? i.e. is there any difference in the effectiveness of this method because of the original OS that wrote the files on the HD? Or is this essentially OS neutral?

cheers

It should be equally effective no matter what the original OS is, AFAIK.  And you shouldn't need to go to the trouble of pulling the hard drives out, just boot up to the liveCD and run it. (or use DBAN, which is a bit faster because there's less overhead).  shred is on the liveCD.

---

### Post by HermanAB on 2009-07-22
Howdy,

All the special software like dban and shred are quite redundant and not as good as the erase routine that is built into the disk drive controller of all modern drives.  These special programs hark back to the days before the drive controllers had erase programs built in.

The advantage of the built-in erase, is that it can erase everything including bad sectors and the space between tracks.  Dban et al cannot do that.

Here is a tool for Windoze to trigger the built-in erase function:
[http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml](http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml)

The Linux version is contained in 'hdparm'.

---

