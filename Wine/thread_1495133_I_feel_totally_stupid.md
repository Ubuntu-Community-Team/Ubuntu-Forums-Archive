---
title: "I feel totally stupid"
date: 2010-05-27
forum: Wine
---

### Post by Yehudah on 2010-05-27
I've had Ubuntu 8 - 10 for more than a year now.. and like it much better than windoze.

Problem:  I need two things, one of them involves WINE.  I need to be able to use Tether in Wine so I can use my blackberry as a modem.

I have the setup.exe file in the download folder, but it doesn't look like it's associate with WINE, and when I double click, it gives me some hoo haa about why I can't launch and executable.

I installed WINE from the WINEHQ site (1.0 I think).

Ugh... now what?:confused:

---

### Post by cogadh on 2010-05-27
I seriously doubt its going to work. Tether most likely operates via a Windows device driver and Windows device drivers do not and never will work in Wine. However, in the interests of confirming that, we can try to help, but you're going to need to help us a bit first. First, you need to be certain about the Wine version you have installed. Second, the specific "hoo haa" message you got might be helpful. Third, try running the setup from the terminal to get Wine's error output and post it here.

---

### Post by hikaricore on 2010-05-27
Yea never gonna happen.
If your device isn't recognized as a modem/network device by linux, nothing you do in wine will change that.

---

### Post by ghormley on 2011-07-07
With respect to Tether, you don't need it.  I used my Blackberry as a modem with my 10.04 laptop on a train ride from North Carolina to Texas without any problem or cost for software where there was cell service for my data plan.

Go to [http://www.berry4all.com/home](http://www.berry4all.com/home) and see how it's done with only a free script available there.

Works like a top for me.  Good luck.:)

---

