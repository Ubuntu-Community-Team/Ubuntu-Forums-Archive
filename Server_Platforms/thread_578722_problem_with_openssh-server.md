---
title: "problem with openssh-server"
date: 2007-10-17
forum: Server Platforms
---

### Post by benma on 2007-10-17
i installed ssh package, which installed openssh-server and openssh-client.
when i CLI: ssh localhost
the cursor moves to next line, which i completely empty. no login, nothing. the only thing that happens is when i press on keys, the cursor prints the keys i pressed.
"exit" does nothing as well.
the sshd process seems to run.
retsrating the daemon doesn't help.
any ideas?
please help.

---

### Post by ruibernardo on 2007-10-17
Hi benma,

take a look here for more info about SSH: [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) (search for the "Logging in to a remote computer over ssh" section).

You should access the SSH server with 
```
ssh username@localhost
```in your case.

---

### Post by benma on 2007-10-17
i get after severall minutes of trying to connect:
ssh: connect to host localhost port 22: Connection timed out

---

### Post by ruibernardo on 2007-10-17
> **benma said:**
> i get after severall minutes of trying to connect:
ssh: connect to host localhost port 22: Connection timed out

Try again and after you see:

```
 username@localhost's password:
```on the screen,  type your password (you got 2 minutes to do it, then you get that error message).

---

### Post by benma on 2007-10-17
it never asks for password. it just shows a blank line and then times out

---

### Post by ruibernardo on 2007-10-17
That's strange, you should have seen a message like this (even before it asks for the password):

```
username@myubuntu:~$ ssh username@localhost
The authenticity of host 'localhost (127.0.0.1)' can't be established.
RSA key fingerprint is 9o:89:zx:ym:rl:h9:ll:89:z3:97:79:v2:xx:9p:oh:ah.
Are you sure you want to continue connecting (yes/no)? 
```Then it would ask for your password.

Can you confirm that you got an openssh-server installed and running? Type

```
sudo netstat -nap|grep ":22"
```and paste the output here, please.

---

### Post by mattc908 on 2007-10-17
Okay Its on your local host. Okay so go on the physical server itself and type: 
```

ifconfig

```
You will get a long read out, look for: inet addr: 192.168.1.___

For example if it says: 192.168.1.104 in you SSH client type:
```

ssh username@192.168.1.104

```

If its still not responding try installing it again on your physical server w/:
```

sudo apt-get install ssh openssh-server

```

---

### Post by benma on 2007-10-18
sudo netstat -nap|grep ":22"                      returns:

tcp6       0      0 :::22                   :::*                    LISTEN     5740/sshd

my IP is 10.0.0.2, and doing: ssh username@10.0.0.2
gives same results

sudo apt-get install ssh openssh-server

says i already have the newest version.

---

### Post by bodhi.zazen on 2007-10-18
Try this :

```
ssh -vv localhost
```

The -vv should give us some idea as to where it is hanging (post the output).

Edit: That is two v (- v v) not a small W

---

