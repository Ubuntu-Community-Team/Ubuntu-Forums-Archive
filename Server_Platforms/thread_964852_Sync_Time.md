---
title: "Sync Time"
date: 2008-10-31
forum: Server Platforms
---

### Post by cjwallace on 2008-10-31
Guys.

I am using ntpdate SERVERNAME to sync my time on my Ubuntu server with my Windows PDC.

It is working fine.

Is there anyway i could get it to do it every hour automatically?

Cheers

Craig

---

### Post by MJN on 2008-10-31
Before someone comes and suggests scheduling it with CRON let me tell you this is not the correct way to do it.
 
Ntpdate is intended to be run as a 'one shot' tool - by this I mean it is not meant to be run regularly. You should be using NTPD instead - this is an NTP daemon that will keep your clock in sync over the long term by making the necessary adjustments, and tiny ones at that, in order to ensure there are never any 'jumps' in time that NTPDATE could result in.
 
Mathew

---

### Post by cjwallace on 2008-10-31
Excellent. I am all for doing by the book.

Can you please let me know what i need to do

Many thanks

Craig

---

### Post by MJN on 2008-10-31
Thankfully very little!
 
1. Have a read of [http://www.cis.udel.edu/~mills/ntp/html/ntpd.html](http://www.cis.udel.edu/~mills/ntp/html/ntpd.html) to learn a little about the background as to what NTPD is and does.
 
2. Install NTPD
 
3. Configure NTPD with your desired NTP server sources. These are entered in /etc/ntp.conf. You already know yours, but others can pick one from [http://www.pool.ntp.org/zone/@](http://www.pool.ntp.org/zone/@)
 
4. That's it! (oh, you might need to restart the deamon with sudo /etc/init.d/ntp restart for the new server settings to take effect)
 
Note that, by design (and as discussed in the docs above), NTPD will make very small adjustments so don't be tempted to force a duff clock and then expect to see if suddenly fix itself - if the time is too far wrong then it assumes a severe hardware problem and will refuse to update the clock (there's no point if things are that bad). You should see occasional syslog entries so you can see it is working (and of course your clock will be bang on at all times).
 
If you want other machines to be able to use you as their time reference then ensure that UDP port 123 is open in any firewall (and forwarded in your home router if you have one).
 
I should point out that whilst NTPD is the perfect solution for your situation (i.e. an always-on server) it would still be better to use NTPDATE for clients/workstations whose machines are, say, turned on/off daily (in which case it could be run from a startup script, but not scheduled to run every hour or whatever).
 
Mathew

---

### Post by cjwallace on 2008-11-02
Thanks for the reply mate. I will take a read up on what you have posted.

Thanks again

Craig

---

### Post by jona7han on 2008-11-02
you can also monitor your ntp status using ntpq -p

---

### Post by cjwallace on 2008-11-02
Thanks mate.

How can i just check the time the server is using? on Windows i would just issue the time command.

Thanks in advance

---

### Post by jona7han on 2008-11-02
This doc [here]("http://tldp.org/LDP/sag/html/ntp-toolkit.html") has some useful commands for checking time

---

