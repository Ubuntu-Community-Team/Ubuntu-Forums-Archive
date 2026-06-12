---
title: "force users to use apt-cache-ng proxy"
date: 2017-01-28
forum: Server Platforms
---

### Post by pqwoerituytrueiwoq on 2017-01-28
I have my apt-cache-ng server setup
i set DNSMasq to reroute the ubuntu repo to my cache server (server does not use the default DNS settings)
eg : [FONT=courier new]address=/us.archive.ubuntu.com/10.0.0.25[/FONT]
i used pound to make port 80 act as port 3142
this is what happens
system request:[INDENT][FONT=courier new]http://us.archive.ubuntu.com/blablabla[/FONT][/INDENT]
DNS server does this[INDENT][FONT=courier new]http:/10.0.0.25/blablabla[/FONT][/INDENT]
pound does this[INDENT][FONT=courier new]http://10.0.0.25:3142/blablabla[/FONT][/INDENT]
but i want it dodo this[INDENT][FONT=courier new]http://10.0.0.25:3142/us.archive.ubuntu.com/blablabla[/FONT][/INDENT]

the main reasons for this is so laptops can update while on other networks than my own

---

### Post by TheFu on 2017-01-28
Interesting idea. Just proves there are 10 ways to solve any issue on Unix.

I just swap the 02proxy settings in /etc/apt/apt.conf.d/02proxy based on the current network.
It is manual today (have 2 files), but the post-up in /etc/network/interfaces could take care of that too, I believe. There are other ways as well, like with an ansible script that enables/disables the proxy if it exists on the current network and runs locally every few minutes. I already use ansible to configure systems, so doing a laptop wouldn't be hard.  Our network uses odd subnets (helps with VPN routing) so just looking at the subnet is probably sufficient for my needs to determine which network we are on.

Looked for a way that APT might handle the multiple-networks issue. Didn't see anything here: [https://debian-handbook.info/browse/wheezy/sect.apt-get.html](https://debian-handbook.info/browse/wheezy/sect.apt-get.html)

Thing I'll get my script working better this morning. Might not work for others who don't use devops techniques and have hundreds of laptops to manage.

The script ... 
```
#!/bin/bash

# file to modify /etc/apt/apt.conf.d/02proxy
FILE=/etc/apt/apt.conf.d/02proxy
SED=/bin/sed
GREP=/bin/egrep
SEARCH="proxy-host:3142"
PROXY_LINE='Acquire::http { Proxy "http://proxy-host:3142"; };'

# Check the current IP address, 
WHATSUBNET=`/sbin/ip add |$GREP -c '172.22.22.1[36]'` # system could have wired or wifi enabled
if [[ $WHATSUBNET = 0 ]] ; then
   # If not on my subnet, remove the proxy.
   $GREP -v "$SEARCH" $FILE > /tmp/$$

else
   # if 1 on my subnet, enable this proxy
   echo "$PROXY_LINE" > /tmp/$$
   $GREP -v "$SEARCH" $FILE >> /tmp/$$

fi
/bin/mv /tmp/$$ $FILE
/bin/rm /tmp/$$
```
Put this "apt-proxy" script into /usr/local/bin/  and add a **post-up /usr/local/bin/apt-proxy** line to the /etc/network/interfaces file.
Don't know whether this works with wifi at this point. Calling it over and over from an automatic process shouldn't be harmful.

---

### Post by pqwoerituytrueiwoq on 2017-01-28
just to be sure i did not miss something
So given my network is 10.0.0.0/24 and dhcp starts at 10.0.0.101 and my server is at 10.0.0.25 this would be my script
```
#!/bin/bash

# file to modify /etc/apt/apt.conf.d/02proxy
FILE=/etc/apt/apt.conf.d/02proxy
SED=/bin/sed
GREP=/bin/egrep
SEARCH="10.0.0.25:3142"
PROXY_LINE='Acquire::http { Proxy "http://10.0.0.25:3142"; };'

# Check the current IP address, 
WHATSUBNET=`/sbin/ip add |$GREP -c '10.0.0.1[36]'` # system could have wired or wifi enabled
if [[ $WHATSUBNET = 0 ]] ; then
   # If not on my subnet, remove the proxy.
   $GREP -v "$SEARCH" $FILE > /tmp/$$

else
   # if 1 on my subnet, enable this proxy
   echo "$PROXY_LINE" > /tmp/$$
   $GREP -v "$SEARCH" $FILE >> /tmp/$$

fi
/bin/mv /tmp/$$ $FILE
/bin/rm /tmp/$$

```

---

### Post by TheFu on 2017-01-28
test it. Does it work or not?  I do see a likely issue since my laptop has 1 of 2 IPs on my LAN. Strengthen your regex-fu.

My .13 IP is wired.
My .16 IP is wifi.

I wasn't specific with the interface in the ip command because different ones are used on different systems here.
I might need to run the command at post-down time too to catch a switch from wired at work to wifi somewhere else. Basically, the default would be NOT to have the proxy specified, but when on the correct wired network, it would be included.  My 02proxy has other settings too - for docker stuff.  If you don't do that, then the script could be much easier, without need for any temporary file.

BTW, I plan to set the temp file at the top and use a variable for it everywhere else below.  Should use mktemp, not just assume /tmp/$$ is unique. ;)  That's what you and I get when someone slaps together a little script. ;)  
Ansible would have been cleaner, but that's a bunch of code that has to work anywhere and my laptop isn't the normal ansible management workstation here. Just for clarity, I simply copy in a pre-created proxy file with ansible. Could do that in the script above too.
Here's the ansible task:
```
---
- name: Put in new Apt-Cache settings
  copy: src=files/etc_apt_02proxy dest=/etc/apt/apt.conf.d/02proxy 
        backup=yes owner=root group=root mode=0644

```

---

### Post by pqwoerituytrueiwoq on 2017-01-29
i don't full understand your grep line but anyway i modified it a bit
```
#!/bin/bash

# File to modify /tmp/aptProxyConfig.cfg
FILE=$(/bin/readlink /etc/apt/apt.conf.d/02proxy)
TEE=/usr/bin/tee
GREP=/bin/egrep
HOST="10.0.0.25"
PORT="3142"
PROXY_LINE="Acquire::http { Proxy \"http://$HOST:$PORT\"; };"
# My DHCP starts at 101, therefore the 1st digit must be 1 or a 2 to be my network
WHATSUBNET=$(/sbin/ip add | $GREP -c '10.0.0.[1-2]') # system could have wired or wifi enabled
if [[ $WHATSUBNET = 0 ]] ; then
   echo "# Not my network" | $TEE $FILE
elif [[ $(/bin/nc -z -w1 $HOST $PORT;echo $?) = 0 ]] ; then
   echo $PROXY_LINE | $TEE $FILE
else
   echo "# No proxy server" | $TEE $FILE
fi
```

---

### Post by pqwoerituytrueiwoq on 2017-01-29
> **TheFu said:**
> 
Put this "apt-proxy" script into /usr/local/bin/  and add a **post-up /usr/local/bin/apt-proxy** line to the /etc/network/interfaces file.
Don't know whether this works with wifi at this point. Calling it over and over from an automatic process shouldn't be harmful.

how do i do this when there is a network manager installed, this is a client side config not a server one

---

### Post by TheFu on 2017-01-29
I don't consider clients and servers to be different. Don't really have any desktop installations here.

Google found this answer: [https://ubuntuforums.org/showthread.php?t=2245608](https://ubuntuforums.org/showthread.php?t=2245608) to the NM post-up stuff.

I don't know anything about NM; it didn't work for my non-trivial network requirements years ago, so always purge it. Thought it would skip over any devices already configured in the interfaces file.  My solution has been working for years now.

For wifi, use wicd-curses.
For wired, use the interfaces config file. Both static and DHCP work this way fine.

My systems are almost always wired. Did over 1200 wifi deployments and learned how much wifi sucks. It is the exception when it works well, IME.  Even good wifi is never as good as average wired.

---

### Post by pqwoerituytrueiwoq on 2017-01-29
```
sudo ln -s /usr/local/sbin/setaptproxy /etc/network/if-up.d/001SetAptProxy
```
thanks

---

### Post by TheFu on 2017-01-29
> **pqwoerituytrueiwoq said:**
> ```
sudo ln -s /usr/local/sbin/setaptproxy /etc/network/if-up.d/001SetAptProxy
```
thanks

SWEET!
Please mark as [solved].

---

