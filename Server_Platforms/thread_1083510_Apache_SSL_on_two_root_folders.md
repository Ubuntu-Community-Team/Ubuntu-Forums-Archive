---
title: "Apache SSL on two root folders"
date: 2009-03-01
forum: Server Platforms
---

### Post by kungfu71186 on 2009-03-01
I got SSL up and running but i want to enable only for two "root" folders.

So i have my main root folder where i store all the website files at. (public_html)
I also want to enable secure access to another folder at the same level.

Problem im having is have to enable it at the parent level of those folders. I have other folders in there that i dont want anyone to be able to access and with SSL enabled on everything all you have to do is go to [https://domain.com/somefolder](https://domain.com/somefolder) and it does show up, even those access is forbidden id rather it just "not exist"

So visually this is what i got

Parent
|---Some Folder
|---Public_html
|---Folder2
|---Folder3

I want to be able to enable SSL on public_html and Some folder.
Right now in order to do that i have to enable it on Parent folder. Anyway to do this? Thanks.

---

### Post by loudog23 on 2009-04-20
Search the forum or google this:
```
AllowOveride on
```

I did not go through the htaccess part of thing yet, but _I think i might be remembering something_ that is liked with your problem. about this command

Sorry i can't help you more

---

