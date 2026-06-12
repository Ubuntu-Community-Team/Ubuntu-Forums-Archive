---
title: "fuser forking uncontrollably in cron job"
date: 2011-10-16
forum: Server Platforms
---

### Post by Will Shackleton on 2011-10-16
Hi

On my Ubuntu Server 11.10 box, several thousand fuser processes are being created every half an hour. (This didn't happen in 11.04.) I traced the problem back to the cron job '/etc/cron.d/php5', which contains the entry:
```
[ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete
```
I think this removes old PHP sessions.

This is an extract from 'ps aux':
```
root      1636  0.0  0.0      0     0 ?        Z    23:51   0:00 [fuser] <defunct>
root      1637  0.0  0.0      0     0 ?        Z    23:51   0:00 [fuser] <defunct>
root      1638  0.0  0.0      0     0 ?        Z    23:51   0:00 [fuser] <defunct>
root      1639  0.0  0.0      0     0 ?        Z    23:51   0:00 [fuser] <defunct>
(many, many more...)
...

real    0m10.832s
user    0m2.796s
sys     0m4.952s
```
There are thousands of these, but they do disappear eventually. Once the cron job exits, all the defunct processes are cleaned up, presumably by init.
This also puts my system load up to about 2 every half an hour.

I could remove the cron job, but I'd imagine PHP sessions wouldn't be cleared up then. I couldn't find any bugs to do with fuser, but it could be perhaps to do with 'find' calling fuser.

Attached is a graph showing load average of this server.

Any ideas on what to do?

Thanks,
Will

---

### Post by Hizeh on 2011-10-16
I have the exact same problem.  Upgraded Ubuntu 11.04 -> 11.10 then I started getting the error "Failed to fork: Cannot allocate memory" at random times.  When I looked into it I found the exact same issue Will describes.

I disabled that cron job to fix it for now..

---

### Post by RastaFeri on 2011-10-17
i have exactly the same problem too (11.04 -> 11.10)

---

### Post by devilmastah on 2011-10-17
Registerd to confirm this bug :)
Updated two servers both have the issue.
Also: testing with disabled cron on one server as i speak will report back!


EDIT:
So far: disabling the cron did the trick.
Now trying new version of php

---

### Post by Hizeh on 2011-10-18
Did updating php5 fix it?

---

### Post by worley on 2011-10-18
I've just upgraded 35 servers from 11.04 to 11.10 and we only have one server that has this issue.
Running PHP-fpm as with all the others, and it's doing exactly as described above.
I've seen 18,000 or so defunct fuser processes within a few hours of upgrading the server.
This is with the new PHP security release that came out today.

---

### Post by worley on 2011-10-18
# ps -ef | grep fuser|wc -l
29751

It's getting pretty high now, that is with an uptime of 1hr 19 min
I've disabled the script in /etc/cron.d/php5 temporarily.

---

### Post by devilmastah on 2011-10-18
> **Hizeh said:**
> Did updating php5 fix it?

Nope it didnt :(
Waiting for a patch

---

### Post by matt_symes on 2011-10-18
Hi

> I couldn't find any bugs to do with fuser, but it could be perhaps to do with 'find' calling fuser.Total shot in the dark but do you still have problems if you edit the cron job to use

```
lsof -t {}
```instead of 

```
fuser -s {}
```They both return pids so i assume they would perform the same function and an error code of 1 on failure; 0 on sucesss.

From man lsof

> -t       This option specifies that lsof should produce terse output with process identifiers only and no header - e.g., so that the output may be piped to  kill(1).
                This option selects the -w option.From man fuser

> fuser  displays  the  PIDs  of processes using the specified files or file systems.Might be worth a try ?

EDIT: You might have to pipe stdout and stderr to /dev/null.

Kind regards

---

### Post by Hizeh on 2011-10-19
I tried matt_symes fix and the "lsof -t" does not fork uncontrollably like fuser was doing.

But, I'm not sure how to check if it is actually clearing old PHP sessions.

---

### Post by matt_symes on 2011-10-19
Hi

> **Hizeh said:**
> I tried matt_symes fix and the "lsof -t" does not fork uncontrollably like fuser was doing.

But, I'm not sure how to check if it is actually clearing old PHP sessions.

Not so much a fix; more of a stab in the dark [-o<

Can you post your cron job script so i can take a look ?

Kind regards

---

### Post by bigchirv on 2011-10-20
To find the file use the command below:

```

find /etc/cron.* -type f -exec grep -Hi fuser {} \;

```

/etc/cron.d/php5 is the file to edit.

EDIT: worley already posted the file name in his latest post.

---

### Post by grazer on 2011-10-20
We found the same problem on 11.10 and the solution is to take out the "fuser" part.  

This is the content of /etc/cron.d/php5 on 11.10:

```
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete
```

And this is the content on 11.04:

```
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete
```

Spot the difference?

The 11.10 version runs fuser for each PHP session file,  using all the CPU when there are hundreds of sessions.   The reason it doesn't happen on 11.04, is 11.04 doesn't call fuser.

---

### Post by matt_symes on 2011-10-20
Hi

> The 11.10 version runs fuser for each PHP session file,  using all the  CPU when there are hundreds of sessions.   The reason it doesn't happen  on 11.04, is 11.04 doesn't call fuser.Interesting. Does anybody know why it was added ? Why would a process still reference the file after its supposed maximum lifetime ?

My assumption would be to deal with some edge condition because it is pretty obvious what they were trying to achieve by adding it.

Kind regards

---

### Post by HaroldS on 2011-10-21
Upgrade my server 2 days ago and got all kind of strange 'can not fork' error to.

I can confirm that I had lots of defunct fuser processes. So I changed the php5 session cleanup cron to the 11.04 version and now all is fine again :-)

---

### Post by kongo09 on 2011-11-04
It's a confirmed bug of 11.10
[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/877894](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/877894)

---

### Post by afshinm on 2011-11-17
Hi

I have this problem with my Ubuntu server 11.10 and I fixed problem by editing **/etc/cron.d/php5** and replace the codes with:

```
09,39 *     * * *     root   [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) -delete
```Now everything works fine! :)

Thanks all

---

### Post by kaliseo on 2011-12-27
I applied the afshinm modification, and it works for me too.

Thanks !

---

### Post by Stolen on 2012-01-25
I hadn't see much in the way of load issues, but I have been getting some errors from exim that may be related:
daemon: accept process fork failed: Cannot allocate memory
Which I though was weird since I never saw memory issues either.  

I had been getting some complaints about my website being down for short intervals intermittantly, but could never catch that either.

I only just caught this today after logging in and seeing the message "you have xxxx zombie processes"

I've applied the lsof/fuser switch in the cron file.  Hopefully that fixes it (and my other issues).

---

### Post by windracer01 on 2012-01-27
Just ran into this same problem today. Funny thing is I upgraded from 11.04 to 11.10 back in October and never noticed it until now. I just happened to be working on something else when suddenly I found hundreds of defunct fuser processes slowing the server down. Made the change suggested above and that seems to have helped.

---

### Post by davidparks21 on 2012-03-22
Based on a google search I found the bug below that seems to suggest this might be fixed. I wonder if afshinm's solution is still the best or if we can/should just update something to address the issue?

[https://bugs.launchpad.net/ubuntu/+source/php5/+bug/876387](https://bugs.launchpad.net/ubuntu/+source/php5/+bug/876387)

---

