---
title: "Unprotected private key file"
date: 2009-08-26
forum: Security
---

### Post by PadawanGeek on 2009-08-26
I was trying to change my SSH port, so i changed "Port" in my sshd_conf file. I tried to restart SSH and go this error:

```
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
* Reloading OpenBSD Secure Shell server's configuration sshd    ...done.
```I tried the commands:
```
sudo ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key
```and
```
sudo ssh-keygen -l -f /etc/ssh/ssh_host_dsa_key
```but they did not work, so then I tried deleting /etc/ssh/ssh_host_dsa_key and /etc/ssh/ssh_host_rsa_key, recreating the file by saving a blank file with those names in nano, and then trying ```
sudo ssh-keygen -l -f /etc/ssh/ssh_host_rsa_key
```and
```
sudo ssh-keygen -l -f /etc/ssh/ssh_host_dsa_key
```again.

I restarted my server and now I get two messages saying WARNING: UNPROTECTED PRIVATE KEY FILE! bla bla bla are to open bla bla bla bad permissions: ignore key: /etc/ssh/ssh_host_dsa_key
could not load host key: /etc/ssh/ssh_host_dsa_key

Can someone tell me how to get the keys working again?

Thanks!

---

### Post by PadawanGeek on 2009-08-26
oops, wrong section. Didn't realize i was in this tab. Sorry.

---

### Post by bodhi.zazen on 2009-08-26
I am going to guess the problem is the permissions on the keys.

It helps if you post the exact error message without  the bla bla bla :twisted:

Try permissions of 600 or 400

---

### Post by PadawanGeek on 2009-08-26
Update:

I successfully created new keys using ```
   sudo ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key
``` and ```
   sudo ssh-keygen -t dsa -f /etc/ssh/ssh_host_dsa_key
```.

Now i do not get the error message at startup, but instead when I try to restart SSH with ```
/etc/init.d/ssh reload
```, I get the error: ```
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
```.

Is there an extra step I'm missing? Also when I try to log in via SSH it says ```
Connection closed by [my server's IP]
```

Thanks

---

### Post by bodhi.zazen on 2009-08-27
run these commands and try to start the ssh server again.

```
ssh-keygen -f /etc/ssh/ssh_host_rsa_key -t rsa -N ''[FONT=monospace]
[/FONT]ssh-keygen -f /etc/ssh/ssh_host_dsa_key -t dsa -N ''
```

---

