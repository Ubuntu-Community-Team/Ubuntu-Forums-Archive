---
title: "Gnome-boxes cannot create new box or connect to old ones"
date: 2013-06-17
forum: Virtualisation
---

### Post by RavanH on 2013-06-17
Hi all,

After I had Gnome Boxes running on an Ubuntu 13.04 with Gnome3/Shell 3.8 from the Gnome3 Team PPA successfully before, I came to a point where I decided to do a clean install of Ubuntu Gnome instead (because of other issues). So I did a backup of my complete home dir and put that back after the clean install. Then I added the Gnome3 Team PPA again and upgraded to Gnome 3.8. All this without any issues.

However, trying to fire up a Windows XP box (I conveniently called it WinXP) I had installed before with Gnome Boxes, I now got the message: ```
Connection to 'WinXP' failed
```
No other info. Just that...

So I started Gnome Boxes from terminal to see if there would be any more info there. Sadly, nothing. But as soon as I tried to create a new box from one of the ISO images on my machine, I got that same failed connection message (other box name obviously) and in terminal the following error appeared:

```
(gnome-boxes:16529): Boxes-CRITICAL **: libvirt-machine.vala:78: Failed to fetch configuration for domain 'boxes-unknown-2': Unable to get domain XML config: Domain not found: no domain with matching uuid '8e08cf24-eee3-cf0f-1aa1-f19ee587a495'
```

Can anyone tell my why Gnome Boxes would not be able to connect me to a previously working local virtual machine installation?

Thanks :)

---

### Post by Zeklandia on 2013-08-07
> **RavanH said:**
> Hi all,

After I had Gnome Boxes running on an Ubuntu 13.04 with Gnome3/Shell 3.8 from the Gnome3 Team PPA successfully before, I came to a point where I decided to do a clean install of Ubuntu Gnome instead (because of other issues). So I did a backup of my complete home dir and put that back after the clean install. Then I added the Gnome3 Team PPA again and upgraded to Gnome 3.8. All this without any issues.

However, trying to fire up a Windows XP box (I conveniently called it WinXP) I had installed before with Gnome Boxes, I now got the message: ```
Connection to 'WinXP' failed
```
No other info. Just that...

So I started Gnome Boxes from terminal to see if there would be any more info there. Sadly, nothing. But as soon as I tried to create a new box from one of the ISO images on my machine, I got that same failed connection message (other box name obviously) and in terminal the following error appeared:

```
(gnome-boxes:16529): Boxes-CRITICAL **: libvirt-machine.vala:78: Failed to fetch configuration for domain 'boxes-unknown-2': Unable to get domain XML config: Domain not found: no domain with matching uuid '8e08cf24-eee3-cf0f-1aa1-f19ee587a495'
```

Can anyone tell my why Gnome Boxes would not be able to connect me to a previously working local virtual machine installation?

Thanks :)

Bump!

I just started having this issue, it must have been caused by a change in the last few months.

---

