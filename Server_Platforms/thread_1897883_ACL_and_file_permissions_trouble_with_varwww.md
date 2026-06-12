---
title: "ACL and file permissions trouble with /var/www"
date: 2011-12-20
forum: Server Platforms
---

### Post by mooreaa on 2011-12-20
Hello, I'm playing around with a slice on rackspace and am running into ACL permissions errors and was hoping to see if maybe you guys could point me in the right direction.

The summary of the problem is that I have a webdev user who is a member of the www-data group. I have setup ACL on the /var/www directory to allow members of the www-data group to modify files by setting default permissions. Unfortunately it seems like these permissions aren't being honored properly.

1) When I try to overwrite an existing file owned by www-data or another user via WinSCP or other sftp software from user webdev, I get a message saying file upload was successful, but it was unable to update the timestamp/permissions for that file. This error message is something I'd like to correct from the server side but cannot figure out why this is. The user webdev clearly can delete/modify/edit the file, why can't it update the permissions/timestamp via sftp?

2) When the apache/php process creates a file in the /var/www directory, it somehow overrides the permissions to not allow group write even though the ACL is supposed to enforce that. In my case I am running WordPress and it means if I do an update from WP, upload, or install of a file, that file cannot be modified at all by user webdev. I have to use my sudo privileges on the admin account to change the permissions of the newly created/modified files. Not sure why the ACL permissions isn't controlling this properly.

The server is a fresh slice with 11.10 running lamp-server stack with wordpress install. Only modifications that were made were:

1) modified /etc/login.defs and /etc/pam.d/sshd to enforce a umask=002 so user uploaded files are group writable.
2) installed ACL and modified etc/fstab to allow acl
3) added user webdev to www-data group
4) set the sticky bit to inherit www-data as group owner of files and acl permissions of /var/www to allow group read/write. (Tried explicitly stating rules for ACL for group www-data and for user webdev with no luck).

Seems like a pretty basic use-case and I'm having a hard time finding my way around this.




Here is the transcript with web support for your reference, they weren't able to help me unfortunately:

Chat Transcript
Please wait while we find an agent to assist you...
Welcome to The Rackspace Cloud. My name is Dom B, may I have your name and email address in case we get disconnected?
Customer:  Hi I have a technical question about a cloud server that I have regarding file permissions.
Dom B:  okay, do you already have cloud servers with us?
Customer:  yes
Customer:  I'm trying to get it setup correctly but I'm having some issues with the access controls and was hoping you guys could point me in the right direction.
Dom B:  okay I'll transfer you to support now
Customer:  thanks
Dom B has left the session.
Please wait while we find an agent to assist you.
Welcome to the Rackspace Cloud! My name is Araceli C, how may I help you?
Customer:  Hi, I'm having some access control permission issues on my cloud server and was hoping you could point me in the right direction.
Araceli C:  Sure
Customer:  I have a basic Ubuntu slice running with the lamp-server stack installed.
Customer:  I installed wordpress and configured it and everything is working ok.
Customer:  Now I am trying to let a 3rd party developer access this server to do some development work, and I didn't want them to have administrative controls over this setup
Customer:  so I setup a new user, added him to the www-data group and setup ACLs and such so they have read/write permissions to /var/www
Customer:  This part is working for the most part and they can sftp in and edit the file there but I am running into two problems
Araceli C:  What problems?
Customer:  1) when the file is owned by www-data with permissions set to group read/write, they can edit, overwrite the file, etc, but they cannot change the permissions on it via winscp. Winscp throws an error saying file upload was successful but that is not able to update the permissions or timestamp
Customer:  the owner of the file was www-data:www-data
Customer:  the new user was web_developer
Customer:  and even though they could read/write the file, they can't change the permissions / timestamp.
Customer:  The only way around this was to have them delete the file first, then upload... this made me think it was a configuration issue on my end but I cannot figure out why
Customer:  The exact error from WinSCP is "Upload of file 'somefile' was successful, but error occurred while setting the permissions and/or timestamp.
Araceli C:  Do you get the same error if you try to use something Like filezilla?
Araceli C:  Because your set up looks good
Customer:  yes this seems to be a common issue with not being able to modify the timestamp when the uploader is not the owner of the file.
Araceli C:  It's possible there may be something wrong with Winscp
Araceli C:  Another thing to look at
Araceli C:  do you have the acls set to have the proper permissions for user that belongs to the same group as www-data
Araceli C:  there should be default rules for the directories along with rules for users and groups
Customer:  I do, heres the output for getfacl /var/www
Customer:  getfacl: Removing leading '/' from absolute path names
# file: var/www
# owner: www-data
# group: www-data
# flags: -s-
user::rwx
group::rwx
group:www-data:rwx
mask::rwx
other::r-x
default:user::rwx
default:group::rwx
default:group:www-data:rwx
default:mask::rwx
default:other::r-x

Customer:  the group www-data has rwx permissions so the web_developer user is able to overwrite/edit/delete etc files owned by www-data, just can't change the timestamp
Customer:  Let me explain my two other issues which may be related to some degree.
Customer:  2) From wordpress I choose to install an update/plugin/theme etc. That file that gets installed by the php/apache process (user www-data) seems to be ignoring the default permissions and sets the files with no group write permissions. This means that the web_developer can no longer update the uploaded/modified files that reside in /var/www even though the ACL is supposed to enforce those settings.
Customer:  so without sudo privileges, web_developer is unable to recover access to the above files, cannot delete, and cannot modify. I'm not sure what/how/why the ACL permissions are being overwritten for these files that get posted by the apache/php process.
Araceli C:  Just a moment
Customer:  Thank you. I'm really stumped with this and I appreciate your help
Araceli C:  Not a problem =]
Araceli C:  setfacl -R -m u:web_developer:rwx /var/www
setfacl -R -d -m u:web_developer:rwx /var/www
Araceli C:  Hopefully that will help
Customer:  Just tested that and its still having the same issues. New files created by the apache/php process is still ending up without the group write permission bits so the web_developer user isn't able to modify those files.
Customer:  Still seeing the same errors with the pre-existing files being over-written with the timestamp permission error.
Customer:  FYI I'm running this all on a fresh new slice that didn't have any other modifications
Araceli C:  I do not know what else to suggest.
Araceli C:  This is out of scope for this level of support
Customer:  i see
Araceli C:  You can create a ticket
Customer:  ok I will do so
Araceli C:  Sorry I couldn't help any further.
Araceli C:  A higher admin may be able to help.
Customer:  I will give that a shot, thank you.

---

