---
title: "a dns cache on a dhcp server"
date: 2005-12-16
forum: Server Platforms
---

### Post by wlarsen76 on 2005-12-16
I have an ubuntu box acting as a firewall and dhcp server.  (dhcp3).  In my dhcp.conf, I had set my nameservers.. In this case they were comcast servers.
-----------------------------------------
subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.40 10.0.0.60;
    #option domain-name-servers 10.0.0.1;
    option domain-name-servers 208.39.158.1;
    option domain-name-servers 64.56.37.245;
    option routers 10.0.0.1;
}
-----------------------------------------

As you can see, there is a line commented out fo 10.0.0.1.  hostname lookups were slow from time to time, so I had decided to install daemon-tools and get a dnscache up and running.

Well, the dnscache runs well..  if I were to run:

host [www.google.com](www.google.com) localhost

while running:

tail -f /service/dnscache/log/main/current

I can see it working.

My question is....(it may be simple and it may not be), how can I run the dns cache so that internal machines ask the cache first, and if it is not there ask my other specified dns addresses?

Now, keep in mind I would rather NOT modify dhclient on client boxes because it is the way it is by default for a reason.  I would rather have any dhclient overwrite it's own resolv.conf whenever it wants, and let the "thinking" be left up to the dhcp/dns server.  I have no problem modifying dhclient on the actual dns/dhcp server if I have to, but I somehow don't think that "that" is the solution here.

Now, I "think" it "might" work if i uncomment the 10.0.0.1 in that code that I just posted, but I'm not to keen on possibly taking my network down just to see.  Can anybody confirm?  I've been searching for awhile and just have not found this specific issue.

Thanks,

Wells

---

### Post by cactus on 2005-12-16
I use dnsmasq, which has a dhcp (simple one) server, and a dns cache/resolver component. It is simply a great solution for a small setup. The dns cacher portion can be used as a caching forward lookup dns server as well, without the dhcp daemon component if you dont need it.

---

### Post by wlarsen76 on 2005-12-16
....In which case, I would only specify 10.0.0.1 in dhcp.conf and then probably specify where to forward lookup in the dnsmasq conf file?

Interesting...  Thank you.  I'm quite fond of having service dirs watch dnscache, but I think I will give this a try.

Thanks again,

---

### Post by LordHunter317 on 2005-12-17
Yes, just uncommenting that will work.  But you don't want your clients doing DNS fallback, as it tends to be slow.  You'd rather have your DNS server forward as necessary.

---

### Post by wlarsen76 on 2005-12-17
Yes, you are right.  Problem is solved and here is how I solved it for the next person that asks.

I have my dhcp server only dish out 10.0.0.1 to my dhcp clients, so dns is completly behind the scenes for them and as far as they are concerned it just works.
--------------------------------------------------
subnet 10.0.0.0 netmask 255.255.255.0 {
    range 10.0.0.40 10.0.0.60;
    option domain-name-servers 10.0.0.1;
    option routers 10.0.0.1;
}
----------------------------------------------------

NEXT:

touch /etc/dnscache/root/ip/127.0.0.1                          #localhost
touch /etc/dnscache/root/ip/10.0.0                                #my subnet

echo 1 > /etc/dnscache/env/FORWARDONLY
echo '208.39.158.1' > /etc/dnscache/root/servers/@     #your isp's primary nameserver
echo '64.56.37.245' >> /etc/dnscache/root/servers/@   #if you isp has a secondary nameserver

echo '127.0.0.1' > /etc/resolv.conf                                   #not sure if I had to do this - better be safe

And finallly the clincher.... Don't forget to punch a hole in your firewall to your local subnet for port 53 (DNS)  And yes, it took me an hour to realize this. (a little slow on the uptake..)

This url was extremly helpfull.  (Although not for the firewall issue)

[http://cr.yp.to/djbdns/run-cache-x-home.html](http://cr.yp.to/djbdns/run-cache-x-home.html)

---

### Post by wlarsen76 on 2005-12-17
... All of the above assumes, that djbdns and daemontools are already installed.

Thank you cactus for the suggestion of using dnsmasq, however I didn't actually try it out.  I am just familiar with the supervise script and I knew that I was missing somthing very minimal.

I did to a little research and it does seem to be exactly the right thing for the situation that I was in, but whatever.  Now I know how to setup dnscache if I ever need it in the future.

Thanks All

---

