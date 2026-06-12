---
title: "Complete Noob, Needing Help :/ Sigh"
date: 2012-01-12
forum: Server Platforms
---

### Post by Aaron053191 on 2012-01-12
Hello everyone, my name is Aaron obviously.

Today I decided I would try and turn my old desktop into a home server.

I have installed Ubuntu w/ SSH.

I am currently trying to set up the desktop under a static up and I am using a linksys router. I have looked online all day to avail....fail.

I have read through some guides and such and I am finally getting to where I am fed up with reading lol.

Can anyone help me out with some simple instruction on how to get the desktop running Ubuntu Server connected to the internet via static w/ router.

Help appreciated, thanks.

---

### Post by Buntumatic on 2012-01-12
Hello Aaron,

why desktop for a server, do you want to use it as a workstation?
If you do not like working CLI over SSH there are various web interfaces that allow you configure your server via a web browser.

---

### Post by spacecheck on 2012-01-12
You would edit your Lan connection to reflect a free address acceptable to your router and manually enter that address. You also have to add the net mask (probably 255.255.255.0 behind your router ) and you would set the router's IP address as the gateway.

Good luck!

---

### Post by rubylaser on 2012-01-12
I'll give it a shot.  First do this..

```
sudo nano /etc/network/interfaces
```

You should have an eth0 entry that looks like this...
```
auto eth0
iface eth0 inet dhcp

```

Change it to look like this..
```
auto eth0
iface eth0 inet static 
address x.x.x.x
netmask 255.255.255.0
gateway x.x.x.x
```

address is the ip address you want to use in your network's subnet, and gateway is probably that ip address of your router.

Then do this.
```
sudo ifdown eth0
sudo ifup eth0
```

Hope that helps.

---

### Post by Aaron053191 on 2012-01-12
> **rubylaser said:**
> I'll give it a shot.  First do this..

```
sudo nano /etc/network/interfaces
```

You should have an eth0 entry that looks like this...
```
auto eth0
iface eth0 inet dhcp

```

Change it to look like this..
```
auto eth0
iface eth0 inet static 
address x.x.x.x
netmask 255.255.255.0
gateway x.x.x.x
```

address is the ip address you want to use in your network's subnet, and gateway is probably that ip address of your router.

Then do this.
```
sudo ifdown eth0
sudo ifup eth0
```

Hope that helps.

That did work man, thanks!

Now I just need to play with getting Samba set up correctly. Linux is a head-ache at first!! Still is..

---

### Post by spacecheck on 2012-01-13
> **Aaron053191 said:**
> That did work man, thanks!...

Since it worked for you, you will surely want to remember to mark the thread as [Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

Have fun!

---

### Post by rubylaser on 2012-01-13
Glad you got it working :)

---

### Post by Aaron053191 on 2012-01-13
OK, next problem...

I can now type in run the ip address of the server and it load the HD folder. However, when I click to access it I get this reponse, picture below.

[IMG]http://i40.tinypic.com/517qt4.jpg[/IMG]

How can I address this issue?

---

### Post by arrrghhh on 2012-01-13
> **Aaron053191 said:**
> OK, next problem...

I can now type in run the ip address of the server and it load the HD folder. However, when I click to access it I get this reponse, picture below.

How can I address this issue?

You should mark this thread solved, and create a new thread if you have a new problem.

Using a general "complete noob need help" thread is not how these forums are supposed to operate.  You're supposed to create 1 thread per problem, and state the problem in the thread.  You should have said you have an issue with a static IP in the thread title, and closed/"solved" this thread.

With that said, check your permissions on that Samba share.  Post another thread, with things you've tried, what you've done to get where you are, what you want to achieve... etc.  Again, 1 topic per thread.  Thanks!

---

