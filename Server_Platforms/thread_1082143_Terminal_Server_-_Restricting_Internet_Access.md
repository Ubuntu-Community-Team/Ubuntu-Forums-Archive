---
title: "Terminal Server - Restricting Internet Access"
date: 2009-02-27
forum: Server Platforms
---

### Post by ILMV on 2009-02-27
Hello All

I work with a few chaps who have asked the question, "How can we restrict internet access on a per user basis using Ubuntu terminal server?".

Basically we have several machines dotted around our offices / factory, some of which we allow internet use, others we only want to be able to connect to our intranet. Is there a way that I can restrict certain users, or even user groups from internet access?

I have been told that whatever internet access the terminal server has, the connecting user will have, this is no good for our situation.

Many Thanks, Ben

---

### Post by cdenley on 2009-02-27
```

sudo iptables -A OUTPUT -d ! 192.168.0.1/24 -m owner --uid-owner userwithoutnet -j REJECT

```

---

### Post by Ian87 on 2013-04-13
> **cdenley said:**
> ```

sudo iptables -A OUTPUT -d ! 192.168.0.1/24 -m owner --uid-owner userwithoutnet -j REJECT

```

Does this command would apply to Windows user in a domain? i've been trying to make this work but until now no luck. 

I have at least ten computer in my domain and I just started using Ubuntu server, i'm using Samba as PDC for my windows computer. My problem now is how to restrict domain users (XP Pro users) from accessing the net and still have outlook running for emails?:confused:

any help would be greatly appreciated.

---

### Post by Doug S on 2013-04-15
Hi Ian87, and welcome to Ubuntu forums.

Note that normally moderators will close old threads with new posts added, and a couple of others around this one were closed for that reason. Perhaps this one was left because, the iptables rules stuff has not changed. Anyway...


That iptables rule will not work for your application. It would only work on the same computer where the packet originates. Owner information does not go over the wire.
As for what to do for your case, it depends: If your Ubuntu server is also your router/gateway to/from the internet then it would be fairly easy to deny internet access for your local computers (but perhaps a little more difficult to learn iptables in general); If you are using a hardware type router/gateway device, then it would depend on the router.

---

### Post by wildmanne39 on 2013-04-19
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

