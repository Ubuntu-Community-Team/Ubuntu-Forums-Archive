---
title: "torrentflux/dyndns problem"
date: 2008-07-14
forum: Server Platforms
---

### Post by peterb518 on 2008-07-14
--------------------------------------------------------------------------------

Hey everyone,

As you can tell I'm new to the forums. I recently got an old computer that I decided to turn into an ubuntu server. So I've got everything up and running. Basically what I want to do with this is create a server in which I can access torrentflux anywhere. I've installed torrentflux and had it working at one point, but now every time I go to my IP nothing loads. Also, I'm trying to use a DNS from dyndns.org. That previously worked as well. I went to a friends house to show him how it worked, and when I got there I typed my address into the browser and nothing happened. I figured it might be something to do with me not being on my home network or ports not being open. So I went home and reconfigured all of that, and also set myself up with a static IP (on the network) so the port forwarding would work. Still nothing. I did not restart the server in this period either.

Also, I've got Hamachi up and running, and am wondering if there would be a better way to set this up through that, if anyone has any experience with that.


Thanks for your help.

---

### Post by osjak on 2008-07-14
peterb518, by saying "nothing happened" do you mean you got an error, or a white screen or else? Can you reach (ping) your server from outside, using DynDNS domain name?

---

### Post by peterb518 on 2008-07-14
Sorry I wasn't very specific.

I've reformatted my question: If I wanted to do what I previously stated, would it be better to have the ddclient use ham0 (hamachi) as the interface, or have it get my public IP and use that for the DNS. I am behind a router and don't know if that will complicate things.

---

### Post by peterb518 on 2008-07-14
Also: Is there a way to check if torrentflux is running? I'm fairly new at linux (I only dabbled in it a few years ago and that was with a GUI) and have no experience with apache/mysql, and i'm reading that both are needed for torrentflux. I had it working at one point--like I said--and I'm just confused why it would stop working when I didn't change any settings.

---

### Post by osjak on 2008-07-14
You can check if Torrentflux is running by pointing your server browser to "http://localhost", assuming you installed Torrentflux into web server root directory. If not, then add that directoiry to the path ("http://localhost/tf_directory_here").

I'm not familiar with hamachi, so I can not advise on it. You can do everything you specified by using DynDNS. You need to make sure your ddclient records your public IP to your DynDNS account, otherwise you will not be able to reach your server from outside. And, as you already pointed out, youe port forward needs to be set up correctly, but sounds like you have done that.

There's no need for using hamachi, you can just use your regular interface. If you have to use hamachi for some reason, then you should probably read the docs, or wait for someone with hamachi experience to answer your question.

---

### Post by peterb518 on 2008-07-15
Alright, I bring news. I can connect to torrentflux using the hamachi IP, however, localhost does nothing. I've followed instructions [here]("http://ubuntuforums.org/showthread.php?t=268985") and can't connect to localhost.

---

### Post by osjak on 2008-07-15
peterb518, please be specific when you describe an error. What does "does nothing" mean? Did you get an error?

I wonder if hamachi messed with the loopback interface. Please post the output of the following commands:

```
ifconfig
cat /etc/hosts
```

---

### Post by peterb518 on 2008-07-15
Sorry, I mean I can't connect to localhost. It displays the "Cannot find this page" in firefox. I've opened both ports 80 and 8080 and edited the apache.conf to listen on those ports.

I'm at work right now, but when I get home I'll get those outputs done.

---

### Post by peterb518 on 2008-07-15
ifconfig

```
eth0      Link encap:Ethernet  HWaddr 00:40:ca:4d:d6:44  
          inet addr:192.168.1.77  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe4d:d644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6401365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5099256 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2067626056 (1.9 GB)  TX bytes:422181120 (402.6 MB)
          Interrupt:16 Base address:0xd800 

ham0      Link encap:Ethernet  HWaddr 00:ff:41:5e:19:55  
          inet addr:5.230.43.237  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:3763 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3065 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:615991 (601.5 KB)  TX bytes:1518429 (1.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2583 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2583 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:211836 (206.8 KB)  TX bytes:211836 (206.8 KB)
```


cat /etc/hosts
```

127.0.0.1	localhost
127.0.1.1	pubuntu.roc.mn.charter.com	pubuntu

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by osjak on 2008-07-15
localhost config looks just fine. You said you tested your site in Firefox. I want to make sure you run tests from your server, not from another machine, right? Otherwise you have to access it via "http://192.168.1.77" because your other machine will have its own "localhost" and therefore would not find your site.

So you should make a port 80 forward from your router to 192.168.1.77. And make sure your virtual host listens to all IP's, not just hamachi.

---

### Post by peterb518 on 2008-07-15
I think my ISP is blocking port 80, because its clear on my router. Also I managed to set up a ventrilo server and people can connect through my public IP so I think the problem lies within the apache ports. I thought I changed it to use port 8080, but could you explain what I need to do to make sure?

---

### Post by osjak on 2008-07-15
> **peterb518 said:**
> I think my ISP is blocking port 80, because its clear on my router. Also I managed to set up a ventrilo server and people can connect through my public IP so I think the problem lies within the apache ports. I thought I changed it to use port 8080, but could you explain what I need to do to make sure?
You change the listening port in /etc/apache2/ports.conf:
```
Listen 8080
```
and change ports in your virtual host config files:

```
NameVirtualHost *:8080

<VirtualHost *:8080>
DocumentRoot /www/example1
ServerName www.example.com

# Other directives here

</VirtualHost>
```
And restart Apache after that.

---

