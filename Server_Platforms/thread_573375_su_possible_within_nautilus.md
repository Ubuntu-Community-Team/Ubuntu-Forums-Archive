---
title: "su possible within nautilus?"
date: 2007-10-11
forum: Server Platforms
---

### Post by itpaul on 2007-10-11
I have recently decided to beef up security on my remote server. One of the measures I took was to disable root login with ssh. I must now log in as paul and then 'su root'.

Sadly I can no longer browse my remote system via nautilus because I cannot find a way to get nautilus to 'su root'. I am stuck as user paul who doesn't have permission to do or even see stuff.

I have been hunting for the solution for this for 2 days now! Can it be done?

---

### Post by James79 on 2007-10-11
Try starting nautilus as root:

```
sudo nautilus
```

---

### Post by tszanon on 2007-10-11
In fact, graphical applications (like Nautilus) should be run with gksu (or gksudo, just the same) instead of sudo. I don't remember why, but that's true. :)

So:
1. press ALT+F2
2. type ```
gksudo nautilus
```

---

### Post by itpaul on 2007-10-11
Nautilus is not installed on my remote server. running 'gksu nautilus' will do nothing there. if i run it on my local machine i get root access to my local machine. i want root access on remote machine.

the problem is that i want to run nautilus locally and 'connect to server...' as paul and then su to root on the remote machine.

i cannot just 'connect to server...' as root as this is disabled for security.

---

### Post by cdenley on 2007-10-11
I think nautilus uses scp or sftp to transfer files, assuming your connecting to an ssh server, which means you can only access your files as a user allowed by the ssh server.  If you want to access files remotely as root, you need to enable root access and set the root password.

---

### Post by itpaul on 2007-10-11
i have disabled root login intentionally for security. i do not wish to re-enable it. i now log in (via ssh) as [email]paul@remoteserver.com[/email]. once logged in, i 'su root' to become the root user.

i want to do this with nautilus (or perhaps another gui).

---

### Post by cdenley on 2007-10-11
Nautilus itself can't sudo. Sudo is for running commands on the machine which the command is run on. Sudo can't be used for remote file access, only local shell access. Nautilus can't get root access because you disabled it, as you should have. You can either install a gui on your server, enable root access, or use the command line.

---

### Post by James79 on 2007-10-11
Or perhaps give your user paul the access that it needs?

---

### Post by itpaul on 2007-10-11
I think I'll enable root login again then. Thankyou.

---

### Post by Fireman_DJ on 2007-10-13
```
sudo sh
```
Then type the user password and you have root.

---

### Post by p_quarles on 2007-10-14
The way to do this without enabling root login is to set up an sshfs network share. 

Quick instructions (let me know if you need more details).
On the remote machine:
```
sudo apt-get install sshfs
sudo chmod +x /usr/bin/fusermount   # try /bin/fusermount if that doesn't work
sudo modprobe fuse
sudo sh -c "echo 'fuse' >> /etc/modules"
sudo addgroup *username* fuse
```
Now make a mount directory. I used:
```
sudo mkdir /media/*servername*
```
You'll need to log out and back in order for the Fuse permissions to take effect. 

Finally:
```
sshfs -o uid=*1000*,gid=*1000* *username*@*remote-ip*:/path-to-folder /media/*servername*
```
1000 is the default uid/gid in Ubuntu, but change that as needed. 

You will now have the remote folder (or the entire drive, if you chose that) mounted on your local system as a browsable drive.

---

