---
title: "Monitoring bandwidth"
date: 2012-02-15
forum: Server Platforms
---

### Post by iainjames88 on 2012-02-15
Hi,

Can anyone recommend a bandwidth monitor (preferably with a PHP front end)? I've Googled around and there seems to be quite an array of tools available for the job but can anyone suggest one they have used and like?

Thanks :)

---

### Post by ajgreeny on 2012-02-15
I use vnstat, and have it display through conky on my desktop.  It is versatile and very useful to me though not php.

Here's a screenshot of what it shows for me using the following in my .conkyrc file.
```
# To make vnstat run as user use command "sudo chmod u+s /usr/bin/vnstat"
#
            DOWN:                    $alignr UP:        
${color #56073D}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $2 $3}'}${color #56073D}${alignr}Today: ${color #DE0084}${execi 300 vnstat | grep "today" | awk '{print $5 $6}'}
${color #56073D}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${color #56073D}${alignr}Week:  ${color #DE0084}${execi 300 vnstat -w | grep "current week" | awk '{print $6 $7}'}
${color #56073D}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${color #56073D}${alignr}Month: ${color #DE0084}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
```

---

### Post by richardjh on 2012-02-15
I would recommend that if you are going to monitor servers you should learn [Nagios]("http://www.nagios.org/about/overview/"). 

It can be difficult to get started but once you understand how the configuration works it is easy to then add new hosts and services, configure all aspects of reporting and alerts. It is well regarded by SysAdmins so learning it is not going to be a wasted effort if you are in that field.

There is a simple quick start guide at [http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html](http://nagios.sourceforge.net/docs/3_0/quickstart-ubuntu.html) which is a good place to start.

Although the front end isn't PHP, it does provide a web interface.

---

### Post by richardjh on 2012-02-15
Sorry. It is late and I am sleepy. Whilst Nagios is great and all, I am thinking of the wrong thing.

I use [MRTG]("http://oss.oetiker.ch/mrtg/") to graph resources.

---

### Post by pctx on 2012-02-17
If we're talking one machine, Webmin does the trick.  In the options you can tell it to monitor bandwidth of which gives you a nice ingress/degress bar of bandwidth consumed.  If you're talking multi-machine portal of bandwidth, MRTG for sure.

---

### Post by CivilizationII on 2012-02-17
excepted the php binding, dstat is a perfect tool for monitoring network bandwith

---

