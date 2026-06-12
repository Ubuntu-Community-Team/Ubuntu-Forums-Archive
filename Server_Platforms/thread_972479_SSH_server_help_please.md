---
title: "SSH server help please"
date: 2008-11-05
forum: Server Platforms
---

### Post by wnaBsd8d on 2008-11-05
hello all,

i have recently set up an SSH server that supposedly is encrypted with keys and whatnot 

however i am very confused with the whole idea of these keys.

i need to see if i've set up this thing properly and they keys are working as they are supposed to.

is there anyway i can check this to be sure that everything is working as it is supposed to?

thanks in advance

---

### Post by ercdvs on 2008-11-06
have you tried connecting to the server via ssh ?

try a program called putty for a windows machine... point it to the ip address of your server..  give it a valid username / password combo (usually root is prohibited by default) 

on the first connection, you will be prompted to exchange keys . . accept, and you are good to go.

You can do it from a machine local to the server, no need to be external.

The usual way to test if ssh is working is to just try and connect .. OpenSSH out of the box should work with no setup.  You can also try to run :

```
ps -ef | grep sshd
```

if this returns a PID of a running sshd process, then the SSH server is running

---

### Post by wnaBsd8d on 2008-11-06
thankyou for your reply

yes i understand that it is working..

i have connected to it and everything seems ok

but my concern is with the encryption keys. I have no previous experience with them and am not sure whether they are operating as securely as possible

i need a way to check to see if my ssh server is secure and that the keys are working because at the moment i feel as though the keys are there but anyone can connect and login without the proper key

---

