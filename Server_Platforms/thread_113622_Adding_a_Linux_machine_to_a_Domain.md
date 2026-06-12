---
title: "Adding a Linux machine to a Domain"
date: 2006-01-06
forum: Server Platforms
---

### Post by harisund on 2006-01-06
Hello everyone

As you would have probably figured out from the title, I want to join a Linux machine to my university's domain. The Primary Domain Controller is a Windows Machine, and I have the username and password to login to the domain (if I add a Windows machine to the domain, it asks me for the domain administrator user name and password.) 

Is there a way to add a Linux machine to the domain? I am using Samba of course. I read through the smb.conf file in the /etc/samba directory and it was pretty well documented, but I am still not able to get things straight. A google search only reveals tutorials on making the Linux machine a PDC for a Windows network. When google fails, I fall back on these forums !

Thanks people !

---

### Post by AndyW on 2006-01-06
Have you tried asking at the IT department? Surely you arent the only one who uses/used linux.

---

### Post by harisund on 2006-01-06
actually we have only Windows machines (old ones running Windows 2000, the new ones running XP and the server running 2003.) The few of us who are trying to spread Linux are still trying to figure out how to join the machines to the main network domain !

---

### Post by nuke on 2006-01-09
I will be working through this painful process in the next week or so.  I hear your pain and hope this can help you too.

Check out these threads in the forums and WIKI.  They may help you.

[http://ubuntuforums.org/showthread.php?t=5409]("http://ubuntuforums.org/showthread.php?t=5409")

and 

[http://ubuntuforums.org/showthread.php?t=113149]("http://ubuntuforums.org/showthread.php?t=113149")

[https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto]("https://wiki.ubuntu.com/ActiveDirectoryWinbindHowto")

Let us know if this helps.

---

