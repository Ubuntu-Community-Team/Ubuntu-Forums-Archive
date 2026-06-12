---
title: "HOWTO: Apache/JBoss/mod_jk2 Configuration"
date: 2005-06-21
forum: Server Platforms
---

### Post by jeffjj on 2005-06-21
This weekend I got Apache and JBoss(Tomcat) up and running. If anyone has
tried getting the two to talk to each other then you know its not the easiest
thing to configure...usually at least. I sat down Sunday morning ready to pull
out my hair for another Apache to Tomcat encounter, but it turned out to be a
piece of cake. In part its because Ubuntu installed Apache, PHP, and mod-jk
through apt without any additional configuration. Then I installed JBoss like
normal, meaning I unzipped it and put it where I wanted it. Then I got lucky
because I found a developer comment in the /etc/apache2/mods-available/jk2.conf
file. Its looks like this:

# To enable mod_jk2, customize workers2.properties* from
# /usr/share/doc/libapache2-mod-jk2/examples and copy it to
# /etc/apache2/workers2.properties. Then uncomment the following line:
JkSet config.file /etc/apache2/workers2.properties

So I copied over the /usr/share/doc/libapache2-mod-jk2/examples/
workers2.properties.minimal file to my /etc/apache2/ directory , renamed it to
workers2.properties,  and put in the proper entry in the bottom of the file:

[uri:/extremesite/*]
info=eXtremeSite.
debug=0

Then, fire up JBoss first by doing /$JBOSS_HOME/bin/run.sh. Lastly, restart
Apache by doing the command "sudo /etc/init.d/mysql restart" and your all set!
You can test whether or not its working by accessing your site by going directly
to port 80 instead of using the default port 8080 on JBoss.

Hope this helps someone!


-Jeff


P.S. here is the whole  /etc/apache2/workers2.properties file:

#
# This is the minimal JK2 connector configuration file.
#

[logger]
info=Native logger
level=ERROR

[config:]
file=${serverRoot}/conf/workers2.properties
debug=0
debugEnv=0

[uriMap:]
info=Maps the requests.
debug=0

[shm:]
info=Scoreboard. Required for reconfiguration and status with
multiprocess servers
file=anonymous
debug=0

[workerEnv:]
info=Global server options
timing=0
debug=0

[lb:lb]
info=Default load balancer.
debug=0

[channel.socket:localhost:8009]
info=Ajp13 forwarding over socket
debug=0
tomcatId=localhost:8009

[uri:/extremesite/*]
info=eXtremeSite.
debug=0

---

### Post by stellaNera on 2005-07-14
Hi jeffjj,

thanks for posting this, I find it indeed very useful.

The question I have for you ( since looks like you know what you are doing  :-)  ) is the following.
What if instead of JBOSS I install a plain Tomcat? Should this in theory be the same?

I guess I could try this myself... but since you got something working, you could easily find out.

Appreciate your help very much.   :)  :)  :)

---

