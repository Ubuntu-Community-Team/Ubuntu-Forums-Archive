---
title: "Screen Resolution Koala Mini"
date: 2009-01-29
forum: System76 Support
---

### Post by tgs1952 on 2009-01-29
I am the owner of a new Koala mini. I am very happy with the machine.

However, from the beginning it failed to detect the proper resolution for my monitor. The best resolution it will give me is 1152.x 864, whereas 1280 x 1024 is the correct res for my monitor - a Samsung Syncmaster 910t.

The xrandr -s 1280x 1024 command works until I reboot the computer at which point I have to run it again.

I could live with that but Firefox is now messed up. It takes up the entire space of the monitor. Epiphany, which I don't mind using for everyday tasks is fine. But I need the developer tools in Firefox when I am working - and at this point Firefox is useless. I believe that this is related to the screen resolution issue.

What can I do to fix all this?

---

### Post by thomasaaron on 2009-01-30
Please run these commands one at a time...

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get --reinstall install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg

Choose ALL DEFAULT SELECTIONS on that last command.

Reboot your computer.

Now go to System > Preferences > Screen Resolution and see if you are offered the correct resolution. If not, please take a screenshot of the Resolution screen and attach it to this thread so that I can look at it.

If that doesn't work, we probably will need to add your monitor manually into the xorg.conf.

---

### Post by tgs1952 on 2009-01-31
Not going well. I ran the commands and begin the reconfigure, accepting the defaults and my keyboard stopped working before I got to the end.

I have rebooted and to my surprise, x still worked. And the resolution I was looking for was available.

However, Firefox is now completely hosed. It is smaller but unmovable. It also leaves trails of jagged white blocks around the desktop. It is weird. Completely unusable.

Update: Actually, restarted Firefox a few times and the problem seems to be resolved.

Thanks for the help.

---

### Post by thomasaaron on 2009-02-02
If the firefox problem re-emerges, please try re-installing it...

sudo apt-get --reinstall install firefox

It could also be that you have a plugin installed for Firefox that is causing issues.

I'm not sure your problems are solved yet, given the *pure luck* factor involved in them going away. But if they rear their ugly heads again, we'll try to figure it out.

---

### Post by tgs1952 on 2009-02-07
The problem is not resolved. I rebooted tonight and ubuntu did not detect the proper resolution.

Rebooted again, and it did.

However, Firefox is a disaster again.

I reintalled w/no extensions - and it is the same problem. Firefox takes up the entire display and won't resize.

I must say, this is really a bummer. I downloaded Opera and it works fine, as does Epiphany.

I am not overly attached to Firefox - but it should work - and the developer tools extensions are important to my work.

---

### Post by thomasaaron on 2009-02-08
I helped another customer with a syncmaster on the phone Friday. They went into the menu on the Syncmaster and selected auto-adjust and it fixed their problem.

If that doesn't do it, please post a screenshot of System > Preferences > Screen Resolution.

---

### Post by tgs1952 on 2009-02-08
Thanks, I'll try that.

By the way, perhaps I wasn't clear enough. The correct resolution was detected on the second reboot and all is well except Firefox.

---

### Post by thomasaaron on 2009-02-09
Let's try re-installing Firefox a different way, then.

sudo apt-get --purge remove firefox
sudo apt-get install firefox

---

### Post by tgs1952 on 2009-02-28
My koala is detecting the resolution correctly now after following the suggestions above.

However, those steps completely hosed Firefox; it because way too big - covering the entire display.

The fix is:

/usr/lib/firefox/firefox -safe-mode

then choose

'reset toolbars and controls'

click 'make changes' and restart

---

