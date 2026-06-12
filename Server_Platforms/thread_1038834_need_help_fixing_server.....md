---
title: "need help fixing server...."
date: 2009-01-13
forum: Server Platforms
---

### Post by hockey97 on 2009-01-13
Hi, ok the update manager decided to delete some files when I allowed the updates to take place.

I currently can't boot into the desktop. I know I have most of the files but I think the update manager deleted alot of files that handels gnome. 

Is there a way I can see a log of what the updater deleted??? so I can go in the command promt and install them to fix the problem.

when I boot i still do get the ubuntu desktop loading page and then it would show a error page saying that failed to boot and then trying backup then found no backup so it was forced to resume.

So it then booted just the bash command. So I have access to that. 

what should I do??? could I see what the update manager deleted and then install those files back?

---

### Post by cariboo on 2009-01-14
Have you tried starting in recovery mode and using xfix to repair your xorg.conf.

When I update my server, I use at the prompt:

```
sudo aptitude update && sudo aptitude safe-upgrade
```

That way there are no surprises when you reboot.

This question could just as well been asked in the general help section, as this has nothing to do with servers.

Jim

---

### Post by hockey97 on 2009-01-14
well, I am using the ubuntu server edition. I had a desktop ubuntu instlled but it's now missing important files cause of update manager.

how would I get in recover? I can still boot into my server edition that is what the desktop ubuntu does it fails to boot the desktop so then it boots the server edition.

so I do have command prompt access.

---

### Post by freerkkalsbeek on 2009-01-14
Try: apt-get install ubuntu-desktop
That will have most of the dependencies to reinstall all gnome stuff

Regards,
Freerk

---

### Post by hyper_ch on 2009-01-14
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by linux_tech on 2009-01-14
To try to re-install the desktop, in the terminal type:
```
sudo apt-get update 
sudo apt-get install ubuntu-desktop
sudo apt-get install gdm
sudo /etc/init.d/gdm start
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by hockey97 on 2009-01-14
thanks for the replies. Before I try it I want to know if it will hurt any config files on the desktop??

I have apache,bind9,mysql,postfix servers. I want to know if there is a way where I can only install system files for the ubuntu desktop without  deleting any config files for the servers.

I have a external hd and installed partimage. I did made a partimage of my ubuntu hd but I have 2 part... one for the ubuntu system and another a 120gb part for extended stuff like websites... it's a extended storage. I was only able to make a partimage of the 2nd one... the extended one. 

So I would like the best way to have a image of the part.. of the hd  so I can easily transfer it to other computers.

I currently have 2 computers. I am still trying to get a system going but need help on how to setup the servers.

I have 2 computers and I need one to be used for school work and other perosnal stuff.

one has to be a server but the problem is that I have a new pc and want to use it as a personal pc but my old computer already has ubuntu on it but it's old I was bought in 2000.

I am thinking to use the new computer as a server. I was woundering if the best way to go is just install only ubuntu by itself.


Sorry for the title... 


So  to recap what I said here. I  am asking if what if reinstall the ubuntu desktop wouldn't it destory any apache config files?

or will it just overwrite the system files and install the missing files?

I don't want to have to reconfig my servers like apache.


the seond one was not much of a question. I just want some suggestions and pointers on  how to pick a computer to be a server. 

what factors should I look for to make my main server and have a backup server.


thanks for the replies.

---

### Post by hockey97 on 2009-01-16
so this should be safe right???

no server files like apache or any programs would get erased?

Is there a way where I can like have the installtion to only add the files that are missing and needed to run the desktop.

something like what windows has. The command in dos was like sfc /scannow  where it scanned the computer and have you put in the windows installation cd and it would copy over missing files or correct any errors the files had.

I don't want to lost the configs of my servers and the software that is already installed.

---

### Post by albinootje on 2009-01-16
> **hockey97 said:**
> 
I don't want to lost the configs of my servers and the software that is already installed.

This :
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```
will simply install everything needed to run the desktop as in the desktop edition.
The only basic difference will be the kernel, because the server installation installs a kernel which is specifically meant for servers.

All your apache config etc. will be still there after this.

---

