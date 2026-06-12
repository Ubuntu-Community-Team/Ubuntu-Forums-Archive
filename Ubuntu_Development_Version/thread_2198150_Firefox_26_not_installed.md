---
title: "Firefox 26 not installed?"
date: 2014-01-07
forum: Ubuntu Development Version
---

### Post by ubunt72 on 2014-01-07
Is it not in the repos yet?   I noticed there are blogs and articles about 26 being released and one should be able to upgrade to 26.   But, it's not even displayed in 14.04 (13.10 shows in my install)?

```
$ apt-cache policy firefox
firefox:
  Installed: 25.0+build3-0ubuntu0.13.10.1
  Candidate: 25.0+build3-0ubuntu0.13.10.1
```

---

### Post by QDR06VV9 on 2014-01-07
Thais has been addressed already.
[http://ubuntuforums.org/showthread.php?t=2196001](http://ubuntuforums.org/showthread.php?t=2196001)
You will see a couple of ways to upgrade and depending on your skill set, I would not recommend the proposed ppa unless you can fix things that get broked.
You can simply add the firefox ppa works on trusty been using it for a bit now.
Firefox PPA works for Trusty.
[https://launchpad.net/~mozillateam/+...e/firefox-next]("https://launchpad.net/%7Emozillateam/+archive/firefox-next")
Regards

---

### Post by ubunt72 on 2014-01-07
I understand this, I think but I still got this error:

> Fetched 27.1 MB in 40s (661 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.


---

### Post by QDR06VV9 on 2014-01-08
> **ubunt72 said:**
> I understand this, I think but I still got this error:

Change or edit that PPA with synaptic from "trusty" to "saucy"

---

### Post by Elfy on 2014-01-08
personally - I just enabled proposed - let firefix update and then disabled it again

---

### Post by fooman on 2014-01-08
> **Elfy said:**
> personally - I just enabled proposed - let firefix update and then disabled it again

ingenious!!  thanks Elfy

---

### Post by QDR06VV9 on 2014-01-08
> **Elfy said:**
> personally - I just enabled proposed - let firefix update and then disabled it again

Or You could do the above:p
Thanks Elfy:D
Although been running firefox next ppa every time the current os Im running isnt current with the firefox version since I think(?)
Maverick without any problems.

---

### Post by ubunt72 on 2014-01-11
EDIT:  Doh!   I just read about changing it from trusty to saucy in the ppa.   It upgraded and installed/upgraded to Firefox 26 but.... BUT, it complained that there was some problems with 'some add-ons.'   What does that mean?  I don't notice anything problematic yet.   

Is there any difference with doing it the 'ppa way' vs the checking/enabling the 'proposed' software way?

---

### Post by mc4man on 2014-01-11
That FF ppa does not have trusty packages so if you wanted to use then you'd need to edit the source entries to saucy

If you must have the latest FF before then just enable -proposed & update FF ,ect
(currently @27

---

### Post by QDR06VV9 on 2014-01-11
> **ubunt72 said:**
> The ppa way doesn't work so I'll try the 'proposed' trick.   

Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Sources           
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages    
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages     
  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

The how-to I found (more than one) more or less instruct the same thing and nothing worked.   There needs to be better instructions or someone confirming it doesn't work so we don't waste our time.
Did you edit your source list for that ppa from trusty to saucy because it not ready for trusty..
Yes just use Elfys way..
Here is my version

---

