---
title: "www-data and chown"
date: 2006-06-10
forum: Server Platforms
---

### Post by Randomskk on 2006-06-10
Hey all
I've got a PHP app which I need to be able to set the owner of a folder it copies from somewhere else.

The folder is a blank maildir folder, skel, and it resides in /home/vmail/skel.
My app needs to copy this folder to /home/vmail/<domain>/<username> and the new folder needs to have the same permissions.
The folder needs to be deleteable by www-data, but most importantly needs to be editable by vmail so email can be delivered.

I've tried using cp -p to preserve the permissions, and this works if I do the command as root or as vmail, but for some reason it doesn't work if I do the command as www-data.

I've tried copying the folder to a directory owned by www-data, but that makes no difference.
Also, if I take a file owned by www-data:www-data and try to chmod it, I get this:
chown: changing ownership of blabla: Operation not permitted

In short, it seems www-data simply cannot set the owner of any file to anything except itself.

Is this set somewhere, and can I change it?

---

### Post by LordHunter317 on 2006-06-10
That's correct. On Linux, you cannot give file/directory ownership away.

One option is to use ACLs and solve the problem that way.  Setting the correct ACL at /home/vmail will solve this problem, regardless of ownership.

Option two is to carefully write scripts to do this for you, and give www-data the ability to do it through sudo.

---

### Post by Randomskk on 2006-06-10
ACLs are probably the better idea, but how would I set one so that /home/vmail is entirely readable/editable by the vmail user, even when the folders belong to the www-data user and group?

---

### Post by LordHunter317 on 2006-06-10
Running:```
setfacl -R -m u:vmail:rwX,d:u:vmail:rwX /home/vmail
```Should do it.  You may also need to set a default ACL mask or default world permissions, depending on the exact behaviors you want.  Look at the setfacl(1) manpage, and post if you have questions.  But FWIW, the best way to figure out what will happen is just experiment and test it yourself. :)

---

### Post by Randomskk on 2006-06-10
Ok, I've apt'd the acl package and will read that man page tomorrow, but seems to be just the thing.

I found out while playing with the file permissions that directories need +x if you want to enter them - why's this?
If I have a few files that have permissions I don't want, could I set the folders to +x (say, 770) but set the files to just read/write? (say 660)?

I can't find any options in chmod to have -R only apply to folders.

---

### Post by LordHunter317 on 2006-06-10
[QUOTE=Randomskk]I found out while playing with the file permissions that directories need +x if you want to enter them - why's this?[/quote]'x' (bit 1) on a directory means access, that you can get to the files and directories inside of it (assuming you have read permission on the file in question).  'r' (bit 4) gives you the ability to read a directory, or run 'ls' and see what's inside.

Generally, that means you want '5' for read access to a dir and '7' for write access.  A situation where '1' is useful is for public_html in user directories.  By giving the world 'x' on /home/user, Apache can open the public_html directory but can't find out what's in /home/user.  It would have to guess.

[qote]If I have a few files that have permissions I don't want, could I set the folders to +x (say, 770) but set the files to just read/write? (say 660)?[/quote]Yes.

> I can't find any options in chmod to have -R only apply to folders.'X' (note the case) applies to only directories and files that have some executable bit set.  In some cases, you'll be forced to use find.

---

### Post by Randomskk on 2006-06-10
Ok, got it. The chmod +X works exactly as I need :)

As far as a public_html folder inside a /home/user folder, surely that doesn't matter if Apache is only serving up public_html, or would having that set be in case Apache was compromised?

---

### Post by LordHunter317 on 2006-06-10
It matters if Apache is compromised, or if it's running scripts for other users (generally a bad idea for that to happen, but whatever) and you don't want them to see your home directory contents.

---

### Post by LordHunter317 on 2006-06-10
Or far more simply, other people have shell accounts on the box and you don't want to let them see /home.

---

### Post by Randomskk on 2006-06-10
As far as user scripts go, if there's no CGI directory set on the virtual host and PHP's been given strict open_basedir instructions for each domain, I'd imagine apache couldn't do much about accessing the user files?

No one else has a shell account, but then again that's not something you want to risk anything on :P

Should chmod 660 -R /home/user; chmod +X -R /home/user; chmod g+X -R /home/user be enough to ensure that Apache can access the public HTML folder, but not the actual user data?

edit: assuming, of course, that the permissions on the public html folder were correctly set.

---

### Post by LordHunter317 on 2006-06-11
[QUOTE=Randomskk]As far as user scripts go, if there's no CGI directory set on the virtual host and PHP's been given strict open_basedir instructions for each domain, I'd imagine apache couldn't do much about accessing the user files?[/quote]No, it still could.  You ultimately can't trust any of PHP's security stuff: PHP modules aren't required to follow it, and some do not.

The only secure way to run PHP on a virtual hosting server is by giving every user a different account and using a tool like suphp.

> Should chmod 660 -R /home/user; chmod +X -R /home/user; chmod g+X -R /home/user be enough to ensure that Apache can access the public HTML folder, but not the actual user data?That's probably excessive.  I'd just say:```
chmod 751 /home/*
chmod 755 /home/*/public_html
```And get what you need.  The values on the other stuff is irrelevant, and we don't want to be presumptious about what the permissions are unless we have reason to do so.

---

### Post by Randomskk on 2006-06-11
[QUOTE=LordHunter317]No, it still could.  You ultimately can't trust any of PHP's security stuff: PHP modules aren't required to follow it, and some do not.

The only secure way to run PHP on a virtual hosting server is by giving every user a different account and using a tool like suphp.[/quote]
What kind of modules would get around the open_basedir directive?
I tried a PHP script that I ran under different virtual hosts to try and access other host's files, but it didn't work - and in the error logs, PHP reports open_basedir as stopping it, but I imagine you mean the modules such as GD, MySQL, etc.

suPHP looks fairly simple (in theory, at least) - with a setup where all the virtual hosts are in a www-users group with apache, using that could I set the files to user-readwrite, group-read and have Apache still be able to read the files, but the users also able to edit their own files via PHP?


> That's probably excessive.  I'd just say:```
chmod 751 /home/*
chmod 755 /home/*/public_html
```And get what you need.  The values on the other stuff is irrelevant, and we don't want to be presumptious about what the permissions are unless we have reason to do so.
Are the 1 and 5 bits for everyone at the end needed if Apache is in a group with the v-hosting users?

**Edit**:
Well, I tried out suPHP and while it seems to kinda work, it doesn't QUITE work - I can't seem to get MySQL enabled on it, for instance, and it can only take one docroot directive and as I use both /var/www and /home/domains/*/html I have to set that to /.
I looked around for open_basedir vulnerabilities, but could only find things that affect PHP 5.0.5 and below. What modules were you thinking of?

(on a somewhat unrelated note, in vsftpd, it tells me it's a bad idea to chroot local users - why is this? I'd have thought it would be more secure, and the vsftpd man page isn't very revealing)

---

### Post by LordHunter317 on 2006-06-11
[QUOTE=Randomskk]What kind of modules would get around the open_basedir directive?[/quote]The Oracle stuff can, for example.  Depending on database permissions, virtually any database engine might be a risk: most support some sort of copy for loading a file into/from the database.  If that's handled by the client instead of the server: boom, instant privilege bypass.

You can also workaround open_basedir with safe_mode off with some clever external command execution, IIRC.  

Also, the PHP team has a terribe track record w.r.t. security, I personally don't trust most of their security features very much.  They've been broken several times.

> suPHP looks fairly simple (in theory, at least) - with a setup where all the virtual hosts are in a www-users group with apache, using that could I set the files to user-readwrite, group-read and have Apache still be able to read the files, but the users also able to edit their own files via PHP?Yes, correct AFAIK.  Ultimately, apache needs reads access to static content and the PHP user needs read access to PHP content, and write access wherever necessary.  There are a bunch of ways of achieving this.


> Are the 1 and 5 bits for everyone at the end needed if Apache is in a group with the v-hosting users?No.  Normally, I grant Apache access through world permissions always.  If apache has group access, this isn't needed.  

> **Edit**:
Well, I tried out suPHP and while it seems to kinda work, it doesn't QUITE work - I can't seem to get MySQL enabled on it, for instance, and it can only take one docroot directive and as I use both /var/www and /home/domains/*/html I have to set that to /.You may be able to set that on a per-vhost basis, I don't know.  I haven't ever used it, I just know many people do.  There are a bunch of ways to secure PHP For multiple users, look around on the Internet.

> (on a somewhat unrelated note, in vsftpd, it tells me it's a bad idea to chroot local users - why is this?There's a possiblity of breaking out of the chroot jail, depending on how it's implemented.  IT is possible on modern Linux, if implemented correctly, to make this impossible, however.

---

