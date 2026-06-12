---
title: "Wireshark (as root) -- expected behavior?"
date: 2009-09-04
forum: Security
---

### Post by Brian Vaughan on 2009-09-04
It seems as if wireshark is running with root permissions, without an admin password, and this worries me.

I'm using Ubuntu 9.04. In a class on networking, we had an introduction to wireshark, so I installed it from the repositories, and used the menu option, "Wireshark (as root)." As I expected, it asked for my admin password, warned me that executing it as root was potentially dangerous, and everything worked as I expected it to.

Earlier today, I tried launching "Wireshark (as root)" again, and noticed that I was not asked for my admin password. "Starting Administrative Application" appeared on my taskbar, but only for an instant. Wireshark offered the familiar warning message about executing it as root being dangerous, and then went on into the main interface. I thought that, perhaps, that it was accepting that my admin status was cached from some other application I'd launched, so I logged out of the GUI, then back in. "Wireshark (as root)" still did not ask for an admin password.

I tried using find to search for files with setuid or setgid, but I didn't see anything that seemed related to wireshark. At this point, I uninstalled wireshark.

As I understand, no user application should be executable with root privileges unless a member of the admin group has entered a password to authorize it. So, either there's a serious bug with wireshark, which is worrisome, or there's some mechanism in play which I don't understand, which is also worrisome.

Was this expected behavior for wireshark? And is there a security issue related to root permissions of which I'm ignorant?

---

### Post by The Cog on 2009-09-05
Running wireshark as root uses gksu behind the scenes to ask you for your user password. gksu (like the textual version, sudo) has a timer that remembers your password for a while (maybe 15 minutes, I forget the exact figure) so that if you embark on a seried of privileged operations, you only have to give your password for the first one. 

I am guessing that you started wireshark within 15 minutes of entering your password to gksu by starting either wireshark or some other admin program. For instance, I just found that I can launch the partition editor without entering a password provided I do it soon after giving my password for starting wireshark as root. There is nothing to be suspicious of wireshark for in this - it is normal system behaviour.

P.S.
Interestingly, with sudo there is an option to kill the timer (sudo -k) so the next use will always need re-entry of the password. There doesn't seem to be any such option for gksu.

---

### Post by Brian Vaughan on 2009-09-06
I tried reinstalling, and yes, after fifteen minutes, it asked for the admin password again.

I had assumed that logging out would clear the admin authorization. Apparently it doesn't.

---

### Post by cariboo on 2009-09-07
If you want to change the sudo timeout have a look [here]("https://help.ubuntu.com/community/RootSudoTimeout").

---

### Post by Brian Vaughan on 2009-09-07
Thanks, all. I changed the timeout to five minutes, which seems to me a better compromise between security and convenience than fifteen minutes, and Wireshark (as root) asked for a password when launched a second time after five minutes.

---

