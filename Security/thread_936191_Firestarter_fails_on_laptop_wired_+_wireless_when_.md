---
title: "Firestarter fails on laptop wired + wireless when wired unplugged"
date: 2008-10-02
forum: Security
---

### Post by DrJohn999 on 2008-10-02
Firestarter works fine on my Dell Dimension D610 (hardy) when the wired NIC is plugged in, regardless of the wireless interface state. If I run wireless only, however, then firestarter fails to start, complaining that etho is not available, which of course it is not.

The traffic monitoring functions appear to work in this state, but I can't edit / create rules or use much else of firestarter's functionality. I like the gui, but could use ufw or gufw equally well if needed.

I'd like to be able to use firestarter when on wireless only. Is there a workaround anyone knows of for this, or should I shrug and give up and use ufw instead? I haven't tried gufi either -- any thoughts / experience with that?

-- DJ

---

### Post by kevdog on 2008-10-02
Im not sure if Firestarter can have multiple profiles -- b/c that is what you need here -- a wireless profile and wired profile -- or at least firewall rules that block traffic independent of incoming port number.

---

### Post by DrJohn999 on 2008-10-03
> ...at least firewall rules that block traffic independent of incoming port number
Do you mean independent of incoming interface (eth0, eth1)? The TCP ports wouldn't change dependent on which interface was up.

The problem seems like a bug in Firestarter to me. It starts and runs fine only if eth0 is up (plugged into a live cable), and it runs if I manually choose the wireless interface in this state.

If eth0 is down (not connected) then firestarter says it's not started, but actually it seems to be running as far as monitoring packets. Also, although I didn't check, it seems very likely that the iptables settings have not been changed (and if I try to make a rule change Firestarter reports that it failed to do so), so the firewall is actually up in either case.

It looks more like a case where Firestarter fails when seeing that the first interface is down, without checking if there are other interfaces available.

I could load Shorewall, but that seems like overkill for a laptop client machine.

UFW works, of course, but is very basic -- there seems to be no way to list its rules once set, so to delete a rule you'd have to have memorized what the rules are. GUFW may be a good way to manage UFW -- any comments on that?

THanks,

DJ

---

