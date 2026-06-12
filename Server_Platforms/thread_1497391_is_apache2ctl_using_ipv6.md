---
title: "is apache2ctl using ipv6"
date: 2010-05-30
forum: Server Platforms
---

### Post by gyre007 on 2010-05-30
for querying the apache2 status ??
I've set up an apache2 on my ubuntu server - just for testing purposes...
everything seems to be working just fine...BUT when I run sudo apache2ctl status I get the following error on the command line: "You don't have permission to access /server-status on this server"
I've checked the apache's error log and found this:
[error] [client ::1] client denied by server configuration: /var/www/server-status

I thought that the problem is in my Vhost config...especially the "Location" part...it's set as follows:

    <Location /server-status>
        SetHandler server-status
        Order deny,allow
        Deny from all
       Allow from 127.0.0.1 127.0.1.1 localhost
    </Location>

so I started looking into this more closely and made few tcpdumps which I checked later in wireshark....
I made 2 basic tests: 
1.) running sudp apache2ctl status 
2.) accessing the server-status page from the browser which is running ON THE SAME machine on which the apache is running...

results:
1.) in tcpdump I can see that apache2ctl is using ipv6 ??? for querying the status of the apache2...WHY ?
2.) everything seems to be "normal" here....I can access sever-status from the browser (RUNNING ON THE SAME MACHINE ON WHICH APACHE2 IS RUNNING) normally and im not seeing anything abnormal in tcpdump either...why should I anyway :)

so my question is...WHY is apache2ctl using ipv6 when querying the apache status with apache2ctl status command ? is there a way how to force it to use ipv4 ?? IBecause I SUSPECT that that might be the reason why I'm getting the error mentioned at the start of this thread...
THanks a lot for help to everyone!

PS1: ataching 2 screenshots from those tcpdumps I mentioned....check the ip protocol version
PS2: when I set the Location directive to  Allow from all everything is working just fine - but I DONT WANT to allow the access to server-status to all...

---

### Post by Bachstelze on 2010-05-30
> **gyre007 said:**
> 
1.) in tcpdump I can see that apache2ctl is using ipv6 ??? for querying the status of the apache2...WHY ?

You probably have a line with an IPv6 address for localhost in your /etc/hosts. Can you paste it? Alternatively, you can also add ::1 in the Allow directive in your vhost block. ::1 is the IPv6 counterpart of 127.0.0.1.

---

### Post by gyre007 on 2010-05-30
> **Bachstelze said:**
> You probably have a line with an IPv6 address for localhost in your /etc/hosts. Can you paste it? Alternatively, you can also add ::1 in the Allow directive in your vhost block. ::1 is the IPv6 counterpart of 127.0.0.1.

UBELIEVABLE! You are correct!!!! This was part of my /etc/hosts

127.0.0.1    localhost
127.0.1.1    gyre-laptop gyre-ding.com

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I commented OUT the ::1 line and tested it again and FINALLY! After 2 hours of troubleshooting it works!!!
thanks A LOT!

one more thing...why does it work like this ? I mean I would expect that it works on first-match basis so when the ServerName directive is resolved to the IP which is before ::1 line then apache2ctl shouldn't care about it any more...or am I missing out something here ?
Thanks again!

---

### Post by Bachstelze on 2010-05-30
> **gyre007 said:**
> 
I commented OUT the ::1 line and tested it again and FINALLY! After 2 hours of troubleshooting it works!!!
thanks A LOT!


Rather, remove localhost from the line. Some programs might expect ip6-localhost to be there.

> one more thing...why does it work like this ? I mean I would expect that it works on first-match basis so when the ServerName directive is resolved to the IP which is before ::1 line then apache2ctl shouldn't care about it any more...or am I missing out something here ?

That's a very good question, I admit I don't know exactly what happens if you have two entries for the same name in your hosts file. On DNS, if there is both an IPv4 and IPv6 entry for the same name, they are both used indifferently (i.e. a program is free to use one or the other if not forced otherwise, though most default to IPv6). The hosts file seems to operate the same way, from the few tests I've done.

---

### Post by gyre007 on 2010-05-30
> **Bachstelze said:**
> Rather, remove localhost from the line. Some programs might expect ip6-localhost to be there.

Good idea, I did that...


[QUOTE= That's a very good question, I admit I don't know exactly what happens if you have two entries for the same name in your hosts file. On DNS, if there is both an IPv4 and IPv6 entry for the same name, they are both used indifferently (i.e. a program is free to use one or the other if not forced otherwise, though most default to IPv6). The hosts file seems to operate the same way, from the few tests I've done.[/QUOTE]

another strange thing is....that it looks like apache2 is listening for ipv6 connections as far as what i can see in netstat...:

gyre@gyre-laptop:/var/www$ netstat -ntl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:41096         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
**tcp6       0      0 :::80                   :::*                    LISTEN **    
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::389                  :::*                    LISTEN     

I haven't done any ipv6 config changes - just playing around with defaults ...not sure why is it so either :)

---

### Post by Bachstelze on 2010-05-30
> **gyre007 said:**
> 
another strange thing is....that it looks like apache2 is listening for ipv6 connections as far as what i can see in netstat...:

gyre@gyre-laptop:/var/www$ netstat -ntl
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:389             0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:41096         0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
**tcp6       0      0 :::80                   :::*                    LISTEN **    
tcp6       0      0 ::1:631                 :::*                    LISTEN     
tcp6       0      0 :::389                  :::*                    LISTEN     

I haven't done any ipv6 config changes - just playing around with defaults ...not sure why is it so either :)

Yes, Apache by default listens on all interfaces, IPv4 and IPv6 alike.

---

### Post by gyre007 on 2010-05-30
> **Bachstelze said:**
> Yes, Apache by default listens on all interfaces, IPv4 and IPv6 alike.

but the question is why am I not seeing something like this in the netstat output as well then (note the omitted "6"):

tcp       0      0 :::80                   :::*                    LISTEN

---

### Post by Bachstelze on 2010-05-30
> **gyre007 said:**
> but the question is why am I not seeing something like this in the netstat output as well then (note the omitted "6"):

tcp       0      0 :::80                   :::*                    LISTEN

Because on Linux, both IPv4 and IPv6 requests are handled by the IPv6 socket (via IPv4-to-IPv6 mapping). See [http://httpd.apache.org/docs/2.2/bind.html](http://httpd.apache.org/docs/2.2/bind.html)

(The correct answer would've been "because tcp means IPv4 and you can't listen for IPv4 requests on an IPv6 address, but I assumed what you meant was [font=monospace]tcp  0  0  0.0.0.0:80  0.0.0.0:*  LISTEN[/font].)

So yes, it is a somewhat gross simplification to say that Apache listens on both IPv4 and IPv6. It actually listens only on IPv6 and handles IPv4 requests through IPv4-to-IPv6 mapping.

---

