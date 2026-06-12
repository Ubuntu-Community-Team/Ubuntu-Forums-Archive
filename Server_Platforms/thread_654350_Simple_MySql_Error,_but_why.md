---
title: "Simple MySql Error, but why?"
date: 2007-12-31
forum: Server Platforms
---

### Post by mattc908 on 2007-12-31
mattc908@mattc908:~$ mysqladmin -u root password ********
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

Why is it failing to connect to itself? I don't understand why this might be happening, I had it working perfectly before I wiped everything and started anew.

---

### Post by ghostdog74 on 2007-12-31
> **mattc908 said:**
> mattc908@mattc908:~$ mysqladmin -u root password ********
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'

Why is it failing to connect to itself? I don't understand why this might be happening, I had it working perfectly before I wiped everything and started anew.
if you put the error message into google search, you may find some answers to your problem

---

### Post by LaRoza on 2007-12-31
It doesn't look like you are using the correct command.

try:

-u root -p<password>

note, there is not space between the p and password.

---

### Post by LaRoza on 2007-12-31
> **ghostdog74 said:**
> if you put the error message into google search, you may find some answers to your problem

That is a common error message for someone (or something) tries to log on without supplying a password, google wouldn't hep much.

Reading the docs for the individual app probably would, because it would give the format of the command.

---

### Post by mattc908 on 2007-12-31
mattc908@mattc908:~$ mysqladmin -u root -p<********>
-bash: syntax error near unexpected token `newline'

---

### Post by cdenley on 2007-12-31
That error is because you used < and >. You need to look up how to use the command. First you were trying to connect without a password, but there is apparently a password already set for root. I'm not sure what you were just trying to do. You specify the password to connect with by using the -p argument, then you will be prompted to enter the password. You change the password by using the password command (password newpass).
```

cdenley@ubuntu:~$ mysqladmin -u root -p password newpass
Enter password: 
cdenley@ubuntu:~$

```

---

### Post by mattc908 on 2007-12-31
mattc908@mattc908:~$ mysqladmin -u root -p password newpass
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

mattc908@mattc908:~$ mysqladmin -u root -p password newpass
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Whats it mean when it says NO or YES, and I never set a password So... I dont know what it could be? I tried my normal username password...

---

### Post by cdenley on 2008-01-02
"using password: NO" means you are trying to connect without using a password. I think by default, root can login from the local machine without a password. However, since you're getting access denied, someone has set a root password for mysql (which is what you are currently trying to do). When you are prompted for a password, if you just hit enter, it will try connecting without a password.

---

### Post by mattc908 on 2008-01-02
Still when I go on local still gives me an error that I can not log in, Is there a a way to completely delete and re install mysql server.

---

### Post by bindatype on 2008-01-02
Whoa...there is no need to do that! Let's try resetting the root password first. Step one is stopping the msql server

```

$ sudo /etc/init.d/mysql stop

```

(On some versions of linux [suse?] it is mysqld I think--if one doesn't work try the other.

Step two is starting mysql_safe
```

$ sudo mysqld_safe &#8211;skip-grant-tables &

```

Step three is actually resetting it
```

$ sudo mysqladmin -u root password 'newpassword'

```

Step four is to start mysql normally again
```

$ sudo /etc/init.d/mysql restart

```

Note: You probably don't need to sudo this--I get a little sudo crazy.

---

### Post by mattc908 on 2008-01-06
mattc908@mattc908:~$ mysqladmin -u root -p password newpass
Enter password: 

It still asks for a password after that? I currently SSH into it so should I go local and type nothing for the pass?

---

### Post by mattc908 on 2008-01-06
I keep getting this error: 
#1045 - Access denied for user 'root'@'localhost' (using password: YES)

When I go local it keeps saying cant connect to localhost why wouldnt it be able to connect to itself?

---

### Post by mattc908 on 2008-01-08
Anyone? Anyone at all?

---

### Post by gali98 on 2008-01-08
Okay. I'm not real good with mysql yet but I had some problems similar to this. first of all when you login you should do something like
```
 sudo mysql -p
```
From there is should prompt you for a password. Enter whatever password you gave it when you installed.
If that doesn't work then try this:
There is an option (sorry can't think of it off the top of my head, and not on linux right now...)
Use```

mysql --help | less
```
to browse through the help. Look for something about host. Use that option to put in your ip address instead of localhost (use ifconfig to find your ip)
If that doesn't work you'll probably just have to wait until someone smarter than I can help you. Once you can login you can edit the tables to allow root@localhost to login. Hope this helps...
Kory

---

### Post by methodical on 2008-01-08
try this:

```
mysql -u root -p
```

Then it will prompt you for your password. Enter it and go.

---

### Post by mattc908 on 2008-01-08
> **bindatype said:**
> Whoa...there is no need to do that! Let's try resetting the root password first. Step one is stopping the msql server

```

$ sudo /etc/init.d/mysql stop

```

(On some versions of linux [suse?] it is mysqld I think--if one doesn't work try the other.

Step two is starting mysql_safe
```

$ sudo mysqld_safe –skip-grant-tables &

```

Step three is actually resetting it
```

$ sudo mysqladmin -u root password 'newpassword'

```

Step four is to start mysql normally again
```

$ sudo /etc/init.d/mysql restart

```

Note: You probably don't need to sudo this--I get a little sudo crazy.


Should I be getting this error:

```
mattc908@mattc908:~$ Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[7362]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[7368]: ended
sudo mysqladmin -u root password 'newpassword'
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
[1]+  Done                    sudo mysqld_safe –skip-grant-tables

```


When I use: And enter a password in

```
mattc908@mattc908:~$ sudo mysqladmin -u root password 'newpassword'
Password:
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```

When I used: 

```
mattc908@mattc908:~$ sudo mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

---

### Post by methodical on 2008-01-08
> **mattc908 said:**
> 
When I used: 

```
mattc908@mattc908:~$ sudo mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```

Looks like the password you entered is invalid. When you installed did you set the root password?

```
mattc908@mattc908:~$ Starting mysqld daemon with databases from /var/lib/mysql
mysqld_safe[7362]: started
STOPPING server from pid file /var/run/mysqld/mysqld.pid
mysqld_safe[7368]: ended
sudo mysqladmin -u root password 'newpassword'
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
[1]+  Done                    sudo mysqld_safe –skip-grant-tables

```

I was screwing around with some things on my server, and I was getting a similar message. I ended up just removing and reinstalling mysql. It worked after that.

---

### Post by mattc908 on 2008-01-09
What would be the code to remove and reinstall it? Im not to good with all this stuff just yet?

I tried:
```
sudo dpkg --purge mysql-server
```

Than did:
```
sudo apt-get install mysql-server
```

Than Did:
```
mattc908@mattc908:~$ mysqladmin -u root -p password newpass
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!
```

So I think I didnt uninstall it correctly?

---

### Post by methodical on 2008-01-09
i think it is:

```
sudo apt-get remove mysql-server
```

---

### Post by mattc908 on 2008-01-09
Still getting this error:

```
mattc908@mattc908:~$ mysqladmin -u root -p password newpass
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)'
Check that mysqld is running and that the socket: '/var/run/mysqld/mysqld.sock' exists!

```


Does anyone know? I'm getting ready to dump the entire server and try again.....

---

### Post by mattc908 on 2008-01-10
Anyone?

---

### Post by felixdecat on 2008-01-10
mattc I had the same problem this is how i fixed it

open up a client and type

```
 sudo nano /etc/mysql/debian.cnf
```

In this file there is a special user that mysql creates to do stuff like reboot n whatnot. I used this user information to loginto phpmyadmin then I changed the password of the root account, you can also just create another account with all prevliages.

I wouldn't change anyhing about this special account though as your mysql will prolly stop working.

---

### Post by mattc908 on 2008-01-12
Thanks, That helped a bunch!

---

