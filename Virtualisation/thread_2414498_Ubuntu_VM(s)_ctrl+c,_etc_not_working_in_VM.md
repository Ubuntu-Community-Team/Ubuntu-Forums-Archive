---
title: "Ubuntu VM(s) ctrl+c, etc not working in VM?"
date: 2019-03-11
forum: Virtualisation
---

### Post by bobmct on 2019-03-11
The system config:
host running Linux-Mint 19.1 with VirtualBox 6.0.0.4 installed.  Ubuntu 15.04 server and 18.10 server VM's installed.   As only tty is available I noticed that the ctrl+? combo don't work.
I've tried running showkey to display the received keystrokes and they show the same whether from the host or client.  But Ubuntu within the guest ignores the ctrl character so if I try to abort a process pressing ctrl+c simply shows a c character and that's it.  same with all other ctrl+combos.   If I use the VBox menu to insert a ctrl+break it works fine.

I've been using VBox with ubuntu server vm's for many, many years and just noticed this.  I've also reverted to Vbox 6.0.0.2 and 5.2.x with the same results.
So, I thought I would ask here to see if anyone else has experienced this strange anomaly and if so how they overcame it.  It's quite annoying...
Thanks:confused:

---

### Post by &amp;KyT$0P# on 2019-03-11
Is your host key set to Ctrl ?

---

### Post by bobmct on 2019-03-12
My VM host key is set to 'right shift'
Just FYI - I tried loading several distros into VBOX and I see the same results which leads me to believe its a Vbox issue.  But I'm just doing my due diligence asking here looking for any other ideas.

---

### Post by ajgreeny on 2019-03-12
Ctrl+C or Ctrl+V will not work in a tty terminal, ie command line; this is exactly the same as using a terminal in GUI mode, where you have to use Ctrl+Shift+C or V.

For other uses in a VM I am not certain but in a VM running a guest GUI OS such as Ubuntu you will normally need the Host key (right Ctrl by default, which you must have changed) +F1-6 in order to move to a tty terminal in the VM itself.  Ctrl+Alt+F1-6 will take you to a tty in the host, not the guest VM.

---

