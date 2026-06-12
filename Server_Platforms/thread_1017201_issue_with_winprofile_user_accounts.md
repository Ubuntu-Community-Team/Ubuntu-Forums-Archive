---
title: "issue with winprofile user accounts"
date: 2008-12-20
forum: Server Platforms
---

### Post by beetlejuice2006 on 2008-12-20
I am new to being an Ubuntu administrator.  Any help would be appreciated.

Just recently, an IT company installed the Ubuntu LTS 8.04 server.  We were running Fedora Core 3.

All of the accounts are roaming profile, so no matter what computer I logged into, I could get access to all my files, emails, favourites etc.

I created the accounts on Ubuntu. The IT company copied all the winprofile from Fedora to Ubuntu.  The IT company suggested to using the microsoft software on each computer to migrate the user on each computer to retrieve the user profile that was saved on that computer.  Once this was done, had to remove the computer from the old domain, and then connect it to the new domain.

Once this was done, then had to migrate the user profile that was saved from the software to import back into the computer.

I hope this makes sense.  I don't really know how to explain it.

Once the user profile was imported back into the computer on the new domain, was having issues with outlook.  It has lost the email settings for the SMTP to retrieve the emails.  The server gets used to send the emails.

As well, when 2 accounts were logged in, outlook was displaying different error messages after a few minutes, and at one time, outlook lost connection to the server.  For me to open outlook again, I had to close outlook, and kill the process in the task manager in windows.

My question is, do I just create brand new accounts for the users and copy the winprofile across from the account that was created on the server, or do I create a brand new account, and copy the winprofile across from the old server (which I don't know how to do), or do I create brand new accounts, copy the pst file for outlook, and manually set up the settings again for outlook?

As well, which I am not sure if there is a simple answer, but also to the mapping of network drives are lost as well.  Is there any quick way to copy the profiles across without losing any outlook settings and network mapping?

Any help would be appreciated.

Thanks
Lindsay

---

### Post by bluesy321 on 2008-12-20
Just a note on the Outlook files.  I don't believe PST files copy over e-mail setup information.  So you may have to copy the files over and setup the account info again.

I know when I was setting up my most recent desktop PC, I copied my PST file from the old PC to the new PC and had to enter all the info for my e-mail accounts again.  Strangely enough, rules were copied over but didn't function properly until they were deleted and re-created.

Hope this helps and sorry I don't have any answers for the rest of your question.

---

### Post by beetlejuice2006 on 2008-12-20
With outlook, I am not copying the file from one computer to another computer.  Previously, when I logged into any computer, all the email settings were still there.

The only thing that has changed is the upgrade of the server.  Even though everything was copied across for the user accounts that were on the server, somehow, the system hasn't transferred the outlook settings.

I might just recreate the accounts, then copy the files across manually, then copy the pst files across and recreate the settings for each users account.

---

