---
title: "HOWTO: Central Splunk Server Setup and Config"
date: 2008-08-25
forum: Tutorials
---

### Post by ryanisablond on 2008-08-25
[i]NOTE:My previous howto involved a much more complicated way of installing Splunk to run as a non-root user. The method was flawed in that it didn't leave a way to upgrade without all sorts of permissions problems... yuck.

For ease of use, I've split all the info up into two posts. This first one contains all the information you need to install and/or upgrade Splunk. The second post will contain all sorts of configuration stuff.[/i]


**_INSTALLING SPLUNK_** is a pretty painless 4-step processs.
1) Navigate to the /opt directory (the default for most Splunk installs... don't ask me why)
2) Grab Splunk from the offical repositories with the *wget* command
3) Unpack the downloaded .tgz file using *tar*
4) Run the script to install/start Splunk

```

cd /opt
sudo wget 'http://www.splunk.com/index.php/download_track?file=3.4.8/linux/splunk-3.4.8-54309-Linux-i686.tgz&ac=&wget=true&name=wget&typed=releases'
sudo tar xvfz splunk-3.4.6-51113-Linux-i686.tgz
sudo splunk/bin/splunk start

```

Accept the E.U.L.A. and your install is complete.  The pretty web UI is now waiting for you at *[http://your.server.ip.address:8000](http://your.server.ip.address:8000)* Simple, no?



**_UPGRADING SPLUNK_** is just about as simple as the install, but requires one more step. Stop the old version, download the new version and extract it in the same folder. Start Splunk back up and it will recognize the upgrade.

You can check back here for several months and I should have the newest *wget* link. Otherwise, you'll have to register for a free splunk account at [https://www.splunk.com/index.php/sign_up](https://www.splunk.com/index.php/sign_up) to get access to the newest links.

```

cd /opt
sudo splunk/bin/splunk stop
sudo wget 'new-splunk-version-link-goes-here'
sudo tar xvfz new-splunk-downloaded-version.tgz
sudo splunk/bin/splunk start

```

I've never had an upgrade go haywire on me. But if you want to be extra safe, backup */opt/splunk/etc* to save your personal settings and */opt/splunk/var/lib/splunk* to save your indexed files. 


See post below for configuration and upgrade info.

---

### Post by ryanisablond on 2008-11-19
**_CONFIGURING SPLUNK_** 
This step will vary, depending on your needs. I still recommend a few settings for everyone:

**Listen for logs on port 514:**
Most devices and many apps (including *syslog*) use port 514 for sending log info. You'll want Splunk to be listening.
[LIST]
[*]navigate to your Splunk web UI ([http://your.server.ip.address:8000](http://your.server.ip.address:8000))
[*]click "Admin"
[*]click "Data Inputs"
[*]click "Network Ports"
[*]"New Input" button.
[*]choose "UDP" and the port number will automagically change to 514. 
[*]click the "Submit" button to save the configuration change
[/LIST]

**Start upon bootup:**
Pretty self-explanatory. When the machine boots up, so does Splunk.
```
 sudo /opt/splunk/bin/splunk enable boot-start
```

**Only allow certain IP addresses to access the Web UI:**
Since the free version of Splunk doesn't secure the web UI, I lock down access to all that sensitive information through iptables. Obviously, you'll want to replace "ip.address1.to.allow" with your address or a range you want to allow access from (i.e. 10.10.10.35 or 10.10.10.0/24). 
```

sudo iptables -A INPUT -s ip.address1.to.allow -p tcp --dport 8000 -j ACCEPT
sudo iptables -A INPUT -s ip.address2.to.allow -p tcp --dport 8000 -j ACCEPT
sudo iptables -A INPUT -p tcp --dport 8000 -j DROP

```


**_SEND MAC/LINUX LOGS TO SPLUNK:_** 
This is a two step process where you add your Slunk server to the list of known hosts on the client machine and then tell the *syslog* process to forward logs to Splunk.

Add the following line to /etc/hosts *(NOTE: Use tabs, spaces won't work.)*

```

ip.address.of.splunkserver			 splunkserver

```

Where *splunkserver* is the name of your Splunk server. Now, add the following lines to /etc/syslog.conf:

```

# additional config for sending logs to splunk
*.info						@splunksever

```

Where **.info* is the _[ level of detail ]("http://userpages.umbc.edu/~jack/ifsm498d/syslog.html#levels")_ you desire to be sent.


_**SEND WINDOWS LOGS TO SPLUNK**_
As far as I know, there is no simple equivalent of syslog for Windows installed by default. So you'll need to install some type of utility or app to send logs. I recommend _[Snare]("http://www.intersectalliance.com/projects/SnareWindows/")_.

Download and Install Snare here: [http://www.intersectalliance.com/download.html?link=http://prdownloads.sourceforge.net/snare/SnareSetup-3.1.2-MultiArch.exe](http://www.intersectalliance.com/download.html?link=http://prdownloads.sourceforge.net/snare/SnareSetup-3.1.2-MultiArch.exe)

Open the Snare interface to configure its log management:
[LIST]
[*]Click on "Network Configuration"
[*]Set the "Destination Snare Server Address" to Splunk's IP
[*]Change "Destination Port" to 514
[*]Click the checkbox to "Enable SYSLOG header"
[*]Select your desired "Syslog Priority" level from the drop down menu.
[*]Click the "Change Configuration" button
[/LIST]

You might need to add an exception for Snare in the Windows Firewall. (tested in XP)
[LIST]
[*]Navigate to the Windows Firwall settings (Start > Control Panel > Windows Firewall)
[*]Click on the Exceptions Tab
[*]Click the "Add Program" button
[*]Browse to C:\Program Files\Snare\SnareCore (or wherever you installed Snare)
[/LIST]


That's all... for now.

---

### Post by DiGiTY on 2008-12-10
> **ryanisablond said:**
> Hmmmm... it's been three months and nearly a thousand pageviews, but no comments? Is there anyone who has been helped by this? Does it need to be re-written?

Please, help me make this a useful resource! :)

Looks good. I will be trying this whole thing out tonight! I'll give ya feedback.

---

### Post by ryanisablond on 2009-01-20
The old version was long and confusing, so I apologise to everyone. I was trying to cram too much information into one post. :(

So, the guide has been completely rewritten and restructured. Splunk now runs as root, but it makes installing and upgrading incredibly easier.

Check it out!

---

### Post by Bubnoff on 2009-02-26
Thanks for the tutorial. Works beautifully on Gentoo as written.:KS

Bub

---

### Post by binbash on 2009-02-27
Works on fedora 10 also  :)

---

### Post by Blu3fish on 2009-04-06
Thanks @ryanisablond this guide was very easy to follow and got my splunk test environment up and running within a matter of seconds.

Cheers!

---

### Post by LaneOlson on 2009-04-20
Nice simple guide.  Just a quick question.  Why do you set the port on the SNARE configuration to 5140?  Isn't the Splunk server listening on port 514?

---

### Post by ryanisablond on 2009-04-21
> **LaneOlson said:**
> Why do you set the port on the SNARE configuration to 5140? 

Aha! I left that in there just to make sure everyone was paying attention! ;)

Well, maybe it's because I forgot to change that from the earlier tutorial. Nice eyes, LaneOlson. Thanks for noticing the mistake.

---

### Post by Pacerfan9 on 2009-05-20
Thanks for the information on installing Splunk. 
 
 Do you know if you can install/configure the "Splunk for Windows Management" on the Linux version of Splunk? I can't find any information that would confirm or deny if that is possible. I was able to install the application but I do not see any method for specifying windows network credentials for WMI.

---

### Post by minsterkermy on 2009-05-21
NOTE: This feature is only available on the Windows versions of Splunk and is NOT enabled by default.

---

### Post by rizonable on 2010-05-17
I'm getting the following error message when installing when trying to run splunk start using the instructions in the first post here. 

Error:  -su: splunk/bin/splunkd: No such file or directory

Im using the following package: splunk-4.1.2-79191-freebsd-6.2-amd64.tgz
Uname -a: Linux domU-12-31-39-10-69-71 2.6.31-302-ec2 #7-Ubuntu SMP Tue Oct 13 19:55:22 UTC 2009 x86_64 GNU/Linux

Any ideas?

---

### Post by fcefan00 on 2010-05-18
@rizonable: Try "/opt/splunk/bin/splunk start" - like an init script.

---

### Post by QuikTopComputing on 2010-07-05
Here is a link to current: [http://www.splunk.com/index.php/download_track?file=4.1.3/linux/splunk-4.1.3-80534-Linux-i686.tgz&ac=&wget=true&name=wget&typed=releases](http://www.splunk.com/index.php/download_track?file=4.1.3/linux/splunk-4.1.3-80534-Linux-i686.tgz&ac=&wget=true&name=wget&typed=releases)

for future versions, it looks like you can just replace everything after the filename in the URL with '&ac=&wget=true&name=wget&typed=releases' I did this and it worked perfect, no registration required. Thank you for the HOWTO ryan

---

### Post by therascalking on 2010-09-03
> **fcefan00 said:**
> @rizonable: Try "/opt/splunk/bin/splunk start" - like an init script.

I get the same error whether I use:

./splunk start 

or the fully qualified path.

Any thoughts? Googling didn't provide much info.

Ubuntu Server 9.04

---

### Post by hallm on 2010-12-02
I'm running a webserver Apache MySQL PHP Pear on Intrepid server.  Will installing Splunk on that same server cause any issues that anyone's aware of?  I'm mainly going to use splunk to capture router logs and server logs, etc.

---

### Post by plao on 2012-12-14
Thanks thanks thanks thanks!!!!
Excellent guide...man, you saved me!

:KS

---

