---
title: "HOWTO: Disable password request after suspend"
date: 2010-04-30
forum: Tutorials
---

### Post by tom4everitt on 2010-04-30
An annoying feature/bug of Ubuntu is:

When the computer resumes from suspend, the screen will be locked. In fact, the screen will be locked even if you have enabled automatic login and set the computer not-to-lock, when screen saver is activated.

Initially this post only included my own solution, but for convenience I've also added the (IMO) most promising solutions suggested by other users in this thread as well. If none of these suggestions worked for you, and you've found another solution that does, please post it here so I can add it as well. 

[B]
How to fix? [/B]

**10.04 Solution**

1. As you've probably already done, uncheck:
"lock screen when screen saver is activated" 
in the System->Preferences->Screen Saver menu.

2. Type gconf-editor in a terminal. Under apps/gnome-power-manager/locks check: 
"use_screensaver_settings". 

3. If still asked for password, you can (also in gconf-editor) go to desktop/gnome/lockdown and check: 
"disable_lock_screen"
Credit to itslofty below for this tip!

PS. For some reason my mouse doesn't show up after resume. To get it back I just switch to another workspace and then back again, i.e: ctrl+alt+rightarrow and then ctrl+alt+leftarrow.


**11.10 Solution**

1. First try the Lock/Unlock button in System Settings -> Personal -> Screen (suggested by brallan, below). 

2. If this doesn't work, try the command
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'

```
see RaymandJr's [post]("http://ubuntuforums.org/showpost.php?p=11415325&postcount=34") below for further info.

---

### Post by MetroPietro on 2010-05-02
...same solution, slightly different method: 
Under System > Preferences I don't have a "screensaver" control panel enabled, but I can access it through Gconf.
I start gconf from an icon that I enabled: 
Applications > System Tools > Configuration Editor
Then:
Under apps/gnome-power-manager/locks, check:
"use_screensaver_settings".
And then:
Under apps/gnome-screensaver, uncheck:
"lock_enabled".
Thanks for the lead on this, tom4everitt!

---

### Post by oldwismn on 2010-05-03
The method described by tom4everitt to disable lock after resume from suspend works for me when I suspend with ctrl-alt-delete, but not when I suspend by clicking the power button.

This is not a critical problem, but stumped me until I discovered the work around.

---

### Post by Crispy2 on 2010-05-03
Clean install of 10.4 nettop ed I can confirm suspend still wants a password even with all the correct options check/unchecked in gconf.

Please someone a solution.

---

### Post by Herman on 2010-05-03
EDIT: Reply not relevant to thread title, deleted.

---

### Post by tom4everitt on 2010-05-04
Apparently there is one more place where you can disable the password request. In the file /etc/default/acpi-support there is a line
```

LOCK_SCREEN=true

```
which can be commented out to disable screen lock. So just put a '#' in front of it, making it:
```

# LOCK_SCREEN=true

```

If someone can confirm that this works better for him/her, I'll add it to the top post.

---

### Post by oldwismn on 2010-05-04
I tried commenting out the "LOCK_SCREEN=true" line in /etc/default/acpi-support and also changing the line to "LOCK_SCREEN=false".  Neither of these changes allowed resume from suspend without a password when I suspended by clicking the button at the right top of the screen (the "Indicator Applet Session" button) .  The changes listed by tom4everitt in the top post allowed me to resume without a password when I suspended by hitting Ctrl+Alt+Delete and then selecting Suspend or used the "Shut Down" applet button.

---

### Post by MoarningSun on 2010-05-05
There are more than one way to initiate a suspend in Ubuntu, not all of them use the same settings.. For more discussion on this also see [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/255228")

---

### Post by FireNoodle on 2010-05-09
This was driving me nuts, I was hunting everywhere for autologin not working... took me a while to realize it was a totally separate issue.

Thanks to tom4everitt, his first post worked for me perfectly.

---

### Post by Greblok on 2010-05-11
Can I use the gconf-editor to disable password when using user switch?
If so, could anyone please point me in the right direction?

I have two user accounts, neither needs password on first login but when switching users, they are prompted for pw. Not needed at all in my enviroment.
 Screensaver pw is disabled for both accounts.

---

### Post by itslofty on 2010-05-11
I was having the same issue
I did what Tom posted above but was still asked for password after suspend.

This seems to resolve the problem - after doing the steps above - 

open  terminal "gconf-editor". 
I went to "Desktop-->Gnome-->Lockdown" then checked the box for "disable_lock_screen"

All good now,

---

### Post by Greblok on 2010-05-12
> **itslofty said:**
> 
This seems to resolve the problem - after doing the steps above - 

open  terminal "gconf-editor". 
I went to "Desktop-->Gnome-->Lockdown" then checked the box for "disable_lock_screen"


You just made my week a lot better! :)
Thank you itslofty, worked just as it should.

---

### Post by almalaci on 2010-05-15
Thanks itslofty,
That's the one that did it for me too.

---

### Post by tom4everitt on 2010-05-16
> **itslofty said:**
> 
open  terminal "gconf-editor". 
I went to "Desktop-->Gnome-->Lockdown" then checked the box for "disable_lock_screen"


Seems like this helps a lot of people. I'll add it to the top post if you don't mind.

---

### Post by mikehattingh on 2010-05-20
In System->Preferences->Screen Saver
"lock screen when screen saver is activated" is unchecked

In gconf-editor
apps/gnome-power-manager/locks use_screensaver_settings is checked and nothing else
desktop/gnome/lockdown disable_lock_screen is checked and nothing else

In /etc/default/acpi-support
#LOCK_SCREEN=true commented out

None of this helped, but after reading the bug report [[COLOR="Blue"]here[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/255228/comments/16") I see the problem. I was using $ sudo gconf-editor, and so was changing the settings for the root user and not for me #-o . All good now.

(Motion Computing Le-1600 Tablet 9.04 jaunty)

---

### Post by izzaboo on 2010-06-05
I typically suspend by closing netbook.  Had to use gconf -> desktop -> lockdown setting for health, happiness & success.

thanks, all, for this thread!

btw, using Ubuntu 10.04 on dell mini 9

-g

---

### Post by Perturbed Penguin on 2010-06-20
I realize this is still a bug in Ubuntu 10.04, a related bug is that you can not disable the hibernate or sleep options in the 'indicator' or power menu. However should this thread maybe be marked solved now since the problem has been discovered and there is already a bug report filed for it? Just a thought...

---

### Post by rworloma on 2010-06-20
Solution is here http://www.liberiangeek.net/2010/06/how-to-disableremove-password-prompts-in-ubuntu-10-04-lucid-lynx-during-sleep-mode/

---

### Post by tom4everitt on 2010-06-21
> **Perturbed Penguin said:**
> I realize this is still a bug in Ubuntu 10.04, a related bug is that you can not disable the hibernate or sleep options in the 'indicator' or power menu. However should this thread maybe be marked solved now since the problem has been discovered and there is already a bug report filed for it? Just a thought...

I marked it solved. The fact that the thread title starts with HOWTO sort of suggests that the thread does contain a solution, but I guess one can never be too clear :)

---

### Post by Perturbed Penguin on 2010-06-28
Ah, yes I see that now. ;) Sounds good.

---

### Post by Apuokas on 2010-07-06
Hi there

I have the same problem as you guys. The "Lock screen when screensaver is active" in the Screensaver settings windows doesn't work. But when I use the "Desktop-->Gnome-->Lockdown" then check the box for "disable_lock_screen" the screensaver doesn't appear at all...

So, what other solutions, besides mentioned ones in this thread you could suggest?

---

### Post by captkit on 2010-09-25
Thank you, tom4everitt. Like you, after completing all the steps, my desktop resumed without a visible mouse cursor but I then discovered that the cursor is active anyway. By pushing the mouse until the invisible cursor is in the top panel then sliding sideways, the home file icon lights up. Then click on the icon and _poof_ the cursor reappears. It ain't pretty but I'll take it.

---

### Post by tom4everitt on 2010-09-26
> **captkit said:**
> Thank you, tom4everitt. Like you, after completing all the steps, my desktop resumed without a visible mouse cursor but I then discovered that the cursor is active anyway. By pushing the mouse until the invisible cursor is in the top panel then sliding sideways, the home file icon lights up. Then click on the icon and _poof_ the cursor reappears. It ain't pretty but I'll take it.

Oh, that was a method I wasn't aware of. My solution (not very pretty either) has been to switch to a different workspace. Then the cursor also reappears. Switching is convenient in the sense that it can be done with a keyboard command: ctrl+alt+left arrow.

---

### Post by tom4everitt on 2010-09-26
> **Apuokas said:**
> Hi there

I have the same problem as you guys. The "Lock screen when screensaver is active" in the Screensaver settings windows doesn't work. But when I use the "Desktop-->Gnome-->Lockdown" then check the box for "disable_lock_screen" the screensaver doesn't appear at all...

So, what other solutions, besides mentioned ones in this thread you could suggest?

Sorry, I think I've mentioned everything I could think of in this thread already.

---

### Post by captkit on 2010-09-26
D'oh! I forgot to mention the simplest trick--when I suspend with Anything open on the desktop--a terminal or any file or directory--the cursor reappears after the desktop resumes. Enjoy

---

### Post by tom4everitt on 2010-09-26
> **captkit said:**
> D'oh! I forgot to mention the simplest trick--when I suspend with Anything open on the desktop--a terminal or any file or directory--the cursor reappears after the desktop resumes. Enjoy

That sounded like the ultimate trick. Unfortunately it didn't work for me. Doh! Thanks for the tip anyway

---

### Post by Ubuk2008 on 2010-10-11
Thanks to all for this **most** helpful tip!

---

### Post by keithspg on 2011-02-04
Arrrrgh! Been through this. This works perfectly on my laptop. I just set our main desktop at home to do this. Suspend works im-perfectly (I loose sound). I was able to fix that with a script (it works some times). WOL works perfectly (with a supported ethernet card). It will "Wake" from off, or suspended. (Yea!). It will not resume to the desktop from whence it was suspended, though. 

I still get the login (user) and password prompts. From a cold boot, it boots to the desktop directly and does not wait for another login.

I cannot get rid of the login and password after suspend by following the noted changes in this thread. Are there any other suggestions? I went and deleted the configurations (rm -rf .gnome .gnome2 .gconf .gconfd .metacity). and started over just to make sure.

This is with 10.10 Maverick fully updated. This is quite frustrating. I want to be able to have this machine be 'suspended' when not in use for power savings, but want to be able to remotely wake it up (done) and access its resources if needed.

K

---

### Post by benoliver999 on 2011-04-21
Done it at last! If the solution in the top post does not work for you, you are probably using sudo to open gconf. Don't type sudo into terminal, and it will save the settings for your profile!

---

### Post by maartmeester on 2011-08-06
Thanks a bundle! That last post was a total life saver! DO NOT TYPE "sudo gconf-editor", but instead simply type "gconf-editor" in a terminal window and perform the changes indicated in the top post to change the settings for your own profile. I (like some others on this topic) used the power button on my laptop to suspend the system and always used to get the password prompt. Not anymore, thank gawd! Thanks all!

---

### Post by debido666 on 2011-10-18
Do not want to disable password. How do I change the theme of the login window instead? I've changed the main login windows. But the one from suspend is different.

---

### Post by tom4everitt on 2011-10-20
> **debido666 said:**
> Do not want to disable password. How do I change the theme of the login window instead? I've changed the main login windows. But the one from suspend is different.

Hi, and welcome to the forum!

This question is slightly different than the topic of the thread, which means you should ask this in a new thread with an appropriate title. 

I would suggest "How do I change the suspend login window theme",
and post it under Desktop Environments. Keeping the forum structured like this is good for everyone in the long run, since it will be much easier for someone else with the same question to find the answer then (and much easier for people knowing the answer to find your question ;)). 

Good luck!


PS. I don't know the answer to your question, unfortunately.

---

### Post by brallan on 2011-10-31
in 11.10, the solution is simple: go to the DASH HOME and type SCREEN. 

Or from SYSTEM SETTINGS > PERSONAL > SCREEN.

there you will find the LOCK / UNLOCK button. Silly thing, you don't even need to enter your password to change it!

---

### Post by RaymanJr on 2011-11-01
in 11.10 the "lock" button under "Screen" didn't worked for me either nor any other hint before. Seems that there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/871560") in 11.10 

After giving the following command I get rid of password prompt suspend:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```

---

### Post by Bungtung on 2011-11-05
> **RaymanJr said:**
> in 11.10 the "lock" button under "Screen" didn't worked for me either nor any other hint before. Seems that there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/871560") in 11.10 

After giving the following command I get rid of password prompt suspend:
```
gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```

Thanks Rayman Jr!!!:D

---

### Post by BornOle on 2012-03-01
Tuning in to say that the solution of disabling user lock worked for me, I love Linux and I love this forum. Peace out :)

---

