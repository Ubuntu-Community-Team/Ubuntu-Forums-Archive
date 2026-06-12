---
title: "Worms on linux?"
date: 2006-09-01
forum: Server Platforms
---

### Post by mihalisla on 2006-09-01
Hello, i would like to know if a worm or virus can be installed on linux without users permission like in windows?
If yes is the antivirus the only security?
Thank you for reading this message:?:

---

### Post by doobit on 2006-09-01
> **mihalisla said:**
> Hello, i would like to know if a worm or virus can be installed on linux without users permission like in windows?
If yes is the antivirus the only security?
Thank you for reading this message:?:

Worms and viruses probably can be made affect Linux programs. However, Linux already has a variety of security measures in place already to help prevent this. The need for certain permissions to access every file is an example of this. Another example is that most communications ports are invisible to the outside by default. Also, the fact that Linux is community based, and therefore community policed, makes it very difficult for virus writers to pull anything over on us without getting, immediately, very noticed. 
There are currently no viruses or worms that affect any Linux programs, that I know of (I'm no expert, but I try to keep on top of current events). However, some viruses and worms can be transmitted through email, which you can pass to your Windows-using friends. You may want to use a virus killer to strip them out before you pass them on, if you are high risk to get viruses.

---

### Post by mihalisla on 2006-09-01
Thank you for the reply but my main concern is , if a virus-worm-like programm can be installed to the system without user knowing so...Exclude from this the vulns that are fixed by system updates....

---

### Post by yomimono on 2006-09-01
It's certainly possible for a trojan to get by on Linux.  Say for example a malicious person sends you an e-mail with an attachment called 'fun-game.bin' which is a binary.  If you execute it blindly, it could take over your user account, and any other accounts which you have passwordless access to.  If your machine has any privilege escalation vulnerabilities, the attacker could use your naivety to take over the entire system.  There have been a [few](http://www.theregister.co.uk/2001/09/07/linux_trojan_spotted/) [scares](http://www.symantec.com/security_response/writeup.jsp?docid=2003-011412-3316-99) about this in the past, but we have yet to see a really major outbreak.

Rather than worms or viruses, Linux machines tend to be compromised by brute-force attacks on insecure usernames and passwords via SSH and VNC.

Does this come closer to answering your question?

---

