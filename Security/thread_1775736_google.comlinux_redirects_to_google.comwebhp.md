---
title: "google.com/linux redirects to google.com/webhp"
date: 2011-06-05
forum: Security
---

### Post by fpgdu on 2011-06-05
I googled "google.com webhp" and the majority of the sites that come up mention rootkits in windows xp. [www.google.com/linux](www.google.com/linux) is the only webpage that redirects me there. Is it possible that this is a rootkit on linux as well? I know that's far-fetched, but just want to make sure.

Does anyone else get that address when trying to access google.com/linux?

---

### Post by nzc3 on 2011-06-05
Hi fpgdu,

here my test and test results:

FYI, I am running:
Ubuntu 11.04 on the test machine

**_Test (1):_**
* Opened OPERA browser (11.11)
* put into the browser:
  [http://google.com/linux](http://google.com/linux)
* received as output:
  [http://www.google.com/webhp](http://www.google.com/webhp)

**_Test (2):_**
* Opened CHROME browser (11.0.696.71)
* put into the browser:
  [http://google.com/linux](http://google.com/linux)
* received as output:
  [http://www.google.com/webhp](http://www.google.com/webhp)

**_Test (3):_**
* Opened both browsers and checked for the URL:
  [http://www.google.com/linux](http://www.google.com/linux)
* it shows up in search but when entering it goes to the "webhp" site
* when looking into the "cached" sit you can find the "Linux" search, but 
  not when trying to access it.

So after checking also some threads and also Google's homepage:
[http://www.google.com/intl/en/about/products/index.html](http://www.google.com/intl/en/about/products/index.html)

It seems that the "old Linux" search might be "gone" ... :-( ... .

Even so always check the security as the redirect you mention, has also been used by some malware.

I hope my findings could help you.

Cheers
nzc3

---

### Post by mikodo on 2011-08-01
I get the same behavior as the OP. Does anyone know a solution, or as suggested by the second poster (nzc3), is it gone now?

Thanks.

---

### Post by mikodo on 2011-08-01
I asked lovinglinux in the Firefox mega thread in Ubuntu forums Beginners section about this. He indicated that Google has pulled the plug on this and similar sites. See this link he provided about it:

[pulled the plug on Linux, Mac and other specialized search portals]("http://www.pcworld.com/businesscenter/article/229774/say_goodbye_to_google_search_portals_for_linux_mac_and_more.html")

Too bad.

---

