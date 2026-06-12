---
title: "Set up a share for one user"
date: 2011-10-12
forum: Server Platforms
---

### Post by DRouleau on 2011-10-12
11.04 Server
What I'd like to be able to do is "share" /var/www for myself only.  This way I can make changes to my intranet pages from my PC, vs having to make a change and save the file, then copy it and then see if it works.  Call me lazy but editing web pages with just a basic text editor from a terminal gets tedious after a while.  Or will doing this cause the pages not to display for other users?

---

### Post by DavidBeijer on 2011-10-12
Could you clarify your needs a bit? Do you mean setting up a samba share so that you can map /var/www as a drive on another PC?

---

### Post by DRouleau on 2011-10-12
That was the original goal, but I think I'll just stick with the moving files method.  Probably a better idea in the long run?

---

### Post by DavidBeijer on 2011-10-12
If by "moving files" you mean downloading a file through ftp, editing and then uploading again, yeah, that is a more secure method (in that sense that you will not add any samba vulnerabilities to your system). However, when your firewall is properly configured setting up a Samba share is not a real risk, and having such a share makes editing your website a lot easier, allowing you more time for actual developing instead of having to worry about the logistics all the time.

[Here]("http://www.ghacks.net/2009/09/04/set-up-your-new-ubuntu-server-as-a-samba-server/") you can find an excellent tutorial on how to set up a samba share that is also accessible from windows machines. If you don't fully understand there's a lot of information in this part of the forums. Just use the search feature with the problem you're facing and you should do fine. If you still cannot find it get back to this topic and I'll take a look at your problem. That is pretty much the way I learned it in the last couple of weeks: I'm also still a n00b, but it's actually very easy if you follow the advice given around here.

Good luck!

---

### Post by koenn on 2011-10-12
^ that looks like a good guide, and using 'security = user', requiring a linux account for users to access the shares, is indeed a good way of limiting the share to only yourself.

If other people have linux accounts on that server and you don't want to give theme share access, you can further fine-tune it using addtitional samba configuration.

---

### Post by Morbius1 on 2011-10-12
You can add the following line to the share definition to make it accessible only to one user. For example:
```
valid users = morbius
```BTW1: You might want to not rewite smb.conf from scratch as proposed by that HowTo as someone has actually put some thought as to how the default configuration should look. You can add his [SHARE-NAME] share definition to the end of it if you want.

BTW2: He uses the following syntax to start/stop/restart samba:
> *sudo /etc/init.d/samba restart*Um ... the "samba" service no longer exists and it's replacement "smbd" is no longer in init.d so the way it's done today is:
```
sudo service smbd start
sudo service smbd stop
sudo service smbd restart

```BTW3: And I'll admit I'm just being persnickety but you don't need to add and enable a user. The following command does both:
```
sudo smbpasswd -a pickles
```

---

### Post by drdos2006 on 2011-10-12
How I did it when setting up my web pages was to install nfs-kernel-server and nfs-common on the server.
I edited /etc/exports on the server to only allow my IP address

/var/www/cms 192.168.1.3(root_squash,async,rw,fsid=0)/// ** my IP address

Then I mounted that shared folder on my machine to edit the files from my machine.
mkdir /media/shared
sudo  mount   192.168.1.1:/var/www/cms   /media/shared /// ** server IP address

regards

---

### Post by DavidBeijer on 2011-10-13
Morbius1, you are off course right. I have picked up those little snippets of information from various posts here on the forum and perhaps some other tutorials online. I have found though that almost none of the other tutorials online cover setting up a share (in a secure way), most describe setting up a printer and how to give users access to their home folders and then call it a day. Others do describe setting up a share but forget to mention adding the samba user, etc.  

Is there one good tutorial that covers all the aspects mentioned in this thread in one single source of information? I myself know how it works by now, but if there is a better source I can refer people to that would be more helpful in the future...

---

### Post by DRouleau on 2011-10-13
You guys have lots of good ideas (I think that's why this forum is one of my favorites, the people are decent).  Currently on this server it's running a few things.  It's acting as a web server for our Intranet Site, mySql server for the site, using it as a file server (though not a primary one just holding a few things for all users) and as of yesterday a print server (long story but was fun getting it to work and it is so I'm happy).  
Basically this server is our "test" to see if when we upgrade our windows network to 2008 if we are going to run a Linux File Server or spend the money for yet another windows license.  It's a old Dell with Dual P3 1.3's (I think) with 2 GB of Memory so it's nothing great but it's working.  Actually in a test I did against our current file server it was only 1.4 seconds slower in writing 1,000,000 which I think is good considering.  Obviously the "production" server would be newer, probably one of our current Terminal Servers (Dual Xeon 3.2 Dual Cores with 8 GB, should be sufficient).  At that point I'll need to figure out how to set permissions for the shares based on the windows security.  I've found some articles on the subject and it looks promising.

---

