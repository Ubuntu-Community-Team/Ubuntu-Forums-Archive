---
title: "How to connect Mysql with my website. Help"
date: 2011-03-15
forum: Server Platforms
---

### Post by Ferariu ANdrei on 2011-03-15
I have a webhost payed and i want to connect it with my server database.
It shows me this error on the website : Lost connection to MySQL server at 'reading initial communication packet', system error: 110

I tryed to open port 22...noone of sollution work to me..
Any help or someone who's good on that???

Thanks in advance and i appreciate your time to help me.

---

### Post by falko on 2011-03-15
Do you have shell access?

Can you post the code that you use to connect to MySQL?

---

### Post by SeijiSensei on 2011-03-15
Are the web site and the database on the same machine, or on different machines?

If you're trying to configure a web server on one IP address to talk to a remote MySQL server, that can be a complex task.  You'd need to connect to port 3306 (the port MySQL listens on, not the SSH port 22) over the Internet.  If the MySQL server is behind a firewall, you'll need to forward packets arriving on the firewall's external interface back to the MySQL server (called "[port forwarding]("http://www.portforward.org")")  A more secure option would involve something like an [OpenVPN]("http://openvpn.net/") tunnel between the MySQL server and the client web server or an [SSH tunnel]("http://www.revsys.com/writings/quicktips/ssh-tunnel.html") for port 3306.

You also need to configure MySQL to listen on another interface (eth0 or tun0 perhaps) besides localhost, the default in Ubuntu.

---

### Post by Ferariu ANdrei on 2011-03-17
If i host the website on my computer, will work to connect with the data base of the server.

But, i have the MYSQL on my PC...The website is hosted on ftp..on internet..
[www.l2roa.com](www.l2roa.com) ..To make it work i connect it to the website data base..but i need to take informations from my home database..
I have there an option with shell acces but i don't know too mutch about Shell.
For openvpn i need to pay to use that service. I never thinked that it's so hard to connect to a remote mysql...

So maybe someone can help me more?? maybe thru team viewer or don't know..
if anyone have time i will apreciate your effort.


Thx in advance.

---

### Post by BkkBonanza on 2011-03-18
We can help you but you need to provide more clear info about how you are setup and what you want to do. It's pretty vague right now. Details are important to get good instructions. 

So far your info is confusing. eg. you can't run a website on ftp. Your website sounds like it's connected to a local server database but you want it to connect to your home database. There are simple ways to do that but first you need either a ssh tunnel or to open ports and make your home computer available to the internet.

Probably the easiest secure way is to open a tunnel to the server (one command) and then config your server script to connect to that tunnel. I'm guessing here about your details but maybe like this.

On home computer,

ssh -fN -L 3306:localhost:3333 [email]user@server.com[/email]

That will create a tunnel to your server and connect port 3306 on your home machine to port 3333 on the remote server. The tunnel traffic goes over the ssh port (22).

Now you can tell your script on the server to connect to mysql on localhost port 3333. It should be able to talk via that tunnel to your home mysql server, assuming it's running on port 3306.

Note - that ssh command above creates a background tunnel process. When you want to close the tunnel you will need to kill that process. You can see it listed with the **ps afx** command.

---

### Post by Ferariu ANdrei on 2011-03-18
I did what u sayd and i get

ssh: connect to host l2roa.com port 22: Connection timed out

Any help on this??

Thx and i appreciate your time!

---

### Post by BkkBonanza on 2011-03-18
This means the server is not open on port 22 (default). Either the ssh server is not running or is on a different port, or is behind a router/firewall that needs forwarding to bypass. 

If you know it's on a different port then you can add a port option to the ssh command,

ssh -p XXXX -fN -L 3306:localhost:3333 [email]user@server.com[/email]

where XXXX is the port #. 

If you think it is on port 22 then you will have to get a normal ssh connection to work before this one will work. Have you ever connected by ssh to this server?

---

