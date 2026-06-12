---
title: "help me, can only connect to mysql through localhost"
date: 2005-07-11
forum: Server Platforms
---

### Post by nephish on 2005-07-11
hey there,
i have a server at work, just put ubuntu linux on it (what i use at home)
and did the whole mysql - apache perl - php thing. whew.
the problem is 
under mysql-admin, i can only connect through localhost.
the ip address on the LAN is 10.10.10.10 but if i put that in the host block it tells me that it cannot connect. same if i put in the host name of the system.
this is a problem because the reason i am trying to get this going is because we have a windows xp computer with an access database. i am trying to use the odbc module from mysql.com and it will not connect
how the &*#$ do i configure mysql to let some other computer on the lan talk to it via network ?
any ideas?
thanks

---

### Post by Ride Jib on 2005-07-12
I know you said you can connect via localhost, but how about localhost ip address (127.0.0.1)? Are your firewall's settings blocking the connection on the mysql port?

---

### Post by nephish on 2005-07-12
[QUOTE=Ride Jib]I know you said you can connect via localhost, but how about localhost ip address (127.0.0.1)? Are your firewall's settings blocking the connection on the mysql port?[/QUOTE]
 i am trying to remember about the 127.0.0.1 i will try tomorrow.
no, i do not have a firewall installed on it yet ( LAN sits behind a large firewall - router) so i had'nt thought it was that important. yet..
let you know what i find out. um.. you should be able to connect to mysql from another computer right ? starting to wonder here

---

### Post by deuce868 on 2005-07-12
search is your friend :-)

[http://www.ubuntuforums.org/showthread.php?t=44919](http://www.ubuntuforums.org/showthread.php?t=44919)

---

### Post by nephish on 2005-07-12
ok, i cannot connect thru 127.0.0.1
only exactly "localhost"
i do not know where the option is to turn this thing on to the net or even accept another host name.

thanks.

---

### Post by jeroevi on 2005-07-12
[QUOTE=nephish]ok, i cannot connect thru 127.0.0.1
only exactly "localhost"
i do not know where the option is to turn this thing on to the net or even accept another host name.

thanks.[/QUOTE]

Try installing mysql-admin on the mysql machine. Once installed go to the GUI and go to user management.
If mysql is on a server: telnet or ssh to the mysql machine. Start the mysql console and add userrights for your user with something like:
*grant all on mytables to myuser@somehost*
See the mysql guide on the net for the correct sql syntax.

regards,
Jeroen

---

### Post by LordHunter317 on 2005-07-12
Ubuntu's default mysql doesn't listen on any address but localhost by default.  You have to edit /etc/mysql/my.cnf and remove the 'bind-address' directive.

Then you have to get user rights setup correctly as well.

---

### Post by nephish on 2005-07-12
victory at last 
edited the my.cnf file in /etc/mysql/

commented out the lines

skip-host-cache
and
skip-external-locking.

now i can log on as (my ip address) and the other machines on the lan can too.
thanks for that search link.

bout got all this whupped !

thanks again.

---

### Post by crazdmnd on 2006-01-16
nice somebody figured it out...too bad it (along with everything else i've been trying for the past 5 hours) didnt solve the problem for me.

i want to build a myth box and end up spending more time on this pita issue.

anyways--

can't connect to mysql (or webmin and other services) from internal lan.

removed bind-address field in my.cnf, no beans.  changed it to lan ip, no dice.

removed ipv6 after some advice read on the threads.  flushed the iptables...

i installed firestarter and it doesnt seem to make a difference on this particular issue, although its input is shown in my iptables output.

have a linksys router, made sure the ubuntu box is in the dmz.   firewall is disabled on the win xp box I'm trying to connect with.

added the lan ip i want to connect to the ubuntu box in the hosts.allow box...

am i missing something here?? is there someplace I am not looking to simply allow my damn box to grant mysql access and I can move on to the more important work of working on my mythtv setup?? i got diverted onto this CF because I wanted to test my myth setup with winmyth.

Thanks in advance!:mad:

---

### Post by LordHunter317 on 2006-01-16
[QUOTE=nephish]victory at last 
edited the my.cnf file in /etc/mysql/

commented out the lines

skip-host-cache
and
skip-external-locking.

now i can log on as (my ip address) and the other machines on the lan can too.
thanks for that search link.

bout got all this whupped !

thanks again.[/QUOTE]There's no way on earth commenting out those lines fixed your problem.

---

### Post by crazdmnd on 2006-01-16
i tried it too and it did nada for me.

i spent another 3 hours with it today trying just about every combo---even removed mysql and installed a new version, still no beans.

downloading the FC4 DVD ISO just in case...i really like what i've seen with breezy so far but i'm at my wits end with this issue.

i hate to do a full reinstall of another distro (or ubuntu for that matter).

---

### Post by crazdmnd on 2006-01-16
gladly, i figured my problem out...after all of this, i must have corrected the host access issue but not realized it and it ended up being a password issue for me....i took away the particular user password and all seems ok.

does the password sent via the remote client (in this case a winmyth setup using the dsmyth filters and myql dll stuff) have to have the encrypted password programmed into the login chat?

thanks guys!

brian

---

