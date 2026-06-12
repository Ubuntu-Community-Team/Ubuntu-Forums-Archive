---
title: "Quanta Plus - setting up file over network?"
date: 2008-07-10
forum: Ubuntu Studio
---

### Post by MicWit on 2008-07-10
Hi,

I have been using dreamweaver for quite a while, and am now getting into Ubuntu studio, so wanted another program to use. The way I had set up dreamweaver, was to map a network driver to a computer here I am running as a web server, and use the folder with the current website as the root folder for that dreamweaver project. Then I would set up the ftp details, so that when I have successfully coded (and tested on my local network), I would upload the changed files to the server.

Is it possible for me to do this with Quanta or any other software in Ubuntu? I presume I would need to link to smb://ip.address/shared_dir/project_root/ or something for the local files, but I cant see where to go to an smb share (in Quanta) or how to have local files as well as the option of upload to ftp. I have a shortcut on the desktop to the /www/ of my web server.

Any ideas? is this possible? cant see why it shouldnt be...

Thanks,
Michael

---

### Post by studiogrynn on 2009-01-15
Did you ever resolve this? I am looking to do this as well.

---

### Post by skullmunky on 2009-01-16
Have you looked at NFS?  It's really solid and not too hard to set up.  Say you have 2 machines on your local network, named "stagingserver" and "devbox".  Set up the NFS server on "stagingserver", and configure it to share whatever directory you need to (such as /var/www/).  

Then, on devbox, make a directory - can be anywhere, named just about anything - for example, /var/www-staging.  Make it different from /var/www, in any case.

Now set up devbox to automount stagingserver:/var/www onto /var/www-staging.  When you're on devbox, using Quanta or anything else, www-staging will look just like a normal directory.  

For the last part of this you want some way to batch upload everything from stagingserver to your production server.  rsync is a popular way to do that.  

that's an answer that's kind of short on details; docs and examples for NFS and rsync are pretty easy to find but let me know if you get stuck.

---

