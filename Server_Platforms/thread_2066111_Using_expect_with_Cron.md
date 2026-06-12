---
title: "Using expect with Cron"
date: 2012-10-03
forum: Server Platforms
---

### Post by jonobr on 2012-10-03
Hi 

I have not done a lot with Expect, but I am hoping someone can figure if I am doing something that should not be done here or if I am misusing cron.

I have written an expect script to extract info from a non-snmp capable device.

The expect script logs into my target via ssh , runs a few commands here and there, gets usage, users, active sessions and so on and quits. 

When I run it it works fine, grabbing the info I need.
I can also then pipe to tee and it captures in a file for me.
This all seems to work well.

I then try and be a smarty pants and place it in cron to run twice every hour
I have a few of these scripts to a few devices so have a few more entries in cron, but here is one example.

```
8,38 * * * * $HOME/scripts/script.exp | tee -a $HOME/stats/`date +\%H\%M_\%m\%d_\%Y_device`.log 2>&1 
```


The file is created. 
However, Im seeing some files truncated like the thing quits before its done.
I would think its a timing or matching thing in expect, but this only happens when I place in cron
I tried placing in sleeps and different expect criteria but it always stops at the same point.


Am I misusing expect or cron here? Is there something I am not doing in Cron that I should be doing? Is there something in my statement that wrong? Is it some idiosyncrasy with cron I'm not aware of?



Thanks a mill

jonobr

PS 10.04 LTS , and now as I write, Im thinking of upgrading just to see if its that!

---

### Post by LHammonds on 2012-10-04
Your script may not be finding the programs.  You might need to set a path in your crontab.  Look on [this page]("http://www.hammondslegacy.com/forum/viewtopic.php?p=261&sid=651d038cbeccf6184b8e1b7d306ef712#p261") for an example of how I manage a crontab schedule.

Also, are you checking return codes from the programs your scripts are calling?  Those codes can get you key information on what is going wrong.

Example:
```

aptitude safe-upgrade --assume-yes --target-release `lsb_release -cs`-security >> ${LOGFILE} 2>&1
ReturnCode=$?
if [[ "${ReturnCode}" -gt 0 ]]; then
  ErrorFlag=8
  echo "Script failed.  aptitude return code is ${ReturnCode}" | tee -a ${LOGFILE}
fi

```

---

### Post by jonobr on 2012-10-04
Hi LHammonds

Thanks for the response,

Its running the program alright as the files are created and those files are either fully populated or half populated with he data I need.

Im not sure its a return code thing but that's something I think I should look at,

thanks for the pointer!!


Jonobr

---

### Post by koenn on 2012-10-04
tee is for duplicating output, i.e. both to your screen and to a file.

So why you need that in a cron job ? 

if nothing else, it makes the cron job line needlessly complicated; you could just dump the output in a file. 
Not sure if this has anything to do with the problem you're describing, but weeding out the cruft certainly won't harm.

Also, ssh + expect is a bit silly, as ssh has built-in capabilities for passwordless logon. [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys) (But maybe that's not possible with the device in question)



> 
it always stops at the same point.
and what point is that ?

---

### Post by jonobr on 2012-10-04
Hey Koenn


You may have a point there, 

Let me try redirection in Cron and see if that works

Thanks!!

Jonobr

PS- I cant use keyless as the target device is a vxworks box that wont let me copy across or insert a public key..

---

### Post by jonobr on 2012-10-29
Hello


I had two main problems with my expect script and cron.
One was using tee which koenn pointed out was incorrect.

The second thing that got me was that I was using an incorrect escape from my script that caused it to hang.

When I closed the session I spawned it seemed to tick along a lot better.

Thanks all for your help!!

Jonobr

---

