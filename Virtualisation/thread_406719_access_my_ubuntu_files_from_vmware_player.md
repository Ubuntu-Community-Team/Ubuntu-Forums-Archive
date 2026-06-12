---
title: "access my ubuntu files from vmware player"
date: 2007-04-11
forum: Virtualisation
---

### Post by Obor on 2007-04-11
I have windows 2000 that I've installed in vmware server some time ago. I'm running it using vmware player and it works fine. I can connect to internet using bridged or NAT connection.

So far all my attempts to access my ubuntu files were unsuccessful. Nothing comes up when I try mapping network places etc. 

What do I need to do to be able to access my ubuntu files from win2000 that I'm running in vmplayer? (I don't need to access files in vmplayer/win from ubuntu.)

---

### Post by damu on 2007-04-11
There are 2 ways that I know of :

-an external HD or usb key : it is the easiest. The only thing is to plug it while while you are in Win/Vmware...it can't be mounted on both systems at the same time.

- networking with samba. Well, I guess you've followed some tutorials for this already. i must say that the simple worked for me: administration/shared folder. Ubuntu ask you to install a few packages. Once this is set, in WinXP( Win 2000 might be different, I don't know) set it/the network with the same login password. It seems that if the login/passwords in Ubuntu and Win are not the same, then it becomes a bit of a mare...

good luck

---

### Post by dexter on 2007-04-11
You could install open-ssh server on your ubuntu box. Install a scp client in your win2000 and create an ssh connection from your windows machine to your ubuntu machine (you could use winSCP under windows). That way you'll able to see all of you ubuntu files in windows without sharing it all.

I use this in my network to transfer files between my MacBook and my Ubuntu machine, works great.

---

### Post by Obor on 2007-04-11
> **dexter said:**
> You could install open-ssh server on your ubuntu box. Install a scp client in your win2000 and create an ssh connection from your windows machine to your ubuntu machine (you could use winSCP under windows). 

Thanks, that worked.

---

### Post by centguy on 2008-02-05
I understand the instructions fully. This only works when I am connected to the internet. This is because from the linux host, I can issue a command /sbin/ifconfig -a to figure out the IP address of
my linux machine, then I use that IP address in windows xp to establish a connection using winscp. 

However, when I am NOT connected to the internet, /sbin/ifconfig -a cannot give me an IP adderess under the eth0 entry, so I don't have a way to transfer files between the two machines. Any great ideas ?

p/s: I tried to understand the file sharing mechanism (from a google search) between windows and linux but I just cannot understand every single step. All these samba, mounting, host file (/etc/hosts ??),... stuff are just too much for me at this moment.

---

### Post by zvacet on 2008-02-05
I hope that you have vmware tools installed.Follow [this](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/) instructions and you will see it is not that hard to do.You can read [this](http://ubuntuforums.org/showthread.php?t=652640&highlight=sharing+files).It is based on first one but maybe easyer to understand.

---

### Post by centguy on 2008-02-05
Thanks zvacet! I looked up the Russ's site you mentioned. I chose NAT in the Network Connection or Custom: Specific virtual network /dev/vmnet8 (for some reason  /dev/vmnet1 should not be used at all, I tried it but it couldn't work hence I sent out an email for help as above...), and the IP address is that the entry under vmnet8 or vmnet1 in the output under /sbin/ifconfig -a command.

Now I have a very primitive way to backup my files in guest machines to a thumbdrive in the host machine. ( i am still figuring how to ask  the guest OS to detect usb drives, so far I have no luck).

Thanks!!

---

### Post by gm.matias on 2010-02-12
I am using VMPlayer and in the configuration I enabled the Share Files options but it did not work for me. I read some more articles and found a good solution that works for me. I put in here: [http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12](http://www.gmmatias.com/sharing-a-disk-drive-of-an-ubuntu-host-to-a-guest-windows-on-vmplayer-using-samba-2010-02-12)

Hope it helps.

---

