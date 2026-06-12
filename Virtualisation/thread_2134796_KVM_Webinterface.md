---
title: "KVM Webinterface"
date: 2013-04-12
forum: Virtualisation
---

### Post by Toxic64 on 2013-04-12
Hi, 

I have an Ubuntu server 12.04 (no GUI of course) I wanted to setup KVM which seems to be fairly easy.

I would like to know if there was some kind of easy webinterface I could setup up for my users to create and administrate their VMs? 

I tried Archipel which seemed to be apropriated but I couldn't figure out how to get it up and running.

---

### Post by CharlesA on 2013-04-13
Archipel looks handy, but the underlying framework looks... complicated. The install guide is here:
[https://github.com/ArchipelProject/Archipel/wiki/Installation-manual](https://github.com/ArchipelProject/Archipel/wiki/Installation-manual)

There are also a few different management tools for KVM. I know a few people who swear by virt-manager
[http://www.linux-kvm.org/page/Management_Tools](http://www.linux-kvm.org/page/Management_Tools)

---

### Post by Toxic64 on 2013-04-13
Hi, Thanks a lot for your answers.

[HTML]Archipel looks handy, but the underlying framework looks... complicated. The install guide is here:
https://github.com/ArchipelProject/A...llation-manual[/HTML]

That's exactly the guide I used, this software seems indeed handy but installation is a nightmare.

[HTML]There are also a few different management tools for KVM. I know a few people who swear by virt-manager
http://www.linux-kvm.org/page/Management_Tools[/HTML]

 I think I'll give a try to a few of these though a webinterface was prefered because of the multiple OS in the company.
any feedback on any of those?

Ok, I just gave a try to webvirtmgr. 
Pretty much all I needed I think, the installation is straight forward, the configuration is simple enough and the interface is very user friendly so I guess that ll be it.

Thanks CharlesA (btw very nice avatar ;) ).
[h=1][/h]

---

### Post by CharlesA on 2013-04-13
> **Toxic64 said:**
> Ok, I just gave a try to webvirtmgr. 
Pretty much all I needed I think, the installation is straight forward, the configuration is simple enough and the interface is very user friendly so I guess that ll be it.

Thanks CharlesA (btw very nice avatar ;) ).
[h=1][/h]

Thanks for the feedback. I was a bit overwhelmed when I saw the variety of management tools for KVM. I'll keep that one in mind, thanks. :)

---

