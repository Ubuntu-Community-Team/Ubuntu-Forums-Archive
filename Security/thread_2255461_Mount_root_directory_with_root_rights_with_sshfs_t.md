---
title: "Mount root directory with root rights with sshfs to server without root login"
date: 2014-12-05
forum: Security
---

### Post by Matyy on 2014-12-05
Hi everybody,

I have two questions - first how I can do what I want to do and second whether it's reasonable to do it at all. That's why I put it here into security.

*Servers*: 
Ubuntu 14.04.1 LTS, one "real" and a few virtual machines.

*Client*: 
Ubuntu 14.04.1 LTS

*Scenario*: 
I want to mount the root file system from the servers with sshfs. **sshfs adminuser@server** works flawlessly. It's also in my fstab. No keys used yet, I am authenticating by typing my password. Since this user is no root but a sudoer, mounting the file system gives me the user's right, not root rights. So I have RW access to ~ but to nothing else. Login with the root account is disabled in Ubuntu. Of course I can create a root password and than mount the share with **sshfs root@server**.
The connection will only happen within our local network or via VPN access.

[I]Question:
[/I]Shall I create a root login on the servers? Is there another way?

[I]Option 1: 
[/I]I give him a real complicated password and make the authentication by keys. I don't really want to create a root password. I try to avoid it. Just to keep the system tighter. 

[I]Option 2:
[/I]I don't mount as root. Than I can't quickly edit for example the configs of ejabberd or apache2 on my client in Geany but have to use an ssh terminal. 
For work like copying websites or other files between the servers, I give the user write access by puting him in the right groups.

[I]Option 3:
[/I]Do you have any?

Thanks,

Matthias

---

### Post by mikewhatever on 2014-12-05
You can you **sudo -i** to become root in Ubuntu, edit stuff, and tipe exit to become a regular user again.

---

### Post by Matyy on 2014-12-05
I don't need root access on the client. When I ssh onto the server that's what I do. Or ist there a way that let's me pass sudo along with my sshfs authentication? 

Though I guess it doesn't really matter. As long as I have any credential that grants me root access will be the same security issue. Losing a sudoers password is as bad as a root account's one. So I guess it's best if I activate it while I need it.

---

