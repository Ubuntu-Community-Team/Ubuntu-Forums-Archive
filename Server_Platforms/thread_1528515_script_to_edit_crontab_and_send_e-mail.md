---
title: "script to edit crontab and send e-mail"
date: 2010-07-10
forum: Server Platforms
---

### Post by hellarough on 2010-07-10
Ok, not sure if this belongs here but since I want to run it on my server (ubuntu 10.04) I am posting here. 

What i want is to be able to send myself/family/friends reminder e-mails (and more importantly texts *phonenumber*@*carrier.com*) for randomly occuring events at specified times. 

Right now I have two commands that can hit my phone/e-mail account...
```

echo "message" | mail email@example.com

OR

mail -s 'subject' -u localuser email@example.com < /dev/null

``` 

but, I have no way actually scheduling the time to send. I am thinking that cron is the way to go but I would like to hear some input on this idea. Thanks in advance!

---

### Post by hellarough on 2010-07-11
Inches away but still need the help of a scripting expert...
I have two scripts and an alias

mailsender.sh
```
#!/bin/sh
echo $2 | mail $1
exit
```
mailscheduler.sh
```
#!/bin/bash
echo "/home/user/mailsender.sh $1 $2" | at $3
exit
```
alias
```
alias remind='/home/user/mailscheduler.sh'
```
So in a terminal I type something along the lines of..
```
remind email@example.com "message" "10:00pm today"
```
my only problem is that the "message" must be one_long_string_like_this otherwise it is truncated to the first word only. Since I am a n00b, and my efforts have been useless, I need help modifying my script(s) to keep the message in tact.

oh and if i combine the scripts (as below) so there is no weird variable stuff, the system sends me the email immediately
```
echo $msg | mail $email_addy | at $given_time
```

---

### Post by CannibalZerg on 2010-07-12
mailsender.sh
     
```
#!/bin/sh
echo [COLOR=Red]"[/COLOR]$2[COLOR=Red]"[/COLOR] | mail $1
exit 

```mailscheduler.sh
```

#!/bin/bash
echo "/home/user/mailsender.sh $1 [COLOR=Red]\"[/COLOR]$2[COLOR=Red]\"[/COLOR]" | at [COLOR=Red]"[/COLOR]$3[COLOR=Red]"[/COLOR]
exit

```Now try to run
```
remind "It works!!!!" "now +1 minute"
```It doesn't work, due to exclamation sign(s).
You should use single quotes instead double quotes for messages with exclamation singns.
```

remind [EMAIL="email@example.com"]email@example.com[/EMAIL] 'Finally it works!!!' "10:00pm today"

```See [http://mywiki.wooledge.org/BashPitfalls](http://mywiki.wooledge.org/BashPitfalls) pp 2; 23 for details.

---

### Post by hellarough on 2010-07-12
Thanks for the reply, I will try that out when I get home!

---

### Post by hellarough on 2010-07-12
Zerg, I tried your edits to the scripts (BTW, thanks for that link, it was very informative!) and they undo the message problems however, it sends the email immediately now...just as if I had put the scripts together for a command like so

```
echo $msg | mail $email_addy | at $given_time
```

---

### Post by hellarough on 2010-07-12
> **hellarough said:**
> Zerg, I tried your edits to the scripts (BTW, thanks for that link, it was very informative!) and they undo the message problems however, it sends the email immediately now...just as if I had put the scripts together for a command like so

```
echo $msg | mail $email_addy | at $given_time
```

I am guessing that some sort of syntax problem is keeping the scheduling from happening but am unsure how I would troubleshoot what is happening since there is no output from the terminal...

---

### Post by CannibalZerg on 2010-07-13
**hellarough**,  "at" expect command from standard input (not result of previous command) , in your case "mail" command execute immediately and sends its result to "at".

If you want "one-line" command, just combine your scripts together:
```

#!/bin/sh
#$1 - E-mail
#$2 - message
#$3 - moment

echo "echo [COLOR=Black]\"[/COLOR]$2[COLOR=Black]\" | mail $1[/COLOR]" | at [COLOR=Black]"[/COLOR]$3[COLOR=Black]"[/COLOR]

```

---

### Post by hellarough on 2010-07-13
**CannibalZerg**, thanks for all your help and explanations. I finally got it working and appreciate your patience. My script is exactly as you said...

```
#!/bin/sh
#$1 - E-mail
#$2 - message
#$3 - moment

echo "[COLOR="Red"]echo \"$2\" | mail $1[/COLOR]" | at "$3"
```

I didnt realize that I was putting the results of mail command to the "at" function, I should have looked at my scripts/commands closer...I knew it was something stupid that I was overlooking.

The cool thing is now that I have it working I can set my aliases like so...
```
alias remind='/path/to/script.sh'
alias remindme='/path/to/script.sh myemail@mail.com'
alias remindmobile='/path/to/script.sh digits@mobile.gateway.com'
alias remindjoe='/path/to/script.sh joe@mail.com'
```

messages to common contacts are now

```
remindme 'message to be sent!' "moment"
remindjoe 'message to be sent!' "moment"
```

while not so common reminders are

```
remind email@example.com 'message to be sent!' "moment"
```


Then scheduling a mass reminder to say friends and family becomes a matter of generating a list of addresses and writing a script to iterate through them with the above command. (sounds like I have my next script to write!)

---

