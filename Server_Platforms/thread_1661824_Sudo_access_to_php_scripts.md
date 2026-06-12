---
title: "Sudo access to php scripts"
date: 2011-01-07
forum: Server Platforms
---

### Post by psykro on 2011-01-07
Hi all. I could use some enlightened advice.

I am writing a small PHP app to manage some basic server activities. Something like Webmin but on a much smaller (specific commands) scale.

I want to allow the app to run specific commands using sudo (eg useradd) that require root privileges.

Obviously this needs to be made as secure as possible to prevent someone being able to upload their own php script to run these commands maliciously. (however this topic is not about server security/php script security).

I've found two ways I can make this possible

1) Create user and command aliases in /etc/sudoers and allowing the alias to run specific commands

eg
```

# User alias specification
User_Alias WEB_USER = www-data

# Cmnd alias specification
Cmnd_Alias WEB_CMDS = /usr/sbin/useradd

# User privilege specification
WEB_USER ALL=(ALL) NOPASSWD:NOEXEC: WEB_CMDS

```

2) Specify the sudo user password in the PHP shell_exec function call

eg 

[PHP]
shell_exec("echo $password_for_the_user | sudo -S useradd -p `mkpasswd password` -d /home/bob -m bob");
[/PHP]

The first example (imo) exposes those commands to any php script, which may be less secure. However in the second command I would need to ensure that the $password_for_the_user variable is placed somewhere where it would not be easily read by a possible hacker (placing it in a directory which is not below the web root and setting the right permissions)

Any comments/suggestions on the two above options?

---

