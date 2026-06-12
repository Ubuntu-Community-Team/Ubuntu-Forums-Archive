---
title: "Might have found a virus?"
date: 2011-05-15
forum: Security
---

### Post by Larkspur on 2011-05-15
ClamAv found a possible virus in my Firefox cache, which it identifies as "PHP.Hide-2."  I've had Ubuntu for almost a year and I've never had a virus reported, not even possible ones, apart from the test one.  At the moment, I've got the virus sitting in Quarantine.  I'm just wondering what to do.  Will deleting it be enough?  With windows viruses, there's usually a procedure to follow, but I guess, with there being no registry, there's no point, right?  I was going to report it, but the options on the dialogue are only "New Malware" or "False Positive."  I know it's not the first because, well, Clam found it, and I don't know if it's the latter.  Clam was keen to point out it was only "possibly" a virus. Should I still submit it?  There doesn't seem to be much on the web about it, except the fact it was added to Clam's signature db, which I kind of know already:rolleyes:.   Any advice?

---

### Post by Dave_L on 2011-05-15
It's listed here, with a couple of alternate names, Backdoor.PHP.Rst.k and Backdoor.PHP.Rst.h: 
[http://lurker.clamav.net/message/20100529.135009.08f6200a.en.html](http://lurker.clamav.net/message/20100529.135009.08f6200a.en.html)

---

### Post by Larkspur on 2011-05-15
Thanks.  I found similar pages, but from the aliases you mention, I got a bit more information: as the names suggest, PHP.Hide-2 are supposed to set up backdoor in infected computers.  It's quite an old piece of malware (IF clamav was right - there's a lot of mentions on the forum about clam's rate of false positives) and I haven't found any open ports yet.  I decided to delete the "malware" - since it wasn't an important file - and cleared FF's cache.  If it crops up again, I'll submit it to clamav as a false positive.  I'd be interested if anyone finds something similar; the sites I was browsing weren't out of the ordinary for me - a couple of blogs, a game site, and a few wallpaper/icon sites - but I haven't seen any sort of detection until today.

---

### Post by ajay_vishvanathan on 2011-05-15
do we need any antivirus for linux?
I personally am not using any AV and its fast enough.. btw i heard that av slows your pc down.. and there arent any much viruses active here in ubuntu.. and every new distro or version will render any virus released for previous distro/version useless.. thats what i heard.. please correct me..

---

### Post by uRock on 2011-05-15
I do not recommend AV unless you are running server applications. The system usually gets patched as soon as vulnerabilities are found.

---

### Post by doas777 on 2011-05-15
interesting.

luckily it appears that it can't really hurt you from within your FF cache, at least not based on the information provided by the av folks. just delete it.

the backdoor needs to be installed on a web server in order to work, so it is more of a peice of malware a hacker leaves behind or plants by executing a vulnerability in the **configuration **of  the webserver or applicaton (PHP). it does not appear to have any capability to spread on its own, so it must be planted on a vulnerable host manually, or by scripted attack. if you had found it in your webserver, I woudl have suspected that you had been hacked and it was left behind to ensure continued access like a rootkit.

since it doesnt rely on a system or application vulnerability to work (just semi-legit features), it isn't really a virus or worm, and cannot be defanged by updates, which is why it still works 4 years after detection.

Edit: thought it does not really use this mechanism to propagate, it does appear to replace other PHP files with itself when run. that is likely how you got it (you went to a page that invoked the script without a mime handler association, so the file was downloaded to the client as a octetstream rather than run; PHP is run server-side and is not passed down with page source, so woudl not typically be downloaded to cache). perhaps it hopes to infect a web developers toolbox, trying to get them to accidentally propagate it like a thumbdrive worm.

---

### Post by Larkspur on 2011-05-15
> **ajay_vishvanathan said:**
> do we need any antivirus for linux?

At the moment, I wouldn't say it was essential, since there's no evidence of a widespread infection.  Then again, it can pay to be cautious . . .

> I personally am not using any AV and its fast enough.. btw i heard that av slows your pc down..

On Ubuntu, it won't because all that is available are on-demand scanners, which are only active when you scan your system.  Then again, some would say that even that is too much, since there's nothing to scan: What I found is most likely a false positive, and, as I say, there's no evidence of viruses in the wild.  AV which constantly scans your system for risks (like the AV suites in windows and now the Mac) have been known to slow down systems, but that is happening less and less now.  

> every new distro or version will render any virus released for previous distro/version useless.. thats what i heard.. please correct me..

In a way, yes: as vulnerabilities are found, patches are released, which secure the system.

---

### Post by Larkspur on 2011-05-15
> **doas777 said:**
> since it doesnt rely on a system or application vulnerability to work (just semi-legit features), it isn't really a virus or worm, and cannot be defanged by updates, which is why it still works 4 years after detection.


Thanks for the info!  It was actually that last part that made me lean toward thinking it was a false positive: for it to get to me, it must have somehow got on to the server of whichever site I picked it up from, but the sort of sites I was looking at aren't the type that would leave their servers open to a four-year old bit of malware.  Still, it was strange that clam should identify it after months of not doing so. . . but anyway, whatever it was, it's gone now.

---

### Post by doas777 on 2011-05-15
> **Larkspur said:**
> Thanks for the info!  It was actually that last part that made me lean toward thinking it was a false positive: for it to get to me, it must have somehow got on to the server of whichever site I picked it up from, but the sort of sites I was looking at aren't the type that would leave their servers open to a four-year old bit of malware.  Still, it was strange that clam should identify it after months of not doing so. . . but anyway, whatever it was, it's gone now.
yeah, its one of those semi-legit administration tools gone wrong. 
I edited my post just a minute ago with a theory about how you got it. when you put a php script up on a server, but the server doesn;t realize that the file is to be run as a php script, it will download to the client as an octetstream (kind of a generic type for raw web data). the Hide script probably got run somewhere else on the server you got the file from, and when it ran, it infected all the other .phps it could, including one in the web app you were accessing.

---

### Post by Duncan Williams on 2011-05-15
Clamav is upgrading its products and definition databases as well as adding new engines to identify malware.
The latest windows version `immunet protect' has 3 engines now that clamav is added.

If you want to check a specific file, use Jotti's malware scan.
(which scans the file with different antivirus engines)
The link for jottis and other linux related security are available in the linux section of my internet security site.
[http://my.opera.com/internetsecurity/archive/]("http://my.opera.com/internetsecurity/archive/")

---

