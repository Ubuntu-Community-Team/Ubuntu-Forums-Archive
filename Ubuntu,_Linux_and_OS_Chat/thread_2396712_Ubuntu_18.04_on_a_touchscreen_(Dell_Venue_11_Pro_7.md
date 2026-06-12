---
title: "Ubuntu 18.04 on a touchscreen (Dell Venue 11 Pro 7140) - problems and solutions"
date: 2018-07-19
forum: Ubuntu, Linux and OS Chat
---

### Post by AlpineCarver on 2018-07-19
*[Note: I'm somewhat ambivalent about where to post this. I'm putting it in the General Help forum, because it's a list of specific problems, many of which I've solved, but some of which I haven't yet. I hope this will be helpful to others, as well as helping me find some better solutions. I chose not to put it in the Mobile Technology forum, because touchscreens are becoming more common on mainstream laptops nowadays.]*

I've installed Ubuntu 18.04 on my Dell Venue 11 Pro 7140 and am using it without a physical keyboard or mouse. It's clear that touchscreen support was not a goal for this release, since many things are broken in very obvious ways, but I have been able to find enough solutions and work-arounds to arrive at a satisfying experience for my limited requirements - this is a secondary device that I use only for web, email, light text editing, and consuming media stored on a samba server. Perhaps there are better desktop environments or distros for this, but I'd like to keep my laptops, servers, and this tablet running the same software, as far as possible.

I'll start with issues of interest to anyone running Ubuntu 18.04 on a touchscreen and finish with issues specific to this particular hardware.


**[SIZE=4]System[/SIZE]**

(1) A single tap in the Dock bar on the left side of the screen acts like two taps. If you click on the "Show Applications" icon in the lower-left corner, the expected page of application icons appears momentarily and then disappears. If you click on a program icon in the dock, you get two running instances of the program.

[https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1725384](https://bugs.launchpad.net/ubuntu/+source/gnome-shell-extension-ubuntu-dock/+bug/1725384)

This a very obvious bug, but it can be worked around. When you get two instances of a running program, close one of them. For the "Show Applications" icon: tap-and-hold until the application icons appear, then slide your finger up into the dock bar, then release.

(2) The on-screen keyboard is incapable of entering capital letters and many of the special characters.

[https://gitlab.gnome.org/GNOME/gnome-shell/issues/135](https://gitlab.gnome.org/GNOME/gnome-shell/issues/135)

This another very obvious bug, but it can be worked around by replacing the default on-screen keyboard (caribou) with a better alternative (onboard).

[INDENT]sudo apt-get install onboard gnome-shell-extension-onboard gnome-tweaks[/INDENT]

In gnome-tweaks, choose the "extension" tab, and turn on Onboard Indicator.

You can customize onboard's appearance and behavior, using Onboard Settings, which you get when you install onboard. The most important tweak is the keyboard's size, which you adjust simply by grabbing an edge and dragging.

(3) There is no way to right-click or middle-click.

You can try:
[INDENT]settings / universal access / click assist / simulated secondary click - ON[/INDENT]

This is supposed to convert a long click into a right-click, and it works under certain circumstances, but it often does nothing.

Not being able to right-click or middle-click is another major usability issue on touch screens, but onboard also provides a work-around for this. In onboard, near the upper-right corner, there is an arrow button. If you tap it, it exposes a number of additional arrow buttons. You can use these to simulate right-click and middle-click. This is cumbersome but reliable.

(4) The window buttons (min/max/close) are tiny. They are hard to hit with your finger, and it is easy to hit something else unintentionally.

I have not yet found a perfect solution to this. A very helpful partial solution is to increase the horizontal space around the window buttons. Create or edit  **~/.config/gtk-3.0/gtk.css** and add lines like this:
```
headerbar button {
	margin-left: 10px;
	margin-right: 20px;
}
```

To activate it, log out and log back in again or, on a physical keyboard, type ALT-F2, then the letter R, and then hit Enter.

If there is an easy way to enlarge the actual icons, or there is a theme better-suited to touchscreens, please let me know about it.

(5) Scroll bars are tiny and hard to operate with your finger. You can enlarge them by creating or editing **~/.config/gtk-3.0/gtk.css** and adding lines like these:
```
scrollbar, scrollbar button, scrollbar slider {
	min-width: 35px;
	min-height: 50px;
}
```

If you prefer tap-in-trough to advance only one screenful at a time, create or edit **~/.config/gtk-3.0/settings.ini** and add the following two lines:
```
[Settings]
gtk-primary-button-warps-slider = false
```

(6) The top bar is tiny and hard to operate with your finger. Since I use this very rarely, I'm willing to trade the inconvenience for the vertical screen real estate.

The thing I would use frequently in the top bar is the Activities button, which pulls up a window and workspace switcher. On the Dell 7140, the physical button at the bottom of the screen accomplishes the same thing, so I don't use the Activities button in the top bar.

(7) Many things are too small, both for viewing and for finger-tapping. These preferences vary from person to person; here are the choices I made:

[INDENT]gnome-tweaks / fonts
[INDENT]scaling factor - 1.33
window title - Ubuntu Medium 16
interface - Ubuntu Regular 14
document - Sans Regular 13
	monospace - Ubuntu Mono Regular 13[/INDENT]
settings / dock / icon size - 56
terminal / preferences / unnamed - custom font monospace regular 14[/INDENT]

(8) Occasionally, the top bar becomes unresponsive to touch events, and sometimes the whole screen becomes unresponsive to touch events. When this happens, the system remains responsive to the physical button at the bottom of the Dell 7140, which pulls up the Activities screen, and tapping it gets the touchscreen unstuck. This might be a serious problem on other hardware.


**[SIZE=4]Applications[/SIZE]**

(9) Thunderbird - can't touch-scroll the overview pane. I switched to evolution, which works well. Wish its icons were a little bigger, but they are usable.

(10) Firefox
touch-scroll:
[INDENT]add the following line to **~/.profile** and log out and log in again:
[INDENT]export  MOZ_USE_XINPUT2=1[/INDENT][/INDENT]
larger icons:
[INDENT]navigate to about:config
set layout.css.devPixelsPerPx to 1.33
(do NOT make it smaller than 1.0, unless exactly -1.0, which uses the system size)[/INDENT]
avoid right-clicking:
[INDENT]install the **Tap To Tab** firefox extension - double-click on links to open in a new tab
to open bookmarks in new tabs automatically:
[INDENT]visit about:config
set browser.tabs.loadBookmarksInTabs to true[/INDENT][/INDENT]

After doing these things, firefox works great!

(10) In many programs, you can navigate menus with the touch screen, but when you tap to make a selection, nothing happens. Some programs that exhibit this bug: evolution, aisle riot solitaire. I have no work-around for this, except to use a physical mouse. For my use cases, I can get away with not using menus in programs that exhibit this problem.

(11) Synaptic's authorization pop-up disables onboard, the on-screen keyboard, so it is completely unusable. You can either plug in a keyboard or use apt-get from the command line.


**[SIZE=4]Hardware-Specific[/SIZE]**

(12) [Dell 7140] MicroSD card reader doesn't work, but there is a work-around.

create **/etc/modprobe.d/sdhci.conf**, containing a single line:
[INDENT]options sdhci debug_quirks2="0x4"[/INDENT]

update-initramfs -u -k all

[https://www.0xf8.org/2016/01/workaround-for-broken-o2-micro-sd-card-reader-support-since-linux-kernel-version-4-1-8/](https://www.0xf8.org/2016/01/workaround-for-broken-o2-micro-sd-card-reader-support-since-linux-kernel-version-4-1-8/)

(13) [Dell 7140] Suspend doesn't work, always results in a reboot. Didn't work in Windows 8 or Ubuntu 16.04 and still doesn't work. No workaround that I know of.

[https://www.dell.com/community/Tablets-Mobile-Devices/Venue-11-Pro-7140-not-Windows-10-compatible-Bluescreens-bad/td-p/5079009](https://www.dell.com/community/Tablets-Mobile-Devices/Venue-11-Pro-7140-not-Windows-10-compatible-Bluescreens-bad/td-p/5079009)

(14) [Dell 7140] Headphones are ununsable. No workaround that I know of.

[https://ubuntuforums.org/showthread.php?t=2390372](https://ubuntuforums.org/showthread.php?t=2390372)


**[SIZE=4]Conclusion[/SIZE]**

The above may sound like a nightmare, and it certainly was more effort than I would have liked, but it has resulted in a system that does all I need and does it well. I've only been using it for a few hours, so more issues may appear, but I'm quite happy with it, for now.

---

### Post by AlpineCarver on 2018-07-27
After a week of use, I'm still very pleased with how the system is working. It has been 100% stable (as was ubuntu 16.04). Most of the problems and workarounds noted in my original post are not encountered in my daily use. The programs I use regularly are: firefox, evolution, gnome-calendar, and vlc.

Here are a few updates:

(6) I've found that I only use the Activities button right after a reboot, to set up workspaces for the apps I use regularly. After that, simply tapping the icon for a running program in the Dock bar gets me to the appropriate workspace.

(8) I've gone a week now without the system losing any touch events. Perhaps this was fixed by a software update or my everyday usage never triggers this bug.

(10) Setting browser.tabs.loadBookmarksInTabs true results in TWO new tabs every time you click a bookmark, so I've set it back to false.

(11) I've found a better workaround for authorization popups (which I get from synaptic and from keyring on reboot): cancel the popup, temporarily turn off onboard-indicator, re-do whatever caused the popup, use the default on-screen keyboard (caribou) to enter the password, then turn onboard-indicator back on. The bugs in caribou, noted in my original post, restrict which characters you can use in a password.

Of the remaining problems, the ones I would most like to see fixed are: (13) suspend and (14) headphone output and (9) thunderbird touch-scrolling.

---

### Post by QIII on 2018-07-27
Not a support request.

Moved to Ubuntu, Linux and OS Chat.

---

### Post by nobodyisnothing on 2018-09-21
Hey.
Thanks for the datails. I am wondering if things are better now. I would like to try Ubuntu on my Venue 11 Pro but don't want to spend time if the system is still not comfortable for daily use.

---

### Post by AlpineCarver on 2018-09-21
Things are still pretty much as described in this thread. For my specific use (firefox, evolution, vlc) it's working well. If you want to do lots of different things, I can't make any promises.

---

### Post by AlpineCarver on 2018-09-28
Another update:

Item #8 in my original post is still very much alive and has been biting me more lately. There are multiple things going on that result in part or all of the screen becoming unresponsive to touch events.

The Activities button (workspace switcher) works fine immediately after a reboot but quickly becomes unresponsive. This has not been much of a problem for me, because the first thing I do after a reboot is open apps in different workspaces. After that, I just click app icons in the dock to switch workspaces. You can also use a 3-finger vertical swipe to switch workspaces.

Occasionally, a tap or swipe in the dock or the top bar can get you into a mode where the whole touchscreen becomes unresponsive. The physical button doesn't help, and a single-finger tap does nothing, anywhere on the screen. Usually, I can get unstuck using random multi-finger gestures. I can't characterize a multi-finger gesture that reliably gets me unstuck, but if I sweep my fingers around on the screen enough, I usually can get unstuck.

---

### Post by AlpineCarver on 2018-09-30
> **AlpineCarver said:**
> Usually, I can get unstuck using random multi-finger gestures.

Most, maybe all, of the times the system becomes unresponsive to touch events, a menu is open. It appears that you can get unstuck by putting one finger down on the screen and using a second finger to tap the menu. At least that has worked the last couple of times I've gotten stuck.

---

### Post by drechsel on 2019-04-28
I found that you cannot use onboard keyboard with wayland, which is a pity because only with wayland you can do scaleable zooming - at a handy factor like 120 or 150% or so.
For that reason I filed a but report [here]("https://bugs.launchpad.net/onboard/+bug/1826742") - confirmation would be great.

As well, I issued a question at GNOME discourse [ here ]("https://discourse.gnome.org/t/tablet-resize-window-buttons/800/5") about resizing window buttons. Everybody is very welcome to vote for this request.
Cheers,
Wolf

---

### Post by ym-gavin on 2019-09-02
I just want to add a new one to this thread that I thought was interesting.

Just the other day I decided to break my old 7140 out of storage and put Ubuntu on it. It had done sterling service as a Windows machine but of course I wanted Linux. I followed much of what you posted above (but my SD card reader worked first install, no problems) and it seemed OK... but quickly got into a situation where it was just freezing hard. Most of the time it was happening within minutes of boot and there didn't seem to be much pattern to it. Finally I opened up a pair of SSH sessions to watch from a remote vantage point while the system was running to see if there was anything going on... watching the syslog and "top" at the same time. They symptoms were that the system would suddenly jump to 50% wait, then a few seconds later would pop up to 75 and finally hang at 98% constantly. Nothing was usable and I was forced to power cycle.

At first I thought the hard drive was going bad so I did a full badblocks from an Ubuntu live USB... it's worth noting the live USB always worked and never failed. No bad blocks. I ran the pre-boot diags for a full memory and hardware check... no problems (it's nice that Dells have this built in!) I was confused and annoyed to the point that I was ready to put Windows back on it. Finally though I decided to try again after a clean reinstall and this time I caught the following error in the syslog right as it hung;

```
Error sending ATA command CHECK POWER MODE: Unexpected sense data returned
```

Aha! Methinks... still a disk error but specifies a power issue. A bit of Googling led me to suspect Link Power Management as an issue. As a result, I did the following;

```
echo medium_power > /sys/class/scsi_host/host0/link_power_management_policy
```

It's worth noting the default is "min_power" which is obviously a decent idea on a low power machine like this, but the error I was getting certainly implied the OS was having some difficulty with the power management of the drive. As on right now, the system has been up and running for 2 and a half hours without a recurrence of the hard hang, or that error in syslog. While I'm not going to call it definitively fixed (and I've probably not done any favours to my on-battery runtime) this is definitely looking a lot more promising. Maybe this can help someone else out if they're planning to put Ubuntu on their 7140.

I should note that it was still crashing on a clean install as above.

---

### Post by leowun on 2020-03-19
Hi, I want to ask a similar question, I worked with the SD reader on a PC, everything was fine.
But after I bought a Asus P15 laptop and started connecting to it. Then periodically when reading files, the system starts to hang.
With USB, everything is OK, the reader does not give an error.
I am a noob in the subject and if you can help determine what the problem is, I will be grateful
using [Kingston FCR-HS4]("https://www.bestadvisor.com/memory-card-readers")
tried to find problems with USB Ubuntu, but i didn't see anything.

---

