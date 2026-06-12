---
title: "so wireshark won't save my captures..."
date: 2010-05-09
forum: Security
---

### Post by gregnorc on 2010-05-09
So I downloaded wireshark via apt, and at first it was not showing any interfaces when launched from the applications menu.

However, going into a terminal and running it as root ("sudo wireshark") allows me to see all my interfaces...

I seem to be able to capture (I might not be going into promoscuous mode properly, but I think I'm probably just misconfiguring something, gonna readn through the documentation again)

The problem is, when I go to save a capture, I get an error. I am running as root, but when I tried to save the capture to the home directory of my main account, I get an error that permission was denied.

This seems _really_ odd... if Wireshark is running as root, shouldn't it pretty much be able to do whatever it wants (eg write a file anywhere)?

I can save captures to the main root directory, but I'd like to be able to save them elsewhere. Anyone encountered anything like this?

---

### Post by bobnutfield on 2010-05-09
> **gregnorc said:**
> So I downloaded wireshark via apt, and at first it was not showing any interfaces when launched from the applications menu.

However, going into a terminal and running it as root ("sudo wireshark") allows me to see all my interfaces...

I seem to be able to capture (I might not be going into promoscuous mode properly, but I think I'm probably just misconfiguring something, gonna readn through the documentation again)

The problem is, when I go to save a capture, I get an error. I am running as root, but when I tried to save the capture to the home directory of my main account, I get an error that permission was denied.

This seems _really_ odd... if Wireshark is running as root, shouldn't it pretty much be able to do whatever it wants (eg write a file anywhere)?

I can save captures to the main root directory, but I'd like to be able to save them elsewhere. Anyone encountered anything like this?

From the wireshark help files:

> setcap 'CAP_NET_RAW+eip CAP_NET_ADMIN+eip' /usr/bin/dumpcap

This allows you to run wireshark as normal user (GUI), and as normal user you should be able to save your captures to your home folder.

---

### Post by Rubi1200 on 2010-05-09
Please do NOT run Wireshark as root; were there to be a security flaw and an escalation of privileges it could affect your whole system.

As suggested by one of the more experienced users on this forum, cdenley, run these commands and then you should be able to see and capture on any interface without the need to escalate privileges.

sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap

Run the commands one at a time.

Good luck!

---

### Post by davidsrsb on 2010-05-18
Thanks for that, working with 10.04

Any idea how to make Etherape work as non-root too?

---

### Post by Rubi1200 on 2010-05-18
> **davidsrsb said:**
> Thanks for that, working with 10.04

Any idea how to make Etherape work as non-root too?

No problem, I am glad it is up and running nicely.

Unfortunately, I cannot offer any help with Etherape. Hopefully someone will offer a solution.

Good luck!

---

### Post by uRock on 2010-05-18
Rubi1200, Wireshark doesn't allow you to select an interface if not opened by root. If I am wrong please help me do it the correct way.

Thanx,
Ronnie

---

### Post by Rubi1200 on 2010-05-18
Hi uRock, did you try setting it up the way I suggested?

> sudo apt-get install libcap2-bin wireshark
sudo chgrp admin /usr/bin/dumpcap
sudo chmod 750 /usr/bin/dumpcap
sudo setcap cap_net_raw,cap_net_admin+eip /usr/bin/dumpcap

Run the commands one at a time.

This method worked for me and a number of other users who I helped with this issue.

Running Wireshark as root is not recommended.

Let me know what happens.

(sorry if my questions seems obvious:oops:)

---

### Post by uRock on 2010-05-18
Yup, that worked.

Thanx,
uRock

---

### Post by Rubi1200 on 2010-05-18
No problem! :)

If you are interested, the following link is from bodhi.zazen's security sticky:

[http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

> [INDENT]WIRESHARK CONTAINS OVER ONE POINT FIVE MILLION LINES OF SOURCE CODE. DO NOT RUN THEM AS ROOT.
 [/INDENT] Indeed, due to the complexity and sheer number of its many protocol dissectors, Wireshark is inherently vulnerable to malformed traffic (accidental or otherwise), which may result in denial of service conditions or possibly arbitrary code execution.

---

