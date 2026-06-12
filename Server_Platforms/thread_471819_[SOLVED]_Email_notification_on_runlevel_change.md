---
title: "[SOLVED] Email notification on runlevel change"
date: 2007-06-12
forum: Server Platforms
---

### Post by vdawg on 2007-06-12
Hi guys,

I have had some experience with administering the student server at my school which is running on slackware and everytime the system was shutdown or rebooted or went on UPS power, an email was sent to pager@<domain> which was forwarded to all the admin staff.

So anyways, I was looking to setup a similar feature for my desktop at home but had no luck googling this pager service. There is commercial software available that monitors the server but I'm sure that we did not buy any such thing for the student server.

Here is an example of such an email 

```
From: pager@<domain>
Date: Tue, 22 May 2007 16:04:06 -0400
Sender: root@<domain>
To: pager@<domain>
Subject: <NAME>-PAGE
Message-ID: <*>
User-Agent: nail 10.7 3/19/04
MIME-Version: 1.0
Content-Type: text/plain; charset=us-ascii
Content-Transfer-Encoding: 7bit

Rebooted, now online
```

cheers!

---

### Post by tribaal on 2007-06-12
I'd go about doing this using the "natural" init scripts:

Have a script that sends out emails, and put it in /etc/init.d
You can then make simlinks to your script from the various /etc/rc#.d/ directories.

Does that make any sense to you (I'm pretty tired right now)?

I'll try to give you copy/paste instructions once I have slept for a few hours :)

Enjoy :)

- trib'

---

### Post by vdawg on 2007-06-12
ok yes that does make some sense, So i create a generic script in /etc/init.d/ and then use that script with relevant messages from the /etc/rc#.d/ directories?

---

### Post by tribaal on 2007-06-12
That would be it.

You might have problems "passing arguments" with simlinks, I'm not really sure about this. 
But you get the general idea. You might need to make several scripts in /etc/init.d/ passing parameters to a "master script" once called, or figure out the current init level (parsing the output of the "init" command for example) and make your script react accordingly.

Could be a nice functionality... If you have something that works while I'm asleep please post back your solution :) Otherwise I'll try to hack something up tomorrow and let you know :)

- trib'

---

### Post by vdawg on 2007-06-12
thanks for the help - I am at work right now so will try this when I get home tonight, will keep this thread updated!

cheers!

---

### Post by craigp84 on 2007-06-13
Hi vdawg,

As a quick fix to cover when the box has been rebooted:

```

sudo crontab -e

```

Add the below line to the crontab:
```

@reboot echo "Rebooted, now online" | Mail -s "`hostname` PAGE" my.email.group@domain.com

```

As for the UPS stuff, normally you can configure that in the UPS software as with the apcupsd software for example.

Alternatively, some LOM cards with watchdog timers have the ability to mail when a machine locks up / reboots etc. Obviously that's dependant on your hardware though :-)

Hope this helps,

-c

---

### Post by vdawg on 2007-06-13
cool thanks my man, I have added that stuff to my crontab.

Just a note, I am using the ubuntu desktop distro so it uses anacron - should i be using that instead of the regular cron?

PS: I didn't even have mailx installed on my system lol

---

### Post by MJN on 2007-06-14
Anacron is more for machines that aren't on 24/7 or, specifically, machines that would likely miss out on important scheduled tasks due to being off at the set time. It tries to make sure these tasks are still executed, albeit potentially not at the time specified.

See [http://en.wikipedia.org/wiki/Anacron](http://en.wikipedia.org/wiki/Anacron) for a nice concise summary.

Mathew

---

### Post by vdawg on 2007-09-01
Hey man thanks a lot, I finally got back to this little project of mine and as it turns out - this line did the trick, but gmail was bouncing all my emails because I was mailing it directly from my system.

Anyways, once I switched to my ISP's relay, I got the email :)

Now to find out the commands for shutdown and startup!!!

thanks again!!!

> **craigp84 said:**
> Hi vdawg,

As a quick fix to cover when the box has been rebooted:

```

sudo crontab -e

```

Add the below line to the crontab:
```

@reboot echo "Rebooted, now online" | Mail -s "`hostname` PAGE" my.email.group@domain.com

```

As for the UPS stuff, normally you can configure that in the UPS software as with the apcupsd software for example.

Alternatively, some LOM cards with watchdog timers have the ability to mail when a machine locks up / reboots etc. Obviously that's dependant on your hardware though :-)

Hope this helps,

-c

---

### Post by vdawg on 2007-09-01
well the reboot command is great, but there are so such directives for shutdown.

Anyone have any idea?


PS: The reboot directive actually works everytime the server is booted not just rebooted :)
PPS: there is tribaal's solution of having scripts run at various runlevels but there should be a simpler way ;)

---

### Post by vdawg on 2007-09-02
:popcorn:

GAME OVER!

Ok, so I got in touch with the admin who built the school server and it turns out that the pager service is actually a simple mailer script and the ups monitor is the service that calls the script at various notification levels.

So anyways, I grabbed that script and decided to try out tribaal's solution and it's working like a charm :)

Here's the script

```

#!/bin/bash
#
# Pager script - send emergency emails to admin's
#
# Usage: -m 'text goes here' | -s (this grabs from stdin)
#
# apparently -r doesnt work
#
address=youremail.com
FR="your-server-name"
SJ="server-PAGE"

if [ "$1" = "-s" ]; then
        # mailx -s $SJ -r $FR $CC $address
        mailx -s $SJ $address

else
        echo "$1" | mailx -s $SJ $address
fi

```

(be sure to set the right permissions for your mailer script)

Now create the notification scripts under /etc/init.d/

/etc/init.d/notify-shutdown.sh 

```

#! /bin/sh
/path/to/pager-script "Shutting down homie!"

```

/etc/init.d/notify-reboot.sh 

```

#! /bin/sh
/path/to/pager-script "Rebooting Mayn!"

```

(Again be sure to set the right permissions : 755)

Awesome, now create the symlinks at the various runlevel directories... I just put the notifications down as 01 but you can go as far as you want until you hit the postfix shutdown script lol (on my system it is at 20)

```

root@puter:/etc/rc0.d# ln -s ../init.d/notify-shutdown.sh K01notify-shutdown

root@puter:/etc/rc6.d# ln -s ../init.d/notify-reboot.sh K01notify-reboot

```

PS: this should probably be in a howto eh?

---

