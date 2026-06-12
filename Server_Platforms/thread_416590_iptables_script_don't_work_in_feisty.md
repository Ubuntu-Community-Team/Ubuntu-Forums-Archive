---
title: "iptables script don't work in feisty?"
date: 2007-04-21
forum: Server Platforms
---

### Post by bullgr on 2007-04-21
hi...

i use these scripts to setup iptables rules and save/enable iptables on boot...
this scripts are working perfect in breezy and dapper desktop and also in the dapper file server i have in my workplace.

in edgy works too after the needed change from #!/bin/sh to #!/bin/bash

with this iptables scripts (very user friendy, it ask y/n for any rule to enable) i enable samba, ssh and allow to ping

but after i upgrade to feisty the iptables rules seems not to work...
the network setup works ok, i can ping to router and to all connected pc's, samba setup it's ok and shows the
shared folder in the host pc, but when i try to connect from another pc to the shares it's not allowed.
from my experience, i had this problem in the past but after using these iptables scripts and enable samba rule all worked well.

i exclude all possibility of error of my network, samba or iptables setup because with these settings, breezy, dapper and edgy (after the change from #!/bin/sh to #!/bin/bash) worked perfect.

i believe there must some changes in the new iptables version of feisty that my iptables scripts are not get to work

i post the whole howto iptables scripts i use...
hope someone can help because it's important issue.

thank's...

> 
Create the default rules script



    * Create a new script:

      sudo gedit /usr/local/bin/iptables-rules



    * Paste the following lines:

#! /bin/bash



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



    * Allow execution:

      sudo chmod +x /usr/local/bin/iptables-rules



    * Run this script to apply iptables rules:

      sudo iptables-rules



Create the firewall daemon

    * Create a new script:

      sudo gedit /etc/init.d/iptables



    * Paste the following lines:

#! /bin/bash



#This is an Ubuntu adapted iptables script from gentoo

#([http://www.gentoo.org](http://www.gentoo.org)) which was originally distributed

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



    * Allow execution:

      sudo chmod +x /etc/init.d/iptables



    * Add daemon to runlevels to run it before network is started (on boot) and kill it after network is stopped (on halt/reboot):

      sudo update-rc.d iptables start 37 S . start 37 0 . start 37 6 .



Starting the firewall daemon



    * Make sure that you set up iptables as explained above:

      sudo iptables-rules



    * Save iptables configuration for the daemon:

      sudo /etc/init.d/iptables save



    * Start the daemon:

      sudo /etc/init.d/iptables start



    * Done !


---

### Post by lashbam on 2007-04-22
i've got the same problem.  i set my iptables manually before i open a file sharing program 

```
aaron@aaron-desktop:~$ sudo iptables -I INPUT -p tcp --dport 4662 -j ACCEPT

```

i get an error message in amule saying no answer from my 4662 port.  now i need to know how to open my ports.  any help much appreciated.

---

### Post by marx2k on 2007-04-24
I'm fiesty...works for me without any issues

Also using the firewall.bash script without any issues.

Can you give more info in regards to the error?

---

### Post by bullgr on 2007-04-25
in edgy (and also breezy and dapper) with this script's i enable the rules i needed (almost samba and ssh).
the shares was visible thru my network and all works fine.

but after i upgrade to feisty, the shares are not visible anymore. i can see the shares from the host pc but not
thru the network.

my network and samba settings are ok (nothing changes after upgrade).

i believe that the iptables rules are not working (not saving?). no matter i setup the scripts again and again,
nothing happens.

after i restore back (image backup) to edgy all works fine again. the iptables rules works again.

for some reason in feisty with this scripts i can't set the iptables rules, and the default iptables rules are remain, and so
samba rule are not allowed go thru iptables.

can someone help me? maybe advise me another method (a little easy, and not firestarter) to setup iptables rules?

thank's

---

### Post by shookone on 2007-04-26
I use Firehol firewall script which incorporates iptables.

Using feisty im getting runtime command errors and line FIN or INIT.

Thorough investigation indicates that this is an issue with Bash upgrade in Feisty Fawn

---

### Post by bullgr on 2007-04-27
i can't understand this changes every six month's, in every new release...

in dapper the iptables script's are working well...

in edgy after the changes in this release, i must change in the top of the script's
from "#! /bin/sh" to "#! /bin/bash" to be able to work the script's again. until i figure out what happens and
what to do i was searching the settings in my network, router, pc's and samba for hours...

and now, in feisty something must be changed again and the script's are not working, again...

im really frustated, every new six month's release to search what happen's and the script's are not working.
and, ok, when i find out what i need to do. but if i stuck and cain't fix it, like now?

i figure out that i have two sollutions to avoid this bad experience:

1. learn to setup iptables rules in my own, the hardcore way, no more ready scripts.

2. follow the computer rule "if it's work, don't touch it". im thinking to keep my installed ubuntu release for 18 months
until the support drop down.

---

### Post by docsmooth on 2007-05-02
can you explain a little about how you're writing these "iptables scripts"?

iptables should work as simply as follows:

set up your rules as you need them, then as root:
<code>
iptables-save >/etc/network/iptables.up.rules
</code>
Then, in your /etc/network/interfaces you can simply:
<code>
preup iptables-restore </etc/network/iptables.up.rules
</code>

This will leave you with iptables rules you can run on any 2.6.9+ kernel that supports iptables.  if you use "ip6tables-save" and "ip6tables-restore" you can do the same with IPv6 iptables rules.

No script required, fully portable, 100% supported by other vendors as well.

---

### Post by sjpwong on 2007-05-02
> **bullgr said:**
> 
1. learn to setup iptables rules in my own, the hardcore way, no more ready scripts.


I use shorewall (fully supported in Ubuntu) to do all my firewalling.  Quite easy to learn and does lots of the nice stuff for you.

---

### Post by bullgr on 2007-05-03
> **docsmooth said:**
> can you explain a little about how you're writing these "iptables scripts"?

iptables should work as simply as follows:

set up your rules as you need them, then as root:
<code>
iptables-save >/etc/network/iptables.up.rules
</code>
Then, in your /etc/network/interfaces you can simply:
<code>
preup iptables-restore </etc/network/iptables.up.rules
</code>

This will leave you with iptables rules you can run on any 2.6.9+ kernel that supports iptables.  if you use "ip6tables-save" and "ip6tables-restore" you can do the same with IPv6 iptables rules.

No script required, fully portable, 100% supported by other vendors as well.

see in my first post. it's a howto i found and uses two scripts to setup iptables rules. it's very easy...
you just type yes or no for each rule. works perfect from Breezy and Dapper, need changes in edgy
(sh to bash) and finaly works again in feisty. it was a vmware issue and not the iptables script i use.
sorry, im so stupid :oops: 

i will see shorewall what is has to offer and i start to learn iptables the hardcore way, to be sure that i can always setting up iptables.

---

