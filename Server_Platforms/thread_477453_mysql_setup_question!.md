---
title: "mysql setup question!"
date: 2007-06-18
forum: Server Platforms
---

### Post by dysolve on 2007-06-18
hello all, I posted this in the general section by mistake.. but here goes again..

I am doing the following as per a tutoral i found,
"mysqladmin -h root@server1 -u root -p password"

then i am asked
"Enter password:"

but i get the following error

"mysqladmin: connect to server at 'root@server1' failed
error: 'Unknown MySQL server host 'root@server1' (1)'
Check that mysqld is running on root@server1 and that the port is 3306.
You can check this by doing 'telnet root@server1 3306'"

when i check to see if it running i get this:

"telnet: could not resolve root@server1/3306: Name or service not known"

any idea whats going on? what am i doing wrong?
thanks
David

---

### Post by carcioni on 2007-06-18
Not sure that telnet supports [email]user@host.com[/email] type of URI.
Try something like 'telnet server1 3306 -l root'

This will probably work, but telnet doesn't understand MySQl communications protocol, so I am not sure you'll see much more than some random junk characters when it connects.

Try 'netstat -a | grep 3306' to see if the port is available and listening.


Cheers
D

---

### Post by asommer on 2007-06-18
You might make sure you've enabled the server to allow connections over the network.  Check this line in **/etc/mysql/my.cnf**:

```
bind-address            = 127.0.0.1
```


If it's 127.0.0.1 you'll probably need to change it to your IP address and restart MySQL.

---

### Post by dysolve on 2007-06-19
what the tutorial is telling me to do is..

    * MySQL comes with no root password as default. This is a huge security risk. You'll need to set one. So that the local computer gets root access as well, you'll need to set a password for that too. The local-machine-name is the name of the computer you're working on. For more information see here 

mysqladmin -u root password your-new-password
mysqladmin -h root@local-machine-name -u root -p password your-new-password
sudo /etc/init.d/mysql restart

also  when i do 
 sudo /etc/init.d/mysql restart

i get the following does that seem right?
I am not sure if the last line is telling me what it is doing or if its an error or sorts.
 * Stopping MySQL database server mysqld                                 [ OK ] 
 * Starting MySQL database server mysqld                                 [ OK ] 
 * Checking for corrupt, not cleanly closed and upgrade needing tables.

thanks again
David.

---

### Post by asommer on 2007-06-19
> mysqladmin -h root@local-machine-name -u root -p password your-new-password

Try this command if you're trying to connect to the MySQL server from the machine it's installed on:

```
mysql -u root -ppassword 
```

or:

```
mysql -u root -p
```


If you want to type the password as part of the command don't put a space between the** -p** and the password text.  If you do a** -p **by itself you'll be prompted to enter the password, which is probably a better way because it won't put the text of the password on the screen.

The restart messages look okay to me.  Those are what I get when I do a:
```

/etc/init.d/mysql restart
```

---

### Post by dysolve on 2007-06-21
does anbody know what this line really does.. 
'mysqladmin -h root@local-machine-name -u root -p password your-new-password"
I thought it gave root access to SQL to non root users on the local machine.

I have only seen that line in one tutorial ( which happens to be the one I am using) so why is it not in others?

---

### Post by Widodh on 2007-06-21
With that command you set a password for the "root" account of your MySQL database.

Since there is no password by default, you will have to set one for security reasons.

---

