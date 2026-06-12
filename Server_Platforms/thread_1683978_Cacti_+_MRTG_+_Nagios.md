---
title: "Cacti + MRTG + Nagios"
date: 2011-02-08
forum: Server Platforms
---

### Post by OneDreamCloser on 2011-02-08
hello all,

could you please tell me how much time it will take setting up (for the first time) :
MRTG, Cacti and Nagios on a network with ~25 routers and ~50 switches 
(using the rrd_tool and snmp, of course) ?

i am a bit familiar with perl and shell scripting.

thanx in advance

---

### Post by elico on 2011-02-08
you will might want to check this specific "CactiEZ"at:
[http://cactiez.cactiusers.org/](http://cactiez.cactiusers.org/)
i have used it once and it's very nice to use.
also:
[https://wiki.fourkitchens.com/display/PF/Stack+installation+on+CentOS+5#StackinstallationonCentOS5-Nagios%28onlyformonitoringserver%29](https://wiki.fourkitchens.com/display/PF/Stack+installation+on+CentOS+5#StackinstallationonCentOS5-Nagios%28onlyformonitoringserver%29)


but in some cases i must tell you that PRTG is working like a charm.

if you have the data on the devices such as ip's and all the SNMP in place it will take you couple of hours of first setup and a week or less to make sure that your system is working fine.

---

### Post by OneDreamCloser on 2011-02-09
thanx a lot, but may i ask :
 
0. from what i have googled so far, the best thing to do is to have cacti polling the data, and then, through passive interfaces, feed these data in Nagios. is that correct ?
1. why is the above a better solution than having nagios actively polling the devices and fill in the records in the rrd_tool ?
2. and last, which is the simplest way of plotting the statistics in real-time (without requesting the plots) ?
 
thank you in advance :)

---

### Post by elico on 2011-02-09
well this specfic piece of software is making job efficient and easy for you.
if you have other needs like realtime usage and not sampling you will might need to do some homework.
for 1. this distro have everyhing in it.. nagios with alll its basic features with many plugins.
rrd tool is only to make the grapghs..
if you now how to work with cacti and nagios you wont have any problem using it efficiency.
for 2. the only option in real time is using snmp with software that support it.
in this scale of 50 Switches and 25 routers if you do have time to expirement and test different setups then just make a nice table on any database with basic info before starting any setup so after you will have that and a runing sampling system you can try other methods.

what do you mean simplest way of plotting in realtime?
there are couple of tools such as rrd_tool that might give you the result.
what nice about cacti is that you can store the data and present it using any template you like on the fly.

---

### Post by OneDreamCloser on 2011-02-09
thank you elico for the reply,

what i mean when i say plotting in real-time, is that i am wondering
if there is a plugin or something else that enables me to plot specific data
without pushing a button and create the graph, but having the graph refresh itself.
i am thinking doing the latter using gnuplot+perl, but i do not know if that is possible through a plugin or not ?

---

### Post by elico on 2011-02-09
the graph is refreshed by itsef in the system.
what you need is somthing else... page refresing.
in cacti you should have this option somewhere and if not you can always add some small script to do it for you.

---

### Post by OneDreamCloser on 2011-02-10
thank you :)

---

