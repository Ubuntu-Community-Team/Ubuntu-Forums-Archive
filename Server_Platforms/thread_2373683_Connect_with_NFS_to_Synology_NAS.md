---
title: "Connect with NFS to Synology NAS"
date: 2017-10-08
forum: Server Platforms
---

### Post by poy1985 on 2017-10-08
Hi,

Im not that used to linux and ubuntu yet.

So I am trying to mount my Synology Nas to my ubuntu server.

I set up the Synology NFS configurations and granted read access for a user.
But when I try to mount (not in fstab yet as mount already fails) I get the message incorrect mount option was specified.

I try following command:
```
sudo mount -t nfs -o username=user,password=pw nas.lan:/volume1/Media /nfs/media
```

I created the dir /nfs/media to mount my Media folder.
I also installed nfs-commons over apt-get

Anyone an Idea which option is wrong?
```
sudo mount -o username=user,password=pw nas.lan:/volume1/Media /nfs/media
```
and
```
sudo mount -t nfs -o user=user,password=pw nas.lan:/volume1/Media /nfs/media
```

I appreciate any help
Thanks in advance :-)

---

### Post by DuckHook on 2017-10-08
Welcome to the forums, poy1985

I am unfamiliar with the Synology product—are you sure that you have exported the share globally? If so, then it should be accessible to the client without declaring username or password. You must also be sure that your path to the server is declared correctly.

Perhaps the following links will help:

Short guide: [https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)
More comprehensive guide: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

---

### Post by SeijiSensei on 2017-10-08
If you're going to mount the device with sudo, I suggest adding "no_root_squash" to the parameters on the server if that's an option on the Synology.  (I use ordinary Linux machines running NFS as servers.)  Then get rid of the user and password options and mount the device as root.  The same user permissions will apply to the files just as if they were part of the main filesystem.

---

### Post by poy1985 on 2017-10-09
Thanks for any tips so far.
If I leave out username and password it works, except that Synolgoy NAS refuses connection cause I set it up with. I changed the synology mapping with the squash so now it works without user and password.
Don't like it that much but it works

---

### Post by DuckHook on 2017-10-09
> **poy1985 said:**
> …Don't like it that much…Not being argumentative; just curious: what is it that you don't like?

---

### Post by poy1985 on 2017-10-09
Sorry forgot to write before that I now used squash to assign all nfs connections to the admin group on Synology.
So now the connections works and not only sudo can access the files.

Since it is only a local NAS for media server thats fine, but I just don't like the Idea that all connections are mapped to Admin.

Think the problem if I don't do that is with the uid that doesn't match between my ubuntu and Synology NAS. Tried both NFS 3 (default) and also enabled NFS4

Don't really want that everyone is that access over NFS can access as admin.
What is the user and usergroup setup for otherwise...

If anyone has an idea how I could fix this, I'm stil all ears :)

---

### Post by slickymaster on 2017-10-09
Thread moved to **Server Platforms** for a better fit

---

### Post by DuckHook on 2017-10-09
> **poy1985 said:**
> …I just don't like the Idea that all connections are mapped to Admin…Don't really want that everyone is that access over NFS can access as admin.
What is the user and usergroup setup for otherwise...

Ah. I see.

In Linux, the convention is to restrict access with user and group permissions. Merely enabling access to the partition (which is what SeijiSensei's recommendation does) is not that bad if user and group permissions are otherwise properly set.

BTW, no_root_squash does not map all users to the admin group. What it actually does is allow access to users *other* than those who belong to admin—a subtle, but important, difference. Therefore, general users don't actually have system admin privileges… they just have access to that specific partition. If you now set restrictive user and group settings on the files within the partition (or even on the partition itself), then you can prevent unauthorized access to your files. You may wish to read up on user and group privileges. There are plenty of links in my sig that will help, including: "A Great CLI Guide" and "Resources for Newcomers".

To be fair, there are methods to get around such restrictions, but they are arcane and require some serious hacker-fu. Any hacker with sufficient knowledge to accomplish that would likely also be able to get around a user/password restriction too. It is a sad but real fact that NFS is not the most secure protocol. It was designed in the pre-internet days when external dangers were not an important concern, but speed and reliability were. Therefore, most security-conscious gurus seem to feel that if you are okay with NFS in the first place, then its rather primitive security features are rather superfluous and dispensible.

For ways to secure your system and network, there is plenty of advice in my sig link: "Security Basics".

---

### Post by SeijiSensei on 2017-10-09
If you mount as root a device with "no_root_squash," permissions for the files will depend on their ownerships just like files in the local filesystem.

---

