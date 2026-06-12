---
title: "sync but no sync"
date: 2010-03-02
forum: Ubuntu One (CLOSED)
---

### Post by tvaiden on 2010-03-02
I just started using ubuntu one today. I place a file in the folder, which began to "sync". I assumed it was being uploaded to the one server so I may share it, or download it at another location. The "sync" took over 3 hours at my full upload speed, but alas, the file is not online in the My Files folder. What Im wondering is what the hell was being done for 3 hours that required all my bandwidth and why the file isnt online now. Maybe I misunderstand the purpose of this service? Where did my data sync to? Now the folder I had shared has been renamed to u1conflict. This is some shady stuff, and I would really enjoy screaming at the coders behind this horrible service, but I dont know how to even email them. Guess itll be dropbox. This is not up to ubuntu standards, bc ubuntu is real nice. i guess I should pay $10 a month to get NOTHING instead of the 2gb of nothing Im getting now.

---

### Post by tvaiden on 2010-03-02
Well, there I have it, I guess the file was too big, as I placed another file in there and it synced up right off, and showed up on the web. But then I deleted it as well as the first file, which never showed up although it did upload. And the client said TWO files were being synced!!! Mind blowing, but I give up, can only use this for small files!

---

### Post by duanedesign on 2010-03-03
tvaiden,
If you are able to upload small files and not large ones it is possibly a pmtu problem.

could you please post the results from running the following in Applications > Accesories > Terminal:

  tracepath -n files.one.ubuntu.com

---

### Post by joshuahoover on 2010-03-03
> **tvaiden said:**
> I just started using ubuntu one today. I place a file in the folder, which began to "sync". I assumed it was being uploaded to the one server so I may share it, or download it at another location. The "sync" took over 3 hours at my full upload speed, but alas, the file is not online in the My Files folder. What Im wondering is what the hell was being done for 3 hours that required all my bandwidth and why the file isnt online now. Maybe I misunderstand the purpose of this service? Where did my data sync to? Now the folder I had shared has been renamed to u1conflict. This is some shady stuff, and I would really enjoy screaming at the coders behind this horrible service, but I dont know how to even email them. Guess itll be dropbox. This is not up to ubuntu standards, bc ubuntu is real nice. i guess I should pay $10 a month to get NOTHING instead of the 2gb of nothing Im getting now.

I'm not sure what the cause of the problems you experienced were but would greatly appreciate it if you could do the following steps so we can get some really good debug information that will help the devs get to the bottom of this problem:

[LIST=1]
[*]Quit the Ubuntu One client
[*]Open (or create if it doesn't exist): ~/.config/ubuntuone/syncdaemon.conf
[*]Add the following 2 lines to this file and save:
[main]
log_level = DEBUG
[*]Open the Ubuntu One client
[*]Try to reproduce the problem you're experiencing
[*]File a new bug by right-clicking on the Ubuntu One client and select "Report a Problem"
[*]Attach ~/.cache/ubuntuone/log/syncdaemon.log to the bug report
[/LIST]
Thank you,

Joshua

---

