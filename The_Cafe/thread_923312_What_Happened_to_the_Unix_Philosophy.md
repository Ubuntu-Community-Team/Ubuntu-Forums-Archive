---
title: "What Happened to the Unix Philosophy?"
date: 2008-09-18
forum: The Cafe
---

### Post by richard42 on 2008-09-18
According to Doug McIlroy the [Unix Philosophy]("http://en.wikipedia.org/wiki/Unix_philosophy") is:

> "Write programs that do one thing and do it well.
Write programs to work together.
Write programs to handle text streams, because that is a universal interface."

So what went wrong?

For example, web browsing.  The tool that I use to browse the internet is Firefox.  It's great for browsing, so it fulfils the first criteria of the Unix Philosophy.  FF handles cookies, javascript, SSL, bookmarks, history etc.  But it fails at the second two hurdles:  FF doesn't work well with other programs and I can't extract information from FF as a text stream.

For example, I'd like to be able to do something like this:

```
ff = firefox.start(visible = false)
ff.go("http://google.com")
ff.type("test search")
ff.click("Google Search")
print ff.body # prints the body of the webpage
ff.close()
```

But you can't do this.  In order to script FF you need to use a complicated javascript injection system such as [selenium]("http://selenium.openqa.org/") or an internal macro system like [Greasemonkey]("https://addons.mozilla.org/firefox/addon/748"), [Chickenfoot]("http://groups.csail.mit.edu/uid/chickenfoot/") or [iMacros]("https://addons.mozilla.org/en-US/firefox/addon/3863").  There's no easy way for another program to get the information from FF that you can so easily get yourself manually using it.

Alternatively, I could avoid FF and opt for a command line program such as [Curl]("http://curl.haxx.se/") or a library such as perl's [mechanize]("http://search.cpan.org/dist/WWW-Mechanize/").  Or I can look at console web browsers like [elinks]("http://elinks.or.cz/").  But as soon as I do this, I lose all the useful things that Firefox provides, such as handling cookies, javascript and SSL etc.  In any event, I don't want to have to use two different tools:  one for my day-to-day work and a different one for scripting.  I want the same tool to work in both contexts.

The same is also true of email:  Gmail does email well -- it fulfils the first criteria of the Unix philosophy.  That's why I use it.  But it fails on the second two.  I can't easily access my email from another program.  There are libraries to access gmail, but they are not feature-rich and they are always fighting against Google.  Google changes the gmail interface, and the libraries have to try to update themselves to continue to work.  I want a tool that does email well, but is scriptable and works with other programs.

Same with Office:  I want to be able to read and create documents in a way that can work with other programs.  For example, I want the contact details that my email client uses to be available to my office package when I am populating a mail merge.  Why is it so difficult to have one address book that will work for your email, office applications and mobile phone?  We should have solved this after 60+ years of computing!

Pulling this together:  Let me give an example of a program that would pull all this together.  I want to be able to write a script that gets some data from a webpage, mailmerges it into a document or spreadsheet and emails it to a certain address.  I want to be able to set this up with a cron job.  I want the email to be in my 'sent items' in my usual email client.  Why is this so difficult accomplish?

I feel endlessly frustrated that I can't find an operating system that adheres to the full Unix Philosophy.  I want my OS to have programs that not only provide their functions well (web browsing, emailing, office functions etc), but I also want these programs to work together well.

Can anyone help?

Richard

---

### Post by Trail on 2008-09-18
Well said.

I guess multiplatform is not always so good, eh...

---

### Post by pp. on 2008-09-18
Firefox, for one, is not a unix program. But then, it has been designed to let a user browse the web with a GUI as the primary User Interface. It does that well. Lastly, all the data processed by the browser (the http data stream, the HTML documents and the scripts) are simple text streams completely composed of printable characters and whitespace.

So, even if it has not been designed as a Unix program, it complies with the first and third wish. Whether it cooperates well with other programs or not I can not say. 

If you want to process the data which Firefox (or any other browser) processes, you'd best work with the source. I.e. if you want a program which extracts data from - say - the Ubuntu forums, fetch the text from Ubuntu forums and not from a program which has the only purpose of showing that text on the screen.

The story goes on. If you want to work with addresses, use a program design to keep addresses, not one designed to use addresses in order to send mails.

The examples you mention are not cases of the Unix philosophy being ignored by some pieces of software but rather cases of your trying to use software for something it was never meant to do.

You can use a bicycle to plow a field or to throw a javelin, but the result is bound to be a bit disappointing.

---

### Post by ukripper on 2008-09-18
> **pp. said:**
> Firefox, for one, is not a unix program. .

That answers it all! 

Sums up - The firefox philosphy is not directly proportional to the unix philosphy, just like tomatoes ain't potatoes!:)

---

### Post by Half-Left on 2008-09-18
Firefox has never been Unix, it's a crossplatform app, made to work with all OS's. It's only had a proper native toolkit since 3.0.

---

### Post by awakatanka on 2008-09-18
Try kde

---

### Post by ukripper on 2008-09-18
> **awakatanka said:**
> Try kde

kde 3.5 is good, 

4.1 is the worst DE i have ever seen.

---

### Post by richard42 on 2008-09-18
Thank you all for your replies.  I suppose my question should have been:  In terms of varied common programs working together, what's the modern GUI equivalent of the original set of Unix console tools?

I'll check out KDE.

Richard

---

### Post by DHag on 2008-09-18
For that matter, NONE of the examples you listed (Firefox, GMail, Office) are UNIX programs.

---

### Post by richard42 on 2008-09-18
> **DHag said:**
> For that matter, NONE of the examples you listed (Firefox, GMail, Office) are UNIX programs.

Conceded.

---

### Post by ukripper on 2008-09-18
> **richard42 said:**
> Thank you all for your replies.  I suppose my question should have been:  In terms of varied common programs working together, what's the modern GUI equivalent of the original set of Unix console tools?

I'll check out KDE.

Richard

Console can't be replaced! Command line is the power which makes you the lord of the *nixes.

---

### Post by richard42 on 2008-09-18
> **ukripper said:**
> Console can't be replaced! Command line is the power which makes you the lord of the *nixes.

I'd happily live at the command line, but I can't get it to do everything that I want!  Do you use console tools for web browsing and email?  If not, why not?

---

### Post by ukripper on 2008-09-19
> **richard42 said:**
> I'd happily live at the command line, but I can't get it to do everything that I want!  Do you use console tools for web browsing and email?  If not, why not?

i do use lynx web browser using command line for text browsing. For online videos, you can only use GUI based web browser. For email mutt is the best cli based mail client i 've ever used [http://www.mutt.org/#features](http://www.mutt.org/#features) and got many shell scripts running which uploads to gmail account and download my uploaded files very easily. GUI only provides entertainment for me, but cli gives me productivity.

---

### Post by qazwsx on 2008-09-19
> **ukripper said:**
> i do use lynx web browser using command line for text browsing. For online videos, you can only use GUI based web browser.

There are  loads of scripts for extracting video content. I hate embedded videos. So I have couple of site specific scripts to watch videos with mplayer :) :lolflag:

---

### Post by ukripper on 2008-09-19
> **qazwsx said:**
> There are  loads of scripts for extracting video content. I hate embedded videos. So I have couple of site specific scripts to watch videos with mplayer :) :lolflag:

Agreed! But not worth extracting all videos.

---

