---
title: "ubuntu in vmware: keyboard issues"
date: 2008-01-07
forum: Virtualisation
---

### Post by jmehdi on 2008-01-07
I'm on Ubuntu 7.10, on a Core duo laptop and I've installed ubuntu 7.10 in vwmare workstation 6.0.0 build-45731.

I've strange problems with the keyboard, sometimes when I type something it displays multiple times the same letter, for example in a terminal: "ssssudo appptitude"

I've tried different configurations for my virtual machine (1 or 2 processors for example) ; I've disabled the CPU frequency scaling, but still the same problem...

Any idea?

---

### Post by popch on 2008-01-07
> **jmehdi said:**
> I'm on Ubuntu 7.10, on a Core duo laptop and I've installed ubuntu 7.10 in vwmare workstation 6.0.0 build-45731.

I've strange problems with the keyboard, sometimes when I type something it displays multiple times the same letter, for example in a terminal: "ssssudo appptitude"

I've tried different configurations for my virtual machine (1 or 2 processors for example) ; I've disabled the CPU frequency scaling, but still the same problem...

Any idea?

Ideas (not diagnostics):

Faulty keyboard

User 'types' exceedingly slow and holds down keys for long times

Virtual machine loses track of time and believes that user holds down keys for a long time. You can adjust the time for the keyboard driver to wait until it enters typamatic mode. I would look in System/Settings/Keyboard or in /System/Settings/Accessibility.

---

### Post by andr3w on 2009-01-27
> **popch said:**
> Ideas (not diagnostics):

User 'types' exceedingly slow and holds down keys for long times



lol...

---

