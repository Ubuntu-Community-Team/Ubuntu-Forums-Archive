---
title: "logs and tracker software"
date: 2009-02-22
forum: Security
---

### Post by jtb74129 on 2009-02-22
I am new to linux and have been trying various flavors of Ubuntu.  One thing that concerns me is security.  I have 2 questions for you all.

How to you block web based sniffer/tracker software that loads a stealth file on your system and then forwards you every move to someone else over the internet?  Is it possible to do this on linux?  The internet is a dangerous place I want to be able to protect myself from prying eyes or at least be alerted to someone trying to break in.

My 2nd question is on internet files.  Are there hidden file logs that the browser does not delete and is there any software for linux that cleans your system thoroughly and completely?

I appreciate your input in advance.

---

### Post by cariboo on 2009-02-23
> How to you block web based sniffer/tracker software that loads a stealth file on your system and then forwards you every move to someone else over the internet? Is it possible to do this on linux? The internet is a dangerous place I want to be able to protect myself from prying eyes or at least be alerted to someone trying to break in.


The only way this type of software can be installed is if you use weak passwords or if you install the malware yourself. You may have noticed that to install system wide programs you need to be root. 

Another way for malware to be installed is through social engineering, but then again it depends on you the user to install it.

> My 2nd question is on internet files. Are there hidden file logs that the browser does not delete and is there any software for linux that cleans your system thoroughly and completely?


Go to Edit-->Preferences-->Privacy and enable Always clear my private data when I close Firefox.

Jim

---

### Post by jtb74129 on 2009-02-23
THank you for your reply.  I reinstalled Ubuntu from a clean install and changed my password completely to a stronger password.  If I suspect that something like this is installed in the future, where would one look to find stealth apps running.  I saw something about matching a base image of the OS to the current image and seeing what is different.  Is this the only way to do this since it is stealth?

As far as internet logs, I thought there were some logs that were buried deep in root that the browser couldn't delete?

Thanks again for your help...

---

### Post by Gouki on 2009-02-23
> where would one look to find stealth apps running

netstat/htop[1] will give you good information of what is running. The first application (netstat) is for your network connections.

> I saw something about matching a base image of the OS to the current 
> image and seeing what is different

I believe you're talking about Tripwire[2][3]. In my opinion, it's overkill for a workstation where you're the only one using.

[1]: [http://packages.ubuntu.com/htop](http://packages.ubuntu.com/htop)
[2]: [http://packages.ubuntu.com/tripwire](http://packages.ubuntu.com/tripwire)
[3]: [http://www.tripwire.com/](http://www.tripwire.com/)

---

### Post by jtb74129 on 2009-02-23
I appreciate your info.  In this day and age, I am not sure that anything is overkill.  I came from the windows platform where you never know who has dropped in for a visit and decided not to leave.  Even with a firewall popping up alerts that an app is trying to do something, hackers have caught on that by naming there files with a similar title as a popular program (ie: MS..., or photoshop...) users are more app to allow it and thereby letting it in without even knowing it.  With me now knowing Linux hardly at all, I am trying to remain sane without crossing over to paranoid.

---

### Post by bodhi.zazen on 2009-02-23
You have several options, see the "Intrusion detection" sticky at the top of these forums.

I like Snort + ossec + SELinux on my servers ;)

---

