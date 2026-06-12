---
title: "Problem with Sibelius-made pdf files"
date: 2012-10-13
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by DavidSommen on 2012-10-13
Hello all,

I am a musician and when on my Mac, I use Sibelius to make scores. I export them to pdf to e-mail them to my bandmembers and so on.

Since updating to Quantal Quetzal two days ago on my main computer, I came up with a curious problem. The pdfs are rendered horribly and are hardly recognisable as scores anymore. It happens in every pdf reader I can use in Ubuntu, so it's not a bug in evince or something, I guess. It also happens on my mother's laptop where Quantal is also installed. I've got an example attached so you can see what I mean.

I don't know against which package I can file a bug. Is there a specific pdf rendering package connected to Quantal?

The examples are saved in jpg in Gimp (in Ubuntu and in Mac OS X). The Mac one is the one how it's supposed to look like. I've saved them without any modifications. They look like this in a pdf viewer as well.

Thanks for your help.

---

### Post by The Cog on 2012-10-13
A wild guess, but have you installed the package ubuntu-restricted-extras? It may be that you need some fonts from this package - it includes an installer that downloads lots of microsoft fonts.

---

### Post by DavidSommen on 2012-10-13
> **The Cog said:**
> A wild guess, but have you installed the package ubuntu-restricted-extras? It may be that you need some fonts from this package - it includes an installer that downloads lots of microsoft fonts.

Yes, I have installed that package (it says it's the newest version).

---

### Post by grahammechanical on 2012-10-13
I have found this link for you:

[https://live.gnome.org/Evince/Testing]("https://live.gnome.org/Evince/Testing")

It does not solve the problem. I might help in determining if this is an issue with Evince or with Evince on 12.10.

I assume that

a) you have not upgraded Sibelius to a newer version that is producing a more refined/improved PDF. 

b) PDFs that were rendered acceptably in 12.04 - Evince are now not being rendered acceptably in 12.10 - Evince.

c) you are using the same settings in Sibelius as you were when Ubuntu was 12.04, including embedded fonts.

Regards.

P.S. a final thought. Does Sibelius use a special font? Or does it use the fonts that come as standard on the Mac? Do you need to install a special font in Ubuntu?

---

### Post by DavidSommen on 2012-10-13
> **grahammechanical said:**
> I have found this link for you:

[https://live.gnome.org/Evince/Testing]("https://live.gnome.org/Evince/Testing")

It does not solve the problem. I might help in determining if this is an issue with Evince or with Evince on 12.10.

Thanks a lot. I didn't open all of them but the ones I did open render pretty much correctly. Sometimes the fonts are ugly. Unfortunately, I have no immediate way of comparing this to Evince in Precise. On my girlfriend's laptop, Precise is installed. But I can't use that laptop until next week at the earliest.
> 
I assume that

a) you have not upgraded Sibelius to a newer version that is producing a more refined/improved PDF. 

Indeed I have not. The pdfs I made earlier, that worked perfectly on ubuntu 12.04, all have the same problem. Even the ones I made on earlier versions of Sibelius have the exact same problem.
> 

b) PDFs that were rendered acceptably in 12.04 - Evince are now not being rendered acceptably in 12.10 - Evince.

Exactly.
> 
c) you are using the same settings in Sibelius as you were when Ubuntu was 12.04, including embedded fonts.

I haven't made any changes to the settings in Sibelius.
> 
Regards.

P.S. a final thought. Does Sibelius use a special font? Or does it use the fonts that come as standard on the Mac? Do you need to install a special font in Ubuntu?
Not that I am aware of. The PDFs always worked perfectly and now they don't anymore.

By the way, I used different pdf readers to test if the issue is caused by Evince or something else. In ePDFviewer I have the same problem. Also in GIMP, when importing the pdfs. However, in "ViewPDF", the pdf is rendered correctly. Although I don't particularly like the GUI of this program, my problem is temporarily solved. Perhaps this can give us a clue as to what causes this strange behaviour?

---

### Post by DavidSommen on 2012-10-14
I can now confirm this issue is not present with the same pdf on Precise Pangolin (my brother's laptop has precise installed).

It's definitely a problem for Quantal. Is it perhaps poppler where we should seek the problem?

---

### Post by DavidSommen on 2012-10-15
I will attach the original pdf to see whether you have the same problem on Precise and/or Quantal.

Can you please reply whether the pdf displays correctly in Evince?

Thanks.

---

### Post by skeve on 2012-10-15
> **DavidSommen said:**
> I will attach the original pdf to see whether you have the same problem on Precise and/or Quantal.

Can you please reply whether the pdf displays correctly in Evince?

Thanks.

This pdf displays wrong in Evince while it renderes correctly in Okular
And btw, 'File' menu in Evince doesn't work for me in Russian environment, but when I start it with LANG=C it works
So I guess there's something wrong with Evince

---

### Post by DavidSommen on 2012-10-15
Okular renders it correctly indeed. So I guess I can file a bug for evince.

Thanks for your effort.

---

