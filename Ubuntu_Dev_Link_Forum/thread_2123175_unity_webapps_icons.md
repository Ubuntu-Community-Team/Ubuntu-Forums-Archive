---
title: "unity webapps icons"
date: 2013-03-07
forum: Ubuntu Dev Link Forum
---

### Post by oly on 2013-03-07
I am a bit puzzled by icon loading, i have set my icons into the same path as the other webapps ie amazon and set the name of the image file in the javascript, everything works except the image does not get loaded is there a way i can debug why the icon is not being found ?

I have tested this on 12.10 and 13.04 and get the same results and cut everything down to a minimum, i have created a few integrations but this seems to happen for some and not others and i am keen to find out why / the cause do webapps log any where, i knwo the javascript console says everything is fine.

---

### Post by oly on 2013-03-07
I tried using an icon from a working webapp and still do not get the image which makes me think there is some kind of icon caching going on in unity thats even surviving a reboot, any one aware of any caching in webapps ?

---

### Post by oly on 2013-03-08
Bingo, it does cache these i removed the cache files not advisable :)

you shoudl only need to run this,

> sudo update-icon-caches /usr/share/icons/unity-webapps-applications

Failing that check this you must have index.theme in /usr/share/icons/unity-webapps-applications, i had removed it so copied it from another machine.
you can generate an icon cache using the below, then run update-icon-caches

> sudo gtk-update-icon-cache -t /usr/share/icons/unity-webapps-applications/
sudo update-icon-caches /usr/share/icons/unity-webapps-applications

---

