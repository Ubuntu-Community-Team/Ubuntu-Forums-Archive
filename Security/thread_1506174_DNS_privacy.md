---
title: "DNS privacy?"
date: 2010-06-10
forum: Security
---

### Post by wlraider70 on 2010-06-10
So i was listening to Leo laport security now and they were talking about DNS.

The point was the your ISP will always know where you are going by viewing what DNS you resolve.


Is there any protocol for secure DNS?
Would it be reasonable to use a secondary DNS for obscurity?


Also when I select my DNS server can I be sure that my machine is actually going there. I know that my cable modem/dsl modem seems to have an ISP DNS hard-coded into it


So how can I keep my ISP from knowing where I'm going? (yeah that rhymes)

---

### Post by movieman on 2010-06-10
> **wlraider70 said:**
> The point was the your ISP will always know where you are going by viewing what DNS you resolve.

Considering that your ISP will see all the packets you send and receive, worrying about using their DNS seems a bit pointless... you can use a different DNS server so that they won't see you look up www.disreputablesite.com, but they'll still see the packets going to and from that site's IP address.

---

### Post by Bachstelze on 2010-06-10
> **movieman said:**
> Considering that your ISP will see all the packets you send and receive, worrying about using their DNS seems a bit pointless... you can use a different DNS server so that they won't see you look up [www.disreputablesite.com](www.disreputablesite.com), but they'll still see the packets going to and from that site's IP address.

They will also see the packets coming to and from whatever DNS server yo uuse, so they will know you asked about the IP address of [www.disreputablesite.com](www.disreputablesite.com) to some DNS server.

---

### Post by cdenley on 2010-06-10
You can use something like TOR. That will resolve domains through a tor router, and any traffic going through your ISP will be encrypted. Whoever does resolve the domain for you (TOR exit node) will be sending the DNS request to some DNS server in plaintext, but whoever can see that DNS request shouldn't be able to match it with your IP.

---

### Post by Saghaulor on 2010-06-10
You could tunnel your traffic through a proxy. Some proxies offer https, so your packets are encrypted as well.

But somewhere down the line someone is going to know what you're up to.

---

### Post by bodhi.zazen on 2010-06-10
> **Saghaulor said:**
> But somewhere down the line someone is going to know what you're up to.

This ^^

Do you really think your ISP , who likely services thousands of clients, is sorting through your personal DNS traffic ? I doubt it.

If you are doing something illegal or shady over the internet you are traceable.

---

### Post by wlraider70 on 2010-06-10
why is that people assume you are doing something illegal or immoral if you don't want to be tracked.

So hypothetically you would need an https to your DNS and then also secure connections to all sites you visit.

---

### Post by Bachstelze on 2010-06-11
> **wlraider70 said:**
> 
So hypothetically you would need an https to your DNS

[img]http://iori.fkraiem.org/stuff/lol.jpg[/img]

---

### Post by cdenley on 2010-06-11
Just use tor. That is what it is for. It is the best way to keep your IP separate from your traffic. Then you only have to worry about revealing your identity or sensitive data within the traffic you send through tor.

---

### Post by koenn on 2010-06-11
> **wlraider70 said:**
> why is that people assume you are doing something illegal or immoral if you don't want to be tracked.

because when someone wants to go to extreme lengths to hide information nobody is looking for to begin with (like your handful of DNS lookups in the shiploads of DNS lookups a DNS server handles daily), people begin to wonder what would make that info worth hiding. Something punishable or something you'd be ashamed of are the first things that come t mind then.

---

### Post by bodhi.zazen on 2010-06-11
> **koenn said:**
> because when someone wants to go to extreme lengths to hide information nobody is looking for to begin with (like your handful of DNS lookups in the shiploads of DNS lookups a DNS server handles daily), people begin to wonder what would make that info worth hiding. Something punishable or something you'd be ashamed of are the first things that come t mind then.

With #3 and #4 being excessive concern and paranoia.

No offense intended by that list simply wanting privacy for personal reasons is lower on most people's list.

---

### Post by Saghaulor on 2010-06-13
I'm not going to pass judgment on you. You asked a question, so I gave you an answer. I'll leave the judgment to the legislatures and justice system.

You could setup your own dns mirror server, and create an ssh tunnel to it. That would effectively cloak you also.

But like bodhi.zazen said, you can never go under the radar, there's always a way to track you.

---

### Post by lisati on 2010-06-13
No matter what steps you take to cover your tracks, someone somewhere will know what you're up to.

A simple web page showing some of what can be learned about you can be found [here]("http://lisati.homelinux.com/whoami"). If you choose to use a proxy server and it's any good, the information shown won't be anywhere near the truth. Don't worry, I don't have any inclination to take it much further than what it already shows.

---

### Post by wlraider70 on 2010-06-14
thanks for the information.

believe it or not, I'm not really worried about privacy. As I initially posted I was just curious.

---

