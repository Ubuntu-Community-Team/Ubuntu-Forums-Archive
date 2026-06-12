---
title: "securely wiping data"
date: 2008-07-28
forum: Security
---

### Post by SpaceMaster on 2008-07-28
Lately, I've been flattening a truckload of hard drives just to cause more chaos in the universe (my life goal).  Of course, I've been using the old command:

```
dd if=/dev/zero of=/dev/(target) ## usually hda or sda
```

Since zeros aren't quite chaotic enough for me, I also like:

```
dd if=/dev/urandom of=/dev/(target)
```


However, it seems that this just loops those zeros (or randomly-generated 1's and 0's) infinitely, regardless of drive size.  Is there a way to get it to stop at the end of the drive, and output a simple message (like "mischief managed")?.

---

### Post by Yannick Le Saint kyncani on 2008-07-28
> **SpaceMaster said:**
> ```
dd if=/dev/urandom of=/dev/(target)
```
[snip]
Is there a way to get it to stop at the end of the drive

Well, dd is bound to stop at the end of the drive already ...

---

### Post by cdenley on 2008-07-28
When it overwites the entire drive, it will stop and say you ran out of space. You can also use tools like shred, srm, or wipe. You can also use something like
```

sudo hdparm --security-set-pass pass /dev/sda
sudo hdparm --security-erase-enhanced pass /dev/sda

```
I'm not 100% sure that is correct, use it at your own risk.

---

### Post by hyper_ch on 2008-07-29
even when wiped some forensic labs can restore data... although I don't think that would be quite cheap.

---

### Post by hpnc2 on 2008-07-30
the command:

dd if=/dev/urandom of=/dev/sd@

should really stop at end of device.
just consider how much is big (Gb) your disk,
for my sata 160 gb it take about 10 hours....

Assuming you only have one instance of dd,
to see some data about the progress you could open another console and type:

kill -USR1 `pidof dd`


for file-swap-mem there is also a good tool in repository:
(i think it can also work on device eg: /dev/sda but for this i would stick with dd)

sudo apt-get install secure-delete

herfe some info: [http://divilinux.netsons.org/index.php/archives/676](http://divilinux.netsons.org/index.php/archives/676)

---

### Post by blastus on 2008-07-30
Put the hard drive in a second machine and use [DBAN](http://www.dban.org/) on it. DBAN's Mersenne Twister is an order of magnitude faster than /dev/urandom. You'll also save some electricity.

---

### Post by /etc/init.d/ on 2008-07-31
Don't forget [HDDErase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml").  It only writes zeros but it's extremely fast (as it is done by the drive's internal firmware) and it will wipe several areas that no software tool can reach, such as reallocated sectors.

If you want to be assured of privacy this is the best option.  All drives manufactured in the last eight years will have the command.

You may even be able to invoke the command from within Linux using hdparm (grep the manual).  I've never had much luck with this, however.

---

### Post by cdenley on 2008-07-31
> **/etc/init.d/ said:**
> Don't forget [HDDErase]("http://cmrr.ucsd.edu/people/Hughes/SecureErase.shtml").  It only writes zeros but it's extremely fast (as it is done by the drive's internal firmware) and it will wipe several areas that no software tool can reach, such as reallocated sectors.

If you want to be assured of privacy this is the best option.  All drives manufactured in the last eight years will have the command.

You may even be able to invoke the command from within Linux using hdparm (grep the manual).  I've never had much luck with this, however.

I already posted the hdparm command. I couldn't get it to work with one of my drives, probably because it was a little older and didn't have the function in the firmware. The "secure erase" function only writes zeros, and ignores sectors marked as bad, which may contain old data. The "secure erase enhanced" function writes random data to all sectors, including those marked as bad. I think both overwrite with an offset to erase track edges.

---

### Post by linux_tech on 2008-07-31
Using linux
There are special devices that can be used to generate data which is usefull for this task: /dev/zero and /dev/urandom. 
While /dev/zero gives you as many zeros as you want, /dev/urandom gives as many random values as you ask it for. Using the dd-command, you should be able to wipe out any data found on the drive. 

for example:
jkl@lbu:~> dd if=/dev/urandom of=devicefile
17899+0 records in
17899+0 records out
25560928 bytes (26 MB) copied
You will need to replace the regular file named “devicefile” with the real disk you wand to erase (e.g. /dev/hda). You will also need to do this as root. 

3rd party tools exist that allow you to create a boot cd that runs independent upon boot and does the secure erase.    [http://www.killdisk.com/](http://www.killdisk.com/) has one that works.   Their free version does 1 pass of zeros.  HD erasing basically comes down to time and electricity to achieve an adequate level of data destruction, which involves random write passe(s)  and erase passe(s) that capture all the records.

---

