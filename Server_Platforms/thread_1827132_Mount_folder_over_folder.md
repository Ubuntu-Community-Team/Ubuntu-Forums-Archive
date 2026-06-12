---
title: "Mount folder over folder"
date: 2011-08-17
forum: Server Platforms
---

### Post by s0bz on 2011-08-17
Hi all,

I'm installing a webserver in a Ubuntu 10.04. I want to install the webserver in a separated volume to backup it easily.

This is a resume:

```
apt-get -y -q install xfsprogs
mkfs.xfs /dev/sdf1
mkdir /ebs
mount /dev/sdf1 /ebs

mv /etc/nginx /ebs/etc/

echo "/ebs/etc/nginx /etc/nginx      xfs noatime 0 0" | tee -a /etc/fstab
mkdir /etc/nginx
mount /etc/nginx
```

When i try to mount the folder i get this message:

```
root@server:/# mount /etc/nginx
mount: /ebs/etc/nginx is not a block device
```

Can help me somebody?

Very much thanks!!

---

### Post by arrrghhh on 2011-08-17
mount --bind perhaps?

---

### Post by SeijiSensei on 2011-08-18
Why not just use a symlink?

```

mount /dev/sdf1 /ebs
mv /etc/nginx /ebs/etc/
cd /etc

# just in case
mv -f nginx nginx.old

ln -s ../ebs/etc/nginx

```

---

