---
title: "access errors on apache"
date: 2012-04-27
forum: Server Platforms
---

### Post by DonTommy on 2012-04-27
Hey
Newbie ubuntu user here. I got a apache server up and running on ubuntu, with vsftp installed as well.

And I am not that keen on the whole permissions thing, can get it to work.

Just get the writing enabled trough ftp, but now I get a 403 forbidden error when accessing the IP of the server trough a browser? But I can access phpmyadmin, so I guess it is my permissions on /var/www that needs to be changed. Its only for personal use, but I need both the ftp access and to view it online as well.

---

### Post by newbie-user on 2012-04-27
```
chgrp -R www-data /var/www && chmod -R 744 /var/www
```

That changes group ownership to the www-data group for all contents of /var/www and sets read-only permissions for the group and world.

---

### Post by DonTommy on 2012-04-28
Hmm that dosnt work, I still get a 403 forbidden error, when trying to access trough browser, I still however can make folders and upload files to the directory trough ftp

---

### Post by DonTommy on 2012-04-28
Ahh got it to work, just had to set the group permissions to access files, instead of only listing.

Thanks :)

EDIT: Hmm after editting a file trough ftp, it went back to 403 forbidden when access trough browser

---

### Post by Jonathan L on 2012-04-28
Hi Don Tommy

> **newbie-user said:**
> ```
chgrp -R www-data /var/www && chmod -R 744 /var/www
```

Just wanted to comment that those are _extremely_ unusual permissions, and I believe the poster meant 755.  Directories pretty much need 'x' bit set to be useful.

Also, chmod -R 755 has the effect of setting the execute bits on all the plain files, which is unlkely to be what you actually want.  You might care to do this:
```
chmod -R 755 /var/www
find /var/www -type f -exec chmod 644 '{}' ';'
```Your FTP description is probably because you have a umask which is masking some of the bits, or your files have the wrong group.
In FTP, before you upload, do
```
umask 22
```Hope that's helpful.

If you still need help, could you post the output of ls -l on files which are giving access forbidden?

Kind regards,
Jonathan.

---

### Post by DonTommy on 2012-04-28
Hey
Thanks for the update, I get it to work, but as soon as I soon edit the index.html trough ftp it gets forbidden again, and I have to do a chmod again..

When I do the ls -l in the /var/www folder in terminal on the computer running the server is says:
-rwxr-xr-x 1 on the index.html file, which is the only file their.

The umask thing I didnt get? As when I edit the files I just connect trough netbeans with the ftp so cant insert code their before ftp'ing?

Hope you can help me out :)

---

### Post by Jonathan L on 2012-04-28
Hi again Don Tommy

> I get it to work, but as soon as I soon edit the index.html trough ftp it gets forbidden again, and I have to do a chmod again..


Could you put the whole output of ls -l after the edit, that is, also showing the user and group?  And then after you've made it work?

NB: if you have rwxr-xr-x your umask is fine.  It's the owners or groups we'll fix.

Kind regards,
Jonathan.

---

### Post by DonTommy on 2012-04-28
This is when it works:
dtserver@dtserver:/var/www$ ls -l
total 4
-rwxr-xr-x 1 dtserver dtserver 209 2012-04-28 18:46 index.html


After I edit a file this is what I get
dtserver@dtserver:/var/www$ ls -l
total 4
-rw------- 1 dtserver dtserver 226 2012-04-28 19:49 index.html


I see the difference, I just have no clue what to do and what it means?;)

---

### Post by Jonathan L on 2012-04-28
Hi Don Tommy

I take back my statement about umask and group: I'd misunderstood before: definitely a umask problem.  Skip to the bottom for the fix if you don't want the explanation.

**First the explanation**

There are three things you can do to a file: _**r**_ead it, _**w**_rite it, and e_**x**_ecute it (run it as a program).

Your web server is (almost certainly) running as a special user called 'www-data', which is in group also called 'www-data'.  (This is defined in /etc/apache2/envvars, if you want to check.)

Your file is owned by dtserver and group dtserver.

Whenever a process tries to open a file, the kernel checks the owner of the process (in this case 'www-data') against the owner of the file (in this case 'dtsserver').  If they're the same, we user the owner permissions.  If not, the process has a list of groups it's in, and the kernel sees if the group of the file is in the list of the process's groups; if it is, we user the group permissions.  Otherwise, we use the 'other' permissions.

**When it works:**
```
-[COLOR=Red]rwx[/COLOR][COLOR=Lime]r-x[/COLOR][COLOR=RoyalBlue]r-x[/COLOR] 1 dtserver dtserver 209 2012-04-28 18:46 index.html
```The file part 'rwxr-xr-x' is a comprised of three parts: the first three letters '[COLOR=Red]rwx[/COLOR]' apply to the owner (called dtserver); the second triple '[COLOR=Lime]r-x[/COLOR]' apply to the group also called dtserver; and the third triple 'r-x' applies  to other users.  The user we're interested in is 'www-data', as that's the user the web server is.  So the third triple applies: and this user can read the file: which is why it works.  For files, you don't really need or what the execute permissions, but there are not stopping it working.

**When it doesn't work:**
```
-rw------- 1 dtserver dtserver 226 2012-04-28 19:49 index.html
```Here, only the owner 'dtserver' can read and write the file.  No group or other permissions are there.

**What you actually want it to be:**
```
-rw-r--r-- 1 dtserver dtserver 226 2012-04-28 19:49 index.html
```Read for everybody, also write for the owner.

**How does it get its permissions?**

When a piece of software creates a file, it asks for the permissions to be [FONT=Courier New]rw-rw-rw-[/FONT] and it is then masked down with the current "umask" which is a "current privacy setting", just like you have a current directory.  The umask might say "I don't want to give away write permission to anybody else" or perhaps "No permission at all to anyone else", or "Let everybody do everything".

"No permissions except for me" means subtract [FONT=Courier New]---rwxrwx[/FONT], we call this a umask of 077
"No writing except for me" means subtract [FONT=Courier New]----w--w-[/FONT], we call this a umask of 022
"No writing except for me and my group" means subtract [FONT=Courier New]-------w-[/FONT], we call this a umask of 002
"Anybody can do anything" means subtract nothing, we call this a umask of 000

(Directories are created with [FONT=Courier New]rwxrwxrwx[/FONT] and masked with the same mask.  If you make subdirectories, which you almost certainly will, you'll want them to show as [FONT=Courier New]drwxr-xr-x[/FONT] owned by dtserver/dtserver.  You can ignore this momentarily: when the files are fixed, the directories will be too.)

What's happening is is that somewhere, _you have a umask setting of 077_.  We have to find where it is set.

**FTP Server Umask**

I see you're using vsftpd, which unusually has a default umask of 077 !

The configuration file is /etc/vsftpd.conf -- have a look in there for 'umask'.  Mine looks like this:
```
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=022
```If you edit this configuration file you'll have to restart the ftp daemon:
```
sudo /etc/init.d/vsftp restart
```Hope that's some help.  Let us know if you find it or need more help.

Kind regards,
Jonathan.

PS.  The statement about "files are created with ..." is true for all normal files.  Files like password files are done differently.)

PPS.   Obviously you can delete files too: deleting a file is actually considered to be writing in its directory.

---

### Post by DonTommy on 2012-04-29
Thank you so much for taking the time for that long explanation, got a much better feeling of how this stuff works now :)

And the umask thing worked perfectly :)

Again thank you!

---

