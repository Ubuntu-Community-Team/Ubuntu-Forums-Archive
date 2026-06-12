---
title: "ufw won't start on startup"
date: 2009-03-01
forum: Security
---

### Post by petersk on 2009-03-01
I run a small server and some programs will not run properly UNLESS I run ufw (I guess I needed more than the standard ports opened, and I DID set up ufw to allow them).  As luck would have it, I'm running 8.04 and after a boot, I log in and type "sudo ufw status", at which point it says it's not loaded.
I then "sudo ufw enable" and it starts fine and says it will start at startup. Which it doesn't - infinite DO loop....

I tried ksysv and added UFW EVERYWHERE (at all levels) except in the shutdown section(s), and still "no joy".  Anyone have any idea what I need to do to get it started on boot?
Kurt

---

### Post by bodhi.zazen on 2009-03-02
I have not seen that error before.

What did you do to configure ufw ? did you change any of the config files ? Did you add rules ? If so, how ?

You could try re-installing ufw perhaps, but that is not a very satisfying answer.

You could learn iptables and skip ufw altogether :twisted:

---

### Post by aitjcize on 2009-04-03
I found out why!!!

It's because of the firestarter

firestarter whill shot down ufw

"sudo update-rc.d -f firestarter remove" won't work

then i remove it.

Then my ufw enabled at start up!!

---

### Post by hyper_ch on 2009-04-03
are you sure you even need firestarter and ufw?

---

