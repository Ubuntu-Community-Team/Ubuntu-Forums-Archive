---
title: "Google Chrome Browser and AppArmor"
date: 2010-01-13
forum: Security
---

### Post by running_rabbit07 on 2010-01-13
Has anyone made an AppArmor profile for Google Chrome?

---

### Post by dogdo on 2010-01-13
But i thought that google chrome is already sandboxed itself?

---

### Post by running_rabbit07 on 2010-01-13
When configuring the settings, it asks if you want to share info and crash reports. Just click no. And with the right AppArmor settings, one can protect one's self from alowing Chrome to access files on the system.

Please, this thread is not meant for the discussion of Google and privacy. **Just Google Chrome and AppArmor making smileys together.**

---

### Post by rookcifer on 2010-01-13
> **running_rabbit07 said:**
> Has anyone made an AppArmor profile for Google Chrome?

I've tried and it's very difficult to do because Chrome does not work like Firefox does -- it's more modular than firefox and opens a number of "renderers."  Therefore, it's hard to contain all the "parts."  It would take someone who is much more familiar with the Chrome renderers than I am to be able to do it.  I have tried using genprof and it simply doesn't produce usable results.  One would need to write the profile by hand.

That said, Chrome already has its own sandbox and it is turned on in Ubuntu (I verified this with the Chrome developers on IRC).  It's called the suid sandbox and you can read more [here.]("http://scarybeastsecurity.blogspot.com/2009/10/chromium-and-linux-sandboxing.html")  Basically it opens the Chrome renderer in a chroot() jail.  There is another sandbox called ["seccomp"]("http://www.imperialviolet.org/2009/08/26/seccomp.html") that can also be used.  However, it is not the default.

P.S. I use Chromium and not Chrome and I know Chromium has the SUID sandbox enabled by default.  I would assume Chrome does as well.

---

### Post by running_rabbit07 on 2010-01-14
That makes me feel a bit better. I was confused about the "sandbox" term when it was posted above. I didn't realize that it means the Google devs are doing security for it. 

That said, I will be doing some studying on how AppArmor works and see if I can start writing profiles for it. I would like to start getting some decent profiles together for AppArmor, so that they can be added to the ones that come with Ubuntu. This is going to be my home system, so I want it to be as secure as we can get it. It makes life easier when people that are new to Ubuntu and Linux in general, if people can just do a quick configuration and move on to their next task.

---

### Post by iansane on 2011-06-11
I began having issues with Chrome after installing apparmor-profiles yesterday, which is a set of default security profiles.

One of them is usr.bin.chromium-browser.
Here is the part in the profile that has references to /dev/shm which is causing permission denied error.

```

# chromium mmaps all kinds of things for speed.
/etc/passwd m,
/usr/share/fonts/truetype/**/*.tt[cf] m,
/usr/share/fonts/**/*.pfb m,
/usr/share/mime/mime.cache m,
/usr/share/icons/**/*.cache m,
owner /dev/shm/pulse-shm* m,
owner @{HOME}/.local/share/mime/mime.cache m,
owner /tmp/** m,

@{PROC}/sys/kernel/shmmax r,
owner /dev/shm/{,.}org.chromium.* mrw,

/usr/lib/chromium-browser/*.pak mr,
/usr/lib/chromium-browser/locales/* mr,

```

Not having a clue how to read one of these profiles yet, I copied the chromium profile and pasted it into a new profile, opt.google.chrome.chrome thinking since the chromium profile is in the profiles package from Ubuntu, it would be a fixed profile and let chrome work. reloaded profiles and tried again with the same results.

Of course this doesn't work because there are several entries for chromium and probably some missing entries for chrome. 

I'm searchin my file system for chrome equivelants to try and use this chromium profile as a template modifying what needs to be modified.

Maybe I'll get it figured out. If so, I'll post a copy of the profile on here.

---

### Post by iansane on 2011-06-11
I installed chromium and reloaded apparmor profiles with no luck. Chromium doesn't work either and has the same error message about being denied access to /dev/shm.

So for a temp fix I thought I would disable the chromium profile and the new chrome profile. I found that by default the firefox profile is already in "disabled" which is confusing because what's the point of having apparmor if your not going to be able to use it on you main internet accessing application?

Anyway, I added links in the disabled directory to match the existing firefox link.
```
sudo ln -s /etc/apparmor.d/opt.google.chrome.chrome opt.google.chrome.chrome

and

sudo ln -s /etc/apparmor.d/usr.bin.chromium-browser usr.bin.chromium-browser


```

followed by ls in the disabled directory to confirm.

Then reload profiles
```
sudo invoke-rc.d apparmor reload
```

Which showed the disabled profiles on load
```
 * Reloading AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: opt.google.chrome.chrome
Skipping profile in /etc/apparmor.d/disable: usr.bin.chromium-browser
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                         [ OK ]

```


staus changed: I restarted the PC and the new profile load took place. Now with the profiles disabled both chrome and chromium work. I'm wondering why reloading the profiles didn't work though. I probably could have logged out and back in to see the changes reflected.

Either way though, now none of my browsers are working under any apparmor security so it's kinda pointless to have it.

---

### Post by Dave_L on 2011-06-12
> **iansane said:**
> Then reload profiles
```
sudo invoke-rc.d apparmor reload
```

I don't know what the "reload" command does.  If I want to reload all the profiles, I've been doing it by restarting apparmor:

```
sudo service apparmor restart
```

---

### Post by iansane on 2011-06-12
Dave_L yeah apparently that command is old or was wrong. I picked it up by googleing how to restart apparmor.

The regular service restart command does work rather than having to log out or restart the PC.

However, this didn't fix the problem and neither does chmod 777 on /dev/shm in my opinion since the point of apparmor is to control access to system resources to help prevent hacking and virus propagation.

Something in the profile for chromium and chrome is causing the denial since simply disabling or removing the profiles allows access again.

I would like to find some more detailed tutorials. Something like "apparmor for absolute beginners, creating a hello world profile" or even better, "creating you first profile for chrome, firefox, and chromium" :-)

I'm reading through this intro by Bodhi.zasen at the moment
[http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

