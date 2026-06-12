---
title: "Ubuntu One slow"
date: 2013-03-05
forum: Ubuntu One (CLOSED)
---

### Post by Redsandro on 2013-03-05
Ubuntu One works fine if you sync a 1kb textfile. But for serious use, syncing takes longer than an 8 hour workday which is unacceptable, while Dropbox does the same in an hour.
Ubuntu One uploaded one megabyte in the last **hour**!

I've read about similar reports from 2 years ago and [Ubuntu One's statement that this is a 10.04 problem]("https://one.ubuntu.com/help/faq/why-is-it-taking-so-long-for-my-files-to-sync/"), but I am running a fully updated Ubuntu 12.10 (Mint 14).

I have previously stopped using [OwnCloud]("https://owncloud.org/") for the exact same reason, but I thought it was because of my server.
Does Ubuntu One use the same code as OwnCloud?

[img]http://ubuntuforums.org/attachment.php?attachmentid=239786&d=1362482284&thumb=0[/img]

To put this more emotionally: Ubuntu One is unimaginable slow and utterly worthless.
I am not using a proxy or firewall that I know of, and Dropbox works lightningfast on the same system.

Any positive experiences or solutions to this speed problem? Certain tricks I don't know about?

I have changed [this bug]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/571371/") from invalid to confirmed. If you experience the same problems, please let them know it [affects you too]("https://bugs.launchpad.net/ubuntu/+source/ubuntuone-client/+bug/571371/+affectsmetoo").

```
$ u1sdtool -s
State: QUEUE_MANAGER
    connection: With User With Network
    description: processing the commands pool
    is_connected: True
    is_error: False
    is_online: True
    queues: WORKING

```

[Someone]("http://askubuntu.com/questions/79093/why-is-ubuntu-one-slow-to-sync-in-11-10-either-backup-or-any-sub-folder-content") said they contacted [Ubuntu One support]("https://one.ubuntu.com/help/contact/"), who in turn advised to do this: ```
u1sdtool -q
rm -rf ~/.local/share/ubuntuone
u1sdtool -c
```..but it doesn't seem to change anything. It only disconnects all my cloud folders, which is very annoying.

---

### Post by JLeon85 on 2013-03-05
Same exact problem here. I tried Ubuntu One for the first time last night thinking I might replace with my Dropbox account with it, and then it just sat there syncing a small number of documents I had tried as a test for it.  Very disappointing, since I practically had my credit card out for a premium account.

---

### Post by DMGrier on 2013-03-05
Thats ruff guys, have you considered backing up to a hard drive, reinstall then try to back up? I know mine runs faster in a sense of about 14.8 GB in about 8 hours.

---

### Post by Redsandro on 2013-03-06
**Update** - next day at the office, computer online overnight. **Ubuntu One** was stuck on the last few megabytes and would not advance. So I rebooted, and it synced the last few megabytes.
I was also syncing stuff at home in the evening, and I noticed some other interesting things:

[LIST]
[*]Whereas Dropbox will sync near-instantly, adding a lot of files on **U1 might take up to an hour before it actually starts uploading** a file, because it does processing very differently from Dropbox.
[*]When uploading finally starts, you get the same notification "FileName001.jpg and 199 other files are uploading" every 5 minutes, **making it look like nothing is happening**. But U1 has the queue backwards and doesn't count beyond 199, so it is actually doing stuff as you can see when you use *ubuntuone-control-panel-qt --show-icon --minified*'s transfer menu item.
[*]**Sometimes**, actually rather often in my experience, **U1** just **gets stuck** on a transfer and needs to restart your machine
[*]Hence, U1 is safe to use on a machine that turns off and on on a daily basis, but I wouldn't recommend it for an always-on machine.
[/LIST]

> **DMGrier said:**
> Thats ruff guys, have you considered backing up to a hard drive, reinstall then try to back up?

Nah, if you think about it, it is effectively the same as:
> **Redsandro said:**
> Ubuntu One works fine if you sync a 1kb textfile. But for serious use, syncing takes longer than an 8 hour workday which is unacceptable, while Dropbox does the same in an hour.
(...)
```
u1sdtool -q
rm -rf ~/.local/share/ubuntuone
u1sdtool -c
```

---

### Post by packrat1 on 2013-04-09
It took me 7 hours to backup 1GB last night. Unfortunately I had just paid for the year for 40GB. I wanted the ease of something made to work with Linux. Riiiiiiggghht. I guess I'll be switching to ... something... in a year. In the meantime, I'll be buying an external HDD.

I think it is pretty poor customer service that this has been an ongoing problem for several years, yet U1 took my money for a service that is essentially unusable as advertised. What a shame.

---

