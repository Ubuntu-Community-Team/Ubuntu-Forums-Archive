---
title: "At a loss custom init script no working on startup"
date: 2007-12-08
forum: Server Platforms
---

### Post by TurboRush on 2007-12-08
I modified a simple script to start tomcat. I want Tomcat to fire up without someone actually logging into the server, i.e., the power blips and it restarts but no one is around to log in.

I've scoured the forums and google but nothing has fixed this. This is the script and it works if you just execute it manually:

```

# Tomcat auto-start
#
# description: Auto-starts tomcat
# processname: tomcat

export JAVA_HOME=/usr/lib/java
export CATALINA_HOME=/usr/lib/tomcat
echo Starting Tomcat
case $1 in
start)
       sh $CATALINA_HOME/bin/startup.sh
       ;;
stop)  
       sh $CATALINA_HOME/bin/shutdown.sh
       ;;
restart)
       sh $CATALINA_HOME/bin/shutdown.sh
       sh $CATALINA_HOME/bin/startup.sh
       ;;
esac   
exit 0

```

tomcat.sh is located in /etc/init.d and is executable
```

chris@cadzimaserver:/etc/init.d$ ls -l tomcat.sh
-rwxr-xr-x 1 root root 411 2007-12-08 14:25 tomcat.sh
chris@cadzimaserver:/etc/init.d$ 

```

I have tried using both:
```
 sudo update-rc.d tomcat.sh defaults 
```
and
```
sudo update-rc.d tomcat.sh start 51 S .
```

However, tomcat doesn't start until I log in as a user. What's more, say I restart and end up at the login screen at 3pm, but don't log in until 3:15pm, the tomcat logs seem to indicate that tomcat started at 3:00pm? 

I tested this all out on my main computer and it worked exactly as I expected. Not quite sure what could be different? 

Thoughts? I'm running or rather have run out of ideas.

---

### Post by TurboRush on 2007-12-09
Ahhh well, I've been meaning to re-do to the server edition anyway... I'll just slug that out and see how it goes.

---

