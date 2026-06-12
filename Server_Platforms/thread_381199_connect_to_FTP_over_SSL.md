---
title: "connect to FTP over SSL"
date: 2007-03-10
forum: Server Platforms
---

### Post by snovak on 2007-03-10
Hello all,
I was wondering if anyone knows of a way to add an option in the "Connect to Server" menu to mount an FTP site over SSL *.  Frankly,, I don't trust any connection that isn't encrypted with my usernames and passwords.  This is a paid hosting service, who won't allow me to connect via SSH, which would be nice.  :( 

Oh well .... :) 

So,, about that SSL....:confused: 

*- I wouldn't mind using the terminal if there is no way in the "connect to server" menu.

Thanks!

---

### Post by MJN on 2007-03-10
You're limited entirely to what your hosting service supports unfortunately....

---

### Post by Mr. C. on 2007-03-10
> **snovak said:**
> Frankly,, I don't trust any connection that isn't encrypted with my usernames and passwords. 

And you shouldn't.  Find a hosting provider that cares about your security.

MrC

---

### Post by nix4me on 2007-03-10
You can use any number of ftp clients which support ssl/tls encryption.

For the command line, i recommend lftp.  For a gui client, i recommend kftpgrabber.

nix4me

---

### Post by Mr. C. on 2007-03-10
> **nix4me said:**
> You can use any number of ftp clients which support ssl/tls encryption.

As the previous poster indicated, the FTP server (ISP) must support this.

MrC

---

### Post by snovak on 2008-01-10
A few of the servers that I have websites on have the ability to connect over an explicit TLS/SSL connection.  I'm currently using Filezilla, which works fine, but it would be real nice to connect via the "Places > Connect to Server" GUI and use nautilus to manage my remote files.  I love the ability to directly edit files over FTP or SSH with gedit. It's just the explicit TLS/SSL encryption that's holding me back.  Where do I put in a feature request?  :)

Thanks for all the help guys.

---

### Post by PetePete on 2008-01-11
> **nix4me said:**
> You can use any number of ftp clients which support ssl/tls encryption.

For the command line, i recommend lftp.  For a gui client, i recommend kftpgrabber.

nix4me

been looking for a decent ftp gui for ages which supports ssh.. cheers!

---

### Post by MJN on 2008-01-11
> **snovak said:**
> A few of the servers that I have websites on have the ability to connect over an explicit TLS/SSL connection. I'm currently using Filezilla, which works fine, but it would be real nice to connect via the "Places > Connect to Server" GUI and use nautilus to manage my remote files. I love the ability to directly edit files over FTP or SSH with gedit. It's just the explicit TLS/SSL encryption that's holding me back. Where do I put in a feature request? 
 
I'm sure there must be a solution already out there that suits your needs. Remote access is as old as the hills, and doing it securely not much younger.
 
Are you talking about accessing files over SFTP (and I do mean SFTP and not FTP-over-SSL)? If so, you might want to look at remote mounting with sshfs to effectively mount the remote location to a local mount point. Or you could use FISH to access the remote location (the native file manager in KDE, Konqueror, supports this out of the box so perhaps there is already something similar in Gnome).
 
Mathew

---

### Post by envygeeks on 2008-01-11
Some hosting providers require you to supply a cert. before you can use FTP over TLS/SSL, mostly because they are way to cheap to provide a shared cert.

---

