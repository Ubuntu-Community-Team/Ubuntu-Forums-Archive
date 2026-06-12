---
title: "ExpanDrive"
date: 2020-04-08
forum: Ubuntu, Linux and OS Chat
---

### Post by Perfect Storm on 2020-04-08
Just found this gem of an app. It gather all the big clouds storage under one roof with easy integration to the filebrowser under linux. I use Google Drive and OneDrive and with few clicks all of it is accessible within the file browser. 
Check it out: [https://www.expandrive.com/](https://www.expandrive.com/)

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=285761&stc=1&d=1588755751[/IMG]

---

### Post by Perfect Storm on 2020-05-06
Now I have used it for some time. It's great piece of software and easy to use. _But_ the price tag on it it's a bit to much in my opinion.
Anyone know anther way to incorporate onedrive and google drive into the file-browser?

---

### Post by Perfect Storm on 2020-05-07
I got in contact with the founder of this software and I got a 30% off the price deal. :guitar:

---

### Post by DuckHook on 2020-05-07
Hi AI,

I have both Google drive and Dropbox incorporated into Nautilus. This can be done using the native tools in the repos and does not require a third party app.

For Dropbox: ```
sudo apt install nautilus-dropbox
```This will set up Dropbox as a file folder in your ~ directory in Nautilus. You will have to enter your user credentials and password on first use, but it is transparent thereafter.

For Google Drive:

If you run vanilla Ubuntu, it's simple: Settings &#8594; Online Accounts &#8594; Google, then enter your Google account credentials and reboot. Google Drive should show up as a remote file system bearing your Gmail address in the left&#8209;side pane of Nautilus. The side benefit is that your calendar appointments will also show up on the pull-down calendar applet on the tray and you will get incessant pop-up notifications tied into the system notification tray. These can get annoying, but can be muted.

Cheers!

---

### Post by Hwæt on 2020-05-07
I use this software for FTP into my personal cloud. It's great. It's definitely a hidden gem.

---

