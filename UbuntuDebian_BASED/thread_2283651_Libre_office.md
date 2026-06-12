---
title: "Libre office"
date: 2015-06-23
forum: Ubuntu/Debian BASED
---

### Post by jesselashcraft on 2015-06-23
Can anyone tell me how to delete a specific document in LibreOffice?   

I can't find instructions anywhere, including "Help."  I don't want to delete the whole list, just a few
specific documents and keep them from appearing when I open LibreOffice. 

Thanks.

---

### Post by SeijiSensei on 2015-06-23
Are these documents that LO says needs to be repaired?  If so, let go through the process of identifying and repairing any documents it finds, then close each one.  It should not bother you about them again the next time.

If you are asking about simply deleting documents from the file system, that is much more easily handled by a file manager like Nautilus.  Navigate to the directory where the documents are stored and delete the ones you don't need.

---

### Post by vasa1 on 2015-06-23
I'm assuming you want specific files not to appear in the *Recent Documents* list. I very much doubt that is possible :(

---

### Post by vasa1 on 2015-06-24
> **vasa1 said:**
> I'm assuming you want specific files not to appear in the *Recent Documents* list. I very much doubt that is possible :(

Just came across this: [https://wiki.documentfoundation.org/ReleaseNotes/4.3#Start_Center_improvements](https://wiki.documentfoundation.org/ReleaseNotes/4.3#Start_Center_improvements)
> Selectively delete Recent Documents

---

### Post by jesselashcraft on 2015-06-24
> **SeijiSensei said:**
> Are these documents that LO says needs to be repaired?

No, I just want to clean up the desk top and delete documents that have outlived their usefulness.

> If you are asking about simply deleting documents from the file system, that is much more easily handled by a file manager like Nautilus. 

When I type "Nautilus" in the search feature of Zorin 9, it takes me to the "Home" file so I guess I don't have that.  But I take your point.

---

### Post by jesselashcraft on 2015-06-24
> **vasa1 said:**
> I'm assuming you want specific files not to appear in the *Recent Documents* list. I very much doubt that is possible :(

Yeah, I noticed that the "Recent Documents" list is the same as what's depicted graphically on the LibreOffice home page.  There's a "Clear List" option there under "File" but I don't want to get rid of all the shortcuts.

Edit: Hey, thanks for the link!  So will 4.3 just show up with a routine Zorin update or will I have to go somewhere to download it?

---

### Post by vasa1 on 2015-06-24
I don't know anything about Zorin.

---

### Post by sandyd on 2015-06-25
For the recent documents list:
Close LibreOffice

Go to
```

~/.config/libreoffice/4/registrymodifications.xcu
```

Search for ```
org.openoffice.Office.Histories/Histories/org.openoffice.Office.Histories:HistoryInfo['PickList']
```
You can now delete the corresponding lines for the recent document you want.

* Tested in Ubuntu 15.04, I don't have another version of Ubuntu to test it on at the moment

---

### Post by Bucky Ball on 2015-06-25
*Thread moved to **Ubuntu/Debian BASED**.*

While Zorin is based on Ubuntu, please be aware that the main support areas here are for the official Ubuntu family of flavours. Thanks.

Right click the file and 'Move to Trash'? Unaware of what desktop Zorin uses or you've installed in it.

---

### Post by dragonfly41 on 2015-06-25
Try installing ...

[http://extensions.services.openoffice.org/en/project/HistoryMaster](http://extensions.services.openoffice.org/en/project/HistoryMaster)

HistoryMaster-1.1.1.oxt

---

### Post by jesselashcraft on 2015-06-25
> **sandyd said:**
> For the recent documents list: Close LibreOffice

Go to...

When cutting and pasting those instructions into "Terminal," something called "Bash" is telling me no such file or directory exists.

But I appreciate your feedback, Sandy.

---

### Post by jesselashcraft on 2015-06-25
> **Bucky Ball said:**
> While Zorin is based on Ubuntu, please be aware that the main support areas here are for the official Ubuntu family of flavours.

OK, I'm confused.  If Ubuntu is the architecture that the Zorin Operating System is built on, why am I on the wrong forum?  I guess I just don't understand the relationship between Ubuntu and Linux and LibreOffice. (I'm new to Linux if you haven't already guessed). 

> Right click the file and 'Move to Trash'? 

Intuitive and rational, right?  That doesn't work.

---

### Post by Bucky Ball on 2015-06-25
Hmm. Can you open a terminal and type in 

```
gksudo nautilus
```

Go to Desktop folder and delete the files there. Close the browser immediately whether it works or doesn't as you have Nautilus open as root and can cause some breakage. 

Did it work? If so, perhaps a permissions problem, because if you can delete them as root, but not as your regular user ...

Is the only problem you're having trying to delete or access Libreoffice files and only on the desktop? Or in the list of 'Recent documents' when actually using Libreoffice? 


* There is the Ubuntu kernel on top of which are built a million and one spins, distros, flavours. Some are similar, some wildly different. It is impossible to support them all in the one place so we stick to the [Canonical-supported family of flavours]("http://www.ubuntu.com/about/about-ubuntu/flavours") which have enough similarities to make it feasible. 

You are, of course, quite welcome to post a thread here. Regardless of the forum section your thread is in, when a post lands on it, it goes to the top of the New Posts list. The categories make it easier for people to find stuff. 

[Zorin also has a forum]("http://zoringroup.com/forum/viewforum.php?f=3") and doesn't hurt posting in both. :)

Hope that helps. How did you go with the deletion?

---

### Post by sandyd on 2015-06-25
> **jesselashcraft said:**
> When cutting and pasting those instructions into "Terminal," something called "Bash" is telling me no such file or directory exists.

But I appreciate your feedback, Sandy.

Updated, I have only tested it on Ubuntu 15.04

---

### Post by jesselashcraft on 2015-06-26
> **Bucky Ball said:**
> Hope that helps. How did you go with the deletion?


OK, I think I'm getting there.  I don't have Nautilus installed.  I get a "Failure to load module" message in "Terminal."  

But by running the cursor over the shortcut on the LibreOffice start page, it tells you where the file is located.  I had documents in two different files which was confusing me - that is: home/jesse and home/jesse/documents.  Not sure how that happened. 

Deleting the document gets rid of the shortcut on the start page. When 4.3 comes out,  I'll find out if I can delete the shortcut without deleting the document.    
Really not that big of a deal but I guess I'm kind of anal-retentive about computer tidiness.  

Thanks for the inputs.

---

