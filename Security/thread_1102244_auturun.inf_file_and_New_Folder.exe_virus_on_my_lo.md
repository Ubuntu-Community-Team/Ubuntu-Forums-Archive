---
title: "auturun.inf file and New Folder.exe virus on my lovly ubuntu"
date: 2009-03-21
forum: Security
---

### Post by chinni.joy on 2009-03-21
hello all,

         I m so worrying about virus which affected to my machine.I installed wine and got some virus through some websites.I have no idea which website i got from .I have One Folder which is shared folder using samba.I saw autorun.inf ,regsvr.exe and New Folder.exe files in that folder 

          i knew a little about those files. than  I removed them from that folder.again those files created and running in system process.I understood that it is better to removed wine from machine to get out from virus.I remved wine from machine.even those files are creating again and again. 

with that virus exe files are creating for each folder in that sharedFolder.

         please help me to getout from that stupid virus.


thanks & Regards

kumar kasimala,

---

### Post by cariboo on 2009-03-21
Is the shared folder located on your Ubuntu computer or on a computer running Windows? Exe files will not run in Linux so they have to be running  on a windows computer.

Jim

---

### Post by chinni.joy on 2009-03-21
hi Jim,

      shareFolder is located in ubuntu machine.if anyone installed wine which is for windows applications to run on linux.than virus will affect to linux machine also.let me know where im wrong.




thanks & Regards

kumar kasimala,

---

### Post by chinni.joy on 2009-03-21
hi jim,

      I cant able to find where is actually virus is.I installed clamscan which for  unix based os to  detect virus and remove it .That program  also didnt helped me. can anyone push me from this virus.

---

### Post by Sukarn on 2009-03-21
once you remove wine and restart your computer, there is no way for a .exe file to run on ubuntu.

I think that the virus might be running on a windows computer which is writing to the shared folder.

---

### Post by chinni.joy on 2009-03-21
hi sukarn & jim,
         thanq for reply.Can you help me how to protect  from that virus?

---

### Post by HermanAB on 2009-03-21
Just delete it.  

Find it with Nautilus, right click and delete.  What can be simpler?

Cheers,

Herman

---

### Post by cariboo on 2009-03-21
I see you install clamav, open an Applications-->Accessories-->Terminal, at the prompt type :

```
sudo freshclam
```

will update the virus definitions, next in the same terminal type:

```
mkdir badfiles
```

This will create a directory in your home directory called badfiles. Next in the same terminal type:

```
clamscan -r -move=badfiles
```

This will check all the directories in your home directory and move all the infected files to the badfiles directory.

One last thing to do is to remove the wine directory. I don't run wine, but you should be able to find it if you open Places-->Home Folder and press Ctrl-h to reveal the hidden files and directories. I would also so suggest deleting the directory and not sending it to trash, to enable delete when you have Nautilus open go to Edit-->Preferences-->Behaviour, under Trash select Include a Delete command that bypasses Trash.

Jim

---

### Post by pietjanjaap on 2009-03-21
If you install wine, for security you have to use "configure wine".
(Applications-wine-configure wine).
Here you have default settings, remove de drives of ubuntu, then windows programs can not see all drives/maps.
Ad programs(like hijsplit.exe)to the list, klik on hijsplit.exe then change the drives where this program is allowed to go in maps.
This is safer.

---

### Post by chinni.joy on 2009-03-21
hi all,

    Thanq for reply . I already uninstalled wine & removed /home/myname/.wine folder.I already used  clamscan program  to remove virus.it is worked for me.but still again same problem  I need to retype command for remove virus.How can i make it to be secure Folder.if there is an way let me know that .plz help me out.

---

### Post by AlexenderReez on 2009-03-21
> **chinni.joy said:**
> hi all,

    Thanq for reply . I already uninstalled wine & removed /home/myname/.wine folder.I already used  clamscan program  to remove virus.it is worked for me.but still again same problem  I need to retype command for remove virus.How can i make it to be secure Folder.if there is an way let me know that .plz help me out.

first of all, do you know Linux still can be affected by virus ? there are security fixed every now and then...but there is no such thing as totally secure while dealing with system . how to defense ourselves ? please do rely on our brain instead of linux or antivirus...but for this case if you really sure it is **.exe** , so we can assume it is a bit safe for linux at this current time . open System monitor , check is there any unwanted running program , Kill it . Check also in session for startup program, is there any new start program exist in there .if you detect something not going right just delete it.Try to find replacement for windows application , what's on earth are you so desperate of using Windows except for gaming because nowadays almost everything can be replace in linux . But if you can't find anything to replace it, Wine still can be consider . 


> **chinni.joy said:**
> hi sukarn & jim,
         thanq for reply.Can you help me how to protect  from that virus?

EXT4 is already exist .harddisk encryption , linux Firewall ...MR Google might able to help you.. one of it might be 

```
http://www.reallylinux.com/docs/linuxvirustop10.shtml
```

---

### Post by bodhi.zazen on 2009-03-21
It is possible to infect system files (in theory) if you are running wine as root.

I always delete all links in ~/.wine to anywhere outside of ~/.wine.

If you have cleaned your Ubuntu machine, and you have removed and reinstalled both wine and ~/.wine, and you are not running wine as root, is perhaps your media (flash drive) infected or the remote server ?

---

### Post by Grey08 on 2009-03-22
> **AlexenderReez said:**
>  what's on earth are you so desperate of using Windows except for gaming because nowadays almost everything can be replace in linux . But if you can't find anything to replace it, Wine still can be consider . 



Hello

Im just wondering what about UBS system? Can it be install at ubuntu or kubuntu?

Regards
grey08

---

### Post by inuit-joe on 2009-03-26
if ur worried about virii and u have cal y not install clamtk.
its a GUi front-end for clam.
that could help atleast help in future

---

