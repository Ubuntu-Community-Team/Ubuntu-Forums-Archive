---
title: "Some services not starting at boot"
date: 2012-03-05
forum: Server Platforms
---

### Post by jfollmann on 2012-03-05
Hello, all. I'm hoping for an older and/or wiser user to point me in the right direction for troubleshooting a problem.

First things first, the platform: I am running Ubuntu 10.04 on my server. It started out as the desktop-oriented version (as I was even more of a newbie when I built it, and wasn't quite ready to go terminal-only). It still more or less is the desktop version, but a while back I did switch it over to the server kernel.

Some services don't appear to be starting when my server boots. I do not know exactly why - I'm looking for help in determining that.

Among the services that have failed at various times are apache2, smokeping, webmin, and 3dm2 (a configuration/monitoring daemon for 3Ware RAID controllers).

When I say they've failed to start, I'm not seeing any errors in the logs or anything. I just mean I notice that I can't access them - none of them seem to be logging any errors in /var/log/syslog or /var/log/messages. Oddly, if I manually start any of the affected services, it will come up just fine. And it will run without any apparent issue, until the next reboot. To my amateur mind, it seems more like the attempt to start them is never made, rather than the attempt being made and then erroring out.

Whatever the problem is, it started in the last few weeks. Because no errors are logged (as far as I know, anyway), and the problem only becomes apparent after a reboot, I am unsure of precisely when it began.

This next part might be significant: Just a couple weeks before I started noticing this, I was working on getting lcdproc working. In the end, I had to modify the priority of the init scripts for lcdproc and LCDd (lcdproc depends on LCDd being started first, but for some reason the default installations don't account for that, so I had to modify things so that LCDd always starts first). lcdproc is working just fine, but maybe something I did to the init scripts caused a problem?

While I basically understand the overarching idea of what I did (making sure a dependency starts before the thing that depends on it - pretty straightforward), I don't really know all that much about the init script system - I just used a walkthrough to get things done. So while I suspect this may have affected something, I don't know precisely how to check whether all is well. I can tell you that if I do an "ls" under /etc/rc3.d or /etc/rc6.d, or any of the other runlevels, it appears to me that entries for all the affected services are present, with (as I understand it) appropriate priority numbers. Whether that is all that needs to be verified, I don't know. Probably not.

It's also possible that the lcdproc thing is a red herring. I don't have anything that really points to my modifications there as the cause, other than that it seems to have been about the right time frame.

As you can probably tell, I don't consider myself a guru, but I've been using Linux as my primary OS for years now and am pretty comfortable on the command line. Please don't hesitate to ask for any information that might be helpful - if I know how to get it, I will, and if I don't know how, I'll figure it out or ask. :)

Any suggestions will be very much appreciated.

---

### Post by kevdog on 2012-03-05
A lot of ground to cover here.  I believe Ubuntu in that edition had transitioned for startup services to use udev rather than system v scripts. I'm not 100% certain since I never installed 10.04.  

How do you start these services now?  What do you type in the command line to start these not-started services -- that should give me a clue.

If its udev that controls the startup scripts, its easy to modify each service where you could specify in the script to not start the service unless a dependency had been started.

---

### Post by jfollmann on 2012-03-06
I'm starting them manually with "sudo service [service name] start."


*Edited to reflect the ACTUAL command I'm using. I blame the limited visibility of typing on a phone. Or something.

---

### Post by kevdog on 2012-03-07
By your syntax, you are calling a udev script.

Let's just troubleshoot this one service at a time.  Can you name one of the services that doesn't start and post the udev script for the service?  The udev scripts are located in /etc/init/ and the name should be fairly self evident.

---

### Post by jfollmann on 2012-03-07
Hmmm... I wonder if we've stumbled upon the problem already. Of the 4 services I've noticed not starting, not one of them seems to have an associated .conf file under /etc/init. There are plenty of files there, just none that match the services in question.

I've already reinstalled the packages, which I would think would have put the right things in place here. Maybe not, though?

---

### Post by kevdog on 2012-03-07
How about we just tackle one of the services -- name one that isn't working, and I'll have a shot at what's going on in my install.

---

### Post by hawkmage on 2012-03-07
Yes Ubuntu 10 is primarily using Upstart scripts but it will still run the older System V scripts.

Also the command "service" is just a wrapper on the init/init.d scripts.

---

### Post by jfollmann on 2012-03-09
Ok, kevdog - let's go with apache2.

Hawkmage - yeah, I've been wondering about upstart. Specifically, once 12.04 becomes available, I wonder if it will only use upstart? If so, maybe some of my problems will be fixed simply because of things getting re-done when the system transitions over to upstart? Either that, or my current messed-up settings would get copied and my upstart configuration will fail just as badly as my current situation. :P

---

### Post by jfollmann on 2012-05-07
Well, if anyone's still listening to this thread, the recent update to 12.04 did not help this issue at all. :(

There has got to be a way to figure out what SHOULD be in place to start these things up. Once I know that, I can probably get things straightened out.

---

### Post by CharlesA on 2012-05-07
Are you just trying to see why apache isn't starting?

---

### Post by jfollmann on 2012-05-11
Well, there's a couple other services that also are not starting, but I wouldn't mind just concentrating on Apache. If I can find out why it's not starting, the solution might apply to some of the other services.

---

### Post by CharlesA on 2012-05-11
Check the syslog and /or apache logs and see what it says.

---

### Post by SeijiSensei on 2012-05-11
I suggest installing chkconfig (sudo apt-get install chkconfig) and using it to activate or deactivate services.  Running the command "sudo chkconfig apache2 on" will set up the links in /etc/rc[0-6].d so that apache2 will start at boot.

If you want to do this manually, you can create the appropriate symlinks in /etc/rc2.d yourself (see /etc/rc2.d/README for details), but it's much easier to use chkconfig. 

To check the status of any daemon, use "sudo chkconfig daemonname", e.g, "sudo chkconfig apache2".  To see the status of all possible services, use "sudo chkconfig -l".  Read the man page for chkconfig for more details.

---

### Post by CharlesA on 2012-05-11
update-rc.d does the same thing as chkconfig as far as I know when it comes to setting when to start/stop services.

---

### Post by jfollmann on 2012-05-11
> **CharlesA said:**
> Check the syslog and /or apache logs and see what it says.

Not much. The word "apache" doesn't appear in /var/log/syslog at all.

I also found /var/log/apache2/error.log but all it has is this:

```
[Fri May 11 15:46:03 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Fri May 11 15:47:57 2012] [notice] caught SIGTERM, shutting down
[Fri May 11 16:00:02 2012] [notice] Apache/2.2.22 (Ubuntu) configured -- resuming normal operations
[Fri May 11 16:06:44 2012] [notice] caught SIGTERM, shutting down
```

Those just seem to be what happens when you install apache2 (the "configured" message) and shut down the machine (the "SIGTERM" message).

---

### Post by jfollmann on 2012-05-11
> **SeijiSensei said:**
> I suggest installing chkconfig (sudo apt-get install chkconfig) and using it to activate or deactivate services.  Running the command "sudo chkconfig apache2 on" will set up the links in /etc/rc[0-6].d so that apache2 will start at boot.

If you want to do this manually, you can create the appropriate symlinks in /etc/rc2.d yourself (see /etc/rc2.d/README for details), but it's much easier to use chkconfig. 

To check the status of any daemon, use "sudo chkconfig daemonname", e.g, "sudo chkconfig apache2".  To see the status of all possible services, use "sudo chkconfig -l".  Read the man page for chkconfig for more details.

I think you put me on the right path here. The TL;DR version is that apache2 appears to be starting at boot for me now.


Longer version is below if anyone's interested:




I did what you suggested, installed chkconfig and ran "sudo chkconfig apache2," it said apache2 was on.

Ok, I thought - I'll turn it off and back on, hoping that will get rid of whatever's wrong and overwrite it with the correct data. So, ran "sudo chkconfig apache2 off." That gave this error:

```
/sbin/insserv: No such file or directory
```

And running chkconfig after that step revealed that it still thought apache2 was on.

I did a little searching on that error and found [[COLOR="RoyalBlue"]this post[/COLOR]]("http://loginroot.com/ubuntu-12-04-64bit-sbininsserv-no-such-file-or-directory/") which sort of indicated that error could be fixed by adding a symlink like this:

```
ln -s /usr/lib/insserv/insserv /sbin/insserv
```

I say sort of because the post was actually about an error they had encountered when turning services on, not off. Still, I thought it was worth a try.

I created that symlink and ran "sudo chkconfig apache2 off" followed by "sudo chkconfig apache2 on." I got a TON of strange output from both that I didn't completely understand, but between the off and on entries I checked status and apache2 was off, so it was having more of an effect this time. Checked again after turning it on, and chkconfig said apache2 was on. Good news again.

And... I rebooted the server and apache2 appears to be running, WITHOUT me having to manually invoke it. Very encouraging. :) I shall try the same thing on webmin and see if it behaves.

---

### Post by jfollmann on 2012-05-11
Well unfortunately the solution that worked for apache2 has had no apparent effect on webmin. And now ProFTPd, which was fine before today, is refusing to start (chkconfig also does not fix it). And there's seemingly no information in the system logs pertaining to either of them. It's like no attempt is made to start them in the first place.

---

### Post by jfollmann on 2012-05-13
> **jfollmann said:**
> Well unfortunately the solution that worked for apache2 has had no apparent effect on webmin. And now ProFTPd, which was fine before today, is refusing to start (chkconfig also does not fix it). And there's seemingly no information in the system logs pertaining to either of them. It's like no attempt is made to start them in the first place.

Gah! Now Netatalk is doing it, too. Didn't notice until I happened to boot up the only Mac in the building today and it was complaining that it couldn't run its last Time Machine backup.

If I don't find a solution very soon I am going to have to reinstall this machine and start over. Probably will do it next weekend. In some ways I'm glad, because I can finally do a proper server install and get rid of all the unnecessary desktop junk that runs on it. Can't say I'm looking forward to putting in the time though.

---

### Post by jfollmann on 2012-05-14
```
<farnsworth>Good news everyone!</farnsworth>
```

TL;DR version: it's fixed.

The rest of the story...

As I think I mentioned at the start of this thread, things started to go wrong shortly after I'd gotten lcdproc working. Now, at one time I attempted to remove all traces of lcdproc. This would have been shortly after I realized there was a problem with the startup process. But it didn't seem to help at the time, so I just put lcdproc back in place, thinking it must not have been the cause.

However, just now out of desperation I went through and uninstalled lcdproc/LCDd, used update-rc.d to remove their startup scripts, and set about removing any files that had to do with lcdproc or LCDd at all. And somehow, it appears to have helped this time! Everything's starting up just fine now.

What I don't know is why removing those things didn't work the first time I tried it. It might be that I just missed a file that time? I would have been using the "locate" command to search, same as I did just now. I was still on 10.04 at the time, not sure if that would have mattered?

I also just noticed that this upgraded 12.04 install is running the generic kernel, not server as before. And I may be crazy, but it seems like I can't find a server specific kernel anymore? Whatever, for now I'm just glad things are working. Thanks to everyone who helped with this.

---

