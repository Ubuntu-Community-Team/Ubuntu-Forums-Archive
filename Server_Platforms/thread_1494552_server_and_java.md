---
title: "server and java"
date: 2010-05-27
forum: Server Platforms
---

### Post by gogreenpower on 2010-05-27
i've been using ubuntu desktop editions to run my server setup and my java based media servers, but the 10.04 update has has ruined my setup as the server wont start without a monitor attached no matter what i try, so im wondering if the server editions can run java programs? and if it'll start with no monitor attached?

thanks

---

### Post by sanguinoso on 2010-05-27
I'm not sure what you mean; the server won't boot without a monitor attached? The server editions are certainly capable of running java programs. And mine certainly starts with no monitor, however the server editions don't have any user interfaces installed by default.

---

### Post by gogreenpower on 2010-05-27
sorry, the desktop edition i was using as the server wont boot without a monitor. 

is java installed by default or do you have to add it?

---

### Post by sanguinoso on 2010-05-27
Usually you have to add it. 
```
sudo apt-get install sun-java6-jdk
```

---

### Post by arrrghhh on 2010-05-27
> **sanguinoso said:**
> Usually you have to add it. 
```
sudo apt-get install sun-java6-jdk
```

This is NOT in the main repo's any longer.  You have to enable the partner repo, or perferrably use the openJDK version which is in the main repo's.

---

### Post by sanguinoso on 2010-05-28
> **arrrghhh said:**
> This is NOT in the main repo's any longer.  You have to enable the partner repo, or perferrably use the openJDK version which is in the main repo's.

Have you ever programmed with the OpenJDK? Its a piece of crap. I had a lot of problems with it these past few months.

---

### Post by arrrghhh on 2010-05-28
> **sanguinoso said:**
> Have you ever programmed with the OpenJDK? Its a piece of crap. I had a lot of problems with it these past few months.

I run Sun's version as well, and don't even program.  I used the word 'preferable' as it is the Ubuntu-preferred package.  Just giving a heads up of the change, because I couldn't install Sun's version until I enabled the partner repo...

---

### Post by sanguinoso on 2011-03-29
Gotcha, as of now the OpenJDK seems to be working fine programming wise.

---

