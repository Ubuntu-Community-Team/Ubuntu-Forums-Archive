---
title: "Fingerprint Reader How To: All System76 Laptops"
date: 2008-07-15
forum: System76 Support
---

### Post by crichell on 2008-07-15
Development has completed for the Fingerprint Reader in all current System76 laptops. The driver was created by the fprint project with a laptop donation from System76. Thanks fprint!

fprint is in an early development stage and there are some important caveats to installing the software.

[LIST=1]
[*]Some Administration interfaces will NOT work! Network, Services, Time and Date, and Users and Groups will not Unlock. This is due to PAM (Pluggable Authentication Method) limitations and will take time to re-work. It is relatively easy to switch back to standard username/password authentication when you need to use these applications.
[*]This software currently requires compiling the bits.
[*]We have only tested in GNOME. Feedback from users of KDE, xfce, and other environments is welcome.
[/LIST]

I appreciate any feedback or ideas you have. With our early testing I don't think that FP Readers are in a production ready capacity within the Linux stack. For this reason it may be some time before we provide this functionality out of the box. Your feedback will go a long way to making this decision. (We  definitely have to get around the admin interface locks imposed by PolicyKit.)

And Finally - The How To:

[http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation)

---

### Post by greg_g on 2008-07-15
It works for me on the Daru2, thanks!

---

### Post by steveneddy on 2008-07-15
This is really exiting!

Thanks for the good work, Carl.

---

### Post by compholio on 2008-07-15
So, by following the HOWTO it appears that I've registered my fingerprint for the root user rather than my own user...

---

### Post by badbull on 2008-07-16
thanks, works for me...but is there a way to disable the promt on gnome startup?
and it would be nice if you can use the fingerprint sensor for scolling ;-)

---

### Post by greg_g on 2008-07-16
badbull, you can scroll already by sliding your finger along the right side of the touchpad.

---

### Post by crichell on 2008-07-16
> So, by following the HOWTO it appears that I've registered my fingerprint for the root user rather than my own user...

You're registering your finger for whomever you're logged in as.

> but is there a way to disable the promt on gnome startup?

Not that I know of. The login screen will timeout if your finger isn't properly recognized or if you don't swipe at all. I think the best solution, once the software stack has improved, is to log in with your finger only - no username or password prompt. That will be really slick for tablets or netbooks that swivel.

> it would be nice if you can use the fingerprint sensor for scolling

I think so too - particularly for fingerprint readers mounted under the arrow keys. I'll pass on the suggestion.

---

### Post by shingalated on 2008-07-23
Any way to tweak the sensitivity?  I have tried registering my finger about a hundred times and it never quite matches up close enough.

---

### Post by jeamer on 2008-07-25
First off, thanks so much for getting this going! Everyone has been whiney babies (myself included) on the fingerprint reader functionality, and I really appreciate the effort going in.

Having said that. I am having issues. In the fprint program, I can get a good "swipe" about 75% of the time, but in actual usage (login etc) it still hasn't worked after about a week and a bit. Also, I am having major issues with any admin stuff.... thru the terminal it is okay, it prompts for the fingerprint, I swipe, it doesn't work, then I enter my password... but graphically any admin stuff will freeze and crash on attempt to open. I assume it's waiting for a fingerprint that I try and provide, but doesn't get read, and then after no "password" it closes. Any way I can fix it? Or alternatively can someone give me the original text for the config file so I can revert back to straight password usage until the functionality gets a bit better? Thanks!

PS A prompt on login (something like "Please swipe your finger") would be really cool too!

---

### Post by greg_g on 2008-07-25
> **jeamer said:**
> Or alternatively can someone give me the original text for the config file so I can revert back to straight password usage until the functionality gets a bit better? Thanks!


If you followed the guide completely from this page (what Carl pointed us to):
[http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation)

Just:
```

sudo cp /etc/pam.d/common-auth_orig /etc/pam.d/common-auth

```

---

### Post by VOLKOV9 on 2008-07-28
Thanks.

I followed the directions on knowledge76 without hiccup, and played with fprint project demo a bit, getting better at getting it to verify.  I set it up to identify with my right index.  However, login works the same as it used to; when I try to open the fprint project demo now, it thinks for a long time and then does nothing, and trying again, it hangs with an error that it cannot open device; and when I try to use sudo, it asks for my fingerprint, I try, and it gives a warning about "some data lost" repeatedly, then just asks for my password.  Anyone know what the problem is?  For now, I've just reverted to my old pam.d/common-auth (thanks Carl, greg_g).

Thanks again.

---

### Post by crichell on 2008-07-28
> Any way to tweak the sensitivity?

Not that I'm aware of. On the Windows systems I've seen, you swipe your finger three times to capture the image. I suspect this offers greater reliability.

> but graphically any admin stuff will freeze and crash on attempt to open

This is a fundamental limitation and according to devs, going to take some time to work through the Linux stack. Libraries, DBUS, and ultimately applications should be biometrics aware. Network, Services, Time and Date, and Users and Groups will not Unlock at this time. As greg_g noted it's easy to revert to standard username + password.

---

### Post by crichell on 2008-07-28
You may have missed one portion of the How To:

```
Go to System > Preferences > Main Menu.
Click Accessories.
Right click fprint project demo and choose Properties.
Change the command to gksu fprint_demo.

Log Out and Log Back In

```

This starts fprint with admin privileges, otherwise the device can't be opened.

> it gives a warning about "some data lost"

I've seen this error while registering, verifying, and using the fp reader. I think fprint is kicking out empty images while the finger is swiped - to gain a better quality image. I'm not yet sure if the error is related.

---

### Post by shadhavar on 2008-08-03
> **VOLKOV9 said:**
> 
when I try to open the fprint project demo now, it thinks for a long time and then does nothing, and trying again, it hangs with an error that it cannot open device; and when I try to use sudo, it asks for my fingerprint, I try, and it gives a warning about "some data lost" repeatedly, then just asks for my password.

I'm getting the hang then 'cannot open device' when I open the fprint project demo as well. It seemed to work at first, but after i played with it for a bit it stopped working.

---

### Post by thomasaaron on 2008-08-04
Yeah, it's still a work in progress.

But now that it is working, development on it should move pretty quickly.

---

### Post by shadhavar on 2008-08-04
np :) I'm pretty excited that its even working at all lol. Can't wait till the bugs are worked out :D

---

### Post by leptons on 2008-08-10
This is awesome stuff. I've been waiting a long time for the fingerprint sensor on my laptop to work... hopefully all the bugs will be worked out soon. Great work to the developers.

---

### Post by Ocean Machine on 2008-08-14
How can I disable the reader? I've been having a lot of trouble logging on since installing it, and if I'm able to get in, I can't update my computer, or even open the fprint demo.

---

### Post by thomasaaron on 2008-08-15
Do this:

```
sudo gedit /etc/pam.d/common-auth
```

Change the file from:

```
auth    sufficient      pam_fprint.so
auth	 requisite	 pam_unix.so nullok_secure
auth	 optional	 pam_smbpass.so migrate missingok
```

to:

```
auth	 requisite	 pam_unix.so nullok_secure
auth	 optional	 pam_smbpass.so migrate missingok
```

Then reboot.

I'm 99% sure that should take care of it.
If not, reverse the above directions and let me know -- and I'll look into it a little deeper.

---

### Post by saxamo on 2008-08-24
The fingerprint reader does work on my daru2, but I can't actually use it as a password authentication. The fprint demo works fine. If I go into a terminal and type a simple application such as "sudo gedit" I get a message:

```
Could not locate any suitable fingerprints matched with available hardware.
```

And then it asks for my passphrase. Any tips?

---

### Post by thomasaaron on 2008-08-25
Make sure you swipe your finger through it with consistent positioning and speed.

At any rate, it's beta software for demo purposes. It'll get better as Ubuntu works on it.

---

### Post by Kheter on 2008-08-29
Great utility, works like a charm on my HP Pavilion HDX9490el.

Too bad network-admin and such are broken, since i'm using wifi to connect to the internet every time i login i need to deactivate fingerprint or else i cannot connect to wifi.

Any workaround available?

---

### Post by san_terre on 2008-10-03
Has anyone been able to disable or revert back from a compile of fprint demo?

I followed the directions from: [http://knowledge76.com/index.php/Fingerprint_Reader_Installation](http://knowledge76.com/index.php/Fingerprint_Reader_Installation) and the install with without a hitch.

But now I cannot admin anything from the GUI with my password (update manager, system prefs....)

My common-auth looks like this:

auth requisite pam_unix.so nullok_secure
auth optional pam_smbpass.so migrate

---

### Post by compholio on 2008-10-03
> **san_terre said:**
> Has anyone been able to disable or revert back from a compile of fprint demo?
...
My common-auth looks like this:

auth requisite pam_unix.so nullok_secure
auth optional pam_smbpass.so migrate

You sure you don't have a line like this?:
```
auth     sufficient      pam_fprint.so
```

All you should need to do is remove that line.

---

### Post by san_terre on 2008-10-03
No I don't have that line anymore.  

Basically, I want to remove all fprint demo tie-ins off my PC.

---

### Post by thomasaaron on 2008-10-03
This should do it...

```
sudo gedit /etc/pam.d/common-auth
```

Change the file from:
```

auth    sufficient      pam_fprint.so
auth	 requisite	 pam_unix.so nullok_secure
auth	 optional	 pam_smbpass.so migrate missingok
```

to:
```

auth	 requisite	 pam_unix.so nullok_secure
auth	 optional	 pam_smbpass.so migrate missingok
```

---

### Post by san_terre on 2008-10-03
Thanks, but I have tried that many times.

What I am seeing, is that when GDM starts, I instantly get a crash report, but cannot view it due to not being able to use my password.  Even in the terminal, I have to type my password twice.  There is something else that has a hook in some authentication config somewhere.

I poked around syslog, kern.log, messages and /var/crash, but can't seem to find what is causing this.

**EDIT** in auth.log, I get this message when I try to run apply updates in update manager.

> Rawpork sudo: pam_unix(sudo:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=chris


---

### Post by thomasaaron on 2008-10-03
I may have to do some more testing on this.

Try deleting all of the fingerprints you registered. Does that let it revert back to the password prompt?

---

### Post by san_terre on 2008-10-03
Now that I am home from work, I have a little more time to explain.

I'm running a Sony TX-47 and thought I would try out fprint.  After compiling and installing, I could never get my fingerprint reader to work or register.  So I just decided to edit my common-auth, back to default.  This did not work.

Now, what I have tried thus far is removing everything that I installed yesterday with dpkg -P (package name).  Still nothing.  

My only guess is that something in GDM got modified where it is not allowing my username or root to access it.  It's not a real big deal, but makes admining through the GUI a bit tough.

Plus I've been fighting Ubuntu on this Sony for about a month, and finally got most everything working and now this.  

If there are any logs or configs that you would like me to pass on, I'm free to act as a guinea pig.

Thanks.

---

### Post by san_terre on 2008-10-07
I found something else, if anyone can help.

I installed sbackup and when I try to run it, I get the below error.


[COLOR="RoyalBlue"]Failed to execute child process "su-to-root" (No such file or directory)[/COLOR]

---

### Post by san_terre on 2008-10-08
Anyone?  I'm almost at the point of backing up my /home directory and starting fresh.

---

### Post by shaunarman on 2008-10-17
HELP!!!!!!!!!!!!!!!
      I followed all direction but I am locked out of all admin rights.
Within the terminal this is what I get shaun@shaun-laptop:~$ sudo cp /etc/pam.d/common-auth /etc/pam.d/common-auth_orig
[sudo] password for shaun: 
Could not locate any suitable fingerprints matched with available hardware.
[sudo] password for shaun: 

shaun@shaun-laptop:~$ sudo gedit /etc/pam.d/common-auth
Segmentation fault
shaun@shaun-laptop:~$ 


I am a compleat new be to UBUNTU I have been playing around with it a lot and dont realy want to have to do another install:(. I would like to get the finger print scanner to work but I woul be happy to just get it uninstalled so I can regain admin rights agine.

---

### Post by compholio on 2008-10-18
> **shaunarman said:**
> HELP!!!!!!!!!!!!!!!
      I followed all direction but I am locked out of all admin rights.
...

Don't panic! Reboot and pick the GRUB option that says "(recovery mode)" next to it (NOTE: you need to hit "ESC" when booting for GRUB to appear).  This option will automatically login as the superuser, at this point you can use "nano /etc/pam.d/common-auth" from the prompt in order to fix the authorization file. nano is a very simple editor that explains all the possible commands at the bottom (the '^' character means to use the control key).

---

### Post by shaunarman on 2008-10-18
I dont know if I did it right or not but I still cant use my password to access system admin rights

---

### Post by compholio on 2008-10-18
> **shaunarman said:**
> I dont know if I did it right or not but I still cant use my password to access system admin rights

Open /etc/pam.d/common-auth with a text editor and post the file, it's possible there's still something wrong with it.

---

### Post by shaunarman on 2008-10-18
It will not let me save, says i dont have permission, i'm not sure if the grub even work like you said it should have.

---

### Post by compholio on 2008-10-18
> **shaunarman said:**
> It will not let me save, says i dont have permission, i'm not sure if the grub even work like you said it should have.

It's a small enough file that you should be able to just paste the contents.  The "recovery mode" option should have automatically dumped you to a text prompt where you have superuser privileges, which would allow you to fix your config file.

---

### Post by thomasaaron on 2008-10-20
To be able to save to a file that has root priveleges, you have to be root. Open the file like this...

sudo gedit /etc/pam.d/common-auth

Then modify, then save, then reboot.

---

### Post by compholio on 2008-10-20
> **thomasaaron said:**
> To be able to save to a file that has root priveleges, you have to be root. Open the file like this...

sudo gedit /etc/pam.d/common-auth

Then modify, then save, then reboot.

His auth file is messed up in some way, so he cannot use sudo - that's why I suggested he use the recovery mode to repair the file.

---

### Post by thomasaaron on 2008-10-20
Ah, sorry. 

I'm in the midst of the Monday morning rush, and I missed that.

Good advice though (recovery mode). 

Thanks.

---

### Post by frogotronic on 2008-12-14
Hi Carl,

 Just followed your System76 FPRINT guide for my HP6910p laptop.  Everything is working well.

Couple of questions:

1) Do I have to always enter the password upon start-up to UNLOCK-KEYRING ?

2) How do I uninstall the packages or disable the reader system?

3) What's the difference between your guide and the Intrepid/Hardy backported packages?

Thanks for the great Guide!
- CH

---

### Post by AikonIV on 2008-12-17
I don't own one of your laptops, but this looks like good stuff. Just fyi, it looks like the Fedora people are working on getting fingerprint stuff nicely integrated in their system ([https://fedoraproject.org/wiki/Features/Fingerprint]("https://fedoraproject.org/wiki/Features/Fingerprint")); you might you might consider getting in touch with them or at least checking out their code as development progresses.

---

### Post by Nuno Bettencourt on 2009-01-20
Hi, I tried the freader and it works ok. Thanks for it :)

Nevertheless, i don't use it as much as that, so, like cement_head

> **cement_head said:**
> 
2) How do I uninstall the packages or disable the reader system?


i would like to know how to remove installed packages (installed using the installation mentioned on the first post) without "hurting" my system?

Bests,

Nuno Bettencourt

---

### Post by compholio on 2009-01-20
> **Nuno Bettencourt said:**
> ...
i would like to know how to remove installed packages (installed using the installation mentioned on the first post) without "hurting" my system?
...

In the style of the HOWTO:

Uninstall packaged programs:
```
sudo apt-get remove build-essential libtool automake1.9 libssl-dev libgtk2.0-dev libmagick++9-dev libpam0g-dev
```

Uninstall libusb-1.0:
```
cd libusb-0.9.2/
sudo make uninstall
```

Uninstall libfprint:
```
cd libfprint-20080810-6b8b17f5/
sudo make uninstall
```

Uninstall pam_fprint:
```
cd pam_fprint-20080330-5452ea09/
sudo make uninstall
```

uninstall fprint_demo:
```
cd fprint_demo-20080319-5d86c3f7/
sudo make uninstall
```

and then you probably already know about removing this line from /etc/pam.d/common-auth:
```
auth    sufficient      pam_fprint.so
```

---

### Post by Nuno Bettencourt on 2009-01-20
Thanks [compholio]("http://ubuntuforums.org/member.php?u=71693"), it worked all right ;) except for the menu option, which I removed by hand (System - Prefs - Main Menu).

Best,

Nuno

---

### Post by frogotronic on 2009-01-21
For some reason, this didn't uninstall cleanly (or something else was buggered in my system) and I had to do a re-install.

:popcorn:

---

### Post by compholio on 2009-01-21
> **cement_head said:**
> For some reason, this didn't uninstall cleanly (or something else was buggered in my system) and I had to do a re-install.

:popcorn:

What happened? I hope you didn't re-install all of ubuntu...

---

### Post by frogotronic on 2009-01-21
> **compholio said:**
> What happened? I hope you didn't re-install all of ubuntu...

clean install beginning to end - but that's okay - I ALWAYS back up on a routine basis.

---

### Post by compholio on 2009-01-21
> **cement_head said:**
> clean install beginning to end - but that's okay - I ALWAYS back up on a routine basis.

Wow, you really shouldn't need to do that... What symptoms did you have?  The only thing I can think of that would be "really bad" would be if you accidentally deleted /etc/pam.d/common-auth.

---

### Post by lightnb on 2009-03-07
Hi everyone, it's nice to see the finger print technology moving forward.

I followed the instructions in the tutorial, and I can use fprint demo to scan / test/ record fingerprints. I've run into a few glitches though:

First, my pam.d/common-auth file looks different than that of the tutorial. I added the:
```
auth    sufficient      pam_fprint.so
```
where I thought it should go.

sudo in the terminal now asks for my finger print. As I scan it, the error:
```
upeksonly:warning [handle_packet] lost some dat
``` shows up. The more I move my finger the more times the error shows up. Then it just asks for my password. Nothing else so far seems to be aware of the fingerprint reader. The login screen doesn't show anything special...

I've just upgraded to Ubuntu 8.10 from 8.04, with a complete format/reinstall. And the system has been very sluggish, glitchy, and ... weird? (when you start typing on the keyboard after a period of not typing, the first letter you type shows up twice, and on a clean install with 4 gb ram and a dual core processor, it shouldn't take 30 seconds for firefox or Kdevelop to open, especially if nothing else is running, should it?)

I don't know if the weirdness is related to the upgrade to 8.10 or the fingerprint demo. (or both)

common-auth file:
```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-5, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    sufficient      pam_fprint.so
auth	[success=1 default=ignore]	pam_unix.so nullok_secure
# here's the fallback if no module succeeds
auth	requisite			pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth	required			pam_permit.so
# and here are more per-package modules (the "Additional" block)
# end of pam-auth-update config
```

Any thoughts on this?

---

### Post by thomasaaron on 2009-03-09
On the fingerprint reader, try swiping your finger across the reader at different speeds. Perhaps you are going too fast?

Regarding the repeating keys, can you adjust that with System > Preferences > Keyboard > General > (various sliders)?

---

### Post by tgeer43 on 2009-06-29
> **cement_head said:**
> Hi Carl,

 Just followed your System76 FPRINT guide for my HP6910p laptop.  Everything is working well.

Couple of questions:

1) Do I have to always enter the password upon start-up to UNLOCK-KEYRING ?

2) How do I uninstall the packages or disable the reader system?

3) What's the difference between your guide and the Intrepid/Hardy backported packages?

Thanks for the great Guide!
- CH

Hey cement_head,

Did you ever get a reply to #1 above? That's the only significant issue that I have with fprint.

tgeer

---

### Post by frogotronic on 2009-07-03
> **tgeer43 said:**
> Hey cement_head,

Did you ever get a reply to #1 above? That's the only significant issue that I have with fprint.

tgeer

Hi,

Nope - but I found the answers, so here goes...

```
1) Do I have to always enter the password upon start-up to UNLOCK-KEYRING ?
```

Yes

```
2) How do I uninstall the packages or disable the reader system?
```

reverse the procedure (i.e. make uninstall)


```
3) What's the difference between your guide and the Intrepid/Hardy backported packages?
```

much more updated (less buggy?)

---

### Post by tgeer43 on 2009-07-03
> **cement_head said:**
> Hi,

Nope - but I found the answers, so here goes...

```
1) Do I have to always enter the password upon start-up to UNLOCK-KEYRING ?
```Yes
Thanks, that's all I needed to know. Kinda self defeating to log in with my fingerprint and then have to enter a password as soon as I get to the desktop. I'm sure it'll get resolved eventually.

tgeer

---

