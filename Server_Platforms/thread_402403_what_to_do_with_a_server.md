---
title: "what to do with a server?"
date: 2007-04-05
forum: Server Platforms
---

### Post by jmvidalvia on 2007-04-05
Hello everybody, 
I started with Ubuntu one year ago: I installed and used kubuntu dapper, ubuntu edgy and now my main system is xubuntu, althoug my machine is powerfull: I love speed and simplicity!. I also run XP as guest in VMWare. I pushed 50 salesmen in my company to use Ubuntu in their laptops, and I am very proud of it (and they work fine!). I love console as well. At home my family shares a laptop with Dapper, and are also proud of it! Just to summarize, I am a total ubuntu/gnu/linux supporter, although I dont work in IT and never studied computing.
Well, I am now considering to go a step ahead: my own linux-server! (at home) but am I still wondering if that makes sense in my case. Thats why I wrote some ideas I have. I would  appreciate to have comments about how easy it would be to make them run.

1- Share files and make laptop backups: I supose the best option would be Samba if anyone in my family uses windows, but...if they use Ubuntu, which would be the best way to share files? Samba, ftp, nfs?
2- Share the printer: I assume cups will work fine.I already use it with success.
3- Manage the server: I've read about ssh. Everybody agrees it is the best system, but, would I be able to manage it also out of my router, from my office, for example?
4- Will it be difficult to acces my files from outside? Which would be the best way: ssh as well?
5- Does it make any sense to mount a proxy in that server?
6- My children are 11 and 8 years old: I would like soon to mount a parental control for them. Would a server be usefull for that purpose?
7- If they insist (some day) in using windows, can I use the server as an antivirus for their laptops?
8- What about multimedia? can I save in the server songs and films an watch or listen to them throught the LAN using WIFI? What about TV?
9- Any way to manage Amule from the server. I would like to leave it always open, instead of laptops, but how to start and select files if I dont' have GUI in the server?
10- Any need to change the standard configuration of iptables?
11- I use gmail: any practical need to configure a mail-server in my machine?
12- I will not use the server as a web-server by the moment, I think.
13- And finally, hardware. My experience is that 99% of my problems with Linux (quite a lot, I can say) came from hardware compatibility. Which is the safest way to check that?
14- I would buy a new computer and I suppose I can choose the components: I understand it must have good hard drives (one or two?), good fans, but no need of extra RAM (which should be the amount of RAM?) and no need of super graphics-card.
I suppose no need of screen and keyboard but, ¿how to make the first instalation? I supose I'll have to borrow those parts in the begining..
15- Any other funny uses of a server at home?

Sorry for so many questions: I know this is not the right way to post, but it was the only way to put order in my head...

Many thanks!

PS: I already read the Ubuntu-Server guide, 	;-)

---

### Post by stalker145 on 2007-04-05
Wow, quite a few questions. But that's good. You're going into this thinking of the possible uses, problems, and solutions. I'll respond where I can, being rather inexperienced myself.

> **jmvidalvia said:**
> 1- Share files and make laptop backups: I supose the best option would be Samba if anyone in my family uses windows, but...if they use Ubuntu, which would be the best way to share files? Samba, ftp, nfs?
I don't know if it's best, but I use Samba on my server. I have my desktop/server, one Ubuntu Laptop, and one Windows laptop on my network. Samba shares between both Windows and Ubuntu nicely in my case.
> 3- Manage the server: I've read about ssh. Everybody agrees it is the best system, but, would I be able to manage it also out of my router, from my office, for example?
Personally, I use a combination of WebMin and VNC. VNC is when I am at home on my LAN and WebMin is the HTTPS interface when I'm away. I'm not sure (never tried it) if WebMin can work without a GUI, though I don't see why it wouldn't.
> 4- Will it be difficult to acces my files from outside? Which would be the best way: ssh as well?
Once again, here I use WebMin. It can do almost anything and I have not become fully comfortable with the command line. I don't see why SSH wouldn't work as long as you did the proper forwarding in your router and set up your SSH server.
> 6- My children are 11 and 8 years old: I would like soon to mount a parental control for them. Would a server be usefull for that purpose?
It is my understanding that you can rather easily set up a filter/parental control using a Linux server. All you would need to do (haven't done it, but read about it) is make sure that the other computers look to the server for proxy settings.
> 8- What about multimedia? can I save in the server songs and films an watch or listen to them throught the LAN using WIFI? What about TV?
I don't know about TV, but I keep all of my music and video on my server and stream it to my wireless laptop. I can't surf the 'net all too well when I'm doing that, but it's a sacrifice I'm willing to make ;)
> 11- I use gmail: any practical need to configure a mail-server in my machine?
No need. Just set up your E-mail client to pull your mail from GMail. It's easier (for me) to read and manipulate and everything stays on GMail for later.
> I suppose no need of screen and keyboard but, ¿how to make the first instalation? I supose I'll have to borrow those parts in the begining..
That's what I did. I set up my system and removed all the ancillary stuff. I ended up putting it on later because I had an issue with my file system breaking, but it's your call. 

I hope you have fun, are successful, and learn a lot. Check back if you run into problems or have ideas for others.

---

### Post by pppetter on 2007-04-05
You can absolutely use your server as a central music/movies archive, though, if a couple of desktops+wifi+movies might not be a great idea(wifi bandwidth is generally not that good). NFS has better performance than samba, so if every desktop is running linux - then that's the way to go.

If you want to have access to the server from outside your LAN, just set port 22 to be forwarded to the server. Then you can access the server with SSH, even from a windows machine (use a client called PUTTY). You may also transfer files with SSH(although inside the LAN, use NFS), just log in with your SSH account (from windows machines, use FileZilla).
If you forward that port, I would advise installing Fail2Ban, so that if someone tries to break your user/password, they'll be banned after 3 incorrect entries.

As for hardware, I really don't think that it will be a big problem, since the server only needs standard equipment... 
And hey, just grab a lame screen from the local refuse center (don't know what it's called in english, but here in sweden it's called Grovsoprum and there is one for every block), I did that for my server. ;)

---

### Post by elst on 2007-04-06
SSH is (arguably) the basic network service, along with HTTP. If the desktops are Linux then you may not need to use any other service for regular file access, as you can use SSH from KDE etc. in pretty much the same way as other protocols. NFS or Samba are better to share the same files between multiple users, or for large files, but are more complex and only work if both the client and the server are on the same network. SSH connections will work from anywhere, which makes them particularly useful for laptops. Streaming media is a special case, as it's highly time-sensitive, and so works best with a lot of bandwidth and specialized network protocols. Today's wireless connections probably aren't quite fast enough.

Web proxy servers provide three functions - they reduce bandwidth consumption, they can filter unwanted data, and they can log access by users. For a small network with broadband access it isn't necessary to have one, but with children, it's a good idea to filter Web access a little. 

If you have email and Web filtering you probably still need anti-virus on the Windows systems themselves, as the sheer volume of infected emails and malware on the Web is so high that some will get through. You also have to consider the risk of somebody copying infected files on to the system from a disk or pen drive.

> **jmvidalvia said:**
> 
Sorry for so many questions: I know this is not the right way to post, but it was the only way to put order in my head...


If you haven't already, try logging in to the Ubuntu IRC channels - there are usually experienced people around that you can talk to in real time about any questions or issues that you have.

---

### Post by bikeboy on 2007-04-06
Having done some of this myself I can say that you might not get it right the first time, expect things to break and take a bit of effort. But once it's working, it is beautiful and "just works" :)

SSH is great, I use it as my main way to admin, with webmin being there for help in areas I don't know as well. But if you want to use SSH from outside your home network, do some reading up on how to secure your SSH server, key-based logins for a start.

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Not sure about managing amule, but you might want to look at torrentflux and see if it's something you would like.

For hardware, there's no need to splash out. Mine is an AMD Sempron 2600+ with 256mb of ram and that's plenty (I'm easy on my ram though). Any hardware that isn't too new should work fine, as server support is very good. Get a CPU that can scale down when not under load, and perhaps a quiet 3rd party cpu cooler, just so it's nice and quiet while running all the time.

All in all I think I've learnt more about Linux through my server than anything else, it's great fun and you can always expand what you want to do with it at any stage. I run a web server on mine now mainly for fun. You will learn heaps and enjoy it, just give yourself time to get setup.

Good luck.

---

### Post by jmvidalvia on 2007-04-08
Thank you everybody for your ideas!
I already got nfs running, and realized it is much faster than Samba.
Now I am fighting with ssh.
I read the howto and configures the openssh-server configuration files, but I have a silly  question.
Some said that Putty is ok for accessing from windows, but ¿what about from linux?
I installed openssh-client but don't know how to execute it.
I guess I don't need vnc or similar as I am not usin GUI in the server.
To summarize, I don't know what programm to use to senbd commands to the server or   transfer files.
Thanks again!

---

### Post by bmathis on 2007-04-08
to make a connection with the server through ssh, simple use the ssh command in a terminal

ssh 192.168.1.100 -l username

---

### Post by nix4me on 2007-04-08
to transfer files over ssh, use the sftp protocol.  gftp and many other ftp programs can use sftp.  I prefer to use kftpgrabber.

nix4me

---

### Post by jmvidalvia on 2007-04-09
ssh works great!
One more question: I've read that I have to delete the entry of my IP in **/home/user/.ssh/known_host** if it changes. Not only I am using dhcp but also work in two networks (home and work) so my ip changes frecuently.
(remember I use VMware, right now, I am in Alfa status ;) )

I vim that file but don't understand anything, it seems to be encrypted or so. Right now, I have something like two very long lines of numbers and letters.
The question is: how to delete an entry of an IP in that file to allow more conections for same user from a different IP?

Thanks again!

---

### Post by jmvidalvia on 2007-04-11
When my server changed it ip i just had to remove /home/user/.ssh folder.
When I tried again to connect...
ssh user@server
...a new folder and keys were generated immediately.
Thanks!

---

