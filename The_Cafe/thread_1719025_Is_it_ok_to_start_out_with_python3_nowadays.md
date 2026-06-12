---
title: "Is it ok to start out with python3 nowadays?"
date: 2011-04-01
forum: The Cafe
---

### Post by user1397 on 2011-04-01
I've been looking into learning how to program lately, I've already chosen python as my starting language.

I see that even though most distributions still employ copious amounts of python2.x and it is still the standard, there are a few distros that use python3 by default.

So what do you guys recommend? Starting out with python3 since it's going to become the standard anyway and I might as well be ahead of the curve?  Or should I play it safe and go for python2.x?

I do want to eventually do some gui programming, so I don't know if that helps or not.  If I do any gui programming it's gonna be on gnome (gtk+).  This actually brings me to my second question since I'm a bit confused on the subject...

Is pyGtk compatible with python3 as of right now? I also hear that the future of pyGtk is pyGObject (correct if wrong please)? what does that mean with respect to python versions?

I've tried googling these things a bit but I have't really gotten any straight answers, and it's all pretty confusing for me, so here's to me hoping that some more knowledgeable people in these forums can help a brother out.

---

### Post by linuxforartists on 2011-04-02
I can't really help you with the Python 3 vs. 2.x dilemma.  But if it makes you feel better, I've heard from several sources that Python is a great first language to learn.  

The book [Head First Programming]("http://www.amazon.com/Head-First-Programming-Learners-Language/dp/0596802374/ref=sr_1_1?s=books&ie=UTF8&qid=1301742253&sr=1-1") uses Python to teach programming.

More interestingly, I attended a seminar on mobile development.  During one segment, a team of mobile developers talked about how to get started.  They had created a cool iPad app.  

The head programmer said iOS apps use Objective-C.  But he actually recommended studying Python first.  A lot of the concepts and patterns carry over into other languages.  He remarked that Python also forced you to write clean code and other good habits.  Then if you do proceed to Objective-C, you'll pick it up much faster than if you dove in it from the start.

Good luck coding!

---

### Post by Neezer on 2011-04-02
Just keep in mind that switching isn't non-trivial. One thing that I have come across while using both languages that is actually a big deal is the print function...

in 2.x:

print "hello world"


in 3.0:

print ("hello world")


so a codde written for 2.x will not run in 3 if it uses a print function like that....good luck and have fun. I really can't comment on if one is better than the other. This is just a simple thing that I have come across that could cause an issue if you choose to use 2.x and then switch to 3.0.


on a side note, 

print ("hello world") will work in 2.x as well...

---

### Post by ssam on 2011-04-02
[http://wiki.python.org/moin/Python2orPython3](http://wiki.python.org/moin/Python2orPython3)

using gtk from python3 is a complex question. the gnome libraries are moving towards using gobject introspection ( [http://live.gnome.org/GObjectIntrospection](http://live.gnome.org/GObjectIntrospection) ) to generate language bindings. so nobody wanted to update the old manually generated bindings for python3. there is also the gtk2->gtk3 transition going on. the gobject stuff seems to be being used for something, but not really documented/stable yet ( [http://www.k-d-w.org/node/79](http://www.k-d-w.org/node/79) ).

(if someone does know some good docs for using the gobject introspection stuff to make gnome apps in python let me know)

so if you just want to learn python, it does not matter which you use, and you may aswell start with python3. if you want to do gtk stuff, now is an awkward time. if you need to write a python gtk app today, then you will have to use the old stuff (python 2, gtk2, pygtk).

i suspect in a years time python3 will be the obvious choice, but python2 will still be around.

---

### Post by user1397 on 2011-04-04
I guess I'll start with python 3 then, seems kinda pointless not to since it will eventually be the standard.  Thanks for the input everyone.

---

