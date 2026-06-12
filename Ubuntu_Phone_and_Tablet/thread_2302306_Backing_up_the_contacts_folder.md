---
title: "Backing up the contacts folder"
date: 2015-11-09
forum: Ubuntu Phone and Tablet
---

### Post by chris-burmajster on 2015-11-09
Hello,

I'd like to back up the contacts folder. Can anybody tell me where it is?

Chris

---

### Post by howefield on 2015-11-09
For contacts..

```
~/.local/share/evolution/
```

within that folder, you'll find addressbook, calendar, mail, memos and tasks folders - addressbook contains the contacts.db file but it probably makes sense to have a copy of all the files, you only need to restore those that you wish to.

---

### Post by derewigekreis on 2015-11-10
Thanks for your answer, howefield. Now my noob question:How do I access this folder? when I plug in my phone to my pc, I can only see the folders for pictures, music etc.

Can you help me?

---

### Post by howefield on 2015-11-10
Well, you could do it with the phones File Manager and copy to a micro SD card if you have one inserted in the phone. This assumes that you install the file manager from the app store as it is not installed by default. Once the File Manager is loaded set it to show hidden files and the rest should be self explanatory.

If you need more than that, let me know.

---

### Post by chris-burmajster on 2015-11-10
Thank you, howefield, for the link. Unfortunately, I can't save it onto the SD card. Can you help me?

---

### Post by howefield on 2015-11-10
Can't save on to the SD card because you don't know how to or because you don't have an SD card ?

If the latter, you can use adb shell to log into your phone from the computer which I'll try and explain if that is what you need.

---

### Post by derewigekreis on 2015-11-11
Thank you, I managed to do it now. It works exactly that way but I had to unlock full access in the file manager's options first. Anyway, I feel safer now :-)

> **howefield said:**
> Well, you could do it with the phones File Manager and copy to a micro SD card if you have one inserted in the phone. This assumes that you install the file manager from the app store as it is not installed by default. Once the File Manager is loaded set it to show hidden files and the rest should be self explanatory.

If you need more than that, let me know.

---

### Post by howefield on 2015-11-11
> **derewigekreis said:**
> Thank you, I managed to do it now. It works exactly that way but I had to unlock full access in the file manager's options first. Anyway, I feel safer now :-)

Cool, glad you managed to figure it out :)

Just for information, another nice app that you might care for is Wifi Transfer - allows you to ftp files to and from the phone.

> Upload and download files to and from your phone over FTP
A simple FTP server for Ubuntu devices; start it and then connect to your device from your normal FTP application on your computer (the file manager, Filezilla, or any other) using the connection details provided.

Files are uploaded to the folder .local/share/wifitransfer.sil on the device; they can be accessed with the device's File Manager app (which you may need to install).


---

### Post by chris-burmajster on 2015-11-11
Can't save onto the SD card because I don't get the opportunity. If I select the SD card I get something asking me "do you want to format this card".

---

