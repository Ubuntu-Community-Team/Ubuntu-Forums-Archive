---
title: "not seriuos/ help reading OSSEC logs"
date: 2010-07-05
forum: Security
---

### Post by BigCityCat on 2010-07-05
I have been reading the OSSEC logs and there are a few things popping up. I was hoping someone could explain them to me. This is a fresh install.

---

### Post by bodhi.zazen on 2010-07-05
> **BigCityCat said:**
> I have been reading the OSSEC logs and there are a few things popping up. I was hoping someone could explain them to me. This is a fresh install.

I see you edited you post.

Keep reading. Tools such as OSSEC are useless unless you do your footwork.

Only you can tell us if the files you previously listed are legitimate changes or not (have you done sys admin ? ).

---

### Post by BigCityCat on 2010-07-06
> **bodhi.zazen said:**
> I see you edited you post.

Keep reading. Tools such as OSSEC are useless unless you do your footwork.

Only you can tell us if the files you previously listed are legitimate changes or not (have you done sys admin ? ).


Not sure what you mean by sys admin?

These are the webui logs I was reading. Not sure what to make of them.



  >   

Latest events

2010 Jul 06 11:11:34 Rule Id: 550 level: 7
Location: paul-laptop->syscheck
Integrity checksum changed.
Integrity checksum changed for: '/etc/apt/sources.list.d/medibuntu.list'
Size changed from '268' to '269'
Old md5sum was: 'bfeacf4f4123b59b791d4c64b3d66e1f'
New md5sum is : '385f5e167b6c2b359f1be0a0cc5ea85f'
Old sha1sum was: 'f360ef6054475d867336a769f37f343f7f059f59'
New sha1sum is : '030fd14c4455f080ff84d22984f945ddc45cb5fe'

2010 Jul 06 11:11:34 Rule Id: 550 level: 7
Location: paul-laptop->syscheck
Integrity checksum changed.
Integrity checksum changed for: '/etc/apt/trusted.gpg'
Size changed from '8274' to '8645'
Old md5sum was: '5f95d840997d1d01f89fe80c1fbef2c9'
New md5sum is : 'f46db815e9ce7094be70e913a8eb5fb4'
Old sha1sum was: '563210f8447f78693158d0fda4ff225aa90054f5'
New sha1sum is : '9e2be2b00afe0a319cd26a4309818bde23b081a7'

2010 Jul 06 11:00:47 Rule Id: 1002 level: 2
Location: paul-laptop->/var/log/syslog
Unknown problem somewhere in the system.
Jul 6 11:00:46 paul-laptop wpa_supplicant[967]: Association request to the driver failed

2010 Jul 06 11:00:41 Rule Id: 1002 level: 2
Location: paul-laptop->/var/log/syslog
Unknown problem somewhere in the system.
Jul 6 11:00:41 paul-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed

2010 Jul 06 11:00:41 Rule Id: 1002 level: 2
Location: paul-laptop->/var/log/syslog
Unknown problem somewhere in the system.
Jul 6 11:00:41 paul-laptop NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)'

---

### Post by bodhi.zazen on 2010-07-06
sys admin = system administration.

Did you edit those files ? 

OSSEC is a HIDS that monitors system files for changes and is notifying you of changes.

Either you personally edited those files, updated your system, etc, or you did not. If you did, ossec is working and detected those changes.

If not, somebody else did.

---

### Post by BigCityCat on 2010-07-06
> **bodhi.zazen said:**
> sys admin = system administration.

Did you edit those files ? 

OSSEC is a HIDS that monitors system files for changes and is notifying you of changes.

Either you personally edited those files, updated your system, etc, or you did not. If you did, ossec is working and detected those changes.

If not, somebody else did.

All the changes I have been alerted to were changes I made, but there are a few system errors I was wondering about.

What did I have to do with sys admin?

---

### Post by cariboo on 2010-07-06
I think this is just a matter of semantics, any time you make changes to your computer you are doing system administration.

The last three errors show us that you are having a wireless  networking problem, specifically wpa_supplicant and network-manager.

Are you having a problem connecting to a wpa encrypted router?

---

### Post by BigCityCat on 2010-07-06
That is why I was wondering. Because I'm not having any issues connecting. I am using wpa2 encryption but everything is fine from what I can see.

---

### Post by BigCityCat on 2010-07-06
I was only asking cause I wasn't sure what the log was trying to tell me but as long as I am secure then I am okay with it.

---

