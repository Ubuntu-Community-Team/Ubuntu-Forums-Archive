---
title: "Monitoring WideAreaNetwork status for disconnections"
date: 2013-05-19
forum: Ubuntu, Linux and OS Chat
---

### Post by welshmike on 2013-05-19
My apologies as this is not strictly a Ubuntu question.
My connection to my ISP, TalkTalk, disconnects for a minute or two several times a day.
So I've written a crude bash script shown below to keep a log of my public IP address.
I also show the contents of the log produced over a few seconds.

I'd really like to get the IP address on the same line as the date and time.
How may I do this in my script please?

_**My crude bash script **_
> 
#!/bin/bash

# wanstatus: Monitor WideAreaNetwork status for disconnections

# After testing make this script a startup application
# sleep 5 minutes (300 seconds)to be sure internet connection is established
#sleep 300
cd /home/mike/Documents
# set start name of wanstatus log (in Documents folder)
logfile="logfile"
logfile=wanstatuslog-$(date +%Y%m%d)-$(date +%H%M%S)
echo "Wide Area Network status log to record disconnections by change of IP address." >> $logfile
echo "==============================================================================" >> $logfile
# start loop here?
while [ 1 = 1 ]
do
	# sleep 1 minute (60 seconds) before obtaining IP address again
	#sleep 60
	sleep 1 # just sleep 1 second for test purposes
	# assign dated value to variable logtime and put my public IP address alongside the time in the logfile
	lineout="Date and Time: "
	logtime=$(date +%Y%m%d)-$(date +%H%M%S) # date and time
	ip="  IP address: "
	lineout="$lineout $logtime $ip"
	echo $lineout >> $logfile
	curl ifconfig.me >> ipaddress
	cat ipaddress >> $logfile 
	rm ipaddress
done
#next to do
# ? How do find out when IP address changes after an internet disconnect/reconnect ?
exit
**_The log file content for the first 4 iterations of the script loop_**
> 
Wide Area Network status log to record disconnections by change of IP address.
==============================================================================
Date and Time: 20130519-123308 IP address:
92.18.33.206
Date and Time: 20130519-123313 IP address:
92.18.33.206
Date and Time: 20130519-123317 IP address:
92.18.33.206
Date and Time: 20130519-123320 IP address:
92.18.33.206

---

### Post by Cheesemill on 2013-05-19
I just use the following line in my root crontab to monitor my external IP...
```
0 * * * * echo "`date`  `curl -s ifconfig.me`" >> /var/log/externalip
```

This gives me a log which looks like this...
```
...
Sun May 19 13:00:00 BST 2013  86.139.169.158
Sun May 19 14:00:00 BST 2013  86.139.169.158
Sun May 19 15:00:00 BST 2013  86.139.169.158
```

I've got mine set to log every hour but you can easily change this by altering the timing in your crontab.

---

### Post by welshmike on 2013-05-19
Many thanks for your solution in one line.

As an old year 1964 mainframe Assembler programmer I need to get up to speed with Linux magic.

---

### Post by mips on 2013-05-19
> **welshmike said:**
> 
As an old year 1964 mainframe **Assembler programmer** I need to get up to speed with Linux magic.

That makes you a real programmer in my book ;):biggrin:

Love assembler.

---

### Post by welshmike on 2013-05-20
> **mips said:**
> That makes you a real programmer in my book ;):biggrin:

Love assembler.

Before 360 Assembler it was 1400 Autocoder and SPS
Earlier on I started with the mystery of programming a Ferranti Pegasus 1 with its nickel delay lines primary storage (RAM).
[IMG]http://www.amipp.org.uk/peg.jpg[/IMG]

---

