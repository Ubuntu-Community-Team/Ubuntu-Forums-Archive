---
title: "backup server howto..."
date: 2009-05-16
forum: Server Platforms
---

### Post by zander1013 on 2009-05-16
hi,

i am trying to setup a backup server. i am using debian for my web server and ubuntu for the backup server.

i am trying to set up a backup server for my wlan using this article

[http://www.linuxjournal.com/article/8590](http://www.linuxjournal.com/article/8590)

as the guide. i am to the point "Software Configuration—rsync and SSH" in that article.

i am having troubble with this command...

rsync -az /home -e ssh bob@bar:/data1/foo

...as an example where foo is the backup client (the machine i want to backup) and bar is the backup server.

i have entered...

af@bubba:~$ rsync -az /home -e ssh af@astonmartin:/Hercules/bubba

where bubba(debian, etch server) is the backup client, astonmartin(ubuntu, 9.04 desktop) is the backup server and /Hercules is the mount point for the partition on an external disk on astonmartin.

this is the result...

af@bubba:~$ rsync -az /home -e ssh af@astonmartin:/Herculese/bubba
ssh: astonmartin: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(453) [sender=2.6.9]
af@bubba:~$

...if i simply try to ssh from bubba to astonmartin i get this this result...

af@bubba:~$ ssh astonmartin
ssh: astonmartin: Name or service not known
af@bubba:~$

i can ssh from astonmartin to bubba but not bubba to astonmartin.

perhaps i have to enable inbound ssh to astonmartin?

please advise.

-zander

---

### Post by ktrnka on 2009-05-17
It appears that it can't resolve astonmartin. Try using astonmartin's ip address. If that works, then all you need to do is add astonmartin's name and ip in /etc/hosts on bubba

---

### Post by zander1013 on 2009-05-17
> **ktrnka said:**
> It appears that it can't resolve astonmartin. Try using astonmartin's ip address. If that works, then all you need to do is add astonmartin's name and ip in /etc/hosts on bubba

hi,

i have not assigned an ip address to astonmartin.

i have a fixed ip address for my web server which is also my router and firewall (all in one). there is a picture of the web server/router/firewall at [http://alonzofretwell.com](http://alonzofretwell.com).

as far as i know the server/router/firewall (bubba) is assigning the ip addresses dynamically to the clients that join my wep wlan. the lynksys wireless blue box is operating in a "bridge" mode (to the best of my knowledge).


perhaps this is the cause of the issue?

so i joined my wlan with astonmartin as a regular client like my other laptop computers with ubuntu desktop. i just enter the wep key and it joins the wlan.

perhaps all i need to do is add astonmartin's name to /etc/hosts on bubba as you recommend?

please advise.

thank you for your help.:D

-alonzo

---

### Post by 3L33T on 2009-05-17
> **zander1013 said:**
> hi,
i can ssh from astonmartin to bubba but not bubba to astonmartin.

perhaps i have to enable inbound ssh to astonmartin?

please advise.

-zander


YES, that would be a good idea.  Check if 'ssh' server is enabled and running on astonmartin server.  Also, add the static ip address of astonmartin in your 'etc/hosts' file.  BTW, do you work for astonmartin?:D:D If this works, I'd love to get an astonmartin logo sticker to stick on my HP Mini running Jaunty :p ... please.

---

### Post by zander1013 on 2009-05-18
> **3L33T said:**
> YES, that would be a good idea.  Check if 'ssh' server is enabled and running on astonmartin server.  Also, add the static ip address of astonmartin in your 'etc/hosts' file.  BTW, do you work for astonmartin?:D:D If this works, I'd love to get an astonmartin logo sticker to stick on my HP Mini running Jaunty :p ... please.

hi,

i do not work for astonmartin. sorry to disapoint you.;)

you can pro'lly get one if you ask them though.

astonmartin does not have a static ip. only bubba does. bubba issues them dynamically to the clients on the wlan (like astonmartin).

i am pretty sure that i must add something to the /etc/hosts file on bubba. but i am not sure what other than "astonmartin".

i was doing some work with hadoop clusters and that required the /etc/hosts file to be setup so that the nodes could communicate via ssh.

perhaps i can find those notes.

thank you,

-zander

---

### Post by windependence on 2009-05-18
You have a BS in Computer Science?

Your problem is with DNS. Each machine does not know the hostname of the other machine because computers only know IP addresses and not names. You need to enter a line in your /etc/hosts file like this:

```
192.168.0.2   astinmartin.yourdomain.tld  astinmartin
```

where 192.168.0.2 is the IP address of astinmartin. This goes in the /etc/hosts of BUBBA, not astinmartin and vice versa. So you will have one entry on each machine describing where to find the other machine. You may want to go into your router and change from DHCP to static for your LAN, or assign each server or client a reserved dhcp address so they will always remain constant.

-Tim

---

### Post by zander1013 on 2009-05-22
> **windependence said:**
> You have a BS in Computer Science?

Your problem is with DNS. Each machine does not know the hostname of the other machine because computers only know IP addresses and not names. You need to enter a line in your /etc/hosts file like this:

```
192.168.0.2   astinmartin.yourdomain.tld  astinmartin
```

where 192.168.0.2 is the IP address of astinmartin. This goes in the /etc/hosts of BUBBA, not astinmartin and vice versa. So you will have one entry on each machine describing where to find the other machine. You may want to go into your router and change from DHCP to static for your LAN, or assign each server or client a reserved dhcp address so they will always remain constant.

-Tim


yes tim i earned a BS in computer science from the howard hughes college of engineering at unlv in 1997.

i am confident that you have given the solution i need but i have not tried to implement it yet.

i agree with your assessment that the issue is with dns.

adding...

```
192.168.0.2   astinmartin.yourdomain.tld  astinmartin
```

to bubba's /etc/hosts is pretty straight forward.

changing from dhcp to static throughout the wlan is somewhat intimidating for me. i have only recently begun to run this type of network and subsequently do not have allot of experience changing that kind of stuff.

i am pretty sure that i change the dhcp to static on bubba.alonzofretwell.com (bubba is router, firewall, web server) and then just assign the addresses to the clients that will be using bubba.alonzofretwell.com wlan.

so after that i will have to go to every machine and switch it to static and assign it an address in the range of bubba.alonzofretwell.com.

can you point me to a tutorial for this or perhaps recommend a keyword to use in a search?

thank you,

-zander (alonzo) :)

---

### Post by koenn on 2009-05-23
manual, static conf :
[http://ubuntuforums.org/showpost.php?p=69643&postcount=9](http://ubuntuforums.org/showpost.php?p=69643&postcount=9)

the alternative is to make a dhcp reservation for astonmartin (on your dhcp server - bubba ?) so it always gives astonmartin the same address

you'll need to restart networking (or reboot) for changes to take effect. Check this with ifconfig, and update the relevant hosts files with the correct address of astonmartin.

This shouldn't affect your dhcp any further so other clients can remain on dhcp.

---

