---
title: "Joomla security issues"
date: 2015-05-25
forum: Security
---

### Post by Sapph1r3 on 2015-05-25
Firstly I must apologize if this is not the correct place to be asking this question.
I have a customer that is having problems with her Joomla permissions.
I am running an Ubuntu 12.0.4 LTS (I think) server.
She is getting unwritable errors on folders.
I have checked Joomla forums and the folders permissions are set to 755 as advised.
I do not want to open it up for the whole world to hack, so 757 and 777 are out of the question.
I know 777 if definitely a no, but how insecure is 757 if my permission options show read, write and list?
Thanks

---

### Post by tgalati4 on 2015-05-25
If the disk drive is having problems, then it will go into read-only mode, so nothing can write to it.  I would check the SMART status of the disk drive on the server.

Open a terminal:

```
sudo apt-get install smartmontools
sudo smartctl -a /dev/sda
```

To find out what you are running:

```
cat /etc/issue
```

I think.

---

### Post by Sapph1r3 on 2015-05-26
Thanks for the response.
I will have a look but I don't think the drive is going into read only mode.
Any file that gets transferred via FTP gets written without problems.

---

### Post by tgalati4 on 2015-05-26
If you look in /var/log/auth.log you should see permission errors.  Are the write failures happening when adding new content or when changing themes and other joomla administrative tasks?

---

### Post by Sapph1r3 on 2015-05-27
I have had a look at 2 instances of that log, and I don't see anything to do with permissions.
I have seen successful log attempts for the user in question and a few authentication failures for something with backup, but nothing that looks useful to me.
I am sorry for the back and forth, but I really don't know how to overcome this :(

---

### Post by Habitual on 2015-05-27
Joomla! version?
See also [http://joomla.stackexchange.com/questions/7026/all-directories-listed-as-unwritable](http://joomla.stackexchange.com/questions/7026/all-directories-listed-as-unwritable)

---

### Post by Sapph1r3 on 2015-05-27
The Joomla version is 2.5.
I have previously set folder permissions to 755, user is still having issues.

---

### Post by Habitual on 2015-05-27
> **Sapph1r3 said:**
> The Joomla version is 2.5.
I have previously set folder permissions to 755, user is still having issues.
and you may continue to have issues, as [Joomla 2.5 is the previous version of Joomla, which was supported until December 31, 2014]("http://www.joomla.org/download.html")
and you should consider that, and all the other possible security risks you are running on an unsupported version of Joomla!

Stop messing with 755 and upgrade joomla! is my best answer, then see what's what with 
> **Sapph1r3 said:**
> She is getting unwritable errors on folders.

---

### Post by bab1 on 2015-05-28
> **Sapph1r3 said:**
> Firstly I must apologize if this is not the correct place to be asking this question.
I have a customer that is having problems with her Joomla permissions.
I am running an Ubuntu 12.0.4 LTS (I think) server.
She is getting unwritable errors on folders.
I have checked Joomla forums and the folders permissions are set to 755 as advised.
I do not want to open it up for the whole world to hack, so 75[COLOR="#FF0000"]7[/COLOR] and 77[COLOR="#FF0000"]7[/COLOR] are out of the question.
I know 777 if definitely a no, but how insecure is 757 if my permission options show read, write and list?
Thanks

To answer your question directly; the folder permissions of 757 is no more insecure for access 777 as the world has read/write access to any subdirectories.   The trailing 7 (shown in red).  In practical terms the folder permissions should be 755 or 775 depending on what you are attempting to do.

On Ubuntu the user always creates folders with 775 permissions and files with 664 permission.  This allows that user read/write permissions on files and read/write and traverse rights for folders.  Traverse means you can descend into that folder to create new files or folders.

The question is really how are you using the section of the file system with Joomla.  Is this a single user or are multiple users attempting to use the same diectory?  What does the file structure look like now.  Show some examples of what is in the various folders.

Your best bet is to use the command line to do this.  Post the output back here of the directory and file listings.

What specifically is the error for this...> She is getting unwritable errors on folders.

---

### Post by mastablasta on 2015-05-28
also if upper directory has less permissions and lower one 777 then they still won't be able to get 777 access as they can 't access the higher up directory.

---

### Post by Sapph1r3 on 2015-06-08
Thanks for all the assistance.
The user eventually got back to me.
On attempting to upgrade, the error reads:

[ATTACH=CONFIG]262485[/ATTACH]

---

### Post by tgalati4 on 2015-06-08
What are the details of the file?

```
ls -la LICENSE.txt
```

Either this is the first of many files that you will have problems with, or the permissions of the directory above it may have a permissions/owner issue.

---

### Post by bab1 on 2015-06-08
> **tgalati4 said:**
> What are the details of the file?

```
ls -la LICENSE.txt
```

Either this is the first of many files that you will have problems with, or the permissions of the directory above it may have a permissions/owner issue.

+1 to that.

This is really a Joomla! problem and not a Linux file permissions problem per si.  Joomla! requires directory and file permissions that are not acceptable to most Ubuntu installs.  It might even be counter to the way Apache should be secured.  My understanding is that Joomla itself must be configured correctly to overcome the discrepancy.

I'm suprised when I read the Joomla! documentation.  It is not how I would secure an Apache server.  If you are in control of the entire Ubuntu server (not a VPS) you might be interested in the Joomla! permissions documentation  available [**here**]("https://docs.joomla.org/Security_Checklist/Hosting_and_Server_Setup") and [**here**]("https://docs.joomla.org/Why_can%27t_you_install_any_extensions%3F#File_ownership_advice_from_ianmac").

Here is a pretty good [**blog post**]("http://onwebdevelopment.blogspot.com/2008/04/secure-joomla-file-permissions-linux.html") about the problems.  Even then it is not what I would do to secure my Apache server.  I don't allow the Apache user (www-data) write permissions to the DocumentRoot at all.  But that's just me.  If the Apache user can only read (and serve) the data it can't be compromised.

[COLOR="#0000FF"]Edit:  My guess as I'm not a Joomla! or Drupal user is that the problem arises when a person tries to update the system via a web interface using PHP.  I think that is a very insecure idea.  The person should use backend tools (i.e. SFTP or vsftp) only.  In that case I would set the directory permissions at 755 or 775 depending upon whether the users were user:user or user:somegroup.  In this scenario the Apache user would always have read access via the other read only permissions. The Apache user does NOT need to be either the user or in the user-group to function correctly. [/COLOR]

---

