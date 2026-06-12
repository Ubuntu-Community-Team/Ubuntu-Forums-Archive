---
title: "Aquaris M10 where are Libreoffice files saved?"
date: 2016-10-28
forum: Ubuntu Phone and Tablet
---

### Post by cirtemnoj on 2016-10-28
I created some files on the Aquaris M10 tablet using Libreoffice. Although I can open the files from within Libreoffice, I cannot find them when I want to transfer them to my computer. Where are they kept?
Thanks for any help.

---

### Post by howefield on 2016-10-29
Should be kept in your ~/home folders, do you have the file manager application installed on the tablet ?

If not, it is available to install from the app store.

---

### Post by cirtemnoj on 2016-10-29
Thanks, howefield. 
I do have file manager installed, but even with full access I cannot find the files anywhere. I even created a new folder and saved to it, but when I open it it is empty.

---

### Post by howefield on 2016-10-29
I installed the libreoffice snap package to a full desktop installation and created a test.ods file and let it save to the default location which seems to be ~/snap/libreoffice/7/

Assuming the tablet is the same, do you have anything in that location ?

---

### Post by vasa1 on 2016-10-29
When you try to save a file using "File > Save As", don't you get to see the existing path (and location)? At least that's how it is on a conventional desktop with regular LibO, not the snap.

---

### Post by cirtemnoj on 2016-10-29
@howefield: Libreoffice was already installed when I bought the Aquaris. Pardon my ignorance, but is there anything that comes before the ~ in the address?

@vasa1: Yes, it does show the path and location, but when I look there after closing libreoffice, there is nothing there.

Again, thanks for the suggestions.

I had transferred a file from my computer to the tablet and put it in Documents folder on my SD card. When I open it in libreoffice and look at its properties it shows the location as /home/phablet/shared. But no folder with this name appears in file manager.

---

### Post by howefield on 2016-10-29
> **cirtemnoj said:**
> @howefield: Libreoffice was already installed when I bought the Aquaris. Pardon my ignorance, but is there anything that comes before the ~ in the address?

Yes, I know LibreOffice comes pre-installed in the tablet, I was just trying to tell you where files are saved to after installing the LibreOffice snap package in a full desktop machine, as far as I know "confinement" means the snap will save to the same location no matter if the application is installed to the phone, tablet or pc. Hope that makes some sort of sense.

~/ is a shorthand way of saying /home/user/. 

Do you have a snap folder in /home/user where "user" could be phablet or your user name ?

---

### Post by cirtemnoj on 2016-10-29
There doesn't seem to be any folder named /home/user. Using file manager, I go to device - home  and there is a file named 'phablet' which has the standard Documents, Downloads, Music, Pictures, Videos folders. No folder named 'jon'.

Thus far I've not used any snaps.

---

### Post by cirtemnoj on 2016-11-02
I'm still dealing with the same problem here.

I created a new libreoffice document and saved it in ~/phablet/documents. No problem,

I then closed the document, reopened it and added more to it. Saved the file. Closed the document.

When I reopened the file, what I had added was not there- only the original file.

I mentioned that libreoffice was installed when I bought the tablet. But later, the libreoffice icon disappeared from the Apps scope. I can still open the file I created, or files I transferred by clicking on the file in file manager and libreoffice writer is one of the options in the open with dialog.

Thinking that perhaps the problems lies in the particular version of libreoffice the tablet came with, I'm thinking that if I remove that version and re-install libreoffice using snaps, perhaps the problems I'm having would be resolved.

However, and here I'm presenting something that maybe should be in a different forum, when I try to install snapsd I get this message:
   W: Not using locking for read only lock file /var/lib/dpkg
   E:Unable to write to /var/cache/apt/
   E: The package lists or status file could not be parsed or opened.

I tried to do the installation of snapd using "sudo apt install snapd"

a. Am I on the right track to finding a solution?
b. What's the problem and how do I solve it with installing snapd?

Thanks for helping.

Jon

---

### Post by wgarcia on 2016-11-03
As far as I understand (I'm a newbie of Ubuntu Touch) the system is read-only and you cannot use "sudo apt-get". This can be changed, but then the system will not receive any automatic update anymore. Ubuntu Touch is set up to install "click" packages, but the rootfs is protected and read-only.

---

### Post by wlbi on 2016-11-04
> **cirtemnoj said:**
> 
[COLOR=#000000]I tried to do the installation of snapd using "sudo apt install snapd"[/COLOR]

[COLOR=#000000]a. Am I on the right track to finding a solution?[/COLOR]
[COLOR=#000000]b. What's the problem and how do I solve it with installing snapd?[/COLOR]

The tablet is by default write only. You can **NOT** install any packages like on the desktop or server system
You can remout it with  write permition, with the following command ```
sudo mount -o remount,rw /
```
But the you may damage the system. As long it is mounted rw, you can not use the [COLOR=#111111][FONT=Ubuntu]OTA updates anymore.[/FONT]
[FONT=Ubuntu]Just wait until S[/FONT][FONT=Ubuntu]naps are implemented properly. Right now that's just a development thing. I am sure they will provide a graphical interface for snaps, because no regular average user would like to hack in any commands. 

[/FONT][/COLOR]

---

### Post by felixgza2 on 2016-11-04
The files are in Device - Home - Phablet or their subfolders

---

### Post by krusty8 on 2016-11-05
> **cirtemnoj said:**
> I created some files on the Aquaris M10 tablet using Libreoffice. Although I can open the files from within Libreoffice, I cannot find them when I want to transfer them to my computer. Where are they kept?
Thanks for any help.

On the M10, Libreoffice is installed on top of something called Libertine. Libertine brings with it a chroot, basically it has it's own folder structure separate from the normal folder structure in the M10. A few select folders are accessible equally in Libreoffice and in the normal ubuntu touch system. For sure Documents is one of these folders (I think Pictures and Videos are also accessible).

In addition be aware that if you open a libreoffice document from the file manager it will actually create a copy of the file and open the copy in libreoffice. So, I'd suggest to open libreoffice first and then open the document you want and always store it in Documents or a subfolder therein.

It's a bit awkward and takes some getting used to.

PS: you can see the separate folder structures here:
/home/phablet/.cache/libertine-container/puritine/rootfs 
/home/phablet/.local/share/libertine-container/user-data/puritine

---

### Post by krusty8 on 2016-11-05
> **cirtemnoj said:**
> 
I created a new libreoffice document and saved it in ~/phablet/documents. No problem,

I then closed the document, reopened it and added more to it. Saved the file. Closed the document.

When I reopened the file, what I had added was not there- only the original file.


I think that's a consequence of the fact that the open with dialog triggered from the filemanager copies the file. 


> 
I mentioned that libreoffice was installed when I bought the tablet. But later, the libreoffice icon disappeared from the Apps scope. I can still open the file I created, or files I transferred by clicking on the file in file manager and libreoffice writer is one of the options in the open with dialog.


You want to add the *desktop apps* scope. The libreoffice icon has moved over there.

I don't think installing snap is what you want to do.

---

### Post by dtarrant on 2016-11-12
I encountered this problem last night. I created a text file with gedit. I was subsequently unable to find any way to delete it. I couldn't find my file within the touch file manager. Gedit could access my file, but there was no means to delete it. I then tried exploring the filesystem with the touch terminal app, but without success. Maybe I need to learn the CLI commands for searching/finding within hidden directories? Which commands will be most relevant?

---

### Post by krusty8 on 2016-11-12
> **dtarrant said:**
> Maybe I need to learn the CLI commands for searching/finding within hidden directories? Which commands will be most relevant?

Reread my posts above, then glance over
```
man find
```
then try
```
find ~/.local/share/libertine-container/user-data/ -iname '*Untitled*'
```
and let me know how it goes.

I just created a new file with gedit and saved it under the suggested name, and the above command gives me:
```
/home/phablet/.local/share/libertine-container/user-data/vivid/Untitled Document 1
```

---

### Post by dtarrant on 2016-11-12
> **krusty8 said:**
> Reread my posts above, then glance over
```
man find
```
then try
```
find ~/.local/share/libertine-container/user-data/ -iname '*Untitled*'
```
and let me know how it goes.

I just created a new file with gedit and saved it under the suggested name, and the above command gives me:
```
/home/phablet/.local/share/libertine-container/user-data/vivid/Untitled Document 1
```


Wow, that works! Many thanks for your excellent advice.

---

### Post by dtarrant on 2016-11-12
OK, so I found my gedit file and successfull deleted it using the command line. Then I revisited the touch file manager and navigated to device/home/phablet/. The folders Documents, Downloads, Music, etc were visible. Then I selected advanced features/show hidden files and a whole raft of folders showed up and I was able to navigate to puritine! Magic! The touch file manager is more powerful than I realised. Thank you krusty8 for pointing me in the right direction.

---

