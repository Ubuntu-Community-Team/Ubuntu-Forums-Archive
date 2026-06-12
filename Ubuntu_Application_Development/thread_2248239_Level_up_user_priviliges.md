---
title: "Level up user priviliges"
date: 2014-10-13
forum: Ubuntu Application Development
---

### Post by baltic on 2014-10-13
Hi!

I am completely new to linux and linux programming.
I am writing a program, which needs access to cpuid and msr instructions. As far as i uderstand, it is done through the /dev/cpu/[N]/cpuid and msr files. The problem is, the program needs higher privileges to run, i've tried to use capability library and set the CAP_SYS_RAWIO on the exe file, and than acquire them through 
```
if (cap_set_flag(caps, CAP_EFFECTIVE, 1, cap_list, CAP_SET) == -1)
```
doesn't seem to help. the wierd thing is, ```
auto err = setuid(0);
``` doesnt work either. I mean, it doesnt give error, but the privileges don't seem to get elevated. Though if i launch it through sudo, it works fine, and shows all the magic.
So,
[LIST=1]
[*]What is the best way to deal with elevated user rights in linux? It's supposed to be a gadget, which shows the current cpu power consumption, and launching it with password reqest every time is not an option. 
[*]What tools are good to debug such issues? Idealy it should show, what the app is trying to access, and why it wasn't allawed to. 
[/LIST]

Thanks!

---

### Post by ian-weisser on 2014-10-13
> **baltic said:**
> 
[LIST=1]
[*]What is the best way to deal with elevated user rights in linux? It's supposed to be a gadget, which shows the current cpu power consumption, and launching it with password reqest every time is not an option.
[*]What tools are good to debug such issues? Idealy it should show, what the app is trying to access, and why it wasn't allawed to.
[/LIST]


I usually write a service that runs as root or a system user (never the login user). So it doesn't have permission problems.
The user-interface display widget is a separate application that runs as the login user. So it doesn't need any permissions.
The two processes communicate using dbus, which is designed to handle exactly this kind of situation.

---

### Post by baltic on 2014-10-17
Can you recommend any tools like windows ProcessMonitor, or some other linux analogue?

---

### Post by ian-weisser on 2014-10-17
I'll leave to gurus with Process Monitor experience to answer that.

---

