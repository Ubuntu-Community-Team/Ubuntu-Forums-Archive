---
title: "Help!! USP broke my system"
date: 2007-03-31
forum: Ubuntu System Panel
---

### Post by mthakur2006 on 2007-03-31
Hi, 
I downloaded the USP alpha2 version and when I tried to install it, it did something but did not install it. I tried it again and said that some other program was using it and so it could not do it so I gave up. A few moments later, an update icon came up saying that the package usp needed to be reinstalled but couldn't find the archives for it. I download it again from the same site and when i tried to reinstall it, it said that the package was corrupted or i didn't have sufficient permission. i tried it as root and still no luck.

I am stuck, i cannot install subversion either because when i do sudo apt-get install subversion (or anything) i says that the package usp blah blah blah (same error).

Can anyone help, please?
I m desperate.
Thanks in advance.

P.S. I upgraded to Fiesty 7.04 today. Ignore my signature please. Thanks.`

---

### Post by Malac on 2007-03-31
I think this is a Feisty issue and we should probably put a warning on the post, if there isn't one there now, as the .deb file was only tested on Edgy.

Boot into Recovery Mode (if you don't see this option hit Esc at the boot screen).
When you get to the prompt run: ```
aptitude remove usp
```or:```
aptitude purge usp
```Or you could try it at a normal terminal in which case you would need "sudo" before the commands.

This should get rid of USP allowing you to install subversion and USP from the SVN.

If those commands don't work try: ```
sudo dpkg -r usp
```

Here is the wiki for the SVN with instructions on installing and configuring USP from the SVN.
[http://code.google.com/p/ubuntu-system-panel/w/list](http://code.google.com/p/ubuntu-system-panel/w/list)

Hope this helps.

---

### Post by mthakur2006 on 2007-03-31
Thanks for the reply.
I tried that but it says that the package is in too bad or inconsistent state and that I should try reinstalling it before attempting removal.
Any suggestion?
Thanks in advance.

---

### Post by Malac on 2007-04-01
> **mthakur2006 said:**
> Thanks for the reply.
I tried that but it says that the package is in too bad or inconsistent state and that I should try reinstalling it before attempting removal.
Any suggestion?
Thanks in advance.
There is a force option for dpkg I think you would need this one "remove-reinstreq" but I'm unsure whether it should be "dpkg --force-remove-reinstreq" or "dpkg --remove-reinstreq" or "dpkg remove-reinstreq" the help is unclear.

You could try ```
sudo aptitude -f remove usp
``` which might be a bit less aggressive but may get the job done.

---

