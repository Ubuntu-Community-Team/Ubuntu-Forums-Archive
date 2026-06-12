---
title: "/usr/share/tomcat6/lib vs. /var/lib/tomcat6/lib"
date: 2009-01-09
forum: Server Platforms
---

### Post by nickbreen on 2009-01-09
Hi All,

A big FYI for anyone else having similar problems!

I've spent a few hours trying to figure out what was wrong with my Tomcat6 setup with a webapp that refused to find classes in Tomcat's common lib.

Specifically I was installing Apache Archiva which requires Derby to be installed in common lib to create it's JNDI resources. Not unreasonable nor uncommon.

So I symlinked [FONT="Courier New"]/usr/share/java/derby.jar[/FONT] to [FONT="Courier New"]/var/lib/tomcat6/lib[/FONT] (CATALINA_BASE) because that's how everything else is done in [FONT="Courier New"]/var/lib/tomcat6/lib[/FONT].

Didn't work, couldn't load the Derby JDBC driver. Spent hours check permissions and file paths and all sorts of arcane nonsense.

Turns out that I should have symlinked [FONT="Courier New"]/usr/share/java/derby.jar[/FONT] to [FONT="Courier New"]/usr/share/tomcat6/lib[/FONT] (CATALINA_HOME).

Inspection of Tomcat's catalina.properties file to determine where the classloader looks confirms that this is correct. Tomcat's common classloader only looks in [FONT="Courier New"]/usr/share/tomcat6/lib[/FONT] by default.

I couldn't find a single reference to [FONT="Courier New"]/var/lib/tomcat6/lib[/FONT] anywhere in any configuration or script.

From memory Tomcat 5 and 5.5 (on Windows at least) only ever, by default,  configured the common (and shared and server) classloaders to look in CATALINA_HOME/lib.

It seems to me that [FONT="Courier New"]/var/lib/tomcat6/lib[/FONT] is a complete red-herring and I would like to know if anyone else thinks the same or has a reason why [FONT="Courier New"]/var/lib/tomcat6/lib[/FONT] is there but apparently unusable by default.

Thanks for listening

---

### Post by LepeKaname on 2009-01-27
Hi nickbreen,

I think it is a good question. 

I found it also confusing. I installed tomcat few minutes ago (after a while) and I notice they are two different "webapps" places. 

at /usr/share/tomcat6/webapps/default_root/ 
at /var/lib/tomcat6/webapps/ROOT/

The content of both are the same but none of them are symlinks. 

When I started tomcat it says:

> This is the default Tomcat home page. It can be found on the local filesystem at: /var/lib/tomcat6/webapps/ROOT/index.html

Tomcat6 veterans might be pleased to learn that this system instance of Tomcat is installed with CATALINA_HOME in /usr/share/tomcat6 and CATALINA_BASE in /var/lib/tomcat6

So, based in this information, the /usr/share/... folder was kept for backward compatibility, right?

But according to what you posted libs are being read from the CATALINA_HOME instead of CATALINA_BASE. 

Perhaps they still keep that default reference to prevent other systems to stop working after updating? 

Good observation!

UPDATE:

I read this at: /usr/share/tomcat6/bin/catalina.sh :
> 
#   CATALINA_HOME   May point at your Catalina "build" directory.
#
#   CATALINA_BASE   (Optional) Base directory for resolving dynamic portions
#                   of a Catalina installation.  If not present, resolves to
#                   the same directory that CATALINA_HOME points to.

When we read at: /etc/init.d/tomcat6 :

(at the beginning) 

CATALINA_HOME=/usr/share/$NAME

(then...)
# Directory for per-instance configuration files and webapps
CATALINA_BASE=/var/lib/$NAME

However, If you try to start TOMCAT manually (as I did long time ago) with:
sudo /usr/share/tomcat6/bin/startup.sh

It displays:
> Using CATALINA_BASE:   /usr/share/tomcat6
Using CATALINA_HOME:   /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME:       /usr
touch: cannot touch `/usr/share/tomcat6/logs/catalina.out': No such file or directory
/usr/share/tomcat6/bin/catalina.sh: 357: cannot create /usr/share/tomcat6/logs/catalina.out: Directory nonexistent

So, why here CATALINA_BASE is set to the same as CATALINA_HOME?

/usr/share/tomcat6/logs/ do not exist, but exists in /var/lib/tomcat6/logs/

I see that my logs are writing into /var/lib/... when starting Tomcat from the init.d script. So its better starting it from there.

---

### Post by Janek Kowalik on 2009-04-02
> 
Using CATALINA_BASE: /usr/share/tomcat6
Using CATALINA_HOME: /usr/share/tomcat6
Using CATALINA_TMPDIR: /usr/share/tomcat6/temp
Using JRE_HOME: /usr
touch: cannot touch `/usr/share/tomcat6/logs/catalina.out': No such file or directory
/usr/share/tomcat6/bin/catalina.sh: 357: cannot create /usr/share/tomcat6/logs/catalina.out: Directory nonexisten


Can you advice me what to do to make it run properly ??

cheers

---

### Post by LepeKaname on 2009-04-06
Janek, I hope my answer still help you or to anyone else...

To run Tomcat from the startup.sh:

modify /etc/init.d/tomcat6:

Add "run)" option after "try-restart)":

```
  try-restart)
        if start-stop-daemon --test --start --pidfile "$CATALINA_PID" \
        --user $TOMCAT6_USER --startas "$JAVA_HOME/bin/java" \
        >/dev/null; then
        $0 start
    fi
        ;;
  run)
        /usr/share/tomcat6/bin/startup.sh
        ;;
  *)    
    log_success_msg "Usage: $0 {start|stop|restart|try-restart|force-reload|status}"
    exit 1
    ;;
```

Then, at your /usr/share/tomcat6/bin/startup.sh:

CATALINA_BASE=/var/lib/tomcat6; export CATALINA_BASE
CATALINA_HOME=/var/lib/tomcat6; export CATALINA_HOME
CATALINA_TMPDIR=/var/lib/tomcat6/temp; export CATALINA_TMPDIR
exec "$PRGDIR"/"$EXECUTABLE" run "$@"

Note: don't forget to change the "start" to "run" at the last line...

And finally, create a link from /var/lib/tomcat6/bin to /usr/share/tomcat6/bin

That's it... 

To start tomcat:
sudo /etc/init.d/tomcat6 run
(if you want to see the log at the console, to stop press CTRL+C)

or

sudo /etc/init.d/tomcat6 run > /tmp/mylog
(if you want to send the output to a file)

This is very useful (at least for me) to be able to have access to the System.out without having to modify java codes or tomcat configuration files...

---

### Post by annrandr on 2010-05-17
just installing Tomcat6 and didn't realize catalina_base was different from catalina_home.  Thanks very much, totally saved my bacon.
It looks like the tomcat logging goes into /var/lib/tomcat6/logs/catalina.date as well as the /var/log/daemon.log file.  
Ann

---

