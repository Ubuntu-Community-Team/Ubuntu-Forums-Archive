---
title: "Lots of strange users registered in my system"
date: 2008-08-14
forum: Security
---

### Post by TaTaE on 2008-08-14
I would like to know if there is a list with known system users created by various applications, where anyone can check his passwd file. I noticed a bunch of strange user accounts which are not quite kusher on my desktop system.
 I have now 37 system accounts on my system and I really don't know which one is legit and which is not.
 Again, I would like to find an OFFICIAL UBUNTU LIST OF SYSTEM USER ACCOUNTS AND THE CORRESPONDING APPLICATION.

---

### Post by kerry_s on 2008-08-14
huh? post your /etc/group

---

### Post by cariboo on 2008-08-14
Run the following script to see the list of users on your system:

```
cat /etc/passwd | cut -d":" -f1
```

Jim

---

### Post by TaTaE on 2008-08-15
Here it is( I have eliminated the ones created by me):
root
daemon
bin
sys
sync
games
man
lp
mail
news
uucp
proxy
www-data
backup
list
irc
gnats
nobody
dhcp
syslog
klog
messagebus
hplip
avahi-autoipd
avahi
haldaemon

postfix
ntop
sshd
dnsmasq
festival

clamav
saned
polkituser
pulse
gdm

libuuid

 Users like gnats, sync, list, www-data, backup, saned, sys, make you really think if this is a desktop system or a dam' server.

---

### Post by kerry_s on 2008-08-15
looks fine, i see nothing to worry about.

---

### Post by kostkon on 2008-08-15
You are OK.

---

### Post by adieb on 2008-08-16
who is festival?

---

### Post by kerry_s on 2008-08-16
> **adieb said:**
> who is festival?

festival is a program. it's part of gnome accessibility.

---

### Post by TaTaE on 2008-08-16
I'd like to say that it would be best to have at least a wiki page which shows all possible system users in ubuntu, where anyone interested could check the users found on his system against the official list.

---

### Post by Vishal Agarwal on 2008-08-16
There is nothing to worry. There is no unusual user. Most of them are system accounts.

---

### Post by TaTaE on 2008-08-16
> **Vishal Agarwal said:**
> There is nothing to worry. There is no unusual user. Most of them are system accounts.

Thank you, but the point was that anyone could use a list of known system users in ubuntu. An official list would be great for the wiki.ubuntu.com

---

### Post by scorp123 on 2008-08-17
> **TaTaE said:**
>  I noticed a bunch of strange user accounts  You can check if those are accounts are even able to login remotely, e.g. 
```
sudo cat /etc/shadow
``` ... The terminal should spit out something like this:
 ```
root:$34AGf347348.Ug6869863$$.:13887:0:99999:7:::
daemon:*:13801:0:99999:7:::
bin:*:13801:0:99999:7:::
sys:*:13801:0:99999:7:::
sync:*:13801:0:99999:7:::
games:*:13801:0:99999:7:::
man:*:13801:0:99999:7:::
lp:*:13801:0:99999:7:::
mail:*:13801:0:99999:7:::
news:*:13801:0:99999:7:::
uucp:*:13801:0:99999:7:::
proxy:*:13801:0:99999:7:::
www-data:*:13801:0:99999:7:::
backup:*:13801:0:99999:7:::
list:*:13801:0:99999:7:::
irc:*:13801:0:99999:7:::
gnats:*:13801:0:99999:7:::
nobody:*:13801:0:99999:7:::
dhcp:!:13801:0:99999:7:::
syslog:!:13801:0:99999:7:::
klog:!:13801:0:99999:7:::
messagebus:!:13801:0:99999:7:::
hplip:!:13801:0:99999:7:::
avahi-autoipd:!:13801:0:99999:7:::
avahi:!:13801:0:99999:7:::
haldaemon:!:13801:0:99999:7:::
gdm:!:13801:0:99999:7:::
sysadm:$1$///7834.7034.70fhd.$lh2390efjdf///$:13833:0:99999:7:::
sshd:!:13833:0:99999:7:::
lastfmproxy:!:13838:0:99999:7:::
uml-net:!:13865:0:99999:7:::
ntp:!:13879:0:99999:7:::
statd:!:14085:0:99999:7::: 
``` 

The second field (the stuff after the username) is important: That's the password in its encrypted form. 

According to my output above only two users on my system have that:

- root (yes, I enabled the "root" account on my system)
- sysadm

The rest of the users have an exclamation mark "!" or an asterisk "*" in that field, meaning they can't login on a console or remotely via SSH.

So as long as you don't see "strange" accounts with a password attached to them, everything should be fine.

Taken straight from the manual: ```
man 5 shadow
``` ... there it says:  > If the password field contains some string that is not valid result of crypt(3), for instance ! or *, the user will not be able to use a unix password to log in, subject to pam(7).

---

### Post by TaTaE on 2008-08-20
thats great, thank you.

---

### Post by scorp123 on 2008-08-21
> **TaTaE said:**
> thats great, thank you. Feel free to hit that "thank you" button ;)

---

