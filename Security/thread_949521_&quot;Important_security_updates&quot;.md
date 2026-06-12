---
title: "&quot;Important security updates&quot; ???"
date: 2008-10-16
forum: Security
---

### Post by xp_newbie on 2008-10-16
I have a pretty stable Ubuntu 8.04 installation. As far as I am concerned, my system is PERFECT, working FLAWLESSLY (not before I spent quite some time solving all kind of  problems that characterize fresh installation on new hardware).

But... Ubuntu's Update Manager keeps bombarding me with notifications about updates (as of now 18 "Important security updates" are pending).

If I learned anything about computers, it is that "if it ain't broke don't fix it"... Why would I want to apply updates to a system that is serving me well in critical missions?

The only good answer, of course, is "Important security updates".

But... here is what I see on the list of those 18 "Important security updates":

```
 * New tzdata 2008g:
    - Updates DST rules for Argentinia (LP: #278419).
    - Other DST rule updates.
    - No time zone changes.
 * nvidia-glx-new
    - The list of changes is not available yet. Please try again later
```

And many more changes that don't seem to do with security (linux-image-2.6.24-21.42-generic, jockey-gtk 0.3.3-0ubuntu8.1, etc.).

Why are these listed as "Important security updates"?

Doesn't this defeat the purpose of having an OS that is much more stable than the various Windows flavors?

Thanks,
Alex

---

### Post by cdenley on 2008-10-16
I don't see those updates in the security branch.
[http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz)
Are you sure those weren't listed under a separate header named something like "recommended updates". If you aren't interested in "recommended updates", uncheck that software source.
System>Administration>Software Sources, select the "Updates" tab

---

### Post by Nepherte on 2008-10-16
> **xp_newbie said:**
> If I learned anything about computers, it is that "if it ain't broke don't fix it"... 
Really? My motto is "If it ain't broken, improve it".

Apart from that, I wouldn't just ignore security updates. They're classified as security updates for a reason. The highest chance to break up your system is with kernel updates or with graphic card drivers. But the issues with graphic cards can normally be solved in a way and you can always use the older kernel if the latest one breaks something.

---

### Post by HermanAB on 2008-10-16
If it is a desktop machine behind a firewall, then I agree "Don't fix it if it ain't broke".

If it is a server on the Wild Wild Web, then maybe apply the fixes that you can see affect the services that you need and which are exposed to the public.

In general, I keep any "automatic fsckup" features turned firmly off.

I do update my machines regularly - once a year or three when I install from scratch...

---

### Post by cdenley on 2008-10-16
> **HermanAB said:**
> If it is a desktop machine behind a firewall, then I agree "Don't fix it if it ain't broke".

I disagree. You need to be concerned about applications the user might run which connects to the internet or opens files downloaded from the internet which may have security flaws. On a desktop computer with no servers running, a firewall is irrelevant.

On a server, I only update when there is a security vulnerability it might have. I only have the security branch enabled. If the server isn't online (LAN only), I don't bother with updates unless something isn't functioning correctly (hasn't happened yet, still running edgy).

---

### Post by xp_newbie on 2008-10-19
> **cdenley said:**
> I don't see those updates in the security branch.
[http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-security/main/binary-amd64/Packages.gz)
Are you sure those weren't listed under a separate header named something like "recommended updates". If you aren't interested in "recommended updates", uncheck that software source.
System>Administration>Software Sources, select the "Updates" tab
You are correct. I mistakenly missed the separating title "Recommended updates" because it is pretty faint. I can now see that under "Important security updates" there are only 3 updates:
[LIST=1]
[*]dbus
[*]dbus-x11
[*]libdbus-1-3
[/LIST]

And thanks also for the tip of unchecking a software source. Now that you told me about this, I can see that here:
```
> Right-click the Updates icon (red down arrow)
  > Preferences
    > Updates (tab)
      > Uncheck: Recommended updates (hardy-updates)

```

Alex

---

