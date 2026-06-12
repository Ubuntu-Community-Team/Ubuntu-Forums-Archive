---
title: "Alert on successful ssh"
date: 2011-05-24
forum: Security
---

### Post by firebat9 on 2011-05-24
I don't know about others, but I generally don't ssh into my computer when I'm already logged on at my desktop. Is there some way to trigger an popup alert box on my end if a user successfully ssh's into my computer *while* I am using it? since this would probably mean that an attacker has gained access.

---

### Post by CharlesA on 2011-05-24
You could write a script to look at the auth.log and notify you if there is a successful authentication.

A better idea would be to secure SSH, that way you won't have to worry about any unauthorized people gaining access to it.

Is SSH accessible from the internet?

---

### Post by firebat9 on 2011-05-24
Ideally, yes. Securing ssh a better idea. But security is not guaranteed. In the worst, case, if an attacker has all of my passwords, I want to know as soon as possible. This means monitoring unusual activity from my accounts. Which leads to this question.

I don't know how well a script would work, because it would have to constantly run in the background, which wastes resources. Also, if an attacker has access, he can potentially clear the logs. Ideally, I would like to somehow trigger an event on every authentication.

I've found Snort, but I don't know anything about it. Does anyone know if Snort can do this?

---

### Post by CharlesA on 2011-05-25
I suppose the question should be:

Are you using a strong password, and what makes you think that someone would try to access your machine via SSH?

---

### Post by Lars Noodén on 2011-05-25
> **firebat9 said:**
> Is there some way to trigger an popup alert box on my end if a user successfully ssh's into my computer *while* I am using it? 

The place to put the script would be [/etc/ssh/sshrc](http://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files#.2Fetc.2Fssh.2Fsshrc).  Any script there will be executed upon successful login *before* any other actions are taken or programs run or shell accessed.

---

### Post by CharlesA on 2011-05-25
> **Lars Noodén said:**
> The place to put the script would be [/etc/ssh/sshrc](http://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files#.2Fetc.2Fssh.2Fsshrc).  Any script there will be executed upon successful login *before* any other actions are taken or programs run or shell accessed.

Thanks for that. I had no idea that even existed.

---

### Post by Lars Noodén on 2011-05-25
> **CharlesA said:**
> Thanks for that. I had no idea that even existed.

The global one is probably what @firebat9 is looking for.  There is also a corresponding per user file, [~/.ssh/rc](http://en.wikibooks.org/wiki/OpenSSH/Client_Configuration_Files#.7E.2F.ssh.2Frc) for users to work with.  Note, that apparently the global file is not run if the user's rc script exists, I'm not sure if that will present problems for the task at hand.

---

### Post by Lars Noodén on 2011-05-25
[OpenSSH sets some environment variables](http://en.wikibooks.org/wiki/OpenSSH/Server#Environment_Variables) upon successful login.  These could be used to pass info to the script about where the login is coming from and the account name.

[sudo](http://www.bsdly.net/~lars/Lectures/Network-06-sudo.odp) can be used to launch [xmessage](http://manpages.ubuntu.com/manpages/natty/en/man1/xmessage.1.html) as the user @firebat9.  Just be sure to set the display variable.

```

sudo -u firebat9 DISPLAY=:0.0 /usr/bin/xmessage -nearmouse "SSH by $USER from $SSH_CLIENT"

```

In /etc/sudoers:

```

ALL ALL=(firebat9) /usr/bin/xmessage

```

There might be security issues with allowing xmessage like that, though.  I'll have to think about it more.  Just because it can be done doesn't mean that it's necessarily a good idea.  Perhaps a clever regex can be smithed to constrain the text of the message to be only the SSH notification.

---

### Post by emiller12345 on 2011-05-25
This script can read iptables LOG entries in a messages file, and makes a beeping sound when matching certain rules...
```

#!/bin/bash
# Usage: ./logbeep.sh /var/log/message_or_other_file
#  Needs apt-get install beep
#  
#Copyright (C) 2011  by emiller12345
#
#This program is free software; you can redistribute it and/or
#modify it under the terms of the GNU General Public License
#as published by the Free Software Foundation; either version 2
#of the License, or (at your option) any later version.
#
#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.
#
#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

if [ -z "$1" ]; then
    echo "Usage: ./logbeep.sh /var/log/message_or_other_file" 1>&2
    exit 1
fi

IPT_LOG_PREFIX='FW: '
TIME=""
PROTO=""
SRC=""
DST=""
SPT=""
DPT=""

tail -f -n 0 $1 | while read -t 3 line || test -f $1; do 
    line=$(echo $line | grep $IPT_LOG_PREFIX) # filter: only grap iptables LOG entries, need ipt rule 
    line=$(echo $line | sed '/^\ *$/d; /^$/d')   # eliminate white spaces 
    TIME=""
    PROTO=""
    SRC=""
    DST=""
    SPT=""
    DPT=""
    for j in $line; do
        if [ -n "$(echo $j | grep -o ']')" ]; then
            j=$(echo ${j%?} | tr -d '[')
            TIME=$j
        fi
        if [ -n "$(echo $j | grep -o 'SRC')" ]; then
            SRC=$(echo $j|awk -F\= '{print $2}')
        fi
        if [ -n "$(echo $j | grep -o 'DST')" ]; then
            DST=$(echo $j|awk -F\= '{print $2}')
        fi
        if [ -n "$(echo $j | grep -o 'PROTO')" ]; then
            PROTO=$(echo $j|awk -F\= '{print $2}')
        fi
        if [ -n "$(echo $j | grep -o 'SPT')" ]; then
            SPT=$(echo $j|awk -F\= '{print $2}')
        fi
        if [ -n "$(echo $j | grep -o 'DPT')" ]; then
            DPT=$(echo $j|awk -F\= '{print $2}')
        fi
    done
    if [ "$DST" = "255.255.255.255" -a "$PROTO" = "UDP" ]; then
        echo 'GENERIC UDP BROADCAST ALERT! '"PROTO=$PROTO SRC=$SRC DST=$DST SPT=$SPT DPT=$DPT TIME=$TIME"
        beep -f 300.7 -d 100 -l 400 -n -f 343.6 -d 10 -l 200
    fi
    if [ "$PROTO" = "TCP" -a "$DPT" = "22" ]; then
        echo 'SSH PORT ALERT! '"PROTO=$PROTO SRC=$SRC DST=$DST SPT=$SPT DPT=$DPT TIME=$TIME"
        beep  -f 343.6 -d 10 -l 200 -n -f 300.7 -d 100 -l 400 
    fi
done

```

---

### Post by bodhi.zazen on 2011-05-25
ssh is secure and my advice is to harden your server.

Use keys, disable password authentication, and add a few rules for iptables or use a service such as denyhosts or fail2ban.

Assuming your ssh server is properly configured, such a script is unnecessary.

---

### Post by emiller12345 on 2011-05-26
> **bodhi.zazen said:**
> Assuming your ssh server is properly configured, such a script is unnecessary.
Yeah, I agree, it's more for convenience.  I have a server that has no monitor, no keyboard, no mouse, and no mail server. Only http port available to try and make it as secure as possible.  To make it easier to detect if I'm getting a massive flood of log entries, I can use a script like this to hear problems instantly. Different tone patterns means different log types.  If it starts beeping like crazy I usually just kill the power to it!

---

