---
title: "A question about Dropbox."
date: 2009-10-05
forum: The Cafe
---

### Post by donniezazen on 2009-10-05
Hi all,

I posted this question on Dropbox forum but have to comeback to ubuntuforums because this the only place where i ever find answers to my technical questions.

If you find it appropriate please answer it and if you hate it please request the moderator to remove it instead of posting offensive replies.

I just installed the Dropbox. I have a few questions. Please help.

1. If i install Dropbox on multiple computers and delete a file from one computer will it get deleted from all computers?

2. Should my computer have free space as much size of my Dropbox? That means are files stored locally after syncing?

3. How did you set up your Dropboxes? I have 2 laptops and an iPhone. Like having folders and links with same name. For example, I have a folder in my Ubuntu home folder. I make a link of it and put it in Dropbox. I now go to other computer and make a folder with same name, create a link and put it in Dropbox. So, i have same names for all links and folder. Will all my folders get updated if i make change in any of the folders?

I am using Ubuntu jaunty and Dell 6400\E1505.

Thank you to all generous Ubuntu forum members-
SK

---

### Post by Tibuda on 2009-10-05
1. yes
2. yes
3. I didn't understood this.

---

### Post by jonian_g on 2009-10-05
Many questions.

I can only answer the first.

1.yes

---

### Post by Joeb454 on 2009-10-05
> **soham_1207 said:**
> 
3. How did you set up your Dropboxes? I have 2 laptops and an iPhone. Like having folders and links with same name. For example, I have a folder in my Ubuntu home folder. I make a link of it and put it in Dropbox. I now go to other computer and make a folder with same name, create a link and put it in Dropbox. So, i have same names for all links and folder. Will all my folders get updated if i make change in any of the folders?


I'm guessing you're referring to using links so that your dropbox syncs files that aren't in the ~/Dropbox directory? I do this on my system, it works very well :)

Have you tried following this HowTo from Dropbox? I believe that's how I set mine up: [http://wiki.getdropbox.com/TipsAndTricks/SyncOtherFolders](http://wiki.getdropbox.com/TipsAndTricks/SyncOtherFolders)

---

### Post by donniezazen on 2009-10-05
Thank you so much.

I am sorry for my bad English. I am not a native English speaker.

The question is as follows.

I want to sync two laptops and my iPhone. I have to have same files in both the laptops. For example.

I have my files in a folder in home folder of Ubuntu-laptop. I do not want to put it in Dropbox so i create a symlink as a root. I move it into Dropbox. I do the same in my Ubuntu-netbook. So as to save myself from many folders with different names i have total 4 folders.

Ubuntu-laptop a folder and its link
Ubuntu-netbook a folder and its link

All have same names. Folders are in Home Folder and Links are in Dropboxes of my laptop and netbook. My question is if i make change in any of the folders or links will the change be implemented on all folder, links and web.

I hope i am more clear now.

Thanks

---

### Post by meho_r on 2009-10-05
I still don't understand 3. But here's an idea.

You have a folder named "Test" which you want to appear on all three of your computers. The easiest way is to put it in your Dropbox folder and then make links of it and put these links on any place you like on all three computers (or 2 comps + iPhone). So, the scheme is as follows:

1. Real folder is in Dropbox folder (~/Dropbox/Test) and it'll appear automatically on every of your computers.

2. On every of your computers you created links to ~/Dropbox/Test and put these links where ever you like and named them as you like. For example, on your laptop you put that link on your Desktop and named it "Test-laptop". When you run link, real folder which is in Dropbox folder (~/Dropbox/Test) will be opened and every change on its content will be saved on every of your computers.

I don't see the point in opposite process, that is of creating link of a folder/file and put that link inside Dropbox folder (at least symbolic link not).

---

### Post by donniezazen on 2009-10-05
> **meho_r said:**
> I still don't understand 3. But here's an idea.

You have a folder named "Test" which you want to appear on all three of your computers. The easiest way is to put it in your Dropbox folder and then make links of it and put these links on any place you like on all three computers (or 2 comps + iPhone). So, the scheme is as follows:

1. Real folder is in Dropbox folder (~/Dropbox/Test) and it'll appear automatically on every of your computers.

2. On every of your computers you created links to ~/Dropbox/Test and put these links where ever you like and named them as you like. For example, on your laptop you put that link on your Desktop and named it "Test-laptop". When you run link, real folder which is in Dropbox folder (~/Dropbox/Test) will be opened and every change on its content will be saved on every of your computers.

I don't see the point in opposite process, that is of creating link of a folder/file and put that link inside Dropbox folder (at least symbolic link not).


So you are saying that original folder must be put in Dropbox folder. Does it matter? I have my original folder in home folder and link in Dropbox and its working.

Thanks,
SK.

---

### Post by meho_r on 2009-10-07
> **soham_1207 said:**
> So you are saying that original folder must be put in Dropbox folder. Does it matter? I have my original folder in home folder and link in Dropbox and its working.

Thanks,
SK.

Well if it's working... Seems that Dropbox does follow the link and upload actual file, not its symbolic link. I wasn't aware of that.

---

### Post by infestor on 2009-10-07
also one question from me:
can you **recover** deleted files in dropbox?

---

### Post by Tibuda on 2009-10-07
> **infestor said:**
> also one question from me:
can you **recover** deleted files in dropbox?

Yes from the web interface. There's a "show delete files" button.

---

### Post by howefield on 2009-10-07
> **infestor said:**
> can you **recover** deleted files in dropbox?

[https://www.getdropbox.com/help/11](https://www.getdropbox.com/help/11)

---

### Post by meho_r on 2009-10-07
> **infestor said:**
> also one question from me:
can you **recover** deleted files in dropbox?

But don't forget that deleted file can be recovered **only** in a period of **one** month after it's been deleted, after which it is removed from Dropbox server. Paid version doesn't have this limitation.

---

