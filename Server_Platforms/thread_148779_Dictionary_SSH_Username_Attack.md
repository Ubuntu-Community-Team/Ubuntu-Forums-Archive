---
title: "Dictionary SSH Username Attack?"
date: 2006-03-22
forum: Server Platforms
---

### Post by Protoss on 2006-03-22
I just got my server back up after my ISP shut off my internet because they detected attacks on my IP. I am looking thru /var/log/auth and I am finding thousands of ```
localhost sshd : Illegal user _____ from ::ffff:0.0.0.0
```Where the username is just a dictionary of different names, from admin to staff, and I'm building a list of at least 15+ IP's that these attacks came from. Can someone please tell me what the hell went on and how I can prevent it? Was this orchestrated by someone, or are these ran by zombie machines? Should I report this list of IP's to my ISP.

---

### Post by Glut on 2006-03-22
Most likely it's a standard dictionary attack from a botnet or similar. If you have decent passwords, don't worry about it, it's not work reporting. 
There are more sophisticated timing attacks that show up in logs the same way, but the solution is the same - good passwords.

---

### Post by Protoss on 2006-03-22
Yea but my ISP shut down my internet because of all this bandwith, there has to be some way to just kill access to them.

---

### Post by Horndog on 2006-03-22
This may help:

[http://fail2ban.sourceforge.net/]("http://fail2ban.sourceforge.net/")

---

### Post by Protoss on 2006-03-22
Actually found DenyHosts...seems to do what I need. Thnx for the help though.

---

### Post by Barrakketh on 2006-03-23
[QUOTE=Glut]Most likely it's a standard dictionary attack from a botnet or similar. If you have decent passwords, don't worry about it, it's not work reporting. 
There are more sophisticated timing attacks that show up in logs the same way, but the solution is the same - good passwords.[/QUOTE]
No, the solution is to disable password authentication.  Use pubkey authentication, and if the user they are attempting to log in as (assuming it even exists) doesn't have the pubkey in ~/.ssh/authorized_keys, they get no cookie :)

---

### Post by MJN on 2006-03-23
[quote=Protoss]Yea but my ISP shut down my internet because of all this bandwith, there has to be some way to just kill access to them.[/quote] 
Really? How much bandwidth was being consumed by these (failed) SSH login attempts?!

For what it's worth I get these all the time and, as others have said, you needn't worry if you're using either strong passwords or (preferably) keys as above.

Mathew

---

### Post by LordHunter317 on 2006-03-23
If bandwidth is the issue, then give your ISP the IPs and tell them to block them.

Really, you should get a new ISP as a competent one would have this information.

Adding blocks on your side won't stop them from consuming bandwidth.  Once you're blocking it at your machine the bandwidth has already been used.  They need to be dropped at the ISP's borders.

---

### Post by Protoss on 2006-03-24
Alrighty I contacted my ISP, they pointed me to a 800 number that I guess is their Abuse 'hotline' :S I'll give them a call and hopefully get this sorted out, at least they didn't go OMG Hosting a Server On a Home Cable Line? FORBIDDEN!

---

### Post by dante on 2006-03-25
What works for me is to change the port ssh is listening on (22).
It's possible to determine what port ssh is actually listening on,
but it's time consuming and can set off alarms, something
scripts don't want to do -- they'll move on until they find an open
port 22.   I've never had any unauthorized attempts to login to
my server, and it's on a public ip. 

It's pretty easy to do,  editing sshd_conf and your firewall settings,
though you'll have to specify your port when you ssh to your
machine.

---

### Post by lcg on 2006-03-25
[QUOTE=dante]What works for me is to change the port ssh is listening on (22).
It's possible to determine what port ssh is actually listening on,
but it's time consuming and can set off alarms, something
scripts don't want to do -- they'll move on until they find an open
port 22. I've never had any unauthorized attempts to login to
my server, and it's on a public ip.[/QUOTE]
I can only second that. I've had lots of automated login attempts for my ssh server with the weirdest login names, until I moved the SSH daemon to another port. Since then, nothing ...
It's a simple change, no extra software involved, it doesn't take any processing power.

HTH,
Lars

---

### Post by stilus on 2006-11-09
moving to another port is the absolute simplest solution.
add an ```
alias youralias=`ssh -p <portnumber> you@yourhost'
``` to your .bashrc on other machines, run ```
. .bashrc
``` and you are good to ssh home with a simple "youralias", without any securityissues. 
I personally have a little shellscript running hourly: ```
/etc/cron.hourly/sshblocking (NO .sh extention!) 
```
```

#!/bin/sh

# (adapted from an example I found on the net (http://www.burngreave.net/node/319 9-11-2006) 
# ... didn't work for me)
#!/bin/sh
LOGFILE="/var/log/auth.log"
HOSTSDENY="/etc/hosts.deny"
BADCOUNT="10"
grep -i "invalid user" $LOGFILE | grep -v Fail | cut -d : -f 4 | cut -d " " -f 6 | sort | uniq -c | while read i

# this does the following:
# look for invalid user entries| 
# filter out 'Failed' lines | 
# remove everyting before the third ':' (needed because for instance "nov   6" has three spaces and "nov 10" only two) |
# cut out the ip number (field six)
# sort ipnumbers 
# count the number of instances and display only only single instances
do
        count=`echo ${i} | cut -d " " -f 1`
        ip=`echo $i | cut -d " " -f 2`
#       echo "count="$count
#       echo "ip="$ip
        already=`grep $ip $HOSTSDENY | grep sshd`
        if [ -z "$already"  ]
        then
                if [ "$count" -ge "$BADCOUNT" ]
                then
                        echo "banned from sshd: "$ip
                        echo "sshd: "$ip >> $HOSTSDENY
                fi
        fi
done


```

---

### Post by stilus on 2006-11-17
okay... my port 22 has attracked more attention then a hot cheerleader in miniskirt at a LANparty.. 
So, I've changed the sshd_config and added 
```
AllowUsers <nick1> <nick2>
```.
I also tweaked my ssh blocking script a little, which I tought I would share:

```
#!/bin/sh

# (Adapted from an example I found on the net (http://www.burngreave.net/node/319 9-11-2006)
# ... didn't work for me)

# Set a bunch of variables
LOGFILE="/var/log/auth.log.*"
HOSTSDENY="/etc/hosts.deny"
BLOCKEDDATE=`date +%a\ %d-%m-%Y\ %H:%M\ \(d-m-y\)`
BADCOUNT="10"

# Filter out the naughty ones
zgrep -i -h "invalid user" ${LOGFILE} | grep -i fail | cut -d : -f 4 | cut -d " " -f 9 | sort | uniq -c | while read i

# This does the following:
# Look for invalid user (ignore case) entries in all (normal and .gz) logfiles 
# ... and display them (supress filename in output)&
# Search for "fail" (ignore case) | cut off everything before the last ":" 
# ... (needed because for instance "nov   6" has three spaces and "nov 10" only two) &
# Cut out the ip number (field nine) delimited by a space &
# Sort ipnumbers &
# Count the number of instances and display only one single instances & 
# Feed the output to:

do
        count=`echo ${i} | cut -d " " -f 1`
        ip=`echo $i | cut -d " " -f 2`
#       echo "count="$count
#       echo "ip="$ip
        already=`grep $ip $HOSTSDENY | grep sshd`
        if [ -z "$already"  ]
        then
                if [ "$count" -ge "$BADCOUNT" ]
# if greater than or equal to badcount
                then
                        echo "banned from sshd: "$ip
                        echo -e "# ${BLOCKEDDATE} ($ip) \nsshd:  $ip"  >> $HOSTSDENY
# else if lesser than or equal to badcount
                elif [ "$count" -le "$BADCOUNT" ]
                then
                        echo "$ip has been naughty $count times"
# else ... what the hell!?
                else    echo "no attacks recorded..."
                fi
        fi
done

```

So, now its
 me -> :-D ](*,)  <- them

(Careful though, If you run this script from a cronjob with all the "echo" statements, you get a full mailbox after a while)

---

