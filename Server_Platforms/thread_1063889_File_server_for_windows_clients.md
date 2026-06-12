---
title: "File server for windows clients"
date: 2009-02-08
forum: Server Platforms
---

### Post by fourthofjuly on 2009-02-08
[COLOR="DarkOrange"]hi,
we have 3 computer labs in our school each with 30 machines running windows xp prof. sp2 on 2 independent peer-to-peer networks. 

the machines are used by students and staff. we face the following issues:

1) security of the data
2) virus infection
3) user data has been scattered all over the place

we plan to setup a central file server with backup facility so that all files created at clients are stored to the server.

i am new to linux at server level, even though i use it at home. I know that linux will work as a great file server, but don't know how to go about it.

please give us a step-by-step guide so that our users can login from windows xp using their passwords and access their files from the ubuntu server. 

i have a very vague idea that i will need samba and putty, but don't know how to get them working?

any help will be greatly appreciated.

fourthofjuly[/COLOR]

---

### Post by linux_tech on 2009-02-08
here are a few guides to help you get started 
[https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/8.10/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.10/serverguide/C/network-file-system.html)
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)

---

### Post by HermanAB on 2009-02-08
Since there are a whole bunch of machines, you should probably install a Samba domain controller.

The best guide is on the Samba web site.  Read the Official Howto.  There is also a guide specific to Ubuntu:
[http://us1.samba.org/samba/](http://us1.samba.org/samba/)


Cheers,

Herman

---

### Post by fourthofjuly on 2009-02-11
> **linux_tech said:**
> here are a few guides to help you get started 
[https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html](https://help.ubuntu.com/8.10/serverguide/C/samba-fileserver.html)
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://help.ubuntu.com/8.10/serverguide/C/network-file-system.html](https://help.ubuntu.com/8.10/serverguide/C/network-file-system.html)
[http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/)
thanks, i will try those links for sure

---

### Post by fourthofjuly on 2009-02-11
> **HermanAB said:**
> Since there are a whole bunch of machines, you should probably install a Samba domain controller.

The best guide is on the Samba web site.  Read the Official Howto.  There is also a guide specific to Ubuntu:
[http://us1.samba.org/samba/](http://us1.samba.org/samba/)


Cheers,

Herman
thanks, but we wish to keep things very simple, so perhaps no domain controller for now...

i read about ebox, which seems to be easy & interesting. any ideas?

---

### Post by HermanAB on 2009-02-11
Using a domain controller is actually a simplification (in management effort).

If you want to do all of this with a simple point and click, then you need to use Mandriva or Suse.  With Ubuntu, it will be a bit of an adventure to set up.

Cheers,

Herman

---

### Post by jimv on 2009-02-11
I'm going to agree with Herman.  Setting up a domain controller will save you some headache in the long run.  Users and groups are all managed on the server, rather than on each individual machine.  Since you have XP Pro, all the machines will hook up to a domain just fine.

The best thing to do would be set up an Ubuntu server with a few XP machines to test with, then once you get the domain controller and file sharing set up correctly, hook it up to the rest of the machines.

---

### Post by bigbearomaha on 2009-02-11
Not only will it keep user info centrally controlled, it will allow your users to log in and have their data available to them regardless of what machine they log into.

Big Bear

---

### Post by fourthofjuly on 2009-02-12
thanks a lot to all of you...

i will go with the domain controller system as per your suggestion. we certainly will like to have easy and very simple administration.

will get back to you for any troubleshooting help, if required.

regards,

devang.

---

### Post by fourthofjuly on 2009-02-14
[COLOR="DarkOrange"]
hi,
well, i installed a customized ubuntu server with ebox and also installed ubuntu-desktop for GUI, since i am more comfortable with it.

i have setup the server for file sharing. the test client machine can access home folder files located on the server successfully.

now, i would like to know if using putty there is some way i can force my windows users to automatically save their files to their respective directories on the ubuntu server, instead of saving the files on xp client machines?

please help...

regards,

fourthofjuly.[/COLOR]

---

### Post by hyper_ch on 2009-02-14
have a look at this howto. It's very extensive and works excellent:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by fourthofjuly on 2009-02-14
> **hyper_ch said:**
> have a look at this howto. It's very extensive and works excellent:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)
thanks,

i will go through it and reply soon.

---

### Post by fourthofjuly on 2009-02-14
hi,

one more question...

actually i am looking to setup a network where all xp users (clients) login to  access their respective directory of files stored on the ubuntu server?

no user should be allowed to save files on xp client machines, even though all clients machines have a hard drive...

possible?

& is this what domain controller setup will facilitate?

please clarify...

---

### Post by hyper_ch on 2009-02-14
you need to set that in WinXP. Altering their default profile folder to the server.

---

### Post by fourthofjuly on 2009-02-14
> **hyper_ch said:**
> you need to set that in WinXP. Altering their default profile folder to the server.
could you please explain how? know that this is a xp-specific question, but please guide me... 

suppose i setup 10 users and give each one a username and password from server, can they login from the clients using putty when xp loads and access their files on server?

also, can user-a login from any of the 90 xp machines, say system-x, and use his files?

---

### Post by hyper_ch on 2009-02-14
no clue... never done anything like that on windows.

---

### Post by fourthofjuly on 2009-02-14
> **hyper_ch said:**
> no clue... never done anything like that on windows.
thanks, your help is much appreciated...

hope someone else can guide me...

---

### Post by fourthofjuly on 2009-02-15
[COLOR="DarkOrange"]**anyone, please?**[/COLOR]

---

### Post by hyper_ch on 2009-02-15
it is not appropriate to bump a thread within 24h after your last post.

---

### Post by fourthofjuly on 2009-02-15
> **hyper_ch said:**
> it is not appropriate to bump a thread within 24h after your last post.
[COLOR="DarkOrange"]lack of awareness... 

please accept my sincere apologies...[/COLOR]

---

### Post by fourthofjuly on 2009-02-17
> no user should be allowed to save files on xp client machines, even though all clients machines have a hard drive...

i was going through a samba setup guide, where it suggested that i could make the xp clients logon to the samba server domain with a username and password, instead of making them login to the local machine...

if i can give a password (not known to others) on all xp machines, then all users will be bound to login to the samba domain from xp clients using their own username and password... this way they cannot save files to the local hard drives?

please suggest if i have understood it correctly and elaborate since this is exactly what i wish to have...

---

### Post by jimv on 2009-02-17
I think what that's talking about is Windows "Roaming Profiles".  Everyone's My Documents, Desktop, Application Data, etc is stored on the server instead of the individual machines.

---

### Post by fourthofjuly on 2009-02-19
> **jimv said:**
> I think what that's talking about is Windows "Roaming Profiles".  Everyone's My Documents, Desktop, Application Data, etc is stored on the server instead of the individual machines.
thanks, tested successfully today...

asked win xp to join my ubuntu ebox server domain, then gave my username and password of domain when prompted, rebooted xp and it now allows me to either login to the server domain or login to the local machine...

tested with 2 different user accounts... in xp, only the user's files stored on the server are now accessible to him once he logons to the domain... 

however he can even save files locally on the client, which i don't want to allow... he should be forced to save files to his own folder on the server... 

hope someone can understand what i want please?

---

### Post by fourthofjuly on 2009-02-19
one more question... 

for safety of our xp clients, we want to install clamav on the server so that it can scan all files stored by users in their folders on server...

now, there is no realtime protection in clamav... so can we write a script so that every hour clamav automatically  scans user files coming from xp clients?

please help...

---

### Post by Raunok on 2009-02-19
> however he can even save files locally on the client, which i don't want to allow... he should be forced to save files to his own folder on the server... 

hope someone can understand what i want please?


I think what you need is a program for Windows called Tweak UI- its free and readily available 

[http://www.download.com/Tweak-UI/3000-2072_4-10002117.html](http://www.download.com/Tweak-UI/3000-2072_4-10002117.html)

you can basically make the PC do anything you want it to do, i would recomend putting this on one of your XP test boxes and trying to tweak it a bit before going crazy with it.  

hope this helps.

---

