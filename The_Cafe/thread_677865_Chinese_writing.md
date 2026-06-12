---
title: "Chinese writing"
date: 2008-01-25
forum: The Cafe
---

### Post by rysh on 2008-01-25
Hi people

Does anybody know about how the support for Chinese writing will be in the next Ubuntu/Kubuntu/Xubuntu release? ... Now i still have to do many manual configuration to make things work ... Wish i could let my Chinese friends see there is a simple and good working alternative.

thanx

---

### Post by tbroderick on 2008-01-25
Not sure, but there is a Chinese Linux distribution based on Ubuntu called Hiweed Linux.

[http://www.hiweed.com/](http://www.hiweed.com/)

There's also Red Flag Linux.

[http://www.redflag-linux.com/eindex.html](http://www.redflag-linux.com/eindex.html)

---

### Post by rysh on 2008-01-25
thank you for your reply, but it was not really what i was asking. :-) Just wish "Ubuntu" could have easier support for Chinese writing ... not some other distribution.

R

---

### Post by macogw on 2008-01-25
I've attached a script that is pretty much just copy and pasted commands from a howto I found online.  It installs IMEs for Chinese (traditional and simplified, I believe), Japanese, and Korean (usually called CJK).  If you just save it and make it executable (chmod +x script.sh) then run it as root (sudo ./script.sh) it'll install it all and set the SCIM stuff to run on every boot so you can always get to it without doing something extra.

---

### Post by rysh on 2008-01-27
Thanks a lot, i tried out this script but seems still something not working good. Also in this script btw. The part it makes the file ~/gnome2/session-manual: the touch line is made with sudo, and then the user tries to write to it with echo "something" >> ~/gnome2/session-manual ... which gives "Permission denied" ... because the file is owned by root. But when making the file manually it every times gets deleted when logging out. and as you might guess: again Chinese writing is not possible in Qt apps. 
I had this problem many times before and still not found a good solution. Just wish (because Ubuntu is also about being user friendly) that the new Ubuntu would deal with this .. Hoped some people here would have heard about this ... Thanks anyway, :-)

---

### Post by inversekinetix on 2008-01-28
install scim
install scim - bridge
install the language you want to input it
select the available langauges in scim's menu.


thats what I did for anthy japanese

---

### Post by rysh on 2008-01-28
Thank you, your message gave me some hints where to look now. Installing scim-bridge did let me install two more packages related to this. An apt-search did show me i also could install scim-bridge-client-qt too ... but to bad this did not let me have Chinese writing support in Konsole (which is a QT app) yet... But then i installed scim-qtimm and now i can write Chinese in QT as well as in GTK applications ... I will add this to that script ... but still it is not very user friendly ... and i do not see my Chinese windows-using friends be enthusiastic about this.

Thanks!!! ... 

Hope Ubuntu Hardy will make some automatic option in the menu's for this !!!

---

