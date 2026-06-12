---
title: "Simple instant messaging server?"
date: 2007-01-03
forum: Server Platforms
---

### Post by christian.convey on 2007-01-03
I'd like to set up a simple instant messaging service within my office.  

I'm not too concerned about user authentication, going through firewalls (other than the one that Edgy installs by default on the desktop that will host the service, etc.), etc.  It only needs to support a few users (< 10).

Also, I'm not very experienced in setting up network services under Linux, so I'd like to not have to futz much with my firewall, etc.

Any recommendations?

---

### Post by Brazen on 2007-01-03
you'll want to use a Jabber server.  The most popular seems to be ejabberd, and then probably Gaim as a client (there are Windows and Linux versions of Gaim).  Search for ejabberd here on the forums and there is a thread with a well written HowTo.

---

### Post by crouton on 2007-01-08
You may want to look at the [Wildfire IM Server]("http://www.jivesoftware.org/wildfire/").  They're moving to a new site, so you could also try [this link.]("http://www.igniterealtime.org/projects/wildfire/index.jsp")  It has a client called Spark, also at either root site.

I haven't used it, but it looks very interesting and there is a Linux/Unix version.

---

### Post by aragorn2909 on 2007-01-08
I have setup Wildfire servers both at my home on an Edgy install and my workplace on a Gentoo server.  Painless install and easy administration, and it just runs.  Hands down my personal choice.

A.B.

---

### Post by InlineFive on 2007-01-11
Do you know of a writeup for installing Wildfire on Ubuntu Server?

Edit: Nevermind, I must have borked the install because I started a new VM from scratch and now it works fine.

---

### Post by netventure on 2007-01-25
Hi,

This might be a little late but i'm posting my experience for some soul that may come searching for this.

The installation I'm describing here is very quick, basic and not-very-secure, but should be enough to get people started.

I've installed Wildfire 3.1.1 on Dapper & Edgy by following these steps:

[LIST=1]
[*]If java is not installed install it with 
```
apt-get install sun-java5-jre
```
[*]Get the wildfire tarball (not RPM) from [this URL]("http://www.jivesoftware.org/downloads.jsp#messenger")
[*] Untar to /usr/local or /opt (putting it elsewhere will need additional configuration which is not covered here)
```
cd /usr/local; tar zxvf wildfire_3_1_1.tar.gz
```
[*]Edit /usr/local/wildfire/bin/extra/wildfired and make these changes:

a. Comment the line by adding # at the begining: 
```
#export WILDFIRE_USER=jive
```
b. Add this line below the above line
```
export INSTALL4J_JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun 
```
c. Save the file and close it.

[*]Copy the script to init.d and add to startup sequence: 
```
sudo cp /usr/local/wildfire/bin/extra/wildfired /etc/init.d/
sudo update-rc.d wildfired defaults 
```
[*]Now start wildfire server with this command (If you get any messages about 'nohup.dat', ignore it.)
```
 sudo /etc/init.d/wildfired start
```
[*] Wait a minute or two for the server to start up it's components.
[*] Access the web management interface through the browser:
```
http://127.0.0.1:9090/
```
[*] Follow the configuration steps which are simple. For a simple and quick setup, use the Embedded database (HSQLDB)
[*] For the domain name, give something short, or even your website domain. Ex: **yourspace.com** or even **homenet**
[*] Create a test user.
[/LIST]


Your IM server should be up now. :guitar: You can use any jabber client to connect to it.

There are 2 things you should know:
**Username: ***the account name as created in the web interface*
**Domain: **yourspace.com or homenet
**Server: **IP.Address.Of.Wildfire.Server


Hope that helps.

-NV

---

### Post by deethree on 2007-01-27
That tar ball seems to be borked. downloaded it a few times now and I get errors when I try to do anything with it. *sigh* Maybe its just me.

---

### Post by krokodil on 2007-01-31
> **deethree said:**
> That tar ball seems to be borked. downloaded it a few times now and I get errors when I try to do anything with it. *sigh* Maybe its just me.

It's not just you. Am struggling with the tarball too. :(

---

### Post by fellwind on 2007-03-14
```
:/etc/init.d$ sudo /etc/init.d/wildfired start
/etc/init.d/wildfired: 52: Syntax error: "(" unexpected
```

I'm getting this error trying to use the tarball, any thoughts?

---

### Post by jkeyes0 on 2007-03-14
btw, I also needed to run
```
sudo chmod 755 /etc/init.d/wildfired
```

to make it executable so the service would run. I've logged in and created accounts and everything.

Note: the administrator username that you set a password up for is "admin"

---

### Post by shoki on 2007-03-17
Good info i am going to try this at work. We have Linux, Mac, and Windows clients and it would be nice if they all could chat.

---

### Post by themaninblack on 2007-03-18
Thanks a bunch for the walkthrough - 1 question:  If you follow those steps for the install on Ubuntu Server, how are you supposed to get to the web interface by going to 127.0.0.1:9090?  Is there some way to edit the config from a command line so it would allow me access to the administration GUI from the internet instead?

---

### Post by themaninblack on 2007-03-18
According to the forums at igniterealtime.org the administrative interface isn't available from the internet on the open source version, so I'm in stalling ubuntu-desktop on my server.  Wild/Openfire looks cool enough to justify it :)

---

### Post by themaninblack on 2007-03-20
OK, I switched to a dektop install of Ubuntu and followed the walkthrough.  Now when I try to start the Wildfire server, I get this:

/etc/init.d/wildfired: 51: Syntax error: "(" unexpected

Any ideas?

---

### Post by renz on 2007-03-27
When I enter

/etc/init.d# /etc/init.d/wildfired start

I get

bash: ./wildfire.sh: No such file or directory

Any idea(s) as to what I've done wrong?

---

### Post by bb002 on 2007-10-11
> **themaninblack said:**
> OK, I switched to a dektop install of Ubuntu and followed the walkthrough.  Now when I try to start the Wildfire server, I get this:

/etc/init.d/wildfired: 51: Syntax error: "(" unexpected

Any ideas?

yeah someone goofed the init script in the tar ball.

Change:```
funtion execCommand() {
```
to:```
execCommand() {
```

think i made a few other changes to it too...can't remember. lol

---

