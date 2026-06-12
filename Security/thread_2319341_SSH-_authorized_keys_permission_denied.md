---
title: "SSH- authorized_keys: permission denied"
date: 2016-04-03
forum: Security
---

### Post by calveym on 2016-04-03
Hello everyone!

I have recently installed ubuntu for the first time, and it took me a couple of installs to get everything to work properly. At the moment, I am trying to set up ssh keys to connect to my ubuntu server, hosted remotely. I had it working at one point, but then while installing a tarball screwed up my OS so had to reset everything. After doing this, I have been unable to get ssh to work, and I have tried changing permissions to the various files, and even deleting and creating the ssh files myself (other than the keys themselves that is).

The exact error code I get when doing
```
ssh-copy-id [username]@[ip]
```
is:
```
bash: line 2: /ssh/authorized_keys: Permission denied
```

I have tried changing permissions of authorized_keys to 0600 and 0700, but I get the same error. Before getting this error, the codes would appear to copy, but I was still asked for a password when trying to do:
```
ssh [username]@[ip]
```


Any help would be greatly appreciated, I'm just getting to grips with all things linux, and it is so much fun! It can be infuriating when things don't work though.

Thanks.

Edit: I know it is not a major issue, but without this writing scripts for backing up files etc to my server becomes much harder.

---

### Post by SeijiSensei on 2016-04-03
Make sure you are in fact the owner of the /home/username/.ssh directory and all files in it.
```

cd /home/username
sudo chown -R username:username .ssh 

```
You'll need sudo to fix any ownership errors.

---

### Post by calveym on 2016-04-03
Hi, thanks for the advice, it has gotten further now! I ended up doing your command on the server as well.  It says the key is copied, but whenever I try to login via ssh it still asks for my password. I could have screwed up some setting in sshd_config :(. I don't really know what else to try, I've tried solutions in many similar threads on here and stack overflow. Any further ideas? Thanks a lot for the help anyway!

---

### Post by SeijiSensei on 2016-04-03
Try using "ssh -v" to connect so you'll get a verbose presentation of the connection attempt. Also take a look at /var/log/syslog on the server to see what errors it throws, if any.

Another thing to check is whether /etc/ssh/ssh_config has GSSAPIAuthentication enabled.  That can lead to long hang times, though usually a connection will eventually be made.  Check that file and remove any hash mark ("#") before the line
```
GSSAPIAuthentication no
```.

---

### Post by steeldriver on 2016-04-03
Does the error really refer to

```

[COLOR=#ff0000]/ssh[/COLOR]/authorized_keys

```

If so, check the AuthorizedKeysFile entry in the remote server's /etc/ssh/sshd_config file

---

