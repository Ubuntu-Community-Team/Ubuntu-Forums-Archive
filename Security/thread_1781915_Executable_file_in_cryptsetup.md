---
title: "Executable file in cryptsetup"
date: 2011-06-14
forum: Security
---

### Post by CharlieDelta on 2011-06-14
Hi
I am  not new to ubuntu, but I am sorry, my knowledge is like a newbie.
When I installed ubuntu,I used the encryption option. I was checking in lib/cryptsetup and I noticed that there is executable (application/x-executable)  file called "askpass". Also, in lib/cryptsetup/scripts there is a file called "passdev". Are these supposed to be there? I believe they are windows files,because the icon is a blue diamond with gears. My concern is that someone is trying to find my login password.

Any help would be appreciated. I am a little paranoid.:)

Thanks
Charlie

---

### Post by Dave_L on 2011-06-14
I don't think that's a problem. Those two files are contained in the package "cryptsetup".  I have them too.

[http://packages.ubuntu.com/lucid/i386/cryptsetup/filelist](http://packages.ubuntu.com/lucid/i386/cryptsetup/filelist)

---

### Post by CharlieDelta on 2011-06-14
Hi
Sorry if this thread is repeated. I tried to post last night but didn't see it up.

I am not new to Ubuntu, but I am a newbie when it comes to knowledge.

I am running 10.04 LTS Lucid Lynx.

When I installed 10.04 LTS, I recall that I was given the option to encrypt my whole hard drive which I took.I do not know how to confirm that this has actually happened, or if the encryption is "on".
Could someone please tell me how to check the status of the hard drive encryption?

Also, I was reading  in one of these forums that the encryption does not really protect my data from being observed while I am on-line. So, I get that if someone steals my laptop they can not  boot off a cd and start poking about my hard drive, as it is encrypted. Ok cool. But that does not protect me from someone snooping about while I am online because I have logged in and everything is open to me. Is this correct?

The posting on the forum also said that someone could observe my password and suggested how it could be done. I checked my lib/cryptsetup and found a "executable (application/x-executable)"  as indicated by file properties , called "askpass". As well, found a "executable (application/x-executable)" in lib/cryptsetu/scripts called "passdev". Both these files wouldn't open when double clicked and show under properties permissions that I am not the owner. Also, the icon is a diamond (square at 45 degrees)
with the image of gears inside. Are these windows executable files?
Are these file ok to be there?

People do know that I am running linux, so the general wisdom of safety through obscurity is probably a bad assumption I my case.

Also, I have been poking about possibly dubious sites and playing with steganography (which I can't figure out). Nothing mischievous, more DaVinci Code type fun. Perhaps I have been playing with mischievous types and not known it. I did notice that gnome changed appearance spontaneously, but that could be something else.

Any help or thought very welcome.

Thank you.

Charlie

---

### Post by CharlieDelta on 2011-06-14
Thanks for your reply Dave. Didn't notice that this post had gone threw and posted again. Anyway, that is comforting to know that it is likely "normal".

---

### Post by Thewhistlingwind on 2011-06-14
Blue file with gears? No, thats a Linux executable dude.

---

