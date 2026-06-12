---
title: "Internet Security Status feeds via Conky"
date: 2010-03-29
forum: Security
---

### Post by yeleek on 2010-03-29
Conky can be used to display a variety of information on the users desktop.  I wanted to use Conky instead to display the current status of security as reported by:

SANS Internet Storm Center
IBM Internet Security Systems
Symantec Threatcon
McAfee Threat Center

I therefore created 4 small scripts which download the current status from these sites, and set the colour of those status's depending on the current value.  The conky configuration allows for a semi-transparent background - though this is optional.

Attached is an example image showing the 4 different colours

Also attached is an archive with the 4.sh files, .conkyrc and draw_bg.lua (from here [http://conky.linux-hardcore.com/?page_id=3002](http://conky.linux-hardcore.com/?page_id=3002)).

Obviously you'll need to change the paths.  Hope its of use to some - requires conky 1.7.2 from repo.  I'm using conky-all.

---

### Post by yeleek on 2010-04-06
Symantec changed format of website new curl command is:

```
curl http://www.symantec.com/security_response/threatcon/ | grep "Level" | sed -n '/^$/!{s/<[^>]*>//g;p;}' | sed -e 's/^[ \t]*//' | sed "s/[.]//g"# | sed q | sed 's/The ThreatCon is currently at //' | sed 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/' > /tmp/symantec

```

---

### Post by unrater on 2010-07-24
I thinks that Mcafee script has some bug, maybe it's a new site :s

CORRECTION:

```
#!/bin/bash
curl -s "http://www.mcafee.com/us/threat_center/default.asp" | grep "Global Threat Condition" | sed -e 's/critical-image-date.*//' | sed -e s/'McAfee Labs'//g -e s/'Global Threat Condition'//g | sed -e :a -e 's/<[^>]*>//g;/</N;//ba' | sed -e 's/^[ \t]*//' | sed 's/.$//' | tr -d '\n' | sed 'y/abcdefghijklmnopqrstuvwxyz/ABCDEFGHIJKLMNOPQRSTUVWXYZ/' > /tmp/mcafee

read STATUS < /tmp/mcafee

if [[ $STATUS == *\'LOW\'* ]]; then
	echo "\${color5} LOW"     #GREEN
elif [[ $STATUS == *\'ELEVATED\'*  ]]; then
	echo "\${color6} ELEVATED"   #YELLOW
elif [[ $STATUS == *\'SEVERE\'*  ]]; then
	echo "\${color7} SEVERE"   #ORANGE
elif [[ $STATUS == *\'CRITICAL\'*  ]]; then
	echo "\${color8} CRITICAL"  #RED
else echo "\${color9}"$STATUS     #BLUE
fi
```

---

