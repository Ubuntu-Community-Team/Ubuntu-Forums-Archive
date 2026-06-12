---
title: "Bandwidth"
date: 2008-04-19
forum: Server Platforms
---

### Post by mattc908 on 2008-04-19
How would I implement something that kept track of bandwidth being used by my server? and also track how much each page is being veiwed on my website? Doesnt have to be the same program.

---

### Post by gombadi on 2008-04-19
For bandwidth usage have a look at vnstat.
It can produce bandwidth usage data on an hourly, daily and monthly basis.

For web page stats have a look at awstats.

From the command line type 
```

apt-cache show vnstat
apt-cache show awstats

```

---

### Post by Dr Small on 2008-04-19
This sparked my curiosity, so I installed bandwithd.

---

### Post by conjur3r on 2008-04-19
It sounds like you are interested in your web statistics rather than the network as a whole.  If this is the case, install any number of web statistic programs (eg awstats), and it will provide you with information such as bandwidth, most requested pages, number of users, browsers, sessions, etc.

---

