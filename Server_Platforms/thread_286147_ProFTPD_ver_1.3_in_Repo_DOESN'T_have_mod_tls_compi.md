---
title: "ProFTPD ver 1.3 in Repo DOESN'T have mod_tls compilied it it????"
date: 2006-10-27
forum: Server Platforms
---

### Post by dannyboy79 on 2006-10-27
To whoever can help me. I have been struggling with FTP using TLS ever since my Ubuntu machine updated my Proftpd to version 1.3, which was about 2 or 3 weeks ago I think. It all started when I did a restart to my server and noticed that it didn't ask me for a Passphrase to restart the server like it did prior to the update. I didn't remove the encrytion from the server.key file either as I want it very secure, so I thought this was very strange. Anyway, I have gone over Frodon's How-To over and over and have deleted and recreated the keys, I have reinstalled Proftpd several times, I have read a little about mod_tls for Proftpd, I have read a little about ssh, openssl, etc etc and no matter what, ever time I tried an ftp client, it would just never use tls. I have learned that TLS is suppose to occur and connect prior to it asking for a username and password, hence why it'll then send the username and password encrypted. Finally I found this website that told me I could type proftpd -l to inform me of what modules were compiled into proftpd. I figured, I am curious so I'll try it. I did and this what came back, daniel@UBUNTU:/var/log/proftpd$ proftpd -l
Compiled-in modules:
  mod_core.c
  mod_xfer.c
  mod_auth_unix.c
  mod_auth_file.c
  mod_auth.c
  mod_ls.c
  mod_log.c
  mod_site.c
  mod_delay.c
  mod_dso.c
  mod_auth_pam.c
  mod_readme.c
  mod_cap.c
  mod_ctrls.c

Then on the same website, another user posted what his version (1.2.10) had compiled in it, they were,
# proftpd -l 
Compiled-in modules: 
mod_core.c 
mod_xfer.c 
mod_auth_unix.c 
mod_auth_file.c 
mod_auth.c 
mod_ls.c 
mod_log.c 
mod_site.c 
mod_ctrls.c 
mod_ratio.c 
mod_readme.c 
mod_auth_pam.c 
mod_wrap.c 
mod_tls.c 
mod_sql.c 
mod_sql_mysql.c 
mod_quotatab.c 
mod_quotatab_sql.c 
mod_quotatab_file.c 
mod_cap.c 

So, I am wondering, have I been trying to enable TLS for my ftp server when mod_tls isn't even a module that is compiled in the 1.3 version that is in the repo's????? Can someone more knowledgable help me out with this?? If this is true, why on earth would the Ubuntu repo's admins, compile something without the secure modules in it or am I wrong in what I am saying? I am a newbie, so I would like to learn more about this stuff. Please help me, thanks.  :-k


I JUST COMFIRMED THIS WITH FRODON, the author of the ProFTPd How-to, he says he is going to inform the developers or do what ne needs to.

I REALIZED THAT THIS IS AN ISSUE FOR DAPPER ONLY IF YOU HAVE THE BACKPORT REPO'S ENABLED IN YOUR SOURCES.LIST, otherwise this only affects Edgy.

---

### Post by btboudreaux on 2006-11-22
was this ever fixed?

---

### Post by dannyboy79 on 2006-11-22
what do you mean by was it ever fixed?? it's not broken. it's just that the version that ubuntu has in their repo's doesn't have tls support compiled in. so if you want it, you either have to use the version that dapper uses or you have to compile it yourself. i have compiled it myself if  you want it but I didn't compile in mod_sql or mod_sql_mysql. I am going to though today if you want it after I do it. the bug was filed you'll have to see if ubuntu compiled another one and replaced the 1 on the repos. you can find out by doing a sudo aptitude update and then do a sudo aptitude install proftpd and then when it's on your machine you would do sudo proftpd -l to see what was compiled into that version.

---

### Post by btboudreaux on 2006-11-24
Yeah I know it's not broken per say, but it does have a security hole in it if you want a secure FTP. Does the download on the official site have mod_tls compiled in it? Seems like it does.

---

### Post by dannyboy79 on 2006-11-29
what download on what official site are you referring to? apparently the version 1.3 within Edgy repo or backport repo for dapper does have mod_tls.c support but it's enabled using the new dso thingy. dso is dynamic shared object and the version within the repo has mod_dso.c compiled in so you just need to add one line at the top of your proftpd.conf, it should read Include /etc/proftpd/modules.conf and then just make sure you edit that file and comment out any modules you DON'T want loaded. (the file is /etc/proftpd/modules.conf) leave everything else alone and just comment out anything you don't want loaded. It's pretty coool how proftpd did this, I only found out because of Frodon, he is the man. He wrote up an awesome guide within this forum on how to create a secure ftp server using proftpd.

---

