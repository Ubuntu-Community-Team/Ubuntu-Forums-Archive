---
title: "Restrict user/group to a single directory tree?"
date: 2007-03-08
forum: Server Platforms
---

### Post by Bruderhead on 2007-03-08
I want to make it so that a user (or group) on my system (Dapper) can only see a single directory tree. 

Years back I admin'd a small Solaris system. I  recall that there was a way to restrict a user (and/or group?) so that they could ONLY see a particular folder (or mount point? or device?). Seems it was a restriction on the user, not on the filesystem. Trying to remember how that was done and hoping I could transfer the technique to Ubuntu.

I am running vsftpd and want to allow members of my "ftpvisitors" group to see my "ftpdata" directory (their home directory) only, with no chance of ever straying out of it. Looked at chroot, but that won't allow them to navigate down the tree.

Probably this is not the right way to do this ... any guidance would be appreciated.

---

### Post by Mr. C. on 2007-03-08
I think you are asking one question, but it reads like two.  I'll go with the one question theory. If I'm wrong, please correct.

You can enable chroot for vsftp, so that users are rooted into their home directories, and can only access deeper into their own directories (you had it backwards - the file system tree in *nix is considered to be upside down).  The will not be able to get to say, /home, or other parts of the file system.

Is this what you're looking for ?

MrC

---

### Post by Bruderhead on 2007-03-09
Yes, Mr.C, that is the basic question.

I have tried setting chroot() ... but I cannot navigate deeper into the tree. Thought this was how it is supposed to work (though strange) ... maybe there is another config or permissions I have overlooked or incorrect?

I am also asking  if this is the "correct" way to accomplish my goal or if there is a better method.

---

### Post by Mr. C. on 2007-03-09
chroot() is a system call.  Are you building a new program, or changing the vsftpd source, or did you mean chroot(1) vs. chroot(2) ?

The vsftpd already has chroot ability in it, and it works fine.  You don't need chroot(1).

man vsftpd.conf

and search for chroot

If you are having problems after you set that, please show the output of your commands, not your interpretation.

MrC

---

### Post by Bruderhead on 2007-03-09
Thanks again for the reply and hlep.
My apologies for writing the wrong thing and the confusion ... I do mean the chroot_list_enable option in vdftpd.conf ... which follows:

listen=YES
connect_from_port_20=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
xferlog_enable=YES
chroot_list_enable=YES
chroot_list_file=/etc/vsftpd.chroot_list
userlist_enable=YES
userlist_deny=YES
chmod_enable=NO
local_root=/ftpdata
hide_ids=YES
nopriv_user=nobody
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
banner_file=/etc/vsftpd.banner

---

### Post by Mr. C. on 2007-03-10
So where are we?  Do you see that chroot is not working for you?  If not, what is it that you are seeing.  Show output if you can.

What is in the file: /etc/vsftpd.chroot_list ?

And does it meet the description in the man page for :
       chroot_list_enable
              If  activated,  you  may  provide  a list of local users who are
              placed in a chroot() jail in their home  directory  upon  login.
              The meaning is slightly different if chroot_local_user is set to
              YES. In this case, the list becomes a list of  users  which  are
              NOT  to be placed in a chroot() jail.  By default, the file con-
              taining this list is /etc/vsftpd.chroot_list, but you may  over-
              ride this with the chroot_list_file setting.

MrC

---

### Post by Bruderhead on 2007-03-27
OK, after a long distraction, I have returned to this issue, and have found that using the chroot option DOES do what I need; I had a couple of other problems with configuration and folder permissions that were complicating the problem.

All is working well now with FTP.

Thanks Mr. C for your help,


Brud

---

### Post by shawnerz on 2007-04-07
All,
OK, I'm confused.  I want to restrict users logging in through vsftp to their home directory.  Here is my .conf file:


listen=YES
anonymous_enable=NO
local_enable=YES
#write_enable=YES
#local_umask=022
#anon_upload_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
xferlog_file=/var/log/vsftpd.log
xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
#nopriv_user=ftpsecure
#async_abor_enable=YES
#ascii_upload_enable=YES
#ascii_download_enable=YES
ftpd_banner=Welcome to Shawnerz FTP service.
deny_email_enable=YES
#chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

I uncommented the chown_local_user and list_enable and vsftp allow me to move about the entire hard drive.

Can you tell me what I'm doing wrong?
Thanks,
-Shawn

---

### Post by Mr. C. on 2007-04-07
If you want to restrict local users to their own directories, you need:

chroot_local_user=YES

You should understand the security implications of doing this.
MrC

---

### Post by shawnerz on 2007-04-08
Mr. C.
I made the change to my vsftpd.conf file.  However, when I log in from another PC, I can still cd/ and go anywhere on the hard drive.
FYI: I made the change to the conf file, then went to /etc/init.d and enetered 'sudo ./vsftpd restart'
I don't need to re-boot do I?

What are the security implications?  I assumed that locking users to only their home directory would be more secure.
Thanks in advance,
-Shawn

---

### Post by wayne_za on 2007-04-08
See this link @ myparadigm.sytes.net

[Lock users in there own directory]("http://myparadigm.sytes.net/Joomla/index.php?option=com_content&task=view&id=61&Itemid=31")

---

