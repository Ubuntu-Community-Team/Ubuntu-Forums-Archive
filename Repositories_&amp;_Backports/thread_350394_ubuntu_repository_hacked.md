---
title: "ubuntu repository hacked?"
date: 2007-01-31
forum: Repositories &amp; Backports
---

### Post by Locke2053 on 2007-01-31
I got this today when updating. It means that the edgy-updates and edgy-security repositories were signed with the wrong keys! Did someone just biff up, or is us.archive.ubuntu.com now the property of eastern european teenagers?


W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by hikaricore on 2007-01-31
Either the key changed. (Unlikely)

The repo list is corrupt (Happens Sometimes)

Or you're experiencing packet loss from your connection or any of a number of servers you're bouncing through to get to the ubuntu repos.  (Also Happens Sometimes)

--

Honestly I wouldn't worry about it, try running apt-get update in a day or two and see if it clears up, which it more than likely will.

---

### Post by Locke2053 on 2007-02-02
So... corruption is a serious problem, n'est ce pas?

Packet loss? I don't buy that. Doesn't this stuff work over TCP?

Key change? Would Ubuntu really just change keys on people without updating the old keys?

---

### Post by hikaricore on 2007-02-02
> **Locke2053 said:**
> So... corruption is a serious problem, n'est ce pas?

Packet loss? I don't buy that. Doesn't this stuff work over TCP?

Key change? Would Ubuntu really just change keys on people without updating the old keys?

Believe what you want, I'm using the same repos as you on 3 different versions of ubuntu which I tested the day you posted previously.  The problem is probably on your end.

---

### Post by paulm on 2007-02-02
Saying "the problem is on your end" doesn't really help anyone fix it though does it?

I am getting the same thing:
> Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


Running apt-get update doesn't fix it though, so what do I have to do?

---

### Post by irene on 2007-02-03
> **Locke2053 said:**
> I got this today when updating. It means that the edgy-updates and edgy-security repositories were signed with the wrong keys! Did someone just biff up, or is us.archive.ubuntu.com now the property of eastern european teenagers?

Eastern European teenagers?! What's that supposed to mean?

---

### Post by bmartin on 2007-02-06
You might be a bit behind the times. Eastern Europe has long been noted for its "special circumstances" that make it a prime area for hacking. Most of the hacking involves e-commerce sites and compromised Windows systems, though, so you're pretty safe.

See [http://www.out-law.com/page-1455](http://www.out-law.com/page-1455), or do a Google search. There are tons of sites out there that talk about the topic.

Most of the people running these scams are sophisticated programmers and hackers. However, given the tools for modern hacking (there are tools out there that have many exploits packaged into one piece of software), hacking is something that could be done easily by anyone with a little computer knowledge. The teenager comment is at best added for humor or effect. It's kind of like how people from NYC point at my state (New Jersey) whenever they smell something foul.

---

