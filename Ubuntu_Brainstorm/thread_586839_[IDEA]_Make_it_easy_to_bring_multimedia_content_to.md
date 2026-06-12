---
title: "[IDEA] Make it easy to bring multimedia content to a multimedia device."
date: 2007-10-22
forum: Ubuntu Brainstorm
---

### Post by Turgon on 2007-10-22
My idea is an easy interface to bring multimedia content from a computer, a local network or the internet to a multimedia device by both "direct transfer" and automatic syncronizations that can automaticly and transperent solve the compatibly problems different formates makes by converting to a format the given multimedia device supports.

This can be achived by including and extending conduit : [http://www.conduit-project.org/](http://www.conduit-project.org/).

I have written a full spec here: [https://wiki.ubuntu.com/Multimedia_syncronization%2e](https://wiki.ubuntu.com/Multimedia_syncronization%2e)

What do you guys think?

---

### Post by Gorlith on 2007-10-23
This idea is pretty good, and has definetly been seen around the forums in many variations. Personally I like the specifics of your plan.

I think with Hardy(8.4) being an LTS though this should probably be left for 8.10 though. That way focus can remain on fixing current functionality and catching up on all the old bugs.

If they DO get around to adding some nice new features I would love this one.

---

### Post by Turgon on 2007-10-24
> **Gorlith said:**
> This idea is pretty good, and has definetly been seen around the forums in many variations. Personally I like the specifics of your plan.

I think with Hardy(8.4) being an LTS though this should probably be left for 8.10 though. That way focus can remain on fixing current functionality and catching up on all the old bugs.

If they DO get around to adding some nice new features I would love this one.

Yeah, I for one has posted this idea before in different syncing threads. 

You might be right, but i'm hoping that we at least could have something in the reppos so that many users easily can try it out an help mature it. I have read a little bit on the conduit mailing list and it seems like they are going to or have already started making much of the stuff needed to do this, so it might just be a question of time. What I hope to see is that ubuntu in hardy or hardy+1 really integrates this nicely and help the conduit guys out if they need to, and even if it might not be ready for hardy doesn't mean that they can't start now.

---

### Post by Jc2k on 2007-10-24
Hi

Just thought i'd make my appearance as the token Conduit dev :-)

Like the spec because it has some specific details, (and because it builds on our platform :D)

I'm not really sure what to suggest for the spec. As you've said, this is basically the direction Conduit is headed in. I guess I would like to see more use cases. A new idea for an "easy" GUI were put forward and its important to see how will your use cases map on to that.

I also agree that I would not be happy shipping something this big and easy to get wrong out of the box in an LTS release. Think a package in universe would be a safer option. With lots of "OMG please be careful" warnings xD

---

### Post by bikeboy on 2007-10-24
A similar idea was produced during Gutsy development, you might find some good/bad points in there.
[https://wiki.ubuntu.com/PimSyncPlan](https://wiki.ubuntu.com/PimSyncPlan)

I have conduit 0.3.4 installed on here (took me quite a while to get all the deps for compiling) and it certainly has awesome potential. Probably among the most exciting early stage free-software projects around IMO. Bluetooth and Evolution plugins didn't seem to install for me (if they're available yet?), but I haven't had time to look into it.

---

### Post by Turgon on 2007-10-25
> **bikeboy said:**
> A similar idea was produced during Gutsy development, you might find some good/bad points in there.
[https://wiki.ubuntu.com/PimSyncPlan](https://wiki.ubuntu.com/PimSyncPlan)

I have conduit 0.3.4 installed on here (took me quite a while to get all the deps for compiling) and it certainly has awesome potential. Probably among the most exciting early stage free-software projects around IMO. Bluetooth and Evolution plugins didn't seem to install for me (if they're available yet?), but I haven't had time to look into it.

Its not the same plan, this one is about PIM syncing. If you look on the bottom of that spec, you will see that I have proposed my idea as an extention of this.

---

### Post by Turgon on 2007-10-25
> **Jc2k said:**
> Hi

Just thought i'd make my appearance as the token Conduit dev :-)

Like the spec because it has some specific details, (and because it builds on our platform :D)

I'm not really sure what to suggest for the spec. As you've said, this is basically the direction Conduit is headed in. I guess I would like to see more use cases. A new idea for an "easy" GUI were put forward and its important to see how will your use cases map on to that.

I also agree that I would not be happy shipping something this big and easy to get wrong out of the box in an LTS release. Think a package in universe would be a safer option. With lots of "OMG please be careful" warnings xD

I will add some more user cases when I have time.

Yes, but (I think this is what you mean) then as a separate package (conduit-extras of something). If it isn't to much, you could in general add some of you more scary things in there (from the CVS) so its easier (i tried to get you cvs going at one point, but there was one of the dependencies that wouldn't compile without breaking something else) to test them out and report bugs.

---

### Post by Turgon on 2007-11-01
Seem like much of what I have proposed is in the SVN version of conduit at this moment.

A nice link to show the progression:

[http://www.johnstowers.co.nz/blog/index.php/2007/10/31/one-thousand/](http://www.johnstowers.co.nz/blog/index.php/2007/10/31/one-thousand/)

Nice job!

---

