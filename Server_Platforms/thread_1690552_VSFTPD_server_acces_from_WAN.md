---
title: "VSFTPD server acces from WAN"
date: 2011-02-18
forum: Server Platforms
---

### Post by WannabeFantasma on 2011-02-18
Hey all

I made a "test" server recently, put a samba + apache + vsftp server on it.

The first 2 work but the VSFTP server is troubling me.
On my lan it works.
but on a wan:
My ISP blocks port 21 so I changed it to 2200, my friend tried to connect earlier (With "ftp://myip:2200") and he had to type in a name and password, he did that (I made him an account)he got 425 failed to establish connection.

Now I Re-installed vsftpd again, did the exact same thing and now it just wouldn't connect. saying the webpage can't be found.

Question 1: What should I do to let a user acces from outside of my LAN?

I think it's because of passive mode: but I have no idea what ports I should open for passive mode? My ftp port is 2200.

FileZilla tells me.
[B]Entering passive mode
Command: List
And than that it can't find directory's[/B]

---

### Post by WannabeFantasma on 2011-02-19
Someone?

---

### Post by Shemahmforash on 2011-02-19
Hello.

Maybe what you need to do is leave the vsftpd on port21 and make the outside port change.

What I mean is, you need to have a port translation in your router from the port 2200 to the port 21. That's easily accomplished in the configurations of your router.

In that way, for someone outside your wan/lan the ftp port is 2200 and for someone in you wan/lan the port remains 21.

If you don't understand what I mean, ask me again that I'll try to explain it better.

---

### Post by WannabeFantasma on 2011-02-19
Well I can try that, hope my router has that...
Can't check it at this moment... + In the next few days I'm a "busy" man... :( 

So if my friend wants to go to my ftp server he presses [FTP://MYIP:2200](FTP://MYIP:2200) and that my router changes it to [FTP://MYIP:21?](FTP://MYIP:21?)


But he could log in, he just got a time out afterwards because it didn't respond to him(I think). So if I change ports in router you say he should be able to get further?

---

### Post by Shemahmforash on 2011-02-20
Sorry for the late reply, but I was out all afternoon yesterday.

"So if my friend wants to go to my ftp server he presses [FTP://MYIP:2200]("ftp://myip:2200/") and that my router changes it to [FTP://MYIP:21?]("ftp://myip/?")"

Yes, that is correct.

Most routers have that kind of option. Check in the configuration page of your router for port forwarding or virtual server. If you don't know how to do it, google for the name of your router and you'll find info for that.

"But he could log in, he just got a time out afterwards because it didn't respond to him(I think)."
Yes, to me it happened the same thing when I changed the port of the vsftpd and try to access it from outside my lan, so I solved this problem by using the router as I described you earlier.

P.S. If you don't want to give your friend the ip of your internet connection, you can use a dynamic dns server, such as no-ip.org, for instance.

---

### Post by Lars Noodén on 2011-02-20
If you can already connect to the machine via SSH, then you can remove FTP and use SFTP instead without having to change anything.

---

### Post by WannabeFantasma on 2011-02-20
> **Lars Noodén said:**
> If you can already connect to the machine via SSH, then you can remove FTP and use SFTP instead without having to change anything.

MM Not sure if SSH works on WAN :D will try it when my friend gets online :)



Anyway I tried Virtual server (I had it at like Public port: 2200 private port 2200)
I changed it to:
Private IP: 192.168.0.20
Public Port: 2100
Private Port: 21
tried to connect and nothing, I Re-installed VSFTPD changed everything i had changed..

This is what I get in filezilla

Antwoord:	200 Switching to Binary mode.
Commando:	PASV
Antwoord:	227 Entering Passive Mode (192,168,0,20,234,94)
Status:	Server genereerde een passief antwoord met een ontraceerbaar adres. Gebruikt het serveradres in de plaats. **(Server generated a passive answer with an untracable address. Use the serveraddres instead of it.)** (Or something) :D 
Commando:	LIST
Fout:	Verbinding verloren **(Connection Lost)**
Fout:	Ontvangen van mappenlijst is mislukt **(Failed to recieve directory)**

---

### Post by Shemahmforash on 2011-02-20
The configuration in your router seems correct!

Can you connect to the ftp from your computer?

To test the local connection, try this at the Terminal from your computer or another computer in your local area: 

```
ftp localhost
```From the outside, your friend needs to specify the port. From the Terminal it's done this way:

```
ftp YOUR-IP 2100
```Now, are you opening anonymous connections to the ftp? 

You should edit the configuration file /etc/vsftpd.conf and change at least the lines:

```
anonymous_enable=YES
```to
```
anonymous_enable=NO
```in order to block anonymous login.

And you should uncomment (remove the #) the line:

```
#local_enable=YES
```

to open connections from the users you have set in your ubuntu.

After changing the file, you must restart the server:

```
sudo /etc/init.d/vsftpd restart
```

I hope this is useful to solve your problem.

---

### Post by WannabeFantasma on 2011-02-20
> **Shemahmforash said:**
> The configuration in your router seems correct!



Did all that stuff isn't working :(
Locally everything works

My friend gets pop up with Username: Passwords: he enters them, after that, connection gets lost

Think I need to setup Passive mode or something? But i have no idea what ports to open. (ftp says entering passive mode than connection gets lost...)

---

### Post by Shemahmforash on 2011-02-21
Hello.

With the configurations with both have it worked flawlessly for me with 2 or 3 servers, so I don't know what's happening with you.

I searched in google for this particular problem and I have 2 suggestions for you to try out:

First, check this thread, that seems to discuss the particular problem you're dealing with:

[http://ubuntuforums.org/showthread.php?t=877198](http://ubuntuforums.org/showthread.php?t=877198)
In this thread, someone putted: "My problem was solved via help on the proftpd irc channel. It turns out  that this was a router problem. Many Netgear routers have a feature  enabled by default called "SPI Firewall". Disabling this feature allowed  the server to be connected to as normal."
Maybe this is what you need.

My other suggestion is, as another user suggested, for you to try to set up an ssh server instead of an ftp server and then you can connect with an ftp client using secure ftp mode.
Here's a small and simple tutorial that you can use to build a ssh server using openssh.
[http://icdif.com/computing/2010/08/11/ssh-server-in-ubuntu/](http://icdif.com/computing/2010/08/11/ssh-server-in-ubuntu/)

I'll only be back later at the end of the day, but I would like to know if any of this suggestions helped you up.

---

### Post by kg4cna on 2011-02-21
Just a shot in the dark...but it seems the connection is dropping after Filezilla switches to "passive mode".  In Filezilla, turn off passive mode and try again.  I had the same problem with passive mode causing a connect/disconnect. When I changed the mode, it started working fine.

I will also recommend you use SFTP with SSH.  Much more secure and no need to have port 21 open. On your router, make sure port 22 is open to the outside OR do like I did and use a different port number for the outside world and forward it to port 22 on the inside.

A~

---

### Post by WannabeFantasma on 2011-02-21
> **kg4cna said:**
> Just a shot in the dark...but it seems the connection is dropping after Filezilla switches to "passive mode".  In Filezilla, turn off passive mode and try again.  I had the same problem with passive mode causing a connect/disconnect. When I changed the mode, it started working fine.

I will also recommend you use SFTP with SSH.  Much more secure and no need to have port 21 open. On your router, make sure port 22 is open to the outside OR do like I did and use a different port number for the outside world and forward it to port 22 on the inside.

A~

Is that the option: Fall back to Active Mode? I get:

Status:	De server genereerde een passief antwoord met een ontraceerbaar adres. Passieve modus zijn mislukt. **(Passive modus has failed)**
Commando:	PORT 192,168,0,102,141,174
Antwoord:	500 Illegal PORT command.
Fout:	Ontvangen van mappenlijst is mislukt

> **Shemahmforash said:**
> Hello.

With the configurations with both have it worked flawlessly for me with 2 or 3 servers, so I don't know what's happening with you.

I searched in google for this particular problem and I have 2 suggestions for you to try out:

First, check this thread, that seems to discuss the particular problem you're dealing with:

[http://ubuntuforums.org/showthread.php?t=877198](http://ubuntuforums.org/showthread.php?t=877198)
In this thread, someone putted: "My problem was solved via help on the proftpd irc channel. It turns out  that this was a router problem. Many Netgear routers have a feature  enabled by default called "SPI Firewall". Disabling this feature allowed  the server to be connected to as normal."
Maybe this is what you need.

My other suggestion is, as another user suggested, for you to try to set up an ssh server instead of an ftp server and then you can connect with an ftp client using secure ftp mode.
Here's a small and simple tutorial that you can use to build a ssh server using openssh.
[http://icdif.com/computing/2010/08/11/ssh-server-in-ubuntu/](http://icdif.com/computing/2010/08/11/ssh-server-in-ubuntu/)

I'll only be back later at the end of the day, but I would like to know if any of this suggestions helped you up.

Were can i find that SPI Firewall? Can't seem to find it.

But SFTP, isn't that command line based?

In my router I found : Non-Standard FTP Port   can that help me somehow?

---

### Post by Shemahmforash on 2011-02-21
Maybe your router does't have SPI firewall, I really don't know...

About "non-standart" ftp in your router, I don't know what that stands for...

About the sftp, you can use it with any typical ftp client such as filezilla (you just need to change the server type in the combobox).

Try to install openssh with the tutorial I showed you in the other post and, after that, to connect from the outside (if you don't change the port), you just need to open the port 22 in your router. If you change the default port, you need to open that port in the router.

I recommend you, with any of the servers you install, to try to connect first from your localhost, in order to check it's all working fine. If you don't do that, when connecting from the outside, you'll be confused and don't know if the errors are from the server configuration or from the router configuration...

Good luck.

---

### Post by WannabeFantasma on 2011-02-22
> **Shemahmforash said:**
> Maybe your router does't have SPI firewall, I really don't know...

About "non-standart" ftp in your router, I don't know what that stands for...

About the sftp, you can use it with any typical ftp client such as filezilla (you just need to change the server type in the combobox).

Try to install openssh with the tutorial I showed you in the other post and, after that, to connect from the outside (if you don't change the port), you just need to open the port 22 in your router. If you change the default port, you need to open that port in the router.

I recommend you, with any of the servers you install, to try to connect first from your localhost, in order to check it's all working fine. If you don't do that, when connecting from the outside, you'll be confused and don't know if the errors are from the server configuration or from the router configuration...

Good luck.

Gonna ask my eveningschool teacher tomorrow evening...

And gonna try SFTP this evening :) hope it'll work!

---

### Post by Lars Noodén on 2011-02-22
> **WannabeFantasma said:**
> But SFTP, isn't that command line based?


As mentioned, you'll need port 22 open, but if you can connect with SSH, then that is already set.  

There are both text-based and [Clients GUI clients]("http://en.wikibooks.org/wiki/OpenSSH/Client_Applications#GUI_Clients") for SFTP.   (Disclosure: I put up the first version of that Wikibook)  FileZilla, which you already have installed, supports SFTP.  You might already have several on that list without thinking about it.

---

### Post by WannabeFantasma on 2011-02-23
Haven't got time to test it.

Probably test it tomorrow.

Edit: Well hopefully....

---

### Post by WannabeFantasma on 2011-02-24
Blah that Sftp server is way too much configuration + wtf with the private keys to set it up.... I'll just call it a day....

If only I found a good How-to for the passive mode.. I would've been ok :(

---

### Post by gobbledigook on 2011-02-24
> **WannabeFantasma said:**
> 
My friend gets pop up with Username: Passwords: he enters them, after that, connection gets lost


have you checked that the root ftp folder he is connecting to has the right permissions?

---

### Post by Shemahmforash on 2011-02-24
>  Blah that Sftp server is way too much configuration + wtf with the private keys to set it up.... I'll just call it a day.... Are you doing it correctly?

For setting up a ssh server with openssh you need just a few simple commands! It's very easy.

First you install openssh:

```
sudo apt-get install openssh-server
```Then you just need to change the /etc/ssh/sshd_config file in order to suit your needs:

Make a backup copy of it:

```
sudo cp /etc/ssh/sshd_config /etc/ssh/sshd_config.backup
```Then edit it with any editor you like and add the following line:

PubkeyAuthentication yes

Then you just need to restart the server:

```
sudo /etc/init.d/ssh restart
```

Now tell me, is this hard?

With this, you can set up a simple but effective openssh server that allows you to connect remotely to your machine.

---

### Post by WannabeFantasma on 2011-02-24
wow, the link I was following didn't show anything of that  "Pubkey" lol I'll try again when I have some time :D

> **gobbledigook said:**
> have you checked that the root ftp folder he is connecting to has the right permissions?

How can you see that? (I chmod 777 it :D )

---

### Post by WannabeFantasma on 2011-02-25
> **Shemahmforash said:**
> Are you doing it correctly?


NVM everything works! wohooow!

thanks for all the help!

He can see every directory though, need to fix that :D

---

### Post by Shemahmforash on 2011-02-26
I'm glad it all worked for you.

Good luck for the rest of your "server experiences".

---

