---
title: "sshd issues"
date: 2006-08-09
forum: Server Platforms
---

### Post by kb3hkg on 2006-08-09
I am running an ssh server on my machine. It had been running fine but just recently stopped. Now whenever I try to connect to it I get nothing.

Not sure what the problem is but help would be appreciated. I did try reinstalling the Openssh server.

---

### Post by kebes on 2006-08-09
Is the ssh server running? Doing "pgrep ssh -l" should list some "sshd" entries. If not, then start it with "/etc/init.d/ssh start".

If it is already running, try restarting it with "/etc/init.d/ssh restart".

If it's definately running, then is it not responding at every level? For instance, if you try to log in from a remote machine, I guess it doesn't respond. What about a local machine? If you're at a terminal already logged into that machine, and go "ssh localhost" can you connect? If so, then something about your remote connections (firewall?) is wrong. If you can't connect locally then your sshd server is really not working. What error message do you get when trying to connecte locally or remotely?

Maybe you could "grep" through some of your "/var/log" files and look for any error messages from "sshd" ? That might help.

---

### Post by kb3hkg on 2006-08-09
when restarting the server I get the following:

 * Restarting OpenBSD Secure Shell server...                                    Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key
start-stop-daemon: warning: failed to kill 9877: Operation not permitted
Could not load host key: /etc/ssh/ssh_host_rsa_key
Could not load host key: /etc/ssh/ssh_host_dsa_key


When trying ssh localhost I get this:

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
98:1c:42:1e:38:24:54:6a:60:cc:e6:4b:bf:7d:8f:1d.
Please contact your system administrator.
Add correct host key in /home/eric/.ssh/known_hosts to get rid of this message.
Offending key in /home/eric/.ssh/known_hosts:2
RSA host key for localhost has changed and you have requested strict checking.
Host key verification failed.

any ideas?

---

### Post by kebes on 2006-08-09
Well at least some of those errors are probably coming from the fact that you reinstalled OpenSSH. That means that your server's key has changed. The key is used to identify the server, to make sure that it is authentic. Most SSH clients, when they see that a server key has changed, will refuse to connect, because a changed key usually means someone has hijacked/hacked the server.

Of course in your case you know that you have simply reinstalled the server, so you want to override this. So go edit this file:
/home/eric/.ssh/known_hosts

And remove (just erase) any of the lines pointing to your server. These will include any with "localhost" or "127.0.0.1" ... and also any that use the domain-name or the IP-address of your server. Once these lines are gone, your SSH client may connect just fine.

It's also possible that your other attempts to connect to the server where being similarly blocked: because your server key had changed. You should follow a similar procedure on those other machines to re-enable connection.

So do this and then try connecting at the localhost level again. If you can connect at the local level "ssh localhost" then at least the server is working. Then you can make sure it's working from remote logins.

If it's still not working (even at the local level), then it's possible that your installation (or reinstallation) failed to generate a valid key (hence the errors during the server restart). Check if you have this file:
/etc/ssh/ssh_host_rsa_key
The file should look like this (only root can read it):
```

-----BEGIN RSA PRIVATE KEY-----
M9907ljdfasjLiuf9klj8jlK <... lots of characters ...>
-----END RSA PRIVATE KEY-----

```

Normally a new key is created during the installation of OpenSSH. If the key is missing you'll need to generate a new one. See here for some info:
[http://www.jigsawboys.com/2006/05/09/generate-sshd-host-key/](http://www.jigsawboys.com/2006/05/09/generate-sshd-host-key/)
Essentially you use "ssh-keygen" to create a valid key.


See if any of that fixes it.

---

### Post by kb3hkg on 2006-08-14
I have the /etc/ssh key. But in the .ssh directory in home I see nothing even close to localhost or 127.0.0.1 all I see is a big mess of characters that do look similar to host keys.

---

### Post by stormblue on 2006-08-14
If the only SSH server you connect to is the one you're having problems with you can delete everything in the file.

---

### Post by kb3hkg on 2006-08-14
localhost now works fine. But I have to connect from work, where unfortunately windows is required. I use putty and winscp to do this. How do I clear their keys?

---

### Post by Iowan on 2006-08-14
Dunno if this helps:> PuTTY records the host key for each server you connect to, in the Windows Registry. Every time you connect to a server, it checks that the host key presented by the server is the same host key as it was the last time you connected. If it is not, you will see a warning, and you will have the chance to abandon your connection before you type any private information (such as a password) into it.

---

### Post by lvanderree on 2006-08-14
The error you described above about restarting ssh looks like a permission problem.

you probably typed 
```
/etc/init.d/ssh restart
```
while not being the root user!

adding sudo to the line should solve your problem.
```
sudo /etc/init.d/ssh restart
```
then your password is asked again, to confirm that you have administrator rights.

I hope this solves your first problem...

---

### Post by kb3hkg on 2006-08-16
Looks like something changed iptables quite a bit, possibly firestarter. Is there any easy way of telling if it is blocking the ssh server?

---

### Post by chonger on 2006-08-16
If you can telnet to port 22 (and get a connection) locally, but cannot do that from an exernal source, then it is possibly a firewall problem.

---

### Post by kb3hkg on 2006-08-16
that looks like it may be the problem. Any help as to how I can fix it?

---

### Post by chonger on 2006-08-16
I think you'll need to mess around with firestarter. I can't help you there, because I'm not familiar with firestarter configuration.

I will not be surprised if the default firestarter configuration blocks all incoming connections (from the Internet). So you'll need to learn how to configure firestarter and find out just what it is doing.

---

### Post by stormblue on 2006-08-16
Can you connect locally from the network. IE From inside your network? can you ssh 192.168.x.x ?

Also, firestarter is just a GUI to interface with netfilters and linux comes with a built in firewall that you can modify via firestarter.

---

### Post by kb3hkg on 2006-08-17
I cannot connect from within my network. And since firestarter doesn't seem to want to let me add any rules how can I edit the firewall to allow 22 to go through?

---

### Post by kb3hkg on 2006-08-17
Nevermind. I was able to get some help with the firewall and now have ssh running just fine. Thank you all for your help.

---

