---
title: "Starting Tomcat as a NON-ROOT"
date: 2011-01-06
forum: Server Platforms
---

### Post by buman on 2011-01-06
Hi,

I know this question may have been asked many times before. I have searched the web and the forums here and got some clues on what I need to do but not the complete solution. Since I am working on a server installation I am asking the question in the "server forum"....

Here's what I have done so far:

1. I have installed tomcat 6 and I am able to run it as ROOT and able to start tomcat on boot as well.
2. Now in order to run it as a NON-ROOT I created a new user "tomcat" in group "tomcat" using:

```
sudo useradd -s  /usr/sbin/nologin -g tomcat -d ~/installs/tomcat/tomcat-6.0.29
```

Since this is a service user I made sure that the user cannot log in.

3. I also set a Unix password for the user and set proper ownerships of the tomcat dir for the above user.

Now when I try to start tomcat using the below thru SSH:

```
su tomcat -c ~/installs/tomcat/tomcat-6.0.29/bin/shutdown.sh
```

I am asked for a password. Since I want tomcat to restart on boot I want to be able to call the scripts without entering passwords. So I added NOPASSWD entry into /etc/sudoers file like below:

```
tomcat ALL=(root) NOPASSWD: /etc/init.d/tomcat6 start,/etc/init.d/tomcat6 stop,~/installs/tomcat/tomcat-6.0.29/bin/shutdown.sh, ~/installs/tomcat/tomcat-6.0.29/bin/startup.sh 
```

But even after doing the above when I restart Ubuntu tomcat does not start up or when I try starting using "/etc/init.d/tomcat6" script I am asked for a password. 

The contents of the "/etc/init.d/tomcat6" script are as below.
 
```
# Tomcat auto-start
#
# description: Auto-starts tomcat
# processname: tomcat
# pidfile: /var/run/tomcat6.pid

export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.21
export CATALINA_OPTS="-Xms64m -Xmx128m"

case $1 in
start)
        su tomcat -c /home/bkane/installs/tomcat/tomcat-6.0.29/bin/startup.sh
        ;;
stop)
        su tomcat -c /home/bkane/installs/tomcat/tomcat-6.0.29/bin/shutdown.sh
        ;;
restart)
        su tomcat -c /home/bkane/installs/tomcat/tomcat-6.0.29/bin/shutdown.sh
        su tomcat -c /home/bkane/installs/tomcat/tomcat-6.0.29/bin/startup.sh
        ;;
esac
exit 0
```

I think I am very close to the solution, but I am missing something....Please HELP...!

thnx much!

bkane

---

### Post by dstanfie3 on 2012-05-02
I just got this to work doing something very similar to what you did.

First of all I added a -r option to the useradd command. I don't know if that helped me or not.

Instead of using su, I used sudo. Instead of
```
su tomcat -c <command>
```
I used
```
sudo -u tomcat <command>
```
and that seems to be working for me.

---

