---
title: "running progams while logged out of ubuntu with a encrypted home"
date: 2010-08-28
forum: Security
---

### Post by gelen9 on 2010-08-28
I would just like to know how to, and know if its secure to run the following programs WHILE LOGGED OUT of Ubuntu:   openvpn, deluge,  and if it can be securely done while the home directory is encrypted.

---

### Post by BkkBonanza on 2010-08-28
How are you going to run any program when you're logged out? You need to be logged in before you can run anything.

If you're talking about configuring these programs to run as root when the machine boots before any user login then NO. Running these programs, and in general most programs, as root is a bad idea. Programs intended to run as root such as ssh and other services are very carefully checked to try and ensure they minimize vulnerabilities. But running a torrent client as root or openvpn is asking for trouble. If that was the question anyway.

---

### Post by OpSecShellshock on 2010-08-28
Those processes all have to be run by logged-in users. That's why when you log out it shuts down any running processes. I don't think there's any way to even have a network connection without being logged in.

Also, the home directory won't be decrypted until the user logs on. Encryption is only in effect when there's not an active session running. While you're logged in the data's not encrypted (because if it were, then nothing would work).

---

### Post by Agent ME on 2010-08-29
You can run programs when you're not logged in by using nohup or crontabs for example. Simplest solution would be to keep the files those programs need unencrypted. Using the same technique people use to keep ".ssh" folders unencrypted should work, but I can't remember that at the moment. Alternatively, you could remove the ~/.ecryptfs/auto-umount file (may be located somewhere else on a fully encrypted home directory) so that way your home folder isn't unmounted when you log out.

Network connections will work when you're logged out if they're set to connect automatically and be available to all users.

---

### Post by FuturePilot on 2010-08-29
Yes, the easiest way is probably to just remove ~/.ecryptfs/auto-umount. Also if the applications you want to run are command line apps, Byobu (screen) is your friend.

---

### Post by BkkBonanza on 2010-08-30
Or starting them as background tasks, eg. **deluge&** works when you logout from terminal (though it makes more sense to run it as console mode, no-gui, **deluge -u console &**). However, you would still have to ensure the encrypted home is ok, or maybe easier, create an alternate user with non-encrypted home that you use to run these tasks. That also helps that if they get compromised they don't have access to your home, and you can remove sudo rights so they cannot go root even if someone got the password.

---

### Post by cariboo on 2010-08-30
I prefer screen for running programs in a terminal, the programs will continue running even if the terminal is closed. Screen is included in a default Ubuntu install.

---

