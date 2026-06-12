---
title: "turn off display backlight on ubuntu server"
date: 2009-03-16
forum: Server Platforms
---

### Post by shinew on 2009-03-16
Hello, I have a dell xps laptop running Ubuntu Server 8.10. I can't figure out how to turn the display's backlight off. Can anyone help?

thank you very much!

---

### Post by 2buntu on 2009-04-17
I was looking to turn off the LCD backlight on a Dell Inspiron 2650 running Ubuntu Server 8.04.2. I found: [http://www.installationexperiences.com/2009/01/turn-off-lcd-display-backlight-with.html](http://www.installationexperiences.com/2009/01/turn-off-lcd-display-backlight-with.html)
I tested by connecting to the laptop via SSH and doing
1. sudo apt-get install vbetool
2. sudo vbetool dpms off
3. sudo vbetool dpms on
4. sudo vbetool dpms off
I'm pretty new to Linux, so I don't know what the side effect to this are, but I'm happy so far, and hope this helps.

---

### Post by shinew on 2009-04-17
Hi 2buntu, although I've noticed that it actually turns itself off after a while, thanks for the reply and vbetool works great! good to know.

---

### Post by juancarlospaco on 2009-04-17
**xset dpms force off**

*(without installing nothing)*

---

### Post by shinew on 2009-04-17
> **juancarlospaco said:**
> **xset dpms force off**

*(without installing nothing)*
that does not work. Unlike vbetool, xset is a "X" level utility. vbetool is already in all my systems by default(Intrepid, 8.10 desktop & server, Mint Felicia 64-bit), so I didn't have to install anything.

---

### Post by Stevan on 2010-08-19
The added benefit of using xset is you don't have to use sudo to get the access to shut down the monitor.

---

### Post by Mi11z on 2010-09-25
Thanks, the information here helped me out too, cheers.

---

