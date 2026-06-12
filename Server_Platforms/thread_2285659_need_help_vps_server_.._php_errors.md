---
title: "need help: vps server .. php errors"
date: 2015-07-07
forum: Server Platforms
---

### Post by iebo on 2015-07-07
i have just created new droplet Ubuntu 14.10 x32  on digital ocean 


i'm trying to setup simple php script  to receive sms from senders then write it into text file


as shown below, both the terminal and var log displaying errors  for every line . 
```
[Tue  Jul 07 12:57:25.513876 2015] [:error] [pid 25159] [client  ip  address:port] PHP Notice:  Undefined index: to in  /var/www/html/callback.php on line 3
[Tue Jul 07 12:57:25.513938  2015] [:error] [pid 25159] [client  ip address:port] PHP Notice:   Undefined index: msisdn in /var/www/html/callback.php on line 4
[Tue  Jul 07 12:57:25.513948 2015] [:error] [pid 25159] [client  ip  address:port] PHP Notice:  Undefined index: text in  /var/www/html/callback.php on line 5
[Tue Jul 07 12:57:25.513956  2015] [:error] [pid 25159] [client  ip address:port] PHP Notice:   Undefined index: messageId in /var/www/html/callback.php on line 6
[Tue  Jul 07 12:57:25.514046 2015] [:error] [pid 25159] [client  ip  address:port] PHP Warning:  fopen(messages.txt): failed to open stream:  Permission denied in /var/www/html/callback.php on line 8
[Tue Jul 07  12:57:25.514101 2015] [:error] [pid 25159] [client  ip address:port]  PHP Warning:  fwrite() expects parameter 1 to be resource, boolean given  in /var/www/html/callback.php on line 9
[Tue Jul 07 12:57:25.514114  2015] [:error] [pid 25159] [client  ip address:port] PHP Warning:   fclose() expects parameter 1 to be resource, boolean given in  /var/www/html/callback.php on line 10




callback.php: line 1: ?php: No such file or directory
callback.php: line 2: //Callback: No such file or directory
callback.php: line 3: =: command not found
callback.php: line 4: =: command not found
callback.php: line 5: =: command not found
callback.php: line 6: =: command not found
callback.php: line 7: //store: No such file or directory
callback.php: line 8: syntax error near unexpected token `('
callback.php: line 8: `$file = fopen("messages.txt","w");'




``` 


can you help me please ... what i can do to fix this ?

php modules are running   +  apache was installed after  apt-get update && apt-get upgrade command

thanks

---

### Post by iebo on 2015-07-07
i tried sudo chmod +x filename or sudo chmod -R 755 /folder  but it didn't help  .

do i need another distro <>version ?

---

### Post by iebo on 2015-07-18
solved !

---

### Post by cariboo on 2015-07-18
> **iebo said:**
> solved !

Could you let the rest of us know what you did to solve your problem?

---

### Post by iebo on 2015-07-18
> **cariboo said:**
> Could you let the rest of us know what you did to solve your problem?


sure...
```
#!/usr/bin/php 
``` 

on the top of the php script.

---

