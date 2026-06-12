---
title: "Remote access to Windows partition"
date: 2010-08-08
forum: Security
---

### Post by pipwhite on 2010-08-08
Is it possible to remotely access, inject, manipulate files and/or folders in the Windows NTFS partition when logged into Ubuntu?

I'm either logged into Windows or Ubuntu but NOT both -- ever.  Therefore, while logged into Ubuntu, would it be possible for someone to crack into Windows via Ubuntu using Wi-Fi or modem?

---

### Post by OpSecShellshock on 2010-08-08
It's not possible as far as I know. Are you able to do it locally? If so, to what extent?

Thing is, there are separate things that would all have to be true in order for it to be a risk. First, a legitimate local user would have to be able to do it (and not just drop files, but manipulate system files). Seems like that would be barrier enough. But even if it's not, a remote intruder would have to hijack a session (probably by way of VNC or SSH with a weak password--but there would definitely have to be a server running with ports forwarded on the hardware router). Then they'd have to know that a Windows partition was there in the first place. Then they'd have to be able to alter it during an active session without you noticing.

If all you want to know is whether or not it can happen by way of a normal user browser session, then no. No it can't. For it to be possible at all it would require dedicated reconnaissance or some kind of trickery to convince you to do it for them. But if they're going to do that, it would make more sense to just do it while you're booted in Windows.

---

### Post by bodhi.zazen on 2010-08-08
In theory it is possible. Most people consider shell access equivalent to root access because of the possibility of a root kit or privilege escalation.

So mounting and editing a ntfs partition would be dependent on how the partition is listed in fstab.

Of course one would first need to take advantage of some exploit, but if you are running a VNC server or ssh, and such a server were cracked (usually due to weak passwords) your ntfs partition (your whole system really) is vulnerable.

I suggest you read the security sticky in the security forums and if you install a server take the time to learn to secure it.

---

### Post by pipwhite on 2010-08-09
Would it be possible, when online, could they crack Windows which is more vulnerable to provide access to either Ubuntu or Windows, depending on which one I am logged into at any given moment?  There are no server hosts installed that Im aware of -- its a simple Ubuntu install w/ current auto-updates.

Im also wondering...if, when Im online if they're monitoring my activity, could they compromise Ubunta via Windows XP? 

Also, I want to mention that, a few days ago in Ubuntu I installed several updates and clicked on "details" to watch the updates install and noticed, at least twice, that it read "Windows XP..." which is on, of course, the other partition.  Is that normal?  Moreover, if these updates (only 2 or 3) read this, it makes me wonder if its normal for Update Manager's installs to "mention" Windows on my other partition, and, therefore, since it saw it, could a cracker go further in Ubuntu and compromise it? Because, I've only used Windows Explorer once, since I've had this machine (a year or so), and after that day, I went into Windows Explorer and a lot of changes -- that I didn't make (eg, allow or block domains in Internet options, some strange home page etc) were/are in there.  I didn't do these.  They wouldve had to be entered somehow by someone.

Thank you all for responding to my post.  I appreciate it VERY much.;)

---

### Post by bodhi.zazen on 2010-08-09
> **pipwhite said:**
> Would it be possible, when online, could they crack Windows which is more vulnerable to provide access to either Ubuntu or Windows, depending on which one I am logged into at any given moment?  There are no server hosts installed that Im aware of -- its a simple Ubuntu install w/ current auto-updates.

Although it is a matter of semantics, possible and probable play a role.

If your system, Ubuntu or Windows, are cracked, all things are possible. The things you mention in this thread are improbable as is cracking into an Ubuntu box.

> Also, I want to mention that, a few days ago in Ubuntu I installed several updates and clicked on "details" to watch the updates install and noticed, at least twice, that it read "Windows XP..." which is on, of course, the other partition.  Is that normal?

My guess would be you upgraded your kernel and that message was an update to grub, that would be normal. Hard to know with what little you posted, but I can not imagine any reason why "Windows XP" would be a part of an Ubuntu upgrade.

> Thank you all for responding to my post.  I appreciate it VERY much.;)

Have you read the security sticky yet ? It covers most of what you need to know as you transition to Linux.

Linux is not Windows, it is much more secure, and security is different on Linux. It requires a higher level of knowledge because there are no easy holes for crackers to leverage. So while that translates into higher security, it also means you have a lot of reading to do if you wish to understand Linux security.

---

### Post by pipwhite on 2010-08-09
Thank you, again, everyone for your responses!  I really appreciate it. :KS

---

