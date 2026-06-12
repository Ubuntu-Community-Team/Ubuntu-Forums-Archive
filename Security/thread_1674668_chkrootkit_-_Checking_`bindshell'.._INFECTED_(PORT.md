---
title: "chkrootkit - Checking `bindshell'.. INFECTED (PORTS: 4000)"
date: 2011-01-24
forum: Security
---

### Post by ramnarayan on 2011-01-24
Hi

Following an article of chkrootkit i tried it and found some disturbing results

The original article is here
[http://www.linuxjournal.com/content/hacking-old-school](http://www.linuxjournal.com/content/hacking-old-school)

Quote
"With the standard install on my Ubuntu box, chkrootkit has 69
available tests."
endquote

After this i tried chkrootkit and found

(rest of the log snipped onl relevant section posted)

Searching for anomalies in shell history files...           Warning:
`//home/ram/.kino-history' is linked to another file

Checking `bindshell'...                                     INFECTED
(PORTS:  4000)


what does this INFECTED mean ?? and what would linked to another file
imply (am assuming the kino  anomaly is less important)

after searching and asking a friend for some help i tried to


m-laptop:~$ sudo netstat -pant|grep 4000
[sudo] password for ram:
tcp        0      0 0.0.0.0:4000            0.0.0.0:*
LISTEN      2485/beagled

so is beagle the file tracker doing all this or is beagled a linux
adjective here

**
I uninstalled beagle but still get the same message

**
the searching the web the only similar page i came across was
[http://ubuntuforums.org/showthread.php?t=746700](http://ubuntuforums.org/showthread.php?t=746700)
and following that tried various commands to see what is wrong, if at all

m-laptop:~$ nmap -P0 localhost

Starting Nmap 5.00 ( [http://nmap.org](http://nmap.org) ) at 2011-01-22 08:48 IST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Interesting ports on localhost (127.0.0.1):
Not shown: 994 closed ports
PORT      STATE SERVICE
631/tcp   open  ipp
4000/tcp  open  remoteanything
5800/tcp  open  vnc-http
5900/tcp  open  vnc
9050/tcp  open  tor-socks
50001/tcp open  unknown

where again Port 4000/tcp says remoteanything ???

*
then ran other tests as below

m-laptop:~$ sudo netstat -an | grep 4000
tcp        0      0 0.0.0.0:4000            0.0.0.0:*               LISTEN

*
m-laptop:~$ sudo lsof | grep 4000
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/ram/.gvfs
     Output information may be incomplete.
beagled    2485        ram   16u     IPv4      12298       0t0
TCP *:4000 (LISTEN)

which yet again shows the same thing

Last in the article below there is a mention of port 4000 in the
context of beagle, though am not sure if this is relevant much
[http://blog.rogersoles.com/2010/07/06/technology/ubuntu-desktop-search/](http://blog.rogersoles.com/2010/07/06/technology/ubuntu-desktop-search/)

***
would appreciate figuring out what is wrong and why this port 4000
INFECTED thingy is happening
ram

---

### Post by ramnarayan on 2011-01-26
Bump, Bumpity Bump

any ideas on this

ram

---

### Post by ramnarayan on 2011-01-26
Bump, Bumpity Bump

any ideas on this

ram

---

### Post by epz on 2011-01-27
Alright there,

first of all mind I'm just trying to help I've no panacea for all evil so first of all you should grab some more infos.

Lets try this.

Netstat stated that something is listening? Nmap stated its using tcp? Perfect go with this.

>  lsof -iTCP -sTCP:LISTEN 

or (if you want to focus on 4000)

>  lsof -iTCP -sTCP:LISTEN | grep 4000 

mind you the latter may be less accurate anyways so I suggest you use the first.


What does it say?


Also, did you run chkrootkit scan while you were using totem's youtube plugin by any chance?

And, what do you have in /home/ram/.gvfs?

If you are not familiar with CLI you should download gufw and block in/outbound connections to/from port 4000, that would be a temporary fix if any bad stuff is communicating with the internet.

Also, you should check synaptic for "vino" , "vinagre" , "vnc" , "remoteanything", remove it all and see if you still have that output from chkrootkit.

Last but not least you may want to try run chkrootkit in verbose mode, it should be sudo chkrootkit -x, not sure though.

Mind you again, we're just trying to see what it may be, good luck.


ps: kino is ok, it does that to me too it's nothing to worry about.

---

### Post by ramnarayan on 2011-01-27
Hi EPZ

```
lsof -iTCP -sTCP:LISTEN
```

ran this and  found nothing

m-laptop:~$ lsof -iTCP -sTCP:LISTEN
COMMAND    PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
ica       2552  ram   20u  IPv4  12650      0t0  TCP *:5800 (LISTEN)
ica       2568  ram   15u  IPv4  12714      0t0  TCP *:5900 (LISTEN)
firefox-b 7839  ram   85u  IPv4  65740      0t0  TCP localhost:50001 (LISTEN)
firefox-b 7839  ram   86u  IPv4  65741      0t0  TCP localhost:40378 (LISTEN)
firefox-b 7839  ram   87u  IPv4  65742      0t0  TCP localhost:38512 (LISTEN)


> or (if you want to focus on 4000)


```
lsof -iTCP -sTCP:LISTEN | grep 4000 
```
 ran this and it came back zilch 

> Also, did you run chkrootkit scan while you were using totem's youtube plugin by any chance?


Nope 


> And, what do you have in /home/ram/.gvfs?

Have nothing - zilch, even checked for hidden files
.

> Also, you should check synaptic for "vino" , "vinagre" , "vnc" , "remoteanything", remove it all and see if you still have that output from chkrootkit.

Uninstalled 
Vino - VNC server for Gnome (uninstalled)
Vinagre - VNC client for Gnome (unintstalled)

VNC - was not installed
could not find remoteanything

> Last but not least you may want to try run chkrootkit in verbose mode, it should be sudo chkrootkit -x, not sure though.


Wow the INFECTED and warnings seem to have disappeared  ran both with-x and without and now could not find anything except the kino message

Had a last question - why this INFECTED message and what were the consequences

thanks
ram

---

### Post by epz on 2011-01-28
hi ramnarayan

I'm glad something is fixed but

>  ica 2552 ram 20u IPv4 12650 0t0 TCP *:5800 (LISTEN)
ica 2568 ram 15u IPv4 12714 0t0 TCP *:5900 (LISTEN) 

wth is that doing there? you probably don't want iTALC on your pc so you're better off without it (from synaptic search it and destroy it)

>  Wow the INFECTED and warnings seem to have disappeared ran both with-x and without and now could not find anything except the kino message

Had a last question - why this INFECTED message and what were the consequences
 

either a false positive or while you were scanning the first time someone was "communicating" with your vnc server.

a few questions.

did you update your firewall rules? (in any case block everything inbound "sudo ufw deny in from any" , "sudo ufw default deny")

who installed ubuntu on your pc? yourself or someone else?

Most of the programs i made you remove are remote administration stuff, pretty much like a faster way to reach your pc if you have a problem, lets suppose John (random name lmao) installed Ubuntu on your pc but you have no idea of how it works when you're stuck you call him and he shows you from your desktop.

To my eyes "remote desktop" & Co. are just some nicer names for backdoors so you probably don't want them.

Also install rkhunter and run a scan with that too, double check is better than single lol.

Glad to help good luck.

---

### Post by ramnarayan on 2011-02-10
> **epz said:**
> hi ramnarayan

> I'm glad something is fixed but

Thanks

Sorry for writing back so late, i got busy which some stuff and could not pull away.

My computer has been acting strange 
last night when shutting down it said cannot shut down unknow program is running. ??

All programmes i had opened were shut and i have not idea about this windowesque program.

 
a few questions.

> did you update your firewall rules? (in any case block everything inbound "sudo ufw deny in from any" , "sudo ufw default deny")

I have firestarter but have no idea how to make and update rules

> who installed ubuntu on your pc? yourself or someone else?

I did, am running 9.10 but a distro called Ultimate Edition


> Also install rkhunter and run a scan with that too, double check is better than single lol.

did run this and these were the "warnings" i got

[11:03:54] /usr/sbin/unhide                                  [ Warning ]
[11:03:54] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.

[11:03:55] /usr/sbin/unhide-linux26                          [ Warning ]
[11:03:55] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.

and the following
[11:06:53]   Checking /dev for suspicious file types         [ Warning ]
[11:06:53] Warning: Suspicious file types found in /dev:
[11:06:53]          /dev/shm/pulse-shm-2140383202: data
[11:06:53]          /dev/shm/pulse-shm-3707541799: data
[11:06:53]          /dev/shm/pulse-shm-797584089: data
[11:06:54]          /dev/shm/pulse-shm-1322839818: data
[11:06:54]          /dev/shm/pulse-shm-1033208539: data
[11:06:54]          /dev/shm/pulse-shm-2106326488: data
[11:06:54]          /dev/shm/pulse-shm-743709925: data
[11:06:54]          /dev/shm/pulse-shm-351083088: data
[11:06:54]          /dev/shm/pulse-shm-1331942024: data
[11:06:54]          /dev/shm/pulse-shm-1912260521: data
[11:06:54]          /dev/shm/mono.2443: data
[11:06:54]          /dev/shm/mono.2467: data
[11:06:54]          /dev/shm/pulse-shm-2905615276: data
[11:06:54]          /dev/shm/pulse-shm-1210813197: data
[11:06:54]          /dev/shm/pulse-shm-289830629: data
[11:06:54]          /dev/shm/pulse-shm-4191095999: data
[11:06:54]   Checking for hidden files and directories       [ Warning ]
[11:06:54] Warning: Hidden directory found: /etc/.java
[11:06:54] Warning: Hidden directory found: /dev/.udev
[11:06:54] Warning: Hidden directory found: /dev/.initramfs
[11:07:05]
[11:07:05] Checking application versions...
[11:07:05]   Checking version of GnuPG                       [ Warning ]
[11:07:05] Warning: Application 'gpg', version '1.4.9', is out of date, and possibly a security risk.

[11:07:06]   Checking version of OpenSSL                     [ Warning ]
[11:07:06] Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.

I don't use opengpg and openssl so i guess thats ok 

but whats the trip with the hiddenn files i .java /.udev an .initramfs ??

**
once again look forward to your help

thanks
ram

---

### Post by cariboo on 2011-02-10
I know it is sometimes easier to ask a question here, instead of searching for an answer, but your question has be asked many times over in this sub-forum. The results you got from rkhunter, are the normal false positives.

As far as a firewall frontend goes, I'd suggest you remove firestarter, as it hasn't been updated except for a few bug fixes since 2005. Ufw is installed by default, and if you would rather set firewall rules with a gui, try gufw. it's in the repositories.

You should completely remove firestarter before installing gufw. You can remove it using the completely remove option in synaptic package manager, or from the command line using the following command:

```
sudo apt-get purge firestarter
```

---

### Post by ramnarayan on 2011-02-10
> **cariboo907 said:**
> I know it is sometimes easier to ask a question here, instead of searching for an answer, but your question has be asked many times over in this sub-forum. The results you got from rkhunter, are the normal false positives.

Yes, i understand, just that the thread was in operation hence the post. Also the subject line , when posted on google, did not get me much productive results

> As far as a firewall frontend goes, I'd suggest you remove firestarter, as it hasn't been updated except for a few bug fixes since 2005. 

and here is me thinking oh i have such good stuff to use :-)

> Ufw is installed by default, and if you would rather set firewall rules with a gui, try gufw. it's in the repositories.


thank you will do.

I still hae one question
what is going on - what kind of intruder would be looking / using the port 4000 and the what are the warnings about.

thanks
ram

---

### Post by cariboo on 2011-02-10
Is there actually any traffic on port 4000?

You can check by running:

```
sudo lsof -i -P
```

---

### Post by ramnarayan on 2011-02-10
> **cariboo907 said:**
> Is there actually any traffic on port 4000?

Yes there is 

earlier also i found it 

```
sudo lsof -i -P
```

beagled    2718        ram   20u  IPv4  12382      0t0  TCP *:4000 (LISTEN)

**
thinking it may have to do with beagle i uninstalled beagle - but in this case it may be more an adjective like your "screwxxd.

should i post the entire lsof -i -P here ??

thanks
ram

---

### Post by ramnarayan on 2011-03-04
> **ramnarayan said:**
> beagled    2718        ram   20u  IPv4  12382      0t0  TCP *:4000 (LISTEN)

**


had posted this and was wondering what the hxll beagled was

no solution to stop it seem to be working, so had to run kill "beagled pid" every day.

Today i ran man beagled and this i what came up 

```
BEAGLE(1)                     Linux User's Manual                    BEAGLE(1)

NAME
       beagled - the Beagle desktop search daemon

```

so i guess either beagle is doing some nasty things listening at port 4000 or its a false positive in chkrootkit

regards
ram

---

