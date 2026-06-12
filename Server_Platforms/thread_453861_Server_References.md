---
title: "Server References"
date: 2007-05-24
forum: Server Platforms
---

### Post by linuxhippy on 2007-05-24
For over a year I've been running a gnump3d server that creates a log entry every time somebody visits my server that indicates their IP address and OS used. I've seen on software that generates statistics out of these log files that it is able to tell where a visitor found your server (a search engine for example). I think this information is found in the first entry of my log file. Here's a recent example:

131.107.0.72 - - [21/May/2007:20:45:49 +0000] "GET /" 200 11110 "-" "Mozilla/4.0 (compatible; MSIE 7.0; Windows NT 5.2; SV1; .NET CLR 1.1.4322; InfoPath.2; .NET CLR 2.0.50727; .NET CLR 3.0.04506.30)"


I don't recognize this visitor that ip2location.com says is in Redmond, WA from Microsoft Corp (ISP). My server has been getting spidered over the last year by MSN, Google, and Yahoo.

Is there a way of knowing where visitors found your server from the log file?

---

### Post by ninocass on 2007-05-24
you could set up the log files to include the HTTP referer.

Or you could use stat counter: [http://www.statcounter.com/](http://www.statcounter.com/) i use it myself and its a bloody good job L:)

---

### Post by linuxhippy on 2007-05-31
That worked real well...I wanted to use for a week to see what it did.  I like the country summary report :)  Thank you!

---

