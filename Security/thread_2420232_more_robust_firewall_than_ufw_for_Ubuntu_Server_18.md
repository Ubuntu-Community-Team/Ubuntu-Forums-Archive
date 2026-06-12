---
title: "more robust firewall than ufw for Ubuntu Server 18.0.4"
date: 2019-06-01
forum: Security
---

### Post by rtgmike on 2019-06-01
Hi all, I'm new here.

Anyway, I normally have a public facing firewall for my servers, but I am doing tests for a replacement for Kerio Connect and the server I am on, despite having dual AMD Epycs and 512GB of ram is nearly full of resources and there was also a reddit post on nat is crap and well, I wanted to play. So I literally set an ubuntu vm with an unfettered public IP. I know, I know, I know.

Does there exist a bit more robust firewall for the local linux server that will run a mail server. No NAT or anything. I just need to lock port 22 down to specific IP Address but while my office is static my home is dynamic and I work from home a lot and without a jump server and yadda yadda yadda. Yes yes I know don't use password set up the keys.

Can I without a iptables script to check my dynamic and recreate the iptables rule just apt-get a firewall that can handle it. I do NOT have a GUI on system so it will need to be console or web-based and moved to another port than 443. Reason being, I may blow away this server 5-6 times in the next week testing different mail servers. I'm very picky. I tried iredmail, but when it takes me 50 minutes to get my wildcard cert installed and I already agreed to pay $1000/year but then the guy was like "Oh I need $99 for that". Forget it, I'll go elsewhere. I'm trying Xeams next.

And before you get into it, I need Activesync and Outlook not on IMAP and I need not-lazy-crap and not-gimme-mo-mo-money support and I need Active/Active or Active/Passive server clustering between two datacenters in two states and the ability to handle like 1000 users and all to offer at cheaper than Office365.  Oh yeah, and I need NO-GFI. Because when they bought kerio, holy cow do they know how to wreck a company. I thought Symantec was great-company-destroyer-in-chief. GFI may take that crown.

But, I just need a firewall people and I don't want to deal with pfSense for like 1 week. I spend enough time in pfsense - I need a break. And if you say TNSR or VyOS I will in my overactive imagination smack you with a rotting trout. Yes thats a script kiddie mIRC reference for all of those under the age of 40.

---

### Post by The Cog on 2019-06-01
Hi, and welcome.

It's not exactly spelled out, but I gather you want your mail server (at work I guess) to have a firewall configuration that permits only your home IP to connect to port 22. But your home address is dynamic and liable to change.
And you don't want an iptables script.

The simplest solution is to use ssh keys, disable ssh passwords, and allow a range of IP addresses to connect (maybe your ISP's address range).

The next simplest is to install a vpn server at work, and run ssh over the VPN. Then you don't expose 22 to the internet at all. I would recommend wireguard for this - it's delightfully easy to set up.

The next I can think of would be to sign up to a DNS service and install a client at home that changes the address associated with your home domain name, and create a script to query the address periodically and update the firewall if the address changes - it can call ufw if you don't want to configure iptables directly.

I can't think why you are suggesting that ufw is not "robust".

---

### Post by rtgmike on 2019-06-01
So I have namecheap for my home domain and I do have a dynamic dns. I already have ipsec vpn tunnels from my home network to my offices and datacenters. But those are internal IPs.

I guess locking it down to an address range may work. Again If ufw had direct dns capabilities it would be best. For instance in production my mailserver doesn’t talk to anything on port 25 except with its antispam servers but since I need to futz with IPs and everything I have also been moving that to dns.

By more robust I basically mean at least have dns. I don’t want to have to write 50 cron jobs in prod either if I go that route. When I go prod I have less taxed servers I can just run pfsense and have pfblockerng.

Then I could do the ssh cert and publish it.

---

### Post by squeaky2 on 2019-06-01
Actually, if you wanted a good firewall (and a decent VPN to boot), I would definitely give Windscribe a shot. 

Windscribe is a free VPN service (they also offer a subscription) that comes with a free firewall. 100% compatible with 18.04 (Pro version gives you keys to set it up over OpenVPN as opposed to terminal commands), commands are simple, straight-forward, and terminal-based. You get 2 Gb's of data to torrent per month. That's not much, but if you're someone who likes their privacy, it's pretty good. 

There are various workarounds that you can use, as far as web browser extensions go. NoScript and Privacy Badger are my two go-to's. NoScript blocks all javascript content on a page, and you can select which scripts to run or block. It also blocks clickjacking attacks, cross-site scripting attacks, and other various forms of nastiness that can happen on the internet. Also, very very easy to break a website without any scripts on it. It's very easy to enable, whitelist, or permanently disable scripts, though.

Edit: I just re-read your post and realized you're running a way bigger setup than I thought. Unfortunately, I don't have any other recommendations than what I've already posted... best of luck to you, though!

---

### Post by The Cog on 2019-06-02
I you are going to keep changing the firewall rules to follow your home IP address, I don't see any choice other than a cron job that queries the DNS name periodically.

I don't think you should need 50 cron jobs, unless all your servers are directly accessible from the internet. Just run the cron job on the firewall/load balancer that you connect through/to. SSH to that and then to the server you want to manage.

If you really need to reconfigure 50 servers, then it's probably worth looking at something like ansible that can reach out and configure all of them from one command. Not just for firewall configuration but for all configuration. It's a bit of a learning curve but will definitely worth it. But then, ansible needs ssh access to the servers, and passwordless is best. Once you have configured passwordless ssh using keys instead, you don't need to worry about password guessers, and there is less need to lock down ssh to approved IPs.

I still think a wireguard VPN server at work is a good idea though

---

### Post by TheFu on 2019-06-02
You are a very difficult customer.  Often, there is what we desire and there is what is possible.  

First, the Linux firewall is built-into the kernel.  ufw, iptables, firewalld are just interfaces to control that.  ufw is designed to be simple, but has limited capabilities so it can be simple. People running internet servers probably need more control than ufw provides.  If you need a powerful editor, you wouldn't choose nano/notepad, right?

If all you need is port 25/tcp in/out and don't intend to block any outbound, then ufw is fine.  Businesses should block outbound too, IMHO. Iptables allows for extremely complex configurations, so it is a complex tool to use if you need to harness that power.  I don't know how well firewalld is supported on Ubuntu. Sorry.

I've been running corporate email servers over 20 yrs, but you've lost me on much of the terms.  1000 users per server isn't all that man. Can't imaging needing 512G of RAM for that, unless activesync requires that.  We don't touch active sync and don't care what email client program is used. If someone wants to use outlook, then they can setup an IMAPS connection. We use standard protocols, not proprietary.    $1000/yr is nothing. I wouldn't touch a system for that low price, especially one that appears to be very critical for 2,000 people.

I wouldn't have ssh listening on the default port. Why allow the entire world to hack away, when listening on some other port, like 63822/tcp, will make your logs tiny and almost 100% stop the ssh scanning scripts?  Setup the ~/.ssh/config file with the new port and never think about it again. All ssh client tools support this.  As for security, using ssh-keys for authentication, never passwords, for internet-based ssh connections is mandatory.  Probably want to setup fail2ban or denyhosts to dynamically block brute force attacks too.  Using the sshd_config settings, you can allow non-key access to specific subnets using the Match ..... configuration.

I'm confused. What does pfsense or VyOS have to do with a software firewall on Linux?  A hardware firewall is still mandatory, IMHO, but that is a separate device.

---

### Post by rtgmike on 2019-06-03
No no no no. I'm not running running all mail servers on that. :P That's my dev server. I run a cloud host & MSP. I have 100+ other VMs on that server doing all sorts of stuff. Right now my dev environment is a single dual-epyc server with 128 total vCPUs and 512GB of ram + a ~180TB NAS running FreeNAS over 2x10GbE fiber lines using NFS to VMWare and an NVME as a slog. Currently I have 3 locations: I lease a cage in North Carolina with 6 racks, I own the entire DC in Pennsylvania and I have 4 racks in NJ, another 4 in NYC but they are a mirror for instant failover (I count them as one because it's one "package" deal from the datacenter). I'm decommissioning NC, and during that process I have become painfully aware of just how limited Kerio Connect is, how bad GFI has made it and how little of the major features us cloudhosts were promised and wined & dined on from Kerio back in the day ever made it to the light of day. Then of course they come in and start jacking up the prices. That and the internal antispam is so bad I have to pay even more for spamtitan.

Anyway, I am done with them. I started looking at other mail servers and this is a development server and out of sheer lazyness and also that this is not my only job and I already have a jenga stack of crap on my plate as it is I wanted a quick and dirty solution. I may nuke this server like 50 times looking at different offerings.

Now to the meat and potatoes. I was on Reddit the other day, because I was sitting and waiting and I think it's inappropriate or at least I feel embarrassed to watch a movie in a waiting room unless you are watching sports. And on Reddit very opinionated people were talking about the evils of NAT and yadda yadda yadda. Now I don't think that way. IP4 addresses aren't cheap, I know I pay for a crap ton and it costs like 10 crap tons. Literally what I pay in IP addresses alone, I could just about lease a Ferrari California.

But, I was intrigued and this is where I hit a wall. I'm not saying cut out UFW, I was merely looking for an expansion pack or a nice interface. I'm used to using real firewalls and I was feeling a bit powerless. Luckily I called my ISP and they only use a 25-bit network in my area (I live in a rural area). So I locked it down to that and my main office's two IP's that we ever use outbound on. Then generated an SSH key for it dump it on my nextcloud server so I ca grab it from the linux vm.

As a test goes, I don't think I'm ever going into prod without NAT and a proper firewall, at very least pfSense.

---

### Post by rtgmike on 2019-06-03
Hi Cog,
I actually made my "own" privacy vpn with 2FA. I had made a grab for IP4 addresses for my NY/NJ DC and got literally a stray in the pack. Some random IP that says its from Idaho while all the rest are in neat blocks. So I stuck pfsense on it, added freeradius and openvpn and poof I have VPN. Added in a few PiHole servers and using roothints with unbound. I charge my clients $0.50/500GB a month, but my cost is much lower. Actually I don't even pay if I use under 2TB of egress if I am not mistaken. I have a nuts home network, with pfSense firewall, Ubiquiti switches and APs, my wiring guy professionally wired it with cat5e and cat6. Proper patch panel and rack.

I have ipsec tunnels to my office and datacenters, locked down to a vlan on my network, plus I also have routes to my other vlans in my office from that.

For safety, I have pfBlockerNG locked so down, I even block windows telemetry and then my DNS goes over TLS. Not that my ISP spies on me, but I used to be on Comcast and they are worse that 90's Russia or 2000's US combined times 100. So the VPN is only for when I am out. My wife volunteers at church on sundays and I sit and work but the IT guy at the church blocks all ports except TCP 80, 443, 465, 587 and a few others and then has a content block on everything - even openVPN's website. So I set up a VPN at my office on 443/tcp to get around that. But I am expanding that to run in my NY DC.

---

