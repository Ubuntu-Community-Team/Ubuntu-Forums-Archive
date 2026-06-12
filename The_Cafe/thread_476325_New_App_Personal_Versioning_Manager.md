---
title: "New App: Personal Versioning Manager"
date: 2007-06-17
forum: The Cafe
---

### Post by kripkenstein on 2007-06-17
I've started to write a new app, meant to help with managing versions ('snapshots') of important files, as well as doing things with the versions (restoring an old version, merging changes with a new version, etc.).

Anyhow, the app is far from at a first stable release, but it has the most basic initial functionality, and seems to work reasonably well, so I thought I'd tell people about it. Feedback or help of any kind is welcome :)

The name of the app (tentative) is "Pevo" (pronounced PEIGH-vough), short for Personal Versioning Manager, or something like that ;)

Some screenshots are below.

The project page is here: [Pevo project page]("http://code.google.com/p/pevo/"). To give Pevo a test run, get the latest release download from the "Downloads" tab (currently 0.1). Or, try the subversion source as explained in the "Source" tab. See below ("INSTALLATION") for dependencies.

NOTE: Pevo is far from being stable. Please don't (yet) rely on it to manage important files! (A similar warning appears in the app itself.)

INSTALLATION: The SVN source may not compile. It might be better to grab the latest stable version ('downloads' tab on the project page). The current stable release is **0.1**.

Pevo was developed and tested on Ubuntu Feisty (7.04). To install dependencies there, do
```
   sudo apt-get install subversion python-svn
```
("python-svn", **not** "python-subversion"! :))

Then, to run Pevo from the subversion source code, simply run ./pevo (after chmod +x pevo, if
necessary) in the pevo directory.

More specifically, required dependencies are:
```

	- pysvn      : Appears as "python-svn" in Ubuntu (and presumably Debian).
	               Note: This is DIFFERENT from the "python-subversion" package!
	- Subversion : This appears, unsurprisingly, in the package "subversion".
	- GTK, PyGtk : These should be installed by default on Ubuntu (but not on other desktops).
	- Python 2.5 : Installed by default on Ubuntu Feisty. Appears as an option (python2.5) on
	               Edgy. Note that Pevo uses Sqlite, appearing only in Python 2.5. However, there
	               are ways to use Sqlite on Python 2.4 (but these have not been tested yet).

```

---

### Post by FryerFox on 2007-06-17
I think you need to install python-subversion for this to work. I did, and yet I still get:
```
Traceback (most recent call last):
  File "gui-gtk.py", line 37, in <module>
    import core
  File "/home/source/python/pevo/core.py", line 37, in <module>
    import vsvn
  File "/home/source/python/pevo/vsvn.py", line 32, in <module>
    import pysvn
ImportError: No module named pysvn
```
I'm using Feisty - maybe that's the problem. I won't be able to try it on gusty until tomorrow.

---

### Post by Golyadkin on 2007-06-17
Hey, I am gonna try this out. I am currently using Cervisia with CVS for the version control on my master thesis which I am writing in LaTeX. It is maybe overkill, but it works and it can be trusted. I don't like that Cervisia is the only decent CVS client because it's so KDE :) I would love a nice GNOME client.

---

### Post by DoctorMO on 2007-06-17
how does it work? it looks like a very cool idea, it would be nice to turn on the kernel level file modification call backs which allow you to take an initial snap shot and just wait for the kernel to tell you when the file was modified.

---

### Post by kripkenstein on 2007-06-18
> **FryerFox said:**
> I think you need to install python-subversion for this to work. I did, and yet I still get:
```
Traceback (most recent call last):
  File "gui-gtk.py", line 37, in <module>
    import core
  File "/home/../source/python/pevo/core.py", line 37, in <module>
    import vsvn
  File "/home/../source/python/pevo/vsvn.py", line 32, in <module>
    import pysvn
ImportError: No module named pysvn
```
I'm using Feisty - maybe that's the problem. I won't be able to try it on gusty until tomorrow.

The problem is that there are two different packages names python-svn and python-subversion, for some reason, very confusing, sadly... My app needs python-svn.

Ok, I will quote the INSTALL file in the original post so others don't run into that problem.

---

### Post by SoulinEther on 2007-06-18
This sounds like a wonderful piece of software. The beginnings of a Time Machine / System Restore, maybe?

---

### Post by kripkenstein on 2007-06-18
> **Golyadkin said:**
> Hey, I am gonna try this out. I am currently using Cervisia with CVS for the version control on my master thesis which I am writing in LaTeX. It is maybe overkill, but it works and it can be trusted. I don't like that Cervisia is the only decent CVS client because it's so KDE :) I would love a nice GNOME client.

Heh, that's exactly why I started to write Pevo, actually, to help out while writing my thesis, also in Latex :)

I agree, most CVS or subversion clients are overkill, and also on the other hand they aren't that user-friendly for the specific things I wanted to do. So that got me to coding...

Anyhow, if you give Pevo a try, please let me know what you think, what other features you would like it to have, etc.

---

### Post by SoulinEther on 2007-06-18
Now I feel like an idiot for not realising an obvious fact. >.>

Don't mind me. Carry on. :S

---

### Post by kripkenstein on 2007-06-18
> **DoctorMO said:**
> how does it work? it looks like a very cool idea, it would be nice to turn on the kernel level file modification call backs which allow you to take an initial snap shot and just wait for the kernel to tell you when the file was modified.

Well, for the snapshots it basically wraps around subversion. For detecting when files change, it currently just checks them every few seconds (user-configurable). Yes, it would be better to somehow wait for a signal from the filesystem or kernel for changes to the file. I will look into this, good idea.

---

### Post by kripkenstein on 2007-06-18
> **SoulinEther said:**
> This sounds like a wonderful piece of software. The beginnings of a Time Machine / System Restore, maybe?

[...]
Now I feel like an idiot for not realising an obvious fact. >.>

Don't mind me. Carry on. :S

No, that is a good question :)

Actually, I am **not** trying to create a Time Machine clone, the goals are slightly different. My goal is to help a user who has a few important files that he/she is working on. Say a term paper, a short story, things like that (not the entire filesystem!). On such files, there are several things users generally want, but currently can't do:

[LIST]
[*] See previous versions of those files
[*] Merge changes made elsewhere (by the user on a different computer, or a different person)
[*] Search/filter the list of important files, by tags
[*] Automatically back up the files (say, to a USB disk, when it is connected)
[*] etc.
[/LIST] 

Pevo currently does the first two, and will hopefully soon do the rest ;)

So, Pevo does or will do some things that appear in other apps, like Time Machine, Beagle, and so forth. But its focus is different. I hope that makes some sense.

---

### Post by SoulinEther on 2007-06-18
Hmm... upon finishing this piece of software, would you consider looking into making an overall system backup type thing? A decent frontend would be equally appreciated.

---

### Post by kripkenstein on 2007-06-18
> **SoulinEther said:**
> Hmm... upon finishing this piece of software, would you consider looking into making an overall system backup type thing? A decent frontend would be equally appreciated.

I do agree that there is room for improvement with backup software, but I think it'll be quite a while until I finish this project, there are a lot of features I want to implement... by then I am sure backup software will be perfected ;)

---

### Post by SoulinEther on 2007-06-18
Not to pull a Tim Russert, but,,,

Are you saying that, in truth, in 2008, you, Al Gore (er... Kripkenstein), democrat from ... whatever state, will be running, truthfully, for Presidential election (or, making an AWESOME! backup program)?

---

### Post by Golyadkin on 2007-06-18
I just checked it out of Subversion and it "installs" fine. When I add a new file (introduction.tex) I get some warnings though:
> 
Pevo - Personal Versioning Manager 0.01 , installed at: /home/yves/Projects/Pevo/pevo
Starting Sqlite DB thread...
Creating database...

** (yelp:7170): WARNING **: AT_SPI_REGISTRY was not started at session startup.

** (yelp:7170): WARNING **: IOR not set.

** (yelp:7170): WARNING **: Could not locate registry


---

### Post by Golyadkin on 2007-06-18
Okay, I played a bit more with the application and I like it.
There are two important things I miss though, a diff and a commit message. Branching and tagging are not really necessary, but I would like to see what the changes are in a document, before I commit (make a snapshot). Also, I would like to be able to store  a message with each revision, because in my thesis I now have 38 revisions, and if I would only see a date and then "Minor changes" "Major changes" I would have no idea to which revision I should revert.

One thing though, when I opened a monitored file in Kile, and I came back to Pevo with Kile still open, Pevo was not responding and I had to kill it. The second time I did this however, it worked fine. Maybe just a glitch on my side.

---

### Post by urukrama on 2007-06-18
I get the following error in Dapper when I try to run ./pevo 

As far as I can tell, I have all the dependencies installed.

```
File "gui-gtk.py", line 272
    ("1" if self.wtree.get_widget("refresh_mainlist").get_active() else "0")
          ^
SyntaxError: invalid syntax
```

---

### Post by Golyadkin on 2007-06-18
This is my line 272 in that file:
> 
 ("1" if self.wtree.get_widget("refresh_mainlist").get_active() else "0")

which is exactly identical, and for me it works. 

What is your output of this command:
> 
$ python -V
Python 2.5.1


---

### Post by Golyadkin on 2007-06-18
(ps, I am using Feisty Fawn 64 bit) 

Do you have python-svn installed?

---

### Post by urukrama on 2007-06-18
I have python-svn installed. Python -V tells me I have python 2.4.3, which seems standard for Dapper.

---

### Post by Golyadkin on 2007-06-18
Well, there is quite a difference between Python 2.4 and 2.4. There were 353 patches applied and 458 bugs fixed between Python 2.4 and 2.5. Maybe you should upgrade to the new version of Python?

Kripkenstein said in his opening post that 2.5 is required:
> 
- Python 2.5 : Installed by default on Ubuntu Feisty. Appears as an option (python2.5) on
	               Edgy. Note that Pevo uses Sqlite, appearing only in Python 2.5. However, there
	               are ways to use Sqlite on Python 2.4 (but these have not been tested yet).


---

### Post by kripkenstein on 2007-06-18
> **Golyadkin said:**
> Well, there is quite a difference between Python 2.4 and 2.4. There were 353 patches applied and 458 bugs fixed between Python 2.4 and 2.5. Maybe you should upgrade to the new version of Python?

Kripkenstein said in his opening post that 2.5 is required:

Indeed, you are exactly right. That notation is new in Python 2.5.

Python 2.5 includes Sqlite, which I use in Pevo anyhow, so I figured I'd write the entire app using 2.5 (also 2.5 is cooler ;) ). However, this is a bit of a problem for people running older versions of Ubuntu, true... well, if enough people complain about this, perhaps I will reconsider...

Urukama, I see you say you are on Dapper? Then I am not sure, but perhaps you can install Python 2.5 somehow. On Edgy 2.5 is installed, but not default (you can run it with "python2.5").

---

### Post by kripkenstein on 2007-06-18
> **Golyadkin said:**
> I just checked it out of Subversion and it "installs" fine. When I add a new file (introduction.tex) I get some warnings though:

Those warnings are from Yelp, which shows the help file. Yeah, I get those warnings too, not sure what the issue is. But Yelp runs fine.

> **Golyadkin said:**
> Okay, I played a bit more with the application and I like it.
There are two important things I miss though, a diff and a commit message. Branching and tagging are not really necessary, but I would like to see what the changes are in a document, before I commit (make a snapshot). Also, I would like to be able to store  a message with each revision, because in my thesis I now have 38 revisions, and if I would only see a date and then "Minor changes" "Major changes" I would have no idea to which revision I should revert.

Ok, I will certainly keep these suggestions in mind. Thanks!
> 
One thing though, when I opened a monitored file in Kile, and I came back to Pevo with Kile still open, Pevo was not responding and I had to kill it. The second time I did this however, it worked fine. Maybe just a glitch on my side.

Hmm, that doesn't sound good. If it recurs, then tell me, there might be a bug.

---

### Post by thorwil on 2007-06-18
Looking at the first screenshot, you could change the first column label to "Managed Files" and drop the "File-specific Actions" label to save some space and have a more streamlined appearance. The action labels should be left aligned

---

### Post by kripkenstein on 2007-06-18
> **thorwil said:**
> Looking at the first screenshot, you could change the first column label to "Managed Files" and drop the "File-specific Actions" label to save some space and have a more streamlined appearance. The action labels should be left aligned

Thanks for the suggestions. The first one sounds good, I'll think about it a bit more before I implement it, though (I think I do want some sort of title, so first-time users aren't *too* confused...).

Regarding the second, the action labels are a toolbar, and GTK doesn't let them be left-aligned, it seems. Now, I could get around this by making them normal buttons, but I like the toolbar look&feel. So I am not sure what is best here. I'm open to being convinced either way.

---

### Post by urukrama on 2007-06-18
kripkenstein, if I install python 2.5 alongside 2.4 would that interfere with other applications that use python? I don't want to criple my system just to try out a program.

---

### Post by thorwil on 2007-06-18
The column caption would be the title. It's not like anything else but that being a list of managed files would make sense.

Buttons for the actions would look horrible. If GTK really doesn't allow left alignment in such a case, it's a bug! ;)

---

### Post by kripkenstein on 2007-06-18
> **urukrama said:**
> kripkenstein, if I install python 2.5 alongside 2.4 would that interfere with other applications that use python? I don't want to criple my system just to try out a program.

Well, I understand your worry. And I am not sure how risky this would be, I never did it myself. If you overwrite python 2.4, then you might have lots of issues. If you install it alongside it, then that might work, but this is harder to do, and probably not worth your time.

So, it seems like this is probably not a great idea, which is sad, since I would like you to try out my app... Unless perhaps someone else has a suggestion?

Anyhow, my conclusion is that I should reconsider my decision to develop for python 2.5. I guess I will try to work towards an app that works on 2.4 or 2.5 (it might take a bit, though).

---

### Post by kripkenstein on 2007-06-18
> **thorwil said:**
> Buttons for the actions would look horrible. If GTK really doesn't allow left alignment in such a case, it's a bug! ;)

Yes, this is quite odd. I'm trying to think of an app that uses a vertical toolbar (since the problem can't be seen in a normal horizontal one :) ), to compare and see what they get. Nothing comes to mind... any ideas?

---

### Post by Golyadkin on 2007-07-01
Hey Kripkenstein, I wanted to bump this thread because I am curious how you are getting along with your cool program :)

---

### Post by Polygon on 2007-07-01
i will be trying this program out! looks intrestering

whoops, looks like svn doesnt work lol

> 
mark@ubuntu:~/svn/pevo$ ./pevo
Traceback (most recent call last):
  File "gui-gtk.py", line 37, in <module>
    import core
  File "/home/mark/svn/pevo/core.py", line 595
    def get_status(self, path):
      ^
IndentationError: expected an indented block
mark@ubuntu:~/svn/pevo$ 



---

### Post by kripkenstein on 2007-07-01
> **Golyadkin said:**
> Hey Kripkenstein, I wanted to bump this thread because I am curious how you are getting along with your cool program :)

Thanks for the interest :)

Well, to tell you the truth, it didn't seem like there were many people that thought the project was a good idea, so I didn't focus on it. Also I've been very busy with other things. A final reason, and perhaps the most important, is that I couldn't decide on how the app should behave, so I decided to take a break until I figure out what the right behavior is. Still no decision (the question is how to handle multiple copies of the same document).

---

### Post by kripkenstein on 2007-07-01
> **Polygon said:**
> i will be trying this program out! looks intrestering

whoops, looks like svn doesnt work lol

Yeah, SVN is a work in progress :)

You can see a working version, though, if you download the 0.1 release (look at the 'downloads' tab on the project page).

---

### Post by needtolookatascreenshot on 2007-07-01
[http://ubuntuforums.org/showthread.php?t=519877](http://ubuntuforums.org/showthread.php?t=519877)

---

### Post by kripkenstein on 2007-07-01
> **needtolookatascreenshot said:**
> Well, I certainly find it very interesting. I just wasn't aware of the project till this thread was bumped and I'm sure there are many people in a similar situation.

Ok, that's nice to know :)

---

### Post by Golyadkin on 2007-07-01
That is also one of the reasons why I bumped this thread. I think this program has potential. Version control is not just for programmers, and this project can make it more accessible for everyone, mostly students who keep wishing they could go back to a previous version of their schoolreports and such. 

offtopic: I myself started learning Python today; I am having some trouble getting data from a SQLite database into a list view control :S I have programming experience, just not with Python. Do you maybe have a pointer for me Kripkenstein?

---

### Post by kripkenstein on 2007-07-01
> **Golyadkin said:**
> offtopic: I myself started learning Python today; I am having some trouble getting data from a SQLite database into a list view control :S I have programming experience, just not with Python. Do you maybe have a pointer for me Kripkenstein?

Well, the examples in the documentation are how I learned:
[URL="http://docs.python.org/lib/module-sqlite3.html"]
http://docs.python.org/lib/module-sqlite3.html[/URL]

Also, you can read the Pevo source code to see concrete uses ;)

If it is a specific problem, then feel free to ask.

---

### Post by Golyadkin on 2007-07-01
Thanks, it is the same what I used. I got it working now :)

---

### Post by Mander on 2008-05-28
I've only just started using Ubuntu regularly, and this is the first I've heard of your program.  Sounds promising, if you are still working on it!

I used a program called FileHamster for a while on XP which kind of worked like what you are proposing.  It would watch designated files and folders for changes and make automatic snapshots at configurable intervals, or you could make manual copies and so on.  It could also be set to automatically ask for a comment when you made changes.  I think that a personal version control system should be something like that--it could run more or less automatically if you wanted it to.  I used it to keep track of my PhD thesis when I was still writing it in Word.  Now that I've switched to LaTeX it seems like I could change to an ordinary version control system, but it just seems so complicated!

Anyway, I just wanted to chime in and say this sounds like a great idea and I hope you revisit it.

---

