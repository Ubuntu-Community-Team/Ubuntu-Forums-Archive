---
title: "disabling sudo -i"
date: 2008-09-30
forum: Security
---

### Post by santhoshsd on 2008-09-30
How to disable sudo -i for a user ?

---

### Post by cdenley on 2008-09-30
> **santhoshsd said:**
> How to disable sudo -i for a user ?

You can add something like this to your sudoers file
```

myuser ALL = !/bin/bash
myuser ALL = !/bin/sh

```
but if they have permission to run commands as root, getting around it would be rather trivial
```

sudo ln -s /bin/bash /bin/bash_for_myuser
sudo /bin/bash_for_myuser

```

---

### Post by santhoshsd on 2008-09-30
Hi cdenley,

I want the user to have permissions to do  "sudo apt-get" (package installations) but I want to restrict the user from becoming root 
(sudo -i, su).

and one more question 
Is it possible to make some files inaccessible to a user who can execute sudo commands ?

---

### Post by cdenley on 2008-09-30
> **santhoshsd said:**
> Hi cdenley,

I want the user to have permissions to do  "sudo apt-get" (package installations) but I want to restrict the user from becoming root 
(sudo -i, su).

and one more question 
Is it possible to make some files inaccessible to a user who can execute sudo commands ?

```

export EDITOR=nano
sudo -E visudo

```
add this to the end of the file
```

myuser ALL = (ALL) /usr/bin/apt-get

```
The user will be able to run apt-get as root, but not a shell, which would cause "sudo -i" to fail. I don't think there is any way to restrict filesystem access through sudo, you can only restrict which files they can execute.

---

### Post by santhoshsd on 2008-09-30
Hi,
I tried with

```

# User alias specification
User_Alias  PARTTIME = friend
# Cmnd alias specification
Cmnd_Alias APT=/usr/bin/apt-get, /usr/bin/dpkg
Cmnd_Alias SUI=/usr/bin/sudo -i,/bin/su

# User privilege specification
root    ALL=(ALL) ALL
PARTTIME  ALL=(ALL) APT,!SUI
```


now user *'friend'* is not able to execute sudo -i but he's able to execute sudo apt-get.

with this can I be assured that user *'friend'* cannot su or sudo to root?

> I don't think there is any way to restrict filesystem access through sudo, you can only restrict which files they can execute. 



can I restrict modification/deletion of certain files owned by root from the sudo user ?

---

### Post by cdenley on 2008-09-30
> **santhoshsd said:**
> Hi,
I tried with

```

# User alias specification
User_Alias  PARTTIME = friend
# Cmnd alias specification
Cmnd_Alias APT=/usr/bin/apt-get, /usr/bin/dpkg
Cmnd_Alias SUI=/usr/bin/sudo -i,/bin/su

# User privilege specification
root    ALL=(ALL) ALL
PARTTIME  ALL=(ALL) APT,!SUI
```


now user *'friend'* is not able to execute sudo -i but he's able to execute sudo apt-get.

with this can I be assured that user *'friend'* cannot su or sudo to root?



can I restrict modification/deletion of certain files owned by root from the sudo user ?

Well, if you let them run dpkg, they can probably create a package that runs a script on installation which gives them a shell prompt, or even modifies their own sudo privileges by editing /etc/sudoers. At least with apt-get, they would probably have to spoof ubuntu's dns records in order to be able to install their own packages.

You can restrict modification/deletion of certain files.
```

sudo chattr +i /path/to/myfile

```
Nobody will be able to modify it (even root) until this command is run.
```

sudo chattr -i /path/to/myfile

```
There is no sudo configuration that would restrict this exclusively for people running commands in sudo. When running a command with sudo, root is accessing the file.

---

