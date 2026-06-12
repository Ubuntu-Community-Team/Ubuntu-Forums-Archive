---
title: "editing files from windows share"
date: 2014-10-05
forum: Server Platforms
---

### Post by wlraider70 on 2014-10-05
When I have to edit the code for pages on my server. I prefer to use windows. So I make the folder a share and then I have to chmod 777 the file so I can be saved from notepadd++.

Questions
1) Is it safe to leave .php or .py files with full read and write.
2) Is there another way to edit files from windows? Share seems better than ftp to me...

---

### Post by cariboo on 2014-10-06
I'd suggest using putty, then one of the text based editors on the server. Changing php permissions while the server is live and connected to the internet, isn't a very good idea.

---

### Post by mastablasta on 2014-10-06
> 
Questions
1) Is it safe to leave .php or .py files with full read and write.

Yes, if you want people to hack your server.

> 
2) Is there another way to edit files from windows? Share seems better than ftp to me...

another option would be to sync using something like grysnc or something. edit local and then sync it. 

I am still on FTP. editing locally, checking it and then throwing it on server.

---

### Post by daniel201 on 2014-10-06
Use a repository.
You can commit changes to the repository and then update the server from the repository.

---

### Post by nerdtron on 2014-10-06
> **wlraider70 said:**
> When I have to edit the code for pages on my server. I prefer to use windows. So I make the folder a share and then I have to chmod 777 the file so I can be saved from notepadd++.

Questions
1) Is it safe to leave .php or .py files with full read and write.
2) Is there another way to edit files from windows? Share seems better than ftp to me...

SFTP would be good (just use filezilla to download/upload files).
But if you're a bit lazy, you can always change back the permissions to their default after you are done editing. :)

---

### Post by wlraider70 on 2014-10-06
Is there a way to authenticate from windows? Files that don't have open permission give me a windows message of, "is this file open by another program"

I've been asked for credentials before, but they never work even if I put the root password in.

---

### Post by nerdtron on 2014-10-06
How do you access the files of the server from your windows machine?

---

### Post by wlraider70 on 2014-10-07
Currently, through a samba share, but I have the "guest" mode enabled. Thus, there is no authentication of any type (as far as I know).

---

### Post by nerdtron on 2014-10-07
That's the same as copying the file to your computer, editing it, save and reupload it to the server. Although done automatically on the background.
Basically any other method for accessing/editing the files as long as you use a windows program to edit will always involve donwloading/uploading the file.

Anyway, since you still use notepad++, just be careful with the permission especially if this is a server with a public website.

---

### Post by mastablasta on 2014-10-08
> **nerdtron said:**
> 
Basically any other method for accessing/editing the files as long as you use a windows program to edit will always involve donwloading/uploading the file.
.

not true. you can SSH into server (from windows using for example putty) and then run either an X program there (e.g. gedit, kate or something like that) or a faster CLi programs for editing files e.g. nano, vim. in both cases you would edit the file on server directly. 
There are also web GUI interfaces that offer you to edit files directly on the server (e.g. the editor on Ajenti server admin webgui or in Cpanel; zpanel likely has one as well).

in both cases you are doing the edit directly on server.

to the OP why are you using guest account? :o guest is meant if you lend your computer to someone.

one more thing you can setup SSH to log in with keys (which is the safer method if you have the ssh port open to public). so you might setup a program to login and open file for editing... :p

---

### Post by wlraider70 on 2014-10-08
I'm not using the guest account when I'm on the machine, CLI only by the way.
I'm using samba with the option to allow guest, when I access the share from the Win7 that's how I get around being asked for a linux/samba user and PW each time. 
I would LIKE to be asked for user/pw but that doesn't seem to work....

---

