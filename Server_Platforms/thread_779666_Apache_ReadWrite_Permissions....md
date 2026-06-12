---
title: "Apache Read/Write Permissions..."
date: 2008-05-02
forum: Server Platforms
---

### Post by erbag on 2008-05-02
I wanted to use the pc as local web development server so I installed LAMP on Ubuntu [7.10], initially it created a folder called '*Apache2*' and I deleted it.

I shared the a folder **/var/www** on my network with Windows PC (mapping the drive in windows). I've attempted to install a CMS for a project I'm working on (CutePHP) and found that some important files are [COLOR="Red"]not writable[/COLOR]. I came across some code online that was to make the directory chmod 777 but that doesn't work. I can't change the chmod using the *ftp client* either. It's as if **safe mode** is on.

**How do I fix this coz I'm running out of time and really need to get this project done by next Fri?**

---

### Post by Dr Small on 2008-05-02
```
chmod 777 /path/to/filename.ext
```

---

### Post by andguent on 2008-05-03
Dr Small's option should take care of it for you. If it does not, can you post a link to the directions you found online, and what happens when you run that command that doesn't work?

---

### Post by ghostknife on 2008-05-03
The fact that you can't write to the files through the windows mapped drive can be that the share isn't writable. 

The fact that FTP can't edit it can again be a configuration option as well.

Are there any files that you can edit?

---

### Post by erbag on 2008-05-03
**to dr. small:** I would have to do this for every file. That is a tonn of work...and I have to use this CMS again which means every project I use it for i would have to run that command for 30+ files.

**to andguent:** if I could find the link back I would be happy. I didn't add it to my Google bookmarks.
[B]
to ghostknife:[/B] I can edit files in dreamweaver or notepad++. I just can't change the read/write permissions.


**WHAT I WANT TO DO?**
Is to permit whatever files are in the folder to be 777/775 automatically or be able to change them using the FTP client.

On most webservers php safemode is on to prevent faulty code in open source apps to be executed.  To me it seems that this is on...can I turn it off? What do I do?

---

### Post by Dr Small on 2008-05-03
If the CMS is any good, it should tell you which files need write permission, and then you would simply chmod those files. But if you are bound and determined to chmod every file 777, then use the -r flag.

Albeit, applying rwx-rwx-rwx (777) to a bunch of files that are web-accessible is highly unrecommended and potentially dangerous.

```
chmod -R 777 /path/to/directory
```

Dr Small

---

### Post by mam00th on 2008-05-03
Use the -r (recursive) option as it will chmod you entire folder

---

### Post by ghostknife on 2008-05-04
If you want to change it via FTP you need to own the file. Maybe the user you are trying to change the permissions as don't own the file.

So, take the user "userX" as the user you are logging in as. Then do:
sudo chown -R userX:`id -gn userX` *

---

### Post by Thirtysixway on 2008-05-04
If you need the script/cms to edit the file, I wouldn't suggest chmod 777.  This lets anyone edit the file.  Instead, change the owner to which user is running the httpd, which by default I believe is   www-data

```
chown www-data /var/www/file.txt
```


This let's the cms edit the file, but keeping everyone else from editing it.

---

### Post by erbag on 2008-05-05
dudes I ran this code
```
sudo chown www-data /var/www/
```
and now I cant access the folder from my pc and when I log into ubunto I can access it either...

I ran ```
chown desktop-user /var/www/
``` and ```
chown nobody /var/www/
``` and I can access the folder but when I go back all my files are gone...

**What must I do now?**

---

### Post by andguent on 2008-05-09
Firstly, if you already got this figured out, let us know.

chown by itself will NOT delete files. It is only capable of changing who owns them. It is more likely that the files are simply not accessible to you. I'm going to work on that assumption below.

My /var/www on my internal testing server looks like this when I do **'ls -lah /var/www'**:
```
drwxr-xr-x  3 root     root 4.0K 2008-02-01 08:57 apache2-default
drwxr-xr-x  3 root     root 4.0K 2008-03-31 19:45 testing1
drwxr-xr-x  3 root     root 4.0K 2008-02-01 23:08 testing2
drwxr-xr-x  9 www-data root 4.0K 2008-04-19 21:24 torrentflux2
```

I realize you have gotten multiple suggestions here, but one of the better ways to manage access is to set the group appropriately, and then add yourself to that group.

The first step is to get you back into your files directly from the workstation.
```
sudo su
ls -lah /var/www
```
Confirm that the files are still there, and simply accessible as your normal username. If we are good, lets continue.

```
chown -R www-data:www-data /var/www
ls -lah /var/www
```
You should see now that every entry has "www-data     www-data" listed in the middle columns. The first is the owner, the second is the group. The -R argument makes chown set this on ALL files within /var/www, even down 
within subdirectories.

```
addgroup erbag www-data
chmod -R 775 /var/www
ls -lah /var/www
groups erbag
```
Add your own username to the group www-data (change erbag to whatever your username is on the workstation obviously...). chmod changes permissions for the owner, group, and everyone else (via three numbers). The second number in 775 is 7, so if you are in the www-data group you have full control over the directory & contents. Search online for chmod to get more details on this.

You should now have directories that look something like this:
```
drwxrwxr-x  3 www-data     www-data 4.0K 2008-02-01 08:57 apache2-default
drwxrwxr-x  3 www-data     www-data 4.0K 2008-03-31 19:45 testing1
drwxrwxr-x  3 www-data     www-data 4.0K 2008-02-01 23:08 testing2
drwxrwxr-x  9 www-data www-data 4.0K 2008-04-19 21:24 torrentflux2
```

Note the rwxrwxr-x pattern compared with earlier.

We have been running all of these commands as root since the sudo su. **Type 'exit' to return to being your normal self.** Try your ls -lah /var/www again. Things should be cleaned up and you should have access again to everything without opening security too wide.

---

### Post by erbag on 2008-05-16
my server crashed and now I've reinstalled everything form scratch...

WHAT WORKED:
sudo chmod -R 777 /path/to/directory/


I copied a folder in the directory after I ean the above command. Started the instillation and was told the sub directories and some files are unwritable.

Is there a way I can avoid running **sudo chmod -R 777 /path/to/directory/** every time I add a new folder?

---

### Post by ghostknife on 2008-05-17
You can change it's ownership to whatever user apache uses?

Beyond this, whenever you create a directory that you need apache to write to you need to change it's permissions or ownership.

---

### Post by erbag on 2008-05-20
**[SIZE="5"]THANKS TO ALL YOU GUYS !!!![/SIZE]**

As said in the prior post...the server crashed and and now I'm able to access all my files on my server after re-installing.


**THE ONLY PROBLEM I HAVE...**
After typing:
```
sudo chmod 777 /var/www/*
```

whenever I add a new folder I still have to type
```
sudo chmod 777 /var/www/folder/name/or/file/name
```

**IS IT POSSIBLE TO ENSURE THAT WHATEVER FOLDER / FILE IS ADDED TO /var/www/ has the CHMOD 777 ?**

---

### Post by molotov00 on 2008-05-20
Quit rushing to reply and think about the responses. If YOU create a new folder, how does the server know Apache should be able to access it? It doesn't.

So, you need to chmod or chown (for www-data) the folders you want Apache to be able to access, after you create them.

Altneratively, you can add www-data and yourself to the same group, which was also described earlier in a rather comprehensive reply you must have overlooked.

m

---

### Post by erbag on 2008-05-26
@ adugent: Sorry man but that didn't work for me....at this point i'm just using vnc to run a chmod 777 when I add the files to the web server...Thanks!

---

### Post by andguent on 2008-05-26
I hope this isn't a publically accessible server from the Internet. 775 is MUCH safer than 777.

Also, try SSH for remote administration. It is significantly quicker, and probably much safer.

---

### Post by ViscountGrey on 2008-10-23
I have recently designed a new web based staff planner, which has an easy point click interface to allocate staff.  When I try and save it back to the database where the information is stored, I get told I do not have permission to do that.  When I try to modify the file or folder attributes in FTP I get error 550 - File or Directory does not exist.  My IT manager told me this is because it is externally hosted from our network, and I need to contact the domain supplier to ask them to change the attributes.  When I phone them, all I get is "It's because you're not on Linux, you need to be on Linux to change the attributes."   Is there any other way I can do this?

---

