---
title: "Is a procces pkexec zombie Ubuntu 16.04"
date: 2016-03-17
forum: Ubuntu Development Version
---

### Post by Makova on 2016-03-17
Hi.
Right now, I'm using Ubuntu 16.04 Gnome on a Lenovo Think Pad X1 carbon Intel® Core&#8482; i7-5600U CPU @ 2.60GHz × 4
  And with this Kernel: 
```

&#9581;&#9472;manu@Lucy ~  &#8249;master*&#8250; 
&#9584;&#9472;&#10148;  uname -a
Linux Lucy 4.4.0-13-generic #29-Ubuntu SMP Fri Mar 11 19:31:18 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```
Always appears a zombie's process with:
```

&#9581;&#9472;manu@Lucy ~  &#8249;master*&#8250; 
&#9584;&#9472;&#10148;  ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]'
Z+    1298  1305 [pkexec] <defunct>

```
kill process with the command:
```

sudo kill -HUP `ps -A -ostat,ppid,pid,cmd | grep -e '^[Zz]' | awk '{print $2}'`

```
but freezes the system. 
Any ideas 
Thanks.

---

### Post by grahammechanical on 2016-03-17
I think that you misunderstand what pkexec is and does.

**PolicyKit/pkexec**

> A privilege authorization feature, designed to be independent of the desktop environment in use and already adopted by [GNOME]("https://en.wikipedia.org/wiki/GNOME")[SUP][[4]]("https://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features#cite_note-4")[/SUP]  In contrast to earlier systems, applications using PolicyKit never run  with privileges above those of the current user. Instead, they  indirectly make requests of the PolicyKit [daemon]("https://en.wikipedia.org/wiki/Daemon_%28computer_software%29"), which is the only program that runs as root.

[https://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features](https://en.wikipedia.org/wiki/Comparison_of_privilege_authorization_features)

[https://en.wikipedia.org/wiki/Polkit](https://en.wikipedia.org/wiki/Polkit)

[URL="https://www.freedesktop.org/software/polkit/docs/latest/polkit.8.html"]https://www.freedesktop.org/software/polkit/docs/latest/polkit.8.html

[/URL]> An authentication agent is used to make the user of a session       prove that the user of the session really is the user (by       authenticating as the user) or an administrative user (by       authenticating as a administrator).


So, if we try to change a system setting and we get a dialog asking us to unlock the utility or authenticate the action, then that is pkexec doing its job. For example, Update Manager will download and install most updated packages without asking for authentication. But if the upgraded package is a Linux kernel, then we are required to authenticate the upgrade. There are a few other packages that this applies to as well.

Regards

---

### Post by Makova on 2016-03-18
Of course it is **pkexec**. I do not understand is because it is like a zombie process in the system.

Regards.

---

