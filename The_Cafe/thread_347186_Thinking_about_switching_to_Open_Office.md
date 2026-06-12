---
title: "Thinking about switching to Open Office"
date: 2007-01-26
forum: The Cafe
---

### Post by SonicSteve on 2007-01-26
I've been wanting to find a way to convert my MS publisher .pub files so I can work on them from either Ubuntu or Windows. From I can see this is a totally fruitless effort. 
This is really bugging me though. The format is so proprietary that your completely stuck. At least MS word has other options. Publisher is completely untu its own. AAGGGGHHH!!!

It's bugging me so much that the only answer I can see is to switch to Open Office. Truthfully the only thing that I may miss at all would be Outlook. Even then I'm not sure how much I will.

Before I do this has anyone found a way to convert these .pub files into a format that can be used by another program?

---

### Post by SonicSteve on 2007-01-26
I should add that even if I were to switch to Ubuntu on both computers which I could do. I would still like to find a way to deal with these dang .pub files.

---

### Post by gjtoth on 2007-01-26
> **SonicSteve said:**
> I've been wanting to find a way to convert my MS publisher .pub files so I can work on them from either Ubuntu or Windows. From I can see this is a totally fruitless effort. 
This is really bugging me though. The format is so proprietary that your completely stuck. At least MS word has other options. Publisher is completely untu its own. AAGGGGHHH!!!

It's bugging me so much that the only answer I can see is to switch to Open Office. Truthfully the only thing that I may miss at all would be Outlook. Even then I'm not sure how much I will.

Before I do this has anyone found a way to convert these .pub files into a format that can be used by another program?

Trust me... you won't miss Outlook.  Evolution or Kontact is every bit as good or better.

As far as the .pub thing... don't know.  Haven't had the occasion to try that.  But you can see the results of using proprietary stuff....  

Get free, dood!  Surely there's a way you can cut & paste through VMware or Parallels.

---

### Post by TheRingmaster on 2007-01-26
> **gjtoth said:**
> Trust me... you won't miss Outlook.  Evolution or Kontact is every bit as good or better.

As far as the .pub thing... don't know.  Haven't had the occasion to try that.  But you can see the results of using proprietary stuff....  

Get free, dood!  Surely there's a way you can cut & paste through VMware or Parallels.

You could try this file conversion web site. [Zamzar - Free online file conversion]("http://www.zamzar.com/")

---

### Post by slimdog360 on 2007-01-26
You can download the MS office viewers through crossover office for free which will let you view and print your .pub files. You cant edit them but its still cool. Unless of course you decide to install MS office through Crossover.

---

### Post by Bloodfen Razormaw on 2007-01-26
OO.o won't solve a thing for your Publisher issues.  It has no DTP application.  The only worthy free software desktop publishing option is Scribus.  I'm not sure if there is way to convert to and from .pub files, but Scribus is a hell of a lot better at publishing than Publisher.  Then again, there is very little out there that isn't.  Publisher is a joke.

---

### Post by Dr. C on 2007-01-26
If one still has Microsoft Publisher, I suggest open the file in Publisher, save it as a Microsoft Word document (.doc) then open the file in Open Office and save it in .odt format. In that way one can rescue the content from the propriety .pub format. A similar approach has to be taken with Microsoft Works files.

---

### Post by SonicSteve on 2007-01-27
> **FineE said:**
> If one still has Microsoft Publisher, I suggest open the file in Publisher, save it as a Microsoft Word document (.doc) then open the file in Open Office and save it in .odt format. In that way one can rescue the content from the propriety .pub format. A similar approach has to be taken with Microsoft Works files.

I'll give that a try. 
On a separate note why does everyone think that Publisher is a joke? Honestly I would like to hear your thoughts.

---

### Post by SonicSteve on 2007-01-27
It kind of worked, yes the shapes are gone but at least I saved tables and text. Now I have to decide if I can do with writer what I did with publisher or if I need to use scribus.

---

### Post by ssam on 2007-01-27
> **SonicSteve said:**
> I'll give that a try. 
On a separate note why does everyone think that Publisher is a joke? Honestly I would like to hear your thoughts.

i think because it is far too basic for real publishing.

if you are doing professional printing you get lots of complex issues with fonts (do the print shop have what you used, does the font have real italics, or does your software just rotate the letters), embedded media (you might have a document that links to external images), colour separation (often printing is done with a few specific ink colours rather than mixing CMYK).

---

### Post by Bloodfen Razormaw on 2007-01-27
> On a separate note why does everyone think that Publisher is a joke? Honestly I would like to hear your thoughts.
It doesn't have anything close to the features needed in professional printing.  It barely has any PDF support (an absolute requirement; Scribus, in contrast, has full support for PDF/X3, and was the first DTP to do so by a year).  Even in Office 2007 it takes an add-on for PDF output; that's acceptable for the likes of Microsoft Word, but for a DTP it is an integral feature.  Having PDF as an add-on for a DTP app would be like making math functions an add-on for a spreadsheet app.  It has awful color management, limited support for font features, and very basic layering.  Simply put, anything you can do with Publisher you could do just as well in a word processor.

---

### Post by SonicSteve on 2007-01-27
OK I'm starting to get the picture. One other thought, if lets say you used Adobe Acrobat or Adobe ... would you not have the same proprietary file issues? Or can Abobe save as something that scribus could open and could scribus save as something that abobe could open? 
I'm not sure it matters since I won't be using Adobe since it just costs too much. I will likely use scribus which completely solves the problem of cross platform. Works in windows and Ubuntu.

The best I've been able to do with my .pub files is save them to .doc which really doesn't save much time since I can just as easilly cut and past between apps as I can within the same app. Since I would only save the text and tables I pretty much have to start from scratch anyway.

---

### Post by Bloodfen Razormaw on 2007-01-27
Yes, the same issues apply.  That is a problem with all closed and undocumented formats.  Adobe and Quark want you tied to their applications to prevent users from migrating to competitors.  Scribus has an open and well-documented XML format, thankfully.  It is possible for anyone to implement it, and it is built on the Qt platform so it works on anything that Qt will work on (which is just about everything).

You may also try saving them as EMF and opening them in another editor, but you will probably lose a lot of information from the file that way.

---

### Post by mips on 2007-01-27
Could OpenXML not maybe solve the problem ?

I'm just taking a stab at things here.

---

### Post by SonicSteve on 2007-01-27
> **mips said:**
> Could OpenXML not maybe solve the problem ?

I'm just taking a stab at things here.

I'm all ears, I know what you're talking about, I just don't know how to implement it. Can office 2k3 use openXML?

---

### Post by Bloodfen Razormaw on 2007-01-27
Even if it did, it would take a long time for other applications to support OpenXML.  But it doesn't matter since it doesn't fix it anyway.  Only Word, Excel, Powerpoint, Infopath, and Visio have open formats.  No OpenXML format was made for Publisher.

---

### Post by SonicSteve on 2007-01-27
That's too bad, I didn't notice any "open" type file formats in the save options of publisher. It seems that I may just have to re-do them in writer. It writer can't do it then I'll use scribus. I'd rather use Writer if possible though, it allows me to save in a way that others can view and edit also.

---

### Post by SonicSteve on 2007-05-23
I should have mentioned this quite a while ago, 
I made the switch to Open Office about 2 months ago. I haven't missed MS office yet, perhaps at some point something will come along that I need to open and I won't be able to but so far I'm very happy using Open Office. I also feel better that in some small way I'm sending a message to Microsoft that I'm not happy with their business practices.

---

### Post by Lucifiel on 2007-05-23
Microsoft Outlook is awful, serious! The last time I used it was way back in 1995 and it had so many problems then and even now, I've never used it again.

Give either Thunderbird or Sylpheed Claws(Claws-mail) a try. :D  
If you want to try Claws-mail for 7.04, look at here for instructions.

[http://ubuntuforums.org/showpost.php?p=2613967&postcount=37](http://ubuntuforums.org/showpost.php?p=2613967&postcount=37)

---

### Post by forrestcupp on 2007-05-23
If you still need help with pub's maybe here is an option to at least be able to print them.  If you still have access to Windows with Publisher, you can download a freeware program called print2pdf.  It will allow you to convert any possible printable document, image, etc. into a pdf file.  With this installed, all you do is print your pub file like normal, only choose print2pdf as your printer instead of your actual printer.  It will convert your pub file to a pdf that looks exactly like what you created; you won't lose your shapes, etc.  I doubt if you can edit the file, but at least you could view and print from Linux or other pdf capable programs.  This is what I did when my wife created a pdf that I had to print on a computer without Publisher.

Also, I don't think Publisher sucks.  It's a great, easy way to quickly throw together some nice looking stuff.  The only bad thing about it is the extremely closed file-format.  At least with Word you can use doc files in other programs.

---

### Post by SonicSteve on 2007-05-23
> **forrestcupp said:**
> If you still need help with pub's maybe here is an option to at least be able to print them.  If you still have access to Windows with Publisher, you can download a freeware program called print2pdf.  It will allow you to convert any possible printable document, image, etc. into a pdf file.  With this installed, all you do is print your pub file like normal, only choose print2pdf as your printer instead of your actual printer.  It will convert your pub file to a pdf that looks exactly like what you created; you won't lose your shapes, etc.  I doubt if you can edit the file, but at least you could view and print from Linux or other pdf capable programs.  This is what I did when my wife created a pdf that I had to print on a computer without Publisher.

Also, I don't think Publisher sucks.  It's a great, easy way to quickly throw together some nice looking stuff.  The only bad thing about it is the extremely closed file-format.  At least with Word you can use doc files in other programs.

This is exactly what I did. Though I used a program called cutewriter. It did what I needed it to do and was free. I could still access windows XP, it's setup as a dual boot still I just haven't found any program under the sun that can convert the pub files into anything else. It came down to cutewriter (pdf), cut and paste into new docs, or recreate from scratch. 
I actually did a combination of those 3 in the end.

---

### Post by KIAaze on 2007-05-23
Oh, .pub files, my first encounter with a document I could not open...
IT'S IMPOSSIBLE TO OPEN IF YOU DON'T HAVE PUBLISHER!!! ](*,)

Of course there's some kind of online service that offers you to convert them into PDF for you.
But I didn't want to trust some website.

So I searched and searched and searched.
In the end I downloaded the MS publisher demo on my XP partition (M$ has NOT made a .pub viewer :( ), which was about 400-500MB or so, waited about 30min to install it and opened the damn .pub file.
Now downloading the demo was not as easy as it seems.
**No, you can't just download the damn time-limited demo!!!**
**_You have to create a Windows Live! account_** ](*,), give your e-mail address, fill out a survey!!!
And then you get a "personal serial number" by mail.
Now for some strange reason, that "personal serial number" is _not required_ to install the demo!
(but you can enter it optionally if you want...)

Now, in the end, after all this stupid M$ nonsense, I could FINALLY easily convert it to PDF thanks to [PDFCreator]("http://sourceforge.net/projects/pdfcreator/").

---

### Post by koshatnik on 2007-05-23
> **Bloodfen Razormaw said:**
>  Simply put, anything you can do with Publisher you could do just as well in a word processor.

Unless its MS Word. Which has trouble formatting a list properly.

---

### Post by SonicSteve on 2007-05-23
> **koshatnik said:**
> Unless its MS Word. Which has trouble formatting a list properly.

OH SOOOO true, it drives me crazy!!! the only way I've found to keep it formatted is to use invisible text boxes, or frames in open office. Word just takes on a mind of its own. Perhaps if you really knew it inside out you could get it to do what you wanted but, I just give up and use the boxes.

---

### Post by forrestcupp on 2007-05-24
> **Bloodfen Razormaw said:**
> It doesn't have anything close to the features needed in professional printing.  It barely has any PDF support (an absolute requirement; Scribus, in contrast, has full support for PDF/X3, and was the first DTP to do so by a year).  Even in Office 2007 it takes an add-on for PDF output; that's acceptable for the likes of Microsoft Word, but for a DTP it is an integral feature.  Having PDF as an add-on for a DTP app would be like making math functions an add-on for a spreadsheet app.  It has awful color management, limited support for font features, and very basic layering.  Simply put, anything you can do with Publisher you could do just as well in a word processor.

Well I'll have to say that even if you can do all Publisher stuff in a word processor, it's no where near as easy to do it.  That's the purpose of Publisher, to automate all of the layout so you don't have to do it manually.

However, I have never seen Scribus before.  I didn't know there is an open source desktop publishing program.  Thank you for the reference; it looks really good.

---

