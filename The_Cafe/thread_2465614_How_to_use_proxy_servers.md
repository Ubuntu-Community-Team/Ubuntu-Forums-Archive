---
title: "How to use proxy servers?"
date: 2021-08-06
forum: The Cafe
---

### Post by jolibe on 2021-08-06
I want to use proxy servers for security when using PayPal payment system. But how secure are these proxies?

---

### Post by TheFu on 2021-08-06
> **jolibe said:**
> I want to use proxy servers for security when using PayPal payment system. But how secure are these proxies?

It depends.  

They will see where all your traffic is headed and if the TLS level is below v1.3, it is possible they can crack the HTTPS and see inside those packets too.

As with any cloudy service, how secure they are depends on many things, some under our control and many not under our control. Plus, companies lie about their security all the time.  For example, this week we found that Zoom's claim of end-to-end encryption were false.  Remember a year ago when they were making huge claims?  A govt is fining them for lying.

All we can do is try to stack the honest for any service into our desired goals, but even a slight misconfiguration, accidental as it might be, could effectively make these useless.

The same applies to VPNs.

A few things that should be common sense.
* If you aren't paying for a service, then YOU and YOUR data are the product being sold.  Using paid services makes it more likely they aren't selling you and/or your data.
* Look at the ownership for the company.  Some of these can be simple to track down and others will be layers upon layers upon layers. If you can't figure out who the real company is, where it is located in reality, that is suspicious to me.  What are they hiding?
* Look at the people running the company.  Are these people trust worthy?  Can you find an address for the company and actually knock on the door?  Can you find where the CEO, CIO, and CSCO live?  Are their names hidden behind corporate layers?  Where do the people running the systems actually live?
* Consider which countries these services are based from.  Do you trust their legal system?  Can the top political person demand access and get it?  Can this person jail people indefinitely without due process and a trial?  When normal people/companies disagree with the govt, do they always lose or do they win in the courts?

All these things matter.  Seems like common sense.

BTW, I suspect Paypal will refuse to work with any VPN or Web proxy. At least I hope they do.

[I]Background:
[/I]I use VPNs for multiple hours every day for my consulting work. Wireguard, openvpn, and IPSec based VPNs.  I run a VPN and a SOCKS5 proxy for personal access back home when I'm traveling. I've designed and deployed corporate VPNs for 5 people and for 25K people using 2FA since 2005. Fortunately, I didn't have the manage the 2FA logistics. What a pain that is.

How do you setup a proxy server depends on the client to be used. Some will use an environment variable, others will have a command-line option and others will have the settings buries in their configuration setup pages.  I know that Chromium-browser can use a SOCKS5 proxy based on a command line parameter. I also know that Firefox doesn't - it requires settings in the profile. Firefox recommends having 2 different profiles - one with a proxy and the other without.  For me, that is too much of a pain because they bury the proxy settings 5 layers deep into the settings->networking->....   so I don't use firefox when I'm using a SOCKS proxy.

An exact example: 
```
$ chromium-browser --proxy-server="socks5://localhost:$PORT "
```
This is what I use because my SOCKS proxy is actually an ssh port forward, so ssh port forwarding is setup on $PORT which pops out on a system elsewhere. All my web traffic appears to come from that remote system.

On ubuntu in the GUI,  Settings > Network > Network Proxy > Manual  
Or you can put a script in specific locations for each program you wish to use a proxy which sets some environment variables:
```
export http_proxy="http://10.10.1.10:8080/"
export https_proxy="http://10.10.1.10:8080/"
export ftp_proxy="http://10.10.1.10:8080/"
export no_proxy="127.0.0.1,localhost"
```
and *source* it.

Some programs want those variables to be UPPERCASE, so for system-wide setup, do both upper and lowercase variables.
Obviously, the proxy value would need to be where a proxy is actually running and accepting your requests.

---

### Post by ianwhite7 on 2021-08-12
why not use [Tor ]("https://www.torproject.org/")instead?

---

### Post by TheFu on 2021-08-12
> **ianwhite7 said:**
> why not use [Tor ]("https://www.torproject.org/")instead?

TOR is commonly blocked by reputable financial institutions.  Have you attempted to TOR and use paypal?

---

### Post by TheFu on 2021-08-13
> **masdertior said:**
> I have been using proxies for a very long time. It is really safe and does not present any difficulties if you use high quality proxies.

Even if you ran the proxy, it isn't as safe as believed.  A proxy run by someone else will necessarily be even less secure. 

They see all your inbound and outbound traffic. When you mail letters or checks, do you seal the envelop or not?  Using a proxy is like not sealing the envelop at all ... or actually ... more like using a postcard.  Everyone along the patch can take a look at the message, see the check stapled to the postcard.

Further, if they've been capturing all your traffic and sifting through it for data, how would you know?  How could you know who they are sharing that data with?

Are you running a proxy and trying to get people to use it so you can capture their data?  Proxying cat video streams or 100% games with no in-game purchasign is one thing.  Proxying financial data is COMPLETELY DIFFERENT.

---

### Post by masdertior on 2021-08-16
As far as I know, all traffic is encrypted.

---

### Post by TheFu on 2021-08-16
> **masdertior said:**
> As far as I know, all traffic is encrypted.

That isn't what a proxy server does.  If you want an encrypted proxy, use TOR.  End-to-End TLS encryption doesn't work with a proxy, unless you've installed a MiTM Cert from the provider. Then all your traffic can be seen by the proxy provider.

Use a VPN with IPSec and strong encryption if you care about security.
TLS v1.2 and earlier, including all SSL versions have been cracked.  Very verify that TLS v1.3 is used for HTTPS traffic and LTS-based VPNs.

There are many subtle things in security. Assuming stuff usually means not being secure.  Heck, even when we do everything correct, a misconfigured server on the other side, or a server where the Govt mandates sharing/registering the certs, can completely break our expectations of privacy.  Of course, none of those providers will announce it or put that in their marketing.  When it comes to claims about security, what they DO NOT SAY, is just as important as what they do say in their advertising junk.  Also, where they are located in the world and where the parent company is located in the world matters greatly as well.

---

### Post by not-published on 2021-08-26
Proxy is a middle man, it would make PayPal less secure not more.  It is a server which at it's own discretion feeds "old or fake" web pages to those bound to listen:  by definition, and by mass use and the past and also practice still today.

Also:  the telephone company proxies material appropriately already.  Infact, if you order Cloudfare hosting they specialize in telephone company level proxyied pages (served locally only when they do not contain dynamic content).

I see zero points in the question and see possibly enabling a federal fraud in the use of the answer.

---

### Post by kevdog on 2021-09-08
I wasn't aware TLS 1.2 had been cracked if configured correctly.

---

### Post by TheFu on 2021-09-09
> **kevdog said:**
> I wasn't aware TLS 1.2 had been cracked if configured correctly.

A well-known govt for citizen internet monitoring and blocking filters all TLS v1.3 VPN connections, but allows v1.2 and earlier. They've been doing this over a year.  It was sufficient that my company decided to only allow tls v1.3+ connections and the hacking attempts dropped 90% with that 1 change. 

We already block as much of the country as possible - seems odd to have so many /8 blocks, but they are targeted towards places that we will never do business and from where hacking seems to be a major pastime for everyone with a computer.  There are just a few countries like that.  Keeping up with their subnets every week isn't too much fun.

---

