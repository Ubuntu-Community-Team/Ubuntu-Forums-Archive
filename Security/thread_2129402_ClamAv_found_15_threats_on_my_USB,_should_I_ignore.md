---
title: "ClamAv found 15 threats on my USB, should I ignore it?"
date: 2013-03-26
forum: Security
---

### Post by asteriks on 2013-03-26
Hi, I installed ClamAv and ClamTK in Kubuntu 12.10 and I updated it, then I scanned my usb device, can you tell me why I got next result:
[http://oi47.tinypic.com/dxbs42.jpg](http://oi47.tinypic.com/dxbs42.jpg)

it says it found 15 threats but all are in exe files of: 7zip, PaintNet, gpg4win, Python and Portable Python...
so, what should I do? Ignore it?

---

### Post by cool110 on 2013-03-26
Thats perfectly fine to leave. Most portable apps are detected as potentialy unwanted as some of them can be used to workaround restrictions in locked down corparate systems and networks.

---

### Post by c24ck32 on 2013-03-27
Yea even if it's really contain a virus it won't affect ubuntu :D

---

### Post by maglinu on 2013-03-27
Unless you particularly want to scan for PUAs (and ClamAV seems more fussy about what is a PUA(P) than any other AV I've used), you could use the CLI method (clamscan -r). I believe it has default = no for detect PUA (and you can configure it anyway). 

Clamtk uses default = yes I think, and has no obvious way to set it to = no that I can see.

---

### Post by delamite on 2013-03-27
Err, 
nevermind

---

### Post by Stonecold1995 on 2013-03-29
I suggest just to be safe you should re-download those files and delete the old ones.  I find it kind of suspicious that all the exes are detected as malware...

Also, why would you even need exes unless you plan to run them on a Windows computer (which can get infected) or through Wine on Linux (which can also get infected, but will cause much much less damage)?

If you don't want to redownload or ignore it, you can scan the files with the site [http://virustotal.com](http://virustotal.com) (this is a great site which will scan any file you upload with many different antivirus products.  It is great for scanning a very suspicious file you feel may have got around AV software, or are in a situation like this where you want to make sure it isn't just ClamAV overreacting).

Not really related but VirusTotal was rather recently taken up by Google, which I kind of hate.  It's just Google increasing their monopoly.

---

### Post by claracc on 2013-03-30
As you can see in this discussion [http://forums.clamwin.com/viewtopic.php?t=3600](http://forums.clamwin.com/viewtopic.php?t=3600), it seems PUA detections made by clamav are false positives.

---

### Post by mharv on 2013-03-30
> Yea even if it's really contain a virus it won't affect ubuntuThat kind of attitude is what malware writers target. The best antivirus is never installing software from untrusted sources and never running as root/administrator on any operating system other than to install software or change system wide-settings.

---

### Post by Stonecold1995 on 2013-03-30
> **mharv said:**
> That kind of attitude is what malware writers target. The best antivirus is never installing software from untrusted sources and never running as root/administrator on any operating system other than to install software or change system wide-settings.
Don't forget keeping software as up to date as possible.  Even if you use Common Sense Internet Security 2013 you'll still be vulnerable to things like drive-by downloads.  If someone hacks an innocent, trusted site you visit, that's out of your control, and yet if you visit it and your browser/operating system is compatible, you'll be infected anyways.  The only variables in that situation are: the capabilities of the exploit kit (it's extremely unlikely that it'll infect Linux, but maybe in the future through insecure applications like Java, Flash, and maybe even HTML5), the security of the site which would be infected with the exploit kit (can they fend off the attacker, or will they succumb and never even know they've been turned into a malware distributor?), and whether or not your computer is up to date (which is partially in your control, but part of this variable is the developer's speed at which they patch exploits, and find new ones to patch).

The most advanced malware doesn't come in "hawt_pr0n.avi.exe" anymore, they come in highly advanced exploit kits that are updated frequently to bypass as many security measures as they can, and these exploit kits aren't always placed on sketchy Russian sites which most people are smart enough to avoid, they can easily be in your favorite blog, a local store's website, or even an advert (which means any legit site that displays the ad will also become a beacon of infection, and it's not like ad companies to put all that much money in security).

---

### Post by asteriks on 2013-04-01
Ok people thanks for answers, I use linux and windows therefore I used clamav to scan my USB and I was susprised to see mentioned results. but OK, I will take it for false warnings.

---

