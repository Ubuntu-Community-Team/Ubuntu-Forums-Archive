---
title: "Daily ISO"
date: 2017-08-07
forum: Ubuntu Development Version
---

### Post by P-I H on 2017-08-07
- I installed the Daily Build from aug 4. The installation and boot of the installed version went OK.
- Had some problems with Ubuntu Software. Search didn't work as expected. Problems to find Chromium and Steam. However this improved after some updates.
- Installed the extensions "Dash to Dock" and "Topicons plus" to get an experience similar to Unity.
- Installed some extensions to get a better experience: "Alternatetab", "Better volume indicator", "OpenWeather", "System-monitor", "Email message tray" and "No topleft hot corner".
- Installed and tried some applications: Gnome Tweaks, Synaptic, Psensor, Steam and CIV VI, snap version of Kodi 18.0-ALPHA1, Spotify, and Handbrake.
- Got the problem with Ubuntu and Ubuntu Wayland sign in, [https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157). Couldn't change location in OpenWeather and set an icon for Kodi in Dash to Dock.
- Used it daily during some days and it behaves well.
```
p-i@pi-MS-7A34:~$ systemd-analyze
Startup finished in 16.479s (firmware) + 5.671s (loader) + 3.194s (kernel) + 8.023s (userspace) = 33.369s
p-i@pi-MS-7A34:~$

```
The time for the loader depends on how fast you hit the return key in the grub menu.

---

### Post by mc4man on 2017-08-07
That's better than I saw with image from a day or so earlier. In that case the $Home folder was basically empty on the initial login which is wayland
(- even though it says ubuntu..) Only had the Desktop & . folders.
Doing an actual login to 'ubuntu' (X11) populated $HOME as expected.

Not sure why they're taking so long to address the login mess, pretty soon it'll have to be - 
ubuntu (the new default of wayland
X11 on ubuntu

So maybe they'll wait & attempt to get it right once

---

### Post by P-I H on 2017-08-07
I had the same problem with an empty $Home after first login, but later it was OK. I suppose after login to ubuntu (X11), as in your case.

---

### Post by mc4man on 2017-08-07
> **P-I H said:**
> I had the same problem with an empty $Home after first login, but later it was OK. I suppose after login to ubuntu (X11), as in your case.
Oh, so it's still happening. Have a bug on, no action
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1708569](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1708569)
Guess they'll square things away at some point this month

---

### Post by Cavsfan on 2017-08-07
I got this and didn't realize it. I created the folders in Home directory. 

I me tooed the bug, which only has 2 people on it now and there *should* be many more.

---

### Post by mc4man on 2017-08-07
Ubiquity likely was wrong source though was not sure what to use (- wayland is not a bug source
So just added gnome-session which may be more appropriate
(- note to others: if starting a bug involving wayland just tag it wayland or wayland-session

---

### Post by P-I H on 2017-08-19
I installed the 19/8 ISO.
The installation takes less than 10 minutes and works fine.
This ISO include the Ubuntu dock and the window controls are to the right.
Active applications are marked with a red dot.
The new control center isn't available yet.


At the login the session is marked as Ubuntu, but I suppose it's a wayland session. To get the Ubuntu session you have to logout, login to Ubuntu on Wayland, logout and then login to Ubuntu.


In the first session, wayland session?, funtions do not work according to expectations 
- the Gnome Software icon is used instead of the Ubuntu Software icon
- Synaptic doesn't work
- there are no Shell extensions
- you have to search to times to find packages e.g. Synaptic


In the Ubuntu session I got an error message when using Synaptic
"W: Download is performed unsandboxed as root as file '/var/cache/apt/archives/partial/lm-sensors_1%3a3.4.0-4_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)"
However the installation of lm-sensors went OK.


Installation of these shell extensions went OK
- Topicons plus
- Weather
- System-monitor


Installation of Kodi in snap version also went OK.


Ubuntu dock was marked as off in Tweak tool, but worked OK.

This is how it looks

---

### Post by mc4man on 2017-08-19
> **P-I H said:**
> I installed the 19/8 ISO.


At the login the session is marked as Ubuntu, but I suppose it's a wayland session. To get the Ubuntu session you have to logout, login to Ubuntu on Wayland, logout and then login to Ubuntu.



In the Ubuntu session I got an error message when using Synaptic
"W: Download is performed unsandboxed as root as file '/var/cache/apt/archives/partial/lm-sensors_1%3a3.4.0-4_amd64.deb' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)"
However the installation of lm-sensors went OK.




Haven't tried recently but (at least before) you just needed to switch back & forth at the login screen, no need to actually login
In other words - 
The login screen always shows "ubuntu" no matter what
So to assure a ubuntu (X11) session just switch at login to ubuntu on wayland, switch back to ubuntu.
(- still an open bug
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1705157)

That sandbox warning on sunaptic has been happening for some time, doesn't affect use in any way, at least to date.

---

### Post by Cavsfan on 2017-08-19
I decided to install the daily ISO also dated today 9/18.

I have just 2 login options Ubuntu (X11) and Ubuntu with Wayland.

The bar on the left is similar to Unity and does not go away like it did on the previous install.
It did on one session, I forget what it was called and the other did like this where the panel is visable.

I installed Vivaldi as a .DEB file with Ubuntu Software and that worked well.
Have not tried installing anything else with it.

[ATTACH=CONFIG]276458[/ATTACH]

---

### Post by P-I H on 2017-08-22
Tried to install the 22/9 ISO, but it didn't work. Got wrong location. Normally I get Stockholm, but this time I got New York. Didn't dare to continue the installation.
Many other locations are missing. like Paris and London.
Never seen this before.

Edit: Installed the 19/8 ISO instead. Worked fine

---

### Post by ventrical on 2017-08-22
> **Cavsfan said:**
> I decided to install the daily ISO also dated today 9/18.

I have just 2 login options Ubuntu (X11) and Ubuntu with Wayland.

The bar on the left is similar to Unity and does not go away like it did on the previous install.
It did on one session, I forget what it was called and the other did like this where the panel is visable.

I installed Vivaldi as a .DEB file with Ubuntu Software and that worked well.
Have not tried installing anything else with it.

[ATTACH=CONFIG]276458[/ATTACH]


I installed the 8/22 daily. Got basically the same thing.  Very smooth install.  It's unity with a supercharger! :)

Regards..

---

### Post by Chanath on 2017-08-22
> **ventrical said:**
> I installed the 8/22 daily. Got basically the same thing.  Very smooth install.  It's unity with a supercharger! :)

Regards..

I am writing from Live Ubuntu 17.10. It doesn't look yet as good as Unity. The "Ubuntu Dock" is too wide, there is no Appearance Settings to make it thinner, as it was in Unity Launcher. You can see that the screen area had become much smaller, without the ability to autohide the Ubuntu dock. Also, if you install Hide Top Bar extension, the top of the Ubuntu Dock would go up and the hiding top panel would cover it, when unhiding. Maybe Ubuntu devs would make this "Ubuntu Dock" as nice as the Unity Launcher.

---

### Post by Frogs Hair on 2017-08-22
As written in the text associated with the dock I switched to the dash to dock extension to get more control over the settings.

---

### Post by P-I H on 2017-08-22
There are  three settings in Settings/Displays.
- Change icon size
- Set Auto-hide on or off
- Set placement

---

### Post by Frogs Hair on 2017-08-22
> **P-I H said:**
> There are  three settings in Settings/Displays.
- Change icon size
- Set Auto-hide on or off
- Set placement

Thanks, now I can try night mode. ;)

---

### Post by Chanath on 2017-08-22
> **P-I H said:**
> There are  three settings in Settings/Displays.
- Change icon size
- Set Auto-hide on or off
- Set placement

I found it. Thanks.
There'd be more surprises in default Ubuntu, I believe.

---

### Post by ventrical on 2017-08-22
This new supercharged prelude could mean that something may be afoot with Unity7.  If devs can successfully intergrate the  Uni-dock (remember .. you heard Uni-Dock here first) :) then  it could spell a possible bon voyage for Unity come the next cycle but  many of the concepts of Unity would be incorporated into the Gnome DE and so  there would naturally be an environment of harmony and good will within the development community as well as the End_User public at large which I think the founders are striving to create.

Regards..

---

### Post by Chanath on 2017-08-22
> **ventrical said:**
> This new supercharged prelude could mean that something may be afoot with Unity7.  If devs can successfully intergrate the  Uni-dock (remember .. you heard Uni-Dock here first) :) then  it could spell a possible bon voyage for Unity come the next cycle but  many of the concepts of Unity would be incorporated into the Gnome DE and so  there would naturally be an environment of harmony and good will within the development community as well as the End_User public at large which I think the founders are striving to create.

Regards..

It also shows that the idea behind Unity was a good one. :)

---

### Post by ventrical on 2017-08-22
> **Chanath said:**
> It also shows that the idea behind Unity was a good one. :)

+1 Absolutely.  I mean why abandon such a solid infrastructure and effervescent experience where one can actually get work done and enjoy doing it?  Lets face it.. unity in real time  freed us from the chains and madness of several security deficient commercial operating systems that dominated the market for a long time. It put a lot of hardware to work that was otherwise ready for the recycle yard and Canonicals economic approach saved a lot of people  a lot of money  and brought a comprehensive DE to parts of the world that would other wise have none.

Regards..

---

### Post by jbicha on 2017-08-23
Chanath or anyone, please try to file bugs when you see issues. &#55357;&#56898;

---

### Post by P-I H on 2017-08-26
Installed Daily ISO:s from 25/8 and 26/8.
Both installs OK, but gnome-software isn't working OK and this makes it hard to use the installation.
Filed a bug [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1713249](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1713249).

At first start after installation the Ubuntu session is marked as used, but the command echo $DESKTOP_SESSION gives the answer ubuntu-xorg. After logout mark of Ubuntu on Xorg and then Ubuntu the command gives the answer ubuntu. I suppose ubuntu = wayland.

---

### Post by mc4man on 2017-08-26
> **P-I H said:**
> Installed Daily ISO:s from 25/8 and 26/8.
Both installs OK, but gnome-software isn't working OK and this makes it hard to use the installation.
Filed a bug [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1713249](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1713249).

At first start after installation the Ubuntu session is marked as used, but the command echo $DESKTOP_SESSION gives the answer ubuntu-xorg. After logout mark of Ubuntu on Xorg and then Ubuntu the command gives the answer ubuntu. I suppose ubuntu = wayland.

The default is now wayland (session ubuntu
If 1st run after install produces ubuntu-xorg then that's not intended. (haven't tried lately myself

If so. ?? then possibly results from installing via the 'try..' live session vs. just installing directly  as live sessions are currently ubuntu-xorg, not wayland. (the live session installer can't work on wayland..

---

### Post by mc4man on 2017-08-26
Additionally I view this as a release blocker if not fixed (again haven't tried recently
[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1706939](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1706939)

---

### Post by mc4man on 2017-08-26
Just tried new image,just as screwed up as previously but now ubuntu-xorg is the session most likely to be used (even if the login option says ubuntu..

---

### Post by ventrical on 2017-08-26
> **mc4man said:**
> Just tried new image,just as screwed up as previously but now ubuntu-xorg is the session most likely to be used (even if the login option says ubuntu..

Without a firewall , wayland becomes a security issue, even with xhost script because you have to close it each time.

---

### Post by P-I H on 2017-09-02
Installed 2/9 ISO today.
Installation was OK, but I didn't get the message to remove the installation media.

Software still don't work as expected. Not able to install Dropbox and Chromium with Software. 
"Gnome Packages" installs OK, and I used this package to install Dropbox and Chromium.
These packages are essential to me as my configuration information is in Dropbox and my bookmarks are in Chrome/Chromium.
The search function in "Gnome Packages" don't work that well. The best way I found out to get Dropbox was to search for Nautilus.

The tab for "gnome extensions", that earlier was available in Software, is removed. Extensions e.g. "Weather" and "Topicons Plus" are however found with the search function.

My printer Brother HL-3140CW was installed automatically and worked. That's really nice. Before I did use a script from Brother to do the installation.

---

### Post by jbicha on 2017-09-02
> **P-I H said:**
> The tab for "gnome extensions", that earlier was available in Software, is removed.

That's [LP: #1713285]("https://launchpad.net/bugs/1713285")

---

### Post by Chanath on 2017-09-03
> **P-I H said:**
> There are  three settings in Settings/Displays.
- Change icon size
- Set Auto-hide on or off
- Set placement

This is gone now  from Settings/Displays, except the night light, right?

---

### Post by P-I H on 2017-09-03
The settings are still available. Both on the 2/9 ISO and an older installation.
In Launcher placement it's only possible to select display.

---

### Post by cariboo on 2017-09-03
I installed the daily ISO on a Gateway laptop yesterday, and everything worked as it should except for cheese, the picture was awfully dark. I could find a way to move the dock, so installed Dash to Dock, and got it back where I wanted it.

---

### Post by jbicha on 2017-09-03
> **Chanath said:**
> This is gone now  from Settings/Displays, except the night light, right?

Yes, if you're using the GNOME3 Staging PPA for artful because the Ubuntu Dock settings patch hasn't been updated yet.

---

### Post by Chanath on 2017-09-03
> **jbicha said:**
> Yes, if you're using the GNOME3 Staging PPA for artful because the Ubuntu Dock settings patch hasn't been updated yet.

Why should I use GNOME3 Staging PPA, when Gnome shell, Ubuntu session etc are right there in the repos? And, that's one of the reason to use Synaptic,to know what's available in the repos.

---

### Post by amano on 2017-09-03
Well for ... testing? Isn't that the reason we are all here?

Some apps are still not updated in the release pocket. E. g. GNOME builder. You need to use the PPA if you want to test that.

---

### Post by Chanath on 2017-09-04
> **amano said:**
> Well for ... testing? Isn't that the reason we are all here?

Some apps are still not updated in the release pocket. E. g. GNOME builder. You need to use the PPA if you want to test that.

Not exactly, as Gnome-shell is in the 17.10 repos. 
Gnome shell version is 3.25.91, the same as in the last Ubuntu (default) daily iso.

The Gnome shell, Ubuntu session etc installed from the repos don't have the following.
> [COLOR=#000000]*Change icon size*[/COLOR]
[COLOR=#000000]*Set Auto-hide on or off*[/COLOR]
[COLOR=#000000]*Set placement*[/COLOR]

I downloaded the last Ubuntu daily to check this out. In that, of course, the above was in the Settings/Displays.

Gnome shell had been there for a long time; there are umpteen extensions and rising. Those, who are used to experiment would always try out the extensions. Few uninitiated or lazy would use the "default" setup. As most of the Linux users are experimenters, the "default" Ubuntu setup would be gone very quickly. When there are too many toys to play with, this is inevitable.

---

### Post by ventrical on 2017-09-04
> **Chanath said:**
> Not exactly, as Gnome-shell is in the 17.10 repos. 
Gnome shell version is 3.25.91, the same as in the last Ubuntu (default) daily iso.

The Gnome shell, Ubuntu session etc installed from the repos don't have the following.


I downloaded the last Ubuntu daily to check this out. In that, of course, the above was in the Settings/Displays.

Gnome shell had been there for a long time; there are umpteen extensions and rising. Those, who are used to experiment would always try out the extensions. Few uninitiated or lazy would use the "default" setup. As most of the Linux users are experimenters, the "default" Ubuntu setup would be gone very quickly. When there are too many toys to play with, this is inevitable.

It is slowly coming along where a lot of unity's ideas will be factored into gnome-shell so it may eventually get honed down to a 'look and behaviour' type gadget in systems settings, but that may not happen well into the 18.04 cycle.

Regards..

---

### Post by ventrical on 2017-09-05
In the daily install the icons under the side dock now justify after you click 'show applications'. This taking place in the live session.

Regards..

---

### Post by P-I H on 2017-09-15
Installed the 25/9 ISO.
No problems with the installation.
The installed system started with Wayland
Software worked OK, installed Tweak Tool, Dropbox and Chromium
Installed these packages with apt: lm-sensors, gnome-gmail and gir1.2-gtop-2.0
Used [https://extensions.gnome.org/](https://extensions.gnome.org/) to install these extensions: Weather, Alternate Tab and system-monitor
Installed Spotify according to [https://www.spotify.com/se/download/linux/](https://www.spotify.com/se/download/linux/)
Installed kodi and Steam with Software

My Brother printer HL-3140CW didn't install automatically as with the 2/9 ISO. I didn't manage to do the installation with Settings/Device/Printer. Had to use Brother's script.

---

### Post by Cavsfan on 2017-09-19
Time has gotten by me and I did not realize that the beta 1 had been released.
Anyway, I tried to install the daily Xubuntu 17.10 ISO from a USB stick yesterday. I've used this method many times without fail until now.
It brought the GUI up for several seconds like normal but, after a bit it went to terminal.
Displaying "A start job is running for Ubuntu LiveCD installer with no limit."
So, I gave it 20 minutes and gave up, hit the reset button and downloaded the beta 1 ISO from August 31 and it did the same thing.

Today I downloaded the daily Xubuntu ISO and thought I'd give it another try. 
After some time it displayed "Starting cleanup of temporary directories" and went back to the first message.

Then after some time it displayed "Starting message of the day" and went back to the first message.

Then after some time it displayed "Started run Anacron jobs" about 51 minutes into it and went back to the first message.
I gave it 2 hours before quitting. Was I supposed to give it 3 hours 4 hours or more?

Geez that was painful to watch...

---

### Post by ventrical on 2017-09-19
> **Cavsfan said:**
> Time has gotten by me and I did not realize that the beta 1 had been released.
Anyway, I tried to install the daily Xubuntu 17.10 ISO from a USB stick yesterday. I've used this method many times without fail until now.
It brought the GUI up for several seconds like normal but, after a bit it went to terminal.
Displaying "A start job is running for Ubuntu LiveCD installer with no limit."
So, I gave it 20 minutes and gave up, hit the reset button and downloaded the beta 1 ISO from August 31 and it did the same thing.

Today I downloaded the daily Xubuntu ISO and thought I'd give it another try. 
After some time it displayed "Starting cleanup of temporary directories" and went back to the first message.

Then after some time it displayed "Starting message of the day" and went back to the first message.

Then after some time it displayed "Started run Anacron jobs" about 51 minutes into it and went back to the first message.
I gave it 2 hours before quitting. Was I supposed to give it 3 hours 4 hours or more?

Geez that was painful to watch...

Yes i had some of the similar from yesterday xubuntu daily but it eventually booted. and I did hard install. I think its busted or something. Too bad cus I really like it so I get discouraged ya know .. when I see that stuff.

Regards..

---

### Post by Chanath on 2017-09-19
> **ventrical said:**
> Yes i had some of the similar from yesterday xubuntu daily but it eventually booted. and I did hard install. I think its busted or something. Too bad cus I really like it so I get discouraged ya know .. when I see that stuff.

Regards..

Simply put the computer off and put the usb back in and boot. It'd boot. If it doesn't, it could be bad download, or bad burning, or even a faulty usb slot.

---

### Post by ventrical on 2017-09-19
> **Chanath said:**
> Simply put the computer off and put the usb back in and boot. It'd boot. If it doesn't, it could be bad download, or bad burning, or even a faulty usb slot.

No .. it is broke iso. Tried it on different machine . got same thing as cavsfan.

edit: "No errors found" when testing disk from nomodeset.

---

### Post by ventrical on 2017-09-19
> **Cavsfan said:**
> Time has gotten by me and I did not realize that the beta 1 had been released.
Anyway, I tried to install the daily Xubuntu 17.10 ISO from a USB stick yesterday. I've used this method many times without fail until now.
It brought the GUI up for several seconds like normal but, after a bit it went to terminal.
Displaying "A start job is running for Ubuntu LiveCD installer with no limit."
So, I gave it 20 minutes and gave up, hit the reset button and downloaded the beta 1 ISO from August 31 and it did the same thing.

Today I downloaded the daily Xubuntu ISO and thought I'd give it another try. 
After some time it displayed "Starting cleanup of temporary directories" and went back to the first message.

Then after some time it displayed "Starting message of the day" and went back to the first message.

Then after some time it displayed "Started run Anacron jobs" about 51 minutes into it and went back to the first message.
I gave it 2 hours before quitting. Was I supposed to give it 3 hours 4 hours or more?

Geez that was painful to watch...

@cavsfan

I used nomodeset technique. Just keep hitting right shift key and it will boot into nomodeset screen. I am writing this from live session now on same iso I downloaded yesterday.

---

### Post by Cavsfan on 2017-09-19
> **Chanath said:**
> Simply put the computer off and put the usb back in and boot. It'd boot. If it doesn't, it could be bad download, or bad burning, or even a faulty usb slot.

3 downloaded ISOs? Each time I restarted and went into BIOS to select the USB stick as 1st choice.

But, I'll give that a try and in another USB slot...

---

### Post by Cavsfan on 2017-09-19
> **ventrical said:**
> @cavsfan

I used nomodeset technique. Just keep hitting right shift key and it will boot into nomodeset screen. I am writing this from live session now on same iso I downloaded yesterday.

Thanks! I'll try that! I should have seen if there were more posts in this thread before I went off. Glad to know it's not just me though! :)

---

### Post by Cavsfan on 2017-09-19
@[COLOR=#000000]ventrical, I was able to get a menu to come up and was able to select [/COLOR][COLOR=#000000]nomodeset[/COLOR][COLOR=#000000] but, it would not go to a live session.
I had no mouse and barely keyboard commands at first until I selected live session, then nothing.

I'll give it a few days because there are obviously problems with the ISO.[/COLOR]

---

### Post by ventrical on 2017-09-19
> **Cavsfan said:**
> @[COLOR=#000000]ventrical, I was able to get a menu to come up and was able to select [/COLOR][COLOR=#000000]nomodeset[/COLOR][COLOR=#000000] but, it would not go to a live session.
I had no mouse and barely keyboard commands at first until I selected live session, then nothing.

I'll give it a few days because there are obviously problems with the ISO.[/COLOR]

+1

Agreed.

---

