---
title: "[SOLVED] /usr/bin/lastlog warning = virus?"
date: 2008-10-23
forum: Security
---

### Post by Camilia on 2008-10-23
I opened mail from stranger, for curiosity got the better of me. 
Ran rkhunter and got /usr/bin/lastlog warning. Does this mean a virus got in?

---

### Post by aysiu on 2008-10-23
Boot up a live CD, mount your Ubuntu drive and see what the contents are of /usr/bin/lastlog

---

### Post by Dr Small on 2008-10-23
> **aysiu said:**
> Boot up a live CD, mount your Ubuntu drive and see what the contents are of /usr/bin/lastlog
Most likely a binary.

---

### Post by Camilia on 2008-10-23
aysiu I don't understand any of what you said. If I boot up from disk I will be starting all over.

---

### Post by aysiu on 2008-10-23
We'll take it one step at a time then.

Do you have a Ubuntu CD?

---

### Post by cariboo on 2008-10-23
It is probably a lot easier just to type last in a terminal:

```
last
```

If you see anything but known users in the list, then it is time to start looking for other indications that you have been cracked.

My list only goes back two days as I recently reinstalled, the only users are myself, reboot and guest as I was playing with the new guest feature in Intrepid.

Jim

---

### Post by Camilia on 2008-10-24
Yes I have the ubuntu CD.

After typing last in terminal just saw my name. Very interesting!!

---

### Post by nubdora on 2008-10-24
> **Camilia said:**
> I opened mail from stranger, for curiosity got the better of me. 
Ran rkhunter and got /usr/bin/lastlog warning. Does this mean a virus got in?

I doubt it. 

Also, rkhunter scans for backdoors, trojans, and possible local exploits all of which need to be installed as the root user to be used effectively on a system so a malicious user can seize the system.

Viruses coded for the linux kernel also have to be ran as root to be effective. 

Unless you've altered the Ubuntu distribution to run every thing with root privileges as our friends at Microsoft have done for Windows, open as much email from strangers as you like. 

If what you're worried about is catching a virus written for the Windows kernel, and the posiblity of spreading it to Windows users, I suggest installing the Avast! virus scanner for Linux. I don't like ClamAV, but in it's defense, if I was running a mail or samba server I would use ClamAV.

Also, don't forget to checksum the file you've downloaded, especially if it is installed and ran as root, as I so carelessly did the other day for Avast! and chkrootkit. After backing up my music I see a wipe and fresh install of Mint in my future.

---

### Post by Camilia on 2008-10-24
Unless you've altered the Ubuntu distribution to run every thing with root privileges as our friends at Microsoft have done for Windows, open as much email from strangers as you like.

Very interesting info. Now I know the main reason why Ubuntu is more secure than Microsoft. I am spreading the news about no virus protection or firewall needed with Ubuntu. Some people don't trust something that is free. If my son-in-law, whom writes software, hadn't given me the CD I might have been skeptical too.

When I had windows I had extra security and still got Trojans. It was security that I found at comodo forum had passed test with high ratings.

The only person I communicate with directly that has windows is my Mother. I revoked administrative privileges for her and put them on the sharer of the computer. 

Does this take away root privileges for her?

---

### Post by nubdora on 2008-10-24
> **Camilia said:**
> 

The only person I communicate with directly that has windows is my Mother. I revoked administrative privileges for her and put them on the sharer of the computer. 

Does this take away root privileges for her?

There is no such thing as root in windows, but it is called administrative access. I apologize if I mislead you in my earlier post. Essentially, both terms mean the same, but are distinct by the kernels.

To answer your question, yes and no. Revoking administrative access in windows ends most of the user created problems, but it is not the same as permissions in linux. 

I don't feel like typing an essay tonight, so, I'll use one written four years ago, but still relevant to the point.

Security comparisons at the Register: [http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/](http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/)

Privilege levels at the most comprehensive and accurate source on the internet: [http://en.wikipedia.org/wiki/Ring_(computer_security](http://en.wikipedia.org/wiki/Ring_(computer_security))

Joking of course.

---

