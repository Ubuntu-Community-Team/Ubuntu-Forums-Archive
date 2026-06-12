---
title: "Virtual Machine (Ubuntu) of actual Hard Drive in Windows 7"
date: 2014-06-13
forum: Virtualisation
---

### Post by quadrplax on 2014-06-13
I tried posting this on the Windows 7 forums first, but it didn't get any attention. Maybe here is a better place anyway.
> Not sure if I should post this here or on Ubuntu Forums...lol
I want to get a second hard drive for my computer, and install Ubuntu to  it, allowing me to boot into it directly. I also would like to be able  to use the same installation in a virtual machine within Windows 7. I've  found other people talking about this, but they wanted the virtual OS  to be Windows, which is harder than Ubuntu since it doesn't get attached  to hardware as much. So, is this possible?

---

### Post by TheFu on 2014-06-13
Never tried this myself, but the idea is workable with Linux inside the VM.  There will likely be different ethernet devices - different models, can't be helped.  

Please post if you get this working.  [http://www.virtualbox.org/manual/ch09.html#idp57804112](http://www.virtualbox.org/manual/ch09.html#idp57804112) says that improper use could lead to "total loss of data".   That is too rich for my blood. I prefer not to bet with my data.

In another thread over there, the site moderator says, "ps. I'm reluctant to get any further into a conversation regarding raw disk access. It's supposed to be an expert level feature, meaning that people qualified to use it should not require technical support."

---

### Post by quadrplax on 2014-06-14
[This is a response to a removed post]

The same thing happened on Windows 7 forums, apparently people can't  read lol. You can't remove posts AFAIK, but you can edit them to just  say [deleted] or something

---

### Post by sudodus on 2014-06-14
You can report a post (the square icon at the bottom left corner of the post area), and ask a moderator to move or remove it if you wish. (I don't tell you to do it, only tell you about it as a service. Since I am here posting now, you can also ask directly in a reply.)

-o-

*@quadrplax*,

I think it is possible to use a drive in KVM - virt-manager (but that is with a linux host). I haven't done it myself, but I have mounted an image of a drive to a device, for example /dev/sdb and then booted a virtual machine from it. It worked like a charm for me. I think it should work with 'a real drive' identified as /dev/sdb too. But I don't know if there is some corresponding way of doing it with a Windows host.

TheFu is the most experienced person that has contributed in your thread (so far). Please read their post (#2) carefully again.

Finally,*** backup*** your data before trying, since this is risky.

---

