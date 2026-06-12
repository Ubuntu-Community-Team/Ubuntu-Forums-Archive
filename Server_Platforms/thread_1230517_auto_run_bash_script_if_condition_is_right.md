---
title: "auto run bash script if condition is right"
date: 2009-08-03
forum: Server Platforms
---

### Post by tatewaki on 2009-08-03
Hi

I'm trying to mount some folder from my home server over the internet, for that i'm using sshfs. But i must admit i'm a bit lazy so i hade a bash script i just have to run and it mount for me. But i like to be a bit more lazy and make it auto run if/when i got internet connection.

So i was thinking of the following:
I got a bash script that contains a if state meant something like:
```

if(ping==true){
./automountsshfs.sh
}
else{ Keep pinging google
}

```
This should run at startup and when i got a internet connection it would run the script automountsshfs.sh

The problem is i'm not sure how to make a bash script like that. And should i just add the script to the runlevel or startup thing of gnome?

---

### Post by walkerk on 2009-08-03
> **tatewaki said:**
> Hi

I'm trying to mount some folder from my home server over the internet, for that i'm using sshfs. But i must admit i'm a bit lazy so i hade a bash script i just have to run and it mount for me. But i like to be a bit more lazy and make it auto run if/when i got internet connection.

So i was thinking of the following:
I got a bash script that contains a if state meant something like:
```

if(ping==true){
./automountsshfs.sh
}
else{ Keep pinging google
}

```
This should run at startup and when i got a internet connection it would run the script automountsshfs.sh

The problem is i'm not sure how to make a bash script like that. And should i just add the script to the runlevel or startup thing of gnome?

A quick python script. It'll get the job done...

[php]#!/usr/bin/python

import os, socket, time, sys

def net_test():
	try:
		s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		s.connect(("www.google.com", 80))
		return True

	except socket.error:
		return False



if __name__ == "__main__":
	LoopIt = True

	while LoopIt == True:
		os.system("clear")
		print "Testing Network Connectivity...\n"

		network = net_test()
		if network == True:
			os.system("./automount.sh")
			LoopIt = False

		elif network == False:
			print "Continue testing network connectivity..."

		os.system("sleep 5")[/php]

---

### Post by walkerk on 2009-08-03
And bash...
[php]#!/bin/bash

PNG="$(ping www.google.com -c1)"

if [[ $PNG =~ "bytes from" ]]
then
	echo "Run your script: ./automount.sh"
else
	echo "No dice."
fi[/php]

---

### Post by samosamo on 2009-08-03
You need to look into AutoFS.  In the ubuntu package the default configs don't include "sshfs" but there are a few good guides on how to do it yourself.

---

### Post by tatewaki on 2009-08-04
Thanks for the scripts walkerk.

But as samosamo has pointed out autofs can be used so i think i will use that. But i will still try your scripts as a learning experience

---

