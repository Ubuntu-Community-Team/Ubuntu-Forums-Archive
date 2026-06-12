---
title: "Trying to Create Vault on Secondary Drive - enc File Not Found"
date: 2018-06-17
forum: Security
---

### Post by uRock on 2018-06-17
I am trying to create a vault outside of the /home partition and getting an error stating the xyz.enc file can't be found. I created the file manually, then tried again. It lets me click open but does nothing. Am I missing a step somewhere?

Screen capture = [https://www.youtube.com/watch?v=MyxtUgNe1UQ&feature=youtu.be](https://www.youtube.com/watch?v=MyxtUgNe1UQ&feature=youtu.be)

---

### Post by #&amp;thj^% on 2018-06-17
> **uRock said:**
> I am trying to create a vault outside of the /home partition and getting an error stating the xyz.enc file can't be found. I created the file manually, then tried again. It lets me click open but does nothing. Am I missing a step somewhere?

Screen capture = [https://www.youtube.com/watch?v=MyxtUgNe1UQ&feature=youtu.be](https://www.youtube.com/watch?v=MyxtUgNe1UQ&feature=youtu.be)

uRock I don't know if you have seen this link or not: [https://www.addictivetips.com/ubuntu-linux-tips/create-encrypted-folders-on-kde-linux-desktop-with-vaults/](https://www.addictivetips.com/ubuntu-linux-tips/create-encrypted-folders-on-kde-linux-desktop-with-vaults/)
EDIT This is a good link also: [https://linuxconfig.org/create-encrypted-folders-with-plasma-vault](https://linuxconfig.org/create-encrypted-folders-with-plasma-vault)
Trust me it was not as easy as I had first thought. :)
I'm now using XFCE so I probably won't remember the hoops I went through.
Tip:
> The location for the encrypted vaults is (by default) ~/.local/share/plasma-vault/. This location shouldn&#8217;t need to be changed and works just fine. Mount points open under ~/Vaults. If you&#8217;d like it to mount somewhere else, go to the &#8220;Mount point&#8221; dialog box and write in a new folder location. Keep in mind that you&#8217;ll only be able to specify a location that already exists, as the Wizard will not create a new folder for you.

---

### Post by uRock on 2018-06-17
Thanks for the reply. So the data actually gets stored in the mount point selection? The interface is kinda confusing. I want to make sure I don't fill the SSD that's being used for / and /home.

---

### Post by #&amp;thj^% on 2018-06-17
> **uRock said:**
>  The interface is kinda confusing. .

True That! LOL ;)
It wasn't hard or fatal on my end with the first few mistakes I made. (Easily corrected)

---

### Post by uRock on 2018-06-22
Went ahead and installed VeraCrypt. I prefer the control offered by the software.

---

