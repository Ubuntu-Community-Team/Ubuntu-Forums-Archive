---
title: "Jaunty updates notification. Not working yet?"
date: 2009-04-26
forum: The Cafe
---

### Post by Kosimo on 2009-04-26
Guys, does your jaunty inform you automatically about new updates?

I keep doing my updates manually but, looks like the final version doesn't notify them. Is this correct?

If yes, this means that somebody who wants to try jaunty for the first time and doesn't make a manual updates check will never be notify about new available updates.   This is an extremely serious bug isn't it?

---

### Post by meeples on 2009-04-26
yea we dont get the notifier anymore :O ive had to put update manager in my startup apps so i remember :(

---

### Post by swoll1980 on 2009-04-26
It will only notify once a week by opening in a "install the updates now, damn you!" kind of way.

---

### Post by Stupendoussteve on 2009-04-26
It does, but by default is set to do so after 7 days (less for security issues). Because you are doing them manually it probably never hits that period.

If you're curious what it looks like, in the gconf-editor you can modify /apps/update-notifier/regular_auto_launch_interval to 1 or 0, and it will pop up more often. If you like the old behavior with the icon in the panel, you can also uncheck the auto_launch checkbox in the same area.

---

### Post by qamelian on 2009-04-26
There is a new default behaviour for updates. It no longer notifies you daily. It is every 7 days instead. If there are updates available at that interval, the update manager will open automatically under any other open windows and remain there until you either deal with the updates or dismiss it.

---

### Post by Sand &amp; Mercury on 2009-04-26
> **qamelian said:**
> There is a new default behaviour for updates. It no longer notifies you daily. It is every 7 days instead. If there are updates available at that interval, the update manager will open automatically under any other open windows and remain there until you either deal with the updates or dismiss it.

This.

If you want the old behaviour back, open up gconf-editor. Then navigate to apps > update-notifier and uncheck "auto_launch"

---

### Post by Giant Speck on 2009-04-26
> **Sand & Mercury said:**
> This.

If you want the old behaviour back, open up gconf-editor. Then navigate to apps > update-notifier and uncheck "auto_launch"

In addition to this, if you want to be notified as soon as updates become available, you can set regular_auto_launch_interval to 0.

---

### Post by Kosimo on 2009-04-26
Cool guys, I didn't know that! :KS


Thank you all!

---

### Post by billgoldberg on 2009-04-26
They shouldn't have changed the behaviour.

Things were good as they were.

But hey, no biggie, I always run apt-get update && apt-get upgrade manually.

---

### Post by Kosimo on 2009-04-26
> **billgoldberg said:**
> They shouldn't have changed the behaviour.

Things were good as they were.

But hey, no biggie, I always run apt-get update && apt-get upgrade manually.

Me too, at least twice per day :P

---

### Post by riseringseeker on 2009-04-26
> **Kosimo said:**
> Me too, at least twice per day :P

Have there *been* any updates to 9.04 since release?  I have run sudo apt-get update as well as asking the update-manager to check for them at *least* daily, and have yet to see any.  

I did a reinstall using the alternate 64 bit disk....

Other than that, things seem to be running just fine.

---

### Post by Kosimo on 2009-04-26
> **riseringseeker said:**
> Have there *been* any updates to 9.04 since release?  I have run sudo apt-get update as well as asking the update-manager to check for them at *least* daily, and have yet to see any.  

I did a reinstall using the alternate 64 bit disk....

Other than that, things seem to be running just fine.

I had some updates but I'm having proposed and backport updates enabled in software sources. How about you?

---

### Post by Polygon on 2009-04-26
and this is why they should not of changed it. everyone is confused on why its not checking for updates anymore.

---

### Post by riseringseeker on 2009-04-26
> **Kosimo said:**
> I had some updates but I'm having proposed and backport updates enabled in software sources. How about you?

Nope, just "Important Security Updates" and "Recommended Updates" are checked.  I have it set to check daily, and only notify about available updates.

---

### Post by Sinkingships7 on 2009-04-26
This is a serious flaw. What happens when a huge bug is uncovered and needs to be patched? Oh no, we're going to have to be vulnerable for a week until update manager decides to bring itself up.

Obviously "we" is used to define the general newbie population. More experienced users can, as stated, change the behavior through the obscure gconf-editor, or will check manually.

This is just a horrible change.

---

### Post by Giant Speck on 2009-04-26
> **Sinkingships7 said:**
> This is a serious flaw. What happens when a huge bug is uncovered and needs to be patched? Oh no, we're going to have to be vulnerable for a week until update manager decides to bring itself up.

Update-notifier will automatically notify you of a security update regardless of the 7-day default setting.

---

### Post by Sinkingships7 on 2009-04-26
> **Giant Speck said:**
> Update-notifier will automatically notify you of a security update regardless of the 7-day default setting.

THAT is very good news to hear. Thank you. :)

---

### Post by Giant Speck on 2009-04-26
> **Sinkingships7 said:**
> THAT is very good news to hear. Thank you. :)

I noticed it when looking at the settings in gconf-editor.  

It would be retarded to have to wait seven days for a security update.  I'm glad the developers were smart enough to realize that, too. :)

---

### Post by riseringseeker on 2009-04-29
> **Stupendoussteve said:**
> It does, but by default is set to do so after 7 days (less for security issues). Because you are doing them manually it probably never hits that period.

If you're curious what it looks like, in the gconf-editor you can modify /apps/update-notifier/regular_auto_launch_interval to 1 or 0, and it will pop up more often. If you like the old behavior with the icon in the panel, you can also uncheck the auto_launch checkbox in the same area.

I unchecked the auto_launch button and yet this morning the update-manager launched by itself, maybe I am missing something here?  (I also changed the interval to 0).

---

