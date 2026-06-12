---
title: "Argh! FTPing in from IE7 shows root folder, not FTP folder!"
date: 2007-05-17
forum: Server Platforms
---

### Post by fyl2u on 2007-05-17
Help!!

Got a bit of a panic on... forgive me, but after setting up vsftp on my ubuntu machine on our corporate intranet, I can access the FTP directories fine from the XP computer on my desk using IE6, but when I get my colleagues at another site to try it (still on our VPN/intranet) with their IE7 XP machine, instead of them seeing the FTP folder, they see the ROOT folder!!!

If they click on the folders inside the root folder they just get error messages, so they can't do anything while they're in there, but it's a bit worrying, and also obviously isn't giving them the required FTP access.

What's going on?  Any ideas?

---

### Post by fyl2u on 2007-05-17
OK, I found a conversation on another forum about this and the gist seems to be that it's a problem with IE7.

I tried altering the vsftpd.conf file so it was using chroot and pico'd a vsftpd.chroot_list and typed in the 2 test usernames just like this:

testuser1
testuser2

(I had been surprised to find that the vsftpd.chroot_list was previously empty and there were no instructions of how it should be properly formatted).

Would I need to restart vsftpd after doing this or would it pick it up automatically?

Anyway, I didn't restart it, but I tried to access the ftp again with IE7 and got the same ROOT folder again, not the expected FTP folder, so the chroot idea did nothing.

Following their instructions, I tried using that same machine but using Windows Explorer rather than IE7 and it worked fine... FTP folder as expected.

Have I done the chroot thing correctly?

If so, is there a way to make this do what it's supposed to do, for IE7?

---

### Post by fyl2u on 2007-05-17
haha..... my mistake - setting up the chroot DOES work for IE7 after restarting the vsftp daemon thus:

sudo /etc/init.d/vsftpd restart


^^^ Check me out, 6 days of linux abuse and I'm talking like a local :-D :-P

---

