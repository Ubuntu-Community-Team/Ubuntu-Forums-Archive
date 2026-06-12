---
title: "ClamAv (Confused on how to set an weekly scan)."
date: 2010-07-05
forum: Server Platforms
---

### Post by barnesey on 2010-07-05
Hi there,
 
I have just setup my new server using ubuntu server 10.04LTS (hardware is not amazing but it works very well) and i have samba file server running with many other options / services running and i would like to have a av scan every sunday night and then email me the results of the scan.
 
I have install clam av with fresh clam and the deamon etc, but dont know how to set a scan to run weekly. I have seen on the Ubuntu documenation of setting a scan in a few days in advance but not a weekly routine ([https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)).
 
How can i achive this as i have spent hours on the net and now i am confused.:lolflag:

---

### Post by elvinatom on 2010-07-05
make the update and daily scan a cron job.

---

### Post by barnesey on 2010-07-05
How would i be able to put the scan into a cron job,
This is an first for me with clam av etc

---

### Post by elvinatom on 2010-07-05
in terminal type:
```
sudo nano /etc/crontab
```
and add those lines
```
23 1    * * *   root    /usr/bin/freshclam
59 13   * * *   root    /usr/bin/clamscan -r
```
to have it update daily at 1:23 am and then scan at 1:59 pm.

---

### Post by barnesey on 2010-07-05
Another Question is how do i set it to send an message to me with the scan results?

---

### Post by elvinatom on 2010-07-05
> **barnesey said:**
> Another Question is how do i set it to send an message to me with the scan results?

someone addressed that in another post: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1369340](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1369340)

basically, create a file, say /usr/sbin/virusscan:
```
sudo nano /usr/sbin/virusscan
```
insert the scan command with your email address:
```
#!/bin/bash
clamscan -ri --exclude-dir=^/sys\|^/proc\|^/dev / | mail -s "ClamAV Scan Results for `date +%D`" YOUR_EMAIL_ADDRESS_HERE
```
make it executable:
```
sudo chmod 755 /usr/sbin/virusscan
```
and use that in cron (after the virus db update):
```
23 1    * * *   root    /usr/bin/freshclam
59 13   * * *   root    /usr/sbin/virusscan
```

I don't know what your motivation is, but just fyi, if you don't use windows, just forget about the virus scan.  ClamAV is intended to protect windows boxes.

---

### Post by barnesey on 2010-07-05
Thanks for the fast replys, now i am going to wait until tomorrow and see if the scan has copleted etc.
 
I am using clam to scan all my files etc as i have windows machines which use the shares and i would like some added virus protection.
 
Just to keep playing safe!!
:lolflag:

---

### Post by elvinatom on 2010-07-05
> **barnesey said:**
> Thanks for the fast replys, now i am going to wait until tomorrow and see if the scan has copleted etc.
 
I am using clam to scan all my files etc as i have windows machines which use the shares and i would like some added virus protection.
 
Just to keep playing safe!!
:lolflag:

makes sense to me.  and as a side note: you can test your script simply by typing in its name into the console without having to wait:
```
virusscan
```
Another note: It's been a while since I set up the scanner on my file server, so I just go by what I find online.

---

### Post by barnesey on 2010-07-05
Thanks for the side note!!!

This has come in very handy as i have typed in virusscan and it seems of found the script but it comes up with an error.

it comes up with :
/usr/sbin/virusscan: line 2: mail: command cant not be found

Any Idea's

---

