---
title: "Internet File Server?"
date: 2007-01-31
forum: Server Platforms
---

### Post by acegolfer on 2007-01-31
I have used WebDAV for my internet file server until now. I want to seek other options.

BACKGROUND 

My Ubuntu file server is in my office running 24/7. I want to read/write from XP anywhere in the world. I don't want to save the files locally in XP. I just want to keep all my files in one central location.

WEBDAV PROBLEM

I like WebDAV as it does what I want to do for most files: doc, ppt, xls. But I can't open pdf files remotely. I first have to save pdf to my XP in order to open it.

Any help will be appreciated.

---

### Post by randomnumber on 2007-01-31
there really is no such thing as opening files remotely. When this appears to happen it is just that the file gets automatically in a temp folder and opened from there. If you don't believe look into the temp/cache folder for your web browser. Even when you view pictures on the web the picture file is downloaded to your computer. I think that the only time this may not be true is when you use a UDP verses TCP, This i am not certain of.

I use the ssh protocols to gain access to my computer and get files. Just install the ssh server on the ubuntu machine. 

If you are using XP get/send files you need to get get a program like filezilla ( [http://sourceforge.net/projects/filezilla/](http://sourceforge.net/projects/filezilla/) )

If you want to log into your machine from remote location you can use a program like putty ( [http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/) )

This is almost all you need, this and some knowledge about networks.
If your server is behind a router/etc you need to forward a port (22 i think) to that machine.

Also there are sometime hackers that try to gain access to your machine through brute force methods. To get around this there are security things that block address after X number of attempts. Anyway this is too to go into here and I do not know that much about it.  

Good Luck

---

### Post by Brazen on 2007-01-31
> **acegolfer said:**
> I have used WebDAV for my internet file server until now. I want to seek other options.

BACKGROUND 

My Ubuntu file server is in my office running 24/7. I want to read/write from XP anywhere in the world. I don't want to save the files locally in XP. I just want to keep all my files in one central location.

WEBDAV PROBLEM

I like WebDAV as it does what I want to do for most files: doc, ppt, xls. But I can't open pdf files remotely. I first have to save pdf to my XP in order to open it.

Any help will be appreciated.

Your best bet would probably be to set up a Samba server and then use a vpn connection (such as OpenVPN) to gain access to the file server.  You'll want to make sure and use a vpn connection though.  You don't want to just leave a SMB file server open to the internet or you'll get haxxx0r3d out your axxx0rs.

---

### Post by acegolfer on 2007-02-01
> **randomnumber said:**
> there really is no such thing as opening files remotely. When this appears to happen it is just that the file gets automatically in a temp folder and opened from there. If you don't believe look into the temp/cache folder for your web browser. Even when you view pictures on the web the picture file is downloaded to your computer. 


This is not entirely true. I'm currently using WebDAV and I can access Ubuntu files from XP in Windows Explorer without web browser outside home network. It opens remotely and saves remotely. Technically, it will download to my local machine RAM not HDD.

I know both SSH and SAMBA.

SSH or VPN is no good because sometimes I have to work from public PC. 
SAMBA is no good outside the home network.

So far, the closest thing to what I want is WebDAV (Web Folders). But as I said in the first post, it comes with a small price.

---

### Post by linuchsan on 2007-02-01
Have you tried Winscp. It can be used explorer-like with drag & drop.

---

### Post by randomnumber on 2007-02-05
use ssh and carry a thumb drive with a ssh client installed on it. 

I did mean that files are downloaded at least into ram.  But most also download to the harddrive too.

---

### Post by acegolfer on 2007-03-03
Well, I tried Winscp. It does what it claims to be. But it doesn't meet my demand.

If I want to edit a remote file, Winscp opens the file locally (after download) but can't save to the server. I have to save locally and then upload to the server, which leaves me 2 files (one in the server and another locally). Is there anyway to save remotely?

---

### Post by Mr. C. on 2007-03-04
Acegolfer,

You are correct in your understanding of WebDav.  As a protocol, it provides sufficiently enabled clients to work with documents remotely.  The documents are not simply copied into a temp folder for local work - rather, the enabled clients, such as Windows XP and its Web Folders, provides the illusion of locality.

Unfortunately in Acrobat only collaborative  PDF document commenting is available.

Your quest for something other than WebDav requires a protocol in which applications are sufficiently enabled to allow such access.  There is no other such protocol, nor ubiquitous application support.

Your only hope is to do as other's suggest - carry with you some small USB-like device with a security-enabling layer (VNP, SSH), and make some connection back to your remote server access the documents locally.

An alternative is to configure your server as a Citrix server, where you can then use a web browser anywhere, which will initiate a very small client download enabling you to access whichever applications are installed and configured on the Citrix server.  ( my wife's company provides this, where she is able to access her applications on a virtual desktop provided by the companies Cirtix server.)  Perhaps you should investigate this.

MrC

---

