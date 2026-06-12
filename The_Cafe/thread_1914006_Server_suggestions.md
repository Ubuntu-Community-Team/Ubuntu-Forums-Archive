---
title: "Server suggestions"
date: 2012-01-23
forum: The Cafe
---

### Post by Crowchild on 2012-01-23
I run a small consulting company and have been using dropbox to share files between my employees. It's worked great but we need more space than dropbox provides.

      I've been thinking about setting up a server but have no idea where to begin or if this is even the best option. I'm look for a solution that take little maintenance and can easily be accessed with Windows, Mac and Linux computers (often on very slow connections)

    Any suggestions will be great appreciated!

-Adam

---

### Post by ubudog on 2012-01-23
Hi there!  

Well, you could set up an svn server, but I think ftp would be better in this situation.

SVN: [https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)
FTP: [https://help.ubuntu.com/11.10/serverguide/C/ftp-server.html](https://help.ubuntu.com/11.10/serverguide/C/ftp-server.html)

Hope this helps you, 
ubudog

---

### Post by KiwiNZ on 2012-01-23
For a business I would not make a strategic decision for my corporate information and capital expenditure based on the response on a forum.

Contact a few reputable vendors in your area have them do a full needs analysis and ask them to provide a viable system config to meet your needs. Include on going support, DR, Backup etc etc.

---

### Post by Crowchild on 2012-01-23
> **KiwiNZ said:**
> For a business I would not make a strategic decision for my corporate information and capital expenditure based on the response on a forum.

Contact a few reputable vendors in your area have them do a full needs analysis and ask them to provide a viable system config to meet your needs. Include on going support, DR, Backup etc etc.

    Be assured, any responses I get here won't be the only information I use for my decision, just a jumping point. I've had a lot of good advice come from the community but will also be looking for expert opinions from some vendors. 

   That said, there are no 'reputable vendors' in my area. I about 1400 Km from the nearest city.

---

### Post by wyliecoyoteuk on 2012-01-23
You will probably get  amore useful response if you list exactly what your needs are, what size and type of files, whether you want to just share files or have an email server, etc, etc.
There are some useful collaborative tools out there.

---

### Post by ubudog on 2012-01-23
> **kiwinz said:**
> for a business i would not make a strategic decision for my corporate information and capital expenditure based on the response on a forum.

Contact a few reputable vendors in your area have them do a full needs analysis and ask them to provide a viable system config to meet your needs. Include on going support, dr, backup etc etc.

+1

---

### Post by Crowchild on 2012-01-23
I only need the server to share medium sized audio, video, photo and GIS files.

---

### Post by ubudog on 2012-01-23
> **Crowchild said:**
> I only need the server to share medium sized audio, video, photo and GIS files.

I think FTP would work, you could set up a test server to try it out.  :)

[FileZilla]("http://filezilla-project.org/") may also be of interest.

---

### Post by Lars Noodén on 2012-01-23
I would then also look at SSHFS which rides on top of SFTP.  It's very simple and very secure.

---

### Post by KiwiNZ on 2012-01-23
> **Crowchild said:**
> I only need the server to share medium sized audio, video, photo and GIS files.

If you were to contact IBM they will provide you with a Business partner or partners that cover your geographic area.

---

### Post by drdos2006 on 2012-01-23
You may have to do some heavy reading to set up your first server on your own.
Zentyal will get your machine running in an office environment while you learn the more detailed operations of a server. [http://www.zentyal.org/](http://www.zentyal.org/)
Uses a GUI at the server, was based on Ubuntu 10. Long Term Support last time I looked.

Here is a HOWTO which I found comprehensive and invaluable for me to start learning about server requirements. 
Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.570_all.deb

Install with :
sudo dpkg -i webmin_1.570_all.deb

Add extra libraries with :
sudo apt-get -f install

```
Uses a browser pointed to [https://server_IP:10000](https://server_IP:10000) to edit files, create shares, startup daemons etc..

regards

---

### Post by juancarlospaco on 2012-01-24
owncloud.org

---

