---
title: "Parallel Scripts"
date: 2009-02-17
forum: The Cafe
---

### Post by Godd on 2009-02-17
Hey.

It really bugs me that I have to run a kill command everytime I want to stop my shoutcast server.

So I've been making a script to help solve this.

But I can't get it to work because when the server starts, the program obviously halts until the server script ends.

I've tried running it in the background, but the server posts everything to the initial shell. So it gets really muddy, which I don't want.

My solution is to run the scripts in parallel. But all the solutions I can find don't work for the server because it's written in python(I believe).

Or to run it in the background and force the script off the screen.

Stdout of the server is already being directed to a .txt file, but in the background it won't even direct to /dev/null.

Here's the script.

```
#!/bin/bash
#server_start
#for me
clear
echo "The server is now running. Please tell me when you want it to stop. :]"
reply=no
cd /etc/server
html="<html><body>`cat /etc/server/output.txt`</body></html>"
./sc_serv& > /etc/server/output.txt
while [ "$reply" = "no" ]
do
        tput cup 3 0; echo "             "
        tput cup 3 0; read reply
        echo "$html" > /etc/server/output.html
done
process_id=`ps -a|more|grep sc_serv|cut -d" " -f1`
kill -9 '$process_id'

read done
clear;exit

```

It's pretty damn clunky in it's design too.

---

### Post by Godd on 2009-02-17
I think the easiest thing to do would to figure out why when the server is running in the background, I can't redirect stdout.

By the way, is this in the right forum? I'm not exactly sure it is.

I wasn't able to find a "script help" forum. Ha

---

