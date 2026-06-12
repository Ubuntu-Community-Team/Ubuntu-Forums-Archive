---
title: "How do I configure Ubuntu on a virtual machine to let mysql clients talk to mysql on"
date: 2012-05-09
forum: Security
---

### Post by rtedbyers on 2012-05-09
I have created a virtual LAN, as it were, comprised on Ubuntu DT 12.04 running in virtual machines created using Oracle's software.
 
I configured the VM to use a bridged network connection, and then I configured the network connection in Ubuntu to use a fixed IP address (192.168.2.20 and 192.168.2.21). I installed MySQL and Postgres on both, as well as their client software.
 
I can ping either machine from the other, as well as a couple Windows boxes on the same LAN. I even have a virtual machine running the latest version of Suse Linux, and can ping these machines from that.
 
On either machine, I can start the client software and connect to the instance of MySQL on localhost without difficulty. However, when I try t connect to mysql on either host from any other machine on the LAN, the connection request times out.
 
I then thought that maybe there's a firewall blocking access to the databases from other machines, so I ran 'sudo ufc enable' fllowed by 'sudo ufc allow 3306', as reading resources onthe web suggested I needed to do this, but it didn't help. I still can't connect to either machine using the mysql client from any other machine. I had even created a test user within mysql that is supposed to have access from any other machine, but nothing I have tried so far has worked.
 
Please understand, I have written programs to run on unix, and I have written lots of code in SQL, C++, Perl, FORTRAN and a variety of other languages, but any kind of system administration is new to me. I even know how to sanitize and then untaint data provided by a user before submitting it to a database. But the realm of administration is a bit of a mystery to me.
 
I would like to have the DB running one one virtual machine while some number-crunching code runs on another virtual machine, but gets the data from the first.
 
Can anyone point me to a good, clear resource that a) shows e how to set up mysql so I can have a myql client on one ubuntu box talk to an instance of mysql server running on the other? And B) best practices in hardening a 'server'?
 
Thanks
 
Ted

---

### Post by Ms. Daisy on 2012-05-10
This site will get you started in securing an Ubuntu server

[http://www.andrewault.net/2010/05/17/securing-an-ubuntu-server/](http://www.andrewault.net/2010/05/17/securing-an-ubuntu-server/)

As for mysql, the manual is your friend.  It was written to explain exactly the type of thing you're looking for.  

I set up an sql server in a windows guest, and the directions are the same whether it's virtualized or not.  The only thing that would need to be configured on virtualbox is how they are networked together.  And you will find the best option in the [virtualbox manual]("http://www.virtualbox.org/manual/"). I'm not sure what your intentions are, so it's probably best for you to review the [networking options ]("http://www.virtualbox.org/manual/ch06.html")for the virtual machines and choose the best one for your situation.

---

### Post by rtedbyers on 2012-05-10
Thanks.
 
I have done this sort of thing on Windows machines, but completing the process I used on Windows was sufficient for me to be able to have a mysql client on one Windows box connect to MySQL server running on another.  Doing the same things, though, on these Linux virtual boxes was not sufficient.  That is why I suspected that I missed something in the linux firewall that was necessary to allow that connection.  I will keep looking throught he documentation, though, to see what it has to say about this...
 
Thanks
 
Ted

---

### Post by darkod on 2012-05-10
One question: If we are discussing only a private LAN, why would you need the firewall enabled on the VMs anyway? The LAN would be in a private range not routeable from the internet, and presumably behind a router/firewall.

Anyway, disabling the firewall temporarily is a quick way to see if it's standing in your way.

---

### Post by rtedbyers on 2012-05-10
> **darkod said:**
> One question: If we are discussing only a private LAN, why would you need the firewall enabled on the VMs anyway? The LAN would be in a private range not routeable from the internet, and presumably behind a router/firewall.
 
Anyway, disabling the firewall temporarily is a quick way to see if it's standing in your way.
 Practice....
 
But anyway, how do I turn the firewall on and off?

---

### Post by darkod on 2012-05-10
Well, if I'm not mistaken both the desktop version and the server version come with the firewall disabled by default.

If you enabled it, disabling it depends on how you enabled it. For example directly using iptables, or ufw, gufw, etc.

How did you enable the firewall?

---

### Post by rtedbyers on 2012-05-10
> **darkod said:**
> Well, if I'm not mistaken both the desktop version and the server version come with the firewall disabled by default.
 
If you enabled it, disabling it depends on how you enabled it. For example directly using iptables, or ufw, gufw, etc.
 
When I couldn't connect to one machine from the other, I assumed the firewall was on, so, I search the web and found info that said that to let mysql listen for connections from other machines I had to use ufw, and so based on that info I ran 'sudo ufc enable' followed by 'sudo ufc allow 3306'.  Alas, that didn't help.  Is there more than one firewall software that might be active?  If so, what can I do to determine which may be on and causing the problem.
 
I would turn off the firewall(s) for the purpose of testing the connectivity configuration of MySQL, but part of the purpose of this exdercise is to learn as I am developing code to run on linux how to do it right in a secure, reasonably hardened LAN.  I know how to write, e.g. cgi scripts that sanitize data coming from a web client and to store it safely in a DB, but I don't know the more general system/LAN hardening administration and how to write code that cooperates with it to make an overall system that is as secure as is practicable.
 
I have found a number of links to info on securing linux machines, but have scarcely begun studying them.  But to get moving quickly, I'd like to get this setup working so that I can proceed on writing good code while I am learning the rest.
 
Thanks
 
Ted
 
Thanks
 
Ted

---

### Post by darkod on 2012-05-10
ufw is just a frontend of iptables. It looked easier to me too, but later I found out that in fact iptables is not that difficult to control and configure.

If you have SSH server installed on those VMs too, you can easily confirm that ufw is enabled and working. It wouldn't let you connect with SSH unless you enable the port.

So, without enabling the port, try to connect. It should block you.

Then disable ufw with:
sudo ufw disable

Try SSH and it should let you in.

By default ufw would configure all basic functions of the firewall, so if you allowed the correct port for mysql, ufw is not your problem.

You can always check ufw status and configured rules with:
sudo ufw status

---

### Post by rtedbyers on 2012-05-10
> **darkod said:**
> ufw is just a frontend of iptables. It looked easier to me too, but later I found out that in fact iptables is not that difficult to control and configure.
 
If you have SSH server installed on those VMs too, you can easily confirm that ufw is enabled and working. It wouldn't let you connect with SSH unless you enable the port.
 
So, without enabling the port, try to connect. It should block you.
 
Then disable ufw with:
sudo ufw disable
 
Try SSH and it should let you in.
 
By default ufw would configure all basic functions of the firewall, so if you allowed the correct port for mysql, ufw is not your problem.
 
You can always check ufw status and configured rules with:
sudo ufw status
 
OK, I installed SSH server, and by turns turned ufw off and on, and by trns was able to connct using ssh or not (I don't know what port ssh uses, so I am not sure what port to open for it.  But, worse, at no time during this process was I able to connect to the mysql server from the client machine 9except with logged into the  'server' using ssh.  What else could it be?  Possibly something I missed in configuring mysql that wasn't necessary on WIndows?  I have more reading to do.  While I have done just enough MySQL administration to let me write my programs, much of that administration seems rather mysterious.
 
Anyway, on the Suse VM I'd set up, there is a port scanner, so I think I'll turn off any firewall on the Ubuntu box and see what ports it appears to have open (I haven't found the corresponding tool for ubuntu.  And Netstat, being a commandline tool, is a bit cumbersome.
 
Thanks
 
Ted

---

### Post by darkod on 2012-05-10
The default SSH port is 22.

But it's best practice to change it anyway, especially if you are practicing for a production server that will be on the internet tomorrow.

The port setting and other option for SSH are in /etc/ssh/sshd_config if I'm not mistaken (maybe it was sshd.config).

---

### Post by CharlesA on 2012-05-10
> **darkod said:**
> The default SSH port is 22.

But it's best practice to change it anyway, especially if you are practicing for a production server that will be on the internet tomorrow.

The port setting and other option for SSH are in /etc/ssh/sshd_config if I'm not mistaken (maybe it was sshd.config).

Changing the port SSH runs on does little for security. It does help with log chatter tho.

The config file for sshd is:
/etc/ssh/sshd_config

---

### Post by rtedbyers on 2012-05-10
> **darkod said:**
> The default SSH port is 22.
 
But it's best practice to change it anyway, especially if you are practicing for a production server that will be on the internet tomorrow.
 
The port setting and other option for SSH are in /etc/ssh/sshd_config if I'm not mistaken (maybe it was sshd.config).
 
thanks loads.
 
I finally found what the problem was.  When I last configured MySQL, and this was on a Windows 7 box, there was a skip-networking flag I could set to false in order to have it listen for connections from other machines.  Now, there is a bind-address that has to be disabled in order for networking to be enabled; that was new to me, and not something I'd encountered in the docs I'd read (which may be a question of their vintage).
 
Thanks again
 
Ted

---

