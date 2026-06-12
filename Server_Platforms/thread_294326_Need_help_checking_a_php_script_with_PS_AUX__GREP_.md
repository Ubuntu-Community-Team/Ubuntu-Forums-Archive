---
title: "Need help checking a php script with PS AUX | GREP in bash..."
date: 2006-11-06
forum: Server Platforms
---

### Post by HedonismBot on 2006-11-06
Hi everybody.

Simple question. I have a bash script I wrote to monitor if two programs are running. Problem: everytime it issues a

```
ps -aux | grep httpd php listener.php
```

it will return a true under my IF / ELSE statements

What I need is to tell it to use PS to see if a php script and it's helper java app are working. IF they are, no action, if not, kill both and restart in a particular order. Right now it just goes in circles because when you issue a PS with grep on linux it's ALWAYS true, as you just gave it a command to check...

So, if anyone smart out there can make me slap my forehead and go "d'oh!" I'd really appreciate it.

:-D

For clarity, here's my *ahem* code (don't make fun!)

```



#!/bin/bash
###################### Listener MONITOR SCRIPT ######################

# email notifier
# email subject
SUBJECT="Listener CRASH ALERT!!!!"
# Email To ?
EMAIL="mail@company.com"
# Email text/message
EMAILMESSAGE="error.txt"

#To start, we need to create a switch to trigger our restarts
phppass=0
javapass=0

#First, lets see if it's php-listener is running:

if ps aux | grep listener.php
then
echo "Listener.php is running"
phppass=1
else
echo "Listener.php is NOT running"
phppass=0
exit
fi

# Now let's see if Java is running

echo "Checking Java WireClient"
if ps aux | grep WireParserClient2.02a.jar
then
echo "Java WireClient is Running Fine!"
javapass=1
else
echo "Java WireClient is not running! PANIC!"
javapass=0
exit

fi

if [ "$phppass" -eq 1 ] && [ "$javapass" -eq 1 ]; then
    echo "Both checks passed: Script is running a-okay!"
else
    echo "One or Both checks have failed. I am now going to restart."

bin/mail -s "$SUBJECT" "$EMAIL" < $EMAILMESSAGE


#Let's kill both processes and restart them in the proper order
echo "Killing App...."
pkill java
pkill php
echo "Restarting app."
/home/dir/php listener.php &
/home/dir/java -jar WireParserClient2.02a.jar ./WireParserClient.properties &

fi

```

---

### Post by Joe_CoT on 2006-11-06
```
ps aux | grep httpd php listener.php | grep -v grep
```

Will remove the grep line

---

### Post by HedonismBot on 2006-11-09
Dude, you rock. Watcher script now works like a mofo.

:D :D :D

---

