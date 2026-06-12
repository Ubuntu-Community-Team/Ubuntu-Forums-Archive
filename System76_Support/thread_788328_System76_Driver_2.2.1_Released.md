---
title: "System76 Driver 2.2.1 Released"
date: 2008-05-09
forum: System76 Support
---

### Post by crichell on 2008-05-09
System76 Driver 2.2.1 has just been released to the repositories. This releases fixes two minor Hardy bugs:

[LIST]
[*][hardy] fix sound on resume from suspend LP Bug #223742 (serp3) (serp4) (gazp5) (gazv5) (panv3)
[*]Install linux-backports-modules-hardy to fix the wireless LED on Intel based cards LP Bug #223874 [/LIST]

The fixes apply to all laptop customers. After the updated driver has been installed go to System > Administration > System76 driver and click the "Install Drivers" tab. Click install. After your next reboot your wireless LED will illuminate!

More driver information can be found here:

[http://knowledge76.com/index.php/System76_Driver](http://knowledge76.com/index.php/System76_Driver)

And the change log:

[http://knowledge76.com/index.php/System76_Driver_Changelog](http://knowledge76.com/index.php/System76_Driver_Changelog)

---

### Post by Luke has no name on 2008-05-09
Awesome. When you guys make these drivers and patches, are they able to be incorporated into the main release to help other people?

---

### Post by Sean-Michael on 2008-05-09
I'm not sure about this one...

> # Install linux-backports-modules-hardy to fix the wireless LED on Intel based cards LP Bug #223874

My light was working fine I think, bright orange when I turned it on.  Now the light is bright orange till I login and then it turns to a light pinkish or purple color.  I hope this is not in indication that something is wrong.:( Anything I need to be concerned with?

Just my observations'
Sean-Michael.

---

### Post by glacialfury on 2008-05-10
Synaptic lists 2.2.0 as the latest driver as of right now.

Edit: Eh, scrap that.  20 minutes from my post it showed up in the update.

---

### Post by Vadi on 2008-05-10
Thanks much!

---

### Post by stewpac on 2008-05-14
I still have some problems with my sound (gazp5) under Hardy. It seems mp3s in VLC play choppily. This happens from a startup as well as resume. I have the system76 driver version 2.2.1. Any suggestions??

---

### Post by kevin11951 on 2008-05-15
> **Sean-Michael said:**
> I'm not sure about this one...



My light was working fine I think, bright orange when I turned it on.  Now the light is bright orange till I login and then it turns to a light pinkish or purple color.  I hope this is not in indication that something is wrong.:( Anything I need to be concerned with?

Just my observations'
Sean-Michael.

actually thats what i thought, until i installed windows (dual boot) and figured out that thats how its supposed to be.

---

### Post by Sean-Michael on 2008-05-15
Thank you Kevin11951,
This eases my mind, all was working well but I was unsure if damage was silently being caused...

Oh, I did notice the System76 site shows the light being blue too lol
[http://system76.com/images/serval-p3-med.jpg](http://system76.com/images/serval-p3-med.jpg)

Regards,
Sean-Michael.

---

### Post by Vadi on 2008-05-15
For some reason sound gets lost again after resuming from hibernate. I think that happened when I installed a fix for the nvidia driver (nvidia-glx-new or something like that from hardy-proposed)

How can I make the driver reinstall what it needs?

---

### Post by thomasaaron on 2008-05-15
System > Administration > System76 Driver > Install Tab > Install Button

---

### Post by Vadi on 2008-05-15
That doesn't work; it says it's done after like 2-3 seconds and I still lose sound after resume. I think it just checks if the fix is installed and that's it.

---

### Post by thomasaaron on 2008-05-15
Which computer model do you have, Vadi?

---

### Post by Vadi on 2008-05-15
serp3, Ubuntu 8.04 64bit

I've reinstalled the system76 driver manager via synaptic, and used the restore settings in the driver, but it doesn't work still :/

---

### Post by thomasaaron on 2008-05-15
Please go to the driver and click the "About" button and verify that you have version 2.2.1 installed.

---

### Post by Vadi on 2008-05-15
Yes, it does say 2.2.1

---

### Post by Gorlith on 2008-05-15
> **Vadi said:**
> For some reason sound gets lost again after resuming from hibernate. I think that happened when I installed a fix for the nvidia driver (nvidia-glx-new or something like that from hardy-proposed)

How can I make the driver reinstall what it needs?

I also lose sound after suspend or hibernate : / have to restart to get it back. i have a gazv5 w/ driver 2.2.1

---

### Post by thomasaaron on 2008-05-15
We'll do some testing here in the shop and see what is going on. I'll be out of the office until Monday, so I'll let you know what I find then.

---

### Post by farruinn on 2008-05-17
Same thing with Serp4 here. I ran the driver then checked /etc/modprobe.d/alsa-base and the line mentioned in bug #223742 hadn't been added. In driverscontrol.py someone just forgot to include the () after sound.alsa9. I made the change, ran the driver installer again and now the toshiba line is in alsa-base. Rebooting now to see if it works! :)

---

### Post by farruinn on 2008-05-17
Success!

EDIT: Just a note to anyone that's looking to make this change for themselves, there are 5 different models that need the alsa9 function, so make sure you add the parentheses to the one for your model. Or all five if you just want to be sure :)

---

### Post by farruinn on 2008-05-18
New observation: when resuming from suspend the laptop makes four loud, high pitched beeps. I'm not sure what this is and I don't have time to look into it but I wanted to post about it in case anyone else is experiencing this after the system76-driver fix as well.

---

### Post by thomasaaron on 2008-05-19
Go to System > Prefs > Power Management > General and de-select the "Use sound to notify..." checkbox. Does that fix it. If not, there is probably a setting in gconf-editor for it.

Let me know if that doesn't work, and I'll try to reproduce it.

---

### Post by Vadi on 2008-05-19
Could the proposed fix be looked at? I don't really want to tinker with those files, just waiting on an update :)

---

### Post by thomasaaron on 2008-05-19
Good eye, farruinn. Thanks much.
We've fixed it in the driver and are looking to see what other bugs we can get fixed in the next driver release (which should happen soon).

---

### Post by stewpac on 2008-05-19
My choppy sound has gone away - I'm not sure why. On another driver related issue...

I've actually had this bug for a while. When resuming from suspend I get a blank screen (and a movable mouse) when the window manager at suspend is Compiz. I end up restarting X (Ctrl+Alt+Del). Metacity on my system (gazp5) doesn't have this problem. I would appreciate it if got considered in the next driver.

---

### Post by Vadi on 2008-05-19
Don't restart, type your password in and it'll login normally. I get this randomly too.

---

### Post by stewpac on 2008-05-19
Thanks for the tip Vadi. I'll try that next time it occurs.

---

### Post by einnar on 2008-05-20
Will this driver work with Mint?

If not, any chance someone could figure out how to make it work with Mint?

Thanks. :)

---

### Post by farruinn on 2008-05-20
> **thomasaaron said:**
> Go to System > Prefs > Power Management > General and de-select the "Use sound to notify..." checkbox. Does that fix it. If not, there is probably a setting in gconf-editor for it.

Let me know if that doesn't work, and I'll try to reproduce it.

Thanks, that was it. It didn't occur to me that this coincided with the little bubble that pops up saying "your computer failed to suspend". The computer is blatantly lying because it's suspending with no problem and resuming with no ill effects :) I will see if I can figure out what's causing this or at least get some more information. Anyone else seeing the same thing? (serp4)

---

### Post by farruinn on 2008-05-20
> **Vadi said:**
> Could the proposed fix be looked at? I don't really want to tinker with those files, just waiting on an update :)

If you want the same effect without modifying the system76 driver, this is essentially what the alsa9 function does, as described in the bug report:

```
sudo echo options snd-hda-intel model=toshiba >> /etc/modprobe.d/alsa-base
```

---

### Post by Vadi on 2008-05-21
That fails to work for me, hence why I'd rather wait.

---

### Post by thomasaaron on 2008-05-21
Hi, Vadi.

You would have to restart your computer after running that command.

---

### Post by Vadi on 2008-05-21
No I meant the command fails to work:

> vadi@ubuntu-laptop:~$ sudo echo options snd-hda-intel model=toshiba >> /etc/modprobe.d/alsa-base
bash: /etc/modprobe.d/alsa-base: Permission denied
vadi@ubuntu-laptop:~$

---

### Post by thomasaaron on 2008-05-21
I see.

Then enter this command: ```
sudo gedit /etc/modprobe.d/alsa-base
```

This will pull up your alsa base file.
Go all the way to the bottom of it and enter this line:

```
options snd-hda-intel model=toshiba
```

Then click Save and restart your computer.

---

### Post by Vadi on 2008-05-21
Thank you, that worked.

---

### Post by jmcnaught on 2008-06-28
Not sure if this is the best thread or not, but I'm still not getting any sound after I resume.

I have a gazp5 with Hardy installed.  I've done both the install and restore for 2.2.1 of the driver.  I also tried adding "options snd-hda-intel model=toshiba" to my /etc/modprobe.d/alsa-base.

Sound works just fine until I suspend.  After resuming I can still use the mixer (e.g. the drivers are still loaded) but nothing comes out of the speakers.

I would have posted about this earlier, but I've been kinda busy.


Jeremy

---

### Post by pauper on 2008-06-28
> No I meant the command fails to work:

```
vadi@ubuntu-laptop:~$ sudo echo options snd-hda-intel model=toshiba >> /etc/modprobe.d/alsa-base
bash: /etc/modprobe.d/alsa-base: Permission denied
vadi@ubuntu-laptop:~$
```

Do this instead:

```
echo "options snd-hda-intel model=toshiba" | sudo tee -a /etc/modprobe.d/alsa-base
```

Quote:
"... tee being used to bypass an inherent limitation in the sudo command. sudo is unable to pipe the standard output to a file."

Source:
[http://en.wikipedia.org/wiki/Tee_%28command%29]("http://en.wikipedia.org/wiki/Tee_%28command%29")

---

### Post by Vadi on 2008-06-28
It's fine, the driver was updated and the sound fot fixed.

---

### Post by jmcnaught on 2008-06-30
Just realized that there's a new 2.2.2 version of the driver that I hadn't tried.  After using it, I still don't have sound after resuming from suspend.

When I click on the about button in the driver application it still says 2.2.1.  /opt/system76/system76-driver/Changelog says 2.2.2.  I completely removed the driver in Synaptic and then reinstalled it, but the about box still says 2.2.1.  So I'm not 100% certain that I'm using 2.2.2 although I don't see how I wouldn't be.

---

### Post by thomasaaron on 2008-06-30
That's a bug in the driver, I believe.
If you installed 2.2.2, you're running it.


Did you run the driver after installing it? System > Admin > System76 Driver > Install Tab > Install Button

(sorry, I have to ask)

Did you reboot your computer after running the driver?

(sorry, I have to ask)

---

### Post by jmcnaught on 2008-07-07
Yes I did all this. I end up having to reboot my computer an awful lot actually because it's easier then unloading all the alsa modules then loading them again.

Maybe someone could tell me if my computer is supposed to have model=toshiba in alsa base or if it should be something else.  I don't really feel like trying all of the models available for the hda-intel driver.  I have a gazp5.

Since installing 2.2.2, I have an additional problem of wifi not working after turned off the radio switch (and then back on).  In order for it to work, I have to rmmod/modprobe iwl3945.

---

### Post by crichell on 2008-07-07
> about box still says 2.2.1

Thanks for pointing this out. I'll update the about dialog with the next release.

> Maybe someone could tell me if my computer is supposed to have model=toshiba in alsa base

```
options snd-hda-intel model=toshiba
```

should be in your /etc/modprobe.d/alsa-base file. The 2.2.2 driver should insert this line for you.

---

### Post by steveneddy on 2008-07-08
I just wanted to go on record that I have a System 76 Serval Performance

Type 1 laptop and I recently (last two weeks) did a complete reinstall of

Hardy on this laptop and I didn't have to run the System76 driver.

Everything worked out of the box.

I already knew about the Intel wireless light, so I enabled backports 

myself and manually loaded the webcam driver kernel module.

Other than that, it is a stock install that rocks!

This laptop is an Intel Core 2 Duo with 2 Gig RAM.

Bluetooth, wireless, Nvidia, USB, Firewire, Synaptic Touchpad, DVD, SD Card reader

Hibernate and suspend work out of the box perfectly.

Also all but one of the Fn keys on the F keys (wireless) works.

I bought this laptop 18 months ago and now all hardware is supported.

---

### Post by jmcnaught on 2008-07-09
I've had that line in my /etc/modprobe.d/alsa-base for weeks now and I still don't have sound after resume.  It's a gazp5.

It's getting to a point where I'm almost ready to reinstall hardy from scratch and not bother with the s76 driver at least at first.  That's just a big pain in the *** though, with all the stuff I'd have to restore on it (LAMP with several client websites in development).

---

### Post by thomasaaron on 2008-07-09
jmcnaught,

Just looked back through the posts, and I'm not seeing whether you are using 32-bit or 64-bit Ubuntu.

Let me know, and I'll try to duplicate your problem before you re-install. Let's at least make sure it actually works.

---

### Post by jmcnaught on 2008-07-09
Hi Thomas,

I'm running 32 bit.  I have all of the ubuntu.com repositories enabled except for hardy-proposed.

---

### Post by thomasaaron on 2008-07-09
OK, I just tested a 64-bit GazV5 with Hardy. Sound works after resuming from suspend. I'll have to image one with 32-bit and see what happens.

---

### Post by jmcnaught on 2008-07-16
Sometimes after suspending running /etc/init.d/alsa-utils restart will bring back sound, but it doesn't always work.

---

### Post by PantherFarber on 2008-07-17
> **crichell said:**
> Thanks for pointing this out. I'll update the about dialog with the next release.




I know this will sound like the typical a**-hole guy comment but instead of waiting till the next release (which will probably be 2.2.3 and a month or two down the road) wouldn't it be convenient not only to us, the system 76 faithful (you rule. i am naming my first child after a character from the game interstate 76 because naming him or her simply system 76 would doom them), but also to the newbies to know that it has been updated. i spent half the night last night trying to figure out why it was still saying 2.2.1 in about when synaptic said 2.2.2. (alcohol was involved.) why not release an update immediately to fix the error. call it 2.2.2.oops or whatever. i know it would have saved me many runs around the System > Administration > System 76 Driver > Install Drivers tab > Install > Close > reboot system; block. But then agian being sober would have saved me that time also.

---

### Post by thomasaaron on 2008-07-18
> wouldn't it be convenient not only to us, the system 76 faithful ... but also to the newbies to know that it has been updated

Yes. It would be incredibly convenient.

Generally, we try to incorporate as many fixes into the driver as possible to be efficient with our time and energy. But this particular bug was indeed confusing.

I'll talk to Carl about it.

---

