---
title: "Script to shut down the server"
date: 2012-11-09
forum: Server Platforms
---

### Post by FloM on 2012-11-09
Hello all,

As in the title, i need a simple script that checks if a PC is still on if not then the server shuts down.

I have:
ubuntu server 10.10
IP pc: 192.168.1.10

This is what i have got untill now

```
#!/bin/bash
server_shutdown="ping -c4 192.168.1.10 2>&1 | grep 0\ received"
if [ ! "$server_shutdown" == "0\ received" ]; then
        echo "Stopping server!"
        sudo shutdown -h now

fi
```

If i run this from the webmin the server shuts down no matter if the PC is on or off...seems to me that i have make some mistakes...but i really don't know where :(:(:(...


Any help will be appreciate....

Thank you in advance!

Cheers,
Florin

---

### Post by drmrgd on 2012-11-09
I don't know exactly how to check for an alive computer on a network (you might google around for strategies).  However, I don't think the way you're doing it is ideal.  What if there's just a network issue and the computer's still alive?

That being said, you've got some problems with the way you're defining things.  Try to echo your variables to see what's store in them to see what's wrong.  In the 'server_shutdown' variable, you're storing a string called "ping -c4 192.168.1.10 2>&1 | grep 0\ received" rather than the result of the command.  For that you need to use command substitution:

[http://www.gnu.org/software/bash/manual/html_node/Command-Substitution.html#Command-Substitution](http://www.gnu.org/software/bash/manual/html_node/Command-Substitution.html#Command-Substitution)

```
server_shutdown="$(ping -c4 192.168.1.10 2>&1 | grep "0 received")
``` 

The next thing is your test operation.  I would assume that you want to test for a null string as a result of a computer being alive and grep not finding anything.  For that you should probably use a string comparison test:

[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html)

So, you want something more like:

```
if [ "$server_shutdown" != "" ]; then 
    echo "shutdown"
else
    echo "still alive"
fi

```

The echo statements are just a test.  You can replace them with the actual shutdown command you want to run (actually don't need the else in there if you're not in testing mode).

---

### Post by FloM on 2012-11-09
@[drmrgd]("http://ubuntuforums.org/member.php?u=1288128")

Manny, manny thanks for your suggestions....:) and for the links...very useful...
About the check it's not a problem of life and death :P:P:P....if due to a network congestion the server shuts down it's no problem since at the time the cron job is scheduled it's almost impposibile that someone will still be at the office :P at that time

I have just used the script with the echo format and seems to work :):)

Now i have changed the cron job and waiting to see the miracle :P

Again thank you!

Florin

---

### Post by drmrgd on 2012-11-09
Excellent!  Glad you found that helpful!  

Let us know if you run into any more issues with the script :)

---

