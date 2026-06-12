---
title: "whats this mean"
date: 2012-03-01
forum: Virtualisation
---

### Post by rollinsmoke on 2012-03-01
VT-x/AMD-V hardware acceleration is not available on your system. Certain guests (e.g. OS/2 and QNX) require this feature and will fail to boot without it.

also have this goin on 

 p, li { white-space: pre-wrap; }  VirtualBox is not currently allowed to access USB devices. You can change this by adding your user to the 'vboxusers' group. Please see the user manual for a more detailed explanation.




  p, li { white-space: pre-wrap; }     Result Code: 
  NS_ERROR_FAILURE (0x00004005)
   Component: 
  Host
   Interface: 
  IHost {dab4a2b8-c735-4f08-94fc-9bec84182e2f}
   Callee: 
  IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}



im running virtualbox 4.1.8 r75467 and ubuntu 11.10 

also have a intel p4 with h/t 3.4ghz and 4 gb ram i would figure id have enough hardware to support this

oh another thing this might be handy thing to know im trying to install windows 8 consumer previwe

---

### Post by imachavel on 2012-03-02
I believe that hardware acceleration is what's required to run mac osx hfs in virtual box. Remember mac OS is EXTREMELY proprietary. guest additions don't hurt btw remember that

---

### Post by Habitual on 2012-03-02
[U]n/m.
[/U][]("http://www.oracle.com/technetwork/server-storage/virtualbox/downloads/index.html#extpack")

---

### Post by rollinsmoke on 2012-03-02
i have the extensions installed but cant get windows 8 to install to be able to install guest additions ive searched hi and low and have found nothing towards solving this problem anyone ideas?

---

### Post by MartyBuntu on 2012-03-04
Your processor needs to support hardware virtualisation.

The Pentium IV's don't.

---

### Post by CharlesA on 2012-03-04
> **MartyBuntu said:**
> Your processor needs to support hardware virtualisation.

The Pentium IV's don't.
Yep.

That just means that you can't run 64-bit guests on a 32-bit host. No big deal there.

As for the vboxusers group, just add the user that is running vbox to that group if you need to use USB devices with the virtual machines.

---

