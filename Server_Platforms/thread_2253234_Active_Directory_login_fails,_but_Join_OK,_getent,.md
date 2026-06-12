---
title: "Active Directory login fails, but: Join OK, getent, wbinfo &amp; smbclient all work??"
date: 2014-11-18
forum: Server Platforms
---

### Post by Wojtek_Dabrowski on 2014-11-18
Hello everybody,

I have a very strange problem with AD authentification. I have a fresh  install of Ubuntu 14.04 on a machine where I want the users to  authenticate via AD. Details:

[LIST]
[*] Copied /etc/nsswitch.conf, /etc/krb5.conf, /etc/samba/smb.conf  and /etc/pam.d/common-* from another Ubuntu 14.04 machine where it  works, changed hostname in smb.conf 
[*] net ads join -U DOMAINADMIN, net ads testjoin says the join is OK 
[*] wbinfo -u: gives a list of all AD users 
[*] wbinfo -g: gives a list of all AD groups 
[*] getent passwd: lists all AD users 
[*] kinit ADUSER with correct password: works, klist shows the ticket. kinit ADUSER with wrong password fails as expected 
[*] wbinfo -a ADUSER%ADPASSWORD: says "plaintext password  authentication succeeded, challenge/response password authentication  succeeded" 
[*] wbinfo --pam-logon ADUSER: asks for password, then says "plaintext password authentication succeeded" 
[*] From another host: smbclient -L SERVER -U ADUSER: Asks for  password, then lists all shares (including the home directory), if I  give the wrong password, fails as expected with NT_STATUS_LOGON_FAILURE 
[/LIST]

So everything looks awesome. However, when I try to log in as an AD user  (be it directly from the console, using su when logged in as a local  user, using SSH from a remote machine), I get a "Login incorrect" and  the following in /var/log/auth.log:

     Quote:
     [TABLE="width: 100%"]
[TR]
[TD="class: bbcodeblock"]                              Nov 12 14:20:26 SERVER login[3863]: pam_unix(login:auth):  authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty3 ruser=  rhost=  user=ADUSER
Nov 12 14:20:26 SERVER login[3863]: pam_winbind(login:auth): getting password (0x00000388)
Nov 12 14:20:26 SERVER login[3863]: pam_winbind(login:auth): pam_get_item returned a password
Nov 12 14:20:26 SERVER login[3863]: pam_winbind(login:auth): request  wbcLogonUser failed: WBC_ERR_AUTH_ERROR, PAM error: PAM_AUTH_ERR (7),  NTSTATUS: NT_STATUS_LOGON_FAILURE, Error message was: Logon failure
Nov 12 14:20:26 SERVER login[3863]: pam_winbind(login:auth): user  'ADUSER' denied access (incorrect password or invalid membership)
Nov 12 14:20:28 SERVER login[3863]: FAILED LOGIN (1) on '/dev/tty3' FOR 'ADUSER', Authentication failure                      [/TD]
[/TR]
[/TABLE]
 
I am completely stumped and, frankly, have totally run out of  ideas where to even look (especially since it seems not to be possible  to get PAM to be any more verbose). Does anyone have an idea what the  problem may be? I mean, it seems to me that PAM is screwing up somewhere  along the line, but I have really no idea where to look anymore.

As mentioned, it works on another server with the exactly same config  files and the same Ubuntu version. I have also made sure that exactly  the same packages are installed on both servers (basically piped the  list of packages on the server where it works to an "apt-get install" on  the server where it doesn't and rebooted).

If necessary, I can post any relevant config files, just didn't want to spam the whole config needlessly.

I would be really thankful for any pointers - as I said, I am completely at my wit's end here.

---

