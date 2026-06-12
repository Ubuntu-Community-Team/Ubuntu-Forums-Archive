---
title: "apt-get not connecting"
date: 2006-11-29
forum: Repositories &amp; Backports
---

### Post by ravikm on 2006-11-29
hi,

i am able to connect to the internet with my browser, but apt-get does not work for me. what am i doing wrong?

> Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (195.248.90.38). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (195.248.90.38). - connect (111 Connection refused)
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to in.archive.ubuntu.com:80 (195.248.90.38). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (195.248.90.38). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (195.248.90.38). - connect (111 Connection refused)
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://in.archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Could not connect to in.archive.ubuntu.com:80 (195.248.90.38). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)


---

### Post by bapoumba on 2006-11-29
Hi,
are you behind a proxy ?
What is the output of **cat /etc/apt/apt.conf** ?

If 
1- you're not behind a proxy
2- apt.conf file does not exist or shows "false" or "direct"
3- global proxy setting is "direct" (GNOME > System > Prefs > Network proxy. For KDE, it should be in K menu, somewhere ;))
then could you check if there is for some reason a proxy declared in /etc/environment ?

---

### Post by ravikm on 2006-11-30
> **bapoumba said:**
> Hi,
are you behind a proxy ?
What is the output of **cat /etc/apt/apt.conf** ?

If 
1- you're not behind a proxy
2- apt.conf file does not exist or shows "false" or "direct"
3- global proxy setting is "direct" (GNOME > System > Prefs > Network proxy. For KDE, it should be in K menu, somewhere ;))
then could you check if there is for some reason a proxy declared in /etc/environment ?

1- I am behind a proxy.
2- apt.conf shows "false".
3- Global proxy setting is through manual proxy configuration.

i have pasted the output of cat /etc/environment :
> 
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_IN"
LANGUAGE="en_IN:en"

should i specify a proxy in /etc/environment ? if yes, what is the usage?

thanks a lot.

---

### Post by bapoumba on 2006-11-30
Okay, if you are behind a proxy, you have to tell apt-get in the /etc/apt/apt.conf file. (apt does not rely upon global settings to connect to the internet, but has its own .conf file). Please read **man apt.conf** :
> http   
HTTP URIs; http::Proxy is the default http proxy to use.  It is in the standard form of [http://[](http://[)[user][:pass]@]host[:port]/
Per host proxies can also be specified by using the form              http::Proxy::<host>
with the special keyword DIRECT meaning to use no proxies. The http_proxy environment variable will over&#8208;ride all settings.
and also read the **acquire** section.

Basically, you should modify the line to make it look like :
**ACQUIRE {http:: proxy "http://<my_proxy>:<proxy_port>"};**

And disregard my comment about the environment file, it was in case you were _not_ behind a proxy and one was declared in that file, blocking access to updates.

edit : I added a blank space between http:: and proxy, it's understood as a smiley. Please take it off in your file.

---

### Post by albesan on 2006-11-30
hello,

I'm having the same problem.
here is some output:

 cat /etc/apt/apt.conf
APT::Authentication::TrustCDROM "true";
Acquire::http::Proxy "false";

$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_GB.UTF-8"
LANGUAGE="en_GB:en"


I'm not behind a proxy, as far as I know (don't know that much really) but I am behind a router.
Internet works fine, ADSL connection.  

any help/ideas appreciated.

a.

---

### Post by bapoumba on 2006-11-30
@ albesan : could you paste the error message to **sudo apt-get update** ?

---

### Post by albesan on 2006-11-30
hey,

this is what is telling me now:

$ sudo apt-get update
Password:
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

thanx.

a.

---

### Post by bapoumba on 2006-11-30
@ albesan : close synaptic and do it again. There is a lock preventing two applications to perform updates/installs etc. at the same time.

---

### Post by albesan on 2006-11-30
doh!

this is what I'm getting now:

sudo apt-get update
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to packages.freecon

that's all, it used to be a longer list...

thanks.

a.

oh no,there is more:
~$ sudo apt-get update
Errhttp://nl.archive.ubuntu.com dapper Release.gpg
  Could not connect to nl.archive.ubuntu.com:80 (32.1.7.184), connection timed out
Errhttp://packages.freecontrib.org dapper Release.gpg
  Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
Errhttp://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://archive.canonical.com dapper-commercial Release.gpg
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Errhttp://archive.ubuntu.com dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Errhttp://nl.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to nl.archive.ubuntu.com:80 (32.1.7.184), connection timed out
Errhttp://archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to nl.archive.ubunt

---

### Post by bapoumba on 2006-11-30
Well do you have a DSL modem ? I've seen that already. There are problems with DHCP and some modems (D-link if I remember correctly, some other ones too). Do you have your ISP DNS in /etc/resolv.conf ?
You might want to look at IPV6 things too. I am not much aware about all of this, I'll have a look.

---

### Post by albesan on 2006-11-30
hey,

Yes DSL modem.
IPV6 is disabled, globally and in Firefox, or at least that is what I think I've spent the last 2 days researching and trying to achieve.

About DNS entries on resolv.conf, that's the problem, I have been looking at a few posts and it seems to be a problem to do with routers and DNS entries.
The solution, forcing the good DNS entries to stay where they should.

My problem now, my ISP asigns dynamic DNS.

I don't suppose by any chance that you have any ideas on how to deal with this one??

I might start a new thread on that...

Thanks for your help :)

---

### Post by bapoumba on 2006-11-30
Okay, that's the problem then.
If you have a D-link, I went across a firmware update that solved it (on mepis though, but should be the same). I'll try to find the url again.

---

### Post by bapoumba on 2006-11-30
One other solution you might want to try : edit you /etc/dhcp3/dhclient.conf file :
[http://www.ubuntuforums.org/archive/index.php/t-250149.html]("http://www.ubuntuforums.org/archive/index.php/t-250149.html")
third post from the bottom.

Cannot find the url I was looking for :/

edit : [found it]("http://www.mepis.org/node/10306") ;)

---

### Post by albesan on 2006-11-30
hey man,

got it done finally!! thanks a lot for your help ;)

a.

---

### Post by bapoumba on 2006-12-01
> **albesan said:**
> hey man,
got it done finally!! thanks a lot for your help ;)
a.

Welcome, and you can make it "woman" ;)

---

