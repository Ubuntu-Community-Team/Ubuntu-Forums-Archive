---
title: "advanced blogging application"
date: 2007-11-29
forum: Ubuntu Brainstorm
---

### Post by darxoul on 2007-11-29
i am switching to ubuntu from xp and want that switch over as smooth as possible. i really need an application to post blogs to new blogger. here are the features that i need:

* posting images via the blogger api
* posting video
* posting mp3 (not essential, but would be great)

we have discussed the issue in the programming forum as well and i wanted to share it here as well to hear from you guys. perhaps i will end up with writing it, then i will need some guidance about the linux environment i believe. any ideas?

---

### Post by tjagoda on 2007-11-29
Whats wrong with OpenOffice + saving in HTML?

---

### Post by 23meg on 2007-11-29
Did you check out the existing applications, such as BloGTK? You may want to add your desired features to them instead of starting from scratch.

---

### Post by darxoul on 2007-11-29
> **tjagoda said:**
> Whats wrong with OpenOffice + saving in HTML?
as far as I know you cannot post to a blog via openoffice. What i am looking for is a blogging application, i am not thinking of a web site. it is easier to just write and send. and it won't be possible to send images, video and mp3 using openoffice. correct me if i am wrong.

> **23meg said:**
> Did you check out the existing applications, such as BloGTK? You may want to add your desired features to them instead of starting from scratch.

yes i checked blogtk. it doesn't support the features that i am looking for. i send an email to the developer to discuss some issues. the last time it has been updated is about 2 years ago, and he writes in a blog post that he is thinking of refactoring the code to support new features. so i am waiting for his response before doing anything. anyway, i do not have that much time, so that is not a pain to wait for a response :)

thank you for your response by the way.

---

### Post by qamelian on 2007-11-30
Have you checked out the ScribeFire extension for Firefox?

---

### Post by darxoul on 2007-11-30
> **qamelian said:**
> Have you checked out the ScribeFire extension for Firefox?

Yes I did. It supports image posting to an FTP address but not directly to Blogger (Picasaweb) as of now. It looks like this kind of an extension is one of the best ways to go. I recently left a message to the developer(s) about their plans. I am waiting for them to say something about their roadmap. I also suggested help for development. If they plan to support such a thing, I might change my mind. ;)

---

### Post by BloGTK on 2008-06-08
> **darxoul said:**
> as far as I know you cannot post to a blog via openoffice. What i am looking for is a blogging application, i am not thinking of a web site. it is easier to just write and send. and it won't be possible to send images, video and mp3 using openoffice. correct me if i am wrong.



yes i checked blogtk. it doesn't support the features that i am looking for. i send an email to the developer to discuss some issues. the last time it has been updated is about 2 years ago, and he writes in a blog post that he is thinking of refactoring the code to support new features. so i am waiting for his response before doing anything. anyway, i do not have that much time, so that is not a pain to wait for a response :)

thank you for your response by the way.

Sadly, BloGTK's in limbo. I'd love to finish 2.0, but every time Blogger changes its API I had to keep rewriting the code. The whole point of the Atom API was one API would work everywhere. Except MT uses their own scheme, Blogger now uses GData, WordPress uses another, etc, etc.

If the APIs would remain stable, I might consider a new version, but I just don't have the time to re-invent the wheel these days.

---

### Post by joey-elijah on 2008-10-16
> **BloGTK said:**
> Sadly, BloGTK's in limbo. I'd love to finish 2.0, but every time Blogger changes its API I had to keep rewriting the code. The whole point of the Atom API was one API would work everywhere. Except MT uses their own scheme, Blogger now uses GData, WordPress uses another, etc, etc.

If the APIs would remain stable, I might consider a new version, but I just don't have the time to re-invent the wheel these days.

Having just "discovered" BLOgtk! it's a shame to find out it's kinda going nowhere.

Out of all the blogging apps i found in my repo's BLOgtk was certainly the best - even if it blogger accounts couldn't use pretty much any of the features, it was nice to see what was there! 

You'd think (on a tangent) that the increase in more stab;e API's for social networking sites would make google think about keeping the blogger api a little bit more grounded to allow apps to be made to post to it. 

There's a great one i have in my OS X dashboard - but it's very limited. I can imagine an iPhone - heck even ANDROID - application allowing posting to blogger would be a terrific idea... especially if it allowed a more feature-ful opportunity supporting images etc. 

Anyway, i use BLOgtk anyway cos it's still the best out there. (Somewhat)

---

