---
title: "Apache mod_jk and Tomcat"
date: 2009-02-12
forum: Server Platforms
---

### Post by wlbragg on 2009-02-12
I have a new install of Ubuntu-Intrepid. 
Apache2.2 I think?
Tomcat6
I am trying to get mod_jk configured correctly but I am having problems.
Java is not being forwarded to Tomcat. The app is working properly under native tomcat. This same app is also working properly under the same basic configuration in Windows using Apache2.2, mod_jk and Tomcat5 so I know the apps coding is correct.

Here is a typical error
```
[Thu Feb 12 11:56:40 2009] [error] [client 127.0.0.1] File does not exist: /usr/share/tomcat6/webapps/default_root/dwr-examples/dwr, referer: http://localhost/dwr-examples/chat/javascript-chat.html

```
Where /dwr-examples is the deployed web app and dwr is the servlet called by using
```
<script type='text/javascript' src='/dwr-examples/dwr/interface/Chat.js'></script>
```

First thing is, I have been reading that with the newer releases of Ubuntu with Apache2.2 and Tomcat6 that mod-jk has been depreciated and to use mod-proxy-ajp. I don't have mod-proxy-ajp available in package manager? Why not?

So on to trying to configure it with mod-jk. 
I found 
[http://ubuntuforums.org/showthread.php?t=971517&highlight=mod_jk](http://ubuntuforums.org/showthread.php?t=971517&highlight=mod_jk)
and am going to try to use it's suggestions (any that are appropriate for my config) while I am awaiting an answer to this post.
Here is what I currently have tried in case someone can see something obvious that I am doing wrong.

```
LoadModule jk_module /usr/lib/apache2/modules/mod_jk.so
<IfModule jk_module>
	JkWorkersFile /etc/apache2/mods-enabled/workers.properties
	JkLogFile /var/log/apache2/mod_jk.log
	JkLogLevel warn
	JkLogStampFormat "[%a %b %d %H:%M:%S %Y] "
	JkOptions +ForwardKeySize -ForwardDirectories
	JkRequestLogFormat "%w %V %T"
	JkMount /dwr-examples/* ajp13worker1
	JkMount /dwr-examples/dwr/* ajp13worker1
</IfModule>
```

the workers.properties

```
workers.tomcat_home=/usr/share/tomcat6
workers.java_home=/usr/share/java
ps=\

# Define worker 'ajp13worker1'
worker.list=ajp13worker1,jkstatus

# Set properties for worker 'ajp13worker1' (ajp13)
worker.ajp13worker1.type=ajp13
worker.ajp13worker1.host=localhost
worker.ajp13worker1.port=8009

#worker.ajp13worker1.lbfactor=1
worker.ajp13worker1.connection_pool_size=10
worker.ajp13worker1.connection_pool_timeout=300
worker.ajp13worker1.socket_keepalive=1

worker.jkstatus.type=status
```

That's about it. I am going to use the above mentioned URL to see if I am configuring everything else correctly, ie: environment, etc.

In the meantime any help greatly appreciated!

---

### Post by mittwit on 2009-10-19
Hi,
I know your post was more than half a year ago but did you sort out getting the configuration working?
I have been following the directions at:
[http://tomcat.apache.org/connectors-doc/webserver_howto/apache.html](http://tomcat.apache.org/connectors-doc/webserver_howto/apache.html)
It doesn't seem like my workers are working. Apache2 seems to try and handle all the web content.

---

### Post by wlbragg on 2009-10-19
Yes, I did get it working. My problem was not with mod-jk but with a DWR servlet program. If it's not working correctly you should see errors in your logs. Search through both the Apache and Tomcat logs to see if you can narrow down the problem. I've found 90% of the time a clue to the answer lies there. If you don't see the problem yourself then post the logs here and we'll take a look.

---

