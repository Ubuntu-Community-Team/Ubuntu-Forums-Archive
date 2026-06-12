---
title: "random high port numbers in jaunty"
date: 2009-05-02
forum: Security
---

### Post by }SoC{phenix on 2009-05-02
I recently put ubuntu Intrepid on my laptop, and then updated to jaunty when it became available.  I was running a port scan to make sure that there weren't any unwanted ports open when I found several high port numbers open, with their label as unkown.  These change every time I do a port scan, and I was wondering if I should be looking for a possible trojan, etc.  A sample of some of the port numbers that show up are:

33166
39714
45603
52755

I looked this up elsewhere in the ubuntu forums, and was told to try **sudo netstat -plantu.  **This command doesn't won't list any of these ports when tried.  Any help would be greatly appreciated.

-}SoC{phenix

---

### Post by cariboo on 2009-05-02
That is a bug in network tools, it has been sent upstream, but hasn't been repaired yet.

---

### Post by Roasted on 2009-05-02
Is this something Jaunty users should be concerned about?

---

### Post by cariboo on 2009-05-02
No, it's actually been around since hardy. I would suggest using a combination of nmap and zenmap for port scanning. They are both in the repositories.

---

### Post by Dr Small on 2009-05-02
> **cariboo907 said:**
> No, it's actually been around since hardy. I would suggest using a combination of nmap and zenmap for port scanning. They are both in the repositories.
It's been around for 3 ubuntu releases ((new release every 6 months) * 3 = 1 1/2 years) and hasn't been fixed? Maybe it's just because it's a low priority.

---

### Post by }SoC{phenix on 2009-05-02
Thanks a lot for the info, glad to know that it's just a bug.

---

### Post by Darin722 on 2009-09-26
I am seeing a similar event while watching traffic with wireshark.  My computer appears to be trying a dns lookup on my isp's mail server using random high port numbers???  Is this the same problem that you folks are discussing?

According to wireshark I'm sending a DNS packet: "Standard Query A Mail.clearwire-dns.net

the next packet is a response, DNS "Standard Query Response, No such name"

The source port then changes and the process repeats continuously.

---

### Post by rookcifer on 2009-09-26
> **cariboo907 said:**
> That is a bug in network tools, it has been sent upstream, but hasn't been repaired yet.

Link please.

---

### Post by cariboo on 2009-09-26
Here's the [link]("https://bugs.launchpad.net/gnome-nettool/+bug/257042") to my bug report, and the [Bugzilla]("https://bugzilla.gnome.org/show_bug.cgi?id=547598") report.

---

### Post by rookcifer on 2009-09-27
> **cariboo907 said:**
> Here's the [link]("https://bugs.launchpad.net/gnome-nettool/+bug/257042") to my bug report, and the [Bugzilla]("https://bugzilla.gnome.org/show_bug.cgi?id=547598") report.

If I understand correctly, this seems to be a flaw in Gnome's native port scan tool, right?  Not a flaw in nmap I assume?

I use Kubuntu so I have never seen this problem, but I hope they get it fixed soon enough.

---

### Post by cariboo on 2009-09-27
It is a flaw in gnome network tools, and not nmap. Gnome nettools work without the need to install nmap.

---

