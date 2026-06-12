---
title: "How to make Online PDF creator for MS Office files?"
date: 2007-05-10
forum: Server Platforms
---

### Post by iggyboy on 2007-05-10
Hi...

First foremost, i'm sorry if this is posted in the wrong forum group. I am just not sure whether to post at General Help or in Severs & Security.

I'm running Ubuntu 6.06LTS with LAMP and my ubuntu box is basically serving as apache running Joomla and Music Index, also running samba for sharing folders for windows PC.

I would like to add a feature to convert MS Office Suite application (word etc...) and others windows application like AutoCAD etc... to pdf format using apache. something like these website provides:

[http://convert.neevia.com/](http://convert.neevia.com/)
[https://www.pdfonline.com/convert_pdf.asp](https://www.pdfonline.com/convert_pdf.asp)

Is this is possible in Ubuntu box. I did read thier manuals but don't really understand. Can someone help me please.

Thank you in advance.

---

### Post by rich.bradshaw on 2007-05-10
Yeah, but you'd need to find a commandline tool to convert the files. Not sure on the details, but I think you'd have to reverse proxy to a program that would send back the converted file...

I'll keep on eye on this, sounds very useful!

---

### Post by JC_510 on 2007-05-10
Forgive me if Im mistaken, but doesnt OpenOffice Writer come with a tool to save in PDF format? I know it does in my version (latest) because I've used it!

EDIT: Doh! Saw the part about Apache - sorry!

---

### Post by iggyboy on 2007-05-11
ThankX for sharing your opinion :)


**rich.bradshaw**
> Yeah, but you'd need to find a commandline tool to convert the files. Not sure on the details, but I think you'd have to reverse proxy to a program that would send back the converted file...

emm... if I'm not wrong your suggestion is to send (say a ms word file) the file to the previously said website and to use some kind of way to capture it back automatically right? If that what you suggest, unfortunately that's not what I want. I would like the conversion process to take place locally in my ubuntu box. I will explain in detail my situation and what exactly I wish to do with my ubuntu box.

**JC_510:** yes open office do come with PDF writer, but that's not what I want. see below please:


okey... here's my actual situation: I have public access intenet-center (not really a public access but within a campus). 19 windows computer running XP (client PC), one ubuntu desktop 6.06 LTS with LAMP and one windows XP computer (Admin PC) that control the logging in and logging out the user PCs.

If somebody want to do a printing job, they are required to do so from the client PC (any of the 19pc running XP). The process of printing is like this:
 
A user will plug-in USB drive to client PC and print using a preferred windows application to a virtual PDF printer (soft copy). Then the user will alert a Staff to print. At the Admin PC the staff will print to actual printer (hard copy) using the PDF file generated from the client PC. (this method is enforce to reduce the paper waste, where generally typical user mostly likely to press "printer button" many times just to make a single copy of printing).

Now here's my problem. Since there is only 19 PCs for about 500 students to share. Sometimes the waiting list, just to do printing job for assignment is very long. This is because the 19 PC is occupied (by chatters for example.). Printing from Admin PC is not really sensible, because it simply not practical at all and doesn't work efficiently for many reason (I have tried).

This is what I want to do, I want to make my Ubuntu Box for printing (beside running some simple cms and file sharing at the background). I do not want to give them access to open open office or anything else.

When I saw this website [http://convert.neevia.com/](http://convert.neevia.com/) [https://www.pdfonline.com/convert_pdf.asp](https://www.pdfonline.com/convert_pdf.asp) I got an idea, may be if I can make something like that in my Ubuntu box then that will solve a lot of problems. Whereby the user have no other options but just simply print their work (they have to make sure their job is well done at their PC).

I tried to explain my situation as much as possible hopefully you can understand and visualise the scenario here :).

May be there are other options, but at the moment I can only think of this. :-S.

ps: sorry for the long post.

---

