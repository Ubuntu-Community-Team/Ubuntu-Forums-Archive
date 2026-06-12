---
title: "How Can I Open A Port?"
date: 2008-10-23
forum: Security
---

### Post by f.ben.isaac@gmail.com on 2008-10-23
I would like to open a port temporarly. I just wrote simple port scanner for practicing. It shows i have all my ports closed or blocked. I need to open a port, to see if it can catch it! If not, then my code sucks...

Can you tell me how to open a port in step by step please...

Is it a usual thing for port scanner to scan ports very fast when its done locally? cause my code scans too fast regardless what range you put...

I'm new to sockets, ports, networking stuff...

---

### Post by Circus-Killer on 2008-10-23
okay, as far as i know, you cant just randomly open a port. i think that only a service can open a port up by listening on that port. so you would essentially need a service that will listen on a specific port, for example a web server (apache) or a database server (mysql), etc.

once you have installed and running a service that listens on a port, you might need to unblock it on the firewall side. the easiest way to do this is to install FireStarter. just run:
```
sudo aptitude install firestarter
```

once it is installed, run it. there will be a section where you can edit policies. you will be able to easily add a port to allow incoming traffic to by adding it to the list. for example, if you have installed apache, you would add port 80 to the firewall incoming exception list. this will allow apache to listen on port 80 and allow the outside to request connections through that port.

hope that helps. ;)

---

### Post by sethvath on 2008-10-23
You DO NOT need to install firestarter to open a port. That is like saying you need to buy a car before you can learn to ride a bike. 

IPtables is installed by default in ubuntu, that explains the closed port system. 

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

To close port 6881 

sudo iptables -A INPUT -p tcp --dport 6881 -j DROP

---

### Post by Kevbert on 2008-10-23
You can do this via UFW which is installed by default
```
sudo ufw allow 25
```
will allow everything (tcp) through on port 25 (smtp) and 
```
sudo ufw deny 25
```
will close it. To get status of all ports use
```
sudo ufw status
```
More details on UFW can be found [[COLOR="Red"]here[/COLOR]]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw")

---

### Post by Circus-Killer on 2008-10-23
> **sethvath said:**
> You DO NOT need to install firestarter to open a port. That is like saying you need to buy a car before you can learn to ride a bike. 

IPtables is installed by default in ubuntu, that explains the closed port system. 

sudo iptables -A INPUT -p tcp --dport 6881 -j ACCEPT

To close port 6881 

sudo iptables -A INPUT -p tcp --dport 6881 -j DROP

you car/bike analogy is completely wrong. car and bike are two completely different entities that do the same job.

firestarter and iptables are NOT two completely different things that do the same job. they do NOT do the same job. firestarter is nothing more than a gui for ip tables. i only suggested it cos not everybody is an expert in using ip tables. so i figured, the easiest way to setup ip tables is with firestarter (from a beginner point of view).

secondly, your explanation for why all ports are closed is only half right. iptables might be the one reason, but ubuntu by default comes with no services listening to open ports.

by my understanding, no services listening == no open ports.

---

### Post by sethvath on 2008-10-23
> **Circus-Killer said:**
> you car/bike analogy is completely wrong. car and bike are two completely different entities that do the same job.

firestarter and iptables are NOT two completely different things that do the same job. they do NOT do the same job. firestarter is nothing more than a gui for ip tables. i only suggested it cos not everybody is an expert in using ip tables. so i figured, the easiest way to setup ip tables is with firestarter (from a beginner point of view).

secondly, your explanation for why all ports are closed is only half right. iptables might be the one reason, but ubuntu by default comes with no services listening to open ports.

by my understanding, no services listening == no open ports.

Please do not get your panties wound up in a bunch because I added that analogy. Just like you are entitled to suggest him installing firestarter I told him there is an alternative way to do it from the command line with iptables. The beauty of linux is there is often more than one solution to the problem, none of which is more correct than the other. 

The entire post was directed FOR the OP, I did not request for you to justify your reasoning for suggesting that and by you doing so I can tell you feel offended. If so my apologies. 

And re-read what I posted, I DID NOT mean to explain how the closed port system work in excruciating detail with just the line "IPtables is installed by default in ubuntu, that explains the closed port system."

If you feel obliged to debate over open/closed ports make a new thread and I will debate as long as you like after lunch in 2 hours.

---

### Post by Sarmacid on 2008-10-23
So assuming you don't have a firewall active, you can open a port with nc, but I'm not sure if it will show up in a portscan(but it should)

```
nc -l portnumber
```

Check with nmap if your scanner doesn't detect it.

---

### Post by hyper_ch on 2008-10-23
by default:

- Ubuntu has no open ports as no services are running
- when you install a service it is not being blocked
- a firewall (iptables) runs since installation time, however it has no rules and lets everything pass - and that is good
- installing firestarter will inverse the openess of iptables. This means by default no port is being blocked, by installing firestarter everything is blocked by default
- chances are that you are behind a NAT router and have already a firewall there - configure that one

---

### Post by kevdog on 2008-10-23
In a default install, all of ubuntu's ports are open by default.

You however need to install/run the service however that is going to run and listen for incoming connections.

---

### Post by koenn on 2008-10-23
> **kevdog said:**
> In a default install, all of ubuntu's ports are open by default.

You however need to install/run the service however that is going to run and listen for incoming connections.

You can use an echo server for this, it's a simple service that can listen on any port you tell it to. eg. if you have an echo server listening on port 80, that port would show up 'open' on a port scan
[http://users.telenet.be/mydotcom/program/c/echosrv.htm](http://users.telenet.be/mydotcom/program/c/echosrv.htm)

---

### Post by The Cog on 2008-10-23
My tuppence:

People use the expression "open a port" to mean two different things.

1)
An open port is a port where an application is listening for incoming connections. A closed port is one where no application is listening and any connection attempt will receive a connection refused message.

In this respect, a default Ubuntu install has all ports closed - no applications listening for incoming calls.

2)
People also refer to firewall configuration as opening or closing ports. I really think it should be called something else, like permitting or blockiing ports, to avoid confusion with 1) above.

A default Ubuntu install has iptables (the inbuilt firewall) set to permit everything, both in and out.


The easiest way I can think of to open a port is to run the command:
```
nc -l -p 1234
```
which will listen for a connection and print any received data to screen. Change 1234 to the port number required. Of course if you have installed / configured a firewall, you will have to configure that to permit the connection in (and the response out).

---

### Post by Sarmacid on 2008-10-23
Ok, so I went ahead and tested, any port you open with nc will appear as open in nmap, so that should solve your problem

```
sudo nc -l -p portnumber
```

---

### Post by f.ben.isaac@gmail.com on 2008-10-24
> **Sarmacid said:**
> Ok, so I went ahead and tested, any port you open with nc will appear as open in nmap, so that should solve your problem

```
sudo nc -l -p portnumber
```

YOU ROCK!!! :)

I LIKE THAT...

Now, which parameters do i have to use, to close it? :confused:


Hey Guys, I appreciate all your answers. It helped me understanding how things go...

THANKS:)

---

### Post by f.ben.isaac@gmail.com on 2008-10-24
I think it closes by itself..hope i'm right! cause now it shows the port as closed...

---

### Post by Sarmacid on 2008-10-24
To close it, just press ctrl + c, no need to do anything fancy there :P

---

