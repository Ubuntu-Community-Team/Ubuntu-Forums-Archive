---
title: "Suspicious Activity - My computer is a zombie?"
date: 2011-01-13
forum: Security
---

### Post by Ellume on 2011-01-13
Reposting

I am running ubuntu 10.10, and fairly new to ubuntu. I've started to pursue computer security as a hobby and hopefully a career later on, but I am still new to most of this stuff.

I ran EtherApe and I realized I had a very suspicious connection open with 200+kbps activity continually. I am not downloading or uploading anything to my knowledge, don't have any torrent programs running. So I'm starting to wonder if my computer may be a zombie. I'm kinda hoping I can use this experience to learn a little bit about this stuff and what I can do besides simply formating and reinstalling everything.

After a while of having etherape up I noticed a second large connection going for awhile, but it ceased after some time. Checking yesterday I noticed a connection with a yet further increased activity of up around 2.6Mbps, which has been continual since then while I have my computer connected to the internet (which I disconnect when I'm not specifically doing something on it now). Screenshots below.

Any advice? 

Pictures from EtherApe
[http://i152.photobucket.com/albums/s200/Ellume/suspicious.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious.png)
[http://i152.photobucket.com/albums/s200/Ellume/suspicious2.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious2.png)
[http://i152.photobucket.com/albums/s200/Ellume/suspicious3.png](http://i152.photobucket.com/albums/s200/Ellume/suspicious3.png)


@Pl@yer: Unfortunately when I was going to look over your advice, I couldn't find my thread. If you would be willing to post it again I would be grateful.

---

### Post by |{urse on 2011-01-13
Yeah, how fast is your line? up/down?
That activity is probably just ubuntu checking for updates.

I sincerely doubt your box is a zombie but you could run rkhunter.
[http://www.rootkit.nl/]("http://www.rootkit.nl/")

You could also check the ```
who
```command. This tells you who is currently logged into your system.

---

### Post by |{urse on 2011-01-13
Yeah, how fast is your line? up/down?
That activity is probably just ubuntu checking for updates.

I sincerely doubt your box is a zombie but you could run rkhunter.
[http://www.rootkit.nl/]("http://www.rootkit.nl/")

You could also check the ```
who
```command. This tells you who is currently logged into your system.

---

### Post by |{urse on 2011-01-13
Yeah, how fast is your line? up/down?
That activity is probably just ubuntu checking for updates.

I sincerely doubt your box is a zombie but you could run rkhunter.
[http://www.rootkit.nl/]("http://www.rootkit.nl/")

You could also check the ```
who
```command. This tells you who is currently logged into your system.

---

### Post by ianblaire on 2011-01-13
I bet it's this:
[http://en.wikipedia.org/wiki/Skype_protocol](http://en.wikipedia.org/wiki/Skype_protocol)

---

### Post by uRock on 2011-01-13
Run this command in a terminal to see what applications are using which connections to help figure out what is communicating.```
lsof -i -n -P
```

---

### Post by Ellume on 2011-01-13
Alright. After running **lsof -i -n -P** I found that there were several connections for **gvfsd-http**. A quick search on the forum found a similar thread to mine in the network section [http://ubuntuforums.org/showthread.php?t=1645117](http://ubuntuforums.org/showthread.php?t=1645117)

I have dropbox, but that came up separately when performing the lsof command. I've shut that down anyway. I have no servers of which I should be syncing with, so I'm not sure what **gbfsd-http** is sucking my bandwidth for.

My line is 5Mbps download and 0.5Mbps upload. After running the **who** command I got:
```
ellume   tty7         2011-01-13 06:56 (:0)
ellume   pts/0        2011-01-13 20:03 (:0.0)
```and then I ran it again just a couple minutes after that and got:```
ellume   tty7         2011-01-13 06:56 (:0)
ellume   pts/0        2011-01-13 20:03 (:0.0)
ellume   pts/1        2011-01-13 20:07 (:0.0)

```I'm not sure what that represents.

I thought it might be skype too after a bit, but I shut it down and haven't been running it for the last day or so now.

---

### Post by uRock on 2011-01-13
These are all normal to see in the output of the command a previously posted. ```
COMMAND    PID   USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
clock-app 1911 rabbit   23u  IPv4  83843      0t0  TCP 192.168.156.100:46575->24.234.21.82:80 (ESTABLISHED)
gvfsd-htt 4613 rabbit    9r  IPv4  37059      0t0  TCP 192.168.156.100:48204->91.189.89.105:80 (CLOSE_WAIT)
gvfsd-htt 4613 rabbit   17u  IPv4  40461      0t0  TCP 192.168.156.100:41745->91.189.89.106:443 (CLOSE_WAIT)
gvfsd-htt 4613 rabbit   18u  IPv4  40061      0t0  TCP 192.168.156.100:45729->91.189.89.31:80 (CLOSE_WAIT)
gvfsd-htt 4613 rabbit   19u  IPv4  40475      0t0  TCP 192.168.156.100:45293->91.189.89.31:80 (CLOSE_WAIT)
gvfsd-htt 4613 rabbit   20u  IPv4  37074      0t0  TCP 192.168.156.100:43581->91.189.89.31:80 (CLOSE_WAIT)
gvfsd-htt 4613 rabbit   21u  IPv4  37079      0t0  TCP 192.168.156.100:43582->91.189.89.31:80 (CLOSE_WAIT)

```

---

### Post by ianblaire on 2011-01-13
I didn't look too closely at the screenshots first, but those IP addresses look very suspicious. And by that I mean suspiciously innocent :P  Last time I checked 239.xxxxxxxxxx aren't a real address on the internet, they are reserved for multi-casting, IGMP that sort of things and therefore looks nothing like a zombie machine.

---

### Post by Ellume on 2011-01-13
> **ianblaire said:**
> I didn't look too closely at the screenshots first, but those IP addresses look very suspicious. And by that I mean suspiciously innocent :P  Last time I checked 239.xxxxxxxxxx aren't a real address on the internet, they are reserved for multi-casting, IGMP that sort of things and therefore looks nothing like a zombie machine.Well that pretty much solves things. It's the cable box for the tv :P It seems to stream data even when the tv is off. The increased rate of download is due to an upgrade the cable company automatically did recently. Well this still helped me learn a little. Thank you for the help everyone, it is appreciated :D

---

