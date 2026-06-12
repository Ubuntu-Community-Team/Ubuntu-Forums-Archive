---
title: "Bizarre behaviour with wikipedia pages"
date: 2011-10-17
forum: The Cafe
---

### Post by spibou on 2011-10-17
During several hours on Sunday October 16th 2011 I noticed some strange behaviour : every wikipedia page I tried to access wasn't accessible , Firefox said that server could not be found , but when I tried to access the secure version of the same page it worked albeit images weren't visible. So for example [http://en.wikipedia.org/wiki/Lively_Kernel](http://en.wikipedia.org/wiki/Lively_Kernel) gave me the error message but [https://secure.wikimedia.org/wikipedia/en/wiki/Lively_Kernel](https://secure.wikimedia.org/wikipedia/en/wiki/Lively_Kernel) worked (without images). Additionally , accessing the non secure pages through 2 proxies , [http://freeproxyserver.net](http://freeproxyserver.net) or [http://www.hidemyass.com](http://www.hidemyass.com) , also worked. I'm based in the U.K. and my ISP is virginmedia. I didn't have any other internet problems. Towards the end of the day or perhaps early Monday morning things returned to normal.

I was wondering whether anyone experienced anything similar or has any theories as to what might have happened. I was thinking that perhaps the [Internet Censorship Foundation](http://en.wikipedia.org/wiki/Internet_Watch_Foundation_and_Wikipedia) might have decided yet again that some wikipedia page might be too harmful for our innocent minds.

---

### Post by fatality_uk on 2011-10-18
Relax, have a coffee and take a breath!!
The internet isn't perfect. Sometimes bits don't work. That doesn't mean BIG BROTHER is monitoring what you can and can't see. Perhaps they were doing maintenance on the servers. Perhaps your ISP was mapping traffic and therefore you were routed through a US hub that was timing out. There might be a 1,000,000 & 1 reasons, conspiracy isn't always my first thought.

---

### Post by Captain Smiley Pants on 2011-10-18
The Government is watching you and have cameras in your house, run!

---

### Post by spibou on 2011-10-18
> The internet isn't perfect. Sometimes bits don't work. That doesn't mean BIG BROTHER is monitoring what you can and can't see.
That's true but the possibility that big brother is responsible *has* to be examined especially in this case where we know that big brother exists and he/they does decide what we can't see.
> Perhaps they were doing maintenance on the servers.
Who , wikipedia ? If they were doing maintenance I would expect a message to that effect and accessing their site through proxies wouldn't work either.
> Perhaps your ISP was mapping traffic and therefore you were routed through a US hub that was timing out.
Why specifically a U.S. hub ?
> There might be a 1,000,000 & 1 reasons, conspiracy isn't always my first thought.
It's not always or even usually my first thought either. I'd love to know some of the other possibilities for educational reasons if nothing else.

---

### Post by emiller12345 on 2011-10-18
> **spibou said:**
>  [http://en.wikipedia.org/wiki/Lively_Kernel](http://en.wikipedia.org/wiki/Lively_Kernel) gave me the error message but [https://]("https://secure.wikimedia.org/wikipedia/en/wiki/Lively_Kernel")[secure.wikimedia.org]("https://secure.wikimedia.org/wikipedia/en/wiki/Lively_Kernel")[/wikipedia/en/wiki/Lively_Kernel]("https://secure.wikimedia.org/wikipedia/en/wiki/Lively_Kernel") worked (without images).

when I come across a page that I know should be accessible, but is not, I usually try
```
$ host en.wikipedia.org 
$ host secure.wikimedia.org
```which will retrieve the ip.addr for the site(s) in question (two different ip's btw), then a simple ping ...
```
ping -c 4 xxx.xxx.xxx.xxx
```to see if it responses to icmp packets || you can traceroute to see if the packets are making it to their destination ...
```
$ tcptraceroute  xxx.xxx.xxx.xxx 80
$ tcptraceroute  xxx.xxx.xxx.xxx 443
```port 80 is for standard HTTP traffic and port 443 is for secure HTTPS traffic

this will give you a little bit more information about what is going on.

---

