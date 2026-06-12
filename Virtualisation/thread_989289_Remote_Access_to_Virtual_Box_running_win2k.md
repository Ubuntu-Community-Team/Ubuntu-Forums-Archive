---
title: "Remote Access to Virtual Box running win2k"
date: 2008-11-21
forum: Virtualisation
---

### Post by Robbyx on 2008-11-21
I need to give a windows user remote access to my Virtual Box running win2k. I also wish to restrict their access to a limited number of subdirectories in the shared folders. I have tried logmein and I am not succeeding in logging into Virtual box. Also I can not see how I can restrict the access rights.

What is the best way to do the above?

Robin

---

### Post by bodhi.zazen on 2008-11-21
Remote access should be easy, either ssh or vnc.

ssh = command line only. Windows client = Putty.

Just look at securing the ssh server (keys , etc)

You can transfer files with winscp (gui).

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

permissions should take care of your access. Make a group "share" and make the directories accessible to the share group.

If you need to further restrict access, take a look at rbash.

If you go with VNC, you can forward the entire desktop, again be sure to secure the VNC server or user FreeNX or tunnel over ssh.

---

### Post by Robbyx on 2008-11-21
What I had hoped for was the remote user can run windows remotely accessing win2k within VirtualBox.  Will what you suggest allow that?

---

### Post by bodhi.zazen on 2008-11-21
> **Robbyx said:**
> What I had hoped for was the remote user can run windows remotely accessing win2k within VirtualBox.  Will what you suggest allow that?

What do you mean exactly ? start virtualbox ? log into windows ?

If you are wanting to log into windows, you can use rdp or vncserver.

---

### Post by Robbyx on 2008-11-21
This the position:

I have some programs that will only run under windows. I have a friend who would like to access them so that he can enter data.  He wishes to do it from his house not mine.

When I wish to run those programs I start up VB and run them from my desktop. I would like him to do the same but from within VB so that he is not also seeing the Ubuntu desktop.

---

### Post by bodhi.zazen on 2008-11-21
My guess is you are wanting to use a VNC connection.

Set you your windows guest with a bridged connection, forward the port from your router to the windows machine.

For security you may wish to look at FreeNX.

[http://www.cyberciti.biz/tips/linux-remote-desktop-for-controlling-windows-xp-desktop.html](http://www.cyberciti.biz/tips/linux-remote-desktop-for-controlling-windows-xp-desktop.html)

(FreeNX, AKA NXServer) ) [http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by Robbyx on 2008-11-23
I decided to install TightVNC. I assume I was correct to install DFMirage on the host not the guest.

Do you know how to find the IP address the guest uses to access the VB through VNC? In VB the VNC icon shows:

10.0.2.15

On the quest side I assume a similar copy of VNC needs to be installed. If not is access via the browser?

Thanks for your help so far.

Robin

---

### Post by HermanAB on 2008-11-24
Windows XP Pro has Remote Desktop (which MS bought from Citrix).  RDP is secure and works very well.  However, the older Win2000 doesn't have this.  So you need VNC.  The only problem with VNC is that it is not secure.  If you can live with someone sending his user name and password in clear over the public internet, then go ahead.

Cheers,

Herman

---

