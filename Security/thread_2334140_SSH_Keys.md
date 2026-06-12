---
title: "SSH Keys"
date: 2016-08-16
forum: Security
---

### Post by themasteredpanda on 2016-08-16
Hello,

So I have recently slapped Ubuntu 16.04 on a node that I will be using to hosting minecraft servers off of. Before I put anything on that server, such as all the custom stuff I have coded, I want to make sure it is near impossible to break in from the backend and screw a ton of stuff up. What I am currently doing is attempting to setup a SSH key pair that is required then logging into the backend of the node so that the user will need the ssh key as well as the password to successfully get into the backend without any problems, something I am currently having problems doing. I have got as far as creating the keys and authorizing the public key correctly then editing the file perms so ~/.ssh is 700 and ~/.ssh/authorized_keys is 400 . The part I am stuck on is getting the server to accept the key rather than refuse it, whenever I attempt to log in with the ssh client having the ssh key feature enabled and setup it gives me this message when I log in.
[IMG]https://gyazo.com/73b3f948d9fc8d53dbc0de645768082e.png[/IMG]
I've been attempting to resolve this for quite some time now and now I have more or less given up and is desperate for a experienced mind to aid me in what I am doing wrong.

Thanks,
Panda. :)

---

### Post by TheFu on 2016-08-17
Ubuntu doesn't use root logins and it is my understanding that discussing using root in this way is against forum policy.

As far as ssh keys - use **ssh-keygen** on the client, then use **ssh-copy-id** from the client to the server to push the public key over. That little program sets the directory and file permissions as needed. It has been over a decade since I've done it manually.

As far as securing ssh, there are many ways to do it and many answers in these forums. Lock down access to ssh so that only those IPs which should access it can.  Block random failed attempts from all IPs, but especially from those outside your normal client access points. 

Allowing remote access to root is a bad idea in most Unix systems, including Ubuntu. There are times when I do it - for network system backups from trusted static internal IPs and for certain system monitoring from other trusted, static, internal IPs. I do not allow remote root access to any internet IPs.

---

### Post by QIII on 2016-08-17
Discussing how to log in to a GUI as root is what we don't want.  :)

I will go so far as to say:  Remote login as root to machines exposed to the internet?  **Don't!**

Set up all of your configurations to disallow root login over SSH.  Also disable password logins.  Use keys only.  Port knocking is not such a bad idea.

---

### Post by themasteredpanda on 2016-08-17
> **QIII said:**
> Discussing how to log in to a GUI as root is what we don't want.  :)

I will go so far as to say:  Remote login as root to machines exposed to the internet?  **Don't!**

Set up all of your configurations to disallow root login over SSH.  Also disable password logins.  Use keys only.  Port knocking is not such a bad idea.

Keys? You mind elaborating more? Do you mean ssh keys?

---

### Post by themasteredpanda on 2016-08-17
I'm trying to do [this]("http://security.stackexchange.com/questions/17931/possible-to-use-both-private-key-and-password-authentication-for-ssh-login") , require a private key and a password when logging into the root user. That is what I am trying to do.

---

