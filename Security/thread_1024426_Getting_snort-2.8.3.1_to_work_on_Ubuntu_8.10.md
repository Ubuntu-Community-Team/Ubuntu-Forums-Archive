---
title: "Getting snort-2.8.3.1 to work on Ubuntu 8.10"
date: 2008-12-29
forum: Security
---

### Post by fast-Eddie on 2008-12-29
Hi All,

I'd consider myself a linux novice and have been trying to install snort 2.8.3.1 on ubuntu 8.10. I've had some luck following Bodhi Zazen's post at [http://ubuntuforums.org/showthread.php?t=919472](http://ubuntuforums.org/showthread.php?t=919472).

When I open Base I see Sensors/Total: 0 / 0 and everything else also at 0. Is anyone able to help me get snort working or point me in the right direction??

Thanks
Eddie

---

### Post by fast-Eddie on 2008-12-29
Does anyone know of any steps/checks I can perform to troubleshoot this issue??

---

### Post by fast-Eddie on 2008-12-29
I used Bodhi Zazen's script in this post "http://ubuntuforums.org/showpost.php?p=5786252&postcount=3" to start/stop snort however it is not saying 'snort failed to start'. 

Is anyone able to help troubleshoot this issue??

Thanks
Eddie

---

### Post by fast-Eddie on 2008-12-29
okay, the script mentioned in the above post from  Bodhi Zazen now works and I was able to successfully start snort!! 

Now when I open BASE, I see "Sensors/Total: 0 / 1 " but no other info on the page (everything else is still '0'). How can I tell if snort is actually working and logging stuff??

---

### Post by Sarmacid on 2008-12-29
One way to find out if Snort is working is either turning on the ICMP chatty rules or running a portscan to the machine, both while watching the alert file for changes ```
tail -f /var/log/snort/alert
```

---

### Post by Kinstonian on 2008-12-29
Just go to [http://testmyids.com/](http://testmyids.com/) and if Snort is working, and is able to see the traffic, it should generate an alert.

---

### Post by lavi17 on 2009-04-28
Well i've tried makin this base thing work using the procedure mentioned in howtoforge as well as the one mentioned by you, but this base is still lifeless... is there anyway to see it moving? am i missing on something, i'm using snort-2.8.4.... i can see alerts on the mysql database... but base is showing nothing....

---

### Post by cqk6 on 2009-05-08
I think you meet this error because your switch is not configure port mirror, you can test by replace a hub.

cqk6

---

