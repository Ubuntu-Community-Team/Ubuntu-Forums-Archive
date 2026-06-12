---
title: "Shell Login Issue"
date: 2010-04-15
forum: Server Platforms
---

### Post by renny666 on 2010-04-15
Hello,

Just trying to change the default shell from bash to somthing that up on ssh connection is a blank or simple ascii secure shell window that will allow port forwarding but not allow the user to type and input anything.

Someone mentioned that using /bin/true as the default shell could work but upon successful connection the shell closes instantly.

Regards,

Cameron Rennie.

---

### Post by cdenley on 2010-04-15
You can either prevent the client from starting the shell and waiting for it to exit
```

ssh **-N** -L xxx:127.0.0.1:xxx user@host

```
or you can create a shell which doesn't exit until the user presses enter
```

echo -e "#\x21/bin/sh\necho You do not have shell access.\necho press enter to exit\nread line\n"|sudo tee /usr/local/bin/fakeshell.sh
sudo chmod a+x /usr/local/bin/fakeshell.sh
sudo usermod -s /usr/local/bin/fakeshell.sh username

```

---

### Post by renny666 on 2010-04-16
> **cdenley said:**
> 
```

echo -e "#\x21/bin/sh\necho You do not have shell access.\necho press enter to exit\nread line\n"|sudo tee /usr/local/bin/fakeshell.sh

```

When I use this as the shell script i get this error upon login

```

/usr/local/bin/fakeshell.sh: Exec format error

```

and no login is possible

Can't get the SSH -N -L to work :s

Any other suggestions please?

---

### Post by cdenley on 2010-04-17
Post the contents of /usr/local/bin/fakeshell.sh to verify it is correct.
```

cat /usr/local/bin/fakeshell.sh

```

and how does this not work?
```

ssh -N -L xxx:127.0.0.1:xxx user@host

```

---

### Post by renny666 on 2010-04-17
> **cdenley said:**
> Post the contents of /usr/local/bin/fakeshell.sh to verify it is correct.
```

cat /usr/local/bin/fakeshell.sh

```


```

root@renny:~# cat /usr/local/bin/fakeshell.sh
echo -e "#\x21/bin/sh\necho You do not have shell access.\necho press enter to exit\nread line\n"|sudo tee /usr/local/bin/fakeshell.sh

```

> 
and how does this not work?
```

ssh -N -L xxx:127.0.0.1:xxx user@host

```

I'm not even sure how to use your command

Is the syntax supposed to be like ssh -N -L 80:127.0.0.1:80 user@host?

will this dynamically forward on connections from that port to their destination?

---

### Post by cdenley on 2010-04-17
> **renny666 said:**
> ```

root@renny:~# cat /usr/local/bin/fakeshell.sh
echo -e "#\x21/bin/sh\necho You do not have shell access.\necho press enter to exit\nread line\n"|sudo tee /usr/local/bin/fakeshell.sh

```

Those were commands I gave you which creates the file /usr/local/bin/fakeshell.sh. Not the contents of a file.
```

cdenley@cdenley:~$ echo -e "#\x21/bin/sh\necho You do not have shell access.\necho press enter to exit\nread line\n"|sudo tee /usr/local/bin/fakeshell.sh
#!/bin/sh
echo You do not have shell access.
echo press enter to exit
read line

cdenley@cdenley:~$ cat /usr/local/bin/fakeshell.sh
[B]#!/bin/sh
echo You do not have shell access.
echo press enter to exit
read line[/B]

cdenley@cdenley:~$

```
The contents of the script are in bold.
> **renny666 said:**
> 
I'm not even sure how to use your command

Is the syntax supposed to be like ssh -N -L 80:127.0.0.1:80 user@host?

will this dynamically forward on connections from that port to their destination?
That is not a dynamic port forward. You never said anything about dynamic.
```

ssh -N -D 80 user@host

```
You use whatever command you were using previously, but use the "-N" switch.
```

man ssh

```
> 
-N      Do not execute a remote command.  This is useful for just forwarding ports (protocol version 2 only).


---

### Post by renny666 on 2010-04-17
Apreciate the help, cheers.

---

