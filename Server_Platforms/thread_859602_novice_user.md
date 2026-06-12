---
title: "novice user"
date: 2008-07-14
forum: Server Platforms
---

### Post by pmackenzie on 2008-07-14
Need some advice on why when I try to use the apt-get command it tells me that whatever pkg I want is not there. Now I have installed Ubuntu server on a notebook should that be an issue and would it affect the apt-get command. If so is there a remedy for it. The package in question is file server and I know it comes with the CD as it is one of the options whilst I was doing the initial install.

---

### Post by chuck jessup on 2008-07-14
well i dont beleve that would have any bearing on apt-get. in the cli type 'find and it should show a directory listing of the packages, and software. correct me if i am wrong... and apt-get shouldne be effected by the type of computer it is installed on... i have a mail server that is a mb and a ps and a rig of jobd hdd there isnt a case its completely a jerry-rig'ed setup. and i know of others who run a server on their notebooks, smoking ones!

best reguards,
Jesse Fender

---

### Post by windependence on 2008-07-15
First, do a:

```
sudo apt-get update
```

Then to find the package you want:

```
sudo aptitude search <keyword>
sudo aptitude show <packagename>
```


-Tim

---

### Post by hyper_ch on 2008-07-15
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

