---
title: "Shared Folder in Virtual Box VERY slow"
date: 2009-09-15
forum: Virtualisation
---

### Post by cforput on 2009-09-15
I have Hardy 8.10 installed. I then installed Virtual Box and have set up XP on it. Everything runs great except when I use Windows Explore to access a shared folder in Hardy. It then runs really slow.

Has anyone experience this problem or have any ideas how I might fix it?

---

### Post by falconindy on 2009-09-15
Are you making sure to access the share through \\VBOXSVR\sharename ?

---

### Post by cforput on 2009-09-15
I'm not sure exactly what you mean. I am pretty new to ubuntu. I start VBox (OS = XP). I then open windows explorer. When I go to the folder that I have shared in Ubuntu, things slow to a crawl. If I access the shared folder in Ubuntu, I have not speed issues. It is only under VBox and Windows.

---

### Post by falconindy on 2009-09-16
> **falconindy said:**
> Are you making sure to access the share through \\VBOXSVR\sharename ?
This is Windows jargon, actually. You have two options to properly access the shared folders in VirtualBox. The first is to map the drive with 'net use' from the command prompt, i.e.:
```
net use x: \\VBOXSVR\share-name /persistent:yes
```
The other is to go through Windows Explorer -> Entire Network -> VirtualBox Shared Folders -> share-name

My assertion is that you're not trying to access the shared folder over the network, and that you're actually using the direct access that VirtualBox provides for you in the form of a faux network share.

---

### Post by theZoid on 2009-09-17
> **falconindy said:**
> This is Windows jargon, actually. You have two options to properly access the shared folders in VirtualBox. The first is to map the drive with 'net use' from the command prompt, i.e.:
```
net use x: \\VBOXSVR\share-name /persistent:yes
```
The other is to go through Windows Explorer -> Entire Network -> VirtualBox Shared Folders -> share-name

My assertion is that you're not trying to access the shared folder over the network, and that you're actually using the direct access that VirtualBox provides for you in the form of a faux network share.

OK...but what about the sluggishness problem...any way to improve that situation?  I've always had sluggishness but haven't look for a cure.

---

### Post by cforput on 2009-09-18
> **theZoid said:**
> OK...but what about the sluggishness problem...any way to improve that situation?  I've always had sluggishness but haven't look for a cure.

Sluggishness? I would love to have sluggishness. When I access the folder through explorer it takes anywhere from 14 to 31 seconds to respond to my activities (change folder, highlight a file, copy, cut, pastec etc). 

The other thing that is interesting is that I can't map a network drive to is. Explorer gives me an error that the folder is not accessible but when I use explorer and just navigate to the folder, I can eventually get there.

I'm not sure if the inability to map is related to the sluggishness but since I can navigate to the folder, I don't really care about being able to map a drive letter, I just want things to run faster. I never had this problem with VMware but I like VBox much better.

Anyone have any ideas on how to speed things up?

---

### Post by falconindy on 2009-09-18
Hmm. No idea, tbh. The only time I ever had slow access to a "foreign" drive in VBox was when I tried to access my host OS's drives via network shares, and not the VB Shared Folders.

By chance is the shared folder on the same physical drive as the Guest OS .vdi file?

---

### Post by theZoid on 2009-09-19
> **falconindy said:**
> Hmm. No idea, tbh. The only time I ever had slow access to a "foreign" drive in VBox was when I tried to access my host OS's drives via network shares, and not the VB Shared Folders.

By chance is the shared folder on the same physical drive as the Guest OS .vdi file?

In my case, the shared folders which is my entire /home/myname, is on the same physical drive.  I work from my virtual machine and save to my /home, it works OK but is very slow to bring up the folders intially....was thinking there might be a way to speed that up...don't know :)

---

### Post by falconindy on 2009-09-19
> **theZoid said:**
> In my case, the shared folders which is my entire /home/myname, is on the same physical drive.  I work from my virtual machine and save to my /home, it works OK but is very slow to bring up the folders intially....was thinking there might be a way to speed that up...don't know :)
Well, my thinking is that you're seeing slow performance because of there being too much hard drive activity going on for a single drive to handle elegantly. Do you have the ability to separate the guest and host OS onto separate physical hard drives? If you do, it may take away some of the latency you're seeing. You won't need to reinstall Windows via VBox to do this -- just move the .vdi file and locate the file for VBox when it complains that the .vdi is missing.

---

### Post by cforput on 2009-09-19
> **falconindy said:**
> Hmm. No idea, tbh. The only time I ever had slow access to a "foreign" drive in VBox was when I tried to access my host OS's drives via network shares, and not the VB Shared Folders.

By chance is the shared folder on the same physical drive as the Guest OS .vdi file?

Could you give me a better understanding of network shares vs VB Shared Folders. The folder is on a single HDD on my laptop.

---

### Post by falconindy on 2009-09-19
> **cforput said:**
> Could you give me a better understanding of network shares vs VB Shared Folders. The folder is on a single HDD on my laptop.
A network share is what you access on someone else's computer. Suppose you and I shared a LAN, and I had some music you wanted to get to. I'd just share the directory and you'd be able to read that share remotely.

VirtualBox's shared folders are accessed sort of in a similar manner to network shares, but the underlying concept isn't the same -- only the method of access. Instead of going out over your ethernet connection, you're just going to your local disk directly. The way they chose to implement it seems to cause some confusion.

---

### Post by theZoid on 2009-09-19
> **falconindy said:**
> Well, my thinking is that you're seeing slow performance because of there being too much hard drive activity going on for a single drive to handle elegantly. Do you have the ability to separate the guest and host OS onto separate physical hard drives? If you do, it may take away some of the latency you're seeing. You won't need to reinstall Windows via VBox to do this -- just move the .vdi file and locate the file for VBox when it complains that the .vdi is missing.

I may try that...I have a couple of large externals...thanks

---

### Post by rhynolu on 2009-09-20
Hi, 

if you are suffered by accessing share folder too slow, maybe you can try that:

1. if your vm is running Windows, 
2. if your share folder name is like that : "\\vboxsvr\<share fodler>"
3. if you install windows in disk c of your vm
4. please modify c:\windows\system32\drivers\etc\hosts
5. modify the line "127.0.0.1 localhost" to "127.0.0.1 localhost vboxsvr"
6. reboot vm, and you can see there's a lot of improvement.

---

### Post by issueperson on 2009-09-28
> **rhynolu said:**
> Hi, 

if you are suffered by accessing share folder too slow, maybe you can try that:

1. if your vm is running Windows, 
2. if your share folder name is like that : "\\vboxsvr\<share fodler>"
3. if you install windows in disk c of your vm
4. please modify c:\windows\system32\drivers\etc\hosts
5. modify the line "127.0.0.1 localhost" to "127.0.0.1 localhost vboxsvr"
6. reboot vm, and you can see there's a lot of improvement.

Can you tell me what I just did?  Because this really helped my speed a lot.

---

### Post by falconindy on 2009-09-28
> **issueperson said:**
> Can you tell me what I just did?  Because this really helped my speed a lot.
You saved yourself a DNS lookup every time you access VBOXSVR.

---

### Post by user667 on 2009-09-30
> **rhynolu said:**
> Hi, 

if you are suffered by accessing share folder too slow, maybe you can try that:

1. if your vm is running Windows, 
2. if your share folder name is like that : "\\vboxsvr\<share fodler>"
3. if you install windows in disk c of your vm
4. please modify c:\windows\system32\drivers\etc\hosts
5. modify the line "127.0.0.1 localhost" to "127.0.0.1 localhost vboxsvr"
6. reboot vm, and you can see there's a lot of improvement.

Holy schnikes, that actually worked.  THANK YOU!!!  I've been suffering with this problem for months now.

---

### Post by theZoid on 2009-09-30
> **rhynolu said:**
> Hi, 

if you are suffered by accessing share folder too slow, maybe you can try that:

1. if your vm is running Windows, 
2. if your share folder name is like that : "\\vboxsvr\<share fodler>"
3. if you install windows in disk c of your vm
4. please modify c:\windows\system32\drivers\etc\hosts
5. modify the line "127.0.0.1 localhost" to "127.0.0.1 localhost vboxsvr"
6. reboot vm, and you can see there's a lot of improvement.

That's exactly what I was looking for....I'm trying it now....

EDIT:  Incredible SPEED UP :)  thanks !!

---

### Post by Kalex12 on 2009-10-13
The map network drive in the XP guest worked great for me, no lag at all now.
Host is Ubuntu 64


:P

---

### Post by ssagi on 2009-11-07
> **rhynolu said:**
> Hi, 

if you are suffered by accessing share folder too slow, maybe you can try that:

1. if your vm is running Windows, 
2. if your share folder name is like that : "\\vboxsvr\<share fodler>"
3. if you install windows in disk c of your vm
4. please modify c:\windows\system32\drivers\etc\hosts
5. modify the line "127.0.0.1 localhost" to "127.0.0.1 localhost vboxsvr"
6. reboot vm, and you can see there's a lot of improvement.

that is amazing. I am using Ubuntu 9.04 (Jaunty) and was suffering from this problem for maybe a year. So much that I gave Vbox up in favor of VMware with very slow setup time. 

I also explored many forums in Vbox who reported that with no help.
I now work solely with Vbox for my XP applications (MS Office) and am very content.

---

### Post by cforput on 2009-12-29
> **rhynolu said:**
> Hi, 

if you are suffered by accessing share folder too slow, maybe you can try that:

1. if your vm is running Windows, 
2. if your share folder name is like that : "\\vboxsvr\<share fodler>"
3. if you install windows in disk c of your vm
4. please modify c:\windows\system32\drivers\etc\hosts
5. modify the line "127.0.0.1 localhost" to "127.0.0.1 localhost vboxsvr"
6. reboot vm, and you can see there's a lot of improvement.

rhynolu,
you are a genius! I had this saved and only now had a chance to try it and WHAMO!!!! This works great. I can now sop thinking of the suffering I would go through to install VMWare.  

You ROCK.........   :guitar:

---

### Post by hexabit on 2010-09-15
Thank You very much adding this entry to hosts file [COLOR=DarkGreen]speed up [COLOR=Black]access to network shares[/COLOR][/COLOR][COLOR=Black].[/COLOR]

---

