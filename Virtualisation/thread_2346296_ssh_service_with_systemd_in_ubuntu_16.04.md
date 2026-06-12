---
title: "ssh service with systemd in ubuntu 16.04"
date: 2016-12-13
forum: Virtualisation
---

### Post by sonuaffriya on 2016-12-13
HI All,
I am using ubuntu 16.04 on my virtual machine.

The ssh service is enabled and running on ubuntu 16.04.

In ssh.service file:
[Install]
WantedBy=multi-user.target

so there should be a symlink in multi.user.target.wants/ directory. But it is not there.
Is there any another way(except systemctl enable) to enable a service.?? As per my understanding, if a service file is enabled then it should have symbolic link in <target>.wants/ directory.
 
If a try to run "systemctl enable ssh.service" then it prints some sysVinit related things.
If you check the ssh.service file, then you will see that there are nothing mentioned regarding "sysVinit" in service file.
Why it is printing sysVinit related logs??

COMMAND PROMPT SNIPPET for above issues:

```
sonu@sonu-VirtualBox:~$ systemctl status ssh.service
&#9679; ssh.service - OpenBSD Secure Shell server
   Loaded: loaded (/lib/systemd/system/ssh.service; **enabled**; vendor preset: enabled)
   Active: active (running) since Tue 2016-12-13 20:47:40 IST; 51min ago
  Process: 1041 ExecReload=/bin/kill -HUP $MAINPID (code=exited, status=0/SUCCESS)
 Main PID: 794 (sshd)
   CGroup: /system.slice/ssh.service
           &#9492;&#9472;794 /usr/sbin/sshd -D

Dec 13 20:47:41 sonu-VirtualBox systemd[1]: Reloading OpenBSD Secure Shell server.
Dec 13 20:47:41 sonu-VirtualBox sshd[794]: Received SIGHUP; restarting.
Dec 13 20:47:41 sonu-VirtualBox systemd[1]: Reloaded OpenBSD Secure Shell server.
Dec 13 20:47:41 sonu-VirtualBox sshd[794]: Server listening on 0.0.0.0 port 22.
Dec 13 20:47:41 sonu-VirtualBox sshd[794]: Server listening on :: port 22.
Dec 13 20:47:41 sonu-VirtualBox systemd[1]: Reloading OpenBSD Secure Shell server.
Dec 13 20:47:41 sonu-VirtualBox sshd[794]: Received SIGHUP; restarting.
Dec 13 20:47:41 sonu-VirtualBox systemd[1]: Reloaded OpenBSD Secure Shell server.
Dec 13 20:47:41 sonu-VirtualBox sshd[794]: Server listening on 0.0.0.0 port 22.
Dec 13 20:47:41 sonu-VirtualBox sshd[794]: Server listening on :: port 22.
sonu@sonu-VirtualBox:~$ systemctl cat ssh.service
# /lib/systemd/system/ssh.service
[Unit]
Description=OpenBSD Secure Shell server
After=network.target auditd.service
ConditionPathExists=!/etc/ssh/sshd_not_to_be_run

[Service]
EnvironmentFile=-/etc/default/ssh
ExecStart=/usr/sbin/sshd -D $SSHD_OPTS
ExecReload=/bin/kill -HUP $MAINPID
KillMode=process
Restart=on-failure
RestartPreventExitStatus=255
Type=notify

[Install]
WantedBy=multi-user.target
Alias=sshd.service
sonu@sonu-VirtualBox:~$ **ls /lib/systemd/system/multi-user.target.wants/**
dbus.service  plymouth-quit.service       systemd-ask-password-wall.path  systemd-update-utmp-runlevel.service
getty.target  plymouth-quit-wait.service  systemd-logind.service          systemd-user-sessions.service
sonu@sonu-VirtualBox:~$
sonu@sonu-VirtualBox:~$ sudo systemctl enable ssh.service
[sudo] password for sonu: 
Synchronizing state of ssh.service with **SysV init** with /lib/systemd/systemd-sysv-install...
Executing /lib/systemd/systemd-sysv-install enable ssh
sonu@sonu-VirtualBox:~$
```

---

### Post by howefield on 2016-12-13
Thread moved to the "*Virtualisation*" forum.

---

### Post by sonuaffriya on 2016-12-14
same behavior is with ubuntu 16.04...so i guess this issue is not related to visualization...its related to systemd..

---

### Post by ynota on 2017-01-06
so you are trying to enable the ssh.service that is all ready loaded and working?

---

### Post by KillerKelvUK on 2017-01-07
Isn't the service name ssh_**d**_.service...the unit ssh.service is a dependency but isn't what I use to manage the SSH server on my servers?

---

### Post by Doug S on 2017-01-07
> **KillerKelvUK said:**
> Isn't the service name ssh_**d**_.service...the unit ssh.service is a dependency but isn't what I use to manage the SSH server on my servers?well, both work, but the sshd one is linked to the real name of ssh.```
$ ls -l /etc/systemd/system/ssh*
lrwxrwxrwx 1 root root 31 Jan 30  2016 /etc/systemd/system/sshd.service -> /lib/systemd/system/ssh.service
```

---

### Post by KillerKelvUK on 2017-01-07
Okay, thanks for the education...not going to ask why that would be but I'm sure there is some logic to aliasing  the name.  FWIW I've just replicated the disable/enable process on my 16.04 host and I the symlink is removed/added as per your expectations...I also get the reference to the SysV init.

I knew I'd read something about this prev when getting to know systemd better, have a look here [https://wiki.ubuntu.com/SystemdForUpstartUsers#A.2Fetc.2Fdefault_files_which_enable.2Fdisable_jobs](https://wiki.ubuntu.com/SystemdForUpstartUsers#A.2Fetc.2Fdefault_files_which_enable.2Fdisable_jobs).  From this I taking it that update-rc.d may be your answer?

---

