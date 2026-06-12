---
title: "how to search through packets"
date: 2008-06-19
forum: Security
---

### Post by hershey101 on 2008-06-19
Hi,
I am new at UNIX and programing in general and only have a basic knowledge of C++. I am helping out with some research at a college and was given the task to sort through captured packets via IP addresses. I was wondering if anyone could help me with writing a code which filters through pcap files by ip addresses and then records the timestamps. I know a few programs that do this type of thing such as WireShark but they take up too much memory when analyzing gigabytes of data and that is why I am looking to write a relatively simple code which just gets my task done and gathers data for me. Please email me at [email]hersh92@gmail.com[/email], any help is appreciated.

---

### Post by HalPomeranz on 2008-06-19
You should use tcpdump for this.  It reads pcap data and can filter on pretty much anything you want, including IP addrs, and dump text output.  "man tcpdump" for more info

---

### Post by robklg on 2008-06-20
Your suggestion to seek help through e-mail is a bit disappointing. It's a public forum you know.

Well, take a look at libpcap. It's not that hard...

If you want SIMPLE, then try Python with any of these modules:

python-libpcap
python-pcapy

The latter sounds the easiest...

Good luck.

---

### Post by hershey101 on 2008-06-23
I was thinking something more along the lines of using a separate text file for the IP addresses and some how use the 'tcpdump -r myfile.pco -w out.pcap ip src "1.2.3.4"' command to make it so that it matches the IPs with the text file. Also I am only interested in the time stamps and don't require the rest of the details of the packets, so it would be helpful if I wrote a code which filters through the clutter and gives me only the time stamps.
Thank You

---

### Post by HalPomeranz on 2008-06-23
```

tcpdump -nr myfile.pco | grep -Ff ipaddrfile | awk '{ print $1 }'

```

This should dump the packet capture into text ("tcpdump ..."), match only the IP addresses in ipaddrfile ("grep ..."), and print only the timestamps ("awk ...").

---

