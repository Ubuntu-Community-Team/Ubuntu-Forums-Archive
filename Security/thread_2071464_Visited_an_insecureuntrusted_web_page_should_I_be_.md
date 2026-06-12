---
title: "Visited an insecure/untrusted web page should I be concerned?"
date: 2012-10-15
forum: Security
---

### Post by Frozen Forest on 2012-10-15
I recently visited a site (see code), before visiting did I get a warning from google that this site was untrusted, I needed to check for specific content so I visited the page anyway. I did take some preconscious before, Noscript activated allow no scripts, allow no cookies, firefox privacy mode, so my question stand should I run some test to check for malware and if so how?

```

www.smj.org.sa

```

---

### Post by BrandonIngalls on 2012-10-15
I would not recomend going to that site, upon me going to it in firefox WOT popped up with a warning advising me to leave the site, also it is reported as an attack site.
```
https://www.mywot.com/en/scorecard/smj.org.sa?utm_source=addon&utm_content=warn-viewsc
```

---

### Post by Ms. Daisy on 2012-10-15
[http://www.google.com/safebrowsing/diagnostic?site=www.smj.org.sa](http://www.google.com/safebrowsing/diagnostic?site=www.smj.org.sa)
> Of the 1194 pages we tested on the site over the past 90 days, 199  page(s) resulted in malicious software being downloaded and installed  without user consent. The last time Google visited this site was on  2012-10-15, and the last time suspicious content was found on this site  was on 2012-10-14.

Malicious software includes 99 scripting  exploit(s), 1 trojan(s), 1 exploit(s). Successful infection resulted in  an average of 2 new process(es) on the target machine.The entire domain got flagged as malicious. The "scripting exploits" were probably blocked by noscripts if you did not allow any on the pages you visited.  The "trojan" could have installed without your knowledge depending on what operating system/browser it was crafted for (which I couldn't determine from the information on the diagnosis page).  The "1 exploit(s)" is a pretty useless description so we can't really know what it was doing.

In order to determine for certain whether you got owned or not, you could run wireshark ON ANOTHER COMPUTER on your network and analyze the packets coming from the suspect computer (odds are if you got owned something will try to "phone home" by connecting to a dubious foreign address maybe on a weird port).  You could dive down the digital forensics rabbit hole if you've got time on your hands. 

Or you could just back up your data & reinstall to be truly certain.

I'm gonna sound like a jerk here, but perhaps it's better practice to come up with a response plan BEFORE you click on the site.

---

### Post by mike acker on 2012-10-15
the note about infections from google doesn't say what platforms were used.  XP is notoriously easy to compromise; Win7 is much better. IE6 was a hackers playground; ie9 much better --- according to reports i've read

since the quote from google doesn't reference platforms their information is of little value.

i still think the thing to do is to use separate ordinary user accounts in Ubuntu|Linux .  what we are concerned with is whether a dropper can leave something in your user libraries that (e.g.) Firefox would pickup on initialization -- a stealthy plug in or something similar -- facilitating a MITB attack

---

### Post by Ms. Daisy on 2012-10-16
A scripting exploit executes in the browser, not the operating system.

---

### Post by OpSecShellshock on 2012-10-17
Going by the Google safe browsing link, it appears that the malware was actually hosted on/served from other domains but that there were scripts injected into the site that would, if run, load content from those domains.

If scripts were not allowed on the domain then the injected scripts wouldn't have run. Even if that site had been allowed to run scripts, I don't think the scripts from the external domains would have run so long as NoScript was in use.

Obviously I can't say for sure one way or the other whether you've got malware or not, but what I can say is that based on the Google safe browsing analysis, the risk of visiting the site to someone using Ubuntu with Firefox with NoScript is very low.

---

### Post by spareproject on 2012-10-17
Does noScript also stop scripts executing on cross-site requests(if they can be executed)? I have not read much into it other than authentication such as cookies being sent for session jacking and the like. But always just assumed that these sites would be able to execute scripts :S

---

### Post by OpSecShellshock on 2012-10-17
> **spareproject said:**
> Does noScript also stop scripts executing on cross-site requests(if they can be executed)? I have not read much into it other than authentication such as cookies being sent for session jacking and the like. But always just assumed that these sites would be able to execute scripts :S

I believe that it does have protection that sort of thing as well.

---

### Post by Frozen Forest on 2012-10-18
First, thanks for all the answers.

> **Ms. Daisy said:**
> [http://www.google.com/safebrowsing/diagnostic?site=www.smj.org.sa](http://www.google.com/safebrowsing/diagnostic?site=www.smj.org.sa)
The entire domain got flagged as malicious. The "scripting exploits" were probably blocked by noscripts if you did not allow any on the pages you visited.  The "trojan" could have installed without your knowledge depending on what operating system/browser it was crafted for (which I couldn't determine from the information on the diagnosis page).  The "1 exploit(s)" is a pretty useless description so we can't really know what it was doing.

In order to determine for certain whether you got owned or not, you could run wireshark ON ANOTHER COMPUTER on your network and analyze the packets coming from the suspect computer (odds are if you got owned something will try to "phone home" by connecting to a dubious foreign address maybe on a weird port).  You could dive down the digital forensics rabbit hole if you've got time on your hands. 

Or you could just back up your data & reinstall to be truly certain.

I'm gonna sound like a jerk here, but perhaps it's better practice to come up with a response plan BEFORE you click on the site.
I do agree that it would have been wiser to make an analysis before i visited the site, I did take some precautions before, noscript, no cookies, separate firefox profile, but as mike said an other user account with no root access would be good. I will reinstall for Ubuntu 12.10 so it will fix any issue if it exist, but I wonder if the malware can hide among my other files, and thus get transfered to my new install. 

My firewall would probably notice if there was a process trying to phone-home, since it blocks outgoing also, as long as it don't connect to a destination port for http, https and a couple of others. Start to wonder what malware actual could do, could it install a keylogger, but that would require root access to begin with. Guess I will have to install an antivirus to check if there exist something in the files I will backup.

---

### Post by Ms. Daisy on 2012-10-18
> **OpSecShellshock said:**
> I believe that it does have protection that sort of thing as well.
It does.
[http://noscript.net/features#xss](http://noscript.net/features#xss)

---

### Post by Ms. Daisy on 2012-10-18
> **Frozen Forest said:**
> I do agree that it would have been wiser to make an analysis before i visited the site, I did take some precautions before, noscript, no cookies, separate firefox profile, but as mike said an other user account with no root access would be good. I will reinstall for Ubuntu 12.10 so it will fix any issue if it exist, but I wonder if the malware can hide among my other files, and thus get transfered to my new install. 

My firewall would probably notice if there was a process trying to phone-home, since it blocks outgoing also, as long as it don't connect to a destination port for http, https and a couple of others. Start to wonder what malware actual could do, could it install a keylogger, but that would require root access to begin with. Guess I will have to install an antivirus to check if there exist something in the files I will backup.
Slow down & educate yourself a little.  

Read [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

If you'd like to do a little investigation to feel better about your current installation, read this:
[https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned](https://wiki.ubuntu.com/BasicSecurity/DidIJustGetOwned)

---

### Post by s1baker on 2012-10-19
I wonder why [www.smj.org.sa](www.smj.org.sa) isn't listed on any of the host files that one can obtain from these sites?:
( about 10 megs worth )

```

http://winhelp2002.mvps.org/hosts.txt 
http://hphosts.gt500.org/hosts.txt
http://www.securemecca.com/Downloads/hosts.txt
http://hostsfile.mine.nu/Hosts
http://sysctl.org/cameleon/hosts.win 
http://hosts-file.net/hphosts-partial.asp
http://hosts-file.net/ad_servers.asp
http://someonewhocares.org/hosts/
https://www.abuse.ch/spyeyetracker/blocklist.php?download=domainblocklist
https://www.abuse.ch/zeustracker/blocklist.php?download=domainblocklist
http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts&showintro=1&mimetype=plaintext

```

---

### Post by OpSecShellshock on 2012-10-20
> **s1baker said:**
> I wonder why [www.smj.org.sa]("http://www.smj.org.sa") isn't listed on any of the host files that one can obtain from these sites?:
( about 10 megs worth )

```

http://winhelp2002.mvps.org/hosts.txt 
http://hphosts.gt500.org/hosts.txt
http://www.securemecca.com/Downloads/hosts.txt
http://hostsfile.mine.nu/Hosts
http://sysctl.org/cameleon/hosts.win 
http://hosts-file.net/hphosts-partial.asp
http://hosts-file.net/ad_servers.asp
http://someonewhocares.org/hosts/
https://www.abuse.ch/spyeyetracker/blocklist.php?download=domainblocklist
https://www.abuse.ch/zeustracker/blocklist.php?download=domainblocklist
http://pgl.yoyo.org/as/serverlist.php?hostformat=hosts&showintro=1&mimetype=plaintext

```

My guess is that it's because it's an otherwise-legitimate site that was compromised in such a way that it redirects to domains hosting malware, rather than hosting malware itself. There are far, far too many of those for it to make sense to add them to blacklists.

---

### Post by mr-woof on 2012-10-21
i agree with OpSecShellshock, its probably a legitimate site that was compromised, virustotal.com has found things on the site.

[https://www.virustotal.com/url/d97194a5570d36f259ef1e34849a8d7c62ae007bb4590862b309138f47bb6360/analysis/1350848611/](https://www.virustotal.com/url/d97194a5570d36f259ef1e34849a8d7c62ae007bb4590862b309138f47bb6360/analysis/1350848611/)

I wonder if you can report it anyone? Maybe the site admin is completely unware it's been compromised.

---

