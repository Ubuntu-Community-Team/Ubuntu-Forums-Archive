---
title: "[SOLVED] Is it possible to boot straight to Virtual OS?"
date: 2008-08-13
forum: Virtualisation
---

### Post by worx101 on 2008-08-13
Using Virtual Box, would it be possible to say, first boot ubuntu, but then automatically load and fullscrean a virtual OS?

---

### Post by prshah on 2008-08-13
> **worx101 said:**
> Using Virtual Box, would it be possible to say, first boot ubuntu, but then automatically load and fullscrean a virtual OS?

Yes; create a script in your home directory with these commands```

cat > ~/launchvm
sleep 60
/usr/bin/VBoxManage -nologo startvm wxp
# Dont type this line, just press Ctrl+d to end editing and save this script
# continue below commands at the prompt
chmod u+x ~/launchvm

```

Now add this script to your startup sessions System-Preferences-Sessions-Add,
Name: Launch VM
Command: /home/username/launchvm
Comment: AutoLaunch VM

Replace username in the path above with the correct username for your user, and "wxp" with the correct name for your virtual machine (case matters!)

The "sleep" command, waits 60 seconds for the entire system to load up, before launching the VM. You can fiddle with this as you like.

---

