---
title: "Workspaces - Precise Maximum Number Limted to Two Workspaces"
date: 2012-03-31
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by djringjr on 2012-03-31
Hello All,

Two days ago March 29, 2012 suddenly my workspace number changed from 4 to 2.  I am using the default Unity desktop in Ubuntu Precise which is fully updated as of today March 31, 2012.  I have followed all the threads on using various settings to change the workspaces and although I can change the number which shows 4 down to 2 and then back up to 4 after a reboot, the number always remains at 2.

I have searched launchpad for a bug of this but cannot find it.

I like having four workspaces!

I have rebooted into Unity, still 2 workspaces, booted into gnome, still two workspaces.

Anyone figure this one out?

David

---

### Post by oldos2er on 2012-03-31
Moved to Ubuntu +1 (Precise Pangolin).

---

### Post by mc4man on 2012-03-31
Why don't you confirm whether you are in an _ubuntu_ session (unity 3d) or a _ubuntu-2d_ session (unity-2d
Log in & from terminal, result will show in obvious manner
```
echo $DESKTOP_SESSION
```
unity 3d sets number of desktops in /apps/compiz-1/general/screen0/options/ & uses 2 settings, one for horizontal, one for vertical
The default is 2 & 2 - see screen1 except I use 4 & 1

unity-2d & gnome classic use metacity - /apps/metacity/general/num_workspaces & there only is 1 setting, the default would be 4 - screen 2

---

### Post by djringjr on 2012-04-02
I'm using Ubuntu 2D.  I checked Gnome and I only have two desktops - which I upgraded about four days ago things changed :-)

I edited with nano 

~/.gconf/apps/metacity/general/%gconf.xml

<entry name="num_workspaces" mtime="1332334736" type="int" value="2"/>

And changed it to be:

<entry name="num_workspaces" mtime="1332334736" type="int" value="4"/>

Save file and now have four virtual desktops again.  Sometimes Ubuntu calls workspaces virtual desktops.

gconf-editor wasn't installed by default.  When installing it, I also added gconf-defaults-service.

Now I used gconf-editor to go to apps / metacity / general and changed the workspaces number 4 back to 2 - it worked immediately.  Then I changed back to 4 - also worked.

See this page also:  [http://askubuntu.com/questions/21755/how-to-add-multiple-workspaces-in-unity-2d](http://askubuntu.com/questions/21755/how-to-add-multiple-workspaces-in-unity-2d)

Thank you very much.

David

---

