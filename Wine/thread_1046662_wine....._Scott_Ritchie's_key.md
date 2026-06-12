---
title: "wine..... Scott Ritchie's key"
date: 2009-01-21
forum: Wine
---

### Post by kingnug on 2009-01-21
I am trying to download wine but when I click the link to  get the Scott Ritchie's key it leads to a page of text... can anyone help me with this?

---

### Post by TheLions on 2009-01-21
press right click and press "Save Link as"

---

### Post by plucky on 2009-01-21
> **kingnug said:**
> I am trying to download wine but when I click the link to  get the Scott Ritchie's key it leads to a page of text... can anyone help me with this?

Try from a terminal this command ```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```


Good Luck

---

### Post by kingnug on 2009-01-28
thanx

---

### Post by Egilan on 2009-02-10
I can't import that file. When I click that file, the window closes and there doesn't come any new lines, what should happen, you know.

Sorry my bad English...:frown:

---

### Post by plucky on 2009-02-10
See this [link](http://www.winehq.org/download/deb) to install the Wine repository.

> I can't import that file. When I click that file, the window closes and there doesn't come any new lines, what should happen, you know.


Are you doing this in a terminal window? All it does is add the key file to authenticate the Wine repository.

Good Luck

---

### Post by Egilan on 2009-02-11
It came there next day... I think reboot helped. But now I don't have icon to Wine, there is some icons in "Lost and found" (I'm not sure, about that, what it is in English, but some kind of that) And I have tried every thing, what is in that manual, what you gave...:(

---

### Post by plucky on 2009-02-11
> **Egilan said:**
> It came there next day... I think reboot helped. But now I don't have icon to Wine, there is some icons in "Lost and found" (I'm not sure, about that, what it is in English, but some kind of that) And I have tried every thing, what is in that manual, what you gave...:(

Those instructions are to install the repository in your sources list.It does not actually install Wine.

Open a terminal and ```
sudo apt-get update
``` to reload the repository databases.If there are no errors then do this again in the terminal ```
sudo apt-get install wine
``` will install wine from the wine repository.

If there are any errors,do not proceed to the next step,but post the terminal output to the forums.


Good Luck

---

### Post by Egilan on 2009-02-11
There was not any errors, and I have already done that next stage, but I still have icons like these: "Notebook", "Delete Wine-program's installs", "Search C:drive" and "Wine's settings". (I'm not sure about that, are those correct names, but I translated them directly) And those files are in "Lost and found" -directory...

And sorry again my bad English...


OH... That winecfg, what I'm trying to find, is Winen asetukset, in Finnish...

---

### Post by plucky on 2009-02-11
> **Egilan said:**
> There was not any errors, and I have already done that next stage, but I still have icons like these: "Notebook", "Delete Wine-program's installs", "Search C:drive" and "Wine's settings". (I'm not sure about that, are those correct names, but I translated them directly) And those files are in "Lost and found" -directory...

And sorry again my bad English...


OH... That winecfg, what I'm trying to find, is Winen asetukset, in Finnish...

The "Lost and Found" directory should not be accessible by the normal user,as it is where the system stores recovered files. When I try to open that directory I get "You do not have the permission necessary to view this folder".

So I am wondering how the files got in there and how you are able to see them?


Those icons in the Lost and Found folder are the icons I have in the Wine menu under Applications.How they got into your Lost and Found folder,I have no idea.

Perhaps someone else can help.


Good Luck

---

