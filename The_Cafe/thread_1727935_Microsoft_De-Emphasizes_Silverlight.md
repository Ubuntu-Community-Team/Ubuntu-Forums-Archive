---
title: "Microsoft De-Emphasizes Silverlight"
date: 2011-04-13
forum: The Cafe
---

### Post by Lucradia on 2011-04-13
[http://news.cnet.com/8301-10805_3-20053285-75.html](http://news.cnet.com/8301-10805_3-20053285-75.html)

Well that's great news.

---

### Post by user1397 on 2011-04-13
Thank god, although this probably means little for netflix's use of silverlight, as it is used mainly for DRM and I do not think html5 can provide DRM :popcorn:

---

### Post by Lucradia on 2011-04-13
> **ubuntuman001 said:**
> Thank god, although this probably means little for netflix's use of silverlight, as it is used mainly for DRM and I do not think html5 can provide DRM :popcorn:

JavaScript can? What about PHP hash checking? :P

---

### Post by Paqman on 2011-04-13
Bizarrely, my wife ran into a site the other day that has *just switched* to Silverlight ([http://www.getamap.ordnancesurveyleisure.co.uk/](http://www.getamap.ordnancesurveyleisure.co.uk/)). Wtf? Why switch now? Must be a purchasing decision that got stuck in the pipe for waaaaay too long.

---

### Post by user1397 on 2011-04-13
> **Lucradia said:**
> JavaScript can? What about PHP hash checking? :P

I actually don't know, but it seems as if you do.  Could netflix use javascript and/or php scripting to achieve the same effect it does with silverlight? That would be interesting to know.

---

### Post by Spice Weasel on 2011-04-13
Good.

Flash and Silverlight based websites really annoy me. Any web developer that chooses solely Flash or Silverlight for a website should be brutally punished, preferably in the form of a public burning.*


*Note: Please don't take this the wrong way if you have chosen to do this.

---

### Post by sdowney717 on 2011-04-13
good news for netflix users. Finally hardware accelerated video
[http://weblogs.asp.net/scottgu/archive/2010/12/02/announcing-silverlight-5.aspx](http://weblogs.asp.net/scottgu/archive/2010/12/02/announcing-silverlight-5.aspx)

I was thinking perhaps Netflix could not have gotten so much content for streaming unless the DRM in silverlight was used.
But it is what it is and the owners of the media are what they are.


> Premium Media Experiences

We are seeing great adoption of Silverlight for premium media solutions. In the last few months we&#8217;ve seen companies like Canal+, TV2, and Maximum TV launch both live and on-demand Silverlight solutions.

Silverlight 5 will enable media experiences to go even further by adding:

    Hardware video decode: Silverlight 5 now supports GPU accelerated video decode, which significantly reduces CPU load for HD video.  Using Silverlight 5, even low powered Netbooks will be able to play back 1080p HD content

    Trickplay: Silverlight 5 now enables variable speed playback of media content on the client with automatic audio pitch correction. This is great for training videos where you want to speed up the trainer while still understanding what he&#8217;s saying

    Improved power awareness will prevent screensavers from kicking in while you&#8217;re watching movies while allowing the computer to sleep when video is not playing.

    Remote-control support is now built-into Silverlight 5 - allowing users to control media playback with remote control devices.

---

### Post by Lucradia on 2011-04-13
> **ubuntuman001 said:**
> I actually don't know, but it seems as if you do.  Could netflix use javascript and/or php scripting to achieve the same effect it does with silverlight? That would be interesting to know.

Netflix could use PHP/MySQL and JavaScript + HTML5 to do DRM and GPU acceleration. PHP would provide hash checks for MD5 if they put DRM into MD5, and the MySQL DB could store all the hashes, and settings for all users (you can use serialize / explode to cover up user settings so that even the admins couldn't see what user had what setting, but the server would.)

---

### Post by CraigPaleo on 2011-04-13
> **Lucradia said:**
> Netflix could use PHP/MySQL and JavaScript + HTML5 to do DRM and GPU acceleration. PHP would provide hash checks for MD5 if they put DRM into MD5, and the MySQL DB could store all the hashes, and settings for all users (you can use serialize / explode to cover up user settings so that even the admins couldn't see what user had what setting, but the server would.)

Would that be able to keep people from saving it once they've paid for access? I know with JS, you can keep people from right clicking but there are ways around that.

Edit: This is driving me nuts. I've been reading up because I really don't know that much about it. There is so much conflicting info on the subject. I've read that DRM is incompatible with HTML5 but then possible with HTML5. I've read that DRM is incompatible with open source but then I find: [http://sourceforge.net/projects/openipmp/](http://sourceforge.net/projects/openipmp/)
Time to hit my pillow! :)

---

### Post by gnomeuser on 2011-04-13
Ah yes, this is productive. Let's hate on a piece of technology based on its origins rather than its merit.

---

### Post by _outlawed_ on 2011-04-13
> **gnomeuser said:**
> Ah yes, this is productive. Let's hate on a piece of technology based on its origins rather than its merit.

Usual bandwagon stuff. :P

---

### Post by Spr0k3t on 2011-04-13
They've been quietly slowing development, advertising, force-feeding the role of silverlight for about a year now.  The first web site to roll out the use of silverlight doesn't even use it anymore (MLB.com).  Many of their fans were upset on the initial launch of the silverlight pages.  I don't think any of Microsoft's own pages require silverlight... just proving what they think of their own product.

---

### Post by Grenage on 2011-04-13
I don't think Silverlight is going anywhere soon, just as Flash isn't going anywhere soon.

---

### Post by Paqman on 2011-04-13
> **gnomeuser said:**
> Ah yes, this is productive. Let's hate on a piece of technology based on its origins rather than its merit.

Some zealots are probably doing just that, but I think the average user has every right to dislike Silverlight. Being forced to install any software just to access content online is annoying. Flash is tolerated because it's ubiquitous, and therefore very useful once installed. Silverlight is just a speed bump on the internet, and from the end user's perspective doesn't seem to offer them anything that couldn't be done with Flash anyway.

It's just an attempt by Microsoft to carve out a piece of the pie for themselves. That's fine as a business strategy, but isn't likely to inspire users.

---

### Post by Lucradia on 2011-04-13
> **Spr0k3t said:**
> I don't think any of Microsoft's own pages require silverlight... just proving what they think of their own product.

You're right. It used to be that their main page used silverlight, where that rotation thing is: [http://www.microsoft.com/en-us/default.aspx](http://www.microsoft.com/en-us/default.aspx)

---

### Post by NMFTM on 2011-04-13
> **gnomeuser said:**
> Ah yes, this is productive. Let's hate on a piece of technology based on its origins rather than its merit.
The difference is, Adobe provides a version (alibet, a very crappy one) of Flash for Linux. While Microsoft doesn't. There is the Moonlight project, but it isn't as advanced as the official Silverlight. That map website one person posted earlier in the thread wouldn't even load for me after installing Moonlight. Plus, Moonlight by nature is always reactionary. Microsoft could, if Silverlight came to replace Flash, try to implement features that would be very hard for the Moonlight people to clone in an attempt to leave Linux users out in the cold.

---

### Post by sdowney717 on 2011-04-14
> if Silverlight came to replace Flash
I do think that was their intent, to muddy the waters, mess up the playing field for linux and other non MS related systems. But it did not work out that way. MS was cold on HTML5 video BUT now seem to embrace it. 
Perhaps flash is not too bad today on linux. For me flash mostly just works.
I do have full screen flash sometimes opening behind underneath all my other windows.

---

### Post by MisterGaribaldi on 2011-04-14
> **Spice Weasel said:**
> Any web developer that chooses solely Flash or Silverlight for a website should be brutally punished, preferably in the form of a public burning.*


*Note: Please don't take this the wrong way if you have chosen to do this.

Hey! Do ***not*** apologize. Organizations and individuals who buy into a one-size-fits-all package deal are single-vendor idiots in the first place. Whether that has to do with their web development technologies, or who they buy hardware from, or some other element of their business model, it all comes down to the same thing.

If it sounds like I come from the land of "been there, done that" you're absolutely right. I hate lock-in.

---

### Post by gnomeuser on 2011-04-14
> **Spr0k3t said:**
> They've been quietly slowing development, advertising, force-feeding the role of silverlight for about a year now.  The first web site to roll out the use of silverlight doesn't even use it anymore (MLB.com). 


People dislike change, and given that it is the first of anything, problems should be expected.

Silverlight is more than just the web, and while Microsoft have been refocusing their development to their needs for Windows Phone 7 it doesn't mean Moonlight is any less capable or any less able to add functionality if any is required by website developers.

> 
Many of their fans were upset on the initial launch of the silverlight pages.


citation needed, I am sure a bunch of pointless FSF supporters were insulted, after all they seem to hate everything Microsoft does on principle. However I suspect most users just carried on browsing, Silverlight is a simple download and works well for the majority of people. 

> 
I don't think any of Microsoft's own pages require silverlight... just proving what they think of their own product.

This argument has been brought up since the day Silverlight was released. The Microsoft web resource is huge and has taken years to develop and implement. They are likely understandably unwilling to start over, it is a different team, with established tools and they do drive one of the biggest sites in the world.

It is like saying Google's failure to do 100% of their websites in HTML5 is a clear sign that it is a failed standard.

Just because something is new and shiny, and moving to it would be a PR win for someone, doesn't mean it is a good idea for you to do so.

Here is what I ask:

1) Disassociate the struggle for open video formats from the web framework battle. It doesn't matter if HTML5, Flash, JavaFX, Silverlight or who ever wins, this is a battle we will be unable to avoid having at some point. HTML5 has no standardized codec and fighting fiercily for it does not make this so. You have the same choice of implementing codec support in Silverlight 3 as you do in HTML5, namely total.

2) Instead of bashing Silverlight for having it's origin at Microsoft, pick something technical to complain about. Given the focus on 1 and the blind hatred of the FSF supporting crowd, there has been very little in terms of technical review of any of the major competitors presented.

3) Stop complaining about Netflix, their use of DRM is not  Silverlight's or Microsoft's problem. This is another independent struggle, DRM is harmful outside of web frameworks and the best approach is clearly to approach it as it's own problem.
Even if Netflix never gets to work under Linux Moonlight still has plenty of merit, e.g. it is a fantastic toolkit for building UX.

---

### Post by Dupointx on 2011-04-14
</sarcasm> What is Silverlight and why should I care? <sarcasm/>

But seriously, I've installed it on Windows in the past thinking, "maybe I'll need it for a web page." Then after months I never used it. Then when I reformatted Windows I was like "why bother installing it."

So, not surprised by this.

---

### Post by Lucradia on 2011-04-14
> **Dupointx said:**
> </sarcasm> What is Silverlight and why should I care? <sarcasm/>

But seriously, I've installed it on Windows in the past thinking, "maybe I'll need it for a web page." Then after months I never used it. Then when I reformatted Windows I was like "why bother installing it."

So, not surprised by this.

Pre-loaded OSes come with silverlight now, with at least version 3. My ASUS Tower did, and I can't wait to get OEM Windows 8 next year or something.

---

### Post by wrtpeeps on 2011-04-15
I think all Windows Phone 7 app's use Silverlight (or at least they did), so it's not going anywhere soon. 

I think it's still used on xbox.com too?

---

### Post by Giant Speck on 2011-04-15
> **wrtpeeps said:**
> I think all Windows Phone 7 app's use Silverlight (or at least they did), so it's not going anywhere soon. 
Almost right.  Apps for Windows Phone 7 must be based on either XNA *or* Silverlight.  Still, your point still stands.  If Windows Phone 7 ever takes off, that is.

---

