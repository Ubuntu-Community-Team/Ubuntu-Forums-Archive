---
title: "What's the easiest way to share a folder between a Windows VMware machine and Ubuntu?"
date: 2007-12-31
forum: Virtualisation
---

### Post by diablo75 on 2007-12-31
Here's what I tried to do:

I created a new folder on the desktop of the Windows machine in VMware server, and configured it to be shared with read/write privileges.  I also renamed the computer and restarted it.  After that (in ubuntu) I would go to Places>Network.  And in the past, I've been able to see the newly renamed windows machine in here, and be able to access the shared folder that was created in windows.

But the furthest I've got is that in the Places>Network, where it usually does display the correct hostname of the VM (I called it vmxp), if I double click on it, it gives an error message, saying the contents can't be found.

What should I do?

---

### Post by fjgaude on 2007-12-31
I tell you, we are all learning all the new things, like virutal machines.

I access everything that is in Ubuntu through setting up SAMBA shares. Then using the Networks (Places) in WinXP to read and copy files.

There's other ways I've never used. You have to set the hosts name with its IP address, one that was given when you installed VMware Server, like vmnet1, 2 and 8. Using ifconfig in Ubuntu or ipconfig in WinXP you can find the IP of the ports, eht0, vmnet1, etc., being used.

Place your chosen name and its IP in Hosts file. I do this by using System/Administration/Network/Network Setting/Hosts. Works good.

From there you should be able to Go to a Server in Nautilus. Also make sure you have set folders and files you wish to share in WinXP using its Explorer File Manager.

Let us know how you make out.

---

### Post by bharadwaj on 2007-12-31
vmware even supports direct copy paste between to OSs

---

### Post by diablo75 on 2007-12-31
> **bharadwaj said:**
> vmware even supports direct copy paste between to OSs

This didn't seem to work...

---

### Post by fjgaude on 2007-12-31
It works for me... this just in:

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

This might be of help.

Happy New Year!

---

### Post by diablo75 on 2007-12-31
> **fjgaude said:**
> There's other ways I've never used. You have to set the hosts name with its IP address, one that was given when you installed VMware Server, like vmnet1, 2 and 8. Using ifconfig in Ubuntu or ipconfig in WinXP you can find the IP of the ports, eht0, vmnet1, etc., being used.

Place your chosen name and its IP in Hosts file. I do this by using System/Administration/Network/Network Setting/Hosts. Works good.

From there you should be able to Go to a Server in Nautilus. Also make sure you have set folders and files you wish to share in WinXP using its Explorer File Manager.

I tried this method, and got an error message when attempting to access the vm's hostname through Nautilus (see attached picture).

I'll give the Samba thing a shot later when I have more time to read.  Thanks for your help.  Happy New Year!:guitar:

---

### Post by diablo75 on 2008-01-03
> **fjgaude said:**
> It works for me... this just in:

[http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/](http://2tap.com/2007/04/22/sharing-files-between-a-windows-guest-and-ubuntu-host-using-vmware-and-samba/)

This might be of help.

Happy New Year!

I tried the above tutorial, and failed.

If I open Places>Network, and browse to my ubuntu machine, the Sandbox folder is displayed.  If I double click on it, it asks me to type in a username, domain name and password.  I change the username to sandbox, leave the domain name as MSHOME, and type in the password.  I get an error message back that says the folder could not be found, and that it might have been recently deleted (which is hasn't been).

One line of the tutorial I changed was

sudo chown russ:sandbox sandbox

into

sudo chown sandbox:sandbox sandbox

because "russ" was an invalid user to specify in the command.

And as far as Windows is concerned, it simply won't connect.  I am currently using NAT in my networking setup and I'm pretty sure I'm using the correct IP address.

Any ideas?

Any other suggestions for making file sharing between computers simple?

---

### Post by fjgaude on 2008-01-03
Likely you problem is simple to fix:

```
sudo smbpasswd -a yourloginname
```

You need to tell Ubuntu your samba password, that's all.

Good luck. P.S. Great screen shot, thanks!

---

### Post by diablo75 on 2008-01-03
> **fjgaude said:**
> Likely you problem is simple to fix:

```
sudo smbpasswd -a yourloginname
```

You need to tell Ubuntu your samba password, that's all.

Good luck. P.S. Great screen shot, thanks!

Could you please explain what it is that that command does.  What username am I suppose to put in?  I tried my own ubuntu username, then tried to open that sandbox folder up again from within Places>Network, let the username be my ubunu username, and type my password it.  It just asks for the username/password to be entered again.  And trying "sandbox:password" again doesn't work.

---

### Post by fjgaude on 2008-01-03
The username is the one you use in Ubuntu and so is the password.

You enter the command given in a terminal while in Ubuntu. You will be asked for your password three times.

After that you will have to reboot your machine to have the samba password come into play.

---

### Post by fmontanez on 2011-03-17
i did thing differently without using the terminal.

in a nutshell:
1. create folder on host machine and give it sharing rights
2. set up folder sharing in vmware for that particular virtual machine
3. map network drive pointing to the shared folder on the host machine.


here's what i did.
1. create folder on desktop of host machine. give it a name and right-click to select properties. select the share tab, then select "share folder". select the other 2 choices to allow read/write to folder from other machine. Select Create Share then say yes to nautilus giving extra permission for the folder. when it's done, close that out.

2. open vmware and choose your machine in the library. select virtual machine settings, then select the "optios tab"...on the left you should see folder sharing. click on that and you will see the options change on the right. select always share. 

3. select add under the folder area and navigate to the folder you created on the desktop. click open then save


4. boot up your virtual machine

5. start -> my computer..then select Tools, Map Network Drive...

6. windows will assign a drive letter. don't worry about this...
under the folder area, click browse

in the network places area, you'll terminal services, windows network, vmware shared folders and web client network...

click on the VMware Shared Folders then vmware-host, then shared folders, and there you will see the folder you created. select the folder, then click ok

click finish and you'll see the new network drive...

you can try putting something in that folder on the host machine just to test, so put like a simple text document in there...then in the virtual machine, select the network drive, and you should see the document there...

hope that helps someone out there. i was frustrated because I use various apps that i need to switch back n forth from Ubuntu to Windows

setup:
Ubuntu 10.10
vmware player
windows xp professional

---

### Post by CharlesA on 2011-03-18
Closed due to necromancy.

---

