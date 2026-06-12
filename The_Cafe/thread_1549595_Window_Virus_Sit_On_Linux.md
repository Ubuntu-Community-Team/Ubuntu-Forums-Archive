---
title: "Window Virus Sit On Linux"
date: 2010-08-10
forum: The Cafe
---

### Post by Khakilang on 2010-08-10
I know Linux is immune to Window virus and I am happy for it. But will it sit in a Linux box just waiting to infect other Window users when you connect to the internet or through other media like pen drive or CD/DVD? I haven't come across any virus since I use Linux but just wondering whether Window virus is in my computer. If so how do I check it? I have ClamAV installed. Does it check for Window virus or is it just Linux virus? So far scanning has coming out nil. I don't want my Window friend complaining that I have virus and ask me to clean my computer knowing very well my computer is not infected by Window virus.
;););)

---

### Post by 1roxtar on 2010-08-10
ClamAV detects and cleans Windows viruses.  It is a useful tool to scan programs and files that could potentially infect a Windows computer through flash drives.

---

### Post by teKro on 2010-08-10
From what I've read, ClamAV isn't a very good antivirus program. How-to Geek did an article on scanning for windows viruses on Linux. [Article]("http://www.howtogeek.com/howto/14434/scan-a-windows-pc-for-viruses-from-a-ubuntu-live-cd/"). At the end they have a list of some antivirus software, most of which are popular in Windows. AV-Comparatives did a test on a handful of antivirus software a few months back. [Article]("http://blogs.pcmag.com/securitywatch/2009/12/av-comparatives_rates_anti-mal.php"), I would recommend using the Linux version of Avast, Avira or Nod32 since they ranked the highest out of the software listed on the How-to Geek article. However, I am not sure if their Linux counterparts would rank just as high as the their Windows ones.

---

### Post by NightwishFan on 2010-08-10
There is a package for a GTK GUI as well.
[Install Clam GTK]("apt://clamtk")

[http://packages.ubuntu.com/lucid/clamtk](http://packages.ubuntu.com/lucid/clamtk)

---

### Post by JustinR on 2010-08-10
> **Khakilang said:**
> I know Linux is immune to Window virus and I am happy for it. But will it sit in a Linux box just waiting to infect other Window users when you connect to the internet or through other media like pen drive or CD/DVD? I haven't come across any virus since I use Linux but just wondering whether Window virus is in my computer. If so how do I check it? I have ClamAV installed. Does it check for Window virus or is it just Linux virus? So far scanning has coming out nil. I don't want my Window friend complaining that I have virus and ask me to clean my computer knowing very well my computer is not infected by Window virus.
;););)

Everyone completely avoided your first question! No, a windows virus doesn't sit on a linux box waiting for a windows user - windows virus' don't run on linux, so the windows user would have to directly open the virus from windows to be infected.

---

### Post by MaxIBoy on 2010-08-10
If there was an infected file on a Linux machine, and that file got moved onto a Windows machine, then that file is still infected and still dangerous for Windows users. 

ClamAV is mainly intended for mail servers and other Linux machines which pass high volumes of data onto Windows machines.

---

### Post by nmaster on 2010-08-10
you should read this: [https://docs.google.com/viewer?url=http://www.cs.berkeley.edu/~hilfingr/security-diatribe.pdf&embedded=true&pli=1](https://docs.google.com/viewer?url=http://www.cs.berkeley.edu/~hilfingr/security-diatribe.pdf&embedded=true&pli=1)

its a bit old, but this professor knows what he's talking about.  he's a bit of a legend.  here's his website for more info: [http://www.cs.berkeley.edu/~hilfingr/](http://www.cs.berkeley.edu/~hilfingr/)

---

### Post by lisati on 2010-08-10
> **MaxIBoy said:**
> If there was an infected file on a Linux machine, and that file got moved onto a Windows machine, then that file is still infected and still dangerous for Windows users. 

ClamAV is mainly intended for mail servers and other Linux machines which pass high volumes of data onto Windows machines.

+1
The only AV setup I have on any of my Ubuntu installations is ClamAV, as part of my email server's scanning for incoming and outgoing emails. It's just one part of what can be done to help avoid problems.

---

### Post by HermanAB on 2010-08-10
Anyhoo, ClamAV works perfectly fine.  Of course other vendors will denegrate it, since they want to sell you their inferior solutions.

---

### Post by Lucifer The Dark on 2010-08-10
ClamAV found an infected file on my system that other Windows based virus checkers missed, so if someone tells you ClamAV is rubbish don't believe them, try it out for yourself.

---

