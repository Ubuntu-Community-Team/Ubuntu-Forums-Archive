---
title: "Howto: Transparent Web Filtering"
date: 2009-02-22
forum: Server Platforms
---

### Post by Dr Small on 2009-02-22
[CENTER][SIZE="4"]Transparent Web Filtering[/SIZE]
[SIZE="7"]&#9617;&#9618;&#9619;»§«&#9619;&#9618;&#9617;[/SIZE][/CENTER]

[SIZE="4"]_Introduction_[/SIZE]

This guide will primarily be written for my setup (which I will explain in a minute) but can be applied to any setup with some minor changes. I write this as a guide for transparent web filtering through DansGuardian, but I use several other tools to accomplish the objective.

The setup consists of a server which runs Squid and DansGuardian and other client computers running some form of Linux. The clients will use a script that I call 'transproxy' to transparently redirect all traffic to Privoxy which must be configured to route all traffic to the server running DansGuardian.

Of course, if you do not have a server, or only have one client computer, you can skip the Privoxy part and just use DansGuardian and Squid if you like. But you will have to adapt that to you current environment.


[SIZE="4"]_Getting Started_[/SIZE]

To begin, we must have ssh access to the server. This guide is not going to tell you how to install a SSH server. There are plenty of guides out there for that. So you need to login to the box and install Squid and DansGuardian:
```
sudo apt-get install squid dansguardian
```

Squid will automatically start and run on port 3128. There really is not any configuration that you need to do to squid, unless you wish to change the cache_mgr option in the /etc/squid/squid.conf file.

DansGuardian on the other hand will not start without first commenting out a line. So we will change into the DansGuardian directory:
```
cd /etc/dansguardian/
```

and edit the configuration file:
```
sudo vim dansguardian.conf
```

About the 5th line down, you should see something that says:
```
UNCONFIGURED - Please remove this line after configuration
```

Please comment that out with a hash (#), otherwise DansGuardian will still refuse to start. Skip down to the "filterport" and change this to "8181". (The reason I change this to 8181 from 8080, is that some services that you install automatically want to take hold of the 8080 port, so just out of habit I change this.)

The "proxyport" should read "3128", as that is what port Squid is listening on.

And "accessdeniedaddress" should be changed to reflect URL of your server and to the "cgi-bin/dansguardian.pl" file. (Note, for this to work, you will need apache2 installed. Otherwise you will not get an "Access Denied" page.)

Save the file, and you may now proceed in starting DansGuardian:
```
sudo /etc/init.d/dansguardian start
```


[SIZE="4"]_Client Setup_[/SIZE]

So long as your server running DansGuardian and Squid have no firewall rules to restrict INBOUND traffic, we may continue on to the client setup of transparently proxying our HTTP requests to the server.

We will start by installing privoxy:
```
sudo apt-get install privoxy
```

Privoxy is one of my favorite filtering proxies, as it contains the ability to yank all those nasty/flashy/annoying ads from off my pages, run them through a shredder, burn them in a hot furnace, and spread their ashes to the four winds.

Yet besides the great aspiring advantage to privoxy, it will be proxying our traffic to the port on which DansGuardian is running on at the server.

But before privoxy can do all this great magic before our eyes, it must be configured to do so, as all great tools.
```
sudo vim /etc/privoxy/config
```

At the beginning of the file, add these two lines:
```
forward  / *serveripaddress*:8181
accept-intercepted-requests 1
```

Of course, where *serveripaddress*, you must replace this with the ipaddress of the server which is running DansGuardian. By default, "accept-intercepted-requests" is disabled elsewhere in the file, so you must find this and comment it out (#). Save the file, and restart Privoxy:
```
sudo /etc/init.d/privoxy restart
```

Thus far, we have been doing all the simple default stuff. Now we will be getting into the fun, script editing, transparent proxy stuff.

Take the following script and save it in /etc/init.d/ as "transproxy". There should not be the need to edit too much of it, if you have stuck to what I have been writing :)
```
#!/bin/sh
# Transparent Proxy designed to use Privoxy to connect to another
# system that is running DansGuardian & Squid. Privoxy needs to
# be configured before using this.
#
# Squid, Dansguardian and Privoxy could all be configured on the
# same system running transproxy (if you wanted), but if you have
# a seperate system that can run these services, it can act as the
# middle man for all connections.
#
# Transproxy by Dr Small <drsmall@mycroftserver.homelinux.org>


# Specify the correct ports
# for the following services.
PRIVOXYPORT=8118
PRIVOXYUSER="privoxy"
HTTPPORT=80
SQUIDPORT=3128
DANSPORT=8181

# Location to save old iptables rules
# NOTICE: Debian users, /etc/iptables does not
# exist. You can create this directory instead.
LOCATION="/etc/iptables/rules.old"

# The location the iptables executable
# It should be located here by default, but
# for those who isn't, this was included.
iptables="/usr/sbin/iptables"

flush () {
	echo "Saving old rules to $LOCATION"
	# Save the old rules
	iptables-save > $LOCATION

	echo "Flushing current iptables rules"
	# Flush the current rules
	$iptables -F
	$iptables -X
	$iptables -t nat -F
	$iptables -t nat -X
	$iptables -t mangle -F
	$iptables -t mangle -X
	$iptables -P INPUT ACCEPT
	$iptables -P FORWARD ACCEPT
	$iptables -P OUTPUT ACCEPT
}

start () {
	echo "Adding new iptables rules for Privoxy"

	# Allow privoxy to connect to DansGuardian
	$iptables -t nat -A OUTPUT -p tcp --dport $DANSPORT -m owner --uid-owner $PRIVOXYUSER -j ACCEPT
	$iptables -t nat -A OUTPUT -p tcp --dport $HTTPPORT -m owner --uid-owner $PRIVOXYUSER -j ACCEPT

	# Allow connections to 128.121.146.100 (twitter.com) without going through transproxy.
	# (Qwit wasn't sending updates properly).
	$iptables -t nat -A OUTPUT -p tcp -d 128.121.146.100 -j ACCEPT

	# Redirect users who access $HTTPPORT to $PRIVOXYPORT
	$iptables -t nat -A OUTPUT -p tcp --dport $HTTPPORT -j REDIRECT --to-ports $PRIVOXYPORT

	# Keep users from connecting to Squid and bypassing Dansguardian
	$iptables -t nat -A OUTPUT -p tcp --dport $SQUIDPORT -j REDIRECT --to-ports $PRIVOXYPORT
}

stop () {
	echo "Restoring iptables rules from $LOCATION"
	# Restore the old rules
	iptables-restore < $LOCATION
}


case "$1" in
	start)
	flush
	start
	;;

	restart)
	stop
	flush
	start
	;;

	stop)
	stop
	;;

	*)
	echo "usage: start|stop|restart"
	;;

esac
exit 0
```

DISCLAIMER: The above script does have a little quirk with it about saving/restoring iptables rules. I have yet to work that little bug out, but in my environment, I do not need my previous firewall rules saved, so I just flush them when starting and stopping to save me trouble. Another thing, I am not an iptables expert, so I may not be doing things correctly. Please correct me if I have made a mistake. But hey, it works :)


We will now add transproxy to the startup:
```
sudo update-rc.d transproxy defaults
```



[SIZE="4"]_Testing the Setup_[/SIZE]

Let's start transproxy, to begin with:
```
sudo /etc/init.d/transproxy start
```

Now, open a browser, and try to access config.privoxy to see if transproxy is actually redirecting traffic to privoxy:
[http://config.privoxy.org](http://config.privoxy.org)

If you get the message that Privoxy is enabled, then transproxy is working. To next see if DansGuardian is working, try accessing some adult related website for testing purposes. (I will not be giving any examples..)


[SIZE="4"]_Troubleshooting_[/SIZE]

*I tried to access the privoxy config page and it said that I was not using privoxy. What now?*
Take a look and see if transproxy actually inputted the rules into iptables:
```
sudo iptables-save
```


*Everything is there as it is supposed to be. What else?*
Did you verify that the ports are all correct in the transproxy script?


*Privoxy is working, but is giving me an error.*
Check your privoxy configuration file and double check that you are forwarding traffic to the correct IP address.


Of course, if there are any other questions/problems, please reply to this thread and I will see if I can help out any. I do not guarantee this all to work, since it took me awhile of fiddling to get it to work myself, but if I have made any known errors or mistakes in this guide, please let me know so I can correct them.

---

### Post by ddigler on 2009-02-24
Dr. Thank you for taking time to write this up!

I am looking for something like this for a single PC that does not incorporate a firewall (most of the tuts on the forums for a single setup like I need include a firewall of some sort). What I need is very similar to your set-up only without the clients.

I already have a FW configured and working and just need to get DG up and running on my Interpid PC for content filtering. I had DG running before and it was great but didn't know how to configure firehol properly for my network sharing so I uninstalled it. Now I have Firestarter up and running but have no content filtering.

Thanks for any help and sorry if I'm off track. I'm new to this and feel as if I'm always ready Greek!

---

### Post by Dr Small on 2009-02-24
> **ddigler said:**
> Dr. Thank you for taking time to write this up!

I am looking for something like this for a single PC that does not incorporate a firewall (most of the tuts on the forums for a single setup like I need include a firewall of some sort). What I need is very similar to your set-up only without the clients.

I already have a FW configured and working and just need to get DG up and running on my Interpid PC for content filtering. I had DG running before and it was great but didn't know how to configure firehol properly for my network sharing so I uninstalled it. Now I have Firestarter up and running but have no content filtering.

Thanks for any help and sorry if I'm off track. I'm new to this and feel as if I'm always ready Greek!
Greetings ddigler,
Initially, when I first started this quest of learning web filtering, I found this guide at Linux.com that is basically written for your type of environment, yet from there I took the knowledge and was able to setup my server and then later discover how to configure the clients to connect to it (with privoxy).

But I feel that the guide pertains to your situation. A single computer running Apache (simply for the purpose of displaying the Access Denied page), Squid and DansGuardian. Privoxy is not needed, as I only use it to forward the the traffic to the remote server (although the filtering ads is a bonus!).

What type of network are you on? Are you directly connecting your computer to the modem, or are you connected to a router/firewall? Depending on your situation, you may/may not need Firestarter on your computer. The Linux.com guide gives examples on how to redirect traffic with iptables to a specific local port (like my transproxy script does), so you can just redirect all traffic to port 8181 for DansGuardian to simplify matters.

Anyhow, here is the guide:
[http://www.linux.com/articles/113733](http://www.linux.com/articles/113733)

If you have any questions, I'll see if I can help you out with it. :)

Dr Small

---

### Post by ddigler on 2009-02-24
First off Small, thanks for the help! I appreciate you taking time. I am proficient with windows and DOS but Linux is still Greek to me but I love it! Prob is with wife and kids not much time to learn...

In terms of my network set-up: PC running Ubuntu 8.10 wirelessly connected to a Linksys router. The router is hard wired to my cable modem. The only other device on my network is an Xbox 360 wirelessly connected to same Linksys router. 

Do I need firestarter installed with this setup? If not I'd like to uninstall it.

I am currently following the tutorial you linked. It seems like exactly what I've been looking for. Would you have me modify it in any way given my setup?

---

### Post by Dr Small on 2009-02-24
> **ddigler said:**
> First off Small, thanks for the help! I appreciate you taking time. I am proficient with windows and DOS but Linux is still Greek to me but I love it! Prob is with wife and kids not much time to learn...

In terms of my network set-up: PC running Ubuntu 8.10 wirelessly connected to a Linksys router. The router is hard wired to my cable modem. The only other device on my network is an Xbox 360 wirelessly connected to same Linksys router. 

Do I need firestarter installed with this setup? If not I'd like to uninstall it.

I am currently following the tutorial you linked. It seems like exactly what I've been looking for. Would you have me modify it in any way given my setup?
I have found that when one is on a network which has a router/firewall, setting up individual firewall rules for different computers on this network tends to cause problems with file transfer, samba, printing, ssh, you name it. (Unless you are on a hostile network where you feel that you would like to restrict traffic to specific services, I do not think that installing and configuring Firestarter is necessary.)

When I first started with Ubuntu, I installed Firestarter out of the windows mindset that I need a firewall, and since Firestarter is a GUI firewall manager, I would be safer. But then I had to keep adding policies to it in order for the rest of the family to access Samba, HTTP or whatever, which became annoying.

Ok, back to the web filter :)

The Linux.com guide should work without a hitch. If you do have any problems, you can just ask me, as I am quite familiar with this stuff. Also, when you get down to the bottom of the Linux.com guide which illustrates the iptables rules for transparently forwarding all your traffic bound for port 80 to port 8080 (DansGuardian), you can add these commands to the transproxy script (above in first post) and still use that script for starting/stopping the transparent proxy.

The script is fairly well commented, but if you should have any difficulty understanding it, please ask.

---

### Post by ddigler on 2009-02-24
OK. I installed DG and Squid w/ no prob and configured both conf files per the tutorial no prob. 

I run into problems when start editing the ip tables; specifically when I go to save the changes:

Home-Office-PC:~$ sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT

Home-Office-PC:~$ sudo iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT

Home-Office-PC:~$ sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8080

Home-Office-PC:~$ sudo iptables -t nat -A OUTPUT -p tcp --dport 3128 -j REDIRECT --to-ports 8080

Home-Office-PC:~$ sudo iptables-save > /etc/sysconfig/iptables

bash: /etc/sysconfig/iptables: No such file or directory

Home-Office-PC:~$ 

When I browsed out to /etc/ there was no sysconfig folder. Did a quick search and found my 'iptables' in /sbin/

Any idea?

---

### Post by ddigler on 2009-02-24
Also, I noticed you mentioned Apache2 above. I do not have this installed according to synaptic and was not aware that I needed it according to the tutorial. Can you clarify?

Lastly, I have removed Firestarter if that helps at all.

---

### Post by Dr Small on 2009-02-24
Ok. To address your first problem:
Apparently the directory /etc/sysconfig does not exist (thus the error and your observation). Simply, you do not have to save the iptables rules specifically there. As a matter of fact, you can save them anywhere. (The point of the transproxy script is to place the iptables rules in it, so they will be restored at startup, since when the system boots, no rules are applied to iptables.)

You will need Apache2 installed (just the barebones, and hardly any real configuration, if I am correct) in order for DansGuardian to "serve" the Access Denied/Banned page. There should be a file called "dansguardian.pl" in /usr/lib/cgi-bin and Apache2 should use that directory as the default cgi-bin (if I am not mistaken... If I am, we will fix that :D)

---

### Post by ddigler on 2009-02-24
To address you first response; I'm not clear here. When I first reboot my machine I'm able to access the Internet. Then I run the code as it is listed in my last post and try to save but get save error prob. Then I try to access the internet again and cannot. However, upon another restarting PC I am then able to access the internet. It seems as if something is changing with those IP config commands but not being saved for next logon. Do I need to save the IP config and if so where to?

I will install Apache2 now...

---

### Post by Dr Small on 2009-02-24
Ok, I will try to break this down so it does not seem so hard to digest :)

When starting the computer, there are no rules applied to iptables. (No restrictions INBOUND or OUTBOUND). You should be able to access the internet just fine.

Now, we will add a few rules to iptables to redirect OUTBOUND traffic to DansGuardian:
```
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -m owner --uid-owner squid -j ACCEPT
sudo iptables -t nat -A OUTPUT -p tcp --dport 3128 -m owner --uid-owner squid -j ACCEPT
sudo iptables -t nat -A OUTPUT -p tcp --dport 80 -j REDIRECT --to-ports 8080
sudo iptables -t nat -A OUTPUT -p tcp --dport 3128 -j REDIRECT --to-ports 8080
```

For a brief explanation of the above commands (in order):
```
Allow user `squid` to connect to port 80
Allow user `squid` to connect to port 3128
Redirect traffic to port 80 to port 8080
Redirect traffic to port 3128 to port 8080
```

Now, do not worry about saving the rules to file yet. Saving them does not literally "apply" them, but saves it in a format that the command `iptables-restore` can read and restore from.

I should safely assume that both Squid and DansGuardian start at bootup. You can check to verify that they are actually running:
```
ps aux | grep squid
ps aux | grep dansguardian
```

If you do not see them running, you can start them with:
```
sudo /etc/init.d/squid start
sudo /etc/init.d/dansguardian start
```

Now, check and see if the internet works in a web browser. I do not see why it should not be, but if not, we will work with it from there and start troubleshooting.

---

### Post by Dr Small on 2009-02-24
Also, please save this script to /usr/bin/iptables-flush, as I have found it comes quite in handy for removing all of those rules in iptables for quick testing.
```
#!/bin/bash
echo "Stopping firewall and allowing everyone..."
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```


Here is something else I would like you to try. Do not apply any rules to iptables (for testing purposes) and open Firefox, Edit-> Preferences-> Advanced-> Network-> Settings-> Manual Proxy Configuration-> HTTP Proxy: "127.0.0.1" and Port "8080".

This should directly use DansGuardian through the web browser. If that works, then we can safely say that both Squid and DansGuardian are working properly, and we can start troubleshooting the iptables rules.

---

### Post by ddigler on 2009-02-24
Installed Apache2 through Synaptic. Changed the cgi-bin file in the conf to the one you specified.

To be certain this is what I have in the Apache2 config:

# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
 ErrorDocument 404 "/usr/lib/cgi-bin/"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)

Look right?

---

### Post by Dr Small on 2009-02-24
> **ddigler said:**
> Installed Apache2 through Synaptic. Changed the cgi-bin file in the conf to the one you specified.

To be certain this is what I have in the Apache2 config:

# Customizable error responses come in three flavors:
# 1) plain text 2) local redirects 3) external redirects
#
# Some examples:
#ErrorDocument 500 "The server made a boo boo."
#ErrorDocument 404 /missing.html
 ErrorDocument 404 "/usr/lib/cgi-bin/"
#ErrorDocument 402 [http://www.example.com/subscription_info.html](http://www.example.com/subscription_info.html)

Look right?
Actually, the cgi-bin should be specified in /etc/apache2/sites-available/default

I just checked on mine, and it is there, so it should not be a problem. What you changed was the Error Document response :D

---

### Post by ddigler on 2009-02-24
OK, so to be certain this is what I did: 

Entered your code for the 4 ip table configs on page 1 at the bottom. Reconfigured Firefox for the manual proxy according to page 2 and nothing, could not access internet.

Upon reboot, when the 4 ip configs should have been wiped, jumped into Firefox still configured for manual proxy and nothing again. 

FYI if this helps:

When I performed the commads given to see if the proxy and DG were running at startup this is what they returned:

zac@Home-Office-PC:~$ ps aux | grep squid
zac       6229  0.0  0.0   7452   872 pts/0    R+   22:28   0:00 grep squid
zac@Home-Office-PC:~$ ps aux | grep dansguardian
zac       6233  0.0  0.0   7452   880 pts/0    R+   22:28   0:00 grep dansguardian

---

### Post by ddigler on 2009-02-24
If this helps:

PC:~$ sudo /etc/init.d/squid start
 * Starting Squid HTTP proxy squid                                              2009/02/24 22:46:20| parseConfigFile: squid.conf:27 unrecognized: 'httpd_accel_host'
2009/02/24 22:46:20| parseConfigFile: squid.conf:28 unrecognized: 'httpd_accel_port'
2009/02/24 22:46:20| parseConfigFile: squid.conf:29 unrecognized: 'httpd_accel_with_proxy'
2009/02/24 22:46:20| parseConfigFile: squid.conf:30 unrecognized: 'httpd_accel_uses_host_header'
                                                                         [ OK ]

-PC:~$ sudo /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                           Error opening/creating log file. (check ownership and access rights).
I am running as squid and I am trying to open /var/log/dansguardian//access.log
                                                                         [fail]
PC:~$

---

### Post by Dr Small on 2009-02-24
> **ddigler said:**
> If this helps:

PC:~$ sudo /etc/init.d/squid start
 * Starting Squid HTTP proxy squid                                              2009/02/24 22:46:20| parseConfigFile: squid.conf:27 unrecognized: 'httpd_accel_host'
2009/02/24 22:46:20| parseConfigFile: squid.conf:28 unrecognized: 'httpd_accel_port'
2009/02/24 22:46:20| parseConfigFile: squid.conf:29 unrecognized: 'httpd_accel_with_proxy'
2009/02/24 22:46:20| parseConfigFile: squid.conf:30 unrecognized: 'httpd_accel_uses_host_header'
                                                                         [ OK ]

-PC:~$ sudo /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                           Error opening/creating log file. (check ownership and access rights).
I am running as squid and I am trying to open /var/log/dansguardian//access.log
                                                                         [fail]
PC:~$
Well now, there is the problem.
See if the dansguardian log directory exists (and see the permissions if it does):
```
ls -l /var/log/ | grep dansguardian
```

If it exists, make sure the permissions/groups looks like this:
```
drwxr-xr-x 2 dansguardian dansguardian    4096 2009-01-29 18:36 dansguardian
```

If the directory does not exist, create it:
```
sudo mkdir /var/log/dansguardian
sudo chown dansguardian:dansguardian /var/log/dansguardian
sudo chmod 755 /var/log/dansguardian
```

After you have finished, try starting DansGuardian again and see if there are any more problems (I can not believe the Ubuntu packagers let this one slip...):
```
sudo /etc/init.d/dansguardian restart
```

---

### Post by ddigler on 2009-02-24
PC:~$ ls -l /var/log/ | grep dansguardian
drwxr-xr-x 2 dansguardian dansguardian    4096 2009-02-23 00:40 dansguardian
-PC:~$ 

Not an exact match to what you supplied. thoughts?

---

### Post by Dr Small on 2009-02-24
> **ddigler said:**
> PC:~$ ls -l /var/log/ | grep dansguardian
drwxr-xr-x 2 dansguardian dansguardian    4096 2009-02-23 00:40 dansguardian
-PC:~$ 

Not an exact match to what you supplied. thoughts?
I would be a bit freaked out if it was an exact match, lol. The only parts that do not match are timestamps, but the rest is the same. This is really mind boggling, as I am running DansGuardian on Debian and you on Ubuntu.

But apparently, I would say that the group does not exist. We shall see, though. Try:
```
sudo groupadd dansguardian
```

If it says:
```
groupadd: group dansguardian exists
```

Then the group exists, of course. So we should look at the dansguardian.conf file. (Why does Ubuntu have to be such a pain in the neck for all of this?) Open /etc/dansguardian/dansguardian.conf and look for "daemonuser" and "daemongroup" options. They should be commented and the default value as "dansguardian" (at least they are on mine), but on Ubuntu who knows.

---

### Post by ddigler on 2009-02-24
lol, you prob read some of the stuff i come up with and just shake your head. If it helps I have full intentions of reading to learn this stuff. This content thing though I need ASAP.

PC:~$ sudo groupadd dansguardian
[sudo] password for zac: 
groupadd: group dansguardian exists
-PC:~$ 

My DG config file:

# Daemon runas user and group
# This is the user that DansGuardian runs as.  Normally the user/group nobody.
# Uncomment to use.  Defaults to the user set at compile time.
# Temp files created during virus scanning are given owner and group read
# permissions; to use content scanners based on external processes, such as
# clamdscan, the two processes must run with either the same group or user ID.
 daemonuser = 'squid'
 daemongroup = 'squid'

The tutorial you had me look at wanted these to 'squid'.

---

### Post by Dr Small on 2009-02-24
Ok, ok. Try this then:
```
sudo chown squid:squid /var/log/dansguardian
sudo /etc/init.d/dansguardian start
```

I really am sorry for leading you on what must feel like a blind chase.

---

### Post by ddigler on 2009-02-24
Please do not apologize. I really appreciate your help.

Office-PC:~$ sudo chown squid:squid /var/log/dansguardian
Office-PC:~$ sudo /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                           Error opening/creating log file. (check ownership and access rights).
I am running as squid and I am trying to open /var/log/dansguardian//access.log
                                                                         [fail]
Office-PC:~

---

### Post by ddigler on 2009-02-25
You still tracking doc?

---

### Post by WattoDaToydarian on 2009-02-25
Hello all!
I am trying to get my intranet web site that is being hosted by apache2 open to the public.
I use the firestarter firewall and in "/etc/firestarter/user-pre" I added "iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3129" for DG filtering.
Does this rule stop incoming port 80 traffic from reaching apache?

---

### Post by Dr Small on 2009-02-25
> **ddigler said:**
> Please do not apologize. I really appreciate your help.

Office-PC:~$ sudo chown squid:squid /var/log/dansguardian
Office-PC:~$ sudo /etc/init.d/dansguardian start
 * Starting DansGuardian dansguardian                                           Error opening/creating log file. (check ownership and access rights).
I am running as squid and I am trying to open /var/log/dansguardian//access.log
                                                                         [fail]
Office-PC:~

Lets see here. Just for the sake of not wasting anymore time, we will try to just start all over with DansGuardian:
```
sudo apt-get remove dansguardian --purge
sudo rm -R /var/log/dansguardian
sudo apt-get install dansguardian
```

Edit the dansguardian config file (/etc/dansguardian/dansguardian.conf) and comment out the following line:
```
UNCONFIGURED - Please remove this line after configuration
```

Now see if DansGuardian will start:
```
sudo /etc/init.d/dansguardian start
```

It should, as we are now running a clean slate of the DansGuardian from the repositories, but if not, please post the errors here again.

I am sorry for the lateness in my reply. I was taken ill with influenza this morning, and have not been feeling well enough to reply.

Dr Small

---

### Post by Dr Small on 2009-02-25
> **WattoDaToydarian said:**
> Hello all!
I am trying to get my intranet web site that is being hosted by apache2 open to the public.
I use the firestarter firewall and in "/etc/firestarter/user-pre" I added "iptables -t nat -A PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 3129" for DG filtering.
Does this rule stop incoming port 80 traffic from reaching apache?


I am not an iptables expert and really have know knowledge in PREROUTING yet. You can try it, but I honestly have no idea of the results. But, why would you want to use PREROUTING over OUTPUT ?

---

### Post by WattoDaToydarian on 2009-02-25
> **Dr Small said:**
> I am not an iptables expert and really have know knowledge in PREROUTING yet. You can try it, but I honestly have no idea of the results. But, why would you want to use PREROUTING over OUTPUT ?
Well that's just what I read somewhere online to use. I changed it to OUTPUT and then my filtering went away so I think maybe firestarter requires it to be PREROUTING.

---

### Post by ddigler on 2009-02-25
OK. Well I got it functioning; thank you! But now, for some reason, upon rebooting the machine I always have to restart squid (takes a few 10-15 secs) to get my internet functioning. Insight?

---

