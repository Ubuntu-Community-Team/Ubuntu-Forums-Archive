---
title: "How to install SCIM in ubuntu 10.04"
date: 2010-06-09
forum: Tamil Team - India
---

### Post by karthick87 on 2010-06-09
I am using ubuntu 10.04,Pls tell me the way to install SCIM..

---

### Post by kimikrishna on 2010-06-25
> **getyourkarthick said:**
> I am using ubuntu 10.04,Pls tell me the way to install SCIM..
Hi,
First,Go to language support and install Tamil .
Then Do this : 

```
sudo apt-get install scim  language-pack-ta language-pack-ta-base scim-tables-additional scim-modules-table 
```

And then 

```
cd /etc/X11/Xsession.d
sudo gedit 75custom-scim_init 
```

A file will be opened.
In that file, Paste these lines and save it :

```
export XMODIFIERS="@im=SCIM"

export GTK_IM_MODULE="scim"

export XIM_PROGRAM="scim -d"
```


Logout and in. Then an icon should appear in the panel, click on it and choose language .

---

