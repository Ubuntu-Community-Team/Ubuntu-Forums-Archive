---
title: "Need help installing Vmware tools"
date: 2010-02-15
forum: Virtualisation
---

### Post by sync00 on 2010-02-15
I'm running Vmware Player v3 in Win 7. I downloaded the 'official' Ubuntu 9.04 appliance. I keep losing the mouse cursor. I'm trying to install Vmware tools.


I extracted the tools to the desktop. When I run 'vmware-install.pl' and select 'Run in Terminal' a window pops up for a fraction of a second and then closes and the tools are not installed.

---

### Post by dcstar on 2010-02-26
> **sync00 said:**
> I'm running Vmware Player v3 in Win 7. I downloaded the 'official' Ubuntu 9.04 appliance. I keep losing the mouse cursor. I'm trying to install Vmware tools.


I extracted the tools to the desktop. When I run 'vmware-install.pl' and select 'Run in Terminal' a window pops up for a fraction of a second and then closes and the tools are not installed.

Follow the instructions in the various threads at the top of this forum.

They will say open a terminal, go to where you have downloaded the software and:

```
sudo ./vmware-install.pl
```

---

### Post by sync00 on 2010-02-26
> **dcstar said:**
> Follow the instructions in the various threads at the top of this forum.

They will say open a terminal, go to where you have downloaded the software and:

```
sudo ./vmware-install.pl
```
I'm not a big fan of using the terminal. I guess that means Linux isn't for me.

---

### Post by dcstar on 2010-02-27
> **sync00 said:**
> I'm not a big fan of using the terminal. I guess that means Linux isn't for me.

If you are incapable of opening a terminal and running one simple command, then I would say you are correct.

---

### Post by HermanAB on 2010-02-27
You most likely have the wrong (or no) kernel headers installed.

---

### Post by dcstar on 2010-02-28
> **HermanAB said:**
> You most likely have the wrong (or no) kernel headers installed.

It has nothing to do with it, vmware-install.pl must be run with sudo - as the instructions say.

The OP is just incapable of opening a terminal and following this simple procedure.

---

### Post by tilixibr on 2010-05-02
The terminal is a tool that you will probably need to use a lot if you're going to use Linux. If you can't use the terminal, you may end up causing more damage than good to the system. I suggest you try to learn the basics by buying/borrowing a book explaining the basics, or finding a tutorial online. That's how I learned to use Linux :)

Linux is a great OS, and I believe everyone should always learn something new :)

---

