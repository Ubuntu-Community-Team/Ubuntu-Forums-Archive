---
title: "Why am I having runaway cron processes that never go away?"
date: 2010-02-10
forum: Server Platforms
---

### Post by narnie on 2010-02-10
Hello,

I have a test cron process going that has the follow result if I have MAILTO="":

```
root      1446  0.0  0.0  18708   996 ?        Ss   18:48   0:00 cron
root      3631  0.0  0.0  91236  2188 ?        S    18:56   0:00  \_ CRON
root      3632  0.0  0.0  91240  1264 ?        S    18:56   0:00  |   \_ CRON
woodnt    3633  0.0  0.0      0     0 ?        Zs   18:56   0:00  |       \_ [sh] <defunct>
root      3720  0.0  0.0  91236  2188 ?        S    18:57   0:00  \_ CRON
root      3721  0.0  0.0  91240  1264 ?        S    18:57   0:00  |   \_ CRON
woodnt    3722  0.0  0.0      0     0 ?        Zs   18:57   0:00  |       \_ [sh] <defunct>
root      3752  0.0  0.0  91236  2188 ?        S    18:58   0:00  \_ CRON
root      3753  0.0  0.0  91240  1264 ?        S    18:58   0:00  |   \_ CRON
woodnt    3754  0.0  0.0      0     0 ?        Zs   18:58   0:00  |       \_ [sh] <defunct>
root      3784  0.0  0.0  91236  2188 ?        S    18:59   0:00  \_ CRON
root      3785  0.0  0.0  91240  1264 ?        S    18:59   0:00  |   \_ CRON
woodnt    3786  0.0  0.0      0     0 ?        Zs   18:59   0:00  |       \_ [sh] <defunct>
root      4155  0.0  0.0  91236  2188 ?        S    19:11   0:00  \_ CRON
root      4156  0.0  0.0  91240  1264 ?        S    19:11   0:00  |   \_ CRON
woodnt    4157  0.0  0.0      0     0 ?        Zs   19:11   0:00  |       \_ [sh] <defunct>
root      4181  0.0  0.0  91236  2188 ?        S    19:12   0:00  \_ CRON
root      4182  0.0  0.0  91240  1264 ?        S    19:12   0:00  |   \_ CRON
woodnt    4183  0.0  0.0      0     0 ?        Zs   19:12   0:00  |       \_ [sh] <defunct>
root      4209  0.0  0.0  91236  2188 ?        S    19:13   0:00  \_ CRON
root      4210  0.0  0.0  91240  1264 ?        S    19:13   0:00  |   \_ CRON
woodnt    4211  0.0  0.0      0     0 ?        Zs   19:13   0:00  |       \_ [sh] <defunct>
root      4891  0.0  0.0  91236  2188 ?        S    19:14   0:00  \_ CRON
root      4892  0.0  0.0  91240  1264 ?        S    19:14   0:00  |   \_ CRON
woodnt    4893  0.0  0.0      0     0 ?        Zs   19:14   0:00  |       \_ [sh] <defunct>
root      5469  0.0  0.0  91236  2188 ?        S    19:15   0:00  \_ CRON

```

If MAILTO is not unset, I get:

```

root     14693  0.0  0.0  91236  1660 ?        S    Feb05   0:00  \_ CRON
root     14694  0.0  0.0  91244  1160 ?        S    Feb05   0:00  |   \_ CRON
woodnt   14696  0.0  0.0  50152  2800 ?        S    Feb05   0:00  |       \_ /usr/sbin/sendmail -i -FCronDaemon -oem woodnt
```

all accumulating.

The only way to remove them is by root killing, and some won't go away even with kill -9 (the defunct one of course)

I have an Ubuntu karmic box. Running the same thing on 2 other karmic boxs and an intrepid box and they DON'T do this.

I have bsd-mailx (depends postfix) installed for receiving the cron mails (thus sym-link sendmail to postfix).

```

$ uname -a
Linux toshiba-laptop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

```

The test crontab (no flames on running every minute, please):

```

MAILTO=""
#m 	h  	dom 	mon 	dow	command
*	*	*	*	*	/home/woodnt/bin/test_cron > /dev/null 2>&1

```

```

$ catprog test_cron 
#! /bin/bash
#

# if ! type promptYesNo > /dev/null 2>&1 ; then . /home/woodnt/scripts/misc.sh ; fi

FILE=/tmp/cron.log
TIME=`date -d now "+%m-%d-%y@%H%M%S"`
if [ ! -f $FILE ] ; then
	touch $FILE
fi

echo "Hello at $TIME" >> $FILE

```

Any clue what might be going on and how to fix it?

With thanks,
Narnie

---

