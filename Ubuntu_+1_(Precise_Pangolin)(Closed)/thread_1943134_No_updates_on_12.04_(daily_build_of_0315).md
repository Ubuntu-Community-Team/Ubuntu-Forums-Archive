---
title: "No updates on 12.04 (daily build of 03/15)"
date: 2012-03-19
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by jvermeulen on 2012-03-19
Hi all,

I'm having troubles getting updates on my 12.04 installation. I used a daily build from March, 15, 2012. When doing an sudo apt-get update && apt-get upgrade gives me nothing new. Software center also doesn't notify me of new packages.

Should I change something in my sources.list for this? Would like to get new updates before the final 12.04 release, as there are still some bugs with my current version.

Thanks a lot!

---

### Post by rapiertg on 2012-03-19
Hello. You can try to change the mirror. 

Before 11.10 Ubuntu's mirror in my country broke down, and i got no updates for a month before i realized something was wrong.

---

### Post by meborc on 2012-03-19
> **jvermeulen said:**
> Hi all,

I'm having troubles getting updates on my 12.04 installation. I used a daily build from March, 15, 2012. When doing an sudo apt-get update && apt-get upgrade gives me nothing new. Software center also doesn't notify me of new packages.

Should I change something in my sources.list for this? Would like to get new updates before the final 12.04 release, as there are still some bugs with my current version.

Thanks a lot!

the brute force option is to just delete the country code from the deb lines in your sources.list file. For example in my case I change ```
deb http://se.archive.ubuntu.com/ubuntu/ precise main restricted
```to ```
deb http://archive.ubuntu.com/ubuntu/ precise main restricted
```

and so for all the lines. I am sure there is a GUI way to do things, but I have not spent enough time with the software center to know how

then update && upgrade or dist-upgrade

---

### Post by grahammechanical on 2012-03-19
You can run Update Manager from the power cog menu. It is the fourth line down. Then click Settings and go to the Update tab and see if Automatically check for updates is set to Never.

From the Ubuntu tab you can select where to Download From by means of a drop down menu. It will even search for the best Mirror site for you.

Regards.

---

### Post by jvermeulen on 2012-03-20
Hi all,

Thanks for your suggestions! I've managed to update my packages, but ran into the 'partial upgrade' bug: [http://ubuntuforums.org/showthread.php?t=1940258]("http://ubuntuforums.org/showthread.php?t=1940258")

I'll try to wait and see if this fixes itself.

---

