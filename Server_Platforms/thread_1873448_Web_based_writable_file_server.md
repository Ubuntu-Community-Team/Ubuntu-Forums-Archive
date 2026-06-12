---
title: "Web based writable file server"
date: 2011-11-01
forum: Server Platforms
---

### Post by perrti-y02 on 2011-11-01
Hello,

I am looking to set up a web based file server than can be written to by any machine with internet access. I essentially want to be able to do what Dropbox, or Ubuntu One does, but I don't want to pay for more storage space. I do realise that it is probably not going to be simple, but I want to learn more about server applications as well as solve my problem.

It is important that it is secure to a fairly high level. I am not looking for anything TOO strong, but I don't want the files to be easy to take off the server without authentication.

I think FTP is probably the starting point, but I read that it isn't the most secure thing in the world. Is there a way to do it securely? I do know that the port for HTTPS is not blocked by my ISP, but I don't know if that would help.

Cheers,

perrti02

EDIT: It needs to be supported by Windows at the client end, since most of the use will be by a Windows machine and installing extra software is less than ideal.

---

### Post by cj13579 on 2011-11-01
You could use SFTP and use a client like FileZilla or WinSCP on the client side.

---

### Post by aeiah on 2011-11-01
there are several cloud storage type applications you could use but i'd probably do it with [unison](http://www.cis.upenn.edu/~bcpierce/unison/).

it acts more like rsync than a constantly synchronising cloud like dropbox. you can set it up in a [star configuration](http://www.cis.upenn.edu/~bcpierce/unison/download/releases/stable/unison-manual.html#usingmultiple) though for multi-client sync to a main server.

you could then make the sync folder on the 'hub' available over https with apache and the like if you wished to access the files on computers you haven't set unison up on

unison transfers over ssh, so you can use keypairs to make things secure. you could set a cronjob to sync files every few minutes on your devices or whatnot.

there are probably packages that mimic dropbox though, but where's the fun in that? :p

---

### Post by kustomjs on 2011-11-01
make sure you dont run into problems with SFTP like I am having when you put your users into there own group called as webmasters. Because I am having that issue right now when you place them in group called webmasters the SFTP client cant connect to the server but you place them in users group and try to connect SFTP it will connect just fine.

---

### Post by perrti-y02 on 2011-11-01
Doesn't SFTP need a SSH client? I was looking at something that con be done through a webpage.

---

