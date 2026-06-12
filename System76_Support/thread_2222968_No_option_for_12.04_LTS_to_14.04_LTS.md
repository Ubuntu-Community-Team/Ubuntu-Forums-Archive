---
title: "No option for 12.04 LTS to 14.04 LTS"
date: 2014-05-08
forum: System76 Support
---

### Post by sviginak on 2014-05-08
Gazelle Pro6, I bought it with 11.10, upgraded to LTS 12.04. On the Ubuntu upgrade page there is no option for 12.04 LTS to 14.04 LTS. On my Upddate Manager, the notification is "12.10 is available". Will 12.04 > 14.04 eventually be there, or do I need to upgrade a different way?

thanks,

---

### Post by SuperFreak on 2014-05-08
I think the upgrade option isn't offered until 14.04.1 comes out in July. I believe there is another way to do it but I can't help you

---

### Post by sammiev on 2014-05-08
This is how I updated a few of my older laptops with no issues. 

Always backup your data or OS first.

Make sure 12.04  is fully updated first before running the command below.

```
sudo update-manager -d
```

---

### Post by hans12345 on 2014-05-09
I have the same problem (only offered upgrade to 12.10) on a Sony laptop.


sviginak - did you try  sammiev's suggestion?

---

### Post by SuperFreak on 2014-05-09
[http://www.cyberciti.biz/faq/howto-upgrade-to-ubuntu-14-04-from-ubuntu-13-10-or-12-04/]("http://www.cyberciti.biz/faq/howto-upgrade-to-ubuntu-14-04-from-ubuntu-13-10-or-12-04/")

---

### Post by hans12345 on 2014-05-09
Thanks Superfreak, but there has to be a cleaner way. 

I cannot believe Canonical expect 12.04 LTS users to follow such a path.

But I just now notice that I have arrived in a System76 thread. Am I posting in the wrong place?

---

### Post by SuperFreak on 2014-05-09
The "cleaner" way is to wait until July when 14.04.1 comes out. The idea being that the major bugs with 14.04 will be fixed by that point and the upgrade button will be available in Software Updates

---

### Post by hans12345 on 2014-05-09
OK, thanks, I'll wait.
:-)

---

### Post by sviginak on 2014-05-09
Thanks for the response everyone. I think I will wait until July, also. It seems a little strange there is not a note on the 14.04 upgrade page telling 12.04 LTS users we have to wait a little while. [https://help.ubuntu.com/community/TrustyUpgrades](https://help.ubuntu.com/community/TrustyUpgrades) is where I was sent from System 76 support. I am busy at work right now, but I have some time off later next week, if I feel frisky I may try something else.
edit: hans, we all upgrade at the ubuntu site, System 76 users then download our driver patch from them. We bought computers from Sys76 set up for Ubuntu, I have been happy with mine for three years or so I have had it.

sviginak

---

### Post by sviginak on 2014-07-24
So here it is July 24, any word on 14.04.1 being available soon for LTS upgrade from 12.04 to 14.04?

---

### Post by SuperFreak on 2014-07-24
Think they are still ironing out the last few bugs. Imminent

---

### Post by kansasnoob on 2014-07-24
> **sviginak said:**
> So here it is July 24, any word on 14.04.1 being available soon for LTS upgrade from 12.04 to 14.04?

There are two nasty bugs in the Precise -> Trusty upgrade process:

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1347721)

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1347964)

I know because I filed both of them ;)

---

### Post by sviginak on 2014-07-25
Thanks for the update!

---

### Post by sviginak on 2014-08-20
Upgraded to 14.04 today, using update manager, everything appears to have went well. Reinstalled System76 driver. Thanks again for the help and advice, everyone.

---

