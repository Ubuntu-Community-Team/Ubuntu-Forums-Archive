---
title: "expect script not working at rc.local level"
date: 2010-10-01
forum: Server Platforms
---

### Post by cuyos on 2010-10-01
Hi there!! I'm trying to run an Expect script that mount an encrypted folder with truecrypt in Ubuntu 10.04, nothing too complicated. The Expect script looks like this:
```
spawn /usr/bin/truecrypt /home/administrador/home.txt -k /home/administrador/key.txt /home/administrador/encry
pted -p password --protect-hidden=no
expect "?assword*"
send "password\r"
send "\r"
expect eof

``` 
I then call it in the /etc/rc.local with:
```
expect previous_script
```

The thing is that the Expect script works like a charm as a login script or as any other script but a boot script. At the boot log I get something like
```
send: spawn id exp5 not open
``` 
I really need it because I want to mount the encrypted file at boot time without human iteraction.
Any thaughts??
Thanks in advance

---

### Post by ajgreeny on 2010-10-01
My understanding is that you add the full contents of the script (without the #!/bin/bash line, of course) to the /etc/rc.local file, just above the final **exit 0** line.

I may be wrong, not for the first time, but it is worth a try.  Whether or not the fact that a password other than your user password is needed has any effect on this I am not sure.

---

### Post by cuyos on 2010-10-04
Still not working!! I've added the code to rc.local but I still get the message of "spawn id exp5 not open" It seems to me that there is something no initiated at rc.local level that at login level is that allows the spawn to iniciate, but, since I don't understand the details of the linux service levels I don't know what's wrong.

---

