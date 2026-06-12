---
title: "COnfusion with apparmor and SE linux"
date: 2010-05-12
forum: Security
---

### Post by keljaden on 2010-05-12
Okay; after reading a bodhi.zazen's security guides, I feel my system is extremely vulnerable.  As a relatively new linux user, bodhi's guides are a bit confusing to me and there are some problems I have.

Apparmor has no gui and if I update the software I am using (like FF) my profile will be false.

Do I need to do all the complex profiles for SElinux that apparmor requires?

I want to be secure, but it seems to be quite difficult.  Is SE linux easier to use than apparmor?

---

### Post by cdenley on 2010-05-12
I don't think SE linux is any easier than apparmor. I doubt you are extremely vulnerable. I would enable the apparmor profile for firefox, then you should be fine.
```

sudo aa-enforce firefox

```

---

### Post by keljaden on 2010-05-12
do I already have the apparmor profile?

---

### Post by doas777 on 2010-05-12
it is available in the repositories if you do not. the package is called apparmor-profiles. mine were preinstalled in karmic

---

### Post by cdenley on 2010-05-12
> **doas777 said:**
> it is available in the repositories if you do not. the package is called apparmor-profiles. mine were preinstalled in karmic

In lucid, the profile is included with the firefox package.

---

### Post by keljaden on 2010-05-12
awesome, other than firefox, are there other apps which I should make sure I have apparmor for, like kopete/evolution, skype, ktorrent/transmission?

Also, I am using linux mint and guarddog is my firewall. I turned it on, right now I only have my IM clients and DNS allowed.  Is that the proper way to set up a good firewall, or should I be using firestarter.

---

### Post by doas777 on 2010-05-12
i would focus first on proprietary programs that do not provide code, since it is not/cannot be peer reviewed. 

secondly just consider the apps that interface most with the outside world.

---

### Post by OpSecShellshock on 2010-05-12
> **keljaden said:**
> Also, I am using linux mint and guarddog is my firewall. I turned it on, right now I only have my IM clients and DNS allowed.  Is that the proper way to set up a good firewall, or should I be using firestarter.

Not sure about guarddog's default settings, but in most cases (particularly regarding ufw's default rules) you won't need to allow anything. As long as ufw is enabled and no ports on your hardware are forwarded, your IM client should connect just fine without any changes when you sign in. When you aren't signed in or the client isn't running, it won't accept any connections at all.

Also, Firestarter, while available, is no longer active/supported. Your iptables configuration needs can be met with ufw/gufw.

---

### Post by keljaden on 2010-05-12
for guwf(ufw)  how do I know its running.  Do I need to keep the config utility open the whole time.  or is it running at all time, ever after i restart my system.

---

### Post by bodhi.zazen on 2010-05-12
> **keljaden said:**
> for guwf(ufw)  how do I know its running.  Do I need to keep the config utility open the whole time.  or is it running at all time, ever after i restart my system.

These tools configure iptables and your settings are saved, even if you reboot.

To see them ```
sudo iptables -L -v -n
```

---

### Post by doas777 on 2010-05-13
> **keljaden said:**
> for guwf(ufw)  how do I know its running.  Do I need to keep the config utility open the whole time.  or is it running at all time, ever after i restart my system.

that is my principal complaint about gufw: the lack of monitoring capability.
that and it handles port ranges stupidly. if you tell it to create a rule for ports 0-65535, it will spend the next 12 hours generating 65536 rules; 1 for each port.

---

### Post by keljaden on 2010-05-13
so with uwf and apparmor on my most common used apps (and my encrypted home folder) I should be good?

I am not doing banking or anything at a local starbucks or something, but I want to know that I am pretty secure using my laptop around campus and other places where your typical college student would use his laptop.

---

