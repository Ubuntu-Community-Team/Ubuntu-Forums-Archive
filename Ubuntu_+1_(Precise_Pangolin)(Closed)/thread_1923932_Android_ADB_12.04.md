---
title: "Android ADB 12.04"
date: 2012-02-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by sethhikari on 2012-02-11
I am doing android development on 12.04 running a 64bit system updated all the way. Was working just fine until yesterday when ADB does not show any devices detected. I had to reinstall ia32-libs a few days before do to the multiarch changes.

Tried running it as SUDO, have the correct udev rules, used more then 1 phone.

Anyone else with this issue or any ideas?

---

### Post by fjgaude on 2012-02-11
I'm sure the updates, as time goes by, will solve 12.04 issues. There are massive changes going on now getting ready at the end of the month for the release of Beta1.

I wouldn't be doing anything important with an Alpha2 these days, breakage, breakage...

---

### Post by cariboo on 2012-02-11
> **sethhikari said:**
> I am doing android development on 12.04 running a 64bit system updated all the way. Was working just fine until yesterday when ADB does not show any devices detected. I had to reinstall ia32-libs a few days before do to the multiarch changes.

Tried running it as SUDO, have the correct udev rules, used more then 1 phone.

Anyone else with this issue or any ideas?

If your work depends on a stable platform, running a development release isn't a very good idea. If you are using a development release to test developer tools, you should also have a stable release installed so that when the development release breaks, and it will, you have something to fall back on

---

### Post by sethhikari on 2012-02-11
Less concerned with my own Android deving because it is a hobby and I do have a fall back and more with the development of Ubuntu. Checking to see if I was the only one with this issue in order to find out if it is a bug that needs to be handled before release.

---

### Post by cariboo on 2012-02-11
As far as I know, you are the first and only one to ask questions about android development. I'd suggest you report the bug.

---

### Post by dsipma on 2012-02-14
Same problem here running 64 bit ubuntu 12.04

I found a work around though,
switch to the directory adb is located in

Kill the server      "adb kill-server"
restart it as root   "sudo ./adb start-server"

when I do this, my adb works correctly.  For some reason, even though it is defined in my profile, it only works when called from the directory.

Seems to be a related to a bug that prevents 32bit programs from functioning correctly in a 64bit environment, (Another fix was to reinstall libc6-i386, I did that, but don't think it mattered, just saying.  Try it if you can't get this to work.)

---

### Post by primetomas on 2012-04-23
Worked for me just now. Downloaded android sdk and installed platform-tools. In ubuntu I had to "sudo apt-get install ia32-libs". After that it worked directly, running adb as a normal user.

---

