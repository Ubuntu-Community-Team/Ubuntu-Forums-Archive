---
title: "BASH scripts on servers for websites"
date: 2011-08-11
forum: Server Platforms
---

### Post by meridionaljet on 2011-08-11
Hello,

I am planning on hosting a website soon, on a linux server, of course. I am new to server-land, and I would like to know how effective it would be to set up BASH scripts on the server to automatically download and process data, and then upload it to my website. Is it even possible? Do servers allow website owners to place BASH scripts that can run automatically, or keep running indefinitely? Information, experience, or opinion regarding this idea would be appreciated.

---

### Post by MG&amp;TL on 2011-08-11
i have absolutely no clue or experience in this whatsoever (not a web person) but the maintainer of LinuxCommand.org says in his tutorials that some sections of his web pages are built via a bash scripts that runs every week. So assumably it's possible.

Good luck on your server-venture. :D

---

### Post by Habitual on 2011-08-11
[http://www.webhostingtalk.com/](http://www.webhostingtalk.com/) may know how/if/when

---

### Post by Lars Noodén on 2011-08-12
Your web site is just a bunch of files in the filesystem, so anything that your script chooses to write to that part of the filesystem will show up on the web site.  The scripts can do just about anything you can imagine.  Can you give more details about where the data is coming from and how it is to be manipulated?

You can also use other scripting languages than Bash, such as Python or Perl.

---

### Post by meridionaljet on 2011-08-12
> **Lars Noodén said:**
> Your web site is just a bunch of files in the filesystem, so anything that your script chooses to write to that part of the filesystem will show up on the web site.  The scripts can do just about anything you can imagine.  Can you give more details about where the data is coming from and how it is to be manipulated?

You can also use other scripting languages than Bash, such as Python or Perl.

Ideally I would like to have scripts maintain many things on my site, but perhaps my largest example is having a script download images from the internet, manipulate them (crop, resize, etc), and then create an updated GIF animation that gets uploaded to my website (I suppose to FTP, so I can link to it in my HTML file).

I just need to be sure that they actually give me enough permissions to run such scripts in my own section of the server. If they give me SSH, I am hoping that this is possible, so that my website content can be constantly updated.

---

### Post by LemursDontExist on 2011-08-12
It depends on the hosting you get.  If you want to reasonably be able to run bash scripts you'll need hosting that gives you shell access - ideally via ssh.  Any VPS service should provide that, as do many shared hosts.  If you're looking for a good shared host, [Bluehost]("https://www.bluehost.com/") has reasonable rates good customer service and provides shell access on request.  

Many of the real discount hosting options only allow ftp access or access via a control panel, which would make shell scripting difficult to manage if not impossible.

So, using bash scripts on a web server is very common, and easy to do - just make sure your web hosting provider gives shell access.

---

