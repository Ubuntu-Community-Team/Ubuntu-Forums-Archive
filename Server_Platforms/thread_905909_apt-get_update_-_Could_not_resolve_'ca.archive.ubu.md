---
title: "apt-get update - Could not resolve 'ca.archive.ubuntu.com'"
date: 2008-08-30
forum: Server Platforms
---

### Post by inadaze on 2008-08-30
Hello, 
I have seen a lot of postings about this but none of the answers seem to work for me.
I am a newbie trying to set up a Ubuntu Server (8.04.1).

I am using this guide:

[http://www.howtoforge.com/perfect-server-ubuntu8.04-lts](http://www.howtoforge.com/perfect-server-ubuntu8.04-lts)

I reached the part where I am supposed to use apt-get update and I get errors Like:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not resolve 'ca.archive.ubuntu.com'

I tried to change the address (from ca to us or de or just archive) but it seems that I can't get onto the internet.

The server machine is behind a wireless router and I think that I didn't set up the "/etc/network/interfaces" or "/etc/hosts" files properly.

At one point I added "91.189.88.31 security.ubuntu.com" to the end of the hosts file and I stopped getting errors for the security part, but still had them for the archive.  I feel like I am close but tired and can't figure it out.

Can anyone help?
Thanks
Jay

---

### Post by windependence on 2008-08-31
Try this. Go your /etc/nsswitch.conf file and edit it with nano or vi.

```
sudo nano /etc/nsswitch.conf
``` 

Findo the line that looks like this;

```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Replace it with this:

```
hosts: files dns
```

Restart your network:

```
sudo /etc/init.d/networking restart
```

Try again and see what happens.

If that doesn't work, add this line to your /etc/hosts on the server:

```
91.189.88.46  ca.archive.ubuntu.com
```

Restart the network again and try it.

-Tim

---

### Post by inadaze on 2008-08-31
Thank you for your response, but it didn't work.

when I checked the nsswitch file, it already contained the line you suggested.

And I tried to add the ip address for ca.archive.ubuntu.com and I got this as an error when I ran apt-get update:

Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/restricted Translation-en_CA                                                  
  Could not connect to ca.archive.ubuntu.com:80 (91.189.88.46). - connect (113 No route to host)

I am stumped.  I really thought that last effort would work.  It must be something deeper.  I have my server connected to my wireless router.  should it be directly connected to my modem?  Is there some configuration of the router that would hinder the servers connection to the outside world?

cheers,
Jay

---

### Post by windependence on 2008-08-31
I certainly wouldn't be running a server over a wireless connection.

You either have a problem with your gateway, or you have a DNS problem.

What is the output of 

```
traceroute ca.archive.ubuntu.com
```

from your server?

Leaving out the fact that you had this server plugged in to the wireless didn't help much with the diagnosis. Any other "details" we should know?

-Tim

---

### Post by inadaze on 2008-08-31
You've misunderstood.  I am not connecting my server by a wireless connection.  It is connect via network cable directly to the wireless router.  I mentioned that in my original posting.   

Quote:

"The server machine is behind a wireless router and I think that I didn't set up the "/etc/network/interfaces" or "/etc/hosts" files properly."

I don't have traceroute installed because I cannot use apt-get.  For example, I get a similar error to the one I originally posted.

"Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy/main traceroute 2.0.9-3
  Could not connect to ca.archive.ubuntu.com:80 (91.189.88.46). - connect (113 No route to host)
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_2.0.9-3_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/t/traceroute/traceroute_2.0.9-3_i386.deb)  Could not connect to ca.archive.ubuntu.com:80 (91.189.88.46). - connect (113 No route to host)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?"


Therefore leading me back to my original post.  If it is a gateway or dns problem, do you have any advice as to how to fix the problem?

cheers,
Jay

---

### Post by cariboo on 2008-08-31
Can you post your /etc/network/interfaces file if you are running a static ip address. If you aren't running a static ip address maybe you should set that up first.

Here is an example of what a static ip address would look like:

```
# The primary network interface
auto eth0
iface eth0 inet static
address	192.168.1.200
netmask	255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Jim

---

### Post by gtdaqua on 2008-09-01
Why is this getting more and more complex?

The query is simple - you cant resolve hostnames. Dont edit hosts file etc...

Check your "/etc/resolv.conf" file. It should have the name servers mentioned

```

nameserver 208.67.222.222
nameserver 208.67.220.220

```

That is all you need apart from configuring IP address on your machine.

To check if it works do the following. Type 'nslookup' and press enter:
```

> server               [COLOR="Red"][this will tell you the DNS sever being used][/COLOR]
Default server: 208.67.222.222
Address: 208.67.222.222#53
Default server: 208.67.220.220
Address: 208.67.220.220#53
> google.com             
Server:         208.67.222.222
Address:        208.67.222.222#53

Non-authoritative answer:
Name:   google.com
Address: 64.233.187.99
Name:   google.com
Address: 64.233.167.99
Name:   google.com
Address: 72.14.207.99

```

---

### Post by gtdaqua on 2008-09-01
> **windependence said:**
> Try this. Go your /etc/nsswitch.conf file and edit it with nano or vi.

```
sudo nano /etc/nsswitch.conf
``` 

Findo the line that looks like this;

```
hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4
```

Replace it with this:

```
hosts: files dns
```

Restart your network:

```
sudo /etc/init.d/networking restart
```

Try again and see what happens.

If that doesn't work, add this line to your /etc/hosts on the server:

```
91.189.88.46  ca.archive.ubuntu.com
```

Restart the network again and try it.

-Tim

Its a simple DNS configuration - why all these is necessary????

---

### Post by inadaze on 2008-09-02
Thank you all for your replies.  After hours searching the web, trying everything under the sun (including all suggestions posted here), I resolved to reinstall the server's OS.  That worked.  Everything that was suggested here, looked to be fine, so I got frustrated and wanted to start from scratch.  I must have done some stupid newbie mistake and could find it anywhere.

cheers
Jay

---

### Post by windependence on 2008-09-02
> **gtdaqua said:**
> Its a simple DNS configuration - why all these is necessary????

Well gtd, this is a bug in earlier releases relating to the repositories, but as he stated, it has been fixed in the new version.

I am with you on this, if DNS is set up properly, it should work with no problems. Putting the entries in his host file should make lookup faster however, it was just a suggestion.

-Tim

---

