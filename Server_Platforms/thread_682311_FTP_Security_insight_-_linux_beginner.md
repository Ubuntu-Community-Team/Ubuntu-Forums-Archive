---
title: "FTP Security insight - linux beginner?"
date: 2008-01-29
forum: Server Platforms
---

### Post by awkward_turtle on 2008-01-29
Hello and thanks in advance for any insight into this topic. I'm a new convert to ubuntu, been using primarily now for a couple of months and love it!

To help myself learn more about linux I often times throw myself into projects which at times are over my head, however, I think I have a pretty good grasp on setting up my FTP server. With that being said I am using vsftpd and have everything up and running my issue is with security. Any tips/recommendations for securing my ftp server as much as possible would be great.

I have all the users I want to access in an ftp group I have created with minimal privileges.

I have all users chrooted to their home dir.

Anonymous access is disallowed.

SSL is enabled and mandatory for use.

(I can post vsftpd.conf if this would help as well)

I realize FTP sends login information in plain text which can easily be intercepted if someone was so inclined. I'm not necessarily worried about someone having access to the files in the designated users directories (if it were to be compromised) however I am worried about them having access beyond said directories and any other malicious exploits that may be possible. With the current set up do I need to worry? 

Please post any recommendations, things I should look for as far as monitoring, or alternatives. I've seen SSH mentioned as alternative quite often, any good how to links/references would be much appreciated.

Thanks again,

Nate (awkward_turtle)

---

### Post by freebeer on 2008-01-29
You might want to look into fail2ban.  It'll monitor your failed logins and block the IP address of anyone failing to log in a specified number of times.  That cuts down on the bots trying to guess passwords and accounts, etc.

---

### Post by awkward_turtle on 2008-01-30
Thanks for the suggestion I'm looking at fail2ban now.

Using my above described setup with no anon logins, designated users under group ftp w/ limited privileges, and users chrooted to home directory if some one was able to gain access with specified users what is the potential for them to wreak havoc or pull off some nasty exploits? I guess I don't fully understand the potential some one I don't want to have access might garner if they were able to gain access. Again, I'm not that worried if they gained access to the files in designated home dir but would like to prevent if at all possible.

Thanks again freebeer - if anyone else has any suggestions/tips or alternatives any insight would be much appreciated.

-Nate (awkward_turtle)

---

### Post by awkward_turtle on 2008-01-30
Should've added this to last post - freebeer or anyone else if you could point me in the direction on some info to configure fail2ban for vsftpd.

I found the below post here on the forums, however, I'm not fully following it.

[http://ubuntuforums.org/showthread.php?t=438260](http://ubuntuforums.org/showthread.php?t=438260)

Thanks,

Nate (awkward_turtle)

---

### Post by HermanAB on 2008-01-30
Well, bear in mind that 'FTP' and 'security' don't belong in the same sentence.  If you are really seriously worried about FTP security, then you should use SSH, not FTP.

If however, you are just playing on the internet, then FTP is fine.

Cheers,

Herman

---

### Post by MJN on 2008-01-30
Nate is using SSL (or says he is! ;)) so the security concerns are no different than using SFTP.
 
Mathew

---

