---
title: "make program start at boot"
date: 2006-08-29
forum: Server Platforms
---

### Post by sd37167 on 2006-08-29
Hi:
I am setting up DansGuardian on this server along with Squid and Iptables. The last thing I need to do is to make sure that iptables, squid, and dansguardian start on boot. The instructions say to use the chkconfig command, but there is no such command in Ubuntu. So what should I do to make these programs start at boot? Thanks.
Stephen

---

### Post by dazedandconfused on 2006-08-29
Hiya,

If you installed them using apt/synaptic they'll probably start at boot anyway. You can check by running

ls -la /etc/rc3,d (rc5.d if you have a GUI running) and you should see a list of service names like this:

S90shorewall@  S12syslog@   S20laptop-mode@  S56rawdevices@      S95kheader@
S03iptables@   S13partmon@  S20xfs@          S56xinetd@          S99local@
S04acpi@       S14acpid@    S25netfs@        S75keytable@
S04pcmcia@     S15cups@     S30dm@           S80freshclam@
S10network@    S17alsa@     S55sshd@         S85vpnclient_init@
S11portmap@    S18sound@    S56ntpd@         S90crond@

Anything starting with K is disabled and anything starting with S will run at bootup.

Incidentely, if you compiled dansguardian from source you can run it from /etc/rc.local by adding 

dansguardian -Q 

to the end of the file. The -Q will kill of any existing processes or traces of and as rc.local is the script that runs last of all during the boot sequence Squid will already have started.

Hope this helps,

Cheers,

Jools

BTW the number at the beginning of the service name in rc3.d determines the order in which services start. The lower the number, the earlier it starts.

---

### Post by sd37167 on 2006-08-29
Hi:
thanks for the help. When I run the command, none of the programs appear becuase I had to compile both squid and dnasguardian. My question, is iptables running? I don't see it on the list. Now, can I add both squid and dansguardian to the list by adding squid before dans both followed by -Q 
Thanks

---

### Post by dazedandconfused on 2006-08-30
Hiya,

Try (in a terminal):

sudo ps -A | grep iptables

If you get a reply something like:

4902 ?        00:00:00 iptables

it's running. The process id no. (4902 in this case) may be different but if you get nothing mentioning iptables it's not running.

---

