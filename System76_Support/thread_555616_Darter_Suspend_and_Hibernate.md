---
title: "Darter Suspend and Hibernate"
date: 2007-09-20
forum: System76 Support
---

### Post by gaussian on 2007-09-20
It's been over a month that I received my Darter Ultra (new version) and I am generally 99.999% satisfied. System 76 service (this forum and email support) have been great and the machine is really cool. And unlike for some of the participants in the forum, the battery monitor seems to work perfectly after the System 76 update.

Two minor issues (Suspend and Hibernate related):

1) Suspend and keyboard. Sometimes after coming out of Suspend my machine does not accept any keyboard input (cannot type my password into the password box). Touchpad works, but that does no good (only way out seems to power switch). I also cannot get into virtual terminal (CTRL-ALT-F1) nor can I restart X (CTRL-SHIFT-Backspace or was it CTRL-ALT-backspace). Casually observing, it would seem that touching the keyboard while the computer is suspended or while you are waking up the computer causes this lock up. Does anyone else have this problem? Is this Ubuntu or Bios-related or something else? This is a minor issue, given that if you don't touch the keyboard I don't get these lock ups.

2) Sometimes after Suspend and Hibernate the wireless does not come up, either requiring restarting X or sometimes even booting up machine. Is this happening to others?

---

### Post by thomasaaron on 2007-09-20
Regarding the keyboard freezing problem, that is interesting. I've not noticed that one, but I'll try it out.

Regarding the wireless problem, there is probably already a fix for that one in launchpad. I think the DarU1 had a similar problem that we fixed. My concern about implementing the fix on the DarU2 is that you say it happens "sometimes." Intermittent stuff is difficult. But we can do some testing and see if we can narrow it down to a specific set of circumstances.

I'd file bug reports on these so that we can start testing them.

---

### Post by gaussian on 2007-09-20
Ok, I will play with Suspend and Hibernate tonight (or over the weekend at the latest) and file a bug report. Thanks!

---

### Post by gaussian on 2007-09-20
I have now spent better part of tonight trying to replicate the keyboard freeze. Cannot do it at the moment. But lock-up has happened to me before (several times, I am not making this up...). So it is clearly intermittent. Not ready to file bug report yet.

I managed to get all sort of other erratic behavior out of going constantly  in out of suspend: alsa crashing (once),  network (wireless) not coming up (once), suspend not working (instead of suspend, message "Computer failed to suspend", once) and machine getting stuck on a reboot (might or might not be suspend related) after all this suspend testing. So it seems that suspend can cause random problems.

---

### Post by shaft350x on 2007-09-27
In regards to your issue with the keyboard not responding, I believe that this is an Ubuntu problem and not necessarily a System76 issue.  I have Ubuntu 7.04 and Ubuntu Studio 7.04 installed (and also WinXP SP2) on an HP Pavilion zv6000, and have also experienced the occassional keyboard malfunction.  Mostly it was when I came back from a locked screen since I always had difficulty with suspend and hibernate so I don't use them.

---

### Post by gaussian on 2007-09-27
> **shaft350x said:**
> In regards to your issue with the keyboard not responding, I believe that this is an Ubuntu problem and not necessarily a System76 issue.  I have Ubuntu 7.04 and Ubuntu Studio 7.04 installed (and also WinXP SP2) on an HP Pavilion zv6000, and have also experienced the occassional keyboard malfunction.  Mostly it was when I came back from a locked screen since I always had difficulty with suspend and hibernate so I don't use them.

I have continued to experience them every once in awhile (at least once since my original post). In general I have experienced some unexpected behaviors coming out of suspend/hibernate, like I mentioned in the original post. This is really not a big issue for me and hopefully some of these issues will disappear when Gusty comes out. It seems that the whole (laptop) suspend/power management is a frontier where Linux (and Ubuntu in particular) is making quick progress.

---

### Post by dahlheim on 2007-10-02
just to add (new?  the same?) more info to the knowledge base here.  new darter ultra, fresh gutsy beta install.  i've tried several things and have  been able to get the machine to suspend to ram into S3 state (very low power consumption) but it freezes entirely on resume (doesn't seem to be responding behind the black screen).  suspend to disk seems to work very nicely.

---

### Post by gaussian on 2007-10-02
As the original poster, I am giving an update. Of all suspend problems I had the most problematic has been the problem of network not coming up after suspend. All other problem seemed rare enough to not to be a real concern, but the problem of network coming up was frequent (I am using wireless).

Following the advice found on [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) (read from Suspend support) I have now added the scripts to stop and start network manager to /etc/acpi.

I can report that at least for last 24 hours I have not been able to get any problems with network not coming up after suspend (I am using Feisty). If this turns out to be the case and this fixes the network  problem I am really happy.

---

### Post by dahlheim on 2007-10-02
> **gaussian said:**
> As the original poster, I am giving an update. Of all suspend problems I had the most problematic has been the problem of network not coming up after suspend. All other problem seemed rare enough to not to be a real concern, but the problem of network coming up was frequent (I am using wireless).

Following the advice found on [https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager) (read from Suspend support) I have now added the scripts to stop and start network manager to /etc/acpi.

I can report that at least for last 24 hours I have not been able to get any problems with network not coming up after suspend (I am using Feisty). If this turns out to be the case and this fixes the network  problem I am really happy.

are you getting out of an S3 suspend state (i.e. very low power consumption, green LED on front of machine and blue one on power button flashing), or using the (default for this machine w/feisty install) "less deep sleep" mode (not sure of the terminology here), which blanks the screen and does some power saving maneuvers but not the flashing etc. i mentioned?

---

### Post by gaussian on 2007-10-02
> **dahlheim said:**
> are you getting out of an S3 suspend state (i.e. very low power consumption, green LED on front of machine and blue one on power button flashing), or using the (default for this machine w/feisty install) "less deep sleep" mode (not sure of the terminology here), which blanks the screen and does some power saving maneuvers but not the flashing etc. i mentioned?

That was a really good question and I needed to get back to my machine (which is usually home) to test that. It is the default state that works for me ("less deep sleep"). 

But inspired by your question I did:
sudo -s
echo -n mem > /sys/power/state

And got the effects you were describing (as far as blinking lights go). There was unfortunately nothing short of keeping the power button pressed down to get me out of that mode.

I am pretty happy with the "less deep sleep" mode, since I have the computer plug to a power outlet whenever I am not using it. Off course getting s3 to work properly would be cool, but the current mode does what I need: locks the screen and cools down the computer (this I guess is good for durability?). Let me (and all of us) know if you have any progress getting them work Gutsy. 

In any case I highly recommend putting those small scripts to /etc/acpi to anyone having problems with network after suspend and hibernate.

---

### Post by gaussian on 2007-10-02
> **dahlheim said:**
> are you getting out of an S3 suspend state (i.e. very low power consumption, green LED on front of machine and blue one on power button flashing), or using the (default for this machine w/feisty install) "less deep sleep" mode (not sure of the terminology here), which blanks the screen and does some power saving maneuvers but not the flashing etc. i mentioned?

Played with it little more. Setting ACPI_SLEEP_MODE=mem in /etc/default/acpi-support causes the problems you were describing, while ACPI_SLEEP_MODE=standby (s1 sleep) works well. And this is in Feisty.

---

### Post by dahlheim on 2007-10-02
> **gaussian said:**
> That was a really good question and I needed to get back to my machine (which is usually home) to test that. It is the default state that works for me ("less deep sleep"). 

But inspired by your question I did:
sudo -s
echo -n mem > /sys/power/state

And got the effects you were describing (as far as blinking lights go). There was unfortunately nothing short of keeping the power button pressed down to get me out of that mode.

I am pretty happy with the "less deep sleep" mode, since I have the computer plug to a power outlet whenever I am not using it. Off course getting s3 to work properly would be cool, but the current mode does what I need: locks the screen and cools down the computer (this I guess is good for durability?). Let me (and all of us) know if you have any progress getting them work Gutsy. 

In any case I highly recommend putting those small scripts to /etc/acpi to anyone having problems with network after suspend and hibernate.

my (partner's, but i've been doing the dirty work, including encouraging him to buy one) machine is a new darter ultra also.  executing the default gutsy acpi suspend script brings the machine down to an S3 state successfully, but pressing the power button briefly to get back out wakes the machine up to a frozen state.  this occurs despite many different potential fixes i have found in various forums (adding kernel boot parameters, altering /etc/default/acpi-support variables).  s2ram (uswsusp) with all command line parameter permutations does the same thing.  the battery monitor applet behaves quite randomly.

on the bright side, compiz works "out of the box" with gutsy beta, the webcam works well, the mic and sound work (except for system sounds, which i think will be fixed soon), headphone jack works, sd card reader works, and hibernate works.

---

### Post by thomasaaron on 2007-10-03
Under Feisty, the DarU2 will not resume from the deeper sleep. 
Sounds like it is the same under Gutsy.

---

