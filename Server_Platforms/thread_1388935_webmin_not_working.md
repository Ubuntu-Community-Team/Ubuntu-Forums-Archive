---
title: "webmin not working"
date: 2010-01-23
forum: Server Platforms
---

### Post by Gipsy25 on 2010-01-23
I installed ubu server 9.10 on my desktop, then i tried to install webmin and i was able to do that too.

When i try to connect to webmin i get "page cannot be displayed" so i thought let's change the port...i changed to port 443 as recommended on the website.
Same problem. here is the miniserv.conf
> 
port=443
addtype_cgi=internal/cgi
realm=Webmin Server
logfile=/var/webmin/miniserv.log
errorlog=/var/webmin/miniserv.error
pidfile=/var/webmin/miniserv.pid
logtime=168
ppath=
ssl=1
env_WEBMIN_CONFIG=/etc/webmin
env_WEBMIN_VAR=/var/webmin
atboot=1
logout=/etc/webmin/logout-flag
listen=443
denyfile=\.pl$
log=1
blockhost_failures=5
blockhost_time=60
syslog=1
session=1
premodules=WebminCore
userfile=/etc/webmin/miniserv.users
keyfile=/etc/webmin/miniserv.pem
passwd_file=/etc/shadow
passwd_uindex=0
passwd_pindex=1
passwd_cindex=2
passwd_mindex=4
passwd_mode=0
preroot=blue-theme
passdelay=1
sudo=1
root=/usr/share/webmin
mimetypes=/usr/share/webmin/mime.types

Now i tried connecting using the ip address and the hostname i also tried with http and https
[https://hostname.com:10000](https://hostname.com:10000) and 443 ... no go

I was wondering if someone might know what the problem is. :(

Thanks in advanced

---

### Post by pirateghost on 2010-01-23
> **Gipsy25 said:**
> I installed ubu server 9.10 on my desktop, then i tried to install webmin and i was able to do that too.

When i try to connect to webmin i get "page cannot be displayed" so i thought let's change the port...i changed to port 443 as recommended on the website.
Same problem. here is the miniserv.conf

Now i tried connecting using the ip address and the hostname i also tried with http and https
[https://hostname.com:10000](https://hostname.com:10000) and 443 ... no go

I was wondering if someone might know what the problem is. :(

Thanks in advanced
did you install all the dependencies as well?

i always add the webmin repo to my /etc/apt/sources.list and then run apt-get update, apt-get install webmin.  it pulls in all the dependencies...

---

### Post by Gipsy25 on 2010-01-23
I am sorry ...i was able to find the file you mentioned, however i am not sure what you mean by adding the repo to the file .... 

The installation just said to download the file and install it ... that is what i did ... then i rebooted the server to apply changes ...then 
apt-get update 
that is all i did ... am i missing something ??

thanks

---

### Post by Gipsy25 on 2010-01-24
(update) 
I did some more research on what was suggested, (repositories), and i added the webmin repo in the /etc/apt/sources.list but i am still having the same issue.

---

### Post by pirateghost on 2010-01-24
> **Gipsy25 said:**
> (update) 
I did some more research on what was suggested, (repositories), and i added the webmin repo in the /etc/apt/sources.list but i am still having the same issue.
after you added them to the repos did you do apt-get update and apt-get install webmin?

---

### Post by Gipsy25 on 2010-01-24
That is correct, as stated on your previous post.

a) added to the repo
b) run the update (got an error) something about a key ... so i installed the public key
c) sudo apt-get install webmin

it said the newest version was already installed...

I am going to try removing the app and reinstalling again ... see if it works that way... (I will let you know)

Thanks for trying to help ... :)


I found this link but i dont know if this is correct:
[http://sourceforge.net/tracker/index.php?func=detail&aid=2876859&group_id=17457&atid=117457](http://sourceforge.net/tracker/index.php?func=detail&aid=2876859&group_id=17457&atid=117457)

It says that webmin might not work in ubuntu server 9.10 but it was tested on beta version. Do you know anything about that???

---

### Post by Gipsy25 on 2010-01-24
This is what it says... it seems to me that i am doing it right:
> 
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/14.4MB of archives.
After this operation, 89.8MB of additional disk space will be used.
Selecting previously deselected package webmin.
(Reading database ... 57385 files and directories currently installed.)
Unpacking webmin (from .../archives/webmin_1.500_all.deb) ...
Setting up webmin (1.500) ...
Webmin install complete. You can now login to [https://aaa.bbb.com:10000/](https://aaa.bbb.com:10000/)
as root with your root password, or as any user who can use sudo
to run commands as root.

I did it the way you told me to, prior to that i followed instructions on the website ... downloaded the package and ran the webmin_1.500_all_deb but i keep getting the same results ... 

The computer is connected to the internet ... works fine ... i am connected to the server using the terminal from another pc ... and i am installing it from there ... Could that be the problem??? 
I guess i am just looking for an explanation that makes sense ... i opened the port 10000 in my router too ... so i know that is not the issue.:(

Thanks

---

### Post by Gipsy25 on 2010-01-25
Does anyone knows what might be the problem.???? 
I've been doing research but i hit the wall every time. 

Any kind of help would be appreciated. 

Thanks

---

### Post by pirateghost on 2010-01-25
> **Gipsy25 said:**
> This is what it says... it seems to me that i am doing it right:

I did it the way you told me to, prior to that i followed instructions on the website ... downloaded the package and ran the webmin_1.500_all_deb but i keep getting the same results ... 

The computer is connected to the internet ... works fine ... i am connected to the server using the terminal from another pc ... and i am installing it from there ... Could that be the problem??? 
I guess i am just looking for an explanation that makes sense ... i opened the port 10000 in my router too ... so i know that is not the issue.:(

Thanks
i use webmin on all my linux servers, from ubuntu server 9.10, arch, debian5, ubuntu 8.04, etc.

i have never installed by using the .deb file

i have always installed installed it via 'apt-get install webmin' after adding the repo, and i have almost always done this via ssh from another machine.  there should be no reason to open a port on your router for local access.  all that does is open it up to the outside world.

have you tried going to it by IP address since you reinstalled?

[https://xx.xx.xx.xx:10000](https://xx.xx.xx.xx:10000)

---

### Post by Gipsy25 on 2010-01-25
Yes.I did try that. IP address and host name. It takes for ever (loading) and then it says to try again. 

I usually do a lot of searching before to post anything, but with this one ... dont know ... i cant figure out.

I am using no-ip for my FTP ... do you think that this could be part of the problem? 
 It is installed on the server itself... 
I thought to mention that just in case ...

Is there any logs i can check to see what could be the causing the problem???

---

### Post by painejake on 2010-01-26
Are you behind a proxy accessing it via the IP? If so make sure to add the ip into your browsers exeptions.

For example 127.0.0.1:*

Also I've never had this issue and always install via the .deb - Don't like added source locations to the sources file that aren't needed.

Also make sure the dependencies are installed 

> sudo apt-get install perl libnet-ssleay-perl openssl libauthen-pam-perl libpam-runtime libio-pty-perl libmd5-perl

Then restart webmin

> sudo /etc/init.d/webmin restart

---

### Post by Gipsy25 on 2010-01-28
The problem is solved. I read in several articles that by default, ubuntu doesn't firewall anything (the policies for the chains are all set to ACCEPT). So having nothing else to check and having no other place to go with the situation i checked the settings of the firewall, i don't know much about it yet but the problem i had was the port some how was closed. 

so i just opened the port in my "iptables" and that fixed the problem ... to be honest i don't even know if i modified it it by default it was closed ... but i know it works now 

sudo iptables -A INPUT -p tcp -d 0/0 -s 0/0 --dport 10000 -j ACCEPT

hopefully i didnt open nothing else with that last command .... 

I just thought to let you know what was the solution to the problem.

**_P.S: i do want to thank you guys for all the advice and the help ... I really appreciate it._** 

Respectfully 

Gipsy ;)

---

### Post by Gipsy25 on 2010-01-28
thank you

---

### Post by pirateghost on 2010-01-29
> **painejake said:**
> 
Also I've never had this issue and always install via the .deb - Don't like added source locations to the sources file that aren't needed.


but when they update webmin, its easier to have it in the repo

---

