---
title: "bash script to print a list of established connections"
date: 2011-06-29
forum: Tutorials
---

### Post by d3v1150m471c on 2011-06-29
I looked on the net for this and couldn't find anything suitable. This is perfect if you have something like conky and want to see just a list of your established internet connections without all the fluff in between:
```

#!/bin/bash
##############################################################################
# A simple bash script to quickly show established connections

x="0"
for i in `netstat -n | grep "ESTABLISHED"`; do
 x=$((x + 1))
  if [ $x == 5 ]; then
   if [[ $i != *'127.0'* ]] && [[ $i != *'192.168'* ]]; then
    echo "$i"
   fi
elif [ $x == 6 ]; then
   x="0"
 fi
done

```

The output will look something like this:
```

72.127.xxx.xxx
42.78.xxx.xxx
98.54.xxx.xxx
...etc, etc

```

Enjoy :)

---

### Post by snitride on 2012-03-24
Hello, i know the last post was posted some time ago, but i was wondering how the script would have to look like, if i would want to add "lsof -i :port" process information behind the established ports and ip addresses? 
Someone who can help me out here? 

Example: 
x.x.x.x:port/COMMAND:USER:NODE:NAME (maybe, just the command+name)

thanks, 
snitride

---

### Post by snitride on 2012-03-26
something like this, it work, but of course its not optimal.. 
you will have to run it with sudo/root permissions.
Also it will only show one line of lsof output for every port..
```


#!/bin/bash
##############################################################################
# A simple bash script to quickly show established connections
x="0"
for i in `netstat -n | grep "ESTABLISHED"`; do
x=$((x + 1))
 if [ $x == 5 ]; then
  if [[ $i != *'127.0'* ]] && [[ $i != *'0.0'* ]]; then
   FORLSOF=`echo $i | cut -f 2 -d :`
   cut1=`lsof -i :$FORLSOF | tail -1 | tr -s ' ' | cut -d' ' -f1`
   cut2=`lsof -i :$FORLSOF | tail -1 | tr -s ' ' | cut -d' ' -f9`
   echo "$i $cut1 $cut2"
  fi
elif [ $x == 6 ]; then
  x="0"
fi
done

```

Anyone got some further ideas, howto to optimize the code?

---

