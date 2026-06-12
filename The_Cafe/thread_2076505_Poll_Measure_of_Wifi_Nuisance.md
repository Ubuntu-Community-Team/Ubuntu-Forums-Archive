---
title: "Poll: Measure of Wifi Nuisance"
date: 2012-10-26
forum: The Cafe
---

### Post by patrick295767 on 2012-10-26
Hi,

This is poll about wifi. If you have too much routers around you, it might be not so much wished. Just a poll

This script calculates for you interface eth1 (you could change it to wlan) the sum of the 6th column.

More than 800, that's pretty a lot.


Command:
```
bash wifinuisance-demo.sh
```

```
  
#!/bin/bash

  if [ ! -f wifipss.pl ] ; then 
      wget "http://pastebin.com/raw.php?i=i5Kh9pzT" -O wifipss.pl
  fi
  if [ ! -f wifipss.pl ] ; then 
    echo "Error."
    exit
  fi
  # If you havent any wlan/eth1, make sure to run before: sudo ifconfig eth1 up
  while : ; do 
    PERLRADAR=` perl wifipss.pl `
    # to be shorten soon
    NBR=` echo "$PERLRADAR"  |    awk '  END{ var=NR-1 ; print var  } '`
    POWERNBR=` echo "$PERLRADAR" | awk ' {  print $6  } ' | grep -v Encry  | awk -F "/" ' { print $1 } ' | awk -v vk=0 ' { vk=vk+$0 ; print vk} ' | tail -n 1 `
    echo "* Routers:$NBR ; Total power:$POWERNBR"
    [ -f /usr/bin/festival ] && echo "$NBR. $POWERNBR" | festival --tts
    sleep 0.2s
  done
  exit


```

---

