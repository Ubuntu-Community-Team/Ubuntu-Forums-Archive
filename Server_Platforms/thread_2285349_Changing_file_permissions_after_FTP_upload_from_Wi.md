---
title: "Changing file permissions after FTP upload from Windows app"
date: 2015-07-05
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2015-07-05
Hi all

Have a Windows application that uploads Windows created or modified files to a website running on Ubuntu server 14.04 LTS.

The files, a mix of *.html, *.jpg and *.pdf, have permissions of 600 when they arrive on the website meaning the website ceases to function properly.

One idea would be to to setup an incron job triggered by a change to a specific file which would run a script that would 'chmod' the required files permissions to say 640 or 660.

Perhaps I'm missing something fundamental that would resolve the issue or is the idea outlined worth pursuing?

TIA

---

### Post by TheFu on 2015-07-05
umask?

Any chance you could use sftp or sshfs?

---

### Post by ChrisRChamberlain on 2015-07-05
TheFu

Thanks for your reply.

Not familiar with 'umask' so will investigate.

The Windows app uses WinAPI calls for the FTP functions and they are the final process after data processing, image resizing/cropping, pdf creation, etc, and am not aware of any WinAPI calls available other than conventional FTP.

---

### Post by TheFu on 2015-07-05
> **ChrisRChamberlain said:**
> TheFu

Thanks for your reply.

Not familiar with 'umask' so will investigate.

The Windows app uses WinAPI calls for the FTP functions and they are the final process after data processing, image resizing/cropping, pdf creation, etc, and am not aware of any WinAPI calls available other than conventional FTP.

Perhaps using a Unix-based tool to push the files would make this easier?  Which program? Also - does your webhost support ssh/scp/sftp instead of the terribly non-secure plain FTP? 15 yrs ago, I fired a webhost for that reason.

---

### Post by SeijiSensei on 2015-07-05
What username does the application use when uploading files?  Let's suppose it is "chris".  Look in the file /home/chris/.profile and find the line
```
#umask 022
```
Now read this: [http://askubuntu.com/questions/44542/what-is-umask-and-how-does-it-work](http://askubuntu.com/questions/44542/what-is-umask-and-how-does-it-work)

If you change the umask in .profile, log out and log back in again to ensure it takes effect. 

A default permission mask of 600 is not common and means that the umask must be 077.  Change it back to 022 if you want to permit everyone to read the uploaded files, which is usually the norm on web sites.

You might also look into the configuration of the Windows program to see whether it enforces stricter permissions on the uploaded files or sets the umask itself.

---

### Post by ChrisRChamberlain on 2015-07-05
SeijiSensei 

Thanks for your reply and suggestion.

In the meantime I have gone back to the Windows app and run a small test using the WinAPI call FTPcommand.

This requires 'CWD /foldername',
followed by 'execCmd(hFtpSession, 'site chmod 664 '+lcVar, 0)',
where 'lcVar' = "filename.ext" and 'execCmd()' is a custom written function for the Windows application.

This test works fine and so provides an alternative.

Your suggestion has the merit of simplicity so will investigate and hopefully report the thread as solved shortly.

---

### Post by ChrisRChamberlain on 2015-07-06
> Look in the file /home/chris/.profile...

Unable to find such a file - alternative location(s)?

---

### Post by SeijiSensei on 2015-07-06
The machine I'm using has a vanilla 14.04 installation.  The initial user account, UID 1000, has a .profile in its home directory.  Was there a user created at installation with that UID?  Did you perhaps have a set of /home directories from before that were not created by Ubuntu?  On RedHat-flavored machines, there is an equivalent file called .bash_profile.  You can set the umask in that, I believe, or create a .profile in the home directory of the account being used to upload the files.

---

### Post by ChrisRChamberlain on 2015-07-07
Apologies - have since realised the server in question is running Ubuntu 12.04.4 LTS and not 14.04 as are the others.

---

### Post by ChrisRChamberlain on 2015-07-08
Found the umask settings for Ubuntu server 12.04 after reading this thread - [http://ubuntuforums.org/showthread.php?t=2154180]("http://ubuntuforums.org/showthread.php?t=2154180") and followed advice already given.

Also refined the Windows app > This requires 'execCmd(hFtpSession, 'site chmod 664 '+lcVar, 0)',
where 'lcVar' = "path/folder/filename.ext" and 'execCmd()' is a custom written function for the Windows application.

The extra burden for the Windows app is of no significance and does allow specific permissions to be applied on a file by file basis by substituting a database table field value for the hard coded '664' in the example code.

It also makes the Windows app "portable" in the sense that different servers can be deployed without needing to go server side to accommodate the Windows app through the umask setting.

Many thanks to TheFu and SeijiSensei for your contributions.

---

