---
title: "Linux Server Resources?"
date: 2006-10-21
forum: Server Platforms
---

### Post by misterE0 on 2006-10-21
I'm running an ubuntu server right now as a file & lampp server.  I'm interested in learning other things that I can do with the machine, but have had trouble finding resources that both describe different possible server functions in real terms and also provide insight on WHY they are useful.  I've been using linux as a desktop os for many years now, and would like to dive a bit deeper into it's possibilities as a server.

Just one example...i'd like to set up a domain on my network, but haven't found any n00b tutorials or info on such a thing.

I'm sure there are lots of other things that I could benefit from, but haven't been able to find the resources.  Anyone have any advice for me?  Thanks in advance.

---

### Post by bswilson on 2006-10-21
Honestly, if you don't know why you would need a server, then you probably don't need one.

However, if you're on a quest to learn more about server programs, specifically on Linux systems, then go for it!  The reason we call a system a server is because it serves users (and that is not a flippant answer).

For example:
[LIST=1]
[*]You want to give multiple users access to some files.  You might want to install an FTP or SSH server (vsftpd, OpenSSH, etc.)
[*]You want to create a Web site that remote people can visit.  You might want to install an HTTP server (Apache, LightHTTPD, etc.)
[*]You want to set up a gaming server and host <insert favorite game here> matches; you might want to set that up, etc.
[/LIST]

There are an infinite number of things you can do. :D

---

### Post by sonic2000gr on 2006-10-21
> **misterE0 said:**
> 
Just one example...i'd like to set up a domain on my network, but haven't found any n00b tutorials or info on such a thing.


Do you mean a Windows or a Linux network? Guessing from what you said (you use Linux as a desktop OS) you mean a Linux network. There are some good advantages to that. A Linux domain consists of at least one NIS server and possibly an NFS server (they can be hosted on the same machine). The NIS server keeps a centralized database of users and passwords, so any account created on the NIS server is valid on all machines that connect to the domain. Meaning you create user joefoo at the NIS server and he can login at any machine, no more setups required. This is where the NFS server comes in also, since you can create  /home  on a server and mount it through NFS to all clients. So not only joefoo has an account valid on all machines, but his documents follow him as well... 
This functionality is roughly equivalent in a windows world to a Windows Domain with roaming profiles and My Documents redirection.

You can learn how to setup NIS server and clients [here]("https://help.ubuntu.com/community/SettingUpNISHowTo"). There are also more resources in the web, just google "Setup NIS server"

NFS, is the windows equivalent of "File and Print Sharing", but for Unix/Linux (If you wish to serve Windows machines, you need the Samba server). Setting up is extremely simple.

A nice tutorial is also [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo"). Again there is lots of this stuff in the web.

---

### Post by elst on 2006-10-21
I think that bswilson has covered it, but I'll just chip in that many network services that you see discussed in older books have been effectively replaced by either HTTP and the Web, or OpenSSH. If you have a Web server then you can share files and applications without needing anything else. FTP is one example of a protocol which is now pretty much redundant.

---

