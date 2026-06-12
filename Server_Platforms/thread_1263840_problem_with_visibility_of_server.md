---
title: "problem with visibility of server"
date: 2009-09-11
forum: Server Platforms
---

### Post by adramalech on 2009-09-11
okay so i was able to setup my ubuntu server....my issue is my server is running at home....but yet i cannot login from outside of my local access!

i am wondering why it is i cannot connect to my webpage that should be running....and i have ddclient running...and my router is linksys so when ever my dhcp wan changes it changes the dns...to link it...

but it still seems that there are issues wrong with my access of my server from say like my college or my parents house....

i have ports 20-22 open for my ssh server access, ftp server access, and then port 80 is open from my router...and it is allowed through ufw on my server....so i don't know why i am being restricted from using the actual server so i can maintain it...

---

### Post by eymorais on 2009-09-11
Had the same issue on my first install.

I had to activate the basic firewall and to open the ports on it also to be able to access it out of my lan.

you can try with this [https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo) or if you install [webmin]("http://www.ubuntugeek.com/ubuntu-serverinstall-gui-and-webmin-in-ubuntu-810-intrepid-ibex-guide.html") on your box you can control it that way also.

Hope this helps.

---

### Post by adramalech on 2009-09-11
umm.... I did have ufw running to deny all port access except port 20-22 and port 80.... I also have port forwarding to my local static ip so when I do ssh to my server my router should forward my request to my server

also I don't want to install desktop on my server that way the server has less processes running...

i might be wrong but I would think that my dens is to blame...

---

### Post by cariboo on 2009-09-11
Just to be sure the ports you want are open use [canyouseeme]("http://canyouseeme.org/"), it may be that your isp is blocking port 80.

---

### Post by adramalech on 2009-09-11
maybe it is.....

so i will switch to port 8080

but it still doesn't help the fact i am using port 21 and 22 for ftp and ssh and it timesout like it isn't there....

because i cannot restart apache because it says something about serverName is wrong or dns server cannot be resolved....

but i look at the file with dns and it is the router....so what i am thinking is the apache is being blocked...

butttt..... it still doesn't tell me why i cannot access vsftpd server or my openssh server....  it isn't denying it so it probably isn't the ufw settings it is just having something to do with the actual connecting to my domain...i need to check to make sure it is linking correctly the ddns needs to maybe see the right ip....

---

### Post by adramalech on 2009-09-11
i also found out my ddns is pointing to 192.168.80.128 which is my server on my local...not on my wan!!! maybe that is a problem so what i need to do is just update my ddns from my router and get it pointed at my wan...and then i should be good to go!

---

### Post by adramalech on 2009-09-13
okay so i did a port scan of my wan ip at my house from my dad's house and none where open but i did a traceroute of the same ip and it worked and i also did a ping etc...and i might just call up my isp and ask them what ports are open???

i will also have to go through the apache2 config file and switch to port 8080 also in my phpmyadmin config file....

---

### Post by Rob_H on 2009-09-13
Assuming router is configured correctly to forward those ports and they're open on the server, there are a couple of other possibilities:

(1) When you did the port scan from your dad's house (good idea, by the way), you got the IP address wrong. Your ISP may change it every so often and even if you're using dynamic DNS, the client that's updating the DNS server may lag behind by some amount of time. Have your dad try it while you're sitting at home and can verify your public IP address at the time of the test.

(2) Your ISP could be filtering the traffic. Pay a visit to [ShieldsUP!]("http://www.grc.com/intro.htm") to see what ports are accessible from the Internet. If the 20-22 port range is closed or stealthed, either your ISP is blocking it or your router/server is misconfigured.

---

### Post by adramalech on 2009-09-13
what was really dumb is that i can see port 8080 okay....what i think is all official ports have been blocked from my isp....

as in 20-22 and 80....i just did canuseeme and port 8080 was good but port 20-22 was timed out and port 80 same thing....

so i am just going to use port 2121 for ftp, port 2222 for ssh, and 8080 for http!!!

ohh yeah i don't use samba how would i totally remove/purge it from my server....less services running the better....

another question i have is i am upgrading my computer from my old x2 6400+ BE to a new i7 860 lga 1156 socket mobo and dual channel ddr3 memory and i was wondering if i should totally erase my hdd and then reload everything with the new system???? because of the drivers and what not....

---

### Post by adramalech on 2009-09-13
well port 2222 works for ssh and for sftp...also port 8080 works for apache2 but i am having problems with apache2....saying something wrong with my dns...but i look at nameserver at is is the ip of my router.....under resolv.conf


```

adramalech@jauntylamp$ sudo /etc/init.d/apache2 restart

[Sun Sep 13 17:53:40 2009] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.80.128 (check DNS) -- or specify an explicit ServerName
 ... waiting [Sun Sep 13 17:53:41 2009] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.80.128 (check DNS) -- or specify an explicit ServerName


```

also my resolv.conf is default.... 

i also changed all the ports to 8080 in the config file of apache2 also i did go through apache2 and write in ServerName zensoft.dnsdojo.net and ServerName localhost and both times came up with the error....

i am going to added in ServerAlias *.zensoft.dnsdojo.net
to the virtual host config files

also 2121 isn't working....i put vsftpd to port 2121 and it was still being blocked for the timing being 2222 should work....

---

### Post by cariboo on 2009-09-13
> another question i have is i am upgrading my computer from my old x2 6400+ BE to a new i7 860 lga 1156 socket mobo and dual channel ddr3 memory and i was wondering if i should totally erase my hdd and then reload everything with the new system???? because of the drivers and what not....

What are going to be running on your server that needs that much horsepower? Unless your going to be running vm's, it is a waste of hardware. :)

You can just put your harddrive in the system without having to do anything. All your hardware should be detected properly.

---

### Post by adramalech on 2009-09-14
okay thanks....

i am only temp. using my new intel build for my server till i can get another hard drive /media drive and a new mobo and case to put my old setup into it to make it into my linux server / firewall box.....

now my other question is since i really am trying to tighten down on security i have installed some chkrootkit stuff to scan my server and then send me an email with the results i also have my log files being sent to my email address with any changes....

i also have my ssh pretty secure and my sftp won't allow anybody but me on...the only thing i haven't done with ssh is to have rsa key assignment to users...and to have apache2 use ssl....

i also am going to start building up my ufw arguments as soon as i can figure out how to tighten my rules...

any good suggestions on how to monitor my daemons (ie. sshd.etc...) would be nice.....

---

### Post by windependence on 2009-09-14
> **adramalech said:**
> well port 2222 works for ssh and for sftp...also port 8080 works for apache2 but i am having problems with apache2....saying something wrong with my dns...but i look at nameserver at is is the ip of my router.....under resolv.conf


```

adramalech@jauntylamp$ sudo /etc/init.d/apache2 restart

[Sun Sep 13 17:53:40 2009] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.80.128 (check DNS) -- or specify an explicit ServerName
 ... waiting [Sun Sep 13 17:53:41 2009] [error] (EAI 2)Name or service not known: Failed to resolve server name for 192.168.80.128 (check DNS) -- or specify an explicit ServerName


```also my resolv.conf is default.... 

i also changed all the ports to 8080 in the config file of apache2 also i did go through apache2 and write in ServerName zensoft.dnsdojo.net and ServerName localhost and both times came up with the error....

i am going to added in ServerAlias *.zensoft.dnsdojo.net
to the virtual host config files

also 2121 isn't working....i put vsftpd to port 2121 and it was still being blocked for the timing being 2222 should work....

You need a ServerName directive somewhere in your main config file. Should be like this:

```
ServerName www.example.com

```

Or you could use the IP address:

```
ServerName  192.168.80.128
```

Just one word of advice. I know you're excited and everything but you should wait to lock down your server until you have everything working properly, otherwise, you may cause your own problems. Also, do ONE thing at a time and test. If all is OK do another thing and test, and so on. If you do 5 things and something gets messed up, you have no idea what your problem is.

-Tim

---

### Post by adramalech on 2009-09-14
okay so i am at school and i went to login again to ssh and walla nothin...and i even tested the port 8080, 2121, and 2222....and canyouseeme worked showing that they where successfully open....

i don't have much security on the ssh server besides no anon login and no root login.... 

i just don't understand....it seems my isp is dooming me to not be able to do anything!!!!

any suggestions.....i don't know what to do anymore... i can be home and on local and totally get in on ssh from my laptop...i then go anywhere outside of local and cannot get into the server!!!  even though port forwarding...on both ufw and router are correctly open for the three services i require....

---

### Post by cariboo on 2009-09-14
Are you using your external ip address when trying to log in via ssh?

---

### Post by Rob_H on 2009-09-14
> **adramalech said:**
> and canyouseeme worked showing that they where successfully open....

So if the ports are open, what error are you getting when you try to connect?

---

### Post by adramalech on 2009-09-14
my bad dumb dd-client was updating ddns wrong so it was pointing to my damn local ip of my server 192.168.80.128 and not my wan ip so i logged into my dyndns account and switched it to wan and then restarted my server and it worked...and no more apache problem....i can log into ssh and sftp....my problem right now is my mysqld fails to restart......

do i need ot have dbserver be setup for my hostname correct??? 

i am using default port for dbserver which i think is 3306 or 3307....

i just probably need to figure out how to configure dbconfig-common stuff.... 

also shouldn't there be a verbose output avaiable to tell me what is wrong with mysqld???

---

### Post by adramalech on 2009-09-16
ookay i don't know wtf is up with my isp i just reinstalled my entire distro and redid all the configuration files and made sure the ddns was working correctly and all the ports are blocked even the new ones....

what should i do just change the ports again????

i should probably ask my isp what are they blocking...

---

