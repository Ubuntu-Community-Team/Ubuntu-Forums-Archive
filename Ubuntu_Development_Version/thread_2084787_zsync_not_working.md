---
title: "zsync not working?"
date: 2012-11-16
forum: Ubuntu Development Version
---

### Post by jbicha on 2012-11-16
I tried using zsync (on raring) for the first time to download the raring image today but it's not working. Have others seen this? When was the last time zsync worked?

```

zsync http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync
#################### 100.0% 306.6 kBps DONE     

reading seed file raring-desktop-i386.iso.part: ******************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read raring-desktop-i386.iso.part. Target 51.3% complete.      ******************************************
downloading from http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso:
##########---------- 51.3%
zsync received a data response (code 200) but this is not a partial content response
zsync can only work with servers that support returning partial content from files. The person/entity creating this .zsync has tried to use a server that is not returning partial content. zsync cannot be used with this server.
See http://zsync.moria.orc.uk/server-issues
##########---------- 51.3% 0.0 kBps aborted    

failed to retrieve from raring-desktop-i386.iso
Aborting, download available in raring-desktop-i386.iso.part
verifying download...

```

---

### Post by dino99 on 2012-11-16
its not a zsync issue, but a borked image built the wrong way. (server misconfigured)

```
The person/entity creating this .zsync has tried to use a server that is not returning partial content. zsync cannot be used with this server.
```

---

### Post by jerrylamos on 2012-11-16
Last time zsync worked for me was this morning.  In U.S.A. whatever server Ubuntu uses for me.

---

### Post by ventrical on 2012-11-16
> **jbicha said:**
> I tried using zsync (on raring) for the first time to download the raring image today but it's not working. Have others seen this? When was the last time zsync worked?

```

zsync http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync
#################### 100.0% 306.6 kBps DONE     

reading seed file raring-desktop-i386.iso.part: ******************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read raring-desktop-i386.iso.part. Target 51.3% complete.      ******************************************
downloading from http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso:
##########---------- 51.3%
zsync received a data response (code 200) but this is not a partial content response
zsync can only work with servers that support returning partial content from files. The person/entity creating this .zsync has tried to use a server that is not returning partial content. zsync cannot be used with this server.
See http://zsync.moria.orc.uk/server-issues
##########---------- 51.3% 0.0 kBps aborted    

failed to retrieve from raring-desktop-i386.iso
Aborting, download available in raring-desktop-i386.iso.part
verifying download...

```


Works great here .. but I always enter my commands  differently. I can't get it to work the way you have the commands entered.

```

dale@dale-desktop:~/Desktop$ zsync -i ./raring-desktop-i386.iso http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync

```

---

### Post by ventrical on 2012-11-16
Read raring-desktop-i386.iso. Target 73.6% complete.      
downloading from [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso:)
#################--- 85.6% 258.4 kBps            

downloading from [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso:](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso:)
#################### 100.0% 251.7 kBps DONE      

verifying download...checksum matches OK
used 594075648 local, fetched 214164537
dale@dale-desktop:~/Desktop$ 

  I'll try on another machine.

---

### Post by ventrical on 2012-11-16
Working fine also  on another install.

---

### Post by VinDSL on 2012-11-16
Tried to duplicate the problem, but it worked fine...

```

vindsl@Zuul:~/Downloads/Ubuntu$ zsync http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso.zsync
#################### 100.0% 239.5 kBps DONE     

No relevent local data found - I will be downloading the whole file. If that's not what you want, CTRL-C out. You should specify the local file is the old version of the file to download with -i (you might have to decompress it with gzip -d first). Or perhaps you just have no data that helps download the file
downloading from http://cdimage.ubuntu.com/daily-live/current/raring-desktop-i386.iso:
#################### 100.0% 397.9 kBps DONE      

verifying download...checksum matches OK
used 0 local, fetched 807711061
vindsl@Zuul:~/Downloads/Ubuntu$

```

---

### Post by jbicha on 2012-11-16
Ok, zsync is working now. Maybe I tried using at the wrong time of day or something. Thanks!

---

### Post by nm_geo on 2012-11-17
You probably tried it while the new spins were being uploaded, or the upload started right after you started.  You can check on the current live build for the time the isos are finished.  

Zsynced 7 different isos today as I do most days and all worked fine.

---

