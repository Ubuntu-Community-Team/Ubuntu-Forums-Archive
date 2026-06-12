---
title: "Help in Setting up a Jabber Server"
date: 2007-11-27
forum: Server Platforms
---

### Post by habtish on 2007-11-27
Hello,

I am wanting to test out a jabber server for office use only (intranet) and installed jabberd on a Gutsy VM following the following guide[ here]("https://help.ubuntu.com/community/SettingUpJabberServer").
To my disappointment, there wasn't a whole lot of guidance on how to setup the server for the sort of use I had wanted to test. I guess am too unexperienced to understand what was listed there and am asking for help here. Here's my set-up:[LIST]
[*]Ubuntu 7.10 running on an XP host, MS-SBS server network in the office
[*][ifconfig] in the terminal gives me an ip of 10.0.029 on eth0, not sure if I should be using this IP for JABBER_HOSTNAME (used the hostname of the VM machine)
[*]Need help on how to set-up new users and/or administer registering new users[/LIST]I can not connect to the jabber server using Pidgin as am sure I have not set things up right in jabber.cfg

I appreciate any suggestions. 

Thanks!

---

### Post by nicweb on 2007-11-27
Perhaps you should give openfire a try ([http://www.igniterealtime.org/projects/openfire/index.jsp](http://www.igniterealtime.org/projects/openfire/index.jsp))... its a easy to use jabber server written in java

---

### Post by jtc on 2007-11-27
[Jabberd2]("http://jabberd2.xiaoka.com/") has a rather nice [Installation guide]("http://jabberd2.xiaoka.com/wiki/InstallGuide").

No matter if you use Jabberd or Jabberd2 the xml configuration files are pretty well commented.

Regarding Openfire it is definitely nice and easy to use. Still, having Java using all that memory...

---

### Post by doogy2004 on 2007-11-27
Give Open Fire a try (formerly WildFire) [http://www.igniterealtime.org/projects/openfire/index.jsp](http://www.igniterealtime.org/projects/openfire/index.jsp)  It is easy to setup and manage.

---

### Post by habtish on 2007-11-28
Ok, I decided to give openfire a try. Installation was an easy process and good documentation on the website. On set-up I used the local domain name of the machine (cbco) as the domain and not the IP of the machine. (all this is still running inside an Ubuntu VM).

Trying to connect to the VM ip (10.0.0.29) via Pidgin  gives a stream error. Same result via a web browser:5222

I can access 10.0.0.29 at port 80 and access the webpage I have put put to test apache2. What am I missing here in the server set up processes (both Jabbed and openfire) that I can't connect to these XMPP servers?

TIA

---

### Post by habtish on 2007-12-05
After a restart of the machine, I was able to get jabberd running right and I was able to register a user name through Pidgin. Now the problem I have is, once logged in, I can not add/find other users on the same server and get the error ```
 Could not query the directory server.
502: Unable to resolve hostname. 
``` when searching and ```
XMPP Message Error
Message delivery to test failed: Unable to resolve hostname. (Code 502)
``` when trying to send.

If the jabberd is limited within the local network, does its hostname need to be a qualified domain name (jabber.myhostname.com) which resolves? Why won't using the IP (10.0.0.29) as the hostname in jabber.cfg and jabber.xml work?
I am willing to apt-get remove --purge and re-install to start from scratch and  get this to work.

---

