---
title: "How to LOGIN as root on my Ubuntu Server"
date: 2016-09-11
forum: Virtualisation
---

### Post by jamesbacon on 2016-09-11
What do I need to do to be able to login as root?
Every time I install Ubuntu Server I need to make an account but how do I make a root account?
\I'm asking this because I pay for a VPS and that gives me root login. So how do I get root login for my home server?

No sudo su- stuff.
Just
login: root
password: rootpassword

---

### Post by KillerKelvUK on 2016-09-11
The root account in Ubuntu is disabled by default by not having a password set.  Once you have a working installed using the account created as part of the installation then you (via a terminal)

```

sudo su  <--to access the root account
passwd  <--this will then create a password for the root account

```

You can then login directly as root with your newly created password.  That said why, the direct usage of a root account presents a clear and present danger as an attacker no longer needs to find your username s/he just needs to crack your root password and then they own you...thus use these steps with caution.

---

### Post by jamesbacon on 2016-09-11
Access denied :(

---

### Post by jamesbacon on 2016-09-11
ok when I log in with SSH / Putty it says access denied. But when I log in on the Server its self, it works.

---

### Post by KillerKelvUK on 2016-09-11
> **jamesbacon said:**
> ok when I log in with SSH / Putty it says access denied. But when I log in on the Server its self, it works.

The SSH daemon in Ubuntu has a specific configuration item that prevents/permits root access via SSH using passwords.  Refer to /etc/ssh/sshd_config and you'll probably find a line that reads 'PermitRootLogin prohibit-password' this is what is stopping SSH as root.  Again this is another security feature, I'd strongly urge you to consider moving away from password based authentication and use public/private key pairs, there is an Ubuntu tutorial on this you should find easily from google.

---

### Post by jamesbacon on 2016-09-12
I've tried this and [http://askubuntu.com/questions/469143/how-to-enable-ssh-root-access-on-ubuntu-14-04](http://askubuntu.com/questions/469143/how-to-enable-ssh-root-access-on-ubuntu-14-04) that. And still nothing.

---

### Post by KillerKelvUK on 2016-09-12
Just tested this...

Edit /etc/ssh/sshd_config and set the following two parameters

```

PermitRootLogin yes
PasswordAuthentication yes

```

This allowed me to ssh as root onto my test vm.

---

### Post by jamesbacon on 2016-09-12
ok Thank you do much. Solved.

---

### Post by ian-weisser on 2016-09-12
Security: NEVER NEVER NEVER enable ssh passwords across the internet. ALWAYS use keys. No exceptions. 

Security: NEVER NEVER NEVER enable ssh root logins across the internet. The combination of a root login vulnerable to a dictionary attack pretty much guarantees a quickly compromised system. 'root' is one of the most common account names tried by ssh attackers. Much more work to destroy your compromised server and start over than to simply use good security habits in the first place. Your admin account+sudo are all the power you need.

---

### Post by QIII on 2016-09-12
^ This.

Those are two things hackers specifically try to exploit.  

DigitalOcean.com has some really great tutorials like [this one]("https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-14-04").

Although there is some setup using your root account (from your provider), later on there are instructions to do this with your /etc/ssh/sshd_config:  

```
PermitRootLogin no
```

Also discussed is using keys.


As for KillerKelvUK's advice,

```
PermitRootLogin yes
PasswordAuthentication yes
```

should ***never*** be used.  Period.  Setting your server up like that is the best way to ensure that a hacker will brute force their way into your server.  You might as well hang a sign saying the door is unlocked and the pastries are on the kitchen counter.  Don't even use that on your home server.

This is not an opinion issue.  This is Server Security 101.

---

### Post by Habitual on 2016-09-13
[https://www.digitalocean.com/community/tutorials/how-to-tune-your-ssh-daemon-configuration-on-a-linux-vps](https://www.digitalocean.com/community/tutorials/how-to-tune-your-ssh-daemon-configuration-on-a-linux-vps)

**Strong ssh-key generation:**
```
ssh-keygen -f /path/to/keyfile_rsa -t rsa -N '' -b 4096 -q
```

**Basic usage:**
```
ssh -i /path/to/keyfile_rsa <user>@host
```

wrt: /etc/ssh/sshd_config
and 
```
PermitRootLogin yes
PasswordAuthentication yes
```
is just wrong, *Wrong*, **Wrong** on [COLOR=#ff0000]public-facing servers[/COLOR].

In a controlled environment like Virtualbox, meh, have to practice somewhere. Right?

Very Important distinction.

---

