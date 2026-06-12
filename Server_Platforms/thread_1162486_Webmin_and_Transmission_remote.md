---
title: "Webmin and Transmission remote"
date: 2009-05-17
forum: Server Platforms
---

### Post by Jeztastic on 2009-05-17
Hi

Neither Webmin nor transmission will allow me to access them remotely. I am sure transmission-daemon is running ok, however it tells me that my IP address is unauthorised. i have checked, and my settings.json file has not changed, the IP address is in the whitelist, and was working fine till last week. I have no idea what the webmin situation is, other than I get a connection refused message in the browser. The squeezecenter web interface works fine, as does sftp and ssh.

Any ideas?

---

### Post by hictio on 2009-05-18
What type of error message you get when you try to connect to Webmin? Is it a webmin generated error message? Like, for instance, the one it generates when you try to connect to the plain HTTP port instead of the HTTPS one?

---

### Post by Jeztastic on 2009-05-18
No it's not that.

```
Failed to Connect
  

The connection was refused when attempting to contact 192.168.1.73:10000.


Though the site seems valid, the browser was unable to establish a connection.




    *  Could the site be temporarily unavailable? Try again later.


    *  Are you unable to browse other sites?  Check the computer's network connection.


    *  Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.
```

Standard Firefox message - not connecting.

---

### Post by windependence on 2009-05-19
Most people here are using rtorrent which doesn't need a gui.

Sounds like you have a network connectivity issue. Can you access Webmin from the actual server using 127.0.0.1:10000 in the browser?

-Tim

---

### Post by Jeztastic on 2009-05-19
I've not got a gui on the server, and it's headless...

---

### Post by hictio on 2009-05-19
> **Jeztastic said:**
> I've not got a gui on the server, and it's headless...

Ok, but if you connect to it via SSH, can you issue a:

```

telnet localhost 10000 ENTER

```

```

telnet its.own.IP.address 10000 ENTER

```

Do it work?

---

### Post by Jeztastic on 2009-05-19
```
Trying 192.168.1.73...
telnet: Unable to connect to remote host: Connection refused

```

Nope...

---

### Post by hictio on 2009-05-19
> **Jeztastic said:**
> ```
Trying 192.168.1.73...
telnet: Unable to connect to remote host: Connection refused

```

Nope...

Ok, what about the test doen over the loopback interface, did it work?
Once again, these tests are to be done connected to your server, either on the console, or thru an SSH session on the same server.

Remember to add the Webmin port at the end, just like I have posted.

If neither the test over the loopback nor using the IP address of the server works, then you should check that the Webmin service is actually running on the server, and if it is, which port Webmin is using.

---

### Post by windependence on 2009-05-19
Yeah I want him to do the loopback test so we can eliminate the server as the problem.

-Tim

---

### Post by Jeztastic on 2009-05-20
```
jez@mediaserver:~$ telnet localhost 10000
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

Sorry, I tried both commands and both returned the same output. I ran the commands via a SSH session over the network. Is that what you wanted?

I have no reason to think the Webmin port has changed.

---

### Post by hictio on 2009-05-20
> **Jeztastic said:**
> ```
jez@mediaserver:~$ telnet localhost 10000
Trying 127.0.0.1...
telnet: Unable to connect to remote host: Connection refused
```

Sorry, I tried both commands and both returned the same output. I ran the commands via a SSH session over the network. Is that what you wanted?

I have no reason to think the Webmin port has changed.

Are you connecting thru SSH to the server you are having issues connecting to Webmin?
You have to run the two tests I posted on the same server you are running Webmin, that is, if you are running Webmin on server A, with IP 192.168.19.2, you have to connect thru SSH to that server, or if it has a monitor and a keyboard attached, login at the console, and then execute the tests.

---

### Post by Jeztastic on 2009-05-20
Yes, that's what I did.

---

### Post by hictio on 2009-05-20
> **Jeztastic said:**
> Yes, that's what I did.

Excelent, now that we are certain of that, can you see the webmin process running at all on your server?
Can you restart the service, just to play it safe?

---

### Post by Jeztastic on 2009-05-25
> **hictio said:**
> Excelent, now that we are certain of that, can you see the webmin process running at all on your server?
Can you restart the service, just to play it safe?

How do I look for Webmin process?

---

