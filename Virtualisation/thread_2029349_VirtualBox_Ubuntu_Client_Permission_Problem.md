---
title: "VirtualBox Ubuntu Client Permission Problem"
date: 2012-07-19
forum: Virtualisation
---

### Post by waltermmm on 2012-07-19
Hallo

Well I know this questions has been discussed very often and I tried differen thins but I don't find an answer to my problem.

I have CentOS 6.2 as host and Ubuntu 12.04 as guest running in VirtualBox.

I have created a shared folder but I have only read access to it. It's a permission problem.

So what I have done:

I have mounted the folder

```
sudo mount -t vboxsf vbox-Share /mnt/vbox-Share
```

and then I added my user to the vboxfs

```
sudo usermod -G vboxsf -a user
```

I also tried to change the owner

```
sudo chown -R user /mnt/vbox-Share
```

I have not idea, but I cannot access my Shared folder in reading mode, using root it works.

Also automatically mounting fails.

Can somebody help me please

Kind regards and thanks in advance

Walter

---

### Post by drdos2006 on 2012-07-19
You might find it easier to control your Ubuntu with Webmin via your browser on CentOS.

Logon to your virtualbox OS, open a terminal and download with :
sudo wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.580_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.580_all.deb)

Install with :
sudo dpkg -i webmin_1.580_all.deb

Add extra libraries with :
sudo apt-get -f install

On CentOS, use a browser pointed to [https://your_virtual_box_OS_IP:10000](https://your_virtual_box_OS_IP:10000) to edit files, create shares, startup daemons, change permissions  etc..

regards

---

### Post by waltermmm on 2012-07-19
Yeah I know this program but I would like to create a Vbox Share not a Network Share.

---

