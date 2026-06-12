---
title: "FTP Weeping and Gnashing of Teeth"
date: 2011-04-23
forum: Server Platforms
---

### Post by DonMegel on 2011-04-23
Please please help me. I have been trying to set up an FTP server on my Linux box for days. I have put a good 13 or 14 hours into trying to do this. My family life is suffering. I am going insane.

I have a headless Ubuntu server, 10.04, I have tried ProFTPd and vsFTPd, I have scoured the interwebs trying countless tutorials, uninstalling the FTP programs and then reinstalling to no avail. All I want to do is set up an FTP with a single user, my Mother, so that she can remote in and look at family pictures I have on the server. 

Please, please someone help me.

---

### Post by Dry Lips on 2011-04-23
Have you tried this tutorial?
[http://www.the-web-book.com/build-your-own-webserver.html](http://www.the-web-book.com/build-your-own-webserver.html)

steps:

1. ```
sudo apt-get install proftpd
```2. ```
sudo gedit /etc/shells
```enter ```
/bin/false
```as a single line.
proofread, save. (The logic is, there is no shell named "false")

3. Make a directory where you'll place the files you'll want her to see.
 ```
mkdir /wherever/your/pictures/are
```4. Make an useraccount:
```
sudo useradd yourmom -d /wherever/your/pictures/are -s /bin/false
```

5. Give your mom ownership to the folder:
```
sudo chown -hR yourmom /wherever/your/pictures/are
```(proofread before doing this!)

6. Set a password for her account
```
passwd yourmom
``` (you'll be prompted to type the password twice)

7. Now your mom can enter the folder you've set up by typing your servers ip-address,
 assuming that you have a static ip address. 
(If not, see the tutorial above, or [http://ubuntuforums.org/showthread.php?t=632841](http://ubuntuforums.org/showthread.php?t=632841) for instructions on doing this.) I haven't actually attempted this as I've got a static ip myself.:-$

---

### Post by DonMegel on 2011-04-24
Thank you but it did not work. To begin with, I had no /var/www/Mother dir. Mother is the user name I created since I did not want to reuse mom and potentially have some permissions issue. 

I tired to log on anyway but to no avail I get a Connection attempt failed with "ECONNREFUSED - Connection refused by server" message. 

I have port 21 forwarded in my router.

---

### Post by HermanAB on 2011-04-24
Uhmmm, first of all, throw all the howto guides that you have been reading, far, far, away...

Both proftpd and vsftpd work out of the box, with zero extra configuration.  If they don't work, then the reason is that you changed the defaults - don't do that.

All you need to do is make an account for your mother, then install proftpd or vsftpd.  Done.  Finis. 

You don't need to do anything else, really, Scout's honour.

If that doesn't work, then you have a firewall or router problem, not a FTP problem.

---

### Post by terrapin893 on 2011-04-24
FTP troubleshooting basics.  

Can you telnet to the address on port 21?  
* First try externally, if you can connect externally you should be good to go . . . I'm assuming that's not the case.  
* Next try internally (from the server).  A 'telnet localhost 21' .  If you are able to connect, that means that your FTP server is running and listening on port 21.  

If you can telnet internally but not externally you have yourself a router/network issue. 

If you are not able to telnet locally . . . the FTP service is either not running or is not listening on port 21.  If this is the case restart the ftp service, eg, /etc/init.d/proftd restart

This troubleshooting should lead you to the cause of the problem.  You need to see if the issue is with the server or with the network.

---

### Post by msandoy on 2011-04-24
I have had good results by using GADMINproftpd. In order to use it on a headless server, you have to log in with ssh -X. That gives you a graphical configuration tool.

---

### Post by Lars Noodén on 2011-04-24
You may not want FTP.

> **DonMegel said:**
> All I want to do is set up an FTP with a single user, my Mother, so that she can remote in and look at family pictures I have on the server. 


Then all you need is SFTP and it is already built into the package OpenSSH-server.  She already has a [SFTP client](http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients).  As a bonus, SFTP is secure and FTP is not.

---

### Post by Dry Lips on 2011-04-24
> **DonMegel said:**
> Thank you but it did not work. To begin with, I had no /var/www/Mother dir. Mother is the user name I created since I did not want to reuse mom and potentially have some permissions issue. 

I tired to log on anyway but to no avail I get a Connection attempt failed with "ECONNREFUSED - Connection refused by server" message. 

I have port 21 forwarded in my router.

Oops sorry! :oops: Typo in my post above:

point 5. should be 
```
sudo chown -hR yourmom /wherever/your/pictures/are
``` and **not**
sudo chown -hR yourmom /var/www/Mother [-X

If you didn't discover my typo, you wouldn't succeed at all. 
There is no /var/www/Mother dir unless you created one in step four...
If I were you, I'd try this again. If you haven't given your Mom's account
ownership over the correct dir, you wouldn't be able to log into her account.

** HermanAB:**> 
All you need to do is make an account for your mother, then install proftpd or vsftpd.  Done.  Finis. 

You don't need to do anything else, really, Scout's honour.

If that doesn't work, then you have a firewall or router problem, not a FTP problem.     Agreed! But when you have never set up an FTP server before, setting up
an user account correctly can be a bit of a pain. The tutorials out there are often
confusing and now and then even has embarrassing errors. (Such as my typo in
what I wrote above.) Even the tutorial I myself used for learning to set up FTP 
isn't accurate in all respects. I struggled quite a bit before I got all the particulars.

However, if going through the steps above still doesn't work, it isn't a FTP-problem.

---

### Post by DonMegel on 2011-04-24
Ok, changing the permissions on the Images folder did not help. When I did telnet localhost 21 I get "unable to connect to localhost, connection refused" restarting the proftpd service did not help. 

What now?

---

### Post by Dry Lips on 2011-04-24
> **DonMegel said:**
> Ok, changing the permissions on the Images folder did not help. When I did telnet localhost 21 I get "unable to connect to localhost, connection refused" restarting the proftpd service did not help. 

What now?
Well, if you followed the steps above you're not allowed to telnet at all from your mothers account. 

> 2. 
     Code:
     sudo gedit /etc/shells 
enter      Code:
     **/bin/false** 
as a single line.
proofread, save. (The logic is, there is no shell named "false")> 4. Make an useraccount:

     Code:
     sudo useradd yourmom -d /wherever/your/pictures/are -s **/bin/false** 
This is a security measure to prevent unwanted intruders gaining 
access to your server  through telnet.
 

Have you tried connecting using Filezilla? Enter the ip-address, the 
username, password, leave the port blank and click QuickConnect.
And are you sure you're using the correct ip address? And please 
mention if you tried this from your server or from another machine 
on your lan.

---

### Post by Pyro.699 on 2011-04-24
Ive always just used sftp.

run: sudo apt-get install openssh-server
type: ssh -v localhost (to ensure its running properly)
then open your ftp client:
  host: sftp://192.168.0.4 (or what ever)
  user: yourmom
  pass: password

Her home directory will be that which is set in her user profile.


This is what i use all of the time. I use FileZilla as the client

~Cody

---

### Post by DonMegel on 2011-04-24
Um, it works. It just started working. I installed the graphical user interface for ProFTPd using a VNC over SSH virtual desktop. I tried that once before and it didn't work but this time it works just fine.

I...I...don't know what to say..

Thank you guys...

---

### Post by brpylko on 2011-04-24
Okay,

1. Is your Mother on the local network?
    If so, it should be working.

2. Is your Mother on an external network?
    If so, you may have to give your server a domain name and host a website

Hope this helps!


By the way, why not use an online service like Picassa?

---

### Post by Dry Lips on 2011-04-25
> **DonMegel said:**
> Um, it works. It just started working. I installed the graphical user interface for ProFTPd using a VNC over SSH virtual desktop. I tried that once before and it didn't work but this time it works just fine.

I...I...don't know what to say..

Thank you guys...

Great!
 
 Otherwise, some of this guys have been giving you good advice. FTP is not  
 as secure as sftp. If your server will be open to the Internet, learning to 
secure it is quite important:
 
 [http://www.codeguru.com/csharp/.net/net_general/internet/article.php/c14329](http://www.codeguru.com/csharp/.net/net_general/internet/article.php/c14329)

---

### Post by ikt on 2011-04-25
.

---

