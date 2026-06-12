---
title: "Ubuntu wont let me disable ping"
date: 2010-08-11
forum: Security
---

### Post by dogdo on 2010-08-11
Ive just read this [https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW) and so i tried this command [B]/etc/ufw/before.rules

but when i enter the command into the terminal i get-


daddy@ubuntu:~$ /etc/ufw/before.rules
bash: /etc/ufw/before.rules: Permission denied
daddy@ubuntu:~$ 


Why didn't ubuntu ask me for my sudo password?

[/B]

---

### Post by Bachstelze on 2010-08-11
> **dogdo said:**
> 
Why didn't ubuntu ask me for my sudo password?


Because you didn't use sudo, but anyway, this is a file you must edit, not a command.

---

### Post by brujoquizz on 2010-08-11
In order to edit that file you should type:

```
sudo pico /etc/ufw/before.rules
```

"sudo" is to edit the file as root, "pico" is a easy to use editor to open teh file with.

---

### Post by bodhi.zazen on 2010-08-11
> **brujoquizz said:**
> In order to edit that file you should type:

```
sudo pico /etc/ufw/before.rules
```"sudo" is to edit the file as root, "pico" is a easy to use editor to open teh file with.

s/pico/nano

I am not sure if pico is installed in Ubuntu (nano is very similar to pico).

EDIT: Me bad, pico is installed.

```
sudo -e /etc/ufw/before.rules
```

If you wish a graphical editor use gksu and gedit

```
gksu gedit /etc/ufw/before.rules
```

---

### Post by Bachstelze on 2010-08-11
> **bodhi.zazen said:**
> 
EDIT: Me bad, pico is installed.


It is actually just a symlink to nano:

```
firas@itsuki ~ % ls -l /usr/bin/pico
lrwxrwxrwx 1 root root 22 2010-08-11 17:01 /usr/bin/pico -> /etc/alternatives/pico
firas@itsuki ~ % ls -l /etc/alternatives/pico
lrwxrwxrwx 1 root root 9 2010-08-11 17:01 /etc/alternatives/pico -> /bin/nano

```

At least by default, until you install pico itself if you wish.

*EDIT:* Actually no, pico itself is not even in the repos, so pico is always just an alias for nano (unless you want to install it from source).

---

### Post by bodhi.zazen on 2010-08-11
> **Bachstelze said:**
> It is actually just a symlink to nano:

```
firas@itsuki ~ % ls -l /usr/bin/pico
lrwxrwxrwx 1 root root 22 2010-08-11 17:01 /usr/bin/pico -> /etc/alternatives/pico
firas@itsuki ~ % ls -l /etc/alternatives/pico
lrwxrwxrwx 1 root root 9 2010-08-11 17:01 /etc/alternatives/pico -> /bin/nano

```At least by default, until you install pico itself if you wish.

*EDIT:* Actually no, pico itself is not even in the repos, so pico is always just an alias for nano (unless you want to install it from source).

Thanks for the information.

---

### Post by dogdo on 2010-08-11
Ok i made those changes to ufw firewall (ufw ping is set to drop). Im connected via a vpn so the vpn provider also has a firewall yes? 

According to the shields up website ping is replied to and port 443 is open. Can i complain to my vpn provider about this? is this not safe? Since my firewall is fully enabled now it must be their firewall thats allowing this traffic...

---

### Post by bodhi.zazen on 2010-08-11
> **dogdo said:**
> Ok i made those changes to ufw firewall (ufw ping is set to drop). Im connected via a vpn so the vpn provider also has a firewall yes? 

According to the shields up website ping is replied to and port 443 is open. Can i complain to my vpn provider about this? is this not safe? Since my firewall is fully enabled now it must be their firewall thats allowing this traffic...

What are you scanning with shields up ?

your router ? your VPN ?

---

### Post by dogdo on 2010-08-11
i scanned my vpn with shields up..i also tested the router firewall and the ufw firewall via the router with the router firewall disabled. Should i complain to my vpn provider?

---

### Post by bodhi.zazen on 2010-08-11
> **dogdo said:**
> i scanned my vpn with shields up..i also tested the router firewall and the ufw firewall via the router with the router firewall disabled. Should i complain to my vpn provider?

The decision is your call, I am not clear what you are going to complain about exactly or what you expect to occur as a result of the complaint.

---

