---
title: "Thinking about learning a new programming language, any ideas?"
date: 2010-05-22
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-05-22
I have a bit of knowledge with Visual Basic, and C++, but I only got as far as beginning arrays (we skipped strings and went straight to arrays :shock:). Well I want to start developing programs for linux like I was learning to do with VB, but VB is out of the question, and I can't stand C++ because it's too heavy on the syntax. So I've noticed that the common ones used in linux are perl, python, C++, C. So which one is a good one to learn?

---

### Post by baddog144 on 2010-05-22
Out of those, I'd be inclined to say Python, as it's getting very popular, can be used in web development via CGI or Django, and is also quite common throughout Ubuntu. Another gem (no pun intended) of a language is Ruby, which I'm learning at the moment and it's really very nice. You could also try a slightly alternative sort of language for fun, LISP or Haskell for even INTERCAL ;)

---

### Post by ssj6akshat on 2010-05-22
There is Mono for C#/.NET on Linux

---

### Post by Legendary_Bibo on 2010-05-22
Well I already have an idea of something I want to make. I want to make an installer for programs because one thing that was simple in windows was installing programs. So I want to make a universal installer (supports tarballs, debs, everything) and have it add it into the repository for updates. I want to help make linux move away from the command line to be easier for new users.

---

### Post by baddog144 on 2010-05-22
> **Legendary_Bibo said:**
> Well I already have an idea of something I want to make. I want to make an installer for programs because one thing that was simple in windows was installing programs. So I want to make a universal installer (supports tarballs, debs, everything) and have it add it into the repository for updates. I want to help make linux move away from the command line to be easier for new users.

Python might be good for that then. You can add a GUI with PyGTK or PyQT or something. Automatically installing tarballs is no mean feat though.

---

### Post by chessnerd on 2010-05-22
> **Legendary_Bibo said:**
> Well I already have an idea of something I want to make. I want to make an installer for programs because one thing that was simple in windows was installing programs. So I want to make a universal installer (supports tarballs, debs, everything) and have it add it into the repository for updates. I want to help make linux move away from the command line to be easier for new users.

Interesting idea. Maybe call it ULI (Universal Linux Installer) for short?

Debs and RPM files are supposed to do this, but I find that many programs still come as tarballs, zip files, etc. If you can make a program for your installer that easily converts from deb to ULI and RPM to ULI and tarball to ULI with a simple GUI, it could be used either by the packager or the recipient and would allow for easy installation. I'm not sure how you would do this, but I do think it might be useful.

For this type of a program, I would probably recommend C++, but since you don't like that I'd look at Python and Ruby. A friend of my really likes programming in Ruby, although I've never used the language before...

---

### Post by v1ad on 2010-05-22
i would say C, then move on to python.

---

### Post by Legendary_Bibo on 2010-05-22
Python it is. I have another important question. If I were to make a universal installer, would I be allowed to take code from the deb and rpm installers and inject it into my program?

---

### Post by baddog144 on 2010-05-22
That would depend on the license the code is under. You'll want to look up the terms of the various GPL licenses, BSD and MIT as well. There are various other licenses out there, GPL and BSD being the most common for open source stuff.

---

### Post by Legendary_Bibo on 2010-05-22
Can anyone recommend a good book for learning python.

---

### Post by Legendary_Bibo on 2010-05-22
I don't know where I would find that stuff though. Do you have to put your code under a license. Legal stuff confuses me, I just want to write code. :(

---

### Post by chessnerd on 2010-05-22
> **Legendary_Bibo said:**
> I don't know where I would find that stuff though. Do you have to put your code under a license. Legal stuff confuses me, I just want to write code. :(

Here are some Wikipedia links you'll probably find helpful:

General Public License (GPL): [http://en.wikipedia.org/wiki/GPL](http://en.wikipedia.org/wiki/GPL)

Lesser GPL (LGPL): [http://en.wikipedia.org/wiki/LGPL](http://en.wikipedia.org/wiki/LGPL)

License/GPL Compatability: [http://en.wikipedia.org/wiki/License_compatibility](http://en.wikipedia.org/wiki/License_compatibility)

BSD License(s): [http://en.wikipedia.org/wiki/BSD_licenses](http://en.wikipedia.org/wiki/BSD_licenses)

MIT License: [http://en.wikipedia.org/wiki/MIT_License](http://en.wikipedia.org/wiki/MIT_License)

A bunch of licenses: [http://en.wikipedia.org/wiki/List_of_software_licenses](http://en.wikipedia.org/wiki/List_of_software_licenses)

Free software licenses: [http://en.wikipedia.org/wiki/List_of_software_licenses#Free_software_licenses](http://en.wikipedia.org/wiki/List_of_software_licenses#Free_software_licenses)



I actually find the legal stuff fun. I usually put my code under the MIT license because it is so brief and to-the-point:

[QUOTE=MIT License] Copyright (c) <year> <copyright holders>

 Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

 The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

 THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.[/QUOTE]

You couldn't fit the GPL here.

---

### Post by ipatfrmww on 2010-05-22
I would say just put a GPL on it, cause its by far the most common, and people know it.
I read it once, but its meaning is sort of just implied nowadays.
If you don't understand them, then you probably won't recognise the differences between them anyway(like me) and it realy wont matter too much (they all mean the same thing to most people: It's Free)

I would say that if you want to use anything other than GPL it would be the MIT one(cause its short and simple)

---

### Post by Legendary_Bibo on 2010-05-22
MIT sounds good to me. So how do I go about registering or whatever under the license?

---

### Post by chessnerd on 2010-05-22
> **Legendary_Bibo said:**
> MIT sounds good to me. So how do I go about registering or whatever under the license?

There are a two main options:

1. On the top of all of the source files, place the license

2. When you distribute your program, include a text file called "LICENSE.TXT" or something similar that holds the license and, in the README file (and maybe the top of source files), point people to the license file

The first is good if you think individual parts of your program's source will be used by other people in other projects. It's okay for other uses, but makes it a bit harder to distribute binary-only copies because the license is in the source.

The second is how most people (including companies) license their software.

I'd go with the second.

---

### Post by Legendary_Bibo on 2010-05-22
Oh that's it, I thought I had to contact the supreme court or something to get a license approved or something. I didn't realize that's all it took.

---

### Post by w0Rm210 on 2010-05-22
Yeah i would have to say python considering it's close to C in a way but much much MUCH more simpler also ruby might be something to consider.

---

### Post by chessnerd on 2010-05-22
> **Legendary_Bibo said:**
> Oh that's it, I thought I had to contact the supreme court or something to get a license approved or something. I didn't realize that's all it took.

Whenever you create anything, you immediately gain ownership over its distribution under US Copyright Law.

[QUOTE=http://www.copyright.gov/help/faq/faq-general.html]When is my work protected?

Your work is under copyright protection the moment it is created and fixed in a tangible form that it is perceptible either directly or with the aid of a machine or device.[/QUOTE]

If you want to give away some of those rights, that's up to you. Copyright law makes licensing easy. 

Side note: copyright law is required in order to make copyleft work. Irony?

---

### Post by w0Rm210 on 2010-05-22
> **chessnerd said:**
> Whenever you create anything, you immediately gain ownership over its distribution under US Copyright Law.



If you want to give away some of those rights, that's up to you. Copyright law makes licensing easy. 

Side note: copyright law is required in order to make copyleft work. Irony?

I was under the understanding that the whole "open source software" thing was dropping the copyright for a small amount of your code so people can make the program better from the source... Guess i'm wrong though huh?

---

### Post by lisati on 2010-05-22
> **w0Rm210 said:**
> I was under the understanding that the whole "open source software" thing was dropping the copyright for a small amount of your code so people can make the program better from the source... Guess i'm wrong though huh?

Please use the default font colour unless you're highlighting something.

---

### Post by chessnerd on 2010-05-22
> **w0Rm210 said:**
> I was under the understanding that the whole "open source software" thing was dropping the copyright for a small amount of your code so people can make the program better from the source... Guess i'm wrong though huh?

In a way, it is, but most people don't fully drop their copyright (which would mean that they put the work in the public domain)

The idea of copyright is that the copyright holder has the exclusive rights to copy and distribute their work. 

The idea of open-source software is that others can see, modify, and improve on your code. 

The two ideas are not incompatible and some projects actually are "open-source" but still have a traditional copyright. What this means is that others can see the source code, but they aren't allowed to use the code without permission. (Sort of like how you can read a book but you can't copy it and try to sell it)

For things that are "copyleft" the copyright holder has decided that people have the right to see, modify, and improve on the code, but if you do, you must release your modifications under the same license. It is using copyright to force people to allow their work to be copied. It turns copyright upside down (hence, copy-LEFT rather than copy-RIGHT), but copyleft licenses need copyright law in order to function because they are controlling what people do with their creations (which is what copyright does).

---

### Post by Eisenwinter on 2010-05-22
I code in Perl, and find myself not really doing "big" projects.

I use it pretty much just for system administration tasks (file manipulation, scanning directories and doing things with the results, and so forth), and sometimes I toy around with bigger things that aren't sysadmin-centered at all.

It can be fun.

---

### Post by w0Rm210 on 2010-05-22
@[chessnerd]("http://ubuntuforums.org/member.php?u=804379")

That makes a lot more sense thanks :)

---

### Post by Legendary_Bibo on 2010-05-22
What if I do the most absurd thing and not put any sort of license in it? Do only weird people do that? I mean I want to try pulling off a version 0.1 of an installer by the end of the summer to get more people into the project, and I mean it would only be useful for linux so would I have to worry about copyright issues?

---

