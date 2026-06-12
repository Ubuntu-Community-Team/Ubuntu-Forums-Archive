---
title: "Ubuntu server 16.04 dropping out"
date: 2016-06-24
forum: Server Platforms
---

### Post by trygaba on 2016-06-24
I have problem with my server dropping out from network few times a day. I have to reset it via power button because can't connect putty etc. anymore. After reset everything works fine. I'm running Ubunut 16.04 LTS (GNU/Linux 4.4.0-24-generic x86_64) running samba,  mysql, apache2, ts3 server and nextcloud(fail2ban).

---

### Post by TheFu on 2016-06-24
Can you connect to the console and look at the log files?
If not, guess you have to physically boot off alternate media, mount the storage and look at the log files that way. Could be almost anything and we need more data to head in any direction.  

HW fault - dying NIC, flaky PSU, interactions from other failing components (I've seen a failing GPU do this).
Bad networking - cables, switch ports, wrong routing.
Corrupted drivers for the NIC.
Bad NIC firmware - lots of off-brand NIC chips seem to have issues.  Even the standard Intel PRO/1000 sometimes has issues with SIP traffic causing a network lockup, though I haven't heard/seen that in about a decade.

Anyway, without looking at the logs - know hope of figuring this out.

---

### Post by trygaba on 2016-06-24
> **TheFu said:**
> Can you connect to the console and look at the log files?


I can connect with log files after I manually boot computer by pressing power button. Which log should I look at I can post them here?

---

### Post by TheFu on 2016-06-24
> **trygaba said:**
> I can connect with log files after I manually boot computer by pressing power button. Which log should I look at I can post them here?

That won't work. The most important HW logs are overwritten at every boot.  **Must boot from alternate media** so the logs aren't touched after a crash/lockup.

If you post any logs, post only the relevant parts and use *code tags*. Posting lots of unimportant things isn't good.

---

### Post by trygaba on 2016-06-24
I tried to look various logs but didn't find anything suspicious. I have no idea what I should be even looking for. When server drops out I can't for example ping it from router etc.

---

### Post by TheFu on 2016-06-24
Sorry - I've been pointed a few different people at their log files recently - thought I'd included some links for you (the Adv reply pg doesn't let me see the conversation).

* ubuntu log files: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
* [https://www.howtoforge.com/tutorial/logwatch-installation-on-debian-and-ubuntu/](https://www.howtoforge.com/tutorial/logwatch-installation-on-debian-and-ubuntu/)
* [https://unix.stackexchange.com/questions/181067/how-to-read-dmesg-from-previous-session-dmesg-0](https://unix.stackexchange.com/questions/181067/how-to-read-dmesg-from-previous-session-dmesg-0) - looks like you don't need to boot from alternate media.

The short answer AFTER YOU READ THOSE ... is **egrep -i error /var/log/dmesg***.  Do something like that for each log file.  For example:
```
$ egrep -i error dmesg*
dmesg:[   20.075082] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
dmesg.0:[   22.478869] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro

```
Nothing bad there.  Checking a few other log files on the same box:
* nothing in syslog
* /var/log/fail2ban.log - had a few entries - someone trying to brute force into the machine.
* kern.log - full of stuff that looks bad. ATA bus error - either a failing disk or bad cable or bad controller. I need to research that ASAP.

Thanks for making me look at my log files.

**Update**
Ok ... my last Seagate disk is starting to fail. The other one (I always buy HDDs in pairs), failed 18 months ago 367 days after purchase. Seagate goes into my NEVER AGAIN vendor list for cheap desktop disks.  Oddly, I have some 320G seagates still going strong here 10+ yrs after purchase. It is only the 750G and larger with this design flaw.   Happy I have know-I-can-recover versioned backups. On that box, think they are 90 days.

---

### Post by SeijiSensei on 2016-06-24
See if you can force it to stay up with periodic pings of your router.  From the prompt run this  command:
```
ping -c 99999999 -i 15 ip.addr.of.router >> /var/log/pinglog &
```
That will ping the router once every fifteen seconds and write the results to /var/log/pinglog.  By including the ampersand at the end, it will run in the background for 99999999 times.

---

