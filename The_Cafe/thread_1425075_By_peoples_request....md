---
title: "By peoples request..."
date: 2010-03-08
forum: The Cafe
---

### Post by MichealH on 2010-03-08
Here it is (sort of)! People lately have been complaining about how Grub is ugly so I have fixed that! So without furtherer ado I present to you...
[SIZE=7]The Ubuntu- Styled Grub Customizer![/SIZE]

Well I haven't thought of a name yet so... never mind. It is still my first release so any bug reports can be filed here and also, Its only in English I am working towards other languages.

So download the script below to get it:

[SIZE=1](BTW, If this actually gets in Lucid I can say Ubuntu was MY Idea :lolflag:)

EDIT: This is on OMG! Ubuntu I never thought this script would get this popular!

[B]Changelog

v1.01
[/B]- Added Purple just do the one with "-P" on the end.
[/SIZE]

---

### Post by Kdar on 2010-03-08
> **MichealH said:**
> [SIZE="1"](BTW, If this actually gets in Lucid I can say Ubuntu was MY Idea :lolflag:)[/SIZE]

HEY! It was mine too. I was thinking about it in Shower :)

---

### Post by dragonboss on 2010-03-08
Any screenshots? I'm hesitant to use this without knowing how it looks first

---

### Post by ovroniil on 2010-03-08
A screen shot would be better!

---

### Post by Lightstar on 2010-03-08
yeah!  screenshot!

---

### Post by 416inversed on 2010-03-08
I saw this over at OMG! Ubuntu. I'm interested in trying it out, but I was wondering if there was a way to undo the changes the script makes to GRUB, just in case....

---

### Post by Queue29 on 2010-03-08
For all of you whining about a screen shot and are too lazy to just look at it yourself..

---

### Post by tylerisfat on 2010-03-08
> **Queue29 said:**
> For all of you whining about a screen shot and are too lazy to just look at it yourself..

see, the thing is, thats not a screen shot. thats a background image. people want to see what it looks like in real life, on a computer.

---

### Post by haydoni on 2010-03-08
Can I change the picture Ubuntu-Eng.png with something else?
For example, the new purple desktop, by naming it Ubuntu-Eng.png and putting it in /usr/shared/images/grub, will this work??
I'm a bit nervous of messing about with that kind of thing...

This is a very neat idea!!

---

### Post by dragos240 on 2010-03-08
I would use it, but I don't use ubuntu :p.

---

### Post by dragonboss on 2010-03-08
> **tylerisfat said:**
> see, the thing is, thats not a screen shot. thats a background image. people want to see what it looks like in real life, on a computer.

Thank you. I don't know what Queue29 means by people whining about screenshots, no offense to the original thread poster but you cant just install something someone says is nice.

---

### Post by nerdzero on 2010-03-08
Hi MichealH,

What is the reason for this line in your script?

```
sudo chmod 777 /boot/grub
```

---

### Post by haydoni on 2010-03-09
My thoughts: The contrast between the white text and the light brown/yellow image isn't high enough.

This could be easily solved with the new purple desktop... or perhaps adding an option in your script to select an image?
-- also you may be able to add the option to change the colour of the text?

Keep up the good work.

---

### Post by cdEWoozy on 2010-03-09
This script messes up the permissions /boot/grub, /usr/share/images and /etc/grub.d by making them world-writable.
It also makes the assumption that you don't already have a directory called "Grub" in the current directory. If you do and have files in it, it's gone after you ran the script.

I wouldn't recommend distributing this script in its current form.

---

### Post by MichealH on 2010-03-09
> **haydoni said:**
> Can I change the picture Ubuntu-Eng.png with something else?
For example, the new purple desktop, by naming it Ubuntu-Eng.png and putting it in /usr/shared/images/grub, will this work??
I'm a bit nervous of messing about with that kind of thing...

This is a very neat idea!!

Should work! Also I may release a purple Version.

> **tylerisfat said:**
> see, the thing is, thats not a screen shot. thats a background image. people want to see what it looks like in real life, on a computer.

Its a white foregroung and the selected item will be black.

> **416inversed said:**
> I saw this over at OMG! Ubuntu. I'm interested in trying it out, but I was wondering if there was a way to undo the changes the script makes to GRUB, just in case....

My script on OMG Ubuntu? I never had the honor!

> **Kdar said:**
> HEY! It was mine too. I was thinking about it in Shower :)

Oh well One word, UNLUCKY! :D

> **dragos240 said:**
> I would use it, but I don't use ubuntu :p.

Should work on any Grub 2 installs

> **nerdzero said:**
> Hi MichealH,

What is the reason for this line in your script?

```
sudo chmod 777 /boot/grub
```

> **cdEWoozy said:**
> This script messes up the permissions /boot/grub, /usr/share/images and /etc/grub.d by making them world-writable.
It also makes the assumption that you don't already have a directory called "Grub" in the current directory. If you do and have files in it, it's gone after you ran the script.

I wouldn't recommend distributing this script in its current form.
Grub is the file it downloaded from dropbox and Therefore the Cleaning up process! I can make the script securer if you want! I also used the chmod because then It could write but I may just use sudo :P I will patch this bug...

---

### Post by MichealH on 2010-03-09
Updated :D Added Purple just get the one with the -P on the end. I have tweaked the newest (the purple installer) so It will not mess up your permissions also If you have an existing Grub folder It will not affect and Write any changes.

For the Purple script see Post #1 or below:

---

### Post by haydoni on 2010-03-09
Good work. I'll think I'll make two further suggestions.

a. The purple logo is still a bit light (mainly due to the white text and white logo).

b. The logo and words are too big (and light) - my white text overlaps half of it, this is my fault for dual booting with windows (!).

I think it would make more sense to have the text/logo, a bit out of the way, on the lower right hand side but inside the white box.
Also you could use the new Ubuntu logo. :) Something like [this]("http://twitpic.com/17lr0r")?


*I'm also enjoying the new lucid terminal which shows though a purple version of my black and white desktop. Very pretty times indeed. :)*

---

### Post by Dexter_Greycells on 2010-03-27
I am not Linux expert, so pleas forgive me for my annoying query.
I am using 9.04 and I downloaded the purple script from Google Chrome. Strangely the file that was downloaded on my desktop was named install-grub-ubuntu-P.download and not install-grub-ubuntu-P.sh.

I changed its permissions to allow it to execute as a program. Double clicking it after that just opened the script in gedit. Renaming the file to install-grub-ubuntu-P.sh and double clicking it resulted in the same. It won't simply run.

Can anyone explain what is wrong here?

In the end I just copy+paste each command from the script in a terminal window to get things done. Not yet rebooted as yet. Let's if this works with 9.04 because you have forgot to mention supported versions :P


Update:
Either the script doesn't work on 9.04 (or the old grub) or I executed the script commands wrongly in the terminal...

---

### Post by MichealH on 2010-03-27
> **Dexter_Greycells said:**
> I am not Linux expert, so pleas forgive me for my annoying query.
I am using 9.04 and I downloaded the purple script from Google Chrome. Strangely the file that was downloaded on my desktop was named install-grub-ubuntu-P.download and not install-grub-ubuntu-P.sh.

I changed its permissions to allow it to execute as a program. Double clicking it after that just opened the script in gedit. Renaming the file to install-grub-ubuntu-P.sh and double clicking it resulted in the same. It won't simply run.

Can anyone explain what is wrong here?

In the end I just copy+paste each command from the script in a terminal window to get things done. Not yet rebooted as yet. Let's if this works with 9.04 because you have forgot to mention supported versions :P


Update:
Either the script doesn't work on 9.04 (or the old grub) or I executed the script commands wrongly in the terminal...

The .download is a temp download are you sure it downloaded correct.

---

### Post by MichealH on 2010-04-12
So Im bumping this... I want to release a new Version but Im out of some Ideas any more Ideas? I will be checking up on how to improve this soon.

An Idea I have is making this script lighter so you don't have to download all this new nonsense going in e.g. languages ect.

---

