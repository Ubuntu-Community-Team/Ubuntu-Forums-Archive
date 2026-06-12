---
title: "detecting server problems"
date: 2008-02-26
forum: Security Discussions
---

### Post by rendon on 2008-02-26
Hello!

I would like to ask some questions, I hope you have some time to answer.

I'm not a real newbie to linux, I'm also comfortable with linux command line, and a lot of programming languages.  But in this particular case I don't know what to do.

I'm responsible for a web server in my company running Ubuntu, and the past week it's been acting a little funny.  First the webpages weren't loading completely, and it said it was "loading from www.somebodyElsesWebsite.com..." at the bottom status bar. but never finished loading the page, just about half of the page every time.  Then it looked like it was trying to get info from somebody else's server... odd?

Then there was even a period of time when it wasn't working at all, the website was down and I couldn't log in...  somebody had to call the place where the server is housed to check on it... they did something... then it was working again.  Of course you will say: "Why didn't you ask those guys what they did?"  ...don't ask!  I'm in China and these people just don't want to communicate.

As of now I can still log in and it seems stable for the moment, but I would like to know where these problems are all coming from...?

I read all of the *stickies* here and I'm going to start using tools such as "tiger" and start setting my "ip tables" for more security, etc...

but for now, I want to know what happened in the past..?  

Should I check syslog?  what should I look for?  or is there another log that can tell me what went wrong at X date and Z time?

I checked the syslog for the time the server went down last and didn't see anything special, or at least, I didn't recognize it at a problem.  I might have to research some of the syslog entries, I must confess I don't understand them all.

Any suggestions?

I have a suspicion that the place where the server is house might be responsible for this problem, sorry I don't know how to refer to this "place".  Is it a hosting provider?  But I can't say for sure...

All responses appreciated!

---

### Post by K.Mandla on 2008-02-26
I'm going to shift this one to Security Discussions, since it *sounds* more like a security problem than a software problem.

For what it's worth (and my opinion on this is quite worthless), I would be suspicious of the hosting site, if they can do "something" and magically things work right. Again, I'm the least knowledgeable person on this though.

---

### Post by rendon on 2008-02-26
I'm not sure...

that's why I have a problem consolidating this issue.  I don't know which of the following might be the problem:

1) security issue
2) hardware issue
3) problem with the hosting house
4) Ubuntu operating system bug
5) something I did to the settings of the server

So, I'm kind of at a loss here, and feel overwhelmed.  That's why I was hoping someone here with some expertise or knowledge in this field might be able to help.

I want to know if there are some logs or services provided in the Ubuntu server OS which will help me investigate this issue.

So, wherever this thread ends up, I just hope someone who would like to help a fellow "Ubunter" can find this thread and give me a tip!

---

### Post by Mr. C. on 2008-02-29
Let me make sure I understand.

You are trying to browse [www.yourWebsiite.com](www.yourWebsiite.com) and you instead see [www.somebodyElsesWebsite.com](www.somebodyElsesWebsite.com) ?

Let's start with the fundamentals.

When the site is working, what IP address does [www.yourWebsiite.com](www.yourWebsiite.com) resolve to vs. when the site is not working?  In other words, is this a DNS problem.  If so, who's DNS servers are being used?  Do the DNS servers actually point your website to either your DNS provider or ISP so that the perform URL relocation or framing ?

If DNS always resolves to your website, and you are not using any of the redirecting services mentioned above, do you have any proxy servers running?

Of your 5 possibilities below, the problem you describe does not sound like 2 or 4.  Option 1 is a possibility, but without know more precisely what is going on, you won't find the issue anyway.  So let's examine the others.  Option 3: this is possible.  But you'll have to describe your hosting setup more (virtual server? shared server, your own hardware, etc.).   Option 5:  Very possible.  You're going to have to get down to the bedrock and see exactly what is happening.

Start by identifying some of the things I've suggested.

MrC

---

### Post by rendon on 2008-03-02
> **Mr. C. said:**
> Let me make sure I understand.

You are trying to browse [www.yourWebsiite.com](www.yourWebsiite.com) and you instead see [www.somebodyElsesWebsite.com](www.somebodyElsesWebsite.com) ?

Let's start with the fundamentals.

When the site is working, what IP address does [www.yourWebsiite.com](www.yourWebsiite.com) resolve to vs. when the site is not working?  In other words, is this a DNS problem.  If so, who's DNS servers are being used?  Do the DNS servers actually point your website to either your DNS provider or ISP so that the perform URL relocation or framing ?

If DNS always resolves to your website, and you are not using any of the redirecting services mentioned above, do you have any proxy servers running?

Of your 5 possibilities below, the problem you describe does not sound like 2 or 4.  Option 1 is a possibility, but without know more precisely what is going on, you won't find the issue anyway.  So let's examine the others.  Option 3: this is possible.  But you'll have to describe your hosting setup more (virtual server? shared server, your own hardware, etc.).   Option 5:  Very possible.  You're going to have to get down to the bedrock and see exactly what is happening.

Start by identifying some of the things I've suggested.

MrC

Mr. C,  Thanks for your response.

The problem I was having stopped after I rebooted the server.  So currently it is not a problem.  It was only happening for about an hour or so.  It wasn't completely redirecting my companies URL to another website's server.  It was downloading half of my websites webpages, and then just hanging there... apparently still trying to load the page, but never completing.  During the time that it was "hanging", I could see on the Firefox "status bar" (at the bottom) it said something like "downloading from www.somebodyElsesSite.com" or "loading from www.somebodyElsesSite.com" or something along those lines.

So it was as if the the connection was getting cut of half way through the process of downloading pages.  Every page I viewed during that time was only giving 50% content.

And then, a couple days later, the server just went down.  Stopped working, and I don't know why or how, but somebody at the "IDC" got it back up and working again.

Now I will try to explain my server's configuration:

Number 1.  Our company owns our own server, we have installed our own operating system on it (Ubuntu), and we have bought a static IP address which I have configured to perform DNS for our domain name.

Number 2.  Where is the server?  Well, I know the answer to this question, but I don't know how to say it!  It at this building with hundreds of other servers.  We pay them money to keep our server there and connect it to the internet, and provide a fast internet connection for our machine.  We do this, of course, because it would be incredibly expensive to have a T1 line run directly to our office.  I guess this place is called a hosting provider, but I don't konw... I think that sounds weird because a "hosting provider" in my humble opinion is the company I pay money to use "their" server for my website... not to use "my" server in "their" location.

Number 3.  configurations.  I basically set up and configured the server myself.  I didn't think I would need to set up any firewalls or virus protection with Linux, but now I'm thinking differently.  I believe that I have the IP and DNS information set up correctly because it's been working fine for months now until these recent odd events.  I can't remember exactly which commands I used (maybe netstat and/or ifconfig), but I remember researching what I needed before I did the job, and I set up the static IP, netmask, submask, etc... as needed.  Then rebooted a couple of times to make sure it was working on it's own.

That's about all the info I can give.  After reviewing this myself, I still feel as though any one of the options I gave might be reponsible for the problems I was having.  And since there were 2 different problems at 2 different times, I might have experienced 2 different problems.

Thanks to anyone who can give more support on this topic, especially if you know which logs I might check or what info I might look for to best investigate the source of these problems.  Unfortunately, I didn't make a habit of checking logs regularly from the beginning (mostly because I'm too busy with work), so I don't really know what a healthy log is "supposed" to look like :(

---

### Post by Mr. C. on 2008-03-08
Sorry for the delay.  It doesn't sound like there are any issues here to resolve, right?

---

### Post by rendon on 2008-03-09
> **Mr. C. said:**
> Sorry for the delay.  It doesn't sound like there are any issues here to resolve, right?

As of now, things are up and working fine.  I'm just nervous about what happened before, especially since we will be building up a strong user base on our website.  It would be horrible if the server suddenly went down or had "weird" problems again after everyone starts logging in.


Since the problems began I have installed and started using "logwatch" and "tiger".  These applications are helping me to view security holes and see other mishaps, but I still haven't found the cause of the critical issues I was having before.

I guess we'll just have to wait and see if it happens again.

Thanks for your concern...

---

