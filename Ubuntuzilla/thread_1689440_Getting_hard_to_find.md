---
title: "Getting hard to find"
date: 2011-02-16
forum: Ubuntuzilla
---

### Post by kansasnoob on 2011-02-16
No doubt because Ubuntu is doing better at staying up to date I discovered today that it's not really easy to find the easy way to use us:

```
echo -e "\ndeb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main" | sudo tee -a /etc/apt/sources.list > /dev/null && sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com C1289A29 && sudo apt-get update && sudo apt-get install firefox-mozilla-build

```

Just run a search. Use Google or Yahoo. I'm so used to using the same "script" I just have a copy in my mailbox and hadn't realized.

Should we at least have a "quick-link" here at the top of the page?

I'm doing some Natty testing and due to FF4-beta instability I still use Ubuntuzilla. Well I almost always use Ubuntuzilla, unless I'm going true Debian based then I:

> apt-get remove iceweasel
mv firefox-X.X.X.tar.bz2 /usr/lib/
cd /usr/lib/
tar -jxvf firefox-X.X.X.tar.bz2
ln -s /usr/lib/firefox/firefox /usr/bin/firefox 

And fiddle around a bit ;)

So, should we have a "quick-link" here? I've never had that command fail, but I also never run 64 bit.

---

