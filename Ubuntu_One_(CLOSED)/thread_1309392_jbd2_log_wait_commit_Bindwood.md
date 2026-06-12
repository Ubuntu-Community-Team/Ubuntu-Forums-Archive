---
title: "jbd2_log_wait_commit Bindwood"
date: 2009-11-01
forum: Ubuntu One (CLOSED)
---

### Post by Merovius on 2009-11-01
With a clean install of Karmic and the Bindwood extension enabled, Firefox grays out like every 30 seconds or so and then comes back. If I open the system monitor it shows Firefox has a status of "uninteruptable" and switches waiting channel from "poll_schedule_timeout" and "jbd2_log_wait_commit" every few seconds.

Without Bindwood there are no gray outs and the status is "sleeping" and the channel stays mostly as "poll_schedule_timeout" and only occasionally goes to "jbd2_log_wait_commit"

I've had very bad luck with Bindwood and think maybe it's best to just lose it. Will I be losing much?

---

### Post by manoriax on 2009-11-02
Same problem here.

---

### Post by joshuahoover on 2009-11-02
> **Merovius said:**
> With a clean install of Karmic and the Bindwood extension enabled, Firefox grays out like every 30 seconds or so and then comes back. If I open the system monitor it shows Firefox has a status of "uninteruptable" and switches waiting channel from "poll_schedule_timeout" and "jbd2_log_wait_commit" every few seconds.

Without Bindwood there are no gray outs and the status is "sleeping" and the channel stays mostly as "poll_schedule_timeout" and only occasionally goes to "jbd2_log_wait_commit"

I've had very bad luck with Bindwood and think maybe it's best to just lose it. Will I be losing much?

Sorry to hear Bindwood isnt' working properly for you. The initial unresponsiveness is expected but that should be a one time thing, not on-going. I just replied to a similar thread here: [http://ubuntuforums.org/showpost.php?p=8223981&postcount=4](http://ubuntuforums.org/showpost.php?p=8223981&postcount=4)

Thank you,

Joshua

---

### Post by slugicide on 2009-11-02
Uninstalling Bindwood worked for me. Too bad Bindwood doesn't work. That was one of the best things about Ubuntu One.

---

### Post by Merovius on 2009-11-02
I may try cleaning out some of my bookmarks and then re enable Bindwood and let it go for a few hours. Maybe I just need to let it get caught up initially.

---

### Post by Merovius on 2009-11-05
This morning I enabled Bindwood and left it go for 20 minutes or so while I was getting going. As of the last 15 minutes of using Firefox it has been OK.

I will try a reboot and add a favorite to see what happens.

---

### Post by Merovius on 2009-11-05
No good. after adding one favorite and restarting it grayed out and I had to wait several minutes for it to come back. Disabled again I'm afraid.

---

### Post by joshuahoover on 2009-11-06
> **Merovius said:**
> No good. after adding one favorite and restarting it grayed out and I had to wait several minutes for it to come back. Disabled again I'm afraid.

We have a fix just about ready. I'm trying to see if we can get this into updates or, at the very least, into our PPA. Please follow bug [https://bugs.edge.launchpad.net/bindwood/+bug/443121](https://bugs.edge.launchpad.net/bindwood/+bug/443121) right now for more info. I know it says "Fix Released" there, we'll need to either change this or create a new bug that I'll post a link to in order to track the progress.

Thank you,

Joshua

---

### Post by Merovius on 2009-11-06
Thanks. Will check it out. :D

---

