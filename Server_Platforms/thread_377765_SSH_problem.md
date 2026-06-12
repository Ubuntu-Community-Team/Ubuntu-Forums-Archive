---
title: "SSH problem"
date: 2007-03-06
forum: Server Platforms
---

### Post by mzracer360 on 2007-03-06
I have ssh installed on my Ubuntu 6.06 server, and PuTTY installed on my Windows XP machine.  I can connect and run my server through ssh, but every so often  I lose connection and get a error "software caused connection abort"

---

### Post by christhemonkey on 2007-03-06
EDIT: dannyboy79 is more on the ball than me today...

How often is "often"?
Every 20 minutes or so?
Every 3 days?

Is there any relevant output in /var/log/smbd.log? (or the similar samba log file)

---

### Post by dannyboy79 on 2007-03-06
well yeah, that's because sshd_config has a setting in it that makes the ssh session timeout due to inactivity. what happened if you were at a remote location and then you left that computer for a while and left your ssh connection open, you wouldn't want it to stay open that whole time and have some1 possibly go on that remote computer and screw up your "home" computer, right!!!! especially since most of the time ssh'ing into your home computer is allowing access to everything, it's not like ftp, where you can chroot them into a directory. (you may be able to do this with ssh but I don't as I like doing administrative tasks thru ssh) not sure off the top of my head what the setting is but you'll find it in /etc/ssh/sshd_config, make sure you save the original file just in case, then restart your ssh server, /etc/init.d/ssh restart. good luck

---

### Post by mzracer360 on 2007-03-06
I'd say about every 10 to 15 minutes.  I first showed up while setting up my web server.  Now I am trying to setup a game server, and it is still doing it in the middle of my downloads.  
I looked, but I don't have a smbd.log file in /var/log/.

Edit: dannyboy79, it never did this to me when I first installed Ubuntu many months ago.  I just reinstalled it this morning.  I'll try editing /etc/ssh/sshd_config.

---

### Post by dannyboy79 on 2007-03-06
I am confussed now on what you are trying to accomplish. are you tunneling your downloads from your web server thru your encrypted ssh server?? you mention setting up a web server, you mention ssh shutting down during a download, I am not sure what you are trying to do.

it definitely wouldn't be in your smbd.log file, that is for the samba daemon. if anything, there may be something within your /var/log/syslog file about it.

---

### Post by mzracer360 on 2007-03-06
lol, I guess it does sound kinda confusing.  I just reformatted my extra pc and installed Ubuntu 6.06.  The first thing I did was to setup my static ip and install ssh.  Now, I'm on my Windows XP machine and am setting up my server the rest of the way through ssh.  First I followed [these instructions]("http://ubuntuguide.org/wiki/Ubuntu_dapper#Database_Server") to install my web server.  Now I installed my SRCDS game server with [these instructions]("http://www.srcds.com/db/engine.php?subaction=showfull&id=1098643920&archive=").  In the middle of installing both the web and game server, I lost connection.

---

### Post by dannyboy79 on 2007-03-06
ok, got it. you'll have to take a look at your log files to see if there is any info in them. check out /var/log/syslog, /var/log/auth (this will have authentification info for when you log into your ssh server and when you use sudo etc etc), /var/log/apache (if this exists? I don't have a web server), and finally if there is a log file for srcds. if you were doing stuff than it wouldn't have disconnected from inactivity but if it was just sitting there than it's possible that your ssh server closes the connection due to a timeout. that's about all i can suggest?

---

