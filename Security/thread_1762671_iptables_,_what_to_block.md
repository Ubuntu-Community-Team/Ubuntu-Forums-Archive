---
title: "iptables , what to block ?"
date: 2011-05-19
forum: Security
---

### Post by CNM on 2011-05-19
Hi ,

i am using an ubuntu box with postfix to relay email for exchange
what happens is that when emails are sent from exchange to the outside , it will be transmitted to postfix which will route them to the destination (the internet)
also i have mailscanner configured with clamav and spamassassin
i want to configure iptables in this logic :
block all but necessary ports ...

does anyone know the required ports for such an installtion ?

thanks :)

---

### Post by Lars Noodén on 2011-05-19
[list]
[*] 22 - ssh
[*] 25 - smtp
[*] 143 - imap
[*] 993 - imaps
[*] icmp
[/list]

---

### Post by CNM on 2011-05-19
> **Lars Noodén said:**
> 
[LIST]
[*] 22 - ssh
[*] 25 - smtp
[*] 143 - imap
[*] 993 - imaps
[*] icmp
[/LIST]


yeah actually i meant what not to block sorry
those and what about 53 ?
are we talking both ways ? in and out ?

---

### Post by Lars Noodén on 2011-05-19
> **CNM said:**
> yeah actually i meant what not to block sorry
those and what about 53 ?
are we talking both ways ? in and out ?

Yes, 53 - dns, will be needed, too.

---

### Post by CNM on 2011-05-19
> **Lars Noodén said:**
> Yes, 53 - dns, will be needed, too.

and both ways
right ?
all of these both ways ?

---

### Post by Lars Noodén on 2011-05-19
> **CNM said:**
> and both ways
right ?
all of these both ways ?

Except for 53, all of those should be allowed incoming.
 
ICMP, 53 and 25 should also be allowed outgoing.

---

### Post by CNM on 2011-05-19
> **Lars Noodén said:**
> Except for 53, all of those should be allowed incoming.
 
ICMP, 53 and 25 should also be allowed outgoing.
[I]
ok so 
inside : 22,25,143,993,icmp
outside : icmp,53,25
[/I]

am i missing anything ?

---

### Post by Lars Noodén on 2011-05-19
```

I
n ---->+A-----C+----->+E------+
t      |       |      |       |
e      |postfix|      |thepox |    
r      |       |      |       |
n      |       |      |       |
e <----+B-----D+<-----+F------+
t

```

My guess:

A+B - SMTP, ICMP
A - SSH, SMTP
B - DNS

D - SMTP
E - SMTP, IMAP, IMAPS
F - SMTP

When you're setting it up, log blocked packets until you're sure you're not blocking something that was needed.  That will help you work out the details of your network.

---

### Post by CNM on 2011-05-19
> **Lars Noodén said:**
> ```

I
n ---->+A-----C+----->+E------+
t      |       |      |       |
e      |postfix|      |thepox |    
r      |       |      |       |
n      |       |      |       |
e <----+B-----D+<-----+F------+
t

```My guess:

A+B - SMTP, ICMP
A - SSH, SMTP
B - DNS

D - SMTP
E - SMTP, IMAP, IMAPS
F - SMTP

When you're setting it up, log blocked packets until you're sure you're not blocking something that was needed.  That will help you work out the details of your network.

wow
that's complicated :P lol

---

### Post by Lars Noodén on 2011-05-19
> **CNM said:**
> wow
that's complicated :P lol

It can be simplified by getting rid of the one on the right edge of the diagram. :)

If you need groupware options, then there is   [Kolab](http://www.kolab.org/),    [Citadel](http://www.citadel.org/),  [Dingo Calendar Server]( http://andrew.triumf.ca/dingo/),   [Darwin CalendarServer](http://trac.calendarserver.org/),    [Bedework](http://www.bedework.org/),   [Zimbra](http://www.zimbra.com/), or     [OpenGroupware](http://www.opengroupware.org/)
        

If you only need [mail](http://bsdly.blogspot.com/2011/02/problem-isnt-email-its-microsoft.html) then there is     [simta](http://rsug.itd.umich.edu/software/simta/),    [Dovecot](http://www.dovecot.org/),         [Postfix](http://www.postfix.org/),    [Exim](http://www.exim.org/), or     [Sendmail](http://www.sendmail.org/).

:D

---

### Post by CNM on 2011-05-19
> **Lars Noodén said:**
> It can be simplified by getting rid of the one on the right edge of the diagram. :)

If you need groupware options, then there is   [Kolab]("http://www.kolab.org/"),    [Citadel]("http://www.citadel.org/"),  [Dingo Calendar Server]("http://andrew.triumf.ca/dingo/"),   [Darwin CalendarServer]("http://trac.calendarserver.org/"),    [Bedework]("http://www.bedework.org/"),   [Zimbra]("http://www.zimbra.com/"), or     [OpenGroupware]("http://www.opengroupware.org/")
        

If you only need [mail]("http://bsdly.blogspot.com/2011/02/problem-isnt-email-its-microsoft.html") then there is     [simta]("http://rsug.itd.umich.edu/software/simta/"),    [Dovecot]("http://www.dovecot.org/"),         [Postfix]("http://www.postfix.org/"),    [Exim]("http://www.exim.org/"), or     [Sendmail]("http://www.sendmail.org/").

:D

hahahahaha wait wait :P lol
i think you took this into a higher level :P hahahha
what are all these : [Citadel]("http://www.citadel.org/"),  [Dingo Calendar Server]("http://andrew.triumf.ca/dingo/"),   [Darwin CalendarServer]("http://trac.calendarserver.org/"),    [Bedework]("http://www.bedework.org/"),   [Zimbra]("http://www.zimbra.com/"), or     [OpenGroupware]("http://www.opengroupware.org/") ??? lol
i am using postfix as relay agent to exchange from internet and to internet from exchange
with on the same linux box , mailscanner configured with spamassassin and clamav ...
i just need to know what port to open , inside and outside :)

---

### Post by CNM on 2011-05-21
is this correct ? :

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT

---

### Post by Lars Noodén on 2011-05-21
Here it is a little more fleshed out as a System V Init script. (I should sit down and learn upstart some day.) 
REJECT makes it easier to diagnose problems and ICMP is important to let in.

```

#/bin/sh
# basic IP Tables-based IPv4/IPv6 filter
# Lars Nooden, lars.nooden@gmail.com

# update-rc.d firewall start 20 2 3 4 5 . stop 20 0 1 6 S .

# See: 
# http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/initscrcomconv.html 
# http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/facilname.html

# For a non-init.d option, See Also:
# https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup

### BEGIN INIT INFO
# Provides:          firewall
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start packet filter at boot time
# Description:       Enable packet filter provided by IP Tables.
### END INIT INFO

# load script logging functions
. /lib/lsb/init-functions

start_4filter()
{
   ## 
   ## set default policies
   iptables --policy INPUT   DROP;              # has to be DROP, 
   iptables --policy OUTPUT  DROP;              # default policy 
   iptables --policy FORWARD DROP;              # won't use REJECT

   ##
   ## start fresh
   iptables -Z; # zero counters
   iptables -F; # flush (delete) rules
   iptables -X; # delete all extra chains

   ##
   ##
   iptables -A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT
   iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
   # allow the courtesy of at least a ping
   iptables -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ##
   ##
   iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT

   ##
   ##
   iptables -A OUTPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -o lo -j ACCEPT
   iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

   # Default policy can't use REJECT, so we add these at the end
   iptables -A INPUT   -j REJECT;       # hack for changing default policy
   iptables -A OUTPUT  -j REJECT;       # from DROP to REJECT
   iptables -A FORWARD -j REJECT;       # 


}

stop_4filter()
{
   ## 
   ## set default policies to let everything in
   iptables --policy INPUT   ACCEPT;
   iptables --policy OUTPUT  ACCEPT;
   iptables --policy FORWARD ACCEPT;

   ##
   ## start fresh
   iptables -Z; # zero counters
   iptables -F; # flush (delete) rules
   iptables -X; # delete all extra chains

}

##
###
##

start_6filter()
{
   ##
   ## set default policies
   ip6tables --policy INPUT   DROP;     # has to be DROP,
   ip6tables --policy OUTPUT  DROP;     # default policy
   ip6tables --policy FORWARD DROP;     # won't use REJECT

   ##
   ## start fresh
   ip6tables -Z;        # zero counters
   ip6tables -F;        # flush (delete) rules
   ip6tables -X;        # delete all extra chains

   ##
   ##
   ip6tables -A INPUT -i lo --source ::1/128 --destination ::1/128 -j ACCEPT
   ip6tables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
   # allow the courtesy of at least a ping
   ip6tables -A INPUT -p icmpv6 --icmpv6-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ##
   ##
   ip6tables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT

   ##
   ##
   ip6tables -A OUTPUT -o lo --source ::1/128 --destination ::1/128 -j ACCEPT
   ip6tables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   ip6tables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   ip6tables -A OUTPUT -p icmp -o eth0 -j ACCEPT

   # Default policy can't use REJECT, so we add these at the end
   ip6tables -A INPUT   -j REJECT;      # hack for changing default policy
   ip6tables -A OUTPUT  -j REJECT;      # from DROP to REJECT
   ip6tables -A FORWARD -j REJECT;      #

}

stop_6filter()
{
   ##
   ## set default policies to let everything in
   ip6tables --policy INPUT   ACCEPT;
   ip6tables --policy OUTPUT  ACCEPT;
   ip6tables --policy FORWARD ACCEPT;

   ##
   ## start fresh
   ip6tables -Z; # zero counters
   ip6tables -F; # flush (delete) rules
   ip6tables -X; # delete all extra chains

}


##
###
##

main()
{
   case "$1" in
      start)
           log_daemon_msg "Loading packet filter rules" "iptables"
           start_4filter;
           start_6filter;
           log_end_msg $?
       ;;
     stop)
           log_daemon_msg "Clearing packet filter rules" "iptables"
           stop_4filter;
           stop_6filter;
           log_end_msg $?
       ;;
     force-reload|restart)
       $0 stop
       $0 start
       ;;
     *)
       echo "Usage: $0 {start|stop|restart|force-reload}"
       exit 1
       ;;
   esac
}

# allow several parameters to be used, in sequence
while test -n "$1";  do
  main $1;
  shift;
done;


exit 0


```

---

### Post by CNM on 2011-05-21
> **Lars Noodén said:**
> Here it is a little more fleshed out as a System V Init script. (I should sit down and learn upstart some day.) 
REJECT makes it easier to diagnose problems and ICMP is important to let in.

```

#/bin/sh
# basic IP Tables-based IPv4/IPv6 filter
# Lars Nooden, lars.nooden@gmail.com

# update-rc.d firewall start 20 2 3 4 5 . stop 20 0 1 6 S .

# See: 
# http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/initscrcomconv.html 
# http://refspecs.freestandards.org/LSB_3.1.0/LSB-Core-generic/LSB-Core-generic/facilname.html

# For a non-init.d option, See Also:
# https://help.ubuntu.com/community/IptablesHowTo#Configuration%20on%20startup

### BEGIN INIT INFO
# Provides:          firewall
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start packet filter at boot time
# Description:       Enable packet filter provided by IP Tables.
### END INIT INFO

# load script logging functions
. /lib/lsb/init-functions

start_4filter()
{
   ## 
   ## set default policies
   iptables --policy INPUT   DROP;              # has to be DROP, 
   iptables --policy OUTPUT  DROP;              # default policy 
   iptables --policy FORWARD DROP;              # won't use REJECT

   ##
   ## start fresh
   iptables -Z; # zero counters
   iptables -F; # flush (delete) rules
   iptables -X; # delete all extra chains

   ##
   ##
   iptables -A INPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -i lo -j ACCEPT
   iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
   # allow the courtesy of at least a ping
   iptables -A INPUT -p icmp --icmp-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ##
   ##
   iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT

   ##
   ##
   iptables -A OUTPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -o lo -j ACCEPT
   iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

   # Default policy can't use REJECT, so we add these at the end
   iptables -A INPUT   -j REJECT;       # hack for changing default policy
   iptables -A OUTPUT  -j REJECT;       # from DROP to REJECT
   iptables -A FORWARD -j REJECT;       # 


}

stop_4filter()
{
   ## 
   ## set default policies to let everything in
   iptables --policy INPUT   ACCEPT;
   iptables --policy OUTPUT  ACCEPT;
   iptables --policy FORWARD ACCEPT;

   ##
   ## start fresh
   iptables -Z; # zero counters
   iptables -F; # flush (delete) rules
   iptables -X; # delete all extra chains

}

##
###
##

start_6filter()
{
   ##
   ## set default policies
   ip6tables --policy INPUT   DROP;     # has to be DROP,
   ip6tables --policy OUTPUT  DROP;     # default policy
   ip6tables --policy FORWARD DROP;     # won't use REJECT

   ##
   ## start fresh
   ip6tables -Z;        # zero counters
   ip6tables -F;        # flush (delete) rules
   ip6tables -X;        # delete all extra chains

   ##
   ##
   ip6tables -A INPUT -i lo --source ::1/128 --destination ::1/128 -j ACCEPT
   ip6tables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
   # allow the courtesy of at least a ping
   ip6tables -A INPUT -p icmpv6 --icmpv6-type echo-request \
         -m limit --limit 1/s -i eth0 -j ACCEPT

   ##
   ##
   ip6tables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT

   ##
   ##
   ip6tables -A OUTPUT -o lo --source ::1/128 --destination ::1/128 -j ACCEPT
   ip6tables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   ip6tables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   ip6tables -A OUTPUT -p icmp -o eth0 -j ACCEPT

   # Default policy can't use REJECT, so we add these at the end
   ip6tables -A INPUT   -j REJECT;      # hack for changing default policy
   ip6tables -A OUTPUT  -j REJECT;      # from DROP to REJECT
   ip6tables -A FORWARD -j REJECT;      #

}

stop_6filter()
{
   ##
   ## set default policies to let everything in
   ip6tables --policy INPUT   ACCEPT;
   ip6tables --policy OUTPUT  ACCEPT;
   ip6tables --policy FORWARD ACCEPT;

   ##
   ## start fresh
   ip6tables -Z; # zero counters
   ip6tables -F; # flush (delete) rules
   ip6tables -X; # delete all extra chains

}


##
###
##

main()
{
   case "$1" in
      start)
           log_daemon_msg "Loading packet filter rules" "iptables"
           start_4filter;
           start_6filter;
           log_end_msg $?
       ;;
     stop)
           log_daemon_msg "Clearing packet filter rules" "iptables"
           stop_4filter;
           stop_6filter;
           log_end_msg $?
       ;;
     force-reload|restart)
       $0 stop
       $0 start
       ;;
     *)
       echo "Usage: $0 {start|stop|restart|force-reload}"
       exit 1
       ;;
   esac
}

# allow several parameters to be used, in sequence
while test -n "$1";  do
  main $1;
  shift;
done;


exit 0


```

thanks a lot mate ! :)
highly informative !
will be looking at that very closely !
thanks :)

---

### Post by Lars Noodén on 2011-05-21
Here's an alternate way to manage the SSH connections, since it will come under fire.

```

start_ssh()
{
   ip6tables -N SSH;    # create chain
   iptables  -N SSH;    # create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;

   # accept incoming connections, in moderation
   ip6tables -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT 
   iptables  -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT 

   # allow finite new connections per timelimit
   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT

   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
}


```

---

### Post by CNM on 2011-05-21
> **Lars Noodén said:**
> Here's an alternate way to manage the SSH connections, since it will come under fire.

```

start_ssh()
{
   ip6tables -N SSH;    # create chain
   iptables  -N SSH;    # create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -j SSH;

   # accept incoming connections, in moderation
   ip6tables -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT 
   iptables  -I SSH -i eth0 -p tcp --destination-port 22 \
      -m limit --limit 1/minute --limit-burst 2 -j ACCEPT 

   # allow finite new connections per timelimit
   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --update --seconds 60 --hitcount 4 -j REJECT

   ip6tables -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
   iptables  -I SSH -p tcp --destination-port 22 -i eth0 \
      -m state --state NEW -m recent --set
}


```

when i was researching i encountered those :
# Allows SMTP access -A INPUT -p tcp --dport 25 -j ACCEPT  # Allows pop and pops connections -A INPUT -p tcp --dport 110 -j ACCEPT -A INPUT -p tcp --dport 995 -j ACCEPT  # Allows imap and imaps connections  -A INPUT -p tcp --dport 143 -j ACCEPT -A INPUT -p tcp --dport 993 -j ACCEPT

so more ports to open ...
actually i need the minimum ports to open ...
by doing this :

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT     
is it enough ?
how do i open the icmp ? (must i open it for in and out?)
i need to do them as commands ... the script form in not really a need for now :)

---

### Post by Lars Noodén on 2011-05-22
> **CNM said:**
>     
is it enough ?

Probably.  Like mentioned, log the blocked packets for a little while when you first try the filter.  That way you might spot something you missed.
> **CNM said:**
>     
how do i open the icmp ? (must i open it for in and out?)
i need to do them as commands ... the script form in not really a need for now :)


Scan for 'icmp' in post #13 above, for a lean example.  You should let ICMP both in and out because it's needed for operation of the network.

---

### Post by CNM on 2011-05-22
> **Lars Noodén said:**
> Probably.  Like mentioned, log the blocked packets for a little while when you first try the filter.  That way you might spot something you missed.



Scan for 'icmp' in post #13 above, for a lean example.  You should let ICMP both in and out because it's needed for operation of the network.

ok so for the icmp part , these are ok ? :

iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

can you please elaborate on the first one ?
is there an example on how to log the blobed packets ? is it a parameter i have to add ?

thanks :)

---

### Post by Lars Noodén on 2011-05-22
> **CNM said:**
> ok so for the icmp part , these are ok ? :

iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

can you please elaborate on the first one ?
is there an example on how to log the blobed packets ? is it a parameter i have to add ?

thanks :)

The first one limits the ping to one per second.  See also this [example](http://www.cyberciti.biz/tips/howto-limit-linux-syn-attacks.html)

Logging packets is done by using the LOG target.  (-j LOG) If you put it at the tail end of the INPUT chain, then any packet that was not ACCEPTed earlier on will get logged.

```

# add this after all other rules
iptables -A INPUT -j LOG

```

Note that you'll want to *not* log that much once you have the iptables rules figured out.

---

### Post by CNM on 2011-05-22
> **Lars Noodén said:**
> The first one limits the ping to one per second.  See also this [example]("http://www.cyberciti.biz/tips/howto-limit-linux-syn-attacks.html")

Logging packets is done by using the LOG target.  (-j LOG) If you put it at the tail end of the INPUT chain, then any packet that was not ACCEPTed earlier on will get logged.

```

# add this after all other rules
iptables -A INPUT -j LOG

```Note that you'll want to *not* log that much once you have the iptables rules figured out.

ok so doing these is ok ? :
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT     
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT
iptables -A INPUT -j LOG

note that i will be using them via CLI , in that specific order ...

p.s
eth0 in the icmp line is the public interface right ?

---

### Post by Lars Noodén on 2011-05-22
> **CNM said:**
> ok so doing these is ok ? :
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT     
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT
iptables -A INPUT -j LOG

note that i will be using them via {shell} , in that specific order ...

p.s
eth0 in the icmp line is the public interface right ?

It looks kind of OK except that you're blocking all outgoing traffic.  Take another look at [#13](http://ubuntuforums.org/showpost.php?p=10845503&postcount=13)

What eth0 is depends on how your machine is set up.  That's something you'll have to look at yourself.

---

### Post by CNM on 2011-05-22
> **Lars Noodén said:**
> It looks kind of OK except that you're blocking all outgoing traffic.  Take another look at [#13]("http://ubuntuforums.org/showpost.php?p=10845503&postcount=13")

What eth0 is depends on how your machine is set up.  That's something you'll have to look at yourself.

all outgoing ?
i allowed on port 25 and 53 and for icmp ...
do you mean this : 
iptables -A OUTPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -o lo -j ACCEPT

??

---

### Post by Lars Noodén on 2011-05-22
> **CNM said:**
> all outgoing ?
i allowed on port 25 and 53 and for icmp ...
do you mean this : 
iptables -A OUTPUT -s 127.0.0.0/8 -d 127.0.0.0/8 -o lo -j ACCEPT

??

I was thinking  the part just below that:
```

   iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

```

It may help to try to draw on paper the workflow.  Packets come in via INPUT and go out via OUTPUT on the respective interfaces.  The drop through until they hit a rule that matches then they go to the target chain specified in that rule.

---

### Post by CNM on 2011-05-22
> **Lars Noodén said:**
> I was thinking  the part just below that:
```

   iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
   iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

```It may help to try to draw on paper the workflow.  Packets come in via INPUT and go out via OUTPUT on the respective interfaces.  The drop through until they hit a rule that matches then they go to the target chain specified in that rule.

so should i do this ? :

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG

iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT
iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

in that specific order ?
why did we add the last lines for tcp,udp,icmp for output and not for input as well ?

---

### Post by Lars Noodén on 2011-05-22
> **CNM said:**
> 
in that specific order ?


Yes, in that order.  -A appends the rule to the end of the chain, -I prepends the rule to the start of the chain.  We're basically making two (INPUT, OUTPUT) flowcharts.  The end of INPUT becomes the beginning of OUTPUT.

(Hmm.  This is kind of hard to work through in a web forum.)

> **CNM said:**
> why did we add the last lines for tcp,udp,icmp for output and not for input as well ?

That's why the ESTABLISHED,RELATED rule was in #13, to allow packets back in that are part of outgoing connections.  They got their hand stamped on the way out so they can get back in again.

---

### Post by CNM on 2011-05-22
> **Lars Noodén said:**
> Yes, in that order.  -A appends the rule to the end of the chain, -I prepends the rule to the start of the chain.  We're basically making two (INPUT, OUTPUT) flowcharts.  The end of INPUT becomes the beginning of OUTPUT.

(Hmm.  This is kind of hard to work through in a web forum.)



That's why the ESTABLISHED,RELATED rule was in #13, to allow packets back in that are part of outgoing connections.  They got their hand stamped on the way out so they can get back in again.

so the rules below are still not complete ? :
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG

iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT
iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT

---

### Post by Lars Noodén on 2011-05-22
> **CNM said:**
> so the rules below are still not complete ? :

Correct.  You allow 25 and 53 out.  What happens to the response, how does it get back in?  Also 53 (dns) often uses UDP, so UDP must be allowed.  

Can you print out post #13?

---

### Post by CNM on 2011-05-22
> **Lars Noodén said:**
> Correct.  You allow 25 and 53 out.  What happens to the response, how does it get back in?  Also 53 (dns) often uses UDP, so UDP must be allowed.  

Can you print out post #13?

oh i see ... what will i have to do more to this ? :

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG

iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT
iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT 

actually i dont have printer access right now ... why do you need me to print it out ?
i have it saved though

---

### Post by Lars Noodén on 2011-05-22
> **CNM said:**
> ... why do you need me to print it out ?
i have it saved though


You don't need to.  It's just that it would be easier to go through it step by step on paper.  It's got all the parts you are asking about.

---

### Post by CNM on 2011-05-22
> **Lars Noodén said:**
> You don't need to.  It's just that it would be easier to go through it step by step on paper.  It's got all the parts you are asking about.
oh ok i see ...

will do that ... 
but do you think this is enough or no ? :

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG

iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT
iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT 

what do you think i should add ?

---

### Post by CNM on 2011-05-22
do i have to open 995 and 465 as well ?
both ways ?

i am using ubuntu just as mail relay to exchange ... with mailscanner to scan incoming/outgoing mail

---

### Post by Lars Noodén on 2011-05-22
I would expect that smtp (port 25) both directions and dns (port 53) going out should be enough.  imaps is only needed if you are going to serve mail from that machine.

---

### Post by CNM on 2011-05-22
> **Lars Noodén said:**
> I would expect that smtp (port 25) both directions and dns (port 53) going out should be enough.  imaps is only needed if you are going to serve mail from that machine.
oh ok
so can i confirm these as complete :

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG

iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT
iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPT


and btw should i use REJECT or DROP ?

and how about those :
iptables &#8211;A INPUT &#8211;i lo &#8211;j ACCEPT
iptables &#8211;A OUTPUT &#8211;o lo &#8211;j ACCEPT

and to use iptables against ip spoofing , are those ok ? :
iptables &#8211;N ipspoof
iptables &#8211;F ipspoof
iptables &#8211;A ipspoof &#8211;j REJECT
iptables &#8211;A INPUT &#8211;i eth1 &#8211;s myinternalsubnet &#8211;j ipspoof
iptables &#8211;A INPUT &#8211;i eth1 &#8211;s myinterfaceip &#8211;j ipspoof

and against SYN flooding , is this ok ? :
iptables &#8211;A FORWARD &#8211;i eth0 &#8211;p tcp &#8211;tcp-flags SYN SYN &#8211;m limit --limit 3/s &#8211;j tab_connexion

---

### Post by JKyleOKC on 2011-05-22
> **CNM said:**
> iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT
iptables -A OUTPUT -p tcp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p udp  -o eth0 -j ACCEPT
iptables -A OUTPUT -p icmp -o eth0 -j ACCEPTUnless I'm totally misreading this part of your rule set, you would get the same result by deleting all four of these rules and changing the policy for OUTPUT to ACCEPT.

The first of these rules accepts tcp output going to ports 25 and 53; that's fine. But the next rule accepts all other tcp packets, followed by one that does the same for udp packets, and finally for icmp packets. The result is that all packets are accepted, and the policy rule is never reached.

You almost HAVE to draw a flow chart of what you want to happen, and one of your proposed rule set, then compare them to see what's different. It's really not all that difficult once you grok it, but the documentation leaves so much to be desired that getting to that stage can be extremely difficult!

---

### Post by CNM on 2011-05-22
> **JKyleOKC said:**
> Unless I'm totally misreading this part of your rule set, you would get the same result by deleting all four of these rules and changing the policy for OUTPUT to ACCEPT.

The first of these rules accepts tcp output going to ports 25 and 53; that's fine. But the next rule accepts all other tcp packets, followed by one that does the same for udp packets, and finally for icmp packets. The result is that all packets are accepted, and the policy rule is never reached.

You almost HAVE to draw a flow chart of what you want to happen, and one of your proposed rule set, then compare them to see what's different. It's really not all that difficult once you grok it, but the documentation leaves so much to be desired that getting to that stage can be extremely difficult!
WOW you're right !
how could've i missed that !
actually i have postfix acting as mail relay to an exchange server ...
what do you think the rule set should be ?

---

### Post by JKyleOKC on 2011-05-22
Here are the rules I use to accept responses to all established connections:```
-A INPUT -m state -i eth1 --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -m state -i eth1 -o eth0 --state RELATED,ESTABLISHED -j ACCEPT
```As for the OUTPUT chain, I simply use ```
:OUTPUT ACCEPT [0:0]
```In my system, eth1 is the interface that connects to my DSL modem and eth0 is an interface for my LAN. Unless you're using the box as a router, with two NICs, you don't need to do anything special with the FORWARD chain.

---

### Post by CNM on 2011-05-22
> **JKyleOKC said:**
> Here are the rules I use to accept responses to all established connections:```
-A INPUT -m state -i eth1 --state RELATED,ESTABLISHED -j ACCEPT
-A FORWARD -m state -i eth1 -o eth0 --state RELATED,ESTABLISHED -j ACCEPT
```As for the OUTPUT chain, I simply use ```
:OUTPUT ACCEPT [0:0]
```In my system, eth1 is the interface that connects to my DSL modem and eth0 is an interface for my LAN. Unless you're using the box as a router, with two NICs, you don't need to do anything special with the FORWARD chain.
actually i am using the linux machine as email relay to an exchange server
also on this machine , i have mailscanner setup with clamav and spamassassin
so i want to close all unnecessary ports , and open ONLY the ones needed ...
what do you think is the best rule set to use for my case ?

---

### Post by JKyleOKC on 2011-05-22
The only ports that can do anything are those on which servers are listening; blocking ports on the OUTPUT side of things has no effect unless a server (or an exploit) is trying to use them. However you could allow only the ports used by mail, plus the DNS port 53, and see whether anything is affected. While setting things up, use a LOG rule at the bottom of the OUTPUT chain, though, so that you can see which other ports (if any) are attempting to get out.

The one time that I was seriously impacted by a virus, back in my Win98SE days, the lockdown of outgoing ports was what alerted me to the problem in time to shut things down and minimize the damage. However since I've been using Linux primarily (almost 10 years now) I've never had a problem with leaving the OUTPUT chain open.

Keep in mind that the OUTPUT chain filters only packets originated by the machine on which it's installed; it never sees packets that originate on other machines. They are all handled by the FORWARD chain. Again, unless the box is serving as a router, this isn't particularly significant to your problem since the mail server is presumably on this machine. You simply have to determine which ports it needs for its dialog with the Exchange server; it's not always 25 and 110 any more.

---

### Post by CNM on 2011-05-23
> **JKyleOKC said:**
> The only ports that can do anything are those on which servers are listening; blocking ports on the OUTPUT side of things has no effect unless a server (or an exploit) is trying to use them. However you could allow only the ports used by mail, plus the DNS port 53, and see whether anything is affected. While setting things up, use a LOG rule at the bottom of the OUTPUT chain, though, so that you can see which other ports (if any) are attempting to get out.

The one time that I was seriously impacted by a virus, back in my Win98SE days, the lockdown of outgoing ports was what alerted me to the problem in time to shut things down and minimize the damage. However since I've been using Linux primarily (almost 10 years now) I've never had a problem with leaving the OUTPUT chain open.

Keep in mind that the OUTPUT chain filters only packets originated by the machine on which it's installed; it never sees packets that originate on other machines. They are all handled by the FORWARD chain. Again, unless the box is serving as a router, this isn't particularly significant to your problem since the mail server is presumably on this machine. You simply have to determine which ports it needs for its dialog with the Exchange server; it's not always 25 and 110 any more.

ok , so the rules below are ok and sufficient ? :

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG

iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT

so that the machine can talk to itself :
iptables –A INPUT –i lo –j ACCEPT
iptables –A OUTPUT –o lo –j ACCEPT

and to use iptables against ip spoofing  :
iptables –N ipspoof
iptables –F ipspoof
iptables –A ipspoof –j REJECT
iptables –A INPUT –i eth1 –s myinternalsubnet –j ipspoof
iptables –A INPUT –i eth1 –s myinterfaceip –j ipspoof

and against SYN flooding :
iptables –A FORWARD –i eth0 –p tcp –tcp-flags SYN SYN –m limit --limit 3/s –j tab_connexion

am i correct ?

---

### Post by JKyleOKC on 2011-05-23
> **CNM said:**
> ok , so the rules below are ok and sufficient ? :

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG

iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT

so that the machine can talk to itself :
[COLOR="Red"]iptables –A INPUT –i lo –j ACCEPT[/COLOR]
iptables –A OUTPUT –o lo –j ACCEPT

and to use iptables against ip spoofing  :
iptables –N ipspoof
iptables –F ipspoof
iptables –A ipspoof –j REJECT
[COLOR="Red"]iptables –A INPUT –i eth1 –s myinternalsubnet –j ipspoof
iptables –A INPUT –i eth1 –s myinterfaceip –j ipspoof
[/COLOR]
and against SYN flooding :
iptables –A FORWARD –i eth0 –p tcp –tcp-flags SYN SYN –m limit --limit 3/s –j tab_connexion

am i correct ?If this is the exact sequence of your rules, those that I've made show as red will be logged regardless of whether the packets are accepted or not. The logging rule should be the very last one in its chain if your purpose is to log only dropped packets.

It's not clear to me whether you have one, or two, interfaces here since some of your rules refer to eth1 and others to eth0. If you do have two interfaces, setting the FORWARD chain's policy to DROP, without providing any rules about what to accept, will effectively block all traffic not originating from or addressed to this machine.

For guarding against SYN flood attacks, I use the setting in /etc/sysctl.conf and don't mention it at all in my iptables rules. Read all the comments in the sysctl.conf file to learn about other flag bits available. My general policy is to keep iptables as simple as possible (but, as Einstein said, no simpler).

---

### Post by CNM on 2011-05-23
> **JKyleOKC said:**
> If this is the exact sequence of your rules, those that I've made show as red will be logged regardless of whether the packets are accepted or not. The logging rule should be the very last one in its chain if your purpose is to log only dropped packets.

It's not clear to me whether you have one, or two, interfaces here since some of your rules refer to eth1 and others to eth0. If you do have two interfaces, setting the FORWARD chain's policy to DROP, without providing any rules about what to accept, will effectively block all traffic not originating from or addressed to this machine.

For guarding against SYN flood attacks, I use the setting in /etc/sysctl.conf and don't mention it at all in my iptables rules. Read all the comments in the sysctl.conf file to learn about other flag bits available. My general policy is to keep iptables as simple as possible (but, as Einstein said, no simpler).

i have one interface with an ip of my internal subnet (eth0)
and one interface connected to the internet (eth1)
i will check the sysctl.conf for the synflood
as for the IP spoofing , is it correct ?

do you suggest i move the rules in red to the latest bottom ?

as for the forward issue , the emails sent from exchange are sent to postfix then sent via the ISP smtp to the destination
the emails comming to exchange will come through the linux machine where they are scanned and sent back to the exchange
what do you suggest i should do ?

---

### Post by JKyleOKC on 2011-05-23
I would move the INPUT logging rule to the absolute bottom, if making minimum changes to your list. Actually, I prefer to group all of the rules for a single chain together. That makes it much easier to spot situations where there's a potential problem.

As I noted before, the absence of rules to accept packets in the FORWARD chain means that all traffic from your LAN will be dropped. I doubt that this is what you want to happen.

You may need some prerouting and postrouting rules in different tables, also, to make certain that traffic from the LAN goes where you want it to go. Your situation is quite a bit different from those with which I'm familiar, so I can't be much more help. The quickest way to set it up is to insert logging rules at the end of every chain, with titles; here's the one I use for checking:```
-A LOG_DROP -j LOG  --log-prefix "[IPTABLES DROP] : "
```where "LOG_DROP" is a chain I created just for logging. You can put such a rule at the end of each chain, and change the title to indicate which chain it's in. Be aware that your /var/log/syslog file will grow quite rapidly -- that's why I no longer use the rule!

---

### Post by CNM on 2011-05-23
> **JKyleOKC said:**
> I would move the INPUT logging rule to the absolute bottom, if making minimum changes to your list. Actually, I prefer to group all of the rules for a single chain together. That makes it much easier to spot situations where there's a potential problem.

As I noted before, the absence of rules to accept packets in the FORWARD chain means that all traffic from your LAN will be dropped. I doubt that this is what you want to happen.

You may need some prerouting and postrouting rules in different tables, also, to make certain that traffic from the LAN goes where you want it to go. Your situation is quite a bit different from those with which I'm familiar, so I can't be much more help. The quickest way to set it up is to insert logging rules at the end of every chain, with titles; here's the one I use for checking:```
-A LOG_DROP -j LOG  --log-prefix "[IPTABLES DROP] : "
```where "LOG_DROP" is a chain I created just for logging. You can put such a rule at the end of each chain, and change the title to indicate which chain it's in. Be aware that your /var/log/syslog file will grow quite rapidly -- that's why I no longer use the rule!

actually , my policy is block all but ...
i only want to open ports of dns and those used for emails ... nothing fancy :)
and of course log what was dropped
so protection should be inside and outside (preventing source routing attacks)
i got lots of solutions but each one different than the other ...
let's say i did this : 

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG
iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT
iptables –A OUTPUT –o lo –j ACCEPT
iptables –N ipspoof
iptables –F ipspoof
iptables –A ipspoof –j REJECT
iptables –A FORWARD –i eth0 –p tcp –tcp-flags SYN SYN –m limit --limit 3/s –j tab_connexion
iptables –A INPUT –i lo –j ACCEPT
iptables –A INPUT –i eth1 –s myinternalsubnet –j ipspoof
iptables –A INPUT –i eth1 –s myinterfaceip –j ipspoof

what's missing ? what's unecessary ? and what's to optimize/edit ?

---

### Post by JKyleOKC on 2011-05-23
I would still move those last three rules up to be just in front of the logging rule for the INPUT chain, unless you really want their packets to be logged. If you do, I would put them right after the logging rule. Having them appear at the end of the list will simply confuse you eventually, since an "iptables -L" command will move them up to follow the logging rule.

Beyond that, simply try it and see. Without knowing all the ports your various servers may need to use, none of us can assure you that your rules are complete. The best we can do is offer suggestions to make your learning curve a bit easier.

---

### Post by CNM on 2011-05-23
> **JKyleOKC said:**
> I would still move those last three rules up to be just in front of the logging rule for the INPUT chain, unless you really want their packets to be logged. If you do, I would put them right after the logging rule. Having them appear at the end of the list will simply confuse you eventually, since an "iptables -L" command will move them up to follow the logging rule.

Beyond that, simply try it and see. Without knowing all the ports your various servers may need to use, none of us can assure you that your rules are complete. The best we can do is offer suggestions to make your learning curve a bit easier.
so you mean going like this ? :
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP
iptables -A INPUT -p tcp -m multiport --dport 22,25,143,993 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 1/s -i eth0 -j ACCEPT
iptables -A INPUT -j LOG
iptables –A INPUT –i lo –j ACCEPT
iptables –A INPUT –i eth1 –s myinternalsubnet –j ipspoof
iptables –A INPUT –i eth1 –s myinterfaceip –j ipspoof
iptables -A OUTPUT -p tcp -m multiport --dport 53,25 -j ACCEPT
iptables –A OUTPUT –o lo –j ACCEPT
iptables –N ipspoof
iptables –F ipspoof
iptables –A ipspoof –j REJECT
iptables –A FORWARD –i eth0 –p tcp –tcp-flags SYN SYN –m limit --limit 3/s –j tab_connexion

---

### Post by JKyleOKC on 2011-05-23
This rule may cause a bit of a problem:```
iptables –A FORWARD –i eth0 –p tcp –tcp-flags SYN SYN –m limit --limit 3/s –j tab_connexion 
```If this is your entire set of rules, that "tab_connexion" target doesn't seem to exist...

---

### Post by CNM on 2011-05-24
[COLOR=Black]> **JKyleOKC said:**
> This rule may cause a bit of a problem:```
iptables –A FORWARD –i eth0 –p tcp –tcp-flags SYN SYN –m limit --limit 3/s –j tab_connexion 
```If this is your entire set of rules, that "tab_connexion" target doesn't seem to exist...

actually you guessed it ;)
i did get an error on that one ... what should i do ?
actually i'm stll wondering is these rules are not enough :

iptables –F

iptables -A INPUT -p tcp --dport 25 -j ACCEPT

iptables -A INPUT -p udp --dport 53 -j ACCEPT

iptables -A INPUT -p icmp -j ACCEPT

iptables -A INPUT –s 127.0.0.0/8 –j ACCEPT

iptables -A INPUT –j DROP


i want to block everything but what i need , however i don't know what's the best practice for OUTPUT rules ...

of course i'll add the rules for ip spoofing and syn flooding

but i still can't get what to do with my original SYN flooding rule , the one you just pointed out ...
[/COLOR]

---

### Post by JKyleOKC on 2011-05-24
Well, you could try a single OUTPUT rule to log all attempts to send anything out and then DROP or REJECT everything via the policy. This would block everything, but the log would show you all attempts and from that you could determine which ports to allow.

As I've said several times before, I've been allowing all OUTPUT for some 10 years now, with no ill effects, but my LAN has only two users (myself and my wife) and we're both quite careful about what we do. Depending on your ISP, you may need to allow a number of ports in the OUTPUT chain, which is why I suggest blocking everything for a test while logging all activity, to see exactly which ports are needed.

As for the SYN flooding rule I have no ideas; you might go back to the posts where you found the rule originally and see what happens in that missing chain, then duplicate its actions.

When I was learning my way around iptables, I found that many if not most of the how-to documents on the web were far more complicated than they needed to be, in their efforts to be totally generic and account for all possible situations no matter how unlikely. I eventually trimmed mine down and found the "webmin" package to be a great help in doing so, although I no longer have it installed on my systems since it does pose a potential security risk in that access to it is protected only by a password, and if it's breached the invader has full root access. It did, however, generate a quite compact set of rules that I've subsequently tweaked as necessary to suit my system changes...

---

### Post by CNM on 2011-05-24
> **JKyleOKC said:**
> Well, you could try a single OUTPUT rule to log all attempts to send anything out and then DROP or REJECT everything via the policy. This would block everything, but the log would show you all attempts and from that you could determine which ports to allow.

As I've said several times before, I've been allowing all OUTPUT for some 10 years now, with no ill effects, but my LAN has only two users (myself and my wife) and we're both quite careful about what we do. Depending on your ISP, you may need to allow a number of ports in the OUTPUT chain, which is why I suggest blocking everything for a test while logging all activity, to see exactly which ports are needed.

As for the SYN flooding rule I have no ideas; you might go back to the posts where you found the rule originally and see what happens in that missing chain, then duplicate its actions.

When I was learning my way around iptables, I found that many if not most of the how-to documents on the web were far more complicated than they needed to be, in their efforts to be totally generic and account for all possible situations no matter how unlikely. I eventually trimmed mine down and found the "webmin" package to be a great help in doing so, although I no longer have it installed on my systems since it does pose a potential security risk in that access to it is protected only by a password, and if it's breached the invader has full root access. It did, however, generate a quite compact set of rules that I've subsequently tweaked as necessary to suit my system changes...

will download webmin and see what i can do
i am thinking on input , to open ports 25,53,sshd and icmp
and that's that !
on output im still flue on it , but 25 , 53 and ssh for sure ... right ?

---

