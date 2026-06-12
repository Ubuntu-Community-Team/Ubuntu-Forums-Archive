---
title: "Upgrad to 13.10 are no permited?"
date: 2013-09-06
forum: Ubuntu Development Version
---

### Post by miguelpires on 2013-09-06
Hi,
I'm trayng to upgrade to 13.10 and when I run " update-manager -d -c" i received this errors:


miguel@miguel-M14xR1:~$ update-manager -d -c
A verificar por uma nova versão do Ubuntu.
autenticar 'saucy.tar.gz' contra 'saucy.tar.gz.gpg' 
a extrair 'saucy.tar.gz'
Traceback (most recent call last):
  File "/tmp/ubuntu-release-upgrader-yfa2q8/saucy", line 10, in <module>
    sys.exit(main())
  File "/tmp/ubuntu-release-upgrader-yfa2q8/DistUpgrade/DistUpgradeMain.py", line 240, in main
    save_system_state(logdir)
  File "/tmp/ubuntu-release-upgrader-yfa2q8/DistUpgrade/DistUpgradeMain.py", line 133, in save_system_state
    scrub_sources=True)
  File "/tmp/ubuntu-release-upgrader-yfa2q8/DistUpgrade/apt_clone.py", line 149, in save_state
    self._write_state_sources_list(tar, scrub_sources)
  File "/tmp/ubuntu-release-upgrader-yfa2q8/DistUpgrade/apt_clone.py", line 230, in _write_state_sources_list
    "./etc/apt/sources.list")
  File "/tmp/ubuntu-release-upgrader-yfa2q8/DistUpgrade/apt_clone.py", line 252, in _add_file_to_tar_with_password_check
    source_copy.write(line)
UnicodeEncodeError: 'ascii' codec can't encode characters in position 97-98: ordinal not in range(128)
miguel@miguel-M14xR1:~$ ubuntu-bug update
miguel@miguel-M14xR1:~$ ubuntu-bug update-manager

(process:24657): GLib-CRITICAL **: g_slice_set_config: assertion `sys_page_size == 0' failed


Can someone help with this?
Best regards
Miguel

---

### Post by craig10x on 2013-09-06
Why not use the actual iso of 13.10 daily build to upgrade your 13.04 install? I did that a few days ago and it went extremely smoothly...Only lost my Google Chrome and MsCore Fonts (probably because they have license agreements) but were quick and easy to re-install (and Chrome remembered all my settings)...all my data and programs transferred over like i did a fresh install and put it all back in myself...

I think using the update manager for upgrades is not usually a great choice...too quirky...The iso installer offers you the option of upgrading....not only was it very smooth for me it was also extremely fast too since it upgrades directly from the iso and does need to go to the internet for the files...only took about 5 minutes more then a clean install...It even LOOKED like a regular clean install except some different things were going on during the process (especially at the end when it put back my data and installed programs)... :)

Always back up your important data stuff of course (i have all my important photos, mp3s, videos and documents on a flash drive) just in case...

---

### Post by cariboo on 2013-09-06
The upgrade-manager does work as it should, most of the time when an upgrade fails, it is because the person doing the upgrade fails to pay attention to any error messages that pop up during the process. The reason for the op's failure, may be that it is still to early in the process to use the update-manager. 

craig10x's solutions is the best one at this point in time.

---

### Post by craig10x on 2013-09-06
Yes, cariboo907 i had never done an upgrade before and my "instinct" told me that doing it directly from the iso would likely be the best way to go and be the "safest" to try....absolutely no error messages came up and in fact, you could easily mistake it for a clean install....you get the little slideshow and everything...and i was really amazed how fast it went...only took about 25 minutes from start to finish...and all my data and installed programs transferred perfectly (except for the 2 items i already noted)...even most of the system settings changes i made were there...only a couple had to be reset...it certainly saved my a lot of extra work... :D

---

### Post by miguelpires on 2013-09-07
HI,
Thanks for the anwsers. I normally update at beta stage. This is the first time i encounter a problem like this. I fill a bug about this. Most pp use update manager, and I think this something that the Devs. have to look.
I will try the CD way!!
Best regards
Miguel

---

### Post by Elfy on 2013-09-07
> update-manager -d -c

> The reason for the op's failure, may be that it is still to early in the process to use the update-manager. 

Just as a FYI - it worked 2 times for me when I tested it earlier in the week, twice yesterday when testing something else. So it does work with vanilla Xubuntu installs/upgrades

---

### Post by craig10x on 2013-09-07
@miguel: After you do it, i would be curious to hear how it worked out for you...it was the first time i ever did an upgrade and using the iso was a very smooth experience for me so it would be interesting to hear how it went for you...

---

### Post by kansasnoob on 2013-09-08
> **Elfy said:**
> Just as a FYI - it worked 2 times for me when I tested it earlier in the week, twice yesterday when testing something else. So it does work with vanilla Xubuntu installs/upgrades

+1!

I can't speak for Ubuntu but during Lubuntu and Ubuntu GNOME Beta 1 testing I completed the standard upgrade tests and they worked just fine.

I almost wonder if changing DL servers would make a difference?

---

### Post by deadflowr on 2013-09-08
Here's the bug the OP had
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1212025](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1212025)

Which has since been fixed, or at least addressed.
I would suggest the OP clean the cache(apt-get clean) and reload the package list(apt-get update), then try again.

---

### Post by miguelpires on 2013-09-09
Hi
@deadflowr thks for your time, but even after I've done what you sugest i received the same errors.

@craig10x I will try your suggestion. When i finish i let you now.

Best Regards
Miguel

---

### Post by deadflowr on 2013-09-10
If you're still having problems even after the fix was released, maybe try Kansasnoob's suggestion and try a different server.
Of course, I don't know whether or not that error is prevalent for all software upgrades you run or only for upgrading to the development release(newer Ubuntu versions).
Of course though, might as well be moot if you're going to try a clean install/ disk install, which in most cases is for the best.

---

### Post by craig10x on 2013-09-10
@deadflowr: I believe Miguel said he was going to try my method which is using the upgrade option on the live iso session...that way he won't have to worry about the server since he will be getting the files directly from the iso itself ;)

He mentioned he would report back after he does it and let us know how it went...my went pretty darn smooth so i hope he has as good as luck as i did (upgrading from 13.04 to 13.10)...

---

### Post by deadflowr on 2013-09-10
> **craig10x said:**
> @deadflower: I believe Miguel said he was going to try my method which is using the upgrade option on the live iso session...that way he won't have to worry about the server since he will be getting the files directly from the iso itself ;)

He mentioned he would report back after he does it and let us know how it went...my went pretty darn smooth so i hope he has as good as luck as i did (upgrading from 13.04 to 13.10)...

lol
That's why I mentioned the server switching and other problems as being moot.
I probably should have used a better/more clearer term than clean install.
As the method you advocate isn't necessarily a clean install, but a straight up upgrade, using the latest disk image instead of the web.
If it works it works. 
That all that matters in the end.
Otherwise it's a bug report.

---

### Post by craig10x on 2013-09-10
Absolutely...i was just really surprised how well the upgrade can go if you do it from the iso...it was my first time, i never thought it would be as smooth as it was...
And it is also very fast...since it doesn't need to go back to the internet to grab files...it's all right there...It was really weird because unless you look specifically at what was going on, it looked very much like a normal "clean" install with the slide show and everything...:)

---

