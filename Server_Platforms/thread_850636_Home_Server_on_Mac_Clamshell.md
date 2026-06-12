---
title: "Home Server on Mac Clamshell"
date: 2008-07-05
forum: Server Platforms
---

### Post by panhandle on 2008-07-05
Hi,

I want to create a home LAN for my three or four computers. This will be insulated from all outside connections and really will be used for experimentation.

This must be done on the cheap, so I was thinking I might use my ancient Clamshell Mac for the server, as I neither want to buy a new or used server nor do I want to pay for all that power consumption.

So, my question: Can I use the latest Ubuntu server software? If not, which distribution then? Does anyone have experience with this? I've searched a fair bit for an answer but found very little help.

btw: 300mhz, 64 MB SDRAM. 6.0 GB HD.

--Thanks

---

### Post by cariboo on 2008-07-06
As long as you aren't running to many services it should be okay, I would add more ram if possible. I've got a G3 that I am using for a dhcp and security cam server in my shop and it works quite well it does have 256mb ram it came with 128MB and I upped it with another 128mb I had lying around as well as a 10GB hard drive. it is slow starting up, but once it's running it's not to bad.

Jim

---

### Post by someonestolemyname on 2008-07-06
Yeah, I can't see any reason why that shouldn't work. The server is really light on resources. My server is pretty decent (1.8ghz 128mb RAM). Definitely get more RAM if possible though. It might be noticeably slower with 64mb RAM (although still usable). As Jim said, not too many processes. Maybe LIGHTTPD instead of apache? I heard it uses less resources.

having a personal server rules.

Daniel

---

### Post by ixus_123 on 2008-07-06
I used to have a G3 366Mhz clamshell with 10GB disk and 320MB RAM running as my webserver.

I don't think Hardy has PPC support but dapper runs perfectly on it.

I ran a LAMP install to power a wordpress blog and Gallery2 software.  Gallery was a little slow but wordpress flew.

It was a great set up as it was totally quiet, would keep running on the battery when power was out, such as when we had building work that needed to be done.  It was great to also have a keyboard and screen on it, should you ever loose SSH.

I'd see if you can find a 512MB soDIMM for it, or 256MB and it should make a perfect home server. The only reason I decomisioned mine is becuase the hard disk got very noisy and they are a bit of a pain to change on clamshells

---

