---
title: "ssh administration questions"
date: 2006-09-04
forum: Server Platforms
---

### Post by arkangel on 2006-09-04
Hi
I am using ssh server to access my computer remotely, for that i created a new user:

1) Apparently I can only access remotely  to my computer from another computer , to which i connected via ssh previously (me as client)
How can access my computer from any other IP ? How can tell ssh server which  IP i can trust i.e specific IPs are allowed to reach my computer via ssh ?

2)  I tried to do a sudo with  my new user , of course it didnt work, i got the message 
"_user_ is not in the sudoers file.  This incident will be reported."
i want to know, reported where or how?

Thanks

---

### Post by Slychilde on 2006-09-04
Greetings arkangel,

All you should need to do is type ssh username@ipaddress in a terminal and it should ask for the password you set for that account.

So, let's say you installed ubuntu server and your login is arkangel, and the ip of the host is set to 192.168.1.101, you would type:

ssh arkangel@192.168.1.101

Best of luck, I hope that helps.

---

### Post by Jussi Kukkonen on 2006-09-04
> Apparently I can only access remotely to my computer from another computer , to which i connected via ssh previously (me as client). 
How can access my computer from any other IP ? 

I believe you are mistaken. I don't know of a connection between these things. What response do you get from the server?

> How can tell ssh server which IP i can trust i.e specific IPs are allowed to reach my computer via ssh ?
Look at */etc/hosts.allow* and *hosts.deny*. I don't remember the format, but you'll want to deny all ssh traffic and then allow ssh from certain hosts. Be aware that this is not really secure, as ip spoofing is not that difficult -- allowing only public key authentication is a lot safer, if you will only connect from known machines...
 
> i want to know, reported where or how
By default, it just ends up in the logs. At least /var/log/auth.log

---

### Post by arkangel on 2006-09-04
thanks for your answer, i understood i didnt ask clearly . I will try to describe what i want to do 

1)
lets assume my IP is  1.2.3.4 (my laptop)

A friend of mine wants to share files with me  or hack me   
her IP is  10.10.10.10
her user name is lady (on my computer)

I have  access to a sun sever whose IP is  3.3.3.3  
my user there is john, and lady has also access to this server (her user name  in sun server is the same as my computer )

when lady uses: ssh  lady@1.2.3.4  from her computer , she cannot connect 

some time ago i used ssh to connect to the sun server 
ssh john@3.3.3.3 (worked fine )
 

lady connects to the sun server , so she types 
ssh lady@3.3.3.3 
when she is in  she can successfully do 
ssh lady@1.2.3.4 , so she has access to my laptop through the sun server

i wonder how she can access my laptop from her  location whose IP is 10.10.10.10 

-NO SURE- Wanna know?  since i connected  to this sun server previosly somehow its IP was recorded  on a "ssh_knows_this_ip_LIST"  ?
when I used ssh john@3.3.3.3 the first time  , I got a public key  
If such a list or tool exist i an want to add
-her IP: 10.10.10.10
-accept all IP 


2)if lady is in  (on my laptop through the sun server ) she  naively  does
sudo rm -r / 
lady is not in the sudoers file. This incident will be reported.

i want to know, reported where or how?

sorry for the long long question

---

### Post by arkangel on 2006-09-04
> **Jussi Kukkonen said:**
> I believe you are mistaken. I don't know of a connection between these things. What response do you get from the server?


Look at */etc/hosts.allow* and *hosts.deny*. I don't remember the format, but you'll want to deny all ssh traffic and then allow ssh from certain hosts. Be aware that this is not really secure, as ip spoofing is not that difficult -- allowing only public key authentication is a lot safer, if you will only connect from known machines...
 

By default, it just ends up in the logs. At least /var/log/auth.log

question  2 answered  :)  thanks it is indeed in /var/log...

host.allow  and host.deny empty   but i have something to start :)

---

### Post by Jussi Kukkonen on 2006-09-04
> 
-NO SURE- Wanna know? since i connected to this sun server previosly somehow its IP was recorded on a "ssh_knows_this_ip_LIST" ?

Like I said I don't see how these things could be related... The server key gets added to your *known_hosts* list when you login to a remote server, but that  has absolutely no relation to a server running on your computer.


Can lady ping your machine from 10.10.10.10?
Please paste the actual response lady gets when she tries to *ssh 1.2.3.4*?

---

### Post by arkangel on 2006-09-04
No she cannot ping my computer from her location : time out error 

ssh lady@1.2.3.4 
any response, the cursor only blinks

---

### Post by Jussi Kukkonen on 2006-09-04
> **arkangel said:**
> No she cannot ping my computer from her location : time out error 

ssh lady@1.2.3.4 
any response, the cursor only blinks
no ping means that this is not a ssh problem, but a more general one. I'm just fishing here, but... Could you have a firewall running? Or maybe you are in a different subnet?

---

### Post by arkangel on 2006-09-04
ah  ok i got it  , she is in another subnet,(she is using one  private proveider  while i have another )  when i meant remotely that is exactly what  i wanted to say, :) 


is there any way someone can connect from any computer , i mean any other computer (in china lets say ) to my laptop ?  maybe it is a stupid question

---

### Post by gruepig on 2006-09-05
This could be caused by any number of things:

* You are having an ssh version mismatch (for example, your server is allowing only ssh2 connecctions and the client machine is trying to connect with ssh1). 
* Your ssh server is only accepting connections from IPs which have valid reverse DNS and the client machine doesn't (ALL: PARANOID in /etc/hosts.deny). 
* You have a firewall installed, or are otherwise controlling access with tcpwrappers (/etc/hosts.deny) or the sshd config file (/etc/ssh/sshd_config). 
* Something besides your server is preventing the connection (either the client machine itself or a router/firewall in between).
* Etc, etc.

In short, there are two many possibilities to know.  Fortunately, there are a few things you can do to gain more information.  Try any/all of these and post the results: 
  
* From the client machine,  try to connect with ssh in verbose mode and see where there is a failure.  If the client machine is another Linux box, run 'ssh -vvv  username@hostname' (for the appropriate username and hostname of your server).  Other ssh clients may have other ways to provide debugging information.
* From the client machine, run 'telnet hostname 22' (where hostname is the hostname of your server).  Port 22 is the typical ssh server port, so this will tell you whether the client machine can connect to the server on the right port. 
* Try to connect from some other machine.  See what happens.

---

### Post by Jussi Kukkonen on 2006-09-05
[QUOTE=gruepig]This could be caused by any number of things:[/QUOTE]

Huh? From reading the posts I'd say it's caused by exactly one -- they're not in the same networks and his server is not visible to the the outside.
[QUOTE=arkangel]is there any way someone can connect from any computer , i mean any other computer (in china lets say ) to my laptop ?[/QUOTE]

Sure, I have that kind of setup at home. If you have a router, you need to make it forward the ssh port (usually 22) traffic to your computer. If you are in a corporate environment you will have to ask your network administrator -- be warned though that competent sysadmins generally won't allow external access to machines they don't control... 

After that you need to know the external ip address lady should be using -- If the common subnet you are in is the internet, use e.g. [www.whatsmyip.org](www.whatsmyip.org) to find it out. 

If your ISP gives you a dynamic ip, that external ip might change in the future though. You'll need to use a dyndns-service to overcome that, but that's another story...

EDIT: one more thing: if you connect your ssh server to the internet wilderness for the first time. please make sure your configuration is secure -- sooner or later you will be targeted by script kiddies with at least dictionary login attempts (only allowing public key logins goes a long way).

---

### Post by sysops on 2006-09-05
Beware of using public IP addresses on local networks. If your IP address isnt on one of the RFC 1918 addresses, then other clients attempting to connect to you will be forwarded on to the real destinations and not yours which could explain the ssh client doing nothing.

Make sure

1. The a proper route to or an alternative means to get to the desintation network exists.

2. No firewalls or other administrative measures are in place prohibiting the connection

3. Make sure the SSHD daemon is listening on INADDR_ANY address (0.0.0.0) as opposed to something local (127.0.0.1 or 192.168.0.1)and that clients can access it.

4. Turn on verbosity/debugging with ssh -v .. should give you hints as to whats failing.

---

### Post by gruepig on 2006-09-05
> **Jussi Kukkonen said:**
> Huh? From reading the posts I'd say it's caused by exactly one -- they're not in the same networks and his server is not visible to the the outside.

Very, very likely, yes.  

However, there are other things which could cause this.  Or, even if that's true, there could be additional problems.  I was trying to introduce some general debugging skills, namely, use whatever debugging the application you are using has available and seeing if the tcp port is open and responding appropriately.  Someone already mentioned ping and checking for firewall rules, which are good troubleshooting techniques.  Other things I've found to be useful include checking the logs and running tcpdump.

---

