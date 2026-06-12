---
title: "Ubuntu Server 23.10 hangs during shutdown/reset"
date: 2023-11-14
forum: Server Platforms
---

### Post by menskiz0r on 2023-11-14
Well as title says the reboot/shutdown process reaches the message

[OK] Reached target poweroff.target  - System Power Off

so I have to REISUB each time to reboot

any ideas? any specific logs I should provide?

---

### Post by darkod on 2023-11-14
What exactly are you using to power off the server, is it 'sudo poweroff'? And for restart you use 'sudo reboot'?

It might be a clash with your hardware or another thing. In any case I wouldn't be too worried how 23.10 acts since it is not a LTS release and people shouldn't be using it for important tasks anyway. Use only LTS for your servers.

---

### Post by MAFoElffen on 2023-11-15
You might want to join this bug as also effected. This came up as affecting 2 people during the beta testing stage of Mantic:
[https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987)
Although those 2 people were on Desktop. They would be very interested to learn that it also affects 23.10 Server.

I have another machine that has a sort of twist to that, where (just) on reboot, it reboots directly to the BIOS Boot Menu, then gets stuck in a boot loop back to that BIOS Boot Menu... Until it is hard-powered down, and booted from cold.

I haven't seen any of these problem with DEV 24.04 yet... Crossing fingers.

---

### Post by menskiz0r on 2023-11-15
> **darkod said:**
> What exactly are you using to power off the server, is it 'sudo poweroff'? And for restart you use 'sudo reboot'?

It might be a clash with your hardware or another thing. In any case I wouldn't be too worried how 23.10 acts since it is not a LTS release and people shouldn't be using it for important tasks anyway. Use only LTS for your servers.


Tried both 'sudo poweroff' and 'sudo shutdown -h now', same result, same with the reboot.

---

### Post by menskiz0r on 2023-11-15
> **MAFoElffen said:**
> You might want to join this bug as also effected. This came up as affecting 2 people during the beta testing stage of Mantic:
[https://bugs.launchpad.net/ubuntu/+bug/2036987](https://bugs.launchpad.net/ubuntu/+bug/2036987)
Although those 2 people were on Desktop. They would be very interested to learn that it also affects 23.10 Server.

I have another machine that has a sort of twist to that, where (just) on reboot, it reboots directly to the BIOS Boot Menu, then gets stuck in a boot loop back to that BIOS Boot Menu... Until it is hard-powered down, and booted from cold.

I haven't seen any of these problem with DEV 24.04 yet... Crossing fingers.

Weeeell it's technically a desktop but it serves lol. That BIOS story is straight out of a nightmare

I will check out 24.04, thanks for the tip

---

### Post by MAFoElffen on 2023-11-16
I test the Dev Builds, currently testing DEV Noble. It is still early pre-alfa. So expect lots of updates and changes from day to day. No-where near stable.

For installers in the Daily builds, Server Edition is working now. Desktop is not. 

If you were talking Server, my tests should okay. Desktop still has some issues. Right now you can only get to desktop by upgrading via "debian-upgrade" method (shown below), or via installing the Noble Server, and then installing 'ubuntu-desktop'.

You can upgrade to the release using 
```

sudo sed -i 's/mantic/noble/g' /etc/sources.list

```
If you are dead-set on testing Noble... Since you have an unknown cause of the error, I would recommend installing fresh from the latest daily build Noble Server ISO.

---

