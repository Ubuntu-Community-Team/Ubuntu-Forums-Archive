---
title: "When will the daily build move to the planned kernel for 22.10?"
date: 2022-08-20
forum: Ubuntu Development Version
---

### Post by morrownr on 2022-08-20
It has been a long time since I checked the dev flow for new releases so there are some things that I need some information about.

Reason for post: The new mt7921u driver was recently mainlined in kernel 5.18 and AP mode support showed up in kernel 5.19. Firmware updates are required for AP mode support. New USB WiFi adapters using the new mt7921au chipset (the mt7921u driver supports this) are now available. See menu item 2 at:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

What I intended to do was check the daily build of 22.10 to see if I needed to post bugs if the mt7921au support is not right. Well, I downloaded the daily yesterday and installed it. No driver and old firmware. I then checked kernel version and it is 5.15. I'm scratching my head. We are half way through the dev cycle and the kernel is the one from the last release? Please educate me on what I am missing.

Regards,

Nick

---

### Post by jbicha on 2022-08-20
There is a newer kernel (5.19) in kinetic-proposed.

It's generally a bad idea to install things from -proposed in the development release. Things are only stuck there if they fail testing or other requirements. It will get unstuck once it meet's Ubuntu's minimum quality standards.

It's possible to briefly enable -proposed to install specific things. But there are risks and it's easy to make mistakes that could cause you major problems.

---

### Post by mikewhatever on 2022-08-20
Well, there is no rule that half way through it has to switch to a newer kernel. Looking at the release schedule, the Kernel Feature Freeze is planned for September 22, so the newer kernel should be in by then.
[https://discourse.ubuntu.com/t/kinetic-kudu-release-schedule/27263](https://discourse.ubuntu.com/t/kinetic-kudu-release-schedule/27263)

---

### Post by xyz-t on 2022-08-21
You can always get it manually there (4 debian packages):


 [https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](https://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)


 Then run this one by one:

```
[FONT=monospace][COLOR=#000000]cd //home/your_user_name/Downloads[/COLOR][/FONT]
```
```
[FONT=monospace][COLOR=#000000]sudo dpkg -i *.deb[/COLOR][/FONT]
``` 


[FONT=monospace]Restart after and make sure secure boot is disabled.

[/FONT]You can also try to install synaptic and search for it inside the app witout touching Proposed.:

 1-linux-image
 2-linux-headers
 3-linux-modules

 Mark them all to install and apply changes. Ask if not sure.

[FONT=monospace]
[/FONT]

---

### Post by morrownr on 2022-08-22
> There is a newer kernel (5.19) in kinetic-proposed.

Where is kinetic-proposed?

> It's generally a bad idea to install things from -proposed in the development release.

I have no intention to install anything from -proposed. I just wanted to look at a couple of things.

Thanks

---

### Post by xyz-t on 2022-08-26
> **morrownr said:**
> > There is a newer kernel (5.19) in kinetic-proposed.

Where is kinetic-proposed?

Thanks

5.19 was not available in Synaptic in Ku 20220820 ISO.

The proposed location is in the software source and it is called pre-released updates. It must be enabled by the user. Deselecting this option closes the repo. Now that Kernel 5.18 has reached EOL on the 21st, 5.19 should be available sooner or later.

---

### Post by luckyknight on 2022-09-01
I was wondering the same here - when will daily update to a more recent linux kernel?

I've tried installing 5.19.6 myself on 22.04 but as I am using secure boot I just run into issues:

[COLOR=#24292F][FONT=-apple-system]"
error: bad shim signature.
error: you need to load the kernel first.[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]Press any key to continue.."

[/FONT][/COLOR]I have a ASUS G14 2022 model and my keyboard backlight is not functioning under 5.15. I need 5.17+ to use asusctl as well.

---

### Post by xyz-t on 2022-09-01
> **luckyknight said:**
> [COLOR=#24292F][FONT=-apple-system]"
error: bad shim signature.
error: you need to load the kernel first.[/FONT][/COLOR]
[COLOR=#24292F][FONT=-apple-system]Press any key to continue.."[/FONT][/COLOR]

You must boot in MoKmanager blue screen to keep secure boot enabled with an unsigned Kernel:

```
sudo mokutil --disable-validation
```


Enter the root password and select twice 12345678 as Mok password. Question to answer is YES to change secure boot state. Enter the given digit(s) to change secure boot state. The machine will be booting with the following message: Booting in insecure mode. Repeat above to turn it off with -*-enable-validation*.

Shim signature bypasses secure boot and allows you to keep it enabled. If you don't feel comfortable with MoKmanager, you should wait or turn off secure boot.

---

### Post by jbicha on 2022-09-02
5.19 landed today. 5.19 is expected to be the major version that Ubuntu 22.10 will use.

However, there is an issue with creating new daily ISOs so there hasn't been a new "daily build" ISO for a few days now.

---

### Post by luckyknight on 2022-09-03
Thanks for the heads up. Upgraded from 22.04 to the development version successfully.

---

### Post by luckyknight on 2022-10-03
Kernel 6.0 was released yesterday. Will 22.10 feature this as the kernel freeze isn't until 6th October?

---

### Post by deadflowr on 2022-10-03
> **luckyknight said:**
> Kernel 6.0 was released yesterday. Will 22.10 feature this as the kernel freeze isn't until 6th October?

No.
[https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/64]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664/64")

---

