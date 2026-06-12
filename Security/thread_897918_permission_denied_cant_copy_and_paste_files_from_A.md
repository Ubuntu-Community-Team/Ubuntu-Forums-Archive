---
title: "permission denied cant copy and paste files from Apple iMac machine"
date: 2008-08-22
forum: Security
---

### Post by bigdee973 on 2008-08-22
hello im having a very stupid problem..my mac operating system is having problems and i need to backup some very very important documents.  i use ubuntu live cd and mac hard drive is mounted.  i can see the files that i want to backup on my mac partition and i can even open the files and save them but when i just try to copy and paste the file onto my external hard drive i get permission denied... i used sudo nautilus ... from sudo nautilus i can actually open the file (pdf files) and then save them onto my external hard drive but the issue is that i have ALLLLOTT OF PDF and doc files.  now this is stupid..i can open the file and save but i cannot copy and paste them... whats going on here?  okay so i need to know if i installed ubuntu onto the mac will i be able to have full read and/or write permissions or will i still get permission denied messages even after i install ubuntu? if i do then what must i do in order to at least copy the files to back them up..im so close and i really really need these files...they are for court.

:(:(:(

---

### Post by cariboo on 2008-08-22
How is you external drive formatted? Depending how it is formatted you may or may not be able to set read/write permissions.

Jim

---

### Post by bigdee973 on 2008-08-22
> **cariboo907 said:**
> How is you external drive formatted? Depending how it is formatted you may or may not be able to set read/write permissions.

Jim

i honestly dont know how its formatted...its a western digital mybook external hard drive with 320gb..it uses power adapter and usb cable..can use firewire and eSata.  but i dont think its the external hard drive to be honest...the external hasnt been modified in anyway or reformatted in anyway its factory setting...i mean i also saved it onto the desktop of ubuntu and i still get permission denied... do u think if i installed ubuntu into my mac machine i will be able to read and write to it?  by default on a windows machine it works just fine...back in the day i use to use the ntfs tool but with hardy heron its really unneccessary to install ntfs partitioner.  i just want to access these files and also in the future be able to read and write to my mac partition...so what do u thinK? i never installed ubuntu on a mac...can ubuntu read and write to a MAC osx partition as of yet?? let me know it will be easier if not then is there a possible way if so could someone tell me thanks in advance.

---

### Post by cariboo on 2008-08-23
It is probably formatted as NTFS. If you manually mount the drive and then change the permissions to the mount point you should be able to write your data to the hard drive. In a terminal:

```
sudo mount /dev/sdbx /mnt
```

where /dev/sdbx is your external drive, then

```
sudo chmod -R 777 /mnt
```

This should give you write permissions to your external drive.

As far as installing Ubuntu on a Mac I have an old G3 that I installed Xubuntu on, it worked, although it was slow. You will have to use a ppc version of ubuntu as the regular x86 version will not install. If you can see your files, you already know that Ubuntu can do that. You would probably be better off backing up your files and then fix your Mac installation. If you want to experiment go ahead and install ubuntu, but backup up your important files first.

Jim

---

### Post by bigdee973 on 2008-08-23
> **cariboo907 said:**
> It is probably formatted as NTFS. If you manually mount the drive and then change the permissions to the mount point you should be able to write your data to the hard drive. In a terminal:

```
sudo mount /dev/sdbx /mnt
```

where /dev/sdbx is your external drive, then

```
sudo chmod -R 777 /mnt
```

This should give you write permissions to your external drive.

As far as installing Ubuntu on a Mac I have an old G3 that I installed Xubuntu on, it worked, although it was slow. You will have to use a ppc version of ubuntu as the regular x86 version will not install. If you can see your files, you already know that Ubuntu can do that. You would probably be better off backing up your files and then fix your Mac installation. If you want to experiment go ahead and install ubuntu, but backup up your important files first.

Jim

alright ima try that to see if it works thanks man but the thing also is that i have no problem what so eve writing or reading to my external hard drive from ubuntu..i can drag and drop all day long from live cd etc to my external...its the mac partition thats not letting me read from it to copy and paste ...i cant even drag and drop it onto ubuntus desktop... could i do the same command u just gave me but do it to macs parition?..for instance i have the directory /User/elizabeth that i want to copy and paste so if i go to terminal in ubuntu and type in sudo chmod -R 777 /User/elizabeth would that give me absolute permisson to copy the file? i dont have the imac at hand no more but this is vital information i will need for the future...hopefully the guy below me (temion) could see and i could learn from him

---

### Post by temion on 2008-08-24
Hey guys, i have a related problem. My imac's hard drive died on me (*disk utility says it has a damaged B-tree and something else which prevents it from being fixed), and a friend showed me unbuntu to attempt to save my files. Well i booted up ubuntu and was so happy to see i can get into my OSX partition. 

However the folders have an X on them and say I don't have permission to open them. Is there anyway to give it my osx login/pass so as to grant permission? 

All i want to do is move the files onto a osx formatted external drive OR burn the files to DVD, but i can't get to them because of this permission problem. 


Thanks for any help!:KS

---

### Post by bigdee973 on 2008-08-24
> **temion said:**
> Hey guys, i have a related problem. My imac's hard drive died on me (*disk utility says it has a damaged B-tree and something else which prevents it from being fixed), and a friend showed me unbuntu to attempt to save my files. Well i booted up ubuntu and was so happy to see i can get into my OSX partition. 

However the folders have an X on them and say I don't have permission to open them. Is there anyway to give it my osx login/pass so as to grant permission? 

All i want to do is move the files onto a osx formatted external drive OR burn the files to DVD, but i can't get to them because of this permission problem. 


Thanks for any help!:KS

okay ill take you one step closer but your probably gonna have the same problem as me and get permission denied...BUT i havent yet done what CARIBOO907 has said..but to get rid of the X and to able to at least OPEN the file with the X but not copy and paste it. 
now go on top at click Applications>accesories>terminal 
in terminal type in 
sudo nautilus
from there navigate to your file on the mac partion, you should be able to at least OPEN the file but not be able to copy and paste it...try what CARiBOO907 said but do it to the folder or file that had the X...so try..sudo chmod -R 777 /path/to/file/or/folder and then try to copy and paste the file/folder you wanted.  tell me if it worked

---

### Post by rogeriopvl on 2008-08-24
I had a similar problem with some files I saved from my macbook on a usb key. I inserted the key on the Ubuntu machine and just did the following on a terminal:

```

sudo chown -R my_ubuntu_username /media/usbkey_name/

```

This worked for me. I hope it works for you.

---

### Post by deggen on 2009-09-25
> **bigdee973 said:**
>  i used sudo nautilus ... from sudo nautilus i can actually open the file (pdf files) and then save them onto my external hard drive but the issue is that i have ALLLLOTT OF PDF and doc files.  now this is stupid..i can open the file and save but i cannot copy and paste them... 


You can copy and paste them - just make sure you use the same (sudoed) window of nautilus - I had the same problem - that fixed it for me. 

As long as u copy, navigate and paste in the same window it works!




Thanks for your help man.

- Darren

---

### Post by macabrem on 2009-09-25
> **bigdee973 said:**
> hello im having a very stupid problem..my mac operating system is having problems and i need to backup some very very important documents.  i use ubuntu live cd and mac hard drive is mounted.  i can see the files that i want to backup on my mac partition and i can even open the files and save them but when i just try to copy and paste the file onto my external hard drive i get permission denied... i used sudo nautilus ... from sudo nautilus i can actually open the file (pdf files) and then save them onto my external hard drive but the issue is that i have ALLLLOTT OF PDF and doc files.  now this is stupid..i can open the file and save but i cannot copy and paste them... whats going on here?  okay so i need to know if i installed ubuntu onto the mac will i be able to have full read and/or write permissions or will i still get permission denied messages even after i install ubuntu? if i do then what must i do in order to at least copy the files to back them up..im so close and i really really need these files...they are for court.

:(:(:(

Are you able to boot from Mac OS at all?  I've never done it with my Mac, but isn't there a way to boot up with just a Terminal window and then you could change permissions with the Mac terminal?  

Seems like it would be a simple issue of changing all to 777, but I'm not sure.

---

