---
title: "Processes run multiple times"
date: 2009-11-17
forum: Server Platforms
---

### Post by _M_ on 2009-11-17
Hi,
I discovered that on my 9.10 Ubuntu Server Edition certain processes run multiple times. I discovered that because my Webapplication's log files (running in Tomcat) contain each message 3 times. The output of ps aux confirms that there are 3 processes running Tomcat. The same is true for other processes. All of these processes autostart at reboot.

What's going wrong here?

Thanks,
Mirko

Processes running multiple times (ps aux after reboot):

> 
...
root        93  0.0  0.0      0     0 ?        S<   15:12   0:00 [kondemand/0]
root        94  0.0  0.0      0     0 ?        S<   15:12   0:00 [kondemand/1]
root        95  0.0  0.0      0     0 ?        S<   15:12   0:00 [kondemand/2]
root        96  0.0  0.0      0     0 ?        S<   15:12   0:00 [kondemand/3]
...
root        97  0.0  0.0      0     0 ?        S<   15:12   0:00 [kconservative/0]
root        98  0.0  0.0      0     0 ?        S<   15:12   0:00 [kconservative/1]
root        99  0.0  0.0      0     0 ?        S<   15:12   0:00 [kconservative/2]
root       100  0.0  0.0      0     0 ?        S<   15:12   0:00 [kconservative/3]
...
root       479  0.1  0.0  17064   980 ?        S<s  15:12   0:00 udevd --daemon
root       613  0.0  0.0  17060   876 ?        S<   15:12   0:00 udevd --daemon
root       626  0.0  0.0  17060   888 ?        S<   15:12   0:00 udevd --daemon
...
root       892  0.0  0.0   5988   608 tty4     Ss+  15:12   0:00 /sbin/getty -8 38400 tty4
root       895  0.0  0.0   5988   604 tty5     Ss+  15:12   0:00 /sbin/getty -8 38400 tty5
root       902  0.0  0.0   5988   604 tty2     Ss+  15:12   0:00 /sbin/getty -8 38400 tty2
root       903  0.0  0.0   5988   608 tty3     Ss+  15:12   0:00 /sbin/getty -8 38400 tty3
root       905  0.0  0.0   5988   604 tty6     Ss+  15:12   0:00 /sbin/getty -8 38400 tty6
...
root      1232  0.2  0.1 239348  8728 ?        Ss   15:12   0:00 /usr/sbin/apache2 -k start
root      1250  0.0  0.0  16584   380 ?        Ss   15:12   0:00 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile
root      1251  0.0  0.0  16584   516 ?        S    15:12   0:00 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile
tomcat6   1253 27.8  1.0 644916 89700 ?        Sl   15:12   0:04 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile
www-data  1255  0.0  0.0 239348  5044 ?        S    15:12   0:00 /usr/sbin/apache2 -k start
www-data  1256  0.0  0.0 239348  5044 ?        S    15:12   0:00 /usr/sbin/apache2 -k start
www-data  1257  0.0  0.0 239348  5044 ?        S    15:12   0:00 /usr/sbin/apache2 -k start
www-data  1258  0.0  0.0 239348  5044 ?        S    15:12   0:00 /usr/sbin/apache2 -k start
www-data  1259  0.0  0.0 239348  5044 ?        S    15:12   0:00 /usr/sbin/apache2 -k start


---

### Post by cairofeevez on 2010-04-22
it's because of jsvc create 3 processes: a launcher process, a controller process and a controlled  process.

[http://commons.apache.org/daemon/jsvc.html](http://commons.apache.org/daemon/jsvc.html)

---

### Post by terazen on 2010-04-22
For the other, apache is supposed to have multiple processes so that it runs smoother.

---

