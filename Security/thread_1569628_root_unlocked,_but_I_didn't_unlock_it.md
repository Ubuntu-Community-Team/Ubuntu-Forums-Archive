---
title: "root unlocked, but I didn't unlock it"
date: 2010-09-07
forum: Security
---

### Post by Chris1274 on 2010-09-07
So I was testing to see what would happen if I tried to open a root shell in recovery mode, WITHOUT having first activated the root-user account (I only installed the system two days ago). I used my ordinary password and was expecting to see something like "Invalid password" or some such message. To my surprise, I got a root prompt. Thinking that this may just be how it works with recovery mode, I tried logging out of my X session and logging back in as root, thinking (or at least hoping) that it wouldn't work. But it did.

Any ideas as to what's going on?

---

### Post by garvinrick4 on 2010-09-07
It will be in this file:
```
gksudo gedit /etc/sudoers
```

Have to be in root to open so be care full.```

```

---

### Post by BkkBonanza on 2010-09-07
Isn't that the purpose of recovery mode? To get root access to fix things. 
I haven't checked recently but I thought when starting in recovery mode you get root by default... with no password, so you can fix password issues and low level problems.

As they say, Physical access = Root access.

Also, **visudo** should always be used to edit /etc/sudoers so that syntax checking prevents you from hosing everything in there.

---

### Post by Chris1274 on 2010-09-07
> **BkkBonaza said:**
> Isn't that the purpose of recovery mode? To get root access to fix things. 
I haven't checked recently but I thought when starting in recovery mode you get root by default... with no password, so you can fix password issues and low level problems.

As they say, Physical access = Root access.

Also, **visudo** should always be used to edit /etc/sudoers so that syntax checking prevents you from hosing everything in there.

Someone had mentioned in another thread that you can accomplish whatever you need to do in recovery mode without being logged in as root, so I assumed they're not equivalent. If so, that still doesn't explain why I can log into X as root. That's not supposed to be an option unless I activate the root account, which I haven't done, at least not intentionally.

---

### Post by The Cog on 2010-09-07
My understanding is that recovery mode places you in root automatically. In most systems, you need to give the root password, but because Ubuntu keeps the root account locked, it has been modified to not require the root password at all - otherwise there would be no recovery possible.

It is also my understanding that if a root password is set, then recovery mode reverts to normal and requires that password. It's only when the root account is locked that recovery allows you in without a password at all.

---

### Post by BkkBonanza on 2010-09-07
I don't think Ubuntu is different in that regard. 
On my Centos system before recovery mode also didn't require a password.
Centos being the same as Red Hat, I think it's standard for recovery mode.
The only thing is on Centos I recall you had to edit the kernel boot line to get recovery mode whereas in Ubuntu they made it a menu item.
But I'm just going on rather stale memory now as it's been years.

---

### Post by endotherm on 2010-09-07
all else aside, if the account is enabled you can relock it with this:
```
sudo passwd root -l
```

---

### Post by FuturePilot on 2010-09-07
> **endotherm said:**
> all else aside, if the account is enabled you can relock it with this:
```
sudo passwd root -l
```

That is not the correct way to re-disable the root account in Ubuntu. [https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account]("https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account")

---

### Post by The Cog on 2010-09-07
> **FuturePilot said:**
> That is not the correct way to re-disable the root account in Ubuntu. [https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account]("https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account")

They suggest "sudo usermod -p '!' root". But what's the difference?

---

### Post by FuturePilot on 2010-09-07
> **The Cog said:**
> They suggest "sudo usermod -p '!' root". But what's the difference?

When you use passwd -l it it locks the account and marks the account expired. This means that things like root cron jobs break. Using the recommended method it only sets the password to an impossible value by putting a '!' in front of the password hash.

---

### Post by endotherm on 2010-09-07
> **FuturePilot said:**
> That is not the correct way to re-disable the root account in Ubuntu. [https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account]("https://help.ubuntu.com/community/RootSudo#Re-disabling%20your%20root%20account")


from man passwd
> 
-l, --lock
           Lock the password of the named account. This option disables a
           password by changing it to a value which matches no possible
           encrypted value (it adds a ´!´ at the beginning of the password).from man usermod
> 
-p, --password PASSWORD
           The encrypted password, as returned by crypt(3).

           Note: This option is not recommended because the password (or
           encrypted password) will be visible by users listing the processes.

           The password will be written in the local /etc/passwd or
           /etc/shadow file. This might differ from the password database
           configured in your PAM configuration.

           You should make sure the password respects the systems password
           policy.
so the command 
```

sudo usermod -p '!' root

```does almost exactly the same thing as passwd -l. the important part of the operation is to make sure that '!' is the first char in the password, making the account unusable. 
the only diff is that in passwd, the ! prepends the existing password, whereas usermod eliminates the password, and appends a !.

---

### Post by Chris1274 on 2010-09-07
I used the usermod approach. I'm still mystified as to how the account got enabled to begin with :?:

---

