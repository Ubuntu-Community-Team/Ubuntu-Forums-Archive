---
title: "iptables"
date: 2010-07-06
forum: Security
---

### Post by judoka1113 on 2010-07-06
I do $ sudo iptables -A INPUT -p TCP -i eht0 --destination-port 80 -j  ACCEPT
and then $ sudo ufw enable
but I still get no internet traffic.  What is wrong? Shouldn't opening  port 80 to TCP allow the packets  though my firewall?]

---

### Post by bodhi.zazen on 2010-07-06
using iptables directly and ufw are not the same thing.

If you are going to use iptables, use iptables.

If ufw, use ufw, but it is not so easy to mix and match. You would need to edit /etc/ufw/before-rules and add that iptable rule.

```
sudo ufw allow 80
```

    [http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/](http://blog.bodhizazen.net/linux/firewall-ubuntu-gufw/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/](http://blog.bodhizazen.net/linux/firewall-ubuntu-desktops/)
    [http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/](http://blog.bodhizazen.net/linux/firewall-ubuntu-servers/)

Hard to tell what your problem is exactly. Are you running a web server ? If so, did you forward port 80 ? 

If you are not running a server, are you limiting outgoing connections ?

---

### Post by judoka1113 on 2010-07-06
I did $ sudo ufw allow 80      but it still doesn't let me see load internet pages.  And I thought that you're sopposed to configure ufw through iptables.  If that is not so then how do you configure ufw? I tired to do $ sudo gedit /etc/ufw/before-rules   but just got a blank document, when i added the sudo ufw allow there is still didn't work.

---

### Post by bodhi.zazen on 2010-07-06
is your internet connection working ?

---

### Post by judoka1113 on 2010-07-06
yes,  when i do:
```
$ sudo ufw disable
```
all works fine, i can surf the net
but when i do:
```
$ sudo ufw enalbe
```
it shuts me our completely
even if i do:
```
$ sudo ufw allow 80
```
nothing happens
it just tells me 
> can't find server
how can i see how ufw is set-up?

---

### Post by judoka1113 on 2010-07-06
I'm also followinf your instructions that your posted on another thread on how to set-up tar.gz files.
I'm trying to set-up fwbuilder-4.0.1.tar.gz
and when i cd in to the dir where the file got untarred to and do:
```
./configure
```
it tells me:
[HTML]bash: ./configure: No such file or directory[/HTML]
I already set-up checkinstall
what am I doing wrong?

---

### Post by judoka1113 on 2010-07-06
in the fwbuilder-4.0.1 folder there are:

configure.in
config.h.in
and install.sh 

files.  should i use these when doing ./
maybe like ./configure.in
instead of ./configure?

---

### Post by judoka1113 on 2010-07-06
By the way, thanks for the links you poster earlier in the string.
I'm reading over them now and find them to be exactly what I was looking for.

---

### Post by bodhi.zazen on 2010-07-06
My guess would be you set ufw to deny outgoing traffic.

Post the output of 

```
sudo ufw status verbose
```

---

### Post by judoka1113 on 2010-07-06
it says:
> Status: inactive

---

### Post by bodhi.zazen on 2010-07-06
> **judoka1113 said:**
> it says:

Well, it it is inactive, your firewall is not blocking your traffic.

FYI when you surf the web, you connect to port 80 on the server. Your computer, as the client, uses a pseudo-random port higher then 1024.

See: [http://bodhizazen.net/Tutorials/iptables](http://bodhizazen.net/Tutorials/iptables)

---

### Post by judoka1113 on 2010-07-06
Thanks for writing the tutorials, they are really great.

---

### Post by bodhi.zazen on 2010-07-06
> **judoka1113 said:**
> Thanks for writing the tutorials, they are really great.

You are most welcome =)

---

### Post by judoka1113 on 2010-07-06
Correction on my previous post:
I forgot to enable the firewall before checking the status
here's the status after enabling it
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
80                         ALLOW IN    Anywhere


```
the weird thing is that I have to disable the firewall before i'm reconnected back to the internet
doesn't the above status check indicate that i should receive internet connection even if
my firewall is enabled?

---

### Post by bodhi.zazen on 2010-07-06
> **judoka1113 said:**
> Correction on my previous post:
I forgot to enable the firewall before checking the status
here's the status after enabling it
```
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
80                         ALLOW IN    Anywhere


```the weird thing is that I have to disable the firewall before i'm reconnected back to the internet
doesn't the above status check indicate that i should receive internet connection even if
my firewall is enabled?

I would not expect those settings to block internet access.

---

### Post by judoka1113 on 2010-07-06
One last question:
I'm also following your instructions that your posted on another thread on how to set-up tar.gz files.
I'm trying to set-up fwbuilder-4.0.1.tar.gz
and when i cd in to the dir where the file got untarred to and do:
Code:

./configure

it tells me:
HTML Code:

bash: ./configure: No such file or directory

n the fwbuilder-4.0.1 folder there are:

configure.in
config.h.in
and install.sh

files. should i use these when doing ./
maybe like ./configure.in
instead of ./configure?

---

### Post by bodhi.zazen on 2010-07-06
You can try running the install.sh

In general, IMO, if you are not going to use ufw I advise learning iptables.

---

