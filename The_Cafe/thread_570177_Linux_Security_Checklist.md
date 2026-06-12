---
title: "Linux Security Checklist"
date: 2007-10-07
forum: The Cafe
---

### Post by Puppy fam on 2007-10-07
I just stumbled upon this [Linux Security Checklist]("http://www.linux-sxs.org/security/scheck.html"), and I've got to admit, I feel pretty vulnerable.

Should I be doing more? Heck, I'm not even sure if my firewall is working...

---

### Post by -grubby on 2007-10-07
I don't feel vulnerable. I'm pretty sure there aren't any crackers trying to get me.

---

### Post by Celegorm on 2007-10-07
Those look like some good tips for securing a server. I'm not really worried about my desktop machine, though I might look into it more if I decide to try enabling remote use of ssh on it.

---

### Post by Ireclan on 2007-10-07
It all depends on the situation how much of this stuff you implement. For example, my box is connected to no other networks but the internet, and I trust everyone who could come into physical contact with it. Add this to the fact that I use dial-up, and I don't even need a firewall, because:

*I don't stay connected to the internet more than 25% of the day, and that's scattered throughout the day (I cannot be attacked unless I'm connected).

*My IP address changes everytime I connect (I cannot be attacked unless the attacker has my IP address).

*I have a recent backup of my data, so even if an attacker WERE to get my IP address while I was connected (which is unlikely if you've seen their length), I could re-install the OS and personal data.

OK, but what about a virus via an e-mail, drive-by download, or manually downloaded executable?

*Most viruses are designed for Windows (only about ten are for Linux last time I checked, and some of them relied on since patched bugs.

*Linux uses the "root" system to protect files necessary for system operation.

*Simple vigilance (if an application tries to install on or trash my system, it's gonna need a root password, which I won't give to something I don't recognize).

The only method for delivery becomes exploiting bugs (which are quickly patched) and social engineering. There lies the weakness of Linux; you could download what you think is an application, run it, give it root privileges, and it would trash your system, steal your identity, etc. But nothing on that list, nor any operating system, will save you from that. Heck, even being careful wouldn't, because someone could hack a repository and slip in a malicious package.

Of course, if you use broadband, it would be wise to implement some, if not ALL of that list, because your IP address is near-constant and your computer is connected to the internet for long periods of time. But even that list won't save you in all circumstances; nothing will. It's just impossible to do.

---

### Post by sp88 on 2012-12-06
I do agree with Ireclan..The security implementation totally depends on the infrastructure that you are working with.

For example imagine that you have a setup of web clusters where all of them is behind a load balencer, and traffic from internet cannot reach the servers directly. In that case, the servers behind are pretty much secure..You need to be extremely cautious about a bastion host which you have on your network..

This links also might provide some more info on the steps required..security [checklist for a linux system administrator]("http://www.slashroot.in/security-checklist-linux-system-administrator") 

But yeah all depends on your infrastructure...!

---

### Post by cariboo on 2012-12-06
This thread is 5 years old, much has changed in that time. I'd suggest you check out the [Security Discussions]("http://ubuntuforums.org/forumdisplay.php?f=338") sub-forum, if you have any questions. Thread closed.

---

