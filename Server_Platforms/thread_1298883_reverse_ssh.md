---
title: "reverse ssh"
date: 2009-10-23
forum: Server Platforms
---

### Post by sprouty on 2009-10-23
Hi,

Is there a way to set up a reverse ssh?

For example i normally ssh into box@myip1 
and get a shell for that box

is there a way that on that box i can ssh into
box@myip2 but a shell on the originating box i.e. ip1

Sorry, not the best at explaining.

Many Thanks,

Sprouty

---

### Post by tarps87 on 2009-10-23
I don't quite understand what you mean, but you can create a connection to and from any machine which has ssh set up.
Say you ssh into box1 form box2 you can then ssh into box3 from box2 or event box1 from box2

---

### Post by kemra on 2009-10-23
If you simply want to start an additional ssh session on the box you are already on you simply type: 

```
ssh localhost
```

If this isn't what you want I have missed the point completely.

---

### Post by sprouty on 2009-10-29
Sorry about the confusion, Lets see if i can make it a bit more clearer.

On one box i have access to the firewall so can edit it,
On the other box i havent. But i need access to it.

At the moment i have been use nc to listen on the box that i have a firewall access then one the second box, getting someone to use netcat to connect with the -e /bin/bash to get a shell.

If any of you guys have done this before you porbably know how might of a nightmare it is and i was wondering is there a way to do this with ssh.


Sorry aboutt this,
Sprouty

---

### Post by Lars Noodén on 2009-10-29
Are you trying to describe a situation where A is on the 'outside' and C is in the 'inside', and it is allowed to SSH initiate from C to A, but the firewall B blocks SSH initiated from A to C?  And you are at A and want to be able to log in and work on C?

```

                  B
   A              =              C
+-----+           =          +-----+
| ssh +->-->-->-X =          |     |
|     |           =          |     |
|     +-<--<--<--------------+ ssh |
+-----+           =          +-----+
                  =

```

---

### Post by sprouty on 2009-10-29
yes, have you got a way around?

---

### Post by Lars Noodén on 2009-10-29
Or are you describing where A is on the 'outside', C is on the 'inside' and B acts as a firewall, but has sshd available.  And you can ssh from A to B or from B to C but not directly from A to C?

```

                  B
   A              =             C
+-----+        +--=--+       +-----+
| ssh +->--->--=> =  |       |     |
|     |        =  =  |       |
|     +        =  =  =------>+ sshd|
+-----+        +--=--+       +-----+
                  =

```

---

### Post by Lars Noodén on 2009-10-29
> **sprouty said:**
> yes, have you got a way around?

Yes, it's called a reverse tunnel.  It is rarely needed except when malice and or incompetence of the network team inhibit the work as written in the job description.  

Set up openssh-server on A and C.  For at least one account on each, allow forwarding.   On A make sure the firewall allows connections on the port you will connect to from A.  (Below I use 22221)

You might want to make that account an unprivileged account which does nothing and has no privileges and does not own or have write access even to its own directory, but can read at least the files ~/.ssh/authorized_keys   Consider using rbash or false as the login shell. 

Do the same on C.

Then you want to make a key pair, just for the purpose of making a tunnel.  

Put both the private key and public key in ~/.ssh/ on C.  Put the public key in ~/.ssh/authorized_keys on A.  

Test that you can log in to A from C using the key pair.  Use it to open the tunnel from C to A.  Then set "Command=" in the key stored on A in ~/.ssh/authorized_keys to prevent execution of arbitrary programs.  Again make sure that the account you are using is not the owner of ~, ~/.ssh, or ~/.ssh/authorized_keys nor that it can write to any of those, but that it can read them.  

[INDENT][FONT="Courier New"]ssh -N -f -i ~/.ssh/tunnelkey -R 22221:localhost:22 *hosta.example.org*[/FONT][/INDENT]

or 

[INDENT][FONT="Courier New"]ssh -o "ServerAliveInterval=60" -N -f -i ~/.ssh/tunnelkey -R 22221:localhost:22 *hosta.example.org*[/FONT][/INDENT]

or 

[INDENT][FONT="Courier New"]ssh -f -i ~/.ssh/tunnelkey -R 22221:localhost:22 *hosta.example.org* "while date >> /tmp/tunnel.log;do sleep 10;done;"[/FONT][/INDENT]


Once you have the connection from C to A, visible in netstat (netstat -tn)
Go to A and log in to the local host on the port you set in the tunnel

[INDENT][FONT="Courier New"]ssh -p 22221 localhost[/FONT][/INDENT]

port 22221 on A is really port 22 on C.  Use the packet filter to disallow connections to it (22221 on A) from other than the local host (A)



The above is from memory and will contain errors, and thus require testing to get the details right.

Later, after the above is working, you can make a script on C to check that the tunnel is open and renew it if it is not so your machine recovers if people powercycle it.

---

### Post by sprouty on 2009-10-30
Thanks Lars Noodén. Will try this out on Monday!!!

Many Thanks for helping me out!!

cheers,

Sprouty

---

