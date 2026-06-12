---
title: "GDM 3.5.91 greeter"
date: 2012-09-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by sgage on 2012-09-09
What's up with the full-screen blah-colored greeter in GDM 3.5.91?

---

### Post by Harry33 on 2012-09-09
> **sgage said:**
> What's up with the full-screen blah-colored greeter in GDM 3.5.91?

I am getting that ugly thing with GS_3.5.91 only.

---

### Post by sgage on 2012-09-09
> **Harry33 said:**
> I am getting that ugly thing with GS_3.5.91 only.

How strange that the shell should affect the display manager greeter... but that seems to be the case.

---

### Post by Harry33 on 2012-09-09
> **sgage said:**
> How strange that the shell should affect the display manager greeter... but that seems to be the case.

I was wondering the same thing.

---

### Post by Stinger on 2012-09-09
> **sgage said:**
> What's up with the full-screen blah-colored greeter in GDM 3.5.91?

Just wait to you try the lock screen, you are in for a BIG surprise :biggrin:

---

### Post by sgage on 2012-09-09
> **Stinger said:**
> Just wait to you try the lock screen, you are in for a BIG surprise :biggrin:

I kinda like the lock screen.  :KS

The full-screen gdm greeter isn't really so bad, except that the set gdm background flashes for a second before it comes up, and shows again in the interval between logging in and the GS coming up. I changed my gdm background so it wouldn't be so jarring.

---

### Post by Stinger on 2012-09-09
@sgage

Graphics card and drivers please ?

---

### Post by jbicha on 2012-09-09
> **sgage said:**
> How strange that the shell should affect the display manager greeter... but that seems to be the case.

That's how it works. gdm can either be run in shell mode where GNOME Shell provides the log-in screen or in fallback mode which doesn't need GNOME Shell or working 3D and looks like gdm 3.0 as present in Ubuntu 12.04 LTS.

You should be able to force fallback mode by editing /etc/gdm/greeter.gsettings and uncommenting the following lines:

```

[org.gnome.desktop.session]
session-name='gdm-fallback'

```

That's done by default in Debian Wheezy, and they also uncomment the bottom two lines in that file.

If you're curious about tweaking GDM, you should also check out custom.conf in that same directory.

---

### Post by sgage on 2012-09-09
> **Stinger said:**
> @sgage

Graphics card and drivers please ?

Nvidia GeForce 8500 GT, nouveau drivers.

---

### Post by sgage on 2012-09-09
> **jbicha said:**
> That's how it works. gdm can either be run in shell mode where GNOME Shell provides the log-in screen or in fallback mode which doesn't need GNOME Shell or working 3D and looks like gdm 3.0 as present in Ubuntu 12.04 LTS.

You should be able to force fallback mode by editing /etc/gdm/greeter.gsettings and uncommenting the following lines:

```

[org.gnome.desktop.session]
session-name='gdm-fallback'

```

That's done by default in Debian Wheezy, and they also uncomment the bottom two lines in that file.

If you're curious about tweaking GDM, you should also check out custom.conf in that same directory.

Thanks for the info, Jeremy. I know how to tweak custom.conf to autologin - I should look into other possibilities.

Didn't know how gdm had a shell mode - interesting!

---

### Post by Stinger on 2012-09-09
> **sgage said:**
> Nvidia GeForce 8500 GT, nouveau drivers.
Could be the [nouveau driver]("http://nouveau.freedesktop.org/wiki/"), have you tried the nvidia driver ? 

Also 'glxinfo' from a terminal should give a hint.

I got:
> direct rendering: Yes
and
> OpenGL renderer string: Gallium 0.4 on AMD RV730

How about 'glxgears' from terminal ? try running the gears in a maximized window.

---

### Post by sgage on 2012-09-09
> **Stinger said:**
> Could be the [nouveau driver]("http://nouveau.freedesktop.org/wiki/"), have you tried the nvidia driver ? 

Also 'glxinfo' from a terminal should give a hint.

I got:

and


How about 'glxgears' from terminal ? try running the gears in a maximized window.

See the reply from jbicha - it's a new "shell mode" for gdm. What will they think of next? :KS

---

### Post by Stinger on 2012-09-10
> **sgage said:**
> See the reply from jbicha - it's a new "shell mode" for gdm. What will they think of next? :KS

My bad, thought you were having some real trouble :rolleyes:

---

### Post by sgage on 2012-09-10
> **sgage said:**
> Thanks for the info, Jeremy. I know how to tweak custom.conf to autologin - I should look into other possibilities.

Didn't know how gdm had a shell mode - interesting!

Hi Jeremy,

I tried

```
[org.gnome.desktop.session]
session-name='gdm-fallback'
```

but gdm is still using the shell mode. Any idea what's going on?

---

### Post by mc4man on 2012-09-10
> **sgage said:**
> Hi Jeremy,

I tried

```
[org.gnome.desktop.session]
session-name='gdm-fallback'
```

but gdm is still using the shell mode. Any idea what's going on?
At least here that schema/key, org.gnome.desktop.session/session-name=, is used currently to set the System default session

So in that regard you wouldn't want it actually being set in dconf to gdm-* as they don't exist.

Overall this may just be some GS bug (unless they decided to go with FS greeter instead of a box on the greeter Bg.

(a debug on the greeter does show something about a fail on modal 'whatever', on my other machine atm & don't quite remember exact wording. May be related or may be nothing ..

---

### Post by Harry33 on 2012-09-11
The grey login screen is really looking terrible.
I would be happy to know how to get back the nice small black window on the background like it was with GS_3.5.4.

---

### Post by sgage on 2012-09-11
> **Harry33 said:**
> The grey login screen is really looking terrible.
I would be happy to know how to get back the nice small black window on the background like it was with GS_3.5.4.

Since I auto-login, I hardly ever see gdm, but I, too, would like it back the old way - seems much more in keeping with the overall GS look...

---

### Post by mc4man on 2012-09-11
> **Harry33 said:**
> The grey login screen is really looking terrible.
I would be happy to know how to get back the nice small black window on the background like it was with GS_3.5.4.

Really looks like something needs fixing - it appers to use /usr/share/gdm/greeter/applications/gnome-shell.desktop which exec='s
Exec=gnome-shell --mode=gdm

(enable debug in the greeter config, maybe you'll pick up on something

While likely a poor atm idea, if that Exec= was changed to the simple-greeters one would get that login window instead.
Exec=/usr/lib/gdm/gdm-simple-greeter

---

### Post by sgage on 2012-09-11
> **mc4man said:**
> Really looks like something needs fixing - it appers to use /usr/share/gdm/greeter/applications/gnome-shell.desktop which exec='s
Exec=gnome-shell --mode=gdm

(enable debug in the greeter config, maybe you'll pick up on something

While likely a poor atm idea, if that Exec= was changed to the simple-greeters one would get that login window instead.
Exec=/usr/lib/gdm/gdm-simple-greeter

I will give it a try (even though it probably IS a poor idea :KS )

[Edit: I did try it - it did give a sign-in dialog on the gdm background, but the old-school dialog box - not the nice black one.]

---

### Post by Harry33 on 2012-09-11
> **sgage said:**
> I will give it a try (even though it probably IS a poor idea :KS )

[Edit: I did try it - it did give a sign-in dialog on the gdm background, but the old-school dialog box - not the nice black one.]

Exactly that happens.
I think the nice black box is only how GS_3.5.4 works.
Instead, GS_3.5.91 gives that grey look for the underlying background as the login screen opens above it.
So this seems to be a GS issue, not a Gdm issue, which cannot be modified by adjusting Gdm settings.

---

### Post by sgage on 2012-09-11
> **Harry33 said:**
> Exactly that happens.
I think the nice black box is only how GS_3.5.4 works.
Instead, GS_3.5.91 gives that grey look for the underlying background as the login screen opens above it.
So this seems to be a GS issue, not a Gdm issue, which cannot be modified by adjusting Gdm settings.

I think that's only partially correct. For example, if you set a gdm background of your choice, you will see it for an instant before the gray screen comes up, and for a second or two after you login and before the GS background comes up.

If you tweak the .desktop file as described above, you will get a login dialog box on top of your chosen gdm background. But the dialog box isn't the nice black one - it's the old-fashioned "simple greeter".

By default now, gdm is set to use "gnome-shell mode=gdm" as the greeter, so yes, gnome-shell is generating that gray screen with the (to my eyes) not-compatible looking login dialog. 

But gdm 3.5.91 does not need to use gnome-shell in a gdm mode as its greeter, as established by experimenting as described above. 

It seems to me that there is a missing greeter - all that's available is the old-style simple-greeter, or to use GS as the greeter. Or perhaps there was simply a regression in simple-greeter. In any case, if GS is going to be used as the greeter, it seems to me there ought to be some way of tweaking at least the background - this should be presented in the Systems Settings or something.

Whatever, I'd like to see it like it was, but again, I auto-login so hardly ever see the greeter anyway ;)

---

