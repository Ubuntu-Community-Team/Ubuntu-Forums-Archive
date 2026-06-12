---
title: "Requests concerning wireless-info"
date: 2018-01-03
forum: Ubuntu, Linux and OS Chat
---

### Post by mringer on 2018-01-03
1. Since wireless-info is so valuable, (my thanks to the authors) I ask that it be 
put onto the Live CD. I think it is unreasonable to ask users to download it if
their network is dead.

2. Over the years I have encountered:

missing or incorrect device driver
wifi card hard or soft blocked
package X not installed
mangled configuration files
Running both wicd and network-manager (NM)
NM running but nm-applet not running
incorrect ESSID
incorrect encrypt key

and several of these are easy to see from wireless-info.txt  , so I 
was able to fix without posting on this Forum & wasting the experts' 
time.

I ask that there be a man page that says 

"if wireless-info says X then you should try Y "

Thank you.
I have L-Ubuntu 14.04. My apology if these have been done already.

---

### Post by DuckHook on 2018-01-03
All of the members of this forum, including all of the staff, are volunteer users just like yourself. We are not affiliated with Canonical or Ubuntu, except as a volunteer help resource that they value and appreciate. They support us by hosting this forum on their servers, but that's really about it. Developers rarely, if ever, visit here.

Therefore, your request is in the wrong place. Requests for features start with familiarizing yourself with the following: [https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages) …then contacting the Ubuntu development team as per that link. You can also discuss the future development of Ubuntu in: [https://community.ubuntu.com/](https://community.ubuntu.com/) Reading those discussions, you might detect an informal expectation that the requester do a lot of the legwork and have some street cred within the community. This is a natural outgrowth of the fact that, as an open source project, those making requests are expected to have made some demonstrable investment into the community.

We are pleased that you find the wireless script useful. Please note, however, that the script is a product of this forum community and is authored and maintained by Krytarik, our very own Wild Man (wildmanne39) and with lots of help from chili555. It is not part of the larger Linux ecosystem and is purely a wireless help resource that is specific to Ubuntu Forums. For that reason, I doubt very much that the developers would include it as a general resource.

---

### Post by wildmanne39 on 2018-01-03
I think it is already in the best place it can be, on github, in the 5 and a half years it has been used even when I hosted it on dropbox I have never heard of it not being able to be downloaded because the site was down. 

Also it can not be down for the same reasons DuckHook posted.

---

### Post by mastablasta on 2018-01-04
i think what the OP is saying that if you have a wireless only connection to work with then you can't really download it and use it in an easy way or need to have it downloaded before you do the install.

on the other hand, it is not good to do updates and install with only wireless connection available.

---

### Post by wildmanne39 on 2018-01-04
The wireless script can be downloaded to an usb drive with a computer that has a connection then ran by doing.

```
chmod +x wireless-info
./wireless-info
```

---

### Post by DuckHook on 2018-01-04
> **mastablasta said:**
> i think what the OP is saying that if you have a wireless only connection to work with then you can't really download it and use it in an easy way or need to have it downloaded before you do the install.
Yes. I also got the same impression from the OP's original post. The OP further asked that the script be included as part of Ubuntu's official distribution. It was that additional request to which I was responding.
> on the other hand, it is not good to do updates and install with only wireless connection available.
+1

I very much agree.

---

