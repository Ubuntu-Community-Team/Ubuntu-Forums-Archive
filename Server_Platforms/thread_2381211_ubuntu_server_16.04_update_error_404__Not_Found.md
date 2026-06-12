---
title: "ubuntu server 16.04 update error 404  Not Found"
date: 2017-12-28
forum: Server Platforms
---

### Post by cod3r- on 2017-12-28
Hello friends how can I fix and fix this error ?  appears when I try to upgrade the software... [I]apt-get update / 

[/I]```


root@softinfo:~# apt-get update
Hit:1 [http://repo.ajenti.org/debian](http://repo.ajenti.org/debian) main InRelease
Hit:2 [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) xenial InRelease
Ign:3 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial InRelease
Ign:4 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial Release
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Ign:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Err:5 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main amd64 Packages
  **404  Not Found**
Ign:6 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main i386 Packages
Ign:7 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu](http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu) xenial/main Translation-en
Hit:9 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:10 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial-security InRelease
Hit:11 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:12 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial-proposed InRelease
Hit:13 [http://bg.archive.ubuntu.com/ubuntu](http://bg.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://ppa.launchpad.net/upubuntu-co...amd64/Packages]("http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages")  **404  Not Found**
E: Some index files failed to download. They have been ignored, or old ones used instead.
root@softinfo:~# sudo systemctl restart salt-minion




```

10x

---

### Post by howefield on 2017-12-28
Moved to the "*Server Platforms*" forum.

---

### Post by darkod on 2017-12-28
If you open the link in a browser it shows there doesn't seem to be repository for xenial in there. Maybe it was removed?
Have you tried using one of the official ubuntu repositories and see if that works?

---

### Post by cod3r- on 2017-12-28
I have not tried .. can you give me a link  10x

---

### Post by darkod on 2017-12-28
Here you have a full list of the mirrors: [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

You can select one close to your geographical location and also with good link speed. You make the changes in /etc/apt/sources.list and need to run apt-get update after that to pull down the list from that mirror.

---

### Post by cod3r- on 2017-12-28
I added these links
deb [http://mirrors.neterra.net/ubuntu/](http://mirrors.neterra.net/ubuntu/) xenial main 
deb-src [http://mirrors.neterra.net/ubuntu/](http://mirrors.neterra.net/ubuntu/) xenial main 

from this site
[https://launchpad.net/ubuntu/+mirror/mirrors.neterra.net-archive](https://launchpad.net/ubuntu/+mirror/mirrors.neterra.net-archive)

in a directory:  [I]sudo nano /etc/apt/sources.list

[/I]then I released this command. and returns me the following: 

```


root@softinfo:~# sudo apt-get update
Hit:1 http://mirrors.neterra.net/ubuntu xenial InRelease
Hit:2 http://bg.archive.ubuntu.com/ubuntu xenial InRelease
Hit:3 http://bg.archive.ubuntu.com/ubuntu xenial-security InRelease
Hit:4 http://bg.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:5 http://bg.archive.ubuntu.com/ubuntu xenial-proposed InRelease
Hit:6 http://bg.archive.ubuntu.com/ubuntu xenial-backports InRelease
Hit:7 http://repo.ajenti.org/debian main InRelease
Ign:8 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial InRelease
Hit:9 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease
Ign:10 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial InRelease
Ign:11 http://download.webmin.com/download/repository sarge InRelease
Ign:12 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial Release
Ign:13 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial Release
Ign:14 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:15 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Hit:16 http://download.webmin.com/download/repository sarge Release
Ign:17 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:18 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:20 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Get:21 http://download.webmin.com/download/repository sarge Release.gpg [173 B]
Ign:22 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:23 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:21 http://download.webmin.com/download/repository sarge Release.gpg
Ign:15 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:17 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:18 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:20 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:22 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:23 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:15 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:17 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:18 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:20 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:22 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:23 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:15 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:17 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:18 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:20 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:22 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:23 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Ign:14 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:15 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:17 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:18 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:19 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:20 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:22 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:23 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Err:14 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
**  404  Not Found**
Ign:15 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:17 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:18 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Err:19 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
**  404  Not Found**
Ign:20 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:22 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:23 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Fetched 173 B in 9s (19 B/s)
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://download.webmin.com/download/repository sarge Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D97A3AE911F63C51
W: The repository 'http://download.webmin.com/download/repository sarge Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu/dists/xenial/main/binary-amd64/Packages  **404  Not Found**
E: Failed to fetch http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  **404  Not Found**
E: Some index files failed to download. They have been ignored, or old ones used instead.
root@softinfo:~#




```

---

### Post by darkod on 2017-12-28
Try something like this:
```
sudo cp /etc/apt/sources.list /etc/apt/sources_backup20171228.list
sudo sed -i 's/ppa.launchpad.net\/upubuntu-com\/ppa/mirrors.neterra.net/' /etc/apt/sources.list
sudo apt-get update
```

That should change all entries in sources.list to the one you want.

---

### Post by cod3r- on 2017-12-28
again the same mistake  **404 Not Found**

```

[I]
root@softinfo:~# sudo cp /etc/apt/sources.list /etc/apt/sources_backup20171228.list
root@softinfo:~# sudo sed -i 's/ppa.launchpad.net\/upubuntu-com\/ppa/mirrors.neterra.net/' /etc/apt/sources.list
root@softinfo:~# sudo apt-get update[/I]
Hit:1 http://mirrors.neterra.net/ubuntu xenial InRelease
Ign:2 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial InRelease
Hit:3 http://repo.ajenti.org/debian main InRelease
Hit:4 http://ppa.launchpad.net/ondrej/php/ubuntu xenial InRelease
Ign:5 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial InRelease
Ign:6 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial Release
Ign:7 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial Release
Ign:8 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:12 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:12 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:12 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:12 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Ign:8 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
Ign:9 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Ign:12 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
Ign:13 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Err:8 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main amd64 Packages
  404  Not Found
Ign:9 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main i386 Packages
Ign:10 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main all Packages
Ign:11 http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial/main Translation-en
Err:12 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main amd64 Packages
  404  Not Found
Ign:13 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main i386 Packages
Ign:14 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main all Packages
Ign:15 http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial/main Translation-en
Hit:16 http://bg.archive.ubuntu.com/ubuntu xenial InRelease
Hit:17 http://bg.archive.ubuntu.com/ubuntu xenial-security InRelease
Hit:18 http://bg.archive.ubuntu.com/ubuntu xenial-updates InRelease
Hit:19 http://bg.archive.ubuntu.com/ubuntu xenial-proposed InRelease
Hit:20 http://bg.archive.ubuntu.com/ubuntu xenial-backports InRelease
Ign:21 http://download.webmin.com/download/repository sarge InRelease
Hit:22 http://download.webmin.com/download/repository sarge Release
Reading package lists... Done
W: The repository 'http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ppa.launchpad.net/kakrueger/openstreetmap/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Failed to fetch http://ppa.launchpad.net/upubuntu-com/ppa/ubuntu/dists/xenial/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
root@softinfo:~#





```

---

### Post by darkod on 2017-12-28
My command needs little modification.

First, I see you are running commands as root. If you do that, just ignore the sudo in front and don't type it. sudo is used for standard user running system commands but if you already use root just forget about the sudo word...

Try the following:
```
sed -i 's/ppa.launchpad.net\/upubuntu-com\/ppa/mirrors.neterra.net/g' /etc/apt/sources.list
apt-get update
```

---

### Post by cod3r- on 2017-12-28
10x



0 packages can be updated.
0 updates are security updates.

---

