---
title: "Security issue SMTP and TCP ports"
date: 2009-07-10
forum: Security
---

### Post by Sleipnirnkn on 2009-07-10
Hi everyone;
I'm using Ubuntu Jaunty about a few months ago but my experience with linux is recent.

Doing a general checks of my ubuntu, in this case, for open ports and others i found this:

cmd: netstat -at

tcp        0      0 vortex:smtp             *:*                     ESCUCHAR   
tcp6       0      0 [::]:netbios-ssn        [::]:*                  ESCUCHAR   
tcp6       0      0 [::]:microsoft-ds       [::]:*                  ESCUCHAR

The open ports are: 25, 139 y 445.

if i not wrong the ports 139 and 445 are from Samba, to share resources with Windows.
i tried to conect to the 25 and i found ESMTP running on this port. I don't use any email client, and don't find any SMTP app running at this time.
Also, run nmap, from other pc of the LAN with backtrack and says:

cmd: nmap -vv {ubuntu-laptop}

139/tcp open  netbios-ssn
445/tcp open  microsoft-ds
513/tcp open  login
514/tcp open  shell
 
Can someone explainme why this is possible ?
i search for close this port or close the process whos trigger that.
 
also try to google all mighty reponse me that, but nothing is exactly like this issue.

other test that made:

cmd: netstat -atop
Conexiones activas de Internet (servidores y establecidos)
Protocolo Recv-Q Send-Q Dirección Local Dirección Externa Estado       PID/Program name Temporizador
tcp        0      0 vortex:smtp             *:*                     ESCUCHAR    2999/exim4       apagado (0.00/0/0)
tcp6       0      0 [::]:netbios-ssn        [::]:*                  ESCUCHAR    3036/smbd        apagado (0.00/0/0)
tcp6       0      0 [::]:microsoft-ds       [::]:*                  ESCUCHAR    3036/smbd        apagado (0.00/0/0)


Seems that exim4 is my karma.

i am clear ?

** Can i close exim4 and delete it from the start without interfiering with the normal use of ubuntu?
** this 139 & 445 TCP ports represents a vulnerability to exploit from others ? and if the prev answer if yes, this cause what on ubuntu ?

i hope to someone help me out with this, beacuse this issue brings me lots of frustrations :P


PD: Sorry for my bad english.

---

### Post by Irihapeti on 2009-07-11
exim4 is a dependency of a number of other programs. Therefore, if you try to remove it, it will want to uninstall these programs.

To close port 25, you can select System -> Administration -> Services and unlock (you'll be asked for your password). Then scroll down to "Mail agent (exim4)" and click on the box to unselect it.

I did this several months ago on one of my computers and everything has run fine since then.

---

### Post by Sleipnirnkn on 2009-07-11
Thanks for the tip really, but already check the 'services' and i don't find any item with or related to exim4. 

A few minutes ago, after read and read and read, finally i find a solution.

y try with BUM (BootUp-Manager)
```
sudo apt-get install bum
```

and here is!, exim4 . i uncheck the running script, and now finally close the port. but ..
 
The weird thing was why exim4 is in BootUp but no in services ?
now, exim4 is deactivated, this process is need for other apps or a critical process ?
i don't want to screw my S.O., too much work on it. xD


and Irihapeti thanks again for tip. :D

---

### Post by Irihapeti on 2009-07-11
I'm running Hardy and you're running Jaunty. There might be some differences between the two in how they manage services.

I think that exim4 is installed with some programs so that it can send email messages to an admin if something needs his/her attention. That would be very useful if you are running a server many miles away, but isn't really needed for computers at home. So I don't see anything harmful happening because the program isn't activated.

If anyone has a different idea on this, please speak up.

---

### Post by MonkeyMayhem on 2009-07-11
exim4 -> used by a couple of programs, but rkhunter is something i know specifically

avahi-daemon uses smtp (i think), you can stop it by stopping services.

---

