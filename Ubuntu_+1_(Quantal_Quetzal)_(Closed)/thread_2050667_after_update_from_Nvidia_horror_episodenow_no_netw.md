---
title: "after update from Nvidia horror episode/now no network."
date: 2012-08-31
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by ventrical on 2012-08-31
I just got back to updating two good installs on the same machine that had the <nvidia-horror> crazed screen with xorg.. etc.

 The way I updated these 2 installs was that I had to do it through using GRUB recovery. I would then log on to network, then root, login, <sudo apt-get update> <sudo apt-get upgrade> reboot and I got my Unity 3D DEs back, but firefox nor even through terminal I cannot get network to work.  The network inidcator is working and has me online but Firefox and Synaptic and terminal tell me they cannot find server.

Any ideas as to what happened here?

---

### Post by doktorOblivion on 2012-08-31
What I normally do when this happens with XFCE is I trying clearing my cache first.  I would back them up first, since I am not sure if they will have adverse affects with Unity.

rm -fr .cache
rm -fr .gconf*
rm -fr .conf

I would try just .cache first and move on from there.  I think there might be something cache that no longer works.

---

### Post by VinDSL on 2012-08-31
> **ventrical said:**
> Any ideas as to what happened here?
I noticed there was a NM package update on 29-Aug-2012 -- network-manager (0.9.6.0-0ubuntu5) quantal

I didn't have any probs, but you might try rolling back NM to ver. 4 or 3.

---

### Post by VinDSL on 2012-08-31
Whoops!  Spoke too soon.

SSH/SFTP/SCP aren't working now...

---

### Post by cariboo on 2012-08-31
> **VinDSL said:**
> Whoops!  Spoke too soon.

SSH/SFTP/SCP aren't working now...

SSH/SFTP/SCP work for me, but I found earlier today that NFS wasn't working. I just checked samba, and it's working too,

---

### Post by ventrical on 2012-09-01
> **VinDSL said:**
> Whoops!  Spoke too soon.

SSH/SFTP/SCP aren't working now...


 Thanks Vin.

 I have been able enable network from GRUB, login, run lightdm and then logon with no problems :). for now.

---

### Post by VinDSL on 2012-09-01
Got "secure login" working now, too.  ;)

It was the same-old-thing...

[INDENT]LINKAGE:  [http://ubuntuforums.org/showthread.php?p=11942203](http://ubuntuforums.org/showthread.php?p=11942203)[/INDENT]


Had to edit /etc/ssh/sshd_config (again):

```
Change to:

[INDENT]RSAAuthentication no

GSSAPIAuthentication no[/INDENT]
```

---

### Post by ventrical on 2012-09-01
Now, all of a sudden, the network is working after the last login from GRUB.

I just ran recovery, and not  use the network option , so it looks as if has healed itself again.

---

