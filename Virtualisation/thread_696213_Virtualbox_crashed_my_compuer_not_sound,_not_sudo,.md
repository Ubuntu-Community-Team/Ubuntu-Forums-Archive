---
title: "Virtualbox crashed my compuer: not sound, not sudo, not administration options"
date: 2008-02-13
forum: Virtualisation
---

### Post by aochoa on 2008-02-13
My Ubuntu 7.10 installation had been running really well and very stable until 3 days ago when installed Virutalbox. I installed it using the Add/Remove option under the "Applications" menu. I followed the installation instructions and after that, it seemed to have changed or restricted access to everything on my system configuration:

1. I can't see the "Add/Remove" option under the application menu anymore.

2. I can't see many of the application on the "administration" menu under "system" including "Users/Groups"

3. I can't use the command "sudo" any more

4. The volume control has got a "red" mark and when I click on it I get the messages:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plug-ins installed, or that you don't have a sound card configured."

"No volume control GStreamer plugins and/or devices found"

5. The firewall "firestarter" doesn't run any more, I get the following message when I try to run it:
"Failed to run /usr/sbin/firestarter as user root.
The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator."

I don't know what to do. I have been looking for information on how to access the machine using root, but because I can not do "sudo" and I can't "access users/Groups" I'm confused about how to continue. I guess the only solution is going to be backing up all my files and reinstall.

Unfortunately, every time I have tried to move away from Windows to Linux, there is something that ruins the process. My idea was to use my best computer at home totally with Linux, and to have a virtual machine with Windows XP to use the applications we use at work that demand the use of Windows. Well, Virtualbox has messes up totally with my computer and my plans (5 months of a very smooth user Linux experience gone to the drainage). I have to admit that I'm not an expert on the operating system yet, I have read a lot and learn a good bunch of commands. I'm trying just to be a good user and to use my computer to organize myself and have my work done, but it seems to me that Linux hasn't achieved this "transparent" experience as the greedy Microsoft has done with Windows.

Because I can't really do much with my Linux computer right now and I need to research if I can't do something to avoid reinstalling it again, I installed Virtualbox in my Windows XP machine, and there were not problems at all. I have installed Ubuntu and PCLinuxOS as virtual machines, and I can run them perfectly at the same time inside Windows.

Well, I hope to find some advice here, but If you think that it is to complex to fix or to explain, do not worry too much. I needed to share a bit of the frustration I'm feeling right now.

---

### Post by aochoa on 2008-02-17
In case you come across this post, someone helped me to find the solution in the following post.

[http://ubuntuforums.org/showthread.php?t=697783]("http://ubuntuforums.org/showthread.php?t=697783")


Please let me know if it was useful and if it helped you. I would like to know how much these questions and answers help others.

---

