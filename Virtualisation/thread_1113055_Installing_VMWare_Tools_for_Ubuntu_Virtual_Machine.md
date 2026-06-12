---
title: "Installing VMWare Tools for Ubuntu Virtual Machine"
date: 2009-04-01
forum: Virtualisation
---

### Post by moonshine560 on 2009-04-01
I have mounted the CD package fine from VMWare Server and that worked fine. Then I unzip the contents of the .tar package into a directory on my desktop called "sigh" From there, when I try running the install file in terminal mode- that fails. Looks like it flashes on my screen, but never does anything. No success.

I've tried going into command or shell to find and run it from there using the sudo prefix. I can't seem to find the path in command to my folder "sigh" located on my only user's desktop.

All of the suggestions and guides haven't resolved my issue. I am not very Linux saavy and would appreciate a member responding to me for some help. I can't imagine it being this difficult to extract files and run an installer.

---

### Post by bodhi.zazen on 2009-04-01
It would help if you posted the exact command you have tried and post any error message.

Try ```
cd Desktop/sigh

sudo ./vmware-install.pl
```

[https://help.ubuntu.com/community/VMware/Tools](https://help.ubuntu.com/community/VMware/Tools)

---

### Post by Dedoimedo on 2009-04-02
Here's a big, slow, step-by-step guide for you:

[http://www.dedoimedo.com/computers/vmware-tools.html](http://www.dedoimedo.com/computers/vmware-tools.html)

Cheers,
Dedoimedo

---

### Post by moonshine560 on 2009-04-03
That guide did it. Was way better than the other ones I'd seen.

Thanks a bunch. Was just a command syntax error.

---

### Post by Dedoimedo on 2009-04-04
If "that guide did it" was meant for me, then thanks!
I believe in visual learning ...
Dedoimedo

---

