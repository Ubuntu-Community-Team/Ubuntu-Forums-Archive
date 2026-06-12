---
title: "Can't sudo when x forwarding"
date: 2011-07-13
forum: Server Platforms
---

### Post by ginge6000 on 2011-07-13
Hi,

I'm trying to set up my mythtv backend on a headless box.  The many tutorials out there tell you to run mythtv-setup from a machine with a display by x forwarding through ssh.  
```
ssh -X username@ipaddress /usr/bin/mythtv-setup
```
The x forwarding works fine except that the first part of the mythtv-setup requires you to stop the mythtv-backend process which you have to do as root.  It brings up a box asking for your password (much like is would if you just typed sudo xxxxxxx in the terminal) but it won't accept the password.  Looking in the auth log it seems that it can't authenticate
```
Jul 13 11:21:08 server su[21869]: pam_unix(su:auth): authentication failure; logname= uid=1000 euid=0 tty=/dev/pts/1 ruser=administrator rhost=  user=root
Jul 13 11:21:10 server su[21869]: pam_authenticate: Authentication failure
Jul 13 11:21:10 server su[21869]: FAILED su for root by administrator
Jul 13 11:21:10 server su[21869]: - /dev/pts/1 administrator:root
```
Now I know that my account (administrator) can have root privileges because I can sudo xxxx to my hearts content via ssh in the terminal, but it seems to not work when it's being requested from a forwarded X window.....  Any ideas???

---

### Post by volkswagner on 2011-07-13
Mythtv-setup need root priv to run.  So the command should be run with sudo to start.

Please confirm the statement is true "can't sudo while X-forward".

Try opening the ssh -X with no trailing command.

```
ssh -X username@ipaddress
```

The try a simple command like:

```
sudo nano test.txt
```

Create some content in the file and save.  If it works, sudo is working while in -X forward.

Then try:

```
sudo mythtv-setup
```

---

### Post by ginge6000 on 2011-07-13
Thanks for that.  I'd read somewhere that you shouldn't do the setup as sudo as it can create odd permissions on things so I hadn't tried that!  It's all working just fine now!

---

