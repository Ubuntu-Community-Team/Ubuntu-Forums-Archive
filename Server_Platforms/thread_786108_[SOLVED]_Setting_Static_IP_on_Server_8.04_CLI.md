---
title: "[SOLVED] Setting Static IP on Server 8.04 CLI"
date: 2008-05-07
forum: Server Platforms
---

### Post by freakypcteck on 2008-05-07
I am new to Ubuntu Server i just downloaded it and installed it... VERY EASY!  only thing is i am not familar with any CLI commands.  If someone could let me know what the command for setting a static address, subnet and gateway.

---

### Post by KevinD_Atl on 2008-05-07
You can try this, it works in 6.0.6


vi /etc/network/interfaces

See This Link For the layout
[[COLOR="Blue"]http://howtoforge.com/perfect_setup_ubuntu_6.06_p3[/COLOR]]("http://howtoforge.com/perfect_setup_ubuntu_6.06_p3")



VI Is tricky at first - Print this for your reference!
[[COLOR="blue"]http://www.digilife.be/quickreferences/QRC/Vi%20Reference%20Card.pdf[/COLOR]]("http://www.digilife.be/quickreferences/QRC/Vi%20Reference%20Card.pdf")

---

### Post by juan@forum on 2008-05-08
you could add the network information on the file /etc/network/interfaces, in that way everytime your system boots it will configure your network adapter automatically

in cli commands, you can use ifconfig or ip

ip belongs to the package named iproute (it's awesome)

for more info about them, check 
man ifconfig
man ip

---

### Post by freakypcteck on 2008-05-08
ok i guess i am having one of those days....  i guess i am going to need a hand holding session.  i have checked out both your options, i ran into the ID10T error so i am having a Brain fart. dumb down for me today it has been a ruff day in the world of windows...

if someone could just break it down into setups it would be greatly appreciated.](*,)

---

### Post by ikt on 2008-05-08
> **freakypcteck said:**
> ok i guess i am having one of those days....  i guess i am going to need a hand holding session.  i have checked out both your options, i ran into the ID10T error so i am having a Brain fart. dumb down for me today it has been a ruff day in the world of windows...

if someone could just break it down into setups it would be greatly appreciated.](*,)

Assuming you know how to use vi editior(If you don't you should probably be using ubuntu desktop edition):



1.  sudo vi /etc/network/interfaces

2. in that file is something that might look like this:

```
iface eth0 inet dhcp
```

change dhcp to be static:

```
iface eth0 inet static
```

and include underneath it:

```
        address 192.168.0.100 (what you want your static ip to be)
        netmask 255.255.255.0 (is normal, just need to copy)
        broadcast 192.168.0.255 (copy)
        gateway 192.168.0.1 (whatever your routers ip address is)
```

save and quit vi

3. sudo /etc/init.d/networking restart 

and it should now be whatever ip address you put in the 'address' section.

---

### Post by songshu on 2008-05-09
> **ikt said:**
> Assuming you know how to use vi editior(If you don't you should probably be using ubuntu desktop edition):

could i add that i have been administrating linux and BSD boxes for about 5 years on the CLI and i don't know how to use vi either (tought it was VIM actually) i personally use nano /etc/network/interfaces wich is a lot easier and does the job well.

all the rest this guy told you is perfect ;)

you could also see the applied settings with the command

```
ifconfig
```

---

### Post by ikt on 2008-05-09
> **songshu said:**
> could i add that i have been administrating linux and BSD boxes for about 5 years on the CLI and i don't know how to use vi either (thought it was VIM actually) i personally use nano /etc/network/interfaces which is a lot easier and does the job well.

that's cool, I probably should have said a 'cli text editor'.

---

### Post by songshu on 2008-05-09
you could do it with commands as well.
something like so:
```

ifconfig eth0 192.168.0.100 netmask 255.255.255.0 up
ifconfig eth0
```


but everytime you start your computer it actually reads the file in /etc/network/interfaces so you would have to do it again everytime.

a nice place to start is here [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by freakypcteck on 2008-05-09
thanks the nano is better for me,  when i try to save the file i get an error witing /ect/network/interfaces: No such file or directory.  i know i am doing something wrong. thanks for the help guys.

---

### Post by songshu on 2008-05-09
nano /etc/network/interfaces


mind the etc

---

### Post by songshu on 2008-05-09
ps.

you could use the tab key to complete the path you are following, just try to pres Tab when you are halfway typing, or twice in a row to see the remaining options.

---

### Post by nicenotty12 on 2008-05-09
When you connect to a web site, it can see your IP address as the
"Remote IP" or "Remote Address". When you surf through a proxy serrver,these fields contain the IP address of the proxy server instead of your own IP address. So the web site will see the address of the proxyinstead of your actual address.But all non-anonymous proxies usually put the IP addresses of their clients (i.e. of the computers using those proxies) in either of the two following request headers (variables): "HTTP_CLIENT_IP" or "HTTP_X_FORWARDED_FOR_IP" There are no strict standards, so one proxy may be sending the IP with "Client_IP" variable and another with "X_Forwarded_For_IP".

---

### Post by freakypcteck on 2008-05-09
yep that was my problem i was typing ect...  Thanks for all you help guys.

---

