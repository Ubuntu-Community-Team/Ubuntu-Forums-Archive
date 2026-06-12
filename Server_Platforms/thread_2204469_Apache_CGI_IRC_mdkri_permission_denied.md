---
title: "Apache CGI IRC mdkri permission denied"
date: 2014-02-08
forum: Server Platforms
---

### Post by markeee on 2014-02-08
Hi y'all

I use cgi irc on my server so i c an connect from work - and up until now it's worked fine

but now i get an error when trying to connect

*** An error occurred: Mkdir error: Permission denied

root@dimension:/home/mark# ps aux | grep http                                                                                 
apache   10229  0.0  0.8  18724  9036 ?        S    19:40   0:00 /usr/local/apache/bin/httpd -k start
apache   10230  0.0  1.2 249384 12960 ?        Sl   19:40   0:01 /usr/local/apache/bin/httpd -k start
apache   10231  0.0  1.5 255012 15376 ?        Sl   19:40   0:01 /usr/local/apache/bin/httpd -k start
apache   10233  0.0  1.2 249492 12716 ?        Sl   19:40   0:01 /usr/local/apache/bin/httpd -k start
apache   10314  0.0  1.2 249760 12864 ?        Sl   19:40   0:01 /usr/local/apache/bin/httpd -k start
root     12289  0.0  0.0   4708   796 pts/13   S+   20:17   0:00 grep --color=auto http
root@dimension:/home/mark#   

apache running as user apache

and  i changed the location of cgiirc to be owned by user apache chown -R /usr/local/apache/htdocs/testing - still didn't work

so i then chmodded the fiels to 777 - and it stil wont work


root@dimension:/usr/local/apache/htdocs# ls -la testing/                                                                      
total 200                                                                                                                     
drwxr-xr-x  7 apache proxy  4096 Dec  7 17:04 .
drwxr-xr-x 94 root   root  69632 Feb  8 16:18 ..
-rwxrwxrwx  1 apache proxy  1100 Dec  7 06:45 backup.conf
-rwxrwxrwx  1 apache proxy  9288 Dec  7 17:08 cgiirc.config
-rwxrwxrwx  1 apache proxy  5222 Dec  7 06:45 client.c
-rwxrwxrwx  1 apache proxy  2239 Dec  7 06:45 client-perl.cgi
drwxrwxrwx  2 apache proxy  4096 Dec  7 06:45 docs
drwxrwxrwx  2 apache proxy  4096 Dec  7 06:45 formats
-rw-r--r--  1 apache proxy    22 Dec  7 06:45 .gitattributes                                                                  
-rw-r--r--  1 apache proxy    29 Dec  7 06:45 .gitignore                                                                      
-rw-r--r--  1 apache proxy   236 Dec  7 08:37 .htaccess                                                                       
-rw-r--r--  1 apache proxy   245 Dec  7 08:16 .htaccess2                                                                      
drwxrwxrwx  3 apache proxy  4096 Dec  7 06:45 images
drwxrwxrwx  3 apache proxy  4096 Dec  7 06:45 interfaces
-rwxrwxrwx  1 apache proxy  1637 Dec  7 06:45 ipaccess.example
-rwxrwxrwx  1 apache proxy  7979 Dec  7 06:45 irc.cgi
drwxrwxrwx  3 apache proxy  4096 Dec  7 06:45 modules
-rwxrwxrwx  1 apache proxy 42055 Dec  7 06:45 nph-irc.cgi
-rwxrwxrwx  1 apache proxy  1797 Dec  7 06:45 README
root@dimension:/usr/local/apache/htdocs#                                                                                      
 


any help would be hugely appreciated - bit stuck as to what to do now :(

---

### Post by markeee on 2014-02-08
Really stuck :( tried everything i can think of!!

---

### Post by howefield on 2014-02-08
Moved to the "*Server Platforms*" forum, you'll have some knowledgeable posters in here and if you get no response within about 24 hours, you can bump the thread.

---

### Post by markeee on 2014-02-08
Thanks howefield - i wasn't really sure where to put it

---

### Post by Bashing-om on 2014-02-08
markeee; Hi !

The IRC network is recovering from a serious DDoS attack.
Is SASL and Blowfish a part of your connection protocol ?
If BLOWFISH, you may have to reconfigure your "cap_sasl.pl" file.

[INDENT][INDENT]maybe yes
[/INDENT][/INDENT]

---

### Post by markeee on 2014-02-08
nope no blowfish or sasl - just a basic cgiirc

Bashing-om - but surely an irc DDOS attack wouldn't affect the above?

The error seems to suggest something wrong with permissions as it cant make a directory?! :(

---

### Post by Bashing-om on 2014-02-08
markeee; Welp;

Mind ya there is more that I do not know than I will ever ever know, but ->

Where does cgi irc try and make that directory, local on the machine - on on the network ?
Anything revealing in the logs ?

[INDENT]sometimes it helps just to have some one to talk to
[/INDENT]

---

### Post by markeee on 2014-02-08
hey mate,

cgiirc is located in /usr/local/apache/htdocs/testing - trying to create a directory locally - but im not sure where i cant see any lgfile with cgiirc and ive never had this error before

apache is running as apache
root@dimension:/home/mark# ps aux | grep http 
apache 10229 0.0 0.8 18724 9036 ? S 19:40 0:00 /usr/local/apache/bin/httpd -k start
apache 10230 0.0 1.2 249384 12960 ? Sl 19:40 0:01 /usr/local/apache/bin/httpd -k start
apache 10231 0.0 1.5 255012 15376 ? Sl 19:40 0:01 /usr/local/apache/bin/httpd -k start
apache 10233 0.0 1.2 249492 12716 ? Sl 19:40 0:01 /usr/local/apache/bin/httpd -k start
apache 10314 0.0 1.2 249760 12864 ? Sl 19:40 0:01 /usr/local/apache/bin/httpd -k start
root 12289 0.0 0.0 4708 796 pts/13 S+ 20:17 0:00 grep --color=auto http
root@dimension:/home/mark# 


and the files look ok? see below ls -la of testing dir..owned by apache and all have 777 perms -

is there a system wide logfile that may shed some light on what dir cgiirc is trying to create??

thanks

---

### Post by Bashing-om on 2014-02-08
markeee; Well.

Here, I am dumber than a sack of rocks. but -> log files, Maybe
```

ls -la /var/log/apach*

```
See if we can find Apache's log file.. and do some heavy reading.
As presently we do not know what file(s) are involved, or what directory, or even where .

When all else fails,
[INDENT][INDENT][INDENT]read the logs ?
[/INDENT][/INDENT][/INDENT]

---

### Post by markeee on 2014-02-08
lol if you're dumber than a sack of rocks, what am i? i didn't know what to do:P

dont be so negative ..'Mind ya there is more that I do not know than I will ever ever know, but ->
' and then the dumb comment..

root@dimension:/var/log/apache2# ls -la                                                                           
total 8                                                                                                           
drwxr-x---  2 root adm  4096 Dec  5 21:16 .
drwxr-xr-x 22 root root 4096 Feb  8 15:43 ..
-rw-r-----  1 root adm     0 Dec  5 21:16 access.log                                                              
-rw-r-----  1 root adm     0 Dec  5 21:16 error.log                                                               
-rw-r-----  1 root adm     0 Dec  5 21:16 other_vhosts_access.log                                                 
root@dimension:/var/log/apache2# cd ..                                                                            
root@dimension:/var/log# ls -la | grep ap                                                                         
drwxr-x---  2 root              adm       4096 Dec  5 21:16 apache2
-rw-r-----  1 root              adm          0 Feb  8 07:43 apport.log
-rw-r-----  1 root              adm        959 Feb  8 06:30 apport.log.1
-rw-r-----  1 root              adm        124 Dec  6 09:36 apport.log.2.gz
-rw-r-----  1 root              adm        742 Nov 26 19:37 apport.log.3.gz
-rw-r-----  1 root              adm        775 Nov 26 01:28 apport.log.4.gz
-rw-r-----  1 root              adm        214 Nov 19 07:52 apport.log.5.gz
-rw-r-----  1 root              adm        264 Nov 16 17:22 apport.log.6.gz
-rw-r-----  1 root              adm        105 Oct 14 22:52 apport.log.7.gz
drwxr-xr-x  2 root              root      4096 Feb  7 17:25 apt
-rw-r--r--  1 root              root     50958 Apr 23  2013 bootstrap.log
root@dimension:/var/log#    

nothing there of use

ARGHH nightmare eh

I didn't change anything either, all i'd been doing is trying to get squidguard to work nothing with a[ache and this has somehow broken:(

---

### Post by Bashing-om on 2014-02-08
markeee; Yeah,
But I would not want that I should mislead ya. Just upfront -> I ain't got no magic answer.
We be hunting !

 /var/log/apache2/error.log ??

List of all Apache log files ( some might be somewhere else .. depends on your configuration ):
```

cd /var/log/apache2 && ls -l

```

"i have just seen in the access log folder for apache2 (/var/log/apache2/) there is a file called other_vhosts_access.log and that is where the log is !"

> 
Apache HTTP Server Logs

The default installation for Apache2 on Ubuntu creates a log subdirectory: /var/log/apache2. Within this subdirectory are two log files with two distinct purposes:

/var/log/apache2/access.log - records of every page served and every file loaded by the web server.

/var/log/apache2/error.log - records of all error conditions reported by the HTTP server


Now if those logs do not exist, something stinks to high heaven, or someone moved them !

[INDENT][INDENT]Oh Where Oh Where can my little
[INDENT][INDENT]log be 
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by markeee on 2014-02-08
> **Bashing-om said:**
> markeee; Yeah,
But I would not want that I should mislead ya. Just upfront -> I ain't got no magic answer.
We be hunting !

 /var/log/apache2/error.log ??

List of all Apache log files ( some might be somewhere else .. depends on your configuration ):
```

cd /var/log/apache2 && ls -l

```

"i have just seen in the access log folder for apache2 (/var/log/apache2/) there is a file called other_vhosts_access.log and that is where the log is !"


found where the log fi


Now if those logs do not exist, something stinks to high heaven, or someone moved them !

[INDENT][INDENT]Oh Where Oh Where can my little
[INDENT][INDENT]log be 
[/INDENT][/INDENT][/INDENT][/INDENT]


The apache2 logs cant be it the modified times

mark@dimension:/var/log/apache2$ ls -la
total 8
drwxr-x--- 2 root adm 4096 Dec 5 21:16 .
drwxr-xr-x 22 root root 4096 Feb 8 15:43 ..
-rw-r----- 1 root adm 0 Dec 5 21:16 access.log
-rw-r----- 1 root adm 0 Dec 5 21:16 error.log
-rw-r----- 1 root adm 0 Dec 5 21:16 other_vhosts_access.log
mark@dimension:/var/log/apache2$ 



found where the log files are

root@dimension:/usr/local/apache/logs# ls -la
total 20872
drwxr-xr-x 2 root root 4096 Feb 8 19:40 .
drwxr-xr-x 15 root root 4096 Nov 16 08:11 ..
-rw-r--r-- 1 root root 9648574 Feb 9 01:42 access_log
srwx------ 1 apache root 0 Feb 8 19:40 cgisock.10228
srwx------ 1 apache root 0 Jan 4 17:00 cgisock.1461
srwx------ 1 apache root 0 Jan 25 06:25 cgisock.1642
srwx------ 1 apache root 0 Dec 10 18:08 cgisock.1647
srwx------ 1 apache root 0 Jan 11 15:14 cgisock.1648
srwx------ 1 apache root 0 Dec 8 16:57 cgisock.1649
srwx------ 1 apache root 0 Jan 24 20:09 cgisock.1656
srwx------ 1 apache root 0 Dec 22 17:24 cgisock.1657
srwx------ 1 apache root 0 Dec 12 20:25 cgisock.1659
srwx------ 1 apache root 0 Jan 10 18:24 cgisock.1685
srwx------ 1 apache root 0 Dec 8 08:53 cgisock.29029
srwx------ 1 apache root 0 Dec 7 08:46 cgisock.7599
-rw-r--r-- 1 root root 171350 Feb 9 01:04 error_log
-rw-r--r-- 1 root root 6 Feb 8 19:40 httpd.pid
-rw-r--r-- 1 root root 11525609 Feb 9 01:42 ssl_request_log
root@dimension:/usr/local/apache/logs# 


looking in error and access atm - thing is though it looks like a cgiirc error rather than an apache httpd error? ;/

---

### Post by markeee on 2014-02-08
OOh i found something in the error_log!

[Sat Feb 8 21:46:24 2014] CGI:IRC Error: Mkdir error: Permission denied (main::load_socket 1252)
[Sat Feb 08 21:53:56.012874 2014] [access_compat:error] [pid 10231:tid 2954840896] 
[client 81.94.213.24:50862] AH01797: client denied by server configuration: /usr/local/apache/htdocs/testing/modules/


[Sat Feb 08 21:53:56.012960 2014] [access_compat:error] [pid 10231:tid 2954840896] 
[client 81.94.213.24:50862] AH01797: client denied by server configuration: /usr/local/apache/htdocs/testing/cgiirc.config

[Sat Feb 08 21:53:56.013522 2014] [authz_core:error] [pid 10231:tid 2954840896] [client 81.94.213.24:50862] AH01630:
 client denied by server configuration: /usr/local/apache/htdocs/testing/.htaccess

---

### Post by Bashing-om on 2014-02-08
markeee; Hey!

The great thing about ubuntu, It logs every thing ! .. Just gotta find where to look.
cgiirc error, may be as simple as a config file messed up and as hard as to find that particular config file !
What is wrote where ??


[INDENT][INDENT]patience is a virtue
[/INDENT][/INDENT]

---

### Post by markeee on 2014-02-08
3 entries..quite long so ive made them on 2 lines each

---

### Post by markeee on 2014-02-08
hey - thanks for helping ..noone else seems interested :D -- found some entries for cgiirc in the error_log in apache logs dir

---

### Post by Bashing-om on 2014-02-08
markeee; Welp;

Not much help, not much anyone can do in a situation like this.
See where the logs lead us to, and then the smart boys ( that term is inclusive ) will chime in.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by markeee on 2014-02-08
it looks like it could be cgiirc.config?

cant make anything from
[Sat Feb 8 21:46:24 2014] CGI:IRC Error: Mkdir error: Permission denied (main::load_socket 1252)
[Sat Feb 08 21:53:56.012874 2014] [access_compat:error] [pid 10231:tid 2954840896] 
[client 81.94.213.24:50862] AH01797: client denied by server configuration: /usr/local/apache/htdocs/testing/modules/

and the last one about .htaccess - dont see how that could affect anything - only using .htaccess to passwd protect the dir and it worked fine

---

### Post by Bashing-om on 2014-02-08
markeee; Well, making some progress,

What does "top" show for the PID 10231 ?

And now we need a smarty, how do we trace "load_socket 1252" see what process owns it ?

as you say, not much to go on !

[INDENT][INDENT]all we can do is look
[/INDENT][/INDENT]

---

### Post by markeee on 2014-02-08
Yea I don't think it can be htaccess but what about the cgiirc.config ?

I can't see the profess in top - maybe it's apache? I've restarted apache since

So would be different process Id - il try cgi irc now see what it writes to the log

---

### Post by Bashing-om on 2014-02-09
markeee; Well,

Let's see what we can find. What returns from:
```

ps aux | grep "cgiirc*"

```

And just to cover a base. What server is "http" connecting to ? Can you ping that server/port ? This just to make sure the problem is in your house, and not elsewhere. (can not get that off my mind )

If we can answer what and why, we can know where .

[INDENT][INDENT]'tis a puzzle indeed
[/INDENT][/INDENT]

---

### Post by markeee on 2014-02-11
hey
sorry for the delay
the server is at 94.193.78/219 and working fine..i can access it [http://94.193.78.219](http://94.193.78.219) sitting in my room


root@dimension:~# ps aux | grep cgiirc
root      6686  0.0  0.0   4704   796 pts/0    S+   18:45   0:00 grep --color=auto cgiirc
root@dimension:~#


i didnt think that would show anything - as theres no prpcess running as its a cgi script just sitting in a dir in the apache htdocs dir

---

### Post by Bashing-om on 2014-02-11
markeee; Welp,

Mind you I am struggling also to understand what is going on.
Can you start [color=red]"irc.cgi"[/color] Manually ? Maybe add some echo statements in the scripts and see how it progresses ?
> 
-rwxrwxrwx 1 apache proxy 7979 Dec 7 06:45 irc.cgi


What has to be running in order to start "irc.cgi" ?

presently ->

[INDENT][INDENT]I am like unto a fish out of the water
[/INDENT][/INDENT]

---

### Post by markeee on 2014-02-11
apache - it runs from the web browser sitting on the apache webserver

root@dimension:/usr/local/apache/htdocs/testing# ls -la
total 196
drwxr-xr-x  7 apache nogroup  4096 Sep 24 10:27 .
drwxr-xr-x 95 root   root    69632 Feb  9 01:26 ..
-rwxrwxrwx  1 apache nogroup  1105 Sep 24 10:27 cgiirc.config
-rwxrwxrwx  1 apache nogroup  9285 Sep 24 10:27 cgiirc.config.full
-rwxrwxrwx  1 apache nogroup  5222 Sep 24 10:27 client.c
-rwxrwxrwx  1 apache nogroup  2239 Sep 24 10:27 client-perl.cgi
drwxrwxrwx  2 apache nogroup  4096 Sep 24 10:27 docs
drwxrwxrwx  2 apache nogroup  4096 Sep 24 10:27 formats
-rw-r--r--  1 apache nogroup    22 Sep 24 10:27 .gitattributes
-rw-r--r--  1 apache nogroup    29 Sep 24 10:27 .gitignore
-rw-r--r--  1 apache nogroup   105 Sep 24 10:27 .htaccess
drwxrwxrwx  3 apache nogroup  4096 Sep 24 10:27 images
drwxrwxrwx  3 apache nogroup  4096 Sep 29 22:36 interfaces
-rwxrwxrwx  1 apache nogroup  1637 Sep 24 10:27 ipaccess.example
-rwxrwxrwx  1 apache nogroup  7979 Sep 24 10:27 irc.cgi
drwxrwxrwx  3 apache nogroup  4096 Sep 24 10:27 modules
-rwxrwxrwx  1 apache nogroup 42055 Sep 24 10:27 nph-irc.cgi
-rwxrwxrwx  1 apache nogroup  1797 Sep 24 10:27 README
root@dimension:/usr/local/apache/htdocs/testing#


[http://94.193.78.219/cgiirc.config](http://94.193.78.219/cgiirc.config)

thats the config file

---

### Post by markeee on 2014-02-11
theres those 3 errors
[Sat Feb 8 21:46:24 2014] CGI:IRC Error: Mkdir error: Permission denied (main::load_socket 1252)
[Sat Feb 08 21:53:56.012874 2014] [access_compat:error] [pid 10231:tid 2954840896] 
[client 81.94.213.24:50862] AH01797: client denied by server configuration: /usr/local/apache/htdocs/testing/modules/


[Sat Feb 08 21:53:56.012960 2014] [access_compat:error] [pid 10231:tid 2954840896] 
[client 81.94.213.24:50862] AH01797: client denied by server configuration: /usr/local/apache/htdocs/testing/cgiirc.config

[Sat Feb 08 21:53:56.013522 2014] [authz_core:error] [pid 10231:tid 2954840896] [client 81.94.213.24:50862] AH01630:
client denied by server configuration: /usr/local/apache/htdocs/testing/.htaccess
Last edited by markeee; 2 Days Ago at 09:00 PM.

but bit stuck really:(

---

### Post by Bashing-om on 2014-02-11
markeee; Hey ,

I ask ya again, are you sure that your distant end server still maintains support for IRC ?
> 
default_server = irc.blitzed.org

Due to the recent DDoS attack, may servers have dropped out of rotation, in order to serve their paying customers.

The server is valid, but does it support IRC ?
> 
sysop@1310mini:~$ ping -c 3 irc.blitzed.org
PING na.iso.blitzed.org (173.255.213.121) 56(84) bytes of data.
64 bytes from stagsleap.strtok.net (173.255.213.121): icmp_seq=1 ttl=53 time=100 ms
64 bytes from stagsleap.strtok.net (173.255.213.121): icmp_seq=2 ttl=53 time=99.0 ms
64 bytes from stagsleap.strtok.net (173.255.213.121): icmp_seq=3 ttl=53 time=95.8 ms

--- na.iso.blitzed.org ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 95.802/98.304/100.032/1.811 ms
sysop@1310mini:~$


I stand in need of education as to how to verify that connection.

EDIT: Will pay us to look at this script:
> 
script_login = irc.cgi


[INDENT]it is a process,
[INDENT][INDENT]one step at a time
[/INDENT][/INDENT][/INDENT]

---

### Post by markeee on 2014-02-11
ok so il open irc.cgi in nano and look for where it triues to make a dir i guess?:|

---

### Post by Bashing-om on 2014-02-11
markeee; Hi !

Yeah, That is what I think. A script somewhere is attempting to "mkdir" somewhere for some reason. That point needs to be identified before any action can be taken.

[INDENT][INDENT]read any scripts lately for
[INDENT][INDENT][INDENT]entertainment
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by markeee on 2014-02-12
root@dimension:/usr/local/apache/htdocs/testing# cat nph-irc.cgi | grep mkdir
   mkdir($config->{socket_prefix}.$cgi->{R}, 0700) or error("Mkdir error: $!");
root@dimension:/usr/local/apache/htdocs/testing#


looks like this could be it

need to figure outbwhat the vars translate to

---

### Post by Bashing-om on 2014-02-12
markeee; Yeah !

That do look likely !
Sorry, but will take one of the server smart guys (and gals) to lend ya a further hand. That is now about 2 steps above my level of comprehension. (sockets)

But you can bet I will keep up on this thread.

[INDENT][INDENT]a know it all
[INDENT][INDENT][INDENT]am NOT[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by markeee on 2014-02-12
thanks for your time :) 

whats irritating me more than anything..is that I dont know what I changed to cause it to break ;/

---

### Post by Bashing-om on 2014-02-12
markeee; Hey !

I do this for a lot of reasons, If I did not want to or like to, I would not.
I welcome any experience that increases my knowledge and ability with this my operating system of choice.

As to what happened to cause it .. who knows, any thing can happen ( still recovering from a loss of power here !). That is the reason we make good backups, just in the event the expedient thing to do is (RE-)install. But, I would always prefer to fix it and go on.

We are not abandoning this, just waiting on someone with the experience to advise further.

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by markeee on 2014-02-19
still noone ;( every question ive posted seems to get lost noone can help :(

---

