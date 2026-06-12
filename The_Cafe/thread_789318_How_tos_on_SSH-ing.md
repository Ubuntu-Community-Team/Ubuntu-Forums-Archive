---
title: "How tos on SSH-ing"
date: 2008-05-10
forum: The Cafe
---

### Post by blithen on 2008-05-10
Does anyone know any good ones?
And if you can connect to windows from linux and vice versa?

---

### Post by Lux Perpetua on 2008-05-10
To connect to a remote computer via ssh, the remote computer needs an SSH server running, and your computer needs an SSH client installed. If these requirements are met, then it's as simple as running "ssh <name_of_server>" in a terminal and following the prompts. (The SSH client in Ubuntu is provided by the package openssh-client.) 

I've never heard of SSHing into a computer running Windows, but it can probably be done by installing Cygwin first. There are other options, like terminal services (if I recall correctly), for connecting to a remote computer that's running Windows, but I don't have much experience with that. 

Connecting *from* a Windows computer to a Unix box via SSH is easier. There are free Windows SSH clients. I seem to recall using something called "putty" when I was still using Windows 2000. 

More information on SSH: [http://www.openssh.com/](http://www.openssh.com/)

---

### Post by Joeb454 on 2008-05-10
You can but you need to install some sort of SSH Server/Client for Windows to be able to do it. Putty is pretty good, though I'm not sure about an SSH Server

---

### Post by blithen on 2008-05-10
Nevermind. and I got it working Windows - Linux.

---

### Post by Matt Yun on 2008-05-10
Here are some links for the SSH software mentioned above:

[OpenSSH for Windows]("http://sshwindows.sourceforge.net/"):  SSH server and client for Windows

[PuTTY Portable]("http://portableapps.com/apps/internet/putty_portable"):  portable PuTTY, an SSH client for Windows, that you can run from a USB stick.

[WinSCP Portable]("http://portableapps.com/apps/internet/winscp_portable"):  portable WinSCP, an SCP/SFTP client for Windows, that you can run from a USB stick.

---

