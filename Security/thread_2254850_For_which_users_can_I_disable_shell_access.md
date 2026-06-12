---
title: "For which users can I disable shell access"
date: 2014-11-30
forum: Security
---

### Post by astarmathsandphysics on 2014-11-30
I ran a tiger security check and got a lot of users, some of which are used by various processes (and might need shell access?), and got a lot of these messages

--WARN-- [pass014w] Login (user) is disabled, but has a valid shell.

The users are
backup 
bin 
daemon 
gnats 
ibuuid 
list lp 
mail 
man 
nobody 
postgres 
proxy 
root 
sshd 
sync 
sys 
user 
uucp

For which of these users can I disable shell access?

---

### Post by thnewguy on 2014-12-01
If the account is locked then the user cannot login anyway, so it doesn't really matter if they have a shell. I would leave it as it is since the lock on the account prevents people from getting to a shell.

However, if you wanted to you could probably swap out the login shell for just about every user except root. I'd leave the root account alone since you might want to use it in a recovery process sometime.

---

### Post by fugu2 on 2014-12-04
A possible way to test which ones you can change *might* be to install VirtualBox and run a guest VM of the version of Ubuntu you have, create a snapshot after the install of the vm, and make your scary changes inside the vm. If you make a change that was not a good one, you'll just need to restore the previous snapshot.

---

### Post by Habitual on 2014-12-04
> **astarmathsandphysics said:**
> --WARN-- [pass014w] Login (user) is **[COLOR=#0000ff]disabled[/COLOR]**, but has a valid shell.says to me they are disabled, no?

---

### Post by astarmathsandphysics on 2014-12-07
I ask because I disabled access for one of my accounts then wasnt able to use sftp on that account.
Spedicically I am worried that if I disable sshd then I might not be able to use sftp/ssh at all.

---

