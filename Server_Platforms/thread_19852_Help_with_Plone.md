---
title: "Help with Plone"
date: 2005-03-14
forum: Server Platforms
---

### Post by Vaquero on 2005-03-14
I am running Hoary and am trying to setup a Plone server. Apt-get went well with no error message. Unlike Window installation, it never stops to ask me to setup password and such. Also, when trying to connect to [http://localhost:9673/manage](http://localhost:9673/manage) will only get a connection refusal, what did I miss ?  This is a fresh Hoary install.

---

### Post by Myles3 on 2005-03-15
I have recently installed plone on my server and I found the best this is to install zope with apt-get then install plone form source.

---

### Post by Vaquero on 2005-03-15
After looking everywhere and numerous trial, here is what I did:

apt-get install plone
apt-get install plone-site

now it prompts me to set up an admin acct, I am in and tweaking the system now  but I can't connect to the Plone server  form another computer, any thoughts ?

---

### Post by Myles3 on 2005-03-15
use the local computer untill you add another user and you will be fine.

---

### Post by Roceal on 2005-05-29
I am attempting the same, but when I try to install the plone-site package, I get the following error:

Preconfiguring packages ...
Selecting previously deselected package plone-site.
(Reading database ... 89805 files and directories currently installed.)
Unpacking plone-site (from .../plone-site_2.0.4-3ubuntu3_all.deb) ...
Setting up plone-site (2.0.4-3ubuntu3) ...
Traceback (most recent call last):
  File "/usr/sbin/dzhandle", line 1983, in ?
    main()
  File "/usr/sbin/dzhandle", line 1979, in main
    rv = action.run(global_options)
  File "/usr/sbin/dzhandle", line 1361, in run
    rv = subprocess.call(cmd)
  File "/usr/lib/python2.4/subprocess.py", line 428, in call
    return Popen(*args, **kwargs).wait()
  File "/usr/lib/python2.4/subprocess.py", line 558, in __init__
    errread, errwrite)
  File "/usr/lib/python2.4/subprocess.py", line 991, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory

I had no problems getting Plone up and running on Debian, but now that we have switched to Ubuntu I can't figure out how to get it to appear in the Zope Management Interface. Any info would be appreciated.

---

### Post by tread on 2005-05-29
Repository problem possibly? Using debian repos in ubuntu is usually not a good idea .. are you doing that?

---

### Post by istoyanov on 2005-05-29
I have installed zope + plone from source as per documentation (without any previous experience) on a warty-powered server and everything went as expected!

Hence I would suggest you to remove the apt-get-ed packages and to try to install zope+plone from source -- just to have everything under control:)

HTH

---

### Post by ripounet on 2005-06-03
Here is how it went with me:
Installation via Synaptic. Looked frozen. Had to click to access to the console, where a password and its confirmation where asked.
[http://localhost:9673/manage](http://localhost:9673/manage) refused any possible login name (which I never chose?!) even with the correct password.
Running zpasswd.py as root, i chose the login name 'admin' and re-typed a password.
Access still denied.
Took me a while before i looked in /var/lib/zope/instance/default/access and found that this "fine" bastard had a login entry 'Admin' with a capital A, which was NOT what i had chosen.
Access granted with login 'Admin'.

---

### Post by otherdave on 2005-06-22
[QUOTE=istoyanov]I have installed zope + plone from source as per documentation (without any previous experience) on a warty-powered server and everything went as expected![/QUOTE]

Can you tell me which versions you installed? I tried this last night with Zope 2.8 and the latest plone (both from source). After seeing some errors during the set up part (once I created a Zope instance and tried to work in Plone) I read online that the latest Plone likes Zope 2.7 and NOT 2.8.

I plan on trying again tonight (time permitting of course) with Zope 2.7.x

---

### Post by limi on 2005-07-18
Plone 2.0.x (which I believe is what Ubuntu ships with) does not run under Zope 2.8, due to fundamental achitectural changes in the new version of Zope.

The upcoming Plone 2.1 runs on Zope 2.8, check [http://plone.org/roadmap](http://plone.org/roadmap) for more details.

The Debian packaging of Plone has traditionally been very badly executed, so your best bet is normally to install the correct Python version (2.3.5) and install Zope and Plone from source. Plone itself is just a matter of dropping directories in the correct Zope subdirecotry, no installation as such is required.

A good how-to can be found at [http://plone.org/robust-installation](http://plone.org/robust-installation) - have fun with Plone, and don't forget that Plone has a friendly and helpful community - both mailing lists and IRC are options: [http://plone.org/contact](http://plone.org/contact)

---

### Post by Druke on 2005-07-18
you have to start the server 

> zopectl startzope

---

