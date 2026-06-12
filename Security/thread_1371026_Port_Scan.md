---
title: "Port Scan"
date: 2010-01-02
forum: Security
---

### Post by small_potato on 2010-01-02
I just did a port scan on my ubuntu 9.10 system. Here is the result:

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2010-01-02 19:45 PST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 999 closed ports
PORT    STATE SERVICE
631/tcp open  ipp

I don't understand why there are 2 IP address. Why do i have a port open? How do i close it. BTW, i access Internet via school network. 

Cheers.

---

### Post by FuturePilot on 2010-01-02
That seems to be normal if you use "localhost" as your target. IPP is part of CUPS but by default it's not listening for any external connections

---

### Post by CharlesA on 2010-01-02
Are you scanning it from itself?

Port 631 is Internet Printing Protocol.

---

### Post by rookcifer on 2010-01-03
As was said, ipp is for CUPS and is bound locally (e.g. it is not listening to the outside world).  A better way to check what ports are open is to run:

```
sudo netstat -tunpvl
```

Under the "local address" column, you will see something like:
```

127.0.0.1:631
```

The 127.0.0.1 is the IP address the open port is bound to.  If you see 0.0.0.0:631, that would mean it is listening to the Internet at large.  So, in other words, any time you see 127.0.0.1:<port #> you are safe.

By default, Ubuntu should have no open ports listening to the Internet at large.

---

### Post by Project PWNED on 2010-01-03
apt-get remove cups

---

### Post by tubezninja on 2010-01-03
> **Project PWNED said:**
> apt-get remove cups

Good luck printing after that one!

---

### Post by Giant Speck on 2010-01-03
> **Project PWNED said:**
> apt-get remove cups

Because printing is overrated.

---

### Post by CharlesA on 2010-01-04
Makes me wonder if you would need cups to print to a PDF...

---

### Post by BkkBonanza on 2010-01-04
> **CharlesA said:**
> Makes me wonder if you would need cups to print to a PDF...

I think that depends on how it's done. OpenOffice has some PDF functions built in and so I think it may work without CUPS. I often use the PDF virtual printer driver though and it definitely installs in CUPS.

---

### Post by CharlesA on 2010-01-04
> **BkkBonaza said:**
> I think that depends on how it's done. OpenOffice has some PDF functions built in and so I think it may work without CUPS. I often use the PDF virtual printer driver though and it definitely installs in CUPS.

Yup you are right. I was thinking about something like cutepdf, but it does require CUPS, or more accurately CUPS-pdf.

[Source.]("http://www.linux.com/archive/articles/61826")

---

### Post by FuturePilot on 2010-01-04
cups-pdf isn't really necessary anymore. Most GTK programs are now using gtkprint which can output to PDF (and PS) directly without using CUPS. One of the exceptions to this is OpenOffice which is still using its own printing interface, but it has an export to PDF feature anyway.

---

### Post by BkkBonanza on 2010-01-04
I hadn't noticed that but I see most programs have a "Print to File" option built in that supports pdf. I expect that's what you mean. So looks like I can remove cups-pdf now. Cool.

Maybe that's why they kept trying to deprecate it on every upgrade cycle. Hmmm.

---

### Post by FuturePilot on 2010-01-04
> **BkkBonaza said:**
> I hadn't noticed that but I see most programs have a "Print to File" option built in that supports pdf. I expect that's what you mean. So looks like I can remove cups-pdf now. Cool.

Maybe that's why they kept trying to deprecate it on every upgrade cycle. Hmmm.

That's exactly why

---

### Post by doas777 on 2010-01-04
network manager will somtimes repeatedly bind the loopback name (localhost) to differant IPs within the 127.255.255.255 block. usually 127.0.0.1 and 127.0.1.1.
this seems to have croped up about the same time everthing started adding ".local" to the end of host names.

---

