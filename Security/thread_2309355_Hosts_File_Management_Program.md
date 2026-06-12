---
title: "Hosts File Management Program"
date: 2016-01-09
forum: Security
---

### Post by ultrageeky on 2016-01-09
Many years ago I wrote a guide to using the hosts file to make Internet browsing safer and quicker. At the time of writing the guide I said I'd write a Linux script to make hosts file management easy. Finally (4 years later) got around to writing that script. For those who want to try the program, the download instructions and usage instructions can be found at [https://host-flash.com](https://host-flash.com).

The program is interactive and compiles a hosts file using multiple sources of reputable hostname blocklists.

The main features are:


[LIST]
[*]several hosts file source download locations 
[*]a whitelist to unblock sites in the downloaded hosts file(s) 
[*]a blacklist for adding additional blocked hosts files 
[*]auto integration with the existing hosts file 
[*](automatic) hosts file backup during updates, and 
[*]a quick run mode -- settings can be saved for reuse. 
[/LIST]

There are plans for future features to be added.

Please test the program and provide feedback so I can ensure it works for others as good as it does for me.

---

### Post by QIII on 2016-01-09
Hello!

Is the source code open and available for users to review?  It seems to me that in a Security sub-forum this would be appropriate.

---

### Post by ultrageeky on 2016-01-09
Good point. The source code can be read on [GitHub]("https://github.com/VR51/host-flash").

If you'd like to be involved in the project send me a request though Github and we'll see how we can enhance the program together.

---

### Post by sonicwind on 2016-01-10
I'm new to Linux so maybe these are dumb comments.

I can't read the screenshots on your website. Is that because they're poor screenshots or is the program design really blue on black? It's very difficult to read for those of us with less than perfect eyesight.

I was reading about using the hosts file to enhance security a few weeks ago using winhelp2002.mvps.org. The example given was a manual method (not GUI) and I gave up because I really didn't understand any of it. I guess I've learned a lot since then, as I just went back and read that page again before replying. I now understand it. My point is that I can definately see a purpose for this for those not wishing to do things that way.

Thanks.

---

### Post by ultrageeky on 2016-01-10
Maybe I need to redo those screenshots to improve their quality. The colours used by the dialogue boxes depend on whether your OS has a custom configuration file for dialog or whiptail (the programs that produce the dialogue boxes). More than likely you won't see blue text on black. Will add instructions to the site this week to explain how to change the colour scheme.

The Host Flash program lets you choose which hosts files to download. The hosts file from winhelp2002.mvps.org is one of the sources offered. You can choose multiple sources. The program combines them into one file with duplicates removed.

Part of the reason for the program is convenience and simplicity: I wrote Host Flash to help others and myself to quickly download, compile and install a list of hosts to block without need to constantly whitelist and blacklist additional sites on every update.

The other reason: I wanted to help other Linux users understand what a hosts file can be used to do and to explain how the hosts file works.

Thanks for the feedback.

---

### Post by sonicwind on 2016-01-10
Would you use this instead of **or** in addition to an ad blocker like AdBlock Plus (Firefox extension) ?

I just checked my AdBlock Plus, it uses the EasyList subscription.

Thanks.

---

### Post by ultrageeky on 2016-01-10
In addition to AdBlock Plus. I use Ghostery as well.

Hostnames rerouted via the hosts file, whether by Host Flash or manually, are rerouted regardless of how the request is made, with the exception of a Tor browser. AdBlock and Ghostery work in the browser so do not stop a wget, curl or ping request, for instance, made through the terminal or by software that are without AdBlock or Ghostery installed in them. Host Flash is browser independent because the blocklists are installed at the OS level.

---

### Post by mikodo on 2016-01-12
Hi.

I use [uBlock Origin]("https://addons.mozilla.org/en-US/firefox/addon/ublock-origin/") in Firefox. No doubt you are aware of it. It has a page to select different Hosts File Lists. What you think of it? Good Lists? 

I am thinking of adding your script in conjunction with uBlock Origin. Good Idea?

MVPS HOSTS 

Dan Pollack's hosts file

hpHost's Ad and tracking Servers 

Thanks

---

### Post by ultrageeky on 2016-01-14
Hi mikodo,

Host Flash offers to download hosts lists from:


[LIST]
[*]hosts-file.net (hpHosts) 
[*]winhelp2002.mvps.org (MVPS - all lists offered) 
[*]rlwpx.free.fr 
[*]hostsfile.org 
[/LIST]

I've sent Dan an email to ask permission to include the Dan Pollack's hosts file.

Hope to have it in Host Flash soon.

I'm not familiar with uBlock Origin.

---

### Post by drm200 on 2016-04-21
Does a HOSTS file provide any protection for Ubuntu 14.04?  In my experimentation ... I modified the hosts file to block facebook by adding 0.0.0.0 facebook.com.  If I go to chrome and type [https://facebook.com/](https://facebook.com/) in the address bar, the site is blocked.  if I ping facebook.com, it returns: 64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.047 ms.  So it seems to work at this level.

However, if I now search google for facebook.com in chrome and then click on the link, the facebook page opens and I am able to log in.  it seems that chrome bypasses completely the hosts file. Since most of the "new" sites I visit are based on some google search, I am wondering if a hosts file is providing any extra protection.    Is there a way to force chrome or firefox to use/respect the hosts file?  I know that I can use a plugin like uBlock ... But, if I must use uBlock, of what value is the hosts file?  And if chrome can bypass the hosts file, why can't any other program that has access to the web?  Am I missing something in my Ubuntu setup?

---

### Post by Habitual on 2016-04-21
The "MVPS HOSTS" hack is so 1998.

---

### Post by ant2ne on 2016-04-21
As discovered, not all apps are going to look at your hosts file. And any malware will surely not. It would be more effective to block the sites at the iptables level instead of the hosts file.

---

### Post by drm200 on 2016-04-22
I do not understand your suggestion.   Can you explain how someone could block the domains listed in a hosts file using iptables?  My hosts file has about 50,000 domains names listed for blocking.  I do not know how to use domain names in iptables.  And is it practical to have 50,000 listing in iptables?   50,000 is not a problem for a hosts file as it adds no decernible lag but I don't know about iptables.

---

### Post by drm200 on 2016-04-22
[COLOR=#000000]........ The "MVPS [/COLOR][COLOR=#417394]HOSTS[/COLOR][COLOR=#000000]" hack is so 1998[/COLOR]

Ok. I understand you do not think a hosts file is relevant today.  But what method is better today for blocking known malware domains from your computer?  I travel 365 days per year .. I only have a laptop and have no servers or company servers to connect to.  A HOSTS file makes sense to me ... But I find no other options available when I search the internet.

---

### Post by Habitual on 2016-04-22
> **drm200 said:**
> But what method is better today for blocking known malware domains from your computer?  I travel 365 days per year .. I only have a laptop and have no servers or company servers to connect to.
A firewall comes to mind.
Malware doesn't just magically "find" a laptop computer connected to an arbitrary network.
Use https on WiFi and some common sense. Adblock(or similar) and NoScript.
Practice safe hex.

---

### Post by drm200 on 2016-04-22
> **Habitual said:**
> A firewall comes to mind.
Malware doesn't just magically "find" a laptop computer connected to an arbitrary network.
Use https on WiFi and some common sense. Adblock(or similar) and NoScript.
Practice safe hex.

I agree that malware does not just "find" the laptop.  The beauty of a hosts file is that it can include lists (like the MVPS list) of known malicious sites ... HTTPS, VPN's or firewalls will not help protect from these malicious sites. NoScript or uMatrix or uBlock provide some protection but only within the browser they are installed.  The best protection would be to simply not visit the malicioius sites.

I do not purposely connect with any of these malicious sites.  But many can be connected to with an innocent slip of the finger while typing in the address bar or searching as these sites are often named very similarly to known good sites. So I still see value in the concept of blocking known good sites.  I am not so young .. and I often find myself making typo's ... so I feel at risk of connecting to an unwanted site.

I am searching for a method to force my Ubuntu system to block malicious sites as defined by my HOSTS file. The script that was mentioned in the original post here provides a easy method to keep the hosts file updated ... but it doesn't help me until I can find a method to force Ubuntu to use the hosts file ... I am hoping that someone has already figured this out.

---

### Post by Habitual on 2016-04-22
the hosts file edits only protect from **known** sites.
What about the unknown ones?

Instead of typos, use bookmarks.:)

See also [http://security.stackexchange.com/questions/9795/any-additional-security-with-large-blacklisting-hosts-file](http://security.stackexchange.com/questions/9795/any-additional-security-with-large-blacklisting-hosts-file)

AdblockPlus has a custom blacklist feature.

---

### Post by drm200 on 2016-04-22
> **Habitual said:**
> the hosts file edits only protect from **known** sites.
What about the unknown ones?

Instead of typos, use bookmarks.:)

See also [http://security.stackexchange.com/questions/9795/any-additional-security-with-large-blacklisting-hosts-file](http://security.stackexchange.com/questions/9795/any-additional-security-with-large-blacklisting-hosts-file)

AdblockPlus has a custom blacklist feature.

Exactly .... First deal with the known threats ... the unknown threats can only be dealt with by "hope and prayer" that the other protections implemented provide some degree of protection. 

I would never refuse to install security updates on my machine for known threats because of worry of the unknown threats.

---

### Post by bashiergui on 2016-04-23
> **drm200 said:**
> Ok. I understand you do not think a hosts file is relevant today.  But what method is better today for blocking known malware domains from your computer?  I travel 365 days per year .. I only have a laptop and have no servers or company servers to connect to.  A HOSTS file makes sense to me ... But I find no other options available when I search the internet.
Use a proxy to filter the sites you visit. There are way too many legitimate websites serving up malware because they are poorly configured and easily hacked. I can't imagine trying to keep up with that myself. 

Bluecoat is an enterprise-grade proxy software. They have a free version called K9. I'd highly recommend it to filter out malicious sites. 
[http://www1.k9webprotection.com](http://www1.k9webprotection.com)

---

### Post by cogset on 2016-04-25
> **drm200 said:**
>  I modified the hosts file to block facebook by adding 0.0.0.0 facebook.com.  If I go to chrome and type [https://facebook.com/](https://facebook.com/) in the address bar, the site is blocked.  if I ping facebook.com, it returns: 64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.047 ms.  So it seems to work at this level.

However, if I now search google for facebook.com in chrome and then click on the link, the facebook page opens and I am able to log in.  it seems that chrome bypasses completely the hosts file. 

That's interesting IMHO, unless the search from google actually redirects to a different domain then facebook.com, I would expect the hosts file to block that even using chrome - unless, among its other interesting "features", chrome also sports the ability to override somehow a redirection to localhost .

---

### Post by ultrageeky on 2017-02-08
> **drm200 said:**
> Does a HOSTS file provide any protection for Ubuntu 14.04? In my experimentation ... I modified the hosts file to block facebook by adding 0.0.0.0 facebook.com. If I go to chrome and type [https://facebook.com/](https://facebook.com/) in the address bar, the site is blocked. if I ping facebook.com, it returns: 64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.047 ms. So it seems to work at this level.

However, if I now search google for facebook.com in chrome and then click on the link, the facebook page opens and I am able to log in. it seems that chrome bypasses completely the hosts file. Since most of the "new" sites I visit are based on some google search, I am wondering if a hosts file is providing any extra protection. Is there a way to force chrome or firefox to use/respect the hosts file? I know that I can use a plugin like uBlock ... But, if I must use uBlock, of what value is the hosts file? And if chrome can bypass the hosts file, why can't any other program that has access to the web? Am I missing something in my Ubuntu setup?

I'm the author of Host Flash. I'm sorry I missed your question. Had an email from sonicwind to draw my attention to it.

A hosts file needs an exact address to be added to it for that exact address to be blocked. Facebook can be reached at facebook.com, [www.facebook.com]("http://www.facebook.com"), en-gb.facebook.com etc... To ensure all Facebook sites are blocked you need to include a rule in /etc/hosts for the root domain (facebook.com) and every sub domain of it that you wish to also block (e.g. [www.facebook.com]("http://www.facebook.com"), en-gb.facebook.com). Your Google search will have brought up a subdomain of facebook.com. That subdomain will not have been blocked by the hosts file unless there was a rule for it in the hosts file.

A hosts file works by re-routing outbound traffic to another IP address. It is like having your own personal DNS server where you control the Internet's address system.

Two advantages of using a hosts file to intercept outbound requests to undesirable domains to redirect them to a safe/preferred alternative domain (via the preferred server's IP address) are:

    
[LIST=1]
[*]A rule stated in the hosts file that denies requests to any specified domain name can normally only be bypassed by use of a VPN/TOR network or by using an IP address to request a resource from an otherwise blocked/redirected host (web server). Keep in mind that most requests for resources stored on web servers are made using domain names not IP addresses, and
[*]Websites do not usually know they are being blocked by a hosts file so ads can be blocked without triggering anti adblock notices to display.
[/LIST]
 
The let-downs are:


[LIST=1]
[*]     A domain needs to be explicitly stated in the hosts file for it to be blocked (a sub domain is a different domain to its root domain), and
[*]Someone with sufficient knowledge of the DNS system or hosts file can find workarounds to allow them to reach blocked hosts
[/LIST]
 
A hosts file will help protect your system from ads, malware downloads and trackers etc.. but it is not the only defence to use to protect a system.

I use the hosts file in conjunction with in-browser adblock & noscript extensions. Ghostery, Adblock Plus, Security Plus and Traffic Light are good browser extensions to use.

The hosts file is my primary defence and works at the OS level (can I drop Linux in there as well ). Browser plugins are secondary defences and only work for the web browser whereas the hosts file is not tied to a specific client.

> **ant2ne said:**
> As discovered, not all apps are going to look at your hosts file. And any malware will surely not. It would be more effective to block the sites at the iptables level instead of the hosts file.

Doesn't matter what an app does. The hosts file works at the OS level. An app/client must work with the OS to be able to send an outbound request. The hosts file is read before requests are sent out. Even a TOR/VPN network needs to go through a hosts file before the network can be established but once established any requests made through a TOR/VPN will go through successfully because the requests will go through an unblocked/non redirected domain. TOR/VPN can be blocked by intercepting the network paths via a hosts file but you need to know which hosts to block.

iptables is another line of defence that works differently to /etc/hosts. Both can be used together to secure a computer more completely than either used alone can manage.


> **Habitual said:**
> A firewall comes to mind.
Malware doesn't just magically "find" a laptop computer connected to an arbitrary network.
Use https on WiFi and some common sense. Adblock(or similar) and NoScript.
Practice safe hex.

A hosts file is a firewall when used as a firewall.

HTTPS is an encrypted connection protocol. It gives no defence against malware served via HTTPS from an HTTPS enabled host. HTTPS is used to prevent data being read as it travels between sender and recipient (client and server/end-to-end).

Adblock and NoScript work within web browsers and offer no protection against requests sent via non browser software. That graphics app you downloaded from Sourceforge that happens to be infected with malware and uses cURL or wget or its own web client to communicate with its command server will never be aware of that browser plugin called AdBlock or NoScript because it does not use the browser that has them installed.

---

### Post by cariboo on 2017-02-09
Moved double posts to the jail.

---

