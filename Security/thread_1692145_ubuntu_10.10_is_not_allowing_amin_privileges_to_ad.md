---
title: "ubuntu 10.10 is not allowing amin privileges to admin user, even tho sudo works"
date: 2011-02-21
forum: Security
---

### Post by wafaringstranger on 2011-02-21
i am relatively new to ubuntu. Just recenty i have not been able to access certain files(for example the history and bookmarks in the firefox folder), download files individually from the internet(music,fonts,etc), recieving an error message 

[QUOTE=firefox error console]Error: [Exception... "Component returned failure code: 0x80520015 (NS_ERROR_FILE_ACCESS_DENIED) [nsIFileOutputStream.init]"  nsresult: "0x80520015 (NS_ERROR_FILE_ACCESS_DENIED)"  location: "JS frame :: file:///usr/lib/firefox-3.6.13/components/nsSessionStore.js :: sss_writeFile :: line 2944"  data: no]
Source File: file:///usr/lib/firefox-3.6.13/components/nsSessionStore.js
Line: 2944[/QUOTE]

i have sudo priveleges and can install via update manager. i read somewhere that compizfusion might affect access permissions and i do use compiz and emerald at the same time.

thanks
wafaring stranger

---

### Post by The Cog on 2011-02-21
You will have noticed with update-manager that you need to give your password before the program can do its thing. The same is true of any program that needs the extra priviledge. Some programs like update-manager know that they need to aks for those priviledges, others don't. If they don't, then you have to ask sudo (or gksu for graphical applications) to raise their priviledges for you by putting sudo or gksu in front of the command, e.g.
**gksu nautilus** instead of just **nautilus** gives you a file browser with full priviledges. Be careful what you do with it - it doesn't ever ask "Are you sure?".

It looks to me as though whatever you are running is trying to overwrite part of the system firefox installation. Are you really sure you want whatever it is to do that?

---

### Post by wafaringstranger on 2011-02-21
[QUOTE=The Cog]
 It looks to me as though whatever you are running is trying to overwrite  part of the system firefox installation. Are you really sure you want  whatever it is to do that?
[/QUOTE]
No. i was tried earllier to fix firefox because it wouldnt remember  history or bookmarks by editing the files,(with instructions), that and  tried to download som music.
either way the gksu prefix does help but many startup programs are  starting without the sudo permission, eg i can't add or edit launchers  on the panel. any ideas on how to fix that?

---

### Post by The Cog on 2011-02-22
> No. i was tried earllier to fix firefox because it wouldnt remember history or bookmarks by editing the files,(with instructions), that and tried to download som music.
You should not need to go outside your home directory for this kind of activity. If FF doesn't remember bookmarks and the like, then you probably have some corruption in your home firefox configuration. Your home firefox configuraton is held in a directory called .mozilla in your home directory. You could try and take ownership of this directory and its contents, in case something has accidentally been taken by root. This command should do it (use your computer username instead of wafaringstranger):
> sudo chown wafaringstranger:wafaringstranger ~/.mozilla
If that doesn't fix things, try to rename the folder so that FF has to create a new one:
> mv ~/.mozilla ~/.mozilla-old
Make the changes while FF is not running.

> many startup programs are starting without the sudo permission, eg i can't add or edit launchers on the panel. any ideas on how to fix that?I don't understand what you mean by this, but it's probably nothing to do with any forefox problems.

---

### Post by wafaringstranger on 2011-02-26
>  	

 	 	 		 			 				[QUOTE]many startup programs are starting without the sudo permission, eg i  can't add or edit launchers on the panel. any ideas on how to fix that? 			 		 	 	 
I don't understand what you mean by this, but it's probably nothing to do with any forefox problems[/QUOTE]
 sorry about that i worde that wrong is was referring to the icons on the top bar that usually can be customised, but not i cant do that, add program launchers to the desktop.

---

### Post by cariboo on 2011-02-26
You can't add anything to the top panel in the netbook edition, no matter what type of permissions you have.

---

### Post by wafaringstranger on 2011-03-02
> You can't add anything to the top panel in the netbook edition, no matter what type of permissions you have
are you sure? I was adding shortcut to the top panel not too long ago... well.. ive formatte the hard drive since then for other reasons. but it was ubuntu 10.10 netbook remix.
another error i have just discovered is right after i boot
> icewm permissions failed id copy paste it but it comes before the rest of the GUI loads.

---

### Post by cariboo on 2011-03-03
> **wafaringstranger said:**
> are you sure? I was adding shortcut to the top panel not too long ago... well.. ive formatte the hard drive since then for other reasons. but it was ubuntu 10.10 netbook remix.
another error i have just discovered is right after i boot
 id copy paste it but it comes before the rest of the GUI loads.

The 10.10 version of the UNE runs on top of mutter, the upper panel is hard coded to not allow panel applets, because of the global menu. You can add indicators, which are not panel applets.

---

### Post by wafaringstranger on 2011-03-07
OH.  i guess that shows how much i know about ubuntu. lol . either way i cant add indicators, or edit them bacause i get the same error that  drove me away from windows: "permission denied".  so what is my problem, besides the fact that computers hate me, that i already know. does it involve this icewm error?

---

### Post by cariboo on 2011-03-08
It seems to me you have screwed up permissions in your home folder, I'd suggest you check all the files and directories in your home folder, and make sure that they are owned by your user, and have at minimum permissions of 755. Once you have that straightened out, you can then fine tune individual permissions.

---

### Post by wafaringstranger on 2011-03-08
Um, sorry if this is a stupid question but, er, how do you do that?

---

### Post by cariboo on 2011-03-08
I personally set my home folder permissions to 700, but 755 is a good starting point, open an Applications->Accssories->Terminal and type:

```
sudo chmod -R 755 /home/<user name>
```

where <user name> = your user name. The above command will set the permissions in your home directory to 755, this means that the following permissions will be applied to all the files in your home directory:

[LIST]
[*]read by owner
[*]write by owner
[*]execute/search by owner
[*]read by group
[*]execute/search by group
[*]read by others
[*]execute/search by others
[/LIST]

Next in the same terminal, type:

```
sudo chown -R user:user /home/<user name>
```

The above command will set the ownership and group to your user name and group.

BTW the -R in the above commands stands for recursive, which means that the changes will be made to all the files and directories in your home directory.

For more pn Linux file ownership and permissions have a look [here]("http://www.tuxfiles.org/linuxhelp/filepermissions.html")

---

### Post by wafaringstranger on 2011-03-09
after typing in the first command  i recieved the following error
> stranger@w4yf421n6s724n632:~$ sudo chmod -R 755 /home/stranger
[sudo] password for stranger: 
chmod: cannot access `/home/stranger/.gvfs': Permission denied

also, in the second command, what to i out in the "user:user"

---

### Post by cariboo on 2011-03-09
> **wafaringstranger said:**
> after typing in the first command  i recieved the following error

also, in the second command, what to i out in the "user:user"

The error you got is normal, ~/.gvfs is owned by root. 

substitute your user name and group for user:user, in your case it would probably be stranger:stranger

---

### Post by wafaringstranger on 2011-03-11
it worked. i just needed to reboot for it to take effect. not the first time ive overlooked a minorthing like rebooting before. thanks. :)

---

### Post by cariboo on 2011-03-11
You're welcome.

---

