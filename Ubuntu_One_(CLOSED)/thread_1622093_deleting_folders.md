---
title: "deleting folders"
date: 2010-11-15
forum: Ubuntu One (CLOSED)
---

### Post by andrea000 on 2010-11-15
I can't delete folders from ubuntu one's web site there is no delete button that i can find.

---

### Post by IBUA on 2010-11-21
> **andrea000 said:**
> I can't delete folders from ubuntu one's web site there is no delete button that i can find.

Having the same problem :|

---

### Post by Jetso on 2010-11-21
Go to >More, and at the bottom it says delete.

---

### Post by duanedesign on 2010-11-22
Folders in your Ubuntu One folder and folders in your User designated Folders (UDF) can be deleted like Jetso pointed out. However User Designated Folders themselves, Folders in your $Home outside Ubuntu One directory that have been set to sync, can not currently be deleted from the web interface.

You can see here that the UDF has only the share Folder option
[[img]http://farm5.static.flickr.com/4129/5197788171_4a872a20eb.jpg[/img]](http://www.flickr.com/photos/56198175@N04/5197788171/)
[SS.u1delete](http://www.flickr.com/photos/56198175@N04/5197788171/)

One way to delete a folder from the cloud but keep it locally is to use the u1sdtool from the commandline.

First run:
```
u1sdtool --list-folders
```

You will get something like this:
>   id=[COLOR="Red"]45c78046-19b3-49b4-bbf3-dcf10aa28876[/COLOR] subscribed=True path=/home/duanedesign/test
Get the [COLOR="Red"]Folder ID[/COLOR], in this example it is [COLOR="Red"]45c78046-19b3-49b4-bbf3-dcf10aa28876[/COLOR], of the folder you wish to delete. Of course this will be different for you. Then run the following command with the [COLOR="Red"]folder ID[/COLOR] you got from the previous command:
```
u1sdtool --delete-folder=[COLOR="Red"]45c78046-19b3-49b4-bbf3-dcf10aa28876[/COLOR]
```

This will delete the folder from the server but leave it untouched locally.

thank you,
duanedesign

---

