---
title: "VMWare Fails to Install"
date: 2008-03-23
forum: Virtualisation
---

### Post by bluewhale on 2008-03-23
I installed Ubuntu and VMWare Server about three weeks ago. However I'm unable to install a newer version of VMWare Server... I have downloaded the tar file and unzipped it. However when I run 'sudo vmware-install.pl' I get a 'command not found' error. 

Have googled it and find there were a lot of people having this problem two years ago, but no one really having it now. 

Do I need to remove the current VMWare installation to install this newer one? If so how might I save the settings and clients already created?

---

### Post by munkyeetr on 2008-03-23
You may need to remove the current installation, but try:
```

sudo perl vmware-install.pl

```

---

### Post by dcstar on 2008-03-24
> **bluewhale said:**
> I installed Ubuntu and VMWare Server about three weeks ago. However I'm unable to install a newer version of VMWare Server... I have downloaded the tar file and unzipped it. However when I run 'sudo vmware-install.pl' I get a 'command not found' error. 

Have googled it and find there were a lot of people having this problem two years ago, but no one really having it now. 

Do I need to remove the current VMWare installation to install this newer one? If so how might I save the settings and clients already created?

The "new" 1.0.5 version of VMware server only has a few security fixes compared to the 1.0.4 version available in the Ubuntu Partner repositories, so it is hardly worth changing for most people.

I imagine the VMware maintainers will upgrade this soon anyway.

---

### Post by bluewhale on 2008-03-24
:idea:  'DOH!'   Forgot I have workstation at work. It's the free server I was writing in about. I had thought to test ways to update it at work as I haven't registered my XP Pro client with MS yet... but as this one is VM Workstation no chance to test it. 

My concern at home is that I just registered XP with MS there a week ago. Could one of  you point me to a URL where detailed steps are listed to save a 'client' and install it on a new VMWare server? 

( I attended a 4 day VMWare ESX class two weeks ago: oddly enough we never got to this part. I guess it's just assumed one knows about it. )

Thanks

---

### Post by fjgaude on 2008-03-24
Go to wherever the VM is installed and simply copy the whole folder to another disk, usually in the range of 10 to 15 Gigabytes. Then you place that file to wherever you have installed your new console to handle it, either Player or Server. Point to it and it runs.

I forget the default location of the .vmx folders but it seems like it is /usr/lib something. I always store my vm in my /home directory.

---

