---
title: "Automatic deletion as security measure"
date: 2016-08-22
forum: Security
---

### Post by wordwanderer on 2016-08-22
Hi, it has been some years seen I have started to use Ubuntu. At this moment I am using the last Lubuntu distribution on a Lenovo S10e. I use the Prey software to recover my computer in case of theft, and have my documents folder encrypted by Cryptkeeper. 

I do not want to use a BIOS password or encrypt my whole disk because that would render Prey useless. If that poor hypothetic thief cannot use the computer, Prey will not activate. So, that sexy thief photos and location would never arrive to my email. 

For that reason, I would like to program some command like "rm -rf /home/documents"  to run automatically 15 minutes after boot; unless I type a password or execute another command in the terminal.  That way, the thief can access freely my computer (and get caught by Prey); but my documents will be deleted after 15 minutes if a special action is not done.  

Does anyone know how to program a command to run 15 minutes after boot, every time?

---

### Post by HermanAB on 2016-08-22
Make a guest account no password and Prey and encrypt your account?

---

### Post by ian-weisser on 2016-08-22
Are you sure you understand just how hard it is to decrypt a file without the key?
Are you also totally sure you want to delete all your files the first time the phone rings or your beloved nephew tries to play Minecraft in the middle of the night?

If so, a 15-minute-after-boot login delay can be done several ways. Use a systemd target or Upstart job to trigger a simple script or 'at' job.
I hesitate to give more detail to forward a project that, if successful, will promptly delete all your data.
systemd, Upstart, atd, and scripting are all well-known and fully-documented applications.

---

