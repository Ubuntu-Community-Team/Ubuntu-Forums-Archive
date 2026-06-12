---
title: "wget uses text transfer for war file"
date: 2008-07-13
forum: Server Platforms
---

### Post by angelochen168 on 2008-07-13
Hi,

In a Ubuntu 7 server, wget uses text/plain mode to transfer Java's war file, here is an example, anyway to make it binary mode:


wget [http://homepage.ntlworld.com/richard_c_atkinson/jfreechart/jfreechart-sample.war](http://homepage.ntlworld.com/richard_c_atkinson/jfreechart/jfreechart-sample.war)

--02:37:44--  [http://homepage.ntlworld.com/richard_c_atkinson/jfreechart/jfreechart-sample.war](http://homepage.ntlworld.com/richard_c_atkinson/jfreechart/jfreechart-sample.war)
           => `jfreechart-sample.war'
Resolving homepage.ntlworld.com... 62.253.162.178, 62.253.162.10, 62.253.162.11, ...
Connecting to homepage.ntlworld.com|62.253.162.178|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,196,062 (1.1M) [text/plain]

100%[====================================================>] 1,196,062    699.47K/s             

02:37:48 (697.09 KB/s) - `jfreechart-sample.war' saved [1196062/1196062]

---

