---
title: "Issues of ubuntu server 12.04 on AMD A75 platform"
date: 2012-06-29
forum: Server Platforms
---

### Post by shadowlinyf on 2012-06-29
I tried to install ubuntu server 12.04 on the AMD A75(with APU A4 3300) platform.
The install process was smooth, but when the system is booted the display has no signal after grub screen.The system is not dead because the numlock still works.If I choose recovery mode in grub list then choose resume normal boot i can enter the system and everything seems fine.
So I think it is something wrong with the graphic driver,because if you choose the recovery mode the system will boot up with a minimal graphic setting.

I think the solution should be either to set the normal boot up by using the same graphic setting as the recovery mode or to find a proper graphic driver.

Does anyone have any idea what i should do?

---

### Post by nothingspecial on 2012-06-30
Moved to Server Platforms.

---

### Post by sandyd on 2012-06-30
> **shadowlinyf said:**
> I tried to install ubuntu server 12.04 on the AMD A75(with APU A4 3300) platform.
The install process was smooth, but when the system is booted the display has no signal after grub screen.The system is not dead because the numlock still works.If I choose recovery mode in grub list then choose resume normal boot i can enter the system and everything seems fine.
So I think it is something wrong with the graphic driver,because if you choose the recovery mode the system will boot up with a minimal graphic setting.

I think the solution should be either to set the normal boot up by using the same graphic setting as the recovery mode or to find a proper graphic driver.

Does anyone have any idea what i should do?
have you tried nomodeset?

---

