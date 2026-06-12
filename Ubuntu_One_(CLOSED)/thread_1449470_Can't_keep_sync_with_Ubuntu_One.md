---
title: "Can't keep sync with Ubuntu One"
date: 2010-04-07
forum: Ubuntu One (CLOSED)
---

### Post by Tig3rzhark on 2010-04-07
Ok, I've been using Ubuntu One's online storage service for the past 2 weeks.  

I've noticed a few things after I synced my laptop and my netbook with ubuntu one...

That when I update the ubuntu one folder from one computer, it doesn't sync on the other computer.

Could someone tell me if there is something wrong on canonical's end or is there something I'm not doing?

---

### Post by dominiquec on 2010-04-07
From my experience, the syncing isn't instantaneous.  You may have to wait a while. :-(

---

### Post by duanedesign on 2010-04-08
I would start by trying to see if its syncing at all or just slow and which computer, or both, might be the issue. I would place a small text file of 3 or 4K in the Ubuntu One folder of each computer and see if that file gets synced to your online storage.

If you determine that one of your computers is not syncing as it should I would file a bug. In versions of Ubuntu with the applet you can select the 'Report a Problem'. Otherwise you can use the command:

```
ubuntu-bug ubuntuone-client
```

Some things to help you include enough information to help with debugging your problem. You should set your log level to debug and then reproduce your issue.

1.) Close the client/preferences window and stop the syncdaemon
   by running the following command from a Terminal:
   ```
u1sdtool -q
```

2) Open Applications->Accessories->Terminal, then run the command:
```
  mv ~/.cache/ubuntuone/log ~/.cache/ubuntuone/log_old && mkdir ~/.cache/ubuntuone/log
```

3) Run the following in the Terminal to open/create this file:
```
 gedit  ~/.config/ubuntuone/syncdaemon.conf
```
   Add the following two (2) lines to this file and save:
```
    
    [__main__]
    log_level = DEBUG
```

4.) restart the client and reproduce your issue.

5.) Attach the logs to your report.  Just zip your $HOME/.cache/ubuntuone/log/ folder and attach the zip using the "Add Attachment or Patch" button at the bottom of the page.

Do this for each computer that has an issue. You might want to file separate reports for each computer that has an issue as they might have different problems.

---

### Post by joshuahoover on 2010-04-08
> **Tig3rzhark said:**
> Ok, I've been using Ubuntu One's online storage service for the past 2 weeks.  

I've noticed a few things after I synced my laptop and my netbook with ubuntu one...

That when I update the ubuntu one folder from one computer, it doesn't sync on the other computer.

Could someone tell me if there is something wrong on canonical's end or is there something I'm not doing?

On the version in Karmic it doesn't normally sync changes from one client to another (either multiple Ubuntu computers or the web UI to an Ubuntu computer) without disconnecting and reconnecting the client. This forces the client to check for new updates.

Thank you,

Joshua

---

### Post by duanedesign on 2010-04-08
Good point Joshua.

As a user of Ubuntu One I sure appreciate the fact that the developers regularly read the forum and answer users questions.

Just wanted to drop some public kudos. :)

---

