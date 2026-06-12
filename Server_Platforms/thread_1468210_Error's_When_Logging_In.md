---
title: "Error's When Logging In"
date: 2010-05-01
forum: Server Platforms
---

### Post by KoffeeKup on 2010-05-01
Hey guys,

I have a server with Ubuntu 10.04 LTS installed. (As of yesterday, 9.10 was there) I recently started to get these errors when I log in: (Yes, I use the ubuntu desktop oackage)

"Could not update ICEauthority file /home/demetrius/.ICEauthority"

"There is a problem with the configuration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"

"Nautilus could not create the following required folders: /home/demetrius/Desktop, /home/demetrius/.nautilus

Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them."

Now when I acknowledge all three errors, the system will just hang at the log in screen. (After you log in). I can boot to the desktop if I use failsafe GNOME.

Any ideas on this one? I want to avoid a reinstall.

Thanks for the help,
-KK

---

### Post by ubuntu1sttimer on 2010-05-01
Not sure that this will be of any help but here goes.

About a week ago with 9.10 desktop I started getting the same "Could not update ICEauthority file /home/demetrius/.ICEauthority" message. Of course, "demetrius" was different in my configuration. Tried a couple things that didn't fix it. Have been just clicking past it. Did determine that on my machine the file .ICEauthority does not exist. Think it may have been something from a update a week or so ago. In your case, if updates were not too recent on your machine it may have come in via a current copy of a file used by both releases that was installed for you with 10.04. 

Last time I updated when 9.10 came out and spent a month getting things working. Many things repaired via new patches that became available as fixes to 9.10. Made up my mind to wait at least a couple weeks before jumping into 10.04 this time.

---

### Post by krodrigue on 2010-05-01
I had the same problem, I had to reset the permissions, as root became the sole owner of the files in the users home directory.

---

