---
title: "Ebooks and what to do..."
date: 2007-03-23
forum: The Cafe
---

### Post by jazzman83 on 2007-03-23
Hi, I have a couple hundred ebooks in .txt format and I have no clue what to do with them to encourage me to give up the paperback and start using them.  

I downloaded FBReader which I like but I am discouraged by the lack of formatting in the txt files.  I was wondering if anyone has tips on what format would be best to use and what program would be best to convert to it.  For example, I have no clue how to convert to OpenReader format.

---

### Post by futz on 2007-03-23
> **jazzman83 said:**
> Hi, I have a couple hundred ebooks in .txt format and I have no clue what to do with them to encourage me to give up the paperback and start using them.  

I downloaded FBReader which I like but I am discouraged by the lack of formatting in the txt files.  I was wondering if anyone has tips on what format would be best to use and what program would be best to convert to it.  For example, I have no clue how to convert to OpenReader format.
I have somewhere between 40000 and 60000 e-books, in all formats - txt, html, pdf, lit, pdb and others. There is no one reader that works for them all, unfortunately. I hadn't heard of OpenReader format. Thanks for the tip.

I really like microsoft's lit format, but there is no linux reader for that, and I haven't been able to get the ms reader to work with wine. You can use c-lit to clumsily convert lit files to html, but it's not a great solution.

Converting from text to something with formatting without adding the formatting manually is impossible, unless you write a very smart program to do it for you. I mean, you can convert it, but that doesn't automatically add formatting. A program could do an ok job, I think, but a human proofreader would very likely still be necessary to clean up the things the program got wrong.

I just read em, and ignore the bad formatting and errors.

One day I want a dedicated reader machine - maybe a PDA - so I can read in bed. It needs a timer so it shuts itself off when I doze off. 

I'm just in the process of setting up a spare machine in the bedroom with monitor on its side for before-sleep reading. I'll use 'shutdown -h XX' to turn it off after a certain amount of elapsed time. I kinda suspect this experiment will be a failure, but I gotta try something.

---

### Post by IYY on 2007-03-23
You might want to consider formatting these text files with LaTeX to create nice looking PDFs. You do it like this:

First, install LaTeX: 

```
sudo apt-get install tetex-base tetex-extra
```

Open the book in a text editor, and add the following lines at the top:

```
\documentclass{book}
\title{The Title of My Book}
\author{The Author of My Book}

\begin{document}
\maketitle

```

at the very bottom, add:

```
\end{document}
```

Wherever a new chapter begins, use the following command:

```
\chapter{Chapter Name}
```

If there are any sections or subsections (if it's a technical book, for example), use

```
\section{Section Name}

```
and

```
\subsection{Subsection Name}
```

Save your edited book as, for example, mybook.tex and then run the following command:

pdflatex mybook.tex

If there have been no errors, you should now have a book called mybook.pdf, with nice formatting , page numbers, a title page and everything else you might expect to find in a book. To add a table of contents, add the line

```
\tableofcontents
```

right after the \maketitle command. You will need to run pdflatex twice: once to generate the table of contents, and once to generate the complete document.

It might sound difficult, but it really is a very simple process and your books will look great!

Here's my blog on the subject, with a sample PDF output:

[http://yakubovich.blogspot.com/2006/11/latex-for-nontechnical-user.html](http://yakubovich.blogspot.com/2006/11/latex-for-nontechnical-user.html)

LaTeX automatically fits the correct number of words per lines (even word processors don't generally do this effectively), uses a good-looking style for the headings, numbers the pages, leaves blank pages where appropriate (ends of chapters where needed), automatically generates a table of contents, properly indents paragraphs (provided that the original document has a blank line to represent a paragraph break, as most of them do), etc.

NOTE: if your books have "quotations" in them, they might look inverted in the output, because LaTeX expects quotations to look ``like this'' and not "like this". I can send you a little program I wrote to make the conversion.

---

### Post by banjobacon on 2007-03-23
> **IYY said:**
> It might sound difficult, but it really is a very simple process and your books will look great!

Seems like it this would be a huge pain in the [butt] to do to a few hundred text files.

I recently came across this tool for formatting the ebooks provided by Project Gutenberg:  [GutenMark](http://www.sandroid.org/GutenMark/). It's supposed to work automatically, requiring no manual editing. Maybe it'll work on your ebooks, or can be modified to do so.

I haven't used GutenMark, though.

---

### Post by Mateo on 2007-03-23
latex is definitely the "best" solution.  only the adding chapter tags will be a little time consuming.

only thing is I don't think Evince has bookmarks, i'll have to look.

---

### Post by Mateo on 2007-03-23
by the way, if you do what IYY suggests, get texlive, not tetex.  Tetex is old I believe no longer in development.

---

### Post by futz on 2007-03-24
> **banjobacon said:**
> I recently came across this tool for formatting the ebooks provided by Project Gutenberg:  [GutenMark](http://www.sandroid.org/GutenMark/). It's supposed to work automatically, requiring no manual editing. Maybe it'll work on your ebooks, or can be modified to do so.
I grabbed GutenMark and compiled it, but it won't run without errors. So I grabbed the pre-compiled executable, and that won't run without different errors. :mrgreen:

It's strictly command-line, so typing in LONG book names with spaces in them is always going to be a pain. To be sure I wasn't messing up the filenames I renamed one book to 'input.txt' and was outputting to 'output.html', just to make things easy and goof-proof.

Got 'stack smashing' errors with my compiled version, and 'segmentation fault' with the pre-compiled one.

With a nice gui front end and no weird bugs, this might be a pretty useful program...

---

### Post by jazzman83 on 2007-03-24
Wow, thanks for all the great suggestions and ideas.  I guess I'm not the only one piddling about with ebooks

...I kind of thought this thread would get no responses and die away into forum eternity...

I thought of Latex but was hoping to use my FBReader program which has a really neat library function but doesn't read .pdf

I'll go and look at this Gutenmark program and see what it's about.

---

### Post by Mateo on 2007-03-24
> **futz said:**
> I grabbed GutenMark and compiled it, but it won't run without errors. So I grabbed the pre-compiled executable, and that won't run without different errors. :mrgreen:

It's strictly command-line, so typing in LONG book names with spaces in them is always going to be a pain. To be sure I wasn't messing up the filenames I renamed one book to 'input.txt' and was outputting to 'output.html', just to make things easy and goof-proof.

Got 'stack smashing' errors with my compiled version, and 'segmentation fault' with the pre-compiled one.

With a nice gui front end and no weird bugs, this might be a pretty useful program...

i used to have that problem with long filenames, but you can just type the first few letters and then press TAB and it'll usually get the rest.  try that to save time.

i'll give the problem a run through myself.

---

### Post by IYY on 2007-03-24
You can't expect a program to be able to automatically determine where chapters begin and end in an ASCII file, because there is no standard. 
```

--- This Could be a Chapter ---
```

and

```
This Could be a Chapter
```

and
```

Chapter 3: This could be a chapter

```

If you are comfortable with scripting, you could write a script that will automatically do the conversions, otherwise... How many chapters does a book have, really? It's not *that* much work, and the result looks great.

---

### Post by Mateo on 2007-03-24
yeah, chapters is the only difficult part with latex.  With gedit you can use the find feature (search for 'chapter').  If the word 'chapter' isn't in the title, then look at the chapter names in the table of contents.  If it doesn't have a TOC, then it *does* become a bit of a pain to find them all.

Granted, you don't have to mark the chapters, it just winds up looking better.

---

### Post by jazzman83 on 2007-03-25
I have been playing around with LaTeX and my txt etexts and so far they come out quite good.  I don't use the book format in documentclass as you suggested because it doesn't come out quite good for reading on the computer to me.  I am using article format instead and I like it much better.  If I was going to print these book than maybe book format would be better but I don't like all the empty pages and how the text is off-centered.

You're right about the pain with Chapter designation but using gedit's find/replace tool makes it go quite quick and now I'm thinking of writing a quick C program which will add a '}' at the end of every line which I put a /section*{ into.

---

### Post by Mateo on 2007-03-25
the book class is slightly off center because in a book the left pages should be slightly to the left and the right pages slightly to the right, to compensate for the spine.

---

### Post by jazzman83 on 2007-03-25
haha, I realize that but I will not be binding these books.  I'd rather spend the couple bucks it would cost to buy these classics from Penguin :)

---

### Post by Mateo on 2007-03-25
the book class might also use smaller paper size, which would result in more pages. I think it's easier to read like that.  just me though.

---

### Post by IYY on 2007-03-25
> You're right about the pain with Chapter designation but using gedit's find/replace tool makes it go quite quick and now I'm thinking of writing a quick C program which will add a '}' at the end of every line which I put a /section*{ into.

This is better done with a script. Can be a one-liner.

---

### Post by Mateo on 2007-03-25
or you could just use the latex plugin for gedit, which allows you to highlight the chapter name and then press a button which wraps the \chapter{} around it (works for part, section, subsection, etc too).

---

### Post by Takmadeus on 2007-03-25
I recommend you use LyX instead of Latex (although they are related) IMO LyX is better suited for those tasks and has a somewhat intuitive interface... and by using LaTeX as a backend, the reults are just amazing.... I have used LyX to edit a lot of my .txt books and it is not that hard.... 

it is in the repos, which is a plus! ;)

---

### Post by jazzman83 on 2007-03-27
> **IYY said:**
> This is better done with a script. Can be a one-liner.

Would you be able to elaborate upon this.  I have no experience with Linux scripting and don't even know where to begin.  Would it be done in python?

---

### Post by IYY on 2007-03-27
> **jazzman83 said:**
> Would you be able to elaborate upon this.  I have no experience with Linux scripting and don't even know where to begin.  Would it be done in python?

Even python is overkill here. Assuming that I understand your goal correctly, this should do it:

```
sed 's/\\section.*/&}/g' somefile.tex
```

What it says is, "Substitute the string starting with \section with that same string with } in the end.

---

### Post by jazzman83 on 2007-03-27
Awesome, thanks.  Is this what you call Bash scripting?  Would you also have any links on learning to script like this - such as teaching syntax etc...

I noticed however that the script works on small test.txt files that I make but when used on really long etexts it changes the leading '\' to '}' from the \section{ lines and doesn't add it do the end.  For instance,

*\section{blah*     will become    *}section{blah*

---

### Post by IYY on 2007-03-27
Well, this is sed, not bash, but when people say they are writing a bash script they usually mean they can include sed or awk one-liners. There are plenty of good sed tutorials online, and also at the Linux Documentation Project.

Can you send me a sample file on which it doesn't work?

---

### Post by IYY on 2007-03-29
Ok, I got the reason. The e-book you sent me is a Windows (DOS) ASCII file, not a Unix ASCII file. Editors like gEdit don't mention anything about this, but when I opened it in vi I immediately figured out the problem:

```
^M
\section*{Chapter 1:  Out to Sea^M
^M
^M
I had this story from one who had no business to tell it to^M
me, or to any other.  I may credit the seductive influence^M
of an old vintage upon the narrator for the beginning of it,^M
and my own skeptical incredulity during the days that followed^M
for the balance of the strange tale.^M
^M

```

DOS files have these extra newline characters (^M). When you run it through the sed script I gave you, the operation is done correctly and your section line becomes:

```
\section*{Chapter 1:  Out to Sea^M}
```

However, ^M is a newline character, so it really is,

```
\section*{Chapter 1:  Out to Sea
}
```

Which probably causes the problems. 

To fix this, you will need to convert the file to UNIX ASCII type. Download a program called 'flip' from the repositories, and then to convert to UNIX ASCII:

```
flip -u filename.txt
```

---

