---
title: "Anti virus installation problems"
date: 2007-12-21
forum: Server Platforms
---

### Post by ubiubi on 2007-12-21
Hi all,

I installed clamAV but canèt find it in the application menu - any ideas?
I  then install AVG but when I tried to run it or eben update it it told me I was not authorised (I am the default administrator !)  very confusing. So, I also installed avast. This did a detailed scan but produced a list of a shed ful of files it was not authorised to inspect. Imagine I had/have a virus hiding there! Again, any suggestions in solving these issues. Assuming I can get them all to function correctly, which would anybody advise keeping?

Many thanks

---

### Post by bmathis on 2007-12-21
You can try installing clamtk which is a graphical front end to clamav. Run it by typing sudo clamtk in a terminal.

It seems as youre running AVG and Avast with your user account which only has access to your home folder, try running them with sudo to give it full access to your drives.

---

### Post by ubiubi on 2007-12-21
I tried running from the terminal with no success. At least avast functions but I'm still restricted to what I can scan. There must be a simple way to overcome this. I'm totally confused as to why avg refuses even to update itself with the excuse of lacking authority.

Maybe I should be in a particular directory when I try to run in the terminal but I've no idea where I should be!

---

### Post by HermanAB on 2007-12-21
Hmm, well, I suggest that you delete it all and find something else to do, since there aren't any viruses for Linux, so installing it all is kinda pointless.

ClamAV and Spam Assassin are useful if you are are hosting mail for other people.

Cheers,

Herman

---

