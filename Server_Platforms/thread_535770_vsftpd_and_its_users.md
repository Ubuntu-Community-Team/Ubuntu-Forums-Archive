---
title: "vsftpd and its users"
date: 2007-08-26
forum: Server Platforms
---

### Post by elvinatom on 2007-08-26
Hello comunity!
I'm running vsftpd on a feisty server and want to have it remotely connect to different locations, depending who's logged on.  To be precise, I want:

1. anonymous users to be jailed somewhere with write access,
2. one user (admin or root) to have full access to the file system with root privileges,
3. some users (or a group) to be jailed into a directory with read privileges,
4. all other users (or a group) to be jailed into a directory with read privileges.
(i could have users 3 and 4 go to the same directory and work out the privileges with group permissions)

I googled around, read the man-pages and searched this forum but I couldn't find anything useful.  Any idea or a pointer into the right direction would be great!

---

### Post by Warren Watts on 2007-08-26
My advice would be to read thru the /etc/vsftpd.conf file.  Most of the configuration settings you want to make are described there, often with samples.

---

### Post by elvinatom on 2007-08-26
Thanks for your reply. I actually read it quite a few times up and down but I couldn't find a solution on how to make different rules for multiple users. chown/chroot/anon seem to be mainly focused on security. But if I missed something, do you know a specific instruction I should have a look at?

---

### Post by Warren Watts on 2007-08-27
I set up my vsftp service some time ago, and my only requirements were logins for users of my system.  They automatically get "chrooted" to their home directories.  So I didn't really have to make a lot of configuration changed to get vsftp to do what I needed.

All I can suggest at this point is to do some more searching and see what you can find.

---

### Post by elvinatom on 2007-08-27
I do appreciate you taking time for my issue and I guess I really have to have a closer look at different ftp daemons and their configuration capabilities - but damn, this is the unix world ... there's got to be a solution. ;-)
Thank you though!

---

### Post by Mr. C. on 2007-08-27
You can do all of the things you want.  I'd suggest you implement one at a time, to gain experience on how vsftpd works, and how the vsftpd.conf settings affect operations, and how authentication will work.  You'll can use a combination of services to do what you want: /etc/passwd for local users, pam's userdb for virtual users, and possibly tcpwrapeprs for IP/hostname-based control.  In addition, you want to use xinetd to launch vsftp so that you can pass an environment variable that specifies the configuration file to use.  You'll want **listen NO** in vsftpd.conf.

1. This should be easy for you to configure.  Get this working first.  Learn all the anon_* settings, and the settings to which they also refer. I won't comment on security issues.  We can get to that later.  

2. Root is just an ordinary, local-user.   However, typically root and other privileged users are specifically denied access for security reasons in vsftpd.user_list or similar.  I strongly recommend against allowing root ftp access.  In any case, do this one last, which you work out the rest.

3. and 4.  You can do this with real or virtual users.  Real users will be specified in the password file.  This is easier to setup, but not as safe as virtual users.  Virtual users require using pam's userdb module.   You can also use tcp_wrappers and the VSFTPD_LOAD_CONF environment variable to allow you to use specific configuration files on an IP/hostname basis.  You can have a general config file, and then more restrictive files that are used depending upon the user, IP, or hostname.   You'll want to use the user_config_dir vsftpd.conf parameter to specify user-specific configuration file. 

user_sub_token will allow specification of user home directories for virtual users.

The basic idea is to create configuration files for your given users or group of users, which specifies the settings or overrides for those users.  For IP-based control, you configure xinetd to launch an instance of vsftpd with the VSFTPD_LOAD_CONF environment variable.

Spend a few minutes with this, and review the settings mentioned, and we'll go from there with specific questions.

MrC

---

