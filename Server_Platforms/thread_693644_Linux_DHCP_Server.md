---
title: "Linux DHCP Server?"
date: 2008-02-11
forum: Server Platforms
---

### Post by ocoskuner on 2008-02-11
I've set up two OS separate computer, ubuntu and windows 2000 server. I've configured DHCP server on both computer. When I try to obtain ip adress automatically, it obtains from windows at first then from linux. When I try after a while, it takes from windows again then linux after. why does my client obtain ip adress first from windows then linux? Which dhcp server is better? If anyone has tried this, I would like to know how was it. 


note: (3 computer are connected to same switch.)

---

### Post by Klunk on 2008-02-11
Why run 2 DHCP servers on the same network? I would imagine the results you see is based on whichever server responds to the broadcast request first.

I would disable one of the servers.

---

### Post by astrotech226 on 2008-02-11
I hope you are using a staggered scope where the windows machine dishes out of one range while the Linux is out of the other.

What you are doing makes sense.  I use two DHCP servers, but they are both Linux and share out of the same pool of addresses.  Your situation is a little different.  You need two if one of your servers goes down, especially if your lease times are short.

One way to help this is to add a delay to the Linux server.  Let Windows be the primary and let Linux answer if a certain amount of time has passed and the client hasn't accepted the Windows address.  Add this to your dhcpd.conf

```
min-secs 2
```

This will make the Linux server wait two seconds before giving out an address from it's pool.

As far as which one is better, Linux is :)

---

### Post by ocoskuner on 2008-02-12
I just wanted to know which gives ip adress first. Has anyone try this?
Thanks for usefull replies :)

---

### Post by astrotech226 on 2008-02-12
If the client has never had an address, the faster server usually wins.  If the client has received an address, it will ask the network if it can have the same address again.

The linux server should show you exactly what is happening in the logs.  Check in /var/log to see what is going on.

---

