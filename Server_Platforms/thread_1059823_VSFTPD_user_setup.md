---
title: "VSFTPD user setup"
date: 2009-02-04
forum: Server Platforms
---

### Post by Sir_Substance on 2009-02-04
just bare with me a bit here, im somewhat new to linux, and although i know some of the basics of using the terminal, my knowledge is somewhat superficial.

if your willing to help, many thanks, but baby steps, ya?

basically, i want to run an FTP server. 

what i have set up is a linux based server (obviously, or i wouldn't be here) using ubuntu.

i have downloaded the VSFTP Daemon, and gotten it to work in it most basic capacity. that is, if i manually put files in the folder it set up (/home/ftp/) by physically plugging a USB into the server and then using the sudo command to transfer them (as you cant log in as root to ubuntu, to my knowledge, i have to use the command line to move them, /home/ftp/ is owned by root) then they will pop up on my file server, and other people can anonymously download them.

i ahve also set it up so i can access the server on the local network, on which my general use PC is connected.

you can see what is currently happening here:

[ftp://150.101.101.215]("ftp://150.101.101.215")

however. this isnt quite all i would like from the server. i dont want anonymous uploads, but i do with to be able to create a username that can upload to the folder you see in that link, which on the server is located at "/home/ftp/".

i want this user to be able to upload both form my general use PC (so i can upload games, files etc) and remotely (so i can back up uni work to there from uni or library's in an emergency).

thing is, i have absolutely no clue how to set up users in vsftpd.

i have looked at various tuts on the internet, but they all seem to want to set it up so users upload to different folders, depending on the user, which is not what i wish to achieve at all.

can anyone help me?

---

### Post by dca on 2009-02-04
It's been a while but you can try this:
 
Make a copy of the /etc/vsftpd.conf file before doing this.  By using a vanilla conf file that was made right after installation of the vsftp.  You can change these or make sure these options are set like those below.
 
anonymous_enable=NO
local_enable=YES
write_enable=YES
chroot_local_user=YES
 
...now make sure those are uncommented (no #) or set as you see above and leave the rest of the conf file alone.
 
Now I'll give explanation of why I set my FTP up like this and you can see if that's what you're going for.  What these settings allowed me to do was on my 8.04 box which was set-up for nothing but FTP.  Wait, lemme' start over.  I have one user account on that box from installation called 'dca'.  After installating vsftp and making changes you see above, it only allows me 'dca' (plus p/w) to login when doing the [ftp://localhost](ftp://localhost) in web browser.  No anonymous, no root, etc, etc.  The files are not kept in /home/ftp, but in /home/dca...
 
Hopefully someone can chime in if I've missed anything.

---

### Post by Sir_Substance on 2009-02-04
correct me if im wrong, but surely if i disable anonymous, people wont be able to download from the FTP site over the internet without me setting them up a login?

all i want is the one login for uploading.

also, ive been told that using the computers login isnt a brilliant idea, since FTP sends passwords and usernames over the internet in plain text. is this correct?

---

### Post by spiderbatdad on 2009-02-04
Apache works well for this using the option Indexes. A nice php file called filethingie [http://www.solitude.dk/filethingie/](http://www.solitude.dk/filethingie/)
works great, as it can be placed in specific user owned directories where authentication is required to access the directory.
Sorry if this is too far off topic.

---

### Post by Poleh on 2009-02-04
> **Sir_Substance said:**
> correct me if im wrong, but surely if i disable anonymous, people wont be able to download from the FTP site over the internet without me setting them up a login?

all i want is the one login for uploading.

also, ive been told that using the computers login isnt a brilliant idea, since FTP sends passwords and usernames over the internet in plain text. is this correct?

Correct.

I use regular user accounts though, and it's fine. What you want to do is leave anonymous available, but protect uploads with password permissions. Then create regular users within the Ubuntu server which can be used to log into the ftp site as well.

As a further precaution you can also setup those users to not be able to login via ssh (which they will if you hvae it installed and you create them as regular users). This links discusses this in some detail:

[http://ubuntuforums.org/showthread.php?t=897477](http://ubuntuforums.org/showthread.php?t=897477)

---

### Post by Sir_Substance on 2009-02-04
interesting and useful in other areas though this is, none of it really answers my original question, which is how do i set up user accounts?

---

### Post by spiderbatdad on 2009-02-04
thought your question was how to allow anon logins but only privleged uploads. Post #5 seemed to address that. There are dozens of well written tutorials for creating accounts and how to configure vsftp:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch15_:_Linux_FTP_Server_Setup)
The bottom half of that page is dedicated to the subject. Google will produce hundreds of other well written tutorials.

---

### Post by inphektion on 2009-02-04
To more directly answer your question.  Set anon users to not have write access.  This will prevent them from uploading.
Setup virtual users using htpasswd file.  In your case 1 virtual user who you can restrict to upload only by using allowed commands the user can use.  
This setup will give you exactly what you want.

---

### Post by Poleh on 2009-02-05
> **inphektion said:**
> To more directly answer your question.  Set anon users to not have write access.  This will prevent them from uploading.
Setup virtual users using htpasswd file.  In your case 1 virtual user who you can restrict to upload only by using allowed commands the user can use.  
This setup will give you exactly what you want.

did you search the forums? :)

[http://ubuntuforums.org/showthread.php?t=518293&highlight=disable+ssh+login](http://ubuntuforums.org/showthread.php?t=518293&highlight=disable+ssh+login)

that's a pretty comprehensive tut right there!

---

### Post by Sir_Substance on 2009-02-05
> **Poleh said:**
> did you search the forums? :)

[http://ubuntuforums.org/showthread.php?t=518293&highlight=disable+ssh+login](http://ubuntuforums.org/showthread.php?t=518293&highlight=disable+ssh+login)

that's a pretty comprehensive tut right there!

ah, now there is a tutorial that looks like it might a) be helpful in getting what i want done and b) make sense to people who dont "get" linux.

now, i assume i want to use:
```

# 3. Just some users are "free":
chroot_local_user=YES
chroot_list_enable=YES
# Create the file /etc/vsftpd.chroot_list with a list of the "free" users.
```

i am assuming "free" means able to upload as well as download?

---

### Post by Poleh on 2009-02-05
correct, good luck!

---

