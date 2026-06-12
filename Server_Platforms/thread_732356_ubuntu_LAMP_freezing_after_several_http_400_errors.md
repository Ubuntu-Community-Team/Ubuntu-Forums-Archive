---
title: "ubuntu LAMP freezing after several http 400 errors"
date: 2008-03-22
forum: Server Platforms
---

### Post by heyasam on 2008-03-22
Hi All,

As in title, I'm getting several freezes lately requiring a hard reboot, which is difficult as the server is in a locked server room!  Just before the system freezes, on most occasion, I have been receiving several http 400 errors emailed to me;

You're speaking plain HTTP to an SSL-enabled server port.

Instead use the HTTPS scheme to access this URL, please.

    Hint: https://myservername.lan/">[https://myservername.lan/](https://myservername.lan/)

Any suggestions, even what logs I should be looking at and looking for greatly appreciated.  My buddy reckons it could be my hardware is old...

---

### Post by craigp84 on 2008-03-23
Hi Heyasam,

You've got a real cracker here :-)

When you say freeze, is it a real proper hard lockup? Do you get an oops on the console? What do you see on the server's console after lockup?

Hard lockups tend to be either drivers (most common) or hardware (relatively rare). These aren't the only 2 causes, but in my experience, they are most common.

What are the patterns leading up to the lockup? Increased CPU or memory usage? What's talking to your webserver at the time? Have a look in the httpd logs (/var/log/apache/). What is being requested from your webserver at these times? Is there a pattern you can identify (common IP address in the logs, common URI being requested? etc.)

Assuming there's nothing in the logs, or on the console, or in the behaviour of the server before the crashes, youronly option is to increase monitoring in order to try and catch the cause.

Look into setting up a "tcpdump" session to record all the network traffic.

Consider turning on auditing (install the userspace tools, kernel side already in the kernel with ubuntu) to track the processes and what they're doing.

I'm afraid there's no silver bullet for this type of issue, but they are by far and away the most interesting type of problem. Secretly every time the phone rings i hope it's a situation like this :-)

-c

---

### Post by ikonia on 2008-03-23
your getting 404 errors because the server is down/unavailable.


look in the syslog, look in the http access and error log,

look at the output of dmesg straight after boot up to see if there is anything obviously wrong

if require enable sysrq and net-dump to get crash information.

---

### Post by heyasam on 2008-03-23
Thanks for the ideas so far guys, I will be able to investigate more on Tues and Weds.

Just a little further to add that I forgot to put in the initial post, is that the 400 http errors are coming from remote ip 127.0.0.1

My server room guy says it was 'frozen'.  I will ask him for more details this time.

Also have been running pretty solid for over a year, and have only installed mutt recently so worried that this may suggest a security compromise...

---

### Post by ikonia on 2008-03-26
127.0.0.1 is not a remote ip address, it's your loopback address

---

### Post by heyasam on 2008-03-27
After an attempt to hard reboot the machine ended in looping through the BIOS screens, decided must be hardware and bought new box.  Chucked old hard drive in new box.  Just got it up after a few teething issues - see  [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148).  Hopefully no more freezes and 400 errors but if the problem continues you will definitely hear from me again!  Thanks again all.

---

### Post by heyasam on 2008-03-29
Ok, I no longer am freezing up now that I'm running new hardware with the same old harddrive plugged in.

However, I'm still getting intermittent emails (11 or so today on three different occasions) telling me http 400 error from (loopback) 127.0.0.1.  I get these emails from my custom apache error page that emails me any time I get a 404, 400 etc.

Hmm so maybe this is an apache problem or something conflicting?? No idea.  Will poke around in  the logs that I know of when I have the chance.  

Don't think this is at all related, but I get the following warning when doing a graceful reboot of apache2:
The Alias directive in /etc/apache2/apache2.conf at line 129 will probably never match because it overlaps an earlier Alias.
line 129; Alias /icons/ "/usr/share/apache2/icons/"

Any ideas appreciated

---

