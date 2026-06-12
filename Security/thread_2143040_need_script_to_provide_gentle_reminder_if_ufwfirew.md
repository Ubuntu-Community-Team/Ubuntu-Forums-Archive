---
title: "need script to provide gentle reminder if ufw/firewall is not enabled"
date: 2013-05-07
forum: Security
---

### Post by thaitang on 2013-05-07
I use dial-up/gprs internet at home, and so it is not always on. I want a script that checks whether ufw (firwall) is active when I am connected to the internet, providing a gentle reminder (notify-send would suffice) if not.

I came accross this command that looks promising, while googling for something suitable:
```
 "--session-command=/etc/init.d/iptables status" ; status=$? ;
```
which of course if I add in:
```
if [[ $staus != 0 ]] ; then notify-send "blah blah blah" ;
```
would give me the second part of the script I have in mind, except when I change 'ip tables' to 'ufw' and run the command as sudo I get the follow error:
```
 sudo: invalid option -- '-'
```
Is '--session-command=' not a command recognized bash, or an option not available in ubuntu? If not can anyone help me out with the equivalent bash/ubuntu command to check the status of the firewall?

---

### Post by papibe on 2013-05-07
Hi thaitang.

Could you post the actual code that leads you to that error? 

Regards.

---

### Post by schragge on 2013-05-07
Well, --session-command is an option to [su]("http://linux.die.net/man/1/su") (not the version in Ubuntu). To check if *ufw* is active, I'd just parse the output of *ufw status*
```

if sudo ufw status | grep -q inactive$; then
  # do something about it
fi

```

---

### Post by thaitang on 2013-05-07
> [COLOR=#000000]Could you post the actual code that leads you to that error?[/COLOR]
```
 01:55 bin $ sudo --session-command="/etc/init.d/iptables status" ;
sudo: invalid option -- '-'
```
But I figured out another way by just querying ufw with its own "status" command.
```
 #!/bin/bash

sudo ufw status verbose > ~/tmp/ufwStat
ufwStat=$(echo `sed -n '1p' ~/tmp/ufwStat`) #|sed -r 's/^Status:[ ]{0,}(.*)[ ]{0,}$/\1/')
#echo "ufwStat: $ufwStat"
if [[ "$ufwStat" != "Status: active" ]] ; then
    notify-send "WARNING: ufw is not enabled." -t 2100
 fi
rm ~/tmp/ufwStat
```
But this command requires sudo, and ideally I would just like the check to occur whenever an internet connection is established, and if ufw is enabled (99% of the time), remain quiet. Is there a way to run the status query on ufw without needing sudo?

And then my next question will be, how can I tell when an internet connection is established, such as when I tether my smartphone's gprs, which is only ever periodically connected?

---

### Post by schragge on 2013-05-07
> **thaitang said:**
> Is there a way to run the status query on ufw without needing sudo?Invoke it from */etc/rc.local*

---

### Post by thaitang on 2013-05-07
> Invoke it from /etc/rc.local
I know very little of kernal inner-workings, so I may be totally out to lunch here, but I thought rc.local file was just for processes that needed to be run during start-up and shut-down, which if that is the case, I need this script to run whenever a network connection is detected/made.

---

### Post by papibe on 2013-05-07
Thanks.

I would recommend taking the sudo out the script, write your script assuming is being run as root, and using sudo to call the script instead.

For instance:
```
#!/bin/bash
ufw status | grep inactive &> /dev/null
if [ $? = 0 ]; then
    notify-send "WARNING: ufw is not enabled." -t 2100
fi
```
and the script would be called like this:
```
sudo /path/to/myscript.sh
```
If you'd like to monitor the status all the time, you can also run this in a loop:
```
#!/bin/bash
while true; do
    ufw status | grep inactive &> /dev/null
    if [ $? = 0 ]; then
        notify-send "WARNING: ufw is not enabled." -t 2100
    fi
    sleep 60s
done
```
Then you could left the program run on the background:
```
sudo /path/to/myscript.sh &
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by Lord_Paradox on 2013-09-01
I had this same issue, for me this was irritating because this is running on my home router and someone would reboot the machine then my wife would be calling me saying "the internet" was not working. I would have to login and start UFW - pain in my ****.

Using this thread, and a few others I have made a script and adjusted CRON to check the UFW status every minute and start UFW if it is not active. Thus solving my problems and ending the non-working internet problem :)

Here is exactly how I did it for those who are still plagued by this problem or end up on this thread like I did :)

NOTE: I did this sudoed as root so you want to start out with:
sudo su

Step 1 - Create your UFW_start.sh and UFW_check.sh (you could probably do this in 1 script but I did this quick and easy)

UFW_start.sh - (Yes I KNOW UFW asks you to confirm y/n when enabling just hang in there)

#!/bin/sh
## Start Firewall
ufw enable

UFW_check.sh - Checks the status, if it is inactive the script runs the above start script and answers YES to any questions (told you I would deal with that)

#!/bin/sh
if sudo ufw status | grep -q inactive$; then
        yes | sh /sbin/UFW_start.sh
fi

Step 2  - edit crontab and set file permissions

BUT WAIT that's not it, you need to make an adjustment to your crontab and add this in as well as set permissions on the files.
I put my files in /sbin/ you can put them where you like.

chmod 755 /sbin/UFW_check.sh
chmod 755 /sbin/UFW_start.sh

Now we need to make sure the crontab for root is setup with the correct path, this is important because even though we are running the crontab for root it
can loose its PATH and running the script will fail

Add this to the crontab

crontab -e (I use vi you can use nano - whatever)

#Set the shell for cron to use sh and give it a full path
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

#Check script - sends output to dev/null runs every minute
* * * * * /bin/sh /sbin/UFW_check.sh >/dev/null 2>&1

do a :wq and you are all set

To test this out all you have to do is sit at the command line and do a ufw disable then wait 1 min and do a ufw status to make sure it 
started up.

Did all this about 30 minutes ago so thought I would share before I forgot ;)

Hope that helps and makes someones day better.
Lord Paradox

---

