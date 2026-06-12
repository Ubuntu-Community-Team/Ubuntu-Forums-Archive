---
title: "adblock host recommendations?"
date: 2010-06-27
forum: Security
---

### Post by jdunn on 2010-06-27
I'm looking for a reputable, frequently updated ad-site list for my hosts file.  I want to try it out for adblocking.

---

### Post by yeleek on 2010-06-28
Is this for a web browser?  Firefox?  If so why not use AdBlock which contains its own updated adblock list.

Actually - just had a look at the preferences - this is the list.  Any help?
[https://easylist-downloads.adblockplus.org/easylist.txt](https://easylist-downloads.adblockplus.org/easylist.txt)

---

### Post by jdunn on 2010-06-28
> Is this for a web browser? Firefox? If so why not use AdBlock which contains its own updated adblock list

I use more than one browser.  Chrome is my primary browser, although I occasionally use Firefox too.  Unfortunately, Chrome only hides ads with the use of its own "ad-blocking" extensions.  In other words, ads won't be visible but the ad-sites still load and could contain trackers, malware, etc.  This is an intentional limitation of Chrome/Chromium because Google depends on advertising.

It doesn't appear that Easylist posts hostfiles.  They just have an ad-ware database for browser adblocking extensions.  This serves the same purpose of adblocking but contains different info and format than hostfiles.

I've looked into other options already:  Privoxy, SRWare Iron, OpenDNS (is limited to 25-50 blocks), etc. so I'm giving host files a try.  I already found one (reputable?) site [http://www.mvps.org/winhelp2002/hosts.htm]("http://www.mvps.org/winhelp2002/hosts.htm").  I'd like to know if anyone can recommend one.

---

### Post by dino99 on 2010-06-28
look about ipblock, and add the list(s) you want (very helpfull)

actually mine deals with more than 2 780 000 000 ips !!!!

---

### Post by bodhi.zazen on 2010-06-28
> **jdunn said:**
> I use more than one browser.  Chrome is my primary browser, although I occasionally use Firefox too.  Unfortunately, Chrome only hides ads with the use of its own "ad-blocking" extensions.  In other words, ads won't be visible but the ad-sites still load and could contain trackers, malware, etc.  This is an intentional limitation of Chrome/Chromium because Google depends on advertising.

It doesn't appear that Easylist posts hostfiles.  They just have an ad-ware database for browser adblocking extensions.  This serves the same purpose of adblocking but contains different info and format than hostfiles.

I've looked into other options already:  Privoxy, SRWare Iron, OpenDNS (is limited to 25-50 blocks), etc. so I'm giving host files a try.  I already found one (reputable?) site [http://www.mvps.org/winhelp2002/hosts.htm](http://www.mvps.org/winhelp2002/hosts.htm).  I'd like to know if anyone can recommend one.

I suggest you use a proxy server.

Privoxy is easy to install and configure and works with all browsers.

You can either configure your browser to use privoxy , or write a few rules for iptables to re-direct traffic automatically.

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

The advantage of iptables, it works for all users and all browsers with minimal configuration.

The "problem" with using a hosts file, it is reactionary and you need to wait for someone else to update the list.

---

### Post by jdunn on 2010-06-28
> **bodhi.zazen said:**
> I suggest you use a proxy server.

Privoxy is easy to install and configure and works with all browsers.

You can either configure your browser to use privoxy , or write a few rules for iptables to re-direct traffic automatically.

[http://blog.bodhizazen.net/linux/how-to-transparent-proxy/](http://blog.bodhizazen.net/linux/how-to-transparent-proxy/)

The advantage of iptables, it works for all users and all browsers with minimal configuration.

The "problem" with using a hosts file, it is reactionary and you need to wait for someone else to update the list.

I've tried Privoxy recently.  The adblocking works well enough for me but it slows page loading down too noticeably.  Maybe it would work faster if cascaded with Squid, which I never tried, but having 1-2 proxy servers for just one computer seems like overkill anyway.

True, a hostfile list is reactionary but so is Easylist for adblocker extensions.  The guy who was in charge of it passed away last year and I hear recent updates have been infrequent.  My point is, I don't mind relying on someone else's efforts to compile a list, so long as its up-to-date and reliable.

I didn't think to try IPtables so I may look into it.  For now, I'm still trying out a hostlist.  The nice thing about the host list is it will work for both linux and Vista on my dual-boot laptop.  I neglected to mention I was dual-booting.

---

### Post by jdunn on 2010-06-28
> **dino99 said:**
> look about ipblock, and add the list(s) you want (very helpfull)

actually mine deals with more than 2 780 000 000 ips !!!!

Thanks, I'll look into this.

---

### Post by bodhi.zazen on 2010-06-29
> **jdunn said:**
> I've tried Privoxy recently.  The adblocking works well enough for me but it slows page loading down too noticeably.  Maybe it would work faster if cascaded with Squid, which I never tried, but having 1-2 proxy servers for just one computer seems like overkill anyway.

True, a hostfile list is reactionary but so is Easylist for adblocker extensions.  The guy who was in charge of it passed away last year and I hear recent updates have been infrequent.  My point is, I don't mind relying on someone else's efforts to compile a list, so long as its up-to-date and reliable.

I didn't think to try IPtables so I may look into it.  For now, I'm still trying out a hostlist.  The nice thing about the host list is it will work for both linux and Vista on my dual-boot laptop.  I neglected to mention I was dual-booting.
  
Adblock is fantastic with Privoxy, I have been using Privoxy for some time now ...

I have not noticed a slow down with Privoxy, you can improve performance with a few tweaks :

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

It is written for ssh, but all the same, at the bottom are some tips ...

If you insist ....

IMO a decent hosts file is here :

[http://hostsfile.mine.nu/downloads/](http://hostsfile.mine.nu/downloads/)

---

### Post by mikewhatever on 2010-06-29
> **dino99 said:**
> look about ipblock, and add the list(s) you want (very helpfull)

actually mine deals with more than 2 780 000 000 ips !!!!

Well, that's more then half of all possible ipv4 addresses, likely an overkill for.

---

### Post by jdunn on 2010-06-30
> **bodhi.zazen said:**
> Adblock is fantastic with Privoxy, I have been using Privoxy for some time now ...

I have not noticed a slow down with Privoxy, you can improve performance with a few tweaks :

[https://calomel.org/firefox_ssh_proxy.html](https://calomel.org/firefox_ssh_proxy.html)

It is written for ssh, but all the same, at the bottom are some tips ...

If you insist ....

IMO a decent hosts file is here :

[http://hostsfile.mine.nu/downloads/](http://hostsfile.mine.nu/downloads/)

I wouldn't recommend Privoxy to anyone except as a last resort.  At times, it doesn't affect page loading times.  At other times, it slows to a crawl.  It seems to have the worst impact on webmail and search engine results.  Too often, I have to refresh search results because only half-a-page is displayed.  And the time I have to wait to load an individual email hearkens back to when I had to use a 56Kbaud modem.  These are the results with the basic settings...I haven't even tweaked it yet and of course, it only does a fair job of adblocking with basic settings.  Keep in mind that most of my experience is with the version in the repositories (3.0.15) but I doubt 3.0.16 is much better.

---

### Post by bodhi.zazen on 2010-06-30
> **jdunn said:**
> I wouldn't recommend Privoxy to anyone except as a last resort.  At times, it doesn't affect page loading times.  At other times, it slows to a crawl.  It seems to have the worst impact on webmail and search engine results.  Too often, I have to refresh search results because only half-a-page is displayed.  And the time I have to wait to load an individual email hearkens back to when I had to use a 56Kbaud modem.  These are the results with the basic settings...I haven't even tweaked it yet and of course, it only does a fair job of adblocking with basic settings.  Keep in mind that most of my experience is with the version in the repositories (3.0.15) but I doubt 3.0.16 is much better.

I have not had that experience with privoxy, neither wish slow connections nor do I have any complaints with adblocking.

Good luck with your hosts file.

---

### Post by jdunn on 2010-07-28
> **bodhi.zazen said:**
> I have not had that experience with privoxy, neither wish slow connections nor do I have any complaints with adblocking

Try privoxy default settings with Google Chrome.  Privoxy on Chrome affects the search results on Google and other search engines but I had no problems with Firefox.  Same is true for webmail on Chrome.

---

### Post by wacky_sung on 2010-07-29
> **bodhi.zazen said:**
> I have not had that experience with privoxy, neither wish slow connections nor do I have any complaints with adblocking.

Good luck with your hosts file.

Why is there a need to use privoxy just for adblocking?It will then accumulated cookies and used up unwanted space.Beside that,how effective is it?Is that a good to have item / necessary?

---

### Post by unspawn on 2010-07-29
> **wacky_sung said:**
> Why is there a need to use privoxy (..) how effective is it
For filtering in a system-wide context and in a browser independent way you'd use a proxy. 
Blacklisting sites using null routes or /etc/hosts are deprecated methods: they're not future-proof, they're inefficient, incomplete and circumventable. 
Performing a few simple tasks will show. How you would do this or block these *in a browser independent way* using your /etc/hosts file:
- update your blocklist on the fly,
- block ad-tracking cookies (FF users also see ghostery.com),
- allow cookies you send not to be modified,
- block ads residing in a path on the same server you visit,
- block ads from a hostname of which the domainname is the same as the server you visit,
- block ads deployed using a CDN,
- block ads shown through via Javascript or Flash,
- filter out Javascript annoyances for specific sites only,
- block ads by host or path using regular expressions,
- de-animate gifs, kill popups and block only webbugs,
- set session-only cookies for a range of sites,
- selectively block popups, refresh-tags and redirects,
- disable or transform page elements,
- keep images with specific sizes from displaying,
- filter out visiting domains based on page content,
- allow [www.site](www.site) but block adtracker.site,
- allow site:80 but block site:443?
* No need to try. The above can't be done using /etc/hosts alone.


> **jdunn said:**
> I wouldn't recommend Privoxy to anyone (..) I haven't even tweaked it (..) it only does a fair job of adblocking
With all due respect but I wonder if dismissing Privoxy, having used it without adapting rulesets to the situation (just like running any tool without necessary knowledge or adjustments) makes any sense at all...

---

### Post by wacky_sung on 2010-07-29
> **unspawn said:**
> For filtering in a system-wide context and in a browser independent way you'd use a proxy. 
Blacklisting sites using null routes or /etc/hosts are deprecated methods: they're not future-proof, they're inefficient, incomplete and circumventable. 
Performing a few simple tasks will show. How you would do this or block these *in a browser independent way* using your /etc/hosts file:
- update your blocklist on the fly,
- block ad-tracking cookies (FF users also see ghostery.com),
- allow cookies you send not to be modified,
- block ads residing in a path on the same server you visit,
- block ads from a hostname of which the domainname is the same as the server you visit,
- block ads deployed using a CDN,
- block ads shown through via Javascript or Flash,
- filter out Javascript annoyances for specific sites only,
- block ads by host or path using regular expressions,
- de-animate gifs, kill popups and block only webbugs,
- set session-only cookies for a range of sites,
- selectively block popups, refresh-tags and redirects,
- disable or transform page elements,
- keep images with specific sizes from displaying,
- filter out visiting domains based on page content,
- allow [www.site](www.site) but block adtracker.site,
- allow site:80 but block site:443?
* No need to try. The above can't be done using /etc/hosts alone.


This sound good to me but i will install it and verify it myself.Thank for the clarification.The most vital features in which i seek after is allowed cookies you send not to be modified which usually used for MTM(Man in The Middle) attack.

---

### Post by wacky_sung on 2010-07-29
> **jdunn said:**
> I wouldn't recommend Privoxy to anyone except as a last resort.  At times, it doesn't affect page loading times.  At other times, it slows to a crawl.  It seems to have the worst impact on webmail and search engine results.  Too often, I have to refresh search results because only half-a-page is displayed.  And the time I have to wait to load an individual email hearkens back to when I had to use a 56Kbaud modem.  These are the results with the basic settings...I haven't even tweaked it yet and of course, it only does a fair job of adblocking with basic settings.  Keep in mind that most of my experience is with the version in the repositories (3.0.15) but I doubt 3.0.16 is much better.

I have just installed **Privoxy** and this is my first time using it.It does not show any significance slow down in my browsing speed and it work great except for some some sites in which i have to use firefox to work without it otherwise i cannot access to the site i wanted,

Currently i am using Firefox to work without Privoxy and use Google Chrome to run with it.

Example Application game in which i cannot get it loaded properly in facebook.com.Therefore i have disable Privoxy in Firefox to get to the problem site as below.

[[IMG]http://img148.imageshack.us/img148/6901/screenshotkingdomsofcam.th.png[/IMG]](http://img148.imageshack.us/i/screenshotkingdomsofcam.png/)

I faces some minor problem and edit the keep alive timeout = 0.Then everything work fine now in which i using it in my Google Chrome.

[[IMG]http://img96.imageshack.us/img96/4810/screenshot502noserveror.th.png[/IMG]](http://img96.imageshack.us/i/screenshot502noserveror.png/)

Thank bodhi for your tutorial in which work great for me and introduced something new to me.

[http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/](http://blog.bodhizazen.net/linux/web-content-filtering-made-easy/)

---

### Post by wacky_sung on 2010-07-29
Currently i am using 3.15 beta version.How can i get to install to the latest stable version 3.16.There do not seem to have any repository on it except from source.Much appreciated if any help can offer.Thank.

---

### Post by bodhi.zazen on 2010-07-29
> **wacky_sung said:**
> Currently i am using 3.15 beta version.How can i get to install to the latest stable version 3.16.There do not seem to have any repository on it except from source.Much appreciated if any help can offer.Thank.

Personally , unless there is a problem, I would stay with the version in the Ubuntu repository.

In terms of using Privoxy, it takes a little effort to learn the rules for configuration, but it is not as difficult at the documentation makes it seem (honest).

Take a look at the web interface. Open a browser and type [http://p.p/](http://p.p/) (p.p for short).

[http://www.privoxy.org/user-manual/configuration.html](http://www.privoxy.org/user-manual/configuration.html)

Privoxy can be configured to white list web sites and, if you wish, crunch cookies.

I had to white list a few sited my children use (webkinz), but you can still block ads (I think it was ads.webkinz).

The biggest problem yo umight have is if you are too aggressive with the settings, you may break some web sites. In that event, white list them.

The default settings are nice, you can test them with any "proxy judge" , although you need to connect directly to test (otherwise the proxy judge may see your router).

---

### Post by wacky_sung on 2010-07-29
> **bodhi.zazen said:**
> Personally , unless there is a problem, I would stay with the version in the Ubuntu repository.

In terms of using Privoxy, it takes a little effort to learn the rules for configuration, but it is not as difficult at the documentation makes it seem (honest).

Take a look at the web interface. Open a browser and type [http://p.p/](http://p.p/) (p.p for short).

[http://www.privoxy.org/user-manual/configuration.html](http://www.privoxy.org/user-manual/configuration.html)

Privoxy can be configured to white list web sites and, if you wish, crunch cookies.

I had to white list a few sited my children use (webkinz), but you can still block ads (I think it was ads.webkinz).

The biggest problem yo umight have is if you are too aggressive with the settings, you may break some web sites. In that event, white list them.

The default settings are nice, you can test them with any "proxy judge" , although you need to connect directly to test (otherwise the proxy judge may see your router).

I have tried using add my trust link to in the trust file but it keep failing(unable to bypass the filter)

```
Link i want to use : http://apps.facebook.com/kingdomsofcamelot/?ref=games_my_recent&fa=1

File to edit : /etc/privoxy/trust
Add to trust : ~apps.facebook.com
             : ~facebook.com
             : ~apps.facebook.com/kingdomsofcamelot/?  
                ref=games_my_recent&fa=1

&

File to edit : /etc/privoxy/user.action
Add : { fragile }
      .apps.facebook.com
    : { allow-ads }
      .apps.facebook.com

```

The best solution is use alternative browser without Privoxy.

---

### Post by bodhi.zazen on 2010-07-30
> **wacky_sung said:**
> I have tried using add my trust link to in the trust file but it keep failing(unable to bypass the filter)

```
Link i want to use : http://apps.facebook.com/kingdomsofcamelot/?ref=games_my_recent&fa=1

File to edit : /etc/privoxy/trust
Add to trust : ~apps.facebook.com
             : ~facebook.com
             : ~apps.facebook.com/kingdomsofcamelot/?  
                ref=games_my_recent&fa=1

&

File to edit : /etc/privoxy/user.action
Add : { fragile }
      .apps.facebook.com
    : { allow-ads }
      .apps.facebook.com

```The best solution is use alternative browser without Privoxy.

First, for a trust file, you need to uncoment the appropriate line in the privoxy configuration file.

Second, if your site is still blocked, that indicates you are too strict with your rules.

Use + and wildcards, get the page working, then decide where you can tighten up.

---

### Post by wacky_sung on 2010-07-30
> **bodhi.zazen said:**
> First, for a trust file, you need to uncoment the appropriate line in the privoxy configuration file.

Second, if your site is still blocked, that indicates you are too strict with your rules.

Use + and wildcards, get the page working, then decide where you can tighten up.

Can show me which line to uncomment it in the trust file.I also used the example, +facebook.com but it still cannot worked.


Beside that,everything is default which mean i didn't even add or remove anything in the filter / rules.

---

### Post by bodhi.zazen on 2010-07-30
> **wacky_sung said:**
> Can show me which line to uncomment it in the trust file.I also used the example, +facebook.com but it still cannot worked.


Beside that,everything is default which mean i didn't even add or remove anything in the filter / rules.

Use your editors earch function , search trust or trustfile.

---

### Post by wacky_sung on 2010-07-30
> **bodhi.zazen said:**
> Use your editors earch function , search trust or trustfile.

In fact,i did edit using gedit in the terminal and saved it.The issue is that it still not working.

File to edit : /etc/privoxy/trust
[[IMG]http://img72.imageshack.us/img72/6628/screenshottrustetcprivo.th.png[/IMG]](http://img72.imageshack.us/i/screenshottrustetcprivo.png/)

File to edit : etc/privoxy/config
Comment : i have removed the # but togather with the trust file but it still not working.
[[IMG]http://img411.imageshack.us/img411/1159/screenshotconfigetcpriv.th.png[/IMG]](http://img411.imageshack.us/i/screenshotconfigetcpriv.png/)

Tell me what have i did wrong.Thank.

---

### Post by bodhi.zazen on 2010-07-30
> **wacky_sung said:**
> In fact,i did edit using gedit in the terminal and saved it.The issue is that it still not working.

File to edit : /etc/privoxy/trust
[[IMG]http://img72.imageshack.us/img72/6628/screenshottrustetcprivo.th.png[/IMG]]("http://img72.imageshack.us/i/screenshottrustetcprivo.png/")

File to edit : etc/privoxy/config
Comment : i have removed the # but togather with the trust file but it still not working.
[[IMG]http://img411.imageshack.us/img411/1159/screenshotconfigetcpriv.th.png[/IMG]]("http://img411.imageshack.us/i/screenshotconfigetcpriv.png/")

Tell me what have i did wrong.Thank.

After editing the files restart privoxy, clear your cache.

If it is not working, your rules are too strict, you need to be more permissive. You have not posted an updated set of rules, but your last rules were restrictive (you used ~ and a full url).

---

### Post by wacky_sung on 2010-07-30
> **bodhi.zazen said:**
> After editing the files restart privoxy, clear your cache.

If it is not working, your rules are too strict, you need to be more permissive. You have not posted an updated set of rules, but your last rules were restrictive (you used ~ and a full url).

I have uploaded all the rules / files which is default that i have not changed any for your review.Probably you can show me how to make it more permissive.


[http://www.filedropper.com/default_15](http://www.filedropper.com/default_15)
[http://www.filedropper.com/default_18](http://www.filedropper.com/default_18)
[http://www.filedropper.com/match-all](http://www.filedropper.com/match-all)

Beside that,what is the command to reload Privoxy.Thank.

---

### Post by bodhi.zazen on 2010-07-30
To restart privoxy:

```
sudo service privoxy restart
```I already gave you advice on your rules.

You are using ~ and a full url

~server.com/page/more_stuff/?php 

is very restrictive.

+server.com 

is less restrictive

+*.server.com

is less restrictive

See also something like this :

[http://feeding.cloud.geek.nz/2010/05/privoxy-rules-to-unblock-tvnz-on-demand.html](http://feeding.cloud.geek.nz/2010/05/privoxy-rules-to-unblock-tvnz-on-demand.html)

---

### Post by wacky_sung on 2010-07-31
Much appreciated for your help but none of it worked.I have tried for hours and still up to no avail editing the default / trust / matchall files.I give up unless there is a already a working file for me to review.

---

### Post by bodhi.zazen on 2010-07-31
> **wacky_sung said:**
> Much appreciated for your help but none of it worked.I have tried for hours and still up to no avail editing the default / trust / matchall files.I give up unless there is a already a working file for me to review.


I finally have some time to look at this.

This page : [http://apps.facebook.com/kingdomsofcamelot/?ref=games_my_recent&fa=1](http://apps.facebook.com/kingdomsofcamelot/?ref=games_my_recent&fa=1)

Loads for me with Privoxy with the default settings.

I did not need to enable the trust file or add any rule at all.

Since I do not have an account I can not log in ...

---

### Post by wacky_sung on 2010-08-01
Yeah you need to have a facebook account in order for you to verify it.The problem with it is that the loading will stop after the page in which you have seem it.

[[IMG]http://img148.imageshack.us/img148/6901/screenshotkingdomsofcam.th.png[/IMG]](http://img148.imageshack.us/i/screenshotkingdomsofcam.png/)

---

### Post by bodhi.zazen on 2010-08-01
I do not  have a facebook account.

Watch the information at the bottom of firefox and look to see what other site or url it is trying to load or google search privoxy + the page / site

---

### Post by PaulReaver on 2010-08-01
[[COLOR="RoyalBlue"]www.mvps.org/winhelp2002/hosts.htm[/COLOR]]("http://www.mvps.org/winhelp2002/hosts.htm")

mvps is quite good and regularly updated.

I use this one because I use many different web browsers.

Using a host file is better than using adblock+ on firefox in the same way linux is better than windows, it gives you more options.
Also good for banning whole websites like youtube, handy for when my relatives are visiting... lol, a bit harsh but mobile broadband is expensive.

 

I should really set up a cron job to fetch it for me instead of having to do it manually.  :confused:

---

### Post by wacky_sung on 2010-08-01
> **bodhi.zazen said:**
> I do not  have a facebook account.

Watch the information at the bottom of firefox and look to see what other site or url it is trying to load or google search privoxy + the page / site

Mainly i use facebook with only a few applications having the problem while the rest is okay.Apart from that,sometime the google search engines may not be able to display properly.I cannot say Privoxy work 100% for me but at least 95% of the sites which work well in default setting.

Thank PaulReaver for your recommendation but Privoxy indeed is a good proxy filter in which i like it inspite facing some problems with it.

---

### Post by bodhi.zazen on 2010-08-01
> **PaulReaver said:**
> [[COLOR=RoyalBlue]www.mvps.org/winhelp2002/hosts.htm[/COLOR]]("http://www.mvps.org/winhelp2002/hosts.htm")

mvps is quite good and regularly updated.

I use this one because I use many different web browsers.

Using a host file is better than using adblock+ on firefox in the same way linux is better than windows, it gives you more options.
Also good for banning whole websites like youtube, handy for when my relatives are visiting... lol, a bit harsh but mobile broadband is expensive.

 

I should really set up a cron job to fetch it for me instead of having to do it manually.  :confused:

Here is a link I used for a while :

[http://bodhizazen.net/adblock/adblock-0.98.sh](http://bodhizazen.net/adblock/adblock-0.98.sh)

You may use it as is or adapt it. It is well commented and will give instructions as to usage ;)

The main problem with a host file are :

1. Maintance of the list.
2. IMO it is slower then a proxy.

If you have more then one computer on a LAN it is much easier to configure a proxy.

IMO privoxy is the easiest to learn, you can look at squid and bfilter as alternatives.

It takes a little time to learn privoxy, but IMO less then squid. the basics of squid are easy, but, adding details or adblock is not so straight forward and does not work as well as provoxy.

The privoxy documentation is hare to understand at first, I highly suggest you use the web interface. The web interface is straight forward (most of the time).

> **wacky_sung said:**
> Mainly i use facebook with only a few applications having the problem while the rest is okay.Apart from that,sometime the google search engines may not be able to display properly.I cannot say Privoxy work 100% for me but at least 95% of the sites which work well in default setting.

Thank PaulReaver for your recommendation but Privoxy indeed is a good proxy filter in which i like it inspite facing some problems with it.

Here is a link to the config file I use for webkinz

[http://bodhizazen.net/adblock/privoxy.user.action.webkinz](http://bodhizazen.net/adblock/privoxy.user.action.webkinz)

look at the very bottom of the file, you will see I needed to add a few url. You get those url either by viewing the page source (+/- reliable) or watching firefox as it loads the page, you will see url flash in the lower right ...

HTH

---

### Post by dummy910 on 2010-08-01
> **PaulReaver said:**
> [[COLOR=RoyalBlue]www.mvps.org/winhelp2002/hosts.htm[/COLOR]]("http://www.mvps.org/winhelp2002/hosts.htm")

mvps is quite good and regularly updated.

I use this one because I use many different web browsers.

Using a host file is better than using adblock+ on firefox in the same way linux is better than windows, it gives you more options.
Also good for banning whole websites like youtube, handy for when my relatives are visiting... lol, a bit harsh but mobile broadband is expensive.

 

I should really set up a cron job to fetch it for me instead of having to do it manually.  :confused:
yep, this site offers one of the list's i've been placing on assorted operating system machines for years now. they usually update once a month or so thus the latest lists are quite large from all these years of updates.

it's amazing how much pollution accounts for what is the internet these days.

---

### Post by wacky_sung on 2010-08-02
> **bodhi.zazen said:**
> 

Here is a link to the config file I use for webkinz

[http://bodhizazen.net/adblock/privoxy.user.action.webkinz](http://bodhizazen.net/adblock/privoxy.user.action.webkinz)

look at the very bottom of the file, you will see I needed to add a few url. You get those url either by viewing the page source (+/- reliable) or watching firefox as it loads the page, you will see url flash in the lower right ...

HTH

Here is the file in which you have edit.

```
Edited file : /etc/privoxy/user.action
Added portion :
{ +block }
ads.webkinz.com
www.ads.webkinz.com

{ -block }
www.webkinz.com
mci2.webkinz.com
wapi11.webkinz.com
webkinz
webkinz.com
kinzpost.webkniz.com

```
What i did to allow my page to load properly.

```
Edited file : /etc/privoxy/user.action
Added portion :
{ fragile }
#.forbes.com
facebook.com
apps.facebook.com


# Here are some sites we wish to support, and we will allow their ads
# through.
#
{ allow-ads }
#.sourceforge.net
#.slashdot.org
#.osdn.net
facebook.com
apps.facebook.com

```

In additional : I have cleared the cache and restart the service.
Result : The page in which i requested still cannot be loaded.

URL : [http://apps.facebook.com/kingdomsofcamelot/?ref=games_my_recent&fa=1](http://apps.facebook.com/kingdomsofcamelot/?ref=games_my_recent&fa=1)

---

### Post by Magnetizer on 2013-01-10
Hi there,

you can also use the script I wrote to create a hostsfile from 11 different blacklists I found on the internet. You can add your own remote hostsfile and you can define your own blacklist and whitelist.

Once your hostsfile is updated you will be sent an e-mail with the changes.

The script can be found in another thread on this forum:

[http://ubuntuforums.org/showthread.php?t=2048812](http://ubuntuforums.org/showthread.php?t=2048812)

Have fun and keep it safe.

---

### Post by howefield on 2013-01-10
Old thread closed.

---

