---
title: "Ubuntu browser hijacker plugin"
date: 2013-10-27
forum: Security
---

### Post by kimmo.sauren on 2013-10-27
Hello all,

I am very new to Ubuntu (but liking the OS very much), so I am very sorry if this comes to wrong forum.

I have managed to get a browser hijacker in my firefox. I have isolated the plugin to be "Ubuntu online Accounts 0.5".
Picture of it: [http://postimg.org/image/yzpqrjltz/](http://postimg.org/image/yzpqrjltz/)

It seems to be the normal searchresult redirector.
Search Google Pic: [http://postimg.org/image/ti082k6iz/](http://postimg.org/image/ti082k6iz/)
Result when clicked:[http://postimg.org/image/xtxoshlcj/](http://postimg.org/image/xtxoshlcj/)
And if you reloaded it gave the correct page: [http://postimg.org/image/vk2eo1lzx/](http://postimg.org/image/vk2eo1lzx/)

Also if you tried to open virus scanning websites, it gave you many times errors like this:
[http://postimg.org/image/sviq5rq87/](http://postimg.org/image/sviq5rq87/)

Also it tried to give me wrong certificates:
[http://postimg.org/image/yex4bxwgt/](http://postimg.org/image/yex4bxwgt/)

Now all this seemed to start after I opened a account to hostgator for a website. I am not saying that hostgator is to blame. I surfed to many WordPress sites and other sites before this.
I tried to download an another webrowser (NetSurf webrowser) to get rid of plugin for blocking removal sites. Weird thing was that the NetSurf got the same infection somewhere immediately.

I know that just removing or disabling that plugin gets rid of the problems (and clearing history and cookies), but is this something that Ubuntu community should be worried with?

---

### Post by kimmo.sauren on 2013-10-27
Well it seems that it is actually not that plug in, but something else.
Trying to locate the plugin....

---

### Post by CharlesA on 2013-10-29
Something is redirecting your browser traffic to hostgator. Try running Firefox in safe mode and see what happens.

---

### Post by Frogs Hair on 2013-10-29
Search Hostgator redirects , I found a number of results . I think it is connected to creating an account with HG.

---

### Post by sandyd on 2013-10-29
> **kimmo.sauren said:**
> Hello all,

I am very new to Ubuntu (but liking the OS very much), so I am very sorry if this comes to wrong forum.

I have managed to get a browser hijacker in my firefox. I have isolated the plugin to be "Ubuntu online Accounts 0.5".
Picture of it: [http://postimg.org/image/yzpqrjltz/](http://postimg.org/image/yzpqrjltz/)

It seems to be the normal searchresult redirector.
Search Google Pic: [http://postimg.org/image/ti082k6iz/](http://postimg.org/image/ti082k6iz/)
Result when clicked:[http://postimg.org/image/xtxoshlcj/](http://postimg.org/image/xtxoshlcj/)
And if you reloaded it gave the correct page: [http://postimg.org/image/vk2eo1lzx/](http://postimg.org/image/vk2eo1lzx/)

Also if you tried to open virus scanning websites, it gave you many times errors like this:
[http://postimg.org/image/sviq5rq87/](http://postimg.org/image/sviq5rq87/)

Also it tried to give me wrong certificates:
[http://postimg.org/image/yex4bxwgt/](http://postimg.org/image/yex4bxwgt/)

Now all this seemed to start after I opened a account to hostgator for a website. I am not saying that hostgator is to blame. I surfed to many WordPress sites and other sites before this.
I tried to download an another webrowser (NetSurf webrowser) to get rid of plugin for blocking removal sites. Weird thing was that the NetSurf got the same infection somewhere immediately.

I know that just removing or disabling that plugin gets rid of the problems (and clearing history and cookies), but is this something that Ubuntu community should be worried with?
Can you post the output of
```

dig answers.yahoo.com
host answers.yahoo.com
cat /etc/resolv.conf

```
Thanks

---

### Post by kimmo.sauren on 2013-11-02
Just found some time to investigate this more. So installed betterprivacy and noscript to be more safe and I actually thought it helped until I got them again.

I tried to connect to Arin to find out more about the IP and it gave me an add page like this:
[http://postimg.org/image/j4rttfvv1/](http://postimg.org/image/j4rttfvv1/)

So I set up a wired connectiong to my modem and set up wireshark. Reloaded the add page and captured with Wireshark. You can find a wireshark capture at:
[http://postimg.org/image/k5espnghn/](http://postimg.org/image/k5espnghn/)

So basically the Ubuntu does not use DNS to find the IP that it is using with Arin. The IP belongs to websitewelcome.com according to arin.
Interesting part is that my dnslookup shows the Arin address to be correct one. Not the one showing in Wireshark capture.

 Also /etc/resolv.conf is clean and dig shows correct answers for yahoo.

Other computers in the network work just fine so it is not like my modem is compromised.
Also the other browser NetSurf is experiensing same problems.

Will investigate this more. Somehow I feel that my dns info is compromised, but nslookup and dig has been hacked to show correct answers when used?

Any ideas?

---

### Post by CharlesA on 2013-11-02
check /etc/hosts

---

### Post by kimmo.sauren on 2013-11-03
Some outputs:
host answers.yahoo.com
```

answers.yahoo.com is an alias for geoycpi-uno-deluxe.gycpi.b.yahoodns.net.
geoycpi-uno-deluxe.gycpi.b.yahoodns.net is an alias for geoycpi-uno.gycpi.b.yahoodns.net.
geoycpi-uno.gycpi.b.yahoodns.net is an alias for eu-ycpi-uno.aycpi.b.yahoodns.net.
eu-ycpi-uno.aycpi.b.yahoodns.net has address 66.196.66.213
eu-ycpi-uno.aycpi.b.yahoodns.net has address 66.196.66.212
eu-ycpi-uno.aycpi.b.yahoodns.net has address 66.196.66.157
eu-ycpi-uno.aycpi.b.yahoodns.net has address 66.196.66.156

```

/etc/resolv.conf
```

127.0.0.1       localhost
127.0.1.1       HP-EliteBook-8460p

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

resolv.conf
```

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.1.1
search Elisa

```
dig answers.yahoo.com
```

; <<>> DiG 9.9.3-rpz2+rl.13214.22-P2-Ubuntu-1:9.9.3.dfsg.P2-4ubuntu1 <<>> answers.yahoo.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 25010
;; flags: qr rd ra; QUERY: 1, ANSWER: 7, AUTHORITY: 0, ADDITIONAL: 0

;; QUESTION SECTION:
;answers.yahoo.com.             IN      A

;; ANSWER SECTION:
answers.yahoo.com.      42      IN      CNAME   geoycpi-uno-deluxe.gycpi.b.yahoodns.net.
geoycpi-uno-deluxe.gycpi.b.yahoodns.net. 48 IN CNAME geoycpi-uno.gycpi.b.yahoodns.net.
geoycpi-uno.gycpi.b.yahoodns.net. 253 IN CNAME  eu-ycpi-uno.aycpi.b.yahoodns.net.
eu-ycpi-uno.aycpi.b.yahoodns.net. 253 IN A      66.196.66.157
eu-ycpi-uno.aycpi.b.yahoodns.net. 253 IN A      66.196.66.213
eu-ycpi-uno.aycpi.b.yahoodns.net. 253 IN A      66.196.66.212
eu-ycpi-uno.aycpi.b.yahoodns.net. 253 IN A      66.196.66.156

;; Query time: 2 msec
;; SERVER: 127.0.1.1#53(127.0.1.1)
;; WHEN: Sun Nov 03 09:03:35 EET 2013
;; MSG SIZE  rcvd: 244

```
nslookup arin.net
```

Server:         127.0.1.1
Address:        127.0.1.1#53

Non-authoritative answer:
Name:   arin.net
Address: 192.149.252.75
Name:   arin.net
Address: 192.149.252.125

```

---

### Post by kimmo.sauren on 2013-11-03
More info. 
I tried to play with foxyproxy and burb proxy to see the web traffic more clearly.
So I set up the foxyproxy and relayed all traffic normally (without local proxy) until I got the ad-page again.
I got the ad-page displayed again and I could repeat it by opening a new tab and pasting the url.

Sooo... I quicly switched foxyproxy to point to my local proxy (burb proxy) and fired up the ad-page again.
And guess what!! The ad-page was gone! 

So at least to me it seems like it is not my DNS that is corrupted, but the browser proxy settings are somehow changed when the hijack happens.
This also explains the security certificate error that I am getting for https. The wierd thing is that I always get hostgator security certificate when this happens. 
So basically it is man in the middle attack type altough I don't think it is used anything more than displaying ads.

So someone or something is changing my browser proxy settings on fly.  It is wierd that this can happen random times. 
There is no inhirent logic behind it. It seems more like timed/random event.

I don't think you can change Firefox proxy settings with JavaScript or flash? I would assume that can't happen?  I mean that would be a huge security issue.
I guess now I have to figure out what changes my proxy settings for firefox. Is there a conf file somewhere for that?

---

### Post by kimmo.sauren on 2013-11-03
Hmmm. Got the same add stuff with hostgator website.Took a wireshark capture.My computer is having getting some scripts from ec2-46-51-168-42.eu-west-1.compute.amazonaws.comhttp://46.51.168.42/notice?domain=hostgator.com&c=te-consentInteresting is that if you change the domain GET parameter to something else the server just gives you 404.So is hostgator using amazon virtual cloud for their service or is this the bad guys server?  This is getting interesting....

---

### Post by Paddy Landau on 2013-11-04
kimmo.sauren

[LIST]
[*]Please boot from a Live CD and then visit the sites. If it stops happening, you know it's on your computer. 
[/LIST]

[LIST]
[*]Otherwise, reboot your router. If the problem stops, it was in your router's cache. 
[/LIST]

[LIST]
[*]Otherwise, bypass your router (e.g. plug directly into your modem, use the Internet from your phone, ask a neighbour to use his Internet connection, go to a public WiFi).
[LIST]
[*]If the problem stops, it's in your router. 
[/LIST]
    
[/LIST]

[LIST]
[*]Otherwise, the problem is either with your ISP or further down the line. 
[/LIST]
Let us know what happens.

---

