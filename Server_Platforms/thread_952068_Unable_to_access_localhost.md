---
title: "Unable to access localhost"
date: 2008-10-18
forum: Server Platforms
---

### Post by R.Bucky on 2008-10-18
My Ubuntu 7.10 box has a LAMP install. However, I cannot access my pages using [http://localhost/](http://localhost/) or any port variation. I tried adding ```
ServerName localhost
``` to my httpd.conf. That killed my server with zero access using my domain name ([http://buckyspalace.net](http://buckyspalace.net)) or [http://localhost](http://localhost). I then tried adding the above code to my /etc/apache2/sites-available/default with the same results. 

Any takers on a solution?

---

### Post by lykwydchykyn on 2008-10-18
Is apache running?

---

### Post by R.Bucky on 2008-10-18
Absolutely, to not have Apache running is sacrilidge!

---

### Post by lykwydchykyn on 2008-10-18
- What error do you get when you try to bring up localhost?  404?  403? 500?

 - What's the output of "sudo netstat -tunap |grep apache2

 - What's the output of "sudo cat /var/log/syslog |grep -i apache"

 - what's the output of "sudo tail /var/log/apache2/error_log"

---

### Post by R.Bucky on 2008-10-18
The localhost simply times out.
```
sudo netstat -tunap |grep apache2
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     14403/apache2       
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     14403/apache2       

```
The second terminal directive produces nothing (I sent the info to a .txt and it was blank too. The third directive prints```
sudo tail /var/log/apache2/error.log
[Sat Oct 18 19:38:54 2008] [error] [client 24.18.97.15] <ul></ul>
[Sat Oct 18 19:38:54 2008] [error] [client 24.18.97.15] <ul></ul>
[Sat Oct 18 19:38:54 2008] [error] [client 24.18.97.15] <ul></ul>
[Sat Oct 18 19:38:54 2008] [error] [client 24.18.97.15] <ul></ul>
[Sat Oct 18 19:38:54 2008] [error] [client 24.18.97.15] <ul></ul>
[Sat Oct 18 19:38:54 2008] [error] [client 24.18.97.15] <ul></ul>
[Sat Oct 18 19:38:54 2008] [error] [client 24.18.97.15] <ul></ul>
[Sat Oct 18 19:53:20 2008] [error] [client 66.249.73.113] File does not exist: /var/www/node
[Sat Oct 18 19:55:06 2008] [error] [client 66.249.73.113] File does not exist: /usr/share/webcalendar/www/robots.txt
[Sat Oct 18 19:55:06 2008] [error] [client 66.249.73.113] File does not exist: /usr/share/webcalendar/www/error_pages

```.

---

### Post by koenn on 2008-10-19
what happens if you do [http://127.0.0.1](http://127.0.0.1) i.s.o. [http://localhost](http://localhost) ?

---

### Post by Zeosa on 2008-10-19
Post the contents of /etc/hosts ;)

---

### Post by R.Bucky on 2008-10-19
127.0.0.1=403error and my localhost meets my timeout

```
127.0.0.1	localhost
127.0.1.1	buckyspalace
"router ip"	localhost
"router ip"	buckyspalace
```

---

### Post by koenn on 2008-10-19
127.0.1.1 buckyspalace and "router ip"	localhost don't belong there

---

### Post by lykwydchykyn on 2008-10-19
Yep, the whole point of a hosts file is to do name resolution -- to resolve a name to an IP.   If you give a name (like localhost) two IP addresses, how does it know which one to resolve?

localhost should only ever point to 127.0.0.1.  Pointing it to anything else will cause problems.

---

### Post by R.Bucky on 2008-10-19
I would agree with both of you regarding the need for only 1 host. However, this is an ongoing issue with my server. Everything works great aside from the inability to access via localhost. 

I changed the /etc/hosts file to include only localhost 127.0.0.1, restarted the computer, and my apache failed to serve my web site. I tried many variations, changing the hostname to localhost, 127.0.0.1, and the current name. Each time a change was made, I restarted my box. Nothing. 

Quite odd. There must be some line in some file that is not quite right. Baffling to me.

---

### Post by Zeosa on 2008-10-19
It's likely that apache's not starting because it can't resolve your hostname (set in your apache config) when you changed resolv.conf. You'll need to make sure that both localhost and the fqdn are resolvable....

The other option is, comment out mod_unique_id loading in your apache configuration.

---

### Post by R.Bucky on 2008-10-19
Apache has always ran perfectly with my current configuration. I simply cannot access my pages or other port associated programs attached to the domain using my buckyspalace.net domain.

---

### Post by koenn on 2008-10-20
For apache to work correctly, i.e serve pages to your browser,  you need two things 
1- a correct network configuration,
2- a correct apache configuration.

So far you haven't even accomplished step 1, and adding wild guesses and plainly incorrect entries to /etc/hosts (like  127.0.0.1 buckyspalace thing or  "router ip" localhost ) is not going to make it any better. It's just going to make troubleshooting harder. 

For starters, you complain that apache doesn't work when you appoach it with a fqdn, but there is no fqdn in your hosts file, so unless your resolv.conf solves that by forwarding to a publiek dns or appending a domain name, there's now way that can work. 

try something like this in /etc/hosts:
```
127.0.0.1 localhost
123.123.123.123 buckyspalace.net buckyspalace
```
replace 123.123.123.123 with the actual IP address of your web server - not your router address or anything like that. 

do a "ping buckyspalace.net" and see if it resolves to the correct address. Assuming you're behind a NAT router, that should be a private address, not (your router's) public address. 

Oh, and there's little use in obfuscating your addresses (the "router ip" part in /etc/hosts, e.g.) if they are in public DNS (does 24.18.97.15 look familiar ?) so if things don't work with the changes described here, post your
- /etc/resolv.conf
- /etc/hosts
without modifications, so we can actually see where the problem is. 

Once you have this working correctly, it's merely a matter of making sure Apache is configured correctly (Server Name, Document Root, Listen Address, ...) and that the permissions on the files are correct.

---

### Post by R.Bucky on 2008-10-20
Ok, let me try the items that you indicated. I edited my /etc/hosts file to read:
```
127.0.0.1 localhost
24.18.97.15 buckyspalace.net buckyspalace


# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

my /etc/resolv.conf reads:
```
# generated by NetworkManager, do not edit!

search hsd1.wa.comcast.net.


nameserver 68.87.69.146
nameserver 68.87.85.98
nameserver 68.87.78.130

```

My ServerName is buckyspalace.net, the DocumentRoot is /var/www (seems to be fairly standard), and a listen port of 80. 

I omitted my router ip. the information is public information, but there is no use to advertise for those who do not know how to get it. I get your point though...

After changing my /etc/hosts file to what you recommended, I restarted my box. My server still times out on [http://localhost/](http://localhost/).

---

### Post by koenn on 2008-10-21
just so we know that we're talking about the same thing :
your running an apache server on a desktop system, where run a browser that, when pointed to [http://localhost](http://localhost), times out, right ?

this is what you should get when pinging localhost : 
```
k@nix:~$ ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.048 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.042 ms
...

```

what do you get ?

---

