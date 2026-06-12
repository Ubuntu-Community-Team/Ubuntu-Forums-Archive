---
title: "[SOLVED] /etc/environment and /etc/init.d"
date: 2008-07-28
forum: Server Platforms
---

### Post by kaig0815 on 2008-07-28
Hi there, 

I'm having problems with setting a global environment variable (e.g. JAVA_HOME) on Ubuntu 8.04 Server. I've installed JAVA and tomcat manually by extracting them (no, I don't want to use the multiverse packages). I want to start tomcat automatically on the boot of the system. Therefore I've linked the startscript to /etc/init.d/catalina and installed startscripts with 
```
update-rc.d catalina defaults. 
```

I've also added the following to my /etc/environment
```
JAVA_HOME="/path/to/my/jre"
```

If I reboot my system It tries to start tomcat but fails because it can't find the JAVA_HOME variable. If I login I don't have any problems with starting tomcat, the variable seems to be available. echo $JAVA_HOME also shows the correct path. 

What am I doing wrong? is /etc/environment the wrong place for this? I tried adding it to a bunch of different locations (e.g. /etc/bash.bashrc or /etc/profile but according to the documentation /etc/environment should be the right place right?

If this is already documented somewhere please be kind with me, I've already searched around in the web for quite some time now ;-)

---

### Post by BaseRunner on 2008-07-28
Hello,

acc. to google /etc/environment is used by pam and should not be used generally. The reason you are not getting your environment in the startup script as expected is that the shell is not run as a login shell there so it does not read the bashrc & co. files.
You could:
- either create a file in /etc/profile.d, say java_env.sh like this:
export JAVA_HOME="/path/to/your/jre"
  and make your script shell behave like a login shell by adding "-l" to the shebang line:
#!/bin/bash -l
The advantage is that /etc/profile.d/java_env.sh is then also available to your shell on the terminal.

- or you create the file and source it in before you start tomcat:
. /etc/profile.d/java_env.sh

- or you just define it in the script itself

Cheers
batta

---

### Post by kaig0815 on 2008-08-01
thanks, that did the trick (-l in combination with a new file in /etc/profile.d)

---

