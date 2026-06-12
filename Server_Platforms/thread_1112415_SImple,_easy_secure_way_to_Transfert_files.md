---
title: "SImple, easy secure way to Transfert files"
date: 2009-03-31
forum: Server Platforms
---

### Post by loudog23 on 2009-03-31
.........I Found all i needed, sry, can some moderator delete this thread plz...........

---Original message below---

Hi,
Ive been looking around the forums to find some information about setting up a place to share file with my friends. And, sorry to say, but the more i read the more i get confused. I'm still considering myself a Newbie in Ubuntu world, but starting to get the hang of it. Hopefully someone will be able to help me on this one.

_So here what i have:_
I have Ubuntu hardy 8.10
An Intel dual core running and connected 24/24 7/7
A ISP that sometimes change my ip address
And some extra space to share.

i when through this post: [http://ubuntuforums.org/showthread.php?t=79588&highlight=2nd+home](http://ubuntuforums.org/showthread.php?t=79588&highlight=2nd+home)

Then i saw around this "server" section of the forum, NOT to use **ftp** but instead use **sftp** for security reason.

So, here a few question:
1) If i create a new user for the ftp (or sftp), can i use my regular user to access, move and delete files inside this user folder?
2) How can i create an simple but secure ftp (or sftp)?
3) Is ther a way people can connect to my computer even if my IP change once i a while
4) sftp? as in Secure FTP?

Hope some can help me out, because ,sorry to say, but 9/10 times people don't reply to my thread on this forum so i end up trying stuff myself and i chrased my computer twice doing "the worng thing" and starting to be feed up of re-installing my system everytime. So please try to keep it simple, accurate and effective.

so, Please i need a simple, secure way to get something up where my friend _(and only them)_ could download and upload files into my system via the internet.

Thank you
Lou

---

### Post by hyper_ch on 2009-03-31
I prefer to use openssh-server, mysecureshell and chroot the people I give access into their home folder and not allowing them to connect through ssh only, only through sftp (e.g. winscp).

quite simple to setup as you can use system users and change their shell to mysecureshell (once you did setup mysecureshell correctly).

Well, if your ip changes you a service like no-ip.com or dyndns.org. If you're behind a router then very likely the router already supports such a dynamic ip service and you'll also need to portforward port 22 then from the router to your "server".

---

