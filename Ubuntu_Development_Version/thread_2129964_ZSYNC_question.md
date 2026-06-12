---
title: "ZSYNC question"
date: 2013-03-27
forum: Ubuntu Development Version
---

### Post by pfeiffep on 2013-03-27
So if I have one iso image on my pc and setup zsync only the deltas will be downloaded - correct? 

Do I have to merge the zsync contents with the iso, or is the process 'automatic"?

If not auto - what is the process?

TIA
Pete

---

### Post by Gavin77 on 2013-03-27
For example, if you have a previous iso file "raring-desktop-amd64.iso" and you want to update to the latest build you can copy the link to the .zsync file and use

```
zsync -i raring-desktop-amd64.iso http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso.zsync
```

It will check your local file against the one on the server and then download only the parts that you don't have and create the new iso file.  Your old one will be backed up in the same folder.

---

### Post by cariboo on 2013-03-27
THis is the output I get when running zsync:

```

 ./update_raring
#################### 100.0% 249.1 kBps DONE     

reading seed file raring-desktop-amd64.iso: ************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read raring-desktop-amd64.iso. Target 47.0% complete.      ********
downloading from http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso:
##########---------- 53.1% 381.9 kBps         A  

downloading from http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso:
#############------- 68.5% 386.0 kBps         A  

downloading from http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso:
#################### 100.0% 398.7 kBps DONE      

verifying download...checksum matches OK
used 386629632 local, fetched 435932522

```

note the last figure, that is how much was downloaded from the server

---

### Post by pfeiffep on 2013-03-27
Thanks for your informative answers [COLOR=#000000]Gavin77 & [/COLOR][COLOR=#000000]cariboo907. I'm going to set up zsync tonight[/COLOR]:KS[COLOR=#000000]

Follow on question ... When are the daily iso's available for download?

TIA[/COLOR]

---

### Post by Gavin77 on 2013-03-27
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

Just check the date next to the filename to see if it's the one you want.

---

### Post by ronacc on 2013-03-27
the same directory where the zsync file is .
[ http://cdimage.ubuntu.com/daily-live/current/ ]( http://cdimage.ubuntu.com/daily-live/current/ )

---

### Post by pfeiffep on 2013-03-28
Thanks ALL - worked like a champ!

---

