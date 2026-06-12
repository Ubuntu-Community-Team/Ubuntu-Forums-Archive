---
title: "ssh response very slow"
date: 2008-12-23
forum: Server Platforms
---

### Post by rilian on 2008-12-23
I have just setup ubuntu 8.10 server. Overall, its going very well. One question I have is that when I use putty for windows to ssh into the box, it comes up with a login prompt quickly but after I enter my username, the password prompt takes roughly 10 seconds to display. 

After that, things seem fine. 
Any ideas on what this delay means:confused:

Thanks,
-rilian

---

### Post by windependence on 2008-12-23
The very first time you connect there will be a delay while your machine generates a password hash. After that it should be faster. I wouldn't worry too much about slow login, but after you are in it should be fine.

-Tim

---

### Post by rilian on 2008-12-24
> The very first time you connect there will be a delay while your machine generates a password hash. After that it should be faster. I wouldn't worry too much about slow login, but after you are in it should be fine.

-Tim

Maybe I need to be more clear. I have repeated this test multiple times. This behavior is not limited to the first time I log into the box over ssh. The time now runs about 6 seconds after entering my username to when I see a password dialog. 

I ran a wireshark sniff on ssh traffic while I was testing and it showed 0 packets coming from the server during the delay. This tells me something on the server is delaying the response. 

I also tested this by ssh'ing into the ubuntu box from another linux box (running debian 3.1x). I got identical response time. 

Like I said, once I complete the login, there are no delays. This only seems to happen during the authentication session. 

Any further help or ideas would be appreciated. 
-rilian

---

### Post by windependence on 2008-12-24
The only thing I can think of is that it's taking that long to verify the password hash. That does seem a bit long. I'll post more if I think of something else.

-Tim

---

### Post by albinootje on 2008-12-24
> **rilian said:**
> 
I also tested this by ssh'ing into the ubuntu box from another linux box (running debian 3.1x). I got identical response time. 

Like I said, once I complete the login, there are no delays. This only seems to happen during the authentication session. 


Could be a name resolving issue.
Did you set up a proper hostname on the ssh-server running machine ?

---

### Post by windependence on 2008-12-24
I'm thinking if you aren't getting any packets, it may be a DNS issue. Put an entry for the machines you ssh to in your hosts file on the box you are sshing FROM. Also, make sure you have your router listed in resolv.conf if it is doing local DNS (most do) and that you have two other good DNS servers listed also. You can use 4.2.2.2 if you need a good one or use the OpenDNS servers **208.67.222.222** and **208.67.220.220**. The server will only use three entries no matter how many you put in the resolv.conf file, so I would recommend putting in your router address first and then two outside DNS servers last like I have on mine:


```
 nameserver      192.168.2.1
nameserver    205.171.2.65
nameserver      205.171.3.65
```

Restart the network after you're done.

-Tim

---

### Post by TestDummy! on 2008-12-25
You could also put

**UseDNS no**

In **/etc/ssh/sshd_config**

and then issue **sudo /etc/init.d/ssh reload**

---

### Post by lptr on 2009-01-04
> I'm thinking if you aren't getting any packets, it may be a DNS issue. Put an entry for the machines you ssh to in your hosts file on the box you are sshing FROM. Also, make sure you have your router listed in resolv.conf if it is doing local DNS (most do) and that you have two other good DNS servers listed also. You can use 4.2.2.2 if you need a good one or use the OpenDNS servers **208.67.222.222** and **208.67.220.220**. The server will only use three entries no matter how many you put in the resolv.conf file, so I would recommend putting in your router address first and then two outside DNS servers last like I have on mine:
...As I read your lines, it it was immediately clear, why we had troubles with very long login delays to FTP server, too. 

After adding the machines as static IPs to /etc/hosts all went as usually: FAST! 

Oh man! Sitting so close in front of the solution. Did not see the trees because of the wood.  Thanks dude! :D

rob*

---

### Post by windependence on 2009-01-07
No problem, sometimes I have to just walk away and have a smoke to clear my mind (what an oxymoron). When I come back to it, it seems clearer. Glad to have helped!

-Tim

---

### Post by Cracauer on 2009-01-09
Another source of these problems is inability to generate Xauthority keys. To test, try logging in with `ssh -x`.

---

### Post by NetDesignate on 2009-04-12
> **TestDummy! said:**
> You could also put

**UseDNS no**

In **/etc/ssh/sshd_config**

and then issue **sudo /etc/init.d/ssh reload**

Thank you - this is what was needed for my issue.
It is now FAST - as it should be.

Don

---

### Post by Cracauer on 2009-04-12
Fixin' the resolver config or the DNS server might have been the better alternative.

---

### Post by windependence on 2009-04-15
> **Cracauer said:**
> Fixin' the resolver config or the DNS server might have been the better alternative.

In what way? I don't recall him ever saying he had a DNS server running. In most cases, no one needs to run their own DNS unless they have a huge network. We DID fix the resolver config - in this case the hosts file and it worked. A good solution for most home or office servers.

-Tim

---

