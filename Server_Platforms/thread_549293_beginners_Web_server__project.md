---
title: "beginners Web server  project"
date: 2007-09-12
forum: Server Platforms
---

### Post by firedancer on 2007-09-12
Hi , i want to starts a webserver , i have two pc 's one running ubuntu-studio with specs celeron 2.4 Ghz, 1 G ram, 30 G hdd , which i mostly use for recording and multimedia stuff and is not connected rite now

since switching to ubuntu  i reached to the point that i can build a pc from scratch which i did , pentium mmx 233 mhz, 2G hdd, 128 ram :) nothing serious no ! but i'm proud of it . runs dyne at the moment , but i now  fixed an issue which was preventing me from trying other distros , had to use two keyboards ...anyway.

the idea is to put up a server where i can put up info about lessons , methods, myself , etc.. 

i'm gonna start my last teaching practise period and want to start this project as a part of it , students and fellow teachers should be able to check all homework, a few documents, links ,   leave messages, etc  

i think my point is clear. 

:)

i have different cd's from alternate, feisty, xubuntu, edubuntu, 
yes i keep'em all , in case someone needs an alternative 

:)


OK then, ...thnx in advance

---

### Post by snyper82 on 2007-09-12
I've recently setup a machine with ubuntu server, LAMP option and installed SMF (Simple Machines Forums)  This works pretty and should be able to do what you need it to.    Here are some links:

[Installing LAMP Server]("http://ubuntuforums.org/showthread.php?t=223805&highlight=installing+webserver")
[LAMP Community Documentation]("https://help.ubuntu.com/community/ApacheMySQLPHP")
[SMF]("http://www.simplemachines.org/")

Sorry, I can't be of more help right now... I'm at work! :lolflag:

---

### Post by firedancer on 2007-09-12
OK, 

but i guess if i use my 'experimenting box' pc  i rather go without the gui , 
i don't wanna mess with my main desktop actually ,but it has some better specs if i'm gonna want/use a GUI being a noob :) ,


i'm gonna try to install the server edition and then do a sudo ap-get xubuntu-desktop and see what happens , 


suggestions are welcome :)

---

### Post by threeten on 2007-09-12
Check out the info here:

[http://users.telenet.be/mydotcom/howto/linux/xremote.htm](http://users.telenet.be/mydotcom/howto/linux/xremote.htm)

Why not run X remotely from your main desktop?

---

### Post by firedancer on 2007-09-12
Thank you for the reply, that will do it for now i guess :)

---

### Post by snyper82 on 2007-09-14
I never realized, I just have Gnome running on my server and VNC into it.  I like the idea of remote X better, uses less resources on the server.:)

---

### Post by juanhunglow on 2007-09-14
> **snyper82 said:**
> I never realized, I just have Gnome running on my server and VNC into it.  I like the idea of remote X better, uses less resources on the server.:)

I have a small (hobby) web server for wordpress, ampache, gallery2 and some file storage.  I use ssh along with webmin to administer the server and filezilla through sftp to up/download files to the server.  very easy to setup. check out the howtoforge for the perfect setup of ubuntu server as well as [http://www.webmin.com/]("http://www.webmin.com/") for webmin (Debian install)

I can't describe enough how much webmin has made server admin so easy, without it I probably would have given up on trying to run a server a long time ago.

Ubuntu LAMP + webmin can have you up, running , and doing admin within minutes.

I have no gui on the server and I don't use any remote X.

Good luck.

---

### Post by firedancer on 2007-09-15
thnx guys ! :)


mmmmm,   interesting !

---

### Post by firedancer on 2007-11-19
Hi, i installed django-python and i trying to get started (with some python ) but i'm not having succes with anything for some days now, 


i tried startes a project "mysite"

but when i need to connect to the djangoserver [http://localhost:8000](http://localhost:8000), it returns cannnot connect to host , 

can anyone help , 

i had a fresh kubuntu 7.10 install , so i don't know if it is related to that , i had a few crashes like adept-installer ,

what do i do , i'm four days busy trying to get back into learning some python programming , and because i have a small homeserver , i thought i start with this , 

little frus:(tarated  now

---

### Post by James79 on 2007-11-19
It doesn't sound like apache is even running, or that it isn't listening on that particular port. Try the following command:

```
nmap localhost
```

If that fails, it's probably because you do not have nmap installed. You can install it by doing:

```
sudo apt-get install nmap
```

---

### Post by firedancer on 2007-11-22
hi, diango comes with it's  own "development server daemon" or am i wrong, possible, 

well did not install apache, 

i have thttpd beta version running on my kubuntu 7.10 pc,since ubuntu install failed, and i'm getting used to it and want to do more with development/production ,who knows 

have to take care of studying first and then i'll try out some things again, 


my debian homeserver, well that's another story, cause since this morning IE won't/refuses connect to my server.

res://shdoclc.dll/DNSERROR.HTM#[http://mysite](http://mysite)  or IP    ,yep:mad::(:confused:

well this is a "common" problem to some but the first time for me,

and i just helped some folks with removing virus,spyware,etc (the pc which i check my server from) ,and now IE giving me this 

can anyone explain ,i know i have to google it and read more , one thread ended [CLOSED] without a proper solution to the problem.

i'll have to check from someoneelses pc  


firedancer

---

### Post by firedancer on 2007-11-22
> my debian homeserver, well that's another story, cause since this morning IE won't/refuses connect to my server.

res://shdoclc.dll/DNSERROR.HTM#[http://mysite](http://mysite) or IP ,yep

installed firefox on the xp pc , same issue 

i have a dyndns , tried with ip but i cant even acces my site using my  ip, so is someoen screwing over the network or what

i'll check if i can reach my server/site using a ubuntulivecd, which i used when i was helping ,threse ppl with removing malware,spyware,virus,worm, from this pc ,     i use it to see if all connection work on my server /site 

so now that's fixed or usable , who knows wether it still is compromised , which i can't tell  ,not an expert

it seems i'm not gonna get any help with this , since it's not a linux-centered question


:(

---

