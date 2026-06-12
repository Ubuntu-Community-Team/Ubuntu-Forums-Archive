---
title: "Newbie: Lamp home web server"
date: 2007-03-13
forum: Server Platforms
---

### Post by laukong on 2007-03-13
Hope somebody can help me.

I have just successfully installed Ubuntu server 6.1, apache 2, mysql, php5, webalizer, proftpd and phpmyadmin.  I followed the instructions on howtoforge's The Perfect Setup- Ubuntu Server 6.1.  My purpose is only to have my own website on the server, only one, no virtual hosting.  And be able to test run a shopping cart.

When I access the server ip ([http://192.168.0.1](http://192.168.0.1)) and domain name ([http://myname.domain.com)](http://myname.domain.com)), i'm able to see the default apache2, phpmyadmin and webalizer folders.  I was able to put in a file test.php (containing <?php phpinfo();?>) using an editor in a terminal.  When I access [http://192.168.0.1/test.php](http://192.168.0.1/test.php), i see the php information.

Now my problem:
When i try to connect to my server ip (192.168.0.1) with a ftp program, i only get a folder icon and nothing else.  I upload the files, and see the files uploaded.  But when i try to access the server ip thru a web browser, the files i uploaded are nowhere to be found.  Its still the same apache, phpmyadmin and webalizer folders.

Hope somebody can help.  What am i doing wrong? Thanks!

---

### Post by astrogazer on 2007-03-13
It sounds like you ftp the files to the wrong folder.
Go to the same directory where you saved your test.php using the shell editor,
are the files you are looking for in there?

---

### Post by laukong on 2007-03-13
I used the nano editor in a terminal, and saved the file in /var/www/ ( it's /var/www/test.php).

In the ftp program, i connect to the server ip, but i only see a folder, no directory tree, no files nor any other folder.  There are no parent folders nor child folders, and no files.  In the ftp program, I connect to [ftp://192.168.0.1](ftp://192.168.0.1) which is the server ip.

---

### Post by bandie on 2007-03-14
I followed the instructions on howtoforge's The Perfect Setup- Ubuntu Server 6.1.

when you typed
hostname and hostname -f did you get the same result?
also can you SSH from another PC?
I am having all sorts of issues getting this working

---

### Post by rjfioravanti on 2007-03-14
-f is the full qualified domain name, mine are not the same i dont think it matters

to install ssh

```

sudo apt-get install ssh

```

i believe...


Then you should be able to ssh... using the IP address, that is imortant you ssh using the ip address. I could never get my router to recognize my server name and broadcast it

---

### Post by nucklebone on 2007-03-15
luakang,

are you logging into as anonymous ftp? or are you logging into your machine as a regular user?

when you log in, you say you see a folder. are you in the /var/www directory? that's where you should be if you are in the default http directory.

if you are logging in to anonymous ftp server, chances are you can only see a folder in that directory called 'incoming' or something like that and you probably can't go or see much of anything else.

nucklebone

---

### Post by laukong on 2007-03-15
i can ssh from another PC.

I log in to ftp using my regular ubuntu username and password. Its the same username and password that i use when i use sudo in a terminal.   

I can not tell what directory i'm in when i log in to ftp, since the single folder icon i see is not even labeled, no name or anything, just a yellow folder icon.

I'm really lost on this.  Is there any other web server turorial you can recommend for my purpose, one that's would get me up and running?

---

