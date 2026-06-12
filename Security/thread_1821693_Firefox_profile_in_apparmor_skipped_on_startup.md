---
title: "Firefox profile in apparmor skipped on startup"
date: 2011-08-09
forum: Security
---

### Post by donsy on 2011-08-09
I have quiet splash disabled so I can see what boot processes are run on startup, and I notice that on every time I boot my computer the Firefox profile is skipped. Here's the message:```
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
``` I checked  /etc/apparmor.d/disable, and see that there is indeed a link to usr.bin.firefox. So I'm wondering how/why it got there. I haven't touched anything in AppArmor since my clean install of Natty. Can I or should I remove it? I'm an AppArmor noob.

---

### Post by FuturePilot on 2011-08-09
It's disabled by default.

---

### Post by donsy on 2011-08-09
> **FuturePilot said:**
> It's disabled by default.

Not much info there. Like I said I'm an AppArmor noob. So what should I do? Enable it? How? By deleting the link in the /etc/apparmor.d/disable directory?

---

### Post by Dave_L on 2011-08-09
To enable the firefox profile, delete /etc/apparmor.d/disable/usr.bin.firefox.

---

### Post by FuturePilot on 2011-08-09
> **donsy said:**
> Not much info there. Like I said I'm an AppArmor noob. So what should I do? Enable it? How? By deleting the link in the /etc/apparmor.d/disable directory?
Do you want it enabled? It's disabled by default because it will break certain functionality of Firefox. (usually plugins)
If you want it enabled see here [https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?]("https://help.ubuntu.com/community/AppArmor#How%20can%20I%20enable%20AppArmor%20for%20Firefox?")

> **Dave_L said:**
> To enable the firefox profile, delete /etc/apparmor.d/disable/usr.bin.firefox.

No, that is not the correct way to do it. See the link above.

---

### Post by twipley on 2011-08-10
Indeed, the correct command is:

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox
```

Then verification through ```
sudo apparmor_status
```

I believe the Firefox profile is included by default in Ubuntu releases starting from 11.10, however it comes unactivated.

Also, some people (such as bodhi.zazen) are advocating that Firefox should be protected by AppArmor by default. Such an approach might make sense. It might be wise to vote over at [http://brainstorm.ubuntu.com/idea/27401](http://brainstorm.ubuntu.com/idea/27401) for the inclusion of such an idea to future Ubuntu releases.

---

### Post by Soul-Sing on 2011-08-11
```
sudo aa-enforce firefox
```  will do
reload the deamon:  ```
sudo /etc/init.d/apparmor reload
```
before you can look at the status: ```
sudo /etc/init.d/apparmor status
```
afaik jamie strandboge makes default apparmor firefox profiles,which are not enabled, from the 10.4 release.

so "we" don't need standard profiles, more a gui as selinux for apparmor to guide us to individual made apparmor profiles.
( ref to the brainstorm idea)

---

