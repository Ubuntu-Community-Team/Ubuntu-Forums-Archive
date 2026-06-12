---
title: "Restricted user right"
date: 2010-01-28
forum: Security
---

### Post by maxixastonehead on 2010-01-28
Hi everyone, i am running internet cafe where people pay for time they use the computer. There is one ubuntu serve and 5 clients ubuntu. I m using gbilling for billing management. The problem is that in the client side user can just kill the gbilling app to by pass the billing system in that client computer. I tried to block the terminal by uninstalling gnome terminal, make xterm cannot be execute, close the virtual console (f1 - f6 not funtion). but there is something in gnome panel called force quit that act like kill i can disable it or remove it. My question is  is thar any way to disable the  force quit in gnome panel? The points are first i give right to users to use internet connectin fairly (no cheating). I don't want they mess the computer so i want restric the use of terminal and any app that can mess the system. Please  give me any solution. It does give haedache. Using ubuntu 9.10. Thank you very much.

---

### Post by mikewhatever on 2010-01-28
I believe you are talking about the force_quit applet. If so, open gconf-editor, and navigate to /apps/panel/global. The lines that seem to be of interest to you are:
disable_force_quite
locked_down

---

### Post by Lars Noodén on 2010-01-28
Just some random ideas:

I would recommend finding a way to put the billing app on the server and have the machine check in and out.

Another option would be to run the gbilling application as a different user and then have that user poll the guest account every minute or so to see if it's still logged in.

---

### Post by Lars Noodén on 2010-01-28
> **maxixastonehead said:**
> ...I tried to block the terminal...

Also you might set the guest user account's shell to rbash or something more limiting, and then have the login script and bashrc clear the $PATH environment variable.  

When you've set up the guest user account's directory the way you want it, use tar or something to copy it to another directory where that account can't access it, except as read-only.  Then use rsync with the --delete option during login to restore the settings.

---

### Post by maxixastonehead on 2010-01-29
Well. That is great idea! It prove me a fool. I more reading in order to be a master of my sleve (computer). I does dare me to know more. Fact is  that i never want to know more about win. Thank you very much....

---

### Post by bodhi.zazen on 2010-01-29
Lots of suggestions, google search Ubuntu kiosk =)

[http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm](http://users.telenet.be/mydotcom/howto/linuxkiosk/ubuntu01.htm)

---

