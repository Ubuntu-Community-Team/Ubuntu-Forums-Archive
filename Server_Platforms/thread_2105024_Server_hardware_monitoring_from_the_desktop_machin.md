---
title: "Server hardware monitoring from the desktop machine"
date: 2013-01-14
forum: Server Platforms
---

### Post by openhairpinleft on 2013-01-14
Hello

Pls correct me if i put the topic in a wrong place.


I run Ubuntu on a desktop and ubuntu server as a homeNAS. Want to monitor the hardware on a desktop real-time. Lm-sensors on the server working good, but it's not too comfortable to login and monitor through SSH. 

Guess, i'm talking about something like: make lm-sensors of the server to share data with the, say, psensor of the desktop PC.  Is there any way to do that? 
Thank you.

---

### Post by Habitual on 2013-01-15
If you have key-based ssh then it's as simple as
```
ssh user@host lm_sensors
```I don't know about psensor's configuration options, but they are other possibilities as well, a conky script.rc or a bash alias (assume key-based ssh), snmp, or collectl.

Other, more experienced members will have something clever to add and I wish I had thought of.

HTH!

---

### Post by Mopar1973Man on 2013-01-15
Little more complicated... Install x11vnc on the server and and then log into server with kdrc and then you can see the desktop. Like my setup I'm using conky. 

Habitual seems to have the easy way... ;)

---

### Post by cariboo on 2013-01-15
Nagios3 should do what you need, and it has a web interface, see the screenshot. I just installed it, and haven't had the time to set up hardware monitoring yet, I'll post back here, once I have it  done, with screenshots. Nagios3 is in the repositories.

---

### Post by openhairpinleft on 2013-01-16
ssh user@host lm_sensors is basically what i do now. The idea is to monitor the status in a usual desktop environment.
The idea to install Xserver on a NAS machine doesn't look so attractive actually (but [Mopar1973Man]("http://ubuntuforums.org/member.php?u=1574534") you're right, that's a nice way in some cases). Here the problem is the same: i don't have an access from the desktop, i have to log in.

Going to check Nagios3 as suggested by [[COLOR=#97310e]**cariboo907**[/COLOR]]("http://ubuntuforums.org/member.php?u=77104") but i'd prefer something else than a web access.

Yeah, something like lm-sensors sending the data to some port, and a conky on my machine which listens this port as [Habitual]("http://ubuntuforums.org/member.php?u=504341") probably is thinking of. Pretty sure that could be done by a bash script or something, seems here i have to get into the shell scripting a bit.
Thanks, will post here if i find something.
[[COLOR=#97310e]****[/COLOR]]("http://ubuntuforums.org/member.php?u=77104")

---

### Post by openhairpinleft on 2013-01-16
Made a short trick: send the conky output to the file, than access it from the local PC over http. Now going to add all the servers we work with (mostly CentOS and Debian) on the same page: so will have a kind of a monitor center, real time, single place.
[ATTACH]230161[/ATTACH]
Ugly but working.

Probably a good idea will be to write the file itself somewhere in /proc and access it via the simlink.

Thanks a lot for those helping.
Kill all humans!

---

### Post by Habitual on 2013-01-17
Glad it worked out!

---

### Post by KillerKelvUK on 2013-01-17
> **openhairpinleft said:**
> Made a short trick: send the conky output to the file, than access it from the local PC over http. Now going to add all the servers we work with (mostly CentOS and Debian) on the same page: so will have a kind of a monitor center, real time, single place.
[ATTACH]230161[/ATTACH]
Ugly but working.

Probably a good idea will be to write the file itself somewhere in /proc and access it via the simlink.

Thanks a lot for those helping.
Kill all humans!

Please could you elaborate a little on your conky solution for this?  I'm new to ubuntu server and am currently looking into the best remote monitoring solution for hardware and OS performance.

TIA... K

---

### Post by floatingworld on 2013-01-17
I use conky too, and gmemusage, but via X11 forwarding over SSH which seems much easier and more lightweight and secure.  X Windows appears to already be installed in Ubuntu server (the standard, non-"minimal" option for 12.04 LTS, at least) and X11 is enabled by default in the OpenSSH package, and so all I've had to do is install xauth, IIRC.  (And enable X11 forwarding in my SSH client, of course.)

---

### Post by jeanfi on 2013-03-24
> **openhairpinleft said:**
> 
I run Ubuntu on a desktop and ubuntu server as a homeNAS. Want to monitor the hardware on a desktop real-time. Lm-sensors on the server working good, but it's not too comfortable to login and monitor through SSH. 

Guess, i'm talking about something like: make lm-sensors of the server to share data with the, say, psensor of the desktop PC.  Is there any way to do that? 
Thank you.

See [http://wpitchoune.net/blog/psensor/remote-monitoring/](http://wpitchoune.net/blog/psensor/remote-monitoring/)

Install (sudo apt-get install psensor-server), and run 'psensor-server' on your server.

On your desktop, you can monitor the server by using a browser ([http://yourserver:3131](http://yourserver:3131)), or 'psensor --url=yourserver:3131'. 

Alternativaly, psensor-server is providing a JSON based web api that you can programmaticaly use.

---

