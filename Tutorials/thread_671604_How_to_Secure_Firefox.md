---
title: "How to Secure Firefox"
date: 2008-01-18
forum: Tutorials
---

### Post by bodhi.zazen on 2008-01-18
[SIZE=6][CENTER]How to Secure Firefox[/CENTER]
[/SIZE]

[CENTER][IMG]http://www.kde-look.org/CONTENT/content-files/48278-firefox_mond.png[/IMG][/CENTER]

_Intro_: What we are going to do is secure Firefox by blocking cookies and Java, then adding only trusted sites via a "White List" (White list = exceptions).

[COLOR=navy]bodhi.zazen: Updated 1/12/1010[/COLOR]

_Contents_:
[LIST=1]
[*]Adblock.
[*]Cookies.
[*]Customize Google.
[*]Java/Flash (NoScript).
[*]Phishing.
[*]Secure private data.
[*]Write an Apparmor Profile.
[*]Using Firefox, ie how to generate white lists.
[/LIST]

_Appendix_:
[LIST]
[*]Surf Anonymously ~ Privoxy/TOR
[*]Other Privacy issues
[/LIST]


[SIZE=4]Adblock[/SIZE]

We have three options here, Hosts file, Firefox extensions, or proxy servers.

[LIST=1]
[*]Hosts file. I prefer a hosts file as it protects more then just Firefox.

Here is how I do a hosts file : [http://ubuntuforums.org/showthread.php?t=241460#2](http://ubuntuforums.org/showthread.php?t=241460#2)

Direct link to [hosts file]("http://www.mvps.org/winhelp2002/hosts.txt")
[*]Firefox extension : [Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865")
[*]Proxy servers. Proxy servers may be used to increase privacy as well (see TOR) and come in several flavors, caching and non-caching. In general, caching is not needed as Firefox uses it's own cache. Configuration of each and every proxy server and configuring a firewall so that a proxy as "transparent" is beyond this post (transparent means you have configured your network so that users do not have to manually configure Firefox and in general involve a hardware firewall + a squid server).

As an example [See here]("http://www.cyberciti.biz/tips/linux-setup-transparent-proxy-squid-howto.html")

IMHO, for single user desktops, I advise Adblock Plus. 
IMHO, in a multi user environment or on a LAN, I advise a proxy server.
[LIST=a]
[*][Privoxy]("http://www.privoxy.org/") is a very popular option.```
sudo apt-get install privoxy
```Privoxy is fast, light, and has adblocking "built in". See "bfilter" below for how to configure Firefox to use a proxy.
[*][Bfilter]("http://bfilter.sourceforge.net/"). As of Ubuntu 9.10 bfilter is no longer supported in the ubuntu repositories. You may still install bfilter using [Autopackage]("http://bfilter.sourceforge.net/download.php"). Autopackage installs the bfilter-gui.

Bfilter runs on windows as well (portable, nice when you are using a guest computer).

Bfilter is easy to install and configure.```
sudo apt-get install bfilter
```To configure, open Firefox preferences -> Advanced tab -> Network tab -> now click the "settings" box. Use 127.0.0.1 port 8080 as a proxy (see screen shot)

[IMG]http://bodhizazen.net/img/config.ff.bfilter.png[/IMG]
[*]Squid. Squid can be used for adblocking and has several advanced features. See also [DansGuardian]("https://help.ubuntu.com/community/DansGuardian").
[/LIST]
 
[/LIST]

If you need a few pointers on Dansguardian or configuring an invisible proxy, see also :

**[How to  transparent proxy]("http://blog.bodhizazen.net/linux/how-to-transparent-proxy/")**

**[Web content filtering made easy]("http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/")**


[SIZE=4]Cookies[/SIZE]

Go to your Firefox menu -> Preferences -> Privacy Tab

UNSELECT "Accept cookies from sites"

All cookies are now blocked.

**Flash manages cookies directly.** To manage flash cookies : [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html](http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager02.html)

[COLOR=blue] ~ Thanks [/COLOR][benny bronx]("http://ubuntuforums.org/member.php?u=319476")


[SIZE=4]Javascript/Flash[/SIZE]

Javascript/Flash are a cross platform programing languages commonly used on the web. They add functionality, but also allow browser hijacks.

Install [NoScript]("https://addons.mozilla.org/en-US/firefox/search?q=noscript&status=4")

To configure, right click on the NoScript icon (lower right) and select options.


[SIZE=4]Optimize Google[/SIZE]

That's right, google is feeding you adds :(

Install this extension.

[Optimize Google]("https://addons.mozilla.org/en-US/firefox/addon/52498")

Then :

Tools -> Optimize Google Options

Go through each category on the Left and tic off "Remove Adds" (and anything else you might like).

Another great extension (IMO) is [googleefree]("https://addons.mozilla.org/en-US/firefox/addon/10687") . This is not really an extension, it is a google search bar that excludes [Expert Exchange]("http://www.experts-exchange.com/") (that annoying service you have to join to see solutions).


[SIZE=4]Phishing[/SIZE]

Phishing is, in a nut shell, spoofing a web site or an attempt to fool users to divulge personal information.

[Wikipedia Phishing]("http://en.wikipedia.org/wiki/Phishing")

There are several Firefox extensions to consider, Web of Trust is one example.

[Web of Trust]("https://addons.mozilla.org/en-US/firefox/addon/3456")


[SIZE=4]Secure Private Data[/SIZE]

[LIST=1]
[*]Go to your Firefox menu -> Preferences -> Security Tab

Set a "Master Password". This will protect others from displaying your passwords. *If you have a sensitive password like to the Ubuntu Forums or your Bank, BEST NOT TO STORE IT AT ALL*.

[COLOR=navy]Hey, while you are there, check out the password strength meter.[/COLOR]
[*]Install [SafeHistory]("https://addons.mozilla.org/en-US/firefox/addon/1502").

[COLOR=blue]Safe History functionality is built into Firefox 3.5.x and is configured under Options -> Privacy tab -> use custom settings (select this option from the pull down menu).[/COLOR]

You may also configure Firefox , in about:config, to disable the use of an offline cache.

browser.cache.offline.capacity 0
browser.cache.offline.enable false
[*]Install [SafeCache]("https://addons.mozilla.org/en-US/firefox/addon/1474") to be safer against CSRF attacks.
[*]As of Firefox 3.5 there is an option for [Private browsing]("http://www.firefoxfacts.com/2009/07/01/firefox-private-browsing-mode-help-and-faq/")
[/LIST]

[COLOR=blue]~ Thanks FaBi3ttO[/COLOR]


[SIZE=4]How to Whitelist[/SIZE]

OK, now you will likely find Firefox somewhat restrictive. The goal here is to allow "normal" functioning. In order to log into forums or your banking sites we need to allow Cookies and Java. We will do this [COLOR=blue]ONLY for specific sites we trust[/COLOR] via white lists.

[LIST=1]
[*]Cookies - Firefox options -> Privacy tab

Copy the Ubuntu url from your browser : [http://ubuntuforums.org/](http://ubuntuforums.org/)

Go to "Cookies" -> click the "Exceptions" button -> paste ubuntu url -> click "Allow for session"

[COLOR=red]For secure sites like Banking you will need to allow multiple url (https), usually one from the home page, then one from the log in page, and sometimes from the next page as well. So if you are having problems, keep adding url to the white list.[/COLOR]
[*]Java - Right click on the NoScript icon -> Allow Ubuntu.com
[/LIST]

[COLOR=blue]Repeat these steps until you have added your sites and have the functionality you need.[/COLOR] 


[SIZE=4]Use Apparmor Profile[/SIZE]

As of Ubuntu 9.10 there is now a profile for Firefox. It is disabled by default, to enable it use the command :

```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5
```The default profile may be a bit too permissive in allowing access to home directories so I advise you review it.

Firefox profiles for older versions of Ubuntu can be found [here]("http://bodhizazen.net/aa-profiles/bodhizazen/")

Apparmor is beyond this thread, but see these two threads :

[[all variants] Introduction to AppArmor - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1008906") 

[Share your AppArmor Profiles]("http://ubuntuforums.org/showthread.php?t=1008911")


[SIZE=4]How to Surf Anonymously ~ Privoxy/TOR [/SIZE]

Privoxy / TOR can significantly increase your privacy, but at a cost of reduced speed. *Please note however, that these services DO NOT offer complete anonymity.*

[Ubuntu wiki TOR]("https://help.ubuntu.com/community/TOR")

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian](http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian)

If you use TOR and have the capacity, consider contributing a TOR server (a few more servers would speed things up for everyone).

[http://en.linuxreviews.org/HOWTO_setup_a_Tor-server](http://en.linuxreviews.org/HOWTO_setup_a_Tor-server)

Tor is not the only option, there are other privacy proxies available to a google search.

[size=4]Privacy[/size]

Privacy is a separate but related issue and I added a page on my blog to get you stared:

[Internet Privacy](http://bodhizazen.net/Tutorials/Privacy)



[FONT=times][SIZE=4]*Peace be with you,*[/SIZE][/FONT][I]

[IMG]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/IMG][SIZE=4] [COLOR=navy][FONT=times]bodhi.[/FONT][/COLOR][FONT=times][COLOR=darkgray]zazen[/COLOR][/FONT][/SIZE][/I]

---

### Post by nikoPSK on 2008-01-18
very nice. I like it. There a bunch of speed tweaks as well I'm planning on writing about. :)

---

### Post by limac on 2008-01-18
great post bodhi, sure is going to be helpful around here! Especially the "Secure Private data"  part. really helpful

regards,
limac   :D

---

### Post by FaBi3ttO on 2008-01-28
Really good post.
I also use [SafeCache]("https://addons.mozilla.org/en-US/firefox/addon/1474")
to be safer against CSRF attacks.

---

### Post by bodhi.zazen on 2008-01-28
> **FaBi3ttO said:**
> Really good post.
I also use [SafeCache]("https://addons.mozilla.org/en-US/firefox/addon/1474")
to be safer against CSRF attacks.

Thanks I will add that link to the list.

---

### Post by nowshining on 2008-01-28
all safe cache does is disable cache - it makes it where each time u download something u'll have to re-download it..

as for others

u can also

about:config
find:

A: network.http.sendRefererHeader  > set this to 0 to disable referell - note some sites may require it - but few sites do - if u get probs, just reset it, and keep the tab open, do what u need and re-set it to 0. What this does is keep sites from knowing what sites u last visited.

B: network.http.sendSecureXSiteReferrer > set to false

C: network.jar.open-unsafe-types > make sure this is set to false

D: Download Contrle de scripts from the add-on site, this allows easier acces to only allow certain pop-ups, clicks, etc.. in other words certain pop-up types, go into prefs of the program and set the following:

Under allow scripts to - uncheck all,

go to the popups tab

Under allowed events only the following should be: click. dblclick, submit

Then press ok.

E: in about:config find browser.preferences.advanced.selectedTabIndex > set this to 2

 Determines which tab in the Advanced section of the preferences is visible.
**0** (default): General
**1**: Update
**2**: Security

---

### Post by bodhi.zazen on 2008-01-28
Thanks nowshining , keep the tips coming :)

---

### Post by SOULRiDER on 2008-01-29
I especially liked the Tor part, i had been wondering how to use Tor for a while but never really bothered to look for info on how to do it :P

---

### Post by nikoPSK on 2008-01-29
> **SOULRiDER said:**
> I especially liked the Tor part, i had been wondering how to use Tor for a while but never really bothered to look for info on how to do it :P
using tor seems a bit over the edge, but I guess that's how bad some things are... :[

---

### Post by Pyre_Vulpimorph on 2008-02-22
Concerning master passwords, how do you rate the FireFox Add-On, **Password Maker**, the one with the LotR-esque catchphrase "one password to rule them all"?

It claims to be uncrackable, but I'm sceptical about such claims.

---

### Post by euler_fan on 2008-02-25
[CookieSafe]("https://addons.mozilla.org/en-US/firefox/addon/2497")?

I've had success using it to handle my cookies.

---

### Post by GuttaMan on 2008-03-12
I found this this tutorial, followed all the steps, and every thing seems to be running smooth....except Google Maps;  after doing this tutorial, i can't seem to get Google Maps to load up anything. Anybody know what could be happening?

---

### Post by bodhi.zazen on 2008-03-12
> **GuttaMan said:**
> I found this this tutorial, followed all the steps, and every thing seems to be running smooth....except Google Maps;  after doing this tutorial, i can't seem to get Google Maps to load up anything. Anybody know what could be happening?

It takes a little effort on the front end, but it is well worth it, IMO

My guess is either you need to allow java / flash (ie NoScript) or allow cookies. When you go to a sub page at google the url may have changed and you may need to allow multiple google cookies.

---

### Post by GuttaMan on 2008-03-12
> **bodhi.zazen said:**
> It takes a little effort on the front end, but it is well worth it, IMO

My guess is either you need to allow java / flash (ie NoScript) or allow cookies. When you go to a sub page at google the url may have changed and you may need to allow multiple google cookies.

Thanx Man. I just decided to create a new Firefox profile and and take every step one at a time and afterwards immediately checking to see if I can load google maps...and now I followed every single step in the tutorial and google maps works just fine, even with Tor enabled and cookies disabled at the same time. I must've done something wrong the first time around.

---

### Post by Jacdeb6009 on 2008-03-15
Thanks bodhi,

This is most useful. It is more or less how I run Firefox, but the bit about host / adblock is new to me.

---

### Post by CharmCityCrab on 2008-04-29
On a Windows machine, what people would typically do is allow cookies and scripts, and then have an antivirus to catch malware and such.  This is obviously not as efficient as blocking cookies and scripts, or using a whitelist to enable select sites, but let's face it, using the Internet nowadays to it's full potential if you visit many common sites basically requires both cookies and scripts, and whitelisting can be a real pain.

Is there anything about the Unbuntu Linux architecture that makes using antivirus in combination with allowed cookies and scripts unworkable from a security prospective (to a greater degree than it may or may not be with Windows)?  Would a firewall help?

Most of the threads I've read about antiviruses and firewalls don't really address what they can or can not do in terms of securing Firefox and other browsers.  I'm wondering if maybe there is a built in assumption that you are not running non-whitelisted cookies or scripts when people recommend not using an antivirus or firewall.

---

### Post by bodhi.zazen on 2008-04-29
> **CharmCityCrab said:**
> On a Windows machine, what people would typically do is allow cookies and scripts, and then have an antivirus to catch malware and such.  This is obviously not as efficient as blocking cookies and scripts, or using a whitelist to enable select sites, but let's face it, using the Internet nowadays to it's full potential if you visit many common sites basically requires both cookies and scripts, and whitelisting can be a real pain.

Is there anything about the Unbuntu Linux architecture that makes using antivirus in combination with allowed cookies and scripts unworkable from a security prospective (to a greater degree than it may or may not be with Windows)?  Would a firewall help?

Most of the threads I've read about antiviruses and firewalls don't really address what they can or can not do in terms of securing Firefox and other browsers.  I'm wondering if maybe there is a built in assumption that you are not running non-whitelisted cookies or scripts when people recommend not using an antivirus or firewall.

Not sure exactly what you are asking about, but I will try to answer. Cookies and Java script are not the same as viruses or blocking connections with a firewall.

I personally do not like cookies and feel the invade my privacy. Thus I use a white list :lol:

With Java script why open yourself up to cross platform attacks / browser hacks? Again, IMO, it makes sense to use a white list.

What is it you want a firewall to do for you ? In a default Ubuntu installation, unlike windows, there are no servers installed, so there is nothing to "protect" with a firewall. If you install a private server you can protect it with a firewall or with a public server use a firewall to block cracking or DNS attacks (ie a black list). You need to understand what you are using a firewall for to configure it.

Or to put it another way, a default Ubuntu install does not have a ssh server, ftp server, <insert_additional_servers_here> installed, so there is no need to configure a firewall to block attempts to connect to ssh server, ftp server, <insert_additional_servers_here>.

You may be accustomed to monitoring network traffic with a windows firewall. Linux is modular and the firewall (and gui front ends) should be used to configure the firewall. Network monitoring is performed with different applications, such as snort or wireshark.

Interms of antivirus, there are no known active Linux viruses, so what are you looking for with a virus scanner ? If you are running a mail server or file server for windows clients it may make sense to install antivirus.

Most Ubuntu users do not need antivirus scanners and some use firewalls for specific purposes or run servers needing protection.

Linux security is different from windows security and I have seen Linux boxes hacked. See this link for additional information.

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by CharmCityCrab on 2008-04-29
> **bodhi.zazen said:**
> 
I personally do not like cookies and feel the invade my privacy. Thus I use a white list :lol:

Makes sense.  One could always just clear one's cookies from time to time, though, right?

> With Java script why open yourself up to cross platform attacks / browser hacks? Again, IMO, it makes sense to use a white list.

I'm not very technologically adept and have a slow learning curve at times.  In fact, I'm fairly amazed I managed to run Linux at all.  So, I hope you'll bare with me if I'm not correctly understanding you.  Using Firefox in Windows, what sort of protection is typically in place against these attacks and browser attacks executed through java script if the user has a standard browser install with scripts enabled (And assuming moderate security measures in place like Norton or McAfee's packages and maybe spybot)?  Is there any?  If  so, what's the best way to duplicate that protection in Ubuntu (if needed)?

Does Spybot Search and Destroy have a Linux version?  Would there be a need for one.

Thanks for the reply.  Some of the post was very helpful.  I think I'll get a grasp on Linux one of these days.  I'm making some progress with it.

---

### Post by benny bronx on 2008-05-28
> CookieSafe?

I have used the updated version of this, cs lite, and it comes with a large blocklist of the usual tracking cookie suspects.

I found noscript to be a real pain,  My solution was to open the options menu and allow top level sites by default.  Less secure but much less noisy when browsing. And it will still block all the 3rd party scripts that are the main privacy concerns. I also block iframes (plugins) and web bugs (advanced).

An issue that was not addressed are flash cookies.  When you allow flash content, these cookies get stored in home/macromedia/shared objects.  You can manually clear them out or you could adjust your flash settings to disallow websites from storing any flash content on your comp.  The adjustment can be made here:

[http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager07.html")

---

### Post by kevdog on 2008-05-31
Not sure if this is Firefox specific -- maybe it is -- but instead of TOR (or in addition), you could always tunnel your Firefox connection using a SOCKS5 proxy through an encrypted ssh connection. This would most likely be applicable to laptop users using various open "cafe" networks, however it could also be used by others.

I think wormser wrote a HowTo how to do this:
[http://ubuntuforums.org/showthread.php?t=723025](http://ubuntuforums.org/showthread.php?t=723025)

---

### Post by Master Chief on 2008-08-19
> **bodhi.zazen said:**
> ...

I personally do not like cookies and feel the invade my privacy. Thus I use a white list :lol:...

You are aware of Flash cookies, right?  Have a look for/in this directory:
/home/[username]/.macromedia

There's also a new/better(evil?) way of storing data:
[http://developer.mozilla.org/en/docs/DOM:Storage](http://developer.mozilla.org/en/docs/DOM:Storage)

**Flashblock** is another good add-on:
[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)
[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)

Which would have saved a few folks from running into this clipboard issue:
[http://www.theregister.co.uk/2008/08/15/webbased_clipboard_hijacking/](http://www.theregister.co.uk/2008/08/15/webbased_clipboard_hijacking/)
[http://www.theregister.co.uk/2008/08/18/malvertizing_epidemic/](http://www.theregister.co.uk/2008/08/18/malvertizing_epidemic/)

p.s. Some people even change their HTTP User Agent to get that little extra "security", but please note that installing add-ons (extensions) might open a can of worms (the a.m.o review process is a mess).

> **Pyre_Vulpimorph said:**
> Concerning master passwords, how do you rate the FireFox Add-On, **Password Maker**, the one with the LotR-esque catchphrase "one password to rule them all"?

It claims to be uncrackable, but I'm sceptical about such claims.

I do happen to know the author/developer (as I work on the Mozilla codebase since 1999) and I can assure you that Eric's work is very good (Eric is also known to be a mozdev.org board member which are good people/funded by MoCo).

---

### Post by bodhi.zazen on 2008-08-19
> **Master Chief said:**
> You are aware of Flash cookies, right?  Have a look for/in this directory:
/home/[username]/.macromedia

Yes, I added a "one liner" about flash under "cookies" some time ago.

> There's also a new/better(evil?) way of storing data:
[http://developer.mozilla.org/en/docs/DOM:Storage](http://developer.mozilla.org/en/docs/DOM:Storage)

I will have to look at at that ....

**> Flashblock** is another good add-on:
[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)
[http://flashblock.mozdev.org/](http://flashblock.mozdev.org/)

Which would have saved a few folks from running into this clipboard issue:
[http://www.theregister.co.uk/2008/08/15/webbased_clipboard_hijacking/](http://www.theregister.co.uk/2008/08/15/webbased_clipboard_hijacking/)
[http://www.theregister.co.uk/2008/08/18/malvertizing_epidemic/](http://www.theregister.co.uk/2008/08/18/malvertizing_epidemic/)

NoScript also blocks Flash , so why add Flashblock ?

> p.s. Some people even change their HTTP User Agent to get that little extra "security", but please note that installing add-ons (extensions) might open a can of worms (the a.m.o review process is a mess).

Thanks for that.

> I do happen to know the author/developer (as I work on the Mozilla codebase since 1999) and I can assure you that Eric's work is very good (Eric is also known to be a mozdev.org board member which are good people/funded by MoCo).

Hats off to all the developers :)

---

### Post by Master Chief on 2008-08-20
> **bodhi.zazen said:**
> Yes, I added a "one liner" about flash under "cookies" some time ago.

Ugh, which I obviously missed with my old dyslectic eyes. Sorry.

> NoScript also blocks Flash , so why add Flashblock ?

First; I personally don't use any add-ons (extensions) at all, but I know that Flashblock implemented "Click-To-View" (an idea of someone I know which was picked up by Jesse Ruderman - who wrote the first public scripts for it, way back in time) and I'm unaware of NoScript using the same kind of trickery.

Have you tried Flashblock?  If not give it a try and let me know what you think of it.

---

### Post by bodhi.zazen on 2008-08-20
LOL Master Chief

Yes, I have used Flashblock in the past and had no problems with it. I was "educated" by another user on these forums, DrSmall, re NoScript blocks Flash as well, so I no longer use Flashblock (Why run 2 extensions when 1 will do).

NoScript is very nice, eliminates ads as well.

---

### Post by tlu on 2008-08-20
> **bodhi.zazen said:**
> 
[Adblock Plus]("https://addons.mozilla.org/en-US/firefox/addon/1865")
[Adblock Filterset.G Updater]("https://addons.mozilla.org/en-US/firefox/addon/1136")

This combination is [NOT recommended]("http://adblockplus.org/en/faq_project#filterset.g") by the Adblock Plus author!

> [*]Hosts file. I prefer a hosts file as it protects more then just Firefox.

An alternative is a [new list for Adblock Plus]("http://adblockplus.org/blog/blocking-malicious-sites-with-adblock-plus") that blocks more than 40,000 malicious websites. (Note: Only recommended for Firefox 3, NOT for Firefox 2!) 


> [SIZE=4]Cookies[/SIZE]

Go to your Firefox menu -> Preferences -> Privacy Tab

UNSELECT "Accept cookies from sites"

All cookies are now blocked.

The problem is that there are websites that require cookies in order to operate properly. A better way is to use a cookie manager. The best and most comprehensive one, IMHO, is [CookieSafe]("https://addons.mozilla.org/de/firefox/addon/2497") (already mentioned in another post)- you should also visit its [homepage]("http://forum.softwareblaze.com/viewforum.php?f=1&sid=91dcf78b2a9a58cc277b9d69eb81e859").


> [SIZE=4]Java/Flash[/SIZE]

Java/Flash are a cross platform programing languages commonly used on the web. They add functionality, but also allow browser hijacks.

Install [NoScript]("https://addons.mozilla.org/en-US/firefox/search?q=noscript&status=4")

You forgot to mention Javascript != Java. Actually most security leaks in Firefox have been related to Javascript.

---

### Post by bodhi.zazen on 2008-08-20
It is nice to see this thread getting a little more traffic / discussion.

* Updated java => javascript

Thanks for the suggestions everyone, keep them coming, I am sure this discussion has helped a number of people.

---

### Post by Master Chief on 2008-08-21
The best thing people can do is to be cautious, and at all times.

The good news is that Mozilla will change the world once more; because we are writing something that will eliminate the need for add-ons like:

Flashblock, NoScript, Permissions manager, Content blockers and even our own Page Info.

It is just a matter of time, and I am sure that Microsoft, Apple, Opera and the others will follow suite again... just like they did with tabbed browsing.

Note: This is the first public posting about this feature. That's how [COLOR="Red"]hot[/COLOR] this feature still is! And that's all I can say about it for now.

---

### Post by Xiong Chiamiov on 2008-12-21
> **benny bronx said:**
> I have used the updated version of this, cs lite, and it comes with a large blocklist of the usual tracking cookie suspects.

cs lite++

---

### Post by tturrisi on 2008-12-21
How is java a threat in Firefox running on Linux?

---

### Post by bodhi.zazen on 2008-12-22
> **tturrisi said:**
> How is java a threat in Firefox running on Linux?

java script to be precise.

[http://it.slashdot.org/article.pl?sid=03/06/08/239237](http://it.slashdot.org/article.pl?sid=03/06/08/239237)

---

### Post by ithanium on 2008-12-22
Great post, I think AdBlock extension is by far the best extention out there for FF.

---

### Post by tturrisi on 2008-12-22
> **bodhi.zazen said:**
> java script to be precise.

[http://it.slashdot.org/article.pl?sid=03/06/08/239237](http://it.slashdot.org/article.pl?sid=03/06/08/239237)

Not a big deal at all.  That bug was in the javascript model itself, specifically javascript code that is used to call a java applet from another Web site and have that applet load in the browser at some later time AFTER the viewer has left the originating Web page.  Java applets are sandboxed and don't have file system access.  The "security risk" here is that javascript on a page calls the applet from another domain and the applet is not loaded at that time, it's loaded later.  But the applet cannot harm the system at all.  It really a non-issue.

IMHO, theres no need to worry about java security in a browser on Linux.  It's not a big deal.  Besides, java applets on the Web are almost not seen anymore except for realtime chats and secure business applications, most sites now use Flash in place of java.  I've not had a java enabled browser for 4 years and haven't missed out on anything.

---

### Post by bodhi.zazen on 2008-12-22
As you wish, to each their own. Personally I do not use flash or java script much, but I prefer to block all and allow by site as needed.

---

### Post by tturrisi on 2008-12-23
> **bodhi.zazen said:**
> As you wish, to each their own. Personally I do not use flash or java script much, but I prefer to block all and allow by site as needed.

Agreed, to each his own.
FYI, a javascript enabled browser on Linux is also very safe as 99.9999% of all Web sites that use malicious javascript code cannot affect a Linux file system either.  It's safe to enable javascript.  It's also a pita to have to use exceptions to view javascript enabled sites.

The items java & javascript really don't belong in a thread called "how to secure...", they belong in a thred called "...privacy...".  That's what threw me to begin with in this thread as these two items are a privacy concern, not a security concern.

---

### Post by halovivek on 2008-12-29
Thanks for posting.

---

### Post by Bakon Jarser on 2009-01-01
Manually deleting flash cookies from adobe's web site is a pain.  I saw a suggestion on another forum to symlink ~/.adobe and ~/.macromedia to /dev/null.  I wanted a second opinion before I tried this.  I don't think it will cause problems, these cookies are mostly used to store things like volume settings.

---

### Post by benny bronx on 2009-03-05
I just installed the FF addon "passive cache".  It is good for all those who are paranoid when it comes to clicking on links. Right click on a link and you can open up the google cache of that link without making any connection to the target site. It also has a wayback machine option for the link.

---

### Post by minsf on 2009-03-07
> **Master Chief said:**
> The best thing people can do is to be cautious, and at all times.

The good news is that Mozilla will change the world once more; because we are writing something that will eliminate the need for add-ons like:

Flashblock, NoScript, Permissions manager, Content blockers and even our own Page Info.

It is just a matter of time, and I am sure that Microsoft, Apple, Opera and the others will follow suite again... just like they did with tabbed browsing.

Note: This is the first public posting about this feature. That's how [COLOR="Red"]hot[/COLOR] this feature still is! And that's all I can say about it for now.

great news! you guys are the best!
i'm sure microsoft will adopt anti flash and anti java things immediatly... LOL
cant wait!

oh and thanks bodhi for the post
one question though: how is safecache and safehistory different than just configuring firefox to clear all private data at the end of each session.
by the way, the TOR link seems to be broken.
i too vote for adding cs/cslite to this post- users are likely to get tired of adding exceptions through the firefox preferences, and cs seems to do it with a single click similar to noscript interface. 

i would love to see some about:config hacks in this post some time ( or a good reference for these)
keep up the good work bodhi!

---

### Post by androidkerra on 2009-03-08
very nice post, really helped me alot specially im just new :D

thanks

---

### Post by tlu on 2009-03-09
> **androidkerra said:**
> very nice post, really helped me alot specially im just new :D

thanks

Yes, with the exception that bodhi.zazen still insists on using Filterset.G Updater with Adblock Plus although - as already mentioned in another post - the ABP author himself does NOT recommend that: [http://adblockplus.org/en/faq_project#filterset.g](http://adblockplus.org/en/faq_project#filterset.g)

---

### Post by bodhi.zazen on 2009-03-09
> **tlu said:**
> Yes, with the exception that bodhi.zazen still insists on using Filterset.G Updater with Adblock Plus although - as already mentioned in another post - the ABP author himself does NOT recommend that: [http://adblockplus.org/en/faq_project#filterset.g](http://adblockplus.org/en/faq_project#filterset.g)

If you take the time to read the first post, you will see Filterset.G is listed as an option.

If you also take the time to read the post, and follow the link I gave, you will also see I do not use either of these extensions (so hard to say i am "Insisting" on using them, :lolflag: )

The point is, IMO, one should use some type of ad blocking. There are several options for doing this and I leave it up to you to decide how to achieve and maintain this.

As a secondary point, several people have asked about firefox extensions.

Here is a link to all the extensions listed under privacy and security :

[https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:12?sort=name](https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:12?sort=name)

There are currently 202 addons. I can not take the time to review each and every one of these.

I would focus less on the extension or disagreements between the extension maintainers (I would not want this thread to degenerate into an aruement between the Adblock + and Filterset.G maintainers / developers) and more on how to secure yoru browser.

So please stay on topic, pick and choose your options, offer suggestions, etc and enjoy a more secure web browser.

---

### Post by tlu on 2009-03-09
> **bodhi.zazen said:**
> If you take the time to read the first post, you will see Filterset.G is listed as an option.

If you also take the time to read the post, and follow the link I gave, you will also see I do not use either of these extensions (so hard to say i am "Insisting" on using them, :lolflag: )

I've taken the time to read the first post, and it just mentions Adblock Plus and Adblock Filterset.G Updater as the two extensions for adblocking. The way how you list them one below the other gives the impression that you recommend to use them together particularly with regard to the fact that Adblock Filterset.G Updater can't be used as a stand-alone extension but only as a companion extension - readers who don't know better will probably go to AMO and install both although they shouldn't. So I don't know why you regard my statement as wrong.

> I would focus less on the extension or disagreements between the extension maintainers (I would not want this thread to degenerate into an aruement between the Adblock + and Filterset.G maintainers / developers) and more on how to secure yoru browser.

I agree, but I think the way how you present that aspect in the first post is misleading and should be avoided.

> So please stay on topic, pick and choose your options, offer suggestions, etc and enjoy a more secure web browser.

I did that already. See post #25.

---

### Post by mynameinc on 2009-07-17
NOTE:  I'm running Firefox 3.0.11, and SafeHistory nor SafeCache will work; both are for older versions of Firefox; only other add-on I tested was NoScript and it worked.

---

### Post by NightCrawler03X on 2009-08-24
[quote="bodhi.zazen"](that annoying service you have to join to see solutions).[/quote]
Or just scroll down the page past those fake advertisements, then you'll see the solutions. Apparently it's really difficult to comprehend that a small scrollbar indicates more content below, despite the suggestion that the page is only short.

That's how gullible people are fooled, through *the power of suggestion*.
Btw, nice post.

---

### Post by bodhi.zazen on 2009-08-24
> **NightCrawler03X said:**
> Or just scroll down the page past those fake advertisements, then you'll see the solutions. Apparently it's really difficult to comprehend that a small scrollbar indicates more content below, despite the suggestion that the page is only short.

That's how gullible people are fooled, through *the power of suggestion*.
Btw, nice post.

Thanks for the tip on that. To be honest I am not sure if I am gullible or if this is new as I have not visited EE in some time.

I do not recall either the long list of "fake advertisements" as you call it or the answers being visible the last time I looked.

---

### Post by Temetka on 2009-11-02
Hello everybody.

While this is only my second post here I would like to contribute a few things. First off my background training includes a Bachelors Degree in Information Security and I do this stuf for a living. I mainly lock down client networks, maintain AD Domains (Active Directory = Corporate Networks) and wireless access points for small and medium business. The thread on locking down Firefox is great and I just wanted to point out a few things as well as ask a question or two of my own.

First off all the computer defenses such as firewalls, anti-virus, hosts files, etc are part of a much larger security scheme known as Defense in Depth. Defense in Depth in a nutshell is what it sounds like. It is multiple layers of of Defense to protect the users from 'Bad Things'. This can include everything from network penetration to viruses to even social engineering. Wikipedia has a pretty good description of it located here:

[http://en.wikipedia.org/wiki/Defense_in_Depth_(computing]("http://en.wikipedia.org/wiki/Defense_in_Depth_%28computing"))

The NSA (National Security Administration, United States) has a wonderful PDF file about the topic which can be downloaded from the link below. If anyone knows security it's the spooks themselves. They also have a nice repository of other PDF's for hardening (locking down) other OS's such as Mac OS X and Windows.

[http://www.nsa.gov/ia/_files/support/defenseindepth.pdf](http://www.nsa.gov/ia/_files/support/defenseindepth.pdf)

The US-CERT Team Computer Emergency Readiness Team has a very good PDF on the topic located here:

[http://csrp.inl.gov/Documents/Defense%20in%20Depth%20Strategies.pdf](http://csrp.inl.gov/Documents/Defense%20in%20Depth%20Strategies.pdf)

I'd also recommend checking out there site in general.

Finally no mention of security would be complete with out a mention of the wonderful folks over at SANS. You can check out there website here:

[http://www.sans.org/](http://www.sans.org/)

They also have a list of what they feel is the Top 20 security problems which you can view here:

[http://www.sans.org/top20/](http://www.sans.org/top20/)

Whew, that's a lot of information to digest. I realize that most Ubuntu users are not Network Administrators, Developers or Security Professionals so I thought I would chime in with some thoughts. Now I would like to take the opportunity to discuss a great Firefox addon that I personally love and use. It is called ghostery and it can be found by checking out the link below. 

[https://addons.mozilla.org/en-US/firefox/addon/9609](https://addons.mozilla.org/en-US/firefox/addon/9609)

You can check out the developers site by clicking on the link below.

[http://www.ghostery.com/](http://www.ghostery.com/)


Now that I have provided some information let me pose my question. It's somewhat advanced but bear with me.

I am well aware of AppArmor and indeed have checked out the wonderful thread over at:

[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

But from what I understand it is not a true sandbox. What is sandboxing? Good question and frankly it is beyond the scope of this post and thread. Wikipedia has a nice little breakdown on it. You can check it out here:

[http://en.wikipedia.org/wiki/Sandbox_%28computer_security%29](http://en.wikipedia.org/wiki/Sandbox_%28computer_security%29)

So now that you've read this far and have a primer into Defense in Depth and Sandboxing for Applications here is the question:

Is there a way to sandbox Firefox?

Sandboxing firefox which when combined with a proper hosts file, a few good extensions and being completely isolated from the OS should provide an excellent amount (some might say paranoid, but it is the world we live in) amount of security.

Thanks for bearing with me through this and if you guys want more info I'd be happy to provide it.

---

### Post by bodhi.zazen on 2009-11-02
Apparmor is, IMO, more secure then "sandboxing" firefox.

If you wish to sandbox firefox you would use a chroot, the weak link with that would be accessing X.

---

### Post by Ijan on 2010-03-14
Thanks for the instructive reading bodhi.zazen!

As you are keeping things up to date I asked myself if the following phrase could not be misread by inexperienced users:
> Privoxy / TOR can significantly increase your privacy, [...] Please note however, that these services DO NOT offer complete anonymity.
I'm no native English speaker, but couldn't this be misunderstood as Tor providing medium level privacy/anonymity to all applications routed through it when it's actually quite classy at it's specific field - providing IP-address- and network-analysis-related anonymity (+ filtering addons) - while it does not at all (at exit node level extra- ) encrypt your application traffic.

Might this not be a dangerous misconception for an inexperienced user learning by your HowTo and the two linked articles how to route an IRC- or Mail-client through Tor without learning that you should double-check that those applications don't use unencrypted protocols in this case if you next to anonymity also need privacy/do transfer login data etc.?

---

### Post by karthick87 on 2010-06-17
Very helpful information..!

---

### Post by needhelppeeps on 2010-08-01
Since I set cookies to per session only and installed NoScript, my firefox (3.68) password manager has went to crap. On many sites, I am never prompted to store the password no matter how many times I enter it. It's like the password manager just doesn't realize it should ask to save them. The few it saved still work just fine. Any tips, wild ideas, or experience with this?

---

### Post by Soul-Sing on 2011-01-06
optimize or customize add-on?
The most optimal way to customize google is the use of the optimize add-on, there was (is?) also a customize add-on. But they are both named in the "howto".
Thx for sharing the information how to secure firefox by the way.:KS

---

### Post by bodhi.zazen on 2011-01-06
> **leoquant said:**
> optimize or customize add-on?
The most optimal way to customize google is the use of the optimize add-on, there was (is?) also a customize add-on. But they are both named in the "howto".
Thx for sharing the information how to secure firefox by the way.:KS

You are most welcome.

Knowing your posting style from your forums activity, you might be interested in some of this information as well (although some of it you already know)

[http://bodhizazen.net/Tutorials/Privacy](http://bodhizazen.net/Tutorials/Privacy)

---

### Post by wolfv6 on 2011-08-21
> **bodhi.zazen said:**
> [SIZE=4]Cookies[/SIZE]
Go to your Firefox menu -> Preferences -> Privacy Tab

UNSELECT "Accept cookies from sites"

All cookies are now blocked.
I am not seeing "Accept cookies from sites" on my Firefox 6.0 on Ubuntu 11.04, Gnome.

Here are the screen shots:
[IMG]https://lh6.googleusercontent.com/-eVD2WUvE9co/TlFQLecnHRI/AAAAAAAAAPA/mPCAHc9_jnw/s640/Firefox_Preferences.png[/IMG][IMG]https://lh4.googleusercontent.com/-2Y3jAcYAHqk/TlFQOavN7FI/AAAAAAAAAPE/aLgnQEaEfD8/Firefox_Cookies.png[/IMG]

Is there another way to UNSELECT "Accept cookies from sites"?

Thank you bodhi.zazen for showing us how to secure Firefox.

---

### Post by bodhi.zazen on 2011-08-21
in the History tab , select "Firefox will" - select use custom settings ;)

---

### Post by wolfv6 on 2011-08-24
> **bodhi.zazen said:**
> in the History tab , select "Firefox will" - select use custom settings ;)

Thanks bodhi.zazen, that works great!  Now my online banking is as safe as can be.

---

### Post by justinsn95 on 2011-12-03
Any new update to this? Some of the info seems to not work anymore.

---

### Post by bodhi.zazen on 2011-12-03
> **justinsn95 said:**
> Any new update to this? Some of the info seems to not work anymore.

Better you start a support thread with any problems you are having or you can PM me with specific details and I will take a look.

---

### Post by bzd454 on 2011-12-29
can we continue this thread? 

 a lot of it can be done by making a user.js file for Firefox from the about:config section. that way you can just copy that user.js file for a re-install or 2nd and 3rd profiles or computers.

stuff like

dom.storage.enabled = false
geo.enabled = false  
geo.wifi.uri = leave blank for linux or "localhost" for windows      
privacy.donottrackheader.enabled = true
browser.sessionhistory.max_entries = 2
browser.display.use_document_fonts = 0
browser.search.suggest.enabled = false
browser.sessionstore.privacy_level = 2
network.cookie.lifetimePolicy = 2
layout.css.visited_links_enabled = false

also, i just use cookie monster and cookie whitelist with buttons, refcontrol and change referer button, cache toggle, and noscript, https everywhere etc.  trying to use request policy also.

did anyone mention:

  panopticlick
  browserspy
  ip-check.info

great tests there to see what they are able to know about your browser and computer.

---

### Post by tlu on 2011-12-31
> **bzd454 said:**
> 
dom.storage.enabled = false
...


also, i just use cookie monster and cookie whitelist with buttons, 

I'm not sure why you need Cookie Whitelist if you use Cookie Monster :confused:

Regarding DOM storage: It's problematic to disable it completely, IMHO, as this breaks some sites (I have a banking site where this is the case). And it's not really necessary for privacy reasons as the same restrictions are applied as to cookies (which you control with Cookie Monster): If you block cookies for a specific site, DOM storage is also blocked. If you allow session cookies for a specific site, the same is applied to DOM storage. And if you allow permanent cookies for a site, DOM storage is also permanently allowed.

---

### Post by euclid1219 on 2012-01-06
Did you make a thread on how to secure Google chromium?
if so can you send me a link please 
looked couldn't find it

---

### Post by bodhi.zazen on 2012-01-07
> **euclid1219 said:**
> Did you make a thread on how to secure Google chromium?
if so can you send me a link please 
looked couldn't find it

Chrome / Chromium is fairly secure under the hood.

I have a few tips here

[http://bodhizazen.net/Tutorials/Privacy#Chrome](http://bodhizazen.net/Tutorials/Privacy#Chrome)

I do not use chromium much, would add any tips anyone sends my way.

---

### Post by tlu on 2012-01-08
> **bodhi.zazen said:**
> Chrome / Chromium is fairly secure under the hood.

I have a few tips here

[http://bodhizazen.net/Tutorials/Privacy#Chrome](http://bodhizazen.net/Tutorials/Privacy#Chrome)

I do not use chromium much, would add any tips anyone sends my way.

2 suggestions:

Replace NotScripts with ScriptNo which is much better.
[Enable Click-to-play]("http://www.howtogeek.com/58058/how-to-enable-flashblock-in-chrome-and-make-it-5000-more-secure/") in order to control flash and other plugins.

---

