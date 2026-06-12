---
title: "Configured Dns over TLS ..... Is this good for privacy?"
date: 2021-02-16
forum: Security
---

### Post by linuxyogi on 2021-02-16
I was using Dns over Https using Firefox for a long time now. Yesterday I read some articles which say that Dns over TLS is a better solution.
I followed this guide >>>>[https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls](https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls)
Only thing is the feature was not working until I disabled IPv6. I didn't get the idea for disabling IPv6 from the internet I was just experimenting .
Nothing was showing up on wireshark until I disabled IPv6.

Q1) Is Dns over TLS better than DoH ?
Q2) Is there any disadvantages of disabling IPv6 ?

---

### Post by DuckHook on 2021-02-16
Wow.

A world of issues to unpack in your questions. Here's my attempt. In no particular order:

IPv6 is the wave of the future. It cannot be avoided. We have run out of IPv4 space and the only option going forward is IPv6. But do I use it? No. I have it turned off. In fact, IPv6 cannot get through my router firewall. Why? Because it opens up an entirely new and massive attack surface. For now, I can get to wherever I want to go using IPv4 alone. So, until I get my head wrapped around IPv6, and until I am forced to use it by necessity, I am too lazy to learn it. But it must be confessed, these are ***my*** limitations; not those of IPv6. On its own, IPv6 has awesome potential. Technically, it allows every connectable device to have its own unique IP address. Think about that. No more NATs, no more ugly kludges that break connectivity, no more having to mess around with port forwardings, bindings and other techno&#8209;nonsense. Packets get delivered from one precise point of origin to another precise destination—end of story. Of course, this opens up an entire world of exposure and risk (which I've already alluded to) but that's the price we pay these days for massively better utility.

There are few disadvantages to disabling IPv6. But that's only because the foundational web of today is still mired in IPv4. Those who use IPv6 are way ahead of the game and have access to utility denied to the rest of us. If you run a massive shipping concern that tracks its assets using embedded IoT devices, then IPv6 cannot be turned off. The benefit is that you could see where every pallet of goods is all over the world in real time. But if you are an ordinary Joe like all consumers, then IPv6 will hardly be noticeable… ***for now.***

DoT is not better than DoH. Nor is DoH better than DoT. They do a similar job differently and both have advantages and disadvantages. Both are designed to stop intermediaries and data carriers (like your ISP) from snooping on your DNS queries. They do so through the theoretically simple expedient of leveraging already proven encryption technology to encrypt your DNS traffic which, until now, has generally been sent in the clear. So, while the actual data that you exchange with your bank is encrypted, the fact that you were visiting your banking site was open and accessible to anyone interested in seeing this. But note that while this is *theoretically* simple, it is *applicably* complex.

DoT is the older tech, but only slightly. It borrows the TLS mechanism that your browser uses and treats it *as a separate tool* to encrypt your DNS traffic. The fact that it acts as a separate tool is important. To do so, it must use a port of its own: I believe it is 853. Without getting too arcane, the practical upshot of this is that evil ISPs or oppressive regimes can continue to spy on you because they can easily cripple DoT by blocking port 853. While my ISP allows this port, I have read that some don't. The benefit of DoT is that it is easier to implement than DoH, especially on standalone apps and use cases where a browser would be unwanted.

DoH works by tunnelling DNS through port 443 which is the port used by all HTTPS traffic. Bad ISPs/regimes cannot block port 443 without also blocking the most important parts of the Internet, so in effect, they cannot block DoH. However, my understanding is that it is harder to implement and requires a browser. I could be wrong. I'm not a programmer and my knowledge in this regard comes only from what I've read.

There's a vast ecosystem of technology behind your seemingly simple queries that I haven't touched on. There's DNSSEC and MitM avoidance and browser fingerprinting, and blah&#8209;blah&#8209;blah. The above explanation is only the quickest and dirtiest of summaries. You cannot hope to get your head properly wrapped around these issues by asking on a forum. It involves a lot of reading and research, which is readily available using even the simplest web search. As a launching point, and even though it is regularly scoffed at by real experts, I have found Wikipedia to be invaluable.

---

### Post by TheFu on 2021-02-16
A new Firefox was installed here over the weekend and it broke all sorts of things.  In my attempt to get it working at all (it wouldn't load any websites remote or local), I ended up flushing the old FF profile and starting fresh - which removed my 10+ about:config tweaks added the last decade.

It still isn't behaving properly, but it is almost usable after I also disabled IPv6.  My systems don't support IPv6, so there is definitely a bug in Firefox that it attempts to use IPv6 on a system with that entire stack disabled in the kernel.

I also disabled the built-in DoH ... since my local DNS is necessary to connect to about 15 internal-only websites. I cheat by using a pihole for both an internal DNS server and DNS filter. I like the idea of NOT having internal DNS sitting on a network appliance like a router.

Opening new webpages is only working about 50% of the time. If I take the failed-to-open URL, manually open a new tab, then paste the exact same URL there, it almost always works. A shift-reload in the original tab or pasting back into the original tab doesn't do anything.

I use firejail with firefox and thunderbird. These programs I consider high-risk and want a little extra protection.  With the newest FF installed, I had to modify the firejail startup parameters that had been mostly working for 2 yrs. Those new settings are: 
```
/usr/bin/firejail  --ignore=seccomp --ignore=protocol
```

There were a few other about:config options that had to be toggled too so access to internal websites like nextcloud would work. Sorry, I don't remember those.

I should mention that Chromium is still working fine. No changes needed, but I dislike using chromium - I'm not comfortable with the addons, so running it inside a firejail --private environment is the only way.

Privacy is a hard thing to finger. Clearly, someone needs to know where your system visits or you'll never have traffic routed there and back.  Who do you want privacy from is the first question.  The more privacy you want, the more complex the answer and the slower the performance.  Do you also the anti-spoofing/anti-malware *features* in your browsers? For those services to work, who needs to know where you go?  Poor DNS performance can make the entire system slower.

---

### Post by DuckHook on 2021-02-16
> **TheFu said:**
> A new Firefox was installed here over the weekend and it broke all sorts of things.  In my attempt to get it working at all (it wouldn't load any websites remote or local), I ended up flushing the old FF profile and starting fresh - which removed my 10+ about:config tweaks added the last decade.
You too!

I thought it was only me. So it was the upgrade. Thought I had done something wrong, but it wasn't me. Now I am seriously cheesed off.

I had to reset too. Lost about the same amount of tweaks as you, which was also years' worth. :-x
> I also disabled the built-in DoH ... since my local DNS is necessary to connect to about 15 internal-only websites.
Hmmm.

I ***do*** use the built-in DoH and can get to all of my internal LAN websites. I wonder why you can't.
> I dislike using chromium - I'm not comfortable with the addons, so running it inside a firejail --private environment is the only way.
I've completely sworn off Chromium. Have substituted Brave. Must say that I'm impressed. It's a slick and well designed piece of work. But, frankly, I don't know how successfully it's been de&#8209;Google&#8209;ized. I tend to use it only for sites on which FF chokes, which, thankfully, are infrequent.
> Privacy is a hard thing to finger. Clearly, someone needs to know where your system visits or you'll never have traffic routed there and back.  Who do you want privacy from is the first question.  The more privacy you want, the more complex the answer and the slower the performance.  Do you also the anti-spoofing/anti-malware *features* in your browsers? For those services to work, who needs to know where you go?  Poor DNS performance can make the entire system slower.I do have all of those features turned on and more besides. I'm not finding DNS performance unduly impacted. Maybe I'm used to it. Mrs DH is always shaking her head when we surf together. I have to consciously permit only very specific scripts to run, and web pages must wait for all of the right buttons to be pressed and knobs to be turned. It drives her bonkers, but I'm so used to it by now that it feels like second nature ("you mean, not everyone surfs this way?").

@linuxyogi

Didn't mean to hijack your thread, but perhaps even this digression gives you some idea of the complexities hidden in your initial queries.

---

### Post by linuxyogi on 2021-02-17
> **DuckHook said:**
> Wow.

A world of issues to unpack in your questions. Here's my attempt. In no particular order:

IPv6 is the wave of the future. It cannot be avoided. We have run out of IPv4 space and the only option going forward is IPv6. But do I use it? No. I have it turned off. In fact, IPv6 cannot get through my router firewall. Why? Because it opens up an entirely new and massive attack surface. For now, I can get to wherever I want to go using IPv4 alone. So, until I get my head wrapped around IPv6, and until I am forced to use it by necessity, I am too lazy to learn it. But it must be confessed, these are ***my*** limitations; not those of IPv6. On its own, IPv6 has awesome potential. Technically, it allows every connectable device to have its own unique IP address. Think about that. No more NATs, no more ugly kludges that break connectivity, no more having to mess around with port forwardings, bindings and other techno&#8209;nonsense. Packets get delivered from one precise point of origin to another precise destination—end of story. Of course, this opens up an entire world of exposure and risk (which I've already alluded to) but that's the price we pay these days for massively better utility.

There are few disadvantages to disabling IPv6. But that's only because the foundational web of today is still mired in IPv4. Those who use IPv6 are way ahead of the game and have access to utility denied to the rest of us. If you run a massive shipping concern that tracks its assets using embedded IoT devices, then IPv6 cannot be turned off. The benefit is that you could see where every pallet of goods is all over the world in real time. But if you are an ordinary Joe like all consumers, then IPv6 will hardly be noticeable… ***for now.***

DoT is not better than DoH. Nor is DoH better than DoT. They do a similar job differently and both have advantages and disadvantages. Both are designed to stop intermediaries and data carriers (like your ISP) from snooping on your DNS queries. They do so through the theoretically simple expedient of leveraging already proven encryption technology to encrypt your DNS traffic which, until now, has generally been sent in the clear. So, while the actual data that you exchange with your bank is encrypted, the fact that you were visiting your banking site was open and accessible to anyone interested in seeing this. But note that while this is *theoretically* simple, it is *applicably* complex.

DoT is the older tech, but only slightly. It borrows the TLS mechanism that your browser uses and treats it *as a separate tool* to encrypt your DNS traffic. The fact that it acts as a separate tool is important. To do so, it must use a port of its own: I believe it is 853. Without getting too arcane, the practical upshot of this is that evil ISPs or oppressive regimes can continue to spy on you because they can easily cripple DoT by blocking port 853. While my ISP allows this port, I have read that some don't. The benefit of DoT is that it is easier to implement than DoH, especially on standalone apps and use cases where a browser would be unwanted.

DoH works by tunnelling DNS through port 443 which is the port used by all HTTPS traffic. Bad ISPs/regimes cannot block port 443 without also blocking the most important parts of the Internet, so in effect, they cannot block DoH. However, my understanding is that it is harder to implement and requires a browser. I could be wrong. I'm not a programmer and my knowledge in this regard comes only from what I've read.

There's a vast ecosystem of technology behind your seemingly simple queries that I haven't touched on. There's DNSSEC and MitM avoidance and browser fingerprinting, and blah&#8209;blah&#8209;blah. The above explanation is only the quickest and dirtiest of summaries. You cannot hope to get your head properly wrapped around these issues by asking on a forum. It involves a lot of reading and research, which is readily available using even the simplest web search. As a launching point, and even though it is regularly scoffed at by real experts, I have found Wikipedia to be invaluable.

As you know any network has two sides. The WAN side & the LAN side. I have disabled IPv6 on the LAN side. When I ping [www.google.com](www.google.com) I still receive reply from a IPv6 address

```
$ ping google.com
PING google.com(ams17s01-in-x0e.1e100.net (2a00:1450:400e:80b::200e)) 56 data bytes
64 bytes from ams17s01-in-x0e.1e100.net (2a00:1450:400e:80b::200e): icmp_seq=1 ttl=106 time=640 ms
64 bytes from ams17s01-in-x0e.1e100.net (2a00:1450:400e:80b::200e): icmp_seq=2 ttl=106 time=596 ms
64 bytes from ams17s01-in-x0e.1e100.net (2a00:1450:400e:80b::200e): icmp_seq=3 ttl=106 time=559 ms
64 bytes from ams17s01-in-x0e.1e100.net (2a00:1450:400e:80b::200e): icmp_seq=4 ttl=106 time=516 ms
^C
--- google.com ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4001ms
rtt min/avg/max/mdev = 515.569/577.403/639.695/45.783 ms


```

So I see no major downsides to disabling IPv6 on the LAN side.

The only advantage of using DoT when compared to DoH is the fact that when DoT is enabled all network facing apps automatically use DoT. In case of DoH it was on a per app basis for example Firefox. The Chrome/Brave browser has disabled DoH for the Linux platform.

---

### Post by linuxyogi on 2021-02-17
> **TheFu said:**
>  Privacy is a hard thing to finger. Clearly, someone needs to know where your system visits or you'll never have traffic routed there and back.  Who do you want privacy from is the first question.  The more privacy you want, the more complex the answer and the slower the performance.  Do you also the anti-spoofing/anti-malware *features* in your browsers? For those services to work, who needs to know where you go?  Poor DNS performance can make the entire system slower.

Lately I read a lot of articles which say that ISPs collect browsing habits of their users so I want privacy from my ISP.
I must mention that after implementing DoT the name resolution process has become comparatively slower.
When I was using DoH (under Firefox) it was quite fast.

---

### Post by DuckHook on 2021-02-17
> **linuxyogi said:**
> When I ping [www.google.com](www.google.com) I still receive reply from a IPv6 address
Your DNS service seems to be resolving to IPv6. If it makes a real difference to you, you can check with them as to why.

Or your router could be set to resolve to IPv6. If, as you say, this is baked into your router and you cannot fiddle with its settings, you may have to live with IPv6. I don't know how things work in your country and I've already learned once not to jump to erroneous conclusions.
> So I see no major downsides to disabling IPv6 on the LAN side.
There should be none…for now.
> **linuxyogi said:**
> Lately I read a lot of articles which say that ISPs collect browsing habits of their users so I want privacy from my ISP.
Different countries have different behaviours. The US just recently permitted its ISPs to skim all sorts of info from/about its users. This is scary enough to heighten the impetus for DoH/DoT and push demand for it into overdrive. I believe that most of Europe is less creepy, but I'm not sure what their rules are. I have no idea whether ISPs in your country operate under any restraints.
> I must mention that after implementing DoT the name resolution process has become comparatively slower.
When I was using DoH (under Firefox) it was quite fast.
Make sure you are using the fastest DNS server in your area—commensurate with privacy of course. The fastest are usually your ISP's followed by Google's. Since your goal is privacy, both of those are non&#8209;starters. I don't know how fast Quad-9 is in your area. You could also try using Cloudflare if you trust their promises. I use Adguard. But TheFu is right (as usual): at some point, you simply have to trust somebody. Otherwise, you have no choice but to stop using a computer. Or a smartphone. Or even a gaming console.

---

### Post by linuxyogi on 2021-02-17
@TheFu / @DuckHook

Do you guys encrypt you DNS ? Which solution are you using ? DoH or DoT ?
If you are using DoT it will give me a sense of confidence.

---

### Post by The Cog on 2021-02-17
> I have disabled IPv6 on the LAN side. When I ping [www.google.com](www.google.com) I still receive reply from a IPv6 address
Clearly, you have not disabled IPv6. It's still working.

I see no reason to disable IPv6. More and more things are using IPv6, and over time, some services are going to become IPv6 only.
If both protocols are working, then your computer is designed to prefer to use IPv6. Google has both IPv4 and IPv6 addresses, as you can see here (the actual addresses may be different in your area):
> ~$ host  google.com
google.com has address 216.58.205.46
google.com has IPv6 address 2a00:1450:4001:801::200e

You can choose which protocol to ping with by using "ping -4" or "ping -6".

---

### Post by linuxyogi on 2021-02-17
> **The Cog said:**
> Clearly, you have not disabled IPv6. It's still working. 

Before I disabled IPv6 in network manager nothing was showing up on wireshark.
After I disabled IPv6 in network manager & restarted NM wireshark started registering DNS.

Please visit this link >>> [https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls](https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls) & scroll down to the section called 

> How to Check if Your DNS Traffic is Encrypted 

---

### Post by TheFu on 2021-02-17
> **linuxyogi said:**
> Lately I read a lot of articles which say that ISPs collect browsing habits of their users so I want privacy from my ISP.
I must mention that after implementing DoT the name resolution process has become comparatively slower.
When I was using DoH (under Firefox) it was quite fast.

DNS providers also collect habits of their users.  That was part of my point about who do you want to be private from?
If you want real privacy, don't use the internet.
There are different levels of privacy and how much you want probably doesn't overlap with how much is easy to accomplish. It isn't for me.

When I want privacy, 
[LIST]
[*]I don't do it from home.  I use a mom-pop cafe, not a corporate one. Corporate places with free wifi are everywhere. Assume those places are capturing your image, connection, DNS, and browsing. There are mitigations against each.
[*]Use a full, paid, VPN who you can trust.  How to know whether you can trust any VPN isn't easy.  You'll need to work into the ownership, logging, and truly who is behind it. Often, the more privacy they claim to provide, the more likely your data ends up in a parent companies hands.  Having headquarters in small countries often means the VPN can manipulate the govt there.  If the CEO/President and CIO for a VPN provider don't actually live in the country where their HQ is located, I consider that a warning sign too.
[*]How has the VPN reacted towards legal demands to provide information on the users?  If you don't hear anything about them fighting cased in court - what does that mean?  To me, it means they handed it all over.  I know of only 1 VPN provider who has fought legal battles AND proved they couldn't provide any logs to the govt, so the govt went away.
[*]When you sign up to pay for a VPN, use anonymous payment methods. Financial tracking is a real thing.  Every year or two, I buy a Gift VISA card to buy VPN service. There is a pre-paid service charge for this ... basically I'm paying 10% more to ensure privacy. This card cannot have more money added to it. The cards that support adding are more traceable. To be used on the internet, we have to register the card with a name and ZIP code here. Many VISA payment systems use the ZIP code along with the PIN to validate the correct user.  I look up a name and address for a real person, with a common name, somewhere else and "borrow" their name for this 1 transaction.  
[*]For the VPN, there are really 2 secure-enough technical solutions - openvpn and wireguard.  I want a provider that does at least 1 of those.  I avoid providers using commercial VPN tools.  In an old job, I deployed VPN for 25,000 users. We used a commercial solution with a SecurID fob. I watch the IT security announcements and every year one of the commercial VPN tools seems to announce a failure in a deployment that effectively made the VPN useless for some months.  OpenVPN can be setup to be very non-secure too. Some of the default settings commonly used have been cracked by govts around the world.  The VPN provider I used last year allowed some control by users to drastically improve they crypto for our connections, but it wasn't the default which was used by most people.
[*]The VPN will slow all connections. There's an extra middle-man between everything, after all.
[*]There is TOR too, and for many people it is fine. A few years ago, I read an article about TOR that estimated 30-60% of all exit nodes were run by different govt spy agencies.  Read up about TOR for why it can be anonymous, but has some very important caveats.  For example, if you've ever use TOR and connected to UbuntuForums.org using your normal userid for the login, then you've just broken the veil of privacy.  When using TOR, never use any accounts that you've used before. It is best not to post at all, since we each have a writing style that can be "finger printed" on the internet. That will lead back to an individual as well, for a sufficiently motivated searcher.
[/LIST]

Privacy is never a yes/no question. It is always on a scale. Always.

But most of us aren't doing anything nefarious or illegal. We just don't think it is anyone else's business. How much is more privacy worth, since it isn't automatic? That's the question.

---

### Post by DuckHook on 2021-02-17
> **linuxyogi said:**
> @TheFu / @DuckHook

Do you guys encrypt you DNS ? Which solution are you using ? DoH or DoT ?
If you are using DoT it will give me a sense of confidence.
You don't need us to be using it in order to feel safe. LinuxBabe writes excellent tutorials and I've used some of them to good effect. FWIW, I use DoH, not DoT, but would consider using DoT without any qualms. I found [this article]("https://www.dnsfilter.com/blog/dns-over-tls") which delineates the differences between DoH and DoT. It's a pretty good high&#8209;level overview without too much techno&#8209;babble.

BTW, as an interesting side note, I'm not sure that LinuxBabe is a "babe". Could be a "he", though these days, I suppose there's nothing to stop a he from also being a babe. The point is that privacy and anonymity are the things that make such ambiguity possible. I consider them indispensable qualities that must be defended.

A further exposition that might help:

Though related, anonymity and privacy are not the same thing. People too often mistakenly conflate them. Best to explain with examples.

[LIST=1]
[*]When you sign in to this forum, it is neither private nor anonymous.
[*]When you interact with your bank, you must have privacy, but it is not anonymous.
[*]When you post on some comment board, you may want anonymity, but it is not private.
[*]When you visit a dissidents' site under an oppressive regime, you need both anonymity and privacy.
[/LIST]
It is more clarifying to break things down in such detail because it allows for different methods/tools/strategies for each.

DoH and DoT give you limited privacy, but they do not give you anonymity. Why is it only limited? Because at some point, a service provider has to take your DNS request and translate it into the actual IP address of the site you want to reach. That service provider will know what you are visiting. This is why TheFu states that you can only push the trust issue further up the food chain, you cannot mask it entirely. You can use DNS resolvers who make a big deal about how "private" they are. I'm more naïve about this than TheFu and am willing to put some level of trust in providers like Quad9.

But although this limitation exists, you can go a long way to eliminating the sheer number of intermediaries by using a VPN provider. A VPN tunnels ***all*** traffic between your machine (or your router if it is set up that way) and their server. Neither your ISP nor anyone else in between can see anything that's transmitted. Your VPN provider will likely run their own DNS resolver too, so you don't even need to trust a third party like Cloudflare or Quad9.

Like TheFu, my choice of VPN provider is based on who has actually been trooped before a court and has demonstrated in front of a judge that they simply do not keep logs. This means that they physically lack the means to track me even under duress. This is as close to private as we are going to get.

For anonymity, the number one rule is to minimize interactivity. This is hard. It's way harder than most people realize, because the Internet's raison d'etre is interacting with stuff. Why else do we go online? But like TheFu states, we can be identified in any of dozens of myriad ways, some incredibly cunning. TOR Browser is a good first guard but too many use it ignorantly. Do not use it in anything other than its default configuration. Do not add any extensions. Do not resize it on your desktop. Do not enter any info while using it. If you are going to fill in some form or sign&#8209;in, you will have entirely defeated the point of TOR Browser and may as well have used a regular browser.

I too have read many articles calling TOR Browser's bona fides into question. Many are just grinding their axe, but a few raise legitimate concerns. If enough nodes fall into the clutches of a three&#8209;letter agency, then it is possible to analyze the data packets to match up point of origin and destination. It's a known weakness in the TOR model. TOR themselves state outright that their objective is to have so many nodes signed up and operating that it becomes pragmatically impossible for any one player to pull off such an analytical deconstruction. So, for what it's worth, take this into consideration when using TOR.

You can layer strategies to achieve even better results. Running TOR over a VPN will yield a very tough nut indeed. I'm convinced that nothing is uncrackable, but that combo would come close, always provided that the operator is not an idiot.

That last point is key: the weakest security/anonymity/privacy link in any chain is the one between the keyboard and the chair. 90% of privacy/security/identity breaches is due to our own carelessness. This should put the current discussion in a more sobering context. Because, while it is important to understand measures like DoT/DoH, they are useless without good user habits. If you reuse passwords between different sites, then obsessing over DoT vs DoH is like rearranging deck chairs on the Titanic.

---

### Post by TheFu on 2021-02-17
You have not disabled IPv6 if you didn't modify the kernel options passed in by grub.  The old ways stopped working around the time that systemd was forced onto us.
```
$ ping google.com
PING google.com (142.250.105.102) 56(84) bytes of data.
64 bytes from 142.250.105.102: icmp_seq=1 ttl=56 time=28.8 ms
64 bytes from 142.250.105.102: icmp_seq=2 ttl=56 time=13.2 ms
^C
```
is what no IPv6 looks like.

I use DoH on 2 of my systems. The others point at a pihole for DNS and updating the config for that to use some encrypted DNS is on my list of things to do.

DuckHook did a good job explaining things.  One more thing.  VPNs almost always leak DNS queries.  I've not seen any VPN available to home users that didn't leak DNS without extra care, extra settings, required.

---

### Post by DuckHook on 2021-02-17
I can't help feeling uneasy about this whole exchange. While it is useful to look into DoT/DoH, by overly focusing on your ISP, I think there's a real danger of missing the forest for the trees.

To be dead honest, I'm not really that worried about my ISP knowing who I bank with. In my neck of the woods, there are only a handful of banks. If they narrow it down to one, it will hardly be surprising and only marginally useful info. They already have my credit card info for my monthly charges. They know where I live, what my bandwidth and usage patterns are, and they are perfectly positioned to do deep packet inspection of every byte that passes into or out of my house. Even if encrypted via VPN, modern analytical tools can extrapolate data of surprising relevancy using only statistical models and side channels.

If my ISP or some three&#8209;letter agency decides that they are after my data, there's very little that I or Joe Ordinary can do about it. This is what makes the conspiracy nuts so laughable: if the government is really targeting you, your best course of action is to call them up and say: "I have no idea why you find me a 'person of interest', but whatever it is, you have my full cooperation". These agencies are too massive and too powerful to fight.

My real worries are twofold:

First are the small and medium fry. From script kiddies to mob syndicates, they are the ones that can give me a really bad day. I'm worried about MitM attacks. My ISP isn't going to do that. I'm worried about ransomware. My ISP isn't going to do that. I'm worried about identity theft. My ISP isn't going to do that either. So, in these regards, focusing on my ISP is not only misdirected, but a waste of time and resources.

Second are the meta&#8209;dangers. I don't like having a shadow version of me floating around out there being sold over and over to whoever waves a nickle under some nameless company's nose. [See this.]("https://privacyinternational.org/long-read/4398/companies-control-our-secret-identities") It's a fascinating/frightening look at how each of us has a virtual simulacrum walking around who looks like us, walks like us and quacks like us. We never gave it permission to spring into being, we have no control over how it's abused, and we are basically powerless to get rid of it. What we ***can*** do is prevent—or at least stunt—its creation in the first place. We can also stop contributing to its continuing sustenance.

The ISP is part of this second danger, but it's only one of many villains. In my opinion, this is far and away the larger danger because it is both pernicious and chronic. But just blinding the ISP does little to remedy it. It grows every time we buy online, every time we leave our e&#8209;mail address, every time we sign up/sign in to something. But this trail is nothing—and I mean ***NOTHING***—compared to how much our participation in social media feeds it. If you use Facebook, Twitter, Whatsapp, Snapchat, Instagram, Google&#8209;anything, blah&#8209;blah&#8209;blah, then why are you even thinking about your ISP? You've got way bigger problems than your service providers. Unless you take measures far beyond DoT/DoH, you haven't even begun to nibble away at this danger. I would say that social media today (plus Google) is over 90% of the real danger. Your ISP just brings up the rear.

I realize that this has gone far beyond your initial inquiry. Apologies if it is a bit of a hijack. But placing your concerns within a larger context may prove both useful and food for further thought.

With that, I think I'll keep quiet now.

---

### Post by linuxyogi on 2021-02-18
Conclusion :
1) No matter what measures a user implements achieving 100% privacy is impossible.
2) The only way to achieve the maximum possible privacy is to use a VPN.
3) The next best tool after a VPN is Tor but Tor is not effective enough in comparison to a good VPN.

Thanks to both of you.

---

### Post by DuckHook on 2021-02-18
> **linuxyogi said:**
> 1) No matter what measures a user implements achieving 100% privacy is impossible.
Correct.
> 2) The only way to achieve the maximum possible privacy is to use a VPN.
Correct.
> 3) The next best tool after a VPN is Tor but Tor is not effective enough in comparison to a good VPN.
Almost but not quite.

[LIST]
[*]*If used correctly*, TOR is for anonymity (with a bit more privacy).
[*]*If used correctly*, VPN is for privacy (with a bit more anonymity).
[*]*If used correctly*, the two together kick serious butt.
[/LIST]
Now I really will be quiet for a while.

---

### Post by SeijiSensei on 2021-02-18
All my DNS queries go to a server on my local network running BIND.  From my reading of this discussion, encrypting DNS only affects the traffic between the client and the DNS server.  As a result I don't use encryption and don't think I need to.

---

### Post by linuxyogi on 2021-02-18
> **SeijiSensei said:**
> As a result I don't use encryption and don't think I need to.
I too was using unencrypted DNS for a very long time until I read articles like this >> [https://blog.cloudflare.com/dns-encryption-explained/](https://blog.cloudflare.com/dns-encryption-explained/)

>  **Unencrypted DNS**
Ever since DNS was  created in 1987, it has been largely unencrypted. Everyone between your  device and the resolver is able to snoop on or even modify your DNS  queries and responses. This includes anyone in your local Wi-Fi network,  your Internet Service Provider (ISP), and transit providers. This may  affect your privacy by revealing the domain names that are you are  visiting.



---

### Post by linuxyogi on 2021-02-19
> **TheFu said:**
> 
[LIST]
[*] if you've ever use TOR and connected to UbuntuForums.org using your normal userid for the login, then you've just broken the veil of privacy.  When using TOR, never use any accounts that you've used before. It is best not to post at all, since we each have a writing style that can be "finger printed" on the internet. That will lead back to an individual as well, for a sufficiently motivated searcher. 
[/LIST]


Yes I agree but that makes me think. What is the role of a solution like this ? >> [https://magpi.raspberrypi.org/articles/tor-router](https://magpi.raspberrypi.org/articles/tor-router)
That will route everything a person does via the Tor nerwork.

---

### Post by SeijiSensei on 2021-02-19
> **linuxyogi said:**
> I too was using unencrypted DNS for a very long time until I read articles like this >> [https://blog.cloudflare.com/dns-encryption-explained/](https://blog.cloudflare.com/dns-encryption-explained/)

> Everyone between your device and the resolver is able to snoop on or even modify your DNS queries and responses. 
There isn't anyone between me and the DNS server; that was my point. I generally don't have other people on my wifi network either, and those that do connect have no interest in my DNS queries.

I'm more interested in what happens between my local DNS server and the upstream servers it consults when resolving a name. I presume that server-to-server traffic happens in the clear, or is it encrypted these days?

---

### Post by linuxyogi on 2021-02-20
> **SeijiSensei said:**
> I presume that server-to-server traffic happens in the clear, or is it encrypted these days?
I think both DoH & DoT encrypts that too.

Please wait for DuckHook or TheFu for the confirmation.

---

### Post by DuckHook on 2021-02-20
I have no expertise at all in server to server stuff, but here's what I've gleaned from reading:

[LIST]
[*]I don't believe that server to server is encrypted out of the box. One must consciously take additional measures to do that. Much of our infrastructure was developed in more innocent times. Sadly, those days are long gone.
[*]Server to server is a legitimate worry because it offers an ideal attack surface for supply chain poisoning. In fact, from a consumer standpoint, it's more insidious because the measures to safeguard against MitM attacks that are available to us as consumers can only guard us as far as our DNS resolver endpoint. Anything further up the food chain must rely on the security chops of the DNS service provider. It's one of the (possibly self-serving) reasons often given not to rely on small DNS providers.
[*]The technical aspects are a lot murkier to me. I've read that it involves DNSSEC, further more esoteric forms of encryption, keys/certificates and so forth, but I've never investigated it in depth because it is awfully arcane stuff and, let's face it, when is a Joe Ordinary like me ever going to implement something like that? Those administering organizations of 10,000, sure, but running a DNS server for Mrs DH and me? Seriously?
[*]I've read about canned "secure" DNS solutions that are meant for big firms. I have no reason to doubt their security bona fides—after all, supplying demand is one of the benefits of free enterprise—but, frankly, I'm just not qualified to even comment of this aspect of security.
[/LIST]
All I can tell you is that such concerns keep me focused on Quad9, Cloudflare, Adguard, etc. I avoid small DNS providers—possibly unfairly—because I don't know enough about them to trust their security savvy.

As a side note: one of the reasons that I don't use my ISP's DNS service is because of above security concern. They are a big outfit, but their primary business is not DNS.

A further side note: like TheFu states, DNS leakage happens all over the place, even with VPN. I'm aware of those pitfalls. I don't even use DoH/DoT to stop DNS spying, but to nuke ads. That's the reason my DoH endpoint for mobile is Adguard (which is a smaller outfit) and not Quad9 or Cloudflare.

---

### Post by TheFu on 2021-02-22
The only automatic DNS encryption that we get is from default settings in Firefox which ignore your local DNS settings for that browser. If you are able to hit internal LAN servers that are not available on the internet too, then perhaps you previously disabled the firefox built-in DNS-over-HTTPS which became default over the last year or so. I think they rolled it out slowly and finished sometime last fall.

linuxyogi, you are trying to create absolute answers where none exist. 
> Conclusion :
1) No matter what measures a user implements achieving 100% privacy is impossible.
2) The only way to achieve the maximum possible privacy is to use a VPN.
3) The next best tool after a VPN is Tor but Tor is not effective enough in comparison to a good VPN.

1) saying that something is 100% impossible isn't factual. There are possible ways, but for normal people, it is highly unlikely and very difficult. YOUR behavior matters.
2) a VPN doesn't provide privacy from everyone and whether that is maximum would depend on who the goal to be private is from. If you use a VPN, and post your real name, address, telephone numbers and visit all the same places that you visited pre-VPN, there is little chance that motivated person wouldn't be able to discover those things.  YOUR behavior matters.
3) Comparing a VPN and TOR is like comparing a boat and a taxi.  They have different purposes.  Regardless, YOUR behavior matters with using either and both.

There are seldom absolutes without 3 pages of caveats included.

If you don't want your ISP tracking you and that's it, using a VPN with an external DNS that isn't leaked around the VPN, and the VPN has sufficiently strong encryption (AES256 or better) and the VPN doesn't use a known cracked protocol (cough, TLS v1.2), and the VPN exit node is outside your country, but not in another country friendly to yours, and .... and ... and ... and ... then it is safe to watch cartoons and may be safe to do other activities.  If the ISP is the parent company of your VPN or the external DNS, all bets are off.  If you use ISP email and check it when connected to the VPN, now they know your current IP ... see how YOUR behavior matters?  Some govts may have rules to track Internet users, VPN access, because ... I don't know ...  they are afraid of any electronic financial transactions using any sorts of privately traded blockchain currencies.  Very, very, few of those are untraceable, BTW.

---

### Post by TheFu on 2021-02-23
Fresh browser/tor/dns issue.
[https://www.theregister.com/2021/02/22/in_brief_security/](https://www.theregister.com/2021/02/22/in_brief_security/)

Browsers are very complex and have bugs. Do not only trust the browser, if you want privacy. They routinely fail.

---

### Post by kevdog on 2021-02-23
@DuckHook

You don't run a pfsense router with built-in DNS resolver? I thought this setup was pretty common now a days for even home users.  And yes -- I mean -- Serious!

---

### Post by DuckHook on 2021-02-23
> **kevdog said:**
> @DuckHook

You don't run a pfsense router with built-in DNS resolver? I thought this setup was pretty common now a days for even home users.  And yes -- I mean -- Serious!
No, I rely on my router almost entirely to provide those services. I am mildly curious about PfSense and now OPNsense (since TheFu mentioned it above), but to be dead honest, it's yet another "thing" I would have to juggle and I'm a lazy sort who just wants something trustworthy that I can set up properly one time, review occasionally, but otherwise largely forget.

Perhaps it would help if I can provide a really high&#8209;level summary of everything that I've written above:

[LIST]
[*]I do not believe that one can realistically "hide" oneself on the Internet. It's possible if one never interacts, but what would be the point?
[*]As already stated, I'm not overly concerned about my ISP knowing which sites I visit. I'm a really boring guy. I visit a lot of tech sites, some mainstream media sites, a few of the big online stores—that's about it. I am as exciting as warmed over rice porridge.
[*]When I visit important sites like my bank, accountants, lawyers, medical etc, I take special measures constrained to certain browsers.
[*]On the exceedingly few occasions that I wish to remain both private and anonymous, I tunnel to my VPN and use TOR Browser.
[*]Other than the above, I have no illusions that what I do online is either private or anonymous. Example: I am now hobnobbing with all of you in the clear. No VPN, no TOR. My FF is DoH-ed into Adguard. I do this not to protect my privacy but to nix ads (which can themselves be pernicious ID profilers).
[/LIST]
Another way to look at it is quantitatively. On a 10&#8209;point scale (10 being the most concerning):
[table="width: 30"]
[tr]
	[td]DNS privacy[/td]
	[td]2[/td]
[/tr]
[tr]
	[td]DNS security[/td]
	[td]10[/td]
[/tr]
[tr]
	[td]ISP spying[/td]
	[td]2[/td]
[/tr]
[tr]
	[td]Profiling[/td]
	[td]11[/td]
[/tr]
[/table]
Note that none of the "critical" stuff involves doing anything special with routers. Instead, it's all about behaviour and habits. Not much there that involves tinkering with hardware or software.

Overall, the biggest issue that I see among all of my friends and family is—it can only be stated bluntly—hypocrisy. They too are concerned about profiling, but unwilling to give up any of the drugs that the profilers hand out to reel them in. I mean, what is the point in profile anxiety when you are the one enthusiastically filling out that Facebook profile page? It's even plainly called a *"profile"* page.

Most people don't really understand "privacy". They throw very disparate elements together into a big vegetable stew and think that magic apps/devices can make up for their lack of care. /rant

So, no, I don't use PfSense with its built&#8209;in DNS resolver. I do use DD-WRT with its DNSSEC connection to a big external DNS resolver, in my case, Quad9, and I do so not to hide from anybody, but for packet integrity/security.

---

### Post by kevdog on 2021-02-23
@DuckHook.  I use QuadDNS for DOT.  This based on a video done at Lawrence Systems which compared the major DNS providers.  

I agree with the overall assumptions of this thread.  It's almost impossible to anonymize oneself since DNS resolution needs to be done somewhere.  I'm not exactly sure TOR is the answer since I believe a lot of the nodes are run by various government authorities.  

I see you said you're running DOH with Firefox.  I have no problem with that, however I think DNS is better controlled at the router level rather than the individual application level at least for my network since I can control all requests on port 53 and redirect them to port 853 and DOT through Quad 9.  I also just think its quicker to DNS resolve at the router level.  I don't know if you run any servers/docker containers on your LAN.  A local DNS resolver is really really helpful in this situation.  In addition segmentation of network traffic via use of VLANs I think is important to segment off the LAN for security purposes.  

I've use pfSense and I'm aware the OPNsense if a fork of pfSense.  I don't know a lot about OPNsense but I'm pretty familiar with pfSense.  I run my pfSense within a hypervisor for my LAN.  It takes definitely a little bit of reading to get things setup and running, however I find it pretty straightforward -- so much so it's pretty set it and forget it now.  If I need to add more VLANs or advanced firewalling, I definitely need to go back and read a little bit since it's not something I really mess with but once in great while. I used to used DD-WRT, however I definitely say pfSense way more advanced in terms of features.  I'm not sure if you do much traveling or need remote access to your LAN, however the ability to run an OpenVPN server through pfSense is really really good and pretty easy to setup.  Supposedly the new version can also do Wireguard, however I'm really pleased with OpenVPN thus far and really don't find a lot of reasons to switch.  The ability to use OpenVPN through the home router is also a security measure if ever accessing internet through open unprotected wifi such as hotels or other areas like coffee shops.

---

### Post by TheFu on 2021-02-23
> **DuckHook said:**
>  I'm a lazy sort who just wants something trustworthy that I can set up properly one time, review occasionally, but otherwise largely forget.
This is why I use OPNSense.  I got tired of consumer routers losing support, so I spent the effort to end that for 10+ yrs at a time, by getting HW specifically designed to be a router, AMD64-compatible, running a BSD router OS with bonehead simple patching and upgrading - AND NO WIFI.  I keep wifi separate from routing.

> **DuckHook said:**
>  
[LIST]
[*]I am as exciting as warmed over rice porridge.
[/LIST]
Please tell more!  I've been meaning to learn to make rice porridge in the rice cooker. ;)

> **DuckHook said:**
>  
[LIST]
[*]Other than the above, I have no illusions that what I do online is either private or anonymous. Example: I am now hobnobbing with all of you in the clear. No VPN, no TOR. My FF is DoH-ed into Adguard. I do this not to protect my privacy but to nix ads (which can themselves be pernicious ID profilers).
[/LIST]
I use a pihole with adblocking lists for DNS on the LAN, not the OPNSense router. I stopped running AV on my LAN systems once my professional insurance wasn't needed for clients anymore.  E&O professional insurance has all sorts of Windows-centric mandates.  Obviously, in my security lab, use of any AV wasn't normal unless that was part of the client's statement of work.

> **DuckHook said:**
>  
Overall, the biggest issue that I see among all of my friends and family is—it can only be stated bluntly—hypocrisy. They too are concerned about profiling, but unwilling to give up any of the drugs that the profilers hand out to reel them in.
My family doesn't care at all. They've all given up or feel that whatever Apple provides is sufficient.  Even the computer nerds who run servers don't seem to care. The family under about age 35 don't care at all - they accept being followed, always and strive to post "stories" somewhere - which I don't get. Whatever.  My friends are about 50/50. Some try to be private and secure, but the other half have given up.  Many friends are CISSPs and work as security consultants or in enterprise security teams. The vast majority have every social networking account possible.  One friend worked in SIGINT and he will get ranting about people using centralized accounts anywhere .... from this gmail account.   <forehead slap!>

> **DuckHook said:**
>  So, no, I don't use PfSense with its built&#8209;in DNS resolver. I do use DD-WRT with its DNSSEC connection to a big external DNS resolver, in my case, Quad9, and I do so not to hide from anybody, but for packet integrity/security.

dd-wrt that is patched at least quarterly is probably 99% more secure than what most people do at home.  For a few years, I used dd-wrt and it was great, until the angel who created the firmware updates got a new router and stopped supporting my hardware. Sure, I could have setup a build environment and become the maintainer for that device going forward or switched to using x86/amd64 releases of dd-wrt and been just as secure.  

Along the way, I had a client that needed excellent QoS control for their campus which had about 6 enterprise wifi APs and up to 80 people. Across the street was a CCP-Chinese compound keeping track of the exiled Tibetan Buddhist Monks in the monastery and their internet use. Anyways, they cared about internet security and the privacy of their communications. It wasn't just some thought exercise. Any day they left the compound, a van could abduct them on the tiny road that these too compounds shared and nobody would know that happened. Ever.

---

### Post by DuckHook on 2021-02-23
> **kevdog said:**
> I'm not exactly sure TOR is the answer since I believe a lot of the nodes are run by various government authorities.
This is the usual concern. I can't say it is without substance, hence the VPN double layer.
> I see you said you're running DOH with Firefox.
…But, as said, for reasons other than privacy. I may as well fully digress from OP's topic.

I try to have as few extensions loaded on FF as I can. There was suspicion some time ago the ad blockers were themselves reporting back to mothership. So it becomes a game of weighing whether I distrust ad blockers or Adguard more. I chose Adguard over ad blockers.
> …I don't know if you run any servers/docker containers on your LAN.  A local DNS resolver is really really helpful in this situation.
A number of servers, but all for internal use. I just started my first external a couple of months ago with Nextcloud. Prior to that, all I needed was a router solution that completely closed off every incoming port. 
> In addition segmentation of network traffic via use of VLANs I think is important to segment off the LAN for security purposes.
DD-WRT can do that. I will look into it. Thanks for the heads&#8209;up.
> I used to used DD-WRT, however I definitely say pfSense way more advanced in terms of features.
I have no doubt that it is. We are comparing an appliance to a full fledged platform. Sorta like comparing a scooter to a Ferrari. The latter is bound to be more powerful.
> I'm not sure if you do much traveling or need remote access to your LAN, however the ability to run an OpenVPN server through pfSense is really really good and pretty easy to setup.  Supposedly the new version can also do Wireguard, however I'm really pleased with OpenVPN thus far and really don't find a lot of reasons to switch.  The ability to use OpenVPN through the home router is also a security measure if ever accessing internet through open unprotected wifi such as hotels or other areas like coffee shops.I'm retired, so travel is all pleasure. When travelling, I've hitherto wanted to leave all home cares behind, so little need for connection. Hitherto mind you.

I'm now testing Nextcloud because I'm uneasy about having my stuff on someone else's platform. I had long ago dropped Google, but my photos are on Piwigo, and I'm not happy even with that. My initial feelings about Nextcloud have been phenomenal. But it does require me to look very carefully at security. For the first time, ports have been forwarded into my LAN. They go straight to an unprivileged LXD contained instance of Nextcloud with fail2ban, forced SSL and only one login (me), but it still constitutes a penetration of my firewall and I readily admit that that makes me squirm.

> **TheFu said:**
> Please tell more!  I've been meaning to learn to make rice porridge in the rice cooker. ;)
Since we are now in full hijack mode, I will keep it short: rice cooker&#8594;ixnay. They are designed to get rice just right, which obviously is not a runny liquidy porridge state. Better to use a deep pot, very little rice, lots of water (I really mean a palmful of rice to 4 litres of water), absolutely minimal heat so that it's just slightly simmering and NO lid. Otherwise, it is guaranteed to foam, boil over and ruin your day. Takes a while, so start early.

> I use a pihole with adblocking lists for DNS on the LAN, not the OPNSense router. I stopped running AV on my LAN systems once my professional insurance wasn't needed for clients anymore.  E&O professional insurance has all sorts of Windows-centric mandates.  Obviously, in my security lab, use of any AV wasn't normal unless that was part of the client's statement of work.
Security lab. Right. You just confirmed for me that you come from a very different universe to that of mere mortals like me.

> My family doesn't care at all. They've all given up or feel that whatever Apple provides is sufficient.  Even the computer nerds who run servers don't seem to care. The family under about age 35 don't care at all - they accept being followed, always and strive to post "stories" somewhere - which I don't get. Whatever.  My friends are about 50/50. Some try to be private and secure, but the other half have given up.  Many friends are CISSPs and work as security consultants or in enterprise security teams. The vast majority have every social networking account possible.  One friend worked in SIGINT and he will get ranting about people using centralized accounts anywhere .... from this gmail account.   <forehead slap!>
It's sad. In my more despondent moments, I feel like the profilers have won through sheer attrition. They've worn down even the most dedicated of us by making it impossible to avoid them. These days, a professional who must engage with others is forced to have a LinkedIn page, a Twitter account, a half dozen social media profiles and twenty different messaging/chatting connections. There's no real&#8209;world alternative because refusing to do so means no food on the table. Look what we went through last year: Zoom has more holes than Swiss cheese, but is completely unavoidable for most people.

I'm lucky that I'm retired. It gives me the freedom to tell them to go stuff it. I've been trying (with varying success) to at least switch my retired friends to Signal and XMPP-based messaging. But it's hard. Their kids are all on Whatsapp, Twitter, Instagram, Facebook… So the choice is messaging either solely with me or with the rest of their friends and family. My personality is not magnetic enough to force that issue.
> dd-wrt that is patched at least quarterly is probably 99% more secure than what most people do at home.  For a few years, I used dd-wrt and it was great, until the angel who created the firmware updates got a new router and stopped supporting my hardware. Sure, I could have setup a build environment and become the maintainer for that device going forward or switched to using x86/amd64 releases of dd-wrt and been just as secure.
I'm not going to pretend that I upgrade every quarter, but I do keep my ear to the ground and upgrade about once a year. More frequently if a nasty exploit is discovered. I purchased a newish model recently. It should remain supported for at least a few years. If not, I will certainly consider then going to Pf/OPNsense.

I sure hope that linuxyogi isn't too upset at our shameless hijack. :biggrin:

---

### Post by kevdog on 2021-02-24
Hey about that Nextcloud thing -- yeah just stick a VPN in front of it -- and you don't have to worry about opening it up to the world!!

---

### Post by DuckHook on 2021-02-24
> **kevdog said:**
> Hey about that Nextcloud thing -- yeah just stick a VPN in front of it -- and you don't have to worry about opening it up to the world!!
I considered it. But I eventually want to offer its use to Mrs DH and the kids. Even selected friends if I can convince myself that it is resilient, can be made reliable and is not too burdensome on me. I already have a VPN set up on my router, but unfortunately, while it isn't any trouble for a tech&#8209;head like me, it just wouldn't work for the Mrs or for others.

Thanks for the thought though.

PS

I do like your suggestion of hiving it off on a VLAN. DD-WRT supports isolating a physical port and segmenting the LAN. I will play a bit with that idea.

---

### Post by kevdog on 2021-02-24
In terms of VLANs, I'm not sure how your Nextcloud setup is configured, however I needed some interVLAN routing.  I'm not certain how DD-WRT handles interVLAN routing since if using this combination you need a router and managed switches capable of handling the VLAN tagging.

---

### Post by TheFu on 2021-02-24
VPNs are used by normal people all the time. 

IMHO, better than putting a php web-app as complex as nextcloud on the internet when it is running inside your LAN.  Mrs DH and the kids should probably be using the VPN full time from their phones anyway. The VPN client configs are pretty easy to setup these days.  They use 2d barcodes and the standard VPN client for the platform.

---

### Post by DuckHook on 2021-02-24
> **kevdog said:**
> In terms of VLANs, I'm not sure how your Nextcloud setup is configured, however I needed some interVLAN routing.  I'm not certain how DD-WRT handles interVLAN routing since if using this combination you need a router and managed switches capable of handling the VLAN tagging.
Current versions of DD-WRT have VLAN tagging. However, I don't purpose to go down that rabbit hole. I'm considering just segmenting one physical port off of the router and attaching my Nextcloud server to it. That way, Nextcloud doesn't even see my LAN. If I get really ambitious, I might install another NIC on the server, bind it to the Nextcloud container, and keep my original NIC for the the physical server. I would have to be very sure of the security implications of that, but it would certainly be more convenient.
> **TheFu said:**
> VPNs are used by normal people all the time. 

IMHO, better than putting a php web-app as complex as nextcloud on the internet when it is running inside your LAN.  Mrs DH and the kids should probably be using the VPN full time from their phones anyway. The VPN client configs are pretty easy to setup these days.  They use 2d barcodes and the standard VPN client for the platform.
Mrs DH, bless her, is a far better person than me in every which way, but she cannot wrap her head around how the gear shift works on a bicycle. It took me years of patience and waiting to wean her off Vista and onto Ubuntu. A VPN is a non&#8209;starter. The kids are a different matter, and the grandkids take to this stuff like fish take to water, but I have found that when it comes to tech, convenience is king. We just alluded to it a couple of postings earlier.

I'm afraid that I will need to keep it stupid&#8209;simple, else everyone will just keep using Google Drive/Onedrive/Dropbox + their plethora of privacy&#8209;murdering/profiling platforms merely because those are less "fussy".

---

### Post by DuckHook on 2021-02-24
To drag this thread kicking and screaming back on topic…

@linuxyogi

I thought this article might interest you: [https://www.theregister.com/2021/02/24/dns_cname_tracking/](https://www.theregister.com/2021/02/24/dns_cname_tracking/)

Forewarning: It makes for depressing reading, but my intent is not to ruin your day; it is to give you a realistic idea of what DoT and DoH achieve so that you don't get a false sense of security.

It also reinforces other elements of this thread: that we have far more to worry about from other parties than from our ISPs.

---

### Post by linuxyogi on 2021-02-24
@DuckHook || @TheFu
I read that article. I give up. I will keep using DoT & hope for the best.

---

### Post by DuckHook on 2021-02-25
> **linuxyogi said:**
> &#8230;I give up&#8230;
Well, don't go *that* far. Our privacy is still worth the good fight, and there are also good people fighting on our behalf. From the same article: > Firefox running the add-on uBlock Origin 1.25+ can see through CNAME deception. So too can Brave, which recently had to repair its CNAME defenses due to problems it created with Tor.
My intent was not to discourage you but to point out where the real enemy is. Once known, we can take measures to beat them. But make no mistake&#8212;it is not a fire and forget world that we live in. It is more like trench warfare where we constantly have to improvise solutions against many pressure points. But it *IS* doable if we take the time to "know thy enemy".

So don't despair. But do stay vigilant. And it pays to keep our eye on new developments in the security/privacy/profiling front.

---

### Post by linuxyogi on 2021-02-25
@DuckHook
I use uBlock Origin under Firefox. I use Brave too but I haven't installed any addons on Brave coz I read its privacy focused by default. Do you think I should install uBlock Origin under Brave too ?
I must also mention that I check for updates every morning, every single day. So no delay in installing security patches.

---

### Post by DuckHook on 2021-02-25
> **linuxyogi said:**
> …Do you think I should install uBlock Origin under Brave too ?
Brave is sufficient on its own. It does not need further adblocking extensions. In fact, extensions are also something to carefully weigh, although stuff like NoScript, Ghostery and similar reputable ones are very useful. It bears mentioning that FF and Brave have evolved—and continue to evolve—to fight many kinds of these tricks. It's another example of the good guys winning some battles on our behalf, another reason for hope and carrying on. I contribute a small amount yearly to the Mozilla foundation. Do whatever you can to help.

I hope that you are starting to understand the two main themes in all of the above:

The first is that overly focusing on any sole set of tools is misguided. Of course we should use DoT/DoH. It's only sensible to do so. But there are many other measures that we must also take. A thread like this cannot teach you all of those things. It will involve a lot of reading and research, but that knowledge will empower you, so don't succumb to the dismay that it also sometimes brings.

The second is that you should revisit your privacy expectations. This is a more subtle point but it is just as important. I have already posted my thoughts on privacy in a few passages above. TheFu also posted a very useful reply quite early in this thread. It is so pertinent that I will quote most of it in its entirety:
> **TheFu said:**
> If you want real privacy, don't use the internet.
There are different levels of privacy and how much you want probably doesn't overlap with how much is easy to accomplish. It isn't for me.

When I want privacy, 
[LIST]
[*]I don't do it from home.  I use a mom-pop cafe, not a corporate one. Corporate places with free wifi are everywhere. Assume those places are capturing your image, connection, DNS, and browsing. There are mitigations against each.
[*]Use a full, paid, VPN who you can trust.  How to know whether you can trust any VPN isn't easy.  You'll need to work into the ownership, logging, and truly who is behind it. Often, the more privacy they claim to provide, the more likely your data ends up in a parent companies hands.  Having headquarters in small countries often means the VPN can manipulate the govt there.  If the CEO/President and CIO for a VPN provider don't actually live in the country where their HQ is located, I consider that a warning sign too.
[*]How has the VPN reacted towards legal demands to provide information on the users?  If you don't hear anything about them fighting cased in court - what does that mean?  To me, it means they handed it all over.  I know of only 1 VPN provider who has fought legal battles AND proved they couldn't provide any logs to the govt, so the govt went away.
[*]When you sign up to pay for a VPN, use anonymous payment methods. Financial tracking is a real thing.  Every year or two, I buy a Gift VISA card to buy VPN service. There is a pre-paid service charge for this ... basically I'm paying 10% more to ensure privacy. This card cannot have more money added to it. The cards that support adding are more traceable. To be used on the internet, we have to register the card with a name and ZIP code here. Many VISA payment systems use the ZIP code along with the PIN to validate the correct user.  I look up a name and address for a real person, with a common name, somewhere else and "borrow" their name for this 1 transaction.  
[*]For the VPN, there are really 2 secure-enough technical solutions - openvpn and wireguard.  I want a provider that does at least 1 of those.  I avoid providers using commercial VPN tools.  In an old job, I deployed VPN for 25,000 users. We used a commercial solution with a SecurID fob. I watch the IT security announcements and every year one of the commercial VPN tools seems to announce a failure in a deployment that effectively made the VPN useless for some months.  OpenVPN can be setup to be very non-secure too. Some of the default settings commonly used have been cracked by govts around the world.  The VPN provider I used last year allowed some control by users to drastically improve they crypto for our connections, but it wasn't the default which was used by most people.
[*]The VPN will slow all connections. There's an extra middle-man between everything, after all.
[*]There is TOR too, and for many people it is fine. A few years ago, I read an article about TOR that estimated 30-60% of all exit nodes were run by different govt spy agencies.  Read up about TOR for why it can be anonymous, but has some very important caveats.  For example, if you've ever use TOR and connected to UbuntuForums.org using your normal userid for the login, then you've just broken the veil of privacy.  When using TOR, never use any accounts that you've used before. It is best not to post at all, since we each have a writing style that can be "finger printed" on the internet. That will lead back to an individual as well, for a sufficiently motivated searcher.
[/LIST]

Privacy is never a yes/no question. It is always on a scale. Always.
Are you prepared to take such drastic measures? Because I'm not. They are just too burdensome and too constraining. I have accepted the fact that online life cannot be private or anonymous. I am more concerned about profiling and can try to keep it to a minimum, but I cannot make even that go away entirely. It's simply the price I pay for using the Internet.

BTW, by coincidence, your concerns are fortuitously being raised at the same time that a lot of explanatory articles have been popping up. Here's another—maybe the most important so far posted—from El Reg that appeared just today: [https://www.theregister.com/2021/02/25/big_tech_extension/](https://www.theregister.com/2021/02/25/big_tech_extension/)

I have personally conducted a similar experiment in a lesser and unsystematic way. If you install NoScript on FF and turn off absolutely all scripting, the Internet essentially becomes unusable. There are no sites these days that are scriptless. Even denying just Google scripts will break most sites. The big four have successfully insinuated themselves into the very fabric of the Internet and have become part of its DNA. Their combined market capitalization is almost 6 Trillion dollars US. They are richer, more powerful and more influential than most small countries. So there's a limit to how much we can do fiddling around with technology and browser extensions. The real way to combat their baleful influence is through legislation. I often feel that my efforts would be better spent canvassing my legislators than adding this or that doodad to my install.

The point is that you must have realistic expectations of what amount of privacy you can expect (profiling is a different matter). We no longer live in the world of our parents.

---

### Post by linuxyogi on 2021-03-04
> **DuckHook said:**
> So don't despair. But do stay vigilant. And it pays to keep our eye on new developments in the security/privacy/profiling front.
Can you recommend me a Youtube channel subscribing to which I will get to know the latest security news ?

---

### Post by DuckHook on 2021-03-04
> **linuxyogi said:**
> Can you recommend me a Youtube channel subscribing to which I will get to know the latest security news ?
I don't find Youtube useful for security learning/news. The security landscape changes too fast and developments pop in and out of existence too quickly for such a production-intensive medium. It's great for cooking/repair/do&#8209;it&#8209;yourself type stuff, but is poor for in&#8209;depth analysis or proper referencing. I use RSS/Atom feeds for security news. There are tons which a simple web search can find. I subscribe to the following, but you can easily find others including local feeds that may be more relevant to you:

[list=1]
[*][https://krebsonsecurity.com/feed/](https://krebsonsecurity.com/feed/)
[*][https://www.privacyinternational.org/rss.xml](https://www.privacyinternational.org/rss.xml)
[*][https://www.theregister.com/security/headlines.atom](https://www.theregister.com/security/headlines.atom)
[*][https://nakedsecurity.sophos.com/feed/](https://nakedsecurity.sophos.com/feed/)
[/list]
Do note that they can be overwhelming. I used to subscribe to more, but found a daily diet of such bad news both depressing and exhausting. It's best to cut back to only a few of the most valuable. I find a good combo to be just one breaking news feed, the rest more analysis/magazine type. Your mileage will vary depending on your personality and appetite for such stuff.

---

### Post by TheFu on 2021-03-04
> **DuckHook said:**
>  
I have personally conducted a similar experiment in a lesser and unsystematic way. If you install NoScript on FF and turn off absolutely all scripting, the Internet essentially becomes unusable. There are no sites these days that are scriptless. 

I've had a different experience.  Most sites will display the data I want without any scripting enabled. For example, ubuntuforums includes googletagmanager.com, but works fine without allowing any javascript or connection from that site.  In fact:
```
$ ping googletagmanager.com
PING googletagmanager.com (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.040 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.056 ms

```
my current system can't even resolve that name. I block many domains at the network layer, not just through DNS.  The web works fine for the most part - even casual google use still works.  I use a site called "xyz123".  They are all about tracking and have 13 tracking includes there.  All of those are prevented from running. I need to allow only the xyz123 and xyz123cdn for the site to work.  Those 13 other trackers - meh.  The same happens over and over and over.  Allow only the parts that actually need javascript to display content you want. Not anything else.

After a few sites, you'll learn which not to allow and to ban some.  
Another trick is to use the old mobile website version which didn't support javascript at all. All the content, fast. None of the extra junk.

How much tracking are we willing to have? Everyone has a different answer.  But we certainly don't need to blindly allow everything. It is always a negotiation. Always.

---

### Post by TheFu on 2021-03-04
> **linuxyogi said:**
> Can you recommend me a Youtube channel subscribing to which I will get to know the latest security news ?

Security stuff requires constant reading. Daily.  For current things, I have some RSS feeds and I'm a member of 3 local defcon groups. They use email lists to communication and invite-only discord.  I find discord to centralized, so I'm email and IRC only. They each have monthly meetings.

I use youtube for deeper security stuff, not news summaries.  

Going to at least 1 security conference will open your eyes. Some of the conferences are very expensive, but some are either free or less than $50 for 3+ days.  Before you go to a security conference, a few tips:
[LIST]
[*]backup any computing devices. Expect to be hacked while there and expect multiple viruses to be placed onto your system.
[*]Leave your smart phone at home. Bring a $10 cell phone if you must have one at all. Sometimes people will run a stingray cell simulator and test out pushing firmware updates to any devices that connect. You've been warned.
[*]Disable all wifi and bluetooth on any computers.  Your laptop needs to be truly stand-alone. No networking at all.
[*]Don't leave any device unattended. Even walking 4m to buy a coffee is enough time for someone to insert a USB drive that automatically sets up a remote access back door.
[*]DO learn to pick locks.  Lock picking is almost always part of this. Ask for help. Have fun.
[*]DO take part in the CTF competition. CTF - Capture the Flag. There are variations on this like KotH - King of the Hill where you hack a web server, then have to prevent other teams from kicking you out. There are practice servers/competitions setup around the world. You can also learn by running a few virtual machines in your home security lab. Probably don't want to allow those easily cracked OSes onto your normal LAN. Air-gapped. Please.
[/LIST]

Have fun.  Even if you just spend a Saturday at one of the free conferences, these are fun people. Know the rules and you'll be fine. Most of all, you'll get into the group and learn a bit. You'll never look at your computer, router, smart phone, tablet, the same again.  You might not look at mass transit, street cameras, and "smart cities" the same either.

Oh ... and for privacy related topics, point your RSS reader at: [http://www.pogowasright.org/?feed=rss2](http://www.pogowasright.org/?feed=rss2)
 DuckHook's links are good. I'd add [https://www.schneier.com/feed/atom](https://www.schneier.com/feed/atom) too.  Bruce has an in-explainable love of squid, which gets shown off on Fridays. Current story today: 
> Four Microsoft Exchange Zero-Days Exploited by China
Microsoft has issued an emergency Microsoft Exchange patch to fix four zero-day vulnerabilities currently being exploited by China.
This is not the day when this news broke. Bruce usually waits until the facts are in so we don't have to follow the hype.

---

### Post by linuxyogi on 2021-03-04
@DuckHook/TheFu
I have bookmarked all the links. The first thing that I do every morning is I check my email. From now I will read all those pages too. Thanks.

---

### Post by DuckHook on 2021-03-04
> **TheFu said:**
> I've had a different experience.  Most sites will display the data I want without any scripting enabled. For example, ubuntuforums includes googletagmanager.com, but works fine without allowing any javascript or connection from that site.
Yes, you're right. I was indulging in a fair bit of exaggeration. I also routinely visit most sites with NoScript in full kill mode&#8212;especially new sites that I'm not sure about. After all, that's the whole point in using it. If a site won't load at all without scripting (there are a lot of those), then I make a determination whether it is worth the visit. More often than not, I decide it's not important enough for me to risk turning on scripting and I forego the visit.

NoScript has the additional advantage of bypassing some paywalls. Many primitive paywalls are just JS overlays. By turning off scripting, the overlay stays dormant.

Unfortunately, practically every banking site and government site I've visited in the last two years will not work without scripting. My accountant's site requires it. Webmail sites require it. Even recently retrieving a dental chart required it. It's really sad these days that web designers will code JS into the guts of their webpages when it is totally unnecessary.
> **TheFu said:**
> &#8230;for privacy related topics, point your RSS reader at: [http://www.pogowasright.org/?feed=rss2](http://www.pogowasright.org/?feed=rss2)
&#8230;I'd add [https://www.schneier.com/feed/atom](https://www.schneier.com/feed/atom) too&#8230;
Thanks for these. I've added them to my feed.
> **linuxyogi said:**
> @DuckHook/TheFu
I have bookmarked all the links. The first thing that I do every morning is I check my email. From now I will read all those pages too. Thanks.
Well, that's a lot of reading. You'll be a security guru in no time. ;) BTW, as is clear from the foregoing, the whole security/privacy/profiling thing occupies a vast continuum with typical users on one end, guys like TheFu on the other end, and someone like me in the middle. You will have a decision to make: where do you want to fit on that continuum? In a way, it's been the whole thrust of this thread.

Good Luck!

---

### Post by TheFu on 2021-03-05
> **linuxyogi said:**
> @DuckHook/TheFu
I have bookmarked all the links. The first thing that I do every morning is I check my email. From now I will read all those pages too. Thanks.

I don't read every article.  By using a feed reader, I see the title and summary for each article and can decide whether it matters or not.  I couldn't imagine trying to do that with a browser.  Get a good RSS/Atom feed reader, so you can skim through everything fast.   [https://linuxrig.com/2021/02/09/why-i-still-use-rss/](https://linuxrig.com/2021/02/09/why-i-still-use-rss/)  Pick just a few to read and 1 to digest weekly.

If you want youtube stuff, here's a Linux Conference with years of talks by experts. [https://www.youtube.com/c/southeastlinuxfest/videos](https://www.youtube.com/c/southeastlinuxfest/videos)
Many conferences have free videos.  

Adrian is security focused. [https://www.youtube.com/user/irongeek/videos](https://www.youtube.com/user/irongeek/videos)  and goes by IronGeek.  I met him over a decade ago at a little local conference. His multi-day training on wireshark is all you need related to that subject. He isn't Linux-centric, so often he'll struggle to use Windows. ;)

---

### Post by linuxyogi on 2021-03-05
@TheFu
Yes I too realized reading every article is not possible. I am deciding which article to read by reading the title.
I have installed akregator. I will definitely subscribe to both the Youtube channels you suggested.
Just in case if I find that the irongeek is more Windows related I will unsubscribe. After all its just a 1 click process.

---

