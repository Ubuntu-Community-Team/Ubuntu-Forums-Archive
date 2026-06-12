---
title: "create side by side video's ???"
date: 2010-03-08
forum: Ubuntu Studio
---

### Post by extendedping on 2010-03-08
ok a quick rant and then please some help...nyc is becoming a place where the city government is just out to stick it to taxpayers. if you don't believe it well [http://www.youtube.com/watch?v=qMco2HBQQd4](http://www.youtube.com/watch?v=qMco2HBQQd4) come live in an outer borough. well anyway. I need some help combining 2 avi videos side by side. I got 2x tickets for $120 for parking in a no parking zone. I have parked on that street for years. I took 40 pictures of the block (there was no sign) and took a video of the block end to end. no sigh, down to the queens traffic court I went, showed my pics and a walking video of the block end to end. no sign. the judge refused to throw out the ticket. 4 days later a sign appeared on the street. went back and took another video, the exact same walk now you actually bump into the new sign with the camera. well anyway (rant over), I now want to make one video of the 2 avi files side by side or one on top of the other. I have downloaded 2 programs cinelerra and avidemux but having never edited a video before I am kind of lost as to how (or if) there are any linux programs that can do this. sorry for the rant I know it was inappropriate but I will post the video's when I am done it is really pretty outrageous that the city would try to stick it to a taxpaying citizen like this.

---

### Post by wkulecz on 2010-03-09
I can't specifically tell you how to do it on Linux, but generally this would be a case of "Picture In Picture" video.  You may need to create a single color background track and then resize the two videos for two PIP overlays -- side by side or top and bottom.

Its more difficult if you have to have final 4.3 or 16:9 aspect ratio for playback - finding the "correct" re-size or crop to show what you want.  Otherwise for a computer playback you can create a 640x960 "stacked" output that will play nicely on a 1280x1024 or larger screen from a pair of 640x480 videos.

Search the docs to see if your editor does PIP, if it does you should be fine once you learn it.

HTH,
--wally.

---

### Post by extendedping on 2010-03-10
thanks I have not been able to figure it out yet. btw I lost the case, the manhattan judge admitted the city put in a sign 4 days after queens court refused to throw out the ticket. but the judge says that I was still parked illegally. I told him 
a) then why did the city put a second sign days after a appealed the ticket. he had no answer. then I said, 
b) so according to you logic every car on that street for years should have been ticketed every day. he said guess so and threw me out of his court room. its not over (my city councilman has agreed to look into it). rant over.

---

### Post by madfirefighter on 2010-03-10
Sorry for your dilemma. No advice on how to do the avi's. I'm a noob to that sort of thing but since you are ranting about the ticket then welcome to the new way of govt. Tax and rob the little man to death and give them no voice.

---

### Post by LuridCinema on 2010-03-10
Fairly easy in Cinelerra. You zoom in on the projector on video 1 track 1 and shift to the right. you zoom in on the projector of video2 track to and keep it to the left...... then render. viola ! split-screen.

---

### Post by extendedping on 2010-03-11
> **LuridCinema said:**
> Fairly easy in Cinelerra. You zoom in on the projector on video 1 track 1 and shift to the right. you zoom in on the projector of video2 track to and keep it to the left...... then render. viola ! split-screen.

thanks, since I have never worked in video editing I hope these are easy menu finds...I will try it tonight.

---

