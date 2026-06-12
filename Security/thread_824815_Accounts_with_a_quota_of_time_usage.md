---
title: "Accounts with a quota of time usage"
date: 2008-06-10
forum: Security
---

### Post by gnebro on 2008-06-10
Hi,

does anybody know if it is possible to create account with a quota of time usage? I mean, for example, an account that can login and use a pc only for 10 hours per month.

Thanks.

---

### Post by HalPomeranz on 2008-06-10
I've seen lots of threads asking for variations of this request, but as far as I know there's no built-in way of accomplishing this.  Seems like a lot of people want this feature, however, so somebody ought to think about hacking it into gdm or something.

---

### Post by brian_p on 2008-06-10
> **gnebro said:**
> Hi,

does anybody know if it is possible to create account with a quota of time usage? I mean, for example, an account that can login and use a pc only for 10 hours per month.

The football finished and I was at a loose end. You'll see the script is incomplete. Run it as a cron job.

```

#!/bin/bash

# /var/log/wtmp is rotated monthly.

# Find number of hours a user is logged on for in each session and get a
# running total.

A=$(last | grep user | awk -F"(" '{ print $2 }' | awk -F":" '{ sum += $1 }; END { print sum }')

if [ $A -ge 10 ]
   then <do something>
   else <do something else>
fi
```

---

### Post by gnebro on 2008-06-11
Hi Brian,

thanks for the script. How and where should I call it? I would like to prompt an "access denied" error message when the user try to log in and he exceed his monthly quota of time usage.

---

### Post by HermanAB on 2008-06-11
The user account parameters do have an expiry date feature.  You can use usermod to set the date on which a user account will become inactive.

See 'man usermod' for example.

otherwise, you could set the above script in /etc/cron.hourly and then disable the account when the time is up.

Another way to limit things, is with Squid-cache and Squidguard.

Hope that helps!

Herman

---

### Post by gnebro on 2008-06-11
Thanks Herman,

usermod give me the possibility to set an expire date for an account but that is not what I'm trying to achieve. I have a different problem: let’s say that I have a PC shared amongst several people. A part from the root, all the other people should be able to login and use the PC only for 10 hours per month. 

The idea to set the script in /etc/cron.hourly seems quite an interesting option, just I’m not an expert in bash scripting and I don’t know how to kick the user out from the System when he exceeded his monthly amount of hours. 

Thanks also for the tip about Squid. I’m looking into it.

---

