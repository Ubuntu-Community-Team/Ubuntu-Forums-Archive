---
title: "DNS Server installed from surces"
date: 2017-10-27
forum: Server Platforms
---

### Post by r0nnie on 2017-10-27
Greetings,

First of all I would like to say that I am completely new to the Ubuntu world. So please be gentle with the noob that I am.

I'm trying to install and configure a DNS Bind Server from sources. It's for an exam I've been trying to pass for a while now and need to practice and understand simple notions about the DNS Server.

So the subject is to install a primary server for two zones. The server must be installed in a specified folder from sources (only the --prefix parameter is a must). I have extracted, set the directory using ./configure, compiled and installed the server. My configuration is as follows:

named.conf (created by me in the etc folder, since the file is not created when installing from sources):
[HTML]options {        recursion no;
        allow-query { any; };
};

zone "10.ro"{
        type master;
        file "/skills/named/var/10.ro";
};

zone "c10.ro"{
        type master;
        file "/skills/named/var/c10.ro"; };[/HTML]

10.ro - zone1:
[HTML]$TTL 100
10.ro.          SOA     ns1.10.ro       admin\.dns.10.ro. 1 3600 60 7200 100

                NS      ns1.10.ro
ns1.10.ro       A       192.168.0.11 www.10.ro       A       192.169.0.11[/HTML]

c10.ro - zone2
[HTML]$TTL 100
c10.ro.          SOA     ns1.c10.ro       admin\.dns.c10.ro. 1 3600 60 7200 100

                NS      ns1.c10.ro
ns1.c10.ro       A       192.168.0.11 www.c10.ro       A       192.169.0.11[/HTML]

I do not know if the files are correct but when typing named-checkzone all is well, the zones are loaded.
When I type named - g I get the following lines:
[HTML]26-Oct-2017 13:26:03.110 starting BIND 9.3.3 -g26-Oct-2017 13:26:03.112 loading configuration from '/skills/named/etc/named.conf'
26-Oct-2017 13:26:03.112 no IPv6 interfaces found
26-Oct-2017 13:26:03.112 listening on IPv4 interface lo, 127.0.0.1#53
26-Oct-2017 13:26:03.112 binding TCP socket: address in use
26-Oct-2017 13:26:03.112 listening on IPv4 interface enp0s25, 192.168.0.11#53
26-Oct-2017 13:26:03.112 binding TCP socket: address in use
26-Oct-2017 13:26:03.113 couldn't add command channel 127.0.0.1#953: address in use
26-Oct-2017 13:26:03.113 ignoring config file logging statement due to -g option
26-Oct-2017 13:26:03.113 zone 10.ro/IN: loaded serial 1
26-Oct-2017 13:26:03.113 zone c10.ro/IN: loaded serial 2 26-Oct-2017 13:26:03.113 running[/HTML]

I do not know how to start/stop/restart the server since service and systemctl commands cant find bind9 installation (I've set the PATH directive to bin and sbin folders). And I don't understand if the server is working and how am I able to be sure of it. Any kind of help is appreciated. Many thanks!

---

### Post by SeijiSensei on 2017-10-27
First try
```
host www.google.com 127.0.0.1
```

then
```
host ns1.c10.ro 127.0.0.1
```

Do they resolve?

Get rid of the back slash in the SOA records.  I'm surprised the zones loaded with that character there.

A standard installation of BIND9 from source puts all its files in /usr/local/.  I haven't compiled BIND from scratch for a while, but I believe everything is installed to /usr/local/named.  If not, then the daemon will be in /usr/local/sbin, the configuration in /usr/local/etc, and so forth.

---

### Post by r0nnie on 2017-10-28
Many thanks for your reply!


Well I must install the server in a specified folder for this task. The folder must be /skills/named (in root directory). There I get the folders "etc, bin, sbin...". I assigned the PATH=$PATH:/skills/named/bin and PATH=$PATH:/skills/named/sbin.

I removed the backslash. 

host [www.google.com]("http://www.google.com") 127.0.0.1
Result is:
[HTML]Using domain server:
Name: 127.0.0.1
Address: 127.0.0.1#53
Aliases: 
[/HTML]

host ns1.c10.ro 127.0.0.1
Result is:
[HTML]Using domain server:
Name: 127.0.0.1
Address: 127.0.0.1#53
Aliases: 

Host ns1.c10.ro not found: 3(NXDOMAIN)[/HTML]

Many, many thanks and appreciations!

---

### Post by SeijiSensei on 2017-10-28
Have you read the [manual page for named]("https://linux.die.net/man/8/named")?  You can't just put the installation in some random location and expect it to work.  You'll need at least to use the "-c" command-line parameter to tell the program where it's configuration file is located.  

I don't know who gave you this assignment, but it makes no sense to build an application from scratch and not let it follow its conventions for where files are located.

Because we have rules about helping with schoolwork projects, I'll just leave you with these couple of hints.

---

### Post by SeijiSensei on 2017-10-28
Have you read the [manual page for named]("https://linux.die.net/man/8/named")?  You can't just put the installation in some random location and expect it to work.  You'll need at least to use the "-c" command-line parameter to tell the program where it's configuration file is located.  

I don't know who gave you this assignment, but it makes no sense to build an application from scratch and not let it follow its conventions for where files are located.  Also /usr/local or /opt are the conventionally agreed-upon places to install software not taken from the distribution's repositories.

Because we have rules about helping with schoolwork projects, I'll just leave you with these couple of hints.

---

