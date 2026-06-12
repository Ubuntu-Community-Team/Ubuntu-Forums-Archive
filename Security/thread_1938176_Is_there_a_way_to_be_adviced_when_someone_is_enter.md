---
title: "Is there a way to be adviced when someone is entering my system via ssh?"
date: 2012-03-09
forum: Security
---

### Post by tanoloco on 2012-03-09
Hello,

in my office they said to me to create a user 'guest' with full privileges to let technicians enter my system via ssh in case I need their help.
As they asked me to let this user always activated even if I don't need anyone to enter my system (and with full privileges!) I would like to know:

1. if there's a way to be warned when someone is entering my system via ssh .. best would be with a notification popup on the right up corner (I'm on lubuntu 11.10)

2. if there's a log somewhere of what a user has done in my system when he/she entered via ssh.

Said that .. I'm trying to keep this user 'guest' deactivated as long as I can :)

Thak you for any info

---

### Post by SlugSlug on 2012-03-09
type ```
w
``` in terminal

and maybe 

```
grep guest /var/log/auth.log
```

---

### Post by haqking on 2012-03-09
I would say that any technician that told me to allow the guest account with full privelege a remote access connection always available should be fired ;-)

I would seek out further advice from your IT department on this matter IMO.

Go for something like teamviewer for ad hoc connections that you can authorize as and when you need assistance.

Cheers

---

### Post by Lars Noodén on 2012-03-09
I agree with haqking.  The request sounds very suspicious and inappropriate.  You should definitely ask for clarification.  What problem are they actually trying to solve?

---

### Post by CharlesA on 2012-03-09
Totally agreed with both Haqking and Lars.

A tech shouldn't need full access (on a guest account, none the less!) to help you solve a problem.

---

### Post by tubbygweilo on 2012-03-09
A loyalty test. If you grant this wish to a tech then it is you who should be fired.

---

### Post by collisionystm on 2012-03-09
To answer the question. I would use an email alert.

Install mailutils

in the home folder of the user account, edit the .bashrc

at the bottom of it, put this

echo "$(whoami) has logged in at $(date)." | mail -s "System detected login from $(whoami)" [email]emailaddress@blahblahblah.com[/email]


If you want to check past logins

cat /var/log/auth.log | grep USERNAME


You may also want to install whowatch on the server

You can have a live view of who is logged in.

---

### Post by Jonathan L on 2012-03-11
> 1. if there's a way to be warned when someone is entering my system via ssh .. best would be with a notification popup on the right up corner (I'm on lubuntu 11.10)Hi Tano

The account is a terrible idea of course, but, the monitoring can be solved nicely with a little script which you run in the background.
```
#!/bin/sh

if [ $# -lt 1 ]; then
    echo "Usage: $0 username"
    exit 1
fi

username="$1"
while true; do
    n=`users | grep "$username" -c || true`
    if [ $n -eq 1 ]; then
        zenity --notification --text="`finger $username`"
    fi
    sleep 10
done
```Hope that's along the lines of what you were thinking.

Kind regards,
Jonathan.

---

