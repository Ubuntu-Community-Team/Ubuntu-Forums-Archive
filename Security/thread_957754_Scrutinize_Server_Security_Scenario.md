---
title: "Scrutinize Server Security Scenario"
date: 2008-10-24
forum: Security
---

### Post by admash on 2008-10-24
I have just read through a lot of postings on physical server security, and I had a couple ideas I would like for you to constructively criticize.

For this scenario assume:

Hardware Setup: Standard, run-of-the mill server hosted at a datacenter colo facility, running Ubuntu Server (of course!) For this scenario, let's say I do not own the box, but rather am leasing one from the host.

Goals: Protect server from hacking attempts, both network and physical and protect sensitive data from intrusion.  Sensitive info on the server is located in mysql DBs, and email.

With that setup and goals in mind, here are a couple ideas I thought would help accomplish my goals, not in any particular order, and certainly not exhaustive:

1. set ssh server to allow login via only gpg key exchange (no server password access); root (for emergencies only) and one admin (sudo) account.

2. create separate truecrypt file containers and run email dirs and mysql db's directly from there. This way if box is unplugged, my sensitive data is locked down. Whole-disk encryption would not be an option since the server is remote.

What are the flaws with these ideas, assuming of course that I am already doing the 'standard' security practices such as  hardening apache, OS patching, permissions policies, etc?

Wouldn't both these implementations deny access to my sensitive data even if a server admin with physical access to the box used a live CD or virtual OS?

Still brainstorming....;-)

---

### Post by hyper_ch on 2008-10-24
you can do full disk encryption with remote login... I wrote a little howto on that.

---

### Post by cariboo on 2008-10-24
Has anybody else had a look at this:

[http://news.cnet.com/8301-13578_3-9876060-38.html?tag=yt](http://news.cnet.com/8301-13578_3-9876060-38.html?tag=yt)

I noticed they were using Ubuntu to crack the encryption.

Jim

---

### Post by hyper_ch on 2008-10-24
cold boot attack is old news and nothing you can prevent from happening this far.

---

### Post by admash on 2008-10-26
> you can do full disk encryption with remote login... I wrote a little howto on that. 

Sorry! I must have missed that, do you have a link? I would love to read this.

> Has anybody else had a look at this:

[http://news.cnet.com/8301-13578_3-98...38.html?tag=yt](http://news.cnet.com/8301-13578_3-98...38.html?tag=yt)

I noticed they were using Ubuntu to crack the encryption.

This article does not bring anything new; If a computer is in a 'sleep' or 'hibernate' mode it is possible to get the encryption keys. The solution is simply to NOT use these modes, or always be sure to dismount all encrypted drives before entering into one of these modes.

> Another interesting technique that Thursday's paper describes is how to supercool the RAM chips with a can of compressed air held upside-down. Then the cooled memory can be physically extracted and inserted in another computer owned by the attacker.

There are articles refuting the practicality of this, including an episode of Security Now ([www.grc.com](www.grc.com)). Basically, an attacker would have to be present when the server is 'on', shut it down while super-cooling, and then they would have about 30 seconds to get the keys. It is just not practical.

> cold boot attack is old news and nothing you can prevent from happening this far. 

Yes, it is old news but I am looking for ways to make it as difficult as possible.

Another question; remember the following:

a. I have disabled all logins except root and one admin account b. both accounts are authenticated ONLY by key exchange. (the private keys have passwords of course, but that is not relevant here)

Is it still possible for someone with physical access to gain access to the box WITHOUT rebooting?

If not, then mission is accomplished because my sensitive dirs are all locked in encrypted vols (with the exception of the super-cooled-ram scenario which my opinion is that it is too impractical). If so, give me an idea how this could be done? There are no user accounts to exploit, network access is blocked so how could access happen without a reboot?

---

### Post by Dr Small on 2008-10-26
> **hyper_ch said:**
> you can do full disk encryption with remote login... I wrote a little howto on that.
Could I see it?

---

### Post by hyper_ch on 2008-10-27
> **admash said:**
> Sorry! I must have missed that, do you have a link?
I don't know it by heart but I guess can find it if you search for it.

> **Dr Small said:**
> Could I see it?

sure :)

---

