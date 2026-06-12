---
title: "update/upgrade"
date: 2012-04-17
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Miykel on 2012-04-17
G"Day,  I tried to do an upgrade/update but I keep getting this return;

code
miykel@miykel-H61M-USB3-B3:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
miykel@miykel-H61M-USB3-B3:~$ 

Has anyone know how to get around this??
Regards Miykel

---

### Post by xebian on 2012-04-17
> **Miykel said:**
> G"Day,  I tried to do an upgrade/update but I keep getting this return;

code
miykel@miykel-H61M-USB3-B3:~$ sudo apt-get dist-upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
miykel@miykel-H61M-USB3-B3:~$ 

Has anyone know how to get around this??
Regards Miykel

Just delete that file and then do apt-get update and then dist-upgrade again.

---

### Post by QIII on 2012-04-17
> **xebian said:**
> Just delete that file and then do apt-get update and then dist-upgrade again.


NO!  DO NOT!

Close the Software Center, Synaptic and the terminal and only open ONE of them.

Using more than one at a time causes this lock condition.

For instance, with Synaptic open and trying to use dist-upgrade in the terminal, the following is appearing in my terminal:

```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by lisati on 2012-04-17
Although you might try deleting the file, it is better to first make sure that you don't have more than one thing that "needs" this file open at the same time, such as software center, synaptic, and update manager.

---

### Post by Miykel on 2012-04-17
Thanks for the reply Xebian; I just tried to delete the "lock" file in /var/lib/dpkg but it will not allow me, I tried to take ownership but I can't cd var/lib/dpkg.
I have no other programs open at all, I don't have synaptic installed and i was only running the terminal at the time, I tried reboot as well but no good.
Any ideas ?
Regards Miykel

---

### Post by QIII on 2012-04-17
Have you closed everything down (Synaptic, update manager, Software Center, terminal, etc) and opened only one of them?

---

### Post by xebian on 2012-04-17
> **Miykel said:**
> Thanks for the reply Xebian; I just tried to delete the "lock" file in /var/lib/dpkg but it will not allow me, I tried to take ownership but I can't cd var/lib/dpkg.
Any ideas ??
Regards Miykel

You have to use sudo

 sudo rm /var/lib/dpkg/lock

---

### Post by Miykel on 2012-04-17
Thanks so much Xebian, that seems to have fixed it, I tried 
code
sudo apt-get dist-update

and received message to run;

code

sudo dpkg --configure -a

done that and it seems to be upgrading again.
many Thanks Miykel

---

### Post by xebian on 2012-04-17
> **Miykel said:**
> Thanks so much Xebian, that seems to have fixed it, I tried 
code
sudo apt-get dist-update

and received message to run;

code

sudo dpkg --configure -a

done that and it seems to be upgrading again.
many Thanks Miykel

np. Glad to be of help.

---

### Post by Bucky Ball on 2012-04-17
Please mark thread as 'Solved' from 'Thread Tools' if it is solved. Cheers. ;)

---

