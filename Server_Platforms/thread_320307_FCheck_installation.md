---
title: "FCheck installation"
date: 2006-12-17
forum: Server Platforms
---

### Post by Bill007 on 2006-12-17
Kia Ora 

Has anyone got a clue on  this fault

I have tried thru 

apt-get

and wget 

but both end in the same result


root@production:/home/bill007# /usr/local/fcheck/fcheck -cadsx
/usr/bin/md5sum: /lib/udev/devices/core: Operation not permitted
fcheck: /usr/bin/md5sum was unable to read /lib/udev/devices/core, or was unable to execute

terminating...


Regards Bill007

---

### Post by chrisfay on 2006-12-17
Have you tried invoking with sudo:

```
sudo /usr/local/fcheck/fcheck -cadsx
```

Did you make the FCheck perl script executable?
```
sudo chmod u+x /usr/local/fcheck
```

---

### Post by Bill007 on 2006-12-17
Yes and No  Im working from the root but havnt chmod the file

I guess I assumed that apt-get would unpack and install the complete package 



I Will try wyth the second option

The problem seems to occur when /usr/bin/md5sum tries reading from the  core sym link  in the directory /lib/udev/devices/core so maybe your are right on the file execution some times is that simple

Ill be back

---

### Post by Bill007 on 2006-12-17
Neither of those worked it seems 

The problem seems to occur when /usr/bin/md5sum tries reading from the core sym link in the directory /lib/udev/devices/core

hence 

root@production:/home/bill007# /usr/local/fcheck/fcheck -cadsx
/usr/bin/md5sum : /lib/udev/devices/core: Operation not permitted
fcheck: /usr/bin/md5sum was unable to read /lib/udev/devices/core, or was unable to execute

terminating...

When I look at it a tiny bit closer  I dont even have a directory  /usr/bin/md5sum

so my fcheck.cfg file is setting up for the wrong directory do i really need md5sum

Or how to get the md5sum file

Hmmmmmmm

---

### Post by chrisfay on 2006-12-17
I just followed this guide exactly:

[http://www.brandonhutchinson.com/fcheck.html](http://www.brandonhutchinson.com/fcheck.html)

...and had it working in 5 minutes without an issue. Literally, just installed it. I would remove the package and give the link a try. Worked for me.

---

### Post by Bill007 on 2006-12-17
Well cancel what I just said, there is a md5sum file in /usr/bin/ but there seems to be some problem here with the md5sum reading from the core symlink in /lib/udev/devices/core


/user/local/fcheck/fcheck -cadsx

# Options explained:
# c create the database
# a is for all
# d is to monitor directory creation 
# s is to create signatures for all files
# x is for extended permissions monitoring

I removed the s option and everything loaded fine  I just dont have md5sum protection on the database files I can live with that for the time being while I find a solution

Bill007

---

### Post by chrisfay on 2006-12-17
Or you could try changing:

```
$Signature = /usr/bin/md5sum
```
to
```
$Signature = /usr/bin/cksum
```

...and just use a different file signiture method altogether.

---

### Post by Bill007 on 2006-12-17
No same problem, nice easy guide though

I have some problem with md5sum and the programme terminates

Oh well i guess ill go with out signitures for the time being

Thanks for you help chrisfay

---

### Post by chrisfay on 2006-12-17
Np....:)

---

