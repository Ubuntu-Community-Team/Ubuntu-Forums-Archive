---
title: "SSH Connection Refused after disabling Password Authentication"
date: 2016-02-27
forum: Server Platforms
---

### Post by Alexah_Woods on 2016-02-27
Hello all! I've just finished implementing SSH key authentication on my Ubuntu server, and as such I want to disable Password Authentication.

The issue is, when I go into my sshd_config file and set "#PasswordAuthentication Yes" to "PasswordAuthentication No", the server refuses all SSH connections. If I add back the "#", I can connect again. Is there any way I can fix this? I'm not sure why this would be causing an issue...

OS: Ubuntu Server 15.10 64-bit

---

### Post by nerdtron on 2016-02-28
So you already set-up your keys for passwordless authentication? 
Then set "PasswordAuthentication no", then restart the sshd service.
Now when you connect try to use verbose mode to see the errors of ssh connection, post the output here. 
```
 ssh -v username@ip.address 
```

Also are you connecting with the correct username and keys? Try to explicitly define your keys using the -i option.
```
 [user@linux ~]$ ssh -v -i /home/user/.ssh/id_rsa.key user@ip.server.address 
```

If it still fails, the post the output of you sshd config (without the extra comments):
```
 grep  ^[^#] /etc/ssh/sshd_config 
```

---

### Post by darkod on 2016-02-28
After you set up the keys, do not disable it immediately. First try to log in using the keys. With keys set up the ssh connection tries to use them automatically, and if it lets you in without asking for password, it works. If it is still asking you for a password then it doesn't use the key and disabling password authentication will lock you out.

Usually the most common problem when setting up key auth is the permission of the .ssh folder in the users home directory and the authorized_keys file. If you set them up by hand (like I have done in many cases), the permissions are not correct because creating the files gives them generic permissions and ssh is very strict.

Using sudo set 700 on the folder and 600 on the file. For example (replace your username with the correct one):
```
sudo chmod 700 /home/username/.ssh
sudo chmod 600 /home/username/.ssh/authorized_keys
```

Then log out and try again to check if the key is used.

If you are connecting from linux client there is a very good command you can use which will set up everything automatically including permissions. It's:
```
ssh-copy-id username@server
```

It asks for the password to authenticate you and sets up the key of the user you are running it from, to the user you use in the command. Note that the usernames don't need to match on both machines of course.

From a windows client I'm not aware of any such command so I use putty for connections and set up keys manually making sure the permissions are as above.

---

