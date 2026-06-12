---
title: "Help installing Latex packages"
date: 2010-04-05
forum: The Cafe
---

### Post by martina22 on 2010-04-05
Hi, apologies for hijacking your post, only it seemed the most similar to my situation. 
 
I am a complete beginner when it comes to computer programs and files and try as I might I struggle to understand virtually anything I find relating to help for installing Latex packages. 
 
Somehow, miraculously, i have been able to install a couple and they work, but I have been having trouble getting the packages beamer and caption to work. Despite downloading the files and copying them into every folder i can possibly think of that might make it work, they always come up with some message telling me that one of the files (.sty) is not installed. I have downloaded everything provided, and sure enough I cannot find a tex\latex\pgf\basiclayer\pgfcore.sty file in the beamer folder or a tex\latex\xcolor\xcolor.sty file and a few others that it claims it needs. My folders with the downloaded stuff are copied into the tex\latex folder which it seems to be asking for. I'm at my wits and would be so so so grateful if anyone can help me and explain things to me in non-technical language!
 
Thank you so much in advance. :)

---

### Post by martina22 on 2010-04-05
Ooh, also I think this forum may not be exactly relevant to me - I only came across it whilst searching for Latex help. Erm....I have no idea what Ubuntu is, is an alternative to windows/linux etc? If this makes any difference to anyone, I am using Windows.

---

### Post by SnickerSnack on 2010-04-05
> **martina22 said:**
> Hi, apologies for hijacking your post, only it seemed the most similar to my situation. 
 
I am a complete beginner when it comes to computer programs and files and try as I might I struggle to understand virtually anything I find relating to help for installing Latex packages. 
 
Somehow, miraculously, i have been able to install a couple and they work, but I have been having trouble getting the packages beamer and caption to work. Despite downloading the files and copying them into every folder i can possibly think of that might make it work, they always come up with some message telling me that one of the files (.sty) is not installed. I have downloaded everything provided, and sure enough I cannot find a tex\latex\pgf\basiclayer\pgfcore.sty file in the beamer folder or a tex\latex\xcolor\xcolor.sty file and a few others that it claims it needs. My folders with the downloaded stuff are copied into the tex\latex folder which it seems to be asking for. I'm at my wits and would be so so so grateful if anyone can help me and explain things to me in non-technical language!
 
Thank you so much in advance. :)

> **martina22 said:**
> Ooh, also I think this forum may not be exactly relevant to me - I only came across it whilst searching for Latex help. Erm....I have no idea what Ubuntu is, is an alternative to windows/linux etc? If this makes any difference to anyone, I am using Windows.

You should consider using [MiKTeX]("http://miktex.org/").  It installs packages automatically.

If you use \includepackage{beamer} in the tex file (and you may also need to use a command from that package in the body of the file), then MiKTeX will attempt to download and install it for you automatically.  This can take several minutes, and if I remember correctly, no indication is given on how much longer it will take, so you must simply wait.  It would probably be a bad idea to interrupt the installation.

And, yeah that is quite a hijack, since you're not asking about ubuntu or texlive.  I'm going to ask a moderator to move these posts to their own thread, though I don't know how much help you'll be able to get.

Once it's moved, you should give as much information as you can about what software you are using.  Are you using something similar to miktek (which is a particualar implementation of tex/latex)?  Which windows version are you using?

---

### Post by perce on 2010-04-06
beamer is installable from the repository. The command is: 

```
sudo apt-get install latex-beamer
```

This will install it systemwide, so you won't need to copy it in every directory. I have no idea about the package caption, since I have never used it, but I bet it is also available in some package.

If you don't know what "installing from the repositories" means, give at look at the excellent Aysiu's tutorials: [http://www.psychocats.net/ubuntu/installingsoftware]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by red_Marvin on 2010-04-06
martina22: Ubuntu is a linux distribution targeted at people with no previous linux experience as well as those who have been around for a while. SnickerSnack mentioned MiKTeX which also turns up in many searches for "latex windows", you might have some luck with that...

perce: martina22 stated that she is using windows

---

### Post by perce on 2010-04-06
> **red_Marvin said:**
> 

perce: martina22 stated that she is using windows

ooops

---

