---
title: "Disabling Security in Ubuntu"
date: 2007-10-16
forum: Server Platforms
---

### Post by skm376 on 2007-10-16
Hi,

I am teaching a class on Computer Security and am hoping to disable all the default security settings that come standard on Ubuntu.  Basically, I want my students to be able to exploit simple buffer overflow programs on my Ubuntu server.  To do this I know I need to disable StackGuard, stack randomization (if Ubuntu has this), and probably some other stuff that I don't know about.  Does anyone have some ideas on how I can go about doing this.  The only other alternative I know is to use a real old kernel image, but I don't want to do that.  Ideas?

Thanks in advance.

---

### Post by skm376 on 2007-10-16
If this isn't possible in Ubuntu server, is it possible in Debian?

---

### Post by skm376 on 2007-12-13
To answer my own question, you can disable Stack Smashing Protection by compiling with the following flag:

--fno-stack-protection

However, stack randomization will still prevent you from exploiting buffer overflows.  To disable stack randomization you can run either of the following:

sysctl -w kernel.randomize_va_space=0

$ echo 0 > /proc/sys/kernel/exec-shield
$ echo 0 > /proc/sys/kernel/exec-shield-randomize

Hope this helps anyone who is interested.

---

### Post by meatpan on 2007-12-13
Sounds like a great class, and I bet your students will learn a lot from this exercise!   I remember taking a course with similar content, and the professor was able to teach both memory and stack engineering, as well as provoke some good ethics discussions regarding security.   In general, there needs to be less FUD and more education about system vulnerabilities. 

BTW, stack randomization makes buffer overflow difficult, but not impossible, so maybe this can be extra credit for some of your advanced students ;)

---

### Post by HermanAB on 2007-12-13
Hmm, you should also try running the desktop as root, disabling netfilter with 'iptables -F' and disabling tcpwrappers with 'ALL: ALL' in '/etc/hosts.allow'.

BTW, I suggest you install this soft target system on VMware, then you can fix the machine by copying the VM after your students blew it full of holes, so they can try again.

Cheers,

Herman

---

### Post by skm376 on 2008-02-21
Last post.  To allow stack-based buffer overflows in Ubuntu (and most modern kernels) there are a number of required gcc options.  Below is an example command-line:

$ gcc -fno-stack-protector -z execstack vulnerable.c

-fno-stack-protector disables SSP (stack guard)
-z execstack marks the stack as executable

Remember to turn randomization off by running:

$ sysctl -w kernel.randomize_va_space=0

Like it was mentioned above, it is best to sandbox any experiments with these options in a controlled environment (VM).  Hope this is useful to anyone whose interested.  The next step is to figure out how to exploit programs not compiled with these options.  Happy hacking :).

---

