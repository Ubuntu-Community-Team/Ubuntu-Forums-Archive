---
title: "Add Repository with a User-Friendly GUI"
date: 2008-12-07
forum: Ubuntu Brainstorm
---

### Post by ibizatunes on 2008-12-07
If I want to Add the Medibuntu Repository (and any other repo's for that matter), I have to go to the terminal and add something like following lines

sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

(Or the repository of your choice)

It would be nice, in the add/remove there was option to run this command for you, adding the repository into the /etc/apt/sources.list.d/medibuntu

Also there could be others like wines repo's etc - which you have to drop in the terminal to do normally, but if there was a GUI it would be ALOT easier (a new users would be more comfortable with it as well)

======

After the install it would be nice, if there was a option of seeing what new application are available after adding new source list to your repository

(Maybe a extra box in the add / remove)

Mediaubuntu - listing thing like google earth, skype etc
Wines - stable version and development version etc


This give new users a easy way to install extra stuff that doesn't come by default with ubuntu 

[http://brainstorm.ubuntu.com/idea/16312/](http://brainstorm.ubuntu.com/idea/16312/)

---

### Post by Sub101 on 2008-12-07
You can add Software Sources from System ==> Admin ==> Software Sources

---

### Post by smartboyathome on 2008-12-07
> **Sub101 said:**
> You can add Software Sources from System ==> Admin ==> Software Sources

And there won't be anything easier for at least a while because the devs are worried that anything easier would be a security hole (which it would be).

---

