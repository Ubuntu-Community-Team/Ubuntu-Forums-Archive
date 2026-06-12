---
title: "ie4linux &quot;This site may harm your computer&quot; Google says"
date: 2009-10-25
forum: Wine
---

### Post by hamidaddin on 2009-10-25
I want to install IE on linux to be able to access OWA full interface.

Found this howto: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

When I tried to download the script, Google search engine says "This site may harm your computer" and Firefox says "This web site at [www.tatanka.com.br](www.tatanka.com.br) has been reported as an attack site and has been blocked based on your security preferences."

Anyone knows if the script is not safe?

---

### Post by dralbin82 on 2009-10-25
I get the same message and need answer to this question too...

---

### Post by alex.rayu on 2009-10-25
Probably because it proposes to install ie6 and other software in an environment that it was not supposed to tun it, so some nice correct people have submitted a few "Beware of hackers" complaints. Probably just about that.

---

### Post by Penguin Guy on 2009-10-25
I doubt it will harm your computer.

---

### Post by riteman on 2009-10-25
Visiting the site from my Windows PC my virusprogram issues an alarm and moves a file into quarantine
I have a copy of the file needed toinstall IE6 but Ihave not been able toinstall - no files get downloaded. I then downloded manually but still I get a file corrupted when the VGX.CAB is to be extracted :(

---

### Post by edin9 on 2009-10-25
[http://safebrowsing.clients.google.com/safebrowsing/diagnostic?client=Firefox&hl=en-GB&site=http://www.tatanka.com.br/](http://safebrowsing.clients.google.com/safebrowsing/diagnostic?client=Firefox&hl=en-GB&site=http://www.tatanka.com.br/) > Advisory provided by    Google Safe Browsing Diagnostic page for tatanka.com.br  What is the current listing status for tatanka.com.br?      Site is listed as suspicious - visiting this website may harm your computer.      Part of this site was listed for suspicious activity 3 time(s) over the past 90 days.  What happened when Google visited this site?     _ **Of the 23 pages that we tested on the site over the past 90 days, 13 page(s) resulted in malicious software being downloaded and installed without user consent.**_ The last time that Google visited this site was on 2009-10-20, and the last time that suspicious content was found on this site was on 2009-10-20.      Malicious software is hosted on 1 domain(s), including query-google.com/.      This site was hosted on 1 network(s) including AS26347 (DREAMHOST).  Has this site acted as an intermediary resulting in further distribution of malware?      Over the past 90 days, tatanka.com.br did not appear to function as an intermediary for the infection of any sites.  Has this site hosted malware?      No, this site has not hosted malicious software over the past 90 days.  How did this happen?      In some cases, third parties can add malicious code to legitimate sites, which would cause us to show the warning message.  Next steps:      * Return to the previous page.     * If you are the owner of this website, you can request a review of your site using Google Webmaster Tools. More information about the review process is available in Google's Webmaster Help Centre.

---

### Post by hikaricore on 2009-10-25
Google's warning system incorrectly flags sites sometimes,this is ocassional due to banner advertisements.

I remember when another site I visit which doesn't even have downloads was flagged for just such a reason.

---

### Post by beastrace91 on 2009-10-25
Also worth noting that any viruses/malware on such sites are NOT going to effect your Ubuntu system. If you share a Windows network or use pen drives that go into window system how ever it would be a good idea to virus scan your system after using such files :)

~Jeff

---

### Post by alex.rayu on 2009-10-26
**No, it IS infected!** I got to it with my windows machine, bypassed the warnings, and my Avast showed a **HTML:Iframe-inf** threat.

Careful people!

---

### Post by ndefontenay on 2009-10-26
So, go on the web site but only with a *nix OS.

---

### Post by alex.rayu on 2009-10-26
I read that some of these worms are JS-based and may harm your computer cross-platform.

Besides, don't forget, you will use it in WINE, which is already knows to support a bunch of malware and worms.

---

### Post by hamidaddin on 2009-10-26
So I gather that the problem is in java scripts in the website and not in the ix4linux script (ies4linux-latest.tar.gz)?

I've already downloaded the file but I did not install it yet.

---

### Post by alex.rayu on 2009-10-26
Right. The web site is infected. Not the program itself.

---

### Post by exaviorn on 2009-10-27
Yea, I installed ie4linux fine, avoided the sites problems and wgeted it, installed fine to my knowlage :D

---

### Post by hamidaddin on 2009-10-27
Thanks.. I'll try installing it now.

---

### Post by hamidaddin on 2009-10-27
OK, I've installed it and it's working. Only I had to repeat running the script many times to insure that all files are downloaded properly. These two links were useful:
[http://ubuntuforums.org/showthread.php?t=692000](http://ubuntuforums.org/showthread.php?t=692000)
[http://ubuntuforums.org/showthread.php?p=4702250](http://ubuntuforums.org/showthread.php?p=4702250)

First attachment shows how OWA looks in ie4linux:



One minor issue though. I have managed to change the colors of wine applications to match the theme i use for Gnome (Dust). As you can see the colors of ie6 do not match the color scheme of other wine apps (attached wineconfig and notepad screen shot).

Any ideas?

---

### Post by hamidaddin on 2009-10-29
I was able to fix the colors. It seems that ies4linux creates its own registry files under .ies4linux folder

I just opened the user.reg file for editing and found the lines for colors.

```

$ gedit ~/.ies4linux/ie6/user.reg
```

The lines that have the interface colors are under this section: [Control Panel\\Colors]

Hope this helps someone.

---

### Post by bigsuccess on 2009-11-02
I'm still not 100% on this, it'd be nice to have it easy to install etc but I decided to try to install ie in wine because google said it scanned this site on the 1/11/09 and it was still malwaring... so that's recent enough for me to think it's not cool.

Anyone else have any authoritative views on this?

---

### Post by alex.rayu on 2009-11-02
I dont understand you people. For last half a year I have been doing an ie6 in wine with winetricks. It seems ies4linux has actually been abandoned because it has not been needed for a long time already.

---

### Post by hamidaddin on 2009-11-02
Thanks for the tip Alex. I hope you said this earlier :) . It is the first time I hear about winetricks and it looks interesting..

---

### Post by alex.rayu on 2009-11-02
I cant understand why I have not said it earlier. I really should have.

Winetricks are suggested by the official wine web site: [http://wiki.winehq.org/winetricks](http://wiki.winehq.org/winetricks)

---

### Post by frank cox on 2009-11-03
> **alex.rayu said:**
> **No, it IS infected!** I got to it with my windows machine, bypassed the warnings, and my Avast showed a **HTML:Iframe-inf** threat.

Careful people!

That is a shame because I loaded it when I first tried Ubuntu and it worked pretty well. 
I rebuilt the system due to other problems and when I got the warnings I tried the wine trick version and it was a nightmare. I wish I was smart enough to remove the malware but I am only smart enough to know I am not smart enough.

---

### Post by alex.rayu on 2009-11-03
it has been some time now that winetricks version is not worse, or maybe even better, that the ies4linux. I think that is why the guy no longer cares about that web site and left it rot there.

But as for the malware on that site - no you can't. You would need ftp data to log into the server and purge the script out from the files manually. I used to do that quite often - it's not hard if you know the basics of php and javascript. But no you cant do anything without ftp access. Unless you are so smart you hack into the ftp =)

---

### Post by hamidaddin on 2009-11-03
You can bypass the reportedly harmful scripts in the website by downloading the file from the command line.

Open your terminal and run this command:

```
wget http://www.tatanka.com.br/ies4linux/downloads/ies4linux-latest.tar.gz

```

You can then use this howto to install: [http://www.psychocats.net/ubuntu/ies4linux](http://www.psychocats.net/ubuntu/ies4linux)

Let me know if you have any problems.

---

### Post by hamidaddin on 2009-11-03
Another note for those who will install ies4linux, before running IE for the first time. I suggest you change the default home page in the launching script.

By default, IE will try going to the infected website (I don't know what harm would that do).

Anyway, to be on the safe side just do the following:
1- Open IE launching script for editing: Press ALT+F2 then paste "gedit .ies4linux/bin/ie6" and press Enter. Depending on what versions you installed, you will have one or more script files (i.e. ie6, ie7..). I assumed here you have only ie6. If you have other versions installed you will do the same for these versions.

2- Look for the lines where wine is called (lines 13 & 15 in my case). In both places after ( wine "/home/../IEXPLORE.EXE" you will find a quotation having the default home page, change it to your liking. I've changed it to "about:blank". When done save the file and close it and you're good to go.

---

### Post by Danse on 2009-12-01
Hello, about the harmful script, I was not careful enough and I browsed through the site with firefox 3.0; watching inside my home, later, I discovered a pdf file called "pdf.pdf", created about the same time while I was browsing the site (I am on linux).

Into the pdf file there was written only:
-=[Coromputer] All y0ur 0dAyZ Ar3 BeL0ng 2 uS [Coromputer]=-

That is not very encouraging, isn't it?

 Searching google about "coromputer" I found this site, full of instructions about exploit and security flaws: [http://www.coromputer.net/](http://www.coromputer.net/)

Well, I wish I had cleaned up at least private datas on my browser, before going into that site! (Sadly I didn't)

I wrote this all as warning for others.

---

### Post by Sticky_Bit on 2009-12-01
I ran into this as well. I heard about ie4linux on a podcast. When I saw the warning I chose to avoid it like the plague. People need to be careful. Just because there aren't really viruses written for Linux, does not mean you are immune to any kind of exploit. There are still rootkits and other vulnerabilies that can be exploited to allow someone to "own" your nix box too.

I'm wondering how viruses or other malware would affect a dualboot system. For instance I am dualbooting Ubuntu and XP. My Windows file system is accessible from within Ubuntu. If I downloaded something in Ubuntu, could it affect the Windows filesystem?

---

