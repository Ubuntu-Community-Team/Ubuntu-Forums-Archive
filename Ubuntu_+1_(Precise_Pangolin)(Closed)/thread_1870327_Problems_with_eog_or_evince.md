---
title: "Problems with eog or evince?"
date: 2011-10-27
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Harry33 on 2011-10-27
Just wanted to know, if someone else is also having problems with eog (image viewer) or evince (document viewer).

I cannot get evince to work with the latest libutouch-geis1 (2.2.1-0ubuntu1), it does not even start with it. After downgrading to libutouch-geis1 to the version 2.1.2-0ubuntu4 all is well again.
Like I said in another thread, I believe this is because I have xserver 1.11.1 installed and it does not have the utouch support yet.

Also, I cannot get eog to work. It will not start either. Not even with the downgraded libutouch-geis1 (2.1.2-0ubuntu4). From the bug reports one can read that there are problems with eog also with xserver 1.10 series.

How about you?

---

### Post by cariboo on 2011-10-27
I had a problem with evince and eog segfaulting, but it was because of missing dependencies, that regular updates have fixed. I'm running a pretty box stock Precise Unity/Gnome-shell install with only grub-customizer, handbrake ppas and calibre installed via the script from the web site.

---

### Post by zika on 2011-10-27
[http://ubuntuforums.org/showthread.php?t=1866250](http://ubuntuforums.org/showthread.php?t=1866250)

---

### Post by mc4man on 2011-10-27
there is this concerning eog, maybe your issue ?
[https://bugzilla.gnome.org/show_bug.cgi?id=662630](https://bugzilla.gnome.org/show_bug.cgi?id=662630)

---

### Post by Harry33 on 2011-10-27
> **mc4man said:**
> there is this concerning eog, maybe your issue ?
[https://bugzilla.gnome.org/show_bug.cgi?id=662630](https://bugzilla.gnome.org/show_bug.cgi?id=662630)

Thanks mc4man, it is actually possible, that it is glib2.0_2.31.0 that causes this.
I do have it installed (from the Ricotz Testing PPA).

---

### Post by Harry33 on 2011-10-28
Today in Xorg-edgers (Oneiric branch) there was a xserver 1.11.1 update, which was built with multitouch patch.
Unfortunately installing this borked desktop and froze applications, apparently after some mouse clicks.
It looked like evdev driver did not handle this right.

Anyway, now there is another xserver 1.11.1 update without multitouch patch.
That one works well.
But, not with eog nor evince with utouch-geis1_2.2.1-0ubuntu1 :p

---

### Post by Harry33 on 2011-11-03
Back to Eog issue and this bug report:
[https://bugzilla.gnome.org/show_bug.cgi?id=662630](https://bugzilla.gnome.org/show_bug.cgi?id=662630)

So this will be fixed soon.

> 
This problem has been fixed in the development version. The fix will be available in the next major software release. Thank you for your bug report.


---

### Post by Harry33 on 2011-11-03
And here is a PPA (Tobias Wolf) with the patched update of Eog:
 - version 3.2.1-0ubuntu1ppa1

[https://launchpad.net/~towolf/+archive/crack](https://launchpad.net/~towolf/+archive/crack)

Just tested it and it works.
Now Eog is working fine with glib2.0_2.31.0 and xserver 1.11.1 rc2.

---

### Post by paul_in_london on 2011-11-03
> **Harry33 said:**
> And here is a PPA (Tobias Wolf) with the patched update of Eog:
 - version 3.2.1-0ubuntu1ppa1

[https://launchpad.net/~towolf/+archive/crack](https://launchpad.net/~towolf/+archive/crack)

Just tested it and it works.
Now Eog is working fine with glib2.0_2.31.0 and xserver 1.11.1 rc2.

Hi Harry,

evince still isn't working for me with that ppa.

```
paul@precise-64:~$ apt-cache policy evince
evince:
  Installed: 3.2.1-0ubuntu2
  Candidate: 3.2.1-0ubuntu2
  Version table:
 *** 3.2.1-0ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main amd64 Packages
        100 /var/lib/dpkg/status
N: Ignoring file 'ricotz-testing-precise.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-precise.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-precise.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-precise.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
paul@precise-64:~$
```

```
paul@precise-64:~$ apt-cache policy libglib2.0-0
libglib2.0-0:
  Installed: 2.31.0+git20111102.d2d62ecf-0ubuntu1~11.10~ricotz0
  Candidate: 2.31.0+git20111102.d2d62ecf-0ubuntu1~11.10~ricotz0
  Version table:
 *** 2.31.0+git20111102.d2d62ecf-0ubuntu1~11.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     2.31.0-0ubuntu1~precise1 0
        500 http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/ precise/main amd64 Packages
     2.30.1-2ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
N: Ignoring file 'ricotz-testing-precise.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-precise.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-precise.list.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
N: Ignoring file 'ricotz-testing-precise.list.save.hidden' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
paul@precise-64:~$
```

```
paul@precise-64:~$ evince ~/Desktop/Absolute_FreeBSD.pdf
Gtk-Message: Failed to load module "canberra-gtk-module"
^C
paul@precise-64:~$
```

What other ppas are you using?

So far I've tried adding the gnome3 team ppa and then purging and reinstalling **libcanberra-gtk-module**.

Some more head-scratching required...

---

### Post by paul_in_london on 2011-11-03
Sorry. The full error output is:

```
paul@precise-64:~$ evince ~/Desktop/Absolute_FreeBSD.pdf
Gtk-Message: Failed to load module "canberra-gtk-module"
`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

`menu_proxy_module_load': evince: undefined symbol: menu_proxy_module_load

Gtk-WARNING **: Failed to load type module: (null)

^C
paul@precise-64:~$
```

---

### Post by paul_in_london on 2011-11-03
Got rid of most of the errors after:

```
sudo mv /etc/X11/Xsession.d/80appmenu /etc/X11/Xsession.d/80appmenu.old
```

and a restart.

Then installed appmenu-gtk3 and tried to start evince a couple of times to see if any of the previous errors came back.

Now I have:

```
paul@precise-64:~$ ls -la /etc/X11/Xsession.d/80appmenu*
-rw-r--r-- 1 root root 108 Sep 29 17:49 /etc/X11/Xsession.d/80appmenu-gtk3
-rw-r--r-- 1 root root 109 Jul 25 18:31 /etc/X11/Xsession.d/80appmenu.old
paul@precise-64:~$
```

and when I try to start evince just the remaining error:

```
paul@precise-64:~$ evince ~/Desktop/Absolute_FreeBSD.pdf
Gtk-Message: Failed to load module "canberra-gtk-module"
```

---

### Post by paul_in_london on 2011-11-03
```
paul@precise-64:~$ locate libcanberra-gtk-module.so
/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
paul@precise-64:~$
```

but I think evince expects to be running under gtk3.

@Harry33: what does the above command give you?

---

### Post by zika on 2011-11-04
> **paul_in_london said:**
> ```
paul@precise-64:~$ locate libcanberra-gtk-module.so
/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
paul@precise-64:~$
```but I think evince expects to be running under gtk3.

@Harry33: what does the above command give you?```
 locate libcanberra-gtk-module.so
/usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so
/usr/lib/gtk-3.0/modules/libcanberra-gtk-module.so

```After update/upgrade this morning...
Evince, still, not working. I have, now, nearly the same setup as @Harry33...

---

### Post by Harry33 on 2011-11-04
1. EOG

The problem with Eog was that it did not work with new glib2.0_2.31.0.
However, this glib2.0 version is not yet available from Precise repos.
I am using the Ricotz testing PPA, and also the new glib2.0 git version from there.

Anyways, after the Eog update (3.2.1-0ubuntu1ppa1) from the Tobias Wolf PPA, it works just fine.

2. EVINCE

Evince does not have problems with glib2.0_2.31.0.
Instead, Evince does have problems with the newest 1.11 series xserver.
This is because xserver 1.11 does not yet have the multitouch support.
However, this xserver version is not yet available from precise repos.
I am using Xorg-edgers PPA (Oneiric branch), and also the new xserver 1.11.2 rc2 git version from there + nvidia-current_290.03.

With the latest libutouch-geis1 (2.2.1-0ubuntu1) Evince does not even start.
But after  downgrading libutouch-geis1 to the version 2.1.2-0ubuntu4 all is well  again.

---

### Post by Harry33 on 2011-11-04
> **paul_in_london said:**
> Hi Harry,

evince still isn't working for me with that ppa.
...
What other ppas are you using?

So far I've tried adding the gnome3 team ppa and then purging and reinstalling **libcanberra-gtk-module**.

Some more head-scratching required...

Please, if you are using Ricotz testing PPA, do not use Gnome3 PPA or gnome3 team ppa. There is nothing new for Precise there. Do not use Ricots Staging PPA either, it is very unstable now.

Evince does not depend on libcanberra (= event sound sysntem).

I would clean the /etc/apt/sources.list first. You must have problems there.
Purge all additional PPA's, leave only pure Precise left.

Then purge evince evince-common libevince3-3 libspectre1.
Then reinstall the purged packages (but not the PPA's).

Does evince then work?

---

### Post by paul_in_london on 2011-11-04
> **Harry33 said:**
> 1. EOG

The problem with Eog was that it did not work with new glib2.0_2.31.0.
However, this glib2.0 version is not yet available from Precise repos.
I am using the Ricotz testing PPA, and also the new glib2.0 git version from there.

Anyways, after the Eog update (3.2.1-0ubuntu1ppa1) from the Tobias Wolf PPA, it works just fine.

2. EVINCE

Evince does not have problems with glib2.0_2.31.0.
Instead, Evince does have problems with the newest 1.11 series xserver.
This is because xserver 1.11 does not yet have the multitouch support.
However, this xserver version is not yet available from precise repos.
I am using Xorg-edgers PPA (Oneiric branch), and also the new xserver 1.11.2 rc2 git version from there + nvidia-current_290.03.

With the latest libutouch-geis1 (2.2.1-0ubuntu1) Evince does not even start.
But after  downgrading libutouch-geis1 to the version 2.1.2-0ubuntu4 all is well  again.

Thanks Harry. This was all on 64 bit so last night after my previous post I added the **towolf/crack** ppa to my PP 32 bit install as well because I started to think the problem might be specific to 64 bit and I was wondering whether I should try running **evince** with 32 bit libraries. As far as I remember, only **eog** was offered as an upgrade from that ppa on the 32 bit install at the time and not **evince**.

Like you, I'm using **xorg-edgers** and **nvidia-current_290.03** so if it's still not working later I'll try downgrading **libutouch-geis1**.

---

### Post by zika on 2011-11-04
> **Harry33 said:**
> 1. EOG

The problem with Eog was that it did not work with new glib2.0_2.31.0.
However, this glib2.0 version is not yet available from Precise repos.
I am using the Ricotz testing PPA, and also the new glib2.0 git version from there.

Anyways, after the Eog update (3.2.1-0ubuntu1ppa1) from the Tobias Wolf PPA, it works just fine.

2. EVINCE

Evince does not have problems with glib2.0_2.31.0.
Instead, Evince does have problems with the newest 1.11 series xserver.
This is because xserver 1.11 does not yet have the multitouch support.
However, this xserver version is not yet available from precise repos.
I am using Xorg-edgers PPA (Oneiric branch), and also the new xserver 1.11.2 rc2 git version from there + nvidia-current_290.03.

With the latest libutouch-geis1 (2.2.1-0ubuntu1) Evince does not even start.
But after  downgrading libutouch-geis1 to the version 2.1.2-0ubuntu4 all is well  again.I've gathered that from Your previous posts. I replicated that and that is what I've reported earlier...

---

### Post by zika on 2011-11-04
> **Harry33 said:**
> Please, if you are using Ricotz testing PPA, do not use Gnome3 PPA or gnome3 team ppa. There is nothing new for Precise there. Do not use Ricots Staging PPA either, it is very unstable now.But, on Ricotz testing PPA, there is warning:
> While using this ppa make sure you also added the Gnome3 PPA of the same
distribution version!
ppa:gnome3-team/gnome3 ([https://launchpad.net/~gnome3-team/+archive/gnome3]("https://launchpad.net/%7Egnome3-team/+archive/gnome3"))...

---

### Post by zika on 2011-11-04
> **Harry33 said:**
> With the latest libutouch-geis1 (2.2.1-0ubuntu1) Evince does not even start.
But after  downgrading libutouch-geis1 to the version 2.1.2-0ubuntu4 all is well  again.Just like that. Downgrading work{s,ed} as we've concluded earlier.

---

### Post by paul_in_london on 2011-11-04
> **Harry33 said:**
> Please, if you are using Ricotz testing PPA, do not use Gnome3 PPA or gnome3 team ppa. There is nothing new for Precise there.

I'm using this one:

```
ppa.launchpad.net/ricotz/testing
```

I can't remember why I also added the **gnome3-team** ppa to my PP 64 bit install last night when I was looking at this problem. I now realise that, although that ppa does have a **precise** channel, it seems to be the same as the **oneiric** channel at the moment.

> **Harry33 said:**
> Do not use Ricots Staging PPA either, it is very unstable now.

Understood.

> **Harry33 said:**
> Evince does not depend on libcanberra (= event sound sysntem).

Yes I know, but I got distracted trying to work out how to get rid of the

```
Gtk-Message: Failed to load module "canberra-gtk-module"
```

error! :) 

> **Harry33 said:**
> I would clean the /etc/apt/sources.list first. You must have problems there.
Purge all additional PPA's, leave only pure Precise left.

Then purge evince evince-common libevince3-3 libspectre1.
Then reinstall the purged packages (but not the PPA's).

Does evince then work?

I'm definitely going to remove the **gnome3-team** ppa, but I'd prefer to keep **xorg-edgers** and **ricotz testing** even if it means I can't use **evince** in precise for a while.

Thanks again for your feedback :)

---

### Post by Harry33 on 2011-11-04
> **paul_in_london said:**
> 
...
I'm definitely going to remove the **gnome3-team** ppa, but I'd prefer to keep **xorg-edgers** and **ricotz testing** even if it means I can't use **evince** in precise for a while.

Thanks again for your feedback :)

Paul, you can have Evince working, but you need to downgrade libutouch-geis1 like I have posted earlier in this thread.

---

### Post by paul_in_london on 2011-11-04
> **Harry33 said:**
> Paul, you can have Evince working, but you need to downgrade libutouch-geis1 like I have posted earlier in this thread.

Just tested this successfully (keeping xorg-edgers and ricotz testing enabled) in a 32 bit VM - thanks! :)

Will try on my 64 bit install @ home tonight or tomorrow.

---

