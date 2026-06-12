---
title: "SFTP - Jail users"
date: 2009-01-05
forum: Security
---

### Post by Ic3m@n on 2009-01-05
I know there has been a post already on using scponly to jail users to their home directories but I have a possible easy solution but need some expert confirmation on the ramifications that this may incur.

So I have several users in /home.  to disallow them to view other users home folder contents I have done chmod 750 /home/otherusers.  Now, the users can still browse and execute up the folder structure to / or where ever they want to go.  So, to disallow this I did a 
chmod 751 /home/.
and a chmod 751 /home/..

In my testing this disallowed an sftp user to browse any other directory besides their own home directory.  Am I missing anything?

---

### Post by cdenley on 2009-01-05
> **Ic3m@n said:**
> I know there has been a post already on using scponly to jail users to their home directories but I have a possible easy solution but need some expert confirmation on the ramifications that this may incur.

So I have several users in /home.  to disallow them to view other users home folder contents I have done chmod 750 /home/otherusers.  Now, the users can still browse and execute up the folder structure to / or where ever they want to go.  So, to disallow this I did a 
chmod 751 /home/.
and a chmod 751 /home/..

In my testing this disallowed an sftp user to browse any other directory besides their own home directory.  Am I missing anything?

Yes. "chmod 751 /home/.." is the same as "chmod 751 /". This would prevent everyone except root from listing the contents of "/". However, this would not prevent anyone from listing the contents of "/usr" or "/etc", or reading the files in any directory.

---

### Post by hyper_ch on 2009-01-05
I'd use MySecureShell for jailing sftp people.

---

### Post by Ic3m@n on 2009-01-06
Excellent solution.  Much quicker and easier than other jail solutions.  Thank you for the suggestion.

---

### Post by dperfors on 2009-01-07
With at least ubuntu 8.10 and OpenSSH it is possible to set ChrootDirectory in the sshd_config file.
ChrootDirectory="%h" will chroot/jail to the home directory of the authenticated user (I am not sure about the syntax, read the man page for that...)

---

### Post by kevdog on 2009-01-07
Wonderful post regarding the chroot capabilities to openssh.  I knew a patch had been floating around for a long time, but not know it had been officially released. Of course the daemon needs to be verion 4.9p1 or later for this to work.  Suprisingly there is not a lot of info out on the net about this function.  The most examples I could tell was using this as a strict ftp server (limiting to uploads and downloads).  Ive read documentation that this can also be used to provide a limited interactive shell, however couldn't find any examples.  Also just an FYI, scp does not work with this openssh variant, only sftp (which is what I use anyway, but others may not).  Hopefully I can play around with it for a while.  Great post.

---

### Post by dperfors on 2009-01-08
In order to get scp or shell access working, you should probably put some executables and libraries into the home directory. I didn't had the need to try to look into this, so I can't give you an example...

look at [this]("http://undeadly.org/cgi?action=article&sid=20080220110039") article for more information...

---

### Post by kevdog on 2009-01-08
Of course after looking into it further, it might just as well be as easy to use rssh for this matter.  It seems to be a fairly well developed ssh fork.  Its also in the debian and ubuntu repositories (sudo aptitude install rssh) so I'm assuming (dangerous assumption) it must be well tested!  Might ask bodhi on this one!

---

