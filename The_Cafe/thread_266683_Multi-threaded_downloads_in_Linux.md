---
title: "Multi-threaded downloads in Linux ?"
date: 2006-09-27
forum: The Cafe
---

### Post by mips on 2006-09-27
I never seem to get good download speeds in ubuntu. Using D4X or WGET simply does not give me the same performance as say GetRight in windows.

With getright i have 5 simultanious segmented downloads of the same files. it literally maes out my adsl connection (384kb/s) to the point that i even battle to just browse the net.

In ubuntu it does not really get better than say 200kb/s.

If I download ISO's i use windows as i find linux to slow.

How can i improve this ???

---

### Post by croak77 on 2006-09-27
aria2

[http://aria2.sourceforge.net/](http://aria2.sourceforge.net/)

```

aria2 has  segmented downloading engine in its core. It can download one file from multiple URLs or multiple connections from one URL. This results in very high speed downloading, very much faster than ordinary browsers.
 As of 0.3.0 release, It can also download BitTorrent files.
 We implemented this engine in single-thread model. The architecture is very clean and easy to extend.
 
 Unlike Aria, which has GTK+ interface, aria2 provides command-line interface only. But GUI-lessness brings lower resource requirement. The physical memory usage is typically 3MB(normal HTTP/FTP downloads) to 5MB(BitTorrent downloads). 
 As of 0.7.1 release, aria2 supports asynchronous DNS using c-ares or ares. This can improve segmented download performance, especially in Metalink download. 

Command-line interface
Download files through HTTP/HTTPS/FTP/BitTorrent
HTTP Proxy support
FTP through HTTP Proxy
HTTP BASIC authentication support
HTTP Proxy authentication support
Segmented downloading
Cookie support(currently aria2 ignores "expires")
Run as a daemon process.
Selective download in multi-file torrent
BitTorrent Fast extension support
Metalink version 3.0 support(HTTP/FTP/BitTorrent)
```

---

### Post by mips on 2006-09-27
Thx. Unfortunately it is cli based. While looking at it I also came across:

[http://dfast.sourceforge.net/](http://dfast.sourceforge.net/)

I'll give them both a try.

---

### Post by croak77 on 2006-09-27
> **mips said:**
> Thx. Unfortunately it is cli based. While looking at it I also came across:



You mean thank god it's cli based ;)

---

### Post by kpkeerthi on 2006-09-27
If you like firefox use the DownThemAll! extension. I'm using it and can't be any happier. 
[https://addons.mozilla.org/firefox/201/](https://addons.mozilla.org/firefox/201/)

I tried d4x but somehow felt very cartoonish to me.

---

### Post by user1397 on 2006-09-27
thats weird.  using bittorrent, i get download speeds of like max 450 kbps in windows **and **linux.

---

### Post by ember on 2006-09-27
I agree with kpkeerthi, DownThemAll is very useful for downloading - I use it both in Windows and Linux.

---

### Post by richbarna on 2006-09-27
> **mips said:**
> I never seem to get good download speeds in ubuntu. Using D4X or WGET simply does not give me the same performance as say GetRight in windows.

With getright i have 5 simultanious segmented downloads of the same files. it literally maes out my adsl connection (384kb/s) to the point that i even battle to just browse the net.

In ubuntu it does not really get better than say 200kb/s.

If I download ISO's i use windows as i find linux to slow.

How can i improve this ???

If the isos are available as a torrent download, I use ktorrent.

---

### Post by mips on 2006-09-30
I tried compiling from source, but I must be doing something wrong or missing dependancies.

**Anybody got a deb ???**

I see you can plug this into other download utils which is cool.



> **croak77 said:**
> aria2

[http://aria2.sourceforge.net/](http://aria2.sourceforge.net/)

```

aria2 has  segmented downloading engine in its core. It can download one file from multiple URLs or multiple connections from one URL. This results in very high speed downloading, very much faster than ordinary browsers.
 As of 0.3.0 release, It can also download BitTorrent files.
 We implemented this engine in single-thread model. The architecture is very clean and easy to extend.
 
 Unlike Aria, which has GTK+ interface, aria2 provides command-line interface only. But GUI-lessness brings lower resource requirement. The physical memory usage is typically 3MB(normal HTTP/FTP downloads) to 5MB(BitTorrent downloads). 
 As of 0.7.1 release, aria2 supports asynchronous DNS using c-ares or ares. This can improve segmented download performance, especially in Metalink download. 

Command-line interface
Download files through HTTP/HTTPS/FTP/BitTorrent
HTTP Proxy support
FTP through HTTP Proxy
HTTP BASIC authentication support
HTTP Proxy authentication support
Segmented downloading
Cookie support(currently aria2 ignores "expires")
Run as a daemon process.
Selective download in multi-file torrent
BitTorrent Fast extension support
Metalink version 3.0 support(HTTP/FTP/BitTorrent)
```

---

### Post by skymt on 2006-09-30
> **mips said:**
> I tried compiling from source, but I must be doing something wrong or missing dependancies.

**Anybody got a deb ???**

I see you can plug this into other download utils which is cool.

What errors do you get when you try to compile?

---

### Post by croak77 on 2006-09-30
Aria2 is in Raphink's unofficial packages for Ubuntu

[http://www.raphink.net/ubuntu/](http://www.raphink.net/ubuntu/)

---

### Post by Josh1 on 2006-09-30
> **mips said:**
> I never seem to get good download speeds in ubuntu. Using D4X or WGET simply does not give me the same performance as say GetRight in windows.

With getright i have 5 simultanious segmented downloads of the same files. it literally maes out my adsl connection (384kb/s) to the point that i even battle to just browse the net.

In ubuntu it does not really get better than say 200kb/s.

If I download ISO's i use windows as i find linux to slow.

How can i improve this ???
Prozilla. Works just like reget for windows.

---

### Post by mips on 2006-09-30
> **croak77 said:**
> Aria2 is in Raphink's unofficial packages for Ubuntu

[http://www.raphink.net/ubuntu/](http://www.raphink.net/ubuntu/)

Thx, they are not the latest but I'll have a look.

---

### Post by mips on 2006-09-30
> **skymt said:**
> What errors do you get when you try to compile?

I'll post the output of ./config & make tomorrow.

---

### Post by mips on 2006-10-01
Attached find output of ./configure & make...

---

### Post by slimdog360 on 2006-10-01
there is also kget, you can make it the default dl manager in konqueror.

---

### Post by mips on 2006-10-01
> **slimdog360 said:**
> there is also kget, you can make it the default dl manager in konqueror.

As far aas i know kget does not support segmented downloading. I have used it before though.

---

### Post by croak77 on 2006-10-01
> **mips said:**
> Attached find output of ./configure & make...

You need libxml 2.6.26 or greater.

---

### Post by mips on 2006-10-01
> **croak77 said:**
> You need libxml 2.6.26 or greater.

I have 2.6.24. Where would I find 2.6.26 ?

---

### Post by skymt on 2006-10-01
> **mips said:**
> I have 2.6.24. Where would I find 2.6.26 ?

Edgy has .26. If you don't want to upgrade yet, your best option is probably to [compile it yourself](http://xmlsoft.org/).

---

### Post by mips on 2006-10-01
> **skymt said:**
> Edgy has .26. If you don't want to upgrade yet, your best option is probably to [compile it yourself]("http://xmlsoft.org/").

I think I'll wait for edgy then or try the older deb in the meantime.

---

### Post by mips on 2006-10-17
wxDownload Fast does the job just fine for me so far.

I also have aria2 installed but have not used it much so cannot comment right now.

Where did I get them from ? [http://www.getdeb.net/](http://www.getdeb.net/)

---

### Post by antini on 2006-12-10
[aria2]("http://aria2.sourceforge.net") is in feisty. There's .debs for [wxDownload Fast]("http://dfast.sourceforge.net") on its download page too.

The new version of KGet in KDE4 will support segmented downloading as well.

Also, check out [Metalink]("http://www.metalinker.org") which is a file used by download managers just for this sort of thing.

---

### Post by antini on 2007-07-23
[DownThemAll!]("http://www.downthemall.net/main/install-it/downthemall-10-beta/") is a Firefox extension that does really fast multithreaded downloads.

---

### Post by kvonb on 2007-07-23
> **mips said:**
> wxDownload Fast does the job just fine for me so far.

I also have aria2 installed but have not used it much so cannot comment right now.

Where did I get them from ? [http://www.getdeb.net/](http://www.getdeb.net/)

Hey, thanks for that link to GetDeb mips, really nice stuff :)

---

### Post by mips on 2007-07-23
> **kvonb said:**
> Hey, thanks for that link to GetDeb mips, really nice stuff :)

No problem ;)  Where have you been as that site has been around for a while.

---

### Post by kvonb on 2007-07-23
> **mips said:**
> No problem ;)  Where have you been as that site has been around for a while.

The older I get, the less I see, or want to see :D

---

