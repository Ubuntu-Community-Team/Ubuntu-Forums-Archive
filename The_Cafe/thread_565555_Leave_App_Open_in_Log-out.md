---
title: "Leave App Open in Log-out"
date: 2007-10-02
forum: The Cafe
---

### Post by Black Mage on 2007-10-02
In Ubuntu, I have VMware Server running a SQL Server 2000. When I boot into Ubuntu I have to start up it and it shuts down when I log out but I want to keep the VMware running for other users to access the database when I log out.

Is there a way that I can do this?

---

### Post by stimpack on 2007-10-02
Being a server does it run from the command line?. If so killing your shell will kill the server.

Use 'screen' first
run vmware
detach from shell with ctrl-a d
logout

it will be running in the background.

If its a GUI app or not what you wanted, I apologise.

---

### Post by Black Mage on 2007-10-02
No,it logs in through a GUI, but thnx for your help though. But is there a way to leave the App running when I log-out through a GUI? And I'm using Fiesa Fawn.

---

### Post by maniacmusician on 2007-10-02
Feisty Fawn*

But no, you can't leave a GUI app running when you log out, because it's tied to your X session, and when the session ends, all those apps end as well. If you can find a way to run vmware from the command line (there should be a way), yo can do as stimpack suggested.

---

### Post by Black Mage on 2007-10-02
i can ssh into my computer from another with no problem and the command line for running VMServer is vmware. But  the -X?

---

### Post by zachtib on 2007-10-02
i've got vmware server running as well, if I leave the VM running when i close vmware, the vms continue running in the background.

i connect remotely to my server from my laptop, so what you want should be possible

---

### Post by Hossie on 2007-10-02
VMware itself is a daemon, it keeps running when closing VMware Server Console. If you really want to keep VMware Server Console (the GUI App) running, use NoMachine (NX).

---

