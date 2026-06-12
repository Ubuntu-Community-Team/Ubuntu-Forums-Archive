---
title: "Problems connecting to server"
date: 2010-11-10
forum: Server Platforms
---

### Post by electric-wildflower on 2010-11-10
Hello everyone i have a problem if anyone can help i created my self a file server using samba and ubuntu 10.10 server edition. I seem to successfully connect to the server through another computer using ssh even created my self a test account and could log in with that although after a few restarts i noticed the ip address kept changing so i changed.

/etc/network/interfaces to static 

after that i did

sudo /sbin/ifconfig eth0 down
sudo /sbin/ifconfig eth0 up

it seemed to work and i tested logging in with the test account and main one on here so i shut down the server for the night but after booting the server up today i tried ifconfig to make sure everything was ok but now all i get is.

inet addr:127.0.0.1

i tried

sudo /etc/init.d/networking stop
sudo /etc/init.d/networking start

but both give out

/etc/network/interfaces:10: unknown method
ifdown: couldn't read interfaces file "/etc/network/interfaces"                         [fail]

have i done something wrong somewhere thanks in advanced

---

### Post by arrrghhh on 2010-11-10
Please post your /etc/network/interfaces file in [ code ] braces.

---

### Post by electric-wildflower on 2010-11-10
this is the /etc/network/interfaces file

---------------------------------------------------------

# this file describes the network interface on your system
# and how to activate them. for more interfaces(5).

# the loopback network interface
auto lo
iface lo inet loopback

# the primary network interface
auto eth0
iface eth o inet static

--------------------------------------------------

---

### Post by arrrghhh on 2010-11-10
Yea, that's very wrong.  First, eth o?  That should be eth0.  Second, if you set it up static, you need to DEFINE what the ip, subnet, etc is...

For example, this is my /etc/network/interfaces file ```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo eth0
iface lo inet loopback

iface eth0 inet static
        address 192.168.0.90
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1
```

That's also what I meant when I said code braces ;)

---

### Post by SeijiSensei on 2010-11-10
First, it's eth0 not "eth o".

Next, you need to specify the static information if you want to set up a static IP address.  See, for instance, [http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319).

---

### Post by electric-wildflower on 2010-11-10
sorry i got the wrong it was 0 not o i wrote it wrong on here also i will try it and post the out come thanks.

---

### Post by electric-wildflower on 2010-11-10
That didn't work this is what i added in /etc/network/interfaces 

------------------------------------------------------------------------------------------
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.0.100
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1

----------------------------------------------------------------
sorry for not doing the braces im using a eeepc to get help for the server so have to manual copy stuff. i did this and restarted eth0 nothing so restarted the server and still it comes up with

/etc/network/interfaces:10: unknown method
ifdown: couldn't read interfaces file "/etc/network/interfaces"                         [fail]

---

### Post by SeijiSensei on 2010-11-10
Maybe an ownership problem?  You say you edited /etc/network/interfaces but the script can't read it?  You did edit it using sudo, right?

What's the result of
```
ls -l /etc/network
ls -l /etc/network/interfaces

```

Also, I assume it's you putting in those lines of hyphens?  If they're in the file itself, that could easily be the problem.  See arrrghhh's file above for the correct syntax.  You also may need the leading spaces before the network information like in his example.

---

### Post by electric-wildflower on 2010-11-10
Yes i edited it using sudo.

"ls -l /etc/network" the outcome for this is "ls: cannot access etc/network: no such file or directory"

"ls -l /etc/network/interfaces" the outcome for this is "-rw-r--r-- 1 root root 381 2010-11-10 15:52 /etc/network/interfaces"

---

### Post by electric-wildflower on 2010-11-10
the lines i used on here there not actually in the interface file

---

### Post by SeijiSensei on 2010-11-10
And the entries are indented?

---

### Post by electric-wildflower on 2010-11-10
well once i finish writing to interfaces file i use : then wq to save if thats any help

---

### Post by SeijiSensei on 2010-11-10
No, I mean are the lines providing the address information indented like they are in the example above:

```

iface eth0 inet static
        address 192.168.0.90
        netmask 255.255.255.0
        broadcast 192.168.0.255
        network 192.168.0.0
        gateway 192.168.0.1

```

In general, you should include the contents of files like these inside [noparse]```

```[/noparse] tags so we can see the exact contents of the file.

---

### Post by electric-wildflower on 2010-11-10
I found the problem i removed 

# The primary network interface
auto eth0

and restarted and then get a ok thanks for your help.

---

### Post by electric-wildflower on 2010-11-10
i now have a new problem arise it seemed to work for a while even let me connect now im starting to get.

# reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth0.
                                                                                    [OK}

and if i reboot the server and type ifconfig it shows up the addresses 

eth0 192.168.1.3
lo 127.0.0.1

everything seems to be fine although not sure

this is my configuration in /etc/network/interfaces

 ```


# This file describes the network interfaces available on your system
# and how to activate them. for more information, see interfaces (5).

# The loopback network interface
auto lo eth0
# Iface lo inet loopback
 
iface eth0 inet static

              address 192.168.0.3
              netmask 255.255.255.0
              network 192.168.0.0
              broadcast 192.168.0.255
              gateway 192.168.0.1

```

---

### Post by arrrghhh on 2010-11-10
Found this:

> While configuring some Ubuntu servers to have a static IP address recently, I came across this error when I attempted to restart the network interfaces:

SIOCADDRT: no such process

I realized that I had invalid IP addresses for both my network and gateway entries in /etc/network/interfaces file:

# The primary network interface
auto eth0
iface eth0 inet static
    address 192.168.0.146
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255
    gateway 192.168.0.1

Once you verify and correct the addresses, don't forget to restart networking:

sudo /etc/init.d/networking restart

---

### Post by electric-wildflower on 2010-11-10
Thanks will try that and let you know how it goes

---

### Post by electric-wildflower on 2010-11-10
Ok that sort of worked i now have a static ip and it loads eth0 it looks like this when i type ifconfig

eth0 192.168.1.3
lo 127.0.0.1

also works when i reboot the server now the problem is connecting  when i ping the router

192.168.1.1

and i get destination host unreachable 

when i ping the eepc

10.42.43.1

i get destination host unreachabel

and when i connect the eeepc to the server i get

error: ssh program unexpectidly exited please select another viewer and try again

---

### Post by arrrghhh on 2010-11-10
You have a 10.x network and a 192.168.x network...?  I'm confused, you're not giving us all the information here...

Why can't you copy and paste again?

> im using a eeepc to get help for the server so have to manual copy stuff  I don't get what you mean by this.  If the machine you're on has internet and ssh access to the box, why can't you copy&paste?

---

