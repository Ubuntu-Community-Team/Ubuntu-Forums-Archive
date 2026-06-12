---
title: "[SOLVED] SSH Remote connection problem"
date: 2008-08-05
forum: Server Platforms
---

### Post by colskinet on 2008-08-05
Hi all

LAN IP 192.168.1.200
WAN IP 212.159.x.x
Router 192.168.1.254

I have installed Ubuntu 8.04 on a machine that I wish to open up to the internet to serve web pages, and I also wish to access this machine from my work machine using SSH.

I have installed SSH on it and can access it using my laptop internally on my home network. All works fine.

I have opened up port 22 on my router and a friend could connect to it from his machine, but we encountered a problem when trying to login. It asks for my username - I put in "username", it then asks for "username@domain.co.uk's password" - whatever I put in it won't accept!

When I added this rule on the router, it informed me that it was moving the routers SSH port to 2222.

The Ubuntu PC will be hosting a web domain ([www.domain.co.uk](www.domain.co.uk) for example) out to the internet - is there anything else I need to configure on the PC side?

I temporarily allowed root to login using SSH but this also failed as it appears to be adding on the FQDN to the username when trying to connect externally!


How do I get around this? This is my first attempt at setting up a Linux server and don't want to be beaten! Sure it's something I haven't done, so feel free to call me stupid!

Thanks in advance for any help.

Colin

---

### Post by ChumleyEX on 2008-08-05
try changing the port and see what happens.

---

### Post by djxcon on 2008-08-05
> I have opened up port 22 on my router and a friend could connect to it from his machine, but we encountered a problem when trying to login. It asks for my username - I put in "username", it then asks for "username@domain.co.uk's password" - whatever I put in it won't accept!

What is the error message? 

Also, you definitely want to make sure port 22 on the router is forwarding to 192.168.1.200.

What OS is your friend's computer running?

---

### Post by colskinet on 2008-08-05
> **ChumleyEX said:**
> try changing the port and see what happens.

Will try that tonight and post back..

Thanks
Colin

---

### Post by colskinet on 2008-08-05
> **djxcon said:**
> What is the error message? 

Also, you definitely want to make sure port 22 on the router is forwarding to 192.168.1.200.

What OS is your friend's computer running?

Port 22 is definitely forwarding to 192.168.1.200.

As for the error message, it is just saying "access denied" - I assume this is because it is looking for the username "user@domain.co.uk" instead of just "user"..

My friends PC is running XP and we can access the SSH PC fine, just not authenticate due to this weird username issue!

Many thanks
Colin

---

### Post by Archmage on 2008-08-05
Try starting ssh with the -l username flag. E.g.

[code]ssh 192.168.0.1 -l username[code]

---

### Post by djxcon on 2008-08-05
On the XP box, you can just run Putty and specify the port and IP. At that point, the router will prompt you for the username.

---

### Post by colskinet on 2008-08-05
> **djxcon said:**
> On the XP box, you can just run Putty and specify the port and IP. At that point, the router will prompt you for the username.

We were using Putty to connect, entered IP and port 22.  It then accepted the username and asked for "user@domain.co.uk's" password, where as it should just be "user"'s password.

Really has confused me, I may wipe the machine and start afresh this evening just in case I have fiddled with something that I shouldn't have.  But from my understanding, setup port forwarding on router, install Ubuntu, install Openssh-server, connect from remote machine...

Regards
Colin

---

### Post by djxcon on 2008-08-05
It sounds like that should work. The fact that you can access the workstation from behind the router with your laptop indicates that SSH is running and working. Did you enable UDP and TCP forwarding on the router?

---

### Post by colskinet on 2008-08-05
> **djxcon said:**
> It sounds like that should work. The fact that you can access the workstation from behind the router with your laptop indicates that SSH is running and working. Did you enable UDP and TCP forwarding on the router?

Hi djxcon

The router suggested that I only need setup TCP for port 22 using SSH, do I need to set it up to use UDP traffic as well?

Colin

---

### Post by djxcon on 2008-08-05
I am not sure, but I know that I enabled it on my router.  I'll test this theory later today and let you know if I can reproduce the problem by disabling UDP.

---

### Post by colskinet on 2008-08-05
> **djxcon said:**
> I am not sure, but I know that I enabled it on my router.  I'll test this theory later today and let you know if I can reproduce the problem by disabling UDP.

That would be most appreciated, many thanks.

Will report back later once I am home from work!

Regards
Colin

---

### Post by djxcon on 2008-08-05
Well...no luck.  I have disabled UDP on the router and ssh is still working from a remote location using Putty. You may want to give it a try anyway or at least revisit the router's settings.  Let us know how it's going.

---

### Post by djxcon on 2008-08-05
How did you install ssh on the workstation?  

I believe all that I did was type the following: 
```
sudo apt-get install ssh
```

---

### Post by colskinet on 2008-08-05
Here is a screen dump of my router
[IMG]http://img.photobucket.com/albums/v465/colskinet/ssh.jpg[/IMG]

Not yet looked at the Ubuntu machine, now off to have a nosey at it.

Colin

---

### Post by colskinet on 2008-08-05
Well it now appears to be working.  Have no idea what has happened/changed (nothing that I know of!)

Would like to thank you all for your help, most appreciated.  Will soon be back with more questions for you! :popcorn::popcorn:

Colin

---

### Post by djxcon on 2008-08-05
Great!  Don't forget to mark this thread as solved.  Also, keep a close eye on that auth.log file.  If you are using basic username/password authentication and you allow port 22 on the router, there is a good chance that some zombie machine will try and brute force its way in. Check out System -> Administration -> System Log -> auth.log.

---

### Post by colskinet on 2008-08-06
> **djxcon said:**
> Great!  Don't forget to mark this thread as solved.  Also, keep a close eye on that auth.log file.  If you are using basic username/password authentication and you allow port 22 on the router, there is a good chance that some zombie machine will try and brute force its way in. Check out System -> Administration -> System Log -> auth.log.

Will be looking at other ways of making it more secure - been reading up on it!

Newbie question - how do I make this thread solved?  Had a quick search but couldn't find anything..

Colin:confused:

---

### Post by djxcon on 2008-08-06
Click on Thread Tools just above the top subject line of the thread and drop down to the marked as solved link.  Good luck to you.

---

