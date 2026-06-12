---
title: "Connect to server -&gt; You entered an invalid"
date: 2010-12-16
forum: Server Platforms
---

### Post by anotherli on 2010-12-16
I have installed netatalk on a Ubuntu Server 10.10 and I am trying to connect to it from a mac client.
I am 100% positive that this has worked before. It just stopped working during the weekend.
I have used the Mac's terminal to ssh into the ubuntu server to do all the work and it has worked fine.

But when I try to connect to it via finder:
afp://<ip-adress>

First I get the log in pop-up. No problem.
"Enter your name and password for the server 'virtserv'"
It can get the host name so it looks fine.

I enter same username and password I use to ssh but then I get the error message:
"**You entered an invalid username or password**."
"Please try again."

Why oh why?

---

### Post by anotherli on 2010-12-21
Solved it... somehow.

---

### Post by makaki on 2011-01-15
Please can you tell me how did you solve it?! I get the same error!

---

### Post by anotherli on 2011-01-19
> **makaki said:**
> Please can you tell me how did you solve it?! I get the same error!

Sorry no. It just magically started working again. Try reinstalling, I guess.

---

### Post by justin007827 on 2011-03-21
I am experiencing the same problem on 10.10. A reinstall did not solve it. Could someone please help me.

---

### Post by theDominik on 2011-05-10
I followed [this thread](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#netatalk2) to install Netatalk and Avahi.

Everything seems to work, I can also see my Ubuntu machine in the Finder. But when I try to "connect as..." I get the error mentioned above. ("You entered an invalid username or password." "Please try again.")

Using afp://<user>@<ip> doesn't work too.
SSH login is working fine.

Any ideas?

I think something with Netatalk is wrong.

---

### Post by theDominik on 2011-05-10
I found a solution for my problem!

**Step by step**

1) Type in terminal: "sudo nano /etc/netatalk/afpd.conf"
2) Scroll down to the end of the file using your "down arrow".
3) Previously I used "- -transall -uamlist uams_randnum.so,uams_dhx.so -nosavepassword"
4) Changed it to "- -transall -uamlist uams_randnum.so,uams_dhx2.so -nosavepassword" (notice the "2")
5) Save changes: press CTRL+X, then press Y, then ENTER
7) Restart your netatalk: "sudo /etc/init.d/netatalk restart"
8) Done.

Thank you [Ali](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/#comment-48859)

---

