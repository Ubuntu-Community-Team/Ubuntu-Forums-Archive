---
title: "Proper way to start set env-vars and start applications on boot"
date: 2014-11-01
forum: Ubuntu, Linux and OS Chat
---

### Post by Birger_Skogeng_Ped on 2014-11-01
Hi all,


I'm fairly new to Linux (as I'm sure you're all about to realize). I've been searching for weeks to figure this out, but I just can't wrap my head around it.

I have a server running ubuntu server (no desktop, using PuTTY to administrate it from my Windows home computer). On this server I have 3-4 applications that I need to startup automatically whenever the server is rebooted. I cannot figure out what is the cleanest, most proper way to do this. I need my server to set the environment variables first, then run several different scripts/commands.

Until now I have tried adding two scripts:
**/etc/profile.d/startup.sh**
```
#!/bin/sh

export JAVA_HOME=/opt/java/jdk1.8_0_25
export PATH=$PATH:$JAVA_HOME/bin

sudo -u myuser /home/myuser/startup.sh
```
[B]
/home/myuser/startup.sh
[/B]```
sh ~/Applications/apache/bin/startup.sh

sh ~/Applications/teamspeak/ts3server_start.sh
```

But my server applications wont start until i log into the server. Also the apache application states that there is no JAVA_HOME set. But after I have logged in, JAVA_HOME IS set and I can run the server application...

Please help me understand what the proper way for setting my server is.


Sincerely,
Birger

---

### Post by Lars Noodén on 2014-11-01
Welcome.

If your application or script is to be run when the server is started, then you can launch it from */etc/rc.local* and it will run every time the system boots.  Or you could set up an Upstart script, though that is more complicated.

If you want your application or script to run only when any user logs in, then keep it in /etc/profile.d/ and it will get run when the login session starts bash for a user.  

But if you are wanting to set system-wide environment variables, then the place for that is in */etc/environment* .  

So it looks like you could use rc.local for the scripts and /etc/enviroment for the variables.

---

### Post by Birger_Skogeng_Ped on 2014-11-02
Thanks for your repy:)
It's a drag that I cant use parameter expansion in /etc/environment...

For some reason, the env variables are not initialized prior to the script being run. Current setup:

[B]/home/birger/startup.sh
[/B]```
# TeamSpeak server
~/Applications/teamspeak3-server_linux-amd64/ts3server_startscript.sh start

# Web server
sh ~/Applications/apache-tomcat-8.0.12/bin/startup.sh

# Minecraft server
cd ~/Applications/Minecraft/ && sh start-detached.sh
```

[B]/etc/rc.local
[/B]```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to 8080

# Startup script
sudo -u birger sh /home/birger/startup.sh

exit 0
```

[B]/etc/envorinment
[/B]```
JAVA_HOME="/opt/java/jdk1.8.0_20"
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/java/jdk1.8.0_20/bin"
```

---

### Post by Birger_Skogeng_Ped on 2014-11-02
After boot and logging in to user "birger" i can run the script **~startup.sh **without any error.

However, if I run the command [B][COLOR=#000000][FONT=Ubuntu Mono]sudo -u birger sh /home/birger/startup.sh
[/FONT][/COLOR][/B][COLOR=#000000][FONT=Ubuntu Mono]Then JAVA_HOME is undefined ...[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]

---

### Post by Lars Noodén on 2014-11-03
> **Birger_Skogeng_Ped said:**
> However, if I run the command [B][COLOR=#000000][FONT=Ubuntu Mono]sudo -u birger sh /home/birger/startup.sh
[/FONT][/COLOR][/B][COLOR=#000000][FONT=Ubuntu Mono]Then JAVA_HOME is undefined ...[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono][/FONT][/COLOR]

Would [the -E option](http://manpages.ubuntu.com/manpages/trusty/en/man8/sudo.8.html) for sudo do the trick?  Usually as part of general safety precautions, it does not transfer the existing environent variables.  The -E would cause it to.

---

