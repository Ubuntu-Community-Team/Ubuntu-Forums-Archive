---
title: "How To Correctly Set File Permissions"
date: 2011-04-30
forum: Security
---

### Post by TheNewbieGeek on 2011-04-30
I have set file permissions for home folder only...what about all the other files and folders?

---

### Post by simonplexus on 2011-04-30
Not quite sure what you are asking here, but perhaps recursive is what you are looking for?
```

chmod -R XXX /path/to/files

```
or
```

chown -R user:group /path/to/files 

```
?

---

### Post by TheNewbieGeek on 2011-04-30
If you dont know ask...thats horrible advice...again how do you set file permissions for anything outside of the home directory...for anybody whos knows what I'm talking about.

---

### Post by simonplexus on 2011-04-30
> .again how do you set file permissions for anything **outside** of the home directory

well thats a different question altogether. Your original question was somewhat vague, but hey at least i tried to help.

To set persmissions for files outside of home directory, if you 'own' the files
```

chmod XXXX /path/to/file

```
if you do not 'own' the file/directory
```

sudo chmod XXXX /path/to/file

```

If this isnt what you are looking for, then could you be a bit less vague in your question and perhaps not be so rude when you get a reply that is not what you expect.

---

### Post by TheNewbieGeek on 2011-04-30
no it's not vague at all...and bad advice isn't worth receiving.

EDIT: permissions is what I said....anyway I found a link that told me.

---

### Post by Morbius1 on 2011-04-30
First, You don't want to change the permissions and ownership of files outside of your home directory. Well, you may want to but you shouldn't. Unless of cource this is a data partition or some other non-system partition.

Second, it differs if you are talking about a Windows filesystem such as FAT32 or NTFS and a Linux filesystem. You can't change ownership or permissions on a Windows filesystem outside of a mount or in fstab. For a linux filesystem it's with a chown ( for ownership ) and chmod ( for permissions ).

Since the title of this thread is "How to correctly set ...." I would like to offer a slightly different way to set recursive permissions of a given directory. If you do the following:
```
sudo chmod -R 777 /path/to/folder
```It will indiscriminately make all folders and files within the folder readable, writable, and executable to everyone.

If you do it this way:
```
sudo chmod -R a+rwX /path/to/folder
```The big "X" in that expressions will make every folder executable ( which you must do to be able to open the folder to "see" what's inside) but will not mark any file that is not already marked executable as executable.

---

### Post by cariboo on 2011-04-30
> **TheNewbieGeek said:**
> I have set file permissions for home folder only...what about all the other files and folders?

That is pretty vague, you don't specify waht files and directories, and where.

> **TheNewbieGeek said:**
> no it's not vague at all...and bad advice isn't worth receiving.

EDIT: permissions is what I said....anyway I found a link that told me.

That is kind of disrespectful to someone who is volunteering their time to help. 

Are you going to share your solution with us?

---

### Post by TheNewbieGeek on 2011-05-01
I apologize to the poster who I said that to he was right. I am following a tutorial on how to set file permissions. Here is the advice I was given:


[LIST]
[*]         [FONT=arial]***home directories** *-  The users\' home directories are important because you do not want  other users to be able to view and modify the files in another user\'s  documents of desktop. To remedy this you will want the directory to have  the **drwx______ (700)** permissions, so lets say we want  to enforce the correct permissions on the user user1\'s home directory  that can be done by issuing the command **chmod 700 /home/user1**.[/FONT]
[*]         [FONT=arial]***bootloader configuration files**  *- If you decide to implement password to boot specific operating  systems then you will want to remove read and write permissions from the  configuration file from all users but root. To do you can change the  permissions of the file to 700.[/FONT]
[*]         [FONT=arial]***system and daemon configuration  files** *- It is very important to restrict rights to system  and daemon configuration files to restrict users from editing the  contents, it may not be advisable to restrict read permissions, but  restricting write permissions is a must. In these cases it may be best  to modify the rights to 644.[/FONT]
[*]         [FONT=arial]***firewall scripts*** -  It may not always be necessary to block all users from reading the  firewall file, but it is advisable to restrict the users from writing to  the file. In this case the firewall script is run by the root user  automatically on boot, so all other users need no rights, so you can  assign the 700 permissions.[/FONT]
[/LIST]
I don't know what system and daemon configuration files I should change same with  bootloader configuration files and firewall scripts. I have successfully changed the home directory.

---

### Post by CharlesA on 2011-05-01
For the most part the default permissions are fine.

If you mess around with permissions or ownership of system files the system can become broken - not bootable, or worse.

---

### Post by TheNewbieGeek on 2011-05-01
OK thanks...you're right...I had to reinstall after trying.

---

### Post by CharlesA on 2011-05-01
> **TheNewbieGeek said:**
> OK thanks...you're right...I had to reinstall after trying.
Ouch. Experience is the best teacher. :)

I know there have been threads where someone has run chmod 777 on the entire OS drive, and it's hosed it up pretty badly. It's a pain to recover from, unless you just back up your stuff and reinstall.

---

