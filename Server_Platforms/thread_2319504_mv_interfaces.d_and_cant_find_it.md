---
title: "mv interfaces.d and cant find it"
date: 2016-04-04
forum: Server Platforms
---

### Post by bill99 on 2016-04-04
Let me start by saying Im a extreme linux/ubuntu newbie.  I moved my interfaces.d thinking it was a file not realizing the *.d meant it was a directory.  Now I cant find it and when I do a ifup or ifdown I get a "couldnt read interfaces file.

I should also say that I have been editing the interfaces with sudo vi and sudo nano. When I restart my starting network device fails.

Ifdown eth0=
/etc/network/interfaces:1 misplaced option
ifdown: couldn't read interfaces file "/etc/network/interfaces"

does the above mean that line 1 of interfaces has an issue?

---

### Post by Graham_Willis on 2016-04-05
Try using history (it's a command) on the account of the user from which these sudos were done and perhaps you will be able to identify where you moved this directory. Alternatively you may try:

```
history | grep mv
```

Another useful command may be:

```
find / -cmin -n
```

It will search for files which were modified less than n minutes ago. The first argument to find is the name of the directory in which this searching should be done, in the above example it is / meaning that everything will be searched, you may change it with something else if you wish.

Also, put the output of:

```
cat /etc/network/interfaces
```

But generally if you change something, be sure to make backup of the config earlier.

---

### Post by bill99 on 2016-04-06
Thanks.  So the history shows:

263 mv interfaces.d /bill
264 sudo mv interfaces.d /bill
282 mv
283 mv --help
323 mv /etc/network/interfaces.d /home/bill
347 sudo mv /etc/network/interfaces.d /etc/network
484 history | grep mv

Im thinking line 264 is where my issue happened.  But when I look in /home/bill the interfaces.d isnt in there.


My interfaces shows following:
 This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.99
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.1
broadcast 192.168.1.255

---

### Post by steeldriver on 2016-04-06
I don't think /etc/network/interfaces.d contains anything, by default - however if you were in the /etc/network directory when you issued command 263, you may find that you **renamed **interfaces.d to a directory called bill in the filesystem root directory, /

The immediate issue is probably that the first line of your /etc/network/interfaces file is a comment, and needs to start with a #

```

[COLOR=#0000cd]#[/COLOR] This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

```

---

### Post by bill99 on 2016-04-06
> **steeldriver said:**
> I don't think /etc/network/interfaces.d contains anything, by default - however if you were in the /etc/network directory when you issued command 263, you may find that you **renamed **interfaces.d to a directory called bill in the filesystem root directory, /


I forgot that linux will rename the file if you dont specify it.  I did add the hashtag and that resolved the issue.  Thanks for the help!

---

