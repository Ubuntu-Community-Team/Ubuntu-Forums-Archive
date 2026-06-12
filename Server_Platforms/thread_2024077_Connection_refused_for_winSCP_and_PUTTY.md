---
title: "Connection refused for winSCP and PUTTY"
date: 2012-07-13
forum: Server Platforms
---

### Post by AndrejsLi on 2012-07-13
Hi folks

I was tried to remove / install OpenSSH, but did something wrong. Now I don't know how to connect to my system again. Please, give me some suggestions.

Sorry about English

Thanks

---

### Post by CharlesA on 2012-07-13
How did you try to remove/reinstall openssh? It is likely it is uninstalled and you will need console access to reinstall it.

---

### Post by AndrejsLi on 2012-07-13
> **CharlesA said:**
> How did you try to remove/reinstall openssh? It is likely it is uninstalled and you will need console access to reinstall it.

I tried with standart sudo commands. But I don't remember that condition now - is it removed or still is. I can't access to server, so I can't to do anything now.

---

### Post by CharlesA on 2012-07-13
If you removed ssh, you are pretty much stuck until you can get console access and get it reinstalled.

Is this on a VPS or a hosted machine?

---

### Post by AndrejsLi on 2012-07-13
> **CharlesA said:**
> If you removed ssh, you are pretty much stuck until you can get console access and get it reinstalled.

Is this on a VPS or a hosted machine?

Ohh..

That is on VPS.

---

### Post by CharlesA on 2012-07-13
You can try contacting the hosting company and seeing if they can help you get ssh installed again.

---

### Post by AndrejsLi on 2012-07-13
> **CharlesA said:**
> You can try contacting the hosting company and seeing if they can help you get ssh installed again.

Is it the only real chance?

---

### Post by CharlesA on 2012-07-13
Unless you have a way to get to the console, yes.

Most VPS companies provide some sort of console access but you'd have to contact them to see for sure.

---

### Post by Cheesemill on 2012-07-13
[Linode]("http://www.linode.com/") provide out-of-band access on their VPS's for exactly this reason, accidentally removing SSH or misconfiguring your firewall (just one of the reasons that they are my VPS of choice).

As CharlesA says your only course of action is to contact your VPS host and see what they can do for you, they may just tell you to reinstall your OS from scratch if they have no out-of-band access feature.

---

### Post by AndrejsLi on 2012-07-13
Thanks for answers to all.

I will press the button in my admin panel and my Ubuntu will install again. And I will spent hours to do all again from the start.

Nice.

---

### Post by Cheesemill on 2012-07-13
Have you contacted you VPS provider first, they might be able to provide you with out-of-band access with which you could fix your problem without a reinstall.

---

