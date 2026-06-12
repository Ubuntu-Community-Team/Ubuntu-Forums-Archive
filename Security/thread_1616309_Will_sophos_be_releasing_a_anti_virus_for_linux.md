---
title: "Will sophos be releasing a anti virus for linux?"
date: 2010-11-08
forum: Security
---

### Post by dogdo on 2010-11-08
I know antivirus is pointless on ubuntu but seeing this story [http://www.theregister.co.uk/2010/11/02/sophos_mac_anti_virus/](http://www.theregister.co.uk/2010/11/02/sophos_mac_anti_virus/) I would like to know if sophos is going to make a linux version for desktops?

---

### Post by deanjm1963 on 2010-11-08
> **dogdo said:**
> I know antivirus is pointless on ubuntu but seeing this story [http://www.theregister.co.uk/2010/11/02/sophos_mac_anti_virus/](http://www.theregister.co.uk/2010/11/02/sophos_mac_anti_virus/) I would like to know if sophos is going to make a linux version for desktops?

Why don't you contact them? They'd be the first ones to know.

---

### Post by tgm4883 on 2010-11-08
Yea, Sophos would be a better direction for that questions. FWIW, Symantec already has a Linux antivirus product

---

### Post by Soul-Sing on 2010-11-09
> Sophos Anti-Virus for Linux &#8211; part of Sophos Endpoint Security and Data Protection &#8211; provides superior on-access scanning for [COLOR="Red"]Linux desktops[/COLOR], laptops and servers, delivering excellent performance

With Norman and Avira (dazuko module), Sophos comes with [COLOR="Red"]on access[/COLOR] antivirus for linux.
there are many (and free) on demand antivirus scanners for linux.

---

### Post by tgm4883 on 2010-11-09
> **leoquant said:**
> With Norman and Avira (dazuko module), Sophos comes with [COLOR="Red"]on access[/COLOR] antivirus for linux.
there are many (and free) on demand antivirus scanners for linux.

Whats the difference between on access and on demand? Sounds similar to me. If anything, on demand could be just telling it to scan a specific file, but on demand would be an odd thing to call it IMO.

---

### Post by Soul-Sing on 2010-11-10
on access = real time protection, the antivirusprog is always active and running in the background
om demand = the antivirusprog is not always running on the background, and scans only "on demand"
Bitedender for unices/avast for linux/f prot for linux (and many more) are such progs.

---

### Post by Velnias on 2010-11-10
Its really weird - no viruses in Linux, but companys waste money creating free antiviruses. Why?

---

### Post by OpSecShellshock on 2010-11-10
> **Velnias said:**
> Its really weird - no viruses in Linux, but companys waste money creating free antiviruses. Why?

Checklist-based security standards in enterprise environments? There's probably also an element of branding in such a competitive market. And then sometimes it's just easier to provide something when people ask, even if it doesn't do much. I'd expect most of the marginal cost to AV developers (aside from advertising and bloatware deals) is in the research and writing up to date detection signatures, which wouldn't require a particularly big investment in a Linux version.

---

### Post by tgm4883 on 2010-11-10
> **Velnias said:**
> Its really weird - no viruses in Linux, but companys waste money creating free antiviruses. Why?

Company policy, government policy, some Linux AV actually scan for Windows threats too (think about a file server), there actually are a few Linux viruses (not many though)

---

### Post by cariboo on 2010-11-10
> **tgm4883 said:**
> Company policy, government policy, some Linux AV actually scan for Windows threats too (think about a file server), there actually are a few Linux viruses (not many though)

I think you can safely say that all the av scanners that run on Linux mostly scan for Windows malware. If I remember correctly clamav is the only one that claims to scan for Linux malware too.

---

### Post by aysiu on 2010-11-10
> **dogdo said:**
> I know antivirus is pointless on ubuntu but seeing this story [http://www.theregister.co.uk/2010/11/02/sophos_mac_anti_virus/](http://www.theregister.co.uk/2010/11/02/sophos_mac_anti_virus/) I would like to know if sophos is going to make a linux version for desktops?
I don't think it really matters whether Sophos does or not.

Antivirus is useless enough on Windows and Mac. It's also useless on Linux.

Another way to think about it is this: if a viable and automated (non-trojan) malware threat appears for Linux, what about having antivirus installed on your machine is going to protect you from this new threat?

---

### Post by tgm4883 on 2010-11-10
> **cariboo907 said:**
> I think you can safely say that all the av scanners that run on Linux mostly scan for Windows malware. If I remember correctly clamav is the only one that claims to scan for Linux malware too.

Yes, they mostly do scan for windows threats. Some have detections for Linux threats as well. I'm not sure about clamav, but Symantec Antivirus for Linux scans for Linux threats

The ones that start with Linux are obviously for Linux. Although that short list there wouldn't include anything that is crossplatform. 
[http://www.symantec.com/business/security_response/landing/azlisting.jsp?azid=L](http://www.symantec.com/business/security_response/landing/azlisting.jsp?azid=L)

---

### Post by cariboo on 2010-11-10
I find it really strange that when searching for any of the Linux viruses, the first 5 or so hits are from companies that sell anti malware software, it looks to me that they are trying hard to open up new markets. :)

---

### Post by OpSecShellshock on 2010-11-11
> **cariboo907 said:**
> I find it really strange that when searching for any of the Linux viruses, the first 5 or so hits are from companies that sell anti malware software, it looks to me that they are trying hard to open up new markets. :)

Yeah, but it's not terribly surprising. It's pretty common for end users to be aware enough about the risks associated with malware to worry, but not worried enough to learn how malware works (not to mention their systems in general).  There are probably opportunities for AV vendors there. I should be clear that I don't mean it in any conspiratorial way--the vendors and their labs are all incredibly helpful, especially when they go public with their runtime analyses of malicious processes. It just usually doesn't have anything to do with desktop Linux.

---

