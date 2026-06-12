---
title: "Ubuntu Server Installation"
date: 2009-06-24
forum: Server Platforms
---

### Post by gaycheckml on 2009-06-24
My background is Mac and Windows servers. I have made the switch to Ubuntu last year for my personal home desktop.  I am confident in Ubuntu enough to set up a a server for my church using Ubuntu Server. But I just want to clarify a few things, after reading "Beginning Ubuntu Server Administration"

This is going to be a mixed office with 1 Mac, 2 XP, 1 Win 98 and 2 Ubuntu.

Here are a few questions:

1. Which one should I install?  Ubuntu 9.04 Server  or Ubuntu 8.04?

2. I am sort of confused as to which File Systems I should use.  I would like to give all the office clients a file folder.

3. Why would I   Guided (use entire disk) vs Guided (use entire disk and set up LVM)

4. The network already exists with DHCP, and giving the computer name "Fred".  I will be installing LAMP as this will be a functioning Intranet. Since I am using DHCP (static IP is not an option) what do I need to do so that those on the network be able to "http://fred"?

5. Backup? The book only offers two options for backup tar and dd. Don't get me wrong, command lines are great. I am looking for more of a GUI system that I can "set it and forget it" to back up MySql, groupware and files. Any Suggestions?

6. Groupware -- I am looking for an email, calendar and collaboration. . Any suggestions?

7. On my Windows network I had my MS SQL server, IIS server, File/Print server and Exchange server all on different machines. Should I be doing the same thing with Ubuntu?

8. Also, any last minute recommendations or clarifications before I start?


Thank you in advance.
Gaycheck ML

---

### Post by Kareeser on 2009-06-24
I shall endeavour to answer as many questions as I can:

1. The Server Edition is specifically designed for server administration, and there are several tweaks "under the hood" to that effect. In practice, it doesn't necessarily matter which edition you choose. A server edition with a GNOME desktop is **essentially** the same as the Desktop version, and the Desktop edition with gnome-desktop removed is pretty much the same as the server version.

9.04 is considered a stable version, and there should be no problems updating. However, editions back to and including 8.04 LTS are still actively supported in terms of security, so there is no need to be at the edge in terms of OS selection.

2. File systems are different from the file hierarchy. All filesystems support the file hierarchy standard (FHS), and to that end, Ubuntu will install correctly on all of the choices - after all, if it didn't, it wouldn't be on the list of supported file systems!

Prevailing opinion is to steer clear from ext4 on server hardware for now. Others even stick with ext2 for its reliability.

4. Just installing apache from the repositories should get you started well enough. I'm a little fuzzy on the default details - apache might limit access to 127.0.0.1 for security purposes, but you can easily change that in the config files to allow everybody (or a subset, such as 192.168.0.0/24) in.

5. Who says you can't set and forget cli-based tools? I personally use a combination of mysqldump (for databases), tar/gzip, and rsync to back up my server. If you prefer a graphical interface, consider file-roller as a front-end to compression, and grsync as a synchronization tool.

7. As with most situations, the answer lies with your local traffic and power of your server. One server should be able to handle the load, and it's *fairly* trivial to move services off to another computer should the need arise.

8. We'll be here to answer all of your questions. Ask nicely, and ignore the pundits who tell you to google your own answers.

---

### Post by gaycheckml on 2009-06-24
Thank you, I guess I am over analysing.  

M

---

