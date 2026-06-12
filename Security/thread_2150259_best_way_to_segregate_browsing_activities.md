---
title: "best way to segregate browsing activities"
date: 2013-05-31
forum: Security
---

### Post by planarian on 2013-05-31
Hi,

I want keep my online financial transactions completely separate from the rest of my web browsing. Obviously the absolute safest way is to simply use separate computers, but that's not particularly convenient. If I were to setup a second X11 login, how much risk would this less sheltered account pose to the other one? And what would be the preferred way to implement this? Perhaps xnest?  I'm not new to Linux, but I'm also not exactly fluent, so please go easy on me :)

Thanks!

---

### Post by 2F4U on 2013-05-31
> Obviously the absolute safest way is to simply use separate computers

No, the absolute safest way I know would be to use a liveCD for internet banking, because no traces would be left behind (at least on the machine).

---

### Post by planarian on 2013-05-31
Interesting suggestion, though it sounds like a hassle since I need an up-to-date java plugin. I'm willing to settle for "good enough."

---

### Post by Grenage on 2013-05-31
A virtual machine would also do the job; it's not bulletproof, but it's pretty viable.

---

### Post by planarian on 2013-05-31
I'm afraid this computer's a bit long in the tooth for a VM...

---

### Post by tubbygweilo on 2013-05-31
Do financial transactions from a guest account as on shut down the guest account is wiped?

---

### Post by planarian on 2013-05-31
Hmm. Still doesn't quite pass the convenience test. (I want the financial account to retain configuration changes)

Based on the fact that no one is endorsing anything like my proposed plan, should I assume it's too risky?

---

### Post by Hungry Man on 2013-05-31
Use a separate user account for banking. Seems like the simplest solution. The other session won't start, so neither should user processes in it. If an attacker already has root you're screwed regardless.

---

### Post by planarian on 2013-05-31
> **Hungry Man said:**
> The other session won't start, so neither should user processes in it. 

I'm not quite sure what you mean by this. My idea was to have the two accounts running simultaneously so that I could toggle between them.

---

### Post by Hungry Man on 2013-05-31
Oh. Well then that's always going to have issues with X11 unless you use a program to start a new X session for the new user. Still, run the browser in a separate process, and all you'll have to worry about is X keylogging. Processes in separate user accounts should not be able to interact.

---

### Post by planarian on 2013-05-31
> **Hungry Man said:**
> Processes in separate user accounts should not be able to interact.

Yes, that's what I was trying to figure out. But if these environments are truly separate, then surely a keylogger installed through the regular account could only read strokes typed into that terminal?

---

### Post by Hungry Man on 2013-05-31
No, unfortunately Linux is sorta ****** in this respect. X keylogging bridges user separation. It pretty much bridges everything.

---

### Post by planarian on 2013-05-31
Interesting. Are there other "bridges" I should know about?

---

### Post by Cheesemill on 2013-06-02
You could set up a dual boot and use one OS just for banking.

---

### Post by Hungry Man on 2013-06-02
X is the biggest bridge. Separation by user account is perfect. It's always best to supplement with something like Apparmor.

---

### Post by planarian on 2013-06-02
Thanks, I'll take that as my answer. Now how do I mark this thread "solved"?

---

### Post by duncan12 on 2013-06-02
Thread Tools (at top of thread) -> Mark as Solved

---

### Post by planarian on 2013-06-02
When I click that drop-down, I only get: 

Show Printable Version
Subscribe to this Thread

---

### Post by Cheesemill on 2013-06-02
[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

