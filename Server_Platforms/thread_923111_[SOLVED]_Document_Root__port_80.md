---
title: "[SOLVED] Document Root  port 80"
date: 2008-09-18
forum: Server Platforms
---

### Post by gishaust on 2008-09-18
Hello ubuntu fans

I am using  Apache2, I was wondering is there any way to upload files to my root document folder through port 80 or through ssl.

---

### Post by qstraza on 2008-09-18
You want to upload to your http folder via port 80?
Well if you run apache on other port than 80 and you run ftp on 80, than its possible:p
Or you can write a php for uploading files, but why do you want to do that?

Do you have ssh access and access to the http dir?

---

### Post by windependence on 2008-09-18
You should probably be using ssh or scp for file transfer. From a Windoze box you can use WinSCP which will allow you to drag and drop files securely. From a Liinux host you can just open Nautilus or Konqueror and sftp the files from the GUI.

Of course you can also use SCP from the command line.

-Tim

---

### Post by qstraza on 2008-09-18
You can use Filezilla rather than WinSCP, dunno which one is better though...

---

### Post by windependence on 2008-09-18
I think it's a matter of personal preferece my self. I just prefer the simple two pane interface of WinSCP.

-Tim

---

### Post by gishaust on 2008-09-18
I have someone using my webserver for there own domain and I want to be able to give them access without them seeing the whole machine. I do use ssh but I am not sure about giving them access. Is there a way to create a new user that does not have sudo privileges and can not scan around the server if I gave them ssh access.

---

### Post by qstraza on 2008-09-18
sure, useradd ;)
and make valid shell. So they can use scp.

Well if you dont trust that guy, you should not give them ssh access. Its better to install a ftp server and let them use it for copying and disable shell logins for that user...


Or maybe you can add user and make valid shell and in sshd conf disable that user, dunno if scp will work in this case, if it does, this is the optimum solution ;)

---

