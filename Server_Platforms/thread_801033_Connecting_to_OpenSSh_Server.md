---
title: "Connecting to OpenSSh Server"
date: 2008-05-20
forum: Server Platforms
---

### Post by hwang251 on 2008-05-20
I setup an openssh-server, and is wondering how do I connect to it?

---

### Post by davidshere on 2008-05-20
> **hwang251 said:**
> I setup an openssh-server, and is wondering how do I connect to it?

From another machine, open a terminal window and type

```
ssh username@192.168.0.0
```

and replace "username" with your username and "192.168.0.0" with the IP address of your server.

---

### Post by windependence on 2008-05-20
From the command line of the client machine:

ssh user@servername_or_IP

It will prompt you for the user's password and then you will be logged on to the server at a command prompt.

-Tim

---

### Post by davidshere on 2008-05-20
Tim and I both had the same answer ... does that answer your question?  There are many ways to connect to a machine via ssh depending on what you want to do.

---

### Post by windependence on 2008-05-20
I guess we should also add that on a Windoze machine you can use PuTTY.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

-Tim

---

### Post by hwang251 on 2008-05-20
> **davidshere said:**
> From another machine, open a terminal window and type

```
ssh username@192.168.0.0
```

and replace "username" with your username and "192.168.0.0" with the IP address of your server.

I tried it, but the the thing times out.
When you say username, do you mean a username created on the machine or hostname.

And is the address, the address next to "inet addr" when I type in ifconfig

---

### Post by windependence on 2008-05-20
> **hwang251 said:**
> I tried it, but the the thing times out.
When you say username, do you mean a username created on the machine or hostname.

And is the address, the address next to "inet addr" when I type in ifconfig

The user name would be the user you created on the server.

The IP address would be the IP address of the server you are trying to connect to.

Also, on the server run this command to start the ssh daemon:

/usr/sbin/sshd

-Tim

---

### Post by cdtech on 2008-05-20
You can see if the port is open by issuing the command:

nmap yourserverip (or your [http://server.com](http://server.com))

Could be a firewall issue, you need to allow access to that port (22).

---

### Post by hwang251 on 2008-05-20
> **windependence said:**
> The user name would be the user you created on the server.

The IP address would be the IP address of the server you are trying to connect to.

Also, on the server run this command to start the ssh daemon:

/usr/sbin/sshd

-Tim

Could you elaborate more about running that command, cause it does not seem to work, when I type that command, and I can't seem to find that folder

---

### Post by davidshere on 2008-05-20
> **cdtech said:**
> 
Could be a firewall issue, you need to allow access to that port (22).

If it were a firewall issue, wouldn't it say "connection refused" right away?

---

### Post by cdtech on 2008-05-20
are you running your server gateway as 192.168.1.1 or something along those lines?

Just run "nmap 192.168.1.1" and see if your server is listening on that port.

---

### Post by windependence on 2008-05-20
> **hwang251 said:**
> Could you elaborate more about running that command, cause it does not seem to work, when I type that command, and I can't seem to find that folder

Sorry, should be 

sudo /usr/sbin/sshd


-Tim

---

### Post by hwang251 on 2008-05-20
> **windependence said:**
> Sorry, should be 

sudo /usr/sbin/sshd


-Tim

Is anything suppose to pop or anything?

---

### Post by cdtech on 2008-05-20
> **davidshere said:**
> If it were a firewall issue, wouldn't it say "connection refused" right away?

I stand corrected.

Then the user is not using the correct ip address.

---

### Post by windependence on 2008-05-20
> **hwang251 said:**
> Is anything suppose to pop or anything?

Nope if you get no feedback that's good. :)

Now try your connection again.

-Tim

---

### Post by hwang251 on 2008-05-20
> **windependence said:**
> Nope if you get no feedback that's good. :)

Now try your connection again.

-Tim

The connection still times out

---

