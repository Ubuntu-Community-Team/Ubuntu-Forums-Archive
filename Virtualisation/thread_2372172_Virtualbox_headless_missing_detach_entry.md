---
title: "Virtualbox headless missing detach entry"
date: 2017-09-22
forum: Virtualisation
---

### Post by accounts0 on 2017-09-22
Ubuntu server 16.04.3 with Kubuntu installed, using Virtualbox Version 5.1.28 r117968 (Qt5.5.1) from official repo, host UEFI on with signed kernel modules, Windows 7 Ultimate x64 guest.

When I start the guest in headless mode the option to detach with guest still running is missing when I click the X close button on the guest's Virtualbox window. However the main Virtualbox window shows a 'Show' button as if it's window could be closed...

Screenshot:
[https://imgur.com/a/x55gW](https://imgur.com/a/x55gW)

---

### Post by accounts0 on 2017-09-25
Bump

---

### Post by accounts0 on 2017-10-17
bump

---

### Post by accounts0 on 2017-10-26
I'd like to mention that recently (though I don't recall exactly when), I've updated Virtualbox to Version 5.1.30 r118389 (Qt5.5.1).

And unfortunately, the issue persists.

---

### Post by SeijiSensei on 2017-10-27
Have you installed the extension pack?

---

### Post by accounts0 on 2017-10-27
> **SeijiSensei said:**
> Have you installed the extension pack?

No, I'd be a commercial user & they only have volume licensing at some enormous number no mere mortal can afford.

---

### Post by accounts0 on 2017-11-05
bump

---

### Post by accounts0 on 2017-12-01
Is the extension pack really necessary for this functionality?

---

### Post by accounts0 on 2017-12-13
Since I've received no reply here I'm tempted to try & see if the missing 'Detach' option appears if I were to install the Extension Pack. Can anyone tell me at least if I can uninstall it easily with no problems after I try & see? I've never seen a way to do so being that it's a file extension that opens with the VirtualBox Manager- IIRC there's no way to remove an added package like that. So I'm hesitant to move forward without knowing ahead of time.

---

### Post by QIII on 2017-12-13
I'm not sure why you would want to remove the extension pack.  Are you really a commercial user?  Is that not part of the cost of doing business?

---

### Post by accounts0 on 2017-12-13
> **QIII said:**
> I'm not sure why you would want to remove the extension pack. Are you really a commercial user? Did you pay for a bulk license for VBox?

Only the ext pack isn't FOSS. I freelance occasionally & use Adobe CS4 on Windows in the VM. Wasn't an issue until I switched from KVM to Oracle. The missing button is a minor issue, tbh. Just annoying that I don't know why- I keep wondering if I can fix it somehow.

"https://www.virtualbox.org/wiki/VirtualBox_PUEL"
```
§ 2 Grant of license. Oracle grants you a personal, non-exclusive, non-transferable, limited license without fees to reproduce, install, execute, and use internally the Product on Host Computers for your Personal Use, Educational Use, or Evaluation. &#8220;Personal Use&#8221; is noncommercial use solely by the person downloading the Product from Oracle on a single Host Computer, provided that no more than one client or remote computer is connected to that Host Computer and that client or remote computer is used solely to remotely view the Guest Computer(s). 
```

"https://shop.oracle.com"

```
US$50.00 / Named User Plus
Store minimum order quantity: 100
```

---

### Post by QIII on 2017-12-13
I'd contact their legal department.  I highly doubt that you'd be considered a commercial user under those terms.

If you would like to try it out on your personal computer to see if the functionality you desire is there, that would certainly be non-commercial.  If you are uncomfortable using it thereafter, you could just uninstall VBox altogether and reinstall it.

It's been a long time now since I've used VBox, so I'm not sure if that exists.

---

### Post by accounts0 on 2017-12-13
> **QIII said:**
> you could just uninstall VBox altogether and reinstall it.

That's exactly what I don't want to have to go through. Oh, well. I've spent enough time on this now, will give up.

Thanks for taking the time to reply here.

---

### Post by QIII on 2017-12-13
You can uninstall and reinstall VBox without affecting your VMs at all.  It's not terribly troublesome.

When you start your VMs, do you choose "Detachable Start"?

How about  using Machine --> Detach GUI?

---

