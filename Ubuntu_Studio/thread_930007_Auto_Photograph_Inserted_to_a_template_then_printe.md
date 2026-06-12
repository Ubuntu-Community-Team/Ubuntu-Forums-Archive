---
title: "Auto Photograph Inserted to a template then printed"
date: 2008-09-25
forum: Ubuntu Studio
---

### Post by Vince4Amy on 2008-09-25
We're running an Open Evening at my school for students who will be possibly moving there next year. 

We created a poster which contains "Wanted by *** School ICT Department" Which contains them words and then an photograph that we take of the student, it's just a bit of fun and something they can take home as a souvenir if you will. 

Last year we would take a photograph, copy it from the camera via USB to the local computer, then insert it into a premade Word Template we made earlier, every time we'd take a photo we'd manually drag it into the template that we made and the printed. Yes this worked, but it was time consuming and the time that each groups to see a department is as short as 10 minutes. 

This year I want to try something new. I'd like to be able to take the photo on the camera, but from there the image will Automatically be inserted into the premade odt template and then it will automatically be printed after this. Just a time saver.

So basically:

Photo Taken>Automatically Inserted in Template>Auto Printed

---

### Post by prshah on 2008-09-25
> **Vince4Amy said:**
> [LIST]
[*]Take a Photo on Digital Camera
[*]Insert the Image into a "Wanted" Word Template we made
[*]Print the image
[/LIST]

This year I want to simplify this process, is there any way I can come up with a system on Ubuntu where we'd simply take the photo, it will then automatically insert it into the template and then send a print signal. 

Here's something you can try. Replace the word document with an openoffice document. Instead of putting the picture into the file, link it to an external file name. (Insert-Picture-From file-Link-OK). Save the file, and close openoffice-writer.

Now, save whatever picture you take with the openoffice-writer-"linked" filename, then give the command```
oowriter -p wantedposter.odt
``` Replace filenames and paths as suitable.

How do you get the picture off the camera? That's something I can't figure out!

---

### Post by Vince4Amy on 2008-09-25
Yeah I would obviously use OpenOffice for this. However the camera will be connected via USB which will be sent right to the correct location.

---

### Post by Vince4Amy on 2008-09-26
Updated the original post to make it clearer.

---

