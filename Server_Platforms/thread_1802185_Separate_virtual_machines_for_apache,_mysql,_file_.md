---
title: "Separate virtual machines for apache, mysql, file server"
date: 2011-07-11
forum: Server Platforms
---

### Post by wenkep3 on 2011-07-11
I'm working on a side project where I would like to install three ubuntu server systems, each with only one task.  So server0 would be the apache server, server1 would be the database and server2 would be the file server.  Can anyone point me in the right direction of which key terms I should be researching?  Thanks,   Paul

---

### Post by CharlesA on 2011-07-11
Running apache and mysql is going to be easy. As for the file server, are you going to be sharing with windows clients?

See [here]("https://help.ubuntu.com/community/ApacheMySQLPHP") on how to install a lamp server on one box, it'll give you an idea of how you want to proceed.

---

### Post by karlson on 2011-07-11
> **wenkep3 said:**
> I'm working on a side project where I would like to install three ubuntu server systems, each with only one task.  So server0 would be the apache server, server1 would be the database and server2 would be the file server.  Can anyone point me in the right direction of which key terms I should be researching?  Thanks,   Paul

Any reason why you want to do this in 3 virtual machines?  If you want to emulate 3 different network connections there are simpler ways of doing it.

---

### Post by wenkep3 on 2011-07-11
Thanks for the quick response.  I've very familiar with installing lamp on a single system, but I'm not sure how the configuration will change with these three systems separated.  I'm hoping the term "file server" isn't misleading.  I want the actual website files to be separate from apache and the database.  Here's a little outline of what I mean,  I believe this method is possible.  Http request sent to server0 (apache) Apache then sends a request to server1 (file server) If necessary, server1 sends a request to server2 (db server) Then everything gets sent back to server0, then to the client

---

### Post by CharlesA on 2011-07-11
That sounds a bit complicated..

You could always store the files on the "file server" and have that directory mounted via NFS on the apache server.

The db server would be a totally different animal tho.

---

### Post by wenkep3 on 2011-07-11
That sounds like something I'll want to do.  Is it a big deal to call the database from apache?

---

### Post by CharlesA on 2011-07-11
> **wenkep3 said:**
> That sounds like something I'll want to do.  Is it a big deal to call the database from apache?

I don't think so. If you set up something that needs access to a db, you can usually point it to the db server.

---

### Post by kgatan on 2011-07-12
Dont think any applications require you to run sql on localhost.

If remeber correctly mysql is setup as default to only accept connections from localhost.
I dont remeber the command to change this but ive done it before to allow odbc connections and it was no problem.

---

### Post by capt.primetime on 2011-07-12
[http://en.wikipedia.org/wiki/Linux-VServer](http://en.wikipedia.org/wiki/Linux-VServer)

take a look at this. Its basically jailing sytem. To each of your servers you can give separate IP.

---

### Post by wenkep3 on 2011-07-12
Thanks for all the information.  This is my current setup, I have three virtual machines, server0 with just apache, server1 as a file server, and server2 as the database.  I'm looking to change the owner of the public_html folder and all its contents on server1 to www-data on server0.  I know I'm going to get an invalid user when I try this, so should I set up a remote user account or something along those lines?

---

### Post by wenkep3 on 2011-07-12
Another thing, is there a way I can configure apache's file (from sites-available) to look at the file server's folder.  I'm guessing I could put in the ip, but is there a way I could put a static address?

---

### Post by kgatan on 2011-07-12
You mount the folder from server 1 on server 0 and set document root in the sites file to the mounted folder.

---

### Post by wenkep3 on 2011-07-13
I've mounted it and pointed to the folder.  Right now I'm getting a forbidden message in firefox.  I've set the correct file permissions where the actual files are located.  So I need to change the permissions of mnt/server1 or anything like that?

---

### Post by karlson on 2011-07-13
> **wenkep3 said:**
> I've mounted it and pointed to the folder.  Right now I'm getting a forbidden message in firefox.  I've set the correct file permissions where the actual files are located.  So I need to change the permissions of mnt/server1 or anything like that?

What permissions does you web server host see?  Can you access the files through a shell?

---

### Post by wenkep3 on 2011-07-13
mnt/server1 is set to www-data with 731.  I can ssh into server1 from server0.

---

### Post by CharlesA on 2011-07-13
> **wenkep3 said:**
> mnt/server1 is set to www-data with 731.  I can ssh into server1 from server0.

Those permissions don't look right.

4 = read
2 = write
1 = execute

Should be either 750 or 755 for folders and 640 or 644 for files - with you as owner and www-data in a separate group.

---

### Post by wenkep3 on 2011-07-13
I'm still getting a forbidden error. I don't see anything wrong, so I'll just list everything.  I know 777 shouldn't be, but I'm just trying to get everything working first.  #Server0 (apache)   #Sites-available file     points to /home/paul/public_html   #/mnt/remoteDir     root:www-data     731   #public_html     755     #pointer to mnt/remoteDir       777  #Server1 (file)   #public_html     755   #index.php     644

---

### Post by wenkep3 on 2011-07-13
I'm almost done, I figured out the forbidden error, but when I go to its ip in firefox it doesn't execute index.php I wants to save/open the file?

---

### Post by wenkep3 on 2011-07-13
Got everything working, thanks for all the help.  One last question, apache2's default username is www-data, is it a standard practice to change the name to something else?

---

### Post by CharlesA on 2011-07-13
> **wenkep3 said:**
> Got everything working, thanks for all the help.  One last question, apache2's default username is www-data, is it a standard practice to change the name to something else?

That's the user the daemon runs under. In practice, it should only be given read access tho.

---

### Post by capt.primetime on 2011-07-15
How did you resolved your problems with permissions and index files. Just curious?

---

