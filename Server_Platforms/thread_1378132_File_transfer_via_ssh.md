---
title: "File transfer via ssh?"
date: 2010-01-11
forum: Server Platforms
---

### Post by humphreybc on 2010-01-11
I have my server set up with AjaXplorer but there is a bug in the flash uploader that doesn't let you upload anything to the server.

The only way I can update any files or add new ones is to physically plug in an external hard drive or USB drive and transfer them.

I have openssh access and that's all set up, but can I transfer files somehow from my laptop to my server using like a cp command?

---

### Post by munky99999 on 2010-01-11
```
man scp
```

---

### Post by humphreybc on 2010-01-11
Perfect!

---

### Post by SecretCode on 2010-01-11
Or rsync or sftp or sshfs :)

eta: Where rsync is really worth looking at

---

### Post by Lars Noodén on 2010-01-11
If you're just getting started with file transfer, then there are a lot of reasons to get used to sftp over scp.  You can even use a fairly similar syntax.

Or, if you are comfortable with graphical interfaces, you can use the built-in sftp clients found in Filezilla,  Konqueror, Dolphin, Nautilus, Cyberduck, Fugu, or Fetch.  For those, enter a URL with the address and, optionally, the directory on the server:

sftp://server.example.org/some/directory/

---

### Post by humphreybc on 2010-01-23
Of course, I completely overlooked "Connect to Server" under the Places menu... idiot.

I even managed to get it auto-mounting and added to my bookmarks just by ticking a box. Man, that was sooo much easier than I was expecting!

But here's another question to test ya'll - Is there a way (like Ubuntu One/DropBox) for me to "sync" folders on my computer and the server?

ie. I have thousands of images, because I'm a part-time photographer. I'm always adding images to my /media/media/Photos directory. I'd like to be able to have this synced with the server, so that whenever something changes on my laptop, it will automatically be reflected on the server.

A bit of a "local dropbox" if you will. Of course the best thing would be to just have my entire laptop "synced" with my server - that way absolutely everything remains backed up and 100% current.

---

### Post by Lars Noodén on 2010-01-23
> **humphreybc said:**
> ...
But here's another question to test ya'll - Is there a way ... for me to "sync" folders on my computer and the server?

ie. I have thousands of images, because I'm a part-time photographer. I'm always adding images to my /media/media/Photos directory. I'd like to be able to have this synced with the server, so that whenever something changes on my laptop, it will automatically be reflected on the server.

A bit of a "local dropbox" if you will. Of course the best thing would be to just have my entire laptop "synced" with my server - that way absolutely everything remains backed up and 100% current.

@ SecretCode mentioned [rsync](http://manpages.ubuntu.com/manpages/karmic/en/man1/rsync.1.html) and that will be the most efficient way to update a second machine.    It works best if you always go the same direction, updating from one machine to the other.  To use it properly, you run it over SSH.

Once you have rsync over ssh configure the way you like it, you can save it as a script and then run that script from the shell or make a 'clickable' icon of it.   

```

# something approx like this might work
rsync -a -e "ssh -t -l humphreybc" \
   /media/Photos/  \
   *theothermachine*/media/Photos/

```

For **rsync** there are additional options like **--delete** which can be use to remove files from the destination if they no longer exist on the source.  

If you sync several times during the same session and want to avoid re-typing the password, then set up key-based authentication for SSH and use ssh-agent and ssh-add to load the key and the key's passphrase into memory.

---

### Post by humphreybc on 2010-01-23
So... for:

Username on server: benjamin
Location of Media on laptop: /media/Media
Location of Media on server: /data/media
Server IP: 192.168.1.2

Would this work?

```

# Syncs Photos, Music, Movies and TV Shows
rsync -a -e "ssh -t -l benjamin" \
   /media/Media  \
   sftp://192.168.1.2/data/media

```

Also, at the moment I don't keep any Movies or TV Shows on my laptop, however there are hundreds on the server. When I run this, it won't delete what's on the server, right?

I don't want it to delete anything... ie say:

I create file1, sync it, delete file1 from my laptop - I want it to still remain on the server. So it's a total backup.

I need to buy another hard drive for my server, and then I will have enough space to run a sync of my home directory too.

---

### Post by gombadi on 2010-01-23
> 
```

# Syncs Photos, Music, Movies and TV Shows
rsync -a -e "ssh -t -l benjamin" \
   /media/Media  \
   sftp://192.168.1.2/data/media


```


Or 
```

rsync -avz -e ssh /media/Media/ benjamin@192.168.1.2:/data/media

```
Note the trailing / at the end of /media/Media - Trailing / are very important with rsync. The -v is optional.

> 
I create file1, sync it, delete file1 from my laptop - I want it to still remain on the server. So it's a total backup.


Correct. You can use --delete if you want to delete files from the destination that are no longer present at the source.

---

### Post by chuina on 2010-01-24
If your server has a ftp server (vsftpd) configured
and you have an access via ftp, then try with gftp.

```
sudo apt-get install gftp
```

Applications->Internet->gftp

You are a photographer. using gftp for upload/download
is more user-friendly than rsync (at least in my case).
After log in only mouse click is needed.

thnx.

---

### Post by Adina on 2010-01-25
Krusader is my favourite tool for file transfer.

```
sudo apt-get install krusader
```

It's commander style and has all the features you need for this. Very much recommended.

---

