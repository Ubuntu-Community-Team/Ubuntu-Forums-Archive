---
title: "Disabling a &quot;valid&quot; shell"
date: 2008-10-15
forum: Security
---

### Post by MidnightJulia on 2008-10-15
Hi! 

I scanned my computer the other day using tiger and while reading the log file  I found an interesting detail. "Login (root) is disabled, but has a valid shell". Being the curios cat that I am, I looked up root account in the passwd file and yes, there is a shell assigned to it. But how do I remove it? Should I delete the text or change it to something else? Would it do any good at all since the account doesn't have a password? 

/MJ

---

### Post by Dr Small on 2008-10-15
I'm not real sure how Ubuntu operates in this field anymore, but it could very well be a false positive. If you don't mind, could you post the line that contains the information for root in /etc/passwd, that way we can see what shell he actually is using.

Totally disabling the root account is a bad idea because if you ever need recovery mode, you could fairly easily ruin your only chance at getting root.

Dr Small

---

### Post by Dr Small on 2008-10-15
--Double post--

---

### Post by cdenley on 2008-10-15
You might not want to give root an invalid shell. You probably won't have any problems, but some scripts or applications might try using root's shell when using root permissions. For example, this would fail if you changed root's shell to /bin/false.
```

sudo su

```
It isn't really a security risk to have a valid shell for disabled accounts, just a "better safe than sorry" type of thing.

---

### Post by MidnightJulia on 2008-10-15
> **Dr Small said:**
> I'm not real sure how Ubuntu operates in this field anymore, but it could very well be a false positive. If you don't mind, could you post the line that contains the information for root in /etc/passwd, that way we can see what shell he actually is using.

Of course! The entry for root is: 
```
root:x:0:0:root:/root:/bin/bash
```

> Totally disabling the root account is a bad idea because if you ever need recovery mode, you could fairly easily ruin your only chance at getting root.

Thanks for the warning :)

---

### Post by MidnightJulia on 2008-10-15
> **cdenley said:**
> You might not want to give root an invalid shell. You probably won't have any problems, but some scripts or applications might try using root's shell when using root permissions. For example, this would fail if you changed root's shell to /bin/false.
```

sudo su

```
It isn't really a security risk to have a valid shell for disabled accounts, just a "better safe than sorry" type of thing.

So this would mean that eg sudo bash and sudo su would not be possible to use for gaining superuser privileges? I agree that such an edit would cripple the system. 

However the other accounts with shells should be safe to change to /bin/false? :)

---

### Post by cdenley on 2008-10-15
> **MidnightJulia said:**
> So this would mean that eg sudo bash and sudo su would not be possible to use for gaining superuser privileges? I agree that such an edit would cripple the system. 

However the other accounts with shells should be safe to change to /bin/false? :)

Generally, you wouldn't have a problem. You would still be able to use sudo, since by default it uses your shell, not the target user's. The su command uses the target user's shell, but su isn't used much in ubuntu. Setting the shell to /bin/false for accounts which server applications run as is typical, because the server application does not require a shell. If somehow, an attacker managed to login to your ssh server as ftp or gdm, they wouldn't be able to do much without a shell.

---

### Post by Gamma746 on 2008-10-15
> **MidnightJulia said:**
> However the other accounts with shells should be safe to change to /bin/false? :)

I'd suggest /sbin/nologin instead; it logs attempted logins.

Don't disable the shells of any account you plan on using, of course.

---

