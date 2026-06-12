---
title: "Are live CDs more susceptible to being compromised?"
date: 2011-03-29
forum: Security
---

### Post by s3a on 2011-03-29
Are live CDs more susceptible than hard drive installations to being compromised in the way that they're structured (such as root having a blank password)? For example, if you enter your credit card information or something on a live CD, would it be relatively risky to have your information be stolen if someone is determined to do it? (If you mention extreme scenarios, make sure you mention the more likely scenario first please).

(I am not taking security bugs into consideration here).

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by Rasa1111 on 2011-03-29
Since the LiveCD basically runs on RAM..
There is no "info" for anyone to get. 

In fact,
 Ive read quite a few places..
 That using a LiveCD for transactions and the like, is about as safe as you could get.

Once you pull the CD out, the info is gone.

---

### Post by rcayea on 2011-03-29
I read the same thing about LiveCDs being the safest you could get. I believe it was a few issues ago in Maximum PC.

---

### Post by uRock on 2011-03-29
Moved to Security Discussions.

---

### Post by 3Miro on 2011-03-29
There are several ways to get an attack. Unless you are running a service (like web-server or samba), then Ubuntu is practically immune to external attacks (i.e. Hollywood style someone entering your computer from the outside). However, you can install malware and in that case it will be easier for a malware program to get to your data. On the other hand, people usually don't install things when running from a liveCD.

Here is the biggest advantage of the LiveCD: every time you reboot, there will be nothing to steal. If I type my credit card number to buy something, then the browser will remember the number. A month later, someone can steal that number. If I use a LiveCD and reboot the machine in the mean time, then everything will be cleaned. An attacker can only access what you have saved in browser history and such in this current session. This is a big advantage to the case where a someone can steal personal information from your machine months or even years later (even if you have deleted it from the HDD).

- For running services, LiveCD is a horrible idea
- For privacy, LiveCD has a huge advantage

---

### Post by bodhi.zazen on 2011-03-29
> **Rasa1111 said:**
> Since the LiveCD basically runs on RAM..
There is no "info" for anyone to get. 

In fact,
 Ive read quite a few places..
 That using a LiveCD for transactions and the like, is about as safe as you could get.

Once you pull the CD out, the info is gone.

> **rcayea said:**
> I read the same thing about LiveCDs being the safest you could get. I believe it was a few issues ago in Maximum PC.

This is one of the biggest pieces of misinformation the internet.

While it may sound good, there are several reasons why this is simply untrue.

1. Most live CD have minimal security features, if any, enabled (apparmor, firewall, etc).

2. The packages on a live CD are out of date, including security updates.

3. "Privacy" is much more then information stored on the hard drive. 

If you are worried about information on the hard drive, either use one of the private browsing features available on a variety of browsers or delete ~/.mozilla (or similar).

You are far better off learning how internet privacy actually "works"

If you read this link, and follow the advice, your hard drive installation will be fare more secure and far more private then any live CD.

[http://bodhizazen.net/Tutorials/Privacy](http://bodhizazen.net/Tutorials/Privacy)

Internet privacy is much more complicated then information on your hard drive and includes several methods.

Information on your hard drive can easily be encrypted, wither with LUKS (encrypted installation) or ecryptfs (encrypted home) and I would put that up against a live CD any day.

---

### Post by s3a on 2011-03-29
Those were pretty interesting responses but I still have more left unanswered which was part of my initial question.

From what I gather a live CD is weaker than a regular installation for a local compromise but what about the "Hollywood-style" attempt and NOT in the long term? Like, let's say I pop in the live CD right now and decide to use a credit card and then five minutes after my credit card was used, I decide to take a one hour shower before returning to shutdown and remove the live CD and at the same that I leave to shower someone is super determined to steal my data, are they going to have it any easier than if they were trying to compromise a hard-drive installation?

Sorry if this seems to be the same question but I am asking it because the way I interpreted the answer for the "Hollywood-style" break in attempt was that by the time the "intruder" is interested into breaking in, the computer will be restarted but my concern is what if I have no restarted the computer, is it relatively easy to break in compared to the hard-disk installation?

Edit: Another way of asking this is: (Ignoring the security bugs) Is the only additional weakness compared to the hard disk installation that of the blank root password and then is the only way to harm the computer in such a way is to be there physically in front of the computer? I know VNC asks the user by default. I don't think SSH asks anything but I have my router blocking external SSH connections.

---

### Post by bodhi.zazen on 2011-03-29
For someone to access your data they either have to have :

1. Physical access. 

The best defense you have here is encryption, and this is only an option on an installed OS, a live CD looses here.

2. Remote access. 

Since a Live CD lacks security updates it is more vulnerable.

On an installed OS you would enable things such as Apparmor,

so again, advantage - installed OS.

3. Some type of network protocol, such as phishing, so called passive fingerprinting, or man in the middle attacks.

Many of these issues are not mitigated in the least by a live CD.

With a hard drive installation you can configure your browser or add extensions to your browser.

Again, advantage hard drive installation.

I can not think of a single advantage of a live CD over a proper installation.

People who push live CD are misinformed and you should not subscribe to such fallacies.

---

### Post by rookcifer on 2011-03-29
A better method than using a LiveCD would be to utilize VM's.  You can use your regular host Ubuntu install for day to day stuff and create a virtual machine that you only use for sensitive stuff.  This way you can keep the VM up to date with security patches and utilize other security mechanisms such as AppArmor.  Also, VM's have the convenient feature of snapshots which allows you to revert back to a previous state.

It is possible for an attacker to break out of a VM, but it would take someone specifically targeting you to do so.  If you don't use your VM very often (most people wouldn't), then the attack window should not be large enough for you to have to worry about becoming a victim of such an attack.

---

### Post by bodhi.zazen on 2011-03-29
> **rookcifer said:**
> A better method than using a LiveCD would be to utilize VM's.  You can use your regular host Ubuntu install for day to day stuff and create a virtual machine that you only use for sensitive stuff.  This way you can keep the VM up to date with security patches and utilize other security mechanisms such as AppArmor.  Also, VM's have the convenient feature of snapshots which allows you to revert back to a previous state.

It is possible for an attacker to break out of a VM, but it would take someone specifically targeting you to do so.  If you don't use your VM very often (most people wouldn't), then the attack window should not be large enough for you to have to worry about becoming a victim of such an attack.

I do not believe a VM is more or less secure then a physical machine.

You would get the same affect if you dual booted, created a second unprivileged account, etc, etc. You can take snapshots of a physical installation as well (LVM is but one example, brtfs snapshots would be another, as would dd or clonezilla).

Better, use the xguest feature in Fedora.

Again, as with a live CD, a virtual machine alone does little to enhance privacy, you still need to privatize your browser, with extensions, etc.

---

