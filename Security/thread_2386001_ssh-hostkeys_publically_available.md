---
title: "ssh-hostkeys publically available?"
date: 2018-02-27
forum: Security
---

### Post by sniper8752 on 2018-02-27
I noticed after doing a nmap scan (intense level), that it returned 3 ssh-hostkeys on my ubuntu 16 server.  Is this good or bad?
In reading this article: [https://www.ssh.com/ssh/host-key](https://www.ssh.com/ssh/host-key) I found this:
```
It is important to regularly change host keys. It is a complicated process and has to be done with due diligence.


```
How do I know if this is happening?  Is this on by default?  If not, how can I do this?

---

### Post by DuckHook on 2018-02-28
Not sure what you mean by: > **sniper8752 said:**
> …How do I know if this is happening?Presumably, if you are the one changing that host key, that's how you know it's happening. Or am I misunderstanding your question?

Even though I'm awfully security-conscious, I do sometimes think that some security measures go way overboard and some security advice is too draconian to be applied generally. The warning to change host keys on a regular basis is necessary for publicly exposed servers with rotating admins, but it gets very annoying and downright silly on private servers with a highly stable set of admins. I don't change my host keys at all because I'm my own one-and-only admin. Moreover, my server is entirely sandboxed from the wider internet and is only used within a local LAN. If a bad guy ever penetrates my firewall and sandboxing, the whole game is up for me anyway, whether my host keys are changed or not.

Perhaps if you provided more context and background, we could advise you with more relevance. As it is, we have no idea whether you are running a small SOHO server or a large internet-facing web server.

---

### Post by sniper8752 on 2018-02-28
It is a SOHO server.  So it sounds like it's not necessary then.
Just curious, what is this "sandbox" setup that you speak of?

---

### Post by DuckHook on 2018-02-28
> **sniper8752 said:**
> …Just curious, what is this "sandbox" setup that you speak of?
My sandboxing mainly consists of:

[List=1]
[*]On my servers:
[LIST]
[*]Running only the bare minimum of needed resources
[*]Disabling unneeded services
[*]Segregation of different services among physically different servers
[*]UFW allowing minimal number of both ingoing and outgoing ports
[*]apparmor
[*]Since they are headless servers, allowing maintenance using only ssh with strong paired RSA keys (this is the host key setup you are inquiring about).
[/LIST]
[*]By far the biggest "sandboxing" guard is to have a robust firewall between your LAN and the WAN on the other side. Most people achieve this using their router, which is actually not too bad as a firewall device provided it is from a good vendor who continues to support it with patches over the long term. Cheap routers from lousy vendors often have their support dropped after a couple of years. But such patches are only as good as how industriously you apply them. And no vendor in the world can protect you if you are intent on poking holes in your firewall to enable loopy services like PTP gaming, etc.
[/list]
When it comes to security, most people direct their energies to the wrong things. You seem to have a healthy interest in matters of general security and may find it useful to read the link in my sig: **Security Basics**

---

