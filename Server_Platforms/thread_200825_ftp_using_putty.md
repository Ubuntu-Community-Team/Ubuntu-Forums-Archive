---
title: "ftp using putty"
date: 2006-06-20
forum: Server Platforms
---

### Post by Isoss on 2006-06-20
I am using PuTTy on my laptop to SSH to the server which has my websites. through PuTTy I tried FTPing to my website and it worked but when I tried to upload a file using "put" it outputted the following:
```

ftp> put index_body.php
local: index_body.php remote: index_body.php
500 I won't open a connection to *serverip* (only to *myip*)
ftp: bind: Address already in use

```
Is there some other way to upload my files using putty or something else?
I am developing my files using ssh with bluefish but everytime I have to upload the editted files I have to go to the server and upload it from there!
I hope somebody has a solution.

Thanks

---

### Post by Stu09 on 2006-06-20
What about WinSCP ? It's like ftp, but uses ssh to copy files.
It also has putty integrated into it so you can open a terminal window if you need to.

---

### Post by Isoss on 2006-06-21
I have two linux michines. My laptop and the server PC. I develop my websites using my laptop but the files are on the server. using putty, I ssh into the server and from the server I ftp so I can upload the files directly form the PC but through putty.

Hope I made my self more clear. I have WINSCP on windows machines, but that's not what I am looking for! I need to connect to the server and from the serve upload the files directly from it to the original server without copying the files to my laptop and then uploading them from the laptop. I don't wanna do that! Just wanna ftp from the server while SSHing to the server from another PC.

Thanks

---

### Post by mat1t on 2006-06-21
Not sure how it works, but look up "passive" or "pasv". That may be your problem.

---

### Post by spifbv on 2006-06-21
[QUOTE=Isoss]I am using PuTTy on my laptop to SSH to the server which has my websites. through PuTTy I tried FTPing to my website and it worked but when I tried to upload a file using "put" it outputted the following:
```

ftp> put index_body.php
local: index_body.php remote: index_body.php
500 I won't open a connection to *serverip* (only to *myip*)
ftp: bind: Address already in use

```
Is there some other way to upload my files using putty or something else?
I am developing my files using ssh with bluefish but everytime I have to upload the editted files I have to go to the server and upload it from there!
I hope somebody has a solution.

Thanks[/QUOTE]


You should definitely investigate using ssh or sftp instead of regular ftp, as ftp does not have any encryption or other important security measures.  In fact if you have used regular ftp to access your account you should change the password using a secure mechanism (SSL protect web page, SSH login - depends on your setup).  If you are using a third party hosting provider, check with them to see what secure protocols they support.  If they do not support any, you should urge them to do so and if they refuse you should find another provider.

That said, if you absolutely must use FTP, definitely use passive mode.  The default is active mode which involves the server initiating a connection back to your client system for data transfers.  This is what is most likely happening here.  You could also use lftp which has passive mode as the default and has some other useful features.

---

### Post by Isoss on 2006-06-21
Alright, my host doesn't support any but I can't find another one now. Anyway, I am not that much into these stuff, barely know what you were talkinga about. I konw lftp is for localhost ftping but I don't need that, I need to connect to the reall host. also not sure what passive and active mode do, and I don't konw how to set the passive mode as default! so I hope you'd help me in this what to do or may you recommend some webpage or thread that talks about that.
THanks.

---

### Post by spifbv on 2006-06-26
[QUOTE=Isoss]Alright, my host doesn't support any but I can't find another one now. Anyway, I am not that much into these stuff, barely know what you were talkinga about. I konw lftp is for localhost ftping but I don't need that, I need to connect to the reall host. also not sure what passive and active mode do, and I don't konw how to set the passive mode as default! so I hope you'd help me in this what to do or may you recommend some webpage or thread that talks about that.
THanks.[/QUOTE]

lftp isn't for "local ftp", it's just another command line ftp program that is more advanced than the default ftp program.  try this:

lftp -u <username> <hostname>

that should do what you need.

---

