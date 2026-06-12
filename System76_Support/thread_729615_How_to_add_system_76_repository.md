---
title: "How to add system 76 repository"
date: 2008-03-20
forum: System76 Support
---

### Post by izquierdista on 2008-03-20
Hello,
A while back after having had an unsuccessful upgrade to gutsy gibbon due to my battery running out in the middle of the upgrade I had to do it from scratch. I installed it and then I never got around to installing the system 76 driver until today. 

Well I installed the driver and was pleased to see that finally my flickering screen was gone and that everything worked perfectly, the only thing that I noticed was that for some reason the repository was not added to my software sources. 

How do I go about adding the system 76 repository to my software sources by hand? 

I tried typing:

[http://planet76.com/repositories/](http://planet76.com/repositories/)

but the "OK" button is still grayed out. what should I do?

---

### Post by thomasaaron on 2008-03-20
You should add this to the bottom of your /etc/apt/sources.list file:

## updates specifically for your computer
deb [http://planet76.com/repositories/](http://planet76.com/repositories/) ./

---

