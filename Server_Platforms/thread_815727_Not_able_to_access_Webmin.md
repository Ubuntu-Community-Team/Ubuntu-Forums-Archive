---
title: "Not able to access Webmin"
date: 2008-06-01
forum: Server Platforms
---

### Post by rgotten on 2008-06-01
I installed ubuntu server 8.04 and Samab, then installed webmin 1.420. I am trying to access it on my networked windows computer on [https://localhost:1000/](https://localhost:1000/) but the page can not be displayed..Any ideas why?

rgotten

---

### Post by tamoneya on 2008-06-01
isnt it localhost:10000

---

### Post by windependence on 2008-06-01
Yes, the default port is 10000. You can and should change it unless you are accessing it only from within the local network.

-Tim

---

### Post by rgotten on 2008-06-02
That is what i am doing, Do i need to install anything else. like i mention i installed ubunti server 8.04, samba and webmin

Thanks

rgotten

---

### Post by windependence on 2008-06-02
Sounds like you should be good to go.

-Tim

---

### Post by tamoneya on 2008-06-02
> **rgotten said:**
> That is what i am doing, Do i need to install anything else. like i mention i installed ubunti server 8.04, samba and webmin

Thanks

rgotten

we are saying that we think you made a typo.  you said localhost:1000 when it is really localhost:10000.  You need to add one "0"

---

### Post by quelx on 2008-06-02
> **rgotten said:**
> I installed ubuntu server 8.04 and Samab, then installed webmin 1.420. I am trying to access it on my networked windows computer on [https://localhost:1000/](https://localhost:1000/) but the page can not be displayed..Any ideas why?

rgotten

Your need to point the browser on your windows machine to the ip address of the server, not *localhost* eg. [https://192.168.0.10:10000](https://192.168.0.10:10000)

---

### Post by Mauler5858 on 2008-06-02
Im having the same thing.  I can connect using the IP:10000 when on my linux partition, but when i try to access my server using hostname:10000 i cannot.  However, when on WinXP on my laptop and XP partition on the desktop, i can access it using localhost:10000.  I am using firefox for the browser in all 3 instances.

---

### Post by quelx on 2008-06-02
> **Mauler5858 said:**
> Im having the same thing.  I can connect using the IP:10000 when on my linux partition, but when i try to access my server using hostname:10000 i cannot.  However, when on WinXP on my laptop and XP partition on the desktop, i can access it using localhost:10000.  I am using firefox for the browser in all 3 instances.

An example

each of these is a different computer

**Server**(ip 192.168.1.10) **WindowsPC** **LinuxPC**

only **Server** can connect using *[https://localhost:10000](https://localhost:10000)* or *[https://127.0.0.1:10000](https://127.0.0.1:10000)* the other 2 machines can only connect using *[https://192.168.1.10:10000](https://192.168.1.10:10000)* or if DNS is setup for your home network *[https://Server:10000](https://Server:10000)*.  Remember the **s** in http**s**.  I don't have a webmin box around at the moment but I believe when you browse to *[http://192.168.1.10:10000](http://192.168.1.10:10000)* it tries to redirect you to what webmin believes the hostname is, and if dns is not setup, that is *localhost* so you get *http**s**://localhost:10000* which you well know will not work.

The moral is http**s** not http

---

### Post by Mauler5858 on 2008-06-02
I dont have an internal dns server setup in my house.  i might try setting one up tonight.

---

### Post by windependence on 2008-06-02
> **Mauler5858 said:**
> I dont have an internal dns server setup in my house.  i might try setting one up tonight.

For a small amount of computers (I'd say less than 10) you don't need a full DNS server. Just edit the hosts file of each computer and add an alias for all the computers on the network. Then they will "know" each other. Like so:


127.0.0.1   localhost
192.168.0.2  mypc
192.168.0.3  server1
192.168.0.3  server2


etc. etc.

-Tim

---

### Post by rgotten on 2008-06-02
did that it did not work

---

### Post by windependence on 2008-06-02
> **rgotten said:**
> did that it did not work

Note that you may have to reboot to read the host file depending on the OS. Also, you should put all the DNS entries in every computer, not just the one for that PC. It will work, trust me.

-Tim

---

### Post by Mauler5858 on 2008-06-02
> **windependence said:**
> For a small amount of computers (I'd say less than 10) you don't need a full DNS server. Just edit the hosts file of each computer and add an alias for all the computers on the network. Then they will "know" each other. Like so:


127.0.0.1   localhost
192.168.0.2  mypc
192.168.0.3  server1
192.168.0.3  server2


etc. etc.

-Tim

Thanks that worked like a charm!!

---

