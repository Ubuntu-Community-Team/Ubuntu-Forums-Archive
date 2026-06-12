---
title: "Kiosk mode - overlayroot using physical partition"
date: 2019-11-04
forum: Security
---

### Post by domstoppable on 2019-11-04
Greetings, all!

I'm trying to setup a kiosk-like, resettable environment using overlayroot. The standard configuration for overlayroot uses tmpfs, and that works great except I need my users to have more space than my machines have RAM. I seem to have overlayroot working with a separate partition, rather than tmpfs, with one small problem - I need to wipe out all changes on the upper filesystem between reboots.

I think the most reliable strategy would be to do this "wipe" on bootup as early as possible, but I'm not sure the right way to actually do that. Can anyone point me in the right direction?

---

### Post by sudodus on 2019-11-05
Have you considered the security aspects of wiping on boot instead of wiping on shutdown?

---

### Post by domstoppable on 2019-11-05
> **sudodus said:**
> Have you considered the security aspects of wiping on boot instead of wiping on shutdown?

Not a concern for this use case. If you're curious, we're using it for UX testing some software. Participants will come in for just a 1-2 hour session to evaluate a product. They'll be allowed to install whatever they want/need for their session, but we need a clean-slate between participants. Although they could, participants never have a reason to login to any personal accounts. Plus, the device is never accessible to the general public, and a researcher is always in the room with it. So security is basically a non-issue for us.

Having said that, wiping on shutdown would probably work for us too - it just seemed like wiping on boot would be more consistent/guaranteed. Honestly though, I'm open to other ideas (except containers).

---

### Post by sudodus on 2019-11-05
- One way get 'more RAM' is to use part of it as **zram** (compressed RAM for swap). This is used in Lubuntu live (when booted live for example from a USB drive). Such a system can be installed into the internal drive if you wish, and it might or might not provide enough memory for the tasks. - It might be worth trying.

- Knowing your use case I agree that it would be OK to wipe the overlay of your current system on boot.

- If you cannot get that to work, you could boot a separate system (from a persistent live drive or from a system installed alongside the test system) and this system's main or only task is to wipe the overlay of your test system.

---

### Post by domstoppable on 2019-11-05
Thanks for the thoughtful response :)

> **sudodus said:**
> - One way get 'more RAM' is to use part of it as **zram** (compressed RAM for swap). This is used in Lubuntu live (when booted live for example from a USB drive). Such a system can be installed into the internal drive if you wish, and it might or might not provide enough memory for the tasks. - It might be worth trying.

That's an interesting idea I hadn't though of. Although, in some cases, participants may need 10's of gigs of disk space, and I have some concerns about performance. We want our participants to have an experience to match their real-world experience as much as possible, and compressed RAM sounds like it might take a performance hit.

> **sudodus said:**
> - Knowing your use case I agree that it would be OK to wipe the overlay of your current system on boot.

- If you cannot get that to work, you could boot a separate system (from a persistent live drive or from a system installed alongside the test system) and this system's main or only task is to wipe the overlay of your test system.

I thought about adding a separate GRUB entry to do exactly that, but I don't feel great about relying on our researchers to remember to do this. I think it's possible to automate switching around the default GRUB entry to do this, but that feels a little more fragile and kludgy than what I'm comfortable with.

I came up with this systemd solution for dumping the overlay content when shutting down:

```
[Unit]
Description=Wipe overlay FS
DefaultDependencies=no

[Service]
Type=oneshot
ExecStart=/bin/sh -c 'OVERLAY_PATH=$$(mount | grep -o ",upperdir=[^,]*" | cut -d "=" -f 2); exec find "$$OVERLAY_PATH" -maxdepth 1 ! -name 'media' ! -path "$$OVERLAY_PATH" -type d -exec rm -rf {} +'

[Install]
WantedBy=halt.target reboot.target shutdown.target
```


Being entirely new to overlayroot and overlayfs though, I'm worried that  this solution overlooks some important detail that I don't have enough  knowledge to even realize. Plus, I think I'd still prefer to do it on boot if I could figure out how to juggle it correctly. So this appears to be working for me for now, but I'd love for another set of eyes to look it over or for any other insights people might have.

---

### Post by sudodus on 2019-11-06
I must admit that you know much more about tampering with systemd than I. (I understand the commands in the ExecStart line, but I can't tell if you have overlooked some important detail.)

Let us hope that someone who really understands these things will chip in and help you.

Otherwise, if you test it and you find that it works, that **rm -rf** at the end of the ExecStart line does its job at the correct location, enjoy :-)

---

