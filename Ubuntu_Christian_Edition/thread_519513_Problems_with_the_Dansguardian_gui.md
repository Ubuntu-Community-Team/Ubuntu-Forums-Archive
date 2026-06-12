---
title: "Problems with the Dansguardian gui"
date: 2007-08-07
forum: Ubuntu Christian Edition
---

### Post by guypilkinton on 2007-08-07
Hi I installed unbuntu feistythe other day before I knew a CE addition existed and then found Dansguardian and your GUI addon. I don't know enough about linux to configure things without a GUI.  I think I have installed the GUI for fiesty correctly, but when I put my password into the configure Dansguardian entry dialog screen, and press enter, things just disappear and nothing  starts.  Any ideas what is going wrong here?

---

### Post by mhancoc7 on 2007-08-07
> **guypilkinton said:**
> Hi I installed unbuntu feistythe other day before I knew a CE addition existed and then found Dansguardian and your GUI addon. I don't know enough about linux to configure things without a GUI.  I think I have installed the GUI for fiesty correctly, but when I put my password into the configure Dansguardian entry dialog screen, and press enter, things just disappear and nothing  starts.  Any ideas what is going wrong here?

I am not sure what is causing this, but the first thing I would suggest would be to run the install script a second time just to be sure everything got installed. The script is supposed to check for you, but that would be my suggestion.

Jereme

---

### Post by mysticrider92 on 2007-08-07
Could you try running it from a terminal (Applications>Accessories>Terminal) and posting the output here? 
Type this to run it:
> sudo /usr/local/apps/parental-control/UbuntuCE_Parental_Controls

My Feisty won't run it from this command, but that will give an idea of what could be wrong.

---

### Post by guypilkinton on 2007-08-07
Hi I ran this in a terminal window and this is what happened.

ruth@ruth-desktop:~$ sudo /usr/local/apps/parental-control/UbuntuCE_Parental_Controls
Password:
Syntax error in project file.
Cannot preload libraries: Success
sizeof(CLASS) = 256 !
gbx: Swapping archive
ERROR: #1: Out of memory
Segmentation fault (core dumped)
ruth@ruth-desktop:~$

---

### Post by guypilkinton on 2007-08-08
Could my problem have anything to do with the gui install being on a 64 bit system or the fact that I don't have a root account?

---

### Post by mhancoc7 on 2007-08-08
> **guypilkinton said:**
> Could my problem have anything to do with the gui install being on a 64 bit system or the fact that I don't have a root account?

Yes, Ubuntu CE has not been released for 64 bit.

Jereme

---

### Post by guypilkinton on 2007-08-08
So how can configure Dansguardian.  I am very new to using linux.  I  want to be able to make it appropriate for a 15 year old to use.  At the moment it won't even let her access her school homework site.  When I go into change the exception list it won't let me change save anything.      How do I log in as the administrator in order to edit exception list?

---

### Post by mhancoc7 on 2007-08-08
> **guypilkinton said:**
> So how can configure Dansguardian.  I am very new to using linux.  I  want to be able to make it appropriate for a 15 year old to use.  At the moment it won't even let her access her school homework site.  When I go into change the exception list it won't let me change save anything.      How do I log in as the administrator in order to edit exception list?

You will need to edit the dansguardian files as root.

```
sudo gedit "PATH_TO_FILE"
```

Then reconfigure dansguardian.

```
sudo dpkg-reconfigure dansguardian
```

Jereme

---

### Post by mysticrider92 on 2007-08-08
I just wanted to suggest a temporary solution to the Dansguardian configuration. There is a program called Webmin that will allow you to set up configurations for network programs in Linux, and a Dansguardian module you can install. This will let you configure Dansguardian using Firefox.

I will try to get a GUI working for 64 bit, but I still am not sure what program/language to use for it, so it might take a while.

---

### Post by guypilkinton on 2007-08-13
Thanks guys I managed to work out how to configure the files and things seems to be working well now.

---

### Post by guypilkinton on 2007-08-16
Hi I got your new dansguardian gui to work on ubuntu thanks very much.  Can you just tell me how to set up another user account so my kids don't have access to the GUI too.  And I have noticed that with Dansguardian going we loose network access to folders on other computers in the house.  How can I fix this?

---

