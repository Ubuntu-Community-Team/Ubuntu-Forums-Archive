---
title: "Firestarter problem"
date: 2009-07-02
forum: Security
---

### Post by best63 on 2009-07-02
I'm running Ubuntu 8.10. On boot up fire starter always shows that it fails. I have looked at my setup several times and I just can't get to run properly. Can anyone help on this. I have thought of using a different fire wall but I have stayed with this one. Thanks,

---

### Post by ajgreeny on 2009-07-02
Do you really need to to run at boot up?  Firestarter is not actually your firewall, that is iptables, and firestarter just configures iptables for you, so once set as you want, that may be all you need.  In fact, only if you are running a server of some kind, eg mailserver, may you actually need to make any changes to the ubuntu default.  I have not installed or run a firewall configuration application since 6.06, and I only did so then becauseI though I had to, being used to Windows XP.

Just another of the many delights of running this OS.

---

### Post by bodhi.zazen on 2009-07-02
Most likely (I am guessing) because it conflicts with ufw.

Try removing ufw 

```
sudo apt-get remove --purge ufw
```

---

### Post by LifeOnMaths on 2009-07-03
If memory serves (I swore off firestarter a while ago, but let's save the debate for another time), firestarter will fail if the device it's meant to be monitoring isn't there. In particular, if you connect using wifi, then because the connection isn't established at boot time, firestarter always fails to load at boot, although it should still be possible to start it once the system is running.

As greeny said, though, you don't need firestarter running - the actual firewall (iptables) is independent and is always active.

EDIT for clarity: I seem to have managed to say things in a way that is quite ambiguous, and I apologise. The statement about firestarter and iptables is meant to be essentially a restatement of:
> Firestarter is not actually your firewall, that is iptables, and firestarter just configures iptables for you, so once set as you want, that may be all you need.Again, I apologise for any confusion caused.

---

### Post by Soul-Sing on 2009-07-03
> As greeny said, though, you don't need firestarter running - the actual firewall (iptables) is independent and is always active.

You need a frontend like firestarter, (g)ufw, or activate iptables.
Iptables is installed, but by default not active.
I recommend using gufw. Firestarter as a project is no longer "active".

---

### Post by LifeOnMaths on 2009-07-03
> **leoquant said:**
> You need a frontend like firestarter, (g)ufw, or activate iptables.
Iptables is installed, but by default not active.
I recommend using gufw. Firestarter as a project is no longer "active".

Sorry, I wasn't entirely clear. Yes, you do need to activate iptables, although once iptables is activated and configured, then firestarter doesn't need to be running. I also recommend gufw.

---

### Post by ajgreeny on 2009-07-03
Sorry to barge in to this thread, but can leoquant and LifeOnMaths tell me what they mean by "Iptables is installed, but by default not active."

I understood that iptables was not needed to be *activated* because, by default, all ports are closed (or stealthed) in Ubuntu, and therefore nothing can get in unless you let it.  I thought, only if you are running a server do you need to open specific ports by default using a utility such as ufw or firestarter.  Certainly on my machine, behind a router, admittedly, and never having "run" anything to do with iptables, all my ports are closed and nothing can come in without me asking for it.  Shields Up always reports that without failure.

Have I got something wrong with this idea?

---

### Post by bodhi.zazen on 2009-07-03
> **ajgreeny said:**
> Sorry to barge in to this thread, but can leoquant and LifeOnMaths tell me what they mean by "Iptables is installed, but by default not active."

I understood that iptables was not needed to be *activated* because, by default, all ports are closed (or stealthed) in Ubuntu, and therefore nothing can get in unless you let it.  I thought, only if you are running a server do you need to open specific ports by default using a utility such as ufw or firestarter.  Certainly on my machine, behind a router, admittedly, and never having "run" anything to do with iptables, all my ports are closed and nothing can come in without me asking for it.  Shields Up always reports that without failure.

Have I got something wrong with this idea?

No that is correct.

The point of "Iptables is installed, but by default not active" is that if you:

```
sudo iptables -L -v
``` iptables is permissive and they prefer to configure iptables.

These discussions go round and round because :

1. Nobody asks the right question, which is 

What do you want to use iptables for ?
routing  to a virtual or private network ?
Limiting access to a server ?

and

2. Many people do not understand what it means when you tell them all ports are closed. They come from a Windows world where there are open ports and they have had it ingrained into them that they need a firewall without understanding things such as services and ports.

People who understand firewalls and use them appropriately (usually) do not ask these questions.

---

### Post by Soul-Sing on 2009-07-03
> Sorry to barge in to this thread, but can leoquant and LifeOnMaths tell me what they mean by "Iptables is installed, but by default not active."

I understood that iptables was not needed to be activated because....

Not a call from me to blindly activate iptables....Ubuntu comes with a zero open port policy. On desktop environments (not server-environments) not nec. at all to use iptables imho.

My reaction is on this sentence: > As greeny said, though, you don't need firestarter running - the actual firewall (iptables) is independent and is always active. 
And that quote is not really from you ajgreeny, but from a message by LifeOnMaths.

---

### Post by ajgreeny on 2009-07-03
Thanks guys!  I'm glad I hadn't got it wrong.  I'm aware that this discussion tends to go round and round, but I have not used a firewall config application since dapper, I think, or maybe before that (been with ubuntu since 5.04) and I just did not quite understand your comment about activation of iptables.  Now I do understand what you both meant.

Thanks again for the clarification.

---

### Post by best63 on 2009-07-04
Thanks for all The information on fire starter.

---

