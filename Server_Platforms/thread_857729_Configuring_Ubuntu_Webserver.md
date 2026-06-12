---
title: "Configuring Ubuntu Webserver"
date: 2008-07-12
forum: Server Platforms
---

### Post by Brenda Watsen on 2008-07-12
Hi, I installed a Ubuntu Server but I am a little confuse about what and where I must enter some information.

Is there someone who knows his/her stuff and want to help me with this information? I don't know if I am on the right way

[COLOR="Blue"]NETWORK SETTINGS[/COLOR]

I want to give my server the name: cyber01

What must I write?

Hostname     : cyber01.mirrage.nl
Domain name  : mirrage1.nl

or

Hostname     : cyber01
Domain name  : [www.mirrage1.nl](www.mirrage1.nl)

Thanks

---

### Post by DualFusion on 2008-07-12
For the hostname all you have to write is cyber01, basically the server name.

Hope this helps,
Kevin.

---

### Post by Kleenux on 2008-07-12
Hostname : cyber01
Domain name : mirrage1.nl

---

### Post by Brenda Watsen on 2008-07-13
Thank you Guys.

I connected my router to an other router (ISP)
I forwarded port 80 to go to my  webserver (192.168.50.100)

I also modified the /etc/hosts file.


127.0.0.1 localhost
127.0.1.1 cyber01.mirrgae.nl cyber01
192.168.50.100 cyber01 [www.mirrage.nl](www.mirrage.nl)
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


Can you Guys tell me if I am on the  right way?
because I have done many modifications.
I hope that every thing is on the right place.

Thanks

---

### Post by Brenda Watsen on 2008-07-28
Hi,

Is there someone on this forum who can help?

Please...........

Thank you

---

### Post by ChumleyEX on 2008-07-28
So are you saying this isn't working or are you asking if what your doing looks ok?

---

### Post by Brenda Watsen on 2008-07-28
I don't know if I configure it good.
I am getting error message: cannot resolve hostname etc.

1) Is there a specific order how to configure this?
2) Is it right to configure the 127.0.1.1 like below or must it also be localhost instead of cyber01.mirrage.nl cyber01
3) How should I configure my webserver to not display that message again? (cannot resolve hostname)

127.0.0.1 localhost
127.0.1.1 cyber01.mirrgae.nl cyber01
192.168.50.100 cyber01 [www.mirrage.nl](www.mirrage.nl)
# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I hope you can help me with this configuration.

Thank you

---

### Post by 47_MasoN_47 on 2008-07-28
Who is hosting the domain name?  If it's somebody like Godaddy you will have to setup the DNS records to point to your IP address.  To test it you could go to [http://your.ip.address.here/](http://your.ip.address.here/) and see if it will open your site.

---

### Post by Brenda Watsen on 2008-08-03
When I am on a public network I can access my website.
When I enter [www.mirrage.nl](www.mirrage.nl) I can see my home page.
That is not the problem.
My ISP connect my pricate IP with my domain name.

My problem is:

Is the below configuration correct?
Does someone have the same configuration?

When I am on my private network and when I went to the terminal to enter some commands I am getting the error message:

sudo: unnable to resolve host cyber01

What is this error message?

I hope I am clear with my explenation.

Thanks


127.0.0.1 localhost
127.0.1.1 cyber01.mirrgae.nl cyber01
192.168.50.100 cyber01 [www.mirrage.nl](www.mirrage.nl)

---

### Post by chickpea on 2008-08-03
is the client machine trying to connect your web server from the local subnet the same as your web server machine?
if it's not, the hosts file on the client machine has to have a line "192.168.50.100 cyber01" in it as well.

---

### Post by mbeach on 2008-08-03
its my understanding that the ip address should be listed only once in the hosts file with the multiple names following.

so instead of:
127.0.0.1 localhost
127.0.1.1 cyber01.mirrgae.nl cyber01

it should be
127.0.0.1 localhost cyber01.mirrgae.nl cyber01

or, if that typo on the 127 address is deliberate and you have both somehow on the go, then disregard this post (as it may be to do with an old bug with sockets/tcp).  I would think having only the one 127 would remove your "unable to resolve" error.

EDIT:
perhaps disregard anyhow - it appears this is how Hardy sets it up by default with the two 127 addresses in hosts.  I never noticed.

---

### Post by mbeach on 2008-08-03
Similar issue here:
[http://ubuntuforums.org/showthread.php?t=878019](http://ubuntuforums.org/showthread.php?t=878019)
and here
[http://ge.ubuntuforums.com/showthread.php?t=723361](http://ge.ubuntuforums.com/showthread.php?t=723361)

---

