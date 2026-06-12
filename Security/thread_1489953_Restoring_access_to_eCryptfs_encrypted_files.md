---
title: "Restoring access to eCryptfs encrypted files"
date: 2010-05-21
forum: Security
---

### Post by wolfv6 on 2010-05-21
I reinstalled Ubuntu, with 10.04 Lynx, and now I am attempting to restore access to my [COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]eCryptfs[/SIZE][/FONT][/COLOR] encrypted files without success.  Please tell me what I am missing.  Here is what I have tried from the command line:
```

  $ sudo apt-get install ecryptfs-utils
 $ ecryptfs-setup-private
 Enter your login passphrase: [entered my Ubuntu login password]
 Enter your mount passphrase: [xxxxxxxxxxxxxxxx]
 Logout, and log back in to begin using your encrypted directory.

```[FONT=Times New Roman, serif][SIZE=3][FONT=Liberation Serif, serif]I logged out and logged back in.[/FONT][/SIZE][/FONT]
```

  $ ecryptfs-mount-private
 Enter your login passphrase:  [entered my Ubuntu login password]
 Inserted auth tok with sig [xxxxxxxxxxxxxxxx] into the user session keyring 

```[FONT=Times New Roman, serif][SIZE=3][FONT=Liberation Serif, serif]I refreshed the file browser, but that changed nothing.  I still do not see decrypted files in the Private directory.  I clicked "Access-Your-Private-Data.desktop" from the file browser, and got this message:[/FONT][/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3][FONT=Liberation Serif, serif]Untrusted application launcher[/FONT][/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3][FONT=Liberation Serif, serif]The application launcher "Access-Your-Private-Data.desktop" has not been marked as trusted. If you do not know the source of this file, launching it may be unsafe.[/FONT][/SIZE][/FONT]
 [FONT=Times New Roman, serif][SIZE=3][FONT=Liberation Serif, serif]So I tried it from the command line:[/FONT][/SIZE][/FONT]
```

  $ sudo Documents/Private/Access-Your-Private-Data.desktop 
 [sudo] password for wolf:  [entered my Ubuntu login password]
 sudo: Documents/Private/Access-Your-Private-Data.desktop: command not found 
 $ ls Documents/Private/Access-Your-Private-Data.desktop 
 Documents/Private/Access-Your-Private-Data.desktop

```[FONT=Times New Roman, serif][SIZE=3]Are there instructions for recreating access to [/SIZE][/FONT][COLOR=#000000][FONT=Times New Roman, serif][SIZE=3]eCryptfs[/SIZE][/FONT][/COLOR]-[FONT=Times New Roman, serif][SIZE=3]encrypted files after a reinstall?
[/SIZE][/FONT]
[FONT=Times New Roman, serif][SIZE=3]Thank you.
[/SIZE][/FONT]

---

### Post by duleep on 2010-07-03
i entered 
> 
root@duleep-desktop:/# ecryptfs-setup-private
mkdir: cannot create directory `/home/duleep/.ecryptfs': File exists
ERROR:  wrapped-passphrase file already exists, use --force to overwrite.
root@duleep-desktop:/# ecryptfs-setup-private
i didn't use --force command is that ok to use or what  i do for open my old home folder plz help any one

---

