---
title: "webmin problem"
date: 2011-04-28
forum: Server Platforms
---

### Post by cakka on 2011-04-28
hello,

i am new ubuntu user...

i try to access my webmin
but it give me "This webpage is not available."
any ideas ?

now, webmin is useless for me
if i want to uninstall webmin, is some other application will affected (like apache, mysql, etc) ?

thanks

---

### Post by falko on 2011-04-28
Did you try to access it on port 10000?
http://<yourip>:10000

---

### Post by sikander3786 on 2011-04-28
> **falko said:**
> Did you try to access it on port 10000?
http://<yourip>:10000
I think it should be 'https' instead of 'http'.

[https://192.168.2.1:10000](https://192.168.2.1:10000)

Where 192.168.2.1 is your ip address.

---

### Post by elico on 2011-04-28
how did you installed webmin?
do you have a firewall installed?
did webmin ever worked for you?
are you sure it's running /installed?
try using the command:
> netstat -ntlp
and
> ps -aux |grep webmin

to get information about the webmin proccess.

---

### Post by cakka on 2011-05-05
> **sikander3786 said:**
> I think it should be 'https' instead of 'http'.

[https://192.168.2.1:10000](https://192.168.2.1:10000)

Where 192.168.2.1 is your ip address.

yes, i have go to that address

---

### Post by cakka on 2011-05-05
> **elico said:**
> how did you installed webmin?
do you have a firewall installed?
did webmin ever worked for you?
are you sure it's running /installed?
try using the command:

and


to get information about the webmin proccess.


thanks you, i have check the proses 
the webmin not run

i have run it again

can you tell me why it can stopped ?
i didn't stopped it

thanks

---

### Post by tgalati4 on 2011-05-05
Check the log files in /var/log.

---

### Post by cakka on 2011-05-05
> **tgalati4 said:**
> Check the log files in /var/log.

which one i should check ?

thanks

---

### Post by cakka on 2011-05-20
> **elico said:**
> how did you installed webmin?
do you have a firewall installed?
did webmin ever worked for you?
are you sure it's running /installed?
try using the command:

and


to get information about the webmin proccess.



again, i can't access my webmin :(

i have try : ```
netstat -ntlp
```

and it give me the result :
```
Last login: Fri May 20 11:45:45 2011 from 114.79.48.193
root@server1:~# netstat -ntlp
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
PID/Program name
tcp        0      0 xxx.xxx.xxx.xxx:53       0.0.0.0:*               LISTEN
11322/named
tcp        0      0 127.0.0.1:53            0.0.0.0:*               LISTEN
11322/named
tcp        0      0 127.0.0.1:25            0.0.0.0:*               LISTEN
11698/sendmail: MTA
tcp        0      0 127.0.0.1:953           0.0.0.0:*               LISTEN
11322/named
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN
11270/mysqld
tcp        0      0 127.0.0.1:587           0.0.0.0:*               LISTEN
11698/sendmail: MTA
tcp        0      0 0.0.0.0:2222            0.0.0.0:*               LISTEN
1708/sshd
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN
3177/portmap
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN
3132/apache2
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN
12063/perl
tcp6       0      0 :::53                   :::*                    LISTEN
11322/named
tcp6       0      0 ::1:953                 :::*                    LISTEN
11322/named
tcp6       0      0 :::2222                 :::*                    LISTEN
1708/sshd
root@server1:~#
```

any ideas ?

thanks

---

### Post by CharlesA on 2011-05-20
It looks like webmin is listening.

What does this return:

```
sudo iptables -L
```

---

### Post by scorch1515 on 2011-05-20
Did you do any major upgrades recently? I had this problem after upgrading to 11.04.  Try running:

     sudo service webmin restart

If this dosen't work you can always reinstall Webmin, which is what i ended up doing.
Good luck!

---

