---
title: "Is ReGet fast or what? Anything else come close?"
date: 2007-02-25
forum: The Cafe
---

### Post by C-A on 2007-02-25
I recently downloaded a file that took about 3 hours. My friend downloaded the same file using ReGet (in windows) and it took him about 45 minutes. We have the same isp so I would think that there should not be too big of a difference between our bandwidth in general.

I have tried KGet in Kubuntu but still did not see ReGet speeds.

Does ReGet make that big of a difference or I am missing something?

---

### Post by PriceChild on 2007-02-25
I'm guessing he's closer to the exchange and so getting a better connection.

---

### Post by prizrak on 2007-02-25
I think wget is pretty damn quick ;)

---

### Post by Mateo on 2007-02-25
wget is really quick, too bad it's not a download manager though.

---

### Post by C-A on 2007-02-25
> **PriceChild said:**
> I'm guessing he's closer to the exchange and so getting a better connection.

You are probably correct. I thought I was closer but my speed does not compare to his.

---

### Post by maniacmusician on 2007-02-25
> **C-A said:**
> You are probably correct. I thought I was closer but my speed does not compare to his.
A good way to test it would be to use the same download manager. The default one in Firefox would work well, for instance.

---

### Post by BarfBag on 2007-02-25
[http://www.broadbandreports.com/](http://www.broadbandreports.com/)

That site may have a speed tester.  If not, it's a useful site.

---

### Post by C-A on 2007-02-26
> **maniacmusician said:**
> A good way to test it would be to use the same download manager. The default one in Firefox would work well, for instance.

I did some testing and it looks like it is a little of both- his connection is faster and reget is faster. We both downloaded a file with the firefox download manager and his connection was somewhat faster. He then downloaded the file with reget and his speed jumped up significantly.

---

### Post by NewOldTimer on 2007-02-26
> **BarfBag said:**
> [http://www.broadbandreports.com/](http://www.broadbandreports.com/)

That site may have a speed tester.  If not, it's a useful site.

yes it has speed test, this is one of my favorite sites that I brought over to ubuntu when I changed, this section of theirs is always good for something...[http://www.dslreports.com/forum/deeplink](http://www.dslreports.com/forum/deeplink)

---

### Post by tbroderick on 2007-02-26
> **Mateo said:**
> wget is really quick, too bad it's not a download manager though.

You could use [wget-queue]("http://decafbad.net/projects/scripts/"). Then wget will sort of act like a download manager. You just have to manually edit a simple file called todo.txt with any wget options and the address.

---

### Post by toxickiwi on 2007-03-06
ReGet is fast because it downloads multiple streams over http at the same time.

I am also looking for something like ReGet or Freedownloadmanager for Ubuntu.  Anyone?

---

### Post by toxickiwi on 2007-03-07
Okay after looking around today I have found two, Axel & Prozilla 

[http://www.cyberciti.biz/tips/download-accelerator-for-linux-command-line-tools.html](http://www.cyberciti.biz/tips/download-accelerator-for-linux-command-line-tools.html)
[http://prozilla.genesys.ro/](http://prozilla.genesys.ro/)

I have only used axel from command line to download http, it is faster than using wget but I still don't seem to get the same speed as reget on windows.

Also the http connection I am downloading from has passwords so I need to use it like this.

axel [http://username:password@site.com/filename.tar.gz](http://username:password@site.com/filename.tar.gz)

I hope that helps a bit.

---

### Post by C-A on 2007-03-07
> **toxickiwi said:**
> Okay after looking around today I have found two, Axel & Prozilla 

[http://www.cyberciti.biz/tips/download-accelerator-for-linux-command-line-tools.html](http://www.cyberciti.biz/tips/download-accelerator-for-linux-command-line-tools.html)
[http://prozilla.genesys.ro/](http://prozilla.genesys.ro/)

I have only used axel from command line to download http, it is faster than using wget but I still don't seem to get the same speed as reget on windows.

Also the http connection I am downloading from has passwords so I need to use it like this.

axel [http://username:password@site.com/filename.tar.gz](http://username:password@site.com/filename.tar.gz)

I hope that helps a bit.

Nice, Thanks! Axel produced really good speeds when I tested it.

---

