---
title: "Most popular alternatives to TrueCrypt, ideally cross-platform"
date: 2014-07-08
forum: Ubuntu, Linux and OS Chat
---

### Post by jcllings on 2014-07-08
I'm looking for a cross platform alternative to TrueCrypt. No arguments please. If you think X is the most popular, just say so and let the next guy have his say also. 

Jim C.

---

### Post by Habitual on 2014-07-08
Why? 7.1a is fine.

---

### Post by grier-devon on 2014-07-08
> **Habitual said:**
> Why? 7.1a is fine.
Because the project has been discontinued and also does not support encryption on Windows 8 UEFI support, as the OP mentioned something cross platform. Wish I could add value to this but I only run Ubuntu and set up full disk encryption through the installer but I will google and play with some things and get back to this topic.

---

### Post by jcllings on 2014-07-08
Define, "fine".  I'm seeing a lot of conflicting information on the web and that is bad. I see in one location where they talk about large swaths of code that were removed, for example. Unmaintained is bad enough though. If a bug is found tomorrow, who gets it? Nobody and that is unacceptable.

---

### Post by Vladlenin5000 on 2014-07-08
> **jcllings said:**
> Define, "fine".  I'm seeing a lot of conflicting information on the web and that is bad. I see in one location where they talk about large swaths of code that were removed, for example. Unmaintained is bad enough though. If a bug is found tomorrow, who gets it? Nobody and that is unacceptable.

 You probably misread/misunderstood something there... Large parts of the code were indeed removed but from the latest (and last) version which is read-only and intended for data backup from already created containers.
7.1a is exactly the same since it was released.
You can use other still maintained apps/tools to manage your current containers if you no longer trust 7.1a to do that for you.
You're bug argument, in this case is... Bugged (pun intended). Your containers aren't more prone to be compromised now or next year then they always were. Likewise, your already installed TC is as prone to a bug that can compromise your containers as is any piece of code you have, had or plan to have in your OS.

---

### Post by grier-devon on 2014-07-08
After much research the only question I have is are you trying to do full disk encryption or just files and folders? If you are just doing files and folders then I recommend....

gpg
AES Crypt
[http://www.aescrypt.com/linux_aes_crypt.html](http://www.aescrypt.com/linux_aes_crypt.html)

For full disk then use.....
GnuPG
[https://www.gnupg.org/](https://www.gnupg.org/)

I think a lot of people are missing the point about TrueCrypt, was it a great encryption tool? Yes, but the project does not support modern hardware configuration (UEFI) and further more why continue to use something no longer being developed? Being the project has been discontinued and for that reason it is important to find an alternative in which we all can stand behind.

---

### Post by Bucky Ball on 2014-07-08
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Inevitably, 'what is the most popular ...' and 'what is the best ...' type threads turn into discussions/debates, as this one has. Incidentally:

>  ... let the next guy have his say also. 

There are plenty of girls here, too. The next user?

---

### Post by SuperFreak on 2014-07-08
> **grier-devon said:**
> 
For full disk then use.....
GnuPG
[https://www.gnupg.org/](https://www.gnupg.org/)


Looks promising but it is CLI right? 
It is still in development but the fork of Truecrypt will (hopefully) be [CIPHERSHED]("https://ciphershed.org/") which will have a similar GUI to Truecrypt

---

### Post by grier-devon on 2014-07-08
> **SuperFreak said:**
> Looks promising but it is CLI right? 
It is still in development but the fork of Truecrypt will (hopefully) be [CIPHERSHED]("https://ciphershed.org/") which will have a similar GUI to Truecrypt

Here is the GUI tool for Windows
[http://www.gpg4win.org/](http://www.gpg4win.org/)

GUI for Ubuntu
[https://apps.ubuntu.com/cat/applications/raring/seahorse/](https://apps.ubuntu.com/cat/applications/raring/seahorse/)

---

### Post by SuperFreak on 2014-07-09
> **grier-devon said:**
> Here is the GUI tool for Windows
[http://www.gpg4win.org/](http://www.gpg4win.org/)

GUI for Ubuntu
[https://apps.ubuntu.com/cat/applications/raring/seahorse/](https://apps.ubuntu.com/cat/applications/raring/seahorse/)

Thanks, I will look into it

---

