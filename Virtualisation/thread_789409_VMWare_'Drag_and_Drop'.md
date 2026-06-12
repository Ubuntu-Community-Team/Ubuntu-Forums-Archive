---
title: "VMWare 'Drag and Drop'"
date: 2008-05-10
forum: Virtualisation
---

### Post by benc123 on 2008-05-10
Hello, I have almost got my VMWare windows XP sorted. The only thing that i still cannot do is to drag and drop' files from Ubuntu to XP. 
When i try i get this message. 

"Unable to open: Virtual machine "/home/benc/Desktop/Group Work jak..doc" is not in the inventory".

jak doc is a open office word doc. (saved in windows doc format)

I would appreciate any help at all in this matter. 

Thanx benc123

---

### Post by fjgaude on 2008-05-10
I'm not sure you can drag and drop from Windows to Linux. I can't... I use Samba to copy files, see files in VM WinXP that are in Ubuntu. I can copy and paste text, one to/from the other.

Maybe if you somehow attached a whole drive to one OS or the other, which I've never done, it is possible to do what you wish.

Samba works fine for me... I have a huge raid5 array with all my data that is accessed by WinXP and by Ubuntu.

---

### Post by dpj23 on 2008-05-10
Just for conversation... Have you tried to copy a file from the host to the vm machine...  I currently have dragged files to and from with no problem... But find it easier to copy a file from one to the other...  


In addition, a good idea is to set up a shared folder in your home directory and then map a drive in windows to that shared folder... then you can just drop a stuff into that folder...  that way you can better manage your files without creating duplicates...

---

### Post by fjgaude on 2008-05-10
I've tried copying a picture file, jpg, to the desktop in Ubuntu, and then tried to paste it into Paint Shop Pro, Xara, and InDesign without success. I have no trouble moving, seeing such files through Samba Shares.

I have no trouble cut, copy, paste text items, i.e., those characters I've dragged across with the cursor, to and from host and guest. Works great in VMware server, the free one, and is why I don't use Virtual Box.

---

### Post by dcstar on 2008-05-10
> **benc123 said:**
> Hello, I have almost got my VMWare windows XP sorted. The only thing that i still cannot do is to drag and drop' files from Ubuntu to XP. 
When i try i get this message. 

"Unable to open: Virtual machine "/home/benc/Desktop/Group Work jak..doc" is not in the inventory".

jak doc is a open office word doc. (saved in windows doc format)

I would appreciate any help at all in this matter. 

Thanx benc123

Have you installed VMware tools?

---

### Post by benc123 on 2008-05-11
yes i have got vmware tools installed. should have mentioned that. lol

---

### Post by myle on 2008-05-11
I use NAT and I have the following problem:
The message above keeps popping up even though I enter the right password. What's wrong?

[[IMG]http://img84.imageshack.us/img84/4972/screenshotss7.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenshotss7.png)

---

### Post by benc123 on 2008-05-11
how do i map a drive in windows to the shared folder?

---

### Post by dpj23 on 2008-05-11
In Windows:

<click on> my Computer -> tools -> map network drive -> browse to your share folder...

---

### Post by fjgaude on 2008-05-12
> **myle said:**
> I use NAT and I have the following problem:
The message above keeps popping up even though I enter the right password. What's wrong?

[[IMG]http://img84.imageshack.us/img84/4972/screenshotss7.th.png[/IMG]](http://img84.imageshack.us/my.php?image=screenshotss7.png)

Did you enter the Samba password in Ubuntu:

```
sudo smbpasswd -a <login>
```

Enter your password about three times and then try and see if that fixed it.

---

### Post by fjgaude on 2008-05-12
> **benc123 said:**
> how do i map a drive in windows to the shared folder?

You use Explorer to go to Network Place or some name like that at the bottom, left side of the window... then Windows Shares or something like that. I'm not at my normal computer now.

---

