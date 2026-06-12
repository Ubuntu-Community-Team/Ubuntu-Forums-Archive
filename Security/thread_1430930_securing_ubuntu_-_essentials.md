---
title: "securing ubuntu - essentials?"
date: 2010-03-16
forum: Security
---

### Post by Fika on 2010-03-16
I've been messing around with linux for a short while now, still trying to figure it all out, and feel I am closer to a reasonably secure system but not sure. Here are the steps I have taken:

secure password
removed telnet
apparmor running in full enforce mode
firestarter

Many of the security tutorials say different things. I am curious what you would add to this list as essential security measures? I am trying to protect myself from remote hacking. Also, can anyone tell me how to install grsecurity suite? I have tried but with no luck. I am running ubuntu 9.04.

---

### Post by Agent ME on 2010-03-16
Remove telnet? Having the "telnet" package is fine. It's "telnetd" you probably don't want.

---

### Post by uRock on 2010-03-16
Firestarter is no longer maintained. UFW is. Either one should work equally as good. If you are behind a router, then you should be fine anyway.

This may be helpful. [http://www.tuxmachines.org/node/8676](http://www.tuxmachines.org/node/8676) I know nothing about that software, but it sounds unnecessary.

---

### Post by bodhi.zazen on 2010-03-16
See the security sticky =)

---

### Post by rookcifer on 2010-03-17
> **Fika said:**
>  Also, can anyone tell me how to install grsecurity suite? I have tried but with no luck. I am running ubuntu 9.04.

If you're using AppArmor, then Grsecurity will be superfluous.  Both of them do essentially the same thing (though Grsecurity does have some extra features like RBAC).  It will be much easier when using Ubuntu just to use the built in MAC -- in this case that's AppArmor.

---

### Post by tgjfxfko on 2012-02-13
> **rookcifer said:**
> If you're using AppArmor, then Grsecurity will be superfluous.  Both of them do essentially the same thing (though Grsecurity does have some extra features like RBAC).  It will be much easier when using Ubuntu just to use the built in MAC -- in this case that's AppArmor.

Grsecurity patch is more than AppArmors RBAC.
AppArmor lacks the PAX buffer overflow protection.

If you disable RBAC during choosing the various options under Grsecurity and SELinux,Tomoyo and CO under security>.. you can perfectly have both grsec and apparmor.

For a lot of applications there are a lot of ready made apparmor policies. 

Why sacrifise if you cab have best of both worlds?

---

### Post by CharlesA on 2012-02-13
Back to sleep you go..

---

