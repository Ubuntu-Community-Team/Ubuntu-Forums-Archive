---
title: "linuxtoday.com not accessible from Sweden?"
date: 2019-06-23
forum: The Cafe
---

### Post by webaake on 2019-06-23
I can't reach linuxtoday.com from my Ubuntu Chrome and Firefox. I get this;

An error occurred while processing your request.
Reference #97.a79a645f.1561277697.611f285

I've checked my firewall and adblocker, deleted linuxstoday cookies. Still can't reach it. So I'm thinking either linuxtoday blocks countrys outside the US, which is not uncommon since the EU GDPR regulations, or my ISP is blocking it for some obscure reason (not probable).

Anyone else from outside the US experience this?

---

### Post by The Cog on 2019-06-23
Same from the UK.

---

### Post by webaake on 2019-06-23
Thanks! Then I don't have to worry too much yet! I've come across several US sites that was blocking visitors from EU since GDPR, but they often had the courtesy of telling what they did. Some of them have since come around again.

I've googled this thing with linuxtoday but nothing has come up, yet.

---

### Post by coffeecat on 2019-06-23
UK here. I am able to get to [https://www.linuxtoday.com/](https://www.linuxtoday.com/) using Ubuntu 18.04 with either Firefox or Chrome, and from a Chromebook, but the website is very slow.

---

### Post by webaake on 2019-06-23
Yeah, the error response takes a long time, so it might be they're having server problems. But I'll try some other DNS servers too.

---

### Post by ajgreeny on 2019-06-23
UK here as well, but I get the same pageblock as the OP using Xubuntu 18.04 and Firefox.

---

### Post by The Cog on 2019-06-23
Interesting. I still can't get them. I tried both my normal ISP (Virgin Media) and a VPN.

---

### Post by webaake on 2019-06-23
Changing DNS didn't help. Pinging or trying to surf directly to IP (70.42.23.51) does not work either.

---

### Post by The Cog on 2019-06-23
Interesting. I still can't get them. I tried both my normal ISP (Virgin Media) and a VPN.
And I can't post their url here either, so there is some filtering going on.
Having tried to post their url (a curl trace) I can't update my posts here either.
Seems I can update my post provided I don't put certain contents in - like the curl output gets me logged out of the Ubuntu forums.

---

### Post by coffeecat on 2019-06-23
Curiouser and curiouser. I am still able to get to [https://www.linuxtoday.com/](https://www.linuxtoday.com/) , albeit slowly. And just to add some more data to the mix. I've tried with two internet connections. The first with my adsl service where the ISP uses their own nameservers. The second through a WISP that uses google's nameservers. Both successful, although glacially slow.

> **webaake said:**
> Changing DNS didn't help.

Did you try Google's nameservers - 8.8.8.8 and 8.8.4.4? 

> **The Cog said:**
> 
And I can't post their url here either, so there is some filtering going on.

Have I got the right URL? As you can see, I've posted it twice now.

---

### Post by The Cog on 2019-06-23
OK, I'll try something. I'll post this plan, then use curl to try to read from that web site. I'll edit this post adding a numbered result with each step. I will be using my VPN which exits through a UK hosting provider's data centre. I will be using 1.1.1.1 for my DNS resolution...
1: 
Before using curl, I did a ping. That worked, resolved address was 23.43.27.23.
2:
Curl gave me the error processing message. Will try to post that next.
3:
I failed to post the curl transcript by editing this post. I got a 403 error and "Forbidden
You don't have permission to access /editpost.php on this server." So let's try just to update my post with this paragraph.
4: 
That was OK (cut-down item 3 was allowed). So now I will try to post just the command I used for curl:
5:
And the curl command was: ```
curl -k https://www.linuxtoday.com/
```
6:
OK, I was able to post that. Now for the complete transcript but with the error response reference number redacted...
7:
Redacting the reference number didn't help. Edit not allowed. So this is just to see if I can edit my post at all any more
8: 
Clearly I can still post ordinary text. It's something in the contents of the transcript that's getting my update refused. Maybe it's the http tags - I'll try to post the http body contents only
9:
```
An error occurred while processing your request.<p>
Reference #97.b48f655f.1561295516.12809fce
```
10:
So maybe all this post has done is to prove that I can't post text that looks like real http tags into this forum. The "You don't have permission to access /editpost.php on this server." is somewhat unhelpful though.

Anyway, the upshot is that I consistently get the message that there was an error processing my request for [www.linuxtoday.com](www.linuxtoday.com). If I use curl with a -v flag I can see a valid-looking certificate come back immediately, and then after about a 10 second pause is the HTTP error message. I think the certificate is being issued by a reverse proxy, and the reverse proxy is unable to get any response from the web service behind it.

@coffeecat: Are you resolving to the same IP address that I am?
```
~$ host www.linuxtoday.com
www.linuxtoday.com is an alias for www.quinstreet.com.edgekey.net.
www.quinstreet.com.edgekey.net is an alias for e8980.b.akamaiedge.net.
e8980.b.akamaiedge.net has address 23.43.27.23
```

---

### Post by webaake on 2019-06-23
Niether 8.8.8.8 nor 1.1.1.1 worked. Pinging does not work either (but that could be blocked in other ways I guess)

---

### Post by oldos2er on 2019-06-23
Not an Ubuntu support question, moved to Cafe.

---

### Post by coffeecat on 2019-06-23
> **The Cog said:**
> @coffeecat: Are you resolving to the same IP address that I am?
```
~$ host www.linuxtoday.com
www.linuxtoday.com is an alias for www.quinstreet.com.edgekey.net.
www.quinstreet.com.edgekey.net is an alias for e8980.b.akamaiedge.net.
e8980.b.akamaiedge.net has address 23.43.27.23
```


Yep.

```
~$ host www.linuxtoday.com
www.linuxtoday.com is an alias for www.quinstreet.com.edgekey.net.
www.quinstreet.com.edgekey.net is an alias for e8980.b.akamaiedge.net.
e8980.b.akamaiedge.net has address 23.43.27.23
```

But something interesting. A few minutes ago I tried opening the link in your post and got:

> An error occurred while processing your request.

Reference #97.b48f655f.1561303143.1328216b 

That was the first time I've seen the error page. But then trying again less than 5 minutes later, it resolved and I was able to view the linuxtoday website. Perhaps an intermittent problem somewhere and I was lucky up until a few minutes ago. It's still extremely slow when it does work.

---

### Post by igorlopez on 2019-06-25
Has been like this for at least a week now(connecting from Sweden).
The response varies only in the reference number
> An error occurred while processing your request.

Reference #97.xxxxxxxx.xxxxxxxxxx.xxxxxxxx

It always responds reasonably fast (~8ms) on ping requests.

---

### Post by webaake on 2019-06-30
I just got thru! Yayy! Will see if it holds out...

PS Mailed linuxtoday at their site about this. Hope they come back to me.

---

### Post by 4-nick-1 on 2019-07-01
I'm getting the same error (UK) 95% of the time for about two weeks now :(

Different IP for me: e8980.b.akamaiedge.net has address 104.127.30.28

It's ping-able ok, so something to do with their web server (apache or whatever they're using) or CMS I guess. Hopefully your mail gets through and they fix their site soon, but will probably have to start looking for alternatives instead.

---

### Post by webaake on 2019-07-02
No reply from them as of yet. But I'll mail them again with some exerpts from this thread. It workd for me just now, again. (from Sweden)

---

### Post by 4-nick-1 on 2019-07-02
I've just been experimenting, and discovered that if I connect through a free proxy ([https://www.hidemyass.com/en-gb/proxy](https://www.hidemyass.com/en-gb/proxy)), then I can connect to LinuxToday every time (as long as I don't choose UK as the server, which gives me a 404 error instead). 

I still can't connect directly from UK, so there's presumably some kind of filtering being employed. That might help them narrow the problem down if they're interested, but thanks for emailing them.

---

### Post by coffeecat on 2019-07-02
> **4-nick-1 said:**
> 
I still can't connect directly from UK, so there's presumably some kind of filtering being employed.

A filter that, presumably, doesn't affect the two different UK ISP's that I successfully used to connect directly to linuxtoday.com on the day this thread was started. See post #10.

And which still work today.

---

### Post by 4-nick-1 on 2019-07-03
> **coffeecat said:**
> A filter that, presumably, doesn't affect the two different UK ISP's that I successfully used to connect directly to linuxtoday.com on the day this thread was started. See post #10.

And which still work today.

Interesting. I was guessing that since I was able to connect through the proxy via my ISP, but not directly from my ISP, that it must have been IP filtering of somekind. Maybe linuxtoday's servers didn't like my http request for some other reason, which the proxy modified, but yours was ok to begin with.

My work ISP (different, but also UK based) would generally result in the same error. I had intermittent success, but when it worked, wasn't slow in any way.

Anyway at the time of typing, from my work ISP I can currently now connect again without error, although there's not much in the way of articles to read: [https://imagebin.ca/v/4mjg2M759nbI](https://imagebin.ca/v/4mjg2M759nbI)

---

### Post by 4-nick-1 on 2019-07-04
Still didn't work from home last night, but now currently producing errors again from work this morning as well. Still works through HMA, so will stick with that solution.

---

### Post by webaake on 2019-07-13
Still no luck here. And no response on my mail to them.

---

### Post by oksanareynuk on 2019-07-16
I'm not sure that the information is relevant, since the question was asked 3 weeks ago, but everything is fine with me.

---

### Post by lykeion on 2019-07-22
I think this is still relevant, I still cannot access it from sweden, and I would like to know of any email answers from linux today

---

### Post by nsi-fusion on 2019-08-14
Still relevant, I am having the same problems from Virgin UK, EE mobile and from BBC guest network so three different ISPs,... Will test later with VPN terminating in USA...

---

### Post by 4-nick-1 on 2019-08-16
I can access less than 1% of the time from my home ISP (Virgin UK), and about 90% at my work. 

I tried with different country endpoints with my own VPN provider, and it works some of the time. So far it's worked all of the time using the free HMA proxy (with USA server), so I just use that if it's unavailable through whichever ISP I'm using at the time.

---

### Post by nsi-fusion on 2019-08-24
So I did few test from my home and workplace. It looks like there is some filtering going on as I have a hit or miss unless I use VPN. Connecting to Surfshark solves the issue. And it does not matter if I am connecting to UK or any other country... Why would Linux Today limit access to anyone??

---

### Post by irv on 2019-09-02
Check out this webpage. I am not having this problem, but you might find this interesting.
[https://www.privacyend.com/how-to-unblock-websites-on-chrome/]("https://www.privacyend.com/how-to-unblock-websites-on-chrome/")

---

### Post by webaake on 2020-03-06
Still big problems reaching linuxtoday.com. And since I started this thread I've changed ISP (fiber as well). It's getting worse. I don't believe my new ISP is blocking this and not my former ISP either. I mean, all other Linux web sites, like Ubuntu forums, OMG Ubuntu , LXser, Linux Insider and wide range of other US and European web sites work flawlessly. It must be something to do with linuxtoday and their servers/hosting. And they don't respond to emails.

By the way VPN is not my cup of tea.

---

### Post by DuckHook on 2020-03-07
There are only a limited number of options. If VPN is not your cup of tea, then you further cut down your already constrained options.

It is possible that linuxtoday unknowingly uses a webhost that is on some ban list for ISPs due to their willingness to host malware/spam/darkweb. Different ISPs have different ban policies (and use different lists) which might account for the large variation in user connection experiencs (I can connect just fine). This is a pure, wild-eyed guess. There is absolutely no evidence so far that this is the case.

If you won't do VPN and the linuxtoday guys are unresponsive, then the only remaining thing I can think of is to contact your ISP.

---

### Post by webaake on 2020-03-08
The problem is that it's intermittent. Yesterday I could reach the linuxtoday site, but not today. But it seems to be getting worse and worse. But, as you say, I might contact my ISP.

---

### Post by Skaperen on 2020-03-08
using my VPN in NL i am able to get there with both HTTP and HTTPS.  i do see that without www. (e.g. the apex address) i get a different IP address than i get for [www.linuxtoday.com](www.linuxtoday.com).  they are using Akamai Edgekey for [www.linuxtoday.com](www.linuxtoday.com) but not for linuxtoday.com.  try including the "www." if you haven't been using it.  also, Edgekey does a double CNAME (a CNAME that refers directly to another CNAME).  this is technically not allowed by DNS standards (i'm guessing because a reference can be made to the correct host directly).  most DNS resolvers don't care and accept it, anyway.  maybe your's doesn't.  or, maybe there's a failure mode with double CNAME that i am unaware of.  or maybe that first server (without [www.)](www.)) is having issues (it worked for me just now).

i do notice that [www.linuxtoday.com](www.linuxtoday.com) at first shows no ad, then quickly reloads with one.  i don't know why they don't have one when it first loads, which is not hard to do.  perhaps it didn't load one the first time because ny VPN's IP address is in NL (in EU) and they used JS to detect that and load a fallback ad and it fails for some places.  try disabling JS to see if you get any content that way.

---

### Post by khelben1979 on 2020-03-09
I'm from Sweden too, and I had to use a VPN service to access linuxtoday.com too! The ISP provider that is being used here is Telia which is pretty much dominating the ISP companies over here. I used to check the news from Linuxtoday at a daily basis x amount of years ago.. so this was completely new to me.

---

### Post by webaake on 2020-03-09
I have another relatively big ISP here in Sweden too. I had Telia before, both ISP:s with the same problem. There's no logic to the ISP:s doing some wierd filtering, when all other sites can be reached without VPN. Well I haven't tested ALL other sites :) , but other big foreign sites like newspapers, TV-stations, Amazon, Ebay, other Linux sites works just fine. 

I'm dreading calling my ISP though, I suspect the support doesn't even know what DNS is. That's last on the list. Do you remember the old Windows support? "Reformat your harddisk and reinstall" Goddag yxskaft!

---

### Post by CelticWarrior on 2020-03-09
> **webaake said:**
> I'm dreading calling my ISP though, I suspect the support doesn't even know what DNS is. That's last on the list. Do you remember the old Windows support? "Reformat your harddisk and reinstall" Goddag yxskaft!


Yeah... But honestly, what else would you expect from an outsourced service with people earning minimum wages?

---

### Post by webaake on 2020-03-09
Had some time on my hands and tested dig +trace;

```
dig +trace www.linuxtoday.com 

; <<>> DiG 9.11.3-1ubuntu1.11-Ubuntu <<>> +trace www.linuxtoday.com
;; global options: +cmd
.			385093	IN	NS	f.root-servers.net.
.			385093	IN	NS	g.root-servers.net.
.			385093	IN	NS	h.root-servers.net.
.			385093	IN	NS	m.root-servers.net.
.			385093	IN	NS	j.root-servers.net.
.			385093	IN	NS	k.root-servers.net.
.			385093	IN	NS	a.root-servers.net.
.			385093	IN	NS	d.root-servers.net.
.			385093	IN	NS	c.root-servers.net.
.			385093	IN	NS	b.root-servers.net.
.			385093	IN	NS	i.root-servers.net.
.			385093	IN	NS	e.root-servers.net.
.			385093	IN	NS	l.root-servers.net.
.			449587	IN	RRSIG	NS 8 0 518400 20200321170000 20200308160000 33853 . f72i06gGaw04avVfAf9TuqSYgxlEe0xfA6PQoS2gy9A756D77qmOZj02 zFphal3EktZEk6d3NFsKmR1d4uRHF8X58Uy9x7fDDUVo7MbHKyb7jdcE JBiR1+TkzRjOWQfDrlmLELS5FynrgsSg0ooqFIXtBAOoYl9Zr5ysONY0 rleM4wN8zF/XUgTP+ZrXrE086sr5eh8jEei2azeJQ+tVJ8L+Ohx+AyFL LWSMzgxuZSjNz/zh4r8RQdQ093ZC+H1zvo9cL2UZ6+NmLyVFhKJ8EVjf ZPxP4Oene7XMgxgEcT6TVbJioaH1p2GDVP0MVQGplzryXrOPfX4E4pLA C7Bsrg==
;; Received 1137 bytes from 192.168.1.1#53(192.168.1.1) in 18 ms

com.			172800	IN	NS	f.gtld-servers.net.
com.			172800	IN	NS	c.gtld-servers.net.
com.			172800	IN	NS	g.gtld-servers.net.
com.			172800	IN	NS	i.gtld-servers.net.
com.			172800	IN	NS	h.gtld-servers.net.
com.			172800	IN	NS	b.gtld-servers.net.
com.			172800	IN	NS	a.gtld-servers.net.
com.			172800	IN	NS	e.gtld-servers.net.
com.			172800	IN	NS	j.gtld-servers.net.
com.			172800	IN	NS	m.gtld-servers.net.
com.			172800	IN	NS	d.gtld-servers.net.
com.			172800	IN	NS	l.gtld-servers.net.
com.			172800	IN	NS	k.gtld-servers.net.
com.			86400	IN	DS	30909 8 2 E2D3C916F6DEEAC73294E8268FB5885044A833FC5459588F4A9184CF C41A5766
com.			86400	IN	RRSIG	DS 8 1 86400 20200322130000 20200309120000 33853 . RTMYCJl25PuAsQFXybethux68YLs9avsxugBG6/F+GcbYIghLPhYcP3C rNGYucUcUemBNAhwpcv56nGsoBkupVEF4Pt2vx+b1dMtyBAhBd62NPso WE4OihNAC0xMlzO0f45PsZgAfoQ9LBct+kShXNOnThE4xkKx+Eu7gi48 CQUhBIxRIW6w8h7tPekn6anOxvzVj/ybHLW6vFwgcK9exhllZ3td+D/X i8Rvrl1sQTfR0BwsZO6h6+T1b12wnYrEEETW/1eEi1V7dzqEF3bJ6fzD UFby7t3GyrtccZT003fyAb7YOYVwnQTXJRqepLx7FdWOuCFmX+iXdY2F K4hKYQ==
;; Received 1178 bytes from 202.12.27.33#53(m.root-servers.net) in 195 ms

linuxtoday.com.		172800	IN	NS	ns5.swiftpost.net.
linuxtoday.com.		172800	IN	NS	ns6.swiftpost.net.
CK0POJMG874LJREF7EFN8430QVIT8BSM.com. 86400 IN NSEC3 1 1 0 - CK0Q1GIN43N1ARRC9OSM6QPQR81H5M9A  NS SOA RRSIG DNSKEY NSEC3PARAM
CK0POJMG874LJREF7EFN8430QVIT8BSM.com. 86400 IN RRSIG NSEC3 8 2 86400 20200314044922 20200307043922 56311 com. s9oJcBy3w9ZGB7CfC5Yq9myW2XBoX/RQhrBJH0KQ1LhvF02bSfPv9q/d T3il80mm6qEUKWIAB8hx5Iy8j/FPr6caUVnYSHB/DJgveffWTwVOeNY9 3sgOxoxCqyPEGBicjWo91wwa5fcWfO1Bq7jtrBFQ+fEm/0RkLtgFKJM/ jClHVbn6T0rNJ8rlJgf4Hoc5Ue6b5II2+HMeRsGUUaWWug==
8INV13TDRCF4KTNL97FU5DLBFJLM6A99.com. 86400 IN NSEC3 1 1 0 - 8IO20O6QSV0DP5S0BN0DK00VPSKLAEL0  NS DS RRSIG
8INV13TDRCF4KTNL97FU5DLBFJLM6A99.com. 86400 IN RRSIG NSEC3 8 2 86400 20200313043514 20200306042514 56311 com. wwzTRA/B2Nesfmtj5nEa2RvTcyPR5nS/tULssQDWJmZjLuqgsq9SgI6O OJsbpbgLuYdEsI05Q4m6ERyMxo1zgf5gE8E+PrXStV/iolcV6e7sLI31 ib6dFfV/Wj0LcCNnO5v9+vdCkUL0PADPith08idzLF3q2FXhFvKEcHGa 3O/cgzxsi2ZeU5gRFBNbLZis3A95V2eZKSZRsWrm/H7UOQ==
;; Received 645 bytes from 192.52.178.30#53(k.gtld-servers.net) in 18 ms

www.linuxtoday.com.	300	IN	CNAME	www.quinstreet.com.edgekey.net.
;; Received 91 bytes from 70.42.23.252#53(ns5.swiftpost.net) in 192 ms
```

Seems to work ok?

---

