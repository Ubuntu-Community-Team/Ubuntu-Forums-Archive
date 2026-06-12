---
title: "Monitor who's connected to the server"
date: 2011-04-08
forum: Server Platforms
---

### Post by dvdme on 2011-04-08
Hi, 

I'm running ubuntu server 10.10 on a virtualbox in order to do some web develop and learn more. 
At this time I have xampp with apache and mysql running and I'm doing some experiments with wordpress and joomla.

Anyway, what I'd like to know is if there is a way to check who's connected to my server machine trought the command line. 
Before, I had all this installed on a windows 7 machine (altough I have to say, everything runs faster on ubuntu server...) and I used wireshark for this puporse. 
I though about tcpdump but it would be hard to monitor on the command line... I'd like a solution with a simpler report.

Any sugestions?
Thanks!

---

### Post by rubylaser on 2011-04-08
You could just use netstat.

```
netstat -an --inet
```

---

### Post by BkkBonanza on 2011-04-08
2 tools come to mind for monitoring real time.

**iftop** will show realtime connections and bandwidth usage. It taps right into the interface to show some bar graph type stats.

**apachetop** will show what people are hitting right now. I don't recall if it has a mode to show who is hitting the server or not. It uses the logs to show change as it happens.

and netstat is always useful. You can run it under watch with a 2-5 second interval to view things as they change. Also it's useful when piped thru grep to remove stuff you don't want.

eg.
watch -n 2 -d 'netstat -nt |grep -P ":80.*ESTABLISHED"'

---

### Post by SeijiSensei on 2011-04-08
When you say "who is connected" does the machine allow remote logins?  Or are you just asking about Apache?

If you want to see an instantaneous snapshot of users running processes on your machine run

```
ps aux | awk '{print $1}' | sort | uniq | grep -v USER
```

Most of these will be system users like "postgres" or "www-data" that own the daemons for their respective services.

---

### Post by dvdme on 2011-04-08
Thank you all very much.

The ps command isn't quite what I was looking for. I wasn't looking for remote logins but for apache connections, for any machine who sent resquests to my server. 
(While on windows 7 with wireshark, I used a filter to only show http GET requests so that I could see machines who resquested to see my webpages.)

The netstat option does the trick I was looking for.

**iftop **looks like a great tool for what I want. I tested it it seams to be it. I'll definitely explore it more.

**apachetop** didn't worked right after install, it says there is no access.log available and I'll have to deal with that issue before testing.

EDIT:
Already solved the problem with **apachetop** the log file wasn't on the default location. 
Anyway this one also looks very good to me. **apachetop** and **iftop** will definitely do what I want.

Thanks!

---

