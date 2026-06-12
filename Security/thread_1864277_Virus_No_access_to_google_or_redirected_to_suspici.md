---
title: "Virus? No access to google or redirected to suspicious sites"
date: 2011-10-18
forum: Security
---

### Post by mxndrwgrdnr on 2011-10-18
Was having this issue a few weeks ago, see [here]("http://ubuntuforums.org/showthread.php?t=1858069&highlight=rkhunter+google"). Though it was a rootkit but eventually ruled that out. Basically I was being redirected to questionable websites when trying to access google.com or gmail or using the addressbar to search in chromium. Either that or I would receive 404 errors. I've run ClamTK and haven't found anything, followed Dangertux's instructions in the thread linked above, but now I'm having the problem again. This time I'm being redirected to "b.aol.com" instead. I uninstalled chromium, now I'm just running straight up chrome in ubuntu 11.04. Seems to have solved the problem for the time being, I'm just worried that since the issue has come up again it might be something more serious. Any ideas???

---

### Post by Dangertux on 2011-10-18
> **mxndrwgrdnr said:**
> Was having this issue a few weeks ago, see [here]("http://ubuntuforums.org/showthread.php?t=1858069&highlight=rkhunter+google"). Though it was a rootkit but eventually ruled that out. Basically I was being redirected to questionable websites when trying to access google.com or gmail or using the addressbar to search in chromium. Either that or I would receive 404 errors. I've run ClamTK and haven't found anything, followed Dangertux's instructions in the thread linked above, but now I'm having the problem again. This time I'm being redirected to "b.aol.com" instead. I uninstalled chromium, now I'm just running straight up chrome in ubuntu 11.04. Seems to have solved the problem for the time being, I'm just worried that since the issue has come up again it might be something more serious. Any ideas???


Hi again, sorry to hear you are still having problems with this. 

Like I said in our previous discussion, it seems to be you have visited something that is hijacking your browser. 

It is unlikely that this is something more malign than that. However, if you are still concerned you can always start playing with the option of a reinstall. Consider also using an extension like NotScripts, while browsing.

Also make sure you are using the LATEST version of Chrome/Chromium. There have been several significant security updates over the past few weeks that may remedy your problem.

Hope this is helpful.

---

### Post by OpSecShellshock on 2011-10-18
Had you recently installed any extensions or web apps before this happened? Had the cached data been cleared recently? Are any other browsers affected? Is it just when using the search function, or does it also happen when the full URL is typed in?

These may end up being irrelevant questions now that you've switched browsers, I suppose.

---

### Post by collisionystm on 2011-10-18
> **mxndrwgrdnr said:**
> Was having this issue a few weeks ago, see [here]("http://ubuntuforums.org/showthread.php?t=1858069&highlight=rkhunter+google"). Though it was a rootkit but eventually ruled that out. Basically I was being redirected to questionable websites when trying to access google.com or gmail or using the addressbar to search in chromium. Either that or I would receive 404 errors. I've run ClamTK and haven't found anything, followed Dangertux's instructions in the thread linked above, but now I'm having the problem again. This time I'm being redirected to "b.aol.com" instead. I uninstalled chromium, now I'm just running straight up chrome in ubuntu 11.04. Seems to have solved the problem for the time being, I'm just worried that since the issue has come up again it might be something more serious. Any ideas???


As long as your /etc/hosts and /etc/resolv.conf look normal I would say It sounds like the default search provider in your browser was changed. No big deal. I see it all the time. Usually some program you installed or box that was clicked. 
Read this to reset it in Chrome
[http://www.google.com/support/chrome/bin/answer.py?answer=95426](http://www.google.com/support/chrome/bin/answer.py?answer=95426)

I see there was a suggestion for noscript. Good addon...

See this.. I know its from 2009, but it might still be current??

[http://hackademix.net/2009/12/10/why-chrome-has-no-noscript/](http://hackademix.net/2009/12/10/why-chrome-has-no-noscript/)

---

### Post by emiller12345 on 2011-10-18
Not sure if this helps, but I've noticed that my ISP has been playing funny games (sometimes) with DNS entries.  I prefer to use alternate DNS servers (from that of my ISP) like google or opendns.  you may consider looking into one of these to see if that helps.

The difference you may have experienced before is the difference in User Agents between the two browsers.

---

### Post by mxndrwgrdnr on 2011-10-18
@OpSecShellshock: yes to all of your questions, webapps/extensions recently installed, firefox was also affected, happened with address bar search as well as entering URL.

@collisionystm: everything looks normal from what i can tell

@emiller12345: can you elaborate on how to use alternate DNS servers?

thanks all

---

### Post by emiller12345 on 2011-10-18
> **mxndrwgrdnr said:**
> @emiller12345: can you elaborate on how to use alternate DNS servers?


If you wanted to use OpenDNS -> 
[http://www.opendns.com/home](http://www.opendns.com/home) >>  208.67.222.222    208.67.220.220

If you're using NetworkManager, which is the default in ubuntu, Right-Click on the NetworkManager Icon in the upper right-hand corner, go to "Edit Connections".

Depending whether you have a wired or wireless connection, click on what's appropriate. select your connection. select "Edit..."

You probably have an IPv4 connection so select "IPv4 Settings" 
Method >> "Automatic (DHCP) address only"
DNS Servers >> "208.67.222.222, 208.67.222.220"
Apply...

---

### Post by collisionystm on 2011-10-19
If you want to try an alternative DNS server

Use googles free DNS [http://code.google.com/speed/public-dns/](http://code.google.com/speed/public-dns/)

set your /etc/resolv.conf to 8.8.8.8

---

