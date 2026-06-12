---
title: "deploy.akamaitechnologies.com uploading large amounts of data  from my pc"
date: 2011-03-29
forum: Security
---

### Post by birdfoot on 2011-03-29
It seems when I have Firefox open, the following address uploads huge amounts of data. Does anyone know what this is

a96-17-164-169.deploy.akamaitechnologies.com  

I discovered it was uploading data by looking at the System Monitor taskbar app. I also used the program iftop, to investigate further. The uploading stops immediately after shutting down Firefox.

If anyone knows anything about what may be causing this, please let me know. Also it would be helpful if anyone knew a program that would tell me what program is uploading the data from my pc. I'm fairly sure it's firefox, but I'd like to confirm it.

---

### Post by bodhi.zazen on 2011-03-29
What is it uploading ?

Best capture a few packets , with tcpdump or wireshark.

---

### Post by cariboo on 2011-03-29
deploy.akamaitechnologies.com is who Microsoft uses to do most of their program uploads, I've never looked, but it wouldn't surprise me if they use it for updates too.

---

### Post by BkkBonanza on 2011-03-30
akamai tech. are one of the biggest content delivery / caching systems on the web. They are used by hundreds of big web companies to spread the load around the world and reduce latency for their pages. 

It would be unusual for you to be uploading to them as generally most uses are for improving download speeds. But there could be some reason for some service you use that you're just not aware is handled via their servers. You may want to disable all plugins and see if it stops. And if so, then enable them one by one until you see which one does it.

---

### Post by expcoderxrrg on 2012-08-09
Amazing I have too the Akamai Issue, they have a really smart technology to jump firewall restriction. I have make a white list for may firewall it mean nothing get out. This solution stop Akamai for some days, but now it is connected again jumping the firewall white list. Akamai install a new process server on my computer and send info to Akamai  server using different ip to my computer assigned ip to jump firewall. Akamai Issue have a proved advanced technologies to jump firewall.
 will try upload image proves

 More references:
 [http://www.matveev.se/net/akamai.htm](http://www.matveev.se/net/akamai.htm)
 

 [http://www.linuxquestions.org/questions/general-10/contact-at-akamai-akamaitechnologies-for-complaints-831481/](http://www.linuxquestions.org/questions/general-10/contact-at-akamai-akamaitechnologies-for-complaints-831481/)
 

 [http://ubuntuforums.org/showthread.php?t=1717448&highlight=akamai](http://ubuntuforums.org/showthread.php?t=1717448&highlight=akamai)

---

### Post by uRock on 2012-08-09
Old thread.

Thread Closed

---

