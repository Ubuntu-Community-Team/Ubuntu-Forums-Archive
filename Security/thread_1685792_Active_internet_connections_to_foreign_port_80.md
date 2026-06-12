---
title: "Active internet connections to foreign port 80"
date: 2011-02-11
forum: Security
---

### Post by coverup1128 on 2011-02-11
Right after booting my Lucid netbook, I see some internet connections to a foreign servers' port 80:

$ netstat -tan
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.13:53197      119.161.91.25:80        ESTABLISHED
tcp        0      0 192.168.0.13:53196      119.161.91.25:80        ESTABLISHED
tcp6       0      0 ::1:631                 :::*                    LISTEN     

The IP address and local ports change on reboot, but I don't see anything that could trigger connection. Firefox is not running. 

How can I find out what causes these connections? On my other Linux systems (Mandriva, KDE), I never have any connections if Firefox is not running. 

Thanks

---

### Post by iissmart on 2011-02-11
use netstat -p to see the PID and name of the program for each connection, and/or nslookup to see who's IP that is.

Running a whois/nslokoup on that IP says you're connecting to vocus.com.au

---

### Post by movieman on 2011-02-11
Could well be the system checking for updates. You could try connecting to that port from firefox and see what's there.

---

### Post by coverup1128 on 2011-02-11
Thanks, guys.

netstat -p says that this is clock-applet. Why would clock-applet access internet? 

Tried [http://119.161.91.25:80](http://119.161.91.25:80) from firefox, and got "Invalid URL The requested URL "/", is invalid. Reference number #9.155a177.blah-blah"

Does this make any sense to you?

---

### Post by iissmart on 2011-02-11
I don't think clock-applet has any reason to connect to the internet. It's not NTP, because that would be on UDP port 123.

---

### Post by Agent ME on 2011-02-11
The clock applet can download weather information.

---

### Post by coverup1128 on 2011-02-12
How can I configure firestarter to prevent clock-applet from accessing the internet?

---

### Post by coverup1128 on 2011-02-15
bump?

---

### Post by tgm4883 on 2011-02-15
What if you right click the clock applet, go to preferences, then uncheck "show weather" and "show temperature"

---

