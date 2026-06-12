---
title: "No updates in nearly two weeks"
date: 2010-05-26
forum: Security
---

### Post by QwUo173Hy on 2010-05-26
According to the [release notes]("http://www.ubuntu.com/getubuntu/releasenotes/1004"), I should be getting updates at least weekly:
> Ubuntu 10.04 LTS launches update-manager  directly to handle package updates, instead of displaying a  notification icon in the GNOME panel.  Users are notified of security  updates on a daily basis, but for updates that are not security-related,  users will only be prompted once a week.  
But I haven't had anything in about two weeks. I have installed some software via the command line with apt-get. Could that be interfering with my updates?

---

### Post by frncz on 2010-05-26
Every few days, i run, in terminal


sudo apt-get update && sudo apt-get upgrade

This seems to be quite an effective way to get the latest updates

Regards

Mike

---

### Post by QwUo173Hy on 2010-05-26
Thanks Mike,

But if the release notes say that notifications are automatic, then I'd like to find out what the problem is and fix it.

Regards,
Jarlath

---

### Post by frncz on 2010-05-26
Have you checked 'settings' in System> Administration > Update Manager ?

The right boxes need to be ticked...

---

### Post by quacked on 2010-05-26
I too was having a problem receiving notifications about updates,, What I had to do was to check the software sources and uncheck some of the repositories that were enabled to receive the updates,, I believe,,,, third party,,,, and there were also sofware restricted by copyright or legal issues,,, ( I had checked at one time,,,),,, In either case,,, you'll have to check which repositories you have enabled,, and enable only the Main,,, and maybe ,, "a"  partner repository to get updates,,,

---

### Post by QwUo173Hy on 2010-05-26
Mike - I do have the boxes ticked to receive updates. So there's something else causing this.

Quacked - Thanks, I've disabled third party software and everything else except Main. If that works, I'll enable them one at a time until I figure out the problem. I think it's quite serious that I'm told that I will be kept secure on a daily basis, but a hidden condition exists which can prevent that. When I find the problem, I'll report it ;)

Thanks again,
Jarlath

---

### Post by crong on 2010-05-26
I agree that something is lacking here.

I installed Ubuntu 10.04 on a laptop 18 days ago and had not seen any updates. When I installed it I had chosen to install security updates automatically but just to be sure I started Update Manager manually and was greeted with "Your system is up-to-date"

"Oh good!" I thought, "the security updates really are being installed automatically in the background as the installation seemed to have promised."

But I also noticed that it said "The package information was last updated 18 days ago" so I had the presence of mind to click the "Check" button and to my great disappointment a bunch of security updates were presented to me.

You know, this is stupidly deceptive - don't tell me my system is up-to-date when it quite clearly isn't.

I checked all the settings in Update Manager and they seem to be correct.

Automatic updates aren't really automatic if we have to manually update the package info to get them (unless, of course, it's me being a stupid noob).

---

### Post by kleskjr on 2010-05-26
maybe you can check in System->Preferences->startup applications for Update Notifier. although mine is off because I prefer to do it manually.

---

### Post by crong on 2010-05-26
Yes, it is there & checked.

I have to say, though, that I'm a bit confused about the difference between package info and updates - I'm sure it's important.

---

### Post by uRock on 2010-05-26
I had about 10MB worth of updates today.

---

### Post by QwUo173Hy on 2010-05-26
Crong, what repositories have you selected other than main? Also, are you using any PPAs? I think that might be whats preventing the update-manager launching.

uRock, did update-manager launch itself to alert you or did you have to check manually?

---

### Post by OpSecShellshock on 2010-05-26
There are two (that I've seen) kinds of updates: security updates and "recommended" updates. If the security box is checked, then that kind of update will be looked for on a regular basis (mine does once a day). However, not all updates are specifically for security reasons, so any that aren't won't fall under that. In my experience, when there's an actual security update available, the Update Manager opens and blinks in the panel until I notice it and install the update. The installation is still a manual process, because you have to elevate privileges in order to do it. It just automatically checks and lets you know.

I also use update manager to check for non-security updates every day, which is entirely manual. It's just something I've had to develop as a habit when I log in at home.

---

### Post by uRock on 2010-05-26
> **jarlath said:**
> Crong, what repositories have you selected other than main? Also, are you using any PPAs? I think that might be whats preventing the update-manager launching.

uRock, did update-manager launch itself to alert you or did you have to check manually?

On my desktop it runs automatically and the Netboot is set to be run manually.

---

### Post by QwUo173Hy on 2010-05-27
> **uRock said:**
> On my desktop it runs automatically and the Netboot is set to be run manually.
uRock, do you have any PPAs enabled? Also, do you have Main, Restricted, Universe, Multiverse or Source ticked in your software sources?

I only have Main enabled at the moment to see what behaviour I get.

---

### Post by howefield on 2010-05-27
> **jarlath said:**
> But I haven't had anything in about two weeks.

A clean install last night of 10.04 had 97 updates waiting for my system, only 5 were security updates, the rest were recommended.

I don't know when the 5 security ones become available, perhaps there haven't been any updates in your 2 week time frame.

---

### Post by Rifester on 2010-05-27
I think what Jarlath is trying to state is that NOTIFICATION of available updates has not taken place.   I have also posted a thread about this.   I have not been notified of security updates once in Lucid.   I was told it was a known issue, and then another person stated there was a change in Lucid where you will only be notified once a week instead of daily...

---

### Post by howefield on 2010-05-27
> **Rifester said:**
> I think what Jarlath is trying to state is that NOTIFICATION of available updates has not taken place. 

Yes, I had it mind that jarlath was only looking for security updates, but it was another poster who mentioned that. My mistake.

---

### Post by QwUo173Hy on 2010-05-27
I doubt very much that it has changed. It's in the release notes that security is daily - others weekly. I'll have a look at launchpad at some stage and see if there's anyone there with the same problem.

---

### Post by SteamInc on 2010-05-27
Yea man I have the same problem I have to manually check for updates every day.

---

### Post by rookcifer on 2010-05-27
Same problem here.  This is my first time using Gnome in many years (I usually use KDE) and I just thought my lack of updates was was me doing something wrong. 

I have always just used the terminal to manually update, but would like to understand what's up here.

> **quacked said:**
> I too was having a problem receiving notifications about updates,, What I had to do was to check the software sources and uncheck some of the repositories that were enabled to receive the updates,, 

This doesn't seem like much of a solution.  Why should I have to uncheck my third party repos just to get updates?  I want everything updated at once.

---

### Post by ptn107 on 2010-05-27
Just because the update manager will prompt you of any pending updates *at least* once a week doesn't mean that there must be an update released every week.  You could go weeks without a bug fix or security patch if there is nothing to fix.

---

### Post by uRock on 2010-05-27
> **ptn107 said:**
> Just because the update manager will prompt you of any pending updates *at least* once a week doesn't mean that there must be an update released every week.  You could go weeks without a bug fix or security patch if there is nothing to fix.

The complaint was made the same day as two of my machine got 10MB updates. I think it is a valid problem.

---

### Post by SteamInc on 2010-05-28
It is best if it were fixed, some people forget about updates and something bad happens.

---

### Post by ptn107 on 2010-05-28
There is nothing to fix.  That is the intended function of the update manager.  If you really just want to apply the updates when they are downloaded (without the wait or prompt), edit 
/etc/apt/apt.conf.d/50unattended-upgrades and change:
```
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu lucid-security";
//	"Ubuntu lucid-updates";
};
```
to
```
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu lucid-security";
	"Ubuntu lucid-updates";
};
```
and save.

---

### Post by QwUo173Hy on 2010-05-28
> **ptn107 said:**
> There is nothing to fix.  That is the intended function of the update manager.  If you really just want to apply the updates when they are downloaded (without the wait or prompt), edit 
/etc/apt/apt.conf.d/50unattended-upgrades and change:...
ptn107, I think you're missing the point. There notification is independent of the time of availability of the update. The notification depends on the set interval expiring and the availability of update together.

This is not happening. I should have had at least one notification within the two weeks.

---

### Post by pr0t3g3 on 2010-05-29
> **frncz said:**
> Have you checked 'settings' in System> Administration > Update Manager ?

The right boxes need to be ticked...
You say the 'right' boxes... 

1. How do we know what the right boxes are....
2. Since there are (for me)  3000+ boxes to click is there an easy way; I tried, ctrl + a
but that seems to work when there is only a small amount of packages; when there are less than 20 or so there is a white space that I can use ctrl + a to select all pacakges..

---

### Post by OpSecShellshock on 2010-05-29
> **pr0t3g3 said:**
> You say the 'right' boxes... 

1. How do we know what the right boxes are....
2. Since there are (for me)  3000+ boxes to click is there an easy way; I tried, ctrl + a
but that seems to work when there is only a small amount of packages; when there are less than 20 or so there is a white space that I can use ctrl + a to select all pacakges..

Not sure you're talking about the same thing. In System-->administration-->Update Manager if you just open it up nothing really happens. In the lower left there's a settings button. If you click that, it will ask for the admin password, then it will open the settings window. There should be a tab called Updates. You can set the types of updates, which by default I think includes Important security and Recommended. You can set it to check daily, and can also set it up to install automatically from the look of things. I don't usually do that, because I like to know what I'm updating and when. I think that still only applies to the Important Security updates though.

Beyond that I'm not sure what can be done. I manually check as part of my daily routine anyway. On most days there are no updates available. It's really not remarkable to go for a long time without seeing one. I just went to Update Manager under the menu and then dragged that to the panel which created a launcher. I hit the launcher when I log in every day and it does its thing. In the case of security updates it's already open when I get home. Bug fixes and tweaks that aren't security related won't cause that to happen.

---

### Post by crong on 2010-06-13
I have two Ubuntu installations here.

The one with the wired Ethernet connection does start the update manager from time-to-time but only after a restart, i.e. there seems to be no periodic polling for updates which strikes me as kinda stupid because, unlike Windows, I don't expect to need to keep restarting my Linux machines.

The other installation which has a wireless connection never starts the update-manager. Could it be that that the update manager starts before the wireless connection is established, assumes there is no connection to the Internet and aborts?

---

### Post by OpSecShellshock on 2010-06-13
> **crong said:**
> I have two Ubuntu installations here.

The one with the wired Ethernet connection does start the update manager from time-to-time but only after a restart, i.e. there seems to be no periodic polling for updates which strikes me as kinda stupid because, unlike Windows, I don't expect to need to keep restarting my Linux machines.

The other installation which has a wireless connection never starts the update-manager. Could it be that that the update manager starts before the wireless connection is established, assumes there is no connection to the Internet and aborts?

As far as I know, the update manager runs as a cron job, so it's set to run at a specific time of day. If your computer with the wireless-only connection is in suspension, hibernation, or is shut down at the time it's set to run, then I suppose it could just run into the same issue every day.

---

### Post by QwUo173Hy on 2010-06-14
My two machines are wireless, so that sounds plausible.

I've asked here: [https://answers.launchpad.net/ubuntu/+source/update-manager/+question/114609](https://answers.launchpad.net/ubuntu/+source/update-manager/+question/114609)

---

### Post by tom56 on 2010-06-21
I'm curious - what happened here?

I installed 10.04 about 2 hours ago, and I still haven't received any notification/pop-up to install updates. 2 hours may not seem all that long an amount of time, but if you only use your computer for 2 hours a day then when is it going to install the updates?

---

### Post by Rubi1200 on 2010-06-21
> **tom56 said:**
> I'm curious - what happened here?

I installed 10.04 about 2 hours ago, and I still haven't received any notification/pop-up to install updates. 2 hours may not seem all that long an amount of time, but if you only use your computer for 2 hours a day then when is it going to install the updates?

You could go to System > Administration > Update Manager and start the process manually.

---

### Post by FuturePilot on 2010-06-21
Are any of you with this problem using a laptop on battery power? It will not check for updates if you're on battery power.

---

### Post by tom56 on 2010-06-21
> **Rubi1200 said:**
> You could go to System > Administration > Update Manager and start the process manually.

Sure, but it's meant to start automatically, so there's clearly something going wrong somewhere.

---

### Post by montysan on 2010-06-21
I have this problem as well. [Thread here.]("http://ubuntuforums.org/showthread.php?t=1504892")

I never had any problems like this with Karmic, and I don't think anything should have changed since then?

Run 'sudo apt-get update', and Update Manager will appear if there are any security updates to install. Surely this means it's either not running at startup, is failing in some way, or something else is supposed to do a similar job?

---

### Post by tom56 on 2010-06-22
montysan is right - running apt-get update manually pushes Update Manager into prompting

I filed a bug - [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/597247](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/597247)

---

### Post by cariboo on 2010-06-22
I was just looking at the Lucid release notes, does reverting how updates works to the previous way by using the following command:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

Make any difference?

---

### Post by QwUo173Hy on 2010-06-22
> **FuturePilot said:**
> Are any of you with this problem using a laptop on battery power? It will not check for updates if you're on battery power.
Really? I'm always on battery power. I only plug it in at night when it's switched off. That means I'll never get updates .. sounds a bit odd.

---

### Post by FuturePilot on 2010-06-22
> **jarlath said:**
> Really? I'm always on battery power. I only plug it in at night when it's switched off. That means I'll never get updates .. sounds a bit odd.

There's where the problem lies. Perhaps you can plug it in while it's on for a few minutes at night. It will usually check within 5-10 minutes after being plugged in.

---

### Post by QwUo173Hy on 2010-06-22
> **FuturePilot said:**
> There's where the problem lies. Perhaps you can plug it on while it's on for a few minutes at night. It will usually check within 5-10 minutes after being plugged it.Thank you FP!

---

### Post by oldsoundguy on 2010-06-22
There has been a gang of updates over the past two Tuesdays .. a bunch of cups stuff today, for instance.

Quick way is to go System> Administration> Update manager .. (that will not shut the auto update system off!!)

---

