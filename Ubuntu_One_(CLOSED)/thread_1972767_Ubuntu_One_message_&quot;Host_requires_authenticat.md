---
title: "Ubuntu One message &quot;Host requires authentication&quot;"
date: 2012-05-03
forum: Ubuntu One (CLOSED)
---

### Post by ljrossi on 2012-05-03
UBUNTU 12.04  , fresh install.

I install UbuntuOne, normal, After making some mistake on passwords, I follow steps on recovering password.

I recover password correctly .

But when I keep geting this message 

"host requires authentication"

I already try

seahorse   .... erasing password... (there is none created anyways)

u1sdtool -q
sudo rm .....
u1sdtool --start


I also reinstall ubuntuone client... and try with a new ubuntuone acount.... and keep geting this 

"host requires authenticacion" message when trying loging with u1sdtool -c


Thanks in advance

---

### Post by ljrossi on 2012-05-07
> 1. Press Alt-F2, type "seahorse", press "Enter"

2. Right-click on any entries with "Ubuntu One" or "Desktopcouch" in the name
and select "Delete"

3. Press Alt-F2, type "gnome-terminal", press "Enter" and then run these
commands one at a time
:
u1sdtool -q

sudo rm -rf ~/.local/share/ubuntuone

u1sdtool -c

4. You should be prompted to enter your Ubuntu One login, be sure to use the
Ubuntu One account you want to use

I try that but it didnt work, I get stuck on step 2, there is no password entri too erase.... I anyways whent to all the other steps with no result.

---

