---
title: "Best way to Setup FTP for website Deploys"
date: 2015-09-04
forum: Server Platforms
---

### Post by Nathan_Veysey on 2015-09-04
Hello - Sorry I'm not sure where I can post this? Could someone move this to the appropriate place, or let me know where to get this information from?

I'm trying to workout how to setup vsftp on Ubuntu and workout the best method for deploying sites to /var/www/
I have the FTP client responding and directing me to the Root users Home directory. 

Thanks

---

### Post by SeijiSensei on 2015-09-04
Don't use FTP; it's insecure. Here are some alternatives:

1) If you're transferring files from Windows machines, use [WinSCP]("https://winscp.net/eng/download.php").  You should be running openssh-server on the server already. WinSCP will use this to copy the files securely.

2) On a Linux client, use a fish:// or sftp:// URL in the file manager to set up an encrypted connection to the server.  Again you'll need to be running openssh-server on server. 

3) Set up a permanent encrypted tunnel using OpenVPN.  I run a static-key tunnel between a server in my office and my remote servers at Linode.  You can also use [sshfs]("http://askubuntu.com/questions/412477/mount-remote-directory-using-ssh") to mount a remote share on your client machine.

---

### Post by howefield on 2015-09-04
Thread moved to the "*Server Platforms*" forum for better support.

---

