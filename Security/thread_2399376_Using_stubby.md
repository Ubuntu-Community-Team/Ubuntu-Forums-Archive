---
title: "Using stubby"
date: 2018-08-24
forum: Security
---

### Post by ubantunovice2 on 2018-08-24
I searched this security forum and didn't find a thread about stubby (dns over TLS) so I hope it is OK to start a new thread.

My question is a very basic one. In a home where the internet is provided by a cable isp (FiOS Verizon) and the home wlan I set up is provided by the isp 's router, does using something like stubby (that acts as a dns resolver)
[https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls](https://www.linuxbabe.com/ubuntu/ubuntu-stubby-dns-over-tls)
provide any additional privacy since, because of the wlan, the result will (I think) still go through the isp's router? So the isp will still get the ip my browser is going to? 

Sorry for the convoluted sentence. I wanted to get in all the relevant details.

---

### Post by TheFu on 2018-08-24
Hiding DNS requests from an ISP may be helpful for privacy.  But they run the network, so unless you use a VPN that encrypts all traffic until it leaves their network, I have doubts for the usefulness. The ISP will see all traffic anyways.

And if you do use a VPN, be aware that large ISPs definitely have the ability to use enterprise solutions to perform "deep packet inspection" to figure out the type of traffic being used on their network. This has been available since 2006 and earlier.  DPI has gotten better since then.

IMHO.

---

### Post by ubantunovice2 on 2018-08-24
Thank you. That's what my common sense told me but I don't know enough to be sure. I don't have great secrets to hide but I'm clinging on to what shreds of privacy 'may' remain.

So you are saying a vpn is the best option but doesn't that mean trusting some unknown operator instead of your own isp? Exchanging one holder of your privacy with another?

Just read https://en.m.wikipedia.org/wiki/Deep_packet_inspection

Makes you just give up any illusion of privacy.

---

### Post by TheFu on 2018-08-24
> **ubantunovice2 said:**
> Thank you. That's what my common sense told me but I don't know enough to be sure. I don't have great secrets to hide but I'm clinging on to what shreds of privacy 'may' remain.

So you are saying a vpn is the best option but doesn't that mean trusting some unknown operator instead of your own isp? Exchanging one holder of your privacy with another?

ISPs are already spying on you, especially those who have been caught doing it.

Many VPN providers spy,  but many have reputations for standing up to legal warrants. The 2nd group might be a good choice, just be certain to use their strongest solutions and understand their fine-print so you don't get too comfortable with poor OPSec.

And you can run your own VPS with a VPN. But then the VPS provider will have network access to your traffic as it leaves those facilities.  I would assume the largest players have provided equipment installation for the national govt in that region, but I wouldn't worry about physical security beyond that.  Really small VPS providers do exist as well. Look for those with physical facilities and redundant connections.  Usually they will allow placement of YOUR hardware into their facilities, which VPS providers like Amazon simply cannot allow.  But physical security at tiny providers is likely poor based on my experience and often, they don't know how to manage their own internet connections.

Another option is to use TOR with dedicated hardware and 100% new accounts that have never been used outside TOR when you feel the need for privacy.

I've only played with TOR a few times.  Be very careful with your OPSec if you want privacy over TOR. Don't expect video to work.

I use VPNs - both ones that I run/manage and from commercial providers - for private use and for work.  They fill different needs. The commercial VPN provider claims to delete all logs within 3 minutes of a connection close, so I do not leave the VPN up longer than necessary for the task.  It definitely isn't up 24/7. They have turned the FBI away. Also, the default setup cipher isn't the strongest, so I force AES-256.  That means using some manual configuration, not checkboxes. I do not use a GUI to manage the VPN.

I don't trust wifi security at all, so all wifi devices have to use a VPN to access my home network.  This is also how corporations work.  My wifi AP sits outside the network and it is treated like any public internet connection. That means guests are free to connect, since they won't have my VPN credentials - it is also handy for those untrustworthy IoT devices - all IoT devices are untrustworthy, BTW - so they can see each other on a LAN, but nothing else interesting.

And I trust bluetooth not at all.

Being on the internet has risks. Fortunately, easier prey are plentiful unless you are specially targeted.

---

