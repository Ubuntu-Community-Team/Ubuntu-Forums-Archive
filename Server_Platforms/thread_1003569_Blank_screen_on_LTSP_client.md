---
title: "Blank screen on LTSP client"
date: 2008-12-06
forum: Server Platforms
---

### Post by luvinit on 2008-12-06
Hi, I have searched far and wide and found nothing on this topic. For a long time I could boot an LTSP client with no problems, in both Gutsy and Hardy. This changed so that most of the time there is a blank screen with only  a mouse arrow, but occasionally it will boot correctly, as it did over the last few days until yesterday. Here is the error message in the client's .xsession-errors.

SESSION_MANAGER=local/mark-desktop:/tmp/.ICE-unix/8216
** Message: another SSH agent is running at: /tmp/ssh-xCJGdO8187/agent.8187
x-session-manager: Fatal IO error 2 (No such file or directory) on X server localhost:12.0.
gnome-settings-daemon: Fatal IO error 0 (Success on X server localhost:12.0.
Xsession: X session started for test at Thu Nov 27 13:23:11 GMT 2008
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.

Does anybody know what this means and have any suggestions for taking action to repair it?
Thanks.

---

### Post by luvinit on 2008-12-08
Well, I have spent weeks now searching the web to see if anyone can offer any help on this problem, but to no avail. The just isn't enough documentation or support for LTSP. The quick guides are clear and good as long as they work, but if they don't, you have a problem. I am considering doing a reinstall of gutsy gibbon because that is what I used the first time I installed LTSP and had no problem. I have also tried searching for general x server errors and SSH problems but it seems that people who have similar blank screen booting problems but on their desktop computer are also short of suggestions of how to fix it.

---

