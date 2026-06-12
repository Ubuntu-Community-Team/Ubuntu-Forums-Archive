---
title: "Linux 3.2 rc6 in Precise repos"
date: 2011-12-18
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-12-18
The newest release candidate (rc6) of the kernel 3.2.0 is very soon in Precise repos.
Right now building in Launchpad. Here:

[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-6.12](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-6.12)

> **Changelog**

          linux (3.2.0-6.12) precise; urgency=low    [ Upstream Kernel Changes ]    * rebase to upstream v3.2-rc6  -- Leann Ogasawara <email address hidden>   Fri, 16 Dec 2011 10:19:02 -0800      


---

### Post by VinDSL on 2011-12-19
Thanks, Harry!

I've re-installed network-manager & network-manager-gnome, in anticipation...  Heh!  :)

---

### Post by xyzzyman on 2011-12-19
Yay. I pulled the Ubuntu source from that page and compiled. My webcam works like 3.0 kernels (Which was apparently fixed around RC3 or so, and my nvidia video works again without just shutting off my LCD (Has been like that with every 3.2 since RC3 or so unless I typed acpi=off at the command line). Works on my Oneiric and Precise installs. I've been wanting a 3.2kernel as it allows me to jack up the buffer for my sound card in the kernel config. I'm watching netflix in HD on my windows 7 starter in virtualbox with no static finally!!!

---

### Post by paul_in_london on 2011-12-19
> **Harry33 said:**
> The newest release candidate (rc6) of the kernel 3.2.0 is very soon in Precise repos.
Right now building in Launchpad. Here:

[https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-6.12](https://launchpad.net/ubuntu/precise/+source/linux/3.2.0-6.12)

Thanks from me too Harry. Haven't had the kernel update from the repos yet, but I installed rc6 from ppa mainline the other day, which is working ok.

---

### Post by paul_in_london on 2011-12-19
The 3.2.0-6.12 kernel update has now arrived via the repos.

---

### Post by VinDSL on 2011-12-20
> **paul_in_london said:**
> The 3.2.0-6.12 kernel update has now arrived via the repos.
I didn't get a chance to install 3.2.0-6.12 until a few minutes ago.

Same ol', same ol', here...  LoL!

No network connection / hangs on shutdown, Unity and GS.

Soooo, once again, I removed network-manager & network-manager-gnome, and re-installed wicd.  Bingo!

Heh!  I'm getting quite adept at switching back n' forth between network-manager and wicd...  Every cloud has a silver lining!  :D

Actually, if it wasn't for the missing network app indicator in the gnome panel, I'd just keep running wicd.  Haven't had a single problem with it, so far...

---

### Post by dino99 on 2011-12-20
> **VinDSL said:**
> 

Actually, if it wasn't for the missing network app indicator in the gnome panel, I'd just keep running wicd.  Haven't had a single problem with it, so far...

i get the icon in the gnome-panel (logged as gnome-classic) without trouble.

---

### Post by VinDSL on 2011-12-20
> **dino99 said:**
> i get the icon in the gnome-panel (logged as gnome-classic) without trouble.
w00t!  You dah man, dino!!!

You got me thinking...  :D

"Why does the app indicator work in Classic, but not Unity"?

Doh!  Wicd isn't in the panel whitelist!

I added wicd to the panel whitelist, logged out, logged in, and there it was.  But, the wicd icon was butt fugly, so...

I made a custom ACYL icon (to match my icon set) stuck it in the wicd icon folder, logged out, logged in, and now it looks identical to the network-manager app indicator.


[INDENT](Click image to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-20-dec-2011-2(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-20-dec-2011-2.png")[/INDENT]


Thank you, bro!!!

---

### Post by xyzzyman on 2011-12-20
Alex Jones.... :P

---

### Post by VinDSL on 2011-12-20
> **xyzzyman said:**
> Alex Jones.... :P
I love that guy, but...

He makes you feel like jumping off a cliff, after 3 hours of listening to him.  :D

---

### Post by paul_in_london on 2011-12-20
> **VinDSL said:**
> I love that guy, but...

He makes you feel like jumping off a cliff, after 3 hours of listening to him.  :D

I think that's a fair summary (without going into a rant)! ](*,)

---

### Post by xyzzyman on 2011-12-20
I listen to Coast 2 Coast AM on nights I don't have an Opie & Anthony to listen to while asleep. C2C will cause some VERY messed up dreams depending on the content of the show. Especially if you already have a sleep disorder.

---

### Post by jerrylamos on 2011-12-20
> **VinDSL said:**
> I didn't get a chance to install 3.2.0-6.12 until a few minutes ago.

Same ol', same ol', here...  LoL!

No network connection / hangs on shutdown, Unity and GS.

Soooo, once again, I removed network-manager & network-manager-gnome, and re-installed wicd.  Bingo!

I haven't been following your network situation.  3.2.0.5 was running fine here, unity-2D, upgraded to 3.2.0.6 no problem with network.  Using wireless on Acer Aspire 1 with intel atom hardware.

Now I do have a Thinkpad T40 runs precise fine but hasn't had ubuntu wireless support since maverick. Now I am able to get wireless by plugging in an even older pc card.  Runs unity-2D but I've been doing lubuntu precise on it just for variety, and of course a lucid LTS which does support wireless on the T40 unlike precise.

---

### Post by VinDSL on 2011-12-20
> **jerrylamos said:**
> I haven't been following your network situation.  3.2.0.5 was running fine here, unity-2D, upgraded to 3.2.0.6 no problem with network.[...]
Brief summary...

[LIST]
[*]Been running this desktop machine for years. High-end Intel chipsets. Very stable.
[*]It uses a wired connection - never had a problem. 
[*]network-manager/Linux 3.2.x combination results in no Lan/Wan connection.
[*]Machine boots/works normally (other than no network) but hard locks on shutdown.
[*]Remove network-manager, install wicd, and life is good again.
[/LIST]

It's a weird one!  ;)

---

### Post by ptn107 on 2011-12-20
I back-ported it for Oneiric users here, enjoy:

deb [http://ppa.launchpad.net/ptn107/ppa/ubuntu](http://ppa.launchpad.net/ptn107/ppa/ubuntu) oneiric main

```
sudo apt-add-repository ppa:ptn107/ppa && sudo apt-get update
```

---

### Post by xyzzyman on 2011-12-20
What is the different backporting to oneiric compared to the compile for precise? The deb's work fine manually installing on oneiric. Is it just for easy of updating when you later backport? It doesn't matter for my usage as I took the source from precise and compiled for core2 and my own .config file but just curious.

---

### Post by VinDSL on 2011-12-24
Linux 3.2 rc7 in out now...

Linkage:  [http://comments.gmane.org/gmane.linux.kernel/1233133](http://comments.gmane.org/gmane.linux.kernel/1233133)

> There it is, likely the last -rc in before final 3.2, so please do
check it out in between your holiday festivities.

Most of the changes are faily simple one-liners, but some qla4xxx
driver updates stand out and in fact account for about 40% of the diff
("qla4xxx: fix flash/ddb support"). That, together with a VMWare DRI
driver update and some dvb updates and the regular random driver fixes
means that 80+% of the changes are in drivers.

Some net updates, some SH updates, and then a (tiny) smattering of
other stuff. The appended shortlog gives the (fairly boring) details,

                    Linus


Mainline Kernel(s):  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc7-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc7-precise/)

---

### Post by paul_in_london on 2011-12-24
> **VinDSL said:**
> Linux 3.2 rc7 in out now...

Linkage:  [http://comments.gmane.org/gmane.linux.kernel/1233133](http://comments.gmane.org/gmane.linux.kernel/1233133)



Mainline Kernel(s):  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc7-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc7-precise/)

Was about to post the same thing before I checked this thread. :)

---

### Post by BC59 on 2011-12-24
For the people who already use it, did you notice a difference?

---

### Post by paul_in_london on 2011-12-24
> **BC59 said:**
> For the people who already use it, did you notice a difference?

If you mean between 3.2 rc6 and 3.2 rc7 I can't say I've noticed anything obvious here so far...

---

### Post by BC59 on 2011-12-24
No I mean between 3.0 and 3.2

---

### Post by effenberg0x0 on 2011-12-24
A probably stupid question: When we get Kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"), those 3 patches in every dir have already been applied before the kernel was packed as .deb, right? Or do we have to apply them? I never understood why they would care to put the patches for download if the thing was already packed.

EDIT:
The grep error is still there.
```

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-030200rc7-generic
Found initrd image: /boot/initrd.img-3.2.0-030200rc7-generic
Found linux image: /boot/vmlinuz-3.2.0-6-generic
Found initrd image: /boot/initrd.img-3.2.0-6-generic
Found linux image: /boot/vmlinuz-3.2.0-4-generic
Found initrd image: /boot/initrd.img-3.2.0-4-generic
Found memtest86+ image: /boot/memtest86+.bin
grep: input file `/boot/grub/grub.cfg.new' is also the output
done

```

---

### Post by xyzzyman on 2011-12-24
> **BC59 said:**
> No I mean between 3.0 and 3.2

[http://www.phoronix.com/scan.php?page=news_item&px=MTAxMjc](http://www.phoronix.com/scan.php?page=news_item&px=MTAxMjc)


> **effenberg0x0 said:**
> A probably stupid question: When we get Kernels from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/"), those 3 patches in every dir have already been applied before the kernel was packed as .deb, right? Or do we have to apply them? I never understood why they would care to put the patches for download if the thing was already packed.


The patches are already applied. You are supposed to provide the patches when you modify the code so that's why they are there. That's kinda the whole point of open-source.
:guitar:

---

### Post by VinDSL on 2011-12-24
> **BC59 said:**
> For the people who already use it, did you notice a difference?

> **paul_in_london said:**
> If you mean between 3.2 rc6 and 3.2 rc7 I can't say I've noticed anything obvious here so far...
And, if you mean between mainline kernels, and the official repo versions...

Yes, there are differences, but no game-stoppers.  ;)

For instance, on this machine, when you do a shutdown, it just shells out to a terminal screen, stops the various services, and turns the PC off, e.g. no Ubu EyeCandy Logo - stuff like that...

---

### Post by VinDSL on 2011-12-24
> **BC59 said:**
> No I mean between 3.0 and 3.2
Heh!  I should have kept reading...

The only difference for me is, Linux 3.0 allows me to use network-manager & network-manager-gnome (the default network managers).

Under Linux 3.2, I must uninstall the default network managers, and run Wicd.  Other than that, they look n' feel the same on this install.

---

### Post by xyzzyman on 2011-12-25
Mainline is missing the patches for ureadahead support.

---

### Post by alfonso78 on 2012-01-09
> **ptn107 said:**
> I back-ported it for Oneiric users here, enjoy:

deb [http://ppa.launchpad.net/ptn107/ppa/ubuntu](http://ppa.launchpad.net/ptn107/ppa/ubuntu) oneiric main

```
sudo apt-add-repository ppa:ptn107/ppa && sudo apt-get update
```

Hi!

I saw on your ppa [here]("https://launchpad.net/~ptn107/+archive/ppa/+packages") with 3.2.0 kernel backported for oneiric. Thank you.
Is it enough to add the ppa, update and upgrade or should I install the specific packages to update the kernel?

thank you.

---

### Post by dino99 on 2012-01-09
> **alfonso78 said:**
> Hi!

Is it enough to add the ppa, update and upgrade or should I install the specific packages to update the kernel?



yes, add it, update then you get 1 image & 2 headers to upgrade.

---

### Post by alfonso78 on 2012-01-09
> **dino99 said:**
> yes, add it, update then you get 1 image & 2 headers to upgrade.

Ok, so if I understand I manually have to "tell" which packet I want to install, it's not automatic.

I'll try.

---

### Post by dino99 on 2012-01-09
> **alfonso78 said:**
> Ok, so if I understand I manually have to "tell" which packet I want to install, it's not automatic.

I'll try.

sudo synaptic

---

### Post by zika on 2012-01-09
> **dino99 said:**
> sudo synaptic```
gksu synaptic
``` or ```
sudo -H synaptic
```

---

### Post by t1497f35 on 2012-01-11
> **dino99 said:**
> yes, add it, update then you get 1 image & 2 headers to upgrade.

I added [this ppa]("https://launchpad.net/%7Eptn107/+archive/ppa") and then "sudo apt-get update" and "sudo apt-get dist-upgrade" but it says there's nothing to update, same thing says the update manager.
Anyone knows what could be wrong?


Using Ubuntu 11.10 amd64

---

### Post by paul_in_london on 2012-01-11
> **t1497f35 said:**
> I added [this ppa]("https://launchpad.net/%7Eptn107/+archive/ppa") and then "sudo apt-get update" and "sudo apt-get dist-upgrade" but it says there's nothing to update, same thing says the update manager.
Anyone knows what could be wrong?


Using Ubuntu 11.10 amd64

That ppa only shows an oneiric channel (I know that's what you're using). In PP there was a kernel update today from the main repos:

```
Linux precise-64 3.2.0-8-generic **#15**-Ubuntu SMP Wed Jan 11 13:57:44 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
paul@precise-64:~$
```

What's your current kernel version in oneiric?

Looks as if 3.2.0-8.14 is still building (32 and 64 bit):

[https://launchpad.net/~ptn107/+archive/ppa/+builds?build_text=&build_state=all](https://launchpad.net/~ptn107/+archive/ppa/+builds?build_text=&build_state=all)

---

### Post by t1497f35 on 2012-01-11
Thanks, I have (had) the usual kernel that comes with Oneiric.
The issue is that I had same experience with that ppa a few days ago (when it wasn't building).

So I installed by hand the 3.2 kernel from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2-precise/").

When the ppa finishes building the kernel I'll give it another try.

---

### Post by paul_in_london on 2012-01-11
> **t1497f35 said:**
> So I installed by hand the 3.2 kernel from [here]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.2-precise/")

Ok. I was going to suggest that actually. :)

---

