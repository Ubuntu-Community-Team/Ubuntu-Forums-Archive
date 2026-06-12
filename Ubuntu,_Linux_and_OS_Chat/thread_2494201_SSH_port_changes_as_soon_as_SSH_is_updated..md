---
title: "SSH port changes as soon as SSH is updated."
date: 2024-01-08
forum: Ubuntu, Linux and OS Chat
---

### Post by sblantipodi on 2024-01-08
hello,
every time I update SSH with an apt upgrade,
my SSH port is rolled back to 22.

I use a custom port and in ubuntu you must modifiy the 
[COLOR=#ADBAC7][FONT=-apple-system]/lib/systemd/system/ssh.socket[/FONT][/COLOR]
file to use a custom port.

This works well but every time SSH is updated, apt restores that file to port 22.

Is there a way to change the SSH port forever?

---

### Post by SeijiSensei on 2024-01-08
For the server, you should modify /etc/ssh/sshd_config and change its "Ports" designation.

For the client, apply the same change to /etc/ssh/ssh_config or use "ssh -p 12345 server_name".

---

### Post by sblantipodi on 2024-01-08
> **SeijiSensei said:**
> For the server, you should modify /etc/ssh/sshd_config and change its "Ports" designation.

that file only does not change the SSH port in Ubuntu 23.10

---

### Post by SeijiSensei on 2024-01-08
As I said, you also need to change /etc/ssh/ssh_config if you want the client to default to a different port.

These have been the standard configuration files for ssh for years now. I doubt it doesn't work in 23.10, but I never use anything other than LTS versions.

---

### Post by sblantipodi on 2024-01-08
> **SeijiSensei said:**
> As I said, you also need to change /etc/ssh/ssh_config if you want the client to default to a different port.

These have been the standard configuration files for ssh for years now. I doubt it doesn't work in 23.10, but I never use anything other than LTS versions.

that's what I have done but as said to change the SSH port on 23.10 you need to edit both 
/etc/ssh/ssh_config
and 
/lib/systemd/system/ssh.socket

but 
/lib/systemd/system/ssh.socket

is automatically changed by apt upgrade every time there is an update.

---

### Post by #&amp;thj^% on 2024-01-08
> **sblantipodi said:**
> that file only does not change the SSH port in Ubuntu 23.10

SSHd now uses socket-based activation (Ubuntu 22.10 and later)
Some info that might help: [https://discourse.ubuntu.com/t/sshd-now-uses-socket-based-activation-ubuntu-22-10-and-later/30189](https://discourse.ubuntu.com/t/sshd-now-uses-socket-based-activation-ubuntu-22-10-and-later/30189)

---

### Post by SeijiSensei on 2024-01-08
After reading that document, I intend to run
```

sudo rm /etc/systemd/system/ssh.service.d/00-socket.conf
sudo systemctl disable --now ssh.socket
sudp systemctl enable --now ssh.service
sudo systemctl daemon-reload
sudo systemctl restart ssh

```
on every future installation of Ubuntu.

All of this is to save a few megabytes of storage? Change the method of configuring sshd that we've all used for decades for that? Who are these developers? Do they talk to real sysadmins in the world?

---

### Post by sblantipodi on 2024-01-08
> **SeijiSensei said:**
> After reading that document, I intend to run
```

sudo systemctl disable --now ssh.socket
sudo systemctl enable --now ssh.service

```
on every future installation of Ubuntu.

does this two commands supposed to fix my issue?
thanks you very much for the answer...

the link above does not open here :)

---

### Post by SeijiSensei on 2024-01-08
Follow the more extensive set of commands I just posted.

---

### Post by sblantipodi on 2024-01-08
ok thanks :)

---

