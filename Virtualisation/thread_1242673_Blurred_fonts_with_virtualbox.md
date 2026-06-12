---
title: "Blurred fonts with virtualbox"
date: 2009-08-17
forum: Virtualisation
---

### Post by running_rabbit07 on 2009-08-17
When using Sun VirtualBox is it normal for all of the font to go really blurry or is it something Compiz is doing?

Edit: So far this has happened every time I have cranked up VBox. Doesn't happen with any other program. I did the CPU test that was one of KVM site and my CPU came out as supported.

---

### Post by bodhi.zazen on 2009-08-17
Moved to it's own thread.

---

### Post by running_rabbit07 on 2009-08-17
Thanks for making the post into a thread.

If anyone can help me that would be great.

---

### Post by bodhi.zazen on 2009-08-17
Well, as you suggested in your OP, try disabling compiz.

---

### Post by running_rabbit07 on 2009-08-17
> **bodhi.zazen said:**
> Well, as you suggested in your OP, try disabling compiz.

Yeah, I guess I should've tried that first. That fixed it. Thanks.

---

### Post by swatkins on 2010-09-14
I use ubuntu, but I'm stuck with a windows desktop at work.  It's not all bad, I can use virtualbox and also Xming with our development server which runs linux.

Anyway, I'm using the latest virtualbox on windows and the fonts just within the virtualbox GUI itself are really blurry.  This doesn't seem to be related to the windows font / anti-aliasing settings.  I guess this is off-topic for an ubuntu forum but anyway maybe someone else experienced this and wound up in this thread!

---

### Post by manuleka on 2012-08-24
same experience here... although my platform: 
Host:  Mint 13 KDE
VBox:  v4.1.20
Guest: Windows XP Pro

changing font effect setting from standard to cleartype fixed mine

quick how to:
1. right click on desktop
2. select properties
3. go to appearance
4. select effect
5. change standard to cleartype (under use the following to smooth edges of screen fonts)
6. click ok then ok

done :)

---

