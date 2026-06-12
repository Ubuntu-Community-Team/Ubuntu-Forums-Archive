---
title: "How to backup/copy an established Ubuntu server."
date: 2016-01-07
forum: Server Platforms
---

### Post by Ben_Fortune on 2016-01-07
Hello,

I first wanted to get a bit of a preamble out of the way  that may help anyone reading this post to ascertain my level of  knowledge/experience, prior to offering any advice.

Firstly, when  it comes to Ubuntu, (and particularly servers) I'm almost a complete  novice. I've previously run Lubuntu through a VirtualBox VM and utilize  Ubuntu at my Uni for basic/embedded programming in Java & C, and  simple scripting in Bash.

I've recently begun volunteering at the  local association for the blind near my university. I've been assisting  where I can with their electronic audiobook library. This primarily  involved ripping audiobooks from CD, reformatting them into Daisy/Epub  format, and uploading them into their already established server. I've  also written some simple scripts to convert their backups from .wav into  .flac using FFMPEG for storage's sake.

They maintain a local,  Ubuntu based, http server which clones itself nightly to an ISP's  server, that handles the actual hosting, using "Carbon Copy." There are  several scripts constantly running on the server (which I believe are  written in Ruby) as well as what I assume are an assortment of other  programs/packages installed on it. This was being managed by an on-site  technician until recently, but I believe due to budgeting concerns he  was unfortunately let go.

What I've been tasked with recently is  attempting to make a back-up/image of the server, one that we can  possibly port to different hardware. Ideally I want to, minus all the  audiobooks, have a backup of the system on a separate machine and be  able to put the system into maybe a VM to test the affects of minor  changes to the database, without putting the system at risk. My issue is  I've never attempted anything like this before, and with my limited  knowledge of Ubuntu, I don't know what's necessarily possible or where I  should start.

I'm sure there's a large amount of important  information I've neglected to mention in this post, but I'll be able to  have access the server within the next two hours to hopefully provide  any other information that may be needed.

Thanks,
Ben

---

### Post by MAFoElffen on 2016-01-08
I do with DD or Clonezilla. I used to do compressed images, but had a problem with one on a restore (besides it was taking longer to do) so now just do without compression. That and I used to do to tape ... but now to disk is not as expensive as it used to be and much faster.

---

### Post by nerdtron on 2016-01-10
To be able to migrate to another hardware/system, you can do a system rebuild and copy the data. It may take a more effort than just cloning but you'll learn how the system works during this process.

1. Make an inventory of all software/services running on the system: apache, ssh, mysql, php etc.
2. Make an inventory of all local user accounts on the server.
3. Make an inventory of the folders used by the software/services, also include the configuration files, folders like:
/var/www/html/*
/var/lib/mysql/*
/etc/*
4. Check the network settings of the server and look into UFW/iptables settings if there are any configured firewall settings.

After this, on the new ubuntu server:
1. Install the needed softwares
2. Copy the needed files/folders
3. Configured network/firewall settings (if any)
4. Create user accounts (if any)

The best way to transfer files to another server is using the "rsync" command. Or you can just archive the needed files, then transfer the files to the new server.
These steps may not be complete, and is time consuming, but at least you'll be familiar with the system and you will be able to rebuild it from scratch if you need to.

---

### Post by mastablasta on 2016-01-12
create image with clonezila. restore it in virtualbox: [http://jlorenzen.blogspot.gr/2010/07/restoring-clonezilla-image-using.html](http://jlorenzen.blogspot.gr/2010/07/restoring-clonezilla-image-using.html)

---

