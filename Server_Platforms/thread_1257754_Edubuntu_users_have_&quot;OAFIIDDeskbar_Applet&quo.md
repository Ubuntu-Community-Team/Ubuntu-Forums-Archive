---
title: "Edubuntu users have &quot;OAFIID:Deskbar_Applet&quot; trouble"
date: 2009-09-04
forum: Server Platforms
---

### Post by kfleten on 2009-09-04
Some of the Edubuntu users encounters problems when logging in: "The panel encountered a problem while loading "OAFIID:Deskbar_Applet".
Do you want to delete the applet from your configuration?"
No matter what you answer, the problem persist.

I have found a possible (?) solution on [https://answers.launchpad.net/ubuntu/+question/1996](https://answers.launchpad.net/ubuntu/+question/1996) :

1. Open a terminal window by Ctrl-Alt-F2
2. At the prompt type "sudo /etc/init.d/gdm stop" without the quotes
3. On the next line type "sudo aptitude reinstall gnome-applets" without the quotes
4. If you get an error message you will need to also type "sudo dpkg --configure -a"

The question is: How will this commands affect a terminal server system like Edubuntu ? Will all gnome settings for all users be reset, clearing all personal settings ?

---

