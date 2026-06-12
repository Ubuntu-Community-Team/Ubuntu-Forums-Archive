---
title: "PXE Boot Problems"
date: 2009-06-13
forum: Server Platforms
---

### Post by magicman5421 on 2009-06-13
I recently configured my server (Xubuntu 8.04) as a PXE server. I've set it up with DHCP and everything, and when I try to netboot the computer gets an IP address, waits at TFTP..., then gives me the error "PXE-E32: TFTP open timeout"
How can I check that TFTP is indeed running on my server, and that computers on my network can access it?

---

### Post by cariboo on 2009-06-14
To check if tftp is running, at the prompt type:

```
ps ax | grep tftp
```

and to check if the proper port is open, install nmap, it is in the repositories, then at the prompt type:

```
nmap localhost
```

---

### Post by magicman5421 on 2009-06-14
TFTP is running, but NMAP showed no port for tftp open.
How do I open a port for TFTP?

---

### Post by dmm1983 on 2009-06-26
these links my help with pxe errors

[normal google search]("http://www.google.com.au/search?q=%22PXE-E32%3A+TFTP+open+timeout%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a")

[http://www.bootix.com/support/problems_solutions/pxe_e32_tftp_open_timeout.html]("http://www.bootix.com/support/problems_solutions/pxe_e32_tftp_open_timeout.html")

[http://h18000.www1.hp.com/products/servers/management/rdp/knowledgebase/00000138.html]("http://h18000.www1.hp.com/products/servers/management/rdp/knowledgebase/00000138.html")

[URL="http://www.google.com/linux?hl=en&q=%22PXE-E32%3A+TFTP+open+timeout%22&btnG=Search"]http://www.google.com
/linux?hl=en&q=%22PXE-E32%3A+TFTP+open+timeout%22&btnG=Search[/URL]

[http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q="PXE-E32%3A+TFTP+open+timeout"]("http://www.google.com/cse?cx=012285703143635244993:i9yr8qlpb18&q="PXE-E32%3A+TFTP+open+timeout"")

---

