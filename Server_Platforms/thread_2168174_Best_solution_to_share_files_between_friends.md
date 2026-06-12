---
title: "Best solution to share files between friends?"
date: 2013-08-16
forum: Server Platforms
---

### Post by ConcreteDonkey on 2013-08-16
Hello,

I currently have a server running SSH, Samba and nginx. I have friends who often want to share files with each other and me, sometimes one file with multiple people (e.g. 10) as such it seems that using the server will be the best solution. But I'm wondering what would be the best way to do this? Would something like FTP be most useful and allow everyone to have an account?

Of course that would mean that each user would have to download an FTP client which would be undesirable. I'll appreciate any help you can give.

---

### Post by papibe on 2013-08-16
Hi badboy4life.

Since you have SSH installed and running, I would suggest the following tips for your friends:
[LIST]
[*]Running Ubuntu/Linux:
[LIST]
[*][*]Use Nautilus (file manager).
[*][*]Use the command line sftp.
[*][*]Install Filezilla.
[*][*]Install a Firefox's plug-in called FireFTP.
[/LIST]
[*]Windows:
[LIST]
[*][*]Install Filezilla.
[*][*]Install WinSCP.
[*][*]Install a Firefox's plug-in called FireFTP.
[/LIST]
[*]Mac:
[LIST]
[*][*]Install Filezilla.
[*][*]Use the command line sftp.
[*][*]Install Firefox and install FireFTP.
[*][*]Install another GUI client (see [here]("http://apple.stackexchange.com/questions/25661/whats-a-good-graphical-sftp-utility-for-os-x")).
[/LIST]
[/LIST]
I hope it helps. Let us know how it goes.
Regards.

EDIT: that list is not exhaustive. There may be more options.

---

### Post by Lars Noodén on 2013-08-16
I'd [avoid FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) and use SSH like papibe suggests above.   The two advantages of SSH in this case are that it is secure and it can be used over the Internet not just the LAN.  

To connect with Nautilus (or most any other file manager in Linux) press ctrl-L and then enter the URI for a folder on your server *sftp://xx.yy.zz.aa/home/badboy4life/* obviously substituting the ip number for your server.  

And to flesh out the list of applications for other systems, you can add [Cyberduck](http://cyberduck.ch/) to the list of Mac software.

---

### Post by ConcreteDonkey on 2013-08-16
The one problem is that my friends aren't so technically inclined as me and as such would prefer a simple solution, I was looking into something like "File Thingie" a PHP script that lets you upload to a folder and download since I already have nginx running. That way it would just be them pointing their browser at example.com/share and getting or uploading the files they need. I have an SSL cert so I assume that the .htaccess logins are secure?

One thing I am worried about is the security of services like File Thingie and other PHP scripts, does anyone have an alternative PHP script or maybe a simple solution for my less technically inclined friends?

---

### Post by papibe on 2013-08-16
I see.

You may want to take a look at [Meiga]("http://meiga.igalia.com/"). Here's a [video]("http://www.youtube.com/watch?v=V8nS_otVivw&feature=youtu.be&t=49m14s") tutorial.

Regards.

---

### Post by Lars Noodén on 2013-08-17
If your friends are not so technically inclined then SFTP is the way to go using the graphical clients.  They are very easy to connect, especially the using the file manager, and once connected are drag and drop.  And it is about as secure as you can get.  What Linux distro are they running?

---

### Post by Rebajas on 2013-08-17
Dropbox allows you to share folders with others? Might be an easier solution once everyone has it set up.

---

### Post by papibe on 2013-08-20
Another alternative would be to use [Woof]("http://www.home.unix-ag.org/simon/woof.html"). Here's the related [video]("http://www.youtube.com/watch?v=faR4NiSGbtg&feature=youtu.be&t=8m7s") tutorial.

Regards.

---

