---
title: "How to customize the Ubuntu Installation for your Distribution - TUTORIAL"
date: 2010-01-01
forum: The Cafe
---

### Post by gosalia on 2010-01-01
Hello. I have looked a lot in almost every page in Ubuntu, Google and some other Linux Distributions Forums, Help Guides and Tutorials, and have never been able to customize, or even find a valuable source on customzing the Ubuntu Installation, also known as Ubiquity.

Now if you are planning on creating a LiveCD or Ubuntu-based Distribution using Remastersys or some program like that, then you will love this tutorial, as do I.

So Welcome to the Ubuntu Installation Customization for your Distribution.

First of all, make sure you have Ubiquity installed.
Quickly goto Synaptic now, and check.

Once you have that, go inside a terminal and type sudo nautilus.
Then goto /usr/share/ubiquity.
You will see some system files which I will now mention again in this tutorial for the sake of my tiredness. 
Please go inside the pixmaps folder.

Here you will see the images that are presented when you select your region in the installation process. You may customize it, but I hardly recemmond it as the areas I tell you to customize are far more rewarding.
Now, just go inside the "ubuntu" folder and see the "logo.png".

Customize it to have your own Logo and Distribution Name. 

After you finish that come out of it, all the way back to /usr/share.
Now we go inside the big area, where we customize a LOT.

Go inside "Ubiquity-Slideshow" folder.

In this folder you will see the images and text that pop up during the installation of Ubuntu. [Do you remember?]("http://images.google.com/imgres?imgurl=http://www.techairlines.com/wp-content/uploads/2009/10/ubuntuinstall.png&imgrefurl=http://www.techairlines.com/ubuntu-9-10-karmic-koala-install-progress/&usg=___WQRdqTYUw2AOMmMx48NHgJjvEA=&h=542&w=650&sz=224&hl=en&start=1&sig2=DGDRTCUqhGp65qXUF2J6jw&tbnid=2AtcDa31euBSEM:&tbnh=114&tbnw=137&prev=/images%3Fq%3Dubuntu%2Binstalling%2Bslideshow%26gbv%3D2%26hl%3Den&ei=me89S_PoCYGgkQWXx43IBQ") 

Now just go into Slides/icons and here you will see the beautiful icons of all the slides. You may notice the extroadinary graphics and input the Ubuntu team has put into most of these, and so I have decided not to customize this, but you can surely go ahead.
However, for legal sake, I had to customize the logo which I have changed it to be mine (that is I deleted the Ubuntu logo and replaced it with a High-Quality version of my logo).

Once you feel you have done enough, please go out of that folder and scroll straight down to customize the writing on the slides in the installation.

[B]Here you will see 13 .html files. HTML is simple, you do not have to know anything in HTML to customize these files, however you must understand to not go out of the boundaries. Stay in the templates, because saying too much will look un-Professional and dodgy when it comes to size issues.

I prefer Cutting huge paragraphs of writing in between the "" and starting to type about the subject in My Distributions way. Making sure that I do not exceed the previous 3-4 sentence that Ubuntu already had.[/B]

Ok, to customize these .html files I will quickly show you one of them and customize it before I fall asleep on my keyboard. 

Right-click "accessibility.html". Click OPEN WITH and select GEDIT.

You will see something like this, however where it says Gosalia, that is my operating system, it used to say Ubuntu. CAUTION - Do not copy my work, there will be severe consequences, considering I took 5 minutes to write it and the rough work your Operating System installation will look...

> <h1 class="title">**Accessibility in Gosalia**</h1>

<div class="main">

<div class="content"><ul>
    <li>**Our accessibility performance exceedes those in most Linux and Windows Operating Systems. We aim to have the best accessibility for you.**</li>  <li>**You can get at these tools in one place: the **<em>**Assistive Technologies Preferences,**</em>** inside the System Menu. From there, you can turn on helpful tools like** <em>**Orca,**</em>** to speak text on the screen, or dwell click to press mouse buttons automatically.**</li>
    <li>**Remember to check out the **<em>**Appearance Preferences**</em>**, too. You can choose between different visual styles and even change the fonts that are used by applications.**</li>
</ul></div>

</div>

<img class="icon" src="icons/accessibility.png" alt="" />The writing in **BOLD** is the ONLY things that you can change, unless you are an expert in HTML, then go ahead, but I do not recommend you exceed this limit.

Enjoy, do this to all of them remembering to only write in between the <li> and the </li>

Remember one thing, where it says "UBUNTU" you can change it, unless it is a file name, then DON'T CHANGE IT! :)

Oh yes, and now when you create your ISO with Remastersys (or equivalent) then you will have your customized Installation ready in the LIVECD process, check it out! It worked for me, and it is spectacular. Making a Video about this now...

---

### Post by gosalia on 2010-01-01
Hope you enjoy. If you are a Ubuntu-based Distribution programmer or budding learner then don't forget to join my Social Club. It is called The Ubuntu-based Distro Developers.

And also, if you are interested in my Ubuntu-based Distribution (not vaiant) then goto [www.gosalia.co.nr](www.gosalia.co.nr) and [www.gosaliaforums.co.nr](www.gosaliaforums.co.nr) to see my Official Release and Forums sites.

---

### Post by superepic on 2010-05-09
hello, thank you for this topic and sorry for my english xD


**gosalia** do you know how change the first step , for example Language, Location.... i try edit the files in /usr/share/ubiquity/gtk ... but i can't, the text don't change , i don't know how it work.

I would like change that text.

somebody else know ??

Thank. :confused:

PD: I have Ubuntu Lucid.

---

### Post by merlin_ie on 2010-09-04
```
After you finish that come out of it, all the way back to /usr/share.
Now we go inside the big area, where we customize a LOT.

Go inside "Ubiquity-Slideshow" folder.

In this folder you will see the images and text that pop up during the installation of Ubuntu. Do you remember?
```

That's as far as I can get, as I don't see the specific folder in /usr/share. I've installed ubiquity as well. Any suggestions? (using Lucid)

EDIT : I installed ubiquity from terminal, but I just looked in synaptic and I found ubiquity-slideshow-ubuntu and after I installed that, thunderbirds are go. Thanks for tutorial

---

### Post by gosalia on 2010-09-04
> **superepic said:**
> hello, thank you for this topic and sorry for my english xD


**gosalia** do you know how change the first step , for example Language, Location.... i try edit the files in /usr/share/ubiquity/gtk ... but i can't, the text don't change , i don't know how it work.

I would like change that text.

somebody else know ??

Thank. :confused:

PD: I have Ubuntu Lucid.

As I believe, there are files in usr/share/ubiquity that have the extension .ui. I believe you can use a coding application from the Ubuntu Software Center (im sorry I don't remember which one) to edit the text in your Ubiquity Installer. Alternative you can use gedit to edit the files. Just right click and click OPEN WITH and find GEDIT.

---

### Post by spiralciric on 2012-05-15
Files you are looking for are in /usr/lib/ubiquity/

---

### Post by overdrank on 2012-05-15
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

