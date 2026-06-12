---
title: "Run a script when connecting to a certain SSID?"
date: 2007-10-27
forum: Ubuntu Brainstorm
---

### Post by Phyzzip on 2007-10-27
I apologize if this isn't the right forum or if there's already a how to that I've missed.

In essence what I want to do is when my laptop connects to my home network it would be nice if it would automatically do things like mount my fileserver's Samba share, run a synchronization utility etc.

About as far as I've gotten on my own is that it would likely involve ifup, but I don't know how one goes about querying the SSID that the interface is connected to from the command line. But since Linux being what it is I have no doubt that the appropriate tools exist only waiting to be chained together properly.

---

### Post by kast on 2007-10-27
do you want the script to connect you to your wireless, or just test to make sure your connected before running the commands you want?

---

### Post by Phyzzip on 2007-10-27
The later. That is run a certain script only on connection to a certain network. I'm connecting to the network fine already.

---

### Post by kast on 2007-10-27
run this command and tell me if it sees you wireless and what ssid your on
[B]

iwconfig[/B]

---

### Post by Phyzzip on 2007-10-28
Yes indeed it does. Great, that's all I need (other than some time) to hack something up. Merci.

---

### Post by kast on 2007-10-28
I worked allot on this last night and have something that works, not the prettiest thing I'm sure but it works.

if you figure it out i would be interest to see your finished code, if your running into issue let me know and i can give you what i have.

my code will need to be tweaked to a few of your specifications, but there easy tweaks. it will depend on if your network connection is eth0/ath0 etc.. and the name of your ssid of course.

---

### Post by Phyzzip on 2007-10-28
Well I obviously more to learn, after smashing my head against a wall for a few hours trying to figure out how to get the comparison done without jumping into say sed I've decided to instead come up with an also unpretty bit of python/shell hybrid. Obviously this has place holders, may not work without modification by anyone else etc.

```
#!/usr/bin/env python

import os
def getSSID(interface = ''):
	connection_info = os.popen('iwconfig '+interface).readline()
	for piece in connection_info.split(' '):
		if piece.startswith('ESSID'):
			return piece.split(':')[1].strip('"')
	else:
		return ''

SSID = getSSID('eth1')

if 'Home' in SSID:
	os.system('echo home')
elif 'MyUniversity' in SSID:
	os.system('echo school')
else:
	os.system('echo away')
```

---

### Post by Phyzzip on 2007-10-28
The above BTW is a mental translation of what I want but don't know how to do in shell scripting. Obviously unless the SSID I'm looking for is something silly that turns up in iwconfig all I really need to get the job done technically is:

```
if SSID in os.popen('iwconfig '+interface).readline():
	#do something
```

---

### Post by kast on 2007-10-28
Good job!

 Funny you mention Sed eheh here's my messed up looking code

[B]#!/bin/sh

ssid=$(cat /tmp/ssid5)

iwconfig | sed -n '/ath0/p' >/tmp/ssid ; cat /tmp/ssid | cut -d: -f2 >/tmp/ssid2 ; cat /tmp/ssid2 | cut -c1-15 >/tmp/ssid3
sed 's/.//' /tmp/ssid3 >/tmp/ssid4 ; sed 's/...$//' /tmp/ssid4 >/tmp/ssid5

if [ "$ssid" = private_net ]
then
     run your commands
else
      could run the ifconfig up commands to get the connection up 
fi

rm /tmp/ssid*[/B]


if you change the **cut **command to cut the right amount characters of your ssid **-c1-15** and your network **eth0/ath0** etc. in the script
it would work :) those are just the ones that i used for testing.

---

### Post by Phyzzip on 2007-10-28
Last one I think.
```
#! /bin/sh
ssid=`iwconfig eth1 | grep ESSID | cut -d\" -f2`

if [ $ssid = Home ]
then
	echo home
elif [ $ssid = MyUniversity ]
then
	echo school
else
	echo away
fi

```

With the format that iwconfig reports for me at least this should work no matter the SSID just change eth1 to whatever's appropriate. Then just hope iwconfig doesn't change in the future in a way that breaks this horribly. Now I just need free time to write the (much simpler) scripts to be executed and set it up so that it's invoked when ever the wireless comes up.

---

### Post by kast on 2007-10-28
that's nice, much simpler and better then all those seds! 

i think i had a ssid= command similar but i didn't get it to work! it think i was missing those back ticks :)

any way great job, it was fun, and since I'm new to scripting/Programming it was educational to!

---

### Post by Phyzzip on 2007-10-29
Yes it would have most definantly been the missing backticks. Bit me too but I've been back and forth over this particular tutorial today.

[http://steve-parker.org/sh/external.shtml]("http://steve-parker.org/sh/external.shtml")

---

### Post by kast on 2007-10-29
sweet, I'll check that out

---

### Post by bernstein on 2008-06-03
ugh guys... i even made a wiki entry for this a year ago....

the forum thread from jan 07 : [http://ubuntuforums.org/showthread.php?t=343284](http://ubuntuforums.org/showthread.php?t=343284)
and the resulting wiki entry : [https://wiki.ubuntu.com/OnNetworkConnectionRunScript](https://wiki.ubuntu.com/OnNetworkConnectionRunScript)

---

### Post by Phyzzip on 2008-06-03
Well on the one hand I fail at google. And I do remember searching for about a day before doing the thread. On the other hand this thread is over half a year old itself.

---

