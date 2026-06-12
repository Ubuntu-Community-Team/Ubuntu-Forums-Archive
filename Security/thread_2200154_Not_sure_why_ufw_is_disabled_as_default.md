---
title: "Not sure why ufw is disabled as default"
date: 2014-01-17
forum: Security
---

### Post by EnglishElectricAndy on 2014-01-17
Yep, I'm a noob who has just upgraded to 13.10.

I was brave enough to  open a terminal and type 'sudo ufw status'. After completing my password I got the response 'Inactive'...

.. so I carried on...

... and typed 'sudo ufw enable'..

Did I do the right thing & (not meant as a criticism) why is ufw not enabled by default in new installs or upgrades?  Be interested to understand the thinking behind why (to me, as an ex-Windows user) a firewall is not enabled as a default.

---

### Post by ian-weisser on 2014-01-17
The firewall *is* enabled by default.
UFW is not the firewall. It's just one tool to manipulate the firewall. There are several good tools available, including UFW.

The firewall on an ubuntu install looks like this: 
```
$ sudo iptables -L
[sudo] password for ian: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   

```
By default, it's set to accept all inbound and outbound connections.

On Windows and OSX and others, you don't have a lot of choice about your applications connections, or how to monitor them. On Ubuntu, you do.

The applications in Software Center don't "phone home" nor make mysterious connections nor open secret backdoors that you will need to block. You can verify that by monitoring your connections, and by reading the source code. You have full control over what services are listening and operating on your system...if you want to take the time to learn it. So there's not much you need to block.

That doesn't mean you can ignore security. It means you can run safe services in a safe way, and simply uninstall or disable services you don't need, instead of blocking those services at the firewall.

---

### Post by EnglishElectricAndy on 2014-01-17
@ian-weisser

Thanks for your prompt reply. I clearly have a lot of Windows heritage/legacy to uninstall from my Armchair to Keyboard Interface Device!

Readng the source code, though, is way above my pay grade ATM.

---

### Post by ian-weisser on 2014-01-17
Nobody is born knowing how to do any of it.
We all learn.
We help each other.
Nobody knows it all. Really.

---

### Post by The Cog on 2014-01-17
ian-weisser is right, but it could be expanded.

The need for a firewall blocking incoming connections in linux is less than in windows because linux doesn't have services waiting for incoming connections that can't be disabled. If you don't want people connecting to a service, then don't choose to install it.

iptables is a command for manipulating firewall rules. It's complicated enough that there's a tool called ufw that's easier to understand, that issues all the iptables commands for you.

That's not source code. It's a command that you type into the terminal:
```
sudo iptables -nvL
```
which says to list all the current iptables firewall rules. The normal output (nothing blocked in, out, or passing through) looks like this:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

If you really want to block incoming connections (they would get refused anyway because a default install doesn't have any listening TCP services) then "sudo ufw enable" will do just that.

---

### Post by EnglishElectricAndy on 2014-01-17
Thanks @The Cog. I am very much a noob & the command 'sudo ufw enable' was a semi-educated guess on my part, having lurked around the forum for a couple of months.

PS Referencing your avatar, if you want me to throw that you'll have to let go of it first!!:) Too many teeth!

---

### Post by fihufil on 2014-01-24
If you are new to console you might consider using** Gufw** [http://gufw.org/](http://gufw.org/). Its graphical interface for ufw. The newest version is in 13.10's repos.
I prefer using Gufw's nice interface than pure console. :)

---

