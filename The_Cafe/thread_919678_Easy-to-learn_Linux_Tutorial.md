---
title: "Easy-to-learn Linux Tutorial"
date: 2008-09-14
forum: The Cafe
---

### Post by Kinetic_lord on 2008-09-14
I made a tutorial for Linux newbies. Easy learn the basics so that Ubuntu won't be as complicated as it was. Learn how to connect to the internet, install video card, configuring Compiz, software alternatives...

The guys from the community can read it also to tell me if it's good for something... there will be other versions if something is wrong or missing.

If someone modifies it and publish it as it's own... Well... at least it's still good for something.

---

### Post by aysiu on 2008-09-14
I have a couple of nitpicks: > Question: Why to swich to Ubuntu?

Answer:
It is the best OS you can get, it's good and free (Windows is stupid and non-free). What would be the advantages? A very very fast OS, virus-free (you don't need any anti virus to slow down you're computer because there are no viruses for Linux), no errors (well... if you install some Microsoft software there might be), with a lot of good open-source applications. 
 I have to disagree here.

Windows isn't "stupid." It's just different. I happen to like Ubuntu better, but that doesn't mean Windows is *stupid*. It's a matter of preference. You also don't have to use antivirus in Windows either if you set up a proper permissions system with SuRun. Every malware infection I've seen has been on a Windows computer that has antivirus installed. Antivirus is more or less useless, except on a mail server.

And there are plenty of errors in Ubuntu. Check out Launchpad sometime. Segmentation faults. Flash causing Firefox to crash. Drives not ejecting cleanly.

Ubuntu is a great OS but making it sound as if it's the cure-all for computing problems and is a problem-free version of Windows will lead only to more "Ubuntu sucks" threads in the Ubuntu Testimonials and Experiences subforum.

> To do this with administrator rights (root) type in terminal:
sudo nautilus

It will open nautilus with administrator privileges. The proper command is ```
gksudo nautilus
``` *gksudo* is for graphical applications. *sudo* is for terminal applications.

---

### Post by jeyaganesh on 2008-09-14
Nice comment Aysiu!

---

### Post by nowin4me on 2008-09-14
> **Kinetic_lord said:**
> The guys from the community can read it also to tell me if it's good for something... there will be other versions if something is wrong or missing.

If someone modifies it and publish it as it's own... Well... at least it's still good for something.

I am guessing we can edit this and re-publish this?
If so I might put up my version here... I have seen a few spelling mistakes and personal opinions.

:lolflag:

Looks great thought I will give you all the credit.
And put Edit at the bottom with my name under yours.

---

### Post by northern lights on 2008-09-14
While I believe your effort to be applaudable, I cannot help but disagree with a few of your statements.

> It is the best OS you can get, it's good and free (Windows is stupid and non-free).Undoubtedly, it's easy to make a strong case for other OSs than Windows. "Stupid", however, can hardly be the most suiting attribute of Windows. I'd say that other than a human being and maybe few other mammals nothing can either be inherently smart or stupid. Windows developers certainly aren't and neither is Steve Balmer, Bill Gates or any other individual on the board in Redmond.
Windows ranks rather low on my personal list of OSs of choice, but that's personal preference.
Further, while I love my Ubuntu, I'd say calling it the best OS ever is a bit over the top. The choice of an OS first of all depends on the kind of usage. Has Ubuntu Server for instance reached the quality of RedHat Enterprise? Probably not.

>  A very very fast OSYour system is always only as fast as the hardware. On a P3 with 256 megs of RAM for instance, there'd be a load of faster distributions.

> no errorsThis claim is ridiculous. If this was true there wouldn't be 258446 bugs reported across 2297 projects on Launchpad as of today.

Further, everything along the lines of > GIMP instead of Photoshop (much easier to learn)
OpenOffice instead of Word (much much better...)is also personal opinion. The GUI of MS Office 2007 for instance is IMHO unbeaten for ease of use - very user friendly and the one and only Microsoft product since Windows 98SE that I really like.

> This was an example, now, you need to do this with a lot of other useful programs, like EnvyNG. Envy will detect you're video card and install it. [Instructions on how to install Envy]A lot of GPUs run perfectly fine without Envy (and do so oob).

---

### Post by Kinetic_lord on 2008-09-16
OK... Many personal opinions... i know... I just really mad that i was restarting my computer 20 times a day because of errors and i fell so happy about having Ubuntu now. (well yeah it has errors too but at least you don't have tot restart the PC and they are rare). It isn't quite something official... Anyway, i know I've done some mistakes in writing that's why i asked for you're opinion. I hope Ubuntu won't be a mistery anymore for some of us who aren't so happy about *their current OS*. That's all, as i said, take it, edit it, but don't get my name out of there, it is my work too. ;)

---

### Post by Kinetic_lord on 2008-09-16
> **aysiu said:**
> And there are plenty of errors in Ubuntu. Check out Launchpad sometime. Segmentation faults. Flash causing Firefox to crash. Drives not ejecting cleanly.

Ubuntu is a great OS but making it sound as if it's the cure-all for computing problems and is a problem-free version of Windows will lead only to more "Ubuntu sucks" threads in the Ubuntu Testimonials and Experiences subforum.


Ok... bugs... lots of them... i know... well... should i write about bad parts in my tutorial too?(Of course not) :) i will delete the personal opinion and republish it. That's all. Any other stuff that i should add?

---

### Post by anotherdisciple on 2008-09-16
> **Kinetic_lord said:**
> Ok... bugs... lots of them... i know... well... should i write about bad parts in my tutorial too?(Of course not) :) i will delete the personal opinion and republish it. That's all. Any other stuff that i should add?

Well, yeah... you should be realistic. I haven't read what you have written yet, but I would definitely throw in that users have the ability to see how well it works with their computer's hardware (Live CD). Tell them to try a dual boot or Wubi and see if they want to use it as their main OS.

Let them know that it's easy to form their own opinions about linux before they completely reformat based on what someone else has to say. Know what I mean?

---

### Post by northern lights on 2008-09-16
> **Kinetic_lord said:**
> [QUOTE=aysiu;5787802]Ubuntu is a great OS but making it sound as if it's the cure-all for computing problems and is a problem-free version of Windows will lead only to more "Ubuntu sucks" threads in the Ubuntu Testimonials and Experiences subforum.Ok... bugs... lots of them... i know... well... should i write about bad parts in my tutorial too?(Of course not) :) i will delete the personal opinion and republish it. That's all. Any other stuff that i should add?[/QUOTE]

1. I'd say personal opinion is not even always a no-no. However it should, whenever given, also be declared as such.

2. Watch out for generalizations based on your personal experience and/or hardware setup.
For instance, you've mentioned Envy. Given the fact that most GPU products work without the use of Envy, it might be rather misleading to the new user/convert to make it sound like Envy is a requirement.

3. You might actually wanna check [aysiu's website]("http://psychocats.net/ubuntu/index.php") for some great examples on wording and structure of tutorials.

Ride on. Good effort.

---

### Post by aysiu on 2008-09-16
You don't have to have lengthy paragraphs outlining all the errors that people could encounter with Ubuntu, but you should acknowledge that errors exist, or at least not put forth the falsehood that there are **no errors** in Ubuntu.

---

### Post by brunovecchi on 2008-09-16
I really appreciate you taking the time to write this tutorial.

One piece of advice! It would be great if you published it with a non-propietary format. Pdf or odt would be better choices than .doc.

---

### Post by henryjm206 on 2008-09-16
Thanks for the tutorial 
henry

---

### Post by Kinetic_lord on 2008-09-19
Made it a .doc because i think most people that want to read a linux tutorial might still be on Windows and M$ Office doesn't recognise .odt's

---

### Post by Kinetic_lord on 2008-09-19
Press the blue ribbon on the lower-right corner of the screen... :)

---

### Post by directcharitycontribution on 2008-11-09
like seperate partition for /home  !

---

