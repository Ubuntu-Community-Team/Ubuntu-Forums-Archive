---
title: "Quick Syntax Question"
date: 2009-07-10
forum: Server Platforms
---

### Post by Thaumaturge Jay on 2009-07-10
Ok, I have directories Mark, Rick & Mike within a directory called FTP which is in the user "Macroom"s home directory which is in my home directory (I'm Jason).

Mark, Rick & Mike are users who only have access to their respective directories.  I have myself (Jason) and one other user (Macroom) in a group called "production".

I need to allow the group "Production" to have read write permissions over files that are put into the other 3 users (Mark, Rick & Mike) directories.

So in a nutshell the group "Production" needs to have full read & write access to the FTP directory including files that are added later, the individual users (Mark, Rick & Mike) should only have read & write access to their respective home directories.

I can't for the life of me figure out the syntax to make this be automated.  An example of my problem:

Rick has a client upload a file into his directory, then I have to go change the permissions to allow the group production to have read/write access.  This poses a problem, I don't like talking to the guy in the Macroom and when I have to change the permissions, he has to come and inform me of this =-(.  If a few command lines would prevent me from talking to him I WOULD LOVE IT!!!


Any help is greatly appreciated....

---

### Post by slugmax on 2009-07-10
This is what the setgid bit is for. Take the directory 'Mark' as an example (I hope I have the directory structure right):

```

cd /home/jason/Macroom/FTP
chown -R Mark.production Mark/
chmod 2775 Mark
find Mark -type d -print0 | xargs -0 chmod 2775
find Mark -type f -print0 | xargs -0 chmod 664

```

The permissions 2775 set the setgid bit and give the group r/w access. On a directory, this bit means that any files created in that directory now will keep the group permissions, not the owner's primary group as is usual. The find commands recurse through the Mark directory and fix permissions on all sub-directories (-type d) or files (-type f). The -print0 and -0 are hedges against funny characters in file or directory names.


Doug

---

### Post by Thaumaturge Jay on 2009-07-13
Doug, I think this is what I was looking for...I'll give it a try and see what I end up with.


Thanks!

---

### Post by Thaumaturge Jay on 2009-07-13
So I tried the above and this is what I got:

jason@ftpserver:~/Desktop/ftp$ sudo chown -R mark.production mark/
jason@ftpserver:~/Desktop/ftp$ sudo chmod 2775 mark
jason@ftpserver:~/Desktop/ftp$ sudo find mark -type d -print0 | xargs -0 chmod 2775
chmod: changing permissions of `mark': Operation not permitted
jason@ftpserver:~/Desktop/ftp$ sudo find mark -type f -print0 | xargs -0 chmod 664
chmod: changing permissions of `mark/.profile': Operation not permitted
chmod: changing permissions of `mark/.bash_logout': Operation not permitted
chmod: changing permissions of `mark/.bashrc': Operation not permitted
jason@ftpserver:~/Desktop/ftp$ 


What did I do?  BTW the structure is /home/jason/Desktop/ftp (/mark, /rick or /mike)  Sticking with /mark for now would probably be the best for this discussion´s sake...

---

### Post by Thaumaturge Jay on 2009-07-15
Is there anyone who knows why I got what I got from this?

---

### Post by druhboruch on 2009-07-15
I think you need ":" between user and group in chown command.
Not a "."

Syntax

chown [ -f ] [ -h ] [ -R ] Owner [ :Group ] { File ... | Directory
... }

---

### Post by unutbu on 2009-07-15
```
sudo find mark -type d -print0 | xargs -0 chmod 2775
```

This command did not work because although the find command is run with root privileges,
the chmod command is run with only jason's privileges.

Try
```

sudo find mark -type d -print0 | xargs -0 sudo chmod 2775
sudo find mark -type f -print0 | xargs -0 sudo chmod 664

```

---

### Post by Thaumaturge Jay on 2009-07-15
Ok, so using the sudo before the chmod got rid of the error, however the file is still locked from production, when I FTP a file from a remote machine logged in as user mark, the group production still has no rights?  I would like them to have the same permissions as the owner and that isn't happening, shouldn't the permissions be 774 or 770? and if so why when I try replacing the 664 with that it still doesn't work?

And I'm not understanding the 2775 part?  why is it not just the one line of the 3 digit permissions?  Forgive the ignorance still trying to sweat all the windows out of my system....

---

### Post by Thaumaturge Jay on 2009-07-15
additionally the permissions for the directory is:

drwxrwsr-x 2 mark production 4096 2009-07-15 13:18 mark

On the other two directories who's permissions I set via the GUI they are:
drwxrws--- blah blah blah

so I've obviously changed the permissions, however when a new file is added to the /mark directory it is not inheriting the permissions, it is:

-rw-------- 1 mark production 48783 blah blah blah


Why is this?

---

### Post by unutbu on 2009-07-15
When you set a directory's permissions with
```

chmod 2775 dir
```

the "2" in "2775" sets the setgid bit. You can see that the setgid bit is set when you see an "s" in the permissions line:
```

drwxrw**s**r-x 
```

The effect of the setgid bit is to make new files and subdirs inherit the same group as the parent dir. That is, new files and subdirs will be in the "production" group.

The group is getting set to "production", but it looks like new files are being created with default permissions set to 600
```

-rw-------- 1 mark production 48783 blah blah blah
```

To force mark's new files to be created with 775 permissions, edit mark's .profile.
Search for the word "umask". Change
```

#umask 022
```

to
```

umask 002
```

Log mark out and then log back in to make the change effective.

---

### Post by Thaumaturge Jay on 2009-07-15
in the .profile the "umask 022" line didn't have the "#" infront of it, I changed it to "umask 002" and still SSDD.

I don't understand why this thing won't do these permissions right? I've tried the GUI side, I've tried the CL and nothing is cooperating?  When I do the permissions on the Filezilla client side it works fine, but I need this to be automated and really I think I'm not asking too much of this, I'm just not asking the right way?

---

### Post by Thaumaturge Jay on 2009-07-22
Ok, so Im a total idiot or something...I do not see where to get into marks profile?  I thought I did, but either made a mess of this, which I do not think is a true statement because I still have files coming in...or I changed a profile file that I did not need?


Any pointers would be great...heading to search for the answer now...

---

### Post by Thaumaturge Jay on 2009-07-30
Still no luck making this work right?  Anyone, able to point me to the dummies guide to finding where Marks profile is? or how to get these permissions working right?

I´ve got the folder permissions correct, I just can´t make it do the permissions correct for new files?

---

### Post by unutbu on 2009-07-30
Try using access control lists (ACL): 
[http://ubuntuforums.org/showpost.php?p=832721&postcount=9](http://ubuntuforums.org/showpost.php?p=832721&postcount=9)

---

### Post by Thaumaturge Jay on 2009-08-03
I could be wrong here, as I am most days, but I don´t think that ACLs is where my problem is?  I think it has to do with the folder permissions.  I have the permissions set correctly on the directories, but when a new file is added to the folder it goes back to defaults (not allowing the group to have rw permissions).

---

