---
title: "fail2ban Bug - Jails can't start in IPTables"
date: 2010-05-10
forum: Security
---

### Post by eXDee on 2010-05-10
Currently suffering from this bug:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=554162](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=554162)

If you don't want to read the whole thing, it appears fail2ban overloads IPTables when you have too many jails, and sends a whole load of commands at once.

I attempted to use the workaround making it sleep for a random period of time, but this does not help at all, it still fails like it used to.

Any ideas? Fail2ban is a pretty popular app...

Ubuntu 9.10.

```
$ aptitude show fail2ban
Package: fail2ban
State: installed
Automatically installed: no
Version: 0.8.3-6ubuntu2
```
I see 0.84 has been out for a while, though in my experience building from source has always been an issue as we're in an OpenVZ VPS environment, so it always seems to create errors when i attempt to build things from source. And i dont know if its going to help.

---

### Post by bodhi.zazen on 2010-05-10
This does not directly answer your question, but I suggest you learn iptables.

You can then use iptables in an openvz guest to accomplish the same thing.

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Scroll down to the section on blocking brute force attempts.

Your other options are to:

1. Wait for the fail2ban developers to fix this bug.

2. Write the code yourself.

---

### Post by eXDee on 2010-05-12
Decided to use
-A INPUT -p tcp -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -d MYIPHERE --dport 80 -j ACCEPT

Which is slightly modified from that tutorial you linked to be only for HTTP. But is this globally limiting it to 30 req's for everyone over the whole server, or is it 30 req's/s per unique IP address?

---

### Post by bodhi.zazen on 2010-05-12
30 requests per IP address per 30 minutes.

IMO this is a rather strict limitation, Apache can dish out thousands of requests / minute.

See the benchmarks here : [http://blog.bodhizazen.net/linux/optimize-wordpress-for-speed/](http://blog.bodhizazen.net/linux/optimize-wordpress-for-speed/)

Take a look at typical client (browser) settings -

[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

Unless you are having a problem I suggest you set more liberal limits.

Otherwise be sure to test your settings and make sure they do not interfere with "normal" browsing / access to your server.

---

### Post by cdenley on 2010-05-12
I thought that would limit the number of TCP connections, not necessarily the number of HTTP requests. I don't think that would prevent someone from using a single TCP connection to perform hundreds of HTTP requests.

---

### Post by bodhi.zazen on 2010-05-12
> **cdenley said:**
> I thought that would limit the number of TCP connections, not necessarily the number of HTTP requests. I don't think that would prevent someone from using a single TCP connection to perform hundreds of HTTP requests.

You are correct, I guess I missed the -m state --state NEW

That rule will not affect established connections.

---

### Post by cdenley on 2010-05-13
I did a little testing with iptables rate limiting. Apache by default allows 100 HTTP requests per TCP connection.
```

grep ^MaxKeepAliveRequests /etc/apache2/apache2.conf

```

This means if you allow 30 TCP connections per minute, then an attacker would still be able to send 3,000 HTTP requests each minute. The number of requests your server can handle depends on how much work a single request can make apache do (such as database queries) and how much resources your server has available.

By default, apache allows a connection to be open for 15 seconds.
```

grep ^KeepAliveTimeout /etc/apache2/apache2.conf

```
I think any web browser in use today will keep connections open until they timeout, so visiting a single page should only use a single connection, even though there may be several different requests for images, javascript files, stylesheets, icons, etc. I don't think limiting them to 30 connections per minute would interfere with any legitimate web browsing, but I wouldn't set it to less than 10.

In case anyone wants to do any of their own testing, here is a simple python script I wrote which will send a specified request a specified number of times over a specified number of simultaneous connections.
```

#!/usr/bin/python
import socket,sys,threading

class TcpThread(threading.Thread):
	def run(self):
		sock=socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		sock.connect((host,80))
		fh=sock.makefile()
		req="GET "+uri+" HTTP/1.1\nHost: "+host+"\nExpect: 100-continue\n";
		for i in range(0,rep):
			sock.send(req+"\n")
			line='not empty'
			while line!='':
				line=fh.readline().strip()
		fh.close()
		sock.close()

if len(sys.argv)<4:
	print 'usage: ./http.py http://mydomain.com/path/ requests_per_connection connections'
	sys.exit(1)
rep=int(sys.argv[2])
if rep<1:
	print 'invalid number of repetitions'
	sys.exit(1)
threads=int(sys.argv[3])
if threads<1:
	print 'invalid number of connections'
	sys.exit(1)
url=sys.argv[1]
if len(url)<7 or url[:7]!='http://':
	print 'invalid protocol, url must start with "http://"'
	sys.exit(1)
host=url[7:]
index=host.find('/')
uri='/'
if index>0:
	uri=host[index:]
	host=host[:index]
print "host: "+host
print "URI: "+uri
print "connections: "+str(threads)
print "requests per connection: "+str(rep)
print "SENDING REQUESTS..."
for i in range(0,threads):
	TcpThread().start()

```

---

