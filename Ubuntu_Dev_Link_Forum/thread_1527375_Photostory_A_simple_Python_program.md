---
title: "Photostory: A simple Python program"
date: 2010-07-09
forum: Ubuntu Dev Link Forum
---

### Post by Tahakki on 2010-07-09
Hey guys - short and sweet post here as I'm pushed for time.

Basically, I've developed a small application for ubuntu with Python. You can read all about it, and download it, at the following page (on my blog):

[http://tahakkistechblog.hostei.com/2010/07/my-new-project-photostory/](http://tahakkistechblog.hostei.com/2010/07/my-new-project-photostory/)

If you guys could test this for me that'd be absolutely fantastic - so far I've only been able to test it with one webcam, and only on Lucid.

Thanks!

---

### Post by Finalfantasykid on 2010-07-10
This is a really cool idea.  I'll have to remember to do this.

I have a suggestion though.  From what I can tell there is no way to delete a photo if it did not turn out very well.

Where are the photos stored since the first one I took, did not turn out.

EDIT:  Also I am on Lucid, and using the Playstation Eye

---

### Post by Tahakki on 2010-07-11
Is the program working alright for you apart from not being able to delete?

Anyway, the photos are stored in /usr/share/photostory/pictures, but deleting them will mess up the database I had to make to number the pictures correctly. If you make a blueprint for this feature I will eventually add it. ^_^

---

### Post by Finalfantasykid on 2010-07-11
Ok thanks, I deleted the picture, and modified the db acordingly.

I did notice one other problem.  If you start the program, and then plug in the usb webcam, the preview will not show up.  I have to restart the program to see the preview.

Also a suggestion for the video creation.  It would be nice to see a file browser.

---

### Post by Tahakki on 2010-07-11
Right, I'll add the file browser thing, put it down to laziness. :P

As for the webcam, I COULD add a button saying 'Start Webcam' or similar, but I think it's easy enough to restart the program. Most people leave their webcams plugged in.

I wonder how hard it is to get something into the software store? Anyone feel like designing a decent icon?

---

### Post by Finalfantasykid on 2010-07-11
I wipped up a quick 'Delete Picture' feature.  I'm not familiar with lauchpad very well, so I'll just post it here.

---

### Post by Tahakki on 2010-07-11
Thanks! Why have you got both os.remove and del?

Anyway, I'll try and add this in - a few wee changes needing made, mainly to the ind file. Thank youuu! ^_^

---

### Post by Finalfantasykid on 2010-07-11
del will get rid of the dictionary entry, while os.remove will get rid of the image from the pictures directory.

I don't really know python, so there is probably a better way :P

---

### Post by Tahakki on 2010-07-11
No, that's great, just didn't realise. :)

I will add this to the next release. Is there a name you'd like put in the credits?

---

### Post by Finalfantasykid on 2010-07-11
David Turner is my real name, so you can put that :)

And ya I wasn't sure how to change the index when deleting it.  Decrementing would not work for many cases since if you delete an image which is not today's date, then a day will be re-written.

Would it not be better to name the images as the date of the image?

ie. 2010-10-06.png

---

### Post by Tahakki on 2010-07-11
That was what it was originally, but the function I use to turn images into a video needs to be a series, like %d. :)

---

### Post by Nick_Jinn on 2010-07-11
So, is this to make like a cartoon, or a series of flat images, or can you make like an animated storybook from drawings with it? I am not clear on what it produces.

---

### Post by Tahakki on 2010-07-11
This is roughly what it produces, though it isn't made with Photostory. Photostory uses your webcam.

[http://www.youtube.com/watch?v=6B26asyGKDo](http://www.youtube.com/watch?v=6B26asyGKDo)

---

### Post by Penguin Guy on 2010-07-11
> **Tahakki said:**
> I wonder how hard it is to get something into the software store? Anyone feel like designing a decent icon?

Nice idea for an app, obviously needs a bit of work though. Why not [make a Launchpad team]("https://launchpad.net/people/+newteam") - with a few people helping out you'll stand a better chance of getting into the official repositories (and until such time, you can set up a PPA). As for the icon, I had a go at making one - I know it's nothing amazing but perhaps it will do until you can find a better one.

---

### Post by Tahakki on 2010-07-11
PG - that's absolutely brilliant, thanks! Maybe a bit more colour though? You've certainly captured the essence of the application. ^_^

Just a hint - I like logos to be roughly circular. Because I'm weird.

---

### Post by Penguin Guy on 2010-07-11
> **Tahakki said:**
> Maybe a bit more colour though?
**...**
Just a hint - I like logos to be roughly circular.
Not sure about either of those requests, I had a go at both but the result seems pretty horrible IMO. Here it is anyway.

---

### Post by Tahakki on 2010-07-11
Hmm...could you do the first one in those colours? It's your call though, you're the artist. :)

What name shall I put in the credits?

---

### Post by Finalfantasykid on 2010-07-11
> **Penguin Guy said:**
> Nice idea for an app, obviously needs a bit of work though. Why not [make a Launchpad team]("https://launchpad.net/people/+newteam") - with a few people helping out you'll stand a better chance of getting into the official repositories (and until such time, you can set up a PPA).

I'll participate.  It could be a good way for me to learn python

---

### Post by Penguin Guy on 2010-07-11
> **Tahakki said:**
> Hmm...could you do the first one in those colours? It's your call though, you're the artist. :)

What name shall I put in the credits?
There we go, I've attached the SVG and some PNGs ready for uploading to Launchpad. As for credit - no need, it's really a lot easier than it looks. However I also know a bit of Python and am familiar with Launchpad, so if you do get a team running, or if you need help setting one up, you can find me at: [https://launchpad.net/~joshbrown](https://launchpad.net/~joshbrown)

---

### Post by Finalfantasykid on 2010-07-12
I believe that I have fixed the index problem that was mentioned earlier.  The only changes that I made should be in the deletePic function.

---

### Post by Tahakki on 2010-07-12
The team can be found here:
[https://launchpad.net/~photostory-team](https://launchpad.net/~photostory-team)

Thanks for your contributions, chaps! FFK, this code is great, but I had a think about this earlier over breakfast and worked out that it doesn't really matter if there are gaps in the numbering of the photos! So your original code works perfectly...sorry! :P

Anyway, I will be away for the next week at camp, so if anyone wants to add anything please post it here or to the project. Thanks!

EDIT: Never mind, I was wrong - FKK's new code *is* necessary. However, it doesn't work - ind is not being decremented properly. Can you check? Also, your indentation looks a bit funny? :)

---

### Post by Finalfantasykid on 2010-07-12
What editor are you using?  The tabbing is probably because we were using different programs.  I used gedit to write that.  It would be best if we used the same program for this, so which one are you using?

Also I tested the decrement out and it did work.  What did your database look like?  And which did you delete?

---

### Post by Penguin Guy on 2010-07-13
> **Tahakki said:**
> Also, your indentation looks a bit funny? :)
> **Finalfantasykid said:**
> What editor are you using?  The tabbing is probably because we were using different programs.  I used gedit to write that.  It would be best if we used the same program for this, so which one are you using?

Mixed tabs and spaces :shock: - try to use 4 spaces for indentation according to [PEP8]("http://www.python.org/dev/peps/pep-0008/"). It might help if you set this up though gedit: [COLOR="Green"]Edit -> Prefernces -> Editor -> Tab Stops -> Tab width: 4, Insert spaces instead of tabs[/COLOR].

---

### Post by Finalfantasykid on 2010-07-13
Thanks I'll make sure to do that :)

---

### Post by Tahakki on 2010-07-20
FFK - could you fix the code (4 spaces instead of a tab) and merge it to the lp:photostory branch?

Thanks! I see there are a few bug reports - some are fixed, some will be. Remember to make a blueprint for each feature, even the delete feature!

---

### Post by Tahakki on 2010-07-20
[Double post, sorry.]

---

### Post by lisati on 2010-07-20
Excuse me but:
[IMG]http://www.microsoft.com/library/media/1033/windowsxp/images/using/digitalphotography/photostory/PS3_hero_pt1.jpg[/IMG]
[IMG]http://www.microsoft.com/library/media/1033/windowsxp/images/using/digitalphotography/photostory/PS3_hero_pt2.jpg[/IMG]

---

### Post by Tahakki on 2010-07-20
Photostory != Photo Story. They do different things too.

---

### Post by Penguin Guy on 2010-07-20
> **Tahakki said:**
> Photostory != Photo Story.
I doubt that 'Photostory' is trademarked, it's too ambiguous a name and trademarks are usually marked with '™'.

---

### Post by Tahakki on 2010-07-20
Indeed.

Anyway, I'm using the Launchpad branch to add changes. Please keep checking it if you want the latest updates! :P

The file chooser dialog is done and pushed, happily. Keep adding blueprints! ^_^

---

### Post by Penguin Guy on 2010-07-20
I'm not a master at packaging but I'll have a go re-making the [FONT="Courier New"].deb[/FONT] package. Also your Launchpad commits seem to be authored as 'Joel Auterson <joel@auterson-study>' which doesn't seem to be registering as a valid user on Launchpad, just a minor issue that I thought I'd point out ;). Everything else is looking great so far - we just need some more team members now.

EDIT: One more thing, if you want to release a Bazaar version it's good practice to tag it, e.g:
```
bzr tag photostory-0.95
```

---

### Post by Tahakki on 2010-07-20
I think we'll just package full releases. As for the commits, it's probably to do with bzr...I'll look into it.

EDIT: Fixed, should work with next contribution. As for the .deb, I'll do that at the next release.

---

### Post by Penguin Guy on 2010-07-21
> **Tahakki said:**
> I think we'll just package full releases. As for the commits, it's probably to do with bzr...I'll look into it.

EDIT: Fixed, should work with next contribution. As for the .deb, I'll do that at the next release.
I meant create a .deb for 0.9 that can then be re-used for later releases. I've already started making a [FONT="Courier New"]setup.py[/FONT] at [[FONT="Courier New"]lp:~joshbrown/photostory/packaging[/FONT]]("https://code.launchpad.net/~joshbrown/photostory/packaging") (although the most recent revision hasn't been pushed yet - want to check it works first).

---

### Post by Tahakki on 2010-07-21
I see...that will store the pictures in the user's home folder? That would be good.

I'm trying to add the 'add music to video' feature. It's tricky.

---

### Post by Tahakki on 2010-08-05
Back, sick. Any news?

---

### Post by Penguin Guy on 2010-08-06
> **Tahakki said:**
> I see...that will store the pictures in the user's home folder? That would be good.
No, that'll have to be done in the code itself the first time the user runs the program, see [[FONT="Courier New"]bug #608366[/FONT]]("https://bugs.launchpad.net/photostory/+bug/608366").

> **Tahakki said:**
> Back, sick. Any news?
I've pushed the first version of the [FONT="Courier New"]setup.py[/FONT] (@ [[FONT="Courier New"]lp:~joshbrown/photostory/packaging[/FONT]]("https://code.launchpad.net/~joshbrown/photostory/packaging")) - the installer works but you can't make a [FONT="Courier New"].deb[/FONT] yet. Still, I think it'd be a good idea to [merge it into [FONT="Courier New"]trunk[/FONT]]("https://code.launchpad.net/~joshbrown/photostory/packaging/+merge/30559") so the whole team can test and work on it. Also, you're the maintainer, so you're the only one who can [triage bugs]("https://bugs.launchpad.net/photostory").

---

### Post by Tahakki on 2010-08-06
Explain what triaging means, briefly? Is that where I assign them to people and set importance etc?

---

### Post by Tahakki on 2010-08-15
Some more branches merged, thanks for your contributions. Can we continue using this topic as a means for discussion and conferring? Launchpad doesn't appear to have a system that makes it easy for us to talk. :)

---

### Post by Finalfantasykid on 2010-08-15
Ya it doesn't really seem like this forum is really the place for a discussion like this.  Using the white board, blue prints and bug reports though we can communicate.  Also does launchpad have a mailing list set up?

---

### Post by Tahakki on 2010-08-15
Ah, a mailing list...clever. I shall look into it.

---

### Post by Tahakki on 2010-08-16
Mailing list set up. Check the Photostory Team page.

---

### Post by lukaszeq on 2010-09-13
Photostory is absolutely gorgeous. I was thinking about that idea for a long time and I have discovered your application on OMG! Ubuntu just now. Fantastic!

I would love to see the following features in next relase:

[LIST=1]
[*]Possibility of changing directory where photos are stored. I would like to store my photos on Dropbox. It is a must have IMO.
[*]Other languages. ;) It would be cool to see Photostory in, i.e., Polish. ;) I am ready to handle this translation.
[/LIST]

Best regards!

---

### Post by Finalfantasykid on 2010-09-14
Thanks for the suggestion about languages.  I just submitted a blueprint for this feature.

---

### Post by Penguin Guy on 2011-02-21
Photostory 1.0 released! Deb and source packages can be downloaded from [Photostory's Launchpad project page]("https://launchpad.net/photostory").

---

### Post by tellapu on 2012-04-20
I like this tool and the picture taking works fine. They are stored in the right folder and I can look at them. But when I try to create a video (choose a folder, test.mp4 as name, create film), there is a new file test.mp4, but it has no content and is 0 bytes. What happens?
(Ubuntu 11.04 AMD64, photostory 1.0)
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

### Post by tellapu on 2012-06-11
Bump :confused:
[LEFT][COLOR=#000000][/COLOR][/LEFT]

---

