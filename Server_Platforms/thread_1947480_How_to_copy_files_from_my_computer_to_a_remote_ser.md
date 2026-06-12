---
title: "How to copy files from my computer to a remote server"
date: 2012-03-26
forum: Server Platforms
---

### Post by Chanpa on 2012-03-26
(I realise it's not ubuntu but the solution might work on both)
Hi,
I've done a website for a small company and I got access to their server to upload it. It's running:
```
cat /etc/issue
CentOS Linux release 6.0 (Final)

uname -a
Linux fsyd-linux01.fsyd.local 2.6.32-71.29.1.el6.x86_64 #1 SMP Mon Jun 27 19:49:27 BST 2011 x86_64 x86_64 x86_64 GNU/Linux
```

What I want to do is to copy my folders with the site to their server on /var/www/html/finnskatten.

I'm using Windows 7 Ultimate x64.

I'm using putty / pscp.

I tried this with pscp:
```
C:\Users\Johan>pscp -r c:\mowes_portable\www\ ****@**.***.**.***:/var/www/html/finnskatten
```
With that I get permission denied on all files/folders it tried to create.
So I tried connecting in putty and still got permission denied when I tried to create files/folders so I figured I needed to run sudo before the command and it worked.
However I don't know how to copy a folder on my computer to the target server in putty.

I tried using scp in putty like this:
```
scp -r C:\mowes_portable\www\ ****@**.***.**.***:/var/www/html/finnskatten
```
But it didn't work, it just replied: Usage: scp [[options etc]].

TL;DR:
I either have to know **how to grant pscp permission when it from my computer** or **how to copy files from my computer to their server using putty(with scp for example)**

Regards,
Chanpa

---

### Post by arrrghhh on 2012-03-26
Why not use WinSCP?  Works great for me.

If you're having permission problems, you'll either have to enable a root SSH account, or give your user rights - either with chown to change ownership or chmod to grant more access.  This may cause other issues, so be wary of changing any permissions.

---

### Post by utnubuuser on 2012-03-26
Filezilla

---

### Post by Chanpa on 2012-03-26
I downloaded WinSCP and got same permission error. What I did to solve it was I used pscp to copy it to my home directory on the server and then used SUDO cp in normal putty to move it to the /var/www/html/finnskatten folder, thanks for help!

---

### Post by arrrghhh on 2012-03-26
> **Chanpa said:**
> I downloaded WinSCP and got same permission error. What I did to solve it was I used pscp to copy it to my home directory on the server and then used SUDO cp in normal putty to move it to the /var/www/html/finnskatten folder, thanks for help!

Either way it's permissions then.  You can either change the rights, or do what you did :p.

Mark the thread SOLVED using the 'thread tools' drop down ;).

---

### Post by papibe on 2012-03-26
EDIT: I think you figured it out already. Sorry for late post.

Hi Chanpa.

Most likely you can't copy directly to /var/www because you would have to use the root user (scp ... root@...).

By default most distribution block both login access, and remote access (ssh) to the root account, and only allow you to became root by using sudo. 

The simplest solution would be to copy the files in 2 steps:
- copy them to your user directory, and then,
- connect using Putty and move or copy the files to /var/www

Although I would not recommended, you can change the settings and allow scp to the root account.

Let us know if you need more help with that.
Regards.

---

