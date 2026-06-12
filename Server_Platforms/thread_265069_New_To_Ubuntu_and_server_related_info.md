---
title: "New To Ubuntu and server related info"
date: 2006-09-25
forum: Server Platforms
---

### Post by LiquidSmokeSL on 2006-09-25
Hello everyone. I want to setup a server so that my friends and family can share things. Another reason I want to create a server is for a game I play. We have a website. Not sure what kind of program but they tell me its been backed up. Someone else was running it on thier works server....got in trouble so now we have no guild site to go to. So I thought I would make a server for us to hoste the guild site and forums on. I have downloaded Ubuntu server. I am pretty sure I can get it to install. Except that it runs off the CD Rom and it must remain in drive to run the program? How can I make a server? The easiest way would be great. I have no clue about this stuff.

---

### Post by tuxthepenguin on 2006-09-25
Well your going to need to install the server not just run it from the CD. Afterwords I'm assuming you want to turn it into a webserver. Just apt-get install apache should do it. Check out the apache website for info on how to set it up. 

In my opinion if you hosting this from you house on Cable/DSL its not gonna have the upload bandwidth that you need for hosting a website. Plus your going to have to enable port forwarding on your router to point to the server that has apache running. Then if your ISP changes your IP address...

Basically what I'm saying is you might want to just look for someone to do your hosting for you.

---

### Post by Child of Wonder on 2006-09-25
Once you have booted to the CD there is an install link on the Desktop.  Use that to install Ubuntu.

Just let it automatically partition your drive.

Once your server is installed, remove the CD, and boot to the server.

Go into Synaptic Package manager and search for and install Apache2 for a web server.

As tux said, if you're running this from home, don't have a static IP, and have less than 512Kb upload speed, just get your site hosted somewhere online for $0-$10 per month.

---

### Post by tuxthepenguin on 2006-09-25
I recommend [http://xstreamhost.com/]("http://xstreamhost.com/")
Great service and can be as cheap as $3 a month. I've been using them for years.

---

### Post by LiquidSmokeSL on 2006-09-25
Thanks a lot guys. Sounds more involved. I defintly want to play around with this some more for the fun and learning. But, ur prob right on just paying for it. I have reaaly good cable package, its upgraded to the next level, the only higher level of cable service I can get is the business class. Which for a forums website, very very little graphics and its only in a few colors would probaly be effiecent. Its all forums with multiple threads. Some pics people load up but they have to be less then 128kb.  

there is like maybe 60 people that go to it through out the week and usually no more then 7 or 8 logged on at any one time. For now I will pay for it. But if I were to get it sucessfully hooked up and ready, could i have the power to hoste a forum site?

---

### Post by chrisfay on 2006-09-25
[This may help get you started...]("http://cjfay.com/lamp.html")

---

