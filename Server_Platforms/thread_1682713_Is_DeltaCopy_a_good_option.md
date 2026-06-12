---
title: "Is DeltaCopy a good option?"
date: 2011-02-06
forum: Server Platforms
---

### Post by garfonzo on 2011-02-06
Hey Folks:

I have a Windows box (running Win 7 Pro) in an office and a Linux server in another office and I need to backup the contents of the Window's drive to the Linux box nightly (or weekly or something). I was thinking of doing this with DeltaCopy on the Windows box. 

I just wanted your opinions on whether DeltaCopy is a good option. Have you had good or bad experiences with it? Is it secure enough for your needs (transmitting business data across the internet)? Is it good enough at doing incremental backups?

If you don't like DeltaCopy, what would you suggest is a better option to automate the process of transmitting business data across the net securely on a daily basis? I was thinking perhaps there's a way to initiate the process *from* the Linux server somehow using rsync and a secure tunnel. 

Thoughts?

Thanks

---

### Post by hictio on 2011-02-06
The main problem, in terms of security, I see is that you are doing this over the internet, can you do the same thru a VPN connection?
Other than that, rsync seems like a pretty good solution to pass the data (it is what DeltaCopy uses), have you take a look at [BackupPC](http://backuppc.sourceforge.net/)? Perhaps it is overkill to you, but there might be a couple of ideas you might want to use.

[Step 5: Client Setup](http://backuppc.sourceforge.net/faq/BackupPC.html#step_5__client_setup)

---

### Post by garfonzo on 2011-02-07
I agree that security over the internet is an issue. However, I found this link here which I might try.

[Link]("http://www.ggtai.com/content/how-install-delta-copy-windows-client-and-linux-target")

---

