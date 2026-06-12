---
title: "where to find contacts and msg on phone"
date: 2016-09-12
forum: Ubuntu Phone and Tablet
---

### Post by mojo risin on 2016-09-12
Hi, my dear phone has a defunct(but not cracked) touchscreen. Works fine and dandy with a mouse, but before I had the mouse i used my sim with a different phone and found that my contacts/messages were not saved on sim.Where would I be able to find this data on my phone so I could make a backup of these files?

---

### Post by howefield on 2016-09-12
You are talking about an Ubuntu phone, yes ?

The SMS should be in..
```
.local/share/history-service/history.sqlite
```

and the contacts database in.. (along with mail, calendar and possibly some other stuff)
```
~/.local/share/evolution/
```

Probably a good idea to backup the whole of the /home folder.

---

### Post by mojo risin on 2016-09-12
Thanl you, I have got most of my media files backed up, but didnt know that my contacs etc were in a diff folder. thanks :) I'll have a look to back up that folder

---

### Post by howefield on 2016-09-12
You're welcome, if the thread is solved feel free to mark as such :)

---

### Post by mojo risin on 2016-09-14
I have got one more question sorry if this is obvious.
How do I get the phablet back on a phone of the same type. I tried to use wifitransfer but nothing happened after I tried copy pasting , and when on the usb line it didnt show the folders needed.
In the ended i got an sql viewer and exported it unto my google acc(and that will have the contacts of uncontacted people from 15 years ago noe xD) and i saved the messages unto my laptop.

---

### Post by howefield on 2016-09-14
Sorry, I'm not sure what you are trying to do, what exactly do you mean by "get the phablet back on a phone...."

---

### Post by mojo risin on 2016-09-15
Sorry if  i wasnt clear. I wanted to try to replace the phablet folder on the new phone( same model) with the folder from my old phone so that I have all messages and similar files on this one. I have got them backed up on my pc so i can look them up if I wanted but I was looking for a way to import them to this phone. the contacts were imported via csv file from/ to gmail but I was looking for a way to get the backed up file replacing the existing file on the phone.

---

### Post by howefield on 2016-09-15
How about using the File Manager to copy to a micro SD card ?

---

### Post by mojo risin on 2016-09-15
Ok after pulling the specific file and rebooting the phone it worked and same with messages. ( tried c+p all of phablet before) also deleted the gmail acc again as that one didnt work. 


 is on the sd card and in the wifi transfer folder but it does not seem possible to transfer it from these places to the home folder. I tried to import the contacts from the file directly which failed for some reason. the csv file( exported using db browser on the computer)didnt work great all it imported was email addresses but not the numbers.(in gmail contacts it does at least also shows numbers even if the owner of the number is just jumbled up symbols)) unless heres a solution i may just transfer(aka create ) the contacts by hand by copying them from the db browser on the computer...

Also on older phones there was always a possibilty of saving contacts on sim any way to export them to sim?

---

