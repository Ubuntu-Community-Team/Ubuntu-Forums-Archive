---
title: "[SOLVED] do corresponding linux user/samba user passwords need to be the same?"
date: 2008-02-27
forum: Server Platforms
---

### Post by beaker15 on 2008-02-27
I'm just thinking when I get users on my Samba domain, logging in to WinXP clients, and want to change their password, am i right in thinking that I just need to add the line 'unix password sync = yes' in smb.conf and the user just needs to press CTRL+ALT+DEL and change password? I take it this will update the smbpasswd file but not the passwd file

:confused:

---

### Post by Chainz on 2008-02-27
Check this tutorial: [http://ubuntuforums.org/showthread.php?t=202605&highlight=share]("http://ubuntuforums.org/showthread.php?t=202605&highlight=share")

It's a detailed HOWTO on SAMBA configuration.

---

### Post by astrotech226 on 2008-02-27
They actually don't need to be the same.  Samba keeps a separate password like you've already discovered.  The only reason you will want to sync the two passwords is if the Windows user needs shell or ftp access in Linux, or if you are using the Linux password for some other type of authentication.

Example:  I sync up the Windows and Linux password because I use the Linux password to authenticate for our proxy servers and email accounts.  So when they hit clt-alt-delete and change their password, they essentially change their email, internet and windows password at the same time.

So using the 'unix password sync = yes' will also update the Linux password.

---

