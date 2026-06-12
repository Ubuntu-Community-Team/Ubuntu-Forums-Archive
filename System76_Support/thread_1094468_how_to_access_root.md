---
title: "how to access root?"
date: 2009-03-12
forum: System76 Support
---

### Post by elphaba on 2009-03-12
can't login to root on my (relatively new - 3 months old) Pangolin laptop system 76 Ubuntu 8.10.
I haven't tried before. I have successfully done updates through the gui sysadmin interface using the "admin password".  I thought admin password would be the root password but I guess not.  
I used to be (5 years ago) an administrator on linux (not ubuntu) and was interested in looking around, i.e. who is in the sudoers file, if there are any parameters that can be adjusted for the firewall, what kind of firewall, hope to do some Perl development - realizing one shouldn't make changes unless one is VERY serious and feels VERY sure but still... 

how can I login to root (or su - superuser)?  Did I miss something when I first brought this up?  another password?

---

### Post by SunnyRabbiera on 2009-03-12
By default Ubuntu disables root, instead all administration is done with sudo.
Ubuntu is not like most traditional linux distros where the root is enabled and can be exploited.

---

### Post by thomasaaron on 2009-03-12
Here is some valuable information about root in Ubuntu...
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jdb on 2009-03-12
> **elphaba said:**
> can't login to root on my (relatively new - 3 months old) Pangolin laptop system 76 Ubuntu 8.10.
I haven't tried before. I have successfully done updates through the gui sysadmin interface using the "admin password".  I thought admin password would be the root password but I guess not.  
I used to be (5 years ago) an administrator on linux (not ubuntu) and was interested in looking around, i.e. who is in the sudoers file, if there are any parameters that can be adjusted for the firewall, what kind of firewall, hope to do some Perl development - realizing one shouldn't make changes unless one is VERY serious and feels VERY sure but still... 

how can I login to root (or su - superuser)?  Did I miss something when I first brought this up?  another password?

It's your system & it's your decision.
I know some folks cringe at a root login, but having cut my teeth on unix in the early 80's, I can't imagine not having one.

sudo su
passwd

jdb

---

### Post by betrunkenaffe on 2009-03-12
You can also sudo to change the password on root (with user auth) to something you know.

---

### Post by 3Miro on 2009-03-12
I think it was on one of the first Ubuntus that was running that I enabled root by editing etc/passwd. You should not be doing this. I got root, but soon afterwards I reinstalled the entire thing.:D

Sudo as opposed to root took some time for me to transitional (OK I have been Unixing only since '00, but still), yet it works fine. I can still do all the things I want and sudo wants a password only the first time. Overall, you will be better protected from yourself (so you don't have to reinstall).

---

### Post by elphaba on 2009-03-13
Thanks very much for the good info. I read the article posted about root-sudo,  can't say I don't agree with it but still..if I end up developing scripts for the system, I'm sure I will find not having direct access a bit of a pain.  Guess I will wait until the day I actually write the scripts and need it before considering it again.

I am amazed at how easy it is to update programs. I had images of what I used to do in my head and this is NOTHING compared to that.  I suspect that some of you guys don't know the headaches you've missed but then, I guess that is what they are striving for when they want to recommend ubuntu for everyone's desktop.  (If I sound like a dinosaur, I am - we need a forum just for us so we can wax nostalgic...LOL)

  Thanks again. Guess I need to browse the help files a bit closer...

---

### Post by Eldera on 2009-03-13
I am very new to Linux, have used Ubuntu about a month. 

By coincidence I read about root in Keir Thomas' manual just before I read this thread. 

elphaba, Mr. Thomas' remarks on Working with Root Powers, p77-78, might interest you. 

The handbook is available at no charge as a PDF download from this site.
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

Good luck with your script writing.
Eldera

---

### Post by betrunkenaffe on 2009-03-14
Anyone know how to disable root once enabled? It doesn't matter anymore since I wiped Ubuntu off that machine (put Dreamlinux on) but would be nice to round off the knowledge in this thread :)

---

### Post by Eldera on 2009-03-14
betrunkenaffe, I am very new at Linux but have been reading instruction books for a long long time. 

There was one description of disabling root in the tutorial thomasaaron referenced [post]6884539[/post]and two different descriptions in Keir's handbook that I was reading [post]6886951[/post] (Different from the tutorial)

I think it might depend on how you went into root in the first place. Have a nice day. Eldera

---

### Post by riseringseeker on 2009-03-14
> **betrunkenaffe said:**
> Anyone know how to disable root once enabled? It doesn't matter anymore since I wiped Ubuntu off that machine (put Dreamlinux on) but would be nice to round off the knowledge in this thread :)

According to the link Tom provided, which is a Ubuntu community document, thus should be trustworthy the procedure is:

[quote=RootSudo]

Re-disabling your root account

If for some reason you have enabled your root account and wish to disable it again, use passwd -l root in the terminal. The bug with passwd -l root was fixed in the package landscape-client - 1.0.25-0ubuntu0.9.04 so you can safely use it as a proper way of re-disabling your root account. [/quote]

---

