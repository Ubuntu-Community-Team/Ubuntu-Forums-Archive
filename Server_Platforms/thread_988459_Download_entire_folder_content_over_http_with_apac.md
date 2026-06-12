---
title: "Download entire folder content over http with apache?"
date: 2008-11-20
forum: Server Platforms
---

### Post by rslrdx on 2008-11-20
Hi, and TIA

I'm in a computer shop and I'm trying to figure out a way to download an entire folder content over http without the use of any software installed on the client pc accessing apache.  

I have a simple cms setup as my homepage and it contains links to a few tools that we use, this would just be an addition to that

I have lots of programs and drivers on a locally hosted box, and like to list the files, which I can do easily, but sometimes I need download the an entire folder, like some driver that is already unpacked/unzip on the server.

I dont see any reasons to use an FTP for this, as a user would have just as much work as accessing it via network path

How can I Download an entire folder content over http with apache without downloading files one by one?

Thanks,
Rodrigo.

---

### Post by Thirtysixway on 2008-11-20
You need to either setup ftp and get an ftp client (most operating systems come with one, even windows  start > run > ftp)  or zip the folder and download that, then extract it (which most linux systems can do and windows xp/vista can unzip without additional software)

Or you could use something like wget on a linux box...

---

### Post by JDiss on 2008-11-20
> **rslrdx said:**
> 
How can I Download an entire folder content over http with apache without downloading files one by one?


The short answer is you can't.  It's the reason why zip files are so ubiquitous and popular.

An alternative would be to have a page describing the file contents and offer a zip* file for download.

* or tar, rar, etc.

---

### Post by mbeach on 2008-11-20
you could probably write a php script (or other language) create a compressed version of the folder and make it available for subsequent download.  I'm sure someone out there has done just that.

I've been using sshfs to temporarily mount a remote folder for a similar purpose, but you would need to install it on the client, and have an ssh service running on your server.
[http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/](http://ubuntu.wordpress.com/2005/10/28/how-to-mount-a-remote-ssh-filesystem-using-sshfs/)

---

### Post by mbeach on 2008-11-20
potentially something you could use:
[http://www.web-development-blog.com/archives/tutorial-create-a-zip-file-from-folders-on-the-fly/](http://www.web-development-blog.com/archives/tutorial-create-a-zip-file-from-folders-on-the-fly/)

---

### Post by shanek on 2008-11-20
Have you checked out the Down Them All Firefox extension? I use it for this sort of thing all the time.

---

### Post by rslrdx on 2008-11-20
Hi, and thanks for the answers, I'll try to reply to options given so far right now the best i can.

@Thirtysixway:

Like I said, if I have to use ftp, samba will be far better, wouldn't even require the re-compression of the files just to decompress it

@mbeach

I already know of an php app for that, its call "php autoindex", but its kinda slow with the amount of files i have, and would eventually fall on the same problem I face with Thirtysixway suggestion, re-compress to decompress, samba is easier then.

@JDiss

Like I mentioned before on this answer, it re-compress to decompress

@shanek

I use a variety of browsers, and most of the time its IE6 or IE7, Firefox represents less then 2% of the work in the shop.


@Everyone

I knew this was a shot in the dark, and I thank you all for the answers, but they are not getting to close to what I like to achieve, but they would all get the job done in another way. For now I'll keep looking (googleling) and hoping for the best. just seems like there is a room for an app that can do that perhaps, given special purpose of course.

Thanks.

---

### Post by neRok on 2010-03-29
old thread, i am aware, but i wanted to do this same thing (download a whole directory from a web server) and found this page on google. i also found a solution so thought i would post it here.

wget can download recursively via http. you can use a command such as 'wget -r [http://site.com/folder](http://site.com/folder)'

---

### Post by jflaker on 2010-03-29
> **rslrdx said:**
> Hi, and TIA

I'm in a computer shop and I'm trying to figure out a way to download an entire folder content over http without the use of any software installed on the client pc accessing apache.  

I have a simple cms setup as my homepage and it contains links to a few tools that we use, this would just be an addition to that

I have lots of programs and drivers on a locally hosted box, and like to list the files, which I can do easily, but sometimes I need download the an entire folder, like some driver that is already unpacked/unzip on the server.

I dont see any reasons to use an FTP for this, as a user would have just as much work as accessing it via network path

How can I Download an entire folder content over http with apache without downloading files one by one?

Thanks,
Rodrigo.

Set up a cron job to zip (rar, tar.gz...pick a flavor) this folder nightly (or hourly depending on the amount of data to be zipped)....That job should replace the file each time...

Set up a link to that file which is static, but the contents will always be current.

---

