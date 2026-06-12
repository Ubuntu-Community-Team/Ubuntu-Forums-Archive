---
title: "Monitor system health. Temp/process/cpu etc."
date: 2009-10-27
forum: Server Platforms
---

### Post by mike909 on 2009-10-27
Trying to monitor system health. Specifically, I'm interested in temp, hdd and memory leaks. Looking for someone to poke holes in my setup...any suggestions appreciated:

    * smartmontools for HDD health status. apt-get install smartmontools & modify /etc/smartd.conf with the following, which should Monitor all attributes, enable automatic online data collection, automatic Attribute autosave, and start a short self-test every day between 2-3am, and a long self test Saturdays between 3-4am. It will syslog temp changes >=2 C and email me if temp. goes above 50 C.
          * /dev/sda -a -o on -S on -s (S/../.././02|L/../../6/03) -W 2,50,50 -m <your_email_address>
          * /dev/sdb -a -o on -S on -s (S/../.././02|L/../../6/03) -W 2,50,50 -m <your_email_address>
    * /etc/default/smartmontools, uncomment the &#8220;#start_smartd=yes&#8221; line  & change 1800 in "smartd_opts="--interval=1800" to the interval you want to run smartmontools on your drives. ( I made it 300 seconds)
    * need to reconfigure exim with
          * sudo dpkg-reconfigure exim4-config (if that fails, apt-get install exim4)
    * Specify this machine as a "smarthost" with no local mail. Enter ISP's outgoing mail server. 'Mail Name' should be the domain mail is sent from. Other options not important.

you can test smartd's ability to email you by specifying "-M test" as one of the switches on one of those config lines.

    * lm-sensors for cpu temp. apt-get install lm-sensors. Issue the following:
          * sudo sensors-detect
          * set up a cron job to run the following script which executes "sensors", grep's for the cpu0 temperature, and emails me if it's >=50 C every 5 mins. create file in /etc/cron.d/ with the following syntax:
    * # m h  dom mon dow   command
    0,5,10,15,20,25,30,35,40,45,50,55 * * * * root /path_to_script/cpu-tempcheck.sh

-----------cpu-tempcheck script----------
#!/bin/bash
#defines the variable 'temp'
temp=`sensors | egrep 'Core0' | sed -e 's/Core0\ Temp:\  +//' -e 's/...C//'`
if [[ "$temp" -ge "50" ]]; then
        echo $temp | mail -s high-cpu <your_email_address>
        exit
fi
-------------endscript---------------

    * alternatively you could use: /usr/share/doc/lm-sensors/examples/daemon/healthd.sh but it won't start for me b/c I have alarms. (can be seen w/ "sensors")

    * for video card temp, set up a cron job to run the following once per hour, and email me if above 60 C. ( similiar to the cpu-temp script)

----------gpu-tempcheck script-----------
#!/bin/bash
#defines the variable 'temp'
temp=`DISPLAY=:0.0 nvidia-settings -q [gpu:0]/GPUCoreTemp | grep "Attribute" | sed -e "s/.*: //g" -e "s/\.//g"`
if [[ "$temp" -ge "60" ]]; then
        echo $temp | mail -s high-gpu <your_email_address>
        exit
fi
--------endscript---------

    * monit for any process that spikes for a while, and/or memory leaks. apt-get install monit.
    * To have daemon check every 20 mins. edit /etc/default/monit set "startup=1"
    * uncomment the following lines, in /etc/monit/monitrc

--------------------
set daemon 20
set logfile syslog facility log_daemon
set mailserver  <outgoing mail server here>              # primary mailserver
set mail-format { from: <valid_domain_from_email_address> }
set alert <to email_address here>                    # receive all alerts
set httpd port 2812 and
use address localhost  # only accept connection from localhost
allow localhost        # allow localhost to connect to the server and
allow admin:monit      # require user 'admin' with password 'monit'
  check system mythbox.donkey.net
    if loadavg (1min) > 4 then alert
    if loadavg (5min) > 2 then alert
    if memory usage > 75% then alert
    if cpu usage (user) > 70% then alert
    if cpu usage (system) > 30% then alert
    if cpu usage (wait) > 80% then alert
-----------------

---

### Post by windependence on 2009-10-27
If you're not running a GUI on your server, you can run Gkrellm over ssh using this tutorial:

[http://www.stearns.org/doc/network-monitoring.v0.1.1.html](http://www.stearns.org/doc/network-monitoring.v0.1.1.html)

-Tim

---

### Post by mike909 on 2009-10-27
I'm running gnome, but am not usually in front of the machine. The alerting would have to be via email...not from viewing a window, as is the case with "Gkrellm". 
Thanks for the suggestion though.

---

### Post by windependence on 2009-10-28
In that case you have a ton of choices. Take a look at Zabbix for starters. I'm sorry, I completely misunderstood what you were looking for.

-Tim

---

### Post by mike909 on 2009-10-28
Tim,
Thanks for the link, that looks like a very power program for server/network device monitoring. Not really what I'm after in this situation though. 
To give some more direction, I'm trying to monitor a system to prevent or diagnose any possible hardware failures. HDD is a big one Ive been hit by many times, and heat can kill anything. I know I can monitor these sort of things with the tools outlined in the OP, but being Linux, I'm sure there are a couple hundred other ways to do it. My way's seem to be "cludgy", and I figured monitoring these sort of things would be a common goal of many overclockers, gamers, server admins etc.
Hope that clears up what i'm after, and again thanks for the suggestions. If you still think Zabbix may fit the bill, I'll give it a shot...though it seems to be more of a platform for monitoring devices, other than the pc it's running on.

---

### Post by mike909 on 2009-11-02
updated OP with what I'm doing. Changed a couple things during the process, but I think this should work for detecting hdd failures, temperature issues (cpu, gpu or hdd) and process crashes, mem-leaks etc.

---

