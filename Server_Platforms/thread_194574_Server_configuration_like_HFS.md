---
title: "Server configuration like HFS"
date: 2006-06-11
forum: Server Platforms
---

### Post by the ev on 2006-06-11
Hey, I think this is an appropriate place to ask this question...

So I have a Win2k3 Server system that I'd like to swtich to Ubuntu 6 Server, but I hesitate because of this neat little program I just found for Windows called HFS (Http File Server), which creates a local webserver/webspace that actively reflects the directory structure of a share.  The basic idea is using a web browser to browse through shares rather than, say, going through Samba or Windows Networking.

Why would I want to do this? Well, while Samba/Windows Networking is definitely faster for local transfers, it tends to be slower across greater distances.  I've networked all my computers via Hamachi ([www.hamachi.cc)](www.hamachi.cc)), and the HFS program for Windows seems to be faster through Hamachi at file servering than Samba/Windows Networking.

Anyhow, my question: I know that there is no Linux port of the literal HFS program, but would it be terribly difficult to setup my own make-shift server in the same fashion?  Or is there a Linux-equivalent program that I'm not aware of that might do the trick?  I'd like to have whatever solution automatically reflect the changes made on the shares on the website, rather than manually updating the server, if you catch my drift.  You can find the HFS program here: [http://www.rejetto.com/hfs]("http://www.rejetto.com/hfs")

Any thoughts, suggestions, comments would be much appreciated! Thanks.

---

### Post by LordHunter317 on 2006-06-11
I dont' see why serving the shares out of Apache wouldn't work.

---

### Post by the ev on 2006-06-11
My experience (however limited) with Apache is that you would serve an HTML document, like any other HTTP server.  How would I be able to just serve the shares?

---

### Post by LordHunter317 on 2006-06-11
Add aliases for the various directories to map them in to the web VFS.  If you turn on indexes for the directories, Apache will serve HTML index listings automatically.  Users can click on the files and download them.

---

### Post by the ev on 2006-06-12
Sweet.  I'll give that a try.  Thanks!

---

