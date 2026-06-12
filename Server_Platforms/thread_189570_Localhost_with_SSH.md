---
title: "Localhost with SSH"
date: 2006-06-05
forum: Server Platforms
---

### Post by Isoss on 2006-06-05
Hey, I have two ubuntu systems on a laptop and a PC, they are connected with ssh. Both have openssh server and apache server and I run localhost on both for my websites. Now I need to use one of them as a localhost, let's say I need to get my PC work as web server and then through the web browser on my laptop I can access the localhost on the PC, upload, develop the my php files directly over the network, and access all the websites as if connecting to the internet.

Thanks in advance.

---

### Post by jdbartlett on 2006-06-05
Well, if port 80 is open on your internal network (it usually is by default), you should be able to just type in the IP address of your server computer in the laptop's web browser, for example:

[http://192.168.0.2/](http://192.168.0.2/)

---

### Post by Isoss on 2006-06-05
didn't work! I have it on 192.168.0.20 and I have the port 80 open and nothing happened it just went error as if page not found.

---

### Post by jdbartlett on 2006-06-05
[QUOTE=Isoss]didn't work! I have it on 192.168.0.20 and I have the port 80 open and nothing happened it just went error as if page not found.[/QUOTE]That's odd. I just tried installing apache2 to a fresh Dapper install and it worked right off the bat. Could there be a firewall running in Ubuntu? Does accessing [http://localhost/](http://localhost/) from firefox on the server machine still work ok?

---

### Post by Isoss on 2006-06-05
I don't have a firewall at all, and localhost just works on both as I mentioned. it's really odd cuz everything else is running, openssh is working and I can transfere data and ssh and everything. I really need to get this done ASAP. Any clues?

---

### Post by Useless on 2006-06-05
Is the Apache service installed and running?  

try this out and see if it works afterwards.

sudo /etc/init.d/apache2 restart

---

### Post by jdbartlett on 2006-06-05
Try:```
$ gksudo "gedit /etc/apache2/ports.conf"
```If you see a line like "Listen 127.0.0.1:80", remove it, it's preventing Apache from listening for incoming connections.

Since SSH is working, you could try opening an HTTP tunnel over SSH! It's a bit silly, but if time is an issue, try this from your laptop:```
$ ssh -N root@192.168.0.20 -L 10001/127.0.0.1/80
```(Once it's connected, it won't come up with the prompt or anything, the cursor will just keep blinking and terminal will look "frozen", it's actually keeping the SSH connection open so you can tunnel through!) Now in FireFox, type:```
http://127.0.0.1:10001
```

---

### Post by Isoss on 2006-06-06
[QUOTE=jdbartlett]Try:```
$ gksudo "gedit /etc/apache2/ports.conf"
```If you see a line like "Listen 127.0.0.1:80", remove it, it's preventing Apache from listening for incoming connections.
[/QUOTE]
I opened it and found:
```
Listen 80
```

[QUOTE=jdbartlett]
Since SSH is working, you could try opening an HTTP tunnel over SSH! It's a bit silly, but if time is an issue, try this from your laptop:```
$ ssh -N root@192.168.0.20 -L 10001/127.0.0.1/80
```(Once it's connected, it won't come up with the prompt or anything, the cursor will just keep blinking and terminal will look "frozen", it's actually keeping the SSH connection open so you can tunnel through!) Now in FireFox, type:```
http://127.0.0.1:10001
```[/QUOTE]
I typed the command u suggested and it asked for the password! I entered it and it's telling me that permission denied:
```
isos@Isos_laptop:~$ ssh -N root@192.168.0.20 -L 10001/127.0.0.1/80
root@192.168.0.20's password:
Permission denied, please try again.
root@192.168.0.20's password:

```

---

### Post by jdbartlett on 2006-06-06
[QUOTE=Isoss]I opened it and found:Listen 80...
I typed the command u suggested and it asked for the password! I entered it and it's telling me that permission denied[/QUOTE]"Listen 80" is correct, it's telling apache to listen to port 80 from all interfaces. Had there been an IP address in front of the '80', that would limit apache to listening for incoming requests to port 80 from only that interface.

Not sure what's going on with your permission denied error. Are you still able to ssh into the box with a regular SSH command?```
$ ssh root@192.168.0.20
```Also, what does terminal say when you've used up your three access attempts? It'll be something like, "Permission denied (publickey,password)."

---

### Post by slakkie on 2006-06-06
try to change ssh root@localhost to youruser@localhost. 
Normally you would disable root login for ssh, check /etc/ssh/sshd_config (PermitRootLogin no)

What you could to to check wheter everything is ok is this:

0) Check wheter apache is running
```

ps -ef | grep http
# or
ps -ef | grep apache

```

If it is running:

1a) Check wheter the port is open
```

netstat -an | grep 80

```

1b) Run nmap (sudo apt-get install nmap) to check wheter the port is open
```

nmap yourhostname

```

If port 80 is open.. 

2) Telnet to your localbox to port 80
```

telnet localhost 80
GET / HTTP/1.1
Host: yourhostname
# Hit enter twice

```

This should produce some output
3) Check your apache logs (/var/log/apache2 or /var/log/httpd) to see wheter you actually connected.

If it was not running, try restarting apache (look in /etc/init.d for the correct startup script).

Happy hunting!

---

### Post by Isoss on 2006-06-13
Alright, I did all that and every thing seems to be ok.
I ran ```
telnet localhost 80
GET / HTTP/1.1
Host: yourhostname
# Hit enter twice
```
And it outputted the following:
```
HTTP/1.1 200 OK
Date: Tue, 13 Jun 2006 04:47:47 GMT
Server: Apache/2.0.55 (Ubuntu) PHP/5.1.2
Content-Length: 2400
Content-Type: text/html; charset=UTF-8

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<html>
 <head>
  <title>Index of /</title>
 </head>
 <body>
<h1>Index of /</h1>
<pre><img src="/icons/blank.gif" alt="Icon "> <a href="?C=N;O=D">Name</a>                    <a href="?C=M;O=A">Last modified</a>      <a href="?C=S;O=A">Size</a>  <a href="?C=D;O=A">Description</a><hr><img src="/icons/folder.gif" alt="[DIR]"> <a href="DHTML%20Menus/">DHTML Menus/</a>            12-Jun-2006 06:04    -
<img src="/icons/folder.gif" alt="[DIR]"> <a href="E-Books%20and%20stuff/">E-Books and stuff/</a>      12-Jun-2006 06:04    -
<img src="/icons/folder.gif" alt="[DIR]"> <a href="NOURELALAM.ORG/">NOURELALAM.ORG/</a>         12-Jun-2006 06:07    -
<img src="/icons/folder.gif" alt="[DIR]"> <a href="Tests/">Tests/</a>                  12-Jun-2006 06:08    -
<img src="/icons/folder.gif" alt="[DIR]"> <a href="Under%20Construction/">Under Construction/</a>     12-Jun-2006 06:08    - 
<img src="/icons/folder.gif" alt="[DIR]"> <a href="apache2-default/">apache2-default/</a>        29-May-2006 04:41    -
<img src="/icons/compressed.gif" alt="[CMP]"> <a href="backup-6.7.2006_07-04-36_nourel58.tar.gz">backup-6.7.2006_07-0..&gt;</a> 12-Jun-2006 06:04  710M
<img src="/icons/compressed.gif" alt="[   ]"> <a href="bible.zip">bible.zip</a>               12-Jun-2006 06:04  1.1M
<img src="/icons/unknown.gif" alt="[   ]"> <a href="calendar.php">calendar.php</a>            12-Jun-2006 06:04  1.2K
<img src="/icons/folder.gif" alt="[DIR]"> <a href="chat/">chat/</a>                   12-Jun-2006 06:04    -
<img src="/icons/folder.gif" alt="[DIR]"> <a href="daftar-anaween.com/">daftar-anaween.com/</a>     12-Jun-2006 06:04    -
<img src="/icons/folder.gif" alt="[DIR]"> <a href="diveintopython-5.4/">diveintopython-5.4/</a>     12-Jun-2006 06:04    -
<img src="/icons/folder.gif" alt="[DIR]"> <a href="libs/">libs/</a>                   12-Jun-2006 06:05    -
<img src="/icons/folder.gif" alt="[DIR]"> <a href="phpmyadmin/">phpmyadmin/</a>             08-May-2006 14:57    -
<img src="/icons/text.gif" alt="[TXT]"> <a href="test.html">test.html</a>               12-Jun-2006 06:07   16
<img src="/icons/unknown.gif" alt="[   ]"> <a href="test.php">test.php</a>                12-Jun-2006 06:07   16
<hr></pre>
<address>Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at 192.168.0.1 Port 80</address>
</body></html>
Connection closed by foreign host.
root@nourelalam:/home/admin#

```

Seems to be working! This is the index that shouold appear on the browser.

Still [http://192.168.0.1](http://192.168.0.1) is not working!!! I am going crazy ](*,)

---

### Post by Iowan on 2006-06-13
Shouldn't make any difference, but you could try:
[http://192.168.0.1:80](http://192.168.0.1:80)

---

### Post by DanielArdelian on 2006-06-14
> 
Not sure what's going on with your permission denied error. Are you still able to ssh into the box with a regular SSH command?


But it probably works with regular user accounts, not root.

Looks like the root account doesn't have a password set. Try "sudo -s -H" and then passwd to set the root password.

---

### Post by LordHunter317 on 2006-06-14
There's umm, ***Absolutely no need to set a root password.  Do not do this.  Don't even suggest it unless you know for a fact it's the only way to accomplish something (which is the case in like 0.01% of situations)*** 

Besides, ***You shouldn't be trying to SSH as root anyway.*** 

With that out of the way:
The troubleshooting here is rather appalling, and I'm having a devil of a time following it.  So confirm some details and follow these steps:[list][*]Apache does function correctly on localhost, correct?[*]It does not appear to be listening on the network.  Attempts to connect by IP to port 80 fail.  We know Apache has been commanded to listen everywhere[*]You're not running a firewall, but verify please via iptables -vL[/list]From there, we can figure out what to do next.

---

### Post by Isoss on 2006-06-15
Hi. Thank you guys for your help

But still struggling and I guess I need to wait untill my hair grows again.

I ran [http://192.168.0.1:80](http://192.168.0.1:80) and didn't work

/etc/apache2/ports.conf Shows "Listen 80" only

telnet localhost 80 is working properly

nmap 192.168.0.1 shows the 80/tcp is open

restarted apache to no avail after every try

I am using putty now to ssh to the server. I have installed ubuntu-server/LAMP on my PC with the IP 192.168.0.1 ... and everything is set right. I have SSH access as I mentioned so right now I am working on my laptop from which I need to access the [http://192.168.0.1](http://192.168.0.1) of the server which I have access to it using "linux" putty.

I tried to run ssh -N root@192.168.0.1 -L 10001/127.0.0.1/80 on the server and after entering the password I went to firefox and tried [http://127.0.0.1:10001](http://127.0.0.1:10001) and didn't work!!

I am just going crazy ... everybody is telling me that it should work and that everything seems to be ok and perfect but ... DUHH! I feel like I wanna give up!

---

### Post by jdbartlett on 2006-06-15
[QUOTE=LordHunter317]You shouldn't be trying to SSH as root.[/QUOTE]The whole SSH as root thing was my fault. It was mentioned that SSH was working and that time was of the essence, so I figured an SSH tunnel to port 80 would be a quick-fix. I used 'root' as an example username. Sorry. I know that was very naughty.

With that out the way, yes to your first two bullet points. As to your third, I believe it was said there is no firewall installed, but you're right, it's best to double check. Isoss, that code again is:```
$ sudo iptables -vL
```

Isoss, you mentioned usng PuTTY in your last post. Is the laptop running Windows? If so, OpenSSH over PuTTY may work differently and may be why the SSH tunnel failed. As I mentioned before, I only intended that to be a quick fix, so it's probably not worth worrying about.

Are there any settings on your router that could be controlling internal traffic or blocking certain ports (such as 80)? What's your router's address if the first DHCP-assigned IP is 192.168.0.1? Most routers default to .1 on the nework.

---

### Post by Isoss on 2006-06-15
Hey ... actually I am running linux on my laptop. I don't really know about routers but concerning 192.168.0.1 it was 192.168.0.20 before and didn't work as well ... I can change it and check but I am not an expert yet with ubuntu-server and the commands so would you please tell me how to change that using a command?

---

### Post by Isoss on 2006-06-15
By the way, I dunno if this is an issue but I tried restarting apache2 and it outputted the following:
```

root@server:/home/admin# /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... 
apache2: Could not determine the server's fully qualified domain name, using 192.168.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 192.168.0.1 for ServerName

```

Is that normal?

When I ran that on my laptop it was just the same but 127.0.0.1 instead of the laptop IP:
```

isos@isos-laptop:~$ sudo /etc/init.d/apache2 restart
 * Forcing reload of apache 2.0 web server... 
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName
apache2: Could not determine the server's fully qualified domain name, using 127.0.0.1 for ServerName


```

---

### Post by Isoss on 2006-06-16
Alright ... this is SILLY .. I am so happy and angry at the same time ... I am angry cuz this took so much time since I have exams but I am happy for two things:
1. IT FINNALLY WORKED! It was the browser. I went to firefox Edit->Preferences ->Connection Settings and I added 192.168.0.1 Where it says: No Proxy For: localhost, 127.0.0.1 ... 
2. I'm happy for you have taught me so much things since I am still a newbie in linux and unix commands so what you have suggested so far trying to solve my problem were precious stuff for me. Thanks a lot.

---

