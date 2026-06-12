---
title: "providing tunneled proxy for overseas users"
date: 2010-07-27
forum: Security
---

### Post by perkhouse on 2010-07-27
Hello folks! I want to provide a service similar to one of these: [http://freeproxies.org/list.htm]("http://freeproxies.org/list.htm")

However, with a few differences... namely, I want mine to be accessed via some sort of authentication: password/keys. (It will still be free, but only to a select few. It will be unknown to most.)

Please see the attached proxy.png for a visual representation of what I'm about to explain.

So, let's say USER is trying to view HTTP(S)-SITE in KUWAIT, but because of governmental policies, SITE is blocked. So, USER logs into my UBUNTU box and is tunneled to SITE.

Now the problems:
[LIST=1]
[*]modem's IP addy is dynamic - I'll just have UBUNTU send an empty email once per day and the header will contain the IP address.
[*]I don't want any of the other PCs on the LAN to use the PROXY (though UBUNTU is a SAMBA file server on the LAN).
[*]Not sure if I need to set ROUTER's DMZ to UBUNTU
[/LIST]

So, what am I missing? Can I set up SQUID to do this? Not sure what I need, but I think I want the simplest solution, i.e. the one with the fewest pieces.

TIA,
Brian

---

### Post by tripolitan on 2010-07-27
Yes, set up squid with authentication and have it accessible to the world but change the default port to an obscure one (to avoid sniffers).

As for the dynamic address, open a free account with dyndns.com and grab a free domain address from their list, example KUWAIT.homelinux.com and have your machine update your address every 4-6 hours.

Users will have to setup their browsers to use the proxy w:KUWAIT.homelinux.com every time they wish to view the blocked sites.

I'm sure there are other ways to set up a web-based proxy where your users would just go to the site and enter the blocked address.

Read the squid manual and how to.

Remember that if your machine is also a file server, it should not be used for anything else (should not connect to the internet) and should be isolated from the outside world because if it gets compromised through squid or ssh or any other vulnerability, your files will also be exposed.

---

### Post by tripolitan on 2010-07-27
[http://www.labnol.org/internet/setup-proxy-server/12890/](http://www.labnol.org/internet/setup-proxy-server/12890/)

[http://kakku.wordpress.com/2007/11/12/proxy-hacks-iv-on-demand-installing-a-web-based-proxy-phproxy-on-your-home-system-install-something-like-kproxycom-useful-only-for-blocked-websites/](http://kakku.wordpress.com/2007/11/12/proxy-hacks-iv-on-demand-installing-a-web-based-proxy-phproxy-on-your-home-system-install-something-like-kproxycom-useful-only-for-blocked-websites/)

---

### Post by HermanAB on 2010-07-27
Howdy,

If you want a secure encrypted proxy, then you need to run a SSH Daemon.  Then in the foreign country, use SSH or PuTTY to open a Socks connection (the -D switch of ssh) on port 443, finally set Firefox or Skype or whatever to use the proxy on localhost.

Note that for Skype, you also need to configure Skype to use the proxy and prevent Skype from using anything else (there is a stupid bug in Skype), with an iptables rule:
```
$ cat /usr/local/bin/skypesocks
#! /bin/bash
# Run Skype over a Socks proxy.
# Etisalat drops about every tenth packet, which makes Skype sound gritty and buggy.
# Skype can use a Socks proxy, but it has a bug and tends to ignore the proxy setting!
# The solution is to drop all other traffic to/from Skype and force it to use the proxy.
# Configure Skype to use a Socks 5 proxy on localhost:1080
# Create a group called socksgrp and add yourself to it, then use this group in iptables
# to drop all other Skype packets on the floor.
# Skype uses about 10 kbs for voice, more for video, but it is remarkably efficient
# if all the packets are allowed to get to the other side.

echo Set up a Socks proxy Virtual Private Network to blahblah.aeronetworks.com on localhost:1080
/usr/bin/gksu "/usr/bin/killall ssh"
/usr/bin/ssh -fND 1080 -p 443 root@72.167.38.123

echo Only allow Skype connections to localhost by filtering on the socksgrp
/usr/bin/gksu "/sbin/iptables -F"
/usr/bin/gksu "/sbin/iptables -A OUTPUT -d 127.0.0.1 -m owner --gid-owner socksgrp -j ACCEPT"
/usr/bin/gksu "/sbin/iptables -A OUTPUT ! -d 127.0.0.1 -m owner --gid-owner socksgrp -j REJECT"

echo Spawn Skype as group socksgrp, to allow the above rules to filter it
sg socksgrp /home/herman/skype/skype_static-2.1.0.81/skype

echo Et Voila!
```

Hope that helps.

---

### Post by perkhouse on 2010-07-27
Thanks everybody for such quick responses!

Here's a little more info:

@tripolitan:
The Ubuntu (Samba) file server doesn't contain any sensitive information. Of course, I'll take every precaution to make sure it's not vulnerable though.

I have read many how-to pages on setting up Squid/Ubuntu as a proxy server, but they all seem to assume the other LAN clients will be using an Ubuntu server as a firewall and none explain how to .

@HermanAB:
I'm not sure what I want. lol I mean, I know I want the remote 'clients' to be able to access http and https sites, but not be able to access my LAN or remote desktop or router.

I know that in Kuwait the Skype program works fine, but all the Skype web pages are blocked (which can be a problem for those who need to recharge their accounts).

That said, I don't think I want the users using Skype or BitTorrent clients - just web pages.

Thanks again,
Brian

---

### Post by HermanAB on 2010-07-28
Howdy,

In Kuwait, UAE etc, the local telco chucks away about every tenth packet if they suspect that it is a VoIP call.  This causes Skype to sound gritty - it works, but not as good as a land line or cell phone and works for Skype to Skype calls only.  Skype Out is completely broken.  If you want to use Skype Out, then you have to run a proxy and Skype has a stupid bug which makes proxying it a little tricky.

---

### Post by perkhouse on 2010-07-28
Ok, I got Squid3 working for my LAN, but not for internet clients - exactly the opposite of what I ultimately want to achieve.

Right now, I just want to get the internet clients working without authentication. I'll add authentication later.

On a related note... after I set up the dyndns.com account and put the url in the browser, I discovered that my router's login page was exposed to the world. YIKES! That was simple to fix by forwarding port 80 to my Ubuntu file server (which, since it isn't a web server, just times out).

Herman, Does the script you provided run on the server or the client? I'm asking because the clients are mostly Windoze.

Also, how recently is your info about Skype in Kuwait? I was talking with someone in Q8 via Skype as recently as last month and the sound quality (for both of us) was better than using a landline or mobile. Perhaps it depends on the ISP of the Q8 user.?.

---

### Post by perkhouse on 2010-07-28
tripolitan, i've tried several things to make squid accessible to the world, but to no avail.

I even tried changing my squid.conf 
```
# defaults
http_access allow manager localhost
http_access deny manager
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
# custom based on suggestion in default conf
http_access deny to_localhost
# custom
http_access allow all
# default
http_access allow localhost
# commented default
#http_access deny all

```

**EDIT: I know that *http_access allow all* line is really stupid, but it's just for testing. I plan to add an acl TRUSTED for specific src IPs once I make some progress.

Router is forwarding ports 80,443,3128 (but not sure I need 443 - think 80 is only needed to keep world from hacking the router). Not forwarding any UDP ports.

Thanks guys!

---

### Post by perkhouse on 2010-07-28
I'm at a loss... I just ran the "Custom Port Test" at [http://www.whatsmyip.org/ports/](http://www.whatsmyip.org/ports/) using 3128 and it says the port is open, so I think I can safely assume the port is being forwarded from the router to Squid, but the Squid /var/log/squid3/access.log is empty.

Any ideas?

---

### Post by HermanAB on 2010-07-29
Howdy,

You need the SSH server on the server listening on the HTTPS port 443 and my script on the client.  It works in UAE and Oman.  I only have hearsay on Kuwait.

It can be done using PuTTY on Windows, but you need a firewall to force Skype to use only the proxy and not try to connect on its own.  You only need this for Skype Out.  

Skype to Skype is OK-ish, my wife uses it straight-up without the proxy to call her friends, but to call her mother with Skype Out, she uses my laptop with the proxy.

---

### Post by perkhouse on 2010-08-05
Well, I gave up on Squid3. Perhaps, my D-Link router isn't forwarding the port, but more likely I couldn't figure out how to configure it properly for my purpose.

So... I've moved on. I now have SSH listening on port 443 and I'm reloading PuTTY onto a Windoze laptop. (I have used PuTTY, but it's been years.)

Thanks!

---

### Post by perkhouse on 2010-08-05
Arrgh! I'm getting so frustrated.

[LIST]
[*]I set the listening port back to 22 for testing and restarted SSHD.
[*]I can log into the SSH terminal using localhost.
[*]I forwarded port 22 in my D-Link wireless router to the Ubuntu server. (The Ubuntu server is using a cat5 link tho.)
[*]I can "ping XXX.XXX.XXX.XXX" using my WAN's IP.
[*]All external port probes say that port 22 is open.
[*]But I can't "ssh XXX.XXX.XXX.XXX".
[/LIST]
Any ideas???

---

### Post by perkhouse on 2010-08-05
Here's the port probe I used last:
[https://www.grc.com/x/portprobe=22](https://www.grc.com/x/portprobe=22)

---

### Post by perkhouse on 2010-08-05
Aha! I connected the Ubuntu box directly to the modem and now any port I configure for SSH works flawlessly, SOOOooo... it has to be this stupid D-Link router that is creating the headache. I have tried every option I can think of for the least restrictive operation (even DMZ), but all ports are still filtered.

Does anyone having experience with D-link routers have a suggestion?

Alternatively, can anyone suggest a low-cost 802.11 **[COLOR="DarkRed"]N[/COLOR]** router which definitely will NOT exhibit this behavior?

Thanks!

---

### Post by OpSecShellshock on 2010-08-05
Have you searched the web for the model of your router and the string "port forwarding" by chance? In most cases you'll find a guide somewhere. I'm assuming you have access to the administrative interface of the router.

---

### Post by perkhouse on 2010-08-05
Yes, I did check with several online guides.

I have tried the router's port forwarding, virtual server, and DMZ options. All ending in the same results. I have reduced the restrictions in packet filtering and turned off all options designed to thwart all types of attacks. None of these made a difference.

All port probing sites say the port is open, but nmap says it's filtered. SSH to localhost succeeds, but SSH to WAN IP fails.

Btw, I have 21+ yrs exp as a professional software developer (nearly 33 yrs since I started programming for fun) and 15+ yrs as a network admin. But that's irrelevant right now. 

Anyway...

I have ordered a newer (Netgear WNR2000) router and it should be here in a week. It will be interesting to see how/if it behaves differently than the D-Link DIR-615.

---

### Post by cariboo on 2010-08-06
A good place to check if you have port forwarding setup properly, or if your isp is blocking ports is [canyouseeme]("http://www.canyouseeme.org/").

---

### Post by HermanAB on 2010-08-06
Why are you using a dinky little router?

Plug the Linux machine straight into the DSL/Cable modem.

---

### Post by perkhouse on 2010-08-06
> **cariboo907 said:**
> A good place to check if you have port forwarding setup properly, or if your isp is blocking ports is [canyouseeme]("http://www.canyouseeme.org/").

Thanks, but as already mentioned... I already tried it:
[QUOTE="CanYouSeeMe.org"][COLOR="SeaGreen"]Success[/COLOR]: I can see your service on **XXX.XXX.XXX.XXX** on port (**YYYY**)
Your ISP is not blocking port YYYY[/QUOTE]

But also as I already mentioned...
[QUOTE=nmap]PORT     STATE    SERVICE VERSION
YYYY/tcp filtered unknown
[/QUOTE]

Which results in...
[QUOTE=ssh]ssh: connect to host XXX.XXX.XXX.XXX port YYYY: Connection timed out[/QUOTE]

---

### Post by perkhouse on 2010-08-06
> **HermanAB said:**
> Why are you using a dinky little router?

It's a wireless N router.

---

### Post by wacky_sung on 2010-08-06
> **perkhouse said:**
> It's a wireless N router.

Wireless router running as server in wifi is slow.If cable, are you using gigabit wireless N router on a Cat 7a ethernet cable.

---

### Post by perkhouse on 2010-08-06
> **wacky_sung said:**
> Wireless router running as server in wifi is slow.If cable, are you using gigabit wireless N router on a Cat 7a ethernet cable.

I'm sorry, but I fail to see the relevance to the current problem with ssh.

To everyone who has actually read the thread...
Since putting the Ubuntu box in the DMZ *should* have solved the problem, I won't post again until the new router arrives.

Oh, and Herman... kudos regarding your site - great articles!

---

### Post by OpSecShellshock on 2010-08-06
I think wacky_sung may have been suggesting that there's a potential latency issue. It may also be a split-tunnel problem if it's SSH over encrypted wi-fi, but neither of those seems to be borne out in the log data.

---

### Post by perkhouse on 2010-08-06
> **OpSecShellshock said:**
> ...there's a potential latency issue. It may also be a split-tunnel problem if it's SSH over encrypted wi-fi, but neither of those seems to be borne out in the log data.

Thanks! I think I've covered that though. I have tried over wi-fi as well as a 100mb cat5 port. I even tried going from the Ubuntu box back to itself via the WAN IP. It works fine if I'm using the Ubuntu machine's LAN address, but doesn't work over the WAN. And nothing (related) shows up in either the router's logs or /var/log/messages.

---

### Post by perkhouse on 2010-08-09
Ok, well... it was definitely the DIR-615 router. The Netgear WNR2000 is set up identically and ssh is working correctly now (with no changes to the Ubuntu machine).

Now, I may install Squid3 again to eliminate the hoops of using an ssh client. I don't mind for myself, but just setting and forgetting the proxy settings in the browser will make it a lot easier for my non-technical friends (aka "clients").

So... to sum up:
[SIZE="4"]Do **NOT** use a D-Link DIR-615 router![/SIZE]

Hope this helps someone.

---

### Post by perkhouse on 2010-08-23
fyi... I also reinstalled Squid3, forwarded the custom port in the Netgear router and it's working flawlessly. The problems before were definitely caused by the D-link router. (Which by the way, was a replacement because the 1st one was broken - no wireless traffic if I enabled any encryption.) No more D-Link for me!!!

---

### Post by BkkBonanza on 2010-08-24
It's fairly common for some routers to filter outbound traffic to it's own WAN IP. I recall reading about this but have never had it myself since I use an Ubuntu box as my router. So in these routers the packets going out to WANIP never make it to the port being forwarded back to the server. There is a name for this "defect" but I don't recall it off hand now.

---

