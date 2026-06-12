---
title: "Looking to Hide an open port"
date: 2014-12-16
forum: Security
---

### Post by welefort on 2014-12-16
Running server 14.04,  I have an SSH service open for remote admin,  and using ufw have restricted it to only accept connections from one ip address using the command 

```
sudo ufw allow from x.x.x.x to any port 22
```

What I'd like to do is "hide" the port from scan attempts.  So when a port scan is done on the server it wont show that open port 22.  Is this even possible?

---

### Post by TheFu on 2014-12-16
Either the port is open or it is closed, period.
You could setup "port knocking" which would start the sshd service based on some other "open port" being knocked with a key packet. I've never used port knocking - sorry.

For most people the best solution to securing ssh is:
* have the edge router listen on a non-default port for ssh and perform port-translation to the server port 22.
* install fail2ban or deny hosts to block all brute force attacks. Be certain to test / validate it is working for your setup.
* only use key-based authentication, NEVER, EVER, EVER, passwords

Even if you only want 1 IP able to ssh in, doing the other things listed would still be smart.

---

### Post by kevdog on 2014-12-16
What TheFu said is true.  I use a port knocker -- specifically the fwknop implementation.  It's pretty easy to use however it does break from time to time (not usually).  I wrote a tutorial how to set up fwknop which is in the forums. [http://ubuntuforums.org/showthread.php?t=1926699](http://ubuntuforums.org/showthread.php?t=1926699).  It seems intimidating reading the instructions, but one you get it running its pretty simple.  

Other tips
Move to different higher port
Filter incoming packets to port 22 if possible restricting the source
Alter the /etc/sshd_config file to allow only certain users.  You could also limit groups if you wanted it.

---

### Post by Penguin360 on 2014-12-18
I don't think there is a way to hide an open port. Sooner or later, the open port will be found. Besides, changing a standard port to a non-standard port only tells hackers that you are trying to hide something valuable.

---

### Post by kpatz on 2014-12-18
> **welefort said:**
> Running server 14.04,  I have an SSH service open for remote admin,  and using ufw have restricted it to only accept connections from one ip address using the command 

```
sudo ufw allow from x.x.x.x to any port 22
```

What I'd like to do is "hide" the port from scan attempts.  So when a port scan is done on the server it wont show that open port 22.  Is this even possible?

You could do this:

```

sudo ufw allow in from x.x.x.x to any port 22
sudo ufw reject in from any to any port 22

```

The first rule allows the one IP that you want to give access in to port 22.  The 2nd rule rejects everyone else.  To any IP other than the one allowed, the port will appear as closed.

If you change "reject" to "deny", the port will be "hidden", as in it won't reply at all to a request.  It'll just drop it.

Other things to do to make it more secure have been suggested already, such as using a different port, fail2ban, use only key authentication and not passwords, etc.  Connection rate limiting is available in ufw as well.  Read the man pages on it to learn more.  But with the firewall rules above, your server will be hard to "find" for anyone other than the one IP you let in.

---

