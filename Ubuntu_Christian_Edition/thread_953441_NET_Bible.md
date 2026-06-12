---
title: "NET Bible"
date: 2008-10-20
forum: Ubuntu Christian Edition
---

### Post by 73ckn797 on 2008-10-20
Has anyone used the NET Bible?

I have it installed and working in Ubuntu though not specifically designed for Linux and not running in any emulation. It is completely free. 

check it out: [http://www.bible.org/category.php?scid=5&category_id=71&parent_id=0](http://www.bible.org/category.php?scid=5&category_id=71&parent_id=0)

They have no instructions for using with Linux. If interested I will tell you how.

---

### Post by david_kt on 2008-10-20
> **73ckn797 said:**
> Has anyone used the NET Bible?

I have it installed and working in Ubuntu though not specifically designed for Linux and not running in any emulation. It is completely free. 

check it out: [http://www.bible.org/category.php?scid=5&category_id=71&parent_id=0](http://www.bible.org/category.php?scid=5&category_id=71&parent_id=0)

They have no instructions for using with Linux. If interested I will tell you how.

For HTML, it could be installed/extracted using wine and then open the extracted file (netbible.chm) using chm viewer. You could install it in windows and copy over netbible.chm to linux as well.

For e-Sword module, you could download it from [here]("http://www.bible.org/ccount/click.php?id=8"), and you could install it to e-Sword using e-Sword installer provided you install e-Sword using the same installer/method:

[http://ubuntuforums.org/showthread.php?t=404042](http://ubuntuforums.org/showthread.php?t=404042)

Choose "manual" and navigate to the downloaded net1_free_esword_setup.exe.

DK

---

### Post by Eutaw on 2008-10-20
Churchpup (Puppy linux) has it setup to run through Firefox, so I use it with the footnotes there. It's not a bad study help.

---

### Post by 73ckn797 on 2008-10-20
> **Eutaw said:**
> Churchpup (Puppy linux) has it setup to run through Firefox, so I use it with the footnotes there. It's not a bad study help.


I have the CD of NET Bible. All I did was copy the CD contents to a directory I created. Using Firefox or any other browser, I created a bookmark link to "index.html". Click on the bookmark and you have the fully functioning NET Bible. I tried the Linux version from Bible.org but it would not run the footnotes.

It is a great study aid.

---

### Post by david_kt on 2008-10-20
> **73ckn797 said:**
> I have the CD of NET Bible. All I did was copy the CD contents to a directory I created. Using Firefox or any other browser, I created a bookmark link to "index.html". Click on the bookmark and you have the fully functioning NET Bible. I tried the Linux version from Bible.org but it would not run the footnotes.

It is a great study aid.

But the downloadable version that I tried is chm, not HTML.

DK

---

### Post by 73ckn797 on 2008-10-20
> **david_kt said:**
> But the downloadable version that I tried is chm, not HTML.

DK


Download the Windows version [HTML Help version (includes search)]("http://www.bible.org/ccount/click.php?id=2")

Click the link and it will ask to save or open. Select save file. 

You could extract the files and burn to a CD. Then copy the contents to the directory or use the disk directly by selecting "index.html".

Then follow the directions I gave.

---

### Post by david_kt on 2008-10-20
> **73ckn797 said:**
> Download the Windows version [HTML Help version (includes search)]("http://www.bible.org/ccount/click.php?id=2")

Click the link and it will ask to save or open. Select save file. 

You could extract the files and burn to a CD. Then copy the contents to the directory or use the disk directly by selecting "index.html".

Then follow the directions I gave.

I have tried the link you give, it give me chm file and what you did I guess was converting it to html. Under windows it looks like extracting, but actually it is converting.

But for those who do not have windows, you could do it in linux as well. First is using chm viewer (I like kchm). But if you want to open it using browser, you should convert it to html. Below is the steps:
```

sudo apt-get install libchm-bin
extract_chmLib netbible.chm outdir
```

DK

---

### Post by 73ckn797 on 2008-10-20
> **david_kt said:**
> I have tried the link you give, it give me chm file and what you did I guess was converting it to html. Under windows it looks like extracting, but actually it is converting.

But for those who do not have windows, you could do it in linux as well. First is using chm viewer (I like kchm). But if you want to open it using browser, you should convert it to html. Below is the steps:
```

sudo apt-get install libchm-bin
extract_chmLib netbible.chm outdir
```DK

I did not convert anything. Of course I do have the OEM CD when I purchased the printed NET Bible. 

EDIT: OPPS! I have never used the downloaded file to install since using Ubuntu but did with Windows. I never paid attention to the files used. You could either buy the CD or the printed Bible and get the CD with it ( I guess, I did). End of discussion.

---

### Post by dorival.ercole on 2010-09-26
To use as html,

[LIST=1]
[*]download the html version (obviously)
[*]open a browser;
[*]type "file:///home/(your own folder name)/Download/NETBible2009/index.htm";
[*]save to favorites.
[/LIST]

Now you can use as html. :popcorn:

note: I assume that your using NETBible 2009, ok?

---

