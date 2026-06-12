---
title: "mySQL remote connection configuration"
date: 2013-06-26
forum: Server Platforms
---

### Post by bigmonmulgrew on 2013-06-26
Hi guys.
I have a small web server running on ubuntu 12.04
Its running Drupal so I have mySQL installed.

I'm currently writing a small application that I want to be able to write to/from the sql database. It needs to access it from multiple IP addresses that will not be static.

I'm told that commenting out bind-address: 127.0.0.1 will open my server to access form any where and this will work.

I'm concerned this is opening a huge security hole. ~Whats the correct way to do this.

---

### Post by volkswagner on 2013-06-26
This opens your DB to the world.

You should limit connections to your application.  The application should run on the server or at least the servers LAN.  This is the model for
the webserver accessing the Database, ie: the webserver is world accessible, but the database backend is not.

Perhaps you can have the roaming clients connect via VPN or ssh tunnel, which will allow for key auth.

---

### Post by bigmonmulgrew on 2013-06-26
The application is an events application used to assist running a competition event. The idea is that any results recorded locally will also appear on a website. The application needs to run without internet connection so it cant be server based. My intention it that whenever the app records the results locally it will also write them to a table on the web server to be displayed by the webpage.

I really don't like opening my DB to the world I think I'll look into sql over SSH. I already have SSH access so that makes sense.

---

### Post by volkswagner on 2013-06-26
> **bigmonmulgrew said:**
> The application is an events application used to assist running a competition event. The idea is that any results recorded locally will also appear on a website. The application needs to run without internet connection so it cant be server based. My intention it that whenever the app records the results locally it will also write them to a table on the web server to be displayed by the webpage.

I really don't like opening my DB to the world I think I'll look into sql over SSH. I already have SSH access so that makes sense.

This seems a bit contradictory (run without internet and update locally while updating the web).  I'm guessing there will be some delay between updating locally and via the website.


Anyway look into a reverse tunnel.  This will allow you to create a secure connection to the database while it appears to be local.

Something like:
```
ssh sqlUser@sqlServer -L 3306:192.168.168.1:3306
```

The above assumes the ssh server is running on port 22 and MySql is running on port 3306.  

You can make a connection to the remote database using "localhost" in your connection string, and it will use the reverse tunnel to communicate with remote server.

---

