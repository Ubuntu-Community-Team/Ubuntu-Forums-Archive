---
title: "New software for Ubuntu"
date: 2008-10-13
forum: The Cafe
---

### Post by Macintosh Sauce on 2008-10-13
I am working on a program called "Civics Flash Cards" for Ubuntu and its derivatives (Mac OS X and Windows Vista as well). I have the program working under Ubuntu after compiling it - need someone to volunteer to package it as a .deb file once it reaches the final release version (since I don't know how). :)

Here are a few screenshots from the latest beta version.

[IMG]http://www.jamesnrhodes.com/personal/james/ubuntu/mainscreen_ubuntulinux.png[/IMG]

[IMG]http://www.jamesnrhodes.com/personal/james/ubuntu/question1a_ubuntulinux.png[/IMG]

[IMG]http://www.jamesnrhodes.com/personal/james/ubuntu/question1b_ubuntulinux.png[/IMG]

---

### Post by billgoldberg on 2008-10-13
Take a look here:

[http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall](http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall)

It should take more than 10 minutes to make one.

---

### Post by Macintosh Sauce on 2008-10-13
> **billgoldberg said:**
> Take a look here:

[http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall](http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall)

It should take more than 10 minutes to make one.

Thanks for the information - I will give it a try. :)

---

### Post by Macintosh Sauce on 2008-10-25
I tried making my own .deb file. Did not work at all! I need someone to make a .deb file so I can release my program for Ubuntu, because it is going to take me a bit of time to learn how to make my own .deb files.

Thanks in advance!

[Link]("http://www.jamesnrhodes.com/personal/james/ubuntu/civicsflashcards_linux.zip") to the executable file.

---

### Post by smartboyathome on 2008-10-25
> **billgoldberg said:**
> Take a look here:

[http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall](http://ubuntuforums.org/showthread.php?t=51003&highlight=checkinstall)

It should take more than 10 minutes to make one.

That isn't recommended. It doesn't make proper deb files and the deb files don't always work on all systems.

---

### Post by Macintosh Sauce on 2008-10-26
> **smartboyathome said:**
> That isn't recommended. It doesn't make proper deb files and the deb files don't always work on all systems.

That's nice to know now after wasting my precious time trying to make a .deb file from those instructions.

If someone doesn't help me initially by packaging this, because I honestly do not know how to do it, I am going to have to cease any development on programs for Ubuntu - a shame IMHO. This exactly illustrates the need for an easy way of installing programs in Linux. Sigh...

---

### Post by loell on 2008-10-26
i have built debs for quite some time now (see my sig for some of them), perhaps i could help, of course  i'll be needing the source to compile and package it.

---

### Post by cariboo on 2008-10-26
When will versions for other countries be available?

Jim

---

### Post by Macintosh Sauce on 2008-10-26
> **cariboo907 said:**
> When will versions for other countries be available?

Jim

What do you mean by that? The program is for U.S. Permanent Residents that want to become U.S. Citizens. ???

---

### Post by Macintosh Sauce on 2008-10-26
> **loell said:**
> i have built debs for quite some time now (see my sig for some of them), perhaps i could help, of course  i'll be needing the source to compile and package it.

My source code to the program? Don't you mean the compiled application? The link is posted above...

---

### Post by bonzodog on 2008-10-26
To build the deb succesfully, it has to be compiled from the source code. I take it you are going to make this Open Source?

---

### Post by loell on 2008-10-26
> **Macintosh Sauce said:**
> My source code to the program? Don't you mean the compiled application? The link is posted above...

when you make a proper deb package usually it goes something like this

source code --> compilation --> packaging

now you obviously want this as closed source, then most likely  you'll gonna have to package it yourself. 

that doesn't mean one couldn't package the binary, its just unusual (improper like checkinstall does) and its more work to do.

---

