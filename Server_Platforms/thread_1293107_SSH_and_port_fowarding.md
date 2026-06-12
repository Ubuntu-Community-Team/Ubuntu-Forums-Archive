---
title: "SSH and port fowarding"
date: 2009-10-16
forum: Server Platforms
---

### Post by rockingabe on 2009-10-16
Hi. I am trying to ssh into my server behind a router.  I have set up the router to forward port 22 to the internal ip of the server.  The strange thing is when i try to connect to ssh in to the server, the server responds, asking for the password but when I enter the password it says "Permission denied.  Please try again."  When I try to ssh directly to the server using its internal ip, it works just fine.  I have done this before with an OpenBSD server and never had a problem.  Could the be something in the sshd_config in the default Ubuntu install that is causing the problem?  Any help would be appreciated.

---

### Post by drumbug1 on 2009-10-16
Is it possibly a username difference between your client machine and your server?

I'm assuming you're doing:

```


ssh my.domain.com


```

Try:

```


ssh username@my.domain.com


```

---

### Post by R.Bucky on 2009-10-17
if you are not already, use the internal ip rather than a hostname. also, check PermitRootLogin to correspond to whatever username that you are using. Then, check for the almighty caps lock!

---

### Post by rockingabe on 2009-10-17
Nope, not doing just the hostname.  I am doing ssh user@host. Here is the problem.  I have a server behind a firwall with NAT.  If i try ssh user@hostname or user@ip-address, there is no problem.  I want to be able to ssh into my server from another location.  So I enabled port fowarding on my linksys router to fowatd TCP and UDP from port 22 coming in to port 22 to the servers ip address.

Then, when I attempt to ssh into my server from the OUTSIDE like so, ssh user@external-ip-address, I get a prompt asking for my password but the password doesnt work.  I have tried caps lock and differnt users and no luck at alll.  Any ideas?

---

### Post by drumbug1 on 2009-10-17
> **rockingabe said:**
> Nope, not doing just the hostname.  I am doing ssh user@host. Here is the problem.  I have a server behind a firwall with NAT.  If i try ssh user@hostname or user@ip-address, there is no problem.  I want to be able to ssh into my server from another location.  So I enabled port fowarding on my linksys router to fowatd TCP and UDP from port 22 coming in to port 22 to the servers ip address.

Then, when I attempt to ssh into my server from the OUTSIDE like so, ssh user@external-ip-address, I get a prompt asking for my password but the password doesnt work.  I have tried caps lock and differnt users and no luck at alll.  Any ideas?

rockingabe - it really sounds like you're doing everything right....  I'm a bit stumped.  There's got to be something simple/silly that's messing this up.  Is it possible to power down the server behind your linksys long enough to see if a connection attempt from the outside still presents you with a password prompt?  Assuming everything's setup correctly you should *not* be prompted for a password (because your server would be off!) - if you are:  then some other machine is accepting your connection on port 22.

If you get even more desperate you could always try removing and re-installing openssh-server like this:

```

sudo dpkg -P openssh-server

```

...then reinstalling it:

```

sudo apt-get install openssh-server

```

That should remove all of the config files and re-create the necessary keys.

---

### Post by Lars Noodén on 2009-10-18
> **rockingabe said:**
> Nope, not doing just the hostname.  I am doing ssh user@host. Here is the problem.  I have a server behind a firwall with NAT.  If i try ssh user@hostname or user@ip-address, there is no problem.  I want to be able to ssh into my server from another location.  So I enabled port fowarding on my linksys router to fowatd TCP and UDP from port 22 coming in to port 22 to the servers ip address.

Then, when I attempt to ssh into my server from the OUTSIDE like so, ssh user@external-ip-address, I get a prompt asking for my password but the password doesnt work.  I have tried caps lock and differnt users and no luck at alll.  Any ideas?

Double check from the outside to be sure that you are connecting to the machine you think you are connecting to.  

Use [ssh-keyscan](http://manpages.ubuntu.com/manpages/jaunty/en/man1/ssh-keyscan.1.html) and [ssh-keygen](http://manpages.ubuntu.com/manpages/jaunty/en/man1/ssh-keygen.1.html) for that.  Do that from outside.  If the key matches, then you are hitting the right machine. 

```

# it appears that a bug or misfeature in these prevent 
# a normal redirect from stdin
$ ssh-keyscan *xx.yy.zz.aa*  > /tmp/x^C
$ ssh-keygen -lf /tmp/x
29:da:5e:25:5e:91:1e:45:f8:9b:3d:a5:37:84:ad:4e  *xx.yy.zz.aa* (RSA)

```

If the key does not match, you are not hitting the right machine.  Then to skip that, during the debugging.  Put something unique in /etc/issue.net and uncomment the corresponding line in sshd_config to turn the banner on:

[INDENT][FONT="Courier New"]Banner /etc/issue.net[/FONT][/INDENT]

```

sudo -c 'echo "Welcome to rockingabe's machine" > /etc/issue.net'
sudo /etc/init.d/ssh reload

```

That should give you the welcome message when you connect (after the key has been accepted, of course).

---

