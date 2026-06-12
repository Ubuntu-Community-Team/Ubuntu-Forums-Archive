---
title: "Newb trying to transfer a simple html doc to Ubuntu Server"
date: 2013-09-24
forum: Server Platforms
---

### Post by Fizzasist on 2013-09-24
Getting my feet wet with Ubuntu Server:
Installed it and am able to SSH into it. Can also see the Index page thru a browser on the network so I know that the server is working.
I created a simple html doc and am trying to transfer it to the server but am running into difficulties.
Using Filezilla and it will connect to server ok and show the directories but it wont let me transfer anything......just says "could not start transfer".
I assume this is a permissions thing but unsure where to go from here.
In Filezilla, the remote site box shows just a "/" and below it is empty. 
I think I need to transfer the html doc to the /var/www folder but can't seem to get to it thru filezilla.....
Any help or pointers would be really appreciated!
:)

---

### Post by Lars Noodén on 2013-09-24
If you are transferring to /var/www then you need to make sure that the file permissions are set so that you can write.  If you are the only user of that server, then it is enough to just take ownership of the directory and its files.

```

sudo chown -R fizzasist /var/www/

```

If you are sharing that server or directory with others then you will need to use group permissions instead.  Either way, it only needs to be done once to set things up.

About the SSH connection, you can also connect via the file manager.  In the file manager, press ctrl-L and then enter the URL

```

sftp://xx.yy.zz.aa/var/www/

```

Substitute the address of your server and the path to the actual directory that you will use.

---

### Post by Fizzasist on 2013-09-24
So right now the html doc is on an XP machine (path is F:\site---if that matters) and using filezilla I can see the doc on the left panel but the right panel doesn't show anything and I can't seem to get it to show the /var/www directory

---

### Post by CharlesA on 2013-09-24
Any error messages from filezilla? It should show your home directory at the very least.

---

### Post by Fizzasist on 2013-09-24
In the response/command dialog box it says "directory listing successful" but the only thing showing in the "remote site" box is a "/" and an empty directory below it. I can't seem to browse at all.....

---

### Post by Fizzasist on 2013-09-24
Oh I logged in anonymously.....I logged back in with the correct username and password and it's all good......Thanks!

---

### Post by Fizzasist on 2013-09-25
Ok so I can transfer the files now but when I do, they don't pull it in a browser on another machine....here is a screen shot of filezilla:

The "index.html" pulls up just fine but neither the "Intranet.html" nor the "TEST2.html" pull up......I get file not found....

---

### Post by nerdtron on 2013-09-25
If you get "file not found", then check your links in the html. There maybe some broken links/paths in your hyperlinks etc.

---

### Post by Fizzasist on 2013-09-25
I must be doing something wrong....I opened WORD and typed TEST and then saved it as a web page (single file) and called it TEST2.HTML, then I copied it into the same directory that has the INDEX.HTML file on the server---the page that WORKS---but when I try to open <server-ip>/TEST2.HTML it says it can't find it
??

---

### Post by Doug S on 2013-09-25
> **Fizzasist said:**
> I must be doing something wrong....I opened WORD and typed TEST and then saved it as a web page (single file) and called it TEST2.HTML, then I copied it into the same directory that has the INDEX.HTML file on the server---the page that WORKS---but when I try to open <server-ip>/TEST2.HTML it says it can't find it
??So, when you open <server-ip>/INDEX.HTML it works? Linux is case sensitive, is the file name actually test.html?

---

### Post by Fizzasist on 2013-09-26
Good point! I'll try that asap and let you know.....

---

### Post by Fizzasist on 2013-09-26
That looks like it might be part of the problem! If I try to pull up "test2" it comes up with NOT FOUND but "TEST2" comes up "Forbidden" so now it looks like a permissions issue......is there a way to set the permissions on the WWW directory for full control of it and all sub directories?

---

### Post by nerdtron on 2013-09-26
Change the permission and ownership of the /var/www/ folder and all its contents.
```
 chown -R username:groupname /var/www 
chmod -R 644 /var/www/*
```

---

### Post by Lars Noodén on 2013-09-27
Just a refinement on that: Directories need to be executable in order to look up file names and so on.

```

chown -R username:groupname /var/www 
find /var/www/ -type f -exec chmod 644 {} \;
find /var/www/ -type d -exec chmod 755 {} \;

```

The directories and regular files need slightly different permissions.

---

### Post by CharlesA on 2013-09-27
I like using chmod with the rX arguments so I don't do a blanket execute on everything.
[http://articles.slicehost.com/2010/7/17/using-chmod-part-1-symbolic-mode](http://articles.slicehost.com/2010/7/17/using-chmod-part-1-symbolic-mode)

```
chmod -R u=rwX,g=rX,o=rX /path/to/folder
```

---

### Post by Lars Noodén on 2013-09-27
> **CharlesA said:**
> I like using chmod with the rX arguments so I don't do a blanket execute on everything.
[http://articles.slicehost.com/2010/7/17/using-chmod-part-1-symbolic-mode](http://articles.slicehost.com/2010/7/17/using-chmod-part-1-symbolic-mode)

```
chmod -R u=rwX,g=rX,o=rX /path/to/folder
```

That's even better and simpler.  I wonder how many more times I'll have to see it before it soaks in. ;)  I may have to weaken the attachment to "find" first.

---

### Post by nerdtron on 2013-09-27
> **CharlesA said:**
> I like using chmod with the rX arguments so I don't do a blanket execute on everything.
[http://articles.slicehost.com/2010/7/17/using-chmod-part-1-symbolic-mode](http://articles.slicehost.com/2010/7/17/using-chmod-part-1-symbolic-mode)

```
chmod -R u=rwX,g=rX,o=rX /path/to/folder
```

All hail the master! :popcorn:

I learned something new. This will surely come in handy!

---

