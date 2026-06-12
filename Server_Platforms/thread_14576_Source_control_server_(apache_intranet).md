---
title: "Source control server (apache intranet?)"
date: 2005-02-08
forum: Server Platforms
---

### Post by lgoss007 on 2005-02-08
We are planning to use subversion as our version control tool, and would like to set it up with apache. I've read the wiki on setting up subversion, but my question is what would be the best way to setup an apache server to run subversion internally?

current setup:
We currently have a Windows IIS server running an internet/intranet.

goal:
We need to access subversion internally only. Using WebDav would be ideal, which is why I want to run the apache server. But I don't think the network admins will allow apache to be installed on the same one as IIS because they don't know how to run it. So we developers have our own development server for source code. I have Ubuntu on the development server running apache.

I know we need to open a port for the apache server, but what security issues does this incur? Will outside intruders be able to exploit this? Basically, what's the difference between a intranet and an internet (technically speaking)?

Thanks,
Lucas

---

### Post by mendicant on 2005-02-08
Well to make it just for an internet, you would only listen on a specific address--the intranet address.  If the intranet and internet addresses are the same (only one NIC), you can use a firewall to block the port for internet users.

---

### Post by lgoss007 on 2005-02-09
Ok, thanks, I think I get it now.

---

### Post by lgoss007 on 2005-02-10
Ok, maybe not  ](*,) 

I keep getting "The connection was refused..."

Here is our setup:

IIS internet server at - example.com
IIS intranet server at - intra.example.com (uses SSL)

So now I'm adding:
Apache intranet server at - ?

Do I need another subdomain? If so do I have to enable it somewhere in windows? which server, intranet?

Does the apache server need a seperate ip address? Does it need to be configured with SSL since the intranet server is?

For httpd.conf I have:
-----
Listen 8080
NameVirtualHost ?:8080

<VirtualHost ?:8080>
  ServerName ?
</VirtualHost>
...
-----

Currently the ip address of the virtual host is the same as the intranet server (IIS), is that how it should be? If not then I suppose I need to assign it an ip address?

Thanks for any help,
Lucas

---

### Post by mendicant on 2005-02-10
Since you're running on a different machine, your intranet server will need its own IP address.  You can add a subdomain if you want, but for now, you can always use the actual IP address for testing.

---

### Post by lgoss007 on 2005-02-22
Well I'm back at this (my primary job is programmer, not network admin).

Can I have an IP address that is given by DHCP but is always the same (so the server always gets the same address), or does it have to be a static address? Again this is only an internal server.

If it can be a permanent DHCP address then I have this problem:

(98)Address already in use: make_sock: could not bind to address 172.24.1.5:80 no listening sockets available, shutting down

---

### Post by mendicant on 2005-02-22
You can have your DHCP server assign a fixed address based on the mac address.  The error you're getting appears to be that some other process is already listening on port 80.  You can use:

% lsof | grep ":www"

to check what processes are listening on port 80.  Alternatively, try 

% lsof | grep ":80"

---

### Post by lgoss007 on 2005-02-22
Ok then the IP address should be fine. I tried:

> 
% lsof | grep ":www"

to check what processes are listening on port 80. Alternatively, try

% lsof | grep ":80"
And both returned nothing. And running
```
user@srvname:~$ sudo /etc/init.d/apache2 reload
 * Reloading web server config...
httpd not running, trying to start
(98)Address already in use: make_sock: could not bind to address 172.24.1.5:80
no listening sockets available, shutting down
 *able to open logs  
```
So I'm not sure what to try next. Would our intranet server have any affect on this? Or could our firewall affect this at all? I tried to make the httpd.conf file as simple as possible using just listen and servername to try to lower the possible points of failure, but I'm still stuck.

Changes I've made:
/etc/apache2/httpd.conf - added listen and servername
/etc/apache2/ports.conf - changed listen to ip address : port
/etc/hosts - added ip address servername

---

### Post by alastair on 2005-02-22
What is listening locally on your machine?

netstat -nlp -A inet

I would forget about "Listen" etc. - keep it basic. A simple "Port 80" is all you need really.

I am confused on your network topology though.

---

### Post by lgoss007 on 2005-02-23
Ok, I've finally got it working with just a "Listen 80". When I had the IP address in it was getting confused (I don't know why).

Is it possible to do IP-based virtual hosts with only one NIC?
If so, how does that work?
[list]
[*]can I assign (from DHCP server) two IP addresses to one NIC?
[*]If yes, how do I get the server to use two addresses? ifconfig? Sounds like what I want, but I'm not sure.
[/list]

---

