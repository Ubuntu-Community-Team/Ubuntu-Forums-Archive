---
title: "Restrict access to nfs mount"
date: 2010-04-12
forum: Server Platforms
---

### Post by dragos2 on 2010-04-12
Hi guys,

I will mount a nfs share on a client with fstab. Is there a way to don't allow some users access
to that folder ?

---

### Post by fang0654 on 2010-04-12
Make the folder not everyone viewable, and put the users that can access it into a group that owns it.

For example:

Say your nfs folder is in /media/invoices and the only users allowed to access are bill, tom, and joe:

```

sudo groupadd invoices
sudo useradd -G invoices bill
sudo useradd -G invoices tom
sudo useradd -G invoices joe
sudo chown root:invoices /media/invoices -R
sudo chmod g+rwX /media/invoices -R
sudo chmod o-rwX /media/invoices -R

```

---

### Post by dragos2 on 2010-04-13
> **fang0654 said:**
> Make the folder not everyone viewable, and put the users that can access it into a group that owns it.

For example:

Say your nfs folder is in /media/invoices and the only users allowed to access are bill, tom, and joe:

```

sudo groupadd invoices
sudo useradd -G invoices bill
sudo useradd -G invoices tom
sudo useradd -G invoices joe
sudo chown root:invoices /media/invoices -R
sudo chmod g+rwX /media/invoices -R
sudo chmod o-rwX /media/invoices -R

```

Thanks but it is not working. Also ACL does not work too.

---

### Post by iissmart on 2010-04-13
Make sure your server is running NFSv4 and your client is mounting it as nfs4 and not just nfs. Then your ACL will work.

---

### Post by dragos2 on 2010-04-14
> **iissmart said:**
> Make sure your server is running NFSv4 and your client is mounting it as nfs4 and not just nfs. Then your ACL will work.

Thanks for this. I will dig into it.

What about using netgroups ?

Here [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo) says:
```

**Note:** This **only**  works if using NIS. Otherwise, you can't use netgroups, and should  specify individual IP's or hostnames in /etc/exports. Read the **BUGS**  section in man netgroup. 
Edit  /etc/netgroup and add a line to classify your clients. (This step is not necessary, but is for  convenience). 
myclients (client1,,) (client2,,)Obviously, more  clients can be added. myclients can be anything you like; this is a *netgroup name*.

```

So I can restrict users on the server side with NIS ?

---

