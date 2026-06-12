---
title: "Best practices for setting up a home file/print server?"
date: 2009-12-22
forum: Server Platforms
---

### Post by MerlinsLair on 2009-12-22
Hi all,

I'm researching into setting up one of my desktops as a home file/print server with no internet access. Just accessible from inside my home network only. I've been trying to get a handle on what all is needed doing and so forth but keep running into some confusion.

What I'm using: Lenovo h210 desktop w/ 320 gb HD (will become the server)
What will be accessing it: LM8 laptop, Vista laptop and a Win7 box
Devices involved: DSL modem and DLink DIR-655 router (wireless)
Would prefer absolute security for the server to allow only the machines on the network.

I'm fair with the command line more or less but would prefer a GUI to operate from as performance issues resulting from that aren't a problem really as the GUI would only be used for initial setup. Preferable but not required.

What I've been reading here and there has been both specific and non-specific so that's why I'm posting this to get some inside advice for a n00bie server installer.

I would like to use the Ubuntu 8.04 LTS server version for stability and have been reading the tutorials and what not. I've already struck out once on my first attempt so to help alleviate too many more failures, what would be the best way to accomplish what I'm trying to do here?

---

### Post by Queue29 on 2009-12-22
For the print server having all those GUI packages aren't necessary; all the configuration is done from a browser through the cups web interface. The hard part is making sure your printer has working drivers.

---

### Post by bpalone on 2009-12-22
Have you considered just setting up a Samba Server.  It will handle the Win boxes as well as the Linux boxes very easily.  Security can be pretty much as tight or loose as you want it.

Here is a link to a pretty good article on setting up a Samba Server: [http://www.melbpc.org.au/pcupdate/2403/2403article7.htm]("http://www.melbpc.org.au/pcupdate/2403/2403article7.htm")

---

### Post by MerlinsLair on 2009-12-23
Thanks for the link and advice. I'll check this out and see what all is involved. ;)

Update: This seems to be what I'm looking for. I'm going to give it a go in the next day or two. Probably after the Christmas holiday. Crazy around here now. Thanks bpalone for the heads up on the article. I'll report back asap and fill you in on the results of my installation. :)

---

### Post by bpalone on 2009-12-23
Another source of info on setting up a Samba Server is Linux Journal.  The Paranoid Penguin column covered setting one up over two or three months.  I would imagine that you could probably see the articles now on-line. 

[http://linuxjournal.com](http://linuxjournal.com)

---

### Post by msw on 2009-12-23
Hi, first post here on the forums. I am the author of the Samba Setup guide which can be [found here]("http://samba.netfirms.com/"). This tutorial (soon to be updated) will assist you in setting Samba as a file server.

Any questions, let me know.

---

### Post by MerlinsLair on 2009-12-23
Again, thanks for the help with this. It's much appreciated. Best wishes to you and yours this Holiday Season. :D

---

### Post by kewlrichie on 2009-12-24
You can do ubuntu server with the web based frontend called Webmin or you can use another web based frontend called eBox [http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server]("http://www.howtoforge.com/running-a-file-and-print-server-with-ebox-on-ubuntu8.04-server")

---

