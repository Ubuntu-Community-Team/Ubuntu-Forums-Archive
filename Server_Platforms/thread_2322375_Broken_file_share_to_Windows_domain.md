---
title: "Broken file share to Windows domain"
date: 2016-04-27
forum: Server Platforms
---

### Post by jose107 on 2016-04-27
Hello,

     I inherited a Ubuntu 14.04 LTS server that has multiple instances of software packages installed and after an update things to seem broken.  I had a file share from the Linux share to the Windows domain that the company is using.  When I attempt to access the share server I get a username and password prompt.  Prior to the update this was not happening.  I have scoured forums and scraped through google but am unable to find anything that will help me resolve this issue.  I have performed extensive troubleshooting on SAMBA and I still have issues.  Someone please help as this is a production server and the file share is broken.

---

### Post by DuckHook on 2016-04-27
Welcome to the Forums, jose107

Your thread has been moved to ***Server Platforms Forum*** for help that is more relevant to your subject.

---

### Post by darkod on 2016-04-28
Do you know if it was not asking for username and password because it could use the user logged into the windows workstation, or because the share had no security set on it (username/password prompt)?

A good start would be to post the content of your /etc/samba/smb.conf. If there are parts of it that are not relevant (like bunch of default commented out options) try cleaning them up before posting, to make it more readable. Also when posting put the text in CODE tags so that formatting is kept.

When applying the updates, do you recall if samba was upgraded/updated to new version?

---

