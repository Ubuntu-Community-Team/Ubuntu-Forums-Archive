---
title: "Power Management on Darter:  always &quot;On AC&quot;"
date: 2009-07-20
forum: System76 Support
---

### Post by Georgesl on 2009-07-20
Brand new Daru3, basic configuration.

When AC power is removed the computer does not seem to go into Battery Power mode.  I've been running on battery for about 20 minutes but when hovering over the Power Management icon the popup reads:

Computer is running on AC Power
Laptop battery discharging (76.4%)
Battery discharge time is currently unknown

I've run though one charge/discharge/charge cycle from 100% down to 8% and back up to 100%.  Discharge took about 1:15.  Charge took about 1:45 with computer on.  The computer doesn't seem to be doing its power saving tasks.

When I pull the AC power from the computer the screen stays full bright but the "AC plug" disappears from the Power Management icon.  It seems to know what's going on, but doesn't react appropriately.

I installed all the recommended updates and reinstalled the System 76 drivers.  I rebooted and the problem remains.

Any ideas?

Thanks, George

---

### Post by marshmallow1304 on 2009-07-21
What you describe sounds very much like the problem on [this thread]("http://ubuntuforums.org/showthread.php?t=1155641"), though the poster (like myself) has a Pangolin.

From what I gathered from that thread, it's a kernel problem.  Some people reported that a kernel update fixed it, but alas, for myself and several others, the latest kernel updates have had no effect.  It seems to be a regression; the problem does not occur in Intrepid.  It seems likely that the problem will be fixed in Karmic, but thomasaaron will know more about that than I do.

So the choices pretty much come down to
  1.  Wait for kernel updates and possibly Karmic.
  2.  Compile your own kernel, as (partially) described in the thread I linked.

---

### Post by thomasaaron on 2009-07-21
First, make sure you're fully updated. Then, run your System76 driver. Then reboot. Did that have any effect?

Second, go to System > Prefs > Power Management > General (tab) and select "Always show an icon."

When you plug in and unplug your ac, does the battery icon in the upper panel change?

---

### Post by Georgesl on 2009-07-21
I did as Thomas instructed.  

Before I started this thread I updated the system completely and ran the System 76 drivers.  I just checked and the computer is completely up to date.

5 seconds after power is plugged in the "AC Plug" appears on the icon.  Two seconds after the power is unplugged the AC plug disappears.  The yellow charge light on the computer also indicates correctly.  

More info:
The power management hover popup always says "Running on AC power" and the screen stays full bright even long after AC power is removed.  "Reduce Backlight Brightness" is checked in power management preferences.

The hover popup always says "Battery discharge time is currently unknown" when on  battery and "Laptop battery ## minutes until charged (##.#%)" when plugged in

When I bring up the Power History window it only shows event markers for "Session active," "Session idle" "Session powersave," "Lid closed," Lid open" and "Suspend."  It does not show markers for "On AC" or "On battery." but it does show the correct colors on the line of the graph.

I've taken the battery down to 10% power and the "Power low" warning popup does appear at that time.  Shortly after that the screen goes to full dim and brightness cannot be increased.  It takes a bit more than an hour to go from full charge to 10%.

This computer has the following information:
Release 9.04 (Jaunty)
Kernal Linux 2.6.28-13-generic
Gnome 2.26.1

[marshmallow1304]("http://ubuntuforums.org/member.php?u=663154"):  I read the referenced thread and it certainly seems to be the same issue.  Since I'm an Ubuntu novice and this is a new computer I'll wait for Thomas to respond.  


George

---

### Post by thomasaaron on 2009-07-22
It all sounds familiar to me except for two things...

1. The screen going dim and not being able to brighten it
2. The battery life seems a bit too short, but you're only running it down to 10%, I'm not sure how hard you're pushing the machine, and the 10% estimate may not be accurate because of this "bug."

One last thing, could you see if suspend works when you close the lid.

Once I know that, I'll run some tests here in the shop and see what happens.

---

### Post by Georgesl on 2009-07-22
> **thomasaaron said:**
> It all sounds familiar to me except for two things...

1. The screen going dim and not being able to brighten it
2. The battery life seems a bit too short, but you're only running it down to 10%, I'm not sure how hard you're pushing the machine, and the 10% estimate may not be accurate because of this "bug."

One last thing, could you see if suspend works when you close the lid.

Once I know that, I'll run some tests here in the shop and see what happens.

1. The screen only dims at about the time the "Battery low" notification popup appears.  It seems to be some sort of "last ditch" powersaving action to definitely tell the user to plug the computer in.  It definitely got my attention!  Once the computer was plugged in I was able to brighten the screen.

2. The lowest battery percentage I have seen indicated is 8% and I'm leery of running expensive laptop batteries to zero.  I wasn't pushing the computer hard at all during this time.  In fact it was idle about half the time with light websurfing (forums, no video) the rest of the time.  Measured time from full to 8% was 1:10 which seems quite short even for a small battery.  The computer is making quite a bit of heat (hot air exiting the left side of the computer and left side of the keyboard warm to the touch) and cycling the fan up and down as needed but this does not seem to correlate to what I am doing with the computer.

Suspend seems to work.  Close the lid and the screen goes off and the power light flashes green.  Open the lid and it wakes up and asks for the password.  These events are recorded correctly in the Power History.

When I remove or apply AC power I do _not_ get the notification popups illustrated in the power manager help page.  Those help pages, however, do not seem to exactly match the power manager as installed on my computer.  The power manager version on the computer is 2.24.2

I ran the computer through another discharge/charge cycle to verify my previous numbers.  It pretty much paralleled the first data.  From 100% it took about 1:10 to get down to 12%, at which point the screen dimmed and could not be brightened.  At 1:14 the "Battery low" notification occurred at 9% power.  At 1:22 the power was down to 3% with no further notifications or actions.  I plugged it in at which point I could immediately increase the screen brightness.  The computer took about 3 hours to get up to 100% while operating.  The cooling fan was running at high speed most of the time the battery was charging, even though I wasn't doing anything more taxing than web browsing.  The room temperature was 78F.  It was loud enough that my daughters commented on it.

To reiterate, the issue is that the Power Manager doesn't recognize when the AC adapter is unplugged and continues to operate in "On AC" mode.

George

---

### Post by thomasaaron on 2009-07-23
OK, I'll run some tests on my shop Darter and report back.

---

### Post by Georgesl on 2009-07-23
> **thomasaaron said:**
> OK, I'll run some tests on my shop Darter and report back.

OK.  Another thing I've noticed is that the fan seems to run quite fast even when the computer is idle (CPUs < 5%).  The CPU _is_ putting out quite a bit of heat so the fan is needed.  This might be related to the power management issue.

---

### Post by Georgesl on 2009-09-07
To bring closure to this thread, I returned the Darter to System 76 for a refund which was made promptly.

If a fix was found perhaps Thomas will post a pointer to the appropriate thread to help those who have searched their way to this thread.

---

### Post by jii on 2009-09-07
As mentioned by marshmallow1304 in the second post, this "power manager thinks I'm discharging on AC" bug is the same problem that was abandoned in [_this thread_]("http://ubuntuforums.org/showthread.php?t=1155641"), as well as other threads. It's confirmed with Jaunty on Pangolins, Gazelles, and Darters, and has been for months. 

Some Pangolin users got it fixed automatically with a kernel update. I live booted Karmic Koala Alpha 5 on my Gazelle the other day and the problem didn't exist there, so I'm looking forward to October 29th when it's officially released. Waiting for the koala is the closest thing you'll find to a fix for this problem, outside of recompiling your own kernel, which you are on your own to figure out.

In regards to the screen going dim and not being able to brighten it, isn't this an expected power saving feature when your power falls down to ~10%? It happens on my Gazu1 everytime, along with a synchronized notification that my battery is low. Plugging in allows me to immediately increase the brightness again.

---

### Post by Georgesl on 2009-09-07
Yes, the issue has been known since May at least, but no solution seems to be forthcoming except "wait for Koala" unless I have missed something.

It seems logical that the screen dimming is the hardware's last-ditch effort to tell the user to plug the computer in or shut it down.  There were no power messages before that, probably because the OS thinks the computer is on AC.

---

