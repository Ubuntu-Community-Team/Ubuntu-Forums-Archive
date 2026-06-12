---
title: "Enabling Wide-screen in VMPlayer"
date: 2008-01-08
forum: Virtualisation
---

### Post by Origin on 2008-01-08
I've been using XP Pro (32 bit) on my VMPlayer on my 64-bit Gutsy installation for some time now, but I've become a bit sick of not being able to utilize my wide-screen capabilities. Ubuntu natively runs 1280x768 just fine, but the virtual machine is restricted to regular 4:3 dimensions.

Do I have to install server or workstation instead? Does the vmplayer not suffice?

---

### Post by dcstar on 2008-01-08
> **Origin said:**
> I've been using XP Pro (32 bit) on my VMPlayer on my 64-bit Gutsy installation for some time now, but I've become a bit sick of not being able to utilize my wide-screen capabilities. Ubuntu natively runs 1280x768 just fine, but the virtual machine is restricted to regular 4:3 dimensions.

Do I have to install server or workstation instead? Does the vmplayer not suffice?

You must install vmware tools on the XP vm.

---

### Post by Origin on 2008-01-09
> **dcstar said:**
> You must install vmware tools on the XP vm.

So I don't need VMware server, and player will work? I just need to find vmware tools and install that onto my virtual XP?

Unfortunately [http://pubs.vmware.com/server1/vm/wwhelp/wwhimpl/common/html/wwhelp.htm?context=vm&file=tools_server.4.3.html](http://pubs.vmware.com/server1/vm/wwhelp/wwhimpl/common/html/wwhelp.htm?context=vm&file=tools_server.4.3.html) doesn't tell me enough about how to get VMware tools and install it...

---

### Post by dcstar on 2008-01-09
> **Origin said:**
> So I don't need VMware server, and player will work? I just need to find vmware tools and install that onto my virtual XP?

Unfortunately [http://pubs.vmware.com/server1/vm/wwhelp/wwhimpl/common/html/wwhelp.htm?context=vm&file=tools_server.4.3.html](http://pubs.vmware.com/server1/vm/wwhelp/wwhimpl/common/html/wwhelp.htm?context=vm&file=tools_server.4.3.html) doesn't tell me enough about how to get VMware tools and install it...

I have no idea where it is on player, but in server you just do VM-Install VMware tools once you have the client running.

---

