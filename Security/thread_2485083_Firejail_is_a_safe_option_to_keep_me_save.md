---
title: "Firejail is a safe option to keep me save?"
date: 2023-03-19
forum: Security
---

### Post by j-101 on 2023-03-19
Hello. I am new en Ubuntu and Linux. And i am searching many options to protect my computer. Firejail is an option to test unknow programs ?

---

### Post by TheFu on 2023-03-20
Yes, but there are others that work in different ways.  Also, firejail doesn't work with any snap packages.
No program can keep you "save".  Bad behavior can completely destroy any settings or programs that are supposed to protect a system from badness.

---

### Post by DuckHook on 2023-03-21
Welcome to the forums j-101

I have found that the best platform to test unknown apps is within a VM. Not only is a VM the strongest sandbox, it can be rolled back to a safe earlier state with its snapshot ability. However, it must be configured properly to be secure, and some people don't configure it properly.

Your reference to "unknown programs" concerns me. If you are coming from the Windows world, then one of the really bad habits that new users from that world bring with them into Linux is the propensity to install outside programs that they download from the Internet. This is one of the most dangerous things that you can do, and is a leading cause of why Windows is such a malware cesspool.

In the Linux world, we have cultivated the good habit of using only apps that are from the repositories. If we run them within firejail or VMs or containers, then this is added security, but not the first, most important defence. As TheFu notes, your behaviour is the most important security. There is no magical app that will save you from bad habits.

By all means, use Firejail, a VM or a container, but never think that these are any more than 10% of the solution. The other 90% is your own computing hygiene.

---

