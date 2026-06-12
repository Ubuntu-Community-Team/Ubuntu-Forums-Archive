---
title: "sudo -i passes on the DISPLAY environment variable"
date: 2019-07-04
forum: Ubuntu, Linux and OS Chat
---

### Post by Skaperen on 2019-07-04
the "[FONT=courier new]sudo -i[/FONT]" command passes on the _DISPLAY_ environment variable, by default.  shouldn't it also pass on these:

```

XDG_CONFIG_DIRS
XDG_CURRENT_DESKTOP
XDG_DATA_DIRS
XDG_GREETER_DATA_DIR
XDG_MENU_PREFIX
XDG_RUNTIME_DIR
XDG_SEAT
XDG_SEAT_PATH
XDG_SESSION_DESKTOP
XDG_SESSION_ID
XDG_SESSION_PATH
XDG_SESSION_TYPE
XDG_VTNR
```

---

### Post by TheFu on 2019-07-05
I'm not seeing that on 16.04 Server that I ssh into.

```
thefu@vpn:~$ env|grep DISPL
thefu@vpn:~$ 
thefu@vpn:~$ sudo -i
root@vpn:~# env|grep DISPL
root@vpn:~# 
```

I am seeing it on a local 16.04 desktop.
```
$ env|grep DIS
HOSTDISPLAY=posc:0
DISPLAY=:0
thefu@posc:/misc$ sudo -i
root@posc:~# env|grep DIS
DISPLAY=:0
```

---

### Post by Skaperen on 2019-07-05
since the server doesn't have DISPLAY set at all, there is nothing for sudo to pass on.

---

### Post by TheFu on 2019-07-05
```
thefu@vpn:~$ env|grep SSH
SSH_CLIENT=172.22.22.13 36614 22
SSH_TTY=/dev/pts/0
SSH_CONNECTION=172.22.22.13 36614 172.22.22.9 22

thefu@vpn:~$ sudo -i
root@vpn:~# env|grep SSH
```

So just DISPLAY?  I suspect there is an explanation ... checking the manpage:
```
     -i, --login
                 Run the shell specified by the target user's password dataâ
                 base entry as a login shell.  This means that login-specific
                 resource files such as .profile or .login will be read by the
                 shell.  If a command is specified, it is passed to the shell
                 for execution via the shell's -c option.  If no command is
                 specified, an interactive shell is executed.  sudo attempts
                 to change to that user's home directory before running the
                 shell.  [B]The command is run with an environment similar to the
                 one a user would receive at log in.[/B]  The Command environment
                 section in the sudoers(5) manual documents how the -i option
                 affects the environment in which a command is run when the
                 sudoers policy is in use.

```
and inside the sudoers manpage:
```
     As a special case, if sudo's -i option (initial login) is specified,
     sudoers will initialize the environment regardless of the value of
     env_reset.  **The DISPLAY, PATH and TERM variables remain unchanged**; HOME,
     MAIL, SHELL, USER, and LOGNAME are set based on the target user.  On AIX
     (and Linux systems without PAM), the contents of /etc/environment are
     also included.  All other environment variables are removed.

```

There you have it.  Documented and working as designed.

---

### Post by Skaperen on 2019-07-05
do you think the SSH variables should be added to the list of what is passed along?

---

