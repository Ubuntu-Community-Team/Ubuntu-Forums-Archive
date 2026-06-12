---
title: "I don't know what DoH (DNS over HTTPS) is and if I should enable it?"
date: 2020-02-27
forum: Security
---

### Post by ardouronerous on 2020-02-27
Hello everyone, I'd like to know what everyone thinks of Firefox's DoH  (DNS over HTTPS) and if I should enable it. I have no idea what DoH is,  so I need some clarification on it.

I've done some research on my  own, but it's still confusing to me. From what I've gathered, DoH will  prevent your ISP from determining what DNS requests you make and that  Firefox uses Cloudflare by default. I don't understand this, can someone  explain thanks.

---

### Post by mastablasta on 2020-02-28
the choice is yours. ISP won't be able to see what sites you are looking at with DOH, but the data will go to another server. is that server safe? according to Mozilla it is.
more here: [https://support.mozilla.org/en-US/kb/firefox-dns-over-https](https://support.mozilla.org/en-US/kb/firefox-dns-over-https)

---

### Post by CatKiller on 2020-02-28
There's some more information about it [here](https://arstechnica.com/information-technology/2020/02/firefox-turns-encrypted-dns-on-by-default-to-thwart-snooping-isps/).

---

### Post by DuckHook on 2020-03-01
> **ardouronerous said:**
> Hello everyone, I'd like to know what everyone thinks of Firefox's DoH  (DNS over HTTPS) and if I should enable it. I have no idea what DoH is,  so I need some clarification on it.

I've done some research on my  own, but it's still confusing to me. From what I've gathered, DoH will  prevent your ISP from determining what DNS requests you make and that  Firefox uses Cloudflare by default. I don't understand this, can someone  explain thanks.

Let's look at the chain of security precautions involved in visiting a modern website. Now that almost all websites use https, it's much harder for bad actors to spy on what we are doing within actual web pages. However, https doesn't kick in until we reach the actual site itself. The road that we take getting to that website is still broadcast to everyone in the clear. In particular, these days, most routers are loaners from ISPs and they are preconfigured to send DNS queries to the ISP's DNS servers. So, while the ISP can't see what you are doing inside your banking site (provided your bank uses https), they do know that you're visiting it because they are the ones who received your request to go there. And even if you use a different DNS server, say Google's, your ISP is still seeing all that DNS traffic in clear text, and can trace all of your comings and goings simply by intercepting your DNS queries.

The technology behind DoH creates an encrypted tunnel to look up DNS queries from a third party DNS server. By encrypting such queries, it not only allows you to bypass your ISP's DNS servers, it prevents your ISP from spying on those queries. If they tried to do so, they would just get a gobbledegook stream of encrypted packets.

But don't get a false sense of security. Your ISP has other means to trace your traffic. After all, it resides at a pretty basic level in your whole network infrastructure. By using DoH, even if your DNS queries are no longer an open book, it's your ISP that has to manage where each data packet gets sent, how many nodes it must traverse, and how the return packets get back to you. This route is still easily viewable by them. However, it is harder for them to track and record such routes than it is to simply log each and every one of your DNS queries. So, while DoH makes life harder for them, it is actually not effective at hiding your activities from your ISP. Its real value is in preventing DNS poisoning, MitM attacks and site spoofing, because it's almost impossible to taint DNS packets that are encrypted.

If you *really* don't trust your ISP (and it's admittedly getting harder and harder to do so), DoH won't help you. What *will* help you is a VPN. A VPN creates an encrypted tunnel between you and the VPN provider. If you create this tunnel at the router level, *all* of your traffic will be channelled to the VPN before it goes to whatever site you are visiting. All return packets also go to the VPN before being sent back to you along that same encypted pipe. Your ISP sees nothing but an encrypted stream of traffic going both ways only to your VPN provider. They can traceroute and log all they want—they can even disassemble each data packet—but they cannot see what you are up to, where you have visited or what sort of data you are transmitting.

Don't rest easy just yet though. Obviously, your VPN provider is now the weak link. It now stands in the same position that your ISP used to occupy. It can see all of your traffic, must decipher your DNS queries to figure out how to resolve them, and can traceroute your data packets from end to end. This is why it is so important to choose a good VPN provider. A good one won't keep logs, won't traceroute and is sufficiently capitalized that it has the computing resources to run all of its infrastructure in volatile RAM so that if their machines ever get confiscated, there is absolutely no record of activity. When choosing a VPN provider, do your research and choose carefully.

---

### Post by DuckHook on 2020-03-01
*Thread moved to **Security** as the more appropriate forum.*

---

### Post by kevdog on 2020-03-02
Honestly -- I think DOH is a tool that should be ran at the router level and not the individual application level.  I've had DOH setup on my pfSense router now for a couple of years. I have much better control where the DNS queries can be directed.  At the application level, Firefox controls these choices.

---

### Post by DuckHook on 2020-03-02
Firefox gives us the option to define our own DNS Server: General &#8594; Network Settings &#8594; Settings &#8594; Enable DNS over HTTPS &#8594; Use Provider <Cahnge to "Custom"> &#8594; <Enter URL of your DNS provider>

…but I understand what you are saying. Setting it in the router makes for a more fundamental enhancement. At least Firefox gives us the option; Chrome doesn't allow DoH unless one adds a very arcane switch to the command line when invoking it.

I try to kill two birds with one stone by setting my DNS provider to dns.adguard.com. In addition to bypassing my ISP (or other tracking providers like Google), it also filters ads. Since setting things up this way, I have not had to use an ad blocker on the browser. I can't tell you if adguard logs your DNS queries. They *say* they don't but we have to take them at their word—ie I don't think it's ever been tested in a court case.

PS. For those interested, to invoke DoH with Chrome, append the following switch to /usr/bin/google-chrome-stable
```
--enable-features="dns-over-https<DoHTrial" --force-fieldtrials="DoHTrial/Group1" --force-fieldtrial-params="DoHTrial.Group1:server/https%3A%2F%2F1.1.1.1%2Fdns-query/method/POST"
```…this directs to cloudflare. To direct to adguard replace 1.1.1.1 with:```
176.103.130.130
```

---

### Post by kevdog on 2020-03-03
Hmm, I've never heard of dns.adguard.com.  I took a look at their website.  I'm not saying its sketchy - however when companies are giving away products for free it's my belief they have to be monetizing the data in some manner.

---

### Post by DuckHook on 2020-03-03
> **kevdog said:**
> Hmm, I've never heard of dns.adguard.com.  I took a look at their website.  I'm not saying its sketchy - however when companies are giving away products for free it's my belief they have to be monetizing the data in some manner.
Yes, it's a very valid concern. However, we already know that ISPs, Google and probably Cloudflare are monetizing our data, so I don't see how to avoid having any concerns at all. They claim that they make their money from corporate customers and large institutions who have to pay for ad-blocking and swear up and down on a stack of holy texts that they don't log anything, but as I mentioned, we have nothing more to go on but their word. I use them specifically to block ads and harbour no illusions about the possibility of DNS logging.

As already mentioned, for surfing that I'm serious about anonymizing, I use a VPN. Actually, I use a VPN in combination with TOR-Browser, but that's too far outside the scope of the OP's original question.

---

### Post by kevdog on 2020-03-03
I have no idea what any DNS provider does with their data in terms of monetization of other nefarious activities.  I'm using Cloudflare.  I run a bunch of server with Lets Encrypt Certs.  Cloudflare's interface and ability to interact with acme.sh makes things real easy to manage. 

In terms of VPN - I guess its how much do you trust your VPN provider as many might keep logs and such.

---

### Post by DuckHook on 2020-03-03
> **kevdog said:**
> &#8230;In terms of VPN - I guess its how much do you trust your VPN provider as many might keep logs and such.
Absolutely. At some point, it just boils down to having to make that leap of trust. Even Ubuntu itself can be compromised if Canonical decides to compile a very sneaky backdoor into the distro. General users like me are simply unequipped to detect anything like that.

Re: VPNs: One of the strategies that some security blogs have suggested is to go with providers who have been issued court orders through FBI investigations. The agency raids their server farms to confiscate the actual machines only to confirm that, yes indeed, the provider keeps no logs and the entire infrastructure runs in volatile RAM, so it all evaporates on seizure. Other providers go to the expense of submitting to third-party audits from accredited security firms.

---

### Post by lwalper on 2020-03-05
So, what about TOR?--and TOR browser? Is that actually as secure as it is advertised? It uses a modified Firefox as its basic browser. Does it make VPN connections or just route packets all over the world making tracking more difficult.

---

### Post by EuclideanCoffee on 2020-03-05
It makes tracking more difficult, but it's not secure. Anyone can see your traffic from the exit node.

---

### Post by DuckHook on 2020-03-05
> **lwalper said:**
> So, what about TOR?--and TOR browser? Is that actually as secure as it is advertised? It uses a modified Firefox as its basic browser. Does it make VPN connections or just route packets all over the world making tracking more difficult.
TOR actually is its own form of VPN in that your connection to the entry node is fully encrypted (essentially a VPN). However, EuclideanCoffee is correct in that, at a minimum, your destination address and metadata **must** be decrypted at the exit node to allow for delivery. But then, this applies to all VPN providers as well, so there's no real difference there.

At the risk of digressing from the OP's topic, there's a lot of noise out there regarding TOR and TOR-Browser. Critics have noted that a number of exit nodes and entry points are so massively overcapitalized that they could only be the result of infrastructure belonging to some three-letter agency. Once a critical threshold of entry/exit nodes are controlled by one entity, the Onion routing paradigm breaks down and anonymity evaporates.

TOR supporters counter that such concerns are highly conjectural fearmongering. There are a lot of well-heeled entities who want TOR to succeed and are willing to fund/support it out of a hybrid of altruism and enlightened self-interest. Everyone from news agencies to NGOs to democracy advocates to financial houses like banks have an interest in promoting its form of anonymity. They could very well be providing massive contributions but keeping very quiet about it for obvious reasons. The triumvirate of Google, Amazon and Apple (who have all made noises about supporting anonymity) could donate insane TOR infrastructure for less than what they spend on coffee.

When one is dealing with an entity whose very reason for being is anonymity and privacy, it is impossible (almost by definition) to arrive at a holistic clarity about its structure and layout. Were it easy to do so, its anonymity would also evaporate. However, it is conceivable that massively funded government programs could penetrate TOR, either through brute force surveillance of large numbers of entry & exit nodes or (more likely) through exploiting some unknown zero-day flaw in the underlying TOR implementation. Naturally, such agencies ain't talkin.

TOR itself has established the goal of expanding its nodes into the millions. I'm no mathematician, but my understanding is that the relationship between number of nodes and anonymity is not linear but geometrical. If TOR were to reach this goal, its anonymization paradigm would be *theoretically* unbreakable (emphasis on "theoretical"). It is generally conceded that TOR already has enough nodes now to make brute force surveillance impractical. This does nothing to alleviate concerns that its underlying implementation is not flawed and therefore exploitable.

If you are interested in the subject of TOR, it's a fascinating rabbit hole you can fall into and waste days of time exploring. As a general intro, [Wikipedia actually has a pretty good entry]("https://en.wikipedia.org/wiki/Tor_(anonymity_network)") on its structure, uses, strengths and weaknesses.

As with all matters of security, it's not TOR itself that constitutes the biggest security weakness, but the people using it. Almost all incidents of purported TOR compromises can be traced back to the foolishness or stupidity of the people relying on it. If you download a picture, movie or song with a hidden payload that reports your IP address back to papa, all the anonymizing in the world won't help you and it won't be TOR's fault when the cops come knocking at your door.

Personally, I think people who use TOR for things like illegal torrenting, drug purchases or other unsavoury things are idiots. They leave their tracks all over the place and are generally too stupid to use it properly. For example, torrenting was never designed to be anonymous and is full of holes that can be exploited to trace both host and client. On the other hand, *if used properly* TOR remains an indispensible friend to millions of democracy advocates, whistle-blowers, abuse victims, censorship sufferers, journalists, privacy advocates and health care providers.

---

### Post by lwalper on 2020-03-06
Interesting. Thanks.

---

### Post by linuxyogi on 2020-03-20
I just enabled Firefox's DoH  (DNS over HTTPS) but how to make sure that its working ?

---

### Post by EuclideanCoffee on 2020-03-20
Go to this website and run a standard test.
[https://www.dnsleaktest.com/](https://www.dnsleaktest.com/)

You should see Cloudflare or whatever you chose for DoH.

---

### Post by linuxyogi on 2020-03-20
> **EuclideanCoffee said:**
> Go to this website and run a standard test.
[https://www.dnsleaktest.com/](https://www.dnsleaktest.com/)

You should see Cloudflare or whatever you chose for DoH.

Yes it is showing 

ISP : Cloudflare
Country : India (but a different city)

But on the [https://www.dnsleaktest.com/](https://www.dnsleaktest.com/) home page it says Hello "IP Address" from "My city name)

---

### Post by linuxyogi on 2020-03-20
@[**[COLOR=#000000]EuclideanCoffee[/COLOR]**]("https://ubuntuforums.org/member.php?u=1943968")
I have added some more info to my last post. Please have a look.

---

### Post by EuclideanCoffee on 2020-03-20
DoH does not hide your IP address.

Before you visit a website, your computer queries a server called a DNS server. This server returns the true IP address for a URL such as ubuntuforums.com.

When you do DoH, your query to the DNS server is hidden from an ISP DNS server. ISPs commonly record DNS lookups and use it for advertisement in the USA.

To hide your IP address, you will need to use a proxy or VPN.

Everything you do on a computer is traced to you. There is no anonymous network or the operation of one.

---

### Post by DuckHook on 2020-03-20
> **EuclideanCoffee said:**
> …Everything you do on a computer is traced to you. There is no anonymous network or the operation of one.
Erhm…

Only a slight disagreement here, but still a disagreement.

It is possible to anonymize some activities over the Internet, but it is much harder to do so than most people realize and requires a level of knowledge that most people are unwilling to learn along with a discipline most will not follow.

[LIST]
[*]TOR can be pretty effective at anonymization—until the user visits some site and then proceeds to enter personal credentials (duh), or thinks they can torrent illegal files only to be de-anonymized when their torrent starts seeding.
[*]Likewise, a VPN can anonymize, but only if it's used very very judiciously and with a ton of other anonymization measures in place.
[*]Most people are not even aware of browser fingerprinting, much less know what to do about it.
[*]What is even the point of anonymity for someone who insists on using Facebook, Whatsapp. Twitter and Instagram?
[/LIST]
I would suggest, perhaps, that it might be more accurate to say: anonymity is possible, but the way most people use their computers and phones makes it impossible.

---

### Post by DuckHook on 2020-05-01
For the Canucks among us, this DoH service was recently made available for Canadians: [https://www.cira.ca/cybersecurity-services/canadian-shield](https://www.cira.ca/cybersecurity-services/canadian-shield)

I see nothing that would prevent this service from working for anybody.

---

