---
title: "unable to access usb in vbox"
date: 2012-03-06
forum: Virtualisation
---

### Post by gwpritch on 2012-03-06
I can't seem to get access to the usb system.  Everything works fine in ubuntu but in winxp running in virtualbox I have no access.
the problem seems to be in adding myself to the group vboxusers.

I have run ```
 sudo usermod -a -G vboxusers me
```

 If I look at the file /etc/groups, I am indeed a member, but if I run the command groups, vboxusers doesn't appear as one of the groups to which I am a member. Additionally I get an error message from vbox suggesting I add myself to the vboxusers group.
I am running the latest version of vbox from the oracle site and usb support is checked in the VM settings, yet my iphone and external backup drive are inaccessible.
Any thoughts?
Thanks in advance

---

### Post by haqking on 2012-03-06
> **gwpritch said:**
> I can't seem to get access to the usb system.  Everything works fine in ubuntu but in winxp running in virtualbox I have no access.
the problem seems to be in adding myself to the group vboxusers.

I have run ```
 sudo usermod -a -G vboxusers me
```

 If I look at the file /etc/groups, I am indeed a member, but if I run the command groups, vboxusers doesn't appear as one of the groups to which I am a member. Additionally I get an error message from vbox suggesting I add myself to the vboxusers group.
I am running the latest version of vbox from the oracle site and usb support is checked in the VM settings, yet my iphone and external backup drive are inaccessible.
Any thoughts?
Thanks in advance

have you logged out and back in to refresh your group membership.

---

### Post by Cheesemill on 2012-03-07
Have you installed the VirtualBox extension pack? It's required for USB access.

[https://www.virtualbox.org/wiki/Downloads](https://www.virtualbox.org/wiki/Downloads)

---

### Post by Grenage on 2012-03-07
Indeed, I don't think the repository version has USB functionality by default.

---

### Post by haqking on 2012-03-07
> **Grenage said:**
> Indeed, I don't think the repository version has USB functionality by default.

> **blogs said:**
> I don't think the repository version has USB functionality by default too.<snip>

The OP said

> I am running the latest version of vbox from the oracle site

But yes as mentioned you need the extensions pack also

You also need to logout and back in after adding yourself to the vboxusers group.

Cheers

---

### Post by gwpritch on 2012-03-07
Shoot me now!... Logging in and out again! Who'd have thought.
:oops:

Thanks for all the replies.

---

### Post by haqking on 2012-03-07
> **gwpritch said:**
> Shoot me now!... Logging in and out again! Who'd have thought.
:oops:

Thanks for all the replies.

no worries glad its solved.

Cheers

---

