---
title: "Making a DVD with buttons to go to properly selected chapters"
date: 2012-06-30
forum: Ubuntu Studio
---

### Post by n3mmr on 2012-06-30
How to cut a video file into separate parts in separate files?
Or, how to make a DVD with chapters from a single video file?

I've tried to make a DVD with a reasonable chapter menu from a single long avi file.
I've tried DVD styler and Bombono and DeVeDe.

None of those allow me, it seems, to put a chapter marker in the video and then create a button on a menu page to go to that chapter.

Bombono claims it can, but the "links" you're supposed to find when editing a button just aren't there!

So, I'm down to trying to split the video file into partial files and then use "add file as chapter" in DVD styler.

But... OpenShot seems not to support splitting a video file???

HELP

---

### Post by mainmeister on 2012-07-01
I've used Avidemux to cut a video into smaller scenes.

---

### Post by n3mmr on 2012-07-15
I just tried kdenlive, which seems to do the right thing. And more.
I'll tell you all about it when I have tried it out more fully.

I think I've just hit the main weakness of any Linux: when it comes down to quality issues, people just don't know and there's no central, well kept, source of usefulness info.

I posted my question as a detail question on using the tools provided in the ubuntustudio distro, assuming that they would be able to perform the job. They were after all provided by a central authority of sorts. 

I am now left with the impression that very little thought actually went into the composition of ubuntustudio, at least for some parts of it.

My view is always: either do a good job, or don't do it at all. Doing a good job might require no more than clearly stating what limitations there are.

I realised that AVIdemuxer wasn't a good choice (although it beats the video editor supplied in ubuntustudio) when I read a documentation site, and realised the instructions given were useless because of stuff like menu choices suggested just didn't exist in avidemuxer.

I have some real experience in SW design and construction, and can safely say that documentation for the complete future target design is one of the first things a team should write. Not necessarily in any detail, but at least a short oneliner for every action a user can take.

And the documentation must exist at the time the application reaches the user.

Otherwise you haven't written an application, but a new form of the ancient Fortune game.

You're in a large program. There are many possible commands.

---

### Post by jejeman on 2012-07-15
Finally I got some time to answer your question.

I'm been using DVDStyler for some time now, and I find it to be the most functional front end for DVDAuthor.

Your task you can do like this:

- make new project that match you video specs.
- add large video file
- go in properties for video file and add chapters
- insert buttons with video preview in menu or text button if you don't need picture
- go to properties for each button and set them to jump to desired chapter

I've noticed few bugs:

- it makes one extra jump chapter option (eg. you make 4 chapters it offers 5 chapters. ignore the extra chapter)
- video preview in buttons are not correct, set them mannualy by inserting the correct time in ms


Splitting video file

Avidemux is great for that. Also, there is mighty ffmpeg which will do the job well. It is great to use it in bash scripts. E.g. I had one project for which I needed to extract frames from video, I've made script whit zenity GUI where I input the range needed and it saved me time and also from makeing mistakes.


Video editing

I've find that Kdenlive is the best. I agree with you on this one it should be included in Ubuntu Studio dvd. I gusess adding Kdenlive to the dvd it would make dvd iso larger because od KDE dependecies.
Since Ubuntu Studio is audio/gtk oriented I don't mind that Kdenlive isn't included by default.


Documentation

I agree it is crutial. I find that GNU/Linux OS is in general well documented. For most programs there is a man page. For some programs one must search for documentation on program's web site. We need to understand that there is lack of man power for documentation. One can argue that, but praxis shows us just that.
This is a nice project
[https://wiki.ubuntu.com/UbuntuStudio/Workflows](https://wiki.ubuntu.com/UbuntuStudio/Workflows)
One can find good starting info there.

p.s.

I've been using Ubuntu Studio for four years now. It took me a lot of time (~3 yr.) and patience to learn how to do some tasks, but now I do everything I need in it.

---

### Post by n3mmr on 2012-07-15
In the days of very long ago, when I was involved in writing "free" versions of existing SW, or rather free software doing what expensive or otherwise unavailable SW already did well, I learned a few lessons. The single most important one was: do not design your own UI. And never write your own manual from scratch. You are a low-resource operation, and you just can't. Stand on the shoulders of any giant that will let you.

Get the most accurate manual of your ideal, your target to emulate, and follow it in every nauseating detail, whatever happens. After that, you will most of the time be able to write any target design changes up as additions to the manual, w/o incurring any extra workload.

I managed to find out how to introduce chapter points in a single video file in DVD styler, thanks to your pointer. Thanks for helping! 
I think the UI is horrid, but it will do the job. Albeit at a bit too coarse a granularity.

---

