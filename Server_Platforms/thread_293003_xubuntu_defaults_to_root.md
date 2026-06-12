---
title: "xubuntu defaults to root"
date: 2006-11-04
forum: Server Platforms
---

### Post by baba^ on 2006-11-04
I've just installed xubuntu 1.10 from the desktop CD, and so far it runs great apart from 2 niggles.

The first is that I have to boot using recovery mode each time, or my monitor loses the signal. This is no biggie as my display works peachy once booted. Of course I would like to fix this if possible, but this is not the topic of this thread.

The second issue is that the default user is root, and there is no password. I can't access the user manager (says no permission) and if I switch users from the terminal (before x is loaded), it says I have no permissions to startx.

I've read a couple of threads, the most promising said that I had to chown the home dir of the user in question, but this hasn't worked.

Has anyone else had this problem?

---

### Post by ingo on 2006-11-05
what hardware you running on? i installed xubuntu on an ancient tp600e and it worked a treat...

---

### Post by kerry_s on 2006-11-05
If your booting in recovery of course your root. The normal boot the first user is admin and you would have to use sudo. You need to find out why your losing the signal, boot normaly than post the /var/log/Xorg.0log.

---

### Post by ingo on 2006-11-06
so how would he go about finding out how he is losing the signal? anybody know?

---

### Post by kerry_s on 2006-11-06
That's why i asked him to boot normal and post his log, that's the best place to start. I'm thinking it's probable a settings issue, that's actully crashing X which can be described as losing the signal. In that case i would ask him to delete his config/settings so they can be replaced with orignals/stock. But i would prefer to see the log first.

---

