---
title: "Slow, Erratic Performance at cdimages.ubuntu.com?"
date: 2015-02-01
forum: Ubuntu Development Version
---

### Post by buzzingrobot on 2015-02-01
Anyone else seeing slow and erratic performance at cdimages.ubuntu.com over the last two days?

Here, the page has been very slow to load; downloads of dailies that typically take 5-10 minutes often begin (per Firefox) with a download time of several hours, eventually decrease to something less than one hour, with the duration remaining bouncing up and down significantly.

Equivalent downloads from other locations aren't affected.

---

### Post by PaulW2U on 2015-02-01
> **buzzingrobot said:**
> Anyone else seeing slow and erratic performance at cdimages.ubuntu.com over the last two days?.

Yes, extremely slow here and erratic like you describe.

I had to do a speedtest to prove that my connection is performing as fast as it should on other sites.

---

### Post by Elfy on 2015-02-01
> **PaulW2U said:**
> Yes, extremely slow here and erratic like you describe.

I had to do a speedtest to prove that my connection is performing as fast as it should on other sites.

I could have posted that post verbatim :)

#################--- 89.9% 53.3 kBps 31:33 ETA

for instance

---

### Post by kansasnoob on 2015-02-02
Yep, it takes literally minutes just to open a manifest for 14.04.2 release candidate images.

I hope maybe things are just tied up because they're busy pushing the Utopic HWE into the 14.04.2_wanna_be images. Seems like they put a lot of work off until the last minute .................. or maybe they'll delay the release of 14.04.2.

---

### Post by PaulW2U on 2015-02-03
Giving up on zsyncing Kubuntu and Xubuntu 15.04 images for now.

@Elfy, I've added weight to your post in #canonical-sysadmin but disappointed that the problem hasn't been resolved especially with 14.04.2 due for release the day after tomorrow. :(

---

### Post by Elfy on 2015-02-03
> **PaulW2U said:**
> Giving up on zsyncing Kubuntu and Xubuntu 15.04 images for now.

@Elfy, I've added weight to your post in #canonical-sysadmin but disappointed that the problem hasn't been resolved especially with 14.04.2 due for release the day after tomorrow. :(

Yep - saw that. 

They're obviously looking - give them time to do it :) 

cdimage.ubuntu.com seems unreachable currently completely

---

### Post by slickymaster on 2015-02-03
> **Elfy said:**
> Yep - saw that. 

They're obviously looking - give them time to do it :) 

cdimage.ubuntu.com seems unreachable currently completely

There's still a huge delay but it's up now:
[ATTACH=CONFIG]259686[/ATTACH]

---

### Post by kansasnoob on 2015-02-03
Badly borked the past few hours:

```
lance@lance-VIA-desktop:~/Downloads/Ubuntu_GNOME$ zsync http://cdimage.ubuntu.com/ubuntu-gnome/trusty/daily-live/20150203/trusty-desktop-i386.iso.zsync
#################### 100.0% 506.7 kBps DONE      

reading seed file trusty-desktop-i386.iso: *****************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************************Read trusty-desktop-i386.iso. Target 67.8% complete.      *********************
downloading from http://cdimage.ubuntu.com/ubuntu-gnome/trusty/daily-live/20150203/trusty-desktop-i386.iso:
#############------- 67.8%bad status code 404
#############------- 67.8% 0.0 kBps aborted    

failed to retrieve from trusty-desktop-i386.iso
Aborting, download available in trusty-desktop-i386.iso.part

```

---

### Post by Elfy on 2015-02-03
yea - all over the place

---

### Post by Elfy on 2015-02-03
seemingly able to, once it's woken up a bit, grab the direct links - seems to be the zsync (for one) to be an issue here.

hob@hob:~/Desktop$ md5sum trusty-desktop-amd64.iso 
aa524a458346fab97df4c0c0001efe68  trusty-desktop-amd64.iso
hob@hob:~/Desktop$ md5sum trusty-desktop-i386.iso 
9a1c052239fdf360d992916bccc6d65c  trusty-desktop-i386.iso

---

### Post by kansasnoob on 2015-02-03
Working at least somewhat better here ATM.

---

### Post by kansasnoob on 2015-02-03
Back to just erratic now, but not totally borked.

---

### Post by PaulW2U on 2015-02-03
Just received a message in #canonical-sysadmin that cdimage.ubuntu.com is back to normal.

Downloading at a steady 4.5MB/s as I type. :p

---

