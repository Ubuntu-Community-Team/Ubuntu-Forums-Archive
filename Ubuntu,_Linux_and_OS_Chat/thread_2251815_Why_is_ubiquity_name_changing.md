---
title: "Why is ubiquity name changing?"
date: 2014-11-06
forum: Ubuntu, Linux and OS Chat
---

### Post by Louis_Levene on 2014-11-06
hi! i am currently in the procces of creating a custom distro of ubuntu with some of my favorite apps included, and i went and changed the .disk/info file to get ubiquity to call it what i want, and i set it to call it Mbuntu OS, and when i boot into the desktop the icon says "Install Mbuntu OS" as i would excpect, however when i double click on that, it says preparing to install Mbuntu without the "OS" at the end... the whole installer continues to call it Mbuntu untill it is finished... any ideas
Thanks!

---

### Post by Bucky Ball on 2014-11-06
*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by Sly_Hackr on 2014-11-07
My immediate guess would be that ubiquity drops everything after the first "word". If my memory serves me correctly, it first shows the version of Ubuntu and 'LTS' if it is an LTS release, such as Ubuntu 14.04 LTS. Obviously, displaying just Ubuntu, which is the name of the OS, would look nicer than constantly showing the whole version scheme. 

You may want to check in the source of Ubiquity, specifically the version you're using. It would either be in the ubiquity package itself (it has some GTK backend stuff in there I believe) or the ubiquity frontend package, probably GTK version if that's what you're using. 

With that said, I could be way off, but, like I said, that would be my first guess.

---

### Post by Louis_Levene on 2014-11-08
What do you mean my check in the source of Ubiquity? (Sorry I'm kind of a Ubiquity nub as this is my first time using it) Also do you know why it would say the whole thing on the desktop but not the installer? And also i found another linux distro called elementary os and im pretty sure that ubiquity calls it elementary os. Thanks for the help.

---

### Post by QIII on 2014-11-08
Just a legal point, here ...

Canonical has a trademark on *buntu, so I'd either consider a different name or check with Canonical's legal department.

From [this]("http://www.ubuntu.com/legal/terms-and-policies/intellectual-property-policy"):

> You will require Canonical’s permission to use: (i) any mark ending with  the letters UBUNTU or BUNTU which is sufficiently similar to the  Trademarks or any other confusingly similar mark, and (ii) any Trademark  in a domain name or URL or for merchandising purposes.

---

### Post by Louis_Levene on 2014-11-08
then how come lubuntu kubuntu etc exsit, do you know where i can ask canonical for permission... if not its not a biggy i can just think of a different name...

---

### Post by coffeecat on 2014-11-09
Because Lubuntu, Xubuntu, etc are [official flavours]("http://www.ubuntu.com/about/about-ubuntu/flavours"). 

> **Louis_Levene said:**
> do you know where i can ask canonical for permission... 

Read the link QIII posted. There is a link in there.

---

### Post by Louis_Levene on 2014-11-11
ok i just changed the name to something else and all is working fine now... thanks for all the help!

---

