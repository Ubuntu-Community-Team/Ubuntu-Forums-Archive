---
title: "HOWTO: Proxy Support"
date: 2004-10-21
forum: Tutorials
---

### Post by gecko on 2004-10-21
[size=6]Proxy Support[/size]

**Proxy support for Synaptic Package Manager.**
Start the software and click Settings-> Preferences-> Network Tab. Click Manual Proxy Configuration and enter your proxy information. If you have to login to the proxy then use the host format username:password@host.

**Proxy support for apt-get package management**
Define the http_proxy variable in the format http://host:port/. If you have to login then use the format http://username:password@host:port/. To define this variable add the following lines to the root login file /root/.bashrc.

http_proxy=http://username:password@host:port/
export http_proxy

**Proxy support for Mozilla Firefox**
Start Mozilla then click on Edit->Preferences. In the General section click on Connection Settings. Enter your proxy infomation here. If you have to authenticate against your proxy then Mozilla will prompt you for a username and password.

**Proxy support for the Gnome desktop**
Click on Computer->Desktop Preferences->Network Proxy
Enter your proxy information here. How do you enter proxy auth here?

**Contribute!**
When you find more proxy configuration steps for other applications then post it as a reply to this message. One day in the future this will be a simple applet that will ask you proxy settings and configure all this for you. *hint* *hint*

---

### Post by FLeiXiuS on 2004-10-22
Very nice, I think you should include the FireFox plugin which allows you to search for a proxy then connect instantly for web browsing.

---

### Post by jdong on 2004-10-24
[QUOTE=gecko][size=6]Proxy Support[/size]

**Proxy support for apt-get package management**
Define the http_proxy variable in the format [http://host:port/](http://host:port/). If you have to login then use the format [http://username:password@host:port/](http://username:password@host:port/). To define this variable add the following lines to the root login file /root/.bashrc.

http_proxy=http://username:password@host:port/
export http_proxy
[/QUOTE]

Ok, extend this a bit:
**Proxy support for the CLI**
Add the following lines to the file /etc/environment

export http_proxy="http://username:password@host:port/"


This will also apply to apt at the CLI. Some applications may pick this up, too. If it doesn't work for you, add the line to /etc/bash.bashrc and /etc/profile, too.

---

### Post by khairillthegreat on 2007-01-17
hi. i just want to ask where the proxy cinfiguration is saved. when i first install ubuntu the installer pop a dialog that asked my proxy configuration. in what text file is this setting saved?

---

### Post by airtonix on 2007-07-03
ok so : 
if i previously used the gnome-gui to change proxy settings ..

then if i had removed the desktop enviroment, right back to terminal machine only....no gui

how do i edit those proxy settings?....like with nano...which file to open?

---

### Post by Jilbert on 2007-07-15
am getting a permission denied error. I don't know how to enable the root account on the terminal. btw, just installed ubuntu server feisty and it doesnt come with gdm. :(

---

### Post by sageb1 on 2007-11-01
$ sudo nano -w /etc/bash.bashrc

then place the following at end of file:

# export http_proxy:port
if [ -z "$http_proxy" ]; then
    export http_proxy="http://proxy_host_name:port/"
fi

---

### Post by Linfreak on 2009-01-12
If the password in [http://username:password@host:port/](http://username:password@host:port/) contains a '@' symbol then it takes the username wrong.

eg:

if username = xxxx and password = zzzz@yyyy

then command would look like [http://xxxx:zzzz@yyyy@host:port/](http://xxxx:zzzz@yyyy@host:port/)

so when i use 

$>apt-get update

it gives "connecting to yyyy@host:port" instead of 
"connecting to xxxx:zzzz@yyyy@host:post/"

how do i actually make it take the username and password together?


Thanks in Advance,
Siva

---

### Post by michelkogan on 2009-07-19
this saved me ... GOD THANKS ... for weeks I have a problem with anon-proxy and apt-get . Thanks ...

---

### Post by mozartlova on 2009-08-20
i don't suppose anyone knows how to include the following into a http_proxy
variable that parses correctly when passed to wget (it seemingly doesn't
work when you just type it into the 'details' section of the network proxy
authentication either ...

username is domain\username@company.com
(i would imagine the "\" and "@" are the difficulties here)
password is blah
proxy server is proxy.company.com and
port is 8080

it works (of course) when you type it into the proxy authentication of a
browser, but fails to parse for me (not when doing the "export http_proxy")
when doing the wget.

---

### Post by MegaJim on 2009-10-21
> **mozartlova said:**
> i don't suppose anyone knows how to include the following into a http_proxy
variable that parses correctly when passed to wget (it seemingly doesn't
work when you just type it into the 'details' section of the network proxy
authentication either ...

username is domain\username@company.com
(i would imagine the "\" and "@" are the difficulties here)
password is blah
proxy server is proxy.company.com and
port is 8080

it works (of course) when you type it into the proxy authentication of a
browser, but fails to parse for me (not when doing the "export http_proxy")
when doing the wget.

http_proxy=http://domain\\username@company.com:blah@proxy.company.com:8080

---

### Post by jdros on 2010-07-05
When you use some proxy settings during installation (Ubuntu 10.04 server), these settings are saved in:

**[FONT=Courier New]/etc/apt/apt.conf:[/FONT]**
[FONT=Courier New]Acquire::http::Proxy "http://x.x.x.x:port";[/FONT]

To setup a (different) proxy for [FONT=Courier New]apt-get[/FONT], you should change this file also.

---

### Post by Quattr0 on 2010-07-05
> **MegaJim said:**
> http_proxy=http://domain\\username@company.com:blah@proxy.company.com:8080

I had the same issue and this solution did not work for me. Any ideas anyone?
username: OCS\username
password: pass

I tried http_proxy="http://OCS\\username:pass@proxy:8080/"; but I still get

error 407 Proxy access denied.

---

### Post by bacardiandwatermelon on 2010-07-23
Does you username have a "." in it? you will need to put a backslash in front of that aswell...

---

### Post by sr20ve on 2010-09-01
> **MegaJim said:**
> http_proxy=http://domain\\username@company.com:blah@proxy.company.com:8080

Thanks, that's what I was missing. My password also contains special characters (!@()) which need to be preceeded by a \.

---

### Post by chopp3r on 2010-10-03
Having been through this whole proxy setting business myself just recently, I thought it may be helpful to post a complete and definitive list of the places you should check for proxy server settings. Some of the files listed here are updated when you set your proxy server through the Ubuntu *System > Preferences > Network* Proxy dialog and choose yes to the question on whether you want to Apply these settings to the entire system.

# /etc/environment
# /etc/bash.bashrc
# /etc/profile
# /etc/apt/apt.conf
# ~/bashrc
# ~/profile
# ~/bash_profile

My Recommendation, if you do not have a user-name and password associated with your proxy access, is to set the proxy server using the Ubuntu *System > Preferences > Network Proxy* dialog. When applying these settings, ensure you choose to apply them to the *entire* system.

If you do have a user-name and password to enter, then I would add the server settings to the **/etc/environment** and **/etc/apt/apt.conf** files. This will set your proxy server credentials for all sign-in accounts on your Ububtu desktop system.

---

### Post by denix on 2011-11-28
Hi all,
thanks for the interesting post, I've lost hours myself trying to figure out how to do apt behind a proxy.
Now I have another problem, I have drupal installed and it is unable to connect to the outside. How do we set proxy variables for web applications in php and perl?

Denis

---

### Post by cirobr on 2012-01-24
Hello,

May I please ask you what about Lubuntu distribution and Google Chrome? Lubuntu apparently comes with no global proxy setting, and Chrome Preferences can not locate the environment configuration.

In my case, Lubuntu is installed on a Windows host running Virtualbox.

Thanks.

---

### Post by cirobr on 2012-01-24
> **cirobr said:**
> Hello,

May I please ask you what about Lubuntu distribution and Google Chrome? Lubuntu apparently comes with no global proxy setting, and Chrome Preferences can not locate the environment configuration.

In my case, Lubuntu is installed on a Windows host running Virtualbox.

Thanks.

Have just found solution at:

[http://ubuntuforums.org/showthread.php?p=11636648#post11636648](http://ubuntuforums.org/showthread.php?p=11636648#post11636648)

---

### Post by Chanemis on 2012-06-11
ok I am new to ubuntu and I am installing it on my old pc.  I was wondering what is the port on the back of my HTTP proxy.  I am sorry if this sounds like a stupid question.

---

### Post by free1proxy on 2012-06-30
Very nice, I think you should include the FireFox plugin which allows you to search for a [proxy sites]("http://proxy125.com") then connect instantly for web browsing.

---

### Post by arsol76 on 2012-07-15
i just for try added  http_proxy=http://username:password@host:port/ to terminal.and it now just use this proxy to connect internet! and next i entered apt-get update to terminal and this time it give me unauthorized error and i know this problem  is for proxy server and i wanna redo this things that i did for proxy how can i do it?please help me i want install a app and i can't.

---

### Post by arsol76 on 2012-07-16
> **arsol76 said:**
> i just for try added  http_proxy=http://username:password@host:port/ to terminal.and it now just use this proxy to connect internet! and next i entered apt-get update to terminal and this time it give me unauthorized error and i know this problem  is for proxy server and i wanna redo this things that i did for proxy how can i do it?please help me i want install a app and i can't.

 Any Idea?

---

