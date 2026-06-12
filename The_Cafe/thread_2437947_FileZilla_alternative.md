---
title: "FileZilla alternative"
date: 2020-03-03
forum: The Cafe
---

### Post by satimis on 2020-03-03
Hi all,

I have been running FileZilla sometimes to work on WordPress websites remotely.  I have about 40 websites running on Godaddy server.  It is very convenient.  All my websites are in the public_html folder.  But the only disadvantage is in some case and for unknown cause/reason a website will be automatically moved into another website while working on FileZilla without my notice.  Until I couldn't browse it with 403 warning popup.

Can any folk give me some advice how to avoid this incident?  Or is there a better tool to replace FileZilla ?

Thanks in advance.

Regards
satimis

---

### Post by sdsurfer on 2020-03-03
I have never had that happen. I have had issues with FZ on Windows (sporadic timeouts, connect failures, slowness, all sorts,) and their support staff is very brusque and not all that ""supportive." But it seems to work great in Ubuntu.

Are you absolutely positively sure it was not user error, late night work and not where you thought you were? It happens.

The second thing is are you using a single window or tabs/multiple windows to access? It's really easy to get them confused, work in a single window.

Are you accessing each site individually, or as root or a "superuser" and can see a whole directory of domains when you log in?

If you are accessing as a superuser, this is a bad idea in respect to security. Even when using SFTP or SSH keys for your login, it is still not all that secure. One intercepted transmission can mean all your domains are hacked, not just one.

Use the domain login for each domain and access them individually. It may be tedious, but far safer. It also means you always know exactly where you are and don't accidentally copy files for site A into site B.

Even if you aren't accessing them all from one login, or are, you can avoid putting the wrong site into the wrong place if you enable and always use Synchronized Browsing (It's on the main menu and tool bar in FileZilla.) When you change directory on either remote or local, the opposite changes with you, so you are always in the same place on both ends.

There are tons of FTP clients out there, I've played a bit with them but don't find any superior or inferior to FileZilla. They all move files left to right and back, support the necessary protocols, have usable GUI's, as FTP clients go FileZilla is fairly robust.

---

### Post by TheFu on 2020-03-03
Use **sftp** from the command line once **ssh** works, if needed.  
Once ssh is enabled, you can mount remote storage using sshfs, authenticated via ssh-key and every file manager in Linux support a URL like sftp://domain.com/.  scp, sftp, rsync, ssh, all work.  Vim can remotely edit files using an rsync:// URL too.

If you need alternate port support, use a ~/.ssh/config file.  They are really, really, easy.  Pretty much the easiest config file on any Unix system.

Don't avoid ssh. Embrace it.

---

### Post by satimis on 2020-03-04
> **sdsurfer said:**
> I have never had that happen. I have had issues with FZ on Windows (sporadic timeouts, connect failures, slowness, all sorts,) and their support staff is very brusque and not all that ""supportive." But it seems to work great in Ubuntu.

Are you absolutely positively sure it was not user error, late night work and not where you thought you were? It happens.
Thanks for your advice.

No.  I have been using FileZilla for more than 10 years.  Such an accident has happened before.  Its disadvantage is once login on my Godaddy account, it connecting/displaying all my websites on Godaddy server under "/public_htlm/" folder.

This incident happened yesterday when I was working on a newly created website, say aaa.bbb.com, an subdomain website.  Suddenly I found a folder, say "xxx" with contents, on it.  "xxx" is the folder of xxx.yyy.com, another subdomain website, having been running on Godaddy server for years.  "xxx" is under "public_html" main folder.  "bbb.com" and "yyy.com" mentioned above are 2 different domains.

While working I haven't touched "xxx".  Then I couldn't browse xxx.yyy.com on Internet with warning "403" popup.  I download the folder "xxx" to my PC, with drag-n-drop from the right-bottom box of FileZilla to the left-bottom box.  I found all content of xxx.yyy.com being there.

Then I created a new "xxx" folder on "/public_html/" and upload all contents of "xxx" on my PC to the newly created folder "xxx".  Thereafter I can browse xxx.yyy.com on Internet but the rotating head-images of the website were not clear and the background music also not clear.  Then I deleted all images on "Cimy Head-Images Rotator", a plugin of WordPress, and upload all images there again.  Now the rotating head-images are now clear.

Regarding to the background music I couldn't solve the problem even deleting its file on /public_html/xxx/wp-content/upload/xxx_upload_folder/ and upload a new file there again.  The background music is still unclear.  That is the present situation.

> 
The second thing is are you using a single window or tabs/multiple windows to access? It's really easy to get them confused, work in a single window.

Sorry I'm not very clear of your question.  On starting FileZilla there is ONLY one window displayed.  I haven't created multiple FileZilla windows on the monitor/display.

> 
Are you accessing each site individually, or as root or a "superuser" and can see a whole directory of domains when you log in?

Yes after login I can see all my websites on /public_html/ folder.  That is the disadvantage of FileZilla.

Other advice noted and thanks.

Just found;
WordPress File Manager Plugin Tutorial 2019
[https://www.youtube.com/watch?v=6MzLVagZLy4](https://www.youtube.com/watch?v=6MzLVagZLy4)

File Manager &#8211; WordPress plugin | WordPress.org
[https://wordpress.org/plugins/wp-file-manager/](https://wordpress.org/plugins/wp-file-manager/)

6+ Best File Manager WordPress Plugins 2020 (Free and Paid)
[https://www.formget.com/file-manager-wordpress-plugins/](https://www.formget.com/file-manager-wordpress-plugins/)
7. File Manager Plugin For WordPress
8. File Manager Advanced Wordpress Plugins
are FREE to use

I suppose 7. and 8. above suitable to me.  They only work on that particular login website not connecting my other websites on Godaddy server, like FileZilla.

I will go through the documents and video before trying them.

Thanks

Regards
satimis

---

### Post by satimis on 2020-03-04
> **TheFu said:**
> Use **sftp** from the command line once **ssh** works, if needed.  
Once ssh is enabled, you can mount remote storage using sshfs, authenticated via ssh-key and every file manager in Linux support a URL like sftp://domain.com/.  scp, sftp, rsync, ssh, all work.  Vim can remotely edit files using an rsync:// URL too.

If you need alternate port support, use a ~/.ssh/config file.  They are really, really, easy.  Pretty much the easiest config file on any Unix system.

Don't avoid ssh. Embrace it.
Hi,

Your advice noted and thanks

Regards
satimis

---

### Post by sdsurfer on 2020-03-04
satimis considering all, I still think Syncronized Browsing is a good habit to form. That is really odd, I don't think it's a GoDaddy issue, and have no explanation for it. I could swear FileZilla allowed you to open multiple tabs, but the point is moot if you're working in one.

---

### Post by SeijiSensei on 2020-03-04
I just use the regular file manager in KDE, Dolphin, to communicate with my remote sites.  I'll split my screen between a local directory and a remote window. If I use a fish:// or sftp:// URL as the address for the remote, I can move files back and forth just by dragging-and-dropping.  Of course, I maintain my sites on a Linode instance so I have full control over both ends of the connection. Indeed I communicate with the remote over an OpenVPN tunnel. I have no idea how applicable this is to a provider like GoDaddy.

---

### Post by satimis on 2020-03-04
> **sdsurfer said:**
>  - snip -
satimis considering all, I still think Syncronized Browsing is a good habit to form. That is really odd, I don't think it's a GoDaddy issue, and have no explanation for it. I could swear FileZilla allowed you to open multiple tabs, but the point is moot if you're working in one.
Hi sdsurfer,

Whether you meant synchronized browsing with FileZilla ?

similar to following link;
How to Synchronize With FileZilla
[https://smallbusiness.chron.com/synchronize-filezilla-47982.html](https://smallbusiness.chron.com/synchronize-filezilla-47982.html)

I suppose I'm using synchronized browsing with FileZilla.  But I couldn't remember exactly because I have been running FileZilla to connect Godaddy server for about 10 years.  All corresponding data for login have been saved on FileZilla.  I just select "user@host_ip_address" under [Quickconnect] 

"Enter master password" window will popup```

Please enter your master password to decrypt the password for this server:

Host: my IP address on Godaddy server (already printed there)
User: aaaaaa (already printed there)
Key identifier: bbbbbb (already printed there)
Master Password [      ]
(check) Remember master password until FileZilla is closed
[OK] [Cancel]

```
Just entering my Master Password --> click [OK].  Then I can connect Godaddy server browsing all content of my websites.

I doubt whether there is any mistake on Godaddy server.  About 4~5 days ago for an unknown reason I couldn't browse one of my websites with warning "404" displayed.  Then I connected Godady support here by phone, reporting my problem.  A technician, answering my call, after checking told me that the cause was unknown and she has to contact USA headquarter, asking me to wait on phone.  After waiting about 15~20 min. she told me that the DNS of that website has been changed.  In response I told her that I haven't touched anything on that website for at least 5~6 months.  Then she made a change on its DNS and and asked me waiting for 24hrs before it can be browsed.

I have been using Godaddy service for more than 10 years.  In the past there was no problem.  Ever since they moved their servers to Singapore about 4 years ago, serving the customers in Asia then problem occurs periodically.

I think I'll try "File Manager Plugin" on WordPress for managing a particular website, avoiding confusing with my other websites.

Regards
satimis

---

### Post by satimis on 2020-03-04
> **SeijiSensei said:**
> I just use the regular file manager in KDE, Dolphin, to communicate with my remote sites.  I'll split my screen between a local directory and a remote window. If I use a fish:// or sftp:// URL as the address for the remote, I can move files back and forth just by dragging-and-dropping.  Of course, I maintain my sites on a Linode instance so I have full control over both ends of the connection. Indeed I communicate with the remote over an OpenVPN tunnel. I have no idea how applicable this is to a provider like GoDaddy.
Hi SeijiSensei,

Thanks for your further advice.
 
The screen between a local directory and remote window already be split on FileZilla window.  Also I can use drag-and-drop moving all data.  Usually to correct data on a file of my website, I'll perform following steps;```

1. drop a copy of the file "aaa" on my local PC.
2. make any change on the file.
3. rename the old file on Godaddy server as aaa.old
4. upload the amended file to Godaddy server

```
It works without problem.

Instead of running FileZilla on a secured tunnel I'll try "File Manager Plugin" of WordPress to manage my website direct on Godaddy server.

Regards
satimis

---

### Post by sdsurfer on 2020-03-04
> **satimis said:**
> Whether you meant synchronized browsing with FileZilla ?

Edit: AGH! None of my images ever load on this forum!

Open a connection to your server and mouse over the top icons, at the right you should see "Toggle Synchronized Browsing." When it is enabled, and you change directory on one side, it changes the directory on the other side automatically. That way the directory  you are in on your server is the same directory as locally.

---

### Post by TheFu on 2020-03-04
> **sdsurfer said:**
>  
Edit: AGH! None of my images ever load on this forum!

Create an album.  Upload the image there.  Link to the image.
Please do not post large images in-line.  People use their cell phones and some of us pay by the byte.  Actually, it would be helpful if you edited your post and removed whatever image it has.  The size is still there, wasting bandwidth.
Please.

---

### Post by satimis on 2020-03-04
> **sdsurfer said:**
>  - delete -
Edit: AGH! None of my images ever load on this forum!

Open a connection to your server and mouse over the top icons, at the right you should see "Toggle Synchronized Browsing." When it is enabled, and you change directory on one side, it changes the directory on the other side automatically. That way the directory  you are in on your server is the same directory as locally.
Recently neither I can attach image file to this forum.  I don't know why?

I couldn't find "Synchronized Browsing" on my FileZilla which was installed on Ubuntu "repo"

On left top-menu
View -> "Synchronized Browsing" (grey out)

FileZilla Ftp - Directory comparision and Synchronized browsing
[https://www.youtube.com/watch?v=ascPaq76tDs](https://www.youtube.com/watch?v=ascPaq76tDs)

$ apt policy filezilla```

filezilla:
  Installed: 3.28.0-1
  Candidate: 3.28.0-1
  Version table:
 *** 3.28.0-1 500
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        100 /var/lib/dpkg/status

```

I must download and install the latest version FileZilla-3.47.1.  Now I have the package download.

According to the NOTE on following article;
How can I upgrade filezilla to the current version?
[https://askubuntu.com/questions/1000269/how-can-i-upgrade-filezilla-to-the-current-version](https://askubuntu.com/questions/1000269/how-can-i-upgrade-filezilla-to-the-current-version)
```

The newest precompiled version of Filezilla is now 3.46.3 which was built for Debian 10.0 (Buster). If you are running Ubuntu 18.04 LTS or older, the libc6 library does not contain GLIBC 2.28 which is now required by the precompiled version of Filezilla 3.46.3. ....

```

glibc-2.28 is required for installation but it is not on Ubuntu "repo".  glibc-source is on "repo"

$ apt policy glibc-source```

glibc-source:
  Installed: (none)
  Candidate: 2.27-3ubuntu1
  Version table:
     2.27-3ubuntu1 500
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages
        500 http://hk.archive.ubuntu.com/ubuntu bionic/universe i386 Packages

```

Can I use glibc-source instead ?

Thank

Regards
satimis

---

### Post by coffeecat on 2020-03-05
> **sdsurfer said:**
> 
Edit: AGH! None of my images ever load on this forum!

@sdsurfer, please do not drag and drop images into the message editor. That will never work - it never has with vbulletin. I had to wade through a mass of base64 code in your post above. If you drag and drop images into the message editor, either the forum software or the browser converts it into base64 code. It used to be that this was then displayed - masses of it - causing immeasurable problems. Now you see nothing, but it is there, clogging up the database and causing problems if someone wants to quote your post. 

Use the forum attachment facility for images - either the paperclip icon in the message editor toolbar, or the "manage attachment" button below the advanced message editor. That way the forum software creates a clickable thumbnail.

> **satimis said:**
> Recently neither I can attach image file to this forum.  I don't know why?


@satimis, perhaps if you post in forum feedback and help with details of the problem you are experiencing with the attachment facility, one of us might be able to help. There are file size limits, but other than that it should be working.

---

### Post by sdsurfer on 2020-03-05
I tried both methods, the second was a last resort.

---

