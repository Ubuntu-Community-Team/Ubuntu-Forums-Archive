---
title: "Help needed to create regular expression for fail2ban"
date: 2012-08-09
forum: Server Platforms
---

### Post by farenheitcx on 2012-08-09
Hi guys, today I install fail2ban in my ubuntu server box, but i can't understand the correct usage for regular expressions for extract the IP from a log generated in the server.

If someone let me a hand with this, to create the correct failregex (regular expression) to make this new fail2ban filter. I have been working for many days and I can't create it for myself.

Here is the expression were the IP I needed to extract

```
Aug  1 03:25:46 ubuntu kernel: [ATTS] Secure: IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=192.168.0.100 DST=192.168.0.122 LEN=38 TOS=0x00 PREC=0x00 TTL=121 ID=9694 DF PROTO=UDP SPT=6135 DPT=17022 LEN=32
```The IP to block is under "SRC=192.168.0.100", where 192.168.0.100 is the IP of the attacker

Thanks in advance.

---

### Post by rubylaser on 2012-08-09
This gets the SRC ip out of that string.  I'm echoing what you put so you can see the results.

```
echo "Aug  1 03:25:46 ubuntu kernel: [ATTS] Secure: IN=eth0 OUT= MAC=xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx:xx SRC=192.168.0.100 DST=192.168.0.122 LEN=38 TOS=0x00 PREC=0x00 TTL=121 ID=9694 DF PROTO=UDP SPT=6135 DPT=17022 LEN=32" | cut -d " " -f12 | cut -d "=" -f2
```

The output is this
```
192.168.0.100
```

---

### Post by farenheitcx on 2012-08-09
Sure, but I need something like this to create my own filter in fail2ban using regex for python.

> # Option:  failregex
# Notes.:  regex to match the password failures messages in the logfile. The
#          host must be matched by a group named "host". The tag "<HOST>" can
#          be used for standard IP/hostname matching and is only an alias for
#          (?:::f{4,6}:)?(?P<host>[\w\-.^_]+)
# Values:  TEXT
#
failregex = ^%(__prefix_line)sFailed (?:password|publickey) for .* from <HOST>(?: port \d*)?(?: ssh\d*)?$To find in the log this entrance.

> 
Aug  5 10:01:37 igs sshd[27931]: Failed password for **username** from 1.2.3.4 port 59556 ssh2That search and extract the "IP" and saved in and predefined string in fail2ban called "<HOST>"

---

### Post by rubylaser on 2012-08-09
Based off that syntax, I would assume it should look something like this if you're trying to match [ATTS] Secure. You will need to test this.

```
^\[ATT\] Secure: .*SRC=<HOST>
```

---

### Post by farenheitcx on 2012-08-09
> **rubylaser said:**
> Based off that syntax, I would assume it should look something like this if you're trying to match [ATTS] Secure. You will need to test this.

```
^\[ATT\] Secure: .*SRC=<HOST>
```


```
# fail2ban-regex /var/log/messages "^\[ATTS\] Secure: .*SRC=<HOST>"

Running tests
=============

Use regex line : ^\[ATTS\] Secure: .*SRC=<HOST>
Use log file   : /var/log/messages


Results
=======

Failregex
|- Regular expressions:
|  [1] ^\[ATTS\] Secure: .*SRC=<HOST>
|
`- Number of matches:
   [1] 0 match(es)

Ignoreregex
|- Regular expressions:
|
`- Number of matches:

Summary
=======

Sorry, no match

Look at the above section 'Running tests' which could contain important
information.
```Nothing with that, 0 matches. Needed to perform that regex for search the IPs in the log file.

---

### Post by rubylaser on 2012-08-09
I am confused by your results though, the regex you passed with the [ATTS] regex doesn't appear to be listed in the regex's used. Unfortunately, I'm not really sure why that's not working.  Everytime I've used Fail2ban, I've been protected SSH or an HTTP/HTTPS site, so I could use the pre-built rules.  Maybe someone with more experience will come along to help out.

---

### Post by farenheitcx on 2012-08-09
Is a typing error from me, i checked the same command with other names. But i have the same result i don't know why this not respond :(. You're really secure with the regex created?

---

### Post by steeldriver on 2012-08-09
I've had a quick play (DISCLAIMER: I know NOTHING about fail2ban) and it looks like the ^ strictly matches only up to the end of the timestamp - so you need to modify rubylaser's rexexp in one of the following ways:

1. explicitly match the "ubuntu kernel: " part as well (including whitespace!)

```
"^ ubuntu kernel: \[ATTS\] Secure: .* SRC=<HOST>"
```2. match any sequence of characters between the timestamp and the [ATTS]

```
"^.*\[ATTS\] Secure: .* SRC=<HOST>"
```3. ignore the line start / timestamp caret and just match from [ATTS] forward

```
"\[ATTS\] Secure: .* SRC=<HOST>"
```

---

### Post by farenheitcx on 2012-08-09
Ok I will try with that.

UPDATED!: Great news!, thanks you guys, the second example by  **[steeldriver]("http://ubuntuforums.org/showpost.php?p=12161444&postcount=8") **is the solution.
** Thanks a lot both of you to solve my problem.**

---

