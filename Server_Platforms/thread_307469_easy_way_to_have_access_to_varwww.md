---
title: "easy way to have access to /var/www"
date: 2006-11-26
forum: Server Platforms
---

### Post by meyrd on 2006-11-26
I ftp my files to my directory on the server. Then I ssh in to move the files to the /var/www directory. Then I have to chmod all the individual files and directories added so they can be viewed on the wan. Is there an easier way to get my website files to the /var/www directory and have them all accessable to the users who view them?

---

### Post by mark_g on 2006-11-26
Yes there is, you can use scp to copy the files using ssh.

---

### Post by meyrd on 2006-11-26
But I would still have to change the permissions after the files hit the /var/www directory.
I should add that sometime the files are created on a W$ machine.
I don't see how using scp or scp ssh would eliminate that much work....Am I missing something here?

---

### Post by autoexec on 2006-11-26
there is probably a way of chmod-ing the entire contents of a directory at once rather then doing each file

---

### Post by Peepsalot on 2006-11-27
> **autoexec said:**
> there is probably a way of chmod-ing the entire contents of a directory at once rather then doing each file
Yes, use the "-R" (for Recursive) option for chmod, and give it the directory path

I think using scp and chmod is not too hard you should be able to do the process with just two commands.  If you want to simplify it more, just write those commands into a bash script.  Voila, a single command to do whatever you want.

---

### Post by MJN on 2006-11-27
As you're using Windows, check out WinSCP ([www.winscp.net]("http://www.winscp.net")) - excellent tool for doing SCP/SFTP.
 
Mathew

---

### Post by piers on 2006-11-27
Whats wrong with allowing ftp access to /var/www ?

---

### Post by MJN on 2006-11-27
FTP for a start... ;)

---

### Post by meyrd on 2006-11-27
Thanks for the replies...

Peepsalot: should the command look like this using your suggestion?

chmod -R u+rwX,g-rwx,o-r /var/www

---

### Post by cjmartin on 2006-11-27
One thing that I do to get files online quickly (if they don't have to be in the root /var/www directory) is create a dir in my my home directory called web, then I soft link to it from the /var/www directory.

For instance, you could make a directory in your home called web:

mkdir ~/web

Then, in /var/www create a link to that dir called whatever you want:

sudo ln -s /home/<your user>/web/ /var/www/personal

Now, if you ftp in, you can simply put your files in your personal web directory and access them by going to:

[http://your-server.com/personal/file.html](http://your-server.com/personal/file.html)

This works for me, and if I need to move them later, at least I can access them in the mean time.

---

### Post by tturrisi on 2006-11-27
You can also set the apache root to /home/~/public_html, works good if you are the only user.

---

### Post by Peepsalot on 2006-11-27
> **meyrd said:**
> Thanks for the replies...

Peepsalot: should the command look like this using your suggestion?

chmod -R u+rwX,g-rwx,o-r /var/www
Well, I don't know because I'm not familiar with that sort of permissions notation.  The most common way I see it is with the 3 digit octal permissions.  [http://snap.nlc.dcccd.edu/learn/madden/intro/perms.html](http://snap.nlc.dcccd.edu/learn/madden/intro/perms.html)

---

### Post by MJN on 2006-11-28
I'd recommend checking out the following URLs as file permissions/notations are a useful (if not essential) concept to get your head around... and it will likely take a couple of reads for it to sink in.
 
[http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)
[http://en.wikipedia.org/wiki/File_system_permissions](http://en.wikipedia.org/wiki/File_system_permissions)
 
Mathew

---

### Post by Ride Jib on 2006-11-28
umask

[http://en.wikipedia.org/wiki/Umask](http://en.wikipedia.org/wiki/Umask)

---

