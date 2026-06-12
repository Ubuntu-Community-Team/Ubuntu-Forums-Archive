---
title: "X-session lock-up"
date: 2010-08-06
forum: System76 Support
---

### Post by reid_rsv869 on 2010-08-06
Hey Group -

I have a Serval Pro, new in April.  Great machine, but am having some flakiness.  I think it's X related but I could be wrong.

For the past few months I've had this periodic problem where the screen becomes locked.  The mouse moves but the screen becomes inaccessible.  I can point but not select.  It doesn't happen every day.  I can't isolate it to an app, or collection of apps, but I'm not a sophisticated user.  I run Chrome, Firefox, Evolution and some graphics apps.  

Ever seen this?  Have any thoughts about how to troubleshoot?

Thanks

Reid

---

### Post by reid_rsv869 on 2010-08-15
Haven't heard from anyone in support.  Need some attention to this issue.  It's a recurring problem.  Happened again last night.

Reid

---

### Post by mhgsys on 2010-08-15
Could be a compiz problem somewhere; you should check your logs/messages..
you'll find them in **/var/log** and could use nano,vi or even gedit to view them.

Easy way is to disable desktop effects to exclude compiz as the problem.;

If you know for sure it's not compiz; check the machine on overheating etc.

You can do this with screenlets 
```
sudo apt-get install screenlets
```

(Applications>accessories>screenlets) sensors

or  computertemp;
```
sudo apt-get install computertemp
```

(after that right click a panel, click add to panel and select computer temperature monitor.
*If it's not there, reboot, It will be there after

If you don't get any output on the computertemp-sensor, install libsensors4 & lm-sensors as well.
after that run ```
sudo sensors-detect
```
and try again.

You can monitor multiple temp-outputs simply by adding more sensors,)

---

### Post by bk7777` on 2010-08-15
Not sure if it would be revelent to your problems but check the above Sticky thread called "[[COLOR=#000000]Serval SerP6 - X Resets[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1545846")"
 
Brian

---

### Post by reid_rsv869 on 2010-08-16
Thanks very much for the replies.

First bk7777...yep I'm very aware of that issue.  Was the one who originally reported it and am very glad that fix was located.  Corrected that issue.

mhgsys:  I think compiz is already off; went through that as part of the X-reset issue.  That is, I go to Appearance Preferences and just turn off all visual effects.  I think that's it.  If there's more just point me in the right direction.

As for logs, I have no problem going there, but have no idea what I'm looking for or how to interpret it.  I mean, Google is my best friend for sure, but you know, "Error #568 in xyz system" isn't very helpful, to ME anyway.  Thoughts welcome.

As for heat, I watched that closely for a while in the X-reset issue and never saw much to notice, I thought.

Anyway, as I say, more thoughts welcome, and thanks again for helping guys.

Reid

---

### Post by bk7777` on 2010-08-17
Since I am the new kid on the block as it relates to this forum and UBUNTU.  Been an IBM AIX system admin for 20 years but this is my 1st taste of UBUNTU.
 
Again just adding food for thought.  You likely already did this.  Have you run memtest86?  It took me 2 weeks to find out I have BAD RAM.  The system would run for the most part then freeze.  I kept chasing the NVIDIA driver issue looking for clues till I got turned on the memtest86.
 
my 2 cents,
Brian

---

### Post by reid_rsv869 on 2010-08-17
Did that earlier, too.  Memory is fine.  Thanks -

Reid

---

### Post by isantop on 2010-08-18
Hi Reid. Let's try a debugging step. Please open a terminal and run the following commands:

```
sudo apt-get install dontzap
sudo dontzap --disable
sudo reboot
```

The computer should reboot after that. When it comes back up, log in, then press Ctrl+Alt+Backspace. It should kick you back to the login screen, like the X resets.

If so, then the next time it locks up, try pressing that. If it kicks you back, I have a feeling it's not an X issue, since it wouldn't respond to that.

---

### Post by reid_rsv869 on 2010-08-19
hi isantop -

Thanks for the input.  Couldn't install dontzap.  Error message from CLI is:


reid@rsv-linux:~$ sudo apt-get install dontzap
[sudo] password for reid: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dontzap
reid@rsv-linux:~$ 


I searched on dontzap and found this link. Could this explain why:  [https://wiki.ubuntu.com/X/Config/DontZap](https://wiki.ubuntu.com/X/Config/DontZap)

thx

Reid

---

### Post by isantop on 2010-08-19
Ah, exactly. The guide I used to get that was from Jaunty. you want to:

* Get to the System->Preferences->Keyboard menu.

* Select the "Layouts" tab and click on the "Layout Options" button.

* Then select "Key sequence to kill the X server" and enable "Control + Alt + Backspace".

---

### Post by reid_rsv869 on 2010-08-19
Alrighty then... configured as asked.  Will monitor and let you know.. 

Thanks Ian

Reid

---

### Post by reid_rsv869 on 2010-08-20
Ian -

Had a lockup this morning.  Used the alt-ctl-Backspace and it kicked me back to the user login screen.  

Captured the logs and have attached them.  System said 9:08 when I noticed it, but I had not been on the machine for a few minutes prior to that. 

Also, when the desktop return I had an error.  Took a snapshot and attached that, too, but it might just be a red-herring.  

thanks

Reid

---

### Post by isantop on 2010-08-20
Was the input fine after reseting the X server?

I would also agree that that sounds like a red herring. Just make sure you "Don't Delete" and try logging out and back in.

---

### Post by reid_rsv869 on 2010-08-20
yep...NP at all.

---

### Post by reid_rsv869 on 2010-09-14
Hello Ian -

Thanks for the suggestions today.  The next time this occurs I will try a quick switch to VT2 with ctrl-alt-F2 and will post the result.

In the mean-time would you please let me know if there's anyway to turn on or access Gnome logging.

Thanks

Reid

---

