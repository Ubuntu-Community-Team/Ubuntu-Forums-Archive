---
title: "Scripture Memorisation"
date: 2009-09-22
forum: Ubuntu Christian Edition
---

### Post by benthorp on 2009-09-22
Does anybody know of any scripture memorisation software? ie it displays a verse for you to learn, and then tests you on it over time, with missing words, etc? I had a hunt around but couldn't really find anything for Linux that appeared to match what I want...

If it doesn't exist, then I plan to write it, but I figured it would be easier to check first ;)

---

### Post by TuckLive on 2009-09-22
I haven't used this app, but have a look at this.

[http://www.crosswire.org/flashcards/]("http://www.crosswire.org/flashcards/")

---

### Post by benthorp on 2009-09-22
Hmmm - it's pretty good, apart from the fact that all the lessons installed by default are on Greek and Hebrew ;) I'll look further and see if it is able to do what I want. 

Thanks

---

### Post by jonathonblake on 2009-09-22
> **benthorp said:**
> Does anybody know of any scripture memorisation software? 

BibleMemorizer   ([http://sourceforge.net/projects/biblememorizer/files/](http://sourceforge.net/projects/biblememorizer/files/) ) which I haven't used.  Cross-platform GNU GPL & MIT License.

e-Sword has a Scripture Verse Memorization component.

jonathon

---

### Post by benthorp on 2009-09-24
> **jonathonblake said:**
> BibleMemorizer   ([http://sourceforge.net/projects/biblememorizer/files/](http://sourceforge.net/projects/biblememorizer/files/) ) which I haven't used.  Cross-platform GNU GPL & MIT License.

e-Sword has a Scripture Verse Memorization component.

jonathon

I took a look at BibleMemorizer - it was OK, but it's idea of a quiz was for you to type in the whole verse when given the reference - there was no sense of it trying to teach you the verse over time. 

What do people think - is this something that is needed, or is it just too niche?

---

### Post by TuckLive on 2009-09-24
It's needed.  If your a developer I'm sure individuals and Churches could use what your looking for.

---

### Post by benthorp on 2009-09-25
OK-dokey. I'm on it :)

---

### Post by TuckLive on 2009-09-25
Awesome.  Send us a link when you get something going.

---

### Post by benthorp on 2009-09-28
OK - I've made a basic commandline start, which you can play with to your hearts desire.

The main program file is at [http://dl.getdropbox.com/u/2023639/pymemoryverse.py](http://dl.getdropbox.com/u/2023639/pymemoryverse.py) and the verses file is at [http://dl.getdropbox.com/u/2023639/verses.csv](http://dl.getdropbox.com/u/2023639/verses.csv) (I know - I should probably be using Ubuntu One). 

Notes:

1. Requires diatheke to be installed, otherwise it will end badly.
2. There is no error correction - this is a proof of concept.
3. "Learn" mode just tells you the verse
4. "Guess" mode has 3 levels of difficulty. Level 1 removes 3 words, level 2 removes 6 words, and level 3 removes every third word. 
5. Punctuation can be a bit funny - I'm working on it ;)
6. If you want to put in a verse you can (eg python pymemoryverse.py 1 John 3:16 )

Plans for the main version:

1. It'll be a GUI - glade/pygtk is my friend ;)
2. I plan to have 3 tabs, one for entering new verses (either by hand or pulling from diatheke/sword), one for "learn mode" which will try and get you to learn an individual verse by gradually removing the words over time, and "quiz" mode which will test you on verses you have learned.
3. The plan is for verses to be allocated to a calendar, so that you learn verses over time - probably aiming at 1 verse to learn every X days, default 7. 
4. It will initially come with the 100 verses in my verses file, which I culled from a website somewhere for the 100 best verses to learn ;)
5. I think quiz mode will probably offer different quizzes - eg. ask for the reference when given the verse, ask for words from the verse with a multiple choice - that kind of thing.

I'm open to suggestions at this point (ideally before I begin the major coding ;) ).

---

### Post by benthorp on 2009-09-28
Oh, and while I'm at it, a couple of things I thought of:

1. A panel applet of some sort that offers reminders through the day of the verse you're learning.
2. An option to customise the quiz offerings (rather than just random words), ie you'll be able to indicate which words are hidden in which words, and alternative words that could be offered to the user.

---

### Post by benthorp on 2009-10-01
Brief status update: I've made good progress so far - the Add/Edit tab is up and running; I'm just beginning work on the Learning tab. At this rate I hope to have a basic alpha release at some point in the next 7-10 days \o/

---

### Post by benthorp on 2009-10-05
Another status update: The learning tab is about 90% complete. All things being equal, I hope to get that up to 100% tomorrow, and I'll release an alpha version without the quiz tab. Testers will be welcome ;)

---

### Post by benthorp on 2009-10-08
OK - version 0.01 of the newly named "Whetstone" is out.

[http://www.jedimoose.org/whetstone](http://www.jedimoose.org/whetstone)

---

### Post by cmckdub on 2009-10-12
> **benthorp said:**
> OK - version 0.01 of the newly named "Whetstone" is out.

[http://www.jedimoose.org/whetstone](http://www.jedimoose.org/whetstone)

Thanks for the work you have done. I have been using Biblememorizer and e-sword scripture memory tool for quite a while. It sounds like what you are doing has a few things in common with the scripture memory tool in e-sword, with the improvement of controling the learning style more. That's great. 
I have not been able to get it to work, and I think it is because I cannot get pysqlite2. It does not seem to be in the repositories. 
I would like to keep testing.

---

### Post by benthorp on 2009-10-13
> **cmckdub said:**
> I have not been able to get it to work, and I think it is because I cannot get pysqlite2. It does not seem to be in the repositories. 
I would like to keep testing.

The package you're looking for is called **python-pysqlite2** and should be in the standard Ubuntu repositories: [http://packages.ubuntu.com/jaunty/python-pysqlite2](http://packages.ubuntu.com/jaunty/python-pysqlite2)

---

### Post by cmckdub on 2009-10-13
Thanks Benthorp.
Your application has lots of interesting features for memorising the Bible. That is great.
2 problems I am having...
1. When I had added a few verses into a new category, it stopped allowing me to add more. The add button had become and update button, as the attached screen shot shows (whetstone-addv).
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131835&d=1255470207[/IMG]
2. When I am in the Learn tab, the attached screenshot (whetstone-learn-cal) shows the calendar, and some attempts at planners, but I do not seem to be able to make it test the new category I have created. 
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=131836&d=1255470207[/IMG]
I wonder what I am doing wrong.
Thanks again for your great work Benthorp.

---

### Post by benthorp on 2009-10-14
> **cmckdub said:**
> 
1. When I had added a few verses into a new category, it stopped allowing me to add more. The add button had become and update button,

The Add button becomes an Update button when it thinks that you're editing an existing verse. Try using the clear button to clear the form (and should return the button to an Add state) and then adding the verse again. 

> 2. When I am in the Learn tab, the attached screenshot (whetstone-learn-cal) shows the calendar, and some attempts at planners, but I do not seem to be able to make it test the new category I have created. 

Hmmm - not sure about this one. I'll take a look and see if I can replicate the problem. Try and restart the application and see if that makes a difference (just in case the planner section is not updating it's list of categories properly from the DB).

---

### Post by benthorp on 2009-10-14
[quote=benthorp]Hmmm - not sure about this one. I'll take a look and see if I can replicate the problem. Try and restart the application and see if that makes a difference (just in case the planner section is not updating it's list of categories properly from the DB).[/quote]

There do appear to be a couple of problems with the initial planner creation and loading of the verses - I'll see if I can iron out these bugs for the 0.02 release, which I'm hoping to get out in the next week or so.

---

### Post by stlsaint on 2009-10-15
nice program from what i can see and since its python im already happy for it!! i will be looking forward to a more stable release...

---

### Post by Dragonbite on 2009-10-15
Looks interesting.

---

### Post by benthorp on 2009-10-16
OK - development of version 0.02 is moving on apace, although it's not quite ready for release yet.

I've got a few fixes in there from the problems noted in 0.01, but the big new item is the inclusion of quizzes. The plan is to offer 3 quizzes initially - guess the verse from the reference, guess the reference from the verse, and guess the missing word(s). These will all be multiple choice, and the questions will either be based on selected categories, or on a particular planner that you have, so you will be able to test yourself on all the verses that you should be learning according to your planner.

I have got the multiple choice window working (although it's a little bit funny in the layout - need to sort out how to deal with ultra-long radiobutton labels) and the verse and reference quizzes working for categories. Should hopefully get the word quiz and quizzes based on planners up and running pretty quickly - aiming for a mid-week release next week. 

Please do let me know if you have more suggestions (or bug reports).

---

### Post by benthorp on 2009-10-19
Monday update: 

0.02 should be out tomorrow, all things being equal. In this update:

 - Fixed some of the above mentioned bugs
 - Implemented multiple choice quizzes:
      * Can choose between categories or your learning planner
      * Can choose how many verses from your planner you want quizzed on
      * Can either guess verse text from a given reference, or reference from a given verse

Still to come in 0.03
 - Probably a load more bug fixing ;)
 - Missing word multiple choice quiz
 - Guess the whole verse quiz
 - Separate Gnome panel applet that will pop up an appropriately distorted memory verse based on your selected planner at a random interval during the day to help you learn

---

### Post by benthorp on 2009-10-20
OK - version 0.0.2 is out!

Get it from [here](http://mrben.jedimoose.org/whetstone-0.0.2.tar.gz).

Full details, as before, at [http://www.jedimoose.org/whetstone](http://www.jedimoose.org/whetstone/)

I'm on the lookout for a nice logo, if any of you are that way inclined ;)

---

### Post by saxasm on 2009-10-20
> **benthorp said:**
> OK - version 0.0.2 is out!

Get it from [here](http://mrben.jedimoose.org/whetstone-0.0.2.tar.gz).

Full details, as before, at [http://www.jedimoose.org/whetstone](http://www.jedimoose.org/whetstone/)

I'm on the lookout for a nice logo, if any of you are that way inclined ;)

[IMG]http://img7.imageshack.us/img7/2884/whetstone.gif[/IMG]

Is that a good one?

If anyone is interested I'll say how I made it.

---

### Post by benthorp on 2009-10-20
It's a good start, although I'm really looking for something visual rather than the word itself.

I was thinking of doing something like an image of a sword being sharpened on a stone, and the sword having a cross motif of some sort. Or maybe a verse etched into the blade.

---

### Post by saxasm on 2009-10-20
> **benthorp said:**
> OK - version 0.0.2 is out!

Get it from [here](http://mrben.jedimoose.org/whetstone-0.0.2.tar.gz).

Full details, as before, at [http://www.jedimoose.org/whetstone](http://www.jedimoose.org/whetstone/)

I'm on the lookout for a nice logo, if any of you are that way inclined ;)

[IMG]http://img35.imageshack.us/img35/2884/whetstone.gif[/IMG]

Alternative one, a bit more colour. Blended the plasma I used to create the "metal" onto the metal. Gives it a petroleum-like shine.

---

### Post by saxasm on 2009-10-20
> **benthorp said:**
> It's a good start, although I'm really looking for something visual rather than the word itself.

I was thinking of doing something like an image of a sword being sharpened on a stone, and the sword having a cross motif of some sort. Or maybe a verse etched into the blade.

Hmm, ok.

I made this one too, I will try to make some more alternatives.

[IMG]http://img30.imageshack.us/img30/2884/whetstone.gif[/IMG]

---

### Post by saxasm on 2009-10-20
> **benthorp said:**
> It's a good start, although I'm really looking for something visual rather than the word itself.

I was thinking of doing something like an image of a sword being sharpened on a stone, and the sword having a cross motif of some sort. Or maybe a verse etched into the blade.

[IMG]http://img260.imageshack.us/img260/2884/whetstone.gif[/IMG]
Still mainly text, but I'll add a sword too, or make the cross look like a cross-sword blend.

---

### Post by saxasm on 2009-10-20
> **saxasm said:**
> [IMG]http://img260.imageshack.us/img260/2884/whetstone.gif[/IMG]
Still mainly text, but I'll add a sword too, or make the cross look like a cross-sword blend.

[IMG]http://img25.imageshack.us/img25/2884/whetstone.gif[/IMG]
Added a sword. What do you think?

It looks better like this, I think:
[IMG]http://img132.imageshack.us/img132/2884/whetstone.gif[/IMG]

---

### Post by Dragonbite on 2009-10-20
> **saxasm said:**
> Hmm, ok.

I made this one too, I will try to make some more alternatives.

[IMG]http://img30.imageshack.us/img30/2884/whetstone.gif[/IMG]

I like this one better, but what about replacing the "t" with a cross-image, maybe in weathered wood?  Not too much, just enough for it to stand out "slightly".

Could even mix the colors so it uses the brown for the "t" and a mixure of Ubuntu colors for the rest (mustart yellow, brown**s**, orange or dirty red, etc.)?

---

### Post by saxasm on 2009-10-20
> **Dragonbite said:**
> I like this one better, but what about replacing the "t" with a cross-image, maybe in weathered wood?  Not too much, just enough for it to stand out "slightly".

Could even mix the colors so it uses the brown for the "t" and a mixure of Ubuntu colors for the rest (mustart yellow, brown**s**, orange or dirty red, etc.)?

[IMG]http://img11.imageshack.us/img11/2884/whetstone.gif[/IMG]
Like this?

---

### Post by shane2peru on 2009-10-21
> **saxasm said:**
> Hmm, ok.

I made this one too, I will try to make some more alternatives.

[IMG]http://img30.imageshack.us/img30/2884/whetstone.gif[/IMG]

I'm liking this, can you underline it with a long narrow sword?  I originally had thought in it (like in the background under the word) but I'm thinking underlining it would probably be the best thus far.  

Shane

---

### Post by shane2peru on 2009-10-21
Very nice app, I'm glad you pulled the from the crosswire project, I was going to ask if different language translations could be used, so that is very nice touch.  Also as a suggestion.  Perhaps if someone wanted to build their own list or input their own verses for something that may not be included in the Crosswire repos, perhaps it would be nice to be able to type in your own verses.  I don't know how necessary this would be, but if it isn't too much trouble to add it, it may be a nice touch.  Looks promising.  

Shane

---

### Post by shane2peru on 2009-10-21
> **saxasm said:**
> [IMG]http://img25.imageshack.us/img25/2884/whetstone.gif[/IMG]
Added a sword. What do you think?

It looks better like this, I think:
[IMG]http://img132.imageshack.us/img132/2884/whetstone.gif[/IMG]

Sorry for so many repeated posts.

This also is good for a start, how about keeping with gray letters, or silver letters and raising them out of the cross a little.  Like 3d effect?  The sword too.  That would look nice I think.  Perhaps this could be the icon?  or even the logo.  

Shane

---

### Post by benthorp on 2009-10-22
> **shane2peru said:**
> Very nice app, I'm glad you pulled the from the crosswire project, I was going to ask if different language translations could be used, so that is very nice touch.  Also as a suggestion.  Perhaps if someone wanted to build their own list or input their own verses for something that may not be included in the Crosswire repos, perhaps it would be nice to be able to type in your own verses.  I don't know how necessary this would be, but if it isn't too much trouble to add it, it may be a nice touch.  Looks promising.  

Shane
You can input verses in free text already. Just type in the verse reference and verse body without hitting the "get from SWORD" button, and hit "Add" and it should put it in the database no problems.

---

