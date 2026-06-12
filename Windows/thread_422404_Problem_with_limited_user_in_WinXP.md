---
title: "Problem with limited user in WinXP"
date: 2007-04-25
forum: Windows
---

### Post by Zdravko on 2007-04-25
I have WinXP SP2 where I am the administrator. There is another profile, which is a limited user. He can not use the cd-burner in any way. IrfanView, Nero etc. - it doesn't work, because the cd-burner isn't recognized or something? What do I do now? The limited user should have access to write CDs.

---

### Post by sharke on 2007-04-25
You have to share the programs with normal users you should have a share folder somewhere.
Regars
Sharke
Ps Dump xp and use Ubuntu

---

### Post by Zdravko on 2007-04-25
I don't understand what you mean. Can you explain?

P.S. I dual-boot with Ubuntu.

---

### Post by insane_alien on 2007-04-25
when you installed the software there is usually an option to make it available to all users or just the one user. you might have used the latter option. it could also be that you haven't given him the priveleges needed to use it. i'm not sure how the windows permission system works(i gave up cos it was a PITA) so i might be wron.

---

### Post by sharke on 2007-04-25
You are testing my memory jt has been a long time since i booted windows.
open my computer find your hard disc normally c drive and open it open programs folder find folder called Ahead open this folder find nero left click on this folder select properties  somwhere here you should see a button called sharing select it and follow instructions.
Regards
Sharke

---

### Post by the.dark.lord on 2007-04-25
I haven't used Windows for a long time, but this might help:
Uninstall, and reinstall  with access to all users.

---

### Post by Zdravko on 2007-04-25
Okay, I will try to reinstall.

---

### Post by yoasif on 2007-04-25
I would recommend Nero BurnRights: [http://www.nero.com/nero6/eng/Nero_BurnRights.html](http://www.nero.com/nero6/eng/Nero_BurnRights.html)

---

### Post by Zdravko on 2007-04-25
No, reinstall doesn't fix the problem. InfraRecorder never asked me about any users to use the application.
But the biggest problem is that even the standard Windows cd-burn feature seems not to work, because the limited user cannot acknowledge the cd-burner properly.

P.S. Why would I use Nero?

---

### Post by sharke on 2007-04-25
You mentioned nero in your first post.
can  the limited user open a cd in the burner 
Regards
sharke

---

### Post by dreadlord_chris on 2007-04-25
> **Zdravko said:**
> I have WinXP SP2 where I am the administrator. There is another profile, which is a limited user. He can not use the cd-burner in any way. IrfanView, Nero etc. - it doesn't work, because the cd-burner isn't recognized or something? What do I do now? The limited user should have access to write CDs.

To allow Limited User's in XP Home to burn/rip CD's, click "Start", then "Run" and enter "REGEDIT". Go to: 

HKEY_LOCAL_MACHINE\Software\Microsoft\Windows NT\CurrentVersion\Winlogon 

Look in the right pane for AllocateDASD and double click the entry. Set the value to 2. 

For Windows XP Pro users, Load the Secpol.msc console (click "Start", then "Run" and enter "Secpol.msc") and browse to "Security Settings/Local Policies/Security Options", look in the right pane for Devices: Allowed to Format and eject removable media. Set this option to Administrators and Interactive Users.

---

### Post by Zdravko on 2007-04-25
[dreadlord_chris]("http://ubuntuforums.org/member.php?u=251300"), I will test whether this will work! :)

---

### Post by Zdravko on 2007-05-13
Nope, it doesn't work. Why?

---

### Post by Zdravko on 2007-06-22
Anyone? I need help!

---

### Post by smoker on 2007-06-22
> **Zdravko said:**
> I have WinXP SP2 where I am the administrator. There is another profile, which is a limited user. He can not use the cd-burner in any way. IrfanView, Nero etc. - it doesn't work, because the cd-burner isn't recognized or something? What do I do now? The limited user should have access to write CDs.

hi, maybe worth a try - you could temporarily give the limited account admin rights, install the software you require, then change  the account back to a limited one.

there is also some info here that may help:
[http://www.techspot.com/vb/all/windows/t-33239-installing-software-to-multiple-users-on-1-pc-using-xp.html](http://www.techspot.com/vb/all/windows/t-33239-installing-software-to-multiple-users-on-1-pc-using-xp.html)

best of luck

---

