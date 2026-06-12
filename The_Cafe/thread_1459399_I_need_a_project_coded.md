---
title: "I need a project coded"
date: 2010-04-21
forum: The Cafe
---

### Post by whistlingtony on 2010-04-21
Hello world!

Heh. So, I had an idea for a piece of software that I wanted coded. Unfortunately, it's been years since I touched that stuff. I'm beyond rusty. I'd really like for the thing to see the light of day, but... 

How can one go about hiring a programmer? A quick google search turned up a couple of websites, but they seemed... sketchy.

My Idea:
I hate facebook. I hate it with a passion. Still, I'd like to put up an online journal website for friends and family to check up on me. I'd prefer to run it myself. I don't want to deal with huge config files. I don't want to write HTML. I'm 31 now. I just want my software to work.

I'd like to have a web server written for me in Python. I enjoy python and once the thing is written, then I could tinker and poke at it.

I'd like for me to have some folders. In the "Front Page" folder would text files. The web server would put those up as updates to the main page. Other folders would have text and pictures in them, and those would be links from the main page. I'd like to keep it simple, no flash or moving objects or anything.

Eventually I'd like to move it to HTML5 so videos could be posted in the same manner.

That's it really. A simple web server that creates pages based on the text and picture content of folders and organized by folders. A bare minimum configuration file, preferably none at all. I want it programmed in Python. Preferably, I'd want everything served up in HTML5. I'd also want the rights to open source the thing.

I have money. How do I give it to someone to do this?

-Tony Diethelm
Hater of Facebook

---

### Post by whiskeylover on 2010-04-21
Web server in python? Whats wrong with apache?

---

### Post by Penguin Guy on 2010-04-21
> **whiskeylover said:**
> Web server in python? Whats wrong with apache?
I believe he means he wants a content manager.

By the way, I'm in the same situation as you (wanting a dead simple text-file-based content manager), and am planning on writing a PHP/Javascript content manager when I get the time. Maybe we could start a launchpad project and see if we can get a few open source people involved?

---

### Post by Ozor Mox on 2010-04-21
Sounds like you want a content management system like [Joomla](http://www.joomla.org/) or [Drupal](http://drupal.org/). You can run a website and post content, all through a nice user interface without touching code and config files.

---

### Post by undecim on 2010-04-21
> **Ozor Mox said:**
> Sounds like you want a content management system like [Joomla](http://www.joomla.org/) or [Drupal](http://drupal.org/). You can run a website and post content, all through a nice user interface without touching code and config files.

+1 to Joomla. I've used it before and love it.

Never used Drupal though. 

Just get a free web host with PHP and install Joomla (most hosts have an auto-installer or some sort)

---

### Post by kvsm on 2010-04-21
> **Ozor Mox said:**
> Sounds like you want a content management system like [Joomla]("http://www.joomla.org/") or [Drupal]("http://drupal.org/"). You can run a website and post content, all through a nice user interface without touching code and config files.

Sounds like he's after something much simpler than Joomla or Drupal, they aren't exactly zero-config systems.

Tony: When you say you want to run it yourself, do you mean from a machine at your home that you'll leave connected to the internet so that people can access it?  The alternative is paying for web hosting (which is probably a better option).

If you go for web hosting you will most likely get access to an Apache web server - not written in Python, but I think that you really mean you would like the web application written in Python rather than the web server itself.  Apache has a module for running web apps written in Python, but this would need to be enabled by the web host, and I don't recall coming across a web host that supports this by default.

Still, I'd be interested in helping out with a project to create a simple web app like this, if nobody can find something which fits the bill.

---

### Post by LowSky on 2010-04-21
Couldn't you just create a wordpress account?

---

### Post by sau99ms on 2010-04-21
> **whistlingtony said:**
> Hello world!

Heh. So, I had an idea for a piece of software that I wanted coded. Unfortunately, it's been years since I touched that stuff. I'm beyond rusty. I'd really like for the thing to see the light of day, but... 

How can one go about hiring a programmer? A quick google search turned up a couple of websites, but they seemed... sketchy.

My Idea:
I hate facebook. I hate it with a passion. Still, I'd like to put up an online journal website for friends and family to check up on me. I'd prefer to run it myself. I don't want to deal with huge config files. I don't want to write HTML. I'm 31 now. I just want my software to work.

I'd like to have a web server written for me in Python. I enjoy python and once the thing is written, then I could tinker and poke at it.

I'd like for me to have some folders. In the "Front Page" folder would text files. The web server would put those up as updates to the main page. Other folders would have text and pictures in them, and those would be links from the main page. I'd like to keep it simple, no flash or moving objects or anything.

Eventually I'd like to move it to HTML5 so videos could be posted in the same manner.

That's it really. A simple web server that creates pages based on the text and picture content of folders and organized by folders. A bare minimum configuration file, preferably none at all. I want it programmed in Python. Preferably, I'd want everything served up in HTML5. I'd also want the rights to open source the thing.

I have money. How do I give it to someone to do this?

-Tony Diethelm
Hater of Facebook

What about Google Sites? Would that do the same job as you're looking to achieve?

---

### Post by Simian Man on 2010-04-21
There are so many ways to do this that writing custom software for this would be insane.

---

### Post by Penguin Guy on 2010-04-21
> **Simian Man said:**
> There are so many ways to do this that writing custom software for this would be insane.
I don't really see your point there.

---

### Post by tgalati4 on 2010-04-21
Hardy server is not difficult to install.  LAMP is not difficult to install.  Drupal is not difficult to install.  You will need those three pieces to have a robust, scalable web content system.

HTML5 is a new framework.  The issue is getting all of the other browsers out there (such as Windows Internet Explorer) to get wider adoption.

If you don't want to set up your own server, then just sign up for a wordpress account, or any of a dozen other blogging acounts.

---

### Post by lovinglinux on 2010-04-21
+1 for Wordpress

I have been using Joomla extensively for a couple of years, but since I started using Wordpress, managing my web sites became a lot easier.

---

### Post by GooglePlexity on 2010-04-21
You might be interested in this light-weight CMS that runs on Django: [http://www.mcnabbs.org/andrew/smug/](http://www.mcnabbs.org/andrew/smug/)

---

### Post by GooglePlexity on 2010-04-21
Wow, double post, I feel like such a noob.  Let me add, then, that you really also might be entirely satisfied with WordPress.  PHP is really not harder to tinker around in than Python and there's a wealth of plugins and themes.

---

### Post by Zerocool Djx on 2010-04-21
[http://ewebscapes.com/add-a-blog-to-your-existing-website/](http://ewebscapes.com/add-a-blog-to-your-existing-website/)

---

### Post by Swarms on 2010-04-21
> **Zerocool Djx said:**
> [http://ewebscapes.com/add-a-blog-to-your-existing-website/](http://ewebscapes.com/add-a-blog-to-your-existing-website/)

Why not buy some hosted service where you have a large amount of space and just use it for Wordpress as others suggested?

---

### Post by Untitled_No4 on 2010-04-21
> **whistlingtony said:**
> I'd like for me to have some folders. In the "Front Page" folder would text files. The web server would put those up as updates to the main page.

If I understand the original poster correctly, he doesn't want to tinker with control panel but rather drop text and image files to folders and have the website scan those folders and create the content from the files in those folders.
Never used Joomla, Drupl or Wordpress, but I don't think they can do that.
Additionally, he's looking for it to be in Python, while all three, correct me if I'm wrong, are written in PHP.

Well, I've never developed in Python but if you ever consider doing this in PHP let me know.

---

### Post by squilookle on 2010-04-21
I'm currently working on something not too dissimilar in php for my own website. 

Already did something similar for work, but that was in asp.

---

### Post by tgalati4 on 2010-04-22
Adding content to drupal is not much more difficult that selecting files from a dialog box.  It doesn't have the "drag-and-drop" functionality that the OP is looking for, but then you don't have to create a new framework to handle user interaction in a web page.  An AJAX page using Ruby-on-Rails comes close, but you are still going to have dialog boxes and lists to deal with.

The OP needs to be more specific on the use cases, otherwise we are just guessing.

The OP mentions that he hates facebook but doesn't say why.  Is it the closed-source nature of the code?  Doesn't like ads in his pages?  Doesn't like the fact that facebook can change its policies at any time?  Doesn't like the workflow of updating pages?

The OP also wants to tinker with python, but doesn't want to work with html and config files.  Well, if you run a web server, you will want to know html and you will have to tinker with config files.  No way around that.

If you don't want the hassle of running your own website, then there are a dozen blogging sites out there--all willing to take your money.  Wordpress is perhaps at the top, but there are other notable ones that can do the job.

All I see from this activity is a giant python script that writes html and modifies configuration files.  Tinkering in this script would more difficult than the html and config files themselves.  Am I missing something?

Perhaps the OP is interested in something that Apple developed:  [http://www.me.com](http://www.me.com)

---

### Post by whistlingtony on 2010-04-23
Hi all, thanks for the replies.

I DON'T want to tinker with a control panel, and I would like to drop text and image files into folders.

Heh, you're all thinking too big. I don't need a scaleable framework. I don't need mass functionality. I just want this little web server to create a page based on text and image files I drop into folders. I don't want any user interaction. It's just a diary or journal that I can let other people see.

I only want Python, because I like python. Coding in C or C++ gives me nightmares. I'm not a coder. I'm just a tinkerer. 

I know enough HTML to make a basic page, and that's all I want. I don't want flashy. Simple is good.

The fun of this is that I could run it off my netbook, or my phone. Fellow nerds might find it while poking the other boxes at the coffee shop. Also, I get to have control over it, not some faceless corp. 

Oh, and my hate of Facebook? I'm a recovered MMORPG addict. I don't want to get sucked in to something like that again. Stupid farmville. Stupid time wasting... Ok, and I hate the ads. 

I could just set up a blog. Sure. But that's boring. And then there's the ads again.

No Apache. No worrying about add ons. No worrying about config files. No worrying about security holes in wierd programs I didn't write. I want this to be usable by my Gramma. My nights of staring at green text at 2am are LONG GONE. I just want it to work.

All this needs to do is make some HTML to house the text, make some links based on the folder names, and serve 'em up. It's not complex, I've just never done this before. 

So.. again with my original question... I have money. How do I find someone with skill at programming to help me with this? Come on Open Source! I can't do this alone, but I can and will contribute my time and moolah. 

-Tony

---

### Post by Penguin Guy on 2010-04-23
> **whistlingtony said:**
> No Apache.
I don't think you properly understand what Apache is (even the simplest of webservers are very complicated) - a single programmer can't write a new one just like that, you'd need a whole team. And it's a pretty bad idea to write anything web-orientated in Python, since it's not really designed for the web. **I would strongly advise you use Apache and PHP.**

> **whistlingtony said:**
> So.. again with my original question... I have money. How do I find someone with skill at programming to help me with this?
If you will allow it to be written in PHP then there are plenty of people who've said they're willing to help you. Otherwise, [try Google]("http://www.google.com/search?q=find+a+programmer").

> I DON'T want to tinker with a control panel, and I would like to drop text and image files into folders.
I know how you feel - these content managers are all too clever. :)

---

### Post by MaxIBoy on 2010-04-23
Joomla is pretty easy to install-- just setup an FTP server, SQL server, and NGINX, then you can literally unzip it, visit the new website, and click through the installation procedure.

However, Joomla is way overkill for a lot of tasks, and while it's pretty easy, I'd be willing to go for something a bit more minimalist if one was written.

---

### Post by Penguin Guy on 2010-05-16
There are probably a few open source people who'd do this for free, but if you really want to hire someone then you should check out the [Community Market]("http://ubuntuforums.org/forumdisplay.php?f=38"), specifically [this]("http://ubuntuforums.org/showthread.php?t=1482487") post.

---

