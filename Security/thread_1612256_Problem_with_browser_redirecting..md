---
title: "Problem with browser redirecting."
date: 2010-11-02
forum: Security
---

### Post by tataraperz on 2010-11-02
Hi,

Okay, i've been getting this problem for like 2 weeks now.

Every now and then, when im surfing the internet, no matter what site it is, it redirects me to friggin stupid adds site, mainly one named fileinxt.com or something like that.

It started happening to me since i installed ubuntu 10.10 and im using google chrome.

It's pretty annoying, and to say one of the main reasons for me to come to linux is "virus-free".


Searching google i found some solutions for windows but i don't know how to translate them to ubuntu.

It happens even when a page is fully loaded and it's been sitting there for a while.

[http://img442.imageshack.us/i/pantallazodf.png](http://img442.imageshack.us/i/pantallazodf.png)

---

### Post by Decatf on 2010-11-02
What are you running or have installed that has come from third party sources (stuff from the web, PPAs, etc)?

If it's not some malicious code in your general system somewhere it could be in Chrome itself. You could try uninstalling it and removing all the remaining files/directories. It stores user specific data in ~/.config/google-chrome

---

### Post by tataraperz on 2010-11-02
Nothing besides the battery-status indicator from a PPA, but i've had that one since i had ubuntu 10.04.

I have the very same software i had with 10.04, which i used for like 4 months. Even the same chrome extensions.

---

### Post by mutex023 on 2010-11-02
If there is a .chrome or .google-chrome or .google directory in your home directory, delete them and then try using chrome. You have to do a View > Hidden Files in nautilus before you can see these hidden folders.

---

### Post by mikewhatever on 2010-11-02
Press shift+ctrl+del, and delete everything except passwords. Make sure you select 'Everything' in the time period box. Just to mention, site redirection usually have nothing to do with viruses.

---

### Post by tgm4883 on 2010-11-02
Nobody that knows what they are talking about says Linux is virus free. Everything has the ability to have a threat installed, most are done though some sort of social engineering.

Browser redirects are easily done though dns/proxy. What are you using for DNS? Any proxy servers in the environment? How do you access the internet? Do any other computers on your network have this issue?

---

### Post by uRock on 2010-11-02
It isn't a virus.

Moved to Security Discussions.

---

### Post by tgm4883 on 2010-11-02
> **mikewhatever said:**
> Press shift+ctrl+del, and delete everything except passwords. Make sure you select 'Everything' in the time period box. Just to mention, site redirection usually have nothing to do with viruses.

Actually, yea they do. I see it all the time.

---

### Post by tgm4883 on 2010-11-02
> **uRock said:**
> It isn't a virus.

Is that based on some profound information that I don't see from the user?

---

### Post by mikewhatever on 2010-11-02
> **tgm4883 said:**
> Actually, yea they do. I see it all the time.

Example?

---

### Post by tataraperz on 2010-11-02
So i guess i'm lying with the virus thing, thread name changed...wow.. i can't see how pages changing to other thing while not even using them and they're loaded isn't a virus, this is like the old windows times when you could get like 100+ pop ups but worse, because now my work on any site just gets trashed when it redirects me


well whatever, i deleted a google-chrome folder in .cache but besides that couldnt find anything with find within *google* or *chrome*

I've deleted ALL data from google chrome with shift+ctrl+del, in fact i do it all the time.

---

### Post by tgm4883 on 2010-11-02
> **mikewhatever said:**
> Example?

There are lots of threats that either alter the hosts file to redirect traffic of certain domains (simple) or create a proxy server that will redirect traffic (more sophisticated). 

An example of this would be [Backdoor.Tidserv]("http://www.symantec.com/security_response/writeup.jsp?docid=2008-091809-0911-99&tabid=2")
> The threat will constantly monitor the user's browser activity. It may watch for URLs requested that contain strings for many popular search engines including:
google.com
yahoo.com
bing.com
live.com
ask.com
aol.com
google-analytics.com
yimg.com
When it identifies such a URL, it will try to extract the parameters from the URL such as "q=" or "query=". In addition it will also either block or redirect the HTTP request.

---

### Post by uRock on 2010-11-02
Have you tried clearing firefox's history? 

If not, then open Firefox, click on Tools, then click Clear Recent History, then select Everything from the drop down.

---

### Post by uRock on 2010-11-02
> **tgm4883 said:**
> There are lots of threats that either alter the hosts file to redirect traffic of certain domains (simple) or create a proxy server that will redirect traffic (more sophisticated). 

An example of this would be [Backdoor.Tidserv]("http://www.symantec.com/security_response/writeup.jsp?docid=2008-091809-0911-99&tabid=2")
Can you give us an example of a Linux virus that has this result?

---

### Post by tataraperz on 2010-11-03
> **uRock said:**
> Can you give us an example of a Linux virus that has this result?

I didn't find anything, but this cleary resembles a windows virus, heck, even being redirected to the same page(fileinxt.com) that the windows version:

[http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=652556&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=652556&forumId=1)
[http://www.neowin.net/forum/topic/928398-solution-firefox-fileinxtcom-google-redirection/](http://www.neowin.net/forum/topic/928398-solution-firefox-fileinxtcom-google-redirection/)

[jokemode]
I know how much you love and workship linux but this is cleary a problem, first step into curing a psychological disorder is accepting the problem[/jokemode]

---

### Post by tgm4883 on 2010-11-03
> **uRock said:**
> Can you give us an example of a Linux virus that has this result?

Now that reply was to the user that said that browser redirects had nothing to do with threats. I gave an example of one (which there are many more) that did just that. I did a quick search for a Linux one, however didn't find one in my 5 minutes of searching. That isn't to say one doesn't exist, as I could see how it could easily happen. 

This was as close as I came in my 5 minutes of searching.
[http://tidystorm.com/423/the-redirect-virus-was-in-my-router/](http://tidystorm.com/423/the-redirect-virus-was-in-my-router/)

My posts here are simply this. The phrase "Linux is virus free" is factually incorrect. Spreading this statement is a disservice to users. Is Linux prone to threats? No, Linux is more secure than windows. But the truth is that users are usually the biggest security hole in the system. Telling these users this statement is borderline negligent. We should be educating on good security practices.

---

### Post by uRock on 2010-11-03
> **tataraperz said:**
> I didn't find anything, but this cleary resembles a windows virus, heck, even being redirected to the same page(fileinxt.com) that the windows version:

[http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=652556&forumId=1](http://support.mozilla.com/tiki-view_forum_thread.php?comments_parentId=652556&forumId=1)
[http://www.neowin.net/forum/topic/928398-solution-firefox-fileinxtcom-google-redirection/](http://www.neowin.net/forum/topic/928398-solution-firefox-fileinxtcom-google-redirection/)

[jokemode]
I know how much you love and workship linux but this is cleary a problem, first step into curing a psychological disorder is accepting the problem[/jokemode]
Lol, Can you access your router to see what DNS it is set for? Usually your PC uses the same DNS addresses as the router, but it is possible for script on a site to change the DNS used by your system.

If your system is Wired, then this would be easy. Just open Network Manager by right-clicking the Networking Icon in the notification area, then select Edit Connections, then click Auto eth0 and delete it.
Do all of this after clearing your browser's cookies and such.
Once deleted, click Add in the Network Manager window, name it then click apply, if you have a router with DHCP or if you connect directly to the modem.
If you have to set it statically , then do so within the IPv4/IPv6 tabs. Then click Apply.

---

### Post by tataraperz on 2010-11-03
I did what you said even though my dns server was the same as the router's. Router's DNS servers are correct(the ones my ISP provides).

Im glad to see you now moved onto step #2, searching for the cause of the problem.

thanks pal! :D

---

### Post by lisati on 2010-11-03
It *might* be [malware]("http://lisati.homelinux.com/wiki/index.php/Malware"), but not necessarily a virus. It looks to me like *something* is messing with DNS resolution.

---

### Post by Ryan Dwyer on 2010-11-03
Please use Firefox for a bit and see if the same problem happens there.

Also try running the following from a terminal:
dig ubuntuforums.org
dig ubuntuforums.org
dig ubuntuforums.org
(and so on... see if the IP address changes)

Finally, edit /etc/resolv.conf and change the nameserver address to 8.8.8.8. That's a Google DNS server.

---

### Post by AlecJ on 2010-11-13
Had the same problem with Google searches being hijacked to ad-sites etc.

The DNS setting in the router were somehow changed? I know not how but they were set to 
213.109.64.50 ect which is somewhere in the Russian federation.

I use a D-Link router that has Advanced Dns Service, I enabled this.

Now the DNS is 204.194.232.200
Wow what a difference, so much faster with no redirections to ad-ware site, or new windows opening up with large animated male genitals!

---

### Post by tgm4883 on 2010-11-13
> **AlecJ said:**
> Had the same problem with Google searches being hijacked to ad-sites etc.

The DNS setting in the router were somehow changed? I know not how but they were set to 
213.109.64.50 ect which is somewhere in the Russian federation.

I use a D-Link router that has Advanced Dns Service, I enabled this.

Now the DNS is 204.194.232.200
Wow what a difference, so much faster with no redirections to ad-ware site, or new windows opening up with large animated male genitals!

Change the default password on your router

---

### Post by OpSecShellshock on 2010-11-13
> **tgm4883 said:**
> Change the default password on your router

Also make sure its administration page is not accessible from the open web.

---

### Post by laughlin.bill on 2010-12-12
I'm having what seems to be a similar problem and have managed to be able to isolate and reproduce the behavior.  

Using firefox, google-chrom or even wget, certain web addresses seem to automatically redirect me to advertising sites.  At first I thought it was an issue with my ISP's DNS servers (Telefonica, Spain) so I changed first to google's DNS servers (8.8.8.8, 8.8.4.4) through network manager, restarted the computer, same result.  I also tried opendns.com servers and had some weird "too many redirects" errors or random pages resolving to "guide.opendns.com"

I then ran a live-cd (usb-stick) version of Ubuntu 10.04, and surprisingly I did NOT get the same erroneous result with firefox or wget: everything worked just fine.  I also do not get the result when I run firefox through TOR with the TOR plugin.

Incidentally - if I use "dig" to resolve the non-functioning addresses, it works fine.  If I use "ping" to resolve the non-functioning addresses, it resolves improperly.  Interestingly, it only happens to CERTAIN addresses that resolve to the same IP:

This one works fine:

~$ dig www.chicagosuntimes.com
; <<>> DiG 9.7.0-P1 <<>> www.chicagosuntimes.com
;; ANSWER SECTION:
www.chicagosuntimes.com. 79833	IN	CNAME	www.suntimes.com.
www.suntimes.com.	2836	IN	A	70.42.43.214


~$ ping www.chicagosuntimes.com
PING www.suntimes.com (70.42.43.214) 56(84) bytes of data.

This one is broken:

~$ dig www.suntimes.com
; <<>> DiG 9.7.0-P1 <<>> www.suntimes.com
;; ANSWER SECTION:
www.suntimes.com.	789	IN	A	70.42.43.214

~$ ping www.suntimes.com
PING www.suntimes.com (74.54.152.70) 56(84) bytes of data.


So I seem to have isolated it to a DNS resolution issue on my machine. It's as if there is some piece of malware in the middle between my requests and the DNS response that switches out the correct IP resolution for the wrong one.  

Any suggestions?

---

### Post by cariboo on 2010-12-12
Have you created new browser profiles?

---

### Post by laughlin.bill on 2010-12-13
I have completely removed google-chrome and have created a new profile in firefox.  As I mentioned, this also happens ONLY on my machine, which could indicate a browser profile issue, but it also happens  with wget which doesn't use browser profiles, so it shouldn't be related.

---

### Post by laughlin.bill on 2010-12-13
I believe I have finally isolated the issue.  Awhile back I had modified the /etc/nsswitch.conf file to "accomodate" windows networking by adding "wins" as the first entry in hosts.  After running strace on my ping command, I noticed some weird references to some samba directories.   I tested by turning some things on/off until it occurred to me that the wins feature of samba has some caching features.  By removing the wins element from the hosts line, I work-around whatever problem wins or samba has.

Anyway, the nsswitch.conf file now reads as follows and everything is working just fine:

```
# /etc/nsswitch.conf
passwd:         compat
group:          compat
shadow:         compat
hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files
protocols:      db files
services:       db files
ethers:         db files
rpc:            db files
netgroup:       nis

```

Hope this helps someone!

---

