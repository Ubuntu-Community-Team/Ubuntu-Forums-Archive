---
title: "How do I allow Deluge to access torrents added to Samba share"
date: 2010-06-22
forum: Server Platforms
---

### Post by mkmcllln on 2010-06-22
Hello all,

I'm trying to set up the following "server" system.  (I say "server" because I'm really running ubuntu-desktop 10.04 LTS):

I have set up Samba and allowed guest access to my /media/Share/data using Windows 7. Everything works great, I can create folders, add files, etc.
However I noticed that when I add files or folders via my mapped drive in Windows 7, it defaults to permissions that do not allow Deluge to access them. I realized that if I go back to the server and give it ```
sudo chmod 0777 /media/Share/data/(folder or file)
``` Deluge can now access the files.
I don't want to have to modify permissions every time I add a new torrent to Deluge's watch folder which is /media/Share/data/Torrents.

How do I configure Samba (or linux, or windows) to give rwx permissions when I add a file or torrent via windows?  And vice versa, if deluge downloads a file and moves it to completed downloads (which I haven't been able to get this far yet) will I be able to access it via Windows 7?

Thanks to all that can help.

---

### Post by BobVila on 2010-06-22
What are the perms on the folder?

---

### Post by mkmcllln on 2010-06-22
> **BobVila said:**
> What are the perms on the folder?

My Samba Share folder which is [data] is full read write guest access.  Every other folder I've created (using windows 7) I gave them sudo chmod 0777.  My problem is, when I download a torrent via windows and move it to my Ubunut Deluge watch folder, the program Deluge can't execute the torrent file unless I go back onto my ubuntu server and change the permissions of the torrent file to 0777.

---

### Post by arrrghhh on 2010-06-22
Permissions from Windows machines are going to be wonky... I was having issues when I would create a new folder, I would have to then redo permissions on it from within the Linux box.  So I have a cron job that chmod's the directory for my torrents to 777 every minute.  Not pretty, but it solves a lot of issues.

With that said, I thought the file would assume the folder's permissions if moved via Samba?  Don't quote me on that, I'm not sure.  I did the chmod script to solve my folder issue, and maybe I would've had this issue with torrent files if I hadn't... I guess the only way to tell would be to remove that cron job and see if torrent files can be dropped in my watch folder & still get downloaded.

FYI I use rTorrent, but the concept should be the same.

---

