---
title: "using apt-cacher behind a proxy server"
date: 2010-03-05
forum: Server Platforms
---

### Post by abraxas334 on 2010-03-05
I am having the following issue:
I want to use apt-cacher on a server that is connected to a few computers via a local network. The server is not connected directly to the internet but behind a proxy.
But I want the server to be the apt-cacher server for the internal network. I have installed apt-cacher and its up and running. When i want to install stuff on the server using apt-get it works fine. My bashrc file has the right export options and my apt.conf file has this line 
> Acquire::http::Proxy "http://proxyname:port";
my sourcelist is usual one 
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe  etc.
Now rather than using this outer proxy I would like to use apt-cacher which then makes use of the outer proxy. Is this possible?

So I am guessing i should set the "outer proxy" in apt cacher config file and the apt.config file should be modified to something like
> Acquire::http::Proxy "http://localhost:aptcacher_defined_port";
does the source.list stay the same?

and where do I set the proxy settings for apt-cacher, because when i use the changed proxy settings my error is this:

> Err [http://ftp.uk.debian.org](http://ftp.uk.debian.org) stable Release.gpg      
  Could not connect to ftp.uk.debian.org:80 (83.142.228.128). - connect (110: Connection timed out)
0% [Connecting to ftp.uk.debian.org (83.142.228.128)]

I used the default /etc/apt-cacher/apt-cacher.conf apart from this line (99) I changed this:
> 
# Apt-cacher can pass all its requests to an external http proxy like
# Squid, which could be very useful if you are using an ISP that blocks
# port 80 and requires all web traffic to go through its proxy. The
# format is 'hostname:port', eg: 'proxy.example.com:8080'.
http_proxy=myproxysettings:myport

these are the ones from the original apt.conf file.
To my understanding everything should work now, but it doesn't any ideas?
Thanks a lot

---

### Post by abraxas334 on 2010-03-05
Ok sorry I found my problem. There was a flag in the apt-cacher, which i hadn't seen which needed changing in order for the proxy to work.
apt-get update does now work but it is very slow. And getting headers takes a long time is this normal?

---

