---
title: "/etc/sudoers requiretty option"
date: 2008-04-11
forum: Security Discussions
---

### Post by ekricyote on 2008-04-11
I'm writing a script that uses rsync to synchronize directories over an ssh connection. Since the source directory is on the remote server and is owned by root, my script logs in with key-based authentication and performs an "sudo rsync" remotely.

The problem is whenever the script executes, I get an error

```
sudo: sorry, you must have a tty to run sudo
```

I am tempted to enable the option "Defaults requiretty" in the server's /etc/sudoers file to permit this, but there is a warning in the comments above it:

```
# Disable "ssh hostname sudo <cmd>", because it will show the password in clear.
#         You have to run "ssh -t hostname sudo <cmd>".
```

Is this relevant to the requiretty default option? I've tried adding the -t switch to my rsync script command:

```
$  rsync -ravz -e "ssh **-t** -i $MY_PRIV_KEY" $source $user@$remoteHost:$dest
```

but I get this error:

```
Pseudo-terminal will not be allocated because stdin is not a terminal.
sudo: sorry, you must have a tty to run sudo
```

Both the local and remote system are running CentOS 5. Not Ubuntu (although I do run Gutsy @ home). I'd figure it post it here since they're both Linux and probably have similar approaches in this issue.

This is driving me crazy. Any suggestions?

---

