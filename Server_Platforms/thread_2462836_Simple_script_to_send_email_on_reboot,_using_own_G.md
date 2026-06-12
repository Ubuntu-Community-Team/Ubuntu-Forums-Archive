---
title: "Simple script to send email on reboot, using own Gmail address"
date: 2021-05-28
forum: Server Platforms
---

### Post by toshko3 on 2021-05-28
This is a small one-liner "script" to send an email on every reboot of a machine.

**0. As the script will be started with the help of /etc/rc.local, to ensure it is started at the end of every reboot, we're creating the rc.local file (of course, don't create it if you already have it):**
Login with root
```
su
```
Create the rc.local file if it's not already present:
```
touch /etc/rc.local && chmod +x /etc/rc.local
```
Add the following 3 lines in rc.local:
```
#!/bin/bash
/root/rebootmail.sh
exit 0
```
If you already have /etc/rc.local, just add the following line before "exit":
```
/root/rebootmail.sh
```

**1. Create a file named "rebootmail.sh" in root:**
```
touch /root/rebootmail.sh && chmod u=rwx,go= /root/rebootmail.sh
```
Add the following inside:
```

#!/bin/bash
# Create this script with ONLY root permissions (because here are your mail credentials) and give it an executable bit.
# This script uses s-nail to log into your Gmail and send an email, without the need to install you own smtp server/agent.
# You need to install it first:
# apt install s-nail
# At the time of writing this, you should enable "Less secure app access" in your Gmail, so this script could login with the standard smtp method, instead of Google's custom one.
# You could use your own Gmail as both a Sender and Recepient, so no email is ever marked as Spam.
# That's it!

# Edit the following variables:

# The hostname of the machine to be written in the subject line
host=thisismyfriendlyhostname

# The mail address we're sending to
recepient=recepient@gmail.com

# Our username of our own mail (in Gmail username is the same as the mail address)
mailuser=ourmail@gmail.com
mailpass=thisismypass

# Log path - the filename with fullpath (example: /root/rebootmail.log)
log=/root/rebootmail.log

# Edit only the quoted message after "echo" (this will be the mail body/message):
echo "test test" | s-nail -r "$recepient" -s "$host,$(date +%Y-%b-%d,%T)" -S smtp=smtp://smtp.gmail.com:587 -S smtp-use-starttls -S smtp-auth=login -S smtp-auth-user="$mailuser" -S smtp-auth-password="$mailpass" -S ssl-verify=ignore $recepient 2>> "$log" ; echo "$(date +%Y-%b-%d,%T) Process of sending mail to $recepient finished. If there is no error before this line, it is sent successfully." >> "$log"

exit

```

**2. Install s-nail**
```
apt install s-nail
```

**3. Enable "Less secure app access" in your Gmail. Use google if you don't know where is the option in your Gmail.**

**4. Start the script to test if it works:**
```
/root/rebootmail.sh
```

**5. Reboot to test if it loads on reboot:**
```
reboot
```

**6. As you may have seen, there is a log variable in the script. This is where logs and errors are logged, so even if mail is not sent successfully, you could see what and when happened.**

---

### Post by TheFu on 2021-05-28
FWIW.

Would be helpful if the specific release and dependencies were all listed at the time.

Why not use @reboot in the the crontab or anacron?  /etc/rc.local has been deprecated for some time.  I believe some systemd service needs to be unmasked to use it for the last few LTS releases.

Also, on default Ubuntu systems the root account is locked, so the first command will not succeed.  More and more distros are moving to a root-less setup. Placing the script under /root/ will prevent any non-root accounts from access if trivial efforts are made.  Of course, anyone with physical access would easily be able to copy anything on the system using a "Try Ubuntu" boot flash drive.  Still, I put stuff under /root/ all the time for similar goals. Nice, within reason.

A few parameters and wrapped lines for things that could change would help the script work better. I'd quote the target email address and password too. Scripts often fail when a PATH is assumed.  Any scripts run from a non-interactive login needs to fully specify the complete file-path to each command to ensure the correct version desired gets used. Scripts often fail because people either change the order of the PATH or the system only has a minimal one.

Which of these is easier to read?
# Edit only the quoted message after "echo" (this will be the mail body/message):
```
echo "test test" | s-nail -r "$recepient" -s "$host,$(date +%Y-%b-%d,%T)" -S smtp=smtp://smtp.gmail.com:587 -S smtp-use-starttls -S smtp-auth=login -S smtp-auth-user="$mailuser" -S smtp-auth-password="$mailpass" -S ssl-verify=ignore $recepient 2>> "$log" ; echo "$(date +%Y-%b-%d,%T) Process of sending mail to $recepient finished. If there is no error before this line, it is sent successfully." >> "$log"
```

```

TARGET_SRV_URL="smtp://smtp.gmail.com:587"

echo "test test" | /usr/bin/s-nail -r "$recipient" -s "INFO: Reboot $host, $(/usr/bin/date  "+%F %T") " \
      -S smtp=$TARGET_SRV_URL -S smtp-use-starttls -S smtp-auth=login \
      -S smtp-auth-user="$mailuser" -S smtp-auth-password="$mailpass" \
      -S ssl-verify=ignore $recipient 2>> "$log" ;
echo "INFO: $(/usr/bin/date  "+%F %T") Sent mail to $recipient." >> "$log"
```

s-nail seems interesting. I've never heard of it before. Been using normal MTAs with a normal email server setup and perhaps a relayhost if the ISP blocks outbound SMTP, but that isn't for normal end-users. OTOH, it is basic admin skill.  Use a "satellite" postfix configuration and it won't accept any network-based inbound email, but any account on the system will be allowed to send email out - assuming MX DNS and DNS records are setup.  For a home user, s-nail is probably 1000x easier. Nice.

With an MTA configured, it is very easy:
```
/usr/bin/mail -s "Good Morning" jblowe@gmail.com  < /home/thefu/morning.txt
```
Plus, at and crontab scripts can redirect STDERR to a system account, if you like.  System accounts can use the /etc/aliases to redirect to your centralized LAN email server, where you'd only need to check 1 account, not 1 account per server.

While a reboot notification isn't too sensitive, sending log files to gmail is a huge security failure.  Log files often contain very sensitive data interspersed with thousands of lines of boring stuff.

We all have different styles. Whatever works, is probably fine for a once a week thing like this.  But at google-scale, all the inefficiencies can add up.

Was this meant to be a tutorial/how-to?  There is a specific section for those in these forums.

---

