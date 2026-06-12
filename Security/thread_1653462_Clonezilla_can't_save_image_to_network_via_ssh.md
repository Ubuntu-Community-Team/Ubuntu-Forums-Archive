---
title: "Clonezilla: can't save image to network via ssh"
date: 2010-12-26
forum: Security
---

### Post by tranduyhung on 2010-12-26
Hello,

I'm working with Clonezilla to back up my test server, I want to store the image to a partition in our network, for example: my computer.
But it still doesn't work. These are my steps:

[LIST]
[*]I reboot my server with Clonezilla CD.
[*]I choose device-image
[*]I choose ssh_server
[*]I choose my network device with dhcp mode
[*]I provide the IP of my computer and port 22, then my username
[*]I choose the path to my hard drive, like /home/username/backup
[/LIST]

But after I type my password to connect, Clonezilla says "remote host has disconnected. Clonezilla image home directory /home/partimag is not a mountint point! Failed to mount other device as /home/partimag! Are you sure you want to continue?"

I try to connect to my computer from another machine, it works, but I don't know why Clonezilla can't.

What do I do wrong here?

Thank you for your feedback :).

Best regards,
Hung

---

### Post by HermanAB on 2010-12-27
Howdy,

That is probably a network problem and not clonezilla per se.  Try a better quality router.

---

### Post by garsh on 2010-12-31
When I had this problem, it was due to my login shell initialization script (.cshrc for me) producing output.  Make sure yours does not.  See [the OpenSSH FAQ]("http://openssh.org/faq.html#2.9") for details.

Another possibility: is /dev/null writable by everyone on your server?  If not, make it so:```
sudo chmod 777 /dev/null
```

---

### Post by Aquariuscrimea on 2011-03-31
now I have the same problem 

chmod 777 /dev/null - try, it doesn't help.

When i manually doing sshfs - everything going good. But when I am doing with the same options throw Clonezilla - I have the same error that topic starter have.

---

### Post by Aquariuscrimea on 2011-03-31
the problem was becaus I choose Russian language in Clonezilla options!!!

---

