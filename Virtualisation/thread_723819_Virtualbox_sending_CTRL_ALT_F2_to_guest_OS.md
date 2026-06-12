---
title: "Virtualbox sending CTRL ALT F2 to guest OS"
date: 2008-03-13
forum: Virtualisation
---

### Post by Ikith on 2008-03-13
I'm in need of some help with virtual box. I have Fedora core 6 (I need this for college) installed as a guest and I need to access tty1-6. But whenever I try to send a ctrl+alt+f1 by hitting the keys my ubuntu install (host os) picks it up instead.

So I was wondering if there was a way to send a ctrl+alt+f1 to the guest OS.

---

### Post by kyphi on 2008-03-13
Open VirtualBox then go to File (top left corner), Preferences, Input and place a tick into Autocapture Keyboard.

Alternatively, go through the menu items to open a terminal.

---

### Post by jnylen on 2008-04-25
I have VirtualBox 1.5.6 and the combination that works for me is Host+F1 through Host+F12 (My host key is set to Right Ctrl but yours might be something different).  I think the developers put these key combos in there specifically for that purpose.

---

### Post by breadstic on 2008-11-10
> **jnylen said:**
> I have VirtualBox 1.5.6 and the combination that works for me is Host+F1 through Host+F12 (My host key is set to Right Ctrl but yours might be something different).  I think the developers put these key combos in there specifically for that purpose.

thanks jnylen,
Exactly what i was looking for...
Right Ctrl + F1 worked for me. I don't know how I did it but I got dumped to busybox during ubuntu install. Must have pressed ctrl + f2 or something by accident.

---

### Post by hellmet on 2009-08-12
> **jnylen said:**
> I have VirtualBox 1.5.6 and the combination that works for me is Host+F1 through Host+F12 (My host key is set to Right Ctrl but yours might be something different).  I think the developers put these key combos in there specifically for that purpose.
Thanks.. was feeling quite handicapped without that.

---

### Post by asashnov on 2009-10-02
Host: ubuntu 8.04
virtualbox-3.0            3.0.4-50677_Ubuntu_hardy

For switch between virtual consoles into guest Linux works following:    Alt + HOST KEY + F1...F7

---

### Post by xtangj on 2012-10-26
> **Ikith said:**
> I'm in need of some help with virtual box. I have Fedora core 6 (I need this for college) installed as a guest and I need to access tty1-6. But whenever I try to send a ctrl+alt+f1 by hitting the keys my ubuntu install (host os) picks it up instead.

So I was wondering if there was a way to send a ctrl+alt+f1 to the guest OS.



hi push ctrl+tab+f1 or f2 
no push ctrl+ALT

goodlook:guitar:

---

### Post by inderchauhan on 2013-02-12
Hi

My worked.. ctrl(hostkey)+ delete

---

