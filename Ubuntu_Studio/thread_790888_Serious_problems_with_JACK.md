---
title: "Serious problems with JACK"
date: 2008-05-11
forum: Ubuntu Studio
---

### Post by suarez.duek on 2008-05-11
Hi there guys!

Im having problems with Jack and Ardour. Ive read several thraets and solutions, but i cant get it to run well. I open Jack control, then Ardour. Im using Ubunstudio Hardy, and im supposed to have a realtime kernel. The problem is that when i chek the Realtime option in jackcontrol setup, Jack frezzes and then dies. If i dont do this, im attacked by lots of xruns and I cant even start the playing in Ardour. I really dont know how to configure Jack so it works normaly!!! I cant work, cause jack closes when a start it.! How can i make it work and dont being bodered by the xruns!?!> 
please someone help me! Im in a hard situation if i dont solve this,cause this was tha reason i have ubuntustudio! Please! I dont want to go back to stupid windows!
Thks

---

### Post by Ryukage on 2008-05-14
I had this problem too. It took me a long time a lot of googling to figure it out. Contrary to what a lot of the tutorials on this forum imply, simply installing the realtime kernel isn't enough to run JACK in realtime mode. You also have to alter the security settings to enable realtime applications.

Open a console window and type "sudoedit /etc/security/limits.conf".  Add the following lines if they aren't already there, then save and exit:

```
@audio  -  rtprio  90
@audio  -  memlock 512000
@audio  -  nice    -19
```

Note that you may need to reduce the number on the second line if you have less than a gigabyte of RAM. The number is in kilobytes, and should be well below the amount of the RAM in your system.

If the lines are already there but have different numbers, that's fine, leave them, as long as "rtprio" is fairly high, "nice" is between 0 and -20, and "memlock" is a reasonable percentage of your RAM. It's also possible that they'll be in pairs with words in place of the hyphen; that's fine too. The important thing is to have all three of the settings configured---some tutorials only list the "rtprio" and "nice" lines, but I found that the "memlock" line is needed as well.

Now, make sure you're in the audio group (open a console window and type "groups" to see a list of the groups you're in), then log out and back in to make the changes take effect. Now you should be able to run JACK in realtime mode. You may also want to bump JACK's priority up a bit to give it precedence over any other RT applications that might be running.

---

### Post by thorgal on 2008-05-14
Windows is not stupid, winXP does a good job for music work if you can cope with high bucks software or pirated ones. But a carefully tuned linux system seems way better in many respects.

Anyways, the PAM security thing is to allow non root users to access realtime privileges when running apps that need RT processes (SCHED_FIFO or SCHED_RR in kernel scheduling priorities). That's why the audio group exists in the first place because normal users are not supposed to run apps with this level of privileges (security risks). So if you belong to the audio group (which you do by default in many linux distros), these changes in limits.conf will open up the privilege to this group. You can restrict it to you only by replacing @audio by your username (without @).

Regarding the memlock amount, I have 'unlimited' in my own setup (but 4G of RAM). Try different things and stick to what works well, YMMV :)
You can also try to run a script called 'rtirq' which can be executed at boot time. It will tweak the IRQ thread priority and give substancial priority to sound card IRQ and timer threads. It only works if you run a realtime kernel because a generic one will not start certain processes (softirq-timer and softirq-hrtimer).

Hope this helps a little bit for the understanding. Now, I hear a lot of complaints about the latest ubuntu studio (based on Hardy ?). Which kernel does it have ? there's a quite big change in RT kernel stuff in 2.6.25. I stick to 2.6.24.3-rt3 for now (in my debian sid system) until this is sorted out. Paul Davis, the author of Jack and Ardour, mentioned that a RT kernel bug has been spotted since 2.6.18 but was only fixed in 2.6.25. The latest svn version of jack (1188 ) has a workaround. I run it myself with great success but the latest ardour SVN (2.4 branch) is a bit unstable with it, at least at start time. On the other hand, many apps that used to behave a bit erratically became rock solid after this workaround. You can give it a try but you would have to compile stuff yourself. That's a harder path ...

---

