---
title: "Server help"
date: 2007-03-29
forum: Server Platforms
---

### Post by Doddsy on 2007-03-29
Hi guys, new member here! I'm looking for a bit of advice about a server I'm looking to setup. I've had a quick look through the forums and couldn't quite see what I needed. I'm a bit of a n00b to linux as well, so go easy on me (I've been using ubuntu about a week and I'm just getting a hang of sudo!)

Ok, I'll get to the point. I'm looking to set up a file server for at home. The server will be for my parents and myself with 2 desktops and a laptop all running XP.

 Ok to the questions; 

Would 6.10 server running samba be the best option? I've seen a couple of people recommend dapper instead. Would this be easy to configure? (I'm not great with the command line interface yet)

I'd be looking to have a few shared folders (DVDs, music etc) that we could all use as well as having private folders that only the individual could access (maybe password protected). Is this possible? Easy to do? 
For example: Main folder (maybe password protected)
                   --shared area with shared folders and password protected private folders
                    
Also would the interface from the users computers just be like going into a shared folders file on windows? Not sure my parents could manage any more complicated.

Thanks in advance for any help, I'm sure there will be more questions soon.

---

### Post by jakev383 on 2007-03-29
> **Doddsy said:**
> Hi guys, new member here! I'm looking for a bit of advice about a server I'm looking to setup. I've had a quick look through the forums and couldn't quite see what I needed. I'm a bit of a n00b to linux as well, so go easy on me (I've been using ubuntu about a week and I'm just getting a hang of sudo!)

Ok, I'll get to the point. I'm looking to set up a file server for at home. The server will be for my parents and myself with 2 desktops and a laptop all running XP.

 Ok to the questions; 

Would 6.10 server running samba be the best option? I've seen a couple of people recommend dapper instead. Would this be easy to configure? (I'm not great with the command line interface yet)

I'd be looking to have a few shared folders (DVDs, music etc) that we could all use as well as having private folders that only the individual could access (maybe password protected). Is this possible? Easy to do? 
For example: Main folder (maybe password protected)
                   --shared area with shared folders and password protected private folders
                    
Also would the interface from the users computers just be like going into a shared folders file on windows? Not sure my parents could manage any more complicated.

Thanks in advance for any help, I'm sure there will be more questions soon.

Any version should work. I can't comment on using the GUI to set it up, but I set up samba servers all the time (usually on CentOS). A simple share that allows everyone to read/write:

[HomeShare]
        comment = Home Share
        path = /rd0/home-share
        writeable = yes
        guest ok = yes
        read only = no
        public = yes
        hide dot files = yes
        follow symlinks = no
  
Change to fit your needs. A more robust one:

[HomeShare]
        comment = Home Share
        path = /rd0/home-share
        writeable = yes
        guest ok = yes
        read only = no
        public = yes
        hide dot files = yes
        follow symlinks = no
  vfs object = recycle
        recycle:repository = .deleted
        #recycle:keeptree = Yes # keeps the whole dir path when deleting files
        recycle:keeptree = no
        recycle:touch = Yes
        recycle:versions = Yes
        recycle:maxsixe = 0
        recycle:exclude = *.tmp
        recycle:exclude_dir = /tmp

That one will also have a "Recycle bin" like Windows called .deleted. I use this one for clients when I set up networks for them.
Hope that helps some!

---

### Post by Doddsy on 2007-03-30
Cool thanks, I'll give that a try.

---

