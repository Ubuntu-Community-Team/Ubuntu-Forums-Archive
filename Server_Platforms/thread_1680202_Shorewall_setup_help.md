---
title: "Shorewall setup help"
date: 2011-02-02
forum: Server Platforms
---

### Post by tburgerjb on 2011-02-02
hi I'm trying to set up my first server, i am running ubuntu server 10.4, and im stuck trying to configure my firewall I've been following a tutroial and after running 
            sudo aptitude install shorewall

it says to run (step 1)

sudo cp /usr/share/doc/shorewall-common/examples/one-interface/* /etc/shorewall/

to back up file and then (step 2)

sudo nano /etc/shorewall/rules

to configure.

but step on gives an error saying the file or directory doesn't exist?

I've looked around and I've found people with the same or similar problem but with no explanation for the solution. any help would be awesome and I'm sorry if this question is too simple.

---

### Post by rudelgurke on 2011-02-02
So - does /etc/shorewall/rules exist ? Also the source file you're trying to copy - /usr/share/doc/shorewall-common/examples/one-interface/rules ?

---

### Post by tburgerjb on 2011-02-02
no I don't think they exist, like I don't think they are still used it is an old tutorial.

I tried:
 is /usr/share/doc/shorewall-common/examples/one-interface/*
and 
 id /etc/shorewall/

but both said not found

and rules comes up as a blank file, and says new file at the bottom of the screen.

is there i different way now to configure shorewall? I'm trying to block all connections except those to port 80 and 22.

thnaks

---

### Post by rudelgurke on 2011-02-02
And why you want to block ? First ensure there's nothing running so all ports are closed already, except the ones you want to use.
Then a firewall may be useless, specially blocking ports where nothing is listening that needs to be protected :lolflag:

Still:

[http://people.debian.org/~srivasta/shorewall-rules.txt](http://people.debian.org/~srivasta/shorewall-rules.txt)

should be the file you're looking for.

---

### Post by tburgerjb on 2011-02-02
thanks but how do I use this file?

---

### Post by rudelgurke on 2011-02-02
Download and place in /etc/shorewall/rules to edit it.

Still - if that is already a problem - are you sure you need a firewall ? Doing something wrong might end in looking yourself out of the machine.

---

### Post by tburgerjb on 2011-02-02
so if i set the server up as an internet server to host a website it will be secure without a firewall?

---

### Post by rudelgurke on 2011-02-02
Check with netstat what services are running and listen on the external interface. Take care about these, secure the services and you'll notice that you don't need a firewall at all.
Because blocking traffic on ports where nothing is running is pretty useless. And dropping a 2 MB ping from the continent atlantis is useless too, because the traffic already reached your machine.
Take care about the services you provide in the first place. A firewall as example won't help much if you run phpMyAdmin in your webroot and never update it.
For SSH - Pubkey Authentication, for Apache the usual things like mod_security, php with Suhosin and so on. Once all this is done - why you need a firewall ?
Maybe harden your kernel with Grsecurity, chroot everything (after Grsecurity) or SeLinux / AppArmor - short, either there is something running and you know it's running and you want it to run - then you open your firewall to allow traffic.
Or there's something running without your permission than you task is to inspect this process and care of it.

In both cases a firewall won't help. Because either you know your server and all it's services and configured them the right way or you don't. If you don't know your own server, a firewall won't help - it's like closing the door while opening all windows putting a huge sign on your house "Normal way is blocked. This way please"

---

