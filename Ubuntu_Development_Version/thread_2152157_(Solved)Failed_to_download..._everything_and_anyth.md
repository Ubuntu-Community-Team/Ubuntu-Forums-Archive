---
title: "(Solved)Failed to download... everything and anything"
date: 2013-06-06
forum: Ubuntu Development Version
---

### Post by loukingjr on 2013-06-06
I have Xubuntu 13.10 installed in VirtualBox from a daily build I created on 5/31. I could of sworn I could update and the repos were up but now I just get "failed to download...." errors for anything. did the repos change and I missed it? or am I imaginging the repos are up?

---

### Post by cariboo on 2013-06-07
Try a different mirror. Go to System Settings-> Software & Updates, and change the server in Download from:

---

### Post by loukingjr on 2013-06-07
well, I tried both the main server and the US server. what's odd is I tried both with Software Updater and Synaptic and both fail. however, apt-get seems to work. the other thing is are any of the repos suppose to say "/Release/"? It's not even alpha yet.

edit: I'm wondering now if something I did screwed things up. I added the Mate Raring PPA along with it's key so I could install the caja file manager. Once installed I disabled the Mate PPAs. Perhaps that caused a problem?

---

### Post by loukingjr on 2013-06-07
I ran select fastest server this a.m. and everything seems fine now.

---

