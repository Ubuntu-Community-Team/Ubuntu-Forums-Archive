---
title: "Can't seem to get vsftpd working, need help"
date: 2008-08-17
forum: Server Platforms
---

### Post by celery on 2008-08-17
I just installed Ubuntu server edition and am trying to get vsftpd working the way I want it to: using virtual users, started through xinetd. I've run into a number of problems along the way resulting in me bashing my head against error 410 if I remember correctly, which being a newbie I decided to correct by simply reading the tutorial included with vsftpd for setting it up with a website and setting up virtual users.
I've used db4.4_load with the following parameters : "-T -t hash -f /etc/vsftpd/logins.txt /etc/vsftpd/vsftpd_login.db" to create a Berkley database with a test user/password, everything seems to check out, yet when I try "ftp localhost" with either my real user login/password or the test - I get a "530 Login incorrect" error.
My permissions are as follows: (644) rw-|r--|r-- root/root for all the config files, (600) rw-|---|--- root/root for the password files.

Here are the files in question:
vsftpd.conf
> # Access rights
anonymous_enable=NO
local_enable=YES
write_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
guest_enable=YES
guest_username=virtual
chroot_local_user=YES
# Security
anon_world_readable_only=YES
connect_from_port_20=YES
hide_ids=YES
pasv_min_port=50000
pasv_max_port=60000
# Features
xferlog_enable=YES
ls_recurse_enable=NO
ascii_download_enable=NO
async_abor_enable=YES
# Performance
one_process_model=NO
idle_session_timeout=120
data_connection_timeout=300
accept_timeout=60
connect_timeout=60
anon_max_rate=50000


vsftpd (xinetd config file)
> # The vsftpd FTP server.
service ftp
{
disable		= no
socket_type     = stream
protocol        = tcp
wait            = no
user            = root
server          = /usr/sbin/vsftpd
log_on_success  += HOST USERID DURATION
log_on_failure  += HOST USERID
nice            = 10
instances       = 200
per_source      = 5
}


vsftpd (pam file)
> auth required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login
account required /lib/security/pam_userdb.so db=/etc/vsftpd/vsftpd_login

---

### Post by Sef on 2008-08-17
Moved to server platforms.

---

### Post by hux on 2008-08-28
It looks like you're missing some virtual users settings in vsftpd.conf. For example, this is what I use:

[INDENT]# VIRTUAL USER SETTINGS
# Activate virtual users
guest_enable=YES
# Specifies home directory for each virtual user
user_sub_token=$USER
local_root=/home/ftp/$USER
# Virtual users to use local user privs, not anon privs
virtual_use_local_privs=YES[/INDENT]

(Obviously, this assumes that your virtual users are located in the account 'ftp' - you may have it set up differently.)

To create a virtual user, I do this:

[INDENT]sudo mkdir /home/ftp/[username]
sudo chown ftp:ftp /home/ftp/[username][/INDENT]

Then I open my "vsftpd-virtual-users.txt" ("/etc/vsftpd/logins.txt" for you) and add a username and password to the list. Then I run the db4.4_load command as you've been doing. Then I restart vsftpd and all is well.

Also, I don't think you need the line "guest_username=virtual" in your conf file.

Hope this helps. :)

---

