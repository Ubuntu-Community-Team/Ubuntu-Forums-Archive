---
title: "The tutorial guide challenge - pimp your workflow"
date: 2011-12-07
forum: The Cafe
---

### Post by keithpeter on 2011-12-07
Hello All

Version 0.2 of my begginer's guide to Unity 2d is now available at

[http://sohcahtoa.org.uk/pages/files/unity2dguide.pdf](http://sohcahtoa.org.uk/pages/files/unity2dguide.pdf)

**Challenge to the Lubuntu Crew and the Xubuntu Posse**

Can you produce a similar guide, using and requiring only the software available in a default install of your chosen Ubuntu flavour?

The only extra you are allowed is the Restricted Extras package for your chosen flavour. Show off your default software!

A Unity 3d guide would be good as well, and I'd welcome rival material for Unity 2d.

*PS: there are three minor 'bugs' or mistakes in version 0.2, can you spot them?*

**Reply to this to accept the challenge, suggest new activities, or just give feedback on my efforts.**

---

### Post by nothingspecial on 2011-12-07
> **keithpeter said:**
> 

**Challenge to the Lubuntu Crew and the Xubuntu Posse**

Can you produce a similar guide, using and requiring only the software available in a default install of your chosen Ubuntu flavour?



Go on, I dare you :)

---

### Post by keithpeter on 2011-12-09
Hello All

I'm bumping this thread, just to say that I have uploaded version 0.21 of the beginner's tutorial guide that corrects a few minor typos. Version 0.3 will have sections on USB sticks and backup to external hard drive.

Anyone else interested in *end user* guides out there at all? Anywhere?

---

### Post by lykwydchykyn on 2011-12-09
When I click your link I get an "access denied" error.

---

### Post by perspectoff on 2011-12-09
Hey dude --

why not set up your own Wiki and put your guide as a wiki (instead of a PDF file that is cumbersome to edit) ?

You can do it for the price of a URL (as cheap as $3/year).

You can use Ubuntu as a server and MediaWiki as the software, all for free.

Instructions are at Ubuntuguide:

[http://ubuntuguide.org/wiki/Ubuntu:All#MediaWiki](http://ubuntuguide.org/wiki/Ubuntu:All#MediaWiki)

or at Kubuntuguide:

[http://ubuntuguide.org/wiki/All#MediaWiki](http://ubuntuguide.org/wiki/All#MediaWiki)

Alternatively, if you're really proud of your user guide, I'd be happy to check it out and incorporate it into Ubuntuguide...

---

### Post by keithpeter on 2011-12-09
Hello folks...

> **lykwydchykyn said:**
> When I click your link I get an "access denied" error.

Agghhhhhhh how embarassing. Fixed now. I have an lftp script that mirrors local folder to remote folder. It mirrors permissions, and I forgot to change them before I uploaded. :oops: Thanks very much for pointing this out.

> **perspectoff said:**
> Hey dude -- why not set up your own Wiki and put your guide as a wiki (instead of a PDF file that is cumbersome to edit) ?

That is an idea I'm considering. The document is designed for use *printed on paper*, so wiki editing would be for many authors to collaborate, which I think would be ace. However, there don't appear to be that many authors around :twisted: 
I would also need to work out how media-wiki -> pdf works ('collections').

The other issue with wiki is that (as you will now be able to see since I fixed the permissions) the guide takes the form of a *connected series of activities* that someone works through. That kind of stuff is tricky with multiple authors working in parallel.

If anyone wanted to contribute a tutorial guide activity for, say, backing up the home drive using Backup, they could post it here and I would be delighted to incorporate the material with attribution and a link back to a Web site.

If you think the tutorial guide looks ok, link away and I can link to the ODT file as well if that helps.

---

### Post by lykwydchykyn on 2011-12-09
> **keithpeter said:**
> 
The other issue with wiki is that (as you will now be able to see since I fixed the permissions) the guide takes the form of a *connected series of activities* that someone works through. That kind of stuff is tricky with multiple authors working in parallel.


I did a similar type of guide years ago for SimplyMEPIS, and I understand what you mean.  I ended up having a few people send me corrections and suggestions, then later posted the .odt file along with the PDF (it's CC licensed so people can make derivative works).

If I were doing a collaborative thing like that again, I'd probably make it a collection of text files in a simple markup format like markdown or RST and put it on github.

---

### Post by keithpeter on 2011-12-10
Hello All

@lykwydchykyn: yes, I had considered Markdown and text files, that is how I write my Web site. The GitHub idea sounds *very* interesting. 

@everyone 

**Question**: suppose I have a Git repository full of Markdown pages with file names in a logical naming convention reflecting the order of the activities. These pages link out to image files of screen grabs held in a directory within the repository. 

What is the *easiest* way to generate a PDF document from the collection? If I get my tools sorted out now, I'll try this method for the 12.04 beginner's guide.

---

### Post by lykwydchykyn on 2011-12-10
> **keithpeter said:**
> 
**Question**: suppose I have a Git repository full of Markdown pages with file names in a logical naming convention reflecting the order of the activities. These pages link out to image files of screen grabs held in a directory within the repository. 

What is the *easiest* way to generate a PDF document from the collection? If I get my tools sorted out now, I'll try this method for the 12.04 beginner's guide.

I haven't done conversions involving linked images. But you could just write a simple script to cat all the chapters together and run them through pandoc.

---

### Post by keithpeter on 2011-12-11
> **lykwydchykyn said:**
> I haven't done conversions involving linked images. But you could just write a simple script to cat all the chapters together and run them through pandoc.

Thanks lykwydchykyn, pandoc is very good if you install texlive and texlive-extras. 

Pandoc -> pdf can pull in images included in the markdown files using the ![]() syntax and it adds captions to each image using the alternate text in the [].

It can also concatenate a lot of markdown files to one large pdf and you can specify a template.

Thanks.

---

