---
title: "How to automatically apply user permission on new files and dirs under /var/www"
date: 2007-03-26
forum: Server Platforms
---

### Post by acco.tn on 2007-03-26
Hi, to all, i'm just a newbie in the ubuntu world (and generaly on linux...) i've set up my webserver but now i've a little problem:

I've read some post that explain how to add my user to www-data and change files and dir permission to www-data group and set access permission too.

**BUT** when i create a new file or dir and try to view it on a browser i obtain "forbidden" etc.

**[COLOR="Red"]How can i do to make new files and dirs to automatically get right access permission????[/COLOR]**


Thanks to all!

---

### Post by elst on 2007-03-26
Add the "setguid" option (identified by the number 2) to the permissions on a directory to cause everything created under it to inherit the same group, e.g.:

chmod 2755 /some/directory/

---

### Post by acco.tn on 2007-03-27
Thanks very very much for ur tip!!

---

### Post by acco.tn on 2007-03-29
hi again, i dont kwon if im doing something wrong but usgin "chmod 2755 -R /var/www" all files in the dir were modified but if i create a new file, with my user (that i've added to www-data group) and i try from browser to access it I obtain "FORBIDDEN.."


how can i do?!?

---

### Post by elst on 2007-03-29
What are the permissions on the new file?

---

### Post by acco.tn on 2007-03-29
the owner and the group id are right, but the new file are not readable by "other" so apache blocks page with "Forbidden.."

---

### Post by huygens on 2007-03-29
> **acco.tn said:**
> hi again, i dont kwon if im doing something wrong but usgin "chmod 2755 -R /var/www" all files in the dir were modified but if i create a new file, with my user (that i've added to www-data group) and i try from browser to access it I obtain "FORBIDDEN.."

You should not have use the -R because now you remove write permission to the group, so to you too.
If you want again to have write permission for the group, then you should type this:
```
sudo chmod -R g+w /var/www
```Take care that now Apache will be able to modify all the files under your root web directory. So you might want to apply the "write permission" only to directories (and even...) If you want to give write permissions to only directories, then you should type this instead of the previous command:
```
find /var/www -type d | sudo xargs chmod g+w
```(take care that in this example, I did not put the -R option)
Now to give yourself write permission to certain files, you juste have to type:
```
sudo chmod g+w <name_of_the_file>
```And replace <name_of_the_file> by the name of the file :-)

---

### Post by Mr. C. on 2007-03-29
Recursively changing all the permissions to 2755 is not the right solution.  The proper solution begins with undestanding what file and directory permissions should be in the first place.  I'll leave that to you to ask more questions if you are interested in learning more about this.

To respond to your problem as to why new files are created without Other permissions - this is a result of your umask.  Your umask strips permissions on newly created files and directories, leaving only those not specifically masked out.  You need to change your umask if you want new files to have world permissions.
```

man umask
```

Review week 2 notes and homework in the Coursework section at: [http://cis68a.mikecappella.com/](http://cis68a.mikecappella.com/)

MrC

---

