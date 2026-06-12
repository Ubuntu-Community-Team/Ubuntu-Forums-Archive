---
title: "Can't initially login to Ubuntu?"
date: 2023-08-26
forum: Virtualisation
---

### Post by saviorone on 2023-08-26
Hello guys,


I'm trying to obtain some knowledge in Linux and I wanted to start with the Ubuntu distro since I've worked with it previously.


The issue I'm facing is that I'm doing the deployment of the 22.0.4 (installed from the official site) to VMware Workstation Pro.


So when I create a new VM and select the Ubuntu ISO, the VMware wizard asks me for the machine name, a user, and a password. After filling in these fields, the Ubuntu machine starts booting up, but the thing is that as soon as the machine boots up it instantly forwards me to the login to the machine menu, asking for a user and a password, instead of the setup wizard ( where we would put things such as location, disk install settings and probably the creation of the actually user name). So basically
The machine goes from initial boot to log in instantly, I've looked for default credentials, and I've tried the credentials that I inserted in the VMware wizard but none of these works, I can't seem to be able to login to the machine and I found it weird that I didn't face the actual ubuntu initial setup.


Thanks in advance for your help. I'll leave two prints on this case that are the only two prompts where I have possible interaction, So I transitioned from the VMware wizard instantly to the Ubuntu login page.


Regards
Salvador Monteiro
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292646&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292647&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=292647&stc=1[/IMG]

---

### Post by TheFu on 2023-08-26
Probably need to as this question from VMware.  It isn't something Ubuntu is doing.  After all, you did buy Workstation, so phone support should be possible.

---

### Post by saviorone on 2023-08-26
I was able to fix the issue, the problem is due to the fact I was using Recommended settings when Building the VM which seem to trigger a lot of issues.

If somebody faces the same problem try doing every step of the VM build manually and don't instantly build the VM with the Ubuntu ISO instead try adding it later

---

### Post by TheFu on 2023-08-26
If solved, please use the "thread tools" button at the top to mark it that way.  This helps the community - both those looking for answers and those seeking to help.  

BTW, the thread title really needs to include "VMware Workstation" ... and this thread should have been placed into the Virtualization sub-forum. Nobody gets this all perfect the first few months, but if someone doesn't tell you, you'll never know. Right?

One last thing, attaching huge images inline isn't really something we do here, but the 2nd set of images were definitely helpful and if they can be pulled from inline and made into attachments, the people on limited internet connections will appreciate it.  I have a limit, for example.

Hope you find these forums welcoming and useful.

---

