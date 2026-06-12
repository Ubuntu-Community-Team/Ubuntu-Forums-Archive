---
title: "dynamic DNS substitute"
date: 2009-01-09
forum: Server Platforms
---

### Post by flatline on 2009-01-09
I have something I want to do with my server, and I don't know if it is a good idea, or even possible.  I mainly use my server as a home media,file,and print server.  It also runs a Torrentflux server (using encryption).  I travel a lot and like to maintain the server using SSH.  However, my IP address is not static and does change from time to time.  I don't want a traditional Dynamic DNS, because I feel like having a resolvable name will only invite more probes/attacks.  

What I was thinking would be maybe like a cron script that gets the public-facing IP address of my server once a day and sends it to my gmail account.  Would this be possible or is it a terrible idea?

---

### Post by kebes on 2009-01-09
> **flatline said:**
> my IP address is not static and does change from time to time.  I don't want a traditional Dynamic DNS, because I feel like having a resolvable name will only invite more probes/attacks.  

What I was thinking would be maybe like a cron script that gets the public-facing IP address of my server once a day and sends it to my gmail account.  Would this be possible or is it a terrible idea?

It is possible but I don't think necessary. Using a free dynamic DNS service (I use [noip]("http://www.no-ip.com/")) is easy. They provide a utility that keeps the redirect up to date. I don't think having a resolvable name increases the change of attacks. As far as I know most attacks just cycle through IP addresses directly; they don't bother doing DNS lookups. (Why would they? The number of IP addresses is much smaller than the number of possible domain names.)

However if you're keen to use a script, I'm sure it's possible. You could write a bash script that uses wget to download a page that tells you your IP (e.g. [this one]("http://www.whatismyip.com/")), then use something like grep or awk to extract the actual IP (like [this]("http://www.ubuntugeek.com/howto-check-you-external-ip-address-from-the-command-line.html")) and save it in a file, and then use sendmail to email yourself the message.

---

### Post by cdenley on 2009-01-09
> **kebes said:**
> Why would they? The number of IP addresses is much smaller than the number of possible domain names.
Scanning dynamic dns domains is probably a good way to find insecure servers, since people who host servers but don't know how to secure them would probably be using a free dynamic DNS account. I wouldn't be surprised if scanning dynamic DNS accounts with dictionary words for the username would find an insecure server quicker than a random IP scan. However, there probably wouldn't be a significant difference, and it shouldn't be an issue anyway, since if you know what you're doing, the automated attacks you're concerned about shouldn't do any harm.

---

### Post by kebes on 2009-01-09
> **cdenley said:**
> I wouldn't be surprised if scanning dynamic DNS accounts with dictionary words for the username would find an insecure server quicker than a random IP scan. However, ... if you know what you're doing, the automated attacks you're concerned about shouldn't do any harm.
Good point, and I agree with you: a properly configured server should be fine against random probes.

That having been said, here is a bash script that I think does what the original poster asked for:
```
#!/bin/bash
# Written by ubuntuforums user "kebes"
# January 9, 2009
# Code is released into the public domain.

# This simple script gets the computer's IP address,
# and emails it to someone.


# Email address to which the mails are sent:
ADDRESS="whatever.username@gmail.com"

# Get the current date/time:
DATE=`date`

# Get the IP address from a website
# (To be courteous to the site, this script should not
# run too frequently.)
IP=`wget http://www.whatismyip.com/automation/n09230945.asp -O - -o /dev/null`

echo "Current IP is: " $IP

# Generate email headers
echo "To: " $ADDRESS > message
echo "Subject: Current IP address is " $IP >> message
echo 'Content-Type: text/html; charset="us-ascii"' >> message

# Generate email body contents
echo "IP address as of $DATE is $IP" >> message


# Send email message
sendmail $ADDRESS < message


exit 0

```
(Obviously it requires sendmail to be already installed and configured properly.)

Hope that helps.

---

### Post by flatline on 2009-01-09
> **kebes said:**
> Good point, and I agree with you: a properly configured server should be fine against random probes.

That having been said, here is a bash script that I think does what the original poster asked for:
...
(Obviously it requires sendmail to be already installed and configured properly.)

Hope that helps.
Thanks!  I may end up going with true DynamicDNS since I already have a suitable domain name registered, but not until I am a little more certain of my box's security.  I'll poke around with this script tonight.

---

