---
title: "Who's goes there?"
date: 2008-04-23
forum: Security
---

### Post by Fate Reconciled on 2008-04-23
I've been wondering this for awhile now.

Is there any method wherein it possible to not only scan a remote target for open ports, but also determine what hosts are utilizing those specific port numbers? Maybe if I am maintaining an open connection to one of these there could there be a way to intercept the packets traveling through in order to determine the hostnames of machines connected to the same port as mine?

Ex. Say I have an open connection to 21 on a certain server, could I possibly monitor existing and further attempted connections?

I'm not sure of the legalities of this, but I'm pretty sure it's okay since I'm just watching and not attempting to gain access where it shouldn't be gained. I also don't know whether this thread belongs in this part of the forum, but it's the closest I could find. If I'm wrong in this, please let me know and I'll discontinue the thread immediately

---

### Post by The Cog on 2008-04-23
> **Fate Reconciled said:**
> I've been wondering this for awhile now.

Is there any method wherein it possible to not only scan a remote target for open ports, but also determine what hosts are utilizing those specific port numbers? Maybe if I am maintaining an open connection to one of these there could there be a way to intercept the packets traveling through in order to determine the hostnames of machines connected to the same port as mine?

Ex. Say I have an open connection to 21 on a certain server, could I possibly monitor existing and further attempted connections?

I'm not sure of the legalities of this, but I'm pretty sure it's okay since I'm just watching and not attempting to gain access where it shouldn't be gained. I also don't know whether this thread belongs in this part of the forum, but it's the closest I could find. If I'm wrong in this, please let me know and I'll discontinue the thread immediately

Only by intercepting the packets in the network or by gaining access to ask the server what connections it has open.

---

### Post by olsmithy on 2008-04-23
I'm not sure of the legalities of this, but I'm pretty sure it's okay since I'm just watching and not attempting to gain access where it shouldn't be gained... You will need access and yes it's illegal to do a MITM/ "man in the middle attack".

---

### Post by Chayak on 2008-04-23
If you can bring up a shell on the target box then it's only a matter of time before it's rooted and then you can monitor all connections coming into it.  Can you see the connecitons by just connecting to a port? No.  The legalities will depend on your location.

---

### Post by Dr Small on 2008-04-23
> **Chayak said:**
> If you can bring up a shell on the target box then it's only a matter of time before it's rooted and then you can monitor all connections coming into it.  Can you see the connecitons by just connecting to a port? No.  The legalities will depend on your location.
You speak as if you could root the box yourself, if you had access to a shell. I think it would be more difficult than you think, unless that shell said root@host:~# from rebooting into recovery mode.

Dr Small

---

### Post by Chayak on 2008-04-23
> **Dr Small said:**
> You speak as if you could root the box yourself, if you had access to a shell. I think it would be more difficult than you think, unless that shell said root@host:~# from rebooting into recovery mode.

Dr Small

Easy... no  Possible... Absolutely
As an example
[http://rootthisbox.org/]("http://rootthisbox.org/")
It's done a lot with just shell access it just takes time.

---

### Post by Dr Small on 2008-04-24
I have played RootThisBox challenges before. The object is not to literally,  "Root the box", but to follow the tips and hints to exploit code for a certain program, and gain authorization to another user.

RootThisBox are missions, basically. Not real life rooting the box. Ask Tronyx. Me and him both were playing the missions on one box before.

Dr Small

---

### Post by Chayak on 2008-04-25
Your taking it too literately.  I used it as an example, a simple example, but an example.  It's possible to exploit a machine over the network without shell access and with shell access it's simply easier.  I'm not going to go into how I know such and such and work in whatever because I don't care to share that information and no one has any real way of knowing fact from fiction unless they know who's posting.  I could go on with paragraphs about debugging, buffer overflows using perl scripts and sequential characters to find at what point the buffer overflows, heap exploits, and fuzzing software and the kernel to find stuff. Then again I could just have cut and pasted it from some site.  In the end people will believe what they want to believe.

---

### Post by hggdh on 2008-04-28
if you have a shell at the target, you could try a series of tools, like netstat, ifconfig, etc, to find out who/what else is connected.

You would still be limited by your access permissions.

Nevertheless, the legality of these actions will depend on what has been agreed between you (or the company you theoretically represent) and the owners/operators of the target box. YMMV widely, since some people out there are very paranoid.

---

### Post by jmore9 on 2008-04-29
I was wondering , you guys seem to be in the know.  Should i be worried if i got 3 ssh attempts on my linux box and all were blocked by firewall -- firestarter gui -- ?  thanks in advance

---

### Post by movieman on 2008-04-30
> **jmore9 said:**
> I was wondering , you guys seem to be in the know.  Should i be worried if i got 3 ssh attempts on my linux box and all were blocked by firewall -- firestarter gui -- ?  thanks in advance

Not really; ssh port scans are common for any machine that's connected to the Internet. If they've been blocked by the firewall, there's not much else you can do other than block them with a hardware firewall before they even reach your server.

If you do want ssh visible over the Internet, you should set it to a non-standard port so script kiddies won't find it; determined hackers will obviously try scanning all ports and find it eventually anyway, but most will just scan for machines with ssh on the default port and then try to break into those by looking for weak passwords. Ideally, disable password login entirely and use 2048+ bit RSA keys instead.

---

### Post by jmore9 on 2008-04-30
oj thanks for the info

---

### Post by Fate Reconciled on 2008-05-01
As long as SSH isn't open it shouldn't matter.

---

### Post by Fate Reconciled on 2008-05-01
Alright. I got the exact answer I was looking for here. I've pretty much figured out what has to be done at this point. With legalities and the fact this is a hypothetical situation in mind. :)

Thanks guys!

---

