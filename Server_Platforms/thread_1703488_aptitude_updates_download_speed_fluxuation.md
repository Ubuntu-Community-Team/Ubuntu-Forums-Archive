---
title: "aptitude updates download speed fluxuation"
date: 2011-03-09
forum: Server Platforms
---

### Post by divided on 2011-03-09
I've noticed this happening on some servers that I manage.  I'll be downloading updates around 300 kb/s - 500 kb/s and then out of nowhere it will drop to about 3 kb/s.  It will stay here forever, if I let it.  I then have to cancel (Ctrl-C) the updates and restart them.  This happens over and over and over until I finally get the full download.  Why does this happen?  Is there something I can do to fix this problem?

Any help is greatly appreciated!

---

### Post by arrrghhh on 2011-03-09
> **divided said:**
> I've noticed this happening on some servers that I manage.  I'll be downloading updates around 300 kb/s - 500 kb/s and then out of nowhere it will drop to about 3 kb/s.  It will stay here forever, if I let it.  I then have to cancel (Ctrl-C) the updates and restart them.  This happens over and over and over until I finally get the full download.  Why does this happen?  Is there something I can do to fix this problem?

Any help is greatly appreciated!

Have you tried a different mirror?

That would at least rule out your internet connection.

If you're on the main US mirrors, those sometimes do get bogged down - but that sounds ridiculously slow, and if it never goes away... hmmm...

I'd try a different mirror, see if that helps!

---

### Post by divided on 2011-03-09
> **arrrghhh said:**
> Have you tried a different mirror?

That would at least rule out your internet connection.

If you're on the main US mirrors, those sometimes do get bogged down - but that sounds ridiculously slow, and if it never goes away... hmmm...

I'd try a different mirror, see if that helps!

I just do an aptitude update and then an aptitude safe-upgrade.  How do you switch mirrors?

---

### Post by arrrghhh on 2011-03-09
> **divided said:**
> I just do an aptitude update and then an aptitude safe-upgrade.  How do you switch mirrors?

[Repositories Using the Command Line](https://help.ubuntu.com/community/Repositories/CommandLine)

and

[How-to find the fastest apt mirror](http://www.go2linux.org/find_the_fastest_debian_mirror-apt-spy_and_netselect-apt)

---

### Post by divided on 2011-03-17
Is there another way to switch mirrors without having to install anything?

---

### Post by arrrghhh on 2011-03-18
> **divided said:**
> Is there another way to switch mirrors without having to install anything?

Manually edit the sources.list file?  On the desktop edition it's a little more straightforward as you have a GUI interface to do it for you...

---

