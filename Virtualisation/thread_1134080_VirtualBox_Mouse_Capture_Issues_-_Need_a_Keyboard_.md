---
title: "VirtualBox Mouse Capture Issues - Need a Keyboard Shortcut"
date: 2009-04-23
forum: Virtualisation
---

### Post by Ceiling Fan Man on 2009-04-23
I'm trying to run Xubuntu on a virtual machine through VirtualBox, from my Ubuntu (8.10) OS. It's giving me the same mouse capture problem as everybody else seems to have. I think I know what I need to do to install Guest Additions and make it work, with one problem: I don't know how to open Terminal without a mouse. <Alt> + <F2> and typing "Terminal" doesn't work, and neither does "gnome-terminal" or "xfce-terminal."

  If anybody could help me out, I'd really appreciate it.

---

### Post by RealG187 on 2009-04-23
I think you use the "host key" to caputure and it's right CTRL by default. The host key is displayed at the bottom right corner.

---

### Post by Perryg on 2009-04-24
Actually the mouse gets captured when you click on the guest and can be released by hitting the right <ctrl> key (also called the host key). There should have been a message box that popped up when you hit the host key, but you may have cleared it so as not to see it any longer.  To get this prompt back just click help on the guest window at the top left and click on reset all warnings.  I would leave this on until you learn more about VBox. To get mouse integration you will need to install the guest additions in the guest.  This also gives you auto-resize and several other features.

Now for your other problem about getting a TTY window.  All Debian based and some other all use the left <ctrl> + <alt> + <F1> through <F6> to get to a full terminal window.  <ctrl> + <alt> + <F7> will get you back the the desktop. You should however still be able to open a terminal editor from within the program I know that it is gnome terminal in standard Kubuntu. It is found in applications, system, and called Konsole.

---

### Post by axel206 on 2009-04-24
Check this guide. Altough it refers to Ubuntu 9.04 might help you solve your problem the same way.

[How to fix mouse pointer integration in Ubuntu 9.04 installed on VirtualBox](http://www.my-guides.net/en/content/view/157/26/)

---

### Post by Ceiling Fan Man on 2009-04-25
Thanks for the replies, but I still was not getting anywhere... That guide was nice, but was for Ubuntu, while I was battling Xubuntu... A friend of mine did come up with the magic word I needed... After pressing <ALT> + <F2>, I needed to run "xterm"... That brought up the terminal in Xubuntu and I was able to run the commands I needed to to install Guest Editions and thus mouse integration. (The host key wasn't working like it does in theory... I had no mouse ability at all)

 Sidethought:
  It's a little bit difficult to find information pertaining to Xubuntu. I'm trying to learn it a bit before I go and put it on my friend's ancient laptop. I want to go XFCE on it because of the old hardware, I think it will breathe new life into it being such a lightweight OS.

---

