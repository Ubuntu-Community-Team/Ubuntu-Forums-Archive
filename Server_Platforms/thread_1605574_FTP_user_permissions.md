---
title: "FTP user permissions"
date: 2010-10-25
forum: Server Platforms
---

### Post by Ub3r Sold4t on 2010-10-25
I'm still very new to setting up servers so this could be a question with a very simple solution but I couldn't find anything to help. I've got an FTP server set up and I want to make it so users can upload and download but not delete files on the server.

---

### Post by WillJeffery on 2010-10-25
Yep, I'm in the exact same boat. Would like to know the answer to this aswell thanks :)

---

### Post by Vegan on 2010-10-25
I use VSFTP and its well known here and its documented in the manuals too.

It can be configured to user accounts easily with a few edits to the config file.

---

### Post by Ub3r Sold4t on 2010-10-25
I'm using VSFTP too actually and have tries editing the config file. The problem is I can't seem to find out how to change the owner of the file once uploaded. I uncommented the chown_uploads=YES and chown_username=name lines. But when I upload files it doesn't chown them. the comment above those lines says its for anonymous uploads so i think thats why it wont chown them. is there another command I need to add? 

All I want to do is make it so the uploads can't be deleted once on the server. On the Manual page for VSFTP I saw " lock_upload_files" and tried that too. no luck. 

I realize that I probably annoyed a lot of people on here by posting what is probably a very simple question, but I'm having a lot of trouble with this and have been searching for a few days now on a solution. Any help would be appreciated.

---

### Post by HermanAB on 2010-10-26
Howdy,

There is another age old FTP trick that is still useful in some situations:  Separate the upload and download directories.

Allow users to upload to one diretory and download from another directory (Do not allow them to do both actions on the same directory).  The FTP administrator periodically vets and copies files from upload to download.  This simple trick thwarts users who want to turn your FTP server into a porn collection.

---

### Post by mlinux on 2010-10-26
In which entry of the vsftpd.conf to set the upload file to be readable to all user. I try to upload file to www but all uploaded file attributes set to r/w for owner only.

---

### Post by Ub3r Sold4t on 2010-10-26
> **HermanAB said:**
> Howdy,

There is another age old FTP trick that is still useful in some situations:  Separate the upload and download directories.

Allow users to upload to one diretory and download from another directory (Do not allow them to do both actions on the same directory).  The FTP administrator periodically vets and copies files from upload to download.  This simple trick thwarts users who want to turn your FTP server into a porn collection.

That's the way I might have to do it sadly. Was hoping for an easy way to chown the files without having to do it manually. Seems either nobody knows how to do what I'm looking for or nobody wants to help. Ill keep looking but I just can't seem to find the answer. Thanks for the idea

---

### Post by HermanAB on 2010-10-26
Yes, your FTP server *can* chown the files to the ftp user usually.  Read the man page of whichever ftpserver you are using.

---

### Post by Ub3r Sold4t on 2010-10-26
I have. Seems it can only shown on anonymoua uploads. Guess ill look into other ftp servers. If I'm wrong please let me know

---

### Post by the_original_billq on 2010-10-26
There is a very specific configuration for anonymous ftp servers.

Some helpful pointers can be found here:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup#FTP_Security_Issues]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup#FTP_Security_Issues")

that address vsftp.

You might also try googling "anonymous ftp server configuration" as there are multiple sites that provide reference configurations to do exactly what you are trying to do.

-Bill

---

### Post by Ub3r Sold4t on 2010-10-26
I'm not looking for anonymous user configurations. I have set users that will log in to upload. I'm looking for a way to change ownership of the files they upload so that the files cannot be deleted after they are uploaded. Ill take a look at that link though. Thanks

---

### Post by the_original_billq on 2010-10-26
> **Ub3r Sold4t said:**
> I'm not looking for anonymous user configurations. I have set users that will log in to upload. I'm looking for a way to change ownership of the files they upload so that the files cannot be deleted after they are uploaded. Ill take a look at that link though. Thanks

Yeah, that was a pretty lousy suggestion.  Sorry - I was reading it much more simply than it really is, and somehow thought it was an anon setup.

I'll re-read the thread a bit more closely and research it a bit before making any suggestions.

-Bill

---

### Post by Lars Noodén on 2010-10-26
> **Ub3r Sold4t said:**
> I'm looking for a way to change ownership of the files they upload so that the files cannot be deleted after they are uploaded.

That is usually called a drop box, if that will help you look for answers.

---

### Post by the_original_billq on 2010-10-26
I believe this [http://www.linuxquestions.org/questions/linux-networking-3/vsftpd-configuration-help-351330/#post1790125]("http://www.linuxquestions.org/questions/linux-networking-3/vsftpd-configuration-help-351330/#post1790125")
is extremely close to what you are looking for.

No anon access.
Users can upload and download, but not delete. (see the cmds_allowed setting)

You will have to diddle with the file_open_mode option to allow reading, but other than that, the provided vsftpd.conf looks like what you need.

I'm bookmarking this one - it's a great reference.

-Bill

---

### Post by Ub3r Sold4t on 2010-10-26
> **the_original_billq said:**
> I believe this [http://www.linuxquestions.org/questions/linux-networking-3/vsftpd-configuration-help-351330/#post1790125]("http://www.linuxquestions.org/questions/linux-networking-3/vsftpd-configuration-help-351330/#post1790125")
is extremely close to what you are looking for.

No anon access.
Users can upload and download, but not delete. (see the cmds_allowed setting)

You will have to diddle with the file_open_mode option to allow reading, but other than that, the provided vsftpd.conf looks like what you need.

I'm bookmarking this one - it's a great reference.

-Bill

You are the best!

added line "cmds_denied=DELE" to vsftpd.conf and thats all it took!

Thank you so much!:P

---

