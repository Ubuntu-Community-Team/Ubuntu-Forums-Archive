---
title: "Removing Linkbucks-whatever from Ubuntu"
date: 2014-04-06
forum: Security
---

### Post by barjaktar on 2014-04-06
Hello.

I am using a 64 bit Ubuntu 12.04 and up-to-date versions of Firefox and Chromium. 

Couple of days ago some webpages went crazy. But, ok, that kind of stuff happens. Neverheless, I am unable to open certain for two days or so. Now I am getting suspicious. When I search something on Google or anywhere else, I get normal results. But when I try to open one of the offered links - Firefox takes me to a blank page. Literally - blank page, just white. Nothing happens, no error messages, just white. Now, yesterday and today it happens even for the big guys - Wikipedia and so. 

Last night I started looking for a solution. Then - a new moment. When I would click a link (not all of them, only some) it would take me to some Linkbucks thing and offer me to Download something. If I try to leave, it asks me to Stay on Page and so on. It's really annoying - This morning my deadline on Coursera passed - I couldn't do my assignments the whole week!

Now, I see that this is not an isolated issue, there are many cases, but - almost all of them on Windows... I couldn't find much help for Ubuntu. So I tried what is already said there. Reset the PC, reset Firefox, actual reset of Firefox to default settings, unninstall Firefox, reinstall Firefox, disabled all the extensions, disabled all the plugins, deleted history, cookies and everything else - zip, nada, zero, nothing - it still takes me to Linkbucks... I restarted my network adapter, my network service, deleted all the stuff from /etc/hosts except for localhost - nothing but Linkbucks.

What is said for Firefox - is the same for Chromium.

Please, could you try to help me here. Thank you for your time.

Regards.

---

### Post by bapoumba on 2014-04-06
Please check for any extension that may be present and try making new users on both browsers :
Chromium : [https://support.google.com/chrome/answer/142059?hl=en](https://support.google.com/chrome/answer/142059?hl=en)
Firefox : [https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles](https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles)

---

### Post by barjaktar on 2014-04-07
Bapoumba, thank you for your time.

I have done so: I have deleted and created a new profile. Also, I have disabled all of the available add-ons and extensions. Unfortunately, the problem persists. Here are several screenshots to paint my situation.

The only new thing I have noticed is that Firefox acts differently when I search via Google and via Bing. When I search on Google, it gives me back results, but when I click on any of them - I get white (as previously described). When I use Bing and click on some of the results - it takes me to some of the pages: say, if the result is a Wikipedia search, or this forum - it will do it; but for others it will giv me Linkbucks; for some (codeskulptor.org) it will give me white - just like with Google.

Please do help me guys if you can, because this is now making me serious problems - it's making me problems on my job.

Thank you very much for your time and effort.

---

### Post by barjaktar on 2014-04-07
Unfortunately, I forgot to attach the screenshots - here they are.

---

### Post by 23dornot23d on 2014-04-07
First thing I would do is move the old configuration and settings file out of the way so its
not being used .......... so move .mozilla its in the users directory ~/ .



.mozilla folder out of the way to something like .mozilla-old

**cd**
**mv .mozilla .mozilla-old**

Then start Firefox ......... 

What will happen then is Mozilla will create a fresh one ..........

See if the same things start to happen again ....... but you will be initializing it so history passwords everything will no longer be there
you will have to start over again when loging into things on the web.

Hopefully that will be enough to clear it .......

---

### Post by bapoumba on 2014-04-07
Have you tried removing your startup page ?
[http://ubuntuforums.org/showthread.php?t=2137401](http://ubuntuforums.org/showthread.php?t=2137401)

---

### Post by barjaktar on 2014-04-07
Thank you both for your time.

Nevertheless, the problem persists. Yes, I have seen that thread and tried to as listed - changing my webpage did not solve the problem. Also, deleting .mozilla/ did not do the trick. I still have the same issues when trying to use my browser (different for Bing and Google).

Looking forward to your further assitance.

Regards.

---

### Post by bapoumba on 2014-04-07
[http://ubuntuforums.org/showthread.php?t=2212306](http://ubuntuforums.org/showthread.php?t=2212306)

Please have a look at your DNS. Looks like this thing redirects your browser queries.

Edit : not for your specific issue, but that is the idea [http://ubuntuforums.org/showthread.php?t=1604649&p=10343326#post10343326](http://ubuntuforums.org/showthread.php?t=1604649&p=10343326#post10343326)

---

### Post by barjaktar on 2014-04-10
Hello, sorry for the late reply, I wasn't home for a while.

Anyway, my /etc/resolv.conf contains only the following line

nameserver 127.0.0.1

When I checked my network, there was a strange thing about DNS setting. I use a router which goes over to my ISP. I have no idea what the router does when talking to the ISP. My PC used to have DHCP running until now, and it was showing me:
ip: 192.168.0.102
gateway: 192.168.0.1
dns: 192.168.10.1 192.168.0.1

I have no ide what the hell is 192.168.10.1, so I switched to manual IPv4 configuration, thus forcing the DNS to be 192.168.0.1 - the same like gateway, i.e. my router here.

And still - I have everything the same. Google links don't work at all, Bing links sometiems do, sometimes take me to Linkbucks sites...

What else can I do about the DNS?

Thank you for your time and effort.

---

### Post by bapoumba on 2014-04-10
I've been including Windows systems to my searches as I've sort of run out of ideas from searches on Linux.
Couple things :

Search engines :
Chromium > Settings Search > Manage search engines. I have Google, Yahoo, Bing and DuckDuckgo. Please remove any other ones
Firefox > Search engine icon > Manage search engines > Same as above.

Proxy :
Look for any proxy in the browsers and network configuration. Remove it if you are not using a proxy.

Router :
I've seen some posts related to a router infection (:confused:). Could you test with another computer ? I've never seen that suggested, but could give it a shot.

---

### Post by barjaktar on 2014-04-11
Hello.

Thank you very much for your effort.

Unfortunately, the thing with search engines I did already - it does not help.

Proxy settings are "No Proxy".

The router is not the problem, because there are several smartphones that use the same router on everyday basis - and they all successfully connect to websites of interest (Google and Codeskulptor, for example).

This question sounds quite stupid, but since we are running out of options... is there any other, "secret" - "only root", way of setting network data? Could there be some little file somewhere telling my browser to go somewhere else?

Regards.

---

### Post by bapoumba on 2014-04-11
Well, this is not something I have ever recommended. Have you considered reinstalling ? Backup your personal files, I would reformat the root partition and the home folder if you set it up on a different partition. I've kind of run out of ideas..
There may be some root system files installed. Not sure how to get at them.

---

### Post by barjaktar on 2014-04-11
Thank you for your time.

How about some malware-virus-recognition tool for ubuntu or something like that? Do these things work?

As far as reinstalling is concerned, sure, but I would refrain from that if possible.

On this machine I have a dual boot of Windows 7 (guilty as charged, but I really do enjoy sitting on the frozen throne occasionally), which I don't use that much. But it just occured me to check that as well. It's pretty much the same thing. Even that strange DNS appeared on Windows. So I went in and pinged the damn address - hell, it didn't just ping back! When I typed the address of it in my Firefox bar, I got a login screen of a router - which is not mine! Somehow somebody is in my network with his router... some kind of wireless interconnect or something... 

I'll get back with more info, when I've explored this further.

Regards.

---

### Post by bapoumba on 2014-04-11
Well, I found some Firefox addons that were supposed to remove the linkbucks redirects but I have not tested them. 
Here is a link to the French ubuntu forum, from a user who developed an addon that is supposed to be working :
[http://forum.ubuntu-fr.org/viewtopic.php?id=628591](http://forum.ubuntu-fr.org/viewtopic.php?id=628591)
Link : [https://addons.mozilla.org/fr/firefox/addon/anti-linkbucks/](https://addons.mozilla.org/fr/firefox/addon/anti-linkbucks/)

I know that reinstalling is only a last resort option, that I have never (as far as I remember) recommended. But I'm not sure where to look now.

---

### Post by bapoumba on 2014-04-11
> **barjaktar said:**
> Thank you for your time.

How about some malware-virus-recognition tool for ubuntu or something like that? Do these things work?

As far as reinstalling is concerned, sure, but I would refrain from that if possible.

On this machine I have a dual boot of Windows 7 (guilty as charged, but I really do enjoy sitting on the frozen throne occasionally), which I don't use that much. But it just occured me to check that as well. It's pretty much the same thing. Even that strange DNS appeared on Windows. So I went in and pinged the damn address - hell, it didn't just ping back! When I typed the address of it in my Firefox bar, I got a login screen of a router - which is not mine! Somehow somebody is in my network with his router... some kind of wireless interconnect or something... 

I'll get back with more info, when I've explored this further.

Regards.

Sorry to bump, but that is something.
I was kinda stuck on the smartphones that may be do not use the same protocols than computers, or at least the same browser features.

Now, when did you first notice the Linkbucks redirects ? From Ubuntu or from Windows ?
Unless I am completely off tracks, I do not believe there is anything in common between the two, but your router. I'm not sure I could imagine corruption at the bios or boot loader level, but I may be wrong.

Edit : are you able to connect the computer to internet via a smartphone using 3G (disable wifi on the device) ?
Edit2 : there are many utilities that are supposed to clean that stuff for windows

---

### Post by mgmiller on 2014-04-27
Your DNS settings are definitely wrong. They should not start with 192.  I don't know who your service provider is, so I can't tell you what their "native" DNS servers are.  

I use Optimum Online and my DNS servers are 167.206.254.1, 167.206.254.2.   

You can try using the official Google DNS servers, they are 8.8.8.8, 8.8.4.4.  

In Ubuntu, click the network icon in the top panel, select your connection and click Edit.  on the IPv4 tab, change the DNS servers to your ISP's servers, or try the Google ones.  Click save and you should be good to go.  You may need to log off and on again to really make it change.

You can also change the DNS settings in your router to match the above.  That will make everything on your network use the new DNS settings.

Here is a link to the Google DNS page, where you can learn more about DNS:
[https://developers.google.com/speed/public-dns/](https://developers.google.com/speed/public-dns/)

---

### Post by maglin2 on 2014-04-27
+1 to the above.

192.168.0.1 is not a DNS address - it is the IP of most D Link and Netgear Routers.

---

