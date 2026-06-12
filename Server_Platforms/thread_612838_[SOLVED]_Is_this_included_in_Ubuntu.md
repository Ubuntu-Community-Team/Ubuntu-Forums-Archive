---
title: "[SOLVED] Is this included in Ubuntu?"
date: 2007-11-14
forum: Server Platforms
---

### Post by Hallvor on 2007-11-14
I did a bit of reading on [Wikipedia]("http://en.wikipedia.org/wiki/Fedora_(Linux_distribution)")

"Fedora also has methods in place to prevent buffer overflow exploits and root kits from functioning. Compile time buffer checks, Exec Shield and restrictions on how kernel memory in /dev/mem can be accessed help to prevent this. [13]"

Is all this included in Ubuntu, or is Fedora less vulnerable to buffer overflows and rootkits?

(Sorry if this post is in the wrong section. Posted it here because it isn`t a help request, and because it essentially is an Ubuntu question (and thus should not belong in Other OS Talk).)

---

### Post by jdong on 2007-11-14
Moved to Security.

Ubuntu uses GCC stack protector functionality to protect against buffer overflows and also does many of the compile-time buffer checks that Fedora boasts. We also include AppArmor, a technology similar in spirit to SELinux though not as advanced (and easier to learn as a result)

Fedora, as a distro, takes more active security precautions than any other big distro I've seen. However, these preventative measures are not anywhere near foolproof. It's a factor toward system security but not necessarily a major one. They also only target one class of vulnerabilities -- those caused by buffer overflows. To say Fedora is more resistant to rootkits or any other kind of attack is a daring statement.

---

### Post by Hallvor on 2007-11-14
Thanks! :)

---

### Post by jdong on 2007-11-14
If you are a serious public server admin (tm), look into the GRSecurity patches too -- those look quite promising for locking down a large multiuser setup of untrusted users (i.e. shared web hosting, shell service, etc)

---

