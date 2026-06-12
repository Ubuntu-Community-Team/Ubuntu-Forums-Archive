---
title: "Xubuntu Noble - New bootstrap installer."
date: 2024-02-21
forum: Ubuntu Development Version
---

### Post by ajgreeny on 2024-02-21
Oh dear! Whatever was the point of this change?

Xubuntu has moved away from using **ubiquity** as the installer application which for me worked without a problem to  using the **ubuntu-bootsrap** installer in the Feb 21 iso which I believe is used already in Ubuntu and I believe is a snap application; correct?
Having tried this tonight it is a complete failure!
There is no Install icon on the desktop; you have to search the menu for "install" whereupon a white empty window appears for about 5 minutes with a spinning icon, but doing nothing visible.
I eventually gave up waiting and aborted the install.
I did notice that ubiquity is still installable and wondered whether to install that and try installing Xubuntu the previous way using that instead of the bootstrap application.

Has anyone else seen this same behaviour?  The iso I downloaded using zsync so it must be a good one.

There does need to be some indication of how to install the OS when booting the new live system with the bootstrap application, and of course, the new bootstrap application also needs to work properly.

---

### Post by Irihapeti on 2024-02-21
I am trying to remember where I saw this, and I can't, unfortunately. But it was that ubiquity is old, the original developers are no longer involved, no one knows quite how it works, and it's got to a point where it's being held together with brown paper and string, with a bit of glue. If that is true, then I guess it makes sense to replace it with something that's currently under development and maintained.

And, in which case, I can stop reporting that bug about auto-resize and additional drives. Maybe this is why nothing has been done about it. :-k

Now to go and see how badly it works for me...

---

### Post by VMC on 2024-02-21
I didn't have much of an issue with its installer, but have had issue for a while now on the installed OS.

---

### Post by guiverc on 2024-02-22
> **ajgreeny said:**
> Oh dear! Whatever was the point of this change?

Xubuntu has moved away from using ubiquity as the installer application which for me worked without a problem to using

The `ubiquity` installer is deprecated in Ubuntu *noble*, which was made very clear to Ubuntu *flavors* (flavor sync meetings etc) back during prior cycles (lunar/23.03 & mantic/23.10 cycle). Only Ubuntu Budgie moved during the *mantic* cycle to using the `ubuntu-desktop-installer`.. which had benefits for *lunar*/*mantic* in that both `ubiquity` and `ubuntu-desktop-installer` ISOs would be created;  Ubuntu Budgie had both for 23.10.

Ubuntu Budgie documented their switch from `ubiquity` to `ubuntu-desktop-installer`, with this made available to all Ubuntu *flavors*.

Lubuntu was already using the `calamares` installer (*having done so since cosmic/18.10*), and plans continuing with that. Kubuntu will also use `calamares` for *noble*. Lubuntu offered to assist (*where they can*) to provide assistance where required if any wish to use `calamares`.

Xubuntu devs discussed `calamares` (Qt5 based) & `ubuntu-desktop-installer` some time ago, screenshots were even created & shared on IRC showing what Xubuntu would look like if using `calamares` but they've opted to using `ubuntu-desktop-installer`.

FYI:  Using `ubiquity` may work for now; sorry I don't know.. but it may not work reliably once python3 updates to 3.12 which is still in proposed for now (that is when problems are expected to appear).

---

### Post by ajgreeny on 2024-02-22
I accept what you have all said about ubiquity but to suddenly see no "Install" icon on the desktop was  a big surprise to me and the time taken for the bootstrap installer to actually start doing something, a few minutes, other than showing an empty white window is unacceptable and most people would do what I did, ie, give up!

OK, the laptop is pretty old (10yrs) with an Intel i3 cpu and 8G ram, and I was using KVM to create a virtual install but is still very good with Xubuntu and I have no wish to move away from it as my main OS.

---

### Post by corradoventu on 2024-02-22
Have you opened a bug for this problem? If you put the link here.

---

### Post by ajgreeny on 2024-02-22
> **corradoventu said:**
> Have you opened a bug for this problem? If you put the link here.
No, not yet; I was waiting to see what other comments came first. I will try again with another newer iso file from today to see if it is still the same and if it is still a problem I will file a bug.

The iso file from 3 days ago (I think) still used ubiquity so it took me a while to figure out what was going on. I was aware that Ubuntu itself had changed to the bootstrap installer but had not seen any comments about Xubuntu going in that direction.

The biggest surprise however, was the huge amoint of time that the installer just sat with a circulation icon and no activity regarding installing occurring.  Might this have been the fact that I was using KVM for a virtual install? If so it's a disaster for me as I use that always when testing new versions of the OSs I'm interested in.

---

### Post by corradoventu on 2024-02-22
I had the same problem with the ISO dated 2024-02-18 01:57 also after refreshing installer to candidate
Note: no new ISO available after 18 feb using new installer
```
corrado@corrado-n2-nn-0220:~$ snap info ubuntu-desktop-bootstrap        
name:      ubuntu-desktop-bootstrap
summary:   Ubuntu Desktop Bootstrap
publisher: Sebastien Bacher (seb128)
store-url: https://snapcraft.io/ubuntu-desktop-bootstrap
license:   GPL-3.0
description: |
  This project is a modern implementation of the Ubuntu Desktop installer,
  using subiquity as a backend and Flutter for the UI.
snap-id: dLfoSWlQziHta7kJaco3IhnPwGVJ3bIt
channels:
  latest/stable:    0+git.15cde5fb 2024-02-12 (6) 122MB classic
  latest/candidate: 0+git.b31fab62 2024-02-20 (8) 123MB classic
  latest/beta:      &#8593;                                   
  latest/edge:      &#8593;                                   
corrado@corrado-n2-nn-0220:~$ 
```

Try open bug with ubuntu-bug -> invited to use snapcraft

open this bug on snapcraft: 
[https://forum.snapcraft.io/t/xubuntu-installer-gives-an-empty-blank-window/39051](https://forum.snapcraft.io/t/xubuntu-installer-gives-an-empty-blank-window/39051)
-> invited to use launchpad:
[https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2054708](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2054708)

I HATE SNAPs!!

---

### Post by ajgreeny on 2024-02-22
I have added myself to your bug.
I have also filed another bug as ubiquity crashed when I installed that to the live session and tried to use that.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2054717](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/2054717)

---

### Post by grahammechanical on 2024-02-22
I have experienced similar behaviour with the Ubuntu ISO installer. Perhaps my USB stick is 1.0 speed when 2.0 at least would be better. But my experience over the last three weeks is a) the blank white screen. b) the white screen eventually loads with a try/install option. c) one daily image lacked the try/install screen altogether. Found an install icon in the Ubuntu matrix. d) the next day's daily ISO had the try/install screen back.

I have found that with this new installer the install (manual partitioning) sometimes fails and the installer easily drops out of the install process leaving just the slide show working. It feels touch & go to complete the install information without the installer dropping out. Perhaps it is a sensitive touch pad.

On another topic I do like the appearance of the accessibility options right at the beginning of the install process. I think that is a good decision.

Regards

---

### Post by ajgreeny on 2024-02-23
On Xubuntu I never got to the Try/Install choice; it simply sat whirling around saying "Preparing Xubuntu" for 38 minutes.

---

### Post by corradoventu on 2024-02-23
The ISO dated 2024-02-17 01:57 still uses ubiquity 
while the ISO dated 2024-02-18 01:57 uses the NEW INSTALLER snap:ubuntu-desktop-bootstrap	stable/ubuntu-24.04 6
so install problems are completely different.
unfortunately there are no ISOs after the one on February 18th and I don't understand why

---

### Post by Irihapeti on 2024-02-23
I found the same nonsense on Ubuntu Cinnamon. :(

In fact, of the various installs I tried today, only Kubuntu worked. That is, apart from little bits and pieces like the ubuntu base smoke tests. There's not much to go wrong there, anyway.

---

### Post by corradoventu on 2024-02-23
Try today ISO 2024-02-23 10:12 still fail [https://bugs.launchpad.net/subiquity/+bug/2054806](https://bugs.launchpad.net/subiquity/+bug/2054806)
Launcher untrusted, forced to authorize!!! [https://bugs.launchpad.net/subiquity/+bug/2054835](https://bugs.launchpad.net/subiquity/+bug/2054835)

---

### Post by ajgreeny on 2024-02-24
Comment added to your "untrusted" bug as I think it has been happening for a long time, going back to previous Xubuntu versions.

---

### Post by Claus7 on 2024-02-24
Hello,

> **ajgreeny said:**
> ...
The biggest surprise however, was the huge amoint of time that the installer just sat with a circulation icon and no activity regarding installing occurring.  Might this have been the fact that I was using KVM for a virtual install? If so it's a disaster for me as I use that always when testing new versions of the OSs I'm interested in.

this reminded me the first days of trying to install ubuntu with the new installer: it was taking a very long time to install while seeing this circulation icon time and again. Trying anew an installation almost a week ago under virtualbox things were much better. I always try to increase the number of processors and memory dedicated to vb from the default values (which are low) though.

Regards!

---

### Post by VMC on 2024-02-24
I get the "white" screen when installing. Nothing spins, just regular but white screen. Same as Ubuntu a few weeks ago.

---

### Post by VMC on 2024-02-24
> **corradoventu said:**
> I had the same problem with the ISO dated 2024-02-18 01:57 also after refreshing installer to candidate
Note: no new ISO available after 18 feb using new installer
```
corrado@corrado-n2-nn-0220:~$ snap info ubuntu-desktop-bootstrap        
name:      ubuntu-desktop-bootstrap
summary:   Ubuntu Desktop Bootstrap
publisher: Sebastien Bacher (seb128)
store-url: https://snapcraft.io/ubuntu-desktop-bootstrap
license:   GPL-3.0
description: |
  This project is a modern implementation of the Ubuntu Desktop installer,
  using subiquity as a backend and Flutter for the UI.
snap-id: dLfoSWlQziHta7kJaco3IhnPwGVJ3bIt
channels:
  latest/stable:    0+git.15cde5fb 2024-02-12 (6) 122MB classic
  latest/candidate: 0+git.b31fab62 2024-02-20 (8) 123MB classic
  latest/beta:      &#8593;                                   
  latest/edge:      &#8593;                                   
corrado@corrado-n2-nn-0220:~$ 
```

Try open bug with ubuntu-bug -> invited to use snapcraft

open this bug on snapcraft: 
[https://forum.snapcraft.io/t/xubuntu-installer-gives-an-empty-blank-window/39051](https://forum.snapcraft.io/t/xubuntu-installer-gives-an-empty-blank-window/39051)
-> invited to use launchpad:
[https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2054708](https://bugs.launchpad.net/ubuntu-desktop-provision/+bug/2054708)

I HATE SNAPs!!

I don't hate Snaps anymore, I just don't use 'em.

I added to your second link. The "white" blank screen.

---

### Post by corradoventu on 2024-02-24
> **VMC said:**
> I don't hate Snaps anymore, I just don't use 'em.

I added to your second link. The "white" blank screen.

If You install Ubuntu you are using a snap: snap:ubuntu-desktop-bootstrap	stable/ubuntu-24.04	6

---

### Post by ajgreeny on 2024-02-24
> **corradoventu said:**
> If You install Ubuntu you are using a snap: snap:ubuntu-desktop-bootstrap	stable/ubuntu-24.04	6

But presumably after installing the system you can still remove all snaps and the whole snap infrastructure as I do to all my installs of Xubuntu.
There are non-snap alternatives for all the applications/packages that I ever use including all of the default applications installed by default now as snaps.  That may not continue to always be the case and they may come to be forced on Ubuntu users (and all the rest of the *buntu family).

At the moment that is certainly so in Xubuntu which is my OS of choice but if snaps are eventually forced on Xubuntu with no usable alternatives I shall start using Mint-Xfce or some other distro that is not "snap-happy".

I'm afraid I do hate snaps as my hardware is fairly old, 10 and 11 years, so just takes far too long to open snaps such as chromium or firefox so they're all gone along with snapd.

---

### Post by VMC on 2024-02-24
That's my sentiments also ajgreeny! If/when the time comes and I can't remove them, I'm gone.

---

### Post by corradoventu on 2024-02-25
I don't remove snaps, just do not use, if you know them they won't kill you
in Ubuntu I don't remove preinstalled snaps, firefox snap works fine, don't use App Center (I install other apps only by terminal with apt)

---

### Post by ajgreeny on 2024-02-25
> **corradoventu said:**
> I don't remove snaps, just do not use, if you know them they won't kill you
in Ubuntu I don't remove preinstalled snaps, firefox snap works fine, don't use App Center (I install other apps only by terminal with apt)
I take your point, bit if you are not going to use them why not get rid of them?  They do use quite a large amount of space and I hate the idea of having no control of them and how or when they update, (unless that last point is now wrong). Do they still update automatically even if they are never used?  I assume they do.

Also, unfortunately for me, my hardware is older than many users now have, and though it still works fine, it's a slower than many machines my friends have meaning firefox-snap just takes far too long to start the first time it's opened in a session; I'm never sure if it's happening or not!

I also don't use an app centre for package management. If I use a GUI at all it is synaptic which makes searching easier than command line only, but for most package management activities I use terminal only.

---

### Post by Irihapeti on 2024-02-25
I started removing snaps when I discovered that they were as slow as %*#@& on my Raspberry Pi 4 (2GB version). I don't know whether or not they've improved from that point of view, but it's now a habit that I just keep on doing. I also have an ancient (2010 or thereabouts) laptop which would struggle with snaps, so same thing there.

I can see the point of them, but they're not something I particularly want to use myself.

---

### Post by #&amp;thj^% on 2024-02-25
> **Irihapeti said:**
> I started removing snaps when I discovered that they were as slow as %*#@& on my Raspberry Pi 4 (2GB version). I don't know whether or not they've improved from that point of view, but it's now a habit that I just keep on doing. I also have an ancient (2010 or thereabouts) laptop which would struggle with snaps, so same thing there.

I can see the point of them, but they're not something I particularly want to use myself.

+1 I still do as well>>>de-snap/unsnap....but i do some testing for some applications like a VPN for just one to name.
Long story short, they have improved on speed opening, but i prefer to be snap free on my personal machine.

---

### Post by corradoventu on 2024-02-26
New ubuntu-desktop-bootstrap still broken: [https://bugs.launchpad.net/subiquity/+bug/2054806](https://bugs.launchpad.net/subiquity/+bug/2054806)

---

### Post by ajgreeny on 2024-02-27
Still broken in today's iso file, Xubuntu 24.04 LTS "Noble Numbat" - Daily amd64 (20240227)

---

### Post by ajgreeny on 2024-02-28
And once again the same problem with today's iso file, Xubuntu 24.04 LTS "Noble Numbat" - Daily amd64 (20240228)

---

### Post by corradoventu on 2024-02-28
Bug [https://bugs.launchpad.net/subiquity/+bug/2054806](https://bugs.launchpad.net/subiquity/+bug/2054806) is still open and Unassigned so It seems like no one cares.
Still same problem with ISO dated 2024-02-29

---

### Post by ajgreeny on 2024-02-29
Tried again with the Xubuntu 24.04 LTS "Noble Numbat" - Daily amd64 (20240229) but still the same!

Have added this to the qa-tracker site.

This is incredibly disappointing as there is no way that anyone can do any installation testing; we are all still using an installation made from a much earlier iso file

---

### Post by corradoventu on 2024-03-01
Still with ISO dated 01-Mar

---

### Post by guiverc on 2024-03-04
With luck Xubuntu will [I]be better soon.

[/I][https://launchpad.net/ubuntu/+source/xubuntu-meta/2.259](https://launchpad.net/ubuntu/+source/xubuntu-meta/2.259)

(*cloud-init*)   ...   fingers crossed anyway.   (Thanks Dennis Loose, FossFreedom, Sean Davis..)
Hopefully tomorrow Lubuntu/Kubuntu/Ubuntu-Unity will have the *calamares* issue fixed, and working ISO too (*in time*; *Simon Q's working on it*).

---

### Post by corradoventu on 2024-03-04
Good new for calamares, but what about Xubuntu new bootstrap installer?

---

### Post by ajgreeny on 2024-03-04
> **corradoventu said:**
> Good new for calamares, but what about Xubuntu new bootstrap installer?
Yes please!

We really need some way to install this iso and test the OS from a new installation.
I have just tried again with the iso ***Xubuntu 24.04 LTS "Noble Numbat" - Daily amd64 (20240304)*** but still no installer appearing.

---

### Post by corradoventu on 2024-03-04
let's console ourselves by thinking that Ubuntu also has an installer that doesn't work: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2055294](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2055294)

---

### Post by ajgreeny on 2024-03-04
> **corradoventu said:**
> let's console ourselves by thinking that Ubuntu also has an installer that doesn't work: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2055294](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/2055294)
Yes, I know that as I have tried it as well!
Just out of inyerest I have also tried installing ubiquity and installing using that but it crashed so I also tried installing and using calamres; it installed but would not start or run so it's back to the drawing board and waiting.

---

### Post by VMC on 2024-03-04
> **ajgreeny said:**
> Yes, I know that as I have tried it as well!
Just out of inyerest I have also tried installing ubiquity and installing using that but it crashed so I also tried installing and using calamres; it installed but would not start or run so it's back to the drawing board and waiting.

I installed ubiquity as well. It crashed around 20%. Odd, it used kde.ui. didn't try calamaris.
It you right-click the installer icon and say use terminal, then you can see the errors.;cloud something.

---

### Post by VMC on 2024-03-05
Xubuntu-minimal Nobel, Now works!
Dated today, 3-5-24

Haven't tried Ubuntu yet.

---

### Post by VMC on 2024-03-05
Just tested Ubuntu, with sha256sum:
2b36bb340c27e062d81782ea149bfdf96ae02b1b7e9e5657395d550d66023319 *noble-desktop-amd64.iso

It now installs. There's a bug to be sent, but otherwise it installs.

---

### Post by ajgreeny on 2024-03-05
If the Xubuntu-minimal installs now i will certainly zsync update my March 4th iso and try again tomorrow with the March 6th iso of a full desktop install.

Here's hoping!

---

### Post by Irihapeti on 2024-03-05
I just tried 20240305.1, full ISO (not minimal)

It loads. It works up until the very last, then fails. Possibly the same error that's been occurring on the Ubuntu installer.

Progress, I suppose...:-s

---

### Post by Irihapeti on 2024-03-05
Tried successfully on a BIOS (non-UEFI) VM, and it works.

I have no idea why the difference, and I don't have a spare UEFI-capable box to test it on. But progress, I guess... :)

---

### Post by VMC on 2024-03-06
Xubuntu-minimal failed near the end.

---

### Post by Irihapeti on 2024-03-06
20240306 xubuntu-full failed near end, too.

Edit: That was on a VM with UEFI. I'll try a BIOS install in a bit, but I want to make my dinner first. :)

---

### Post by VMC on 2024-03-06
I have Ubuntu Nobel installed from an older ISO. Since a few days ago with full update, I get this with Firefox:
"**Gah. Your tab just crashed.**", then it says to restart tab. Nothing works. Checked online and tried every possible solution. nada.
I installed Chrome and it works. Xubuntu just now after today's updates does the same thing.

I'd be curious to see if anyone else has this issue once they get Ubuntu installed.

---

### Post by Irihapeti on 2024-03-06
I've got Ubuntu noble (updated from jammy) on a Surface Go 3. I use Firefox-esr from the LP PPA, I was using it extensively last night with no problems.

Maybe that doesn't quite count, as I tend to remove all snaps and a few other things when I do a working install (as distinct from just testing).

---

### Post by corradoventu on 2024-03-06
> **VMC said:**
> I have Ubuntu Nobel installed from an older ISO. Since a few days ago with full update, I get this with Firefox:
"**Gah. Your tab just crashed.**", then it says to restart tab. Nothing works. Checked online and tried every possible solution. nada.
I installed Chrome and it works. Xubuntu just now after today's updates does the same thing.

I'd be curious to see if anyone else has this issue once they get Ubuntu installed.

I have the same problem with Firefox trunk [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/2055973](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/2055973)
but seems common with Firefox.deb

---

### Post by corradoventu on 2024-03-07
Today install SUCCESSFUL from ISO dated 2024-03-06!!!

---

### Post by ajgreeny on 2024-03-07
Yes, same here on both my desktop and laptop, both using KVM/QEMU and both UEFI.

I was totally confused by our broadband network going down and originally thought it was the VMs but it was gone throughout the area for 2 hours, so haven't had time to fully check everything but so far all looks good.

The new installer seems to take a little longer than ubiquity did but that maybe because I am just not used to it.
I would, however, appreciate a bit more feedback about what is actually happening. All it tells you is that it's "installing the system" then that its "setting up the system", nothing more than that which is a bit disappointing. 

I'll report further on anything else after using them tomorrow. At least it's now possible to install from a newer iso file than has been possible for some time.

Incidentally I have had no problems at all with firefox, but I use the direct download of the .tar.bz from Mozilla not the snap, nor even a .deb package. All working fine!

---

### Post by ajgreeny on 2024-03-08
Broadband now back so I have updated both the desktop and laptop successfully.
I note that thunderbird is now moving to a snap package as well as firefox and so a test-bed I removed thunderbird from the Noble system, downloaded the thunderbird.tar.bz (or was it .tar.gz) extracted that and ran it from the executable in the new thunderbird folder. No problems picking up my old profile and it all seems to work seamlessly.

My hardware is all getting old; too old to run snaps fast enough for me so I remove them all along with the complete snap infrastructure so I'm delighted to see that the Mozilla thunderbird archive mentioned above works just the same as the firefox archive which I've been using since Ubuntu forced that snap on users.

Snap rant over! Now back to testing Xubuntu Noble again.

EDIT:
I was too soon saying I had no problem with Firefox on these two KVM installs as today I can not get anything except a Tab crashed notice.
I am still using the Mozilla .tar.bz archive in these two installs.
Hopefully updates to the system will overcome this quickly.  The Mozilla archive is the same as the one I'm using to write this on my 22.04 main machine, so it is not that archive at fault but its use by 24.04.

---

### Post by corradoventu on 2024-03-08
The problem with FireFox.deb comes from: [https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844](https://bugs.launchpad.net/ubuntu/+source/apparmor/+bug/2046844)
so I'm afraid the solution is far away

---

### Post by ajgreeny on 2024-03-08
That sounds a big problem with firefox which must be overcome quickly as it is the only preinstalled browser in the Ubuntu family. I always remove snaps as my computer is too old to run them quickly enough. I have just started the installed firefox snap which did work but it took over a minute to show anything on screen, far too long to keep them on my machines.

Another problem I have just found is the inability to open Software & Updates from the menu.
This is probably a result of the change of the sources from **/etc/apt/sources.list** to **/etc/apt/sources.list.d/ubuntu.sources** but it needs sorting out so that changes can be made more easily than searching for those sources.

This also means that trying to open the Settings -> Repositories in synaptic fails - not good!

---

### Post by corradoventu on 2024-03-09
For Software & Updates the bug is: [https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/2053228)

---

### Post by ajgreeny on 2024-03-09
Have added myself to that bug.

EDIT:
I have also just realised that the snap firefox still does work in Noble; it is the **.deb** version or the archive **.tar.bz** that throws the error about the tab crashing so have temporarily (I hope) installed the slow snap firefox.
Maybe I will eventually get used to the slow opening and just live with it as I can not manage without firefox as my main browser, or not yet anyway.

---

