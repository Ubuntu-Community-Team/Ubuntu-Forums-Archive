---
title: "iPhone Notes Client"
date: 2011-03-28
forum: Ubuntu One (CLOSED)
---

### Post by aardvark4 on 2011-03-28
Hello,

First, I'm not sure if this is the correct venue to be asking this question, so if not, I apologize.  

I'm a big fan of Tomboy notes and the ability to sync them with UbuntuOne.  I like having my notes accessible across all of my computers, and would like to be able to do the same thing on my phone.  I know there is a client for Android, but from what I could tell, no such client exists for iPhone. 

I'd been meaning to play around with learning some iPhone development anyway, so I did some reading on iOS development, spent some time, and wrote an application that does most everything that I use Tomboy for. It can link to your Ubuntu One account, sync notes back and forth, and it supports the majority of the formatting (bold, underline, highlight, etc.) options.  I'm sure that someone more experienced in iOS development could have done a better job, but it seems to work well enough for what I need.

I'd like to put it in the apple app store for free and make the source available (as I'm sure it could stand to be fixed and refined by someone more knowledgeable than myself), but I'm not sure what the rules are for such a thing. Right now I've just got it on my own computers and haven't gone to the trouble to pay to enter the Apple developer program because I have some questions about whether I can do so, before I spend the money.
  
As it stands right now, I've used the Ubuntu font in the application (font.ubunu.com), as well as some mentions of Ubuntu itself and the Ubuntu One logo. I suspect the use of the font is probably okay, but I have my doubts about the logo, so some rebranding might be necessary.  More than that, am I even allowed to access the Ubuntu One Notes service in this way? I know Ubuntu has some mobile applications for syncing other Ubuntu One services (music, contacts, etc.), but I couldn't find mention of notes, and as I said before, I know that Tomboy and Tomdroid are already utilizing Ubuntu One as a sync destination.  

Basically, I was hoping someone might either know the answers to some of these questions, or be able to point me toward someone who does.  Obviously I can just continue using this application for myself as it does what I wanted, but I thought it might be nice to make it available for other people and, if someone more knowledgeable about iOS development were so inclined, to improve it.

Thanks,
Adam

**EDIT:**

Asked this question at 
[http://askubuntu.com/questions/32628/i-am-writing-an-iphone-notes-client-can-i-integrate-it-with-ubuntu-one](http://askubuntu.com/questions/32628/i-am-writing-an-iphone-notes-client-can-i-integrate-it-with-ubuntu-one)
and got the answer I needed

---

### Post by forrestcarter on 2011-06-06
Have you thought about putting it up on cydia or one of the other jailbroken app stores?  They don't have the user base of the apple app store, so not as many people will have access to the app.  But the upside is that Apple can't tell you that they don't want your app...

Also, is there a way I could get a copy of this?  I have been looking for hours for a solution to this very problem.  I would like to have my laptop, desktop, and iphone all share notes.  (I have a MTBI from an explosion in Iraq and my memory isn't great.  I use tomboy and the iphone notepad VERY frequently)  

What note app do you use on the iphone to write notes with?  (I don't really have a preference as long as it's not overly complicated and I can share the notes with my computers)

---

### Post by waynerod on 2011-06-27
This would be cool. I would also like a copy of it. Try and get it into the actual App Store if possible. :popcorn:

Currently, I just sync the Notes with my Google Account which just sends myself emails (Sure this'll put it on the web, but it isn't really efficient).

---

### Post by duanedesign on 2011-07-06
@aardvark4
You should definetly [put the source code up on Launchpad]("https://launchpad.net/projects/+new") so others can benefit from the work you have done and help you improve your code.

As far as the trademark issues, you can find more info about that [here]("http://www.ubuntu.com/aboutus/trademarkpolicy").

respectfully,
duanedesign

---

### Post by aardvark4 on 2012-07-24
After quite some time, I finally managed to get around to getting this little project into Apple's app store. 

I had to make some compromises in terms of the OAuth stuff and it was rejected a couple of times because Ubuntu One's OAuth page has links to things that a user could buy (outside of in-app purchases), and that sort of thing.

In any case, though not the best notes client by any means, it syncs with Ubuntu One's notes store, so you can get your Tomboy notes on your iPhone and have any changes you make waiting for you when you get back to a computer, and that's really all I wanted out of it. 

Some markup is supported, though perhaps a bit awkward. Apple has not yet made rich text editing practical without a whole lot of work, so for now it'll have to be in-line markup. In any case, I don't know if anyone will see this or not, but I figured I'd update the thread since it has finally been published.

[http://itunes.apple.com/us/app/webnotes-powered-by-ubuntu/id519580240?ls=1&mt=8](http://itunes.apple.com/us/app/webnotes-powered-by-ubuntu/id519580240?ls=1&mt=8)

---

### Post by spaceshipguy on 2012-09-26
> **aardvark4 said:**
> 

[http://itunes.apple.com/us/app/webnotes-powered-by-ubuntu/id519580240?ls=1&mt=8](http://itunes.apple.com/us/app/webnotes-powered-by-ubuntu/id519580240?ls=1&mt=8)
Your link doesn't work for me. What is your app called so I can search the store?

---

### Post by aardvark4 on 2012-09-26
> **spaceshipguy said:**
> Your link doesn't work for me. What is your app called so I can search the store?

It's hard to say what went wrong there. It worked for me just now, but in any case, it is called "**webNotes**." In the store, its full name is "**webNotes (powered by Ubuntu One)**" since, believe it or not, other people have thought to put the words "web" and "notes" together before.

---

### Post by overdrank on 2012-09-26
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

