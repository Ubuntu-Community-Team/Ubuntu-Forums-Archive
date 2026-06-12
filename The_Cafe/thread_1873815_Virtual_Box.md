---
title: "Virtual Box"
date: 2011-11-02
forum: The Cafe
---

### Post by argoz17 on 2011-11-02
So, can virtual box os's get viruses...like say i was running an os in virtual box, downloaded a bad file...got a virus...does the whole computer get a virus or just virtual box and can i just remove the bad os

---

### Post by wolfen69 on 2011-11-02
*Just* the guest OS would get a virus unless you had a shared folder or something network related. But in general, if you keep both OS's separated, it only affects the guest OS and can be deleted in a heartbeat.

---

### Post by argoz17 on 2011-11-02
They share same internet..does that matter?

---

### Post by doorknob60 on 2011-11-02
> **argoz17 said:**
> They share same internet..does that matter?
No, unless somehow your network is insecure and it finds a way to your other computers through it (Not gonna happen unless you purposefully try to make it do something like that realistically, so the answer is no, you're fine)

---

### Post by sffvba[e0rt on 2011-11-02
Also, if the guest is Windows and it gets infected it won't do much (anything actually) to a Linux host... (except mess up any shared files perhaps)...


404

---

### Post by haqking on 2011-11-02
as already mentioned.  A virus can easily infect the guest OS just as usual, as to whether it can propogate or not depends on how things are setup as already mentioned shared folders, network traffic (email etc).

However there are no known linux Viruses in the wild so it is unlikely you will get one, if your VM is windows then as mentioned a virus is written for a given target OS and so a Windows virus will not necessarily infect the Linux host, though not impossible for it to be written to do so, similar to viruses in Wine.

Cheers

---

### Post by argoz17 on 2011-11-02
My host is MAC OSX and my OS on VM is Ubuntu 10.10

---

### Post by argoz17 on 2011-11-02
My host is MAC OSX and my OS on VM is Ubuntu 10.10

---

### Post by jonkiribati on 2011-11-02
Only the guest machine gets virused. But that can depend on you're configuration if you're machines are sharing files, applications and other stuff they could be virused (espacially if they are Windows).

---

### Post by doorknob60 on 2011-11-02
> **argoz17 said:**
> My host is MAC OSX and my OS on VM is Ubuntu 10.10
In that case you truly have nothing to worry about, since there is almost no malware for either of those OSes, particularly Ubuntu. Windows is maybe a different story, but don't worry about anything, just use common sense on the internet and you should be fine (on any OS).

---

### Post by Linuxratty on 2011-11-02
I always thought Windows was safe from infections if it was in a vb.Thanks for explaining.

---

### Post by wolfen69 on 2011-11-02
> **Linuxratty said:**
> I always thought Windows was safe from infections if it was in a vb.Thanks for explaining.

Well, for all practical purposes, it *is* a real install. And if you go online with it, sure, you can get viruses just like a stand alone install. Vbox is just a container of sorts for an OS.

---

