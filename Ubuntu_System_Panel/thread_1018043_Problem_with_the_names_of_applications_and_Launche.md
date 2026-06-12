---
title: "Problem with the names of applications and Launcher icons created"
date: 2008-12-21
forum: Ubuntu System Panel
---

### Post by Pafrapé on 2008-12-21
Hello.

Thank you to apologize for my language, but I'm French and I am unfortunately not very good at the language of Shakespeare.

I find USP fantastic and I can not get through.

But I have two problems :
- the names of applications is not like the Gnome application menu. Thus, in the gnome, applications are in French, while in the name USP remains in English ;
- when I create a launcher, the icon attached to the launcher does not appear in USP.
	
Thank you tell me how to solve these problems, especially the second.

Thank you in advance for your reply.

---

### Post by Malac on 2009-01-04
> **Pafrapé said:**
> Hello.

Thank you to apologize for my language, but I'm French and I am unfortunately not very good at the language of Shakespeare.

I find USP fantastic and I can not get through.

But I have two problems :
- the names of applications is not like the Gnome application menu. Thus, in the gnome, applications are in French, while in the name USP remains in English ;
- when I create a launcher, the icon attached to the launcher does not appear in USP.
    
Thank you tell me how to solve these problems, especially the second.

Thank you in advance for your reply.
Your English is better than my French :)
Unfortunately we have not done any internationalisation of USP.
The only solution at present is to edit the easyfiles.py and replace the ```
            if datalist[i][0:5] == "Name=":
                PlaceName = datalist[i][5:]
```
with ```
            if datalist[i][0:**9**] == "Name**[fr]**=":
                PlaceName = datalist[i][**9**:]
```
This will at least give you the name in French but you may find that some apps don't have Name[fr] in the launchers.

USP follows the icon name in the launcher file if you don't have that icon in your theme it should default to standard theme icons. However there is a bug that I am going to be working on which involves spaces between the = and the icon name.

I will put both of these on a bug report at launchpad so I don't forget.

Hope this helps.

---

### Post by Pafrapé on 2009-01-21
Hello.

I applied what you told me and the names of applications appears in French.
As against a number of applications is not translated and appears far more on the menu, except the icon, even though the name of the application is in French in the gnome menu.
How to solve this problem?

Thank you very much.

---

### Post by Malac on 2009-01-22
> **Pafrapé said:**
> Hello.

I applied what you told me and the names of applications appears in French.
As against a number of applications is not translated and appears far more on the menu, except the icon, even though the name of the application is in French in the gnome menu.
How to solve this problem?

Thank you very much.
Please attach a copy of a .desktop file for an application that shows up in gnome but not in usp to a post and I will take a look at it, they are usually in /usr/share/applications.
Copy one from there to your desktop then change the .desktop to .txt and attach it.

Thanks.

---

### Post by Pafrapé on 2009-03-23
Hello,
I rely again on USP.
So I reinstalled ubuntu and usp.
But when I apply the changes you told me to do to translate the names of applications in french, nothing happens. The applications are always in English.


Thank you in advance for your answer.

---

### Post by Malac on 2009-03-26
> **Pafrapé said:**
> Hello,
I rely again on USP.
So I reinstalled ubuntu and usp.
But when I apply the changes you told me to do to translate the names of applications in french, nothing happens. The applications are always in English.


Thank you in advance for your answer.
Sorry for the late reply.
The procedure should be exactly the same as before.
I am puzzled as to why it isn't working this time. :confused:
Have you tried a reboot to see if this works?

---

### Post by Pafrapé on 2009-03-29
The names of recent applications is in French, which works very well, but the names of applications in the application window remains entirely in English.

---

### Post by Malac on 2009-03-30
> **Pafrapé said:**
> The names of recent applications is in French, which works very well, but the names of applications in the application window remains entirely in English.
Sorry I missed this one.
Replace the code Line 576-578 of applications.py  with the same as in easyfiles.py
```
                                if datalist[i][0:5] == "Name=":
                                                PlaceName = datalist[i][5:]
                                                BTip = datalist[i][5:]
```
becomes:
```
                                if datalist[i][0:**9**] == "Name**[fr]**=":
                                                PlaceName = datalist[i][**9**:]
                                                BTip = datalist[i][**9**:]
```
If this doesn't sort it let me know.

---

### Post by Pafrapé on 2009-04-10
I did as you said.
Unfortunately, many applications are not translated: the icon appears next to it but no name, nor in English nor enfrançqis, especially applications not gnome (kde for example).

---

### Post by Malac on 2009-04-10
> **Pafrapé said:**
> I did as you said.
Unfortunately, many applications are not translated: the icon appears next to it but no name, nor in English nor enfrançqis, especially applications not gnome (kde for example).
I'm sorry this is not working.
Could you zip/tar a couple of .desktop files which are having problems (these are usually in /usr/share/applications) then attach them to a post and I will take a look at them to see why they are not working.

Thanks very much for your patience.

---

### Post by Pafrapé on 2009-04-11
I looked in the file /usr/share/applications.
Applications that are not translated are in sub-directories kde and kde4.

---

### Post by Malac on 2009-04-12
> **Pafrapé said:**
> I looked in the file /usr/share/applications.
Applications that are not translated are in sub-directories kde and kde4.
 Okay thanks I will check on mine tomorrow(Mon).

---

### Post by Pafrapé on 2009-04-14
I also have a translation problem regarding tooltips: these are not translated.

---

### Post by Malac on 2009-04-29
> **Pafrapé said:**
> I also have a translation problem regarding tooltips: these are not translated.

I will look into this at the weekend too as part of a total 'internationalisation' re-code I'm doing this week.

---

### Post by Malac on 2009-05-01
Okay I have committed revised plugins and some language templates to the SVN Rev #386.
I have tested this with the French locale setting of fr_FR and it seems to be okay for the translations in applications, recent and favourites. However favourites will have to be re-done to take advantage of the translations.

I think I have tested everything but as ever if anything breaks for you then pm me and I'll try and sort it asap.

Pafrapé, if you could send me the French translation .po files I will compile them to .mo and upload both to the SVN.

Thanks.

---

