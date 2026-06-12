---
title: "Anyone using bluefrog ???"
date: 2006-05-07
forum: The Cafe
---

### Post by towner on 2006-05-07
Hi all

Just been browsing digg and came across bluefrog by bluesecurity.com
I've been clocking up bucket full of spam in my gmail account recently and wanted to start giving the spammers a bit of their own medicine.

Does anyone out there use bluefrog ? I'm having trouble compiling the source.
Does it work ?

Cheers

---

### Post by DigitalDuality on 2006-05-07
I have been keeping up with the digg thread.  QUite interesting.  I did a summary of it all in my blog (see link).

I'm on fedora and i can't get bluefrog installed.  Couldn't get VLC 0.8.5 installed earlier today either.  Don't know what i'm doing wrong in either case.

---

### Post by towner on 2006-05-07
Thanks for the link to your blog. I'll check it out soon.
I've sent the bluefrog developers a mail, and hopefully they'll give me a solution.
When it comes !! I'll post on this thread
Cheers

---

### Post by DigitalDuality on 2006-05-09
Got the software installed on ubuntu dapper but i can only access it through the command line and i can't get my account to sign in.  The plugins for both Firefox and Flock seems to be doing ok.

This is how you get it installed though

sudo apt-get install alien

then download the bluefrog rpm (just released last night)

[http://prdownloads.sourceforge.net/bluefrog/bluefrog-1.9.1.1151-0.fc3.i386.rpm?download](http://prdownloads.sourceforge.net/bluefrog/bluefrog-1.9.1.1151-0.fc3.i386.rpm?download)

place the file in your home folder.  Then type this:

sudo alien bluefrog-1.9.1.1151-0.fc3.i386.rpm

This will create a bluefrog deb file.

Then sudo dpkg -i bluefrog-1.9.1.1151-0.fc3.i386.deb

---

### Post by towner on 2006-05-11
Hi all

Just got a mail back from bluesecurity (makers of bluefrog) with a link to the latest release [here]("http://sourceforge.net/project/showfiles.php?group_id=153754"), which I've been told contains fixes to the problems encountered.

I'm going to try again now

---

### Post by bionnaki on 2006-05-11
whats bluefrog?

---

### Post by DigitalDuality on 2006-05-11
[www.bluesecurity.com](www.bluesecurity.com) explains it.

Basically you submit your spam to it and they send opt-out requests to the address that spammed you.

So lets say, ... 100,000 bluefrog members got spam for the same source, well that source gets 100,000 opt-out messages requestion they clear their spam lists.

It's basically "fighting back" rather than filtering it out.

---

