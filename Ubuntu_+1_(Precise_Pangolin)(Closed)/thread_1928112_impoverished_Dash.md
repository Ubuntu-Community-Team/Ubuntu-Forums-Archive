---
title: "impoverished Dash"
date: 2012-02-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Gregory Lee on 2012-02-19
My Dash is just a shadow of its former self.  Is it something I'm doing?  Used to be, when I clicked on the Apps icon, I would see a bunch of stuff -- now, there's nothing there at all.  Some things are left in Home under Recent Apps, but not much, and I can't launch programs from there, any more.  I think I recall, a couple of days ago, being able to click on a program's icon in the Dash in order to launch it.  Now, I click, and nothing happens.

---

### Post by josephmills on 2012-02-19
Do you think that you could take a screen shot of this happening? Then post it here.? Thanks.

---

### Post by Jay Car on 2012-02-19
> **Gregory Lee said:**
> My Dash is just a shadow of its former self.  Is it something I'm doing?  Used to be, when I clicked on the Apps icon, I would see a bunch of stuff -- now, there's nothing there at all.  Some things are left in Home under Recent Apps, but not much, and I can't launch programs from there, any more.  I think I recall, a couple of days ago, being able to click on a program's icon in the Dash in order to launch it.  Now, I click, and nothing happens.


Hi Gregory Lee,

Try clicking on the small icons at the bottom of the shadowy dash and see if one of them will give you what you need. The whole big shadowy dash thing seemed odd to me too.

:)

---

### Post by PaulW2U on 2012-02-19
> **Gregory Lee said:**
> My Dash is just a shadow of its former self.  Is it something I'm doing?  Used to be, when I clicked on the Apps icon, I would see a bunch of stuff -- now, there's nothing there at all.  Some things are left in Home under Recent Apps, but not much, and I can't launch programs from there, any more.  I think I recall, a couple of days ago, being able to click on a program's icon in the Dash in order to launch it.  Now, I click, and nothing happens.

I was seeing something like this too. One of unity components was crashing on log-in. Logging out and back in again solved the problem.

Are you seeing any crash notifications? If so, a restart might help.

---

### Post by Gregory Lee on 2012-02-19
> **josephmills said:**
> Do you think that you could take a screen shot of this happening? Then post it here.? Thanks.
No, I don't see the icons vanishing before my eyes.  Rather, over the course of days, I've seen less and less there.  Using the Home lens, I see 10 recent apps and 5 recent files.  Using the Files & Folders lens, there are some icons.  Using the Apps lens, there is nothing at all.  Except for the Search and Filter bars at the top, the window is entirely empty.  Blank.  Unrelieved absence of icons.  (Filter results is set All.)

---

### Post by Gregory Lee on 2012-02-19
> **Jay Car said:**
> Try clicking on the small icons at the bottom of the shadowy dash and see if one of them will give you what you need. The whole big shadowy dash thing seemed odd to me too.
Yes, it's a little spooky.  Clicking the lens icons gives the results I mentioned just above.  And, by the way, I don't see a video lens icon -- isn't that supposed to be in the current version?  (I'm up to date with software updates/safe-upgrades.)

---

### Post by Gregory Lee on 2012-02-19
> **PaulW2U said:**
> Are you seeing any crash notifications? If so, a restart might help.

```

# ls -l /var/crash
total 11108
-rw------- 1 greg greg 10146166 Feb 13 16:55 _usr_bin_compiz.1000.crash
-rw-r----- 1 greg greg    70414 Feb 15 16:45 _usr_bin_jockey-gtk.1000.crash
-rw-r----- 1 greg greg    53309 Feb 15 05:45 _usr_lib_gnome-settings-daemon_gsd-backlight-helper.1000.crash
-rw-r----- 1 greg greg  1036231 Feb 17 13:02 _usr_lib_unity-lens-applications_unity-applications-daemon.1000.crash
-rw------- 1 greg greg    26454 Feb 19 05:40 _usr_share_oneconf_oneconf-query.1000.crash
-rw-r----- 1 greg greg    24846 Feb 19 05:40 _usr_share_oneconf_oneconf-service.1000.crash
```

Hmm.  That unity-lens-applications daemon is running now, but maybe that's the problem.  I'll try the reboot.

---

### Post by mc4man on 2012-02-19
There is this current bug on the unity-lens-applications that can cause nothing to be opened from the apps lens & maybe other related issues. Usually a log out/in restores, sometimes it may take 2 or a restart
[https://bugs.launchpad.net/ubuntu/+source/unity-lens-applications/+bug/917606](https://bugs.launchpad.net/ubuntu/+source/unity-lens-applications/+bug/917606)

---

### Post by Gregory Lee on 2012-02-19
I guess that was it.  After rebooting, now I see icons in the Dash Apps lens, and also, now I can launch one by clicking on it.

There are lots of bugs -- I suppose that is not shocking news to you all.  In trying to restart Ubuntu just now, the system would not come back up.  I got a Unity screen with four white lights which never changed.  I had to power down before I could get Ubuntu up again.

And I tried to make this post an edit of my preceding post, instead of starting a new post, but found that Firefox's edit-post screen had no scrolling, so I could not get down to the bottom of my previous post to make an addition. [Edit: However, I now notice that I can lengthen the edit-box by clicking the little down-down mark at the upper right.  Maybe that's just the way it's supposed to work, now.]

Whew.

---

### Post by Gregory Lee on 2012-02-19
> **mc4man said:**
> There is this current bug on the unity-lens-applications ...[]("https://bugs.launchpad.net/ubuntu/+source/unity-lens-applications/+bug/917606")
Aha.

---

### Post by grahammechanical on 2012-02-19
I got Unity 5.4 through a ppa for testing. Until I unchecked the ppa in software sources I was not receiving Unity updates through the regular channel. After unchecking the ppa I got updates to Unity that brought in a regular Unity 5.4 but to get the video lens I had to install it. Search the software centre or synaptic for unity lens and you will find it.

By the way, it is possible to re-install lenses. That was how I fixed an issue with the Dash.

Regards.

---

### Post by Gregory Lee on 2012-02-19
> **grahammechanical said:**
> Search the software centre or synaptic for unity lens and you will find it.
Thank you -- got it.  (I don't actually see it.  Maybe after the next restart.)

I discovered by accident that if I right click on an App in the Apps lens under Apps Available for Download, that brings up the Software Center with information about that App.

---

