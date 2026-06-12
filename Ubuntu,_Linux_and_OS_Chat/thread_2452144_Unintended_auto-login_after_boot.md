---
title: "Unintended auto-login after boot"
date: 2020-10-17
forum: Ubuntu, Linux and OS Chat
---

### Post by medovicn on 2020-10-17
Good morning from the East Coast of the US, folks.

I'm running 20.04.1 LTS (x86_64) on Intel(R) Core(TM) i5-7200U CPU @ 2.50GHz, with pre-fab hardware (laptop).

I don't usually report anything, and maybe this was operator error.

I set my laptop down last night on my desk with about 12%.  I commited my project and everything was saved, so no big deal, but the battery died overnight while the PC was asleep.

By asleep, I mean I closed my lid, and walked away (which usually means I come back, press my power button on my laptop, and I get a login prompt).

I had to choose OS at grub, so I selected Ubuntu.  I let it do its thing, and I was greeted with desktop instead of a login screen.

Just feels kinda un-secure for a session to automatically spit you a desktop after sleep.  Hoping someone can show me a config or something I've got messed up.

Cheers, guys

---

### Post by medovicn on 2020-10-17
Worth mentioning that I have since closed my lid, let it go to sleep, opened the lid, hit the power button, and received a login prompt.

---

### Post by metacell on 2020-10-20
My guess is that your computer automatically went to Hibernate when it reached 10% battery, and that your system is set up to lock the screen when going to Sleep, but not when Hibernating.

What does it say in your power settings applet? Is "Lock screen when system is going to sleep" checked? Is the system standby mode set to Sleep or Hibernate?

---

