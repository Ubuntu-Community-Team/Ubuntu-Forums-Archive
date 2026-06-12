---
title: "Keeping an ssh session open forever"
date: 2010-03-27
forum: Server Platforms
---

### Post by R.Bucky on 2010-03-27
I stream my local police station dispatch on the web using an icecast/darkice configuration ([http://wacomputing.com](http://wacomputing.com)). The downside of using this software is that once you initiate darkice, a terminal has to be open - the process does not run in the background. 

I tried placing a monitor on my server (ouch, that hurt) and keeping darkice alive that way, but my mail server kicks the process. Now, I set the KeepAlive variable to something outrageous and keep an ssh session open on my desktop box to keep the stream going. Screen does not work as Postfix boots that as well. 

Any suggestions for keeping the process going indefinately?

---

### Post by stlsaint on 2010-03-27
See here. [KeepAlive]("http://www.howtogeek.com/howto/linux/keep-your-linux-ssh-session-from-disconnecting/")

---

### Post by Agent ME on 2010-03-27
> **R.Bucky said:**
> I tried placing a monitor on my server (ouch, that hurt) and keeping darkice alive that way, but my mail server kicks the process. ... Screen does not work as Postfix boots that as well.
Er, postfix is killing your processes? I don't have much experience with mail transfer programs but that doesn't quite sound right.

---

### Post by smeerbartje on 2010-03-28
You can also have a look at '[screen]("http://ubuntu-tutorials.com/2007/05/04/command-line-multitasking-with-screen/")'.

---

### Post by R.Bucky on 2010-03-28
Yup, used screen as mentioned earlier. For now, I'll just keep an open ssh session on my Ubuntu Desktop machine. Something will pop up eventually.

---

### Post by fang0654 on 2010-03-29
You can play around with the [nohup]("http://en.wikipedia.org/wiki/Nohup") command.

---

