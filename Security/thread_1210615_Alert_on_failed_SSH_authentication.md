---
title: "Alert on failed SSH authentication?"
date: 2009-07-11
forum: Security
---

### Post by laeg_ on 2009-07-11
Is it possible to receive an alert when there is a failed authentication attempt as opposed to just logging it?

I had found this great guide [https://help.ubuntu.com/community/SnortIDS]("https://help.ubuntu.com/community/SnortIDS") which had me installing the LAMP suite, Snort and ACID but someone on IRC has said it would be too much overhead for my desktop edition PC?

Someone has also suggested fail2ban which I'll look at next.

I just thought there must be others here that have wanted the same utility?

---

### Post by HermanAB on 2009-07-11
No, the number of alarms will be deafening.  If SSH is running on a standard port, then you can be getting tens of thousands of failed login attempts per hour.

---

### Post by laeg_ on 2009-07-12
> **HermanAB said:**
> No, the number of alarms will be deafening.  If SSH is running on a standard port, then you can be getting tens of thousands of failed login attempts per hour.

Already have it changed to a port in the 7000-7999 range, is this wrong?

---

### Post by rossbielski on 2009-09-15
I am looking for the same type of utility as well. I haven't found any pre-written ones yet, so I'm trying to write my own. I'll post it as soon as I'm done. fail2ban is a useful program, however. I don't remember it actually having an on-screen or in-ear alert option, but nonetheless it is a neat utility.

---

### Post by TuckLive on 2009-09-15
Look at [[COLOR="Blue"]OSSEC[/COLOR]]("http://www.ossec.net/").  Simple app with email alerts built in.

---

### Post by rossbielski on 2009-09-16
> **rossbielski said:**
> I am looking for the same type of utility as well. I haven't found any pre-written ones yet, so I'm trying to write my own. I'll post it as soon as I'm done. fail2ban is a useful program, however. I don't remember it actually having an on-screen or in-ear alert option, but nonetheless it is a neat utility.
Alright finished. Its very basic but it does the trick, edit it as you like. Here is the[COLOR=Red] [link]("http://brassmonk.com/scripts/alert")[/COLOR] to it.
I used the following [COLOR=Red][wav]("http://www.franksradio.net/startrek/sounds/COMPUTER-Access%20Denied.wav")[/COLOR] for the alert sound, and renamed it denied.wav. You will have to have mplayer installed for the sound in the script to work, however. Place the shell script in your crontab and set it to go off every minute and you should be good. It however only goes off if there was an invalid login name used. I'll update it for valid names maybe later but hopefully you get the jist. I got some useful hints for the script from this [site]("http://www.programva.com/en/linux-tips-and-tricks/196-monitor-your-authlog-check-illegal-attempts"), so check it out for more elaborate filters.

---

