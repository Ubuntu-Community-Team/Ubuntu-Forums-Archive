---
title: "Ubuntu and cloud?"
date: 2011-02-27
forum: Security
---

### Post by opendoors on 2011-02-27
Recently, I read about some kind of connection between Ubuntu and cloud computing. What is this connection?

If I use Ubuntu, am I forced to participate in the cloud? If so, in what way? My main concern is that my personal files or data might be uploaded somewhere without my knowledge. For example, if I have credit card information stored in a file somewhere, then it could prove to be dangerous if Ubuntu is connected to a cloud somehow. I don't want my files or information getting out. Please enlighten me regarding this situation. I therefore don't want anything to do with any cloud, period. I don't care if the connection between my computer and the cloud is encrypted. I just don't want to store any kind of personal information anywhere except on my own hard drive. What are my options?

---

### Post by tgalati4 on 2011-02-27
Canonical offers "UbuntuOne" a cloud-based, off-site, storage and syncing service.  It is not installed on your machine, nor does it compromise security of a standard Ubuntu installation.  If you sign up, I believe they currently offer 2 GB of free file storage.  It's helpful for sharing photos with your relatives for instance.

Your privacy concerns are valid.  Since Ubuntu is based on open source source software, many eyes have looked at the code.  I wouldn't use it if I didn't think it was safe.

---

### Post by DrJohn999 on 2011-02-28
UbuntuOne is installed but not configured (ie inactive) in a default Ubuntu 10.10 desktop system. If you do nothing with UbuntuOne it will do nothing in return. If you want to set it up the process is simple. Start at System, Preferences, UbuntuOne. Alternatively, if you *really* are uncomfortable with it even being present on your system then uninstall it from Applications, Ubuntu Software Center.

I use it only for limited quick and convenient file sharing across desktop <--> laptop of noncritical rapidly changing files such as drafts of articles I am writing. But I directly synchronize the home folders of the laptop (encrypted with ecryptfs) and desktop using rsync over my local network on a regular basis: this covers all the other files as well that I don't put in the cloud. I don't use the cloud for this synchronization or for backups -- my personal terabyte doesn't fit and anyway would take maybe a month to synchronize once. I do local daily backups, keep archive copies in a different, secure building in case of fire or theft, and test the restore process regularly.

I too would never put sensitive information into a cloud account, although the data out there is relatively safe from intrusion. I would worry more about losing access temporarily due to an update or incompatibility issue. For my configuration there are three copies of each file anyway, one on the desktop, one in the cloud, and one on the laptop, that are made identical each time the systems sync with the cloud. So losing the cloud copy is a non-issue.

You have total control of your data so take that control and make it work for you.

---

