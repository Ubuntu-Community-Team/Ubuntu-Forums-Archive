---
title: "Squid HTTP Proxy"
date: 2012-08-01
forum: Server Platforms
---

### Post by jplanter on 2012-08-01
Hello

I have been attempting to make this work and have gotten close however not quite there and was hoping someone could assist me or at least point me in the right direction. Thank you in advance :)

So here is what I am trying to accomplish:

I have a large network with a firewall/web filter. I have 200 students that are issued laptops. I would like to setup a http proxy server so when they are at home their internet connection is configured to the squid proxy server so when they surf the internet they are still filtered through my firewall/webfilter.

I attemped to set this up and the result I got was close. It would filter any attempts to view innapropriate websites however when I would try any normal website like Google it would direct me to the squid servers apache server "It Works!" page.

Any Ideas?

Here is my squid.conf file:
```

refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0 0% 0
refresh_pattern .               0       20%     4320
# Leave coredumps in the first cache dir
coredump_dir /var/spool/squid3

#acl whitelist dstdomain "/etc/squid3/whitelist.txt"

# Allow localnet machines to whitelisted sites
#http_access allow localnet whitelist

# block all other access
#http_access deny all

# allow all access
http_access allow all

```Running ubuntu server 12.04 with Squid3.

Any help is greatly appreciated. Thank You! :)

Jared

---

### Post by SeijiSensei on 2012-08-02
> **jplanter said:**
> I have a large network with a firewall/web filter. I have 200 students that are issued laptops. I would like to setup a http proxy server so when they are at home their internet connection is configured to the squid proxy server so when they surf the internet they are still filtered through my firewall/webfilter.

What's to prevent them from changing that?  Changing the proxy settings in a browser is incredibly easy.  Is the proxy buried deeper into the operating system?  Aren't you just going to create a business opportunity for competent students to help disable the proxies on their fellow students' computers?  A deeper question is why should you have any control over how the students use the Internet when they are *at home*?

As for the Squid problem itself, we need some more details.  How, exactly, is the proxy configured?  Is it simply forwarding all requests to the Squid server's public IP on port 3128?  Can we see all of squid.conf?  What do you see in /var/log/squid/access.log when you try a test connection?

---

### Post by darkod on 2012-08-02
I hope this is not thread hijacking, I need some advice too Sensei.

I am considering implementing a squid proxy at work (my first) and precisely because changing the proxy settings of the browser is easy, I was thinking about this idea:

1. Set up a box with ubuntu and enable iptables routing.
2. Install squid and change the port it's working on to 80.
3. Set the box as gateway in network settings which users can't change without admin password.

Is the general line of thought OK about the squid part? Is changing the port to 80 all that it takes? Do I need to have consideration about port 443 too?

I already know how to do the routing.

---

### Post by SeijiSensei on 2012-08-02
> **darkod said:**
> I am considering implementing a squid proxy at work (my first) and precisely because changing the proxy settings of the browser is easy, I was thinking about this idea:

1. Set up a box with ubuntu and enable iptables routing.
2. Install squid and change the port it's working on to 80.
3. Set the box as gateway in network settings which users can't change without admin password.


No, changing the port Squid listens on won't do it.  What works is to set up Squid as a transparent proxy on the egress gateway and push all requests for port 80 on external servers through the proxy.  You add an iptables rule to the gateway like this:

```
iptables -t nat -A PREROUTING -m tcp -p tcp -s 192.168.1.0/24 --dport 80 -j REDIRECT --to-ports 3128
```

replacing 192.168.1.0/24 with the appropriate subnet declaration for your network.  You also need to add the "transparent" keyword to the http_port directive in squid.conf.

That takes care of HTTP traffic, but HTTPS is a whole other can of worms.  You cannot do anything useful with HTTPS traffic in Squid because the browser will see interception by the proxy as a "man-in-the-middle" attack.  Some clever developers are far along with methods to deal with this problem, but they require a lot of configuration, including configuration on the clients.  Basically you need to create a "certificate authority" and install the CA root certificate in all the browsers.  You then create and sign a certificate for the proxy.  Now you can make use of some cute tricks in Squid 3.2 that enable it to forge the certificates of remote HTTPS hosts and send the forgeries to the browsers.  Because the browsers have the CA root certificate, they trust the proxy's forgery, and the user never knows the difference.  I've got a test version of this running right now, but the problem is it doesn't yet work with transparent proxies.  (For details on all of this read about [ssl_bump]("http://wiki.squid-cache.org/Features/SslBump") and its associated friends at the Squid Wiki.)

At my client's site with a large Squid installation, we simply route traffic for port 443 directly to the remote hosts with a variety of iptables rules to control who can go where.  Because I have organized all the Squid ACLs into separate files by function, I can use the same lists of permitted/denied hosts that we have set up for Squid to write iptables rules for HTTPS connections as well.

I've attached a copy of the squid.conf file for this site.  For reference, I use capital letters to denote lists that allow connections and small letters for lists of things that should be blocked.  This ruleset accomplishes the following:

1) uses [SquidClamAV]("http://squidclamav.darold.net/") to scan all incoming objects with ClamAV to block viruses and malware;

2) blocks infected hosts from POSTing information to IP-only websites; we had some hosts that were "checking in" with their botnet masters;

3) blocks connections to hosts in the "[Malware Block List for Squid]("http://www.malware.com.br/squid.html")" and to any hosts we have identified locally;

4) blocks other connections based on file extensions or target domains;

5) allows certain users to access social networking sites and blocks everyone else.

Maybe this will give you some useful ideas!

---

### Post by darkod on 2012-08-02
OK, it's a bit more complicated than that, but I think your idea should work. This project will wait for a while so I will open a thread when I need it and hope you see it. :)

Otherwise this will become thread hijacking. The thing is that only part of the office needs to have squid domain filtering while others need to have full access.

That's why I planned the gateway to be a Draytek router (not ubuntu box) and only the computers that need to be filtered to have an ubuntu box with squid in between themselves and the Draytek.

But your idea should work in this case too, this ubuntu box will call the transparent proxy/squid while the Draytek will simply route the other users directly outside.

---

### Post by d4m1r on 2012-08-02
> **SeijiSensei said:**
> A deeper question is why should you have any control over how the students use the Internet when they are *at home*?

Couldn't have said it better myself....

---

