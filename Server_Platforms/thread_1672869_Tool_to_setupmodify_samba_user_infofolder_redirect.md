---
title: "Tool to setup/modify samba user info/folder redirection"
date: 2011-01-21
forum: Server Platforms
---

### Post by TDrakeHI on 2011-01-21
I have been looking and looking and have not found any helpful solution this past week.  I currently have a small business network with 6 clients, all running XP Pro, pulling roaming profiles off of the PDC which is running Ubuntu Server 64-bit 10.04 LTS.

Some of the profiles have gotten rather large and so login/logoff times are taking way too long, and so, I remember when I set the network up that there was an option to save the majority of the profile information on a shared folder on the server so that the profiles would not update it on login/logoff.  

I now know that it is called folder redirection but have been unable to find any information about updating the roaming profiles to do that.  At least I haven't found a way to do it in Linux.  

Does any body have any info on what I need to do to setup the profiles to be able to do this.  Is there some RegEdit type program that I need to use?  Or is there some sort of samba user tool that will do this.  I really have no idea where to start. 

Any help will be much appreciated.

---

### Post by Boondoklife on 2011-01-21
Are you trying to setup redirected folders on the windows machines, or are these ubuntu machines?

If windows then take a look [[here]("http://www.windowsnetworking.com/articles_tutorials/Profile-Folder-Redirection-Windows-Server-2003.html")].
If ubuntu then they only way I have found to do this is map the needed shares on login, and then make the Documents folders, Music, Video, etc. symbolic links (ln -s) to the shared locations.

---

### Post by TDrakeHI on 2011-01-21
But how do I do that with an Ubuntu server, as I can't run any win programs on the server.  Can the group policy be edited from a client machine on the network??

---

### Post by Boondoklife on 2011-01-21
You would not do this on the server, this is a client configuration. You might wanna check out msc or maybe see if you can do it with a vbs file and tweaking the registry. If the latter, then you may be able to create a startup script that will do it on login.

---

