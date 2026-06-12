---
title: "Need a Way"
date: 2007-07-26
forum: Server Platforms
---

### Post by MasterXandrex on 2007-07-26
All, 

Here's my situation and limitations:

My work workstation is a Windows XP PC to which I do have administratve rights. My server at home is a standard Ubuntu Linux (:guitar:) server. I need a way to share a directory (possibly a network directory) to my home from my work PC. 

Firstly, needless to say, I probably shouldn't be doing this do I need as low a profile as possible. Currently, I have a server setup and am able to SSH from work into the server. I cannot go the other direction in any way (nor do I really want to create an SSH server on my workstation). Does anyone know a way for me to do this? 

Thanks,

Xan

---

### Post by reckless2k2 on 2007-07-26
i think you are saying you need samba setup. Query samba setup in this forum and you'll get a nice how to.

---

### Post by MasterXandrex on 2007-07-26
No, you misunderstand (or I did not state). I need a way to pull files from my work PC without having to store a second copy or install a server system on the work PC.

Basically I need a way for the client to share files with the server... a bit backwards I know.

Xan

---

### Post by Modernity on 2007-07-26
If you want to store files on your home server, by using your work pc, then maybe FTP access (on your server) would be sufficient. Not sure if this is what your looking for, but it might be the easiest way for you to store stuff and have global access. If this is not what you are planning to do with it, please explain in a little more detail what you want to do.

---

### Post by MasterXandrex on 2007-07-26
"Without having to store a second copy" but thanks for playing.

Really what I was looking for was a software that would allow me to share files through a client-side initiated connection. Basically, like SFTP but once the connection was iniated on the client-side the server could browse (within limits of course).

Xan

---

### Post by p_quarles on 2007-07-26
It's not possible to do what your asking for without installing some kind of server software on what you're calling the "client" machine. The lowest profile way of doing this would be to install an ssh server on the Windows workstation. That way, you'll have access to everything on that machine. Sftp would work, too, and it's just a matter of setting up the folders you want access to as shared.

But in order to get remote access to the machine, it needs to be running a service. Which would make it a server.

---

### Post by Subnet on 2007-07-26
There is a graphical program for windows called winscp that will allow connect to your SSH server and allow you to copy files over. Here is a link to their website:[http://winscp.net/eng/index.php]("http://winscp.net/eng/index.php"). You should be able to connect from your Windows XP workstation to your home server and then view and copy files over. I have done this, and this is pretty slow over the net, so I hope you have a fast home and work connection. 

I hope that helps

Subnet

Edit:
Oh, by the way, you can also install OpenSSH on the Windows box and use nautilus/konqueror to view the files on the Windows system. You can find the Windows version of OpenSSH on the sourceforge website.

---

### Post by MasterXandrex on 2007-07-27
My original problem is that the files are being updated by others. While we rarely run into each other, I cannot simply copy, make changes over a period of hours or days and then come back and replace all the files. I installed an SFTP server on my server at home, I then established protected directories which I could sign into and write. I then simply used a program which would sync the files in the directories I needed with the share anytime a file was modified. I also used this program to Sync one small file every 15 minutes so as to keep the connection alive. While this solution does not work as directly as I hoped my solution would, it does accomplish my needs.

---

### Post by hggdh on 2007-07-27
It sounds like what you need is source code control, or similar (you state others will be updating the files, perhaps concurrently).

Look at [subversion]("http://subversion.tigris.org/") or [cvs]("http://www.nongnu.org/cvs/"), to name just two.

I think [SugarCRM]("http://www.sugarcrm.com/crm/") also had some sort of support for this, either native or via a plugin. Or, perhaps, WebDAV will do the trick for you.

YMMV. I humbly suggest you to carefully plan your security setup.

---

### Post by Biochem on 2007-07-27
I know that netdrive allows you to connect to ftp or webdav server as network drive (ie. W: )
[http://www.acs.uwosh.edu/novell/netdrive.htm](http://www.acs.uwosh.edu/novell/netdrive.htm)

Might be what you are looking for.

---

