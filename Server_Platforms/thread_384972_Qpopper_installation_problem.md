---
title: "Qpopper installation problem"
date: 2007-03-15
forum: Server Platforms
---

### Post by acidrop on 2007-03-15
Hello!

I have ubuntu 6.10 edgy eft installed and i'm trying to setup a mailserver on it.
I've already installed postfix (working).
I'm trying to install qpopper also for pop3 server.
During the installation i get this message which prevents it to install correctly:


Can't use PAM: can't find libpam

When i see package managment i see that libpam-runtime is already installed.
Do i have to install something else? 


thank you

---

### Post by Mr. C. on 2007-03-15
You need the PAM libraries, and you need to configure qpopper when you build it to find those libraries.

MrC

---

### Post by acidrop on 2007-03-17
Hello!

I sucessfully installed qpopper with --without-pam parameter.
Now the problem is that each time i try to run it i get this message on syslog:

Unable to obtain socket and address of client: Socket operation on non-socket (88) [pop_init.c:1116]

does anyone know what this mean?

---

### Post by Mr. C. on 2007-03-17
What user are you running qpopper as ?  It must be root.

MrC

---

### Post by acidrop on 2007-03-17
i have made an entry on inetd.conf file for that so i suppose it runs as root
i also tried with sudo -su login as root...

---

### Post by Mr. C. on 2007-03-17
inetd can be used to run services as other users.

Check with 

ps -ef | grep pop and show the output if you don't know how to read ps output.

Let's see your inetd entry.  

The error "Socket operation on non-socket" indicates qpopper is attempt to open up a file or directory perhaps, instead of a socket.  This is likely just a misconfiguration on your part.

MrC

---

### Post by acidrop on 2007-03-18
Hello and thank you for your response

The outoput of ps is the following:
root@ubuntu:/etc# ps -ef | grep pop
root      4698  4659  0 20:23 pts/0    00:00:00 grep pop

and the inetd.conf is:

pop3 stream tcp nowait root /usr/local/lib/popper qpopper -s

---

### Post by Mr. C. on 2007-03-18
The problem is occuring because no inetd is running, so your entry is not being used, and popper is attempting to determine the name of the peer on the other end.  It is assuming it was launched via inetd.

Instead of using inetd, you can build the popper to run in standalone mode, where it is always ready.  Your mail clients will get faster response this way.

Also, to build with libpam, you need the pam development libraries.

```
sudo apt-get install libpam0g-dev
```

Change directories to your qpopper source and reconfigure and build

```
sudo make realclean
./configure --enable-standalone
make
sudo make install
```

Then, run :

```
sudo /usr/local/sbin/popper -s
```

You probably want to start popper via a startup script in /etc/rc3.d.  Take a look at some of the other scripts there.

If you'd prefer to run via inetd, you will need to add your inetd entry and startup inetd as well.

MrC

---

### Post by acidrop on 2007-03-19
thank you!
Everything worked just fine!
One more last thing.To make it load each time i have to put a script on /etc/rc3.d
I have to create it by myself or there's one ready for that job?

---

### Post by Mr. C. on 2007-03-19
Your welcome.  I'm glad its working out.

There might be one somewhere on the net; they are pretty straight forward.  You can look at any of the existing  /etc/init.d scripts, copy one, and start changing it to startup qpopper with the desired arguments.

You can also just add it to the /etc/init.d/rc.local.  This is like the kitchen sink.  You'll want start and stop entries.

MrC

---

### Post by acidrop on 2007-03-20
Well done!

I made the script...thank you very much for your help!

---

