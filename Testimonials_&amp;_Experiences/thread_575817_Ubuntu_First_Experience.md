---
title: "Ubuntu First Experience"
date: 2007-10-14
forum: Testimonials &amp; Experiences
---

### Post by pnosko on 2007-10-14
Please consider this constructive criticism.  I've been in IT for nearly 30 years.  I'm no longer a fan of Windows, and want an alternative.  I'm generally comfortable at the Unix and Linux command line, but more from an application programming perspective as my admin skills are rusty.  I'm looking for a friendly GUI.  And yes, as friendly as Windows, without the headaches.

I wiped a Win2K Latitude C840 (2.4GHz) and installed Feisty Fawn.  Here's thoughts from my initial experience.

1. I tried the Live CD boot first to see how it would like my hardware.  During the boot, it appears to display what seemed like fatal errors (ata1 exceptions), but if i waited patiently, it moved on and booted successfully.  (I wonder how many folks gave up too soon).  Somehow during my exploration, the Win2K installation got hosed and would no longer boot.  The wired connection didn't help since installing SAMBA said it required a reboot (not helpful from a read-only-CD).  I obtained a USB-IDE adapter and tied to connect a drive to backup my documents.  Unfortunately the NTFS partition would only mount as read-only.  I made do with a thumb drive.

2. I installed it.  Easy as pie.  Well, except for step 5 of the install: Migrate Documents and Settings.  It says "There were no users or operating systems suitable for importing from".  I'd give odds that the overwhelming majority of users would be migrating from Win2K or XP.

3. It detected 125 updates.  I let them install.  Easy as pie.

4. I'm up & running.  I configure my iGoogle home page.  Firefox needs a flash plug-in.  I follow the instructions for using the rpm.  But when I try to install it (as root), is says the rpm program isn't installed.  WTF?  So I go the tar.gz route.  Works as advertised.

5. Root password-- when I logged-in as root using MY password, I did a sudo passwd and 001
.thought I changed root's password.

6. I decide to reboot.  From the first Ubuntu logo to login prompt: 1m58s.  That's slower than Win2K.  Root access remains via my account password.  This is far from ideal.

7. I try to access XP desktops on my Win2K domain.  The first prompt fails, but a second attempt has me seeing my entire domain and browsing my desktop drives via the c$ and d$ shares.  This is VERY IMPRESSIVE; beats every other flavor of Linux I've ever tried (more than a couple). :KS

8. I try out some GUI adjustments.  Anything below 1600x1200 is fuzzy, so I stick with the reading-glasses resolution.  Themes-- I want to try another one-- Mist, a blue minimalist one (emphasis on blue).  Because the desktop colors remained pretty much unchanged (and maybe because of the high resolution and my aging eyesight), it wasn't apparent that just clicking on a new theme made it switch immediately.  Without an "Apply" button, I got lost in the "Install Theme" option, thinking I had to install the theme.  

9.  Eventually I realized what was going on.  But I wanted to see some blue color.  I tried Desktop Effects, and it asked me if I wanted to enable the NVIDIA accelerated graphics driver.  Who would refuse?  On reboot (which it required to activate it), I lost my video entirely; pure black screen.

I will try a fresh install again.  But frankly, I can see most Windows users walking away at this point.  :(

---

### Post by |Eric| on 2007-10-14
ok i do have a grudge against nvidia : yes the driver messes up your screen you still can go & fixit Also i would advise NOT to install nvidia driver for some reason it dosent work well (i need to investigate this ;) ) 

also another mistake you made  ... rpm IS NOT INSTALLED !!! its called .DEB as in _Debian_ what this distro is derived from !

yes tar.gz  is neat somtimes ...


Note: you can install debian packages i believe in ubuntu

---

### Post by jdq997 on 2007-10-14
"I will try a fresh install again. But frankly, I can see most Windows users walking away at this point."

After a few days you'll get there.  Try the new 7.10 installation (currently in release candidate, and will upgrade to the release version as the days pass), that might give you better luck with Nvidia.   On my end the latest Nvidia drivers are working great.  Extremely zippy interface.  Most Windows users probably would walk away at that point -- even more so the power users who are used to knowing how to do everything and think these skills will transfer directly.  For themes go to [www.gnomelook.org](www.gnomelook.org).  To install them take the downloaded compressed file and drag it into the "themes" application.

BTW you don't run RPMS in Ubuntu (You can install .DEB files) and you are better off installing things like Flash via Synaptic and the proper repositories.

 - Jason

---

### Post by -grubby on 2007-10-15
> **pnosko said:**
> 
  Firefox needs a flash plug-in.  I follow the instructions for using the rpm.  But when 
just go to a flash enabled site such as google video and it will say something like "missing plugin" and it will automatically install

---

### Post by rustybronco on 2007-10-16
> **pnosko said:**
> Please consider this constructive criticism.  But frankly, I can see most Windows users walking away at this point.  :( Yes I agree most would walk away at that point, but it's as people have said before "not windows" and will take some work installing and configuring. people today "from my perspective" like to have things done for them, if it can be done easily they will try, but if it becomes a little too difficult they tend walk away and that is sad. there is so much they're missing from thinking, learning and doing new things. patience? a long forgotten art.
the the only thing I would like to add is, if you stick with it long enough I am sure it will grow on you. 
good luck, Dale

---

### Post by rustybronco on 2007-10-16
> **jdq997 said:**
> 
After a few days you'll get there.  Try the new 7.10 installation (currently in release candidate,)  give it a try, can't hurt...
but you first may want to search this site and read up on issues that people may have had with your model. it's always nice to know what you're up against before hand.

---

### Post by pnosko on 2007-10-16
> **rustybronco said:**
> people today "from my perspective" like to have things done for them, if it can be done easily they will try, but if it becomes a little too difficult they tend walk away and that is sad.From an end user's perspective, it is valuable feedback that should not be ignored or taken lightly.  Not if Linux is ever to be perceived as something other than a geek's OS.  I've seen far too many posts (I'm not saying yours, and I'm not implying here) where Linux advocates get defensive about newbie complaints and comments.  I think that is misdirected and has kept Linux in the minority of desktop deployments.

As far as walking away, I wasn't speaking for myself, of course.  I interrupted the boot and logged-on as root and tried to fix it via "dpkg-reconfigure xserver-xorg".  But it asked way too many questions and I aborted after a dozen or so and will reinstall.

Interestingly enough, logging on as root this way required the password change I had made, whereas a "sudo -i" from my user account would only take my user password.  I don't think it's wise to make root so easily accessible.

---

