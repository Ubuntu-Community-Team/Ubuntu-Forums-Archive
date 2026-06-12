---
title: "&quot;Maverick Bypassing password when it shouldn't.&quot;"
date: 2010-11-01
forum: Security
---

### Post by MasterNetra on 2010-11-01
My Bug report should explain things well enough...

"I'm duel booting Maverick & Windows 7. And did a re-install of Ubuntu 10.10 And set it to not encrypt my home directory but did have it set to ask for a password at login screen. But after reboot to my surprise it keeps jumping to the desktop without ever going to the login screen. I checked my user options and checked the Don't ask for password option, which isn't checked. So if it was working right it should be going to the login screen and not directly to the desktop. This wasn't a issue with a encrypted home directory and this is the first time I did a Ubuntu 10.10 install without encrypting the home directory.

Also its fully updated and still does it.

*Update*
I selected the "Don't ask for password on login" option then restarted to test to see if it was in reversed. Same result. Skipped login and went to desktop.
I then unselected it then restarted in case unselecting it after it was selected my get it working right, but on load it once again skipped the login screen and went to desktop. So it seems to be completely broken for unencrypted home directories.

I'll try adding another user and see if I can get it to behave correctly.

*Update*
No dice. Even with another user its skipping the login screen and going to my Admin account. This is very very concerning. As it leaves my entire system open to people on the keyboard side."

---

### Post by cariboo on 2010-11-01
Check /etc/gdm to see if there is a custom.conf file, and post the contents.

---

### Post by MasterNetra on 2010-11-02
"
[daemon]
AutomaticLoginEnable=true
AutomaticLogin=syscontrol
TimedLoginEnable=true
TimedLogin=syscontrol
TimedLoginDelay=10
"

Its strange considering I never set it to do this. It was suppose to simply not encrypt my home directory and that was it.

I've manuelly set it to

"
[daemon]
AutomaticLoginEnable=false
AutomaticLogin=
TimedLoginEnable=false
TimedLogin=
TimedLoginDelay=10
"

and she is behaving as she should now. Don't understand how it decided to setup like that... I'm 100% certain I didn't select its option when I set it to not encrypt home at install...hmm will have to test run some installs...

---

### Post by cariboo on 2010-11-02
Usually /etc/gdm/custom.conf is only created when you set auto login, you can safely delete it.

---

