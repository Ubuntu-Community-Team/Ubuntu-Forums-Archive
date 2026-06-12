---
title: "HOWTO: Use iptables as firewall with a daemon on system startup"
date: 2005-08-15
forum: Tutorials
---

### Post by Sam on 2005-08-15
This howto is intended to set up a firewall without installing firestarter (useful if you don't use any wm, eg: servers). It uses iptables which is available with a fresh Ubuntu install, and a init.d script to run it as a daemon on boot.

Please correct me if I'm wrong about iptables configuration, and feel free to improve the script or tell me new ports to include in the script. Thanks !

[size=3]**Create the default rules script**[/size]
[list][*]Create a new script:
```
$ sudo gedit /usr/local/bin/iptables-rules
```

[*]Paste the following lines:
```
#! /bin/sh

#
# Initialize the rules with iptables.
#

ROOT_UID="0"

#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
	echo -e "\nAborted by user."
	rm -rf $TMP_DIR
	exit 2
}

#Check if run as root
if [ "$UID" -ne "$ROOT_UID" ] ; then
	echo "You must be root to do that!"
	exit 1
fi


echo "Which ports do you want to open ?"


allow_icmp="0"
echo -n "Allow ping (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_icmp="1"
fi

allow_ftp="0"
echo -n "Allow ftp (file transfert) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_ftp="1"
fi

allow_ssh="0"
echo -n "Allow ssh (secure shell) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_ssh="1"
fi

allow_smtp="0"
echo -n "Allow smtp (mail sending) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_smtp="1"
fi

allow_http="0"
echo -n "Allow http (web server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_http="1"
fi

allow_pop3="0"
echo -n "Allow pop3 (pop3 mail server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_pop3="1"
fi

allow_imap="0"
echo -n "Allow imap (imap mail server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_imap="1"
fi

allow_https="0"
echo -n "Allow https (secured web server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_https="1"
fi

allow_mysql="0"
echo -n "Allow mysql (database server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_mysql="1"
fi

allow_vnc="0"
echo -n "Allow vnc (remote desktop) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_vnc="1"
fi

allow_samba="0"
echo -n "Allow samba (Windows file sharing) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_samba="1"
fi


echo -e "\nDo you really want to apply iptables rules ? This will clear every iptables"
echo "settings. Use Ctrl-C then 'iptables-save' to save your current settings."
echo -n "(y/n)? [n] "
read input
if [ -z "$input" ] || [ "$input" == "n" ] || [ "$input" == "no" ] || [ "$input" == "N" ] || [ "$input" == "NO" ] ; then
	exit 1
fi


echo -n "Applying rules..."


#Flushing the current rules
iptables -F


#Allow connections already established
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#Accept everything from localhost
iptables -A INPUT -i lo -j ACCEPT


#Ping
if [ $allow_icmp -eq "1" ] ; then
	iptables -A INPUT -p icmp -j ACCEPT
fi

#ftp (20,21)
if [ $allow_ftp -eq "1" ] ; then
	iptables -A INPUT -p tcp -m multiport --destination-ports ftp-data,ftp -j ACCEPT
fi

#ssh (22)
if [ $allow_ssh -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport ssh -j ACCEPT
fi

#smtp (25)
if [ $allow_smtp -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport smtp -j ACCEPT
fi

#http (80)
if [ $allow_http -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport http -j ACCEPT
fi

#pop3 (110)
if [ $allow_pop3 -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport pop3 -j ACCEPT
fi

#imap (143)
if [ $allow_imap -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport imap2 -j ACCEPT
fi

#https (443)
if [ $allow_https -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport https -j ACCEPT
fi

#mysql (3306)
if [ $allow_mysql -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport mysql -j ACCEPT
fi

#vnc (5900)
if [ $allow_vnc -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport 5900 -j ACCEPT
fi

#samba (tcp 135,139,445, udp 135,137,138,139,445)
if [ $allow_samba -eq "1" ] ; then
	iptables -A INPUT -p tcp -m multiport --destination-ports 135,139,445 -j ACCEPT
	iptables -A INPUT -p udp -m multiport --destination-ports 135,137,138,139,445 -j ACCEPT
fi


#Drop everything else
iptables -A INPUT -j DROP

#Outbound: allow everything
iptables -A OUTPUT -j ACCEPT

echo " ok !"

exit 0
```

[*]Allow execution:
```
$ sudo chmod +x /usr/local/bin/iptables-rules
```

[*]Run this script to apply iptables rules:
```
$ sudo iptables-rules
```[/list]

[size=3]**Create the firewall daemon**[/size]
Thank you pinnockio for your [iptables firewall script](http://ubuntuforums.org/showthread.php?t=19106) !

[list][*]Create a new script:
```
$ sudo gedit /etc/init.d/iptables
```

[*]Paste the following lines:
```
#! /bin/sh

#This is an Ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
#under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.

. /lib/lsb/init-functions


IPTABLES_SAVE="/etc/default/iptables-rules"
SAVE_RESTORE_OPTIONS="-c"


checkrules() {
	if [ ! -f ${IPTABLES_SAVE} ]
	then
		echo "Not starting iptables. First create some rules then run"
		echo "\"/etc/init.d/iptables save\""
		return 1
	fi
}

save() {
	/sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
	return $?
}

start(){
	checkrules || return 1
	/sbin/iptables-restore ${SAVE_RESTORE_OPTIONS} < ${IPTABLES_SAVE}
	return $?
}


case "$1" in
	save)
		echo -n "Saving iptables state..."
		save
		if [ $? -eq 0 ] ; then
			echo " ok"
		else
			echo " error !"
		fi
	;;

	start)
		log_begin_msg "Loading iptables state and starting firewall..."
		start
		log_end_msg $?
	;;
	stop)
		log_begin_msg "Stopping firewall..."
		for a in `cat /proc/net/ip_tables_names`; do
			/sbin/iptables -F -t $a
			/sbin/iptables -X -t $a

			if [ $a == nat ]; then
				/sbin/iptables -t nat -P PREROUTING ACCEPT
				/sbin/iptables -t nat -P POSTROUTING ACCEPT
				/sbin/iptables -t nat -P OUTPUT ACCEPT
			elif [ $a == mangle ]; then
				/sbin/iptables -t mangle -P PREROUTING ACCEPT
				/sbin/iptables -t mangle -P INPUT ACCEPT
				/sbin/iptables -t mangle -P FORWARD ACCEPT
				/sbin/iptables -t mangle -P OUTPUT ACCEPT
				/sbin/iptables -t mangle -P POSTROUTING ACCEPT
			elif [ $a == filter ]; then
				/sbin/iptables -t filter -P INPUT ACCEPT
				/sbin/iptables -t filter -P FORWARD ACCEPT
				/sbin/iptables -t filter -P OUTPUT ACCEPT
			fi
		done
		log_end_msg 0
	;;

	restart)
		log_begin_msg "Restarting firewall..."
		for a in `cat /proc/net/ip_tables_names`; do
			/sbin/iptables -F -t $a
			/sbin/iptables -X -t $a
		done;
		start
		log_end_msg $?
	;;

	*)
		echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
		exit 1
    	;;
esac

exit 0
```

[*]Allow execution:
```
$ sudo chmod +x /etc/init.d/iptables
```

[*]Add daemon to runlevels to run it before network is started (on boot) and kill it after network is stopped (on halt/reboot):
```
$ sudo update-rc.d iptables start 37 S . start 37 0 . start 37 6 .
```[/list]

[size=3]**Starting the firewall daemon**[/size]
[list][*]Make sure that you set up iptables as explained above:
```
$ sudo iptables-rules
```

[*]Save iptables configuration for the daemon:
```
$ sudo /etc/init.d/iptables save
```

[*]Start the daemon:
```
$ sudo /etc/init.d/iptables start
```

[*]Done ![/list]

---

### Post by Spudgun on 2005-08-15
Little correction, SSH is port 22, and not 23. Looks good apart from that though :)
What what I do to insert my own choice of port numbers to open?
Also, is it possible to have blocked connections logged, such as in Firestarter?

Thanks,
Spudgun

---

### Post by Nano on 2005-08-15
[QUOTE=Spudgun]Little correction, SSH is port 22, and not 23. Looks good apart from that though :)
What what I do to insert my own choice of port numbers to open?
Also, is it possible to have blocked connections logged, such as in Firestarter?

Thanks,
Spudgun[/QUOTE]
 Good view!

---

### Post by Sam on 2005-08-15
[QUOTE=Spudgun]Little correction, SSH is port 22, and not 23. Looks good apart from that though :)
What what I do to insert my own choice of port numbers to open?
Also, is it possible to have blocked connections logged, such as in Firestarter?

Thanks,
Spudgun[/QUOTE]
Thanks for your reply. I corrected the port number.
For insering your own ports, just edit the script (it should be enough self explaining). Or tell me what you want and I'll add to the script.
About logging, I'm not sure, I'm not an iptables expert. I'll check and post if I find something !

---

### Post by kf_man on 2005-08-21
Could this also be used for creating a router using Ubuntu?  Obviously some of the settings would need to be changed, but it seems logical anyway.  The Daemon script appears to be very generic and would save any iptables settings that you use.  I have been seriously contemplating a nice Ubuntu router since I would love things like DNS on the network.  The only thing that gets confusing the the iptables part of the configuration.  If I understand correctly, iptables commands have to be issued on every boot, correct?  Sorry if I am a little confusing, feel free to ask questions.

Thanks,

Kyle

---

### Post by Bill Statler on 2005-08-29
Thanks, Sam, this is exactly the information I needed! One question...

You have this command for starting the daemon:

```
$ sudo update-rc.d iptables start 37 S . start 37 0 . start 37 6 .
``` 

But pinnockio (in his original [post that you linked to](http://ubuntuforums.org/showthread.php?t=19106)) has this command instead:

```
sudo update-rc.d iptables start 37 S . stop 37 0 .
```

I've been using Linux for a *whole two days* so I am obvously a real expert on this -- but is one of these wrong, or are they equivalent?

Thanks.

---

### Post by Sam on 2005-08-29
[QUOTE=Bill Statler]Thanks, Sam, this is exactly the information I needed! One question...

You have this command for starting the daemon:

```
$ sudo update-rc.d iptables start 37 S . start 37 0 . start 37 6 .
``` 

But pinnockio (in his original [post that you linked to](http://ubuntuforums.org/showthread.php?t=19106)) has this command instead:

```
sudo update-rc.d iptables start 37 S . stop 37 0 .
```

I've been using Linux for a *whole two days* so I am obvously a real expert on this -- but is one of these wrong, or are they equivalent?

Thanks.[/QUOTE]
Both a different. pinnockio's way was wrong, because the firewall is stopped before the network daemons. I took some time to find out that in runlevel 0 and 6 (halt and reboot), services flagged as starting are stopped after those flagged as stopping (sounds weird...). So if you look at the order, the iptables daemon is stopped after other network daemons.

And I also added firewall's deactivation in case of a reboot ('start 37 6').

Hope you understand !

---

### Post by Bill Statler on 2005-08-30
Thanks for the explanation!

[QUOTE=Sam]... in runlevel 0 and 6 (halt and reboot), services flagged as starting are stopped after those flagged as stopping (sounds weird...)[/QUOTE]

I tried standing on my head to read that, and now it makes perfect sense. This really covers a lot of what I'm trying to do on my new PC -- now all I have to do is add IP masquerading to the stew so my wife's WinXP machine can share the Internet connection. Oh, and then I'll have to figure out Samba. No problem!

Thanks again!

---

### Post by LaSSarD on 2005-08-30
opening http, imap, smtp and pop3 is just for servers? i access sites and i receive/send a lot of mails, without being a server. if i block those ports, am i going to be able to do what I'm used to?

---

### Post by Sam on 2005-08-30
[QUOTE=LaSSarD]opening http, imap, smtp and pop3 is just for servers? i access sites and i receive/send a lot of mails, without being a server. if i block those ports, am i going to be able to do what I'm used to?[/QUOTE]
Yes! This firewall works only for incoming traffic. All your outgoing traffic is not blocked (you're supposed to know what you're doing). If you don't use any server services, just allow ping with the firewall setup.

You pointed out that it's not clearly explained with the firewall setup. I'll update this when I'll have some time.

---

### Post by chivchila on 2005-09-18
hello 

i have a little problem after installing and performing all the things published here for configuration of iptables. After that my server doesn't work anymore, nobody can connect to it. Just after I perform the command  $ sudo /etc/init.d/iptables stop my server works perfectly. I don't really understand what is tha problem with iptables and how can I solve it. maybe someone had simmilar problem and can tell what is wrong? thanks

---

### Post by Sam on 2005-09-22
[QUOTE=chivchila]hello 

i have a little problem after installing and performing all the things published here for configuration of iptables. After that my server doesn't work anymore, nobody can connect to it. Just after I perform the command  $ sudo /etc/init.d/iptables stop my server works perfectly. I don't really understand what is tha problem with iptables and how can I solve it. maybe someone had simmilar problem and can tell what is wrong? thanks[/QUOTE]
Which ports do you use ?

---

### Post by mulperi on 2005-09-23
Thanks for this tutorial, it gives a nice example of how to play with iptables. 

However, I think most Ubuntu users use a wm and firestarter is just a GUI to iptables. This would be a helpful comment before joe sixpack starts to mess up his network connections.

What I have been wondering is that how we could you get a system that pops-up outgoing connection attempts and offers to make a rule of it (i.e. similar to Zonealarm etc in windows)? Does this really require recompiling the kernel?

//mulperi

---

### Post by slapper on 2006-05-21
Hi!! 
because i am running my server without any security i am intend to use this script.But before that i want to ask you e few questions before apply it.

1.I have two network interfaces in my server.I supose that the script works fine with two ethernet cards?
2.I am running a proftpd server(standalone,anonymous) and ssh-server in other ports than the usuals.If i am guess right the only think i have to do is to change the ports number into the script.    e.g  21-->1500 and 22--> 1600

#ftp (20,21)
if [ $allow_ftp -eq "1" ] ; then
	iptables -A INPUT -p tcp -m multiport --destination-ports ftp-data,ftp -j ACCEPT
fi

#ssh (22)
if [ $allow_ssh -eq "1" ] ; then
	iptables -A INPUT -p tcp --dport ssh -j ACCEPT

 
Thanks!!!!!!!:-D :-D :-D

---

### Post by slapper on 2006-05-21
Everything works fine (apache2,ssh,mysql) exept my proftpd server in port 1980.
Any ideas??:-k :-k

---

### Post by Sam on 2006-05-22
Hello slapper

1) Don't know this one. If iptables manages all interfaces, the answer is yes.

2) Just change the port numbers or add a new service:

First part of the script:```
allow_proftpd="0"
echo -n "Allow proftpd (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
	allow_proftpd="1"
fi
```

Second part```
#proftpd (1500,1600)
if [ $allow_proftpd -eq "1" ] ; then
	iptables -A INPUT -p tcp -m multiport --destination-ports 1500,1600 -j ACCEPT
fi
```

---

### Post by lutzky on 2006-06-27
Excellent howto, much thanks!

I have a suggestion though: This is most common for headless servers, I'd imagine. There's always the danger of mistakenly locking oneself out (say, disabling SSH accidentally). Is there a way to make this similar to resolution-switching safety? That is, have it give you 15 seconds to click 'Yes I am sure' after the firewall has been activated, and if you don't respond, disable the firewall...

---

### Post by Sam on 2006-06-27
[QUOTE=lutzky]Excellent howto, much thanks!

I have a suggestion though: This is most common for headless servers, I'd imagine. There's always the danger of mistakenly locking oneself out (say, disabling SSH accidentally). Is there a way to make this similar to resolution-switching safety? That is, have it give you 15 seconds to click 'Yes I am sure' after the firewall has been activated, and if you don't respond, disable the firewall...[/QUOTE]
Yes you're right. But the script doesn't handle that feature, however some scripting is required to do that. However, you can use the 'at' command to do some actions at some time (like deactivating the firewall).

But notice that this script must be used by people knowing what they do.

---

### Post by docko on 2006-07-02
do you use this script only for servers?
i'm looking for something like this, i want to use it on my gateway box, but i'd need it not to block icq, jabber, etc...

---

### Post by Sam on 2006-07-03
[QUOTE=docko]do you use this script only for servers?
i'm looking for something like this, i want to use it on my gateway box, but i'd need it not to block icq, jabber, etc...[/QUOTE]
I don't know if it works for a gateway. The thing is to use iptables only for the incoming interface.

To add more services you can modify the script as described [here](http://ubuntuforums.org/showpost.php?p=1041702&postcount=16).

---

### Post by kevdog on 2007-08-24
I know this thread has been dead for a long time, however as a regular user I am unable to run:
/sbin/iptables-save


But as root I am.  As root I changed the privileges to 777, and still as a regular user I am unable to run this command.  Is this by design??

---

### Post by TheCelloFellow on 2007-09-04
The iptables system is an interface to the kernels built in firewall. Normally, normal users do not access the kernel. Therefore, you should not be able to do anything with iptables as normal user, but instead have to use sudo.

As it is, this thread describes how to get iptables working at boot time, which therefore should require minimal user interaction, and then using sudo, to set up. After that you just forget about it cause it just works.

CelloFellow

---

### Post by tbeehler on 2007-10-08
This worked perfectly.  Thank you!

---

### Post by brabo on 2007-10-24
Hi,

i am quite new to iptables and such,
but i have some recurring errors with this script.
after each option i get 4 errors like:
Allow ping (y/n)? [y] n
[: 32: ==: unexpected operator
[: 32: ==: unexpected operator
[: 32: ==: unexpected operator
[: 32: ==: unexpected operator
where 32 is always the line after "then" where the script sets its variable.
also, after the "yes" on applying changes, it gives again 4 times:
[: 100: ==: unexpected operator

what dumb thing am i doing?

grtz,
brabo.

---

### Post by Beacon11 on 2008-05-02
Sorry for posting on an old thread, but I found this using Google. I've never really messed with iptables, but it seemed relatively straightforward until I read that manually editing iptables could be devastating to NetworkManager (I'm using Kubuntu, so I guess KNetworkManager ;) ). For a reference, read
[https://help.ubuntu.com/community/IptablesHowTo#head-928fdd039d2c99bd1a98a40c3c5747fb6c581aee](https://help.ubuntu.com/community/IptablesHowTo#head-928fdd039d2c99bd1a98a40c3c5747fb6c581aee)

Can anyone confirm this? Does anyone know if it still causes problems in 8.04 (Hardy)?

EDIT: My network/interfaces is empty except for the loopback. I have eth0 (wired) and eth1 (wireless) as well, but entries for these interfaces are not present in network/interfaces. Does this mean that it's completely up to NetworkManager to take care of them?

---

### Post by johnmorkoss on 2011-12-10
> **Sam said:**
> This howto is intended to set up a firewall without installing firestarter (useful if you don't use any wm, eg: servers). It uses iptables which is available with a fresh Ubuntu install, and a init.d script to run it as a daemon on boot.

Please correct me if I'm wrong about iptables configuration, and feel free to improve the script or tell me new ports to include in the script. Thanks !

[SIZE=3]**Create the default rules script**[/SIZE]
[LIST]
[*]Create a new script:
```
$ sudo gedit /usr/local/bin/iptables-rules
```
[*]Paste the following lines:
```
#! /bin/sh

#
# Initialize the rules with iptables.
#

ROOT_UID="0"

#Ctrl-C trapping
trap ctrlc INT
ctrlc()
{
    echo -e "\nAborted by user."
    rm -rf $TMP_DIR
    exit 2
}

#Check if run as root
if [ "$UID" -ne "$ROOT_UID" ] ; then
    echo "You must be root to do that!"
    exit 1
fi


echo "Which ports do you want to open ?"


allow_icmp="0"
echo -n "Allow ping (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_icmp="1"
fi

allow_ftp="0"
echo -n "Allow ftp (file transfert) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_ftp="1"
fi

allow_ssh="0"
echo -n "Allow ssh (secure shell) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_ssh="1"
fi

allow_smtp="0"
echo -n "Allow smtp (mail sending) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_smtp="1"
fi

allow_http="0"
echo -n "Allow http (web server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_http="1"
fi

allow_pop3="0"
echo -n "Allow pop3 (pop3 mail server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_pop3="1"
fi

allow_imap="0"
echo -n "Allow imap (imap mail server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_imap="1"
fi

allow_https="0"
echo -n "Allow https (secured web server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_https="1"
fi

allow_mysql="0"
echo -n "Allow mysql (database server) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_mysql="1"
fi

allow_vnc="0"
echo -n "Allow vnc (remote desktop) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_vnc="1"
fi

allow_samba="0"
echo -n "Allow samba (Windows file sharing) (y/n)? [y] "
read input
if [ -z "$input" ] || [ "$input" == "y" ] || [ "$input" == "yes" ] || [ "$input" == "Y" ] || [ "$input" == "YES" ] ; then
    allow_samba="1"
fi


echo -e "\nDo you really want to apply iptables rules ? This will clear every iptables"
echo "settings. Use Ctrl-C then 'iptables-save' to save your current settings."
echo -n "(y/n)? [n] "
read input
if [ -z "$input" ] || [ "$input" == "n" ] || [ "$input" == "no" ] || [ "$input" == "N" ] || [ "$input" == "NO" ] ; then
    exit 1
fi


echo -n "Applying rules..."


#Flushing the current rules
iptables -F


#Allow connections already established
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#Accept everything from localhost
iptables -A INPUT -i lo -j ACCEPT


#Ping
if [ $allow_icmp -eq "1" ] ; then
    iptables -A INPUT -p icmp -j ACCEPT
fi

#ftp (20,21)
if [ $allow_ftp -eq "1" ] ; then
    iptables -A INPUT -p tcp -m multiport --destination-ports ftp-data,ftp -j ACCEPT
fi

#ssh (22)
if [ $allow_ssh -eq "1" ] ; then
    iptables -A INPUT -p tcp --dport ssh -j ACCEPT
fi

#smtp (25)
if [ $allow_smtp -eq "1" ] ; then
    iptables -A INPUT -p tcp --dport smtp -j ACCEPT
fi

#http (80)
if [ $allow_http -eq "1" ] ; then
    iptables -A INPUT -p tcp --dport http -j ACCEPT
fi

#pop3 (110)
if [ $allow_pop3 -eq "1" ] ; then
    iptables -A INPUT -p tcp --dport pop3 -j ACCEPT
fi

#imap (143)
if [ $allow_imap -eq "1" ] ; then
    iptables -A INPUT -p tcp --dport imap2 -j ACCEPT
fi

#https (443)
if [ $allow_https -eq "1" ] ; then
    iptables -A INPUT -p tcp --dport https -j ACCEPT
fi

#mysql (3306)
if [ $allow_mysql -eq "1" ] ; then
    iptables -A INPUT -p tcp --dport mysql -j ACCEPT
fi

#vnc (5900)
if [ $allow_vnc -eq "1" ] ; then
    iptables -A INPUT -p tcp --dport 5900 -j ACCEPT
fi

#samba (tcp 135,139,445, udp 135,137,138,139,445)
if [ $allow_samba -eq "1" ] ; then
    iptables -A INPUT -p tcp -m multiport --destination-ports 135,139,445 -j ACCEPT
    iptables -A INPUT -p udp -m multiport --destination-ports 135,137,138,139,445 -j ACCEPT
fi


#Drop everything else
iptables -A INPUT -j DROP

#Outbound: allow everything
iptables -A OUTPUT -j ACCEPT

echo " ok !"

exit 0
```
[*]Allow execution:
```
$ sudo chmod +x /usr/local/bin/iptables-rules
```
[*]Run this script to apply iptables rules:
```
$ sudo iptables-rules
```
[/LIST]

[SIZE=3]**Create the firewall daemon**[/SIZE]
Thank you pinnockio for your [iptables firewall script]("http://ubuntuforums.org/showthread.php?t=19106") !

[LIST]
[*]Create a new script:
```
$ sudo gedit /etc/init.d/iptables
```
[*]Paste the following lines:
```
#! /bin/sh

#This is an Ubuntu adapted iptables script from gentoo
#(http://www.gentoo.org) which was originally distributed
#under the terms of the GNU General Public License v2
#and was Copyrighted 1999-2004 by the Gentoo Foundation
#
#This adapted version was intended for and ad-hoc personal
#situation and as such no warranty is provided.

. /lib/lsb/init-functions


IPTABLES_SAVE="/etc/default/iptables-rules"
SAVE_RESTORE_OPTIONS="-c"


checkrules() {
    if [ ! -f ${IPTABLES_SAVE} ]
    then
        echo "Not starting iptables. First create some rules then run"
        echo "\"/etc/init.d/iptables save\""
        return 1
    fi
}

save() {
    /sbin/iptables-save ${SAVE_RESTORE_OPTIONS} > ${IPTABLES_SAVE}
    return $?
}

start(){
    checkrules || return 1
    /sbin/iptables-restore ${SAVE_RESTORE_OPTIONS} < ${IPTABLES_SAVE}
    return $?
}


case "$1" in
    save)
        echo -n "Saving iptables state..."
        save
        if [ $? -eq 0 ] ; then
            echo " ok"
        else
            echo " error !"
        fi
    ;;

    start)
        log_begin_msg "Loading iptables state and starting firewall..."
        start
        log_end_msg $?
    ;;
    stop)
        log_begin_msg "Stopping firewall..."
        for a in `cat /proc/net/ip_tables_names`; do
            /sbin/iptables -F -t $a
            /sbin/iptables -X -t $a

            if [ $a == nat ]; then
                /sbin/iptables -t nat -P PREROUTING ACCEPT
                /sbin/iptables -t nat -P POSTROUTING ACCEPT
                /sbin/iptables -t nat -P OUTPUT ACCEPT
            elif [ $a == mangle ]; then
                /sbin/iptables -t mangle -P PREROUTING ACCEPT
                /sbin/iptables -t mangle -P INPUT ACCEPT
                /sbin/iptables -t mangle -P FORWARD ACCEPT
                /sbin/iptables -t mangle -P OUTPUT ACCEPT
                /sbin/iptables -t mangle -P POSTROUTING ACCEPT
            elif [ $a == filter ]; then
                /sbin/iptables -t filter -P INPUT ACCEPT
                /sbin/iptables -t filter -P FORWARD ACCEPT
                /sbin/iptables -t filter -P OUTPUT ACCEPT
            fi
        done
        log_end_msg 0
    ;;

    restart)
        log_begin_msg "Restarting firewall..."
        for a in `cat /proc/net/ip_tables_names`; do
            /sbin/iptables -F -t $a
            /sbin/iptables -X -t $a
        done;
        start
        log_end_msg $?
    ;;

    *)
        echo "Usage: /etc/init.d/iptables {start|stop|restart|save}" >&2
        exit 1
        ;;
esac

exit 0
```
[*]Allow execution:
```
$ sudo chmod +x /etc/init.d/iptables
```
[*]Add daemon to runlevels to run it before network is started (on boot) and kill it after network is stopped (on halt/reboot):
```
$ sudo update-rc.d iptables start 37 S . start 37 0 . start 37 6 .
```
[/LIST]

[SIZE=3]**Starting the firewall daemon**[/SIZE]
[LIST]
[*]Make sure that you set up iptables as explained above:
```
$ sudo iptables-rules
```
[*]Save iptables configuration for the daemon:
```
$ sudo /etc/init.d/iptables save
```
[*]Start the daemon:
```
$ sudo /etc/init.d/iptables start
```
[*]Done !
[/LIST]
 i created the default rules script, but when creating the firewall daemon and typed sudo gedit /etc/init.d/iptables , it did nothing, didn't create a new script. And when went through the GUI and tried to create it manually, i coudn't because i didn't have that option there. So, what to do????

---

### Post by Sam on 2011-12-12
> **johnmorkoss said:**
> i created the default rules script, but when creating the firewall daemon and typed sudo gedit /etc/init.d/iptables , it did nothing, didn't create a new script. And when went through the GUI and tried to create it manually, i coudn't because i didn't have that option there. So, what to do????

That's weird. Especially since it was working in the first step! What happen if you run in a terminal:```
gksudo gedit /etc/init.d/iptables
```
Can you create the script?

---

