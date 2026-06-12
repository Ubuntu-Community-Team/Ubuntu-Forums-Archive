---
title: "Make shutdown available for all users"
date: 2008-07-13
forum: Security
---

### Post by wemersonrv on 2008-07-13
Hi,

When i try to run the **shutdown** command, the root rights are required (or sudo/su) to run this...

There are a way to configure this command to run in all users without root privileges? I need to run this like a normal user withoud use sudo, gksu, or other superuser maker app...

---

### Post by gmendoza on 2008-07-13
> **wemersonrv said:**
> Hi,

When i try to run the **shutdown** command, the root rights are required (or sudo/su) to run this...

There are a way to configure this command to run in all users without root privileges? I need to run this like a normal user withoud use sudo, gksu, or other superuser maker app...

This would typically be considered very dangerous, especially for multiuser environments.  If you would give a little detail as to what the reasoning behind the request, we could probably make suggestions that fall in line with "best practices".

However, throwing all security concerns to the wind, you could set the SUID bit on the executable, which really just means that any user with execute privileges on the file /sbin/shutdown will execute it with root privileges.

```
$ sudo chmod +s /sbin/shutdown
```

Again... it's not a good practice... and I don't think anyone else would recommend it.

---

### Post by wemersonrv on 2008-07-14
Thanks, it works fine... :lolflag:

	
I know about the risks.

But this does not belong to any computer network, and only in the shutdown that I will do that.

---

### Post by k_grdn on 2008-07-14
Hi,

Better practice to use the sudoers file:

Create a group or users default,

vi /etc/sudoers
%admin ALL = NOPASSWD: /sbin/shutdown


Regards,

k_grdn

---

### Post by Vivaldi Gloria on 2008-07-15
It is important to edit /etc/sudoers using visudo.

**Part 1.** Make changes so that visudo starts with nano rather than vi.

You can pass this part if you want

Edit ~/.bashrc and add this line somewhere:

```
export EDITOR=/usr/bin/nano
```

so that visudo opens with nano rather than vi (i hate vi). Now in terminal:

```
source ~/.bashrc
```

so that the change in .bashrc takes place. All we did upto know is to start visudo with

```
sudo -E visudo
```

in nano rather than vi.


**Part 2.** Changing /etc/sudoers using visudo

Start 

```
sudo -E visudo
```

Under the line "# User alias specification" add a list of users as follows:

```
# User alias specification
User_Alias USERS = user1, user2, user3
```

Write the name of the users sepatated by commas. These users will close the computer without a pswd asked. Write as many users as you want.

Now below the line "# Cmnd alias specification" add a command list as follows:

```
# Cmnd alias specification
Cmnd_Alias SHUTDOWN_CMDS = /sbin/shutdown, /sbin/reboot, /sbin/halt
```

Now below the line "%admin ALL=(ALL) ALL" add the command which will let USERS give SHUTDOWN_CMDS without a pswd:

```
%admin ALL=(ALL) ALL
USERS ALL=(ALL) NOPASSWD: SHUTDOWN_CMDS
```

Now "sudo shutdown", "sudo halt", and "sudo reboot" won't ask passwd. If you want, you can put an alias for halt="sudo halt" etc.

---

### Post by Vivaldi Gloria on 2008-07-15
I just found out about this thread:

[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

Read the second post and the links at the end which give more info on sudoers.

---

