---
title: "how to ssh to new server"
date: 2008-12-13
forum: Server Platforms
---

### Post by Bartee on 2008-12-13
I am very new to all of this...

I have ubuntu desktop installed which I use as my main machine 

I am trying to learn more about servers.  I install ubuntu server on a old machine I had.

The install worked.

I can ping the server local IP from my desktop.  

How can I ssh for terminal access to the new server?

I did ssh username@192.168.1.66  I get cannot access port 22.

---

### Post by hrod beraht on 2008-12-13
> **Bartee said:**
> I did ssh username@192.168.1.66

That's the way to do it.
Did you install the SSH *client* on the computer your trying to SSH *from*?

Bob

---

### Post by martien on 2008-12-13
> **Bartee said:**
> I am very new to all of this...

I have ubuntu desktop installed which I use as my main machine 

I am trying to learn more about servers.  I install ubuntu server on a old machine I had.

The install worked.

I can ping the server local IP from my desktop.  

How can I ssh for terminal access to the new server?

I did ssh username@192.168.1.66  I get cannot access port 22.
You must install openssh-server on your server and then you will be able to connect ;)

---

### Post by gypsumwolf on 2008-12-14
> **martien said:**
> You must install openssh-server on your server and then you will be able to connect ;)

I have a "xubuntu" installed on my laptop and a "ubuntu server" installed on a desktop. the ssh server is installed. The server has an encrypted file system. I have the client and Server installed on the laptop.

I tried: ssh ipaddressofserver
and it said: conection refused.

No passwords or usernames were asked for. I can ssh from my laptop into one of my friends servers somewhere in the world.

Is the server set up by default to refuse ssh connections? The "ubuntu server" system is for the most part installed "straight out of the box".

**[COLOR="Red"]EDIT: I did have the wrong IP address. LOL![/COLOR]**

---

### Post by cdtech on 2008-12-14
Check this out:
[http://www.brennan.id.au/16-Secure_Shell.html](http://www.brennan.id.au/16-Secure_Shell.html)

---

### Post by Iowan on 2008-12-14
> **gypsumwolf said:**
> 
**[COLOR="Red"]EDIT: I did have the wrong IP address. LOL![/COLOR]**Wish I could say I've never done that, but...

(SOLVED? Use THREAD TOOLS to let everyone know)

---

### Post by Bartee on 2008-12-14
> **martien said:**
> You must install openssh-server on your server and then you will be able to connect ;)

This was the answer.

BUT,  I first had to 

sudo apt-get update

to get all the parts needed for the server install be complete.

The I was able to 

ssh username@192.168.1.66 ( the server ip address )

It gave me some warning statements, but did let me log in.  This is all on my private lan network so I am not concerned with security.

Thanks for all the input.

---

