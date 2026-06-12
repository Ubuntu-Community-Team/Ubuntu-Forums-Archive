---
title: "Internet privacy, here is a good read..."
date: 2008-11-28
forum: The Cafe
---

### Post by handy on 2008-11-28
The following link is very educational regarding internet privacy & should really be read by all who use the internet imho:

***_[https://www.torproject.org/torusers.html.en](https://www.torproject.org/torusers.html.en)_***
________________

Some people consider the use of [***_Tor_***]("https://www.torproject.org/") to be an inconvenience as it slows down their internet use.  It comes down to personal priorities in the end.

Another extremely useful tool is [***_Privoxy_***]("http://www.privoxy.org/") which combines very well with Tor & web browsing.

I use the Firefox [***_TorButton_***]("https://addons.mozilla.org/en-US/firefox/addon/2275") to handle Tor & Privoxy as it offers far more configuration options (than it used to).

On OS-X Tiger & above the QT based [***_Vidalia_***]("http://www.vidalia-project.net/") works very nicely with Tor & Privoxy, in combination with the TorButton.  This may be the case with Ubuntu, as I'm not running Ubuntu I can't test it.

---

### Post by Yownanymous on 2008-11-28
OK, I installed Tor, now what?

---

### Post by handy on 2008-11-28
You need to set up Tor, which will include installing Privoxy, here is a good page with instructions:

***_[https://www.torproject.org/docs/tor-doc-unix.html.en](https://www.torproject.org/docs/tor-doc-unix.html.en)_***

This Privoxy config file may be all you need:

***_[https://wiki.torproject.org/noreply/TheOnionRouter/PrivoxyConfig](https://wiki.torproject.org/noreply/TheOnionRouter/PrivoxyConfig)_***

Also, use the [***_TorButton_***]("https://addons.mozilla.org/en-US/firefox/addon/2275") if you are using Firefox, it is better than Vidalia, in fact it has improved so much since I last looked at it that I will edit my original post.

---

### Post by Eclipse. on 2008-11-28
Tor isnt good.

Everybody elses dirty work gets routed through you.

---

### Post by handy on 2008-11-28
> **Eclipse. said:**
> Tor isnt good.

Everybody elses dirty work gets routed through you.

I'm sorry, you don't understand how Tor works. 

You should go & read about Tor at the Tor site, links provided in the OP.

Here is a paragraph from the Tor site:

*Tor is a software project that helps you defend against traffic analysis, a form of network surveillance that threatens personal freedom and privacy, confidential business activities and relationships, and state security. Tor protects you by bouncing your communications around a distributed network of relays run by volunteers all around the world: it prevents somebody watching your Internet connection from learning what sites you visit, and it prevents the sites you visit from learning your physical location. Tor works with many of your existing applications, including web browsers, instant messaging clients, remote login, and other applications based on the TCP protocol.*

---

### Post by blakjesus on 2008-11-29
I heard some people were complainging to the makers of Tor about people using Tor for illegal uses, and wanted them to allow people to see what is being routed through them. I dont know hoe far this got but isnt that pretty much just as bad as an ISP selling your information to businesses.

---

### Post by linuxguymarshall on 2008-11-29
> **blakjesus said:**
> I heard some people were complainging to the makers of Tor about people using Tor for illegal uses, and wanted them to allow people to see what is being routed through them. I dont know hoe far this got but isnt that pretty much just as bad as an ISP selling your information to businesses.

I dont support that but this is more like a ISP wanting to see what you are doing in their routers.

---

### Post by handy on 2008-11-29
> **blakjesus said:**
> I heard some people were complainging to the makers of Tor about people using Tor for illegal uses, and wanted them to allow people to see what is being routed through them. I dont know hoe far this got but isnt that pretty much just as bad as an ISP selling your information to businesses.

No matter what you do & how many people that are happy with your work, you will always have the noisy one's complaining because they have a perceived loss of some kind, or of course they don't understand the situation.  

I've read a fair bit of the Tor site's documentation & some of their blog & their is no indication that they are going to do anything at all that will go against their prime philosophy of protecting people's privacy.

---

### Post by tomcheng76 on 2008-11-29
IMO Tor is not needed for general users. I tried Tor, it is really slow thing down.
Firefox with no script, abp is just fit.
They can block ads and analytics js.

---

### Post by handy on 2008-11-29
> **tomcheng76 said:**
> IMO Tor is not needed for general users. I tried Tor, it is really slow thing down.
Firefox with no script, abp is just fit.
They can block ads and analytics js.

NoScript is extremely complex with subtle traps built in that few would notice.  If you think you need protection for somewhere on the net it would seem that the Tor/Privoxy combination with nothing else will give you the best we can get.  

If you combine Tor/Privoxy with NoScript, you are just as likely making a security hole in the screen according to the Tor website.

So forgetting to use the TorButton becomes the biggest security risk under these circumstances. 

I'm currently trying to get [***_Polipo_***]("http://www.pps.jussieu.fr/~jch/software/polipo/") working as a caching proxy on the machine I use, if I can get it to work, it will speed up my internet access (reduce lag) & also do some of the Privoxy shielding for me.

---

### Post by smartboyathome on 2008-11-29
Well, I might've looked into it if it worked with OpenDNS. Unfortunately, according to [this post]("http://forums.opendns.com/comments.php?DiscussionID=2190"), tor treats OpenDNS as a DNS that has been hacked.

---

### Post by handy on 2008-11-29
> **smartboyathome said:**
> Well, I might've looked into it if it worked with OpenDNS. Unfortunately, according to [this post]("http://forums.opendns.com/comments.php?DiscussionID=2190"), tor treats OpenDNS as a DNS that has been hacked.

Very interesting post, I expect that the Tor people would sort that out.

I just searched their blog for opendns & got no results?

---

### Post by echo6 on 2008-12-04
Out of interest how did you build Privoxy?

> configure: WARNING: You are using the static PCRE code which is scheduled for removal, for details see:

---

### Post by magmon on 2008-12-04
I use foxy proxy, easy and integrates with firefox.

---

### Post by bryncoles on 2008-12-05
> **handy said:**
> NoScript is extremely complex with subtle traps built in that few would notice.

that got my attention! what subtle traps, might i ask?

---

