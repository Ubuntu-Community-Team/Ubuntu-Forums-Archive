---
title: "Convert HTML to Text using w3m"
date: 2015-08-17
forum: Tutorials
---

### Post by aeden.d on 2015-08-17
This is a brief tutorial on converting HTML to Text.
The program used in this tutorial is [w3m]("http://packages.ubuntu.com/search?suite=default&section=all&arch=any&keywords=w3m&searchon=names") -- available in the repos. This is not the only option as there are others,  but I chose to focus on just one.
w3m also has a sourceforge site available [here]("http://w3m.sourceforge.net/"). 
This tutorial has been written for Ubuntu 14.04 LTS 

I will give short examples (the most common uses) and this is by no means an exhaustive HOWTO. I recommend referencing the MAN pages for [w3m]("http://manpages.ubuntu.com/manpages/trusty/man1/w3m.1.html") for more advanced configurations.

One of the advantages of converting HTML to text is that you can "dump" the contents of an HTML file as a text file. Using w3m will strip all the source code of the html file and give you a clean text file with the contents formatted. 

[B]w3m
[/B]> w3m is a text-based web browser as well as a pager like `more' or `less'. With w3m you can browse web pages through a terminal emulator window (xterm, rxvt or something like that). ***Moreover, w3m can be used as a text formatting tool which typesets HTML into plain text.*** - sourceforge w3m page 

All-in all, w3m is a text based interactive web browser that can be run in the Terminal. But you can use it in non-interactive mode by means of the **-dump** command. You can use a URL or the filename of a .html file you have saved to convert.

A few examples may be:

** Example One:**

There is a site with a howto that you wish to save as a text file. You could save the page for offline viewing but that limits your options as far as editing the file for personal notes, etc. Saving the html file for offline viewing also limits your options of the programs you can use to view the file - a web browser. 

Before we get started, go ahead and make sure your system is up-to-date using the following command
```
sudo apt-get update && sudo apt-get upgrade
```

Now, go ahead and install w3m with the following command
```
sudo apt-get install w3m
```

Now that you have w3m installed, open a Terminal session by using Ctrl + Alt + t

Open a web browser of your choice and navigate to a howto site of interest.

Copy the URL of the site.

Navigate back to your Terminal and cd to the directory you wish to save the converted html file.

With the following command you will be able to save the html to text.
```
w3m -dump url-of-how-to-site > output.txt
```

Output.txt can be anything you wish to name the file. Typically I use the title of the url site since it already describes the context of the howto.

** A couple of things about what we just did.**

We used w3m non-interactively (we didn't open the text-based browser) and we evoked the **-dump** option to dump the formatted page into stdout

We redirected the output to a file by using **> output.text**

While still at the Terminal use the following command to get a list of the files in the present working directory or the directory you saved the text file
```
ls -ac --group-directories-first
```

You should see a file listed [B]file-name-you-chose.txt

[/B]Use the following command to view the file in the Terminal```
nano file-name-you-chose.txt
```

You should now see the previous webpage formatted into a text file.

**Example Two**

Lets say you have an html file saved to your hdd and you wish to convert that file to text. you can use **w3m **to produce the same results as the previous example with a URL.

Navigate to the directory of your html file

Use the following command to convert the saved html file to text
```
w3m -dump input.html > output.txt
```

In this example **"input.html"** is the name of the html file you have saved and **"output.txt"** is the name you choose to give the txt file.

To check if everything went well follow the previous steps of listing the contents of the directory and using nano to view the txt file.

This is a very basic HOWTO. There are some powerful options when using w3m, have fun a play around with it. Also, should you dump someone else's work to a txt file for your own research, [B]DO NOT strip the credits to the author or redistribute without their permission... That's not cool

Enjoy
[/B]

---

### Post by Kenneth_C._Brown on 2015-08-26
thank you for this tutorial, although it is brief, it has been of immense help. Keep on posting more tutorials on this .

---

### Post by aeden.d on 2015-08-28
You're welcome.

---

### Post by coldraven on 2015-08-29
Thanks, that could come in very handy.

---

### Post by vasa1 on 2015-08-29
+1. Bookmarked this. I often save web pages to disc. If w3m allows me to clean up the page, it'll be great.

---

### Post by v3.xx on 2015-08-29
Just tried it and yes, this can come in handy.  Thanks

---

