---
title: "ssh from php"
date: 2014-07-10
forum: Server Platforms
---

### Post by Dr_Lion on 2014-07-10
I'm trying to launch some scripts remotely on my machine, from a second machine through php.

I have a php webpage, and i was trying to use "Net/SSH2.php" to execute a remote script through php, i have a keypair with a passphrase. But i could not get SSH2 to work, it give 2 warnings, says it doesn't find the file, and to insert a absolute path, which i don't know what it is.

I've been struggling 2 or 3 days with this, and i decided to use python with paramiko, because with python i can make the connection, and i've decided to use php to call the python script with shell_exec().

I think it is not the best, neither the beautifull way, but i only need it working and that's all it is not.

The real problem is that i need to access php by browser, for this to work, i was testing this on the machine itself and very happy because it was working if i call php from the command line, it would call python and everything works like supose. Well i tried to execute php from browser and i became unhappy because it doesn't work.

In browser php code runs until the end, and it calls python code, because i put python writing onto a file, and the file is written too. But the remote scripts doesn't execute.

Anyone have a clue about what is happening? i've been searching the web and nothing..
Sorry for my bad english and thanks in advance.

---

### Post by SeijiSensei on 2014-07-11
PHP web applications run with the permissions of the "user" that owns the Apache process.  On Ubuntu, that user is called "www-data".  So you would need to create a public key for the www-data user and use that to log in remotely.  From the command line, PHP will run with the current user's configuration, or with root's configuration if you use sudo.  (Sudo is not an option for PHP scripts run through a browser.  Never give the www-data user root privileges; it creates an enormous security hole.)

---

### Post by spartica on 2014-07-11
Why not just copy / paste the key into the PHP script itself? ie.

instead of doing $rsa->loadKey(file_get_contents('...')) why not do this?:

```
$rsa = new Crypt_RSA();
$rsa->loadKey('-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQCqGKukO1De7zhZj6+H0qtjTkVxwTCpvKe4eCZ0FPqri0cb2JZfXJ/DgYSF6vUp
wmJG8wVQZKjeGcjDOL5UlsuusFncCzWBQ7RKNUSesmQRMSGkVb1/3j+skZ6UtW+5u09lHNsj6tQ5
1s1SPrCBkedbNf0Tp0GbMJDyR4e9T04ZZwIDAQABAoGAFijko56+qGyN8M0RVyaRAXz++xTqHBLh
3tx4VgMtrQ+WEgCjhoTwo23KMBAuJGSYnRmoBZM3lMfTKevIkAidPExvYCdm5dYq3XToLkkLv5L2
pIIVOFMDG+KESnAFV7l2c+cnzRMW0+b6f8mR1CJzZuxVLL6Q02fvLi55/mbSYxECQQDeAw6fiIQX
GukBI4eMZZt4nscy2o12KyYner3VpoeE+Np2q+Z3pvAMd/aNzQ/W9WaI+NRfcxUJrmfPwIGm63il
AkEAxCL5HQb2bQr4ByorcMWm/hEP2MZzROV73yF41hPsRC9m66KrheO9HPTJuo3/9s5p+sqGxOlF
L0NDt4SkosjgGwJAFklyR1uZ/wPJjj611cdBcztlPdqoxssQGnh85BzCj/u3WqBpE2vjvyyvyI5k
X6zk7S0ljKtt2jny2+00VsBerQJBAJGC1Mg5Oydo5NwD6BiROrPxGo2bpTbu/fhrT8ebHkTz2epl
U9VQQSQzY1oZMVX8i1m5WUTLPz2yLJIBQVdXqhMCQBGoiuSoSjafUhV7i1cEGpb88h5NBYZzWXGZ
37sJ5QsW+sJyoNde3xH8vdXhzU7eT82D6X/scw9RZz+/6rCJ4p0= 
-----END RSA PRIVATE KEY-----');


$ssh->login('username', $rsa);
```

---

### Post by SeijiSensei on 2014-07-11
Perhaps because loading a *private key* into PHP is not a good idea from a security perspective?

---

### Post by thnewguy on 2014-07-11
Maybe I'm missing something, but if all you want to do is run a remote SSH session, then why not just enable OpenSSH on the server? Why go through the trouble of setting up a PHP script to launch a shell or a shell script?

---

### Post by Dr_Lion on 2014-07-14
> **SeijiSensei said:**
> PHP web applications run with the permissions of the "user" that owns the Apache process.  On Ubuntu, that user is called "www-data".  So you would need to create a public key for the www-data user and use that to log in remotely.  From the command line, PHP will run with the current user's configuration, or with root's configuration if you use sudo.  (Sudo is not an option for PHP scripts run through a browser.  Never give the www-data user root privileges; it creates an enormous security hole.)

Ok, so the next step i need is to create a key pair for the www-data user. I know how to create a key-pair for logged in user, but for www-data i don't know how.

I'm beeing a little noob, but is there an option to create a key pair for other user, or do i have to log in with www-data user to create a key for this user? If this is the way, how should i log in, i supose i shoudn't log out and log in on the main screen when i reboot right?
How do i do it?


> **spartica said:**
> Why not just copy / paste the key into the PHP script itself? ie.

instead of doing $rsa->loadKey(file_get_contents('...')) why not do this?:

```
$rsa = new Crypt_RSA();
$rsa->loadKey('-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQCqGKukO1De7zhZj6+H0qtjTkVxwTCpvKe4eCZ0FPqri0cb2JZfXJ/DgYSF6vUp
wmJG8wVQZKjeGcjDOL5UlsuusFncCzWBQ7RKNUSesmQRMSGkVb1/3j+skZ6UtW+5u09lHNsj6tQ5
1s1SPrCBkedbNf0Tp0GbMJDyR4e9T04ZZwIDAQABAoGAFijko56+qGyN8M0RVyaRAXz++xTqHBLh
3tx4VgMtrQ+WEgCjhoTwo23KMBAuJGSYnRmoBZM3lMfTKevIkAidPExvYCdm5dYq3XToLkkLv5L2
pIIVOFMDG+KESnAFV7l2c+cnzRMW0+b6f8mR1CJzZuxVLL6Q02fvLi55/mbSYxECQQDeAw6fiIQX
GukBI4eMZZt4nscy2o12KyYner3VpoeE+Np2q+Z3pvAMd/aNzQ/W9WaI+NRfcxUJrmfPwIGm63il
AkEAxCL5HQb2bQr4ByorcMWm/hEP2MZzROV73yF41hPsRC9m66KrheO9HPTJuo3/9s5p+sqGxOlF
L0NDt4SkosjgGwJAFklyR1uZ/wPJjj611cdBcztlPdqoxssQGnh85BzCj/u3WqBpE2vjvyyvyI5k
X6zk7S0ljKtt2jny2+00VsBerQJBAJGC1Mg5Oydo5NwD6BiROrPxGo2bpTbu/fhrT8ebHkTz2epl
U9VQQSQzY1oZMVX8i1m5WUTLPz2yLJIBQVdXqhMCQBGoiuSoSjafUhV7i1cEGpb88h5NBYZzWXGZ
37sJ5QsW+sJyoNde3xH8vdXhzU7eT82D6X/scw9RZz+/6rCJ4p0= 
-----END RSA PRIVATE KEY-----');


$ssh->login('username', $rsa);
```

Besides the security problem that that solution may create, this way the connection would work with the user key, or i would need to create a key for www-data user too? because from the first awnser to this topic i assume this is my true problem. Me using a key for user "duck" when php/apache is "owned" by user www-data.


> **thnewguy said:**
> Maybe I'm missing something, but if all you want to do is run a remote SSH session, then why not just enable OpenSSH on the server? Why go through the trouble of setting up a PHP script to launch a shell or a shell script?

I think you didn't got the point, my objective is to have a php script automating the launch of scripts in a remote machine, and connection between machines should be secure, over ssh.

---

### Post by SeijiSensei on 2014-07-14
Here's one way to create a key-pair as www-data:

1) Use sudo and an editor like nano to edit the file /etc/passwd.  Duplicate the entry for www-data and make the two entries look like this:
```

#www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/bin/bash

```

2) Now become the root user momentarily then switch to www-data:
```

$ sudo su
[password]
# become the www-data user
# su www-data
# generate an SSH key for www-data
$ ssh-key-gen ...
$ exit
# exit

```

3) Add the new id_rsa.pub entry in /var/www/.ssh to the "authorized_keys" file of the remote user that will be running the applications.

4) As a test, I'd replay step (2) so you become the www-data user and use SSH to connect to the remote as intended.

5) If everything works, re-edit /etc/passwd so that www-data has /usr/sbin/nologin as its default shell once more.

---

### Post by Dr_Lion on 2014-07-15
Well, thanks a lot, finally i did acomplished that. Although it wasn't the beatifull way, using only php it is working, later if i have time i may come back to this, but from now it has to be. Since my ssh2.php instalation must have some problem and i'm not able to find those files in correct path.

Thanks to all that helped, the problem was the keys that were from my user, and python was beeing executed by other user, www-data from apache.

---

