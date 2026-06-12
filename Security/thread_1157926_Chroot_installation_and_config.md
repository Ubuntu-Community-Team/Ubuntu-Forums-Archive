---
title: "Chroot installation and config"
date: 2009-05-13
forum: Security
---

### Post by pc-cito on 2009-05-13
I all.

I have a script to backup from PC1, PC2, PC3, ... to server over ssh.

I want to use chroot to make possible each user (user1, user2, ...) access to the server but only see his own files.

Someone have experience with chroot?

I want that every time i add a user all envoirment configures automatly.

---

### Post by cdenley on 2009-05-13
This relies on the ChrootDirectory option in ssh, and I don't think that is available before ubuntu 8.10.

I never thought the security benefits of a chroot are worth the trouble of setting it up. However, I was bored, so I wrote a script you might find useful. First to setup a chroot and configure ssh to use it, run these commands:
```

sudo -i
mkdir -p /chroot/master
mkdir /chroot/users
mkdir /chroot/union
apt-get install debootstrap aufs-tools
CODENAME=`grep ^DISTRIB_CODENAME= /etc/lsb-release|cut -d = -f 2`
debootstrap $CODENAME /chroot/master/ http://archive.ubuntu.com/ubuntu
echo Match group sshchroot>>/etc/ssh/sshd_config>>/etc/ssh/sshd_config
echo "   ChrootDirectory /chroot/union/%u">>/etc/ssh/sshd_config
/etc/init.d/ssh restart
exit

```

Next, install this script in /usr/local/bin/newchroot and make it executable:
[ATTACH]114533[/ATTACH]
```

sudo wget -O /usr/local/bin/newchroot "http://ubuntuforums.org/attachment.php?attachmentid=114533&d=1242912181"
sudo chmod +x /usr/local/bin/newchroot

```

Now, to setup a new user that uses a chroot environment when connecting through ssh:
```

sudo newchroot [username]

```

I also made a script to delete chroots/users.
[ATTACH]113647[/ATTACH]
```

sudo wget -O /usr/local/bin/delchroot "http://ubuntuforums.org/attachment.php?attachmentid=113647&d=1242238817"
sudo chmod +x /usr/local/bin/delchroot

```

It's kind of a complicated process, and I don't think I can make it any easier. All users will share a master chroot, but any changes they make (to their home directory) will be written to a separate directory outside the master chroot. It works kind of like the livecd, where the chroot is read-only, and instead of writing filesystem changes to memory, it's written to /chroot/users/[username]. None of the users can see the other's chroot changes, or even see which other users exist.

My script makes changes to /etc/fstab, and adds users and changes passwords. I haven't tested it thoroughly, so use it at your own risk.

---

### Post by pc-cito on 2009-05-13
Hi!

thanks for the scripts :)

I have a problem with

```
echo ChrootDirectory /chroot/union/%u>>/etc/ssh/sshd_config
/etc/init.d/ssh restart

```

It's something wrong into sshd_config

And into apt-get install is debootstrap, not deboostrap (to help another possible interested)

---

### Post by cdenley on 2009-05-13
> **pc-cito said:**
> It's something wrong into sshd_config

What do you mean?
```

man sshd_config

```
As I said in the first sentence of my post, it only works with ubuntu 8.10 or newer. The ChrootDirectory option was not available before that.
```

cat /etc/lsb-release
dpkg -l openssh-server

```

---

