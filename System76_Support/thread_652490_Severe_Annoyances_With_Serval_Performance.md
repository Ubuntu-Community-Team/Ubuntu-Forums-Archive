---
title: "Severe Annoyances With Serval Performance"
date: 2007-12-28
forum: System76 Support
---

### Post by jdmelton on 2007-12-28
I have a Serval Performance model SER-P3, order #5348. I am running Ubuntu 7.10 with all updates.

There are three very very annoying problems with this laptop.

I have not used hibernate, I normally shutdown at the end of the day or when I am finished working on something. That means that the laptop gets booted at least once per day, sometimes more.

1. At boot, I see the Phoenix flash screen, then get an underscore. The system does not boot, and there are no error messages. I believe that Grub is not running since I do not see any of the usual messages or countdowns. To recover from this problem, I shut off the laptop, then use F2 at the next startup. I enter the BIOS setup, then just exit. From here, Grub will go ahead and run. This happens about every fourth or fifth boot. If I just shut off the start, I get the same problem. Only after entering the BIOS setup and exiting does the system go on to run Grub.

2. Occasionally, after booting, at the login screen, the keyboard does not respond and the mouse does not respond. To get around this, the only thing I can do power off. Today I had to power off three times. Each time after power off, I start and can enter BIOS with F2. Each time, I just exit without saving. So, the keyboard responds before Grub runs. Entering BIOS setup did not help with keyboard and mouse response.

3. The wireless drops a connection, then prompts me for the wep key. I enter the wep key again, and the icon shows that the wireless is trying to connect. It never does reconnect. With this, no other applications can be started. Not even the shutdown button works. I read about this on another thread, but I have not found it again. I had this happen twice at my home. My Ubuntu 7.04 desktop is also wireless, but has not exhibited this behavior. I also had this happen once at a hotel. There, the wireless lost connection, then tried to reconnect. Again, the icon shows that there is an attempt to connect in progress. No other programs could be started. Any programs currently running would respond. On both occasions, I was running gedit and Firefox. After reboot the wireless connects OK and other applications respond OK. During this problem I can switch between desktop screens.

I can't dmesg for the first one. Dmesg for the second one does not work since the keyboard does not respond. Dmesg for the third one does not work since I could not start a terminal. Perhaps there is another way to try and capture the errors?

---

### Post by tgalati4 on 2007-12-28
Run memtest from either the grub screen or from a Live CD.  Let it run for 30 passes to rule out memory.  If you get memory errors, then try reseating the RAM.

---

### Post by Rasputin_III on 2007-12-28
I have the same model S.P. and have experienced at least problems #1 and #3.

As near as I can tell, the wireless problem is with the module for our wireless chipset (by default Gutsy uses ipw3945).  One workaround is to use the iwl3945--which will be the default in Hardy--but seems to have some other issues itself.  One of the (many) reports about ipw3945 is:
[https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139080](https://bugs.launchpad.net/ubuntu/+source/linux-ubuntu-modules-2.6.22/+bug/139080)
[https://launchpad.net/ubuntu/+bugs?field.searchtext=ipw3945](https://launchpad.net/ubuntu/+bugs?field.searchtext=ipw3945) lists 92 at the moment...

I am curious to follow what they say about problem #1 as it's bit me a few times as well (with a similar frequency--maybe 1 in 5 or 6).  Sometime a ctrl-alt-del will clear whatever snag and it'll boot correctly, but a power cycle will usually take care of it the rest of the time (I don't think I've had to enter the setup utility in my case, though).

Ras

---

### Post by steveneddy on 2007-12-29
Are you guys running 32 or 64 bit?

---

### Post by Rasputin_III on 2007-12-29
I'm running 32-bit.

---

### Post by Bromo on 2007-12-30
I have a Serval as well, about the same vintage (brand new!)

For #1 and #2 - run a liveCD to see if you have any troubles.  I was thinking a memory test would be a good thing to run as well.  If the LiveCD behaves in a flaky manner, you may have narrowed it down to a hardware problem.  If the LiveCD behaves flawlessly you may only need to do a system restore!  Make note of how you run the laptop as well - if you are using it in your lap on a chair, propped up on something , flat on a table - and make sure to do that with the liveCD - because if there is something loose or intermittent, you want to give it a chance to go intermittent with the LiveCD!

For #3 - I would try for an experiment running off of wired Internet to see if you have issues with connections.  I have had no issues with running my Serval off of wireless in my house and no issues with wired.  I haven't had this computer get in the mac address database at work so I have not tried it there.

I have seen software mimic a hardware problem, but if most of your issues are happening as or before Linux loads, you may be having a hardware problem - or even a BIOS issue (!).  You can check to make sure the RAM is seated properly - which is an easy fix - if it isn't in there good and tight, it could have got loose in shipping.  After running it on a LiveCD, and figuring the RAM out, you may need to get on the phone with system76 and arrange for a RMA to be repaired (or for them to walk you through a few checks on the hardware).  It is possible there is an intermittant connection, RAM, a cable or something else.  

Hang in there, my Serval (I believe my order number was 2 ticks later than yours!) has so far been doing well - and I realized Linux has come a LONG way in the past 3 years.

---

### Post by jdmelton on 2007-12-30
Update on Serval annoyances.

A. Memtest showed no errors on 30 runs. However, after exiting memtest, the keypad and mouse did not respond. I had to power off four times. Each time, the keyboard responds to F2 or F12 keys at startup. If I press F2 at the BIOS flash screen, the BIOS setup appears. Key presses process as expected. After exiting, Grub runs and eventually I see the graphical Ubuntu login screen and hear the little drum roll. At this point, the cursor is blinking in the username box. Keyboard and mouse movement or mouse buttons do not work. The mouse pointer is on the screen, but does not move.

B. I have been using my laptop on a desk, not my lap. It is plugged in to AC power, not running off the battery.

C. The failure to load the operating system still occurs. I have a little more information about this problem. It happens during a startup, not during reboot. The times I am seeing this problem are when the computer has been powered off and allowed to set for some time (a half hour or more). The laptop has been plugged into AC power continuously. Again, what happens is I see the Phoenix flash screen, then a blank screen with a blinking cursor in the upper right hand corner. Grub does not appear to run. There are no error messages even if I leave the machine alone for 15 minutes or more.

I seem to remember a problem like this some time ago with a chipset not being initialized properly at times. I have not been able to find the web references to this type problem.

D. My serval is 32bit, an Intel Core 2 Duo T7100 1.8 GHz. It has 2 GB ram and the 512M Nvidia graphic card, not shared memory.

E. The wireless connection drop and problem starting any new application problem has not occurred since my original post.

---

### Post by jdmelton on 2007-12-30
OOPS! For C. above, that is the other upper right hand corner! (Some people would call this the upper left...)

---

### Post by thomasaaron on 2007-12-31
Next time you get as far as the (unresponsive) login screen, reboot the comuter and run: cat /var/log/messages >> ~/Desktop/messages.txt Then send me the file that it produces on your Desktop. (support(at)system76(dot)com)

---

### Post by jdmelton on 2007-12-31
I sent the file this morning.

---

### Post by thomasaaron on 2007-12-31
OK, I'll have a look. Thanks.

---

### Post by steveneddy on 2008-01-01
I'm curious to know what this issue may be.

Any answers yet, Tom?

---

### Post by jdmelton on 2008-01-01
stevenedddy,

I have been corresponding via email with Tom. He has been very quick in responding, considering the holidays! We have not resolved the issue yet, but part of that is due to me traveling for the holidays. When we get this resolved, I will be sure to post a report on this thread.

---

### Post by steveneddy on 2008-01-01
Thanks

---

### Post by ScruffyScrode on 2008-01-04
I have a serp3 model with the same problems as mentioned in the original post. Exactly the same. My order was 5159

---

### Post by thomasaaron on 2008-01-07
ScruffyScrode,

You might want to edit your post and delete your order number. It is not a good idea to post private info on the fourms, as somebody could use it to request technical support or other private info about your account from System 76.

Please send me an email detailing your problem to support(at)system76(dot)com, and I'll help you.

---

### Post by jdmelton on 2008-01-07
Update:

Since my last post, I have had several email contacts with Tom at system 76. Here is what I have tried.

A. Memory Test with 30 passes. No errors.

B. Reseat ram.

C. Inspect kernel messages (dmesg) and logs.

D. Boot with Ubuntu 7.10 CDROM.

E. Open laptop and reseat keyboard ribbon cable. While I was at it, I reseated all the other accessible connectors accessable from the bottom plates. -- No connectors were found to be loose or appeared to be improperly seated. I do not recommend this step for everyone since ribbon-style connectors and ribbons are easily damaged. (I work in the industrial controls sector at the moment and deal with these frequently.)

Results? Well...

1. I have found that when booting from the battery, the unresponsive keyboard/mouse has not happened yet. This is after several power-off and reboot scenarios. I discovered this accidentally while traveling on several short flights. Since then, I have only seen this problem when booting with the AC power connected. Why? I have no idea! However, I have yet to see this problem surface when booting from the battery. So my work-around is to boot from the battery, then plug in the AC after. Honestly, this does not make sense, but it works.

2. I still get the failure to process Grub after the BIOS flash screen. I believe, but do not know for sure, that a chipset may not always be initialized properly. This is based on an experience I had with an industrial computer some years ago. Again, this is speculation on my part. However, I have a simple work-around now. I just press CTRL + ALT + DELETE. The laptop reboots, and so far, has always processed Grub. Someone suggested that it could be a power switch problem. I do not think so since the computer does POST. While annoying, I can live with this type of problem on a laptop since the work-around is simple and I have no need to remote reboot it.

3. I still get the wireless connection drop then no other program will start problem. I received it the 4th time yesterday at home. I have had this problem 4 times, I believe. It has occurred at home twice and on the road twice.

Otherwise, I have been satisfied with the Serval and Ubuntu 7.10.

I am not sure what the next steps will be.

---

### Post by jdmelton on 2008-01-07
I forgot to mention the results of booting with the Ubuntu 7.10 CDROM. The laptop always booted. However, I did get an unresponsive keyboard on one try. The mouse worked, though. I performed the CDROM boots/reboots on AC power. I did not try on the battery only.

---

### Post by thomasaaron on 2008-01-07
Regarding the machine dropping the wireless connection:

Try this:
echo blacklist ipw3945 | sudo tee -a /etc/modprobe.d/blacklist
echo iwl3945 | sudo tee -a /etc/modules 

If it doesn't help, you can reverse it by:
sudo gedit /etc/modprobe.d/blacklist
<remove the line that says blacklist ipw3945>
sudo gedit /etc/modules
<remove the line that says iwl3945>

---

### Post by jdmelton on 2008-01-16
Update on problems:

1. The first problem was that at boot the BIOS splash screen displayed, then cleared. Next I saw a blinking cursor in the upper left corner. The boot loader, Grub, did not process. I still have that problem. However, the work-around is simple. I just press Ctrl+Alt+Delete. The system reboots and always goes on to run the Grub boot loader. I do not need to remote boot this laptop, so for me, the problem is solved.

2. The second problem was that sometimes the keyboard and mouse were unresponsive at boot. I tried some things as previously posted. I  thought that I had found a work-around by booting with the AC power unplugged. This work-around made no sense to me, but it seemed to work. I write 'seemed' since I the laptop has been on AC power continuously for 5 days now, and I have not seen the problem. There have been some updates in the meantime. It may have been one of the kernel ones. I have been doing several reboots per day to try and reproduce the problem. However, it has not come back. I do not know how, yet I consider this problem resolved. (Most unsatisfactory from a technical point of view!)

3. The third problem was dropped connections on wireless, both at home and while traveling. To date this has happened 5 times. The last time, earlier today, This time, I just waited for the search to time out. This took a couple of minutes it seemed, but I was not timing it. Then the network wireless symbol changed from the 'bars' to the 'tiny computer monitor' with the orange alert symbol. The system did not freeze and new applications could be started. Also, the connection could be re-established by clicking on the networking icon then selecting my home wireless network. See Tom's last post to me about the wireless module. I consider this problem solved.

Thanks to Tom for his support.

---

