---
title: "noob cant start freeradius"
date: 2010-01-02
forum: Server Platforms
---

### Post by tha_minkee on 2010-01-02
Greetings everyone; 
 
I have been trying to run freeradius, which i installed using synaptic. Now i must confess i'm quite noobish and am trying my best. There are alot of freeradius tutorials but none have much in the way of troubleshooting new installs, other than debugging mode "radiusd -X" which only returns the "The program 'radiusd' can be found in the following.......Try sudo apt get..... then bash: radiusd: command not found"....hmm... 
 
So after a day or so of trying to manually edit the bash.rc file and learning vi to try to add the command radiusd to my PATH still nada. I have "sudo ls -la" both /etc and /freeradius and all of the packages appear to be in etc/freeradius...:confused: 
 
 
Any help would be greatly appreciated.

---

### Post by tha_minkee on 2010-01-02
There is a radiusd.conf file in etc/freeradius however the daemon wont run in debug (or any other) mode.
 
So after more googling i found a way to look at the running processes and a nifty grep command "ps -eaf grep radius" which returned the following: 
 
"root 11266 1 0 00:44 ? 00:00:00 /usr/sbin/freeradius"
and of course the grep command itself.
 
so does this mean radiusd is running?](*,)....alskdflkjdfja
 
there is also a man page for radiusd.

---

### Post by SteveNorman on 2010-01-02
from the radius wiki ([http://en.wikipedia.org/wiki/RADIUS](http://en.wikipedia.org/wiki/RADIUS))

```
The RADIUS server is usually a background process running on a UNIX or Windows NT machine.
```

ps is a command to list all the processes running on your machine, so if you see something after typing ps it means it is running.
It looks like its running under root as job number 11266  to me. You could type ```
killall freeradius
```

or the equivalent
```
killall 11266
``` 

then run your ps search command again. 
 
You should only see the grep command this time. Run it again and check you ps output. As far as how to start it, you have to use the man page or the following page to figure out what switches to use [HTML]http://linux.die.net/man/8/radiusd[/HTML] , but it should be something to this effect

```
radiusd -X
``` make sure the x is capitalized, -X not -x, and you may need sudo if you get a permissions error.

---

### Post by tha_minkee on 2010-01-02
Thank you Steve for trying to help. 

I killed the process and still get the same error when i issue the

"radiusd -X"   command.  Is there an init.d switch or something??

The man pages which i have read thoroughly give limited information as to how to start the daemon. ANY valid radiusd command is returned with the error:

"bash: radiusd: command not found"

what the heck am i not doing

:sad:

---

### Post by tha_minkee on 2010-01-02
so i have now a radiusd-livingston version which i installed using apt-get, it seemed to have nuked  mysql as it was installing however mysql is still in /etc

I am still hoping i can get a "ready to proccess request" response from the server...thoughts, suggestions?? Heck id even take insults at this point.

---

### Post by tha_minkee on 2010-01-02
bump

---

### Post by SteveNorman on 2010-01-02
Sorry that didnt help, post your exact error messages, if your getting the apt-get message like this

```
The program 'supertux' is currently not installed.  You can install it by typing:
sudo apt-get install supertux-stable
bash: supertux: command not found

```

but with the program you are trying to launch instead of supertux, you havnt installed it yet. You need to do```
sudo apt-get install supertux-stable
``` replacing supertux-stable with the program listed in the output.

Also you may want to post in the server platforms section for more specific help on that program, as I have no idea what its used for. The help I am giving is general install help, and you may need a higher level than that.

Make sure to copy and paste your error messages directly from the terminal as that will help us diagnose your exact problem. use the # button above to enclose any output or messages from your attempts.

---

### Post by HermanAB on 2010-01-03
Here is a guide that includes some debug information:
[http://www.aeronetworks.ca/radius.html](http://www.aeronetworks.ca/radius.html)

---

### Post by tha_minkee on 2010-01-04
How about a UBUNTU how to. Most of the tutorials i've read are non-debian specific.  Directories, files are in non standard places. Where is /etc/raddb in ubuntu? hell where is raddb at all?... a sample schema for the mysql db is supposed to be in /usr/share/docs/freeradius...oops not there in ubuntu.  

I am now trying to import a lovely mysql schema from the freeradius wiki, however am unsure as to 1) where i should put it so mysql can access it  2) exactly how do do this.  Google has been my saviour so far.  Heres to hoping a Ubuntu specific guide to fresh freeradius installs might be a reality in the new decade.

---

### Post by HuckBerry on 2010-01-13
I am interested as to where the Ubuntu mods have place /etc/raddb as well. I had some trouble getting freeradius onto Ubuntu 9.04, but it installs beautifully onto 9.10 right from apt-get. So tha_minkee, if you are running 9.04 I HIGHLY suggest switching to 9.10.

Also remove all the IPv6 localhost references from /etc/hosts. This was one of the stumbling blocks I had before I got it to work on 9.04. Seems freeradius is IPv6 enabled so it picks the ::1 localhost before it picks the 127.0.0.1 localhost.

What's the deal with Ubuntu and Open-ssl? I understand that Ubuntu is not allowed to distribute open-ssl due to some lisence issue? Should this be related to the missing /etc/raddb then a quick point in the right direction would be nice. Where might I be able to install the open-ssl headers from?

---

### Post by tha_minkee on 2010-01-20
Thank you Huck for your kind words. I am marking this to solved as I now have an almost working mysql/freeradius/daloradius box. The only thing left is to figure out how get the nas talking to the box...but that is for another thread.   :P

---

