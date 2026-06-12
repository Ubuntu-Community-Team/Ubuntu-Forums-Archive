---
title: "FTP from seedbox to ubuntu server??"
date: 2017-02-19
forum: Server Platforms
---

### Post by biggyk on 2017-02-19
Im currently renting a seedbox and I have setup a media server at home. Just wanted to know what the best way to dial into my seedbox from the server to transfer files from the seedbox to my machine?

---

### Post by TheFu on 2017-02-20
Don't know what "seedbox" means.  Generally, plain FTP should **never** be used. It doesn't work with firewalls well and it puts credentials into plain view.  Use ssh/sftp/rsync/scp instead.  For server settings, many people would use git or etckeeper or some other DVCS or their normal backups.

Main thing is NOT to use plain FTP. The other methods mentioned would all happen through secure channels, unlike plain FTP which should have died off in 1994.

If a 'seedbox' is used for PXE booting, then use the http option instead of Plain FTP.  I suppose if you locked down the FTP server at the firewall to only work for the single machine you need or a lab subnet, then it could be ok to use, but many people forget to do that and eventually put it on the internet where FTP just shouldn't be used anymore (since 1994-ish). There are multiple other better options.

---

### Post by biggyk on 2017-02-20
> **TheFu said:**
> Don't know what "seedbox" means.  Generally, plain FTP should **never** be used. It doesn't work with firewalls well and it puts credentials into plain view.  Use ssh/sftp/rsync/scp instead.  For server settings, many people would use git or etckeeper or some other DVCS or their normal backups.

Main thing is NOT to use plain FTP. The other methods mentioned would all happen through secure channels, unlike plain FTP which should have died off in 1994.

If a 'seedbox' is used for PXE booting, then use the http option instead of Plain FTP.  I suppose if you locked down the FTP server at the firewall to only work for the single machine you need or a lab subnet, then it could be ok to use, but many people forget to do that and eventually put it on the internet where FTP just shouldn't be used anymore (since 1994-ish). There are multiple other better options.

Seedbox is a remote server I rent to allow me to download and seed torrents then ftp the files to and from my local machine.

I just didnt want to have to download to my desktop then transfer it to my server. I wanted to be able to access the seedbox from the server and download directly to my shared media folder.

---

### Post by TheFu on 2017-02-20
Ah ... then use rsync over ssh.  Using ssh is the default with rsync since around 2006-ish.

$ rsync -avz {source} {target}

* source or target can be local OR remote.
* rsync will restart downloads if they are interrupted.
* rsync won't resend anything that is already gotten, unless there is a change to the data at the block level.  The changed blocks get sent, nothing else.

Just setup ssh-keys to make it easy.  Also setup ~/.ssh/config for any alternate ports or different userids or just to make a longish remote servername something short.  All ssh-based tools honor the ~/.ssh/config file.   That's ssh, scp, sftp, rsync, rdiff-backup and probably 20 other backup tools.  More convenient AND more secure - great win.

---

### Post by biggyk on 2017-02-20
> **TheFu said:**
> Ah ... then use rsync over ssh.  Using ssh is the default with rsync since around 2006-ish.

$ rsync -avz {source} {target}

* source or target can be local OR remote.
* rsync will restart downloads if they are interrupted.
* rsync won't resend anything that is already gotten, unless there is a change to the data at the block level.  The changed blocks get sent, nothing else.

Just setup ssh-keys to make it easy.  Also setup ~/.ssh/config for any alternate ports or different userids or just to make a longish remote servername something short.  All ssh-based tools honor the ~/.ssh/config file.   That's ssh, scp, sftp, rsync, rdiff-backup and probably 20 other backup tools.  More convenient AND more secure - great win.

okay i will look into it. Thank you. Any questions il be sure to ask.

---

