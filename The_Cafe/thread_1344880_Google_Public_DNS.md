---
title: "Google Public DNS"
date: 2009-12-03
forum: The Cafe
---

### Post by abhiroopb on 2009-12-03
Google just posted something interesting in their [Offical Google Blog]("http://googleblog.blogspot.com/").

"[Introducing Google Public DNS]("http://googleblog.blogspot.com/2009/12/introducing-google-public-dns.html")". The article explains quite simply what Google is doing, that is launching their own public DNS resolver.

They provide [easy instructions]("http://code.google.com/speed/public-dns/docs/using.html") to change your current DNS settings to the one's provided by Google. Being Google they even provide instructions for linux and ubuntu!!

[B]The DNS IP Addresses are:
8.8.8.8
8.8.8.4[/B]

If you don't want to open the link the steps to change your DNS in ubuntu are as follows:

1. Back up /etc/resolv.conf:
```
sudo cp /etc/resolv.conf /etc/resolv.conf.auto
```

2. Edit /etc/dhcp3/dhclient.conf:
```
sudo gedit /etc/dhcp3/dhclient.conf
```

**NB:** the instructions to change the DNS to the Google Public DNS in ubuntu suggests editing the file "/etc/dhcp3/dhcpclient.conf". In Ubuntu 9.10 (Karmic) I have not been able to find this file, however, other posts suggests editing the file: "/etc/dhcp3/dhclient.conf".

3. If there is a line containing domain-name-servers, write down the IP addresses for future reference.

4. Replace that line with, or add, the following line:
```
prepend domain-name-servers 8.8.8.8,8.8.4.4;
```

5. Save and exit.

6. Restart any Internet clients you are using.

7. To test just go to any website ([www.google.com](www.google.com)). If it does not work check out the "[testing your settings]("http://code.google.com/speed/public-dns/docs/using.html#testing")" section in the instructions.

After running a few quick tests the speed is really really fast. I never realised changing the DNS could make such a huge difference! It also corrects errors such as [www.wikipedia.com](www.wikipedia.com) to [www.wikipedia.org](www.wikipedia.org) (although most browsers do this anyway).

Only concern really is the big one about privacy. I'm not overly familiar with how the DNS system works so I cannot comment on whether my changing my ISP given DNS to Google's means they can literally watch every website I go to.

Thoughts?

---

### Post by Bachstelze on 2009-12-03
Google: all your DNS are belong to us.

(Would make a motivator, but I'm lazy.)

---

### Post by abhiroopb on 2009-12-03
well played!

---

### Post by sdowney717 on 2009-12-03
> Only concern really is the big one about privacy. I'm not overly familiar with how the DNS system works so I cannot comment on whether my changing my ISP given DNS to Google's means they can literally watch every website I go to.

you betcha they can.
but really anything you do on the web is tracked or trackable.
any nefarious or raunchy site has your ip address, time of visit, what you did, etc...
all the emails you send, someone else can read. you are an open book.

so if you download illegal movies, your isp knows you went there. I wonder if someday they will block sites to sanitize the web.

---

### Post by Tristam Green on 2009-12-03
> **Bachstelze said:**
> Google: all your DNS are belong to us.

(Would make a motivator, but I'm lazy.)

This is no lie.

Sorry Goog, you just made a line that I'm not crossing :|

---

### Post by abhiroopb on 2009-12-03
Their [privacy policy]("http://code.google.com/speed/public-dns/faq.html#privacy") regarding the Google Public DNS says that nothing is actually collected or stored (but who knows!)

---

### Post by Tristam Green on 2009-12-03
> **abhiroopb said:**
> After running a few quick tests the speed is really really fast. I never realised changing the DNS could make such a huge difference! It also corrects errors such as [www.wikipedia.com](www.wikipedia.com) to [www.wikipedia.org](www.wikipedia.org) (although most browsers do this anyway).

Only concern really is the big one about privacy. I'm not overly familiar with how the DNS system works so I cannot comment on whether my changing my ISP given DNS to Google's means they can literally watch every website I go to.

Thoughts?

I use the OpenDNS servers, and have been ever since the 2007 AT&T weekend DNS meltdown.  They work way faster than the other DNS servers I've seen.

---

### Post by bluelamp999 on 2009-12-03
> **Tristam Green said:**
> I use the OpenDNS servers, and have been ever since the 2007 AT&T weekend DNS meltdown.  They work way faster than the other DNS servers I've seen.

So do I. Has anybody noticed any speed diff between the Google & OpenDNS servers?

---

### Post by JBAlaska on 2009-12-03
SWEET! Thanks for the info abhiroopb.

I am forever having to call ISP's to get their DNS servers to set up users static IP's

And now many ISP's are very reluctant to give out this info...their like "you need to use DHCP-why do you need our DNS numbers"

This makes my job a bit easier.

[COLOR="Blue"]Edit: they seem damn fast so far.[/COLOR]

---

### Post by abhiroopb on 2009-12-03
Glad to help.

Although, like many others mentioned OpenDNS has been around for quite a while. Never used it myself!

---

### Post by Regenweald on 2009-12-03
Well if they are going to succeed in turning the web into thin clients logging into googlenet, they need to make the internet a lot faster. 

I for one know that they are not datamining my life because they made a website and told me so :) and I know that they won't share of log my internet access because they are just too nice :) 

Google, making the internet faster... because we love you.

---

### Post by JBAlaska on 2009-12-03
I've used OpenDNS from time to time, but I have run into issues with them not propagating new domains quickly..hopefully Google will be better at this

---

### Post by Grenage on 2009-12-03
Oh noes, they can see what sites we resolve... wait... so can any DNS provider.

No reason I'm going to trust opendns or my ISP any more than google; I appreciate that there is now another freely-usable DNS provider with the bandmwidth to cope.

---

### Post by whiskeylover on 2009-12-03
Comcast started redirecting non existing domains to their own server instead of returning a NXDOMAIN. Good think they provided a way to turn it off. I like the default "Server Not Found" page instead of a bunch of ads.

---

### Post by PhoHammer on 2009-12-03
> **bluelamp999 said:**
> So do I. Has anybody noticed any speed diff between the Google & OpenDNS servers?

I just switched to Google's and there is a *very* noticeable speed difference. Way faster.

---

### Post by lovinglinux on 2009-12-03
Slower for me. I wasn't even able to open Ubuntu forums page. Switched back to my ISP DNS.

---

### Post by wavery on 2009-12-03
I know this isn't a Google thread, but since we're talking about it...to use this type of service, would I change the DNS settings in my OS *_and_* my router?  Google's How To page makes it seem like either/or.

---

### Post by lovinglinux on 2009-12-03
> **wavery said:**
> I know this isn't a Google thread, but since we're talking about it...to use this type of service, would I change the DNS settings in my OS *_and_* my router?  Google's How To page makes it seem like either/or.

If your OS is configured to use DHCP, which is the default for Ubuntu, than you just need to change the router.

---

### Post by crimesaucer on 2009-12-03
I'm using it and so far it seems the same as OpenDNS. (I never liked being redirected to the openDNS yahoo page so at least that should be better)

---

### Post by Ylon on 2009-12-03
All my national (Italy)ISP are forced to filter (china style) DNS in order to prevent access to international poker on line rooms, and p2p sites.
So, I commonly use opendns... that google thing sound interesting: I will try some time.
Anyway, the besy way is:


```
sudo cp /etc/resolv.conf /etc/resolv.conf.back
sudo gedit /etc/resolv.conf
```

overwrite everithing with just this
```
# No... definitely NetworkManager didn't generate this.
nameserver 8.8.8.8
nameserver 8.8.4.4
```

and```
sudo chattr +i  /etc/resolv.conf
```






revert back:
```
sudo chattr -i  /etc/resolv.conf
mv /etc/resolv.conf.back /etc/resolv.conf
```

---

### Post by Knowle on 2009-12-03
> **wavery said:**
> I know this isn't a Google thread, but since we're talking about it...to use this type of service, would I change the DNS settings in my OS *_and_* my router?  Google's How To page makes it seem like either/or.I would say it depends on how you want to use it. You can change it on the computer only and that's the only place the change will take effect, for testing purposes and so on. If you change it in your router, all computers that connect to it would automatically use the DNS server provided by Google.

---

### Post by doas777 on 2009-12-03
is there an app to rotate dns server addresses from a list dynamically? I have a list of a few, and it would be nice if they

---

### Post by Ylon on 2009-12-03
> **doas777 said:**
> is there an app to rotate dns server addresses from a list dynamically? I have a list of a few, and it would be nice if they

a cronjob with something like?
```

sudo echo "nameserver x.x.x.x" > /etc/resolv.conf
sudo echo "nameserver x.x.x.x" >> /etc/resolv.conf
```

---

### Post by speedwell68 on 2009-12-03
I have been using OpenDNS for a while now and OpenDNS seems to be faster for me than Google's DNS.  I have to say that I am dubious of using it anyway, Google have far too many fingers in far too many pies these days.  It started with a search engine, then mapping and street imaging, online apps, next came a browser, an OS and now DNS servers.

---

### Post by karlmp on 2009-12-03
waaaaaaaaaaaaay to much

---

### Post by mmix on 2009-12-03
no thanks, I am running my own DNS server : 127.0.0.1

ISP/GOOGLE/GOV is big brother.

---

### Post by madhi19 on 2009-12-03
I just tried it and jesus it fast! And am comparing it to OpenDNS that use to be the all time champion!

---

### Post by crimesaucer on 2009-12-03
So I had OpenDNS with dnsmasq, now I have GoogleDNS with dnsmasq..... I'm just wondering if using something like Bind is better than both of these?

---

### Post by doas777 on 2009-12-03
> **crimesaucer said:**
> So I had OpenDNS with dnsmasq, now I have GoogleDNS with dnsmasq..... I'm just wondering if using something like Bind is better than both of these?


i use bind to map my internal zone, and forward requests to another ISPs servers if it is a remote address. that way I get both internal and external resolution with a single query. I'm not sure what else it would get you, unless you could perform zone transfers from the root servers.

---

### Post by Crunchy the Headcrab on 2009-12-03
> **JBAlaska said:**
> SWEET! Thanks for the info abhiroopb.

I am forever having to call ISP's to get their DNS servers to set up users static IP's

And now many ISP's are very reluctant to give out this info...their like "you need to use DHCP-why do you need our DNS numbers"

This makes my job a bit easier.

[COLOR=Blue]Edit: they seem damn fast so far.[/COLOR]
I'm confused why you can't get this information yourself.  If your machines are running dhcp, then the router already knows the dns server of the isp.  Am I mistaken?

---

### Post by doas777 on 2009-12-03
> **Crunchy the Headcrab said:**
> I'm confused why you can't get this information yourself.  If your machines are running dhcp, then the router already knows the dns server of the isp.  Am I mistaken?

yes, but lots of people use static IPs in their home networks, or use complicated multi network configurations, or just run their own dhcp server. in these cases, you cannot retrieve it from the isp via dhcp. you can get an ip without dns names, but not the other way around. if you have a dhcp server of your own, how do you configure it to pass a dns address to clients, if you don't know it?

---

### Post by wavery on 2009-12-03
I tried it and there is a significant speed increase.

---

### Post by handy on 2009-12-03
I found OpenDNS to be very useful, whilst I was using an ISP who changed their DNS addresses quite regularly.  Which was something that made life tough as I was having trouble with the early versions of Ubuntu, loosing my DNS addresses.  The fix was to prepend the DNS addresses in dhclient.conf as follows:

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

Anyway, back on topic. I found OpenDNS to be a bit faster than when I used that ISP.  I later changed ISPs, & found that they were at least as fast if not faster than OpenDNS, so I now use them.

I also think that though Google have done a LOT of good things for our internet experience, I don't want to give them any more power/control.  Google is just too big, & monopolies are not healthy.

---

### Post by madhi19 on 2009-12-03
> **handy said:**
> I found OpenDNS to be very useful, whilst I was using an ISP who changed their DNS addresses quite regularly.  Which was something that made life tough as I was having trouble with the early versions of Ubuntu, loosing my DNS addresses.  The fix was to prepend the DNS addresses in dhclient.conf as follows:

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

Anyway, back on topic. I found OpenDNS to be a bit faster than when I used that ISP.  I later changed ISPs, & found that they were at least as fast if not faster than OpenDNS, so I now use them.

I also think that though Google have done a LOT of good things for our internet experience, I don't want to give them any more power/control.  Google is just too big, & monopolies are not healthy.

I did not get that bug since at least Jaunty and the main reason that bug existed was because the network manager did not "sudo" you when you wanted to edit a connection! Now you have to give your password and that bug is gone.

---

### Post by pwnst*r on 2009-12-03
*chants*

"tin foi hats, tin foil hats*

---

### Post by Dr. C on 2009-12-03
> **handy said:**
> I found OpenDNS to be very useful, whilst I was using an ISP who changed their DNS addresses quite regularly.  Which was something that made life tough as I was having trouble with the early versions of Ubuntu, loosing my DNS addresses.  The fix was to prepend the DNS addresses in dhclient.conf as follows:

prepend domain-name-servers 208.67.222.222, 208.67.220.220;

Anyway, back on topic. I found OpenDNS to be a bit faster than when I used that ISP.  I later changed ISPs, & found that they were at least as fast if not faster than OpenDNS, so I now use them.

I also think that though Google have done a LOT of good things for our internet experience, I don't want to give them any more power/control.  Google is just too big, & monopolies are not healthy.

One needs to ask the question here what is in it for Google? They are after all a for profit company. If one has good clean fast DNS either because one has a good DNS provider or one runs one's own DNS then Google DNS is simply of no interest. 

The target of this move is the poor ISP DNS providers in particular those providers who monetize typos by redirecting NXDOMAIN to the ads of a Google competitor. Yahoo! in particular has been very active in making deals with ISP's to purchase traffic. This is a Canadian example  [http://help.yahoo.com/l/ca/rogers/portal/]("http://help.yahoo.com/l/ca/rogers/portal/") Who is paying Rogers here for the NXDOMAIN traffic? In the US who is behind the NXDOMAIN DNS redirection at Comcast? Again Yahoo! [http://arstechnica.com/tech-policy/news/2009/08/comcasts-dns-redirect-service-goes-nationwide.ars]("http://arstechnica.com/tech-policy/news/2009/08/comcasts-dns-redirect-service-goes-nationwide.ars")

This is nothing more than a move by Goggle to regain traffic back, that it has earned by providing better organic search results, from competitors that are placing resources into purchasing typo traffic from ISPs, and in the process causing no end of problems to end users. The Internet would be a much better place if these competitors actually placed these resources into improving their own organic search results to compete with Google on the basis of search quality.

This a a very smart move on the part of Google. The free market at its best.

---

### Post by handy on 2009-12-03
> **madhi19 said:**
> I did not get that bug since at least Jaunty and the main reason that bug existed was because the network manager did not "sudo" you when you wanted to edit a connection! Now you have to give your password and that bug is gone.

I'm glad to hear that it has been sorted out. Hopefully for everyone.  It was a total pain in the rr's in the early days of Ubuntu. Even more so due to my inexperience with Linux overall.

> **FineE said:**
> 
One needs to ask the question here what is in it for Google? They are after all a for profit company. If one has good clean fast DNS either because one has a good DNS provider or one runs one's own DNS then Google DNS is simply of no interest. 

The target of this move is the poor ISP DNS providers in particular those providers who monetize typos by redirecting NXDOMAIN to the ads of a Google competitor. Yahoo! in particular has been very active in making deals with ISP's to purchase traffic. This is a Canadian example  [http://help.yahoo.com/l/ca/rogers/portal/]("http://help.yahoo.com/l/ca/rogers/portal/") Who is paying Rogers here for the NXDOMAIN traffic? In the US who is behind the NXDOMAIN DNS redirection at Comcast? Again Yahoo! [http://arstechnica.com/tech-policy/news/2009/08/comcasts-dns-redirect-service-goes-nationwide.ars]("http://arstechnica.com/tech-policy/news/2009/08/comcasts-dns-redirect-service-goes-nationwide.ars")

This is nothing more than a move by Goggle to regain traffic back, that it has earned by providing better organic search results, from competitors that are placing resources into purchasing typo traffic from ISPs, and in the process causing no end of problems to end users. The Internet would be a much better place if these competitors actually placed these resources into improving their own organic search results to compete with Google on the basis of search quality. 

It is certainly easy for me to accept that theory. Thanks. :)

> **FineE said:**
> 
This a a very smart move on the part of Google. The free market at its best.

I agree that it is a smart move for Google. I still doubt I'll ever use it. I prefer to support the little fish when & where I can.  Even if that just means choosing to not strengthen a giant anymore than necessary.

---

### Post by abhiroopb on 2009-12-03
> **handy said:**
> I'm glad to hear that it has been sorted out. Hopefully for everyone.  It was a total pain in the rr's in the early days of Ubuntu. Even more so due to my inexperience with Linux overall.



It is certainly easy for me to accept that theory. Thanks. :)



I agree that it is a smart move for Google. I still doubt I'll ever use it. I prefer to support the little fish when & where I can.  Even if that just means choosing to not strengthen a giant anymore than necessary.


That's a good point, but, there was a time 10 odd years ago when google was a little fish as well.

---

### Post by bluelamp999 on 2009-12-03
Script here to compare DNS servers - [http://www.manu-j.com/blog/opendns-alternative-google-dns-rocks/403/](http://www.manu-j.com/blog/opendns-alternative-google-dns-rocks/403/)

Interesting...

---

### Post by vishzilla on 2009-12-04
funny. my ISPs DNS trumps google in all accounts. given the frequent websites i visit

---

### Post by treesurf on 2009-12-04
I think a lot of it depends on where you are in relation to the DNS servers.

---

### Post by gnomeuser on 2009-12-04
I originally switched to OpenDNS to get around my ISP censoring certain websites and also agreeing to a wider censorship without transparency in the name of combating childporn - which incidently has done nothing to lessen said problem and instead serves as a means to blocks reported sites without as far as I can tell any oversight. 

It always annoyed me that OpenDNS hijacked bad requests, not so much for the ads but for the use for Yahoo for the searching but I understand that is how they make money.

I am pretty happy with the Google DNS server right now for the reason that it does not hijack anything, however I am worried that they might bend easily to certain kinds of pressure and start blocking websites.

---

### Post by doorknob60 on 2009-12-04
I'll stick to OpenDNS, since I have no problems with it, and it has some cool features.

---

### Post by sdowney717 on 2009-12-04
[http://www.manu-j.com/blog/opendns-alternative-google-dns-rocks/403/](http://www.manu-j.com/blog/opendns-alternative-google-dns-rocks/403/)
i just tried pinging a couple sites in the list and my isp cox was faster than google on one and slower on the other
Am i wrong?

> 
DNS Results (Irvine, California, US) 
Domain  	Google  	4.2.2.2  	OpenDNS
lifehacker.com 	65       	12 	52
facebook.com 	65 	        16 	50


> PING lifehacker.com (69.60.7.199) 56(84) bytes of data.
64 bytes from 69.60.7.199: icmp_seq=1 ttl=247 time=41.7 ms
64 bytes from 69.60.7.199: icmp_seq=2 ttl=247 time=41.2 ms
64 bytes from 69.60.7.199: icmp_seq=3 ttl=247 time=40.0 ms
64 bytes from 69.60.7.199: icmp_seq=4 ttl=247 time=39.0 ms
64 bytes from 69.60.7.199: icmp_seq=5 ttl=247 time=39.9 ms


> scott@scott-desktop:~$ ping facebook.com
PING facebook.com (69.63.181.12) 56(84) bytes of data.
64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=1 ttl=244 time=101 ms
64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=2 ttl=244 time=101 ms
64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=3 ttl=244 time=107 ms
64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=4 ttl=244 time=101 ms
64 bytes from www-11-01-snc2.facebook.com (69.63.181.12): icmp_seq=5 ttl=244 time=101 ms
^C



---

### Post by Grenage on 2009-12-04
Pinging has nothing to do with DNS; once it's resolved, it's resolved.

---

### Post by sdowney717 on 2009-12-04
well i switched to google dns and facebook is pinging faster
if you ping the name then it must be resolving the name to a number

i noticed this, facebook chaged its ip 
cox is 69.63.181.12
google 69.63.184.142

> PING lifehacker.com (69.60.7.199) 56(84) bytes of data.
64 bytes from 69.60.7.199: icmp_seq=1 ttl=247 time=40.5 ms
64 bytes from 69.60.7.199: icmp_seq=2 ttl=247 time=40.5 ms
64 bytes from 69.60.7.199: icmp_seq=3 ttl=247 time=40.0 ms
^C64 bytes from 69.60.7.199: icmp_seq=4 ttl=247 time=39.2 ms

--- lifehacker.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 15178ms
rtt min/avg/max/mdev = 39.204/40.064/40.531/0.593 ms
scott@scott-desktop:~$ ping facebook.com
PING facebook.com (69.63.184.142) 56(84) bytes of data.
64 bytes from www-10-03-ash1.facebook.com (69.63.184.142): icmp_seq=1 ttl=245 time=17.4 ms
64 bytes from www-10-03-ash1.facebook.com (69.63.184.142): icmp_seq=2 ttl=245 time=17.8 ms
64 bytes from www-10-03-ash1.facebook.com (69.63.184.142): icmp_seq=3 ttl=245 time=16.0 ms
64 bytes from www-10-03-ash1.facebook.com (69.63.184.142): icmp_seq=4 ttl=245 time=17.5 ms


---

### Post by Grenage on 2009-12-04
Yes; it resolves it once, caches it, and uses the cache.

---

### Post by handy on 2009-12-04
> **abhiroopb said:**
> That's a good point, but, there was a time 10 odd years ago when google was a little fish as well.

There was a time when MS was just a couple of guys who got a bunch of their friends to come & help them code.  They were a bunch of smelly young hackers working in a few rooms of the accommodation they rented.

MS is now somewhat of a monopoly. I choose to support them as little as possible.

Both Google & MS have done great things for the world of computing.  They have also done not so great things.

Google's database has to be the largest in the world.  They have very sophisticated ways of working with that data & they have apparently done work with it for various governments.

Scary stuff I think.

---

### Post by sdowney717 on 2009-12-04
ok, i modded his batch file and ran it using cox in the list
except for two international sites, .fr and .uk, cox is faster

> scott@scott-desktop:~/Desktop$ ./newfile
4.2.2.2 lifehacker.com 17 msec
8.8.8.8 lifehacker.com 17 msec
208.67.222.222 lifehacker.com 15 msec
68.105.28.11 lifehacker.com 14 msec

4.2.2.2 facebook.com 16 msec
8.8.8.8 facebook.com 17 msec
208.67.222.222 facebook.com 20 msec
68.105.28.11 facebook.com 9 msec

4.2.2.2 manu-j.com 17 msec
8.8.8.8 manu-j.com 18 msec
208.67.222.222 manu-j.com 15 msec
68.105.28.11 manu-j.com 19 msec

4.2.2.2 reddit.com 261 msec
8.8.8.8 reddit.com 18 msec
208.67.222.222 reddit.com 16 msec
68.105.28.11 reddit.com 10 msec

4.2.2.2 tb4.fr 17 msec
8.8.8.8 tb4.fr 17 msec
208.67.222.222 tb4.fr 16 msec
68.105.28.11 tb4.fr 107 msec

4.2.2.2 bbc.co.uk 15 msec
8.8.8.8 bbc.co.uk 18 msec
208.67.222.222 bbc.co.uk 99 msec
68.105.28.11 bbc.co.uk 105 msec


---

### Post by sdowney717 on 2009-12-04
i added in 1 more cox dns and ran them all again
and cox is by far the faster
68.105.28.12 is best.

but really this seems rather pointless to me.
even 100 ms you would not notice

> 
4.2.2.2 lifehacker.com 15 msec
8.8.8.8 lifehacker.com 17 msec
208.67.222.222 lifehacker.com 16 msec
68.105.29.11 lifehacker.com 44 msec
68.105.28.12 lifehacker.com 10 msec

4.2.2.2 facebook.com 17 msec
8.8.8.8 facebook.com 16 msec
208.67.222.222 facebook.com 16 msec
68.105.29.11 facebook.com 44 msec
68.105.28.12 facebook.com 11 msec

4.2.2.2 manu-j.com 16 msec
8.8.8.8 manu-j.com 18 msec
208.67.222.222 manu-j.com 16 msec
68.105.29.11 manu-j.com 47 msec
68.105.28.12 manu-j.com 49 msec

4.2.2.2 reddit.com 38 msec
8.8.8.8 reddit.com 17 msec
208.67.222.222 reddit.com 16 msec
68.105.29.11 reddit.com 43 msec
68.105.28.12 reddit.com 9 msec

4.2.2.2 tb4.fr 17 msec
8.8.8.8 tb4.fr 17 msec
208.67.222.222 tb4.fr 15 msec
68.105.29.11 tb4.fr 190 msec
68.105.28.12 tb4.fr 10 msec

4.2.2.2 bbc.co.uk 16 msec
8.8.8.8 bbc.co.uk 23 msec
208.67.222.222 bbc.co.uk 15 msec
68.105.29.11 bbc.co.uk 169 msec
68.105.28.12 bbc.co.uk 9 msec





---

### Post by JBAlaska on 2009-12-04
> **handy said:**
> There was a time when MS was just a couple of guys who got a bunch of their friends to come & help them code.  They were a bunch of smelly young hackers working in a few rooms of the accommodation they rented. 

Then it came to pass that Xerox said.."Come have a look at this GUI thingy we invented, because we are sure it won't amount to anything...

Now thoust "smelly young hackers" haveith more money than GO...well the big guy lol..

---

### Post by mmix on 2009-12-04
my DNS configuration :)

[img]http://ubuntuforums.org/attachment.php?attachmentid=138513&stc=1&d=1259927754[/img]

---

### Post by karlmp on 2009-12-04
is irrelevant, I always get different results all the time.

---

### Post by PhoHammer on 2009-12-04
> **handy said:**
> 
Google's database has to be the largest in the world.  They have very sophisticated ways of working with that data & they have apparently done work with it for various governments.

Scary stuff I think.

Sources, maybe?

---

### Post by crimesaucer on 2009-12-04
My results had OpenDNS just a bit fastest (I didn't try my cox dns):

```

4.2.2.2 lifehacker.com 10 msec
8.8.8.8 lifehacker.com 9 msec
208.67.222.222 lifehacker.com 9 msec
4.2.2.2 facebook.com 10 msec
8.8.8.8 facebook.com 10 msec
208.67.222.222 facebook.com 9 msec
4.2.2.2 manu-j.com 10 msec
8.8.8.8 manu-j.com 14 msec
208.67.222.222 manu-j.com 10 msec
4.2.2.2 reddit.com 31 msec
8.8.8.8 reddit.com 10 msec
208.67.222.222 reddit.com 7 msec
4.2.2.2 tb4.fr 9 msec
8.8.8.8 tb4.fr 14 msec
208.67.222.222 tb4.fr 9 msec
4.2.2.2 bbc.co.uk 9 msec
8.8.8.8 bbc.co.uk 10 msec
208.67.222.222 bbc.co.uk 7 msec
4.2.2.2 digg.com 8 msec
8.8.8.8 digg.com 10 msec
208.67.222.222 digg.com 7 msec
4.2.2.2 surfline.com 126 msec
8.8.8.8 surfline.com 9 msec
208.67.222.222 surfline.com 10 msec
4.2.2.2 ubuntuforums.org 86 msec
8.8.8.8 ubuntuforums.org 9 msec
208.67.222.222 ubuntuforums.org 7 msec
4.2.2.2 bbs.archlinux.org 10 msec
8.8.8.8 bbs.archlinux.org 10 msec
208.67.222.222 bbs.archlinux.org 9 msec
4.2.2.2 archlinux.org 11 msec
8.8.8.8 archlinux.org 11 msec
208.67.222.222 archlinux.org 9 msec
4.2.2.2 deviantart.com 79 msec
8.8.8.8 deviantart.com 9 msec
208.67.222.222 deviantart.com 8 msec

```

```

4.2.2.2 lifehacker.com 8 msec
8.8.8.8 lifehacker.com 12 msec
208.67.222.222 lifehacker.com 9 msec
4.2.2.2 facebook.com 10 msec
8.8.8.8 facebook.com 9 msec
208.67.222.222 facebook.com 7 msec
4.2.2.2 manu-j.com 10 msec
8.8.8.8 manu-j.com 11 msec
208.67.222.222 manu-j.com 95 msec
4.2.2.2 reddit.com 10 msec
8.8.8.8 reddit.com 11 msec
208.67.222.222 reddit.com 7 msec
4.2.2.2 tb4.fr 8 msec
8.8.8.8 tb4.fr 10 msec
208.67.222.222 tb4.fr 9 msec
4.2.2.2 bbc.co.uk 87 msec
8.8.8.8 bbc.co.uk 11 msec
208.67.222.222 bbc.co.uk 90 msec
4.2.2.2 digg.com 9 msec
8.8.8.8 digg.com 9 msec
208.67.222.222 digg.com 7 msec
4.2.2.2 surfline.com 10 msec
8.8.8.8 surfline.com 11 msec
208.67.222.222 surfline.com 8 msec
4.2.2.2 ubuntuforums.org 10 msec
8.8.8.8 ubuntuforums.org 10 msec
208.67.222.222 ubuntuforums.org 8 msec
4.2.2.2 bbs.archlinux.org 9 msec
8.8.8.8 bbs.archlinux.org 9 msec
208.67.222.222 bbs.archlinux.org 9 msec
4.2.2.2 archlinux.org 8 msec
8.8.8.8 archlinux.org 10 msec
208.67.222.222 archlinux.org 8 msec
4.2.2.2 deviantart.com 10 msec
8.8.8.8 deviantart.com 9 msec
208.67.222.222 deviantart.com 10 msec

```

I'm gonna stay with GoogleDNS for a while just to see how it is for a few weeks.

---

### Post by RATM_Owns on 2009-12-04
BTW, if you miss OpenDNS shortcuts, in Firefox:

1. Create a bookmark for the page you want a shortcut for.
2. Right-click the bookmark in the Bookmarks Menu.
3. Enter your shortcut name in the "Keyword" section.
4. Click "Save."

Tah-dah.

---

### Post by handy on 2009-12-04
> **JBAlaska said:**
> Then it came to pass that Xerox said.."Come have a look at this GUI thingy we invented, because we are sure it won't amount to anything...

Now thoust "smelly young hackers" haveith more money than GO...well the big guy lol..

That Xerox invitation to come to see what Xerox was up to at their PARC facility wasn't given to MS, but to Apple.  Steve Jobs traded I forget the number now (but lets say $1,000,000 worth of Apple shares) for the privilege.  & so was born the Macintosh, as Steve Jobs saw Alan Kay's, Smalltalk GUI & was gob-smacked, knowing that this is how the world will use computers in the future.  Alan Kay & others actually went & worked for Apple for some time.

The early days were so much more personal, than the monstrous corporations that have developed from teams of 2 people, such as those that started both Apple & MS.

If only the management of Xerox could have got out of their copier mentality, the world of computing would most likely hardly have heard of the likes of Jobs, Wozniak, Gates, Paul Allen, Balmer & co.

---

### Post by handy on 2009-12-04
> **PhoHammer said:**
> Sources, maybe?

I found sources well over a year ago, just by searching the internet.

China was one of the countries I remember that Google worked for, I believe that certain agencies in the U.S. were also known to talk with Google, as certain U.S. security services monitor the internet.

---

### Post by PurposeOfReason on 2009-12-06
[http://googleblog.blogspot.com/2009/12/introducing-google-public-dns.html](http://googleblog.blogspot.com/2009/12/introducing-google-public-dns.html)

[quote=]This Blog Google Blogs Web Blog News 
This Blog     
.Google Blogs     
.Web     
.Blog      
News      
Introducing Google Public DNS
 
12/03/2009 08:35:00 AM 
When you type [www.wikipedia.org]("http://www.wikipedia.org/") into your browser's address bar, you expect nothing less than to be taken to Wikipedia. Chances are you're not giving much thought to the work being done in the background by the Domain Name System, or DNS.

Today, as part of our ongoing effort to make the web faster, we're launching our own public DNS resolver called Google Public DNS, and we invite you to try it out.

Most of us aren't familiar with DNS because it's often handled automatically by our Internet Service Provider (ISP), but it provides an essential function for the web. You could think of it as the switchboard of the Internet, converting easy-to-remember domain names — e.g., [www.google.com]("http://www.google.com/") — into the unique Internet Protocol (IP) numbers — e.g., 74.125.45.100 — that computers use to communicate with one another.

The average Internet user ends up performing hundreds of DNS lookups each day, and some complex pages require multiple DNS lookups before they start loading. This can slow down the browsing experience. Our research has shown that speed matters to Internet users, so over the past several months our engineers have been working to make improvements to our public DNS resolver to make users' web-surfing experiences faster, safer and more reliable. You can read about the specific technical improvements we've made in our product documentation and get installation instructions from our product website.

If you're web-savvy and comfortable with changing your network settings, check out the Google Code Blog for detailed instructions and more information on how to set up Google Public DNS on your computer or router. 

As people begin to use Google Public DNS, we plan to share what we learn with the broader web community and other DNS providers, to improve the browsing experience for Internet users globally. The goal of Google Public DNS is to benefit users worldwide while also helping the tens of thousands of DNS resolvers improve their services, ultimately making the web faster for everyone.

Posted by Prem Ramaswami, Product Manager                      [/quote]

Privacy issues aside, I like it. Comcast's DNS servers are poo.

---

### Post by NoaHall on 2009-12-06
We know, we know.

---

### Post by Bachstelze on 2009-12-06
As long as it doesn't start deciding where domains it doesn't own point, like the one mentioned below...

---

### Post by LeifAndersen on 2009-12-06
I'm more worried about it disappearing than anything else: [http://leifandersen.net/2009/12/04/googles-public-dns-success-or-failure/](http://leifandersen.net/2009/12/04/googles-public-dns-success-or-failure/)

I mean, they don't really have a good track record for keeping products up 24/7, than again, who does?

---

### Post by NCLI on 2009-12-06
> **VMC said:**
> Speaking of Google, have you seen the latest offer, for free [DNS]("http://googleblog.blogspot.com/2009/12/introducing-google-public-dns.html"). What do you thing?
It's the fastest DNS service I've ever tried, so I'm very satisfied with it, and using it as my primary DNS address. Sure, Google probably uses my data to earn money by customizing their ads to fit my browsing habit, but I really don't care about that. I'm not doing anything I don't want others to see, and if I were, I'd use TOR.

---

### Post by newbuntuxx on 2009-12-07
I started using Google Public DNS because it is free, fast, and it does not re-direct me to an ad when I type an incorrect address! I already pay my ISP for the connection. They should provide me with an ad-free connection because I pay them 50 bucks every month!

Now, for those of you complaining about privacy issues, do us a favor and go to: [www.google.com](www.google.com), in the search box type: "google public dns privacy", the 6th result from the top is:

[http://code.google.com/speed/public-dns/privacy.html](http://code.google.com/speed/public-dns/privacy.html)

Click it:

> What we log
Google Public DNS stores two sets of logs: temporary and permanent. The temporary logs store the full IP address of the machine you're using. We have to do this so that we can spot potentially bad things like DDoS attacks and so we can fix problems, such as particular domains not showing up for specific users. 

We delete these temporary logs within 24 to 48 hours. 

In the permanent logs, we don't keep personally identifiable information or IP information. We do keep some location information (at the city/metro level) so that we can conduct debugging, analyze abuse phenomena and improve the Google Public DNS prefetching feature. We don't correlate or combine your information from these logs with any other log data that Google might have about your use of other services, such as data from Web Search and data from advertising on the Google content network. After keeping this data for two weeks, we randomly sample a small subset for permanent storage.

Finally, if you're interested in knowing what else we log when you use Google Public DNS, here is the full list of items that are included in our permanent logs: 

Request domain name, e.g. [www.google.com](www.google.com) 
Request type, e.g. A (which stands for IPv4 record), AAAA (IPv6 record), NX, TXT, etc. 
Transport protocol on which the request arrived, i.e. TCP or UDP 
Client's AS (autonomous system or ISP), e.g. AS15169 
User's geolocation information: i.e. geocode, region ID, city ID, and metro code 
Response code sent, e.g. SUCCESS, SERVFAIL, NXDOMAIN, etc. 
Whether the request hit our frontend cache 
Whether the request hit a cache elsewhere in the system (but not in the frontend) 
Absolute arrival time in seconds 
Total time taken to process the request end-to-end, in seconds 
Name of the Google machine that processed this request, e.g. machine101 
Google target IP to which this request was addressed, e.g. one of our anycast IP addresses (no relation to the user's IP) 

As for the "Big brother theories" well, that can be said about every ISP in the world! Every ISP in the world will have to release information to government parties if there is a court order. ITS THE LAW.

Those who don't agree with this law should contact their member of parliament, congressman, senator etc...Or should nominate themselves for those positions and change the law.

The other solution of course is to house google's servers on the moon, where no government has any jurisdiction, but I am sure a few people here will come up with the "Big Alien theory"...

Lastly, you can set your ISP's DNS and open dns as your third and fourth dns servers, in case google's servers fail.

---

### Post by newbuntuxx on 2009-12-07
> **NCLI said:**
> It's the fastest DNS service I've ever tried, so I'm very satisfied with it, and using it as my primary DNS address. Sure, Google probably uses my data to earn money by customizing their ads to fit my browsing habit, but I really don't care about that. I'm not doing anything I don't want others to see, and if I were, I'd use TOR.

[http://code.google.com/speed/public-dns/privacy.html:](http://code.google.com/speed/public-dns/privacy.html:)

> We don't correlate or combine your information from these logs with any other log data that Google might have about your use of other services, such as data from Web Search and data from advertising on the Google content network.

---

### Post by mivo on 2009-12-07
> **newbuntuxx said:**
> I started using Google Public DNS because it is free, fast, and it does not re-direct me to an ad when I type an incorrect address!

They get something much more value from you than they could ever get by showing you a few ads whenever you type in an incorrect address.

---

### Post by ice60 on 2009-12-07
> **newbuntuxx said:**
> I started using Google Public DNS because it is free, fast, and it does not re-direct me to an ad when I type an incorrect address! I already pay my ISP for the connection. They should provide me with an ad-free connection because I pay them 50 bucks every month!

Now, for those of you complaining about privacy issues, do us a favor and go to: [www.google.com](www.google.com), in the search box type: "google public dns privacy", the 6th result from the top is:

[http://code.google.com/speed/public-dns/privacy.html](http://code.google.com/speed/public-dns/privacy.html)

Click it:



As for the "Big brother theories" well, that can be said about every ISP in the world! Every ISP in the world will have to release information to government parties if there is a court order. ITS THE LAW.

Those who don't agree with this law should contact their member of parliament, congressman, senator etc...Or should nominate themselves for those positions and change the law.

The other solution of course is to house google's servers on the moon, where no government has any jurisdiction, but I am sure a few people here will come up with the "Big Alien theory"...

Lastly, you can set your ISP's DNS and open dns as your third and fourth dns servers, in case google's servers fail.
aol kept similar logs and it was very easy to track down most people when they decided to make the logs public.

there are ways to keep your privacy if you want to (running your own dns and tor i suppose), but the thing about google is the amount of personal information one company has and how everything they do is aimed at getting more personal information. i don't like them and don't think they have an honourable cause - gathering the world's information to make it searchable.

anyway, there's already a good free dns - opendns run by one of the world's dns experts. he proved himself with the kaminsky vulnerability. why give more privacy away to google with new unproven dns servers? the permanent logs will likely be used to help with their targeted ads

---

### Post by PryGuy on 2009-12-07
> **bachstelze said:**
> google: All your dns are belong to us.

(would make a motivator, but i'm lazy.)+1

---

### Post by afeasfaerw23231233 on 2009-12-07
How to compare the performance of DNS server? By nslookup command? Is it possible that Google's DNS faster than my ISP's DNS?

---

### Post by Twitch6000 on 2009-12-07
> **bluelamp999 said:**
> So do I. Has anybody noticed any speed diff between the Google & OpenDNS servers?

Well my upload is faster when using googles public dns.

Download is about the same.

---

### Post by v8YKxgHe on 2009-12-07
removed

---

### Post by PurposeOfReason on 2009-12-07
Everybody might want to try this, beats guessing.

[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

---

### Post by lovinglinux on 2009-12-07
> **AlexC_ said:**
> Erm, that has nothing to do with DNS. DNS basically is a phonebook, find a name, give an address. It is done once and cached (most of the time). Changing DNS servers does not speed up your internet connection, never has - never will. 

Sure, if you get a slow DNS server the initial DNS lookup will be slow, and will appear to make your connection slow. However, your connection speed is 100% the same.

What you're seeing is simply fluctuations in your ISP, I have it all the time. For example, my normal download speed here in good ol' UK is about 70kb/s, however past few days I have been getting 250kb/s. Give it a week and I'll most likely be down to 20kb/s. No ISP in the world can give you a constant connection speed, impossible. Also depends on the other end of the network, as well. 

There is loads of variables, however DNS is not one of them. In fact, DNS is not even needed.

I agree.

Just to complement, there are some [Firefox settings](http://blog.taragana.com/index.php/archive/simple-firefox-hacks-to-boost-performance/) that allow you to tweak DNS caching, so the browser makes less DNS queries. This helps to speed up browsing, specially on those days your DNS server is slow. But as already mentioned above, the download speed is the same, what changes is that the site is contacted faster.

---

### Post by hobo on 2009-12-08
The IP addresses on the first post are half correct. Should be:

**8.8.8.8 and 8.8.4.4**

---

### Post by newbuntuxx on 2009-12-08
> **ice60 said:**
> 
anyway, there's already a good free dns - opendns run by one of the world's dns experts. he proved himself with the kaminsky vulnerability. why give more privacy away to google with new unproven dns servers? the permanent logs will likely be used to help with their targeted ads

[http://www.opendns.com/privacy/](http://www.opendns.com/privacy/)


> OpenDNS runs a Domain Name System (DNS) service. DNS translates a domain name (e.g., [www.example.com](www.example.com)) into the corresponding numerical address (e.g., 192.0.34.166) that allows your system to access the domain over the network. **OpenDNS' DNS service collects the date and time of each DNS request and the domain name requested ("Statistics"). Statistics are not personally identifiable but are correlated to your IP address and your account if you have signed up for one. OpenDNS uses Statistics to provide you with the DNS service and for internal analysis.**

**In addition, OpenDNS also collects potentially personally-identifying information like the Internet Protocol (IP) addresses from which DNS requests are made. For its DNS services, OpenDNS temporarily stores logs to monitor and improve our quality of service, and to collect high-level aggregate Statistics. For customers without an account, OpenDNS generally removes the IP address from its logs within 2 business days, except for backup or archival copies which are not generally accessed in the normal course of business.** For customers with an account, such Statistics and data may be stored for as long as the account is open (although, customers with an account may also choose, at any time, to have DNS data purged automatically from within their account).

As you can see, their privacy policies are pretty much the same. In fact, I think google's is much more transparent! 

They all collect personal and non-personal information and store it, some temporarily and some permanently. You just can't run a fast and successful DNS server operation without knowing what your users want!

So, at the end of the day, it is up to the user to make his choice.

---

### Post by newbuntuxx on 2009-12-08
> **PurposeOfReason said:**
> Everybody might want to try this, beats guessing.

[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

Thats great! Thanks

---

### Post by pwnst*r on 2009-12-08
> **PurposeOfReason said:**
> Everybody might want to try this, beats guessing.

[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

nice, thank you!

---

### Post by gutterslob on 2009-12-08
> **PurposeOfReason said:**
> Everybody might want to try this, beats guessing.

[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

Interesting.... I'll try it out.
Thank you.

---

### Post by brookie on 2009-12-08
That's a sweet tool! My results showed that opendns was 87% faster than the dns server I was using. It also suggested using comcast as the secondary dns because it is closest and also fast. I was using the 4.2.2.* servers before. Sweet!

ps...a second test showed that comcast was 104% faster than open dns. it looks like speeds are changing depending on how busy the dns servers are.

---

### Post by infestor on 2009-12-08
> **PurposeOfReason said:**
> Everybody might want to try this, beats guessing.

[http://code.google.com/p/namebench/](http://code.google.com/p/namebench/)

how do i run the tgz file graphically?

---

### Post by pwnst*r on 2009-12-08
> **brookie said:**
> That's a sweet tool! My results showed that opendns was 87% faster than the dns server I was using. It also suggested using comcast as the secondary dns because it is closest and also fast. I was using the 4.2.2.* servers before. Sweet!

ps...a second test showed that comcast was 104% faster than open dns. it looks like speeds are changing depending on how busy the dns servers are.

did you compare with google's dns?

---

### Post by brookie on 2009-12-08
The readme.txt file has instructions on how to install the app permanently. I just ran it from the folder I extracted it to by cd-int to that directory and running the command given in the readme file (./namebench.py). When it finished it said it made a file in my tmp dir so then copy/paste that link (**/tmp/namebench_2009-12-08_1101.htm**) into your browser to get a graphical output of the results. 

For example: 
* Saving html summary report to **/tmp/namebench_2009-12-08_1101.htm**l
- Rendering template: html.tmpl
- Saving rendered html output
* Saving request details to /tmp/namebench_2009-12-08_1101.csv 

I didn't install it permanently yet.

---

### Post by brookie on 2009-12-08
> **pwnst*r said:**
> did you compare with google's dns?

Google's DNS seems like it's third in the list every time.

Note - after adding google's dns 8.8.8.8 to my router and wireless connection my syslog gets hammered with these: 
Dec  8 11:24:06 (my computer name) kernel: [12740.446808] [UFW BLOCK] IN=eth1 OUT= MAC=00:0e:35:ec:07:04:00:13:10:8e:c9:55:08:00 SRC=74.125.159.99 DST=(MY_IP_ADDRESS) LEN=40 TOS=0x00 PREC=0x20 TTL=50 ID=45185 PROTO=TCP SPT=443 DPT=50603 WINDOW=0 RES=0x00 RST URGP=0 

I use gufw enabled to deny all by default. So is google pinging me back or something? I didn't see these in the logs when using other dns servers.

---

### Post by karlmp on 2009-12-08
```
Recommended configuration (fastest + nearest):
----------------------------------------------
nameserver 8.8.8.8         # Google Public DNS
nameserver 205.234.170.215 # Tiggee US  NXDOMAIN Hijacking
nameserver 208.96.162.13   # TakePolls US



********************************************************************************
In this test, Google Public DNS is 20.7% faster than Tiggee US
********************************************************************************

```

:)

---

### Post by pwnst*r on 2009-12-08
thanks brookie, and thanks for that results list karlmp

---

### Post by Teabicky on 2010-01-07
I was having real speed issues with my internet so I tried a speed test and found that I was running at the full 10mbps I should be.  I thought I'd give google dns a whirl and all I can say is wow!!  It has made an enormous difference.

With regards to the privacy issue, I would be concerned if I was being forced by law to use such a service but I am not, it is my choice and I have other options available.... as with the google search engine really.

---

### Post by EmoDx on 2010-02-01
I have a newb questions here. I would like to set up my box to cache IP addresses and serve those up when I am surfing on that box. If not, then use resolvers of my choice. I know that Firefox can do this. But I also want the box to serve up to my localnet too. How can I go about this?

---

### Post by Trevster on 2010-02-01
Hi, this is an interesting DNS benchmarking tool that works well in wine.

[http://www.grc.com/dns/benchmark.htm]("http://www.grc.com/dns/benchmark.htm")

---

### Post by Viva on 2010-02-02
Never trust an online company no matter how big it is.

---

### Post by tjeremiah on 2010-09-29
> **newbuntuxx said:**
> [http://www.opendns.com/privacy/](http://www.opendns.com/privacy/)




As you can see, their privacy policies are pretty much the same. In fact, I think google's is much more transparent! 

They all collect personal and non-personal information and store it, some temporarily and some permanently. You just can't run a fast and successful DNS server operation without knowing what your users want!

So, at the end of the day, it is up to the user to make his choice.
its a good thing with OPENDNS that you can purge the data at anytime.

---

### Post by pwnst*r on 2010-09-29
> **Viva said:**
> Never trust an online company no matter how big it is.

Then I suggest building your own internets.

---

### Post by fatality_uk on 2010-09-29
> **pwnst*r said:**
> Then I suggest building your own internets.

Cool, i'm up for it :)

Let me see. I have about 20' of copper cables, lan cables, a spare router and an 8 port switch! It's a start.

---

### Post by Señor Banana on 2010-09-29
> **fatality_uk said:**
> Cool, i'm up for it :)

Let me see. I have about 20' of copper cables, lan cables, a spare router and an 8 port switch! It's a start.
I've been wanting to do this for quite some time, due to the bs with the government control over the internet. I don't believe they can have jurisdiction over your private network.

---

### Post by fatality_uk on 2010-09-29
> **Señor Banana said:**
> I've been wanting to do this for quite some time, due to the bs with the government control over the internet. I don't believe they can have jurisdiction over your private network.

Pretty easy really. You just need about $5 billion, a team of about 5,000 to lay cables and space for servers etc.

---

### Post by Prohibited on 2010-09-30
Sure sounds easy. Lets all chip in and try to get the $5 billion. 

Lets see here... I got $2.60 in cash to put in. What about you guys?

---

### Post by fatality_uk on 2010-09-30
> **Prohibited said:**
> Sure sounds easy. Lets all chip in and try to get the $5 billion. 

Lets see here... I got $2.60 in cash to put in. What about you guys?

*EMPTIES POCKETS*

Some lint, an Orange sim card, a piece of paper with 3/4's of an IP address *EH*, a USB data key, abut £4 in change, some cigs and a lighter.

So we have hit about £5. Only another £4,999,999,995 to go ;)

---

