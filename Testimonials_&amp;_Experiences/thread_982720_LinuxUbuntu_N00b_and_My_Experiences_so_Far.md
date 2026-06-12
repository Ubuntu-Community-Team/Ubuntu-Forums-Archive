---
title: "Linux/Ubuntu N00b and My Experiences so Far"
date: 2008-11-15
forum: Testimonials &amp; Experiences
---

### Post by keithld on 2008-11-15
Wellllllllllllllllll, first... I'm running a Dual Boot with Windows XP on an AMD Dual Core Machine...

Sorry this is Long and as Verbose as I can get... If your Bored Easily, then this will bore you...

First off I think this is a great OS and Desktop tho I do wish there were a few more useful Apps preinstalled... (no biggie)

1. I started playing around (downloaded a bunch of games) and decided I'd mess with the screen saver... Opps!!!, I was going through everyone in the list until Ubuntu locked up... It locked up everytime I tried to get into the screen saver for about two days... Then "Magically" it seemed to fix itself and I could go in and I chose the "Flying Toasters" since they reminded me of my days on the ol' MAC OS 8 etc... Fun stuff I may say...

2. I tried to import all my Bookmarks from Firefox 2.0.??? from Windows via hitting the Host folder (Windows) and importing from there... Opps! Big Mistake that crashed Firefox in Ubuntu about every minute or so... So  found out I should delete the default Profile and create a new one so I did... Thennnnnnnnnnnnn!!! I "Copied" my bookmarks from PC Firefox and Pasted to my Ubuntu Desktop and then imported them... Ahhhhhhhhhh!! all is almost well but not quite... I had to move all my "Toolbar Bookmarks" from the newly created folder to the Default "Toolbar Bookmarks"... The first time this totally killed most of my Bookmarks (I have a few 100) and I couldn't delete them, hence the reason for the new profile (yes I did this: Delete bookmarks-(date).json files from the bookmarkbackups folder when you copy bookmarks.html to the profile and delete places.sql... Okay so that finally worked well and I am happy )... But!!!!

Now if I ever Click & Drag a "Favicon" from the address bar and put it in the "Toolbar Bookmarks" area it will show up at the bottom of the list and if I try to move it from there it will lock up Firefox everytime...  

No Biggie I can live with it until it gets fixed...

3. Okay I need some more stuff (Apps) to play with, well I install Audacity which I like in the Win environment and it was working nice then I thought I'd see if it "Records"... Not gonna happen!!!! it doesn't recognise my "Onboard Audio Card".. Oh well no biggie it's a free App after all (Donate to the project and I'm sure they'd offer more)... I'm still happy

4. I've seen on a few Tech Sites and heard from others about this "Desktop Cube" Graphics Effects thing that Linux can do... So what do I do, well of course I download the "Simple CompizConfig Settings Manager"... Hey!!!! I like the Eye Candy Just Like Everyone Else!!!!!!!

WOW!!!, that stuff is cool... (hmmm had to do a manual "FSCK" since on one of the Boots it failed... No Biggie...

5. Opps!!! "My Shift Key No Longer Works!!!" (yes I have a spare keyboard and it does the same).... Hmmm what the heck ever caused that problem... My My there have been a "Bunch of Udates" here in the last few days... Hmmm that the problem???

Nope!!!!... Did I try different settings in the Prefs "Keyboard Option?"... Well of course I did!!!! No Go...

6. Yes I searched the Net & Google and my underware drawer for every answer I could but nothing seemed to work, not even in Terminal: Sudo setkeybxmap /xorg (not sure if I posted that one right but I did enter it right when I found the original post)... So what did I do???

I waited a couple of days of course and looked here at the forums with no avail... No biggie since my "Shift Key" still works fine in WinBlows...

7. WOW!!! I have been getting a bunch of "Update Manager" Notices in the upper right panel but they are not the familiar Yellow Triangle with an "Explanation Mark" in it, No!!! it's a Puke orange or something like that when I click on it it goes and does a search and gives me "Errors on Packages" that are outdated or links that just don't work...  That's cool only they seem to show up a few times a day and nothing seems to be resolved if I bother to click on it...

8. Ho-Lee-Kow!!!!!!  (yes that was the name of a song my Band in L.A. recorded)...

My Shift Key is working again!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

What did I do to fix this???.. Well hell I don't know but I did choose a few option in the "CompizConfig Settings Manager" for some cool stuff like the "Paint Fire on the Screen" and the "Water Effect"... Whoah!!!!  those are cool...

Well after another day I disabled those two effects and went through a couple more useless updates and I figured "Let it Be" for a few days...

Yes the "Shift Key Still works!!!!"

So I guess the best thing I have learned about using Ubuntu 8.10 is just let things happen and in a day or so it will fix itself (or not) hehehe...

Ghost in the machine??? or Gremlins???


:guitar:

---

### Post by BlackDragonBE on 2008-11-15
Definitely ghosts.

---

### Post by 3rdalbum on 2008-11-16
Thanks for your testimonial. The situation with Audacity is worth explaining. There are lots of different ways of playing and recieving audio data on Linux. One is called OSS, another is called ALSA, and the latest one is called Pulseaudio. Unfortunately, these three sound systems conflict with eachother to various extents, and for some reason Audacity has always been affected with this. Just when the problem was starting to go away, Pulseaudio came along :-(

If you can turn Pulseaudio off, you might have some more luck. DO NOT UNINSTALL PULSEAUDIO as its disappearance will stop you from being able to log in.

Finally, I'd like to add that I also like Flying Toasters because it reminds me of the System 7 days :-)

---

