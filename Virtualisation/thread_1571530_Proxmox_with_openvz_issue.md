---
title: "Proxmox with openvz issue"
date: 2010-09-09
forum: Virtualisation
---

### Post by stlsaint on 2010-09-09
I started another thread on the proxmox forums but they were unable to help much so i figured i ask the world here! ):P

Here is the post: [http://forum.proxmox.com/threads/4629-Upgrade-issue](http://forum.proxmox.com/threads/4629-Upgrade-issue)

i know its an openvz issue...just dont know solution.

---

### Post by bodhi.zazen on 2010-09-09
Can you try booting an older kernel ?

---

### Post by stlsaint on 2010-09-10
So i edited menu.lst and booted original kernel (2.6.24-8-pve)
and i am able to access everything using vz tools but i am having some networking issues (ssh, updating, etc). But with newly released kernel for proxmox (2.6.32-3-pve) i am unable to reach two out of my four containers. I will be bringing this up to the folks over at the proxmox forum to see if this is a potential bug. My only problem is that according to the site. My working kernel is no longer being supported by them and is strictly available for legacy reasons! So sooner or later i will be needing to upgrade my system to the new kernel!! :(

EDIT: Remaining at the older kernel is not an option as it messes up my websites due to the networking issues!

---

### Post by bodhi.zazen on 2010-09-10
> **stlsaint said:**
> So i edited menu.lst and booted original kernel (2.6.24-8-pve)
and i am able to access everything using vz tools but i am having some networking issues (ssh, updating, etc). But with newly released kernel for proxmox (2.6.32-3-pve) i am unable to reach two out of my four containers. I will be bringing this up to the folks over at the proxmox forum to see if this is a potential bug. My only problem is that according to the site. My working kernel is no longer being supported by them and is strictly available for legacy reasons! So sooner or later i will be needing to upgrade my system to the new kernel!! :(


OK. I have found the openvz patch on a 2.6.32-x kernel to be quite buggy on a debian system. By report it works on Centos, I have not tried it.

It is sad to see this happen to the openvz project, and, IMO, LXC is not ready yet ...

Looks as if I may be migrating to kvm.

You should be fine on an older kernel for a while but unless Proxmox or Debian has a working openvz kernel you may need to consider alternates.

---

### Post by stlsaint on 2010-09-10
Thats the bad thing...i wont be fine! My networking issues are too hindering to just put up with or work around. For now my website is up and working but i have a media server linked to the website and that is not working. I need this fixed also as i cannot update or install anything in my vps'! oh noes!! :(
And whats even more pathetic is my lappy supports kvm but my 4 core server does not!! Darn xeons!!

---

### Post by bodhi.zazen on 2010-09-10
> **stlsaint said:**
> Thats the bad thing...i wont be fine! My networking issues are too hindering to just put up with or work around. For now my website is up and working but i have a media server linked to the website and that is not working. I need this fixed also as i cannot update or install anything in my vps'! oh noes!! :(
And whats even more pathetic is my lappy supports kvm but my 4 core server does not!! Darn xeons!!

Openvz is complex, may I ssh in and take a look ?

---

