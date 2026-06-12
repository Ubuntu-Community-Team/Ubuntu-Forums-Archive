---
title: "Can't log in to the GNOME flashback/fallback (no effects) session"
date: 2013-09-29
forum: Ubuntu Development Version
---

### Post by kansasnoob on 2013-09-29
I'm testing the Ubuntu Saucy Final Beta and I'm having trouble logging into the flashback/fallback session.

I'm beginning with a fresh install of Ubuntu Saucy Final Beta. The default Unity DE is truly unusable on this hardware:

Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

So I decided to give fallback (now named flashback) a try. I first noticed that just installing 'gnome-panel' fails to draw in 'gnome-session-fallback' but I tried it anyway. Sadly I could not login to the "flashback (no effects)" session after just logging out and trying to log back in :(

So I tried another fresh install (needed to do that anyway to follow up on an unrelated bug), the default Unity DE is still unusable other than opening a terminal with CTRL+ALT+F1, so this time I tried installing 'gnome-session-fallback' which was better.

I could then logout and log back into the "flashback (no effects)" session so I tried some of the tweaks I've used in Quantal and Raring:

[http://ubuntuforums.org/showthread.php?t=1966370&page=19&p=12417104#post12417104](http://ubuntuforums.org/showthread.php?t=1966370&page=19&p=12417104#post12417104)

About a 90% success rate BTW, but after a full restart I once again can't login to the "flashback (no effects)" session - it just drops back to the login screen :(

Anyone know what might be up?

---

### Post by Doug S on 2013-09-29
all I can say it that, due to another problem I have been working on, I have been logging on and off of all 3 options (Ubuntu (default), GNOME Flashback, GNOME Flashback (No Effects)), all day without any issues.

---

### Post by sgage on 2013-09-30
Installing gnome-panel here in a fresh install of Ubuntu Gnome brought in gnome-session-flashback as a dependency, as expected. Everything working just fine.

---

### Post by kansasnoob on 2013-09-30
> **Doug S said:**
> all I can say it that, due to another problem I have been working on, I have been logging on and off of all 3 options (Ubuntu (default), GNOME Flashback, GNOME Flashback (No Effects)), all day without any issues.

When did you install Ubuntu Saucy, or was it a different flavor of Ubuntu?

It does work for me (poorly) if I start with Ubuntu GNOME.

---

### Post by kansasnoob on 2013-09-30
> **sgage said:**
> Installing gnome-panel here in a fresh install of Ubuntu Gnome brought in gnome-session-flashback as a dependency, as expected. Everything working just fine.

Login works OK for me using Ubuntu GNOME but clicking on any menu item leaves the screen littered with that menu until I logout, so I'd hardly call it "just fine" ;)

---

### Post by Doug S on 2013-09-30
> **kansasnoob said:**
> When did you install Ubuntu Saucy, or was it a different flavor of Ubuntu?I created the 64 bit 13.10 VM awhile ago. I added GNOME to it sometime later. And have been keeping it up to date once a day.

---

### Post by kansasnoob on 2013-09-30
> **Doug S said:**
> I created the 64 bit 13.10 VM awhile ago. I added GNOME to it sometime later. And have been keeping it up to date once a day.

Aha! What could possibly be different :confused:

I'm trying to test what happens with a freshly installed image and trying to install a "fallback session" using Metacity.

BTW, I'm curious about what you mean by saying, "I added GNOME"????

What did you actually add, and how?

---

### Post by mc4man on 2013-09-30
gnome-session-flashback is a recommend of gnome-panel so should be installed along with gnome-panel unless you're using some method that doesn't install recommends
(if one wants gnome-session-flashback then just install gnome-session-flashback

As far as video glitches, is that both before & after your 'tweaks' or just after?

---

### Post by kansasnoob on 2013-09-30
> **mc4man said:**
> gnome-session-flashback is a recommend of gnome-panel so should be installed along with gnome-panel unless you're using some method that doesn't install recommends
(if one wants gnome-session-flashback then just install gnome-session-flashback

As far as video glitches, is that both before & after your 'tweaks' or just after?

Since I've not been able to get Ubuntu Saucy Final Beta to run at all acceptably on this hardware I've just been using the terminal via Ctrl+Alt+F1, and then using the tty to install fallback/flashback.

I'm basically going to wait until the beginning of RC week, Oct 10, and see what happens.

One thing I want to stress here is that I'm starting from freshly installed images. just as most users would!

I want to stress that we're not Tweak-buntu!!!!!

---

### Post by Doug S on 2013-09-30
> **kansasnoob said:**
> BTW, I'm curious about what you mean by saying, "I added GNOME"???? What did you actually add, and how?Please forgive me, I am actually an Ubuntu server guy, and only created desktop VM's for the first time a couple of weeks ago. I hardly know what a "GNOME" or a "Unity" is and know almost nothing about the GUI desktop environment.
I'm guessing that I meant to say "I installed GNOME flashback or falllback or whatever" (I didn't know GNOME and GNOME flashback seem to be a bit different). This is the command I used:```
doug@doug-desktop:~/docs-1310/ss/html$ grep "apt-get install" ~/.bash_history
sudo apt-get install gnome-session-fallback
```Edit: Now I "added" GNOME via guessing that I needed to "sudo apt-get install gnome". Now my environment options during logon are: GNOME; GNOME Classic; GNOME Flashback; GNOME Flashback (No effects); Ubuntu (Default)
So far, I seem to be able to log off and on into any of the 5 Desktop environments at will.

---

### Post by mc4man on 2013-09-30
Referring back to orig. post - 
As mentioned it's best to just install gnome-session-flashback (not fallback, not gnome-panel

You seemed to indicate that after 'your  tweaking' that upon reboot the session wouldn't load, if so then look at what you did..

Reason for it not to load - 
missing a required_component, most obvious would be gnome-screensaver, listed in /usr/share/gnome-session/sessions/whatever.session

Other possibilities - 
I've seen on rare occasion where the session will actually load but take an inordinate amount of time to do so,  30 - 60 sec's
Or again quite rarely it just won't load, hasn't happened in some time now
In both cases, at least here, removing any file(s) in ~/.dbus/session-bus  proved helpful

---

### Post by ventrical on 2013-09-30
What I did here was install fvwm-crystal after I installed Ubuntu Saucy Beta.

 I went to terminal and installed synaptic;
then I rebooted and chose fvwm-crystal as DE from Logon.

then I opened synaptic from there.

then

I installed gnome-session-flashback

then I installed gnome-session-fallback

then:

sudo reboot

 It works beautifully overclocked at:

```


[sudo] password for ventrical: 
    Max Speed: 4000 MHz
    Current Speed: 4247 MHz
ventrical@ventrical-System-Product-Name:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:      +1.56 V  (min =  +1.45 V, max =  +1.75 V)
 +3.3 Voltage:      +1.66 V  (min =  +3.00 V, max =  +3.60 V)
 +5.0 Voltage:      +1.58 V  (min =  +4.50 V, max =  +5.50 V)
+12.0 Voltage:     +12.09 V  (min = +11.20 V, max = +13.20 V)
CPU FAN Speed:     4115 RPM  (min =    0 RPM, max = 1800 RPM)
CHASSIS FAN Speed:    0 RPM  (min =    0 RPM, max = 1800 RPM)
POWER FAN Speed:      0 RPM  (min =    0 RPM, max = 1800 RPM)
CPU Temperature:    +34.0°C  (high = +90.0°C, crit = +125.0°C)
MB Temperature:     +31.0°C  (high = +70.0°C, crit = +125.0°C)
Power Temperature:  +21.0°C  (high = +80.0°C, crit = +125.0°C)

nouveau-pci-0400
Adapter: PCI adapter
temp1:        +36.0°C  (high = +95.0°C, hyst =  +3.0°C)
                       (crit = +105.0°C, hyst =  +5.0°C)
                       (emerg = +135.0°C, hyst =  +5.0°C)

ventrical@ventrical-System-Product-Name:~$ 

```


  I installed ccsm and it works like old Lucid ! :)

---

### Post by kansasnoob on 2013-10-01
I need to do some more testing but I'm now thinking this login problem is a lightdm thing.

I most recently tried a fresh install of Ubuntu 20131001-i386 and then booted into the Unity DE which is still totally unusable on this hardware:

Intel Atom CPU  230 @ 1.60GHz
Intel 82945G/GZ Integrated Graphics Controller (rev 02)
Intel N10/ICH 7 Family High Definition Audio Controller (rev 01)
Realtek RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
2GB DDR2 RAM

I should note that since I'm playing with alternative DE's I choose NOT to automatically login during installation!

But after installing even 'lubuntu-core' I'm then unable to login to any DE at all! Trying to login just continually rolls me back to the login screen :(

Now, I think that Ubuntu GNOME is still using 'gdm' which would account for me being able to at least login to a "no effects" session :confused:

---

