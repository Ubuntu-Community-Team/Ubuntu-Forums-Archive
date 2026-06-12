---
title: "Is WebDAV &quot;supposed&quot; to cache/buffer while moving a file?"
date: 2012-06-22
forum: Server Platforms
---

### Post by Roasted on 2012-06-22
I'm running several systems here. Laptop, desktop, server. All Ubuntu 12.04 64 bit. The server is running "OwnCloud" which is basically like Dropbox with additional functionality but on your own self hosted server. I noticed something about WebDAV and I'm trying to understand whether this is by design or if there's an actual issue elsewhere.

The question: Is WebDAV supposed to cache/buffer the file you're sending during transmission? 

Reasons I ask is this... I mounted the WebDAV server from Nautilus (which I assume utilizes .gvfs) and sent a 6.0GB file to my WebDAV server. It eventually tanked the connection as my RAM has maxed out (I have 8GB of RAM). Factor in the system and application RAM and you have the remaining ~2.0GB unaccounted for. I sent 8,000 pictures amounting to 30GB to the server via WebDAV in Nautilus and it worked great. But sending a single 6GB file is a different story. I assume the overhead of having to process file by file of the 8k files allowed the system to "let go" of memory quick enough that I never even saw an increase, whereas the single 6GB file being sent over gigabit LAN... different story. That's my assumption, at least.

I found [this bug here]("https://bugs.launchpad.net/ubuntu/+source/gnome-vfs2/+bug/42720") and thought, oh dang, it's a Nautilus/.gvfs bug. But then I installed davfs2 and mounted my WebDAV server on a local folder I created on root, named simply, /webdav. I used the following command:

> sudo mount.davfs -o file_mode=775,dir_mode=775,uid=jason [http://myserverurl.com/owncloud/files/webdav.php](http://myserverurl.com/owncloud/files/webdav.php) /webdav

I also duplicated the same steps but changing the mount point from /webdav to /home/jason/webdav. 

In both scenarios, it still eats up space on my root partition (I have root and home split), likely due to the /tmp directory (I'd have to guess, anyway) taking on the brunt of the caching.

So I guess this begs the obvious question. Is it normal for WebDAV to cache in any way? Is it expected behavior that Nautilus/.gvfs utilize system memory for transferring the files, or would that still be considered a definite bug?

---

### Post by Roasted on 2012-06-24
Well dang. Lookie here at the davfs man page:

> [INDENT]Caching

mount.davfs tries to reduce HTTP-trafic by caching and reusing data. **Information about directories and files are held in memory, while downloaded files are cached on disk.**

mount.davfs will consider cached information about directories and file attributes valid for a configurable time and look up this information on the server only after this time has expired (or there is other evidence that this information is stale). So if somebody else creates or deletes files on the server it may take some time before the local file system reflects this.[/INDENT]

I assume that WebDAV access via Nautilus is the same deal, but I couldn't find any confirmation on that.

---

