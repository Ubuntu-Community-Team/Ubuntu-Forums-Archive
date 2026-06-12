---
title: "passwordless non-administrative user = hazard?"
date: 2008-05-01
forum: Security
---

### Post by jakupl on 2008-05-01
My computer has another user without administrative rights.

I used 
```
sudo passwd -d 'user'
```

but it made me think about the possible security hazards doing so.
Is it bad or not?

btw. I am normally a pretty paranoid Ubuntu'er ;)

these are the password-less user's permissions.

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/Screenshot-AccountbartalProperties.png[/IMG]

---

### Post by Dr Small on 2008-05-01
Are you running SSH or FTP?
Generally it is not a wise idea for a passwordless account, but if it can not do much, then there isn't much of a risk.

---

### Post by jakupl on 2008-05-01
eeerhh.. how do I know?

edit: is this what you mean?

[IMG]http://i228.photobucket.com/albums/ee289/jakupl/Screenshot-AccountbartalProperti-3.png[/IMG]

---

### Post by p_quarles on 2008-05-01
> **jakupl said:**
> eeerhh.. how do I know?
According to your first screen shot, the user doesn't have sudo privileges. The only area for concern (in the unlikely event that this account got compromised by a remote attacker) is the modem privileges. If you have a dial-up modem, this account has the permissions to use and configure it. Meaning that an attacker could potentially dial up a 900 number and run up your phone bill. 

Apart from stuff like that, the only threat would be to this user's own files (usually, anything in its home directory). Basically, anything that this user can do could also be done by a remote attacker. 

> edit: is this what you mean?
That's just the default shell environment for that user. In other words, when you open up a terminal emulator while running this user, you get a Bash environment, rather than zsh, dash, csh, python, or any other shell. Nothing to do with security, really.

---

### Post by jakupl on 2008-05-01
great :) in that case, yeah. shell.

thanks, but would it not be easier for a potential hacker to access the administrator account if he already had accessed the other account?

---

### Post by cdenley on 2008-05-02
I think it compromises a layer of security. Ideally, you would want to prevent access to any unauthenticated remote users. If a remote user gained limited access to your machine, I think it would be easier to compromise your system if you have a privilege escalation vulnerability. This is why ssh doesn't permit empty passwords by default. If you don't run any other servers, I don't think it would be an issue.

---

### Post by jakupl on 2008-05-02
well... today this account started behaving a bit strangely, It wouldn't let me log on, so I just gave it a password. Problem solved ;)

---

### Post by lespaul_rentals on 2008-05-06
If you have an SSH daemon running, don't even think about having any user without a password.  Especially since the account name is something fairly obvious, user.  If someone got in with that account, they could use the SSH connection as a tunnel to do illegal things -- not to mention damage your box.

---

### Post by cdenley on 2008-05-06
> **lespaul_rentals said:**
> If you have an SSH daemon running, don't even think about having any user without a password.  Especially since the account name is something fairly obvious, user.  If someone got in with that account, they could use the SSH connection as a tunnel to do illegal things -- not to mention damage your box.

From the default /etc/ssh/sshd_config
> 
# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no


Unless he changes this setting, I don't think that would be possible.

---

### Post by lespaul_rentals on 2008-05-07
> **cdenley said:**
> From the default /etc/ssh/sshd_config


Unless he changes this setting, I don't think that would be possible.

Because vulnerabilities and exploits don't exist.

I get what you're saying, but I wouldn't risk it.  Let's say you have a daemon that you don't need running (think ipp or such).  Who cares if you add an iptables rule to block that port?  Why not just stop the daemon?  If you have an unneccessary opening in your fortress, it's far more secure to rebuild the wall then to stuff a little plaster in the hole.

---

