---
title: "mirror server rsync issues"
date: 2008-07-21
forum: Server Platforms
---

### Post by cyclefiend2000 on 2008-07-21
we have a server and a backup. i am trying to set them up so that they will automatically rsync at various intervals. i searched the forums and found this solution (post #4)...
[http://ubuntuforums.org/showthread.php?t=253511](http://ubuntuforums.org/showthread.php?t=253511)

which more or less works. however, when i run the rsync from the command line, i have to type the password for the root user each time. how can i avoid that? or is there a better solution than the one i have already found?

i am using ubuntu 7.10 server distro.

thanks.
bradley

---

### Post by Titan8990 on 2008-07-21
Create a cron job as root. Then that cron job will execute with root privileges not asking for your password.

If you are referring to scp password for SSH then you need do something with exchanging keys. I was looking for the tutorial that I originally read and based my server back up system on but with no luck

---

### Post by windependence on 2008-07-22
[http://ubuntuforums.org/showthread.php?t=776585&highlight=Backups+rsync](http://ubuntuforums.org/showthread.php?t=776585&highlight=Backups+rsync)

[http://linuxgazette.net/104/odonovan.html](http://linuxgazette.net/104/odonovan.html)

[http://troy.jdmz.net/rsync/index.html](http://troy.jdmz.net/rsync/index.html)

Read these tutorials and then create a cron job as Titan8990 has mentioned, but make sure you use root's crontab.

-Tim

---

### Post by hyper_ch on 2008-07-22
here you have key authentication: [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

---

### Post by cyclefiend2000 on 2008-07-22
> **hyper_ch said:**
> here you have key authentication: [http://www.howtoforge.com/mirroring_with_rsync](http://www.howtoforge.com/mirroring_with_rsync)

i have been trying to get the authentication key set up. i followed the above tutorial, but i have one problem.

"It is important that you use a FQDN like mirror.example.com instead of an IP address after from=, otherwise the automated mirroring will not work!"

i can access my mirror via the ip address, but not using the hostname. i have checked the hostname on the mirror using:

```
hostname
```
and 
```
hostname --fqd
```

i get what i expect, but for some reason i can only access this computer from the other computers in the network using the ip address.

---

### Post by Titan8990 on 2008-07-22
Did you define it in your /etc/hosts list?

---

### Post by hyper_ch on 2008-07-22
why is it important to use a fqdn?

I'm not quite getting this "only access this computer from that one". Can you elaborate?

---

### Post by cyclefiend2000 on 2008-07-22
> **Titan8990 said:**
> Did you define it in your /etc/hosts list?
yes

---

### Post by windependence on 2008-07-22
> **cyclefiend2000 said:**
> yes

You gotta edit hosts on EACH machine on the network.

-Tim

---

### Post by cyclefiend2000 on 2008-07-22
> **hyper_ch said:**
> why is it important to use a fqdn?

I'm not quite getting this "only access this computer from that one". Can you elaborate?

i dont know why it is important to use a fqdn. that is just what it says in the tutorial. when i use the ip address, i still have to type in the password. not sure why there is a difference?

i will try to elaborate... i have two servers. the main one is named tux and has an ip address of 192.168.1.1. the backup is named putt and has an ip addresss of 192.168.1.18. 

from any windows machine on the network, i can type in "\\tux" in the address bar of windows explorer and access the main server. however, if i type in "\\putt" i get an error message, but if i use the ip address i get access to putt with no issues. 

same deal with accessing putt from tux. i have to use the ip address. i am not sure why i am not able to access putt by just using its name instead of the ip address?

---

### Post by hyper_ch on 2008-07-22
in what tutorial does it say to use the fqdn?

---

### Post by windependence on 2008-07-22
> **hyper_ch said:**
> in what tutorial does it say to use the fqdn?

Well I thought that strange myself but if he wants to access all the machines by name he is gonna have to get DNS straight anyway, no?

-Tim

---

### Post by hyper_ch on 2008-07-22
well, I normally reference my machines by IP ;)

---

### Post by cyclefiend2000 on 2008-07-22
> **hyper_ch said:**
> in what tutorial does it say to use the fqdn?

[http://www.howtoforge.com/mirroring_with_rsync_p2](http://www.howtoforge.com/mirroring_with_rsync_p2)

---

### Post by cyclefiend2000 on 2008-07-22
> **windependence said:**
> You gotta edit hosts on EACH machine on the network.

-Tim

can you explain a little bit more? i dont think i am getting exactly what you are saying.

---

### Post by windependence on 2008-07-22
If you have 5 machines on your network, and let's say 2 are linux and three are Windows and you want to be able to access them all by name instead of IP, you must make an entry in the hosts file of every computer on the network.

Now for what you are doing, you will just need an entry in the main server and the mirror server's hosts file so they can know each other by name. You will want to restart the network after yo do this also.

-Tim

---

### Post by cyclefiend2000 on 2008-07-22
i thought that was what you meant, i just wanted to make sure.

will have to wait to restart until everyone goes home for the day.

edit: of course that really doesnt explain the issue i am having from the windows machines on the network. why can i access tux by typing its name, but not the same for putt?

edit2: ok i added the line for tux to the hosts file on putt. i restarted the putt server, and now i can't access it using putty. i get "Disconnected: No supported authentication methods available". i can still access putt using its ip address through windows explorer. not sure why this affected putty access? but i am afraid to change the hosts file on the main server until i find out why.

edit3: i took out the line i added to the hosts file on putt and restarted it again. still having putty issues from my windows computer. not sure why it started all of a sudden. was working fine earlier.

---

### Post by windependence on 2008-07-22
Do you have an entry in that machine's hosts file for putt?

-Tim

---

### Post by cyclefiend2000 on 2008-07-22
> **windependence said:**
> Do you have an entry in that machine's hosts file for putt?

-Tim

on my windows machine?

---

### Post by Titan8990 on 2008-07-22
Post the contents of you /etc/hosts list.

> will have to wait to restart until everyone goes home for the day.

A networking restart my production server takes less than 5 seconds. Depending on your environment there is a good chance you can get away with during a usual day.

And yes, you will need edit your hosts file on your Windows machine as well.

---

### Post by cyclefiend2000 on 2008-07-22
```
127.0.0.1       localhost
192.168.1.1     tux.triad-office.com tux
192.168.1.18	putt.triad-office.com putt

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by cyclefiend2000 on 2008-07-22
> **Titan8990 said:**
> And yes, you will need edit your hosts file on your Windows machine as well.

i looked at the hosts file on my windows machine. there arent any entries for either server, but i have no problems accessing the main server, tux.

here is the contents of my windows machine's host file...

```
# Copyright (c) 1993-1999 Microsoft Corp.
#
# This is a sample HOSTS file used by Microsoft TCP/IP for Windows.
#
# This file contains the mappings of IP addresses to host names. Each
# entry should be kept on an individual line. The IP address should
# be placed in the first column followed by the corresponding host name.
# The IP address and the host name should be separated by at least one
# space.
#
# Additionally, comments (such as these) may be inserted on individual
# lines or following the machine name denoted by a '#' symbol.
#
# For example:
#
#      102.54.94.97     rhino.acme.com          # source server
#       38.25.63.10     x.acme.com              # x client host

127.0.0.1       localhost
```

---

### Post by Titan8990 on 2008-07-22
Why did you remove the 127.0.1.1 line that contains your hostname? This machine is tux correct?

---

### Post by windependence on 2008-07-22
You should put an entry for both servers in your Windoze hosts file.

-Tim

---

### Post by cyclefiend2000 on 2008-07-22
> **Titan8990 said:**
> Why did you remove the 127.0.1.1 line that contains your hostname? This machine is tux correct?

i didnt.

yes this host file is from the tux machine.

edit: ok i got putty to work with the back up server again. it was a config file that i had edited yesterday that was causing the issue.

edit2: ok, i added putt and tux to my hosts file on my windows machine, and i can now access putt (on my windows machine) by name .

---

### Post by hyper_ch on 2008-07-22
you can skip page 2 more or less from that howto :) the important part is how to generate the keys and exchange them ;)

---

