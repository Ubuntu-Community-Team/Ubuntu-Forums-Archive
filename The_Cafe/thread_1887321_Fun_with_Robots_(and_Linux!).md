---
title: "Fun with Robots (and Linux!)"
date: 2011-11-26
forum: The Cafe
---

### Post by ve4cib on 2011-11-26
Several weeks ago I posted a thread/quasi-blog about the 2011 FIRA Cup in Taiwan.  FIRA, for those who don't know, is an international robotics competition.  A team from the University of Manitoba participated in HuroCup, an octathalon for humanoid robots that included:

- Sprint (run forwards and backwards)
- Marathon (follow a track for ~80m)
- Wall climbing (exactly what it sounds like; climb a wall equipped with grips)
- Weight lifting (carry CDs across a line without falling over)
- Obstacle run (navigate around obstacles without touching them)
- Penalty kick (dribble the ball and kick it into the goal)
- Lift and carry (carry a basket of weights over uneven ground)
- Basketball (throw/place a ball into a cup)

Since the old thread has been abandoned I figured I would create a new one to wrap things up in.

First off, our robot, Darwin, is a slightly modified commercial robot produced by a company called Robotis.  We designed custom arms for FIRA, and wrote all sorts of custom software.  Darwin is basically an Ubuntu-powered netbook with motors attached; the main motherboard has an Atom CPU running at about 1.2GHz.  A secondary motherboard with at AtMega128 is used to control the servos.

Darwin comes with a default installation of Ubuntu 9.04 (slightly old now, but everything works and we haven't bothered upgrading yet since we've only got the one robot right now).  He's got 20 motors (2 in the head, 2 in each shoulder, one in each elbow, three in each hip, one in each knee, and two in each ankle).  All the communication is done over an RS232 serial connection, making the robot pretty OS-independent in that respect.  A webcam in his face is controlled via v4l2.

[IMG]http://img.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/IMGP8731.jpg[/IMG]
*Me with Darwin, practicing for the basketball event*

On the software front we expanded heavily on the open-source framework that comes with the robot.  It's all implemented in C++ with obvious classes.  Extending the software is very easy.

For example, we rewrote the LinuxCamera class so make use of the OpenCV library to make our vision processing easier.

Fortunately at FIRA the events are designed to make vision pretty easy; everything is very vibrant, contrasting colours.  The marathon track is marked with white tape, the basketball is orange with a red basket, the obstacles for the obstacle course are blue, red, and yellow, etc...  Image processing consisted mainly of finding the largest area of the target colour.  (Next year we're planning on improving the vision so we rely more on shapes and less on colour.)

But enough about the software and hardware.  On to the competition!

FIRA 2011 was held in Kaohsiung, Taiwan.  Most teams were from Asia (Taiwan, Singapore, and Korea mainly), with one team from Canada (us), one team from the UK (University of Plymouth), and one team from Mexico.

[IMG]http://img.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/IMGP8871.jpg[/IMG]
*All the robots from the competition, including two "teen-sized" robots*

The events were all very high-stress.  Your robot has to be ready to go immediately, so little bugs, like dead batteries, cause major nightmares.  Each event is run twice, except the marathon.

Unfortunately our little Darwin did not perform terribly well the first couple of days.  The basketball (which I'd worked for months on) was a dismal failure the first day, the sprint was slow, and the weight-lifting didn't lift very much.

The next couple of days did go better though.  We finished 4th overall in the obstacle run (first on the second time the event was run, but a poor showing in the first trial bumped us off the podium).  We were in the middle of the pack on the basketball (we got 1/5 successful baskets on the second run -- almost 2/5, but the robot clipped the basket and was disqualified on one attempt), and finished a spectacular 2nd place in the marathon!

[IMG]http://img.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/IMGP8972.jpg[/IMG]
*Darwin and one of the robots from U Plymouth; even the robots made friends!*

Hats off to University of Plymouth for their record-setting runs in the sprint and marathon events.  They smashed the world record for the sprint, and beat us by about 1.5 minutes over 84m in the marathon to set that world record too.  (In defense of my own team, we also broke the old world record.  Plymouth just broke it by more than us.  Also, we wrote the entire marathon event code the night before the competition.  So FIRA 2012 should be a good rematch that we're all looking forward to.  Plymouth's robots can *move*!)

After FIRA a few teams went back to Taipei to participate in TIROS, an ad-hoc competition at the Taipei International Robotics Show.  We repeated the penalty kick, obstacle run, basketball, and marathon events there, in front of enormous crowds.

TIROS was a much lower-stress event.  The crowds were fantastic; competing with the other teams around is one thing, but when you've got an enthusiastic crowd taking hundreds of photos it's something else entirely.

Rather than rehash the entire event I'll just post some photos and links to some more videos.  If anyone has any questions feel free to ask.  I'll do my best to answer them!

**Videos**

[http://youtu.be/VQC0694Yhwk](http://youtu.be/VQC0694Yhwk)
*A montage of Darwin videos and stills from FIRA, TIROS, and the work in the lab*

[http://winnipeg.ctv.ca/servlet/an/local/CTVNews/20110909/wpg_morninglive_apps/20111123/?hub=WinnipegHome](http://winnipeg.ctv.ca/servlet/an/local/CTVNews/20110909/wpg_morninglive_apps/20111123/?hub=WinnipegHome)
*A short segment on the local news about Darwin and our robotics program*

[http://www.youtu.be/e9EhQw44mhM](http://www.youtu.be/e9EhQw44mhM)
*Darwin competing in the marathon event at TIROS in Taipei, a few days after FIRA*

[http://youtu.be/Q9eeZJYHGcw](http://youtu.be/Q9eeZJYHGcw)
*Darwin playing basketball at TIROS*

[http://youtu.be/XfFA8YCR_Q4](http://youtu.be/XfFA8YCR_Q4)
*Darwin's POV during the basketball event*

[http://youtu.be/EUOLOHhIsCA](http://youtu.be/EUOLOHhIsCA)
*Darwin's penalty kick skills at TIROS*

[http://youtu.be/XQxWUJHJg8I](http://youtu.be/XQxWUJHJg8I)
*Darwin going through the obstacle course at FIRA*


**Stills**

[IMG]http://img.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/IMGP8974.jpg[/IMG]
*Robots ready to start the marathon at TIROS*

[IMG]http://img.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/IMGP8849.jpg[/IMG]
*The team from the University of Plymouth*

[IMG]http://img.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/IMGP9177.jpg[/IMG]
*The team from the University of Manitoba*

[IMG]http://img.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/IMGP9118.jpg[/IMG]
*The four robots that went to TIROS from FIRA*

[IMG]http://img.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/IMGP8749.jpg[/IMG]
*All the participants at FIRA (well, as many as would fit in the frame)*


I would post more photos, but apparently we're limited to just 8 per post.  So instead here's a link to the whole gallery of all the pictures (over 1k) I took while we were there.  There are lots of touristy photos from Taiwan in there too.  And my camera's auto-numbering rolled over, so the last photos of the trip appear at the beginning of the album.

[http://smg.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/?start=all](http://smg.photobucket.com/albums/v215/laucian_meliamne/FIRA2011/?start=all)

---

### Post by hansdown on 2011-11-26
That looks like a blast,ve4cib.

Thanks for posting.

---

