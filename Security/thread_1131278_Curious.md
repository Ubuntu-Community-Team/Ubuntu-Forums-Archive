---
title: "Curious"
date: 2009-04-20
forum: Security
---

### Post by jordanp123 on 2009-04-20
How do you tell if a account on a system is disabled, Namely Im interested in making sure that through some system changes I haven't advertly enabled the root account on my system. If i try "SU" then enter my password, I always get an authentication failure, does this mean that the account is indeed disabled ? Sorry if this is a dumb question.

---

### Post by sisco311 on 2009-04-20
```
passwd -l root
```disables the root account.

/etc/shadow file stores the password in encrypted format for user's account with additional properties.

```
less /etc/shadows
root:**!**$1$P7cY6z6q$LOL457OLULZD3yrF001HWU/V.:13214::::::
```

! or * indicate that the user will not be able to use the password to log in. 

In other words user login will be disabled.

---

### Post by jordanp123 on 2009-04-20
I just went ahead and ran the first command "Passwd -1 root" to disable it, just in case, it was enabled. Thanks man.

---

### Post by cdenley on 2009-04-21
> **jordanp123 said:**
> I just went ahead and ran the first command "Passwd -1 root" to disable it, just in case, it was enabled. Thanks man.

That should be "sudo passwd -l root" with a lower-case letter "L", not the number "1".

---

### Post by bodhi.zazen on 2009-04-21
Actually ...

```
sudo usermod --lock root
```

    ** sudo passwd root -l will break Ubuntu.

---

### Post by sisco311 on 2009-04-21
> **bodhi.zazen said:**
> Actually ...

```
sudo usermod --lock root
```

    ** sudo passwd root -l will break Ubuntu.

it was a bug, but it's fixed now.

---

### Post by cdenley on 2009-04-21
> **sisco311 said:**
> it was a bug, but it's fixed now.

Or, I always do
```

sudo usermod -p ! root

```
To restore the password hash to the original value "!", instead of inserting a "!" before the current hash.

---

### Post by bodhi.zazen on 2009-04-21
> **sisco311 said:**
> it was a bug, but it's fixed now.

nice to hear it is fixed, do you have a link ? must be quite recent as I just saw this problem I am going to guess a month age ?

> **cdenley said:**
> Or, I always do
```

sudo usermod -p ! root

```To restore the password hash to the original value "!", instead of inserting a "!" before the current hash.

SWEET ! I really, really like that one, I have uses for that.

---

### Post by sisco311 on 2009-04-21
> **bodhi.zazen said:**
> nice to hear it is fixed, do you have a link ? must be quite recent as I just saw this problem I am going to guess a month age ?


[https://bugs.launchpad.net/ubuntu/hardy/+source/shadow/+bug/238755]("https://bugs.launchpad.net/ubuntu/hardy/+source/shadow/+bug/238755")

> **man passwd(Ubuntu)]
-l, --lock
           Lock the password of the named account. This option disables a
           password by changing it to a value which matches no possible
           encrypted value (it adds a ´!´ at the beginning of the password).

           Note that this does not disable the account. The user may still be
           able to login using another authentication token (e.g. an SSH key).
           To disable the account, administrators should use usermod
           --expiredate 1 (this set the account´s expire date to Jan 2, 1970).

           Users with a locked password are not allowed to change their
           password.
[/quote]

[quote=man passwd(arch)]-l, --lock
           Lock the named account. This option disables an account by changing
           the password to a value which matches no possible encrypted value,
           and by setting the account expiry field to 1.
[/quote]

[QUOTE=cdenley said:**
> Or, I always do
```

sudo usermod -p ! root

```
To restore the password hash to the original value "!", instead of inserting a "!" before the current hash.

good to know, it's easier than editing /etc/shadows :)

---

### Post by bodhi.zazen on 2009-04-21
Thanks for the info sysco, are you sure this is a fix and not a fix to landscape-client ?

---

### Post by sisco311 on 2009-04-21
I only know that is fixed from my personal experience(Jaunty). :)

The community documentation also recommends(again) "passwd -l root" to disable the root account. 

[uhelp]community/RootSudo[/uhelp]

---

