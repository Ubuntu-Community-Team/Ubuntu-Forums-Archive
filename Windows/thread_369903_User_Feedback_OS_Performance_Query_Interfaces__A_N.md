---
title: "User Feedback OS Performance Query Interfaces:  A New Idea?"
date: 2007-02-25
forum: Windows
---

### Post by mavigozler on 2007-02-25
This may not be a new idea.

But it is obvious that as a user of Windows or Linux demands that many processes ("tasks" "applications") be started up during the booting process, the time it takes before the user can see a responsive mouse click or keypress will get longer and longer.

In some cases, the user sees a huge amount of time to boot up and has no idea why, since he made no installation of a new driver/daemon/monitor/service.  This is especially true of a Windows environment.  The user ends up having to run a "msconfig" instance to find out what service or application/task is being run at startup, and still he has no idea which of the startup tasks has turned a 90 seconds boot-up time into a 15-minute bootup time.

===
Performance Troubleshooter
===

The user of any OS (or "operating environment" as Windows is often disparaged as not being an OS) should have a tool available to the user to help in evaluating performance of the OS at startup/boot and also throughout a session.  The tool would have metrics that help monitor the times certain activities are completed, and be set up to inform the user when there is a sudden large deviation from a running average.

When a user is sitting there waiting 10 minutes before he gets a screen update from having moved a window or made a mouse click, he wants to inform the system that he is waiting impatiently and he wants to know why.  Sometimes the system is waiting on an input from a network and then proceeds after a timeout, but the user is oblivious to knowing what's going on in the blackbox.

I believe that Windows users would be using fewer expletives if Microsoft actually included that tool with built-in intelligence that determines itself what software has been installed, how many applications are open simultaneously, kept a database which profiles the times and monitors deviations beyond a significant limit, and also asks the user from time to time if the user is happy with the speed of the interface.  Thus input/data not only comes from time metrics but from the user's "happiness" with the system.

---

### Post by warlock_handler on 2007-02-25
> **mavigozler said:**
> This may not be a new idea.

But it is obvious that as a user of Windows or Linux demands that many processes ("tasks" "applications") be started up during the booting process, the time it takes before the user can see a responsive mouse click or keypress will get longer and longer.

In some cases, the user sees a huge amount of time to boot up and has no idea why, since he made no installation of a new driver/daemon/monitor/service.  This is especially true of a Windows environment.  The user ends up having to run a "msconfig" instance to find out what service or application/task is being run at startup, and still he has no idea which of the startup tasks has turned a 90 seconds boot-up time into a 15-minute bootup time.

===
Performance Troubleshooter
===

The user of any OS (or "operating environment" as Windows is often disparaged as not being an OS) should have a tool available to the user to help in evaluating performance of the OS at startup/boot and also throughout a session.  The tool would have metrics that help monitor the times certain activities are completed, and be set up to inform the user when there is a sudden large deviation from a running average.

When a user is sitting there waiting 10 minutes before he gets a screen update from having moved a window or made a mouse click, he wants to inform the system that he is waiting impatiently and he wants to know why.  Sometimes the system is waiting on an input from a network and then proceeds after a timeout, but the user is oblivious to knowing what's going on in the blackbox.

I believe that Windows users would be using fewer expletives if Microsoft actually included that tool with built-in intelligence that determines itself what software has been installed, how many applications are open simultaneously, kept a database which profiles the times and monitors deviations beyond a significant limit, and also asks the user from time to time if the user is happy with the speed of the interface.  Thus input/data not only comes from time metrics but from the user's "happiness" with the system.

Hmmm... interesting... you are asking alittle too much from uncle Bill (who assumes that windows is used by dumb ppl... and hence uses a MAC)

---

### Post by erlyrisa on 2007-02-25
It's called Microsoft Bootvis....
It does exactly what you describe.
As for linux... it really shouldn't need anything like that... you can see exactly what's getting booted and when and how long each one takes.

---

