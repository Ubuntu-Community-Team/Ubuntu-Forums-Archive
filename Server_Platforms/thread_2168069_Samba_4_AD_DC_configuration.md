---
title: "Samba 4 AD DC configuration"
date: 2013-08-16
forum: Server Platforms
---

### Post by Ant59 on 2013-08-16
I've just setup a Samba 4 AD DC on Debian 7. I want to link the computers at my workplace to it, so that we can hot-desk using roaming profiles.

I have a Synology NAS which I would like to use for user homes and profiles. The NAS has the ability to join the domain, list the domain users and groups and can apply privileges to domain users/groups to each share. I found this page on working with profiles [https://wiki.samba.org/index.php/Samba_%26_Windows_Profiles](https://wiki.samba.org/index.php/Samba_%26_Windows_Profiles) But how do I get it to work using storage on the NAS rather than on the server (which doesn't have much space)?

I have never setup a Windows domain before. First step, I would like to get the user homes and profiles on the NAS device. Secondly, I would like to join an Ubuntu PC or Windows 7 PC to the domain and authenticate as a domain user.

I'd be most grateful if anyone would be willing to lend me a hand please?

---

### Post by lingpanda on 2013-08-16
> **Ant59 said:**
> I've just setup a Samba 4 AD DC on Debian 7. I want to link the computers at my workplace to it, so that we can hot-desk using roaming profiles.

I have a Synology NAS which I would like to use for user homes and profiles. The NAS has the ability to join the domain, list the domain users and groups and can apply privileges to domain users/groups to each share. I found this page on working with profiles [https://wiki.samba.org/index.php/Samba_%26_Windows_Profiles](https://wiki.samba.org/index.php/Samba_%26_Windows_Profiles) But how do I get it to work using storage on the NAS rather than on the server (which doesn't have much space)?

I have never setup a Windows domain before. First step, I would like to get the user homes and profiles on the NAS device. Secondly, I would like to join an Ubuntu PC or Windows 7 PC to the domain and authenticate as a domain user.

I'd be most grateful if anyone would be willing to lend me a hand please?

I'm working on something similar now. What about using folder redirection?

---

### Post by Toxic64 on 2013-08-30
I would advise against romaing profiles due to network congestion and authentication problems.

You will be able to join any windows client computer from XP to win7. 
Ubuntu clients computers will need to install ***likewise-open5*, *likewise-open5-gui*** in order to join them.

You can contact me via Skype if you need help.

---

