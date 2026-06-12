---
title: "SmoothWall + 2Wire modem/router = not so smooth"
date: 2012-02-28
forum: Security
---

### Post by youngunix on 2012-02-28
I'm trying to set up SmoothWall like the following:

**AT&T UVerse modem/router --->SmoothWall box ---> AT&T 2Wire modem/router ---> wired/wireless Devices.**

1. I've installed SmoothWall on a box with **two NICs**. 
2. Configured it following these steps: [http://www.youtube.com/watch?v=2w28gn5nDlM](http://www.youtube.com/watch?v=2w28gn5nDlM)
3. Connected **Red to Uverse** and **Green to 2wire**, and no go. SW is not pushing the connection through to 2Wire.

Is there any configuration that needs to be done to the 2Wire for it work?

Thanks.

---

### Post by Dngrsone on 2012-02-29
You need to turn the 2 wire router into a wireless access point.

I'd first look in the documentation that came with your router, and failing that, do a web search with the specific model and the term "access point" and see if there are specific instructions.

If you are going to use the Smoothwall for DHCP, then you will have to disable turn off DHCP on the router.

You can also search for answers and, failing that, posit the question on the [Smoothwall Forums](http://community.smoothwall.org/forum/index.php).

---

### Post by mr-woof on 2012-03-01
do you get a network connection on a wired/wireless device connected to the 2 wire?

Can you connect to the web gui of the smoothwall box?

If yes to the above, when you setup the smoothwall what did you put as the dns?

---

### Post by Dngrsone on 2012-03-01
That reminds me-- on your client computers, it is essential you turn off any software firewalls, and set the DNS to the Smoothwall IP.

If you don't do that, then internet will be slow and unreliable.

---

### Post by youngunix on 2012-03-01
Thank you guys for the replies.
I've done some research and decided that a stand alone box running SWE is kind of an overkill, plus the electricity bill will show some increase. Going to to get a good wireless router that'll support DD-WRT, I believe it'll do the same as SWE, besides all the devices on the network have their own firewall software.

---

### Post by Dngrsone on 2012-03-01
I use Smoothwall with CLAMAV and Dan's Guardian content filtering.

---

