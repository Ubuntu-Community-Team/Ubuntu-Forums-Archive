---
title: "ufw firewall will not start on reboot"
date: 2016-01-03
forum: Security
---

### Post by makepublic4everyon on 2016-01-03
I have 2 Ubuntu desktop running 14.04.03 and neither will start UFW firewall after rebooted. The OS has been updated using apt-get update and apt-get upgrade.   After the machine is rebooted the and I perform "ufw status" it is inactive for both. How can it be enabled on startup automatically ?

---

### Post by deadflowr on 2016-01-03
It's unclear if you ran
```
sudo ufw enable
```
but that should enable it and keep it enabled after a restart.

You can also change the setting manually by editing the line in /etc/ufw/ufw.conf, change the line from ENABLED=no, to ENABLED=yes

---

### Post by haplorrhine on 2016-01-04
Not sure how it should be by default, but this might remedy the situation.  [https://help.ubuntu.com/community/DynamicFirewall#Iptables_INIT_Script](https://help.ubuntu.com/community/DynamicFirewall#Iptables_INIT_Script)

ufw is just a frontend for iptables

---

### Post by sammiev on 2016-01-04
> **haplorrhine said:**
> Not sure how it should be by default, but this might remedy the situation.  [https://help.ubuntu.com/community/DynamicFirewall#Iptables_INIT_Script](https://help.ubuntu.com/community/DynamicFirewall#Iptables_INIT_Script)

ufw is just a frontend for iptables

Hi haplorrhine,

I get this from your [link]("https://help.ubuntu.com/community/DynamicFirewall#Iptables_INIT_Script").

---

### Post by QDR06VV9 on 2016-01-04
> **sammiev said:**
> Hi haplorrhine,

I get this from your [link]("https://help.ubuntu.com/community/DynamicFirewall#Iptables_INIT_Script").
I get the same as sammiev..
And deadflowr's advice will work on 14.04.
It will start UFW and enable it on startup..
Now if you are using systemd that is default on 15.10 you would use different text.
```
systemctl start ufw
sudo systemctl enable ufw

```

Regards

---

### Post by lisati on 2016-01-04
It could be a temporary glitch - the [link]("https://help.ubuntu.com/community/DynamicFirewall#Iptables_INIT_Script") worked for me.

---

### Post by QDR06VV9 on 2016-01-04
> **lisati said:**
> It could be a temporary glitch - the [link]("https://help.ubuntu.com/community/DynamicFirewall#Iptables_INIT_Script") worked for me.
How odd?? I still get
And that is follwing your link lisati:o

---

### Post by lisati on 2016-01-04
> **runrickus said:**
> How odd?? I still get
And that is follwing your link lisati:o

I got the 500 error this time too.... :( I cleared my browser cache and it worked..... Odd.

---

### Post by deadflowr on 2016-01-04
> **haplorrhine said:**
> Not sure how it should be by default
ufw is off by default Or inactive, or disabled. which ever term you prefer.

---

### Post by mikodo on 2016-01-04
> **deadflowr said:**
> ufw is off by default Or inactive, or disabled. which ever term you prefer.

How I have been enabling the default Ubuntu settings.

                        [URL="https://help.ubuntu.com/community/UFW"]https://help.ubuntu.com/community/UFW

[/URL]Not sure if this is helpful or not in this instance though.

---

### Post by haplorrhine on 2016-01-04
> **deadflowr said:**
> ufw is off by default Or inactive, or disabled. which ever term you prefer.

I meant the /etc/init.d directory.

---

### Post by deadflowr on 2016-01-05
> **haplorrhine said:**
> I meant the /etc/init.d directory.
UFW is not a service, so there should be nothing for it in that folder, by default.

---

