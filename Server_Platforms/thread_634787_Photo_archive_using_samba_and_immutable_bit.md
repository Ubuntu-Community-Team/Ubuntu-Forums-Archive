---
title: "Photo archive using samba and immutable bit"
date: 2007-12-08
forum: Server Platforms
---

### Post by andca97 on 2007-12-08
Situation description
I have a small network with 5 clients, 3 running Windows XP and 2 running Ubuntu 7.10 Desktop. I am about to setup a server running Ubuntu 7.04 Server. The server disk configuration is to be as follows, 40 GB system disk and 3 x 80 GB RAID-5 for storage.

What I want to do
I want to have a photo archive located on the RAID-5 drive. The archive is to be shared on the network using samba. I want all users to be able to upload photos. I want NO user to be able to delete photos. The idea is to protect the photos from unintentional deletion.

How I have tried to solve it
Samba configuration:
```
sudo useradd –c ”Netwok User” –g users –p abc123 net_photo
sudo mkdir /radid5/photo
sudo chown net_photo /radid5/photo
sudo chmod 770 /radid5/photo
```

/etc/samba/smb.conf:
> [global]
workgroup = ACTK
netbios name = UBUNTU
security = SHARE

[data]
comment = Photo archive
path = /radid5/photo
force user = net_photo
force group = users
read only = No
guest ok = Yes
create mask 0770
directory mask 0770

Inotify-tools-3.10:
I have installed inotify-tools-3.10
source added: deb [http://www.prodeia.de/mms/feisty/](http://www.prodeia.de/mms/feisty/) binary/
```
sudo apt-get update
sudo apt-get install inotify-tools
```

Inotifywait setup:
File created: /etc/init.d/run_inotifywait.sh with the following contents:
> inotifywait –mr – CREATE –format ”%w%f” /shared_data/ | xargs – max-args=1 /etc/scripts/immute.sh

```
sudo chmod +x /etc/init.d/run_inotifywait.sh
mkdir /etc/scripts
```
File created: /etc/scripts/immute.sh with the following contents:
> chattr +i $1

```
sudo chmod +x /etc/scripts/immute.sh
cd /etc/init.d
sudo update-rc.d run_inotifywait.sh start 2 S .

```

Problem description
The script runs at boot but the files added to /raid5/photo/ does not get the immutable bit set. If I change the command in /etc/scripts/immute.sh from *"chattr +i $1"* to *"echo $1"* it works just fine and the script prints all filenames added to /raid5/photo/ on the screen.

I would be greatly thankful for any ideas on how to get this to work as intended.

regards
Anders Carlsson

---

