---
title: "In the words of Homestar Runner, Windows is . . ."
date: 2006-10-28
forum: The Cafe
---

### Post by boz on 2006-10-28
BAWEETED!  Wiped it from my laptop's hard drive about 10 minutes ago.  Now if only I can get my wife to convert, I won't have to deal with that crappy OS any more.  Except at school and work.  :(

---

### Post by rfruth on 2006-10-28
Windows = [ATTACH]18411[/ATTACH]

---

### Post by gerowen on 2006-10-28
From the previews I've seen of Vista, it's moving in a Linux-y direction.  Now it requires root(woops, I mean Administrator ;) ) passwords to install software, and I've heard that the file system is even changing to a journalized file system to eliminate the need for defragmenting.

---

### Post by boz on 2006-10-28
LOL @ rfruth

I'm kind of up "a" creek right now myself.  I forgot about the grub menu when I removed windows and changed my partitions around!  ](*,) Is there a way to remove grub from the live cd?

---

### Post by kuja on 2006-10-28
> **marcusdean.adams said:**
> From the previews I've seen of Vista, it's moving in a Linux-y direction.  Now it requires root(woops, I mean Administrator ;) ) passwords to install software, and I've heard that the file system is even changing to a journalized file system to eliminate the need for defragmenting.
I heard the new filesystem was going to be delayed and Vista would be released without it, and it might see support in one of the service packs.

---

### Post by kuja on 2006-10-28
> **boz said:**
> LOL @ rfruth

I'm kind of up "a" creek right now myself.  I forgot about the grub menu when I removed windows and changed my partitions around!  ](*,) Is there a way to remove grub from the live cd?
You could simply overwrite the master boot record from whatever you plan to be installing, or, if you want to make changes, you can from the live cd. Boot up, install dchroot from Universe, mount the filesystem, chroot into it. Voila, you can do whatever you need from there (in a trusty shell of course).

---

### Post by 3rdalbum on 2006-10-28
> **marcusdean.adams said:**
> From the previews I've seen of Vista, it's moving in a Linux-y direction.  Now it requires root(woops, I mean Administrator ;) ) passwords to install software

Actually, it doesn't - it just needs you to click the "Ok" button to allow a program to run as administrator; i.e:

1. User downloads the file "OMGZ britney spears NUDEZ!.jpg.exe" from an e-mail
2. User double-clicks on it.
3. Windows Vista asks "Did you perform this action? If so, click OK"
4. User thinks "Yes, I double-clicked on the file and I want to see the nudies!"
5. User clicks OK
6. Computer becomes infected with virus, which e-mails itself to everyone in his address book and inbox. Cycle repeats.

Vista even lets you disable User Account Protection with just a couple of clicks, so you can run as root (whoops, I mean Administrator) non-stop.

---

### Post by gerowen on 2006-10-29
It's kind of funny really, I mean technically a virus is a program just like any other, it just does things you don't want it to and that harm your system.  I mean I could sit down and take 2 minutes to write a python script consisting of:
```

#Virus.pyw
#It's .pyw extension so it doesn't open any windows
#it just runs in the background.  Python files with
#.pyw extension are usually programs that open and
#draw their own windows and do not display a terminal.
x=0
infile=open("virus.txt", "w")
while x==0:
     infile.write("This is a virus!\n")
infile.close()
```
Technically I could call that a virus, I wrote one similar just as an experiment and it filled up 15 GB of space in roughly 5 minutes(it's only purpose is to fill up your hard drive), and since it's python it will run on any system that will run python, including Linux.  Now don't get me wrong, I love Linux and the Open Source idea.  Software is much more maneuverable and customizable when it's open source, and free software is much better than paying $100+ for each new release.  But tell me, how is it that a company as big as Microsoft can have software "so" buggy that it's as vulnerable to attacks that it is?  I mean users should be able to use their PC without the worry of being hacked or compromised or having their computer crash because they received an e-mail with a virus in it or because an advertisement on a website happens to be linked to a malicious site.  Maybe the fact that it's open source is the reason Linux is so secure, users can find and fix the exploits and inform the devs, therefore taking stress of them.  I dono, just wanted to rant a little, :p.

---

### Post by Polygon on 2006-10-29
the new filesystem wont be avaiable to users, its just going to go in the high end server edition of vista from what ive heard (unless they changed it)

---

