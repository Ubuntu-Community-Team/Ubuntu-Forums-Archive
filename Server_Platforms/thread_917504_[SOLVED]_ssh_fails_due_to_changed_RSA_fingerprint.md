---
title: "[SOLVED] ssh fails due to changed RSA fingerprint"
date: 2008-09-12
forum: Server Platforms
---

### Post by Pro-reason on 2008-09-12
I have been happily using *ssh* to log on to another computer for some time.

Now, suddenly, it doesn't work.  I tried to connect as usual, and I got a message saying that the fingerprint of the host had changed.  I had to delete my *~/.ssh/known_hosts* file.

If I now try to connect, it first asks me whether I trust the authenticity of the host.  I say yes, and then it lets me enter the password.  However, it always rejects the password.

I get the same thing if I go to the other computer and try to connect to my own.

Why has this happened?

---

### Post by Sef on 2008-09-12
moved to server platforms.

---

### Post by cpetercarter on 2008-09-12
The problem probably lies in the computer you are trying to log into. Perhaps the username or password has been changed, or the owner has changed the sshd configuration file to permit access only by certain users, or in some other way.

---

### Post by Pro-reason on 2008-09-12
> **cpetercarter said:**
> The problem probably lies in the computer you are trying to log into. Perhaps the username or password has been changed, or the owner has changed the sshd configuration file to permit access only by certain users, or in some other way.

No, that's not it.

---

### Post by jerome1232 on 2008-09-12
Generally if the RSA fingerprint changes and there's no reason for the server to have regenerated it's keys; Your not connecting to the machine you think you are.

I'm immediately suspicious of some sort of man in the middle attack.

I don't know how to go about finding out more though

---

### Post by Pro-reason on 2008-09-12
Our ADSL modem/router is connected to the internet, and provides a local network.  Its local IP address is 10.1.1.1.  

This computer is 10.1.1.2.  The other computer is 10.1.1.3.

Each computer runs Hardy, and has one account on each. I know the passwords for both.

The command &#8220;ssh erin@10.1.1.3&#8221; used to work.

---

### Post by cariboo on 2008-09-12
Can you log on to the computer itself, that is if you've got a keyboard and monitor hooked up to it?

Jim

---

### Post by Pro-reason on 2008-09-12
> **cariboo907 said:**
> Can you log on to the computer itself, that is if you've got a keyboard and monitor hooked up to it?

Jim

Of course.

---

### Post by windependence on 2008-09-12
> **jerome1232 said:**
> Generally if the RSA fingerprint changes and there's no reason for the server to have regenerated it's keys; Your not connecting to the machine you think you are.

I'm immediately suspicious of some sort of man in the middle attack.

I don't know how to go about finding out more though

I'd think more like his IP is not static and when he logs in with the new DHCP address, ssh does not recognize the machine or associates it with another machine that was allocated that address at another time.

-Tim

---

### Post by Pro-reason on 2008-09-12
> **windependence said:**
> I'd think more like his IP is not static and when he logs in with the new DHCP address, ssh does not recognize the machine or associates it with another machine that was allocated that address at another time.

-Tim

The IP address that our ISP assigns us is dynamic, but on this side of the router the IP addresses are stable: 10.1.1.1, 10.1.1.2, and 10.1.1.3.

Would the external address make any difference?

---

### Post by windependence on 2008-09-12
No, I was referring to your internal IP, so if that is static, then I'm barking up the wrong tree. ;)

> If I now try to connect, it first asks me whether I trust the authenticity of the host

This is standard behavior the first time you log in without a key having been created.

Go to the actual machine you are trying to log on to, open a terminal and do this:

```
sudo ssh 127.0.0.1
```
If you can log on that way, your server is OK and it MAY be a man in the middle attack.

Let us know what happens.

-Tim

---

### Post by Pro-reason on 2008-09-12
Logging on to 127.0.0.1 succeeds on either machine, but logging on to 10.1.1.2 (on mine) or 10.1.1.3 (on the other), which should be the same as 127.0.0.1, fails.

And yet, I can use those IP addresses, or the hostnames, to ping either computer from the other.  The /etc/hosts file is the same as before.

The only thing that I can think of that has changed since the last time this worked, is that I have updated a few packages, as I do from time to time.

---

### Post by windependence on 2008-09-12
OK, I guess i should explain what we are doing here. When you log on to 127.0.0.1, you are logging on to that particular machine through it's "loopback" interface. It's kinda like a short circuit to make applications think they are actually going through the network. The reason I had you do that of course is that if you can do that on the box you want to get in to remotely, then your passwords and most everything else on that box are OK and it has to be something between your server and the box you are logging in FROM. In this case, it's not useful to log in to the loopback on the client machine because you are actually going nowhere, just logging on to the local host.

The actual IP 10.1.1.2 is not the same as the loopback address.

what is the output of 

```
sudo ifconfig
```

-Tim

---

### Post by Pro-reason on 2008-09-12
> **windependence said:**
> 
what is the output of 

```
sudo ifconfig
```

-Tim
```
eth0      Link encap:Ethernet  HWaddr 00:1a:4d:6e:66:a4  
          inet **addr:10.1.1.3**  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21a:4dff:fe6e:66a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:316010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:198281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:419468178 (400.0 MB)  TX bytes:17706313 (16.8 MB)
          Interrupt:220 

eth1      Link encap:Ethernet  HWaddr 00:48:54:88:93:68  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0xa000 

eth1:avahi Link encap:Ethernet  HWaddr 00:48:54:88:93:68  
          inet addr:169.254.6.221  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1963 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1963 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:145372 (141.9 KB)  TX bytes:145372 (141.9 KB)

```

Why does it say 10.1.1.3?  This machine is 10.1.1.2!

Edit: and the other machine says 10.1.1.2, when it is 10.1.1.3!  How could they have swapped around??

Edit: I've just gone into the router preferences (by visiting 10.1.1.1 in a browser) and verified that the IP address 10.1.1.2 is still assigned to the hostname of this machine, and 10.1.1.3 is still assigned to the hostname of the other machine.  The /etc/hosts file on both computers also correctly matches these IP addresses with the appropriate hostnames, as they always have.

---

### Post by windependence on 2008-09-12
You'll have to make sure the address you have for the hostname in their /etc/hosts file matches what their IP address is. If you need to change their IPs do you know how to do that? I assume you do. ;)

Also, are you sure you are plugged in to the correct ethernet port? What is that virtual avahi interface? That is pulling a 169 address and that is not good if you need that interface working. I think that is probably your problem.

-Tim

---

### Post by Pro-reason on 2008-09-12
ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:1a:4d:6e:66:a4  
          inet addr:**10.1.1.2**  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21a:4dff:fe6e:66a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2668 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2333968 (2.2 MB)  TX bytes:350238 (342.0 KB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2685 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2685 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:153690 (150.0 KB)  TX bytes:153690 (150.0 KB)

```

I actually had two ethernet cards (onboard and PCI) on this machine.  I've pulled one of them out to simplify matters.  I haven't used it for about a year anyway.  That seems to have magically removed the avahi thing that had put itself there somehow.

Looking at my internet settings in the GNOME control centre, I can see that you were right about the dynamic IP thing.  It was indeed set up to use DHCP rather than a static address.  DHCP had provided the correct address for so long that I'd forgotten that it wasn't actually static.  When it decided one day to swap the IP addresses around, I got confused.

I have now set up both machines to use static IP addresses, which correspond both to the settings inside the router and to the settings in /etc/hosts.

After flushing out *~/.ssh/known_hosts*, I can now use *ssh* without problems, from either machine to either machine.

Thank you for your help.

---

### Post by windependence on 2008-09-12
You're welcome. Glad to help. 

-Tim

---

