---
title: "any examples of an edited sudoers list, to include a NT account"
date: 2009-04-07
forum: Security
---

### Post by lithiumKid1976 on 2009-04-07
Hi
if anyone has edited a sudoers list to give thier NT account root privelidges, can they post it here?

(i think this is what i need to do also, as there are some options not available to me when i log on using my NT account)


Thanks

---

### Post by bodhi.zazen on 2009-04-07
What is a NT account ?

---

### Post by cdenley on 2009-04-07
Post the output from running this command while using your "NT account".
```

whoami

```

---

### Post by lithiumKid1976 on 2009-04-08
> **cdenley said:**
> Post the output from running this command while using your "NT account".
```

whoami

```




ok, just to clear this up.
ive installed likewise software to allow me to log on to my ubuntu laptop, with my domain user name and password.

$ whoami
INSTITUTE\dbrennan
$ 

this is all fine, but when i try to open "user and groups" while logged in using this account i get "The configuration could not be loaded, You are not allowed to access the system configuration." 

which is happening (i think) because this account is not in the sudoers list?? and i am looking for users who have this set up so i can follow there example.

(im new to ubuntu, so if anyone can point me in the right direction, id appreciate it)

Thanks
Damien

---

### Post by cdenley on 2009-04-08
While logged in as your admin user, run this command
```

sudo EDITOR=gedit visudo

```
add this line to the end
```

INSTITUTE\dbrennan ALL=(ALL) ALL

```
Save, close. I think that should work. Never tried it before with an external Windows Domain user. How did you configure ubuntu to use your Windows Domain for authentication? Likewise?

---

### Post by lithiumKid1976 on 2009-04-08
> **cdenley said:**
> While logged in as your admin user, run this command
```

sudo EDITOR=gedit visudo

```
add this line to the end
```

INSTITUTE\dbrennan ALL=(ALL) ALL

```
Save, close. I think that should work. Never tried it before with an external Windows Domain user. How did you configure ubuntu to use your Windows Domain for authentication? Likewise?

Hi
i edited that file, but im still getting the same error.
you are correct about likewise, i installed the latest version of it yesterday.
Thanks
Damien

---

### Post by cdenley on 2009-04-08
[http://ubuntuforums.org/showthread.php?t=766763](http://ubuntuforums.org/showthread.php?t=766763)
It seems you need to escape the backslash in the sudoers file
```

INSTITUTE\\dbrennan ALL=(ALL) ALL

```

---

### Post by lithiumKid1976 on 2009-04-08
> **cdenley said:**
> [http://ubuntuforums.org/showthread.php?t=766763](http://ubuntuforums.org/showthread.php?t=766763)
It seems you need to escape the backslash in the sudoers file
```

INSTITUTE\\dbrennan ALL=(ALL) ALL

```



Hi
ok ive edited the sudoers file as such


[I]# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Uncomment to allow members of group sudo to not need a password
# (Note that later entries override this, so you might need to move
# it further down)
# %sudo ALL=NOPASSWD: ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%INSTITUTE\\dbrennan ALL=(ALL) ALL[/I]




But im still getting the same error. ive also edited it without the % sign at the start... any other suggestion for me to check?
thanks again..

---

### Post by cdenley on 2009-04-08
The "%" only precedes a groupname.
```

%group ALL=(ALL) ALL
user ALL=(ALL) ALL

```
You can try using your group instead of your username, since that seemed to work on the other thread. You can use this command to get your primary group.
```

id -gn

```

---

### Post by lithiumKid1976 on 2009-04-08
> **cdenley said:**
> The "%" only precedes a groupname.
```

%group ALL=(ALL) ALL
user ALL=(ALL) ALL

```
You can try using your group instead of your username, since that seemed to work on the other thread. You can use this command to get your primary group.
```

id -gn

```

Hi
ran that command, got the primary group 'domain users', edited that into the sudoers file, but still no joy...

thanks for all your help...

---

