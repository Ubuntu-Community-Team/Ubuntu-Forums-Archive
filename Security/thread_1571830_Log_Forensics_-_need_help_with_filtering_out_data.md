---
title: "Log Forensics - need help with filtering out data"
date: 2010-09-10
forum: Security
---

### Post by wconstantine on 2010-09-10
I've written a script that analyzes auth.log for brute force attacks against the sshd. I need some help right now. The server is a honeypot so it's not anything serious. It's just for educational purposes only.

One of the brute force attacks:

Start time: Apr 19 05:38:01 
End time: Apr 19 08:58:54 
Login attempts: 9259 
Attacker IP: 219.150.161.20 
Successful: True 
    Number of successful logins: 4 
    ROOT ACCOUNT COMPROMISED 
Total list of compromised accounts: 
Apr 19 05:41:44 : root 
Apr 19 05:42:27 : root 
Apr 19 05:55:20 : root 
Apr 19 05:56:05 : root 

I need a CLI command that will help me filter out dates before a certain given date. For example.

cat * | date all after Apr 19 05:42:27

So I'll be shown exactly everything that happened in the logs after that time. Is there a command for this? :)

Edit:

I've looked closer in the log files now and it would seem that they don't have the same structure. So the time stamps are reported in different ways. I came up with an idea that I could convert the date to seconds from epoch. That way it's more manageable for a script to handle.

Still interested if there's no easier way though.

---

### Post by BkkBonanza on 2010-09-10
You could probably use **awk** to match the date formats and then feed them into the **date** command which can reverse them into epoch for you. Then compare against a reference epoch to drop/keep. Then push it out in a more useful format.

---

### Post by msandoy on 2010-09-10
Have you installed logwatch? It will do alot of the log filtering for you.

---

### Post by gzarkadas on 2010-09-10
Yes, [GNU awk]("http://www.gnu.org/software/gawk/") (because strftime, mktime are GNU extensions) is one of the ways to go; python and perl are also appropriate.  

I just finished this script, copy the entire code tag and make it a file in your path ( "date-tail" or "logtail" are good names for it). Then do a `chmod u+x <file>' to make it executable and you are ready to go. Examples are given after the code.

```

#!/usr/bin/gawk -f

# This program is free software; you can redistribute it and/or modify it 
# under the terms of the GNU General Public License as published by the 
# Free Software Foundation; either version 3 of the License, or (at your 
# option) any later version.
# This program is distributed in the hope that it will be useful, but 
# WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY 
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License 
# for more details.
# You should have received a copy of the GNU General Public License along 
# with this program; if not, write to the "Free Software Foundation, Inc., 
# 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA"

function month_cvt(month)
  {
    return sprintf( "%02d", (2 + \
    match("JanFebMarAprMayJunJulAugSepOctNovDec", month)) / 3 )
  }

function time_cvt(time)
  {
    return gensub(/:/, " ", "g", time)
  }

# Check input variables
NR == 1 {
    if (year == "")
      year = strftime("%Y", systime())
    if (month == "" || day == "" )
      {
        print "either 'month' or 'day' were not specified." > stderr
        exit 1
      }
    if (time == "")
        time = "00:00:00"
    argstamp =  year " " month_cvt(month) " " day " " time_cvt(time)
}

{
    logstamp = year " " month_cvt($1) " " $2 " " time_cvt($3)    
    if (mktime(logstamp) >= mktime(argstamp))
        print
}

```Usage (items enclosed in [] are optional):
```

date-tail [year=NUMBER] month=Mon day=NUMBER [time=HH:MM:SS]

```If not supplied, year defaults to current one and time to 00:00:00.
Month must be supplied as three letter abbreviation with first one capitalised.

Examples (with pipe or argument):
```

cat auth.log | date-tail month=Sep day=10 time=17:08:50

date-tail month=Sep day=10 time=17:08:50 auth.log

```[/CODE]

---

### Post by Kinstonian on 2010-09-10
Are the people who are helping you compete in the honeynet challenge going to get credit or part of the prize if you win? ;)

---

### Post by gzarkadas on 2010-09-10
> **Kinstonian said:**
> Are the people who are helping you compete in the honeynet challenge going to get credit or part of the prize if you win? ;)

May I suppose you mean [this]("http://www.honeynet.org/challenges/2010_5_log_mysteries") ? :-k hmm, I may give it a try. Anyway, the OP served a useful cause; we now have another one little tool to play with our logs :tongue:!

---

### Post by wconstantine on 2010-09-10
> **gzarkadas said:**
> Yes, [GNU awk]("http://www.gnu.org/software/gawk/") (because strftime, mktime are GNU extensions) is one of the ways to go; python and perl are also appropriate.  

I just finished this script, copy the entire code tag and make it a file in your path ( "date-tail" or "logtail" are good names for it). Then do a `chmod u+x <file>' to make it executable and you are ready to go. Examples are given after the code.

```

#!/usr/bin/gawk -f

# This program is free software; you can redistribute it and/or modify it 
# under the terms of the GNU General Public License as published by the 
# Free Software Foundation; either version 3 of the License, or (at your 
# option) any later version.
# This program is distributed in the hope that it will be useful, but 
# WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY 
# or FITNESS FOR A PARTICULAR PURPOSE. See the GNU General Public License 
# for more details.
# You should have received a copy of the GNU General Public License along 
# with this program; if not, write to the "Free Software Foundation, Inc., 
# 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA"

function month_cvt(month)
  {
    return sprintf( "%02d", (2 + \
    match("JanFebMarAprMayJunJulAugSepOctNovDec", month)) / 3 )
  }

function time_cvt(time)
  {
    return gensub(/:/, " ", "g", time)
  }

# Check input variables
NR == 1 {
    if (year == "")
      year = strftime("%Y", systime())
    if (month == "" || day == "" )
      {
        print "either 'month' or 'day' were not specified." > stderr
        exit 1
      }
    if (time == "")
        time = "00:00:00"
    argstamp =  year " " month_cvt(month) " " day " " time_cvt(time)
}

{
    logstamp = year " " month_cvt($1) " " $2 " " time_cvt($3)    
    if (mktime(logstamp) >= mktime(argstamp))
        print
}

```Usage (items enclosed in [] are optional):
```

date-tail [year=NUMBER] month=Mon day=NUMBER [time=HH:MM:SS]

```If not supplied, year defaults to current one and time to 00:00:00.
Month must be supplied as three letter abbreviation with first one capitalised.

Examples (with pipe or argument):
```

cat auth.log | date-tail month=Sep day=10 time=17:08:50

date-tail month=Sep day=10 time=17:08:50 auth.log

```[/CODE]

Wow, thanks!

> Are the people who are helping you compete in the honeynet challenge going to get credit or part of the prize if you win

Definitely credit. :) I have no chance of winning though, I'm sure of it. I'm doing it to learn. ;)

---

### Post by msandoy on 2010-09-10
Well, my suggestion of installing logwatch would not do much good when you are analysing the logfiles from the contest. I do have a server running, with FTP and SSH on standard ports, so I keep a close eye on the logfiles. It's actually quite interresting. I also use Denyhosts to stop them when they start with their dictionary attacks. Amasing how many countries are represented in my denied hosts file.

---

