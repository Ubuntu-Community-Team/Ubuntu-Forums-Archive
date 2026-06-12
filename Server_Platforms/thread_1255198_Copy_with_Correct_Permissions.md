---
title: "Copy with Correct Permissions"
date: 2009-09-01
forum: Server Platforms
---

### Post by lazerradial2003 on 2009-09-01
Ok so I run an apache web server with WHM & CPanel installed. Each Account has it's own user and their public directory is /home/username/public_html.

Quite often I'll develop a site under one user and then need to transfer the site to the other one. I can do this by downloading all files via FTP and then uploading them to the new account but that seems silly when I have SSH access. 

The problem is I can't for the life of me work out how to copy a folder from one users home folder to the other in such a way that all the permissions from the origating user are applied to the copied files but for the new user. 

So say I copy from /home/user1/public_html/dev1 to /home/user5/livesite I need user5 to have all the permissions over the new files that user1 did originally.

Advice much appreciated!

---

### Post by slakkie on 2009-09-01
You can do it with tar, or scp -p (which perserves permissions and such).

---

### Post by terazen on 2009-09-01
You could just use chown I think.```
sudo chown -R user:group /directory/
```  That would change permissions on everything though, even maybe .htaccess or things that only root should have permissions to.

Or if you just want to change permissions on only html files you could do something like ```
sudo chown user:group `find /directory/ -name *.html`
```

---

### Post by apmcd47 on 2009-09-01
login as user5, then assuming the machine is called server:
[PHP]scp -rp user1@server:public_html/dev1 public_html/livesite[/PHP]

-p is for preserving permissions and -r is for recursive copies.

At least that seems to be what you are asking.

Andrew

---

### Post by lazerradial2003 on 2009-09-15
> **apmcd47 said:**
> login as user5, then assuming the machine is called server:
[PHP]scp -rp user1@server:public_html/dev1 public_html/livesite[/PHP]

-p is for preserving permissions and -r is for recursive copies.

At least that seems to be what you are asking.

Andrew

Many thanks for this, has saved me an enourmous amount of time. 

I ended up using: 

scp -rp user1@server:public_html/dev1/* public_html

to go from a subfolder on my test server to the public_html folder of the live site. 

Thanks again everyone

---

