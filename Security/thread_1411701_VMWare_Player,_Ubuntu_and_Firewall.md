---
title: "VMWare Player, Ubuntu and Firewall"
date: 2010-02-20
forum: Security
---

### Post by Advait on 2010-02-20
Hi All,

I've got Firefox running in Ubuntu 9.1 which is running in VMWare Player 3 which is running on top of Win7 64bit. I've got a good firewall (Blink) always running in Windows.

Question: Does all the IP traffic for Ubuntu go thru my Windows firewall? Or do I need to setup a firewall in Ubuntu?

I installed and enabled gufw in Ubuntu just in case. Is gufw really needed in my case? On the other hand I'm guessing that having 2 firewalls running doesn't hurt.

Thanks,

Tom the Uber Newbie

---

### Post by cariboo on 2010-02-20
If you aren't running any services, there is no need for a firewall. TO check if you have any services running. Go to System->Administration->Network Tools->Port Scan. It will in a default installation show that port 631 is listening, you don't have to worry about that, as it is the cups printing daemon listening on 127.0.0.1 only.

There may be some higher port numbers, that change every time you click the scan button, these are false positives caused by a bug in the program, it is well known, and we are waiting for the upstream devs to fix it.

---

### Post by Advait on 2010-02-20
Thanks for the info. If I understand you, in my particular setup, all the IP traffic for my Ubuntu *is* going in and out of my Windows firewall? Is that true?

Thanks!

Tom the Uber Newbie

---

