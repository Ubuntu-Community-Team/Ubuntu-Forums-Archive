---
title: "server remote desktop"
date: 2010-04-02
forum: Server Platforms
---

### Post by Papa Oso on 2010-04-02
I have a pc running ubuntu 9.10 and another one running ubuntu 9.10 server with ubuntu desktop (im a rookie). From the machine running server Im able to log an remote manage the ubuntu machine but when i try to do it backward the server don't even appear in the menu. Im using the remote desktop viewer that came with the desktop. On the server Im using zoneminder what I can log-on and manage from the PC and also share the printer that is conected to the server. What can be happen? 

Thanks in advance.

---

### Post by guessswh0 on 2010-04-02
trust me, it can be challenging, but just take the desktop off of the server and force yourself to do it all command line.  It will take a little while longer initially, but you will learn so much more.

---

### Post by Papa Oso on 2010-04-02
> **guessswh0 said:**
> trust me, it can be challenging, but just take the desktop off of the server and force yourself to do it all command line.  It will take a little while longer initially, but you will learn so much more.

I understand, GUI is very imitating but if I can't access remotely from the pc to the server with the console will be the same. Any one with an idea what can be wrong?

---

### Post by megahost on 2010-04-02
So if you need to remotely connect to a server from  your ubuntu computer, you can always connect via SSH. You can do that by using the connect to server application under places, or with SSH in the terminal.

> 
sudo aptitude install ssh


Use the IP of the server through the shell, and it will ask for log in and password.

---

### Post by nerr on 2010-04-02
> **guessswh0 said:**
> trust me, it can be challenging, but just take the desktop off of the server and force yourself to do it all command line.  It will take a little while longer initially, but you will learn so much more.

Agreed.  Install ssh, log in, and start reading and playing around.  You'll learn quickly what works, what doesn't, and how to maintain your server.  In a day or two, given the time, you'll be confident enough to really dig in and enjoy what the command line is capable of.

---

### Post by haddog on 2010-04-03
> **Papa Oso said:**
> I have a pc running ubuntu 9.10 and another one running ubuntu 9.10 server with ubuntu desktop (im a rookie). From the machine running server Im able to log an remote manage the ubuntu machine but when i try to do it backward the server don't even appear in the menu. Im using the remote desktop viewer that came with the desktop. On the server Im using zoneminder what I can log-on and manage from the PC and also share the printer that is conected to the server. What can be happen? 

Thanks in advance.

I ssh in to my ubuntu lucid lynx 10.04 server from a command prompt using this format:

ssh user@serveripaddress

so for me it is:

ssh myubuntusrvr@192.168.1.15

you will then be asked for the user password.

btw. I typed ifconfig from a terminal prompt get the ip address for my server. I also installed xubuntu-desktop on the server, but I am going to uninstall the gui. Real men don't use a gui on their servers do they? ;-)

---

