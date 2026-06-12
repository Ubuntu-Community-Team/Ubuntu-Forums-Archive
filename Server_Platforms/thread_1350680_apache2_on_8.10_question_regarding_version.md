---
title: "apache2 on 8.10 question regarding version"
date: 2009-12-09
forum: Server Platforms
---

### Post by xkaliburx on 2009-12-09
Afternoon all, we run 'hackersafe' which basically is a great app that checks both application as well as code.  It's been complaining about apache2 version and I don't see an update newer than 2.2.9 for 8.10.

Looking here ([http://packages.ubuntu.com/search?keywords=apache2](http://packages.ubuntu.com/search?keywords=apache2)) I can see 2.2.12 even 2.2.14 available for Karmac and I am wondering if/when these binaries are ported to older server versions, or can they be installed on 8.10?

-- or --

Since 9.10 is out, dare I just dist-upgrade?  Not sure what problem(s) I will incur, I have never done on Ubuntu server yet, but I assume apache config's, perl mod's, etc. all stay in place right?


Thanks.

---

### Post by munky99999 on 2009-12-09
The thing is. You can goto [http://packages.ubuntu.com/karmic/apache2](http://packages.ubuntu.com/karmic/apache2)

Download each dependency. etc etc. But it'll be hard.

Personally it's easier to just upgrade. However that's situational.

Somewhat testy and potential for bad things to happen. You can add the karmic repo to your 3rd party software area. That basically gives you the ability to upgrade those packages.

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) karmic main universe multiverse restricted

reload synaptic to get fresh list. Yes this pretty much would also at the same time make ubuntu updater try to make you upgrade to karmic. Just dont do that :) Grab apache's latest and then uncheck that repo you would have just added. Then reload the lists again to go back to hardy.


Havent tried this myself in awhile. I just stay with the latest release. Doing this might void the whole support thing also. So do at your own risk.

---

### Post by xkaliburx on 2009-12-09
Cool, tnx.  Will take 1 of the 8 webservers and give it a shot 2nt!

---

