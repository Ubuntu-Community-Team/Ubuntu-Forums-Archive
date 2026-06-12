---
title: "Did I get hacked?"
date: 2018-10-03
forum: Security
---

### Post by fedebaka2 on 2018-10-03
In my office we have several PCs connected to the main university network (which is out of our control). Two are windows, one is ubuntu and one is a Rocks (i think it's redhat based) cluster front end. The network administrators gave us static IPs and I don't know what they did but gave us external IPs to access both the linux machines from outside the university via ssh.

A few months ago, I was away, and they told me the cluster front-end got hacked, the person who mantains those systems puts ridiculously easy passwords so I think that's how they entered, though I don't know how they found the IP or the usernames. I don't know what the hacker did either. The person in charge supposedly cleaned the mess.

So recently I come back to the office and want to use the Ubuntu machine and find that for some reason ubuntu was "reinstalled" by the person in charge, again with ridiculously easy passwords. I found constantly running rsync and crond processes using 100% of all processors ran by a user, laura, that wasn't even logged in and had no idea what that is. I changed the passwords and found that laura had a crontab pointing to a hiddden .ttp directory in her home with a couple weird directories and files. I deleted the directory and wiped the crontab several times, but the processes, crontab and the directory kept appearing every few hours or days. I also checked .profile, .bash_profile, init.d and all I could think of and found nothing weird. Luckily, laura isn't a sudoer.

The last thing I did was to create a "stopper" .ttp directory in her home owned by root so, i suppose, whatever tries to re-create it will fail. It has worked at least for 24 hours now, but it's a dirty solution.

Do you guys think this is a hack/rootkit/trojan? Is there a better solution?

Thank you very much.

---

### Post by fedebaka2 on 2018-10-03
OK, sorry I didn't realize before, but it's the same malware reported in [this thread]("https://ubuntuforums.org/showthread.php?t=2395684&p=13781283"). Still remains the question as to how to cleanly remove it.

---

### Post by QIII on 2018-10-03
Don't worry about starting a new thread.

Unlike many Stack Exchange forums, we would actually prefer that users start their own threads for their issues.  Although the symptoms may be similar, the root cause is often different.

That being the case, tagging on to someone else's thread causes confusion.

Adding a link to another thread can be informative, however, so that is fine.

As to the problem -- I'd agree with the other responders to the thread linked:  A compromised machine can never be trusted.  I'd wipe the drive and reinstall.  You will find out soon enough whether a rootkit has buried itself deeply enough that a thorough disk wipe is in order.  If after a disk wipe the problem persists, the rootkit might have been wrangled in to the motherboard's firmware, which is a really bad situation.

---

### Post by TheFu on 2018-11-08
Agreed.  Wipe the system and start over.  This time, disable passwords for all remote access and only allow ssh-keys.  Also, install fail2ban to prevent unlimited brute force attacks.

Oh ... and fire the other guy using simple passwords.  An Admin should be setting up 20+ character passwords.  Nothing less. Even 100% random passwords should be at least 16 characters in length.

A good solution might be to force pamusb to be used for 2FA on the Linux systems.

And once the attackers are on the subnet, expect that all other devices connected have also been compromised.  Wipe and start over, especially the servers and Windows systems.

Once compromised, a computer can never be trusted again until the OS is wiped.

---

### Post by bashiergui on 2018-11-14
> **TheFu said:**
> And once the attackers are on the subnet, expect that all other devices connected have also been compromised.  Wipe and start over, especially the servers and Windows systems.
That is drastic advice for a crypto miner. I would be more concerned about crappy passwords in use on other systems, especially if the same sys admin works on them all. Make sure all systems in the LAN are using good passwords. If they’re not then check them for compromise. I would only wipe systems showing indications of compromise.

---

### Post by 1clue on 2018-11-14
Crypto miner or not, critical system or raspberry pi. It's all the same. A compromised system is a threat to your entire network. And it's handling money of a sort. A compromised system can't be truly trusted unless you've wiped the disks completely, including the partition tables, and checked the firmware on the motherboard and any disk controller.

+1 for firing the guy who gives out easy passwords. Get somebody who has a clue about security, or at the very least google "<distro> security" and read the first few hits.

Security best practices is actually a moving target. I've been building physical systems and VMs - both publicly reachable and not - occasionally for decades. Every time I build something I google the best practices, unless I'm doing a bunch of systems at the same time. I still take into account the purpose and 'location' of the system (public, private, what job it does) and apply human logic to determine what exactly to do each time.

---

### Post by bashiergui on 2018-11-14
Wiping the infected computer is good advice. Wiping *every other server * on the LAN is overkill.

---

### Post by 1clue on 2018-11-15
This scenario (one system getting hacked) is exactly why you should treat every system as though it were publicly facing. Everything should get a regular security scan, no matter how well-protected you think it is. All you need is one computer to get hacked -- or to get malware -- and your hypothetical million dollar firewall is useless. It happens to supposedly impenetrable government agencies with secrets to keep and professional security staff, so why would anyone think their home network is safe?

---

