---
title: "Not LAMP but AMP?"
date: 2008-01-17
forum: Server Platforms
---

### Post by PartisanEntity on 2008-01-17
I have Ubuntu Gutsy installed on my laptop. I need to do some web development at the office, but due to the nature of the working environment, the connections and firewalls are very restrictive. So I am not able to FTP into the server where I want to create a website.

So, can I set up Apache, MySQL and PHP on my laptop and do the work here?

Anyone know of good tutorials on setting up this combo? (I have never done this before).

Thanks very much.

---

### Post by hsweet on 2008-01-17
I don't know of a tutorial but it's pretty easy.
I've done it to test a cms system at home and have installed  it at work a couple/3 times.

One option would be to install the server version of Ubuntu which I believe is a full blown LAMP install. 

Or you can install the following packages.
```
sudo apt-get install php5 php5-mysql apache2 mysql5
```

Or do the same thing with Synaptic.

That should pretty much do it as far as getting the basic system running.  You can test Apache by trying [http://localhost](http://localhost) in your browser.

Web files probably will be in /var/www

You can drop a file.php into that folder with a bit of php code to see if php is running.

Beyond that, you might want to read more about Apache configuration if you need that at their site.

---

### Post by PartisanEntity on 2008-01-17
Thanks very much for this info so far.

If I install Apache, will it by default open port 80 (or any other ports)? (I don't want it to open any ports at all).

---

### Post by koenn on 2008-01-17
look in /etc/apache2/apache2.conf for server name and ipaddress(es) and change them to localhost  and 127.0.0.1  - apache will only be accessible from your laptop

---

### Post by aks44 on 2008-01-17
Easier install method:
```
$ sudo tasksel
```then select "LAMP server"


As far as TCP ports go, yes it will open port 80 by default. You have *_no choice_*, if you want an Apache server the *_only_* way to access it is through TCP.
If you don't want it to be accessible from the outside, just use a firewall or restrict the IP binding to localhost (the firewall method is more flexible since you can more easily allow specific external connections if you need to).

---

### Post by koenn on 2008-01-17
> **aks44 said:**
> 
As far as TCP ports go, yes it will open port 80 by default. You have *_no choice_*, if you want an Apache server the *_only_* way to access it is through TCP.
And why would it be impossible to make that TCP connection to 127.0.0.1:80 ?

---

### Post by aks44 on 2008-01-17
> **koenn said:**
> And why would it be impossible to make that TCP connection to 127.0.0.1:80 ?

I never said it would be impossible. In fact I even said that one of the solutions to restrict access was to force Apache's IP binding to localhost (it's not the most flexible solution though).

I was merely answering the OP who stated that (s)he didn't "*want [Apache] to open **any** ports at all*", which is what is impossible since Apache can only communicate through TCP. Even if Apache is listening on a socket that is only bound to localhost, a port is still open (not available from the outside, mind you, but it's still an open port).


Now you can call me picky... ;)

---

### Post by Jose Catre-Vandis on 2008-01-17
> **aks44 said:**
> 
```
$ sudo tasksel
```


What a great little command!  :)

---

### Post by koenn on 2008-01-17
> **aks44 said:**
> I never said it would be impossible. In fact I even said that one of the solutions to restrict access was to force Apache's IP binding to localhost (it's not the most flexible solution though).

I was merely answering the OP who stated that (s)he didn't "*want [Apache] to open **any** ports at all*", which is what is impossible since Apache can only communicate through TCP. Even if Apache is listening on a socket that is only bound to localhost, a port is still open (not available from the outside, mind you, but it's still an open port).


Now you can call me picky... ;)
OK, I see. 
I don't think of local sockets as open ports, but a do consider e.g.port that has a service listening on it open, even if acces to that port is made impossible by lack of a route, are by a packet filter, or whatever. That's why I suggested binding to local host (no open ports by my definition) in stead of a firewall sollution (open ports with access control).

Now you can call *me* picky  :-)

---

### Post by aks44 on 2008-01-18
> **koenn said:**
> I don't think of local sockets as open ports, but a do consider e.g.port that has a service listening on it open, even if acces to that port is made impossible by lack of a route, are by a packet filter, or whatever. That's why I suggested binding to local host (no open ports by my definition) in stead of a firewall sollution (open ports with access control).Technically even local IP server sockets (in opposition to Unix sockets) open a port on the machine.

The code needed to open a local-only server socket or a world-accessible one is exactly the same, except for the second argument ("address") of the bind() call which binds the socket to one (or more) address(es)+port(s).

A socket that is exclusively bound to localhost only means that the access control is moved from a possible firewall to the entrails of the OS kernel.


> **koenn said:**
> Now you can call *me* picky  :-)Can we reach a compromise then...? :p




Damn, this has gone way off topic, but hopefully this can help the OP choosing what fits him/her best.
To sum it up: I see no relevant technical difference between the two approaches. Using a firewall is more flexible than using Apache's config file, but also a bit more complex (especially when dealing with iptables). As far as I am concerned I prefer the firewall way, but YMMV.
Pick your poison. :)

---

