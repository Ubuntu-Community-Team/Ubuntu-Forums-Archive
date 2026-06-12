---
title: "JDK problem after installation"
date: 2010-02-17
forum: Ubuntu Dev Link Forum
---

### Post by shirazbj on 2010-02-17
Hi 

I installed the jdk-6u18-linux-i586.bin file and have added bellow in the /etc/profile:

JAVA_HOME=/opt/jdk1.6.0_18

export JRE_HOME=/opt/jdk1.6.0_18/jre

export CLASSPATH=.:$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH

export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH

After reboot, when type "java -version" in a terminal, it still says java not installed. 

Why?

I tried on Ubuntu 8.1 & 9.04

Thanks

Cean

---

### Post by Rushyang on 2010-08-10
When you reboot, and open new terminal, are these paths already exists?

>  env | grep PATH 

or

echo $PATH I always save my personal settings of path, PS1, HISTORY and other into ~.profile or ~.bashrc file.

& always execute them when I start a new terminal by...

>  source $HOME/.profile

---

