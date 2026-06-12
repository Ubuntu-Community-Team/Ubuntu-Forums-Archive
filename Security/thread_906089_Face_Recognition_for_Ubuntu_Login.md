---
title: "Face Recognition for Ubuntu Login"
date: 2008-08-31
forum: Security
---

### Post by bdfoster on 2008-08-31
Ok so here it goes...
I've been doing alot of research on face recognition. As I am learning more and more about Linux, I wonder how face recognition would work on Ubuntu. I have a few ideas on how this could work.

1. Use bluetooth from a mobile phone, and when that comes into range, it would tell the program what face it should be looking for, and initiate the webcam to start picking up images.

2. Have the program always be scanning for images and comparing at the same time. When it detects a face, have the program look through a database, then allow access.

3. Use your ID as a way to gain access to the computer. Since you should be carrying this with you at all times, it can be used as the key. It could recognize the picture along with the DL number or something like that.

4. Same as 2, except use some techniques to detect whether it is a photo or not. Like detect if the face is moving at the same speed as something in the background of the picture. Or if it is a stationary computer (desktop), it could detect in the abrupt change of scenery. 

Other ideas presented on this thread...

1. Prison photo system. User would have to turn to the left and right as well as a frontal shot so that it would be harder to use a photo of someone.

2. Use two cameras so that it could detect head movement.

3. Use thermal imaging. -Not cost effective.
All of this could be implemented just by switching the login screen for Ubuntu or something to that effect.

Anyway this is as much as I can come up with. As I said before I have done research and they have a program like this in Windows, but not to this degree. Somehow, it needs to know that the face isn't a photo or isn't the right photo. I'm looking to facilitate the development of this but I am not a programmer. I just want to brainstorm and get some ideas and the interest of some developers. 

Any ideas?

---

### Post by Paradoxfox93 on 2008-08-31
I know nothing of how this sort of this works but wouldn't you have to run some kind of motion detection to discern real movement and  from 2D picture?

Or  randomly demanded semi-profile of at least three different angles.

Although, if 'they' have you tied up and fed a camera that could produce profiles of your face on demand...

however such it would seem would only be added security for physical access so naturally it would go hand in hand with one hell of an encryption code i assume.

Of course....nothing really beats aes-256 with a 40 char hashphrase

---

### Post by bdfoster on 2008-08-31
> **Paradoxfox93 said:**
> I know nothing of how this sort of this works but wouldn't you have to run some kind of motion detection to discern real movement and  from 2D picture?
It would have check reference points across the image so it would have to be better than a simple motion detector. 

> Or  randomly demanded semi-profile of at least three different angles.
Like prison? That might be a good idea.

> Although, if 'they' have you tied up and fed a camera that could produce profiles of your face on demand...
Not all to concerned with that...really. Even though this would go hand in had with some other security measure. 

> however such it would seem would only be added security for physical access so naturally it would go hand in hand with one hell of an encryption code i assume. The idea is to be able to walk up to a computer and login without much of a password or encription code. 

> Of course....nothing really beats aes-256 with a 40 char hashphrase

---

### Post by Biochem on 2008-09-02
I'm no expert but it seems to me that the simplest way to detect if it's a picture or not is to use more than one camera. That way you can get a better representation of 3D structure and it become very complicated to presents multiples picture taken at the right angles that moves (our head is never completely still) in a coherent manner.

Now if you have 2 standard camera (one on each side of the screen) and a central thermal camera that detect body heat that would make even harder.

But that will take a hell of an algorithm.

---

### Post by Pro-reason on 2008-09-02
Hey, but they could still cut your head off and use that.

Your fancy face recognition don't look so clever now, does it? eh?  :lolflag:

---

### Post by bdfoster on 2008-09-02
Here's the thing. It can't be too complicated or no one would want to implement it because they could just use a fingerprint reader. Very interesting idea I might add. But it isn't very cost-effective. Even though the software would be free, the hardware wouldn't.

---

### Post by bdfoster on 2008-09-02
> **Pro-reason said:**
> Hey, but they could still cut your head off and use that.

Your fancy face recognition don't look so clever now, does it? eh?  :lolflag:

We'll get to that.

---

### Post by Biochem on 2008-09-03
> **Pro-reason said:**
> Hey, but they could still cut your head off and use that.

Your fancy face recognition don't look so clever now, does it? eh?  :lolflag:

No if you use thermal camera. A decapited head would be cold, thus not registering.

Anyways it'S always easier to kidnap and torture the kids of the target. They'll do anything to save them... Works with long complicated password and finger print too or any other security schemes you might think off! The point is that the user is always the weakest link.

---

### Post by bdfoster on 2008-09-04
> **Biochem said:**
> No if you use thermal camera. A decapited head would be cold, thus not registering.

Anyways it'S always easier to kidnap and torture the kids of the target. They'll do anything to save them... Works with long complicated password and finger print too or any other security schemes you might think off! The point is that the user is always the weakest link.

> **Pro-reason said:**
> Hey, but they could still cut your head off and use that.

Your fancy face recognition don't look so clever now, does it? eh?  :lolflag:

Can we stay on topic please? I know it's funny and all and I'm all about fun but this is a serious topic and I want to seriously get rolling on the development of a program.

I do however think that we should start with a simple face recognition program that measures relative distances between landmarks on a face. Then we should add on to it with security features. We should concentrate on keeping the cost low on implementation atleast at the beginning.

Do I have any programmers in the house that needs a project?

---

### Post by thevikas on 2008-09-04
your project is very interesting and so are the jokes.
specially, the bluetooth based activation is very good.
it will give a little rest the CPU (though now instead of image scans its busy with detecting bluetooth devices and jamming the bloody room all the time!)

have you started on any code?

---

### Post by bdfoster on 2008-09-05
> **thevikas said:**
> your project is very interesting and so are the jokes.
specially, the bluetooth based activation is very good.
it will give a little rest the CPU (though now instead of image scans its busy with detecting bluetooth devices and jamming the bloody room all the time!)

have you started on any code?

No, I haven't. I'm a newb on linux although I am excellent with windows. Since I like to experiment alot, windows was just not stable enough.

I am not a programmer of any sort so I don't have that kind of experience. If you are interested in helping develop this program please PM me.

---

### Post by HermanAB on 2008-09-05
A laptop with a built-in camera (Eee PC) would be a good one to experiment with.  There is a program called 'motion' that will capture pictures and post them on a web server whenever there is movement in the camera field of view.  That may provide you with a starting point.

Cheers,

Herman

---

### Post by bdfoster on 2008-09-05
> **HermanAB said:**
> A laptop with a built-in camera (Eee PC) would be a good one to experiment with.  There is a program called 'motion' that will capture pictures and post them on a web server whenever there is movement in the camera field of view.  That may provide you with a starting point.

Cheers,

Herman

I do have a laptop with a built in webcam, but not an Eee PC. I've heard of those. Anyway the motion program I do have so we could start there. Obviously it wouldn't be very effective unless you wanted to know who logged in so maybe that should be an option.

---

### Post by njsanders1 on 2009-02-23
For what it's worth, ASUS ships a facial recognition application for Vista on their laptops.  (I had an M70S that came with this bundled.)  They call it "Smart Login" or something like that, and it gives you the choice of facial, fingerprint, or typed credentials.  I would love to see something like that for Ubuntu, with ideally having the option to require two of three for authentication.

As for the ASUS app, when you registered an image, it would store up to 45 images, which is how they accounted for motion and angle.  It took 15 stills each time you told it to record an image.  When the computer was locked or otherwise waiting for login, the app scanned the cam's field of view to find a discernable face in the image, and then would automatically begin processing whatever face it found for verification of ID.

I would think that something like this, if done correctly, could have huge commercial potential in the Linux world.

---

### Post by vrangforestillinger on 2009-02-23
> **Researchers hack biometric faces**
Vietnamese researchers have cracked the facial recognition technology used for authentication in Lenovo, Asus, and Toshiba laptops in lieu of the standard logon/password.

[http://it.slashdot.org/article.pl?sid=09/02/17/216216](http://it.slashdot.org/article.pl?sid=09/02/17/216216)

---

### Post by Dave_Connor on 2009-02-24
Not to be a spoil sport but isn't this type of security much more open to flaws then tradition password ?

---

### Post by njsanders1 on 2009-02-25
I had often wondered if a static image (I.e., photo) could be used to bypass the facial recognition, and my guess that it *could* was apparently correct, so thanks for sharing.  But therein lies my reasoning for a two-pronged approach to authentication.  Plus, different systems require varying depths of security, and in some cases, the convenience of facial recognition outweighs the risk.  For example, on my desktop at home, I am not concerned about my 10 year old (or even my wife) using a photo to "hack" into my computer and read what I bought them for Christmas or sneaking into my office to get on the Internet past bedtime.  

The commercial viability, given a second prong of authentication (whether with credentials, fingerprints, voice, etc.), is still a considerable factor, particularly if the work started by Asus and others (presently proven  to have some inadequacies) could be improved upon in a Linux build.

---

### Post by x3roconf on 2009-02-28
> **Paradoxfox93 said:**
> 
Of course....nothing really beats aes-256 with a 40 char hashphrase

torturing beats..;)

---

### Post by monks700 on 2009-03-29
I would like this especially since I am probably going to get an eeepc. I wouldn't want this for extra security I would just want it for convenience as I would be bringing it to school and I would want to just open it, have it see me and log in.

---

### Post by filtro_tuc on 2009-04-10
The point 1 (use the bluetooth to detect) you can use BlueProximity available on Ubuntu

---

### Post by Psychopump on 2009-04-16
There is a wondoze app that does this called "LemonScreen"...
Could it be ported to *nix?

---

### Post by sdpiowa on 2009-10-20
Some face recognition programs simply have you blink your eyes to determine if it's a picture or not.

---

### Post by iamuser_2007 on 2011-06-27
Here you can find the Pam-Face-Authentication Tutorial and commands, Try it

[[COLOR="Red"]Face Recognition Login Ubuntu(All Versions)[/COLOR]]("http://noobslab.com/2011/06/facial-recognition-ubuntu.html")

---

