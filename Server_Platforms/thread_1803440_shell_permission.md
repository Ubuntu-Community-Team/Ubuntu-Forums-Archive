---
title: "shell permission"
date: 2011-07-13
forum: Server Platforms
---

### Post by kirthi on 2011-07-13
I am using Ubuntu 10.04 lucid lynx. Is it possible for others to access my system's login through the shell if they know the host of my system? If yes, I want to know how. And should I give permissions for them to access my system. 
 Thanks in Advance.

---

### Post by yota on 2011-07-13
SSH is the swiss army knife for remote login to a machine.

Start from [here]("https://help.ubuntu.com/community/SSH").

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> I am using Ubuntu 10.04 lucid lynx. Is it possible for others to access my system's login through the shell if they know the host of my system? If yes, I want to know how. And should I give permissions for them to access my system. 
 Thanks in Advance.

I think you should start from the top.  Do you want for people to access your system?

---

### Post by CharlesA on 2011-07-13
> **karlson said:**
> I think you should start from the top.  Do you want for people to access your system?

This ^. Also, note that installing SSH while having a weak password is one of the best ways to get your box cracked.

---

### Post by dozycat on 2011-07-13
I will add are you inside a network behind a nat with ip public?

---

### Post by conradin on 2011-07-13
I take it you want to prevent poeple from getting in.
first step would be to configure the firewall, and my yourself invisible,
by dropping packets unsolicited. 
[https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

---

### Post by kirthi on 2011-07-13
I want to know if linux can give the permission for others to access my system if they know my host through any commands in terminal.

---

### Post by CharlesA on 2011-07-13
> **kirthi said:**
> I want to know if linux can give the permission for others to access my system if they know my host through any commands in terminal.

They'd need to know your username and password to get in.

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> I want to know if linux can give the permission for others to access my system if they know my host through any commands in terminal.

> **CharlesA said:**
> They'd need to know your username and password to get in.

Depends on what is configured and how it is configured and what type of access you want to prevent.

For remote access most commonly used now is:

SSH

You also have:

RSH
RLOGIN
TELNET

There are some more obscure that I won't mention, but again you need to specify what is it that you want to let the users do or prevent them from doing.

Any computer connected to the network is at risk.  Can this be minimized? Absolutely.

---

### Post by kirthi on 2011-07-13
I want to know if something can be done to access my system by others.
Using ssh by knowing my host can they access my system. If they can do that will they be able to handle my system without my permission.

---

### Post by CharlesA on 2011-07-13
> **kirthi said:**
> I want to know if something can be done to access my system by others.
Using ssh by knowing my host can they access my system. If they can do that will they be able to handle my system without my permission.
You will need to be more specific as to what you want to know.

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> I want to know if something can be done to access my system by others.
Using ssh by knowing my host can they access my system. If they can do that will they be able to handle my system without my permission.

Simple solution:

Remove all services like SSH/RSH/TELNET/NFS/APACHE/CUPS, that way people cannot have remote access to your system if that is what you are trying to do because you are still not making yourself clear.

If you want to allow someone to access your system you might want to install and configure the services I have mentioned above

---

### Post by kirthi on 2011-07-13
Hey I am planning to do a project with this concept related to mysql connection and ssh server. So I want to know is there any way to get connected to other's system. Through ssh server or any other server could I connect myself to others.  If I get connected what is all that I can do. Is it possible for me to access that system completely.

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> Hey I am planning to do a project with this concept related to mysql connection and ssh server. So I want to know is there any way to get connected to other's system. Through ssh server or any other server could I connect myself to others.  If I get connected what is all that I can do. Is it possible for me to access that system completely.

Much better.

If you need to set up the MySQL server you will need root access initially so SSH for remote access at least on initial stages would be needed as well as sudo access at least to set up the MySQL.

---

### Post by kirthi on 2011-07-13
I have a doubt. Generally with the terminal what are all the applications we can do. And if others can access my system will they be able to do all the stuff which I can do?

---

### Post by kirthi on 2011-07-13
Yeah I must know all those. But does the linux commands give permission to access other's system.

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> I have a doubt. Generally with the terminal what are all the applications we can do. And if others can access my system will they be able to do all the stuff which I can do?

The applications you can launch via a GUI you can launch the same application via a command line in a shell.  I think you may want to start from [here](http://heather.cs.ucdavis.edu/~matloff/unix.html).

But you may want to look at other ones [from here](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=unix+tutorial).

Can people do the same stuff you can do if they log on to your system if they have the same or higher level privileges the answer is yes.

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> Yeah I must know all those. But does the linux commands give permission to access other's system.

You should not confuse the two.  Permission or rather permissions of what you can do are not defined by the command you run but by the configuration of the command you run or by your effective User ID or group id's you are assigned to.

---

### Post by kirthi on 2011-07-13
> **karlson said:**
> The applications you can launch via a GUI you can launch the same application via a command line in a shell.  I think you may want to start from [here](http://heather.cs.ucdavis.edu/~matloff/unix.html).

But you may want to look at other ones [from here](http://www.google.com/search?sourceid=chrome&ie=UTF-8&q=unix+tutorial).

Can people do the same stuff you can do if they log on to your system if they have the same or higher level privileges the answer is yes.

So now I can have the privileges to access others system. Is there any way to restrict the user to some extent.

---

### Post by kirthi on 2011-07-13
> **karlson said:**
> You should not confuse the two.  Permission or rather permissions of what you can do are not defined by the command you run but by the configuration of the command you run or by your effective User ID or group id's you are assigned to.

I  am not clear with what you said. Can you make me understand.

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> So now I can have the privileges to access others system. Is there any way to restrict the user to some extent.

If you were given these privileges then yes.

There is absolutely a way to restrict them.

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> I  am not clear with what you said. Can you make me understand.

The permissions of what files you are able to access are specified by permissions set on the directories and files on the system you are logged into.

This could also restrict the set of commands you can execute based on the shell that is configured for you on the system, but I think you should really start with UNIX tutorials to understand what it is I am referring to.

---

### Post by kirthi on 2011-07-13
> **karlson said:**
> If you were given these privileges then yes.

There is absolutely a way to restrict them.

What all can be restricted. And how?

---

### Post by kirthi on 2011-07-13
> **karlson said:**
> The permissions of what files you are able to access are specified by permissions set on the directories and files on the system you are logged into.

This could also restrict the set of commands you can execute based on the shell that is configured for you on the system, but I think you should really start with UNIX tutorials to understand what it is I am referring to.

So I can restrict few commands in my system. Have this been already existing?

---

### Post by karlson on 2011-07-13
> **kirthi said:**
> What all can be restricted. And how?

> **kirthi said:**
> So I can restrict few commands in my system. Have this been already existing?

Start from [here](https://help.ubuntu.com/)

---

