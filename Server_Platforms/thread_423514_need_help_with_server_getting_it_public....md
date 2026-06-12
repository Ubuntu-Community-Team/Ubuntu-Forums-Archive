---
title: "need help with server getting it public..."
date: 2007-04-25
forum: Server Platforms
---

### Post by hockey97 on 2007-04-25
Hi I need help on getting my website on my apache2 server to public.

I know my external ip adress and did setup my router to port forward 80 and also allow my computer that has the server to be viewed to public..

What I need to know or do, is to make my website viewable throughout the internet I mean for now I want to get my ip adress thing working so that over the internet you can type my ipadress and it would take you to my server ect.

I later do plan on getting my own domain name, and would need help with setting bind9 and getting the domain named host to direct traffice to my server ect...

THanks for your time.

---

### Post by hockey97 on 2007-04-26
I also need help with mysql...   I   get this error    The full MySQL error message was : connect to server at 'localhost' failed error: 'Access denied for user 'aaron'@'localhost' (using password: YES)'

I am also using webmin and get the same error in the mysql section , in the terminal I can type and get into mysql with no error or problems but when I use a php script to connect to mysql  it get that error.

I also tried mysqladmin in the terminal and got a page with this info stuff.

 mysqladmin -u root -p password thier your happy!! lol
mysqladmin  Ver 8.41 Distrib 5.0.38, for pc-linux-gnu on i486
Copyright (C) 2000-2006 MySQL AB
This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL license

Administration program for the mysqld daemon.
Usage: mysqladmin [OPTIONS] command command....
  -c, --count=#       Number of iterations to make. This works with -i
                      (--sleep) only.
  -#, --debug[=name]  Output debug log. Often this is 'd:t:o,filename'.
  -f, --force         Don't ask for confirmation on drop database; with
                      multiple commands, continue even if an error occurs.
  -C, --compress      Use compression in server/client protocol.
  --character-sets-dir=name 
                      Directory where character sets are.
  --default-character-set=name 
                      Set the default character set.
  -?, --help          Display this help and exit.
  -h, --host=name     Connect to host.
  -p, --password[=name] 
                      Password to use when connecting to server. If password is
                      not given it's asked from the tty. WARNING: Providing a
                      password on command line is insecure as it is visible
                      through /proc to anyone for a short time.
  -P, --port=#        Port number to use for connection.
  --protocol=name     The protocol of connection (tcp,socket,pipe,memory).
  -r, --relative      Show difference between current and previous values when
                      used with -i. Currently works only with extended-status.
  -O, --set-variable=name 


I really need help.

Thanks for your time.

---

### Post by strixy on 2007-04-26
> mysqladmin -u root -pcooldude

You don't have to put the password in after the -p

eg. mysqladmin -u root -p

The system will prompt you to enter your password.

As for getting a public address, check out dyndns.com or zoneedit.com or easydns.com or no-ip.com and check out their dynamic dns services. You'll have to make sure that your ISP isn't blocking access to port 80 and that it's not against your TOS to run a server. If you're on dial up or (most) DSL forget about it. If you don't have a static IP address you'll want to look into getting a dynamic IP updater installed. All the above services can provide more information on that.

---

### Post by Catsworth on 2007-04-26
Can I suggest that you remove your password from the posts above?

---

### Post by az on 2007-04-26
[https://help.ubuntu.com/community/DynamicDNS](https://help.ubuntu.com/community/DynamicDNS)

[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by hockey97 on 2007-04-26
That is not my password just put a comment thing to show where my password would be how ever I did just used -p and a prompt came up and I put the password in and I got access.

My problem was that when I use a php script in my apache2 ect I get a mysql error saying acess denied.
I don't fully know what to do I did try one thing make a table and add a user account but that didn't work someone on here suggested that.

The DNS think I got an external ip adress I used it in windows on a ftp  server I send files to my firineds computer that's outside my network.  

What I want right now is to have my apache2 server able to be accessed outside my network just using my own ip adress I don't need a dns name ect I plan to do that later, right now I am having trouble with just getting my server seen on the internet. using ubuntu.

I  have also windows xp and have a ftp and also a web server on it and works I can access it anywhere like I just type in my external ip adress and I can then see my website ect.

Trying to get the same with apache2 in ubuntu 7.02 , I can access it with any computer on my network but not outside my network.


Also is their any thing that I should look for on downloading to protect my server from spammers and hackers ect?

Thanks for your time.

---

### Post by hockey97 on 2007-04-28
HI I need help with mysql, when I use a php script to connect to it I get an error : Access Denied at localhost@****** with password (yes).

Do I need to make a login table?? I tried alot fo stuff I can get in with the terminal in mysql, I am using webmin, also I did made a table and gave grants to it and still have the same error.

any Idea's?

I am trying to fix this before I start paying for my domain name I ddin't get one yet plan in near future.

Thanks for your time.

---

