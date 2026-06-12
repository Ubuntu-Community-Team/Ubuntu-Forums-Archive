---
title: "Guitar Songbook for church  - LaTex?"
date: 2006-10-06
forum: Ubuntu Christian Edition
---

### Post by _axiom_ on 2006-10-06
I need to create a song book for my church.  It need to show the cords in my version, and just have the word for the congregation.

I have found this: [http://www.rath.ca/Misc/Songbook/](http://www.rath.ca/Misc/Songbook/)  which I may use, but LataX seems unnecessarily completed to me.  (I think that is because it is so old, and there are so many different instructions online, which either don't apply anymore, or are mutually exclusive.)

I would like something more specific, like opensong, but I don't have one of those fancy projectors.

I already have most of these song it plain text, and have been think about writing a script to convert them to the LaTeX markup, but before I do that I thought I would ask if anyone else had tried something similar.

(Note: I am not trying to typeset music with all the note.  Just chords, C, G, F, etc.)

---

### Post by Peturrr on 2006-10-07
I think you need to search for chordpro tools. Chordpro is a standard for lyrics with chords notation. 

There are a few programs available that use it. A good free Java one is SongSheetGenerator: [http://www.tenbyten.com/software/songsgen/](http://www.tenbyten.com/software/songsgen/)

At our student union we use the chordpro format to create a songbook. Because chordpro is a standard we have created a online websystem that can generate a PDF of a song, transpose songs, etc. etc.

An example of a chordpro song:

```

[A]This is [C]a [Dm]beautiful songline.

```Result after conversion with software like the one mentioned above:
```

[FONT=Fixedsys]A         C Dm
This is a beautiful songline
[/FONT]
```

As you see it makes it very easy to create songs with chords in a way that you do not have to worry about the position of the chords. Gone are the days modifying spaces to fit the chords in a text editor :).


[FONT=Fixedsys] [/FONT]

---

### Post by mjpatey on 2006-10-15
Nice!  This is great!  I'll be downloading that piece of software when I get home to my Ubuntu machine.  I've been typing songs and chords in the old-fashioned way forever.

---

### Post by IYY on 2006-10-15
You don't have to code in pure LaTeX. There is a program, for example, that converts chordpro to LaTeX (chopro2latex). Then if you get that package, you'll be able to have a nice songbook. There is also a module for Lyx (a graphical editor for LaTeX) on the page you linked to, so that can make things easier.

---

### Post by hamlen on 2009-02-18
You might also want to check out a newer LaTeX package called "songs":

[http://songs.sourceforge.net](http://songs.sourceforge.net)

It's designed to be easily usable by LaTeX novices, has downloadable self-installers for Windows, and step-by-step tutorials are on the website.  Song entry is very similar to chordpro; basically you just write "\[A]" instead of "[A]".  It also does projector slides (digital or overhead), guitar tablature diagrams, automatic transposition, scripture indexes, and lots of other stuff.

---

