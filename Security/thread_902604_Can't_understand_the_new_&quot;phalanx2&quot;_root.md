---
title: "Can't understand the new &quot;phalanx2&quot; rootkit."
date: 2008-08-27
forum: Security
---

### Post by nerd0795 on 2008-08-27
Well I was online and I found out "linux is under attack" installing a rootkit through SSH Keys.  Now I don't understand... do you get infected instantly by just connecting to the internet?  Or do you need to go to an infected site first?  What does it normally do?  Can this screw up grub since I don't own this computer?  I tried to read the posts on other sites, but since I'm a linux n00b I can't understand it.

---

### Post by Oldsoldier2003 on 2008-08-27
in a nutshell: crackers are using stolen or compromised ssh keys to connect to a system then use a local kernel exploit to break into a root shell and install the rootkit.

If you don't have ssh enabled and keep your system patched as secuity updates are released it is a non issue.

---

### Post by umechanism on 2008-08-28
> **Oldsoldier2003 said:**
> in a nutshell: crackers are using stolen or compromised ssh keys to connect to a system then use a local kernel exploit to break into a root shell and install the rootkit.

If you don't have ssh enabled and keep your system patched as secuity updates are released it is a non issue.

But what if you do have ssh (OpenSSH) installed but everything is up to date (I'm running OpenSSH 4.7)?  Is it still an issue?

---

### Post by cariboo on 2008-08-29
I use denyhosts, the attacker gets 5 tries and then their ip address is blocked. I also use a strong password using a combination of upper and lower case letters and numbers.

Denyhosts is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by jerome1232 on 2008-08-29
If you read the articles it's exploiting a weakness in openssl which has been patched and addressed, there's also a sticky at the top of this section that tells you how to insure you aren't using compromised keys. If you keep your system updated this is a non-issue.

---

### Post by umechanism on 2008-08-29
> **cariboo907 said:**
> I use denyhosts, the attacker gets 5 tries and then their ip address is blocked. I also use a strong password using a combination of upper and lower case letters and numbers.

Denyhosts is available in the repositories and you can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

I also use denyhosts.  The attacker gets one, and only one, chance then he is black listed.  I have seemed to have black listed myself because as of this morning, I can't log into my own machine remotely from my office computer.  Hmmmm....

---

### Post by moonpup on 2008-08-29
> **umechanism said:**
> I also use denyhosts.  The attacker gets one, and only one, chance then he is black listed.  I have seemed to have black listed myself because as of this morning, I can't log into my own machine remotely from my office computer.  Hmmmm....

LOL, you should at least change that setting to 3 :) Anyway, if you always login from work and you come from the same ip address, then add that ip to the whitelist option in denyhosts, and you will no longer lock yourself out.

---

### Post by brian_p on 2008-08-29
> **jerome1232 said:**
> If you read the articles it's exploiting a weakness in openssl . . . . 

That's conjecture on the part of the author.

---

### Post by umechanism on 2008-08-29
> **moonpup said:**
> LOL, you should at least change that setting to 3 :) Anyway, if you always login from work and you come from the same ip address, then add that ip to the whitelist option in denyhosts, and you will no longer lock yourself out.

At least I know it works. :>)  I'll white list myself.

---

